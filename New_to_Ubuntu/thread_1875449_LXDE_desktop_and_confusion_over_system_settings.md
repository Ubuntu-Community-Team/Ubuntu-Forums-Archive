---
title: "LXDE desktop and confusion over system settings"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by palloy on 2011-11-04
With 20 years experience on Windows, this was my first foray into Linux.
From Win 7 I downloaded Ubuntu 11.10 32-bit,
and set it up on a bootable USB stick and installed OK.
Then the first thing I encountered was the ghastly launcher.
Whoever thought that one up must be built differently to me.

So I started looking for an alternative desktop that was more Windows-like,
and located at the left of my wide screen where there is acres of space,
and that was LXDE, which installed OK.

Next the need was for a decent file manager, I chose Dolphin, which is part of KDE4.
You can perhaps see where this is going -
some later changes I made to desktop/windows features just didn't show up
or only lasted till the next restart.
Things that were present were reported as being not found
and I became hopelessly confused and felt I must have stuffed things up
so I decided on a clean install.

Something was wrong with the USB stick configuration,
so I decided to download Wubi which downloads the installation package again.
Little did I realise that I was getting the 64-bit version -
I have a 32-bit CPU (Intel E6300) but it has extensions to handle 64-bit instructions
and Wubi decides to take advantage of that.
It would be nice if Ubuntu would announce this on the initial screen.

So I went through the desktop changing business again
and ran into exactly the same problems, specifically:

1.  The System Settings window now has less icons than it did.
One that has definitely gone missing is Sound.
The Sound icon that I put on the Application Launch Bar of LXPanel
now launches System Settings, not Sound.
Gnome-sound-panel.desktop does the same thing.

