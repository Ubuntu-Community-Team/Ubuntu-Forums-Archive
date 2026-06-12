---
title: "[SOLVED] Anything Better Than Wine?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by rsnow on 2008-08-12
I realize that my problems with wine are probably due to my inexperience and lack of understanding. However, my initial reaction to wine is that it is primarily meant for gamers. So I would like to find out if there is/are other programs that enable running Windows apps on linux?

---

### Post by perlluver on 2008-08-12
There is Cedega, wine-doors, and you can run Windows in a Virtual Machine.

---

### Post by Thelasko on 2008-08-12
If you decide to stick with Wine, I recommend reading [this page ]("http://ubuntuforums.org/showthread.php?t=497332")beforehand.

---

### Post by Thelasko on 2008-08-12
P.S. what are you trying to run in Wine?

---

### Post by Vorian Grey on 2008-08-12
I just run my non-games in XP in Virtualbox. It works better all around.

---

### Post by chrisod on 2008-08-12
There is also Crossover Office, which is more or less the commercial version of Wine.

---

### Post by TDragon on 2008-08-12
> **perlluver said:**
> There is Cedega, wine-doors, and you can run Windows in a Virtual Machine.
 
 
Keeping in mind that the third option requires you to have a full copy of windows to install in order to get the VM to work.

---

### Post by rsnow on 2008-08-12
I knew I'd get good help here! I've read 'the page' and I can see there is a lot more to running wine than I first suspected.

I was hoping to run some of my Windows photo and video editing programs. I know that Linux has some of their own but being familiar with the ones I have makes me want to keep using them.

I will check out Cedega, wine-doors and Virtual box. 

Thanks to all. I just finished going through Rickford Grant's book, _Ubuntu for Non_Geeks, 2nd Edition_ so I feel a little more comfortable with Linux now.

Any suggestions on a follow-up book?

---

### Post by Thelasko on 2008-08-12
Video editing programs not native to Linux will be difficult.  You will probably lose some performance by running them in a virtual machine, wine, etc.  I'm not saying it's not possible.  But it won't be as fast.

There has been a lot of work done to get Photoshop to work under Wine.  I heard a rumor that Google even provided funding to make it work.  There are guides at[ winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631"), and [some blogs]("http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps").

---

### Post by rsnow on 2008-08-12
Well, I can see that this will not be a short term project. I hope to eventually learn a lot more about these matters. I am not much into gaming so I'll be looking more closely at my other Windows apps as possible candidates for Wine or whatever I decide to use. 

I do not have to force the issue right now as I have one machine for windows and one for Linux. I do not plan to continue Windows beyond XP so I want to prepare for going totally Linux and as far as I can see at the moment, video editing is the only thing that might pose a problem. 

By the time I have to totally drop Windows even video editing in Linux may be on a par with what I'm using now.

---

### Post by Thelasko on 2008-08-13
> I do not have to force the issue right now as I have one machine for windows and one for Linux. I do not plan to continue Windows beyond XP so I want to prepare for going totally Linux and as far as I can see at the moment, video editing is the only thing that might pose a problem.

By the time I have to totally drop Windows even video editing in Linux may be on a par with what I'm using now. 
If that's the case, why use video editing software written for Windows on your Linux machine?  If your Ubuntu machine is just for experimenting/learning at the moment, try a Linux video editor.  As far as I know [Cinelerra]("http://en.wikipedia.org/wiki/Cinelerra") is the most advanced [video editor]("http://en.wikipedia.org/wiki/Comparison_of_video_editing_software#System_requirements") for Linux at the moment.  If you don't like it, you can try messing with whatever you are using in wine.

If your going to be installing Avid in Wine, you will be in uncharted territory.  The [Wine database]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=471") shows that only one attempt has even been made at installing it, likely due to the expense of the licenses. There has been some success at installing [Adobe Premiere]("http://appdb.winehq.org/appview.php?iAppId=128"), but it's limited, and depends on the version.

If this machine is going to be used primarily for multimedia work, you should consider installing Ubuntustudio.  From what I have read here on the forums, I don't recommend installing it fresh from a DVD.  The best way to install it is by packages on top of your current installation of Ubuntu.  [Here are the instructions to do so.]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy")  Note that Cinelerra isn't installed with it, I don't know why.

---

### Post by Thelasko on 2008-08-13
P.S. There appears to be a CMYK plugin (possibly more than one) for GIMP.  If that's what's holding you back.  [Here's a link]("http://ubuntuforums.org/showthread.php?t=620505") to a forums page discussing it.  Most of the information is in post #6.

---

### Post by rsnow on 2008-08-13
Thanks for the tip and link about Studio. It just so happened that I had the Studio dvd in my hand and was getting ready to install it when I decided to check the forum first. After reading your tip and going to the web site, I followed the instructions and I now have Studio on my Ubuntu machine. I will now be spending my time learning how to use all it has to offer.

---

### Post by Thelasko on 2008-08-14
> **rsnow said:**
> Thanks for the tip and link about Studio. It just so happened that I had the Studio dvd in my hand and was getting ready to install it when I decided to check the forum first. After reading your tip and going to the web site, I followed the instructions and I now have Studio on my Ubuntu machine. I will now be spending my time learning how to use all it has to offer.

Awesome, have fun!

---

