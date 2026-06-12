---
title: "Bizarro sound (bluetooth?) problem"
date: 2017-12-17
forum: New to Ubuntu
---

### Post by kate.t on 2017-12-17
Hi everyone, 

I have a sound problem the likes of which I cannot find elsewhere, even after days of googling.

My laptop, a Lenovo G-50-70, runs ubuntu 16.04.3 LTS. Except for a sound stuttering problem when streaming audio, my bluetooth Tower Stereo speakers were connecting and playing nicely with ubuntu via bluetooth until the other day.

But suddenly I get no sound. But that's not *quite *true. My speakers show up as a choice in Sound Settings. When I click to test the speakers, the voice saying "Front left", "Front right" rings loud and clear. Other system sounds show up fine, like notifications for an RSS feed.

But I cannot play music. YouTube videos "play" on the screen, but no sound comes out. (The sound will come out of the internal speakers just fine.) When I play CDs on the hard drive, there is no sound from the speakers either, although in rhythmbox it "looks" like it's playing. 

Hold on! I just now tested something, and it's another weird quirk. I decided to try to play a CD on the CD drive, and the sound came out of the speakers!!! With the same stupid, annoying stuttering, but I suppose fixing that's for another day and another thread. The mystery is thus compounded. What would make the audio from online streaming and the CDs on the hard drive fail, but permit the CD drive to function properly? That would suggest it's definitely a bluetooth problem, yes?

Thanks in advance for any advice!

Kate

---

### Post by Autodave on 2017-12-17
Sure sounds like a bluetooth issue.  Is there another bluetooth  device close by that may be causing interference?  You may want to move everything else bluetooth far away and see what the speakers do then.

---

### Post by kate.t on 2017-12-17
Autodave,

Thanks for your response. The only other bluetooth device I have is my smartphone, so I made sure bluetooth was turned off (it was) and then for good measure I put it in airplane mode.

Here's what's weird: I earlier got an "extra" device picked up on a search by blueman, listed by MAC address. I removed the device. I then ran a search again, and yet ANOTHER MAC address popped up.

The thing is, I have no other bluetooth devices. What do I do? Are these my next-door neighbors?

---

### Post by Autodave on 2017-12-18
Could be neighbors, but they would have to be rather close to you. I am no expert on bluetooth devices: I prefer my 21" screen to a phone's 4" screen. :-)

I really doubt that a device more than 20 feet away would affect you. (Again, I am NOT an expert on bluetooth.)  Are you using a bluetooth mouse or keyboard?

---

### Post by kate.t on 2017-12-18
No, Autodave, I use my laptop's keyboard and a USB mouse. Bewildering, isn't it? Let me know if you need more information from me, and thanks for your responses.

---

### Post by Autodave on 2017-12-18
Are you sure that there are no other bluetooth items around?  There are so many today that you may have one that you are not thinking of: TV, music player, etc.

When you scan for other ones, do you keep "finding" the same ones as before?  Maybe try moving about your house/apartment and see if you find or lose some.  That could give you an idea of where these unknown ones are actually at.

---

### Post by kate.t on 2017-12-18
While that sounds like a good idea, we have seriously LOW tech in this house. The stuff still functions after many years and our budget means that we make do. :)

---

### Post by Autodave on 2017-12-18
"When you scan for other ones, do you keep "finding" the same ones as  before?  Maybe try moving about your house/apartment and see if you find  or lose some.  That could give you an idea of where these unknown ones  are actually at." 				

Any luck doing that? It may eliminate your neighbors if that is what indeed is interfering.

---

### Post by jeremy31 on 2017-12-18
Hi kate.t
Still the same hardware as when you had the problems with mono audio on the Sony headset?  If you are using wifi at the same time, it could be issues with wifi interference

---

### Post by kate.t on 2017-12-18
Today I've been unable to "find" extraneous bluetooth devices anywhere in the house. They are nowhere to be found. Good!

Now I have another dreadful problem. Suddenly I'm unable to connect the tower stereo speakers, it says it pairs, but will not connect. The blueman icon flashes for a moment like it's connecting, but then it doesn't completely connect. So now I can't even try working on the problem! 

