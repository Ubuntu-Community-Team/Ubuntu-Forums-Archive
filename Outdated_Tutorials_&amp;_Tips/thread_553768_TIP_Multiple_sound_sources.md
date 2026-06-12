---
title: "TIP: Multiple sound sources"
date: 2007-09-18
forum: Outdated Tutorials &amp; Tips
---

### Post by bunker on 2007-09-18
This is just a quick one I thought I'd document because there seem to be many workarounds and "kinda" solutions that don't really address the problem.  (Also note that some cards support hardware mixing to different degrees so some things that work for some people do not work for others)

First of all, let's solve the most common one: amarok's "xine cannot initialise any audio drivers" error.  It's often a permissions error (If you run amarok as root there is no problems).  Check that you are in the 'audio' group, or if you're running a non-standard configuration, whichever group owns the sound devices.  This solves the vast majority of problems.

If it does not, then change the settings in Settings->Configure Amarok->Engine and change the output plugin to Audodetect.  Strange but true.  (By the way, this is why deleting amarokrc also works).

Next up: mixing with ALSA.  This is copied shamelessly from [http://alsa.opensrc.org/index.php](http://alsa.opensrc.org/index.php) - which is very good source for fixing audio problems.

Note: first try *$ aplay testfile.wav* in two consoles at the same time.  If one of them does not say "device busy" (or words to that effect) then your problem lies elsewhere.  This is the definitive way to check that mixing is working.  Simply running different sound playing programs won't do.  Eg, flash and vlc will work fine together without software mixing under some circumstances.  Further, note that not all sound cards that support hardware mixing have drivers that actually implement it ;)

Put this in ~/.asoundrc or if you'd like to apply it to every user /etc/asound.conf

```

pcm.my_card {
  type hw
  card 0
  # note this is ONLY for my sound card (via 82xx) - most hardware does not need a special sub-device.  
  # If you do have multiple sub-devices, test them with aplay -D hw0,x testfile.wav where x is one of the sub-devices.
  # Other threads have better info on how to find out details like this on your card
  device 1
}

# for outputting sound
pcm.dmixed {
    type dmix
    ipc_key 1024
    # let multiple users share
    # ipc_key_add_uid false
    # IPC permissions for multi user sharing (octal, default 0600)
    # ipc_perm 0666           
    slave {
    pcm "my_card"
    #   rate 48000
    #   period_size 512
    }
}

# for recording sound
pcm.dsnooped {
    type dsnoop
    ipc_key 2048
    slave {
    pcm "my_card"
    #   rate 48000
    #   period_size 128
    }
}

# combines half duplex to full duplex with the asym plugin
pcm.asymed {
    type asym
    playback.pcm "dmixed"
    capture.pcm "dsnooped"
}

# does automatic sample rate conversion
pcm.pasymed {
    type plug
    slave.pcm "asymed"
}

# for OSS compatability
pcm.dsp0 {
    type plug
    slave.pcm "asymed"
}

# sets the default device as your mixed device
pcm.!default {
    type plug
    slave.pcm "asymed"
}

# says what the mixer will control
ctl.!default {
  type hw
  card 0
}

```

This should work verbatim on most sound cards, though YMMV on the more weird breeds, hence TIP not HOWTO :).  If you still have problems, experiment with telling applications to use specific devices, not just the default.

Anyway, this should hopefully save you from the hassle of setting up a sound server and finding apps that are aware of them.

---

### Post by darck on 2007-12-14
how to mix that with my code which output sound simultaneously to 2 sound cards?

```
pcm.!default {
	type plug
	slave {
		pcm multi
	}
	ttable.0.0 1.0
	ttable.1.1 1.0
	ttable.0.2 1.0
	ttable.1.3 1.0
}

pcm.multi {
	type multi
	slaves.a.pcm "hw:0,0"
	slaves.a.channels 2
	slaves.b.pcm "hw:1,0"
	slaves.b.channels 2
	bindings.0.slave a
	bindings.0.channel 0
	bindings.1.slave a
	bindings.1.channel 1
	bindings.2.slave b
	bindings.2.channel 0
	bindings.3.slave b
	bindings.3.channel 1
}

ctl.!default {
	type hw
	card 1
}

```

---

