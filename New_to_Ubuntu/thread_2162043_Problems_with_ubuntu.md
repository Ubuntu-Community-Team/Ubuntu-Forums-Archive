---
title: "Problems with ubuntu"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by Sasukan on 2013-07-12
The problem is that ubuntu is very glichy for me. For some reason I can't click on the x button (or the minimize or expand buttuns) to exit an application I have to either alt+f4 or go into file then quit. Another thing is that sometimes after the bios promt pass but before ubuntu boots up it just gives me a purple screen with no text on it when that happens I hit reset. Whenever a window pops up it doesn't let me click ok, cancel or the x buttun I have use the arrowkeys enter and tab. The last problem I'm having is that I can't have click in between windows. This one is difficult to explain so here my best shot :/ lets say I have 2 firefoxs open one ono left and the other on the right I can only use the one on the left I try to click on the other one but it stays in the background.

This is my first time running linux and I would like to keep going on to contine but ubuntu is giving me some problems. I don't know if this because of the hardware or software.
Specs
3.2 gtz 
4gb ram
128 ssd
radeon 5770
Ubuntu 13.04

---

### Post by fantab on 2013-07-13
Have you updated your Ubuntu? If not update it.
Have you installed any Proprietory Graphic drivers for 'radeon'? If yes then try Uninstalling those.
You'll have to look in the **log files** to see what is going wrong... [Read HERE for more info]("https://help.ubuntu.com/community/LinuxLogFiles").

For Ubuntu beginners it would be a good idea to start with an LTS (Long Term Support) versions, as they are very stable compared to a non-LTS version like 13.04. Ubuntu 12.04 is a LTS version.
Re-installing Ubuntu is always the best solution. 

Good Luck...

---

### Post by Sasukan on 2013-07-13
Well something really wierd just happened I got ubuntu 12.04 lts and I did i live boot and eveything was fine. I was like wow this guy was right 12.04 is a lot more stable. Then I installed it and all the previous problems I had came back again.

---

### Post by Hexxus on 2013-07-13
If you just migrated to 12.04LTS I would suggest updating it to see if it helps correct some of these. Also sometimes the image can be corrupt so you could try re-downloading it and burning it to CD or USB Flash drive. 

To update and install updates you could run this from the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Let us know what happens.

---

### Post by Sasukan on 2013-07-13
Updated and uninstalled the proprietory graphic drivers, still same results.

---

### Post by fantab on 2013-07-14
> **Sasukan said:**
> Well something really wierd just happened I got ubuntu 12.04 lts and I did i live boot and eveything was fine. I was like wow this guy was right 12.04 is a lot more stable. Then I installed it and all the previous problems I had came back again.

You seem to be having some Hardware issues, particularly with your Graphics drivers. You perhaps need to remove the fglrx proprietory driver throughly and then reinstall the opensource driver, Follow the instructions [HERE]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx").

---

### Post by Sasukan on 2013-07-16
Well I uninstalled fglrx and installed the opensource drivers nothing changed so I manually installed fglrx and the the only thing that changed was that about an inch of my screen border was black but I fixed that by changing the scaling options in CCC to %0. Back to square one again.

---

### Post by MirrorUniverse on 2013-07-17
> Well something really wierd just happened I got ubuntu 12.04 lts and I  did i live boot and eveything was fine. I was like wow this guy was  right 12.04 is a lot more stable. Then I installed it and all the  previous problems I had came back again. 				
Does anyone know if live boot uses different drivers than the full install?  Would there be a way to revert to the live boot drivers?

---

### Post by oldrocker99 on 2013-07-17
> **MirrorUniverse said:**
> Does anyone know if live boot uses different drivers than the full install?  Would there be a way to revert to the live boot drivers?

The full install is basically a mirror of the live boot. You **might** get a dialog to install proprietary drivers (video, wireless, etc). The live boot does not have proprietary drivers on it; it's using open source drivers.

---

### Post by mastablasta on 2013-07-17
boot uses opensource drivers. 

when you boot hardware is probed and propper drivers are then loaded. but sometimes install writes some settigns it seems. and sometimes you need to blacklist soem chips to not loadthose settings if i understand it correctly. all i know is that evrytime i try live session my sound card works liek a charm. but upon install it sometimes starts acting up forcing me to unload and reload sound modules. luckily i managed to make a simple script as workarround and all it takes is a double click and user password to execute it.

anyway back to grpahics drivers - you card should be well supported by (AMD) fglrx drivers. what is the CPU actually? does it have another GPU chip?

How did you install fglrx drivers?

---

### Post by Sasukan on 2013-07-17
My cpu is Phenom II X4 965 and I installed the drivers by folling this guide [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx).

---

### Post by Gnawnsense on 2013-07-17
Review this page completely: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by mastablasta on 2013-07-18
you cna install them with GUI directly from repositories. you need to enable partner repositories (software center settings) then use additional drivers or in software center in settigns ther eis a tab i believe that will show you the drivers when you enable repositories. then you select what you want and click install. like here : [B][http://*********************.com/2012/09/28/to-do-list-after-installing-ubuntu-13-04-aka-raring-ringtail-operating-system/](http://*********************.com/2012/09/28/to-do-list-after-installing-ubuntu-13-04-aka-raring-ringtail-operating-system/)
[/B]under [B]Video Drivers and Proprietary Drivers Check (Required
[IMG]http://debianhelp.files.wordpress.com/2012/09/screenshot-from-2013-03-18-085048.png[/IMG]

for some reason forums give asterisks in web address. it should be: **[B]debianhelp[dot]wordpress** there

it seemsthat might be a swear word :-) but probably to protect users from spamers.

[/B][/B]

---

### Post by Sasukan on 2013-07-18
> **mastablasta said:**
> you cna install them with GUI directly from repositories. you need to enable partner repositories (software center settings) then use additional drivers or in software center in settigns ther eis a tab i believe that will show you the drivers when you enable repositories. then you select what you want and click install. like here : [B][http://*********************.com/2012/09/28/to-do-list-after-installing-ubuntu-13-04-aka-raring-ringtail-operating-system/](http://*********************.com/2012/09/28/to-do-list-after-installing-ubuntu-13-04-aka-raring-ringtail-operating-system/)
[/B]under [B]Video Drivers and Proprietary Drivers Check (Required
[IMG]http://debianhelp.files.wordpress.com/2012/09/screenshot-from-2013-03-18-085048.png[/IMG]

for some reason forums give asterisks in web address. it should be: **[B]debianhelp[dot]wordpress** there

it seemsthat might be a swear word :-) but probably to protect users from spamers.

[/B][/B]
Tried that nothing happened.

---

### Post by Boab1993 on 2013-07-18
Graphics Cards and their workings certainly aren't my forte, so this is more of learning thing, but you dont ask you dont get.
Is it possible that this is a problem with optimisation with the multicore amd? or is that what graphics drivers actually do?

---

### Post by blinkydamo on 2013-07-18
What mouse are you using?
I ask because I had a similar problem with my rat 7 and had to remap the buttons in the xorg.conf file.
Just a thought.

---

### Post by Sasukan on 2013-07-19
> **blinkydamo said:**
> What mouse are you using?
I ask because I had a similar problem with my rat 7 and had to remap the buttons in the xorg.conf file.
Just a thought.
  I actually have that same mouse how do I remap it?

---

