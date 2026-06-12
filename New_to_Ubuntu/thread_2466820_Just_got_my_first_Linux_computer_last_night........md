---
title: "Just got my first Linux computer last night......."
date: 2021-09-06
forum: New to Ubuntu
---

### Post by linuxnewbie60077 on 2021-09-06
Just got my first Linux laptop last night, it is a dell Latitude D620. It was running 14.4 LTS and I figured out how to get the wifi working by terminal commands and also how to upgrade/update it to 16.4. Figured out how to set up Thunderbird email client, and got it running. I'm wondering if I should try to remember how I got it to upgrade/update to 16.4 and since a friend told me I really should have 18.4 LTS or 20.4 LTS on it upgrade/update it further? If I do that, will I have to set up the email client again, as well as the browser bookmarks or no? So far I like the fact I am not being pestered by microsoft bs with this program has a problem and needs to close or constant update needed messages, but I supposed it would be good to have it running a current version as well.Just wondering if I should have waited to set up the email client and bookmarks in the browser until it was upgraded/updated further?

---

### Post by grahammechanical on 2021-09-06
May I suggest that you now learn how to backup and then restore the email client settings/contacts and the browser book marks? That will remove one worry.

Go to Software & Updates>Updates tab and make sure that Notify me of new Ubuntu version is set for For Long-term support versions. Then when you run Software Updater you may get an offer to update to 18.04. If that does not happen there might be something else you need to do.

When we run a Ubuntu Long Term Support (LTS) version we can directly upgrade to the next Long Term Support version. They are released every two years towards the end of April. So, thinking ahead, there is Ubuntu 22.04 LTS to come next April.

Online upgrades work best when the operating system is in a default state. So, if you are going to work your way from 16.04 through 18.04 to 20.04 then it is best to do so now before you make too many changes and collect documents that you do not want to lose.

I would also suggest that you download an ISO image of Ubuntu 20.04. If the series of upgrades does not work out well then you will already have an install DVD/USB stick with Ubuntu 20.04 on it to do a fresh install.

[https://ubuntu.com/#download](https://ubuntu.com/#download)

[https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-before-you-start](https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-before-you-start)

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Regards

---

### Post by Bashing-om on 2021-09-06
linuxnewbie60077; Hello - Welcome to the Forum

'tis all the better here, me Thinks

Running a End-Of-Life release is a real bad idea for sure.
> 
Ubuntu 16.04 LTS (Xenial Xerus) was the 24th release of Ubuntu. !End-of-life was April 30th, 2021.


If you choose to upgrade - current latest LTS is 20.04:
> 
For upgrading, see the instructions at [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) - see also 
               [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)


The process is painless - with a fast wired internet connection - and "should not"  affect anything in your home directory. Your configs there will remain.

[INDENT]the adventure begins :)
[/INDENT]

---

### Post by oldfred on 2021-09-06
You also may want to consider converting to a lightweight flavor.
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

