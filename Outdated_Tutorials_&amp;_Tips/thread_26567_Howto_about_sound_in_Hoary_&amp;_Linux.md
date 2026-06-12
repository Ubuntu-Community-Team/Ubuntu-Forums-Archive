---
title: "Howto: about sound in Hoary &amp; Linux"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by dusu on 2005-04-13
_**[SIZE=3][COLOR=Sienna]Foreword[/COLOR][/SIZE]**_

The following howto has been posted by *ploum* on the French Ubuntu forums.

I have been answering sound questions "many" times on the Ubuntu forum, after having myself asked why sound did not work any more after upgrading from Warty to Hoary.
I have found this howto interesting, and thought it might also be interesting for everyone here, that's why I translated and adapted it. Please forgive any translation that sounds "Frenchy" ! This howto is partly redundant with other threads related to sound issues, such as for example [http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882).
However, it is original in the sense that it also describes sound features in Linux in general.

_**[SIZE=3][COLOR=Sienna]Introduction[/COLOR][/SIZE]**_

Many questions are related to sound. In many cases, there is no hardware problem, but simply a lack of understanding how the system works.
Here are some technical explanations. It's a bit complicated, so if you really do not get the point, please go straight to the next topic.

_**[SIZE=3][COLOR=Sienna]Technical Explanations[/COLOR][/SIZE]**_

**[COLOR=DarkRed]OSS: Open Sound System[/COLOR]**
The Linux kernel is sending the sound to the sound card, by using the appropriate sound driver. A long time ago, the system which allowed to do that was OSS. Many drivers have been developed for OSS. Applications thus use the OSS interface to send sound to the driver.

**[COLOR=DarkRed]ALSA: Advanced Linux Sound Architecture[/COLOR]**
OSS is not technically perfect, so a better system has been developed, namely ALSA. As a consequence, programs making use of sound have to be rewritten in order to be able to use ALSA instead of OSS. That's why, for example, xmms has an OSS plugin and an ALSA plugin. (The output plugin can be chosen in xmms, in options -> preferences).
Nevertheless, for older applications to go on working, a compatibility layer exists in ALSA. It ensures OSS applications believe they do use OSS while they actually use ALSA (as for example the flash plugin).

**[COLOR=DarkRed]ESD: Enlightened Sound Daemon[/COLOR]**
In theory, only one sound can be played, since there is only one loud speaker. In order to play many sounds, one uses a sound mixer. That's the role of ESD. Applications send their sounds to ESD, the latter mixes these sounds, sends the result to OSS, which transmits it to ALSA.

_**[SIZE=3][COLOR=Sienna]In case you have a problem, read this before you post on the forum[/COLOR][/SIZE]**_

One must be aware that only one application can use the sound card. In the default configuration, ESD (which is itself an application) is launched on startup and has access to the sound card.
In most cases, you cannot get sound simply because ESD blocks the access to the sound card.

The first thing to do is thus to kill ESD (use the command: killall esd), and then to have a look at what applications use the sound card:
```
lsof /dev/dsp
```   tells you which programs use OSS
```
lsof /dev/snd/* 
```tells you which program use ALSA

Before you post, please check that all this is empty, and tell it in your post.

_**[SIZE=3][COLOR=Sienna]Howto properly configure the sound[/COLOR][/SIZE]**_

A good thing to do is to tell ESD not to run when one does not need it. Do (assuming gedit is your prefered editor): 
```
sudo gedit /etc/esound/esd.conf
```
and edit it so that it looks like
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```
Restart your session, and normally you should not have problems with games such as frozen-bubble. You just have to stop the music two seconds before you start the game.

_**[SIZE=3][COLOR=Sienna]You still have some problems ![/COLOR][/SIZE]**_

Please follow these steps:

 1) Check your loud speakers, if they are properly plugged in, etc...

 2) Check the sound volume ! In alsamixer, MASTER, PCM must be at some high value value, and without MM above or under.

 3) If the music seems to play properly but you hear nothing, check the above two points. If Linux does not detect the sound card, it NEVER plays any sound ! and LWAYS gives an error ! Check that your computer does not have two sound cards, and plug your loud speakers on the other one (using a particular sound card is another problem).

 4) If you get an error message of the type: "Not found or busy", check with "lsof" (see above)

 5) In any other desperate situation, post on the forum and give:
  - the precise error type
  - the precise model of your sound card
  - the result of "lsmod|grep snd"
 
_**[SIZE=3][COLOR=Sienna]Howto go further: listening many sounds at the same time, without ESD ![/COLOR][/SIZE]**_

Now it becomes more technical and so also facultative. But it can be of interest for more than one person.
!!! *[COLOR=Red]BE CAREFUL[/COLOR]* !!! You should try the following only if you already managed to get proper ALSA sound (for example xmms manages to play with the ALSA plugin).
It is not clear that the following will work for any sound card.

The first thing to be done is to tell ESD to use ALSA instead of OSS:

```

sudo apt-get install libesd-alsa0

```

One now creates the asound file:
```

sudo gedit /etc/asound.conf

```
which should look like
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}

```

Then one restarts ALSA:
```

sudo /etc/init.d/alsa restart

```

