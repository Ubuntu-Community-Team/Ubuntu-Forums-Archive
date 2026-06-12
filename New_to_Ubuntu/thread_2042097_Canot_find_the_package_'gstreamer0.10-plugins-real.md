---
title: "Canot find the package 'gstreamer0.10-plugins-really-bad' in Synaptic."
date: 2012-08-14
forum: New to Ubuntu
---

### Post by sebin on 2012-08-14
I am a beginner level ubuntu user. 

In Synaptic Package manager i cannot find the package "gstreamer0.10-plugins-really-bad".

Information may be needed to help me
--------------------------------------------------
>lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

>uname -r
2.6.32-32-generic

My requirement:
I want to play .m4a in my 'Totem Movie Player 2.30.2'

So i found that i have to install the above mentioned package
The information i got it from: [http://www.linuxforums.org/forum/debian-linux/87647-gstreamer-aac-m4a-support-etch.html](http://www.linuxforums.org/forum/debian-linux/87647-gstreamer-aac-m4a-support-etch.html)

I have found i can download the .deb file from [http://www.deb-multimedia.org/dists/stable/main/binary-sparc/package/gstreamer0.10-plugins-really-bad](http://www.deb-multimedia.org/dists/stable/main/binary-sparc/package/gstreamer0.10-plugins-really-bad)

But i would like to install it with Synaptic.

In Synaptic i can find 'nice', 'good', 'bad' and 'ugly' but not 'really-bad'.

Thanks.
(this is my first post :)

---

### Post by NikTh on 2012-08-14
Hi , 
If you want to search for Ubuntu packages , you can go here --> [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and fill the required fields 
or 
you can open a terminal (ctrl+alt+t) and use the search option from apt like this 
```
apt-cache search <package name or part of>
```This package you are looking for , is not in Ubuntu's Official repositories. Is an external package , so you must add an external repository to your system to install this package. 

These repositories listed here --> [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) , (this  is a link from the link you gave) , is for Debian. I don't know if you add a debian repository to Ubuntu will work ok or if you install the .deb package make any difference. 

As for m4a files , I think are playable on Ubuntu 12.04 with gstreamer plugins you added. 
Probably another player needed to play them. 
Try to install Smplayer.
Open a terminal and ```
sudo apt-get install smplayer
``` and try to open your files again with Smplayer.
Thanks

---

### Post by mc4man on 2012-08-14
you need the ffmpeg gstreamer plugin & likely the bad one as well. 
Your link is somewhat generic post from 5 yr.'s ago, Ubuntu doesn't have a 'really bad' package anymore
So installing these three should take care of most decoding needs

gstreamer0.10-ffmpeg 
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-ugly

Or copy & paste this complete command into a terminal, press enter on keyboard

```
sudo apt-get install gstreamer0.10-ffmpeg \
gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by sebin on 2012-08-19
@NikTh As you suggested i install the SMplayer. while playing the m4a i got a warning telling my MPlayer is old( i have attached the screen shot). And i have attached the log file.

As mc4man told, the package is old so i have not installed the '**really-bad' **from other sources. 

@mc4man all the three packages you have mentioned are installed in my computer.

Still the m4a is not working. 

Thank you for the help.

---

### Post by Frogs Hair on 2012-08-19
Ubuntu is based on Debian and this comment was in synaptic under sound-juicer.   > gstreamer0.10-plugins-really-bad (not available in Debian)

---

### Post by sebin on 2012-08-19
So what can be the problem for not playing the m4a file? :(

---

