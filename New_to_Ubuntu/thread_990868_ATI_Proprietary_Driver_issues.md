---
title: "ATI Proprietary Driver issues"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by TOMM_1230 on 2008-11-23
I downloaded the ATI Radeon 4800 series driver which said it was self installing.  It has not self installed so how do I make it install.  When I click on it it opens up in Kate.

The file name is:
"ati-driver-installer-8-11-x86.x86_64.run"

I am running the 64-bit version Kubuntu 8.04 (Hardy Heron).

---

### Post by tardeevo on 2008-11-23
I got K flavor 64 as well and a radeon 3200HD and I'm coming from the long road to install just yesterday and after all that cr@p I'd the bad surprise to discover that **those drivers were crippled** and today I'd to rollback.
But if you wanna try anyway you have first to turn executable the .run file and then launch it from konsole.
Then you gotta choose to build the install stuff for ubuntu 8.04 and then you must install a huge bunch of packets (don't remember exactly - you got to find out by yourself reading the error messages) to build that stuff.
If you'll succeed, you may start again the .run and this time you may launch the install procedure safely.
Hope you better luck than me.
Anyway this is not a good way to go, dear AMD-ATI.

---

### Post by Bablefish on 2008-11-23
Your not the only one to have problems with those !@#$^&* ATI drivers. It crashed my video drivers when I tried to install them.

---

### Post by xravexheavenx on 2008-11-23
Open your terminal and navigate to the folder you saved the file in and type

```
sudo sh ati-driver-installer-8-11-x86.x86_64.run
```

Should take you the the install

I should warn you though...  ATI's drivers are garbage.

---

### Post by tardeevo on 2008-11-24
Today I got news, good ones
After experiencing bad issues with win XP on the same machine as well while playing with Bioshock, an extensive testing revealed that I had a faulty memory bank #-o. 
I pulled it out then and I went to finish the whole Bioshock demo without a hiccup, therefore I reinstalled the ATI drivers for linux and, hell, now it works like a charm! \\:D/

---

### Post by GordonJ on 2008-11-24
I hope this helps as I'm very new to Ubunto.  I installled an ATI 3450 graphics card and downloaded the drivers from the ATI site. could not get them to install as I could not login as a superuser.
Went onto the Add/Remove programes and typed in ATI. This brought up a list of programes one of which was for ATI drivers (about 1/3 of way down list). Installed it and the card is now running properly. Also installed a file (System Information) which allows me to check various things such as processor, memory etc. This shows the graphics card is installed and working.
GordonJ

---

### Post by tardeevo on 2008-11-25
I guess this is the best solution for beginners GordonJ, cos it avoids the hassle of getting into nerd things. The only drawback is that you miss the catalyst control center that is useful to fine-tune your card and so, since I still have the built up of the latest Ati drivers I mentioned above I'll share it for those who got Kubuntu 8.04 **64 bit** (should work for the Ubuntu 64 flavor as well)
Grab the targz [_from here_]("http://www.fabiushouse.com/ati-driver-installer-8-11-x86.x86_64.tar.gz") and do as follows:
1. unpack it as usual from the desktop (click the right mouse button over the file, then click **extract->extract here** from the popupmenu)
2. enter the unpacked folder starting with ati-driver-installer... and open a console clicking the right mouse button into a blank zone of the same window and choose **actions->open terminal here** (on kubuntu - on ubuntu dunno if is like this as well)
3. in the console window type: **sudo ./ati-driver-installer** then press the **tab key** in your keyboard to auto complete the right file name that have to ends with **.run** or write by yourself the entire file name (find out in the unpacked file list).
4. type in the console prompt asking, the administrator password (the password of a user with admin rights or the user you used to install ubuntu)
5. wait until the script loads and if you did right will pop out the ati installer panel with a penguin. Click **continue** and from now on will be a piece of cake.

---

### Post by GordonJ on 2008-11-26
Many thanks tardeevo for the reply. One of these days I might go a bit nerdy when I get more experience with Ubunto.  Am now trying tom get the sound card working so will check it out.
GordonJ

---