Restart your session (that's for ESD), and there you are, you should in principle be able to hear all the "click click" of the interface, to listen to music with xmms, and to play a video with totem, everything at the same time (applications must use ESD or ALSA, ALSA being a better choice).

*[COLOR=DarkRed]The only dark point[/COLOR]*: OSS applications can still only have access to the sound card one after the other, which is the case of the flash plugin. Thus it is necessary to switch off all sound *before* launching a flash animation. Sometimes one even has to restart the navigator.

*[COLOR=DarkRed]If someone knows a trick to make flash use ALSA or ESD, please tell us ![/COLOR]* About this, you can go and see the post by wrochal in this thread

*[COLOR=DarkRed]For people having two sound cards[/COLOR]*: You should have a look at the posts by MonoLT in this thread, and at his thread called 'HOWTO Set sound if you have 2 soundcards', [http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

---

### Post by ChamPro on 2005-04-13
Thanks for the guide. I now have delay free video and audio. (With the default Ubuntu sound settings I was getting a couple second delay with all sounds.)

Although not a desperate situation, a few other problems present themselves after taking the steps you described.

[list]
[*]Some games still have no sound (an example would be Frozen Bubble)
[*]The volume applet (as well as the multimedia keyboard buttons) no longer work to control the sound volume. Is there a way to change these so they control the ALSA mixer main volume?
[/list]

Thanks for the help ;-)

By the way, my sound card is unknown in my Dell Inspiron 8600 laptop, but I assume it's built in to the Intel 82801 motherboard.

Here is the lsmod|grep snd output.```
snd_intel8x0           32352  0
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm

```

---

### Post by ploum on 2005-04-13
[QUOTE=ChamPro]
[list]
[*]Some games still have no sound (an example would be Frozen Bubble)
[/quote]
Those games use OSS. I don't know why, but it seems that you don't have OSS.

[QUOTE=ChamPro]
[*]The volume applet (as well as the multimedia keyboard buttons) no longer work to control the sound volume. Is there a way to change these so they control the ALSA mixer main volume?
[/list]
[/quote]
Right Click > Preferences  on the volume applet.

Select the ALSA mixer in the dropdown menu.

---

### Post by nehalem on 2005-04-13
Great guide!

I've always wondered about all the differences but mostly got the gist of it, this helps clear things up finally.  

How long has it been the main sound system (I'm thinking it was new in 2.6?)?  What are the advantages?  Why do things like Doom 3 still use OSS if ALSA is so much better?  Why doesn't Hoary use ALSA (probably same reason)?  

Sorry so many questions but I've honestly never fully understood sound on Linux.

---

### Post by wrochal on 2005-04-14
Dear,

Solution for Sound in Flash, create link

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Bye, \\:D/

---

### Post by ploum on 2005-04-14
[QUOTE=wrochal]Dear,

Solution for Sound in Flash, create link

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Bye, \\:D/[/QUOTE]
 Doesn't work for me :-(

Could you explain a bit more why it would work ?

---

### Post by artinla on 2005-04-14
Worked for me..  I now have sound in Flash!

Thanks,

Art

---

### Post by MonoLT on 2005-04-14
It could sound strange but my problem was no sound with Rhythmbox and Xine only. Totem and XMMS (with ALSA plugin) could play sound. No system sounds and GAIM too. I thought this guide could help me return sound (my fav player is Rhythmbox not XMMS) but actually nothing works now only XMMS (ALSA).

I have 2 sound cards. Volume control uses the right one (Ensoniq AudioPCI). (look attached picture) But when I type "alsamixer" command I see that default is another one (SiS SI7012) (look attached picture). Does anyone know how to fix this? Maybe this could solve many other users' problems?

---

### Post by dusu on 2005-04-15
Hi MonoLT,

did you try *alsamixer -c1* to have access to the other sound card ? (By default alsamixer performs -c0)
Don't know if this helps...

---

### Post by MonoLT on 2005-04-15
Thank you dusu.

That helped me to understand my problem a bit more. With "alsamixer -c1" I see that  my card is Ensoniq "AudioPCI" (just what I need) but chip is set to "SigmaTel" (that's ethernet card if I'm not mistaken). So maybe you know how to associate my card (Ensoniq) with needed chip? Or I'm doing something wrong.

---

### Post by dusu on 2005-04-15
Hi MonoLT,

the only advice I can give is to read the man page for alsamixer... I'm really not an expert about this. But it seems the -D option can be useful also (?).
Good luck !

---

### Post by MonoLT on 2005-04-15
Guys! Thanks a lot!!! You helped me to solve the problem in a way. I've just changed some parameters in config file to me it all work!

So I decided to write HOWTO based on this one:
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)


P.S.
Problem was in dmixer default device

P.P.S.
Thanks again

---

### Post by dusu on 2005-04-15
You're welcome MonoLT !
I'm really happy that you managed to get things to work ! :D 
And thanks also for producing your howto. I'll edit my howto and put a link to yours !

P.S. This Ubuntu community spirit is really cool. 8)

---

### Post by ChamPro on 2005-04-15
[QUOTE=ploum]Those games use OSS. I don't know why, but it seems that you don't have OSS.


Right Click > Preferences  on the volume applet.

Select the ALSA mixer in the dropdown menu.[/QUOTE]
I can work on getting OSS working, but my more pressing dilemma is with the volume applet. The applet is loaded in one of my bars (there's actually two applets loaded). However, I can't even see the applet. I know they are both there because I checked in gConf. But how do you delete an applet or manually change it's settings so I can either see it and / or get it working correctly by associating it with ALSA?

I apologize if this goes outside the scope of this thread.

---

### Post by MonoLT on 2005-04-15
ChamPro
I can't really understand what you mean so I provide 3 options...hope that at least one will help.


**[SIZE=3][COLOR=DarkSlateBlue]Solution N1[/COLOR][/SIZE]**
Volume applet allows you to change alsamixer parametres using GUI. So you can always run this command in terminal:

```
alsamixer
``` 
or this (if you have 2 soundcards):
```
alsamixer -c1
``` 


**[SIZE=3][COLOR=DarkSlateBlue]Solution N2[/COLOR][/SIZE]**
1. Applications --> Sound & Video --> Volume Control

2. Click File menu --> Change Device --> (choose device)

Volume Applet should use this device by default




**[SIZE=3][COLOR=DarkSlateBlue]Solution N3[/COLOR][/SIZE]**
System --> Preferences --> Multimedia Systems Selector

Set ALSA there (Test will most probably fail but you stil be able to hear the sound thru applications)


Hope that this could help you. Good luck!

---

### Post by DoubleDangerClub on 2005-04-15
Hi Dusu,

I was wondering if you know what could cause my laptop to play sound only in the left speaker, but as soon as you move the volume at all, it plays through both?  Seems to me like something wakes up and starts doing what it should.  Anyhow, any help would be appreciated.  Thanks!

DDC

---

### Post by ChamPro on 2005-04-18
[QUOTE=MonoLT]ChamPro, I can't really understand what you mean so I provide 3 options...hope that at least one will help.


**[SIZE=3][COLOR=DarkSlateBlue]Solution N1[/COLOR][/SIZE]**
Volume applet allows you to change alsamixer parametres using GUI. So you can always run this command in terminal:

```
alsamixer
``` 
or this (if you have 2 soundcards):
```
alsamixer -c1
```[/QUOTE]This might be my only working solution.> **[SIZE=3][COLOR=DarkSlateBlue]Solution N2[/COLOR][/SIZE]**
1. Applications --> Sound & Video --> Volume Control

2. Click File menu --> Change Device --> (choose device)

Volume Applet should use this device by defaultThis gives me a nice error. "No volume control elements and/or devices found."> **[SIZE=3][COLOR=DarkSlateBlue]Solution N3[/COLOR][/SIZE]**
System --> Preferences --> Multimedia Systems Selector

Set ALSA there (Test will most probably fail but you stil be able to hear the sound thru applications)For some odd reason, neither ALSA nor ESD show up in this box anymore. It's only Custom and Silence and neither one has a working test sound. Looks like I'm stuck with using the ALSA mixer.

The whole "I can't remove the applet in my bar thing" I figured out. Just delete the bar.... However, I still can't get a working volume applet. It will probably work just fine as soon as I can get the volume control to work.

---

### Post by jmather on 2005-04-19
Ok, so I have the same error as mentioned above...being the tinkering person that Iam....I had sound working fine....except for in a few scenarios...dvd playback was choppy and no real audio...could get it to start, but no sound...

Anyways...now I changed some setting in my volume control applet and upon reboot....when I try to access the volume control applet I get:

"No volume control elements and/or devices found."

I think I changed something from OSS to intel or alsa...I cant remember....but I cant seem to fix it....anyone have any suggestions?

---

### Post by copperfish on 2005-04-19
Thanks guys.  Worked for me!

---

### Post by jiyuu0 on 2005-04-19
added to ubuntuguide.org
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by coldturkey on 2005-04-19
Great! Thanks for the howto, worked great for me.
Btw, is there a fix for the annoying sync problem with movies and sound?

---

### Post by locque on 2005-04-19
I am still having problems getting my sound to work. I have tried everything listed in every post I have found regarding no sound. I have tried both the internal speakers as well as externals. I have reconfigured ALSA... you name it... I tried XMMS with all available plugins. It plays and shows the EQ bar going crazy like it is playing, but nothing comes out of the speakers...

Here is the output os lsmod | grep snd:
snd_intel8x0           29984  0
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

Any help would be great!!

BTW: This is on a Gateway 4520GZ laptop

---

### Post by _osorio_ on 2005-04-23
scuse me, my english is very bad ;) . my problem is ubuntu not detect my sound card, what command i need for detect my sound card?