If you are still patient, do you have any suggestions for what to do about this, Autodave? I tried turning pulseaudio off and on, tried rebooting. Tried removing the stereo speakers and having blueman find them again. Nothing worked.

---

### Post by kate.t on 2017-12-18
Jeremy31,

Good to see you again!

Yes, it's the same laptop. What is so weird is that sometimes it works and sometimes it doesn't. And it seems like each time it doesn't work, it happens in a different way!

If it's the wifi and I turn that off, then I'm not going to be able to stream anything that's online. So that would mean just tough luck for me, right? There is no way to fix wifi interference?

---

### Post by #&amp;thj^% on 2017-12-18
> **kate.t said:**
> Jeremy31,

Good to see you again!

Yes, it's the same laptop. What is so weird is that sometimes it works and sometimes it doesn't. And it seems like each time it doesn't work, it happens in a different way!

If it's the wifi and I turn that off, then I'm not going to be able to stream anything that's online. So that would mean just tough luck for me, right? There is no way to fix wifi interference?

So far are we guessing that it is WiFi  interference?
@kate.t has anything you might have done changed? (Installed or changed packages or .conf files)

---

### Post by jeremy31 on 2017-12-18
kate.t see the wireless script link in my signature and upload the results to paste.ubuntu.com and post the URL.  There is a chance that using another channel for wifi might help if it is possible.  1fallen has seen your post and will likely post if he has any ideas

---

### Post by kate.t on 2017-12-18
Jeremy31,

Here's the url:

