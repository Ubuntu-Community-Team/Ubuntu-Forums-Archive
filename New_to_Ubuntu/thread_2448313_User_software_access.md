---
title: "User software access"
date: 2020-08-05
forum: New to Ubuntu
---

### Post by t-sofre on 2020-08-05
I am new to Ubuntu.  

We had a few old laptops in various states of not working well.  After harvesting from a few I have a laptop that is working perfectly. I am actually using it to type here. (HA!! Throwing Traumatic Brain Injury off the cliff on a mountain highway!!)
  
I installed 16.04, updated, added some software and then added a non-sudo user.

I logged in to see if everything was working and none of the third party software is loaded.  

I am guessing there is a permissions issue or I installed incorrectly. 

I am not sure I am understanding how the installation structure works.  I have read information on users, groups, super users and am missing something obvious. So confused .  . . 

How do I give the new user access to use all loaded software without giving access to add or delete software?

T

---

### Post by Impavidus on 2020-08-05
First: Why 16.04? It's over 4 years old and less than a year from end of life. Better use 20.04 or (if you really want things to be rock solid) 18.04. If the hardware is too weak for 20.04 (hardware requirements haven't changed much), use one of the lighter flavours, like Xubuntu or Ubuntu Mate. And if you now suddenly decide to use 20.04 after all, don't upgrade, but fresh install. It's faster and you haven't done anything yet that could be lost.

What kind of third-party software do you mean? Normally, we install stuff from the official repositories and that should be installed system-wide, so that all users can use it. Have you tried to install stuff manually?

---

### Post by crip720 on 2020-08-05
If you are talking about the third-party software that you are asked if you want it install during installation, most of that are drivers and/or stuff to play DVDs, which you will not see unless take a deep look inside system.  Other third-party software like Chrome should be able to see for all users.  Most software you add after install will not have an icon yet on the desktop.  Just click on top icon on the left side and start typing name of software, can then lock the icon to dash panel.

---

### Post by t-sofre on 2020-08-05
The other machines are 32bit and I started with the most recent and then  went down because it was dragging.  I used 16.04 just to get something  to work.  After that I just  stuck with what worked.  These are the specs for this laptop. It is  probably the only one that can handle 20.04  [https://www.cnet.com/products/hp-pavilion-dv6000/specs/](https://www.cnet.com/products/hp-pavilion-dv6000/specs/) The memory isn't  the same. I am not sure if it could handle 20.04

Zoom, ESET NOD32, some alternative PDF/scanner software ... not major stuff ...

---

### Post by t-sofre on 2020-08-05
The software installations were from either the source like Zoom,  I used the terminal for some installs and GUI for others after downloading .deb files. 
OH do you mean log into the the new user and then lock.  Okay ...  I'll do that on the 32bit

---

### Post by t-sofre on 2020-08-05
Just realized I did not answer you about installations ... some were manual and some were not.

---

### Post by Impavidus on 2020-08-06
That laptop isn't exactly a powerhouse, but it's 64 bit so it should handle 20.04. If it has somewhere around 2GB of memory, I'd use a lighter flavour of Ubuntu. The lightest is Lubuntu, but with 2GB I think that Xubuntu and Ubuntu Mate would work quite well too. These give you a lighter desktop environment, leaving more memory for your applications. You may have to install nvidia proprietary drivers. The best way to do this is by using the additional drivers utility. It can also be done during installation. For 32 bit hardware (that must be ancient), Lubuntu 18.04 is the final option (and the only currently supported one) in the Ubuntu family. It has only 8 months of support left. (Technically, Xubuntu 18.04 also has a 32 bit version still supported for 8 months, but 32 bit hardware must be so old that you'd better use Lubuntu.)

Most of the time, we install software that has been packaged for Ubuntu. Traditionally, these are .deb packages that get installed from the official repository, but you can also use unofficial repositories or stand-alone .debs, with less reliability. These packages get installed by the package manager, which has several front-ends, both GUI and command line. There are some newer package formats, like snap, which I avoid. When you install software that was properly packaged, it will be available to all users.

Some software is not properly packaged. There are no hard rules on installation of such software. It may take an expert to get it properly installed. Avoid it if you're new.

Configuration of the GUI is separate for each user. Could it be that you just didn't find the launcher for an application with the second user, whilst this launcher was already present for the first user? Have you searched for the application as second user? I don't really know what the GUI of Ubuntu 16.04 looked like. I never used it (I prefer Xubuntu) and it has changed for more recent versions.

---

### Post by t-sofre on 2020-08-06
You are right! For a newbie who stumbled through installing 16.04 are the alternatives you referring to relatively similar in process or is it like learning how to ride a bicycle instead of a tricycle?

I have to check and see if I can add to launcher.  I can't remember if I added them to the first user - reflecting ... I may have.  I can figure that out meanwhile explore installing a lighter version. 