thank you

_osorio_

---

### Post by josuealcalde on 2005-04-23
Are you sure Ubuntu hasn't detected you Sound Card? or simply you cant' hear sound?

Sometimes, sound can be corrected going to System->Preferences -> Multimedia System Selector. I have traduced it form "Sistema->Preferencias->Selector de Sistemas Multimedia in Spain) so it could be some different depends on your languaje.

---

### Post by ChamPro on 2005-04-23
I went back and rechecked all my settings against Ubuntu Guide and the related sound forum post. Although all sound works fine, Gnome won't recognize it at all. Sound plays, but the Multimedia Systems Selector has no options, Volume Control gives the error "No volume control elements and/or devices found.", and the related applet doesn't even show up.

My previous posts include my lsmod|grep snd.

I guess I'm ok with using alsamixer for the rest of the time, but there has to be a simple reason why Gnome won't see my drivers and then I can use the multimedia keyboard keys again.

---

### Post by Kakalto on 2005-04-27
First off, Thanks for the guide. It made me think that I could get my sound working.... Sadly, it didn't, but atleast I have a specific place to get help from.

[useless information I deleted]

I found why it isn't working - some XFCE setting screwed up. after logging into KDE to see if it did sound properly, which it did, then I logged into XFCE again, and sound worked in XFCE. Strange.

---

### Post by nickless on 2005-05-02
damn I startet today and nothing was wrong. I simply watched one Aqua Teen Hunger Force episode and about in the middle of the .ogm file my sound broke. Very scratchy now ... what the %&$ happened? :/

