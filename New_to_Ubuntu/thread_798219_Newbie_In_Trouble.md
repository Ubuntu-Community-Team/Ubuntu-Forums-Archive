---
title: "Newbie In Trouble"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by tad214 on 2008-05-18
Hello Everyone,:)
I am Brand new to the ubuntu world. but i must say, it is an ***[COLOR="Red"]awesome[/COLOR]*** os. Now, what has happened is i downloaded several updates and they all install just fine all but one.:confused: So, i rebooted the system so i could try it again, and everytime i log in, it sends me back to the login screen. It will not let me log in.:confused: Any help with this matter, would be greatly appreciated. Thanks in advance for the help.

**[COLOR="Red"]P.S.[/COLOR]** Also, i would like to upgrade from 6.06, to 8.04, but i downloaded the cd image and can't find the executable to open it up. Can someone tell me why i can't just upgrade online, and if so, how do i go by doing that? Thanks again. Dale

---

### Post by tamoneya on 2008-05-18
when the GRUB loads during startup hit "escape".  Then select the recovery option.  From here you can reset your password in case it got messed up.  ```
sudo passwd username
```Then restart again and try logging in.

---

### Post by tad214 on 2008-05-18
Thank you very much. I will try that now.

---

### Post by tad214 on 2008-05-18
Well, i tried the password change, and it did not fix the problem. When i enter my username and password, the screen changes over like its fixing to load, instead, a black screen briefly says something about desktop login, and then it goes back to the login screen.

---

### Post by HotShotDJ on 2008-05-18
> **tad214 said:**
> Also, i would like to upgrade from 6.06, to 8.04, but i downloaded the cd image and can't find the executable to open it up. Can someone tell me why i can't just upgrade online, and if so, how do i go by doing that?
You can upgrade from 6.06 (Dapper) to 8.04 (Hardy).  See: [http://ubuntu-tutorials.com/2008/04/23/upgrade-ubuntu-606-to-ubuntu-804](http://ubuntu-tutorials.com/2008/04/23/upgrade-ubuntu-606-to-ubuntu-804)

Of course, you'll need to get that login issue sorted first.

---

### Post by tad214 on 2008-05-18
Ok, thank you. i will do that just as soon as i get through this. Thanks again

---

### Post by tad214 on 2008-05-18
Is there anyone that can help me? Or, is this problem unheard of?

---

### Post by Neobuntu on 2008-05-18
Punt.

My recommendation would be to get the correct 8.04 Kubuntu Live CD for your processor downloaded and burned. (this assumes you have 384Mb RAM or better) Test it for errors.

Use it to back up everything you care about in your /home directory. Hey, everyone needs a back up anyway, right?

Install clean. Copy your stuff back into you newly organized /home directory (your preference.)

Continue to add packages you may like. ...Restricted drivers, Media compatibility etc.

This all, is the faster way. Plus you will be on a more common base for fixing any imperfections, that may come along.

This all depends on the hardware set that you have. It's a near miracle how (K)ubuntu just works and on so many differing sets of hardware. Don't freak out if you have to set a preferred CRT resolution (and/or 3D card) to your liking. If you have a special graphics setup, backup your "xorg.conf" configuration file too.

Managed dist-upgrading is great and all but only when it works and leaves nothing else to do. To often, you may simply create a system so far off the beaten path, it's hard to keep up. You may even lose some foundational improvements. For the best foundation remember, clean installing is not the bear; like with Windows.
[B]
Remember. if you are on a mission critical system, you do not have to install over your old partition. You may make room (easy installer) and clean install, into a new one and try it out, without overwriting anything.[/B]

---

### Post by Xiong Chiamiov on 2008-05-18
It doesn't sound so much like a login issue as an issue with video card drivers or some such.  I've heard some KDE users having a similar issue, somewhere in the forums, but not any GNOME people.  Can you do us a favor and install KDE and see if that works?

Press alt+f2 to get to a terminal prompt.  Log in and run
```

sudo aptitude install kde-core
startx

```
If it asks you which display manager to use, choose gdm.  At the login screen, then, go to options and choose a session type of KDE, then log in and see what happens.

---

### Post by tad214 on 2008-05-18
Hi, thanks for the reply. I have the iso image on this windows system, but after i opened and burned it, it does not autorun when i put it in the drive. Also, i can not find an executable file on it to install it either. Any advice on this?

---

### Post by tad214 on 2008-05-18
Thanks. I will try your solution and see what happens. this is a dual boot system, so i will try it and come back and post the results. Thanks again.

---

### Post by Xiong Chiamiov on 2008-05-18
> **tad214 said:**
> Hi, thanks for the reply. I have the iso image on this windows system, but after i opened and burned it, it does not autorun when i put it in the drive. Also, i can not find an executable file on it to install it either. Any advice on this?
How did you burn the CD?  You have to burn as an image file, rather than as a normal data CD.

---

### Post by tad214 on 2008-05-18
I extracted the image, and then burned it. I tried the kde core install, and it got almost through it, and said i was out of disk space. but, i think you may be right, because, several of the programs i downloaded, was kde. That must be the problem. So, im just goin to re-burn this image, and just start all over fresh. Thanks for the help guys!!!!

---

### Post by Xiong Chiamiov on 2008-05-18
Oh, I didn't ask how much disk space you had >.<

Is this a fairly fresh install?  I'm guessing so, since you said you're brand new, even though you have 6.06.  If you've got data and stuff you don't want to lose, there's probably a way to fix it (correction: it's linux; there *is* a way), but reinstalls are always the easiest.  I just don't want you to reinstall if you're losing stuff...

