---
title: "Looking, but..."
date: 2013-05-28
forum: New to Ubuntu
---

### Post by byroniczero on 2013-05-28
Hi.  I found my way over from the Ubuntu website.  I hope this is the right place to ask this question.

I'm looking around at Ubuntu, and I tried the virtual tour, and I like what I see.  I'm currently running a late 2011 MacBook Pro 15", upgraded to OS X Mountain Lion.  I love my Mac, and I have no issues with it at all...but I like the look of this new Ubuntu, and I'm itching to give it a spin.  

My dilemma is this:  why should I give up OS X for Linux?  I don't want to touch off any angry debates or anything, I'm just trying to ask an honest question.  From what I've seen, Ubuntu looks good...but so does OS X.  Mac and Linux share a Unix core from what I understand, so a lot of the security benefits are present in both systems.  

I just want to know, I guess, if I'm missing something about Ubuntu, a decision-maker, a game-changer...something like that.  The tour looks nice, but I've only got about 10GB free on a 120GB SSD, and I wouldn't want to try partitioning my drive anyway.  Is there a way I can give it a shot inside of OS X?  

Thanks for the input.  I really hope I don't touch off any Mac vs. Linux arguments...I'm just a guy looking for the best computing experience he can find.

---

### Post by squakie on 2013-05-28
First off forgive me but I don't know mac's, so if I say something stupid that would be why.  I doubt 10gb is enough to really try out much.  Perhaps you could try the livedvd (if that works on a Mac).  Perhaps a USB flash install with persistence?  They wouldn't be as fast as being on hard disk, but you could look at it and do a test drive that.

---

### Post by Irihapeti on 2013-05-28
You don't need to give up OSX for Ubuntu. Lots of people run Windows and Ubuntu, so I imagine the same is possible for a Mac. Assuming a Mac can be made to boot off an external USB drive, you could install Ubuntu on that.

---

### Post by HermanAB on 2013-05-28
Howdy,

I'm a Mac user too.

I suggest that you install Virtualbox from the Oracle web site and experiment with Linux in virtual machines.  Here is a direct link to the installation image for Mac [http://download.virtualbox.org/virtualbox/4.2.12/VirtualBox-4.2.12-84980-OSX.dmg](http://download.virtualbox.org/virtualbox/4.2.12/VirtualBox-4.2.12-84980-OSX.dmg)

The Mac and Linux OS are almost exactly the same.  Both have very good performance and a virtualizer will allow the guest system to run at almost native speed.  I usually have both Linux and Windows virtual machines going at the same time on my Mac and switch between applications all the time.

[http://www.aeronetworks.ca/2013/05/virtualbox-ubuntu.html](http://www.aeronetworks.ca/2013/05/virtualbox-ubuntu.html)

---

### Post by mastablasta on 2013-05-29
just one thing to add Linux is Unix like OS while Mac OS is really derived from Unix.
Closer to Mac OS might be FreeBSD. And ofcourse Darwin OS

anyway this is not really important for end user. i second virtual box. i have it in windows to run Xubuntu in it. Install needs at least 8GB hard disk, but you can also just boot into live OS (select try it on boot) in virtualbox using the iso file.

yet another virtualbox install guide with pics: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by byroniczero on 2013-05-29
Thanks for all the replies. I tried it out in virtualbox as suggested and there were some serious lagging issues. Maybe I just didnt have virtualbox configured correctly, but my Mac has a quad core i7 and 8GB of RAM, so I figure its a config issue and not a hardware one. 

I saw a cheap chromebook or something online for like $250. Would it be possible to get one of those and wipe the drive and install Ubuntu?  Or will the new Ubuntu run on older hardware?  

Thanks again for all the help. I'm really glad I didn't start a Mac vs.Linux war. :)

---

### Post by GregA on 2013-05-30
Yes, you could overlay any one of the top 10 or 12 linux distros over the chrome OS, as it's already running a linux kernel.  Or you can get a fairly recent refurbished Dell or any main brand PC that uses the popular Intel chipsets for wireless, graphics and I5 core.   Or another  route is to get a system with Linux pre-installed (and thereby be on a level playing ground with Microsoft or Apple).    If you opt for a refurbished system, try to stay away from a recent system that uses UEFI, Secure Boot as it makes it much tougher to install.

Here's the link for pre-installed systems:  [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

On a final note, one additional reason some Linux users use linux versus Windows or Mac are the restrictions enforced on the users by those companies - - if you're not familiar with that complex and controversial topic, just google Richard Stallman and the Free Software Foundation (free as in speech, not as in beer).

---

### Post by mastablasta on 2013-05-30
> **byroniczero said:**
> Thanks for all the replies. I tried it out in virtualbox as suggested and there were some serious lagging issues. Maybe I just didnt have virtualbox configured correctly, but my Mac has a quad core i7 and 8GB of RAM, so I figure its a config issue and not a hardware one. 



yah it could be since Ubuntu uses 3D acceleration and i am not sure how well that part is supported in vbox. maybe it needs additional setting. you could try 12.04 and then switch to unity 2D on login (same as 3D only no hardware acceleration).

i can't run these new DESKTOP ones since i have single core and can assign only 512MB ram to the OS :-) maybe if i had more ram i could run KDE well. i tried it with debian it ran fine at first but then started to lag. Ubuntu just default to fallback.

hmm, maybe you need to increase ram dedicated to graphics in virtual box and overall ram.
lets say you give it 2 GB overall and then dedicate 512MB to graphics and maybe 2 cores.

i have a cheap 11" netbook with E-450 - bought it for about for 300$ (now they have another E version CPU) and way i haven't installed to it yet, but tried it live and Kubuntu runs circles arround windows7 on it. so i plan to install it later,increase the ram to at least 6 GB (maybe 8GB). can't wait for it. if only i had the time to do it.

---

### Post by byroniczero on 2013-05-30
Well I finally tried the LiveCD out. Everything loaded just fine, except when Ubuntu finally came online my screen brightness and keyboard backlights were maxed out, the battery meter was incorrect (said it was nearly dead when it was nearly full), and the system didn't read my WiFi card at all.  

From what I've read, that's pretty par for the course for Ubuntu...but it didn't lag (anymore than you would expect when running from a CD).  

It froze the system when I told it to restart (from the LiveCD to OS X), but once I forced a hard reboot everything came up fine.  

I like the way it looks, but there seem to be a lot of issues that are hard to justify when I can boot into OS X and everything just works.  

If I ever pick up another Windows based laptop/PC though, I'll be sure to give Ubuntu another try.

Thanks to all who replied.  I appreciate it.  :)