edit: Works now... didn`t do anything... stange

---

### Post by DarkGreen16 on 2005-05-03
edit: figured it out

---

### Post by alainhenry on 2005-05-04
[QUOTE=dusu]_**[SIZE=3][COLOR=Sienna]Foreword[/COLOR][/SIZE]**_

The following howto has been posted by *ploum* on the French Ubuntu forums.
[/QUOTE]

I did not find any reference to a French Ubuntu Forum on this web site or on the main UbuntuLinux site.  Could you point me to the right url?  

Thanks

Alain

---

### Post by dukeinlondon on 2005-05-06
Alsa also comes with Oss emulation. That's how OSS based apps are catered for in other distros. But it seems that ubuntu doesn't include it, at least for the sound blaster driver emu10k1 in my case. 

I am wrong about this ?

---

### Post by ChamPro on 2005-05-06
I finally gave in and just reinstalled Hoary. Following the similar steps outlines in the UbuntuGuide, I now have working sound.

I did notice something though. Pausing music in XMMS or BMP works, but once you try to unpause, nothing happens. You are forced to start the song from the beginning. Even with killing ESD. I checked the pause function in RhythmBox and it works fine there.

[QUOTE=ChamPro]I went back and rechecked all my settings against Ubuntu Guide and the related sound forum post. Although all sound works fine, Gnome won't recognize it at all. Sound plays, but the Multimedia Systems Selector has no options, Volume Control gives the error "No volume control elements and/or devices found.", and the related applet doesn't even show up.

My previous posts include my lsmod|grep snd.

I guess I'm ok with using alsamixer for the rest of the time, but there has to be a simple reason why Gnome won't see my drivers and then I can use the multimedia keyboard keys again.[/QUOTE]

---

### Post by dongdongdog on 2005-05-07
For those laptop computers that use Intel AC'97 sound card, you need to mute the external amplifier to get the sound. Do these,

1. alsamixer
2. Use the right arrow key to move the far right of the display.
3. Highlight External Amplifier
4. Press m. There is an "MM" shown on the volume bar. 

In most cases, you should get the sound because Ubuntu is able to set up  this very common sound card.


[QUOTE=locque]I am still having problems getting my sound to work. I have tried everything listed in every post I have found regarding no sound. I have tried both the internal speakers as well as externals. I have reconfigured ALSA... you name it... I tried XMMS with all available plugins. It plays and shows the EQ bar going crazy like it is playing, but nothing comes out of the speakers...

Here is the output os lsmod | grep snd:
snd_intel8x0           29984  0
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

Any help would be great!!

BTW: This is on a Gateway 4520GZ laptop[/QUOTE]

---

### Post by ChamPro on 2005-05-10
Whee! I finally fixed my sound. I undid the things I did suggested in this thread and the UbuntuGuide. Then I tried them seperately one by one. I found that changing the /etc/esound/esd.conf as suggested and installing the libesd-alsa0 but NOT using the suggested /etc/asound.conf worked. I just deleted the asound.conf and my sound delay was gone. Pause in Beep and XMMS work fine now as well.

I suppose it was an ALSA setting that my sound card didn't like that did me in. However, it works now.... off to fix my Intel 2200B/G card now.

[QUOTE=ChamPro]I finally gave in and just reinstalled Hoary. Following the similar steps outlines in the UbuntuGuide, I now have working sound.

I did notice something though. Pausing music in XMMS or BMP works, but once you try to unpause, nothing happens. You are forced to start the song from the beginning. Even with killing ESD. I checked the pause function in RhythmBox and it works fine there.[/QUOTE]

---

### Post by girlfreddy on 2005-05-21
Ok. I did almost all that you said here, (except the expert stuff at the end) and I still have no sound at all through Ubuntu. What's up now?
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
 ](*,) 
I've been doing this for a month trying to figure it out. RT#M isn't working.

---

### Post by vishnukv on 2005-05-22
I have a strange problem with sound on my Hoary. I installed alsa sound drivers for my sound card. The sound card on my laptop is Cirrus logic Crystal clear sound fusion audio accelaerator. Before I tinkered with sound and alsa, everything was fine, a nice sound used to come when system booted in Ubuntu. Now no sound comes when I boot and added to it sound is played in only XMMS and Realplayer. Totem and MusicPlayer play files but there is no sound output. I have done all the things suggested on this page. Can somebody explain to me why this is happening and what is the remedy to this.
Thanks in advance.

---

### Post by krinor1966 on 2005-05-24
I've been ttrying to get sound on my Ubuntu by following this thread but when I reach

sudo /etc/init.d/alsa restart

Ubuntu reaks out and beeps multiple times with the following "lyrics"

sudo /etc/init.d/alsa restart

krister@ubuntu:~$ sudo /etc/init.d/alsa restart
 * Shutting down ALSA...
 * /etc/init.d/alsa: Warning: 'alsactl store' failed with error message 'alsactl : save_state:1194: No soundcards found...'.
Invalid card number.
Usage: amixer <options> command
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
Available commands:
  scontrols       show all mixer simple controls
  scontents       show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> command


Something is wrong and I can't figure out what ...

krister@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:02:01.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:07.0 Ethernet controller: Digital Equipment Corporation DECchip 21041 [Tulip Pass 3] (rev 21)
0000:02:09.0 Serial controller: Timedia Technology Co Ltd PCI2S550 (Dual 16550 UART) (rev 01)

lsmod

snd_intel8x0           29984  0
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

Rgds,

Krister

---

### Post by mv@acea.be on 2005-05-28
[QUOTE=wrochal]Dear,

Solution for Sound in Flash, create link

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Bye, \\:D/[/QUOTE]
 Dear,

Thx for this hint. It worked! But... can you explain why this does the trick?

Marc

---

### Post by rama on 2005-05-29
I 've got a 4.1 speaker set and I only get sound (using XMMS) from 2 speakers.Could you tell me how to set up Hoary so that I can switch from 2 speakers (or headphones) to 4 speakers and back? Is there some sort of a setup dialog for that?

---

### Post by Philipude on 2005-05-30
[SIZE=4]**Sound export via Lame is too fast.  :^o ** A kind of happyending workaround in the below  :???: [/SIZE]

It cannot be true that Lame do not function on modern PCs? Earlier I googled & found that you may get Lame functioning through a reverse overclocking so just a 900 mhz PC appeared as an 800 mhz PC so what about a 3+Ghz PC?

I have Googled and found no alternative to Lame exept below and no way to make just Lame function slower, but more reliable. The sound is galloping.

This well-renoumet- project seams basic in most Hoary decoding , and I like to save mp3 format eks from Kino to Audacity for editing..
I do run Alsa:
aplay -D plug:dmix /home/phili/test.wav
which run fine but not in audacity - Errormesseges:

[SIZE=2]To control ALSA I have tried:

 lsof /dev/dsp/*
 lsof: status error on /dev/dsp/*: Not a directory

 phili@:~$ lsmod|grep snd
 snd_ens1370            18528  4
 snd_rawmidi            24480  1 snd_ens1370
 snd_seq_device          8460  1 snd_rawmidi
 snd_pcm_oss            52132  0
 snd_mixer_oss          19680  2 snd_pcm_oss
 snd_pcm                94696  3 snd_ens1370,snd_pcm_oss
 snd_timer              25060  2 snd_pcm
 snd_page_alloc          9732  2 snd_ens1370,snd_pcm
 gameport                4448  1 snd_ens1370
 snd_ak4531_codec        7552  1 snd_ens1370
 snd                    55012  12
 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec soundcore              10016  2 snd

In /etc/esd.conf I have corrected this to:
 [esd]
 auto_spawn=1
 spawn_options=-terminate -nobeeps -as 2 -d default
 spawn_wait_ms=100
 # default options are used in spawned and non-spawned mode
 default_options=

and the rest in:
I have followed the guidelines of [http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567) and  [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)
, which helped Kino and XMMS but not Lame.[/SIZE]

How to get export through Kino using Lame to function without slowing the whole computer down??
[SIZE=4]
**AND the workaround Lame usable solution:  :???: **[/SIZE]

"Decode" without Lame .

How to redraw usefull mp3 and Wav sound out of vidios without the Lame project problem of fast computers:

Use eg. Kino for Video and Audacity for sound-editing

In Kino choise which video part (that include wav sound) you like to edit. press the FX and Export as MP2 (that use sox, that do not sox like Lame).
Close Kino.

Rename the resulting "yourchoise.MP2" file to "yourchoise.mp3"

Go to Audacity, file open the yourchoise.mp3 , make your changes and save NOT as yourchoise.wav but still as a .mp3 eg.: yourNEWchoise.mp3 .

Open a xterm window to transcode by writing:
sox yourNEWchoise.mp3 yourNEWchoise.wav

Now you can import your newly revised Audio into Kino again:
sudo Kino
press the FX and Audio Transition, Dub or Mix yourNEWchoise.wav into your vidio again.

Hope you can use this. A better way -a Lame solution- is wellcome.

Best regards 
Phillip

---

### Post by Philipude on 2005-05-31
[QUOTE=girlfreddy]Ok. I did almost all that you said here, (except the expert stuff at the end) and I still have no sound at all through Ubuntu. What's up now?
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
 ](*,) 
I've been doing this for a month trying to figure it out. RT#M isn't working.[/QUOTE]
 **Solve software-problem with change of hardware.**
I have the same primitive on-board soundcard as you - not really wellfunctioning in general. And did not bother that long. I placed an old 10$ sound-blaster convertible soundcard in a free slot in the motherboard, disabled the onboard one in the advanced bios setup when we startup the PC, and restarted Ubuntu and it functioned at once.
Though my PC has only a Lame problem not a hardware problem exept if you find that hardware must adapt to software and not upside down. (a too fast PC). A workaround you may find in my question.
Best regards
Phillip

---

### Post by tomjbo@telus.net on 2005-06-07
Thank you very much for the How To.

I have been looking for weeks to properly get sound setup properly for my Soundcraft mixer and my M-Audio 2496 on Linux.

I have only been on Linux for that few weeks, but this tutorial has helped me immensely.

Your knowledge is very much appreciated!

I am so happy that I don't have to go back to windows!!!

---

### Post by LokeDK on 2005-06-15
I'm having problems with my soundcard Creative SoundBlaster Audigy 2 in Ubuntu Hedgehog. 
I've tried to download alsa and compile it with ./configure --with-cards=emu10k1 --with-sequencer=yes; make; make install - I get no errors so everything seems to be fine. I also ran snddevices.
I still have no sound, and I've check if anything is muted but the sound still doesn't work.

loke@wombat:~$ lsmod | grep snd
snd_emu10k1            83588  2
snd_rawmidi            23072  1 snd_emu10k1
snd_seq_device          8588  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         65912  1 snd_emu10k1
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9376  1 snd_emu10k1
snd_pcm_oss            47648  1
snd_pcm                82056  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  2 snd_emu10k1,snd_pcm
snd_page_alloc          9604  2 snd_emu10k1,snd_pcm
snd_mixer_oss          16768  2 snd_pcm_oss
snd                    51300  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  3 snd
loke@wombat:~$

loke@wombat:~$ lsof /dev/dsp
COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
esd     7338 loke    5w   CHR   14,3      6063 /dev/dsp
loke@wombat:~$

loke@wombat:~$ lsof /dev/snd/*
loke@wombat:~$

And lspci, the only Creative device listed there:
0000:00:0a.0 Multimedia audio controller: Creative Labs: Unknown device 0008

I've also had this problem in Fedora Core 3, but SuSE 9.3 Professional did recognize it perfectly, and played without any problems.
It's getting kind of annoying and I've searched on google like an maniac without finding a solution.

---

### Post by okaaay on 2005-06-21
All this worked for me very well. 
What I'm looking for now is a way to change bass/treble on my Nforce2 AC97 soundcard.
Those controls arent present in the alsamixer at all. 
Third party mixer, perhaps?
(Using Kubuntu, if that matters)

---

### Post by Dave_is_sexy on 2005-06-24
Hmm. I get this:

> Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

When I ask Gstreamer-properties to test the default source. If I leave it as ALSA, sometimes it changes itself back. 

And no gtk ap has sound. which sucks.  :smile:

---

### Post by NeoChaosX on 2005-06-24
Did you install libesd-alsa0? That "failed to construct pipeline" error shouldn't happen if it is installed.

---

### Post by Dave_is_sexy on 2005-06-25
No, it's not in my repositories. I think my repositories are worse than everyone elses. Found the .deb on google ta

---

### Post by Dave_is_sexy on 2005-06-25
OK, here's what's happened. And same error  :| 

```
dave@D5:~/Desktop$ sudo dpkg -i libc6-i686_2.3.2.ds1-20ubuntu13_i386.deb
(Reading database ... 72426 files and directories currently installed.)
Preparing to replace libc6-i686 2.3.2.ds1-20ubuntu13 (using libc6-i686_2.3.2.ds1-20ubuntu13_i386.deb) ...
Unpacking replacement libc6-i686 ...
Setting up libc6-i686 (2.3.2.ds1-20ubuntu13) ...

