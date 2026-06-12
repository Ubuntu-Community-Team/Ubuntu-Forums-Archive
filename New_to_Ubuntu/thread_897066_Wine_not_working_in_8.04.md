---
title: "Wine not working in 8.04"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by edzell on 2008-08-21
Absolute newbie here, migrating from Win98 (non power-user.) I've installed 7.10 to master disk & upgraded to 8.04; have Win98 on second drive on boot menu. I now want to instal some of my Win programs on main drive under wine. Can't get it to work. "Configure wine" dailogue box comes up but going through the "Add" steps produces no result. Programs don't show up on virtual C drive. I've tried both adding the installer and the actual program exe but neither appears to work.

Tried running winecfg from the terminal and I get the error message "fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer.

All assistance gratefully received (plain English if possible!)

---

### Post by rockerphil on 2008-08-21
ok, my suggestion is to open up a terminal and cd (works just like the DOS command) to where you downloaded the .exe file (more than likely "Desktop"). normally the file downloaded is an install program, so run it through wine via the terminal to install it with the "wine" command. somthing like this, for example i installed Firefox 2 in Wine, so i ran this

wine Firefox\ Setup\ 2.0.0.7.exe

thus running the install file for Firefox 2, then all you need to do is cd to the folder it installed to, in my case it's ~/.wine/drive_c/Program\ Files/Mozilla\ Firefox, then simply use the wine command again to run the program's main .exe file, in my case, firefox.exe, i hope this isn't too confusing and is of some help, if it is confusing, please feel free to reply back and i'll be more than willing to help

Phil

---

### Post by 4Orbs on 2008-08-21
> I get the error message "fixme:mixer:ALSA_MixerInit

I think you can go to the audio settings in winecfg and switch to the OSS mixer, the error will stop. Untick the ALSA mixer, tick the OSS mixer, click the test sound button, if it works save and close.

---

### Post by Butthead on 2008-08-21
You all *DO* know that you can install Wine in 8.04 by going to "System Settings" and hitting the "Advanced" tab at the top, right? :confused:

It installs an older (albeit stable) version of Wine.

I think this is maybe why so many people are having trouble installing Wine from scratch in 8.04.  Maybe it conflicts with the one installed by default? :confused:

---

### Post by edzell on 2008-08-21
Oh dear!

Thanks for the replies but you don't realise what a newbie you're dealing with.

rockerphil: I either don't understand the command syntax or the directory/folder structure in Ubuntu. I've tried every cd command I can think of to get to the directory where the instal .exe sits, with always the message "no such directory." Tearing my hair out.

4Orbs: Tried the switch to OSS but the error message persists. I would think Wine should run without the sound anyway?

Butthead: I haven't found "System Settings" or any "Advanced" tab - ??? I have system preferences and system administration but neither of them seems to contain the choices you mention.

I'm really puzzled - Wine worked just fine under 7.10, and even I managed to figure out how to set it up.

---

### Post by Butthead on 2008-08-21
"System Settings" found under your main KDE (or) K menu (I don't know about Gnome though?). :confused:

Looks like a Wine glass icon when you finally see it.

---

### Post by edzell on 2008-08-21
> **Butthead said:**
> "System Settings" found under your main KDE (or) K menu (I don't know about Gnome though?). :confused:

Looks like a Wine glass icon when you finally see it.

AHA! I'm running Gnome, which explains that part of my confusion. Do you think KDE is more intuitive when switching from Windows?

---

### Post by Butthead on 2008-08-22
Hmm, I really don't know.  Personally, I have always used KDE since I made the switch. :confused:

I imagine "System Settings" is found somewhere in Gnome too? :(

---

### Post by billgoldberg on 2008-08-22
> **edzell said:**
> 
rockerphil: I either don't understand the command syntax or the directory/folder structure in Ubuntu. I've tried every cd command I can think of to get to the directory where the instal .exe sits, with always the message "no such directory." Tearing my hair out.



I hope you realise you can just use nautilus (the file manager, start it by going to places -> home), navigate to the folder you downloaded it to and double click it. Wine should open it by default. Or else right-click it and open with Wine.

---

### Post by edzell on 2008-08-23
> **billgoldberg said:**
> I hope you realise you can just use nautilus (the file manager, start it by going to places -> home), navigate to the folder you downloaded it to and double click it. Wine should open it by default. Or else right-click it and open with Wine.

Hot damn!! Thanks; That works. With windows on my slave drive, I just click on the program exe's and they run, even though I haven't "actually" installed them in ubuntu/wine.

Not all of them work though, so maybe I'm missing something. Are there some that just run, some that have to be "formally" installed, and some that just won't work at all?

Thanks for the help meantime.

---