---

### Post by NightwishFan on 2008-05-18
Good luck, and please inform of if you need any more advice.

---

### Post by tad214 on 2008-05-18
Thanks to everyone for the help. I downloaded the 8.04. image, but it doesnt seem to want to boot off the cd at startup. Also, when extracted with iso buster, i cant seem to locate an executable to execute it myself.

---

### Post by NightwishFan on 2008-05-18
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

> Download and install [Infra Recorder]("http://infrarecorder.sourceforge.net/"), a free and open source image burning program. 
Insert a blank CD in the drive and select Do nothing or Cancel if an autorun dialog pops up. 
Open Infra Recorder, and select the 'Actions' menu, then 'Burn image'.
Select the Ubuntu CD image file you want to use, then click 'Open'. 
In the dialog, click 'OK'.

To use live cd, reboot with cd in the drive. Make sure your computer is setup to boot from cd first.
To use wubi, run the wubi.exe file while in windows.

---

### Post by HotShotDJ on 2008-05-18
> **tad214 said:**
> Thanks to everyone for the help. I downloaded the 8.04. image, but it doesnt seem to want to boot off the cd at startup. Also, when extracted with iso buster, i cant seem to locate an executable to execute it myself.You keep talking about extracting iso's.  Why are you doing this?  You must use the Burn Image mode in your CD writing software to make a working, bootable CD from the iso image. A couple things... did you make sure that the ISO image that you download is ok (using MD5SUM).  Also, when you burn the image, try reducing the burn speed down to 4X.  This sometimes helps.

---

### Post by tad214 on 2008-05-18
Cool, thanks. I will try that. I am determined to get my linux up and going!!!! :lolflag:

---

### Post by SunnyRabbiera on 2008-05-18
sometimes it takes experimenting, but dont give up okay?

---

### Post by tad214 on 2008-05-18
Oh no, i **[COLOR="Red"]will not [/COLOR]**give up. I love this ubuntu . I will eventually get it going.:lolflag:

---

### Post by tad214 on 2008-05-18
Well guys, i must have a copy of a bad image. Could someone give me a link to a good 8.04 image download? Thanks

---

### Post by NightwishFan on 2008-05-18
[http://cdimage.ubuntu.com/releases/8.04/release/](http://cdimage.ubuntu.com/releases/8.04/release/)

---

### Post by tad214 on 2008-05-18
Thanks a lot Nightwish.

---