dave@D5:~/Desktop$ sudo dpkg -i esound-common_0.2.35-2_all.deb
dpkg - warning: downgrading esound-common from 0.2.35-2ubuntu2 to 0.2.35-2.
(Reading database ... 72426 files and directories currently installed.)
Preparing to replace esound-common 0.2.35-2ubuntu2 (using esound-common_0.2.35-2_all.deb) ...
Unpacking replacement esound-common ...
Setting up esound-common (0.2.35-2) ...

dave@D5:~/Desktop$ sudo dpkg libesd-alsa0_0.2.35-2ubuntu2_i386.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use dselect for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
dave@D5:~/Desktop$ sudo dpkg -i libesd-alsa0_0.2.35-2ubuntu2_i386.deb
(Reading database ... 72426 files and directories currently installed.)
Preparing to replace libesd-alsa0 0.2.35-2.1 (using libesd-alsa0_0.2.35-2ubuntu2_i386.deb) ...
Unpacking replacement libesd-alsa0 ...
dpkg: dependency problems prevent configuration of libesd-alsa0:
 libesd-alsa0 depends on esound-common (>= 0.2.35-2ubuntu2); however:
  Version of esound-common on system is 0.2.35-2.
dpkg: error processing libesd-alsa0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libesd-alsa0
dave@D5:~/Desktop$ sudo dpkg -i esound-common_0.2.35-2ubuntu2_all.deb
(Reading database ... 72426 files and directories currently installed.)
Preparing to replace esound-common 0.2.35-2 (using esound-common_0.2.35-2ubuntu2_all.deb) ...
Unpacking replacement esound-common ...
Setting up esound-common (0.2.35-2ubuntu2) ...

dave@D5:~/Desktop$ sudo dpkg -i libesd-alsa0_0.2.35-2ubuntu2_i386.deb
(Reading database ... 72426 files and directories currently installed.)
Preparing to replace libesd-alsa0 0.2.35-2ubuntu2 (using libesd-alsa0_0.2.35-2ubuntu2_i386.deb) ...
Unpacking replacement libesd-alsa0 ...
Setting up libesd-alsa0 (0.2.35-2ubuntu2) ...

