---
title: "upgrade"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by sean neilan on 2012-11-17
I have Ubuntu 10.04 and I want to upgrade to 12.04 but I'm afraid if I do that things can go wrong. I'm not that good at this computer stuff and I am really comfortable with what I have so if anyone has advice for a beginner that would be great thank you for your time.

---

### Post by Aaron Christianson on 2012-11-17
The best way to upgrade is always to back everything up on an external drive and install a fresh system with a usb stick (there are good instructions for this elsewhere, and it is very easy). [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

When you install a fresh system, you get rid of all the old files which might cause weird things to happen and generally gunk-up your computer (geeks refer to this as cruft. Cruft has a more broad definition, but this is definitely a form of it).

However, if you do not want to do this, the upgrade should theoretically take care of itself without major problems. It isn't much different from a normal update, except that it is doing a whole lot of packages rather than just a few (and changing the package sources, but don't worry about that). You should still back everything up on an external drive before you do this, just to be safe. Of course, you should always back up all important data regularly.

It can cause problems, but that is the nature of computing. Most of the time, upgrading from one release to another is not a huge problem. If you encounter something, the forums are always here.

---

### Post by deadflowr on 2012-11-17
Well backup all your files, cause unlike other upgrades, this one is a major game changer.
Because the difference between 10.04 and 12.04 is so gigantic, I would strongly recommend downloading a fresh copy from Ubuntu.
This way you can test drive it, and see what exactly is so different.
Unfortunately, the changes might not be to your liking, so I would also point you toward sibling distributions, like

[Lubuntu]("http://lubuntu.net/")

[Xubuntu]("http://xubuntu.org/")

[Kubuntu]("http://www.kubuntu.org/")

---

### Post by 3rdalbum on 2012-11-17
My theory is that upgrades work better when your Ubuntu is as close to "normal" as possible. If you don't feel like you're very proficient with Ubuntu, your Ubuntu is probably very close to default, and an in-place upgrade will work just fine.

If you've really hacked around with it under-the-hood then you might run into problems.

What's the worst that can happen? Your data will still be accessible, you'll just need to reinstall Ubuntu. That takes twenty minutes.

I think **it'll all work out fine for you**, but even if the upgrade is a failure you can still just do a fresh install of Ubuntu 12.04. **Make sure you have a 12.04 CD already**, just in case.

Just another note, too: Ubuntu 12.04 is two years newer than 10.04 and there are a lot of major changes. These shouldn't cause problems with the upgrade, but you'll need some time to familiarise yourself with the differences. For a start, the graphical user interface is almost totally different. Much more modern. I like it, not everyone does, but if you stick with it for a week or so you'll probably not want to go back to 10.04.

---

### Post by monkeybrain2012 on 2012-11-17
Why not just save your data and do a clean install. Upgrade is problem prone when you have several intermediate releases to go through and the change from 10.04 to 12.04 is quite drastic. Moreover, even if it works (which you can't know for sure until later) it takes a very long time as oppose to about 20-30 minutes to install from scratch and maybe another half an hour to reinstall your programs (you can restore your settings if you back up your /home folder and transfer the relevant configuration files to your new install, or if you have a separate /home partition you can just delete the outdated configurations before you do a reinstall)

All the upgrade doubts, questions and headaches afterwords are easily avoidable. :)

---

### Post by crip720 on 2012-11-17
Hi  I just did a clean install of 10.04, then an upgrade to 12.04.  It did not work so well.[see post on upgrade problem]  I would recommend backup plus a clean install to be safe.  Good luck, Colin

---

### Post by sean neilan on 2013-03-22
Where would I get a disk of Ubuntu 12.04 so I can do a clean install? I called around to Fry's and to Micro center and they don't have it so what can I do, I believe that I'm not proficient enough to down load it from the software center here in the community.

---

### Post by ManamiVixen on 2013-03-22
If you must buy a copy and cannot make your own, you will have to buy it from Ubuntu's shop. But it will not be cheap as it will be shipped from the UK. Also, it will only be 32bit and unfortunately you cannot buy a legit copy of Ubuntu anywhere else.
[URL="http://shop.canonical.com/index.php?cPath=17"]
[http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)
[/URL]
But making your own disk isn't hard go here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) pick 12.04 or 12.10, then when downloaded use a disc writer to write the ISO to a blank CD for 12.04 or a blank DVD for 12.10.