Dell D620 Mutter bug BIOS system
[https://ubuntuforums.org/showthread.php?t=2401319](https://ubuntuforums.org/showthread.php?t=2401319)

My 2006 laptop used to run full Ubuntu. When they converted to Unity, then it started to run really slow, so converted to a lightweight gui.
Tried 20.04 since they have gone back to gnome, but it would not install. Had to install server version & then the lightweight gui.
Since then converted Desktops to Kubuntu which is more of a mid-weight flavor.
It did install in old laptop which surprised me, and worked ok. Old laptop was never fast.

---

### Post by rsteinmetz70112 on 2021-09-07
Welcome to Ubuntu.

Echoing others upgrade to 20.04 as soon as possible, when I last checked the 16.04 repositories were still on line.  If you wait too much longer they may not be. You will still be able to upgrade but it gets much more complicated.
As noted above check to see if your computer is set to upgrade to LTS versions then do the following:

Open a terminal (Alt Ctrl- T)
At a command prompt:

```
$ sudo apt update
$ sudo apt full-upgrade
$ sudo apt autoremove
$ sudo apt autoclean
$ do-release-upgrade
```

During the upgrade you may be asked a few questions.
Assuming you have a typical desktop installation all of your existing programs and settings should be preserved.

---

### Post by GhX6GZMB on 2021-09-07
> **linuxnewbie60077 said:**
> Just got my first Linux laptop last night, it is a dell Latitude D620. It was running 14.4 LTS and I figured out how to get the wifi working by terminal commands and also how to upgrade/update it to 16.4. Figured out how to set up Thunderbird email client, and got it running. I'm wondering if I should try to remember how I got it to upgrade/update to 16.4 and since a friend told me I really should have 18.4 LTS or 20.4 LTS on it upgrade/update it further? If I do that, will I have to set up the email client again, as well as the browser bookmarks or no? So far I like the fact I am not being pestered by microsoft bs with this program has a problem and needs to close or constant update needed messages, but I supposed it would be good to have it running a current version as well.Just wondering if I should have waited to set up the email client and bookmarks in the browser until it was upgraded/updated further?

Congratulations!

Working with Linux/Ubuntu/whatever is more about _mindset_ than the software itself. I went through this transformation two years ago.

With M$, version upgrades always discard older hardware. You need the newest HW, always. Drivers etc. are no longer available.
Conversely, you can't use older M$ software on newer machines, or only in very limited form.

Those times are over with Linux. That was my big revelation when switching.
When a driver is once in the repository, it stays there. The same with all other HW and software specific stuff.
Eg, Is your laptop 12 years old?
No problem, everything also works with a 20.04 install.
The whole XP, Vista, 7, 8, 10 race is over..

Enjoy your new machine and do not be afraid to upgrade. All the old stuff will still work.

And Welcome to the Club.

---

### Post by kurt18947 on 2021-09-07
I would certainly make a USB installer for 20.04. Going thru the 14.04 -> 16.04 -> 18.04 -> 20.04 upgrades may work but I'd be prepared for glitches just in case. It really doesn't take long to do a clean install; what takes me the time on a new install is getting the extensions and settings as I like them. Be sure to back up any data - documents, photos that sort of thing - on a regular basis. Something else you might consider before you get too far along. I presume your Dell has a conventional hard drive. If so, you might consider an SSD if it fits your budget. An SSD can make an older machine feel much faster. Certainly you don't NEED an SSD but it makes an older machine feel young again.

---

### Post by linuxnewbie60077 on 2021-09-08
I likely will try to upgrade when I get home, 16.04 works good on it, but being end of life, it is better to be current.

---

### Post by kurt18947 on 2021-09-08
> **linuxnewbie60077 said:**
> I likely will try to upgrade when I get home, 16.04 works good on it, but being end of life, it is better to be current.

Yes it is. One of the differences between Windows and Ubuntu is that Ubuntu or any Linux distro responds to security issues by patching the underlying flaw rather than relying on antivirus and the like. Once a distro is out of support those flaws are public knowledge but are no longer patched. That  to me is the biggest reason to use a currently supported version. Windows also has to be careful that any patch doesn't break too many applications. There are 16 zillion Windows apps out there, 8 zillion of which are old & unsupported, poorly written/easily broken. I don't envy the people responsible for Windows security and patches. 

Another reason is hardware support. Windows you usually download drivers to support newer hardware. Any hardware vendor is going to support Windows. The same is not true of Linux. Generally hardware support is provided by the kernel. Newer kernels are more likely to support newer hardware. This is certainly true of AMD CPU and GPU support. Older distros didn't work well with newer Ryzen CPUs or GPUs. You have a machine that's been around for a while. In the Linux world that's a good thing.

---

### Post by linuxnewbie60077 on 2021-09-09
Well, I managed to upgrade the laptop to 18.04 and it seems to have went smoothly, it seems to be working the way it did on 16.04, course only have used it for a couple hours after the upgrade. I'll put it this way, it hasn't acted stupid yet so that is a very good thing. debating if I want to keep it on 18.04 for a day or two or push my luck and go for 20.04 tonight....

---

### Post by rsteinmetz70112 on 2021-09-12
Congratulations.

You have plenty of time to decide when to upgrade, probably best not to push it.
In the meantime keep things simple and don't install any software not in the Ubuntu Repositories, that will make upgrading later riskier.

---

