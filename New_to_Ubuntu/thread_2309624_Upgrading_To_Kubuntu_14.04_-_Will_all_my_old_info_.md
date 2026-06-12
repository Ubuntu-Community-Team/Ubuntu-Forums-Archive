---
title: "Upgrading To Kubuntu 14.04 - Will all my old info be wiped out?"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by cedric9 on 2016-01-12
I've been using Ubuntu 14.04 LTS for a while now, (4x Intel cor 2 Quad @ 2.40 Ghz - 2 GiB of Ram) and I'm thinking about upgrading to Kubuntu 14.04, because it seems to have a more friendly interface.  I've already downloaded the ISO image for Kubuntu, and have burned it to a DVD, but before I reboot my computer from this DVD, can anyone tell me if all of all the user accounts I created under Ubuntu will still be there after I install Kubuntu?  I really don't want to do a fresh install, I'm hoping that I can just run this disk and upgrade my computer to Kubuntu without any complications?  I've backed up all my important documents, but still I'd prefer if everything wasn't removed from my drive during installation?

---

### Post by ajgreeny on 2016-01-12
The "safest" way to do this is to install the package kubuntu-desktop using the normal way that you install any other package.

I admit it will possibly give you a rather muddled and possibly confusing menu system in Kubuntu, and I do not know exactly how the unity dash system will behave after doing so, but I think it is at least a good way to try out the DE in a proper OS rather than just investigate it in a live OS.

If you find that the duplication of, for example dolphin and nautilus as file managers annoys you, just remove the one you don't want being careful that it does not take with it some other package that you do want to keep; that is the main problem when having more than one DE on a single OS, but I used to do it in the days of gnome-2 and KDE-3.5 without a problem.

You may not have come across synaptic package manager as it is no longer installed by default, but I suggest to you that it is the best way to deal with the sort of package management activities that you are thinking about as it gives you so much more info than the software-centre; it is what I use as my main package management tool and I thoroughly recommend it to you.

---

### Post by cedric9 on 2016-01-12
Well, since I'm not that familiar with Linux, I've come up with a scheme that will allow me to try out Kubuntu without possibly burning all of my bridges.  So far I've cloned my entire hard drive using Clonezilla to an older drive had sitting around, and then I used Boot Disk Repair 32 to make the cloned hard drive bootable, just like the old one.  It's getting late over here, but tomorrow I plan on running the Kubuntu install DVD on the cloned hard drive to see what happens.  If things don't work out well, I can just go back to my original hard drive.  I'll post an update within the next day or so.

---

### Post by grahammechanical on 2016-01-12
> I've already downloaded the ISO image for Kubuntu, and have burned it to a DVD, but before I reboot my computer from this DVD

What you are about to do is the same as a fresh install. If you use the Something Else option and not tick to format the Ubuntu partition you should not lose the user configurations. I have done this with a re-install of Ubuntu but never with an install of another flavour of Ubuntu over Ubuntu. So, I cannot say how successful this will be.

If you have a separate /home partition & if you install Kubuntu into the Ubuntu partition it will not matter if you format the Ubuntu partition. You give the /home partition the mount of /home but do not tick the box to format the /home partition. You should not lose your user settings.

But as you intend, it is always best to experiment with an OS that can be wiped and replaced then experiment with the only OS on the machine.

Regards

---

### Post by cedric9 on 2016-01-13
Unfortunately I didn't create a separate /home partition when I initially installed Ubuntu, and the installation DVD won't let me do anything unless I first format the root partition, so I gave up on trying to use the installation DVD for this project.

After poking around in this forum a bit, I found the below commands which allowed me to download and install Kubuntu and Plasma:

sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install plasma-desktop plasma-workspace plasma-workspace-wallpapers
sudo apt-get dist-upgrade

After I completed the above steps, I was greeted with a splash screen reading "Kubuntu" but I still had the same desktop environment as before.  After poking around (not sure exactly what I did) I was able to get Kde up and running, but I seem to be having trouble with not being able to write to certain system files.  

Every time Kde launches I receive the below error message, and I'm unable to save any changes that I make to my system settings.  I'm getting at least two separate error messages, (both error messages appear to be very similar) but I didn't manage to catch the text of the second message.

Below is one of the error messages I'm getting when Kde launches:

Configuration file "/home/example/.kde/share/config/plasma-desktopprc" not writeable

I'm assuming that I have to take ownership of certain system files that were created under Ubuntu?  

For the meantime I'm going to put my original hard drive back in place, and will probably put this project on hold until next week.  Meanwhile, any advice will be greatly appreciated.

---

### Post by SeijiSensei on 2016-01-13
Use that drive to hold /home and copy the contents of the current /home to it.

Suppose the second drive is /dev/sdb. Use gparted to create a single large partition on the drive and format it as ext4.  Now mount it and copy the contents of /home like this:
```

sudo mkdir /mnt/home
sudo mount /dev/sdb1 /mnt/home
cd /home
sudo rsync -av . /mnt/home/

```
Now you can install Kubuntu and choose "something else" in the disk partitioning step to tell the installer to use /dev/sdb1 as /home.

---

### Post by cedric9 on 2016-01-15
> **SeijiSensei said:**
> Use that drive to hold /home and copy the contents of the current /home to it.

Suppose the second drive is /dev/sdb. Use gparted to create a single large partition on the drive and format it as ext4.  Now mount it and copy the contents of /home like this:
```

sudo mkdir /mnt/home
sudo mount /dev/sdb1 /mnt/home
cd /home
sudo rsync -av . /mnt/home/

```
Now you can install Kubuntu and choose "something else" in the disk partitioning step to tell the installer to use /dev/sdb1 as /home.

Hmm....Interesting.   What if I copy my home directory as you suggested, but then I copy it back to it's original location after the installation is complete (without telling the installer to use /dev/sdb1)?  If possible I'd like to keep everything within the same ext4 partition for ease of backing it up with Clonezilla.

---

### Post by SeijiSensei on 2016-01-15
You could do that, yes.  You should consider creating a separate partition for /home when you install, so this problem doesn't arise again.  Rsync is a bit touchy about syntax when it comes to referencing the source and target directories, particularly when and when not to use a trailing slash.  Use "man rsync" to read its manual page.

---

### Post by cedric9 on 2016-02-01
Nope, after doing some experimenting, I couldn't get the KDE desktop to load properly, and the entire thing became very unstable after I attempted to install some updates (the menu seemed to be having some problems and mouse pointer disappeared).  I decided to redo the entire partition and start over from scratch using the Kubuntu 14.04 install disk.  Bottom line, it would have been easier if I'd just used the install DVD in the first place.  Anyway, I still have all of my original documents and short cuts on the original hard drive.

---