[http://paste.ubuntu.com/26211799/](http://paste.ubuntu.com/26211799/)

---

### Post by kate.t on 2017-12-18
Hi 1fallen,

Yes, I confess that I changed a couple of .conf files in my effort to fix the horrific stuttering audio. I changed them back right away when they didn't work. All except for one (or two? I think it was one). I am deeply ashamed to say I didn't write it down, but I do remember that the one that didn't get changed back to the original added "tsched=0" to a line of code.

Nice doggie pic, by the way.

---

### Post by #&amp;thj^% on 2017-12-18
> **kate.t said:**
> Hi 1fallen,

Yes, I confess that I changed a couple of .conf files in my effort to fix the horrific stuttering audio. I changed them back right away when they didn't work. All except for one (or two? I think it was one). I am deeply ashamed to say I didn't write it down, but I do remember that the one that didn't get changed back to the original added "tsched=0" to a line of code.

Nice doggie pic, by the way.

Well let's be sure to do that or check it anyway.
Post back this while jeremy31 looks at your script.
```
gedit /etc/pulse/default.pa
```
The Dog is Jake, now he is all red faced. (He is a shy guy)

---

### Post by kate.t on 2017-12-18
```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect tsched=0 
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input

#load-module module-bluetooth-discover
```

:smile:

---

### Post by #&amp;thj^% on 2017-12-18
> **kate.t said:**
> ```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect tsched=0 
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input

#load-module module-bluetooth-discover
```

:smile:

Ok Great now lets get rid of this "tsched=0"
Edit the line where it looks like the below:
```

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect[COLOR="#FF0000"] tsched=0[/COLOR] 
```
To look like this
```
load-module module-udev-detect
```
Using this code:
```
sudo gedit -H /etc/pulse/default.pa
```
Save and close the file.
and then run
```
pulseaudio -k
```
This "should" at least give you onboard sound. (PC Speakers)

---

### Post by kate.t on 2017-12-18
Done!

However, pulseaudio -k gives me this: 

```
E: [pulseaudio] main.c: Failed to kill daemon: No such process


```

Sounds dire...

---

### Post by kate.t on 2017-12-18
Also, my PC speakers already work fine, and with no stutter whatsoever. They just suck.

---

### Post by #&amp;thj^% on 2017-12-18
Nah not dire just the flaky pulseaudio.
Try this and report any errors thrown.
```
pulseaudio -D
```

---

### Post by kate.t on 2017-12-18
No errors, yay!

---

### Post by #&amp;thj^% on 2017-12-18
While we are waiting to see if jeremey31 has anything to add, if your not concerned with volume or privacy while listening>>>Do you have a Earphone Jack on your lappy, and do you have a jack on your headset for this?

---

### Post by kate.t on 2017-12-18
I don't mind volume or privacy issues.

---

### Post by kate.t on 2017-12-18
Another "in the meantime" matter: I can no longer get the tower stereo speakers to pair successfully with bluetooth. The latest error msg is "Connection Failed: blueman.bluez.errors.DBusFailedError: Resource temporarily unavailable" and the last error msg was "Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available".

So at the mo, I'm unable to test out any fixes until I can pair/connect this device. This has happened to me before, but I can't remember exactly what I did to fix it. (I'm a big help, I know.)

---

### Post by kate.t on 2017-12-18
Dinner calls, and I need to relax a bit, too. This has been driving me batty. But I'll be back!!):P

---

### Post by #&amp;thj^% on 2017-12-18
When you return give a try:
```
pactl load-module module-bluetooth-discover
```
Now try to pair the Speakers again. Or report any errors shown from the terminal.;)

---

### Post by kate.t on 2017-12-19
Good morning, 1fallen! 

Here's the latest result:

```
Failure: Module initialization failed


```

Is this where the non-connection problem lies?

Thanks!
Kate

---

### Post by jeremy31 on 2017-12-19
Hi
I was unable to find any issues in the script results.  You might have to shutdown and reboot when you can't pair with the speakers.  When you can't pair again look at results for ```
dmesg | tail
```
I would suspect hci timeouts

---

### Post by kate.t on 2017-12-19
Jeremy31,

Here were the results of dmesg | tail :

```
dmesg | tail
[   65.777054] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   65.779968] ata2.00: configured for UDMA/133
[   65.780465] ata2: EH complete
[  316.440149] mce: [Hardware Error]: Machine check events logged
[ 3591.532842] kauditd_printk_skb: 19 callbacks suppressed
[ 3591.532845] audit: type=1400 audit(1513643186.672:89): apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/usr/share/applications/python3.5.desktop" pid=1588 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[14166.582509] perf: interrupt took too long (2509 > 2500), lowering kernel.perf_event_max_sample_rate to 79500
[18510.804091] perf: interrupt took too long (3145 > 3136), lowering kernel.perf_event_max_sample_rate to 63500
[24298.666703] perf: interrupt took too long (3939 > 3931), lowering kernel.perf_event_max_sample_rate to 50750
[36916.211468] perf: interrupt took too long (4973 > 4923), lowering kernel.perf_event_max_sample_rate to 40000


```

Does this tell you what's wrong?

Thanks very much!
Kate

---

### Post by Autodave on 2017-12-19
My last thought: it won't cost you anything other than 10 minutes of your time. When I get a laptop that does unexplainable things (especially one where everything used to work normally), I always try this.  You would not believe how many are corrected by this.....

  	 	 	 	   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by kate.t on 2017-12-19
I have no peripherals.

Taking out the battery can fix pulseaudio???

---

### Post by #&amp;thj^% on 2017-12-19
> **Autodave said:**
> My last thought: it won't cost you anything other than 10 minutes of your time. When I get a laptop that does unexplainable things (especially one where everything used to work normally), I always try this.  You would not believe how many are corrected by this.....

  	 	 	 	   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.
+1 I can also recommend this from time to time.
I'm always surprised to see some improvements from this method Autodave has offered.

> **kate.t said:**
> I have no peripherals.

Taking out the battery can fix pulseaudio???
Well you do have some internal  peripherals. ;)
No it won't fix pulseaudio just a cleaner boot. (Providing no hardware problems or corruption in software)
Looks to me like things posibly have been corupted settings wise In addition this command takes care of stopping and respawning pulseaudio in case it hangs.

    Are there wrong user settings for the pulseaudio daemon?
    To test this we have to rename the settings directory in the affected user's HOME followed by a restart of pulseaudio.

