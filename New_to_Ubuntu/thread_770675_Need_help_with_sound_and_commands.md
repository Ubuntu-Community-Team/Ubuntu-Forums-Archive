---
title: "Need help with sound and commands"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Bukarts on 2008-04-27
Hi to everyone!
    I am a newbie with Linux and I mean it!  I installed Ubuntu aa few days ago, so far everything was OK! I culd made WI-fi work, Ethernet, but i have some problems with sound! I read all threads about that and solutions, but i can't try all them!
   Becose- I dont know how to get root rights!  Example I need to make some changes in etc/modprobe.d/alsa-base  file, i have to add one line  "options snd-hda-intel model=acer" But it keeps saying me I have no rights to do that! I hope someone will help me.  
BTW. I have Acer Aspire 5710Z  I bought it with preinstalled Vista.

Thanx In advice!:lolflag:

---

### Post by dokdoom on 2008-04-27
To make the changes to that file just put

sudo

in front of the command. An example would be

sudo vim /etc/modprobe.d/alsa-base

Or use whatever editor you perfer. 

Have you tried running

alsamixer

This will let you adjust your systems volume settings.

---

### Post by Bukarts on 2008-04-27
Yes I tried HDA intel (alsa mixer), it is curently selected! I also have Realtek ALC268( OSS Mixer) But no sound with any of them!

---

### Post by overdrank on 2008-04-27
> **Bukarts said:**
> Hi to everyone!
    I am a newbie with Linux and I mean it!  I installed Ubuntu aa few days ago, so far everything was OK! I culd made WI-fi work, Ethernet, but i have some problems with sound! I read all threads about that and solutions, but i can't try all them!
   Becose- I dont know how to get root rights!  Example I need to make some changes in etc/modprobe.d/alsa-base  file, i have to add one line  "options snd-hda-intel model=acer" But it keeps saying me I have no rights to do that! I hope someone will help me.  
BTW. I have Acer Aspire 5710Z  I bought it with preinstalled Vista.

Thanx In advice!:lolflag:

HI and welcome you will need to use root with the editor like ```
gksudo gedit
``` then the location, if you are you using KDE that would be I believe ```
kdesu kate 
```
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bukarts on 2008-04-27
Ok! Thanx! I got the changes saved! Now going to restart! To see what will happen! :)

---

### Post by Bukarts on 2008-04-27
No luck!  Everything seems Ok! But there is still no sound! :(

---

### Post by Bukarts on 2008-04-27
I found my mistake! I added an extra sign "-" betveen  hda and intel. So thanx for help! 

  Now the last thing, where I can find the CUBE??

---