dave@D5:~/Desktop$ gstreamer-properties
```

---

### Post by alaithea on 2005-06-25
[QUOTE=NeoChaosX]Did you install libesd-alsa0? That "failed to construct pipeline" error shouldn't happen if it is installed.[/QUOTE]

I was getting this error for ALSA and OSS both, but ESD worked (I have sound in all apps, except ones that require ALSA). When I saw your suggestion, I installed libesd-alsa0 (and synaptic removed libesd0 when I did this). Now I get the "failed to construct pipeline" error for ESD and ALSA, but OSS works. ??????

I found a script called "aadebug", and when I run it, I get the following output:

> ALSA Audio Debug v0.0.9 - Sat Jun 25 13:50:22 EDT 2005
[http://alsa.opensrc.org/?page=aadebug](http://alsa.opensrc.org/?page=aadebug)

Kernel ----------------------------------------------------
Linux shuttle 2.6.10-5-386 #1 Tue Jun 7 08:26:42 UTC 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           29984  3
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  3 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Jun  7 2005 for kernel 2.6.10-5-386.
0 [nForce2        ]: NFORCE - NVidia nForce2
                     NVidia nForce2 with ALC650E at 0xee082000, irq 21
  0: [0- 0]: ctl
 18: [0- 2]: digital audio playback
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: Intel ICH : NVidia nForce2 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : NVidia nForce2 - MIC ADC : capture 1
00-02: Intel ICH - IEC958 : NVidia nForce2 - IEC958 : playback 1

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2p  timer

CPU -------------------------------------------------------
model name      : AMD Athlon(tm)
cpu MHz         : 1597.505

RAM -------------------------------------------------------
MemTotal:       484372 kB
SwapTotal:     1413680 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

I'd really love to get ALSA working, as I'm a musician, and one of my reasons for moving to Linux was all the great free music recording/sequencing software out there. I've already googled this topic to death, and nothing I've tried seems to work, so I've come to the conclusion I'm just not Linux-experienced enough to do it on my own. I started out with a SoundBlaster Live! card in my box, but sound with that wouldn't work at all, so I popped it out, and found that the onboard sound worked (with ESD). Can anybody help me get ALSA up and running? Thanks.

---

### Post by Lunde on 2005-07-06
Thank you for this excellent Howto!

---

### Post by filemanager on 2005-07-12
When I run this:
sudo apt-get install libesd-alsa0

I get this error:
Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate


Also, if I run "alsamixer" in a terminal, it says file does not exist or cannot be found.

Gah!! I can't watch DVDs without sound.. well I can but it's definitely not as enjoyable.

EDIT: Actually I just put a DVD in, and Totem starts up and says "ALSA device "default" does not exist".. so in fact I can't watch DVDs at all  ](*,)

---

### Post by filemanager on 2005-07-12
[QUOTE=filemanager]When I run this:
sudo apt-get install libesd-alsa0

I get this error:
Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate


Also, if I run "alsamixer" in a terminal, it says file does not exist or cannot be found.

Gah!! I can't watch DVDs without sound.. well I can but it's definitely not as enjoyable.

EDIT: Actually I just put a DVD in, and Totem starts up and says "ALSA device "default" does not exist".. so in fact I can't watch DVDs at all  ](*,)[/QUOTE]
 [http://ubuntuforums.org/archive/index.php/t-16284.html](http://ubuntuforums.org/archive/index.php/t-16284.html)

ALSA doesn't exist for amd64? How do amd64 users get sound then!?

---

### Post by sav2005 on 2005-07-13
[QUOTE=ploum]Doesn't work for me :-(

Could you explain a bit more why it would work ?[/QUOTE]

Are you using OSS or ALSA. I opened the volume control and chose the ALSA device and Flash audio works. The ubuntuguide.org deatils the steps to do first but I don't think it mentions this.

Laurie

---

### Post by tseliot on 2005-07-24
I've followed this steps:

Howto go further: listening many sounds at the same time, without ESD !

Now it becomes more technical and so also facultative. But it can be of interest for more than one person.
!!! BE CAREFUL !!! You should try the following only if you already managed to get proper ALSA sound (for example xmms manages to play with the ALSA plugin).
It is not clear that the following will work for any sound card.

The first thing to be done is to tell ESD to use ALSA instead of OSS:

Code:

sudo apt-get install libesd-alsa0



One now creates the asound file:
Code:

sudo gedit /etc/asound.conf


which should look like
Code:

pcm.card0 { type hw card 0 } pcm.!default { type plug slave.pcm "dmixer" } pcm.dmixer { type dmix ipc_key 1025 slave { pcm "hw:0,0" period_time 0 period_size 1024 buffer_size 4096 periods 128 rate 44100 } bindings { 0 0 1 1 } }



Then one restarts ALSA:
Code:

sudo /etc/init.d/alsa restart



Restart your session (that's for ESD), and there you are, you should in principle be able to hear all the "click click" of the interface, to listen to music with xmms, and to play a video with totem, everything at the same time (applications must use ESD or ALSA, ALSA being a better choice).


Now it messed my system up and I can't get ALSA work any more(no sound). How can I go back to my previous settings?

OSS works though...

PLEASE HELP ME ](*,)

---

### Post by ieatw0rms on 2005-07-31
hi there.  my problem is precisely the opposite.  i can get sound in anything BUT totem (xine).  any ideas?

---

### Post by dahli.llama on 2005-08-01
Ok, I have followed the instructions in this thread perfectly.  I can get sound in both xmms through alsa and in cedega (City of Heroes) fine, but not at the same time.

I'd like to be able to hear the sound effects of the game, but listen to music at the same time.  When I start CoH and then xmms, I get this error when I try to play anything in xmms:

Couldn't open audio
Please check that:
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard

My "soundcard" is the builtin card on my nForce2 motherboard.  Like I said I followed the instructions in this thread to the T.  Could anyone give me any suggestions?

---

### Post by Thomvis on 2005-08-06
I have a weird problem with my sound on my Ubuntu 5.04 box. This is my second Ubuntu install, the first was on my laptop wich is working perfect now. Whith that install I only had to deal with a lot of display errors but soudn & linux is all new to me.

The problem is that I can't control the sound with the alsa mixer. None of the sliders work, exept the mute function of the PCM channel. Another problem related to it (I guess)is that Enemy Terretory has no sound. 
But I can control the volume in other ways: most of the apps(i.e Rhythmbox) have an own volume slider and that one works. And in Xine i'm only able to control the sound using esd as the output module. 
I followed all the suggestions on several topics concerning sound problems but it didn't help. Today I discovered this one, I followed the instructions, but still no succes.

Some info: My system is a Medion 8088XXL
The ALSA mixers sees two devices: 
- Intel ICH5 (Alsa Mixer)
- C-Media Electronics id 69 (OSS Mixer)

lsmod|grep snd output:
```