```
 mv ~/.config/pulse ~/.config/pulse.bad  
```
**@kate.t you do not need to follow the below more as added info to try making this a more complete trouble shooting pulseaudio on Debian/Ubuntu.**
    Are channels muted from ALSA?
    We may open the alsamixer in a terminal to adjust channel volumes, and to unmute a channel in case it was accidentally muted:

   ```
 alsamixer
```

    Make sure users are not in the 'audio' group
    A user in the audio group has exclusive access to the pulseaudio server. Other users can not access it while this user uses it. Therefore user should not be in the audio group.
**kate.t please follow this below.**
    Start Pulseaudio manually
    In case pulseaudio was not running we can also start the daemon from command line with

   ```
 pulseaudio -D

```
    Pulseaudio then uses default settings and starts it's daemon. We can also put this command to our Autostart Applications to overcome the case when pulseaudio fails to run before the desktop was loaded.
If this is still a futile effort then we can try to look at debug logs but this is a very lengthy process. (Just a friendly heads up) :)

---

### Post by kate.t on 2017-12-19
I'm trying to unmute a channel in the Alsamixer (headphones), but can't remember what key to press to unmute it. Arrows don't work, tab is wrong, etc. Can you remind me?

---

### Post by kate.t on 2017-12-19
1fallen,

pulseaudio -D fails.

This is the result:

```
E: [pulseaudio] main.c: Daemon startup failed.


```

:(

---

### Post by kate.t on 2017-12-19
I figured out how to unmute the headphones in Alsamixer! :D

---

### Post by #&amp;thj^% on 2017-12-19
> **kate.t said:**
> I figured out how to unmute the headphones in Alsamixer! :D
Sorry i had a customer come in. Great Job in figuring that out! ;) unmute just press the "m" over the muted channel.
So any luck with the Speakers? Lets just try to stay with one device this go round if that's ok with you? Less confusing to our very fragile pulseaudio...LOL

---

### Post by kate.t on 2017-12-19
Now that I can't start pulseaudio, nothing happens when I turn on my bluetooth tower stereo speakers. Nothing at all.

---

### Post by kate.t on 2017-12-19
I am told by blueman that the "resource is unavailable."

---

### Post by #&amp;thj^% on 2017-12-19
Well lets see if we can motivate it then.
```
pulseaudio -k
```
Then run:
```
pulseaudio --start

```
Paste back the return from the last command please.

---

### Post by #&amp;thj^% on 2017-12-19
> **kate.t said:**
> I am told by blueman that the "resource is unavailable."
I Forgot to ask you to remove all devices shown in the blueman control.

---

### Post by kate.t on 2017-12-19
I didn't get very far. When I ran pulseaudio -k I got this:

```
E: [pulseaudio] main.c: Failed to kill daemon: No such process


```

:sad:

---

### Post by kate.t on 2017-12-19
Oh, and I restarted the computer before running the last commands. The only thing that happened was that the blueman icon totally disappeared from the top bar.

Yikes.

---

