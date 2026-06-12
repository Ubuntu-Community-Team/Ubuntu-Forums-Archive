---
title: "DVD playback"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by bgast1 on 2008-09-12
I have a DVD that I want to play. It plays in totem, but I am not satisfied with the appearance. The image is not as sharp as I would like. I have a widescreen monitor and I am getting very small lines in the picture. 

I have VLC installed but it says that it cannot open the disc. 

Kaffeine is asking me to install ccs.sh but I have already installed it, so I don't really know what gives. 

I have turned off desktop effects as well in hopes that it would help. It did not.

---

### Post by crjackson on 2008-09-12
If you have Hardy 32-bit, paste this code into a terminal and see whast happens.  It ALWAYS works for me.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

---

### Post by LindaLou on 2008-09-14
I'm also not pleased with the DVD play on totem.  When viewing there is a definitely horizontal line going through the frame nearly dead center.  The DVD was viewed on a laptop running XP and everything was perfect.
I'm using Ubuntu 64bit.

---

### Post by Casper Hansen on 2008-09-14
> **LindaLou said:**
> I'm also not pleased with the DVD play on totem.  When viewing there is a definitely horizontal line going through the frame nearly dead center.  The DVD was viewed on a laptop running XP and everything was perfect.
I'm using Ubuntu 64bit.

What video card do you have?

---

### Post by bgast1 on 2008-09-14
> **Casper Hansen said:**
> What video card do you have?

I have an ATI Radeon X1950 Pro PCIe card. I now have Kubuntu installed and am trying to play a DVD through Kaffeine. I installed like the 'sorry k-dialog' said but that doesn't work.

---

### Post by SunnyRabbiera on 2008-09-14
> **bgast1 said:**
> I have an ATI Radeon X1950 Pro PCIe card. I now have Kubuntu installed and am trying to play a DVD through Kaffeine. I installed like the 'sorry k-dialog' said but that doesn't work.

your issue might be your ATI card, ATI support under linux stinks but that is more of a ATI issue.

---

### Post by bgast1 on 2008-09-14
> **SunnyRabbiera said:**
> your issue might be your ATI card, ATI support under linux stinks but that is more of a ATI issue.

I haven't been having too many problems with my ATI card. I did what the poster above said to do and I still cannot play DVD's with Kaffiene. I am attempting to play an encrypted DVD. To be precise -- Alice Cooper - Live at Montreux.

---

### Post by mc4man on 2008-09-14
> trying to play a DVD through Kaffeine. I installed like the 'sorry k-dialog' said but that doesn't work.
That is a generic 'somethings wrong' error
Try installing or make sure they're installed - libxine1, libxine1-ffmpeg

