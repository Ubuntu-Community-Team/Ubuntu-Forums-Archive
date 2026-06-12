---
title: "Problem removing pre-installed apps from Lubuntu desktop"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by WorBry on 2013-02-27
I've just recently started using Lubuntu. 

The first time I installed the 'minimal' system (from 'Minimal CD) and then installed the Lubuntu desktop on top. At that time I had no problem removing certain of the pre-installed applications (Pidgin, Penguin games etc) that I did not particularly need.

In the process of attempting to resize some partitions (evidently the wrong way) I messed up and decided to start over (new partition table) and re-install the full system. 

This time I installed Lubuntu directly from the Lubuntu ISO 'Live' CD.  All went fine except that now I find that whatever pre-installed application I mark for removal with Synaptic Package Manager (whether Removal or Complete Removal)  it always lists the 'Lubuntu desktop' as one of the co-dependency packages that will be removed as well. So obviously, not wanting to lose the desktop, I have refrained.

I'm trying to think of what could have made the difference.

I don't know if it's relevant but when I first installed the desktop on top of the minimal system I used the command as instructed in the Lubuntu minimal install guide:

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

```
sudo -i 
apt-get install lubuntu-desktop 
apt-get dist-upgrade 
apt-get autoclean 
rm /var/cache/apt/archives/*.deb 
reboot
```Whereas when I did the full install from the 'Live CD' I just did a software upgrade from the desktop using Software Updater. No command lines or anything. 

So I'm wondering if there is some 'clean-up' operation that would resolve this? Otherwise, if it's not possible, I'd be inclined to re-install again using the 'minimal method'.

Edit: Just ran : 

```
apt-get autoclean 
rm /var/cache/apt/archives/*.deb
```

to see if it made a difference, but not.

Edit 2: Also now run: 

```
apt-get clean
apt-get autoremove

```

plus

Removed any Not Installed (residual config) entries, with Synaptic Manager - there was one
Removed any orphaned packages with GtKOrphan - there was just one

Hope I didn't do anything wrong there (other than a thorough clean-up), but again it made no difference. 

So, I thought, what the heck, went ahead, marked one application (Gnome Mplayer) for complete removal. Applied it expecting the desktop to disintegrate before my eyes. But apparently not.  Not only that, on marking other pre-installed applications for removal 'Lubuntu desktop' no longer appeared as a co-dependency for removal, only the specific application dependencies? 

A relief, but what was that all about??

---

### Post by DuckHook on 2013-02-28
One of the oddities of all the 'buntu flavours is that it is, in fact, okay to remove the so-called 'buntu Desktop. This action won't really harm your desktop. The reason is, this name does not actually refer to the individual apps that make up your desktop environment, but rather, only to the metapackage that lists what all of those apps are as a collective. If you remove even one of those apps, the collective is broken and the metapackage (or listing) is no longer valid. Hence, it can be and even should be removed.

The useful thing about this methodology is that if you ever want to reinstall all of the apps that make up a default desktop environment, all you have to do is reinstall the metapackage. This will drag in all of the previously deleted apps needed for a standard default desktop.

---

### Post by DuckHook on 2013-02-28
By running *autoremove*, the "Lubuntu Desktop" metapackage would have been deleted. This is why you are no longer seeing it.

---

### Post by WorBry on 2013-02-28
OK thanks. That explains it. Interesting. So, on that basis it would be reasonable to assume that the "Lubuntu desktop" as applied (by download) to the installed 'minimal' Ubuntu system does not feature a collective 'meta package' of applications as such. Not a big deal either way, but that's useful to know.

---

### Post by DuckHook on 2013-03-01
> **WorBry said:**
> ...it would be reasonable to assume that the "Lubuntu desktop" as applied (by download) to the installed 'minimal' Ubuntu system does not feature a collective 'meta package' of applications as such.No, it's the other way around. After you install Ubuntu minimal, you have a minimal command line environment. If you then subsequently install Lubuntu Desktop, you *are* installing a Metapackage (named Lubuntu Desktop) which is a big package of all the smaller packages that make up a default Lubuntu Desktop. Think of it as one of those do-it-yourself kits where a big box of computer parts is dropped off at your door. Inside are smaller boxes containing the actual individual parts. You can buy the parts separately and build exactly the same computer. But the kit is easier because someone has collected all of the needed parts together in one box for you.

What is confusing you is that you thought removing "Lubuntu Desktop" would throw away the computer. In fact, it just throws away the big box. This is really stretching the analogy, but it gets the main idea across. The confusion arises because the phrase "Lubuntu Desktop" is being used in two different and unrelated ways:

1. It refers to the GUI that is running on your computer, and
2. It is also used for the metapackage of apps used to create that GUI.

The two terms don't refer to the same thing. By throwing out the metapackage, you are not throwing away your GUI.

---

### Post by vasa1 on 2013-03-01
> **DuckHook said:**
> ... The confusion arises because the phrase "Lubuntu Desktop" is being used in two different and unrelated ways:

1. It refers to the GUI that is running on your computer, and
2. It is also used for the metapackage of apps used to create that GUI.

The two terms don't refer to the same thing. By throwing out the metapackage, you are not throwing away your GUI.
Nicely put :)

Here are a couple of links:
[http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop)

---

### Post by WorBry on 2013-03-01
> **DuckHook said:**
> No, it's the other way around. After you install Ubuntu minimal, you have a minimal command line environment. If you then subsequently install Lubuntu Desktop, you *are* installing a Metapackage (named Lubuntu Desktop) which is a big package of all the smaller packages that make up a default Lubuntu Desktop. 

I understand the concept, but when I first installed the Lubuntu desktop (package) on top of the 'minimal' system and came to uninstall certain pre-installed applications in Synaptic Manager it only listed the specific dependencies for the particular application that would be removed. It was only when I did a clean sweep re-installation from the Lubuntu 'Live' CD and went to uninstall applications that the 'Lubuntu desktop' was lshown as a dependency that would be 'removed' along with the application. Surely, according to what you are saying it would have been the other way around then? 

Either way, it appears that no harm was done, which was my principal concern.

---