The thing is that I am setting it up for relative because they downloaded what I think was a worm on their computer. All the computers starting having problems with firefox having millions of files associated. This system (Ubuntu 16.04) be will an alternative to provide during stay at home order.  While I wait to get it back I can experiment on another computer. Just not sure about the driver part.  I am working working on a Ralink RT5390R issue on another computer and am having the WORST time and stuck with trying to fix on Window 10.  Sorta driver-d out at the moment.

Looking forward to learning enough to have a preference :)

Thank you for helping me learn!  Reading material isn't the same has having someone put it in context.

---

### Post by Impavidus on 2020-08-06
The difference between the various Ubuntu flavours is nothing more than the collection of software that gets installed by default. That includes the entire GUI, so the looks are very different, but under the skin they're all very similar.

---

### Post by TheFu on 2020-08-06
So, I'd install Xubuntu or Ubuntu-Mate 20.04.1 for this relative. These are light, but very usable, flavors of Ubuntu.

To install proprietary video drivers (and some other proprietary drivers), use 
```
sudo ubuntu-drivers autoinstall
```

Setup the system to auto install security patches every week and you should ssh into the system to apply other patches at least monthly. 
```
sudo apt update && sudo apt full-upgrade
``` is all that is needed provided you only install software from the repos.  Manually installed software, outside the repos, requires manual maintenance, so it is to be avoided.

For scanning, I use **gscan2pdf**, but my $55 sheet scanner with autofeed is well supported.

There is very little need for any anti-virus on Linux. The system architecture doesn't allow normal users to harm the OS and because only about 3% of the desktops in the world us Linux, we aren't a target in that way.  Assuming this computer will be behind a typical, patched, home router, it is extremely unlikely to ever get any malware or virus that is typical for Windows users.

Be certain you setup remote ssh access to the system through their router and firewalls. Use a high, non-standard, port.  With that, you can handle any issue that doesn't break the booting or networking on the system without physically going to the computer. It can be extremely secure, provided only ssh-key are used for authentication, strong enough keys are used, and brute force attacks are blocked after just a few attempts. If you live nearby, this might not be necessary, but it can still be useful.  I patched Mom's system at the same time I patched all my systems here via ssh. With ssh, it doesn't really matter if the computer is 2ft away or 15km away.

While you are at it, setup a daily, automatic, backup solution. Something like Back-In-Time works well. Did this for Mom with an external USB disk, just for backup of her most important data files in her $HOME.  Showed her were the backups were placed, how they were organized, that made her very happy that it was all automatic and she didn't need to do anything.  Once a week, I'd rsync her backups overnight to one of my systems. She just needed to remember to leave the computer on overnight. Normally, she'd power it on, go make b'fast, come back, do "computer stuff" for 30-60 minutes, then power it off until the next day. Leaving it on was hard for her.  

BTW, I did all this for my Mom after she was hacked on WinXP around 2010. I can't blame her for being tricked. What great grandma wouldn't click an email with "New Baby Photos" from a great granddaughter who had a baby a few weeks earlier? She never had a chance. ;)

Mom used that system until she died in 2013. I provided remote support from about 400 miles away.  When the old P4 computer died, we swapped the HDD into a Core i7. Mom didn't really notice the difference, since it was running a lite-Ubuntu already. To make me feel better, she did say it seemed "a little faster." I doubt she really noticed. Lubuntu 10.04 was an excellent OS. I miss it.

---

### Post by grahammechanical on 2020-08-07
I think that all the flavours of Ubuntu use the same installer. At least they did when I tried out different flavours some years ago. So, the screens you saw when installing Ubuntu you will see again when installing Xubuntu. The colour scheme will be different. The method and information required will be the same.

I installed Zoom Client for Linux from the Zoom web site. It was an old version without some of the better security features of the later versions. Since then I have installed the snap app version of Zoom Client. It is at version 5.1.4 having had several updates since I installed it in March.

[https://snapcraft.io/docs/installing-snap-on-xubuntu](https://snapcraft.io/docs/installing-snap-on-xubuntu)

You can install Zoom-client snap from here.

[https://snapcraft.io/zoom-client](https://snapcraft.io/zoom-client)

Regards

---

### Post by t-sofre on 2021-03-22
I know this is an old post.  I just wanted to thank you all for the input and guidance.
I have pretty much converted most of the family machines over to Linux. 
The older machines like the ones was asking her are 90% better with Xubuntu.
Some of the machines were getting forced updates from Windows despite having auto-updates disabled - rendering the machines practically useless - sitting waiting upwards of 5 minutes for an application to open. After experiencing this they understand what I have been grumbling about for the past 15 years.   

I should have made the switch sooner!! Thankful for being able to find forums like this!!!

---