2. The Startup Applications icon launches the window 
and has AutoKey-GTK and KNemo in it,
but they don't launch at session startup.
The path the for the items said the apps were in /usr/share/applications/*.desktop
so I changed that to /usr/share/applications/kde4/*.desktop
which is where they really are, but they still don't launch.

3. There are numerous apps for changing windows' appearance,
but most don't actually change anything,
and for some the changes don't stick.

I hope you get the picture.
I mustn't have grasped something basic about desktop environments.
It would be good if there was an explanation of the basic Ubuntu system file structure
and how changing desktops affects this.
Unfortunately the keywords are so general that searching turns up everything.

---

### Post by wojox on 2011-11-04
If you want something close to windows, install Kubuntu. As for the file system just learn Linux. They are pretty much all the same.

---

### Post by palloy on 2011-11-05
Thanks for that.
Do you have a link for "just learn Linux" ?
Let me guess - Google it.

---

### Post by matt_symes on 2011-11-05
Hi

Sounds like you want something *really* close to Windows.

Just install Windows.

My current phone work completely different from my last phone and is almost unidentifiable from my phone 5 years ago.

We adapt to change all the time with other technologies and don't blink an eyelid. 

It must also happen on the desktop and is happening on Linux and well as on Windows (Metro interface....)

That comfy pair of slippers are old and thread bare. They can only be darned so many times.

Kind regards

---

### Post by wojox on 2011-11-05
> **palloy said:**
> Thanks for that.
Do you have a link for "just learn Linux" ?
Let me guess - Google it.

[URL="http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/"]Linux Filesystem Hierarchy
[/URL]

---

### Post by Script Warlock on 2011-11-05
ok and you want windows like then install ylmf..

---

### Post by amjjawad on 2011-11-05
> **palloy said:**
> With **20 years** experience on Windows, this was my first foray into Linux.


Hello and Welcome to an entirely new world.

Your first link that you need to start reading is:

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

_**Section G**_**[COLOR=RoyalBlue] (Useful Links)[/COLOR]**

[LIST=1]
[*][Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")
[/LIST]

---

### Post by anewguy on 2011-11-05
If you're trying to do this on a bootable USB stick, did you use something like unetbootln to create it?  I guees what I'm getting at is this:  if you created a USB stick to act like the LiveCD, it will not have persistence.  So if you make changes, etc., then reboot, you'll lose those changes.  You must make it a persistent USB install.

This of course only if you're still trying to run Ubuntu from a USB stick.

Also, be aware that Wubi is meant at best to be just for a test-drive before actually installing Ubuntu in some fashion (stand-alone or dual-boot).

I know people don't like to hear "google it", but you'd be VERY amazed that many of the replies posted here come from doing search-engine searches and reading through all the material.  Sometimes it takes a little from A, a touch from B and maybe a dash of C to realize the problem is X.  Google/Yahoo!/Bing, etc., really are ones best friends here.

Also, if you are trying out Ubuntu and you have enough hardware power, run something like VirtualBox in Windows and create a VM with Ubuntu in it.

Dave ;)

---

### Post by palloy on 2011-11-05
Thanks for [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/) ,
that's one to bookmark for sure.

I don't understand the passive-aggressive over wanting something that suits my needs.
I am very happy with LXDE's LXpanel (see attachment).
I don't want to give up and go back to Windows,
and I don't want to give up on Ubuntu after a weeks' work and try Kubuntu/Lubuntu.

Its just that something seems to affect the number of icons in System Settings after I load it.
Is there a filter on which icons show according to which desktop I have ?
Where is that folder in the standard Unity layout ?
Is it a different folder when LXDE is the desktop ?
Are these the wrong questions ?
Help me out, please.

---

### Post by Script Warlock on 2011-11-05
thanks for cooling down... :)

---

### Post by matt_symes on 2011-11-05
Hi

> I don't understand the passive-aggressive over wanting something that suits my needs.My comments were not intended to be aggressive (passive nor otherwise) in any way. 

I  was merely highlighting the fact that all desktops are changing and  that you have moved to a new OS as well as a desktop environment. You  have to expect some changes.

As for Lubuntu  suiting your needs, amjjawad knows Lubuntu very well and should be able to help you along with a whole host of other people.

I only suggest that Linux may not work in the exact same way Windows did.

I hope you get answers to your problems.

Kind regards

---

### Post by Zill on 2011-11-05
palloy:  The best advice I can offer is *not* to mix up apps from different Desktop Environments.  Trying to get bits of Gnome, LXDE and KDE to work properly together can be a challenge, even for experienced Linux users!  Just install the OS/DE of your choice, then stick to just the apps for that DE and you will avoid a lot of problems.

Remember that you don't need to actually *install* a Linux OS to your HDD to try it out - most are "Live" CDs allowing you to test the distro without installation.  Similarly, although WUBI installs might seem useful, IMHO these are basically just for test purposes and a "real" installation to the HDD is best to run a Linux system properly.

As your experience builds, you will learn the various "wrinkles" needed to use different apps - but this will take time and effort.

amjjawad gave good advice and you really should take the time to read the link [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm").

---

### Post by amjjawad on 2011-11-05
> **Zill said:**
> Remember that you don't need to actually *install* a Linux OS to your HDD to try it out - most are "Live" CDs allowing you to test the distro without installation.  Similarly, although WUBI installs might seem useful, IMHO these are basically just for test purposes and a "real" installation to the HDD is best to run a Linux system properly.

Plus you can install to an USB Drive and in that case, your system will remain untouched.

I have two guides for that, both are on my thread. One is:
How to avoid Wubi and install Ubuntu to USB Drive
and the other one is
How to install Lubuntu to 4GB USB Drive.

---

### Post by palloy on 2011-11-05
>  Trying to get bits of Gnome, LXDE and KDE to work properly together can be a challenge, even for experienced Linux users!Ah, that seems to be the source of my confusion.
Since Ubuntu Software Center offers all kinds of packages, 
and sorts out all the dependencies,
I imagined I could forget about those low-level intricacies.

I'm going to have to have a think about this.
(I don't suppose there's such a thing as Compatibility Mode, is there?)

---

### Post by dFlyer on 2011-11-05
Just my 2 cents. Don't know much about windows anymore, I haven't use it in many years. I can assure you that linux is very stable and easy to learn if your willing to take the time. Ubuntu is a great distro and I've stuck with it since version 6.06. I believe the first thing a person has to understand is that linux is not windows, nor should it be. All you need to do is go slow, have fun and use of the search function in this forum which should answer 99% of your questions, the other 1% can be found on google or another search site. If by chance you can't find the answer, I'm fairly sure if you post to the forum providing as much information about your problem your having including error messages, someone will help you fix it.

---

### Post by Zill on 2011-11-05
> **palloy said:**
> ...Since Ubuntu Software Center offers all kinds of packages, and sorts out all the dependencies, I imagined I could forget about those low-level intricacies...
Ubuntu Software Center offers all these packages because all the Ubuntu based distros, including Lubuntu (LXDE) and Kubuntu (KDE) and Xubuntu (XFCE) use the same base packages.  However, each variant uses its own menu structure and custom configurations which makes it difficult to integrate apps from a different variant.

A further complication is that each variant uses some different libraries to the others.  This means that, while your chosen default DE installs, for example, all the Gnome libraries, if you then wish to install a KDE application (eg. Dolphin) then many of the KDE libraries will also need to be installed as dependencies.  If you add LXDE applications as well then even more libraries are required.

Fortunately, the apt-get package management system (used by all Ubuntu distros) ensures that all the libraries required will be installed automatically.  However, the downside is that your system will be clogged up with many more libraries than would be installed than if you stuck to apps from your default DE.  These all take up disk space and lead to an unnecessarily bloated filesystem that needs to be maintained with future updates.

Regarding "Compatibility Mode", a quick Google search reveals that this seems to be a Windows thing and, as such, I doubt you will find it on Linux systems. ;-)

---

### Post by amjjawad on 2011-11-05
> **Zill said:**
> A further complication is that each variant uses some different libraries to the others.  This means that, while your chosen default DE installs, for example, all the Gnome libraries, if you then wish to install a KDE application (eg. Dolphin) then many of the KDE libraries will also need to be installed as dependencies.  If you add LXDE applications as well then even more libraries are required.


That is exactly why (main reason) I always advise the users to go for Clean Fresh Installation and NOT to just install the Desktop Package.

Couldn't agree more :)

---

### Post by Kevin McCready on 2012-03-26
Re mixing aps, my experience is the opposite. I installed Lubuntu, found it needed tweaking and so started to delete packages and install the ones I wanted with apt-get. Nothing could be simpler.

I ran it on an old slow laptop and the library bloat spoken about wasn't a problem. It DID take a long time to download Dolphin but I am very happy with it. The biggest drawback is actually PCManFM which is as slow as a dog opening files from a large directory. I end up finding the file with Dolphin and opening it from there.

---

