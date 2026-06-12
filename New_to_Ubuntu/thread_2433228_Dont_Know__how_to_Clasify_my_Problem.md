---
title: "Dont Know  how to Clasify my Problem"
date: 2019-12-16
forum: New to Ubuntu
---

### Post by rohitdave8401 on 2019-12-16
Hi
I do not have any programming experience neither do I have any experience with Linux
I am not sure how to explain my problem / issue / ignorance so please bear with me.
I recently installed Ubuntu 18.04 on my laptop with Windows 7 as a dual boot.
I am interested in listening to Digital Radio Mondial (DRM) used by many radio broadcasters. For those interested, I use the sdr.hu  web site to log into receivers from around the world.
To listen on Windows 7 there is a Windows specific program which I use successfully.
To listen to DRM on Ubuntu we need to install a program called DREAM specific to Linux.
 For this I had gone to[B] Github ([https://gist.github.com/onetransistor/4cbe3a8ab5d47da22cde]("http://Dream Github")) and copied and pasted it to my Terminal on Ubuntu. Is this Correct ?
If this is correct then how do I make DREAM run ?
If this is wrong then how do I use the code on Github to run DREAM with Ubuntu ?
Please if someone can help.
Thanks
Rohit

[/B]

---

### Post by Impavidus on 2019-12-16
That script hasn't been updated in over two years, so it's a bit old. Furthermore, it will download, build and install everything manually, which means doing things the hard way and no automatic updates. That is really the last resort to install anything on Ubuntu.

Dream uses libfaad2 to do the actual decoding of audio streams. The script you linked to will install libfaad2 version 2.7. On Ubuntu 18.04, you can get libfaad2 version 2.8.8 from the repositories. I see that the vlc media player depends on libfaad2, so I assume that vlc can play digital radio mondiale streams. I never tried it myself, but I think that's the best way to make this work.

BTW, the link in your post doesn't work. You swapped around the target and the link name.

---

### Post by oldfred on 2019-12-16
I have a tiny app that used to use qt4 & webkit. My own python browser with some background automation, so I can push a button to change links & display info from local sqlite db.

But I have updated it to qt5 & webengine, so your link is installing old versions of just about everything.

---

### Post by hk42 on 2019-12-21
Thanks for the link.
 It worked for me but I have yet to try the software.
dream is located in /usr/local/bin
Another way to receive DRM is swradio here:
[https://github.com/JvanKatwijk/swradio-8](https://github.com/JvanKatwijk/swradio-8)
The APPimage file worked for me with an SDRplay device.

---