snd_intel8x0           29984  4
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  4 saa7134,snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
```

the lsof output is empty.

I really hope somebody has a clue, because I'm out of ideas. 
Thanks in Advance!
Thomas Visser

---

### Post by Tiede on 2005-08-11
I was reading this howto and it helped me fix my sound! I cannot say thank you enough! Great howto
Now for my 2 cents.
About telling flash plugin to use ESD or AlSA, doesn't the command
```

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

``` do the trick? 

If not, how about installing alsa-oss to route all OSS apps sounds to alsa?
```

sudo apt-get install alsa-oss

```

And thanks again for the GREAT how to!

---

### Post by vkkim on 2005-08-11
Hi, I have a Panasonic CF-R3 notebook (I'm not sure what sound card it is, but I assume it's the default Intel one) and I have been unable to get sound to work AT ALL.  Here is my lsmod|grep snd:

```
snd_intel8x0           30144  1
snd_ac97_codec         65912  1 snd_intel8x0
snd_pcm_oss            47648  0
snd_pcm                82184  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
snd_mixer_oss          16768  1 snd_pcm_oss
snd                    51300  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  1 snd
```

---

### Post by soybean genome on 2005-08-11
[QUOTE=wrochal]Dear,

Solution for Sound in Flash, create link

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Bye, \\:D/[/QUOTE]

I'm joining this discussion way late, but when I do the above, I do get sound from my flash files.  There was no response from a previous poster as to why this works.  <rhetorical question>Should I just chalk this up to voodoo magic?</rhetorical question>

 ;-) 

Thanks.

---

### Post by varunus on 2005-08-11
I think this is a typo in flash, it looks for the wrong number on the end of the ESD library. At least, that's what it seems like.

---

### Post by Tiede on 2005-08-11
This is necessary because when installing libesd0-alsa, libesd.so.0 gets removed... However, OSS being old like it is, it cannot realize that by itself, so we create a link to the newly installed libesd.so.1 by alsa to fool OSS into thinking that everything is still purrrfect.

---

### Post by franziski on 2005-08-14
[QUOTE=dusu]
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```
[/QUOTE]

Very Good!!!!

This simple edit worked fine to me: now I can use xmms to play MP3 without freezes...

My m/board: AsRock (SiS 745) with internal audio card based on ( infamous ;-) ) SiS7012/Intel810 chip

Thanks for the help!

---

### Post by Slugger on 2005-08-14
[QUOTE=franziski]Very Good!!!!

This simple edit worked fine to me: now I can use xmms to play MP3 without freezes...

My m/board: AsRock (SiS 745) with internal audio card based on ( infamous ;-) ) SiS7012/Intel810 chip

Thanks for the help![/QUOTE]
 Very good and very helpful thanks :)

---

### Post by bjweeks on 2005-08-14
Still cant get my  sound working. :mad:

---

### Post by wactuary on 2005-08-14
I think it would be worthwhile to add "apt-get install libsdl1.2debian-alsa" to the standard instructions.  This fixed sound in TuxPaint and gCompris, too childrens games that were relying on OSS because the standard Ubuntu package installed was libsdl1.2debian-oss.

I installed alsa-oss, but that didn't seem to fix my problems.  This package was what I was missing.

Chris

---

### Post by Mataanin on 2005-08-15
And what about 5.1 sound?

Have any of you guys configured it? Perhaps, you could write another good howto;)

---

### Post by Tiede on 2005-08-16
[QUOTE=bjweeks]Still cant get my  sound working. :mad:[/QUOTE]
 what have you tried already? What is he make of your soundcard? Give us more details and we might be able to help then...

---

### Post by vkkim on 2005-08-16
[QUOTE=bjweeks]Still cant get my  sound working. :mad:[/QUOTE]

me too...  :-x 

