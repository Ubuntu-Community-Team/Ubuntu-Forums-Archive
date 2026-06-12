---
title: "Lots of Q's, dev mode, installing flash, utorrent, etc."
date: 2013-09-29
forum: New to Ubuntu
---

### Post by kyla2 on 2013-09-29
Hi, I just got the Acer C7 and put Ubuntu 13.04 (crouton, cinnamon) on it.  I have run into a few problems though.  The first one was installing things; I went to the Adobe Flash Player website and the thing went to my downloads but I don't have an rpm unpacker or whatever.  I was able to put skype on there successfully, but even from the Ubuntu apps website I choose "Launch Application" and nothing happens.  

I tried entering sudo apt-get flashplugin-installer but I always get "sudo: apt-get: unknown command".  Unknown command sudo, etc. 

I also thought maybe getting out of dev mode would help and wanted to see if I don't have to be in dev mode for Chrubuntu to work, but now I can't get back to Chrubuntu with ctrl+alt+f2.    So I have to stay in dev mode the whole time to keep chrubuntu?  

So
1. Installing stuff. 
2. Stay in dev mode?
3. If I don't have to stay in dev mode, it really will wipe everything each and every time I enter it again right, even after I install Ubuntu?

Thanks guys

---

### Post by ajgreeny on 2013-09-29
Use command ```
sudo apt-get [COLOR=#ff0000]install[/COLOR] flashplugin-installer
``` You forgot the "install" part.

For skype you need to look in the Internet group in the menu, or using dash start typing **skype** and it's launcher should appear in the list.

I have no idea what you are talking about when you say "dev mode", what are you asking about; do you mean in live system running from a DVD or USB?

---

### Post by kyla2 on 2013-09-29
Developer mode...I got flash to work a few hours ago thankfully.

---

### Post by kyla2 on 2013-09-29
Yep got out of Developer mode, wiped everything including Ubuntu.  Reinstalled cinammon crouton 13.04 today and now it won't let me put icons on the desktop...ok.

---

### Post by JeQhdMD on 2013-09-29
From what I've read about Chromebooks - - you have to invoke developer mode, the Crouton app uses a chroot environment to run Linux alongside ChromeOS (not a dual-boot, no reboot required, just a hot-key switch).   But, you can't go back to the regular Chromebook configuration as it restores the original clean ChromeOS, wipes out your changes, and enforces "verified-boot" again.   In other words, "DON'T" press the space bar at startup - continue to run in dev mode.

See this for more info:  [http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/)

---

### Post by ajgreeny on 2013-09-30
Sorry about my ignorance; I didn't realise that the Acer C7 is a chromebook.

---

### Post by kyla2 on 2013-09-30
lol no it's ok I'm the beginner.  I should have said it was a chromebook.  What's odd is I restarted my computer today to see if that would help move the icons, and I stayed in developer mode (did not press space bar and renable OS verification) and I got back to chrome OS where all of my chrome stuff was still there but couldn't get to chrubuntu with ctrl+alt+shift+f2.  Looks like it's just gone.

---

### Post by kyla2 on 2013-10-10
Update: Fixed.  Didn't know I had to use sudo startcinnamon again to get back into the program upon restart.

---

### Post by newb85 on 2013-10-10
I know you said you already got flash working, but in case you haven't realized/been told yet, *.rpm aren't for Ubuntu (or any other Debian-based Linux).

---

