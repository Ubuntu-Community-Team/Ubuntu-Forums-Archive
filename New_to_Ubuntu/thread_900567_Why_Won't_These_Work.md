---
title: "Why Won't These Work?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Agrajag27 on 2008-08-25
I've migrated my Dell XPS 1530 laptop over to Ubuntu 8.04 and I really am coming around on it to the point of preferring to boot into it instead of Vista (which is also on the laptop).

However, I have a few nagging problems that remain and they're really annoying ones that take the wind out of my sails for recommending it to others or feeling like I can uninstall Vista and, ultimately, give up XP on my desktop down the line.

Can anyone help attack the following list of annoyances?

1. I cannot play ANY commercial DVD using Ubuntu. The drive is fine because everything plays just fine in Vista. Totem tells me that nothing is there. I prefer VLC but it too refuses to play.

I've installed libdvdcss2. I've installed codecs. I've followed every thread I could find on this. VLC reports (after seeing the DVD in the drive and ID'ing it properly):

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted


2. My touchpad is driving me nuts. I've gotten it under control following threads on it but the bottom line is that scrolling using it only works about 40% of my sessions. Sometimes I boot and it works but most of the time I boot and it won't work. Again, there's a lot of talk about this but no one seems to have any clue why it would work one boot and not another.

3. I have a game service I like to run on my PC and it has a Java client. It's called Brettspielwelt. The download page is here:

[http://brettspielwelt.de/Community/Download/]("http://brettspielwelt.de/Community/Download/")

The problem is that I have no clue what to do with the files I get. I'd like to understand the process so that future similar apps I'll be able to install on my own but for now I'm at a complete loss.

---

### Post by philinux on 2008-08-25
For 1.

I assume you've installed ubuntu-restricted-extras and been here

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

To get the medibuntu stuff.

If so you can find further help here.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by philinux on 2008-08-25
For 3 obviously choose the linux stuff which is a tar file. Think zip file.

Download it to your desktop and double click the folder. Extract it to you desktop. There should be a readme file.

---

### Post by Agrajag27 on 2008-08-25
For 1. I did install all of that. 

For 3. No readme that helped. It's just an SH file that doesn't launch.

---

### Post by SunnyRabbiera on 2008-08-25
Well for your DVD concerns you can try other applications to try them out, but normally when you get libdvdread and libdvdcss it normally works so we may have to do some hunting here.
I know some commercial DVD's have issues under linux though, not our fault mind you

---

### Post by starcannon on 2008-08-25
If you can get your hands on [LinDVD[COLOR="DarkOrange"][/COLOR]]("http://www.intervideo.com/jsp/Product_Profile.jsp?p=LinDVD") Currently only available to manufactures, of which Dell is one, it comes standard on a Dell Ubuntu Computer, that should address your DVD concerns entirely. That said the libdvdcss2 package from medibuntu plays most DVD's, indeed I haven't had one that didn't play yet; mind you, I usually don't have new release movies anyway.

---

### Post by ugm6hr on 2008-08-25
For your multimedia issues (inc DVD), check the media link in my signature below.

Trackpad issues are unusual.  Is it possible that the scrolling area is just narrow, and hence works intermittently?

---

### Post by crjackson on 2008-08-25
> **Agrajag27 said:**
> I've migrated my Dell XPS 1530 laptop over to Ubuntu 8.04 and I really am coming around on it to the point of preferring to boot into it instead of Vista (which is also on the laptop).

However, I have a few nagging problems that remain and they're really annoying ones that take the wind out of my sails for recommending it to others or feeling like I can uninstall Vista and, ultimately, give up XP on my desktop down the line.

Can anyone help attack the following list of annoyances?

1. I cannot play ANY commercial DVD using Ubuntu. The drive is fine because everything plays just fine in Vista. Totem tells me that nothing is there. I prefer VLC but it too refuses to play.


Pick your Hardy version below, then paste all related to your install (32bit or 64bit) into a terminal in one swoop and it will PROBABLY fix your DVD issues.  It ALWAYS works for me.

For 32-bit Hardy

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

for 64-bit Hardy
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w64codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

---

### Post by Agrajag27 on 2008-08-25
crjackson, your 32-bit entry fixed it. It's working now. Many thanks!

Only a couple more to go and I'm set.

---

### Post by crjackson on 2008-08-27
> **Agrajag27 said:**
> crjackson, your 32-bit entry fixed it. It's working now. Many thanks!

Only a couple more to go and I'm set.

You're welcome. Don't forget to hit the many thanks button (little gold star) on the bottom right of any posts that helped solve your issues.

---

### Post by Agrajag27 on 2008-08-27
The trackpad isn't an issue with the size of the scroll area. Several people are having this problem. In one session it's easy to scroll. In the next it's impossible to use the pad to scroll no matter where or how you try.

---

### Post by OldTimeTech on 2008-08-27
I have to say I have the same kind of laptop you have and I actually uninstalled the trackpad and run a small laptop mouse and have no problems with the scrolling.

---

### Post by Agrajag27 on 2008-08-27
That'd be fine except the way I use the laptop. I use it all over the house and often on my lap, etc., where there's no space for the mouse and I'd have to go find it each time.

---

