---
title: "How persistent is persistence ?"
date: 2013-12-21
forum: New to Ubuntu
---

### Post by hitsware on 2013-12-21
If I run 12.04 from a USB stick, and add some apps ......
And then use the USB stick to install 12.04 on another
PC (with no internet) ......
Will the apps be in the HD installation on the second PC ?

Thank You,
Michael Miller

---

### Post by grahammechanical on 2013-12-21
I do not expect that to happen. Any install of Ubuntu, whether from DVD or USB stick, will install the default applications. Those applications that you install on the USB stick will not be in the install scripts of Ubuntu. That is my opinion.

I guess to do what you want you would have to create a customised Ubuntu ISO image according to your needs and install that on the USB stick. That is possible but I cannot advise on how to do it. I can see that such a customised Ubuntu ISO image would be useful to a business that needed to have Ubuntu installed on many machines. But I wonder if putting in a default install of Ubuntu and then using Software Centre to add/remove applications as necessary is not more simple. I guess it depends on how many repeat installs are needed.

Regards.

---

### Post by JeQhdMD on 2013-12-21
I wonder if it's possible to use the command line or an app like "Synaptic" to add/enable a new repository listing the USB Flash Stick as a source?   Perhaps using the PPA add process - so the new software would be available to be accessed and installed locally.   

Also, the standard install should already include Qdebi, or Gdebi so installing deb files _already downloaded_ should be easy . . . . if not, why not?

---

### Post by hitsware on 2013-12-21
> **JeQhdMD said:**
> I wonder if it's possible to use the command line or an app like "Synaptic" to add/enable a new repository listing the USB Flash Stick as a source?   Perhaps using the PPA add process - so the new software would be available to be accessed and installed locally.   

Also, the standard install should already include Qdebi, or Gdebi so installing deb files _already downloaded_ should be easy . . . . if not, why not?

I've tried copying the .deb files onto the stick and then installing them (with the package manager), 
but I get a 'source not trusted' type message.
Even dpkg -i doesn't seem to work (though I need to explore that further) ..... 
"Qdebi, or Gdebi" ? Would you elaborate on those please ?
Ubuntu does really seem 'cloud' oriented ..... Maybe all Linux is ? Thanx for the help !

---

### Post by JeQhdMD on 2013-12-21
If you're running Ubuntu, then use Gdebi, if using KDE via Kubuntu (a more MS-Windows like desktop) - then use Qdebi.  These are programs designed to install "stand-alone" debian packages.  I would suggest you try these first before looking into dkpg (which is the package install system back-end).

But, I'm pretty sure another method would be to add a "local source" as a repository - - perhaps someone else here on the boards can advise if adding a PPA (personal package archive) is feasible in this scenario - - there is a way to add the security credentials to a local archive so you won't get the untrusted source error message.  Some package manager allow you to override that warning anyway (as you know where and whether or not the packages are trusted IF you downloaded them from the official repos or another reliable source).

---

### Post by buzzingrobot on 2013-12-21
If the USB stick contains the Ubuntu installer, then it will install Ubuntu.

If Ubuntu is installed onto a USB stick, then, of course, booting it will run Ubuntu, not the installer.

If you need to migrate applications added after an install to a second, new, installation, the simplest way would be to simply keep a record of those apps. Once the new system is ready, install them.

Or, collect the install debs for those applications, store them someplace, and install them later. Dpkg, the Software Center, gdebi, qdebi, etc., should all be capable of installiing them. If a package has dependencies that are not currently installed, the repositories for those dependcies will need to be in the sources list. (Dpkg, though does not resolve dependencies.)

---

### Post by hitsware on 2013-12-21
> **buzzingrobot said:**
> If the USB stick contains the Ubuntu installer, then it will install Ubuntu.

If Ubuntu is installed onto a USB stick, then, of course, booting it will run Ubuntu, not the installer.

If you need to migrate applications added after an install to a second, new, installation, the simplest way would be to simply keep a record of those apps. Once the new system is ready, install them.

Or, collect the install debs for those applications, store them someplace, and install them later. Dpkg, the Software Center, gdebi, qdebi, etc., should all be capable of installiing them. If a package has dependencies that are not currently installed, the repositories for those dependcies will need to be in the sources list. (Dpkg, though does not resolve dependencies.)

The problem being: If you're not online, (which my target PC is not) and need dependencies, gdebi et al cannot access them ......

---

### Post by buzzingrobot on 2013-12-21
> **hitsware said:**
> The problem being: If you're not online, (which my target PC is not) and need dependencies, gdebi et al cannot access them ......

Correct.  The assumption that users have access to broadband connections is built in to Windows, OS X and Linux. But, it's an assumption with consequences.

If you can get the dependencies you need before doing the install on the disconnnected machine, I've had luck with using dpkg to install a package and all its dependencies by using wild cards to call dpkg.  E.g., put the package and all its dependencies in a folder. Exeute "dpkg -i *.deb". That seems to avoid the problem of X failing because it needs Y, and Y failing because it needs X.

I haven't tried this, though, with more than a few dependencies so I can' say if it works with a large number with a long dependency chain.

---

### Post by hitsware on 2013-12-21
Thanks Everyone !
My answer may be to simply run off the 'live' usb
Maybe I don't need no stinkin' HD .....<|8^))

---

### Post by Impavidus on 2013-12-22
Synaptic can create a download script to get a package with all its dependency via a different computer and a usb drive, so you can easely install it on a computer without internet access. Of course, with synaptic no longer installed by default, you'd have to install that first...

---

### Post by hitsware on 2013-12-22
> **Impavidus said:**
> Synaptic can create a download script to get a package with all its dependency via a different computer and a usb drive, so you can easely install it on a computer without internet access. Of course, with synaptic no longer installed by default, you'd have to install that first...

As I said above :
I have downloaded the main app I want. (Wine)
When I try to install it with Software Manager
(Synaptic?) it refuses and gives a 'untrusted source'
error. There appears to be an overide 'install anyways',
but it does not work (sends you back to the beginning)
Unless I'm missing something ?????

---