---

### Post by sean neilan on 2013-03-23
Thanks for the information, my laptop is set up as a 32-bit unit I have a Acer 5742 when my friend put Ubuntu 10.04 he made it a 32 bit how I don't know but he did. Will you be able to assist me if I do up-grade to 12.10 but I took the tour and there it tells me that I have to install 12.04 first then I can install 12.10 is this correct? Also I tried to put 12.10 on and I stopped my self when it told me that I would lose 38 plug ins and I know that those control certain things like my e-mail, my getting on to the web, my writing programs. So my question to start is how would I back up my system I know how to get to the command screen if that is what I need to do but would I have to go through all the software that I do have installed and re install those programs? you see I'm such a beginner and I do need the coaching and the friend that put on 10.04 I can't find and I LOVE Ubuntu the ease of it, the way it is so fast, and it never fails me ever, so if you would can you please help me??

---

### Post by deadflowr on 2013-03-23
> **sean neilan said:**
> Thanks for the information, my laptop is set up as a 32-bit unit I have a Acer 5742 when my friend put Ubuntu 10.04 he made it a 32 bit how I don't know but he did. Will you be able to assist me if I do up-grade to 12.10 but I took the tour and there it tells me that I have to install 12.04 first then I can install 12.10 is this correct? Also I tried to put 12.10 on and I stopped my self when it told me that I would lose 38 plug ins and I know that those control certain things like my e-mail, my getting on to the web, my writing programs. So my question to start is how would I back up my system I know how to get to the command screen if that is what I need to do but would I have to go through all the software that I do have installed and re install those programs? you see I'm such a beginner and I do need the coaching and the friend that put on 10.04 I can't find and I LOVE Ubuntu the ease of it, the way it is so fast, and it never fails me ever, so if you would can you please help me??


If by upgrading to 12.10 through the network, then yes you'd have to be have 12.04 installed.
If you're doing a fresh install of 12.10, then upgrading from 12.04 is not needed.

Do you know what 38 plugins were going to get "unplugged'?

Something about backup:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by MoebusNet on 2013-03-23
I would like to recommend trying out the new version of Ubuntu from Live-CD/DVD or Live-USB before you attempt an upgrade. Running from Live-CD/DVD or Live-USB will confirm your hardware compatibility with your desired new Ubuntu version without making changes to your hard drive. It will also allow you to see the User Interface that you will be using once you have upgraded.

[http://www.ubuntu.com/download/help/try-ubuntu-before-you-install](http://www.ubuntu.com/download/help/try-ubuntu-before-you-install)

VERY IMPORTANT: Back up any data that is important to you before running a Live-version or attempting an upgrade. If things go wrong, at least you won't lose your data.

---

### Post by sean neilan on 2013-03-23
No it didn't tell which ones how can I found out which ones, or should I go through all my plugins and copy those by hand to make sure I install the correct ones with 12.04 and 12.10?

---

### Post by ManamiVixen on 2013-03-23
What exactly are these "plugin-ins" you have? What do they do. That can help us alot here.

---

### Post by sean neilan on 2013-03-23
When I thought about doing the upgrade to 12.10 from my update manager and when I got to the last screen and that is when it told me if I press the last enter button that it would be to late for to go back to what I system I was operating and that is it told me that I would lose my plug-ins but it did not specify which ones. Is there a way that I can find out or do I have to go the Software center and find which ones I do have by seeing if they are installed or not?

---

### Post by sean neilan on 2013-03-23
Also I just read that 12.04 will be supported for 5 years and that 12.10 is only supported for 18 months why is that and is this important for a beginning user like me?

---

### Post by oldos2er on 2013-03-23
12.04 is a Long Term Support release, 12.10 isn't. See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) and [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by Sef on 2013-03-23
Best to clone your system with [Clonezilla]("http://clonezilla.org").  That way in case the install goes bad you can reinstall your original os.

---

