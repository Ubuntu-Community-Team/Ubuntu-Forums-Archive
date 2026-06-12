---
title: "HOWTO: 4 Channel output with RhythmBox"
date: 2006-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by EvanL on 2006-08-25
**[COLOR="Red"]Note: Scroll down to post #3 for a much better way to do this.[/COLOR]**

Finally figured out how to get 4-channel output from RhythmBox for MP3 Playback.  This HOWTO is for ICH8x0 AC'97 cards, although it may work for other sound systems.  Basically, YMMV.

1) Create a .asoundrc file in your home directory.

```
gedit ~/.asoundrc
```

2) Copy the configuration from [this thread]("http://www.ubuntuforums.org/showthread.php?t=167986&highlight=.asoundrc+xmms") into the new file.

```
pcm.ch40dup {
type route
slave.pcm surround40
slave.channels 4
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
}

pcm.ch51dup {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

```

3) Run gstreamer-properties

```
gstreamer-properties
```

4) Under "Default Output Plugin," choose "Custom" then enter the following line in your Pipeline input box.

```
alsasink device=ch40dup
```

5) That's it!  Test RhythmBox to make sure it works!

Note that entering ```
alsasink device=ch51dup
``` should work for 5.1 systems, but I don't have a 5.1 system to test it on, so that one's up to you.

An interesting note is that the alsamixer slider volume control for surround doesn't work, but the surround mute function does work.

---

### Post by EvanL on 2006-09-16
Update, I found a better way to do this:

Use the code found [here]("http://alsa.opensrc.org/FAQ028") for your .asoundrc file. Note that I changed "hw0,1" to "hw0,0".  Code is pasted below:

```
pcm.dmixs51 {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 4096
    }
}
pcm.duplicate {
    type plug
    slave.pcm "dmixs51"
    slave.channels 6
    route_policy duplicate
}

```

Now in gstreamer-properties, change your output plugin to: 
```
alsasink device=duplicate
```

Now you should have downmixing capabilities in addition to playing stereo files on multiple channels.

-Evan

---

### Post by EvanL on 2006-10-30
New .asoundrc file.  This works for me on the Intel ICH8x05 chipset.  Aoss and ALSA will play together nicely, but for the life of me, I can't get firefox to output sound when I'm running another sound source.  Unbelievably annoying.  Anyway, here's the file:

```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
	type hw
	card 0
	device 0
}

pcm.dmixs40 {
	type dmix
	ipc_key 1024
	ipc_key_add_uid false
	ipc_perm 0666
	slave {
		pcm "snd_card"
		rate 48000
		channels 4
		period_time 0
		period_size 1024
		buffer_time 0
		buffer_size 4096
	}
}

pcm.duplicate {
	type plug
	slave.pcm "dmixs40"
	slave.channels 4
	route_policy duplicate
}

pcm.input {
	type dsnoop
	ipc_key 2048
	ipc_key_add_uid false
	ipc_perm 0666
	slave.pcm "snd_card"
}

pcm.asym40 {
           type asym
           playback.pcm "dmixs40" 
           capture.pcm "input" 
}

pcm.!defualt{
	type plug
	slave.channels 4
	slave.pcm "asym40"
	bindings{
		0 0
		1 1
		2 2
		3 3
	}
}

###############
#     OSS     #
#  Emulation  #
###############

pcm.dmix0 {
        type dmix
        slave {
                pcm "hw:0,0"
                rate 44100
                channels 2
        }
}

pcm.dsp0 {
	type plug
#	slave.channels 4
	slave.pcm "dmix0"
#	slave.pcm "dmixs40"
#	ttable.0.0 0.5
#	ttable.1.1 0.5
#	ttable.0.1 0.5
#	ttable.1.0 0.5
}

```

---