Also in the kaffeine settings set the dvd device to /dev/scd[COLOR="Red"]x[/COLOR] instead of a /dev link like /dev/dvd ect.
(red = what the drive is, scd0, scd1 ect.

kaffeine -> settings -> xine engine parameters -> media

edit: if you don't know what your drive is (scdx) run sudo lshw -C disk and it'll be listed

---

### Post by SunnyRabbiera on 2008-09-14
> **bgast1 said:**
> I haven't been having too many problems with my ATI card. I did what the poster above said to do and I still cannot play DVD's with Kaffiene. I am attempting to play an encrypted DVD. To be precise -- Alice Cooper - Live at Montreux.

well if you have the proper stuff installed like libdvdcss things might still be messed up.
Some DVD's dont like linux or its players, but another DVD app for you to try is xine, my preferred DVD playing app.

---

### Post by bgast1 on 2008-09-14
> **mc4man said:**
> That is a generic 'somethings wrong' error
Try installing or make sure they're installed - libxine1, libxine1-ffmpeg

Also in the kaffeine settings set the dvd device to /dev/scd[COLOR="Red"]x[/COLOR] instead of a /dev link like /dev/dvd ect.
(red = what the drive is, scd0, scd1 ect.

kaffeine -> settings -> xine engine parameters -> media

edit: if you don't know what your drive is (scdx) run sudo lshw -C disk and it'll be listed

It starts to play, but then stops saying it is an encrypted DVD and I need libdvdcss installed. But I already have it installed. Adept tells me that libdvdcss2 is installed and I also just did an update on it as well.

---

### Post by mc4man on 2008-09-14
Is a dvd icon showing up on the desktop? If so right click on it -> open with dolphin. Then right click on the VIDEO_TS folder -> open with kaffeine.
What happens then?

---

### Post by bgast1 on 2008-09-14
> **mc4man said:**
> Is a dvd icon showing up on the desktop? If so right click on it -> open with dolphin. Then right click on the VIDEO_TS folder -> open with kaffeine.
What happens then?

No the DVD icon doesn't even show up. This is really baffling me. Even Xine doesn't work. The thing is, I played this DVD with Totem when I had a regular installation of Hardy Heron. I just didn't like the way it looked so I went searching for alternatives.

---

### Post by mc4man on 2008-09-14
Kubuntu can be a real pita.
eject the dvd and re-insert, if it doesn't show up (the icon)  click on the kmenu icon -> system -> open dolphin manager and see if it's listed in storage media.

A related thread, what I saw from fresh install and the 3 ways to open disk properly 
[http://ubuntuforums.org/showthread.php?p=5685122#post5685122](http://ubuntuforums.org/showthread.php?p=5685122#post5685122)

If you can get it going do remember about dvd device in settings

---

### Post by bgast1 on 2008-09-14
Well, I really don't want to, but I guess I will do a fresh install of the Gnome version. If it still doesn't work I guess I will just have to watch it on the TV set.

---

### Post by LindaLou on 2008-09-15
I have a nvidia.

> **Casper Hansen said:**
> What video card do you have?

---

### Post by bgast1 on 2008-09-15
> **LindaLou said:**
> I have a nvidia.

I solved my problem. I ended up using my internal dvd drive instead of my external. I also used VLC to watch my video. You might want to try that instead of Totem. In fact in the past I have always had good luck with VLC, even in windows. I assume you installed everything that was suggested in the past. I have only seen what you desribe from a downloaded movie. I don't watch downloaded movies for 2 reasons. The first being it is probably illegal, and the second being the quality. Same with downloaded music. I would rather have the real thing, artwork and all. i-tunes has started supplying artwork but I don't know how to use i-tunes in Linux, so I use Amazon MP3 or e-Music if I **must** download. Anyway I got off topic, sorry. 

I won't mark this solved on your behalf.

---

### Post by LindaLou on 2008-09-15
bgast1,    Thanks for the info on VLC and not marking this as solved.  I will check it out and see if it works better than Totem and post back.

The DVD in question here, was not a downloaded movie. It is in fact a professional made promotional DVD that I have for my business.  
I don't do downloads either.  I'm in agreement with your opinions.

---

### Post by LindaLou on 2008-09-16
I've downloaded VLC.  How do I make VLC my default movie viewer?  When I insert a DVD, by default Totem plays and the poor image quality is still an issue.

---

### Post by bgast1 on 2008-09-17
> **LindaLou said:**
> I've downloaded VLC.  How do I make VLC my default movie viewer?  When I insert a DVD, by default Totem plays and the poor image quality is still an issue.

I don't know for certain, but if I wanted VLC to be my default, I would just uninstall Totem. I'm not certain if different distros are an issue or not, but when I installed Mint Xfce, I think that the picture was clearer than in Ubuntu. Right now I have Open Geu installed and I tried to watch the same DVD in VLC and I don't think it was as clear as it was in Mint xfce.

---

### Post by LindaLou on 2008-09-18
I was thinking the same - just uninstalling Totem.  

About your mention of Mint xfce.  I'm not familiar with that and when I googled it I came upon this link  [www.linuxmint.com/download.php](www.linuxmint.com/download.php)

Uncertain as to which version I would install in Unbuntu (LTS 64bit), what is recommended??

---

### Post by bgast1 on 2008-09-18
Mint is an entirely different distro based upon Ubuntu. It has most of multimedia stuff already configured. If you like Ubuntu Gnome, you might like Mint Gnome. I only installed the Xfce version because I was playing around. It just so happens that my DVD looked very good in VLC with Mint.

---

### Post by LindaLou on 2008-09-25
Well thanks for the feed back.  Appreciated.  I'm bookmarking the noted pages for future use on my laptop.  Right now, my office PC will most likely be used for DVD viewing so I'll look at installing your suggestions.

---