---

### Post by mastablasta on 2013-05-31
> **byroniczero said:**
> I like the way it looks, but there seem to be a lot of issues that are hard to justify when I can boot into OS X and everything just works. 


yeah probably needs some tweaking after install. as for the wi-fi depends on the chip, but often all you need to do is connect with awire to internet and you would be offered to install the wi-fi drivers. they can not be packaged on the DVD image as they are not free.

macOS is made to run on specific hardware like yours. OS also came preinstaleld on the system. if Ubutnu comes preisntalled it will also work with no issues (eg. Dell XPS developers edition, System76, ZaReason...).

and if OS X works fine and does what you need it to do then why change (well other than experiment & learn)? ;)

---

### Post by byroniczero on 2013-05-31
I getcha.  Not bashing Ubuntu.  The fact that Apple made the hardware and software to work together was one of the main reasons I dropped $2,000 on a MacBook in the first place.  Got tired of using stuff that was just thrown together.  

Tweaking I don't mind, and hooking the laptop up to the router wouldn't be a problem at all if I only had to do it once.  Are you sure that's how it works, though?  I'm looking at what you said ("depends on chip", "often", etc.) and wondering.  Is there a way to find out?  

I ask (and to answer your question) because yes -- OS X works great, but I could always run Ubuntu from an external drive or something, right?  I wanna play around with it, want to learn.  OS X and Ubuntu share a lot of similarities (my first thought was that, in a lot of ways, OS X was "Ubuntu, finished") in look and feel...but there are differences, and while I can see a few big, glaring problems with the Unity setup...I like the ideas driving it.  

(Plus, I have about $450 in software (Scrivener, MS Word 2k11, Adobe Fireworks CS5) that I need for work and that are Mac only (at least the versions I have serial numbers for are).)

So is it really difficult to install to an external drive, like a USB flash stick?  

Thanks again for all the helpful replies.  :)

---

### Post by Irihapeti on 2013-05-31
Assuming that the Mac will boot from USB, or can be made to, yes, you can run Ubuntu on an external drive. A flash drive mightn't be the best idea for a longer-term install, because of the wear issues, but just for having a more in-depth look at how Ubuntu behaves on your system, it should be fine.

---

