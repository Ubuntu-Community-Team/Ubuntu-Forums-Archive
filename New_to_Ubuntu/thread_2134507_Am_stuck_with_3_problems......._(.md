---
title: "Am stuck with 3 problems....... :("
date: 2013-04-11
forum: New to Ubuntu
---

### Post by virus7 on 2013-04-11
Hello Everybody .. am a newbie to LINUX, and start my journey with Ubuntu 12.04, and am stuck with 3 problems.. 

1.  My First problem is pretty funny. My headphone doesnt work though it  used to when I found a solution from a net and implemented it. solution  was like i had to append a like **options snd-hda-intel model=eapd probe_mask=1 position_fix=1 **to my **/etc/modprobe.d/alsa-base.conf **file.  It was working fine until day before yesterday and then on yesterday  when I logged into my Laptop it stopped working. I tried to switch  several times to sound system with and without headphone but its not  working anymore.
   
2. I want to play .swf format files, Currently am playing it on Gnash  viewer/player but am not happy with it. So is it possible to play this  file using current default player which is Movie Player, and if so then  which kind of plugin I might need to install ??? [ So far Tried to use VLC/KMplayer/Mplayer/Movie Player Nothing of them has worked :( ]

3. How can I install Skype? [ Solved ]

thanks in advance ..

---

### Post by 25tom on 2013-04-11
Skype should be in the Software Center, try searching for it there first. If not you can get it here:

[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)

Select your version of Ubuntu from the dropdown menu and download the .deb file. You should then be able to open the .deb file with the software center, and install it from there.
Hope this helps :)

---

### Post by 3rdalbum on 2013-04-11
1. Never come across that before, sorry. It's always just worked for me with the default Pulseaudio system.

2. Open them with your web browser. Seriously, it works.

3. [http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/) and choose "Ubuntu 12.04 (multiarch)".

When it has downloaded, double-click its icon on your desktop and it will open Ubuntu Software Center. CLick Install, type your password, wait a few moments and it will install.

---

### Post by virus7 on 2013-04-11
> **25tom said:**
> Skype should be in the Software Center, try searching for it there first. If not you can get it here:

[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)

Select your version of Ubuntu from the dropdown menu and download the .deb file. You should then be able to open the .deb file with the software center, and install it from there.
Hope this helps :)

Thanks... a lot it works ....

---

### Post by virus7 on 2013-04-11
> **3rdalbum said:**
> 1. Never come across that before, sorry. It's always just worked for me with the default Pulseaudio system.

2. Open them with your web browser. Seriously, it works.

3. [http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/) and choose "Ubuntu 12.04 (multiarch)".

When it has downloaded, double-click its icon on your desktop and it will open Ubuntu Software Center. CLick Install, type your password, wait a few moments and it will install.

ok I have installed skype, that went smooth .. but am having a tiny problem with my microphone.. dont know why its sounds pretty low... is there any thing i need to fix ?? 

by the way i knew that i can play my .swf in web browser, but basically i want to play some tutorial so i need to manuver through the timing a lot... so need a player which has some capabilities where i can play with the time manu. 

Thanks..

---

### Post by Vaphell on 2013-04-11
is this an ordinary video clip? if so try it in vlc or mplayer, might work
if they don't work, install swftools and see if you can extract assets from the swf file.

---

### Post by nerdtron on 2013-04-11
> **virus7 said:**
> ok I have installed skype, that went smooth .. but am having a tiny problem with my microphone.. dont know why its sounds pretty low... is there any thing i need to fix ?? 

Not sure since I don't use skype but try adjusting the MIC options in alsamixer. Type the alsamixer command in the terminal and use those options to adjust the mic volume/gain etc....
```
alsamixer
```

---

### Post by virus7 on 2013-04-11
> **nerdtron said:**
> Not sure since I don't use skype but try adjusting the MIC options in alsamixer. Type the alsamixer command in the terminal and use those options to adjust the mic volume/gain etc....
```
alsamixer
```

when i go to alsamixer i can only see 3 options : Headphone, Speaker, PCM but couldnt find any Mic option :(

---

### Post by nerdtron on 2013-04-11
(This may be a dumb reply)

Have you tried pressing left and right arrow keys? mine has a lot of options including front mic, rear mic etc.

---

### Post by zrdc28 on 2013-04-11
**I want to play .swf format files,**

Download and install VLC and it will play almost everything that you through at it.

[http://www.ubuntugeek.com/install-vlc-2-0-1-in-ubuntu-12-0411-10.html](http://www.ubuntugeek.com/install-vlc-2-0-1-in-ubuntu-12-0411-10.html)

---

### Post by anthoj on 2013-04-11
> **virus7 said:**
> when i go to alsamixer i can only see 3 options : Headphone, Speaker, PCM but couldnt find any Mic option :(

I know this may be trivial, but did you scroll to the right? Because when I ran alsamixer my mic options are to the right (off the screen).

---

### Post by virus7 on 2013-04-12
> **nerdtron said:**
> (This may be a dumb reply)

Have you tried pressing left and right arrow keys? mine has a lot of options including front mic, rear mic etc.

no its not e dumb reply trust me am a new too.. you could expect me to do this ... too :P but fortunately this time  i tried to do that... and let me share one more info with you.. when i first installed Ubuntu 12.04 if am not wrong i had seen so many options in AlsaMixer but now am having only 3 :(

---

### Post by virus7 on 2013-04-12
> **zrdc28 said:**
> **I want to play .swf format files,**

Download and install VLC and it will play almost everything that you through at it.

[http://www.ubuntugeek.com/install-vlc-2-0-1-in-ubuntu-12-0411-10.html](http://www.ubuntugeek.com/install-vlc-2-0-1-in-ubuntu-12-0411-10.html)


yes I have tired this option. but I can hear audio but not video. do you think i should install some kind of plugins for VLC to show me video ?

---

### Post by Vaphell on 2013-04-12
what about mplayer?
you can also check if installing ubuntu-restricted-extras package helps. There are some codecs in it.

---

### Post by 25tom on 2013-04-12
With regard to the mic levels, I think there is an option in Skype to have it set your levels automatically... fiddling with that may help. It may be that it's over-lowering your levels, or it could be off and activating it might help the mic levels, perhaps...
Hope this helps :)

---

### Post by virus7 on 2013-04-16
> **Vaphell said:**
> what about mplayer?
you can also check if installing ubuntu-restricted-extras package helps. There are some codecs in it.

yes I have used Mplayer and on very first day after installing Ubuntu 12.04 I have installed ubuntu-restricted-extras. :(

---

