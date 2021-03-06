# mpdnotify

Sends a notification when mpd song changes. Forked from [chuugar's mpdnotify](https://github.com/chuugar/mpdnotify).

![mpdnotify](https://raw.githubusercontent.com/tadeassoucek/mpdnotify/master/screenshot.png)

## Installation

It has been tested on Manjaro 20.1.2, and it should work on any other Linux distribution with Python >= 3.2.

### Requirements

* `notify-send`
* Python >= 3.2
* [Pillow](https://github.com/python-pillow/Pillow)
* [python-mpd2](https://github.com/Mic92/python-mpd2)

### Installation

~~~
git clone https://github.com/tadeassoucek/mpdnotify.git
cd mpdnotify
pip3 install -r requirements.txt -e .
~~~

## Usage

A few arguments can be passed to mpdnotify:

* **`-a` / `--appname`**: specifies the app name for notify-send.
* **`-c` / `--config`**: path to the configuration file.
* **`-f` / `--titleformat`**: format for the notification title ([see here](#formatting)).
* **`-b` / `--bodyformat`**: format for the notification body ([see here](#formatting)).
* **`--host`**: mpd's address.
* **`-m` / `--musicdir`**: path to mpd's music library folder.
* **`-p` / `--port`**: mpd's server port.
* **`-o` / `--oneshot`**: send a notification and exit immediately.
* **`-t` / `--timeout`**: amount of milliseconds for which notification will be shown.

All of these arguments can be save in a configuration file, please see [`mpdnotifyrc.sample`](https://github.com/tadeassoucek/mpdnotify/blob/master/mpdnotifyrc.sample) for further informations.

**Once running, `mpdnotify` will wait for the next song to send a notification** (unless **`-o` / `--oneshot`** has been passed).
Cover is used as notification icon if a file called `(cover/front/album).(png/jpg)` is find in the same folder as the music file.

## Formatting

You can use these values in title and body formats:

* `{title}`
* `{album}`
* `{artist}`

If you want to use literal curly brackets, double them like this:

    {{NOW PLAYING}} {title} - {album} ({artist})

That would look like this while playing, for example, the song [IRC by Master Boot Record](https://masterbootrecord.bandcamp.com/track/irc):

    {NOW PLAYING} IRC - INTERNET PROTOCOL (MASTER BOOT RECORD)
