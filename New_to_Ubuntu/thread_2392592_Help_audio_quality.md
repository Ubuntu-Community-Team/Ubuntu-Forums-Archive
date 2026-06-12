---
title: "Help audio quality"
date: 2018-05-23
forum: New to Ubuntu
---

### Post by imcooler211 on 2018-05-23
Im really new and my speakers and mic are set to 16bit quality and i have no idea how to change it to 24bit.  Thank you!

---

### Post by mrdc76 on 2018-05-23
You can modify those settings in /etc/pulse/daemon.conf. That's not necessary however, you can't hear the difference between 16 and 24 bit output anyway.

---

### Post by imcooler211 on 2018-05-23
Okay well the quality isnt what it was in windows and my biggest issue is my mic quality.  My voice out put is really high pitched .
any ideas ?

Also the command you gave me was not found even when i used "sudo".

---

### Post by mrdc76 on 2018-05-24
I don't know what might cause your voice to be really high pitched, but changing output from 16 to 24 bits is not going to solve it.

That was not a command but a settings file that can be edited with any text editor.

---

### Post by NM5TF on 2018-05-24
have you tried an equalizer yet ???

I use PulseAudio Equalizer.....try this:

```
sudo add-apt-repository ppa:alex-wv/pulseaudio-equalizer-ppa
```

```
sudo apt-get update
```

```
sudo apt-get install pulseaudio-equalizer
```

it comes with lots of preset configurations...or you can customize it as you wish & save it as default...or change it on the fly...

tommy

---

### Post by imcooler211 on 2018-05-24
> **mrdc76 said:**
> I don't know what might cause your voice to be really high pitched, but changing output from 16 to 24 bits is not going to solve it.

That was not a command but a settings file that can be edited with any text editor.

Okay I figured it wasn't a command after it didn't work so I searched for it and I had no result.  I even scowered my system files to no avail.  


