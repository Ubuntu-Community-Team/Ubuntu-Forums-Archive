---
title: "Can I change the currently playing track from the command line?"
date: 2012-06-08
forum: Programming Talk
---

### Post by Maheriano on 2012-06-08
I found a way to change the volume without installing any third party applications but now I'm trying to change to next track. For example in Banshee or Rhythmbox. How can I change the track inside the terminal?

---

### Post by diesch on 2012-06-08
Have  a look at [rhythmbox-client]("http://manpages.ubuntu.com/manpages/precise/en/man1/rhythmbox-client.1.html")

---

### Post by codemaniac on 2012-06-09
I really like mplayer for its native bash scripting support .

You can do wonders with mplayer with some bash scripting knowledge .

[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

---

### Post by andrew.46 on 2012-06-09
Mplayer can do this when using a playlist:

[https://help.ubuntu.com/community/MPlayerTips#Tip_8:_Using_playlists](https://help.ubuntu.com/community/MPlayerTips#Tip_8:_Using_playlists)

---

### Post by roelforg on 2012-06-11
Or vlc using either the web (in combination with links(2)), telnet, etc interface.

---

### Post by Maheriano on 2012-06-12
Thanks guys, I'm writing an Android application which will incorporate the ability to change the track/volume of a song already playing on your machine. So I'm looking for something which sends the command to the already playing application and I'm fairly certain most people don't use Mplayer and VLC for their music playback. Do they? I figured Banshee and Rhythmbox would be at the top so I'll incorporate those plus it looks like Rhythmbox at least has the ability to query the current track and display it on the handset.

If you come up with any other ideas with the new criteria please post it here, I'll add it and let you know where you can download it!

---

### Post by doorknob60 on 2012-06-12
In Banshee:
```


austin@austin-desktop ~ % banshee --help-playback
Usage: banshee [options...] [files|URIs...]

Playback Control Options

  --next                     Play the next track, optionally restarting if the
                             'restart' value is set

  --previous                 Play the previous track, optionally restarting if
                             the 'restart' value is set

  --restart-or-previous      If the current song has been played longer than 4
                             seconds then restart it, otherwise the same as
                             --previous

  --play-enqueued            Automatically start playing any tracks enqueued on
                             the command line

  --play                     Start playback
  --pause                    Pause playback
  --toggle-playing           Toggle playback
  --stop                     Completely stop playback
  --stop-when-finished       Enable or disable playback stopping after the
                             currently playing track (value should be either
                             'true' or 'false')

  --set-volume=LEVEL         Set the playback volume (0-100), prefix with +/-
                             for relative values

  --set-position=POS         Seek to a specific point (seconds, float)
  --set-rating=RATING        Set the currently played track's rating (0 to 5)

```

---

### Post by roelforg on 2012-06-12
> **Maheriano said:**
> Thanks guys, I'm writing an Android application which will incorporate the ability to change the track/volume of a song already playing on your machine. So I'm looking for something which sends the command to the already playing application and I'm fairly certain most people don't use Mplayer and VLC for their music playback. Do they? I figured Banshee and Rhythmbox would be at the top so I'll incorporate those plus it looks like Rhythmbox at least has the ability to query the current track and display it on the handset.
 
If you come up with any other ideas with the new criteria please post it here, I'll add it and let you know where you can download it!
 
Mplayer, dunno
VLC, Used very much. It's in the top 5 of players people use as an alternative to windows' crappy wmp, that counts for a lot of people. Same goes for linux. And VLC is very powerful: playlists, streaming (playing AND sourcing AND streaming (i remember how some versions even came with a build in streamingserver when compiled with the right switches and you used the right settings)), eq, huge array of configurations to tune your a and v in-/outputs, it uses the de-/encoding library ffmpeg uses (giving it a huge array of supported formats, no gstreamer that constantly needs plugins; vlc is even a framework on its own), fully embeddable, web/telnet/cli/dbus interface, the list goes on and on.

---

### Post by hakermania on 2012-06-12
An idea that will work with most applications, is to simulate the > (Next) key that most PCs have with a program that simulates keyboard input, but I haven't searched it a lot...

---

### Post by diesch on 2012-06-12
If you are into DBus programming you could try to use the Sound-Indicator interface to controll any app that uses the Sound Indicator.

---

### Post by Maheriano on 2012-06-14
How do I show a slider bar for how much of the song has elapsed? I'm trying to run ```
deemar@Olsen:~$ DISPLAY=:0 rhythmbox-client --print-playing-format=%td

``` but it doesn't return anything. Always blank. I was going to subtract the elapsed time from the track duration and do it that way. Is that wrong?

---

### Post by Maheriano on 2012-06-22
Does anyone know how to seek the current track in rhythmbox-client? I try the help which says there is a command:

> deemar@Chugger:~$ rhythmbox-client --help
Usage:
  rhythmbox-client [OPTION...]

Help Options:
  -h, --help                               Show help options

Application Options:
  --debug                                  
  --no-start                               Don't start a new instance of Rhythmbox
  --quit                                   Quit Rhythmbox
  --check-running                          Check if Rhythmbox is already running
  --no-present                             Don't present an existing Rhythmbox window
  --next                                   Jump to next song
  --previous                               Jump to previous song
  --seek                                   Seek in current track
  --play                                   Resume playback if currently paused
  --pause                                  Pause playback if currently playing
  --play-pause                             Toggle play/pause mode
  --play-uri=URI to play                   Play a specified URI, importing it if necessary
  --enqueue                                Add specified tracks to the play queue
  --clear-queue                            Empty the play queue before adding new tracks
  --print-playing                          Print the title and artist of the playing song
  --print-playing-format                   Print formatted details of the song
  --select-source=Source to select         Select the source matching the specified URI
  --activate-source=Source to activate     Activate the source matching the specified URI
  --play-source=Source to play from        Play from the source matching the specified URI
  --set-volume                             Set the playback volume
  --volume-up                              Increase the playback volume
  --volume-down                            Decrease the playback volume
  --print-volume                           Print the current playback volume
  --set-rating                             Set the rating of the current song



So I try to use it by typing:

> deemar@Chugger:~$ DISPLAY=:0 rhythmbox-client --seek=34

and the track simply restarts.

So I try:

> deemar@Chugger:~$ DISPLAY=:0 rhythmbox-client --seek=+34

using a plus sign and again it just restarts the track. I can't get it to seek at all, everything I try just causes the track to restart.

---

### Post by __j__ on 2012-07-12
> **Maheriano said:**
> I can't get it to seek at all, everything I try just causes the track to restart.

I'm seeing the same thing. 'rhythmbox-client --seek (secs)' always sets the position of the current track to 0. This happens whether the track is playing or paused.

I took a (very) quick look at the Rhythmbox source. The --seek flag seems to use the "SetPosition" method implemented in rb-mpris-plugin.c. Looks like something may be awry with the relative position calculation. This is a bummer...it would be a really handy feature! May dig further to see what's up...

---

### Post by __j__ on 2012-07-13
A little digging into the seek issue led to a more complete answer for the original poster's question:

All the major media players (Rhythmbox, Banshee, Amarok, etc) implement a dbus interface that supports external control of expected functions: play/pause, previous/next, seek, etc. For Rhythmbox, 'rhythmbox-client' is a small, separate program that simply takes command line arguments (e.g. --next) and sends the corresponding commands to a running rhythmbox instance using this dbus interface. Very handy.

Of course, we can do the same thing rhythmbox-client does...which is good because 'rhythmbox-client --seek' has a bug: it sends a message to the wrong dbus method ("SetPosition" instead of "Seek"). And these take their arguments in microseconds, not seconds, so 'rhythmbox-client --seek 10' is moving (when it should be seeking) to 10 *microseconds* into the track, which sounds rather like the beginning. :)

Where rhythmbox-client works for you, just use that. Where it doesn't (e.g. --seek), just make the right dbus call in your favorite scripting language, and call that script. Here are some shell examples:

```
# seek forward 10 sec
dbus-send --print-reply --dest=org.mpris.MediaPlayer2.rhythmbox /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Seek int64:10000000

# skip to next track
dbus-send --print-reply --dest=org.mpris.MediaPlayer2.rhythmbox /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Next

# toggle play/pause state
dbus-send --print-reply --dest=org.mpris.MediaPlayer2.rhythmbox /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlayPause
```

A bit too verbose for routine command line use, so just pop them into conveniently named scripts, and away you go! The list of commands can be found here:
[http://standards.freedesktop.org/mpris-spec/2.0/Player_Node.html](http://standards.freedesktop.org/mpris-spec/2.0/Player_Node.html).

---

