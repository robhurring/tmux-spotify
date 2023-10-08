# Tmux Spotify Plugin

Tmux plugin that shows the current music status for Spotify, Apple Music, or iTunes in your statusline.

Introduces the following new status variables:

* `#{music_status}`
* `#{artist}`
* `#{album}`
* `#{track}`

### Usage

The following interpolations are made available for your statusline:

* `#{music_status}` - Spotify status icons
* `#{artist}` - Current artist
* `#{album}`  - Current album
* `#{track}`  - Current track

Here's the example in `.tmux.conf`:

```bash
set -g status-right "♫ #{music_status} #{artist}: #{track} | %a %h-%d %H:%M "
```

Customize the icons with:

```bash
set -g @spotify_playing_icon ">"
set -g @spotify_paused_icon "="

# optional: defaults to `paused_icon`
set -g @spotify_stopped_icon "X"
```

By default, Spotify is used as the media source. iTunes or Apple Music can be used by setting `MUSIC_APP` in your `bashrc`:

```bash
# set tmux-spotify to use Apple Music instead of Spotify
export MUSIC_APP="Music"
```

Set `MUSIC_APP` to `iTunes` instead on macOS Catalina.

If the `status-right` overflows when the music title is too long, you can increase the `status-right-length` by using the following line in `.tmux.conf`:

```bash
set -g status-right-length 70
```

### Screenshots

![status](/screenshots/spotify-status.png)

### Installation with [Tmux Plugin Manager](https://github.com/tmux-plugins/tpm) (recommended)

Add the plugin to the list of TPM plugins in `.tmux.conf`:

```bash
set -g @plugin 'robhurring/tmux-spotify'
```

Hit `prefix + I` to fetch the plugin and source it.

### Manual Installation

Clone the repo:

```bash
$ git clone https://github.com/robhurring/tmux-spotify ~/clone/path
```

Add this line to the bottom of `.tmux.conf`:

```bash
run-shell ~/clone/path/music.tmux
```

Reload the TMUX environment:

```bash
# type this in the terminal
$ tmux source-file ~/.tmux.conf
```