S.O.S. I just want to be able to chat in-game :{



> **NM5TF said:**
> have you tried an equalizer yet ???

I use PulseAudio Equalizer.....try this:

```
sudo add-apt-repository ppa:alex-wv/pulseaudio-equalizer-ppa
```

```
sudo apt-get update
```

```
sudo apt-get install pulseaudio-equalizer
```

it comes with lots of preset configurations...or you can customize it as you wish & save it as default...or change it on the fly...

tommy


Okay so I'm running Ubuntu 18.04 LTS and those updates were for older os' apparently.  Anyways, I installed the equalizer.  However, I have no idea how to open it.  Please help.  I'm extremely new to this.

---

### Post by NM5TF on 2018-05-24
have you looked in the menu for something like "multimedia" or "sound" in the applications section....

since I don't have Ubuntu on this box, I don't know what it's called...but you should find something similar...

or....open a terminal & type

```
pulseaudio-equalizer-gtk
```

tommy

---

### Post by imcooler211 on 2018-05-25
> **NM5TF said:**
> have you looked in the menu for something like "multimedia" or "sound" in the applications section....

since I don't have Ubuntu on this box, I don't know what it's called...but you should find something similar...

or....open a terminal & type

```
pulseaudio-equalizer-gtk
```

tommy

alexander@alexander-desktop:~$ pulseaudio-equalizer-gtk
pulseaudio-equalizer-gtk: command not found


This is what it came up with.

So I got this far finally!

default-sample-format = s16le
; default-sample-format = s24le
; alternate-sample-rate = 192000
; default-sample-channels = 2
; default-channel-map = front-left,front-right

 Nothing has changed though.  My voice is still distorted.  I also can't get the first "default-sample-format" line to save as s24le.  
In windows my headset works fine.  Initially it'll start at 48khz and my voice will be distored like it is in linux.  However,  once I change it to 192khz, my voice becomse undistorted.  
Anyways to the point,  I figured if I could get this changed in linux it'd make my mic clear again. 

Any ideas?  


Thank you for your time and helps guys!  I am really enjoying Linux, but this is really disheartening :(

---

### Post by #&amp;thj^% on 2018-05-25
> **imcooler211 said:**
>  Anyways, I installed the equalizer.  However, I have no idea how to open it.  Please help.  I'm extremely new to this.
To open the EQ gui:
```
qpaeq

```
If you have not already set this up you also need to add this to "/etc/pulse/default.pa"
```
load-module module-equalizer-sink
load-module module-dbus-protocol

```
I use nano to do that via:
```
sudo nano /etc/pulse/default.pa

```
You can just add the lines I mention at the bottom, save and close. 
Then just run:
```
pulseaudio -k & pulseaudio -d
```
now it will show you the interface to edit and save as a preset.

---

### Post by speartip on 2018-05-25
Just to step back a bit, at install did you install all the necessary codecs?
If not then:
```
sudo apt install ubuntu-restricted-extras
```
See if that helps.

---

### Post by imcooler211 on 2018-05-25
> **1fallen said:**
> To open the EQ gui:
```
qpaeq

```
If you have not already set this up you also need to add this to "/etc/pulse/default.pa"
```
load-module module-equalizer-sink
load-module module-dbus-protocol

```
I use nano to do that via:
```
sudo nano /etc/pulse/default.pa

```
You can just add the lines I mention at the bottom, save and close. 
Then just run:
```
pulseaudio -k & pulseaudio -d
```
now it will show you the interface to edit and save as a preset.


So after I edited the pa file I just used ctrl+x to save it.  So I added the lines at the bottom and saved.  I don't know if that's what you meant.  After I did as you said and ran pulseaudio -k etc. Then I tried running qpaeq and this is what I received. 

$ qpaeq
Gtk-[COLOR=#8AE234]**Message**[/COLOR]: [COLOR=#3465A4]14:20:59.813[/COLOR]: Failed to load module "canberra-gtk-module"
There was an error connecting to pulseaudio, please make sure you have the pulseaudio dbus module loaded, exiting...

> **speartip said:**
> Just to step back a bit, at install did you install all the necessary codecs?
If not then:
```
sudo apt install ubuntu-restricted-extras
```
See if that helps.


So I did this.  It downloaded and installed then a window popped up, like a terms of service type window, and at the bottom was an "ok".  However, it wouldn't let me click "ok" or press enter on it/select it.  So I ended up closing the window with the "x" at the top right.  I tried the code again to make sure it worked and this is what I received:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by #&amp;thj^% on 2018-05-25
> **imcooler211 said:**
> 
$ qpaeq
Gtk-[COLOR=#8AE234]**Message**[/COLOR]: [COLOR=#3465A4]14:20:59.813[/COLOR]: Failed to load module "canberra-gtk-module"
There was an error connecting to pulseaudio, please make sure you have the pulseaudio dbus module loaded, exiting...
it did not save then, please show me the output of:
```
gedit /etc/pulse/default.pa
```

---

### Post by imcooler211 on 2018-05-25
```
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
load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

### Make some devices default
#set-default-sink output
#set-default-source input
```

---

### Post by kazakore on 2018-05-26
> **imcooler211 said:**
> So I did this.  It downloaded and installed then a window popped up, like a terms of service type window, and at the bottom was an "ok".  However, it wouldn't let me click "ok" or press enter on it/select it.  So I ended up closing the window with the "x" at the top right.  I tried the code again to make sure it worked and this is what I received:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


This implies another program is using it. Have you got a GUI software installer open such as the Software Centre or Synaptic? You need to close it before you can run those commands from the commandline (or search for them and install through the GUI.)


Also what makes you think the hardware you are trying to use even supports 24bit audio? And why do you think that will help with the issue as described? Sounds to me you are chasing a phantom.....

---

### Post by NM5TF on 2018-05-26
I agree with @kazakore about the hardware 24bit support.....do we even know what hardware/driver he is using ???

@imcooler211.....could you post the result of

```
inxi -A
```

you will most likely have to install inxi 1st.....

```
sudo apt-get install inxi
```

we can go from there to see what your hardware supports...

tommy

---

### Post by imcooler211 on 2018-05-27
Okay so I claim to support 24 bit because when in windows I have the same problem with my mic.  My voice comes in distorted (i.e. too high).
So I just change the quality to 24 bit 192khz and it fixes the problem which is why I think it'd fix it in linux too, but I could be completely wrong since, as you can see, I'm a real amateur.

Anyways after running " sudo apt-get install inxi"  I got another "END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE ".   And again I cannot click the okay button my only option is to close it which kills the terminal.  So I don't know what to do.

> **NM5TF said:**
> I agree with @kazakore about the hardware 24bit support.....do we even know what hardware/driver he is using ???

@imcooler211.....could you post the result of

```
inxi -A
```

you will most likely have to install inxi 1st.....

```
sudo apt-get install inxi
```

we can go from there to see what your hardware supports...

tommy


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Also, this is what i recieved after running "inxi" code:

So I keep getting the line "Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?".  So I decided to hunt the folder down and find it's properties.  At the bottom it says "You are not the owner, so you cannot change these permissions."  Anyways I'm like wtf cuz I'm the only account on my system and I set it up as an admin or at least I assumed I did.  Could this possibly be a cause as to why none of the codes I'm being given are working?

---

### Post by imcooler211 on 2018-05-27
Okay so I borrowed a usb headset and it all works fine.  I'm starting to think the headset is just a pos.

---

### Post by NM5TF on 2018-05-27
did you ever try using speakers to see if the "problem" was system-wide ???

might have saved some time & frustation....just sayin'

---

### Post by yannickhk on 2018-05-30
> **imcooler211 said:**
> 
Anyways after running " sudo apt-get install inxi"  I got another "END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE ".   And again I cannot click the okay button my only option is to close it which kills the terminal.  So I don't know what to do.


When the license agreement pops up in terminal, TAB until ok is selected, ENTER. I had the same issue. I am a n00b too :P

---