[QUOTE=Tiede]what have you tried already? What is he make of your soundcard? Give us more details and we might be able to help then...[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=47048](http://ubuntuforums.org/showthread.php?t=47048)

---

### Post by Tiede on 2005-08-17
[QUOTE=vkkim]me too...  :-x 



[http://ubuntuforums.org/showthread.php?t=47048](http://ubuntuforums.org/showthread.php?t=47048)[/QUOTE]
 Follow the instructions [ on this link ](http://www.ubuntuguide.org/#configuresoundproperly) and then report back here.

---

### Post by vkkim on 2005-08-18
[QUOTE=Tiede]Follow the instructions [ on this link ](http://www.ubuntuguide.org/#configuresoundproperly) and then report back here.[/QUOTE]

didn't change anything...

---

### Post by mapman on 2005-08-21
Thanks for the tip Wactuary!  Installing libsdl1.2debian-alsa brought sound to tux paint too.

---

### Post by masterLoki on 2005-08-30
From [Ubuntu-es]("http://www.ubuntu-es.org/node/6878")

Problem with sound y Hoaty and a SIS SI70012 (This work for many SIS cards and also VIA)

1º Open Volumen Control (path: Aplications/Video & Sound/Volume Control), (another path: from console: sudo gstreamer-properties)

2º "File"/Change Device/Choose the one will use.

3º Click on "Edit"/Preferences & check "IE958 Capture Monitor", close window.

4º Click on Tab "Commutators" & Uncheck "IE958 Capture Monitor".

And that's it   \\:D/

---

### Post by fberna on 2005-08-30
what if during installation ubunto does not recognize any sound card?

If I start the volume monitor it says that it cannot connect to the sound daemon.

The esd command gets a 

root@linux:~ # esd
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave

skype logically says "audio problem".

PC is a Compaq desktop (pentium III) with its original Compaq premium sound card.

I am new on linux, so doesn't have a clue on how to proceed for getting the card recognized.

Thanks for any help.

---

### Post by Tiede on 2005-09-06
give us the outputs of ```
lsmod | grep snd 
``` and that of ```
lspci
```
Prefarably in [here](http://ubuntuforums.org/showthread.php?p=331464)

---

### Post by Garyu on 2006-04-19
yeehaaw. thank you. killing esd makes me able to play sounds in breezy from all kinds of places. just a detail, but very nice. :cool:

but this makes me wonder... why include esd if I don't need it???

---

### Post by ubu-for on 2006-05-24
I don't have sound for Wolfenstein-ET and TC-Elite.

dsp error messages:
------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------

or asdp error message:
------- sound initialization -------
/dev/adsp: No such device
Could not open /dev/adsp
------------------------------------

"lsmod | grep snd":
snd_intel8x0           33692  2
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

"lspci":
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
0000:05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

THX for your HELP!

---

### Post by ubu-for on 2006-05-25
> 
I don't have sound for Wolfenstein-ET and TC-Elite.

dsp error messages:
------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------

or asdp error message:
------- sound initialization -------
/dev/adsp: No such device
Could not open /dev/adsp
------------------------------------


Solved! :mrgreen: 

1. open Terminal
2. "sudo -i" Return
3. "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" Return
4. "echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss" Return
5. close Terminal
6. open Terminal
7. "et" Return

---

### Post by tspier2 on 2006-08-03
I did the things it says for sound, but my sound still won't work. I can play music fine with xmms and on the web, but I cannot hear anything.

---

### Post by er-ku on 2006-08-06
> **dusu said:**
> *[COLOR=DarkRed]The only dark point[/COLOR]*: OSS applications can still only have access to the sound card one after the other, which is the case of the flash plugin. Thus it is necessary to switch off all sound *before* launching a flash animation. Sometimes one even has to restart the navigator.

You can use the `aoss` wrapper from alsa-oss package to make OSS programs use ALSA.

> *[COLOR=DarkRed]If someone knows a trick to make flash use ALSA or ESD, please tell us ![/COLOR]* About this, you can go and see the post by wrochal in this thread

The same applies here. If you use Flash inside Firefox (not Galeon or Konqueror), you can edit /etc/firefox/firefoxrc file by adding the following line to it:
```
FIREFOX_DSP="aoss"
```

Then Firefox will know it has to use AOSS wrapper for Flash content. I don't know how to achieve the same in other browsers though...

However, Flash was crashing along with Firefox for me at the end of each and every YouTube movie, and now that I think of it, aoss could have been a reason for that...

---

### Post by tammx on 2006-09-12
Hi!
Last night I upgraded from Breezy Badger to Dapper Drake and after that my soundcard stopped working :(

>lsmod | grep snd
snd_pcm_oss            46368  0
snd_pcm                78344  1 snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_mixer_oss          16128  1 snd_pcm_oss
snd                    48644  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9184  1 snd

>lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

> /etc/init.d/alsa-utils start
 * Setting up ALSA...  * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'...                                            

Further more, even ">cat /dev/dsp" returns "cat: /dev/dsp: No such device" . Xmms with OSS output doesn't work, neither with ALSA, neither does anything else... 
Any ideas?

EDIT: oops wrong forum, how can I delete this message ](*,)

---

### Post by daageep on 2006-11-08
adding the symlink works! wow! thanks!

---

### Post by ssavelan on 2007-02-14
I think that this thread may be too outdated to help with my specific problem.  I did learn from and enjoy the background on OSS/ALSA/etc.

It is Feb 2007 and I am(was) running a two sound card set-up with layla24 and snd-via82xx, the VIA being the default (up until yesterday) on Edgy-generic.  The sound on Flash went out; yet, everything else was working.  I tried some tinkering and now.... I can't get a sound out of the machine at all (unless I boot to my xubuntu or windoze partitions).  It was running so smoothly and happily for a couple of weeks.

Error message... can do something as simple as open up gedit to get it:

ALSA lib confmisc.c:1283:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3972:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm_direct.c:1427:(_snd_pcm_direct_get_slave_ipc_offset) Unknown slave PCM hw:0,0

The Via was 0 and the layla was 1.  Now it doesn't see the VIA and doesn't play anything out of the layla or launch JACK or anything.

"
Then one restarts ALSA:
Code:

sudo /etc/init.d/alsa restart

"

I get:

biouser@reishi-tsunami:/etc/init.d$ sudo /etc/init.d/alsa restart
sudo: /etc/init.d/alsa: command not found

from anywhere in the terminal.

I reckoned that this thread is pretty old and there is an "alsasound" command of some sort in the /etc/init.d filesys so I tried:

biouser@reishi-tsunami:/etc/init.d$ ./alsasound restart

and a window pops-up saying that the volume manger in the panel, formerly assigned to the VIA, quit unexpectedly.  It is crossed out in red and unavailable when I boot to this partition now anyway (with no sound upon splash and no sound upon entering the desktop).

oh... the error message that I got was because I didn't sudo...

so I get....

biouser@reishi-tsunami:/etc/init.d$ sudo ./alsasound restart
Shutting down sound driver: done
biouser@reishi-tsunami:/etc/init.d$ 

hmm.. no error, encouragingly, and this time it does not disturb the disabled volume manager.

yet, no sound in anything.

Strangely, Preferences>Sound has no cards now, last time I booted the Layla 24 was there, only the VIA was lost.

When I:

biouser@reishi-tsunami:/etc/init.d$ lsmod|grep snd

I get:

snd_page_alloc         11656  0 

I am currently a bit out of my league there (Feb '07) but would like to know what that means.

biouser@reishi-tsunami:/etc/init.d$ sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

goes of without a hitch.... but I already had that from... well I can find the thread where I got that from originally...

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx")

and

[https://help.ubuntu.com/community/EchoMia]("https://help.ubuntu.com/community/EchoMia")
 
have been my mainstays in dealing with my sound cards, in addition to ubuntuguide.org
-ctrl-f "midi"-

I fear that I may have to start again with a mint install.  If anyone can help they would be my heroish of course.

Who is the Ubuntu sound master?  How is Ubuntu Studio coming along; it seems pretty dead; I've been trying to find people that I can help.

I was thinking about launching a mint install and documenting my every move.

---

### Post by ltdung80 on 2008-08-19
dear all !
I've just working on Ubuntu 7.10. and I have a problem with my sound on board.

this is my PCI sound :

```
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)

```

I am using ALSA. everything of sound not wrong. but I had a bit little problem. It is not real-sound.  when i listen a song . Voice of singer is not real. small and far and same a wave .

Does that problem be drivers sound, doesn't it ?

I checked on Windows Xp . The sound is well.

My computer's using 2 OS.

plz help a solution ! thanks . Sorry if my English is not well.

---

### Post by swissz on 2010-08-11
Hi!
I have Karmic Koala and I had no ringing in and other notification sounds in Skype. I found out, that their volume was set to zero in the system settings.
So, the solution is to go System-> Preferences-> Sound preferences -> Sound effects and set the "Alert volume" from zero to something higher. Thats it. Now it is working!
The alert volume was probably set to zero when the login sound of Ubuntu was deactivated.

---