### Post by #&amp;thj^% on 2017-12-19
Yes that's to be expected it wasn't running in the first place.:) the "-k switch" just makes sure we dont start 2 pulseaudio instances.
Go ahead now and run the last command in my previous post and paste that back here.
Please wait for me to help you.... a restart with unfinished code suggestions could result in some nasty side effects. :(

---

### Post by kate.t on 2017-12-19
I ran the last command earlier, and I was just taken back to the prompt. Shows no problems.

---

### Post by #&amp;thj^% on 2017-12-19
Did you remove the devices yet? From Blueman.

---

### Post by kate.t on 2017-12-19
Yes, the devices were removed. I then was able -- yay! -- to pair and connect the tower speakers. Once again, when I test the speaker sounds ("front left", "front right"), the sound comes out of the speakers just fine.

But when I go to play Eric Clapton on YouTube, the sound comes out of the internal speakers, despite the choice of "Tower Stereo" being set in the Sound Setting. 

At least we're now back to the original problem in this thread!

---

### Post by #&amp;thj^% on 2017-12-19
There are other places to look also in "pavucontrol" ...Try to look for the Tab <Playback> should see your browser and make sure the right device is chosen there also.
Screenshot on mine shows Built in Audio.

---

### Post by kate.t on 2017-12-19
The Tower Stereo shows up in pavucontrol, and it's not muted.

Does it matter that the speakers are called a "headset" in the "Port" drop-down menu?

---

### Post by #&amp;thj^% on 2017-12-19
Not sure? You have had these speakers working recently right?

---

### Post by kate.t on 2017-12-19
Yes, they worked recently. If you can call horrific stuttering "working". But sound was coming out of the speakers just fine.

The latest hiccup. YouTube videos won't start, they just have a rotating circle in the center and the msg to restart the device if the video continues to balk. So I went to archive.org to play a streaming audio, and that won't start either.

Sigh.

---

### Post by #&amp;thj^% on 2017-12-19
pulseaudio dose not have any effect on page loading of browsers, must be something else.
But I am now wondering about some sort of interference, be it WiFi or poor connection to the Bluetooth Speakers.

---

### Post by kate.t on 2017-12-19
Okay, now YouTube works again. I discovered the reason why. When pavucontrol is up, the streaming audio stops completely. When I turn it off, the audio restarts. I checked this by turning it off and on multiple times, and that seems to certainly be the reason why the streaming audio stopped. WEIRD.

If WiFi is the interference, is there any fix? If I have to turn off WiFi, it defeats the whole situation, which is that I want to play streaming audio over WiFi. How to test this?

Hope I'm not driving you crazy...

---

### Post by #&amp;thj^% on 2017-12-19
> =kate.t;13722711
If WiFi is the interference, is there any fix? If I have to turn off WiFi, it defeats the whole situation, which is that I want to play streaming audio over WiFi. How to test this?

Hope I'm not driving you crazy...
I'm way past Crazy! :lolflag:
Well to see if we can do anything we will have to debug pulseaudio, Takes a bit of time to finish.
If you want to get started have a read here: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
Then when you have done that: post a link back for the logs it has recorded with:[https://paste.ubuntu.com/](https://paste.ubuntu.com/)
Then we can try to see what is going on...when trying to use the device with sound. (Try and note the time when you do that use the device with sound.)
Got to Dash for the evening see you tomorrow. Cheers!

---

### Post by kate.t on 2017-12-20
Hello again, 1fallen!

Well, that was VERY interesting.

On the second command (killall pulseaudio), I needed to run it as sudo, because without sudo this was the result:

```
pulseaudio(1305): Operation not permitted
pulseaudio(1526): Operation not permitted


```

Here's my url at pastebin: [https://paste.ubuntu.com/26223187/](https://paste.ubuntu.com/26223187/)

When I went to start up streaming audio at about 1:05 pm, to my SHOCK & UTTER AMAZEMENT it worked!!! Music (stuttering music, but music) poured out of my speakers!!! :guitar:


What is this, some sort of pulseaudio version of Schrödinger's cat, where looking at the process up close alters the outcome (in this case, we have a live cat)??

What does all this mean?

Yours truly,
Deeply Perplexed

---

### Post by #&amp;thj^% on 2017-12-20
Dear Deeply Perplexed 
   Fear not all is not lost. (Pretty Good Huh?) LOL
let me look at the pasted text, and try to find anything that hopefully might be obvious! (Could happen!)

---

### Post by #&amp;thj^% on 2017-12-20
Holy Crap! Is this a Pre-installed System? (Installed by manufacturer)
**EDIT: kate.t will you show me the out put of this also please.**
```
lspci -knn | grep Net -A3; lsusb 
```

---

### Post by kate.t on 2017-12-20
Thanks for the encouragement! :KS

This computer was purchased from a company that takes Lenovo computers and installs Linux on them and sells them.

Here's the info:```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo RTL8723BE PCIe Wireless Network Adapter [17aa:b736]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 5986:055d Acer, Inc 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 045e:07fd Microsoft Corp. Nano Transceiver 1.1
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kathleen@kathleen-Lenovo-G50-70:~$ 


```

---

### Post by #&amp;thj^% on 2017-12-20
> **kate.t said:**
> Thanks for the encouragement! :KS


Oh sure...Now I'm going to feel bad if I deliver bad news! :(
> **kate.t said:**
> Thanks for the encouragement! :KS

This computer was purchased from a company that takes Lenovo computers and installs Linux on them and sells them.


Yep I thought so.....I may need to think with that in mind forward then.
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo RTL8723BE PCIe Wireless Network Adapter [17aa:b736]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be
**Bus 002 Device 002: ID 045e:07fd Microsoft Corp. Nano Transceiver 1.1**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kathleen@kathleen-Lenovo-G50-70:~$ 


```

This I know nothing about "Device 002: ID 045e:07fd** Microsoft Corp. Nano Transceiver 1.1**"
Do You?

---

### Post by kate.t on 2017-12-20
Nope. Could it be a microphone?

---

### Post by #&amp;thj^% on 2017-12-20
I asked you first.:p
I did not see anything for your Speakers though.
Can you give me the name and or model of the Bluetooth Speakers.
There is interference though that could/might be fixed switching to 5GHz on your Router. (If Available)

---

### Post by kate.t on 2017-12-20
Sorry it took so long. I had to pore over the speakers, top, sides, back, front, bottom, NO MODEL NO. Looked through all the saved manuals in the filing cabinet, not there.

Finally found it by googling and then searching through the online manuals to find the one identical to mine. It is:

"Innovative Technology ITSB-200 Bluetooth Tower Stereo".

In the meantime, more trouble in River City. I lost my connection to WiFi, so I restarted the computer and got it back (this happens sporadically). When I went to reconnect the speakers, it wouldn't reconnect...it would pair, but not connect...again. Can't remember what to do to get it back.  Aarrgghh.

---

### Post by kate.t on 2017-12-20
Suddenly I'm reconnected. I just kept trying. This is so buggy and so frustrating, but I will NOT give up.

EDIT:  BUT! The sound's not coming out of the tower speakers any more.

---

### Post by #&amp;thj^% on 2017-12-20
Can you use the 5GHz wifi channel?
This has the look and feel of a over crowded NetWork.

---

### Post by jeremy31 on 2017-12-20
1fallen, the wifi card doesn't support 5 GHz, one of the things I looked for in the script results

---

### Post by #&amp;thj^% on 2017-12-20
> **jeremy31 said:**
> 1fallen, the wifi card doesn't support 5 GHz, one of the things I looked for in the script results

Thanks for that jeremy31.
I'm not sure how to offer anything else....just** have **to have a much better connection.
There are ways to get  5 GHz though, USB WiFi Dongle at a $ cost though.

---

### Post by kate.t on 2017-12-20
Jeremy31 and 1fallen,

I just switched to 5 GHz in my Netgear router and my computer was able to connect to WiFi with no problem. I restarted the computer, but now when I try to connect bluetooth to the tower speakers, I get "device added successfully, but failed to connect."

EDIT: I get this msg, too: "Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available"

---

### Post by #&amp;thj^% on 2017-12-20
Sorry I will reword this.
Delete the Device again and re-add it.

---

### Post by kate.t on 2017-12-20
Did that. No dice.

---

### Post by #&amp;thj^% on 2017-12-20
```
pactl load-module module-bluetooth-discover
```

---

### Post by kate.t on 2017-12-20
Result:

```
Failure: Module initialization failed


```

:(

---

### Post by #&amp;thj^% on 2017-12-20
Once more Delete the Device and re-add.
Praying

---

### Post by kate.t on 2017-12-20
Nope. Our prayers have not been heard.

I've been removing and re-finding the speakers over and over again, and a couple of times I once again had the mysterious appearance of ghost bluetooth devices (twice, two different ones, not mine and not the same ones that showed up the other day!!!). They're both gone now.

---

### Post by #&amp;thj^% on 2017-12-20
That's not unusual...just near by devices showing.
I keep forgetting to ask how far away the speakers are, and are they on the same floor/level?

---

### Post by kate.t on 2017-12-20
I spoke too soon. Somebody's prayer was (partially) heard. I ran pulseaudio -D for the heck of it and was then able to connect to the tower speakers. Yay.

However...music still comes out of just the internal speakers.

---

### Post by strixtux on 2017-12-21
Speakers' batteries deceased? Or their BT devices?

---

### Post by #&amp;thj^% on 2017-12-21
> **kate.t said:**
> I spoke too soon. Somebody's prayer was (partially) heard. I ran pulseaudio -D for the heck of it and was then able to connect to the tower speakers. Yay.

However...music still comes out of just the internal speakers.

jeremey31 has pointed out:
The Realtek RTL8723BE is a b/g/n 1x1:1 (one (1) transmit and receive radio chanel).
 

If the Wireless Mode under WiFi properties is set to Auto, this means that card will use the fastest connection possible first, which is** "802.11n".**

In addition, a b/g/n wireless card **will not be able to detect a 5GHz wireless access point as these type of cards can only detect and connect to a 2.4Ghz band.**

kate.t the problem is Bluetooth and 2.4 GHz WiFi share the same radio frequency.
The only way to improve BT performance is to disable Wi-Fi, (You have heard this many times) or use 5GHz.

If you just need to have Bluetooth, look into the cost of either a, USB Wi-Fi 5GHz Adapter and or Another Bluetooth Receiver. **NOTE:**(Very Important to make sure they work with Linux)
I'm just offering other alternatives to help.

---

### Post by kate.t on 2017-12-23
Sorry I disappeared yesterday, work was pressing.

Here's the next question:

If my card cannot work with a 5GHz band, how come it did just that?

I went into the router and changed the setting from 2.4GHz to 5GHz and my computer was just fine online. I was able to post here when I had it set to 5GHz. 2.4GHz was completely turned off.

My roommate's newer-model Lenovo computer, however, could not handle the 5GHz, so we switched to having both running. Additional question: when both 2.4GHz and 5GHz bands are running at the same time, which does my computer pick to use?

Thanks so much in advance for your continued help with this problem. I hope your holiday season is great! :KS

---

### Post by jeremy31 on 2017-12-23
kate.t
Please run the wireless script again and post results

---

### Post by kate.t on 2017-12-23
Thanks Jeremy31!

Here's the link to the wireless script results:

[http://paste.ubuntu.com/26241336/](http://paste.ubuntu.com/26241336/)

I can clearly see the line which indicates:  
WIFI-PROPERTIES.5GHZ:                   no

However, there must be a mistake somehow. Is it possible for a script 
like this to give wrong information? I definitely changed to 5GHz in the
 router and turned off 2.4GHZ. I then had no trouble using the wireless 
network. The proof that the router definitely changed the settings was 
that my roommate suddenly could no longer access the internet. This is 
mysterious, no? 

I also wish you a great holiday season! :KS

---

### Post by jeremy31 on 2017-12-23
I am not sure what happened but your script result shows
```
Frequency:2.417 GHz
```
Nothing in the script results show anything to argue with that you are still connected to 2.4Ghz on 
```
NETGEAR38         <MAC 'NETGEAR38' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
```

---

### Post by kate.t on 2017-12-23
> Nothing in the script results show anything to argue with that you are still connected to 2.4Ghz

We have both 2.4GHz and 6GHz enabled in the router. This answers my question regarding which frequency would be used by my laptop under this scenario. (I had to enable 2.4GHz again or my roommate would not be able to use his computer in the house.)

Nonetheless, during the period when I had 2.4GHz turned off and 5GHz turned on, my computer ran just fine on the wireless network. That's what seems strange to me.

---

### Post by jeremy31 on 2017-12-23
kate.t, it was still using channel 2 on 2.4 GHz
```
wlp2s0    13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.417 GHz (Channel 2)
```
It is possible that another 2.GHz network was within range that you had allowed in Network Manager

---

