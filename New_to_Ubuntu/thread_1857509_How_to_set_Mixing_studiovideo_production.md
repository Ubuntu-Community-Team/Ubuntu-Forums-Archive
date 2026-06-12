---
title: "How to set Mixing studio/video production"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by Stanley2011 on 2011-10-10
Hi, I a big time Beginner to Ubuntu. How to set up the on a budget mixing/video production studio on Ubuntu 11.04 or Ubuntu studio 11.04? I have been using windows for years and Ubuntu is Greek to me. What are the best setting, software, and hardware on a budget for the job? Record live sound, Video ext.

---

### Post by duke.tim on 2011-10-10
Try using ubuntu studio
[http://ubuntustudio.org/](http://ubuntustudio.org/)

Audacity audio editing
Jokosher - really nice layout for recording
Rosegarden for midi + studio work


You could also try using 
Ardour which I've heard good things about...but haven't tried since
my system is 64bit and unsupported.

---

### Post by Stanley2011 on 2011-10-10
I have tried both Ubuntu 11.04 some how lost the sound, Ubuntu studio 11.04 is what I have installed now but having a hard time getting thing to work.

---

### Post by duke.tim on 2011-10-10
You are probably having problems with jack. (compared to pulse-audio)

Try reading through some of these and see if they help

[http://www.youtube.com/watch?v=fMz6fDGBnA4](http://www.youtube.com/watch?v=fMz6fDGBnA4)

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)


*This guy has some good tutorials
[http://www.youtube.com/user/jkymarsh#p/u](http://www.youtube.com/user/jkymarsh#p/u)

---

### Post by Stanley2011 on 2011-10-10
**Ok. Just open Qjack.ctl and it gave me the error messages...**and lost sound......
[B]Now would it be better to reinstall Ubuntu Studio 11.04 and pick a different setting? 
Have no clue what I'm doing...........[/B]


 p, li { white-space: pre-wrap; }  [COLOR=#999999]17:23:29.998 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:23:30.014 Statistics reset.[/COLOR]
 [COLOR=#cccc99]17:23:30.058 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]17:23:30.070 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]17:23:45.953 JACK is starting...[/COLOR]
 [COLOR=#990099]17:23:45.953 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]17:23:45.975 JACK was started with PID=1739.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfbcf4000 irq 16
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#ff0000]17:23:53.086 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Driver is not running
 Cannot create new client
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.
 [COLOR=#999999]17:23:53.265 JACK was stopped successfully.[/COLOR]
 [COLOR=#cc3366]17:23:53.266 JACK has crashed.[/COLOR]

---

### Post by duke.tim on 2011-10-10
Have you ever had sound working on your system?
Try unticking Realtime and see if that fixes your problem
[http://ubuntuforums.org/showthread.php?t=1544395](http://ubuntuforums.org/showthread.php?t=1544395)
-----------------------------------------------
The settings/configuration you use depends on what you want to do. If you need realtime recording and playback, you should use jack. This doesn't mean you are limited to jack.

The big advantages that I see with jack is that
*Low latency audio processing
*Piping audio streams from one program(server) to another (client)

The advantage of using Pulse IMO is
*Easy setup (if it works)
-----------------------------------------------
Does pulse audio work? If you don't need Jack (or Ardour I believe) then try using pulse.
-----------------------------------------------
```
aplay -L
``` will show you among other things which 
sound server you are using. If you are trying to use jack and 
pulse at the same time you will need to stop the pulseaudio sound
server.

Since pulse audio has the tendency to spawn after being killed, start jack before killing it
```
sudo killall pulseaudio
```

You can also download pulseaudio manager, and click disconnect.
-----------------------------------------------
Insure that Interface, Output Device, Output Channels is correct.
Default worked for me, but if you need you can define where the audio is routed.

```
aplay -l
```
the above command will list your sound devices
The sound card 0 would be hw:0
The device 1 on sound card 0 would be hw:0,1

My settings are shown below if it is any help.

[IMG]https://fbcdn-sphotos-a.akamaihd.net/hphotos-ak-ash4/315504_2559852119391_1346678943_3098185_2140005781_n.jpg[/IMG]

Take a look at this
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by Stanley2011 on 2011-10-10
**I got this **
Package configuration TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE   




[B]
 when I run this [/B]
sudo apt-get install ardour audacious hydrogen 
jackd jack-rack qjackctl seq24 vkeybd zynaddsubfx 
patchage vlc kino pitivi acidrip ubuntu-restricted-extras 
ubuntustudio-menu gcdmaster

Now it want let me do anything. Man this is so much fun 4 days and stall have not got this up and running.

---

### Post by Stanley2011 on 2011-10-10
Yes I have sound on this  system. the first link [http://ubuntuforums.org/showthread.php?t=1544395](http://ubuntuforums.org/showthread.php?t=1544395)[COLOR=Black] AutoStatic said [/COLOR][ add your account to the audio group ]("http://ubuntuforums.org/member.php?u=746131")
So way would I need to add to the audio group?

---

### Post by duke.tim on 2011-10-10
I'm not sure if I understood your question. i'll try to answer anyway

groups are part of the linux security model, adding yourself to the audio group would allow you access to what the audio group has access, which in this case would be audio related components.

To add your account to the audio group 
System -> Users and Groups -> Manage groups ->audio -> Check the box by username

---

### Post by Stanley2011 on 2011-10-10
> **duke.tim said:**
> I'm not sure if I understood your question. i'll try to answer anyway

groups are part of the linux security model, adding yourself to the audio group would allow you access to what the audio group has access, which in this case would be audio related components.

To add your account to the audio group 
System -> Users and Groups -> Manage groups ->audio -> Check the box by username


I guess my question would be. There are no groups on my computer, no one but me why would I need to be added to the auto group? I not understand. And now my system what play youtube video.
Just what to know how long dose it take to set up a stable system?
What is the worst thing to happen to my system if I keep tinkering around in it? 
Don't what to fry anything.

---

### Post by duke.tim on 2011-10-10
You are the only user yes, But there will also be groups on your system.

[IMG]https://fbcdn-sphotos-a.akamaihd.net/hphotos-ak-ash4/313615_2560411853384_1346678943_3098611_1986033709_n.jpg[/IMG]

It might be a good idea, to reinstall and start with a simpler setup in ubuntu. Try using a regular install of ubuntu and learn about the system a little, It will help a lot when setting up jack! :)

---

### Post by Stanley2011 on 2011-10-11
I have followed the youtube video of how to set up groups by [jkymarsh]("http://www.youtube.com/user/jkymarsh") when I get to the the *audio.conf page the last page of the setup it was blake. you said may need to reinstall *and start with a simpler setup in ubuntu? which setup?I have done 3 install now Ubuntu 11.04 and UbuntuStudio 11.04 twice. No luck evey time something new go wrong. It would be nice to download from Ubuntu Software Center and it work fine. And now I will have to reinstall just so I can watch video.

---

### Post by Stanley2011 on 2011-10-11
OK, real witch Ubuntu to install? Ubuntu or Ubuntu Studio? If I install Ubuntu Studio witch to install. At the end of set up it ask you to choose? I thank they are 5 to choose from? I want to record live sound like garage band. all so like to editing Video I thank I will be using Kdenlive for that, and live stream a show to the internet. I would like to set up a small home studio. Now all so can I use one Computer for that are do I need 3 computers? and I need to be able to watch videos on the internet to. Day 5 and 4th install 2 Ubuntu 11.04 and 2 Ubuntu Studio 11.04 one 3D something and one Sound soething. I realy need to get this up and run. I hate to work on some video editing and lose it all.

---

### Post by duke.tim on 2011-10-12
I'd suggest ubuntu 11.04 . Install kdenlive, audacity, rosegarden. For streaming you will have to ask somebody else since i've never had a need to set that up.

---

