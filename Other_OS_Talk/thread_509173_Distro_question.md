---
title: "Distro question"
date: 2007-07-25
forum: Other OS Talk
---

### Post by Somenoob on 2007-07-25
I'm planning on making a partition an a external HDD for a distro, or maybe just the main hard drive. I was wondering what are the least resource consuming but still quite modern distros?, only containing the essential, bare-bone components? and easy to install of course(or at least not too difficult)

I got a pretty modern laptop(Intel M processor 1.7 ghz)

---

### Post by ddrichardson on 2007-07-25
There are loads of good, stable distros available as Live CD's for you to try without installing. [Ubuntu]("http://www.ubuntu.com") ofcourse, but there are lots more, [this site]("http://distrowatch.com/") gives a good comparison and lets you search for one that meets your needs.

---

### Post by LaRoza on 2007-07-25
Zenwalk is very complete and uses little resources. It has a nice GUI and useful apps.

---

### Post by igknighted on 2007-07-25
> **LaRoza said:**
> Zenwalk is very complete and uses little resources. It has a nice GUI and useful apps.

I wouldn't recommend Zenwalk for this situation... especially on an external drive.  I don't trust lilo's abilities to handle anything modern like that, and it is so much harder to configure.  If it installs wrong you are pretty much SOL, but if grub installs wrong you can edit the entries and save the system easily.

As far as the system itself, ZenWalk is a great distro.  But in your less than normal boot situation I wouldn't recommend it.

You might want to check out a custom install of Fedora or OpenSuse.  These distro's may not have a reputation of being quick, but they will give you the easiest installer that lets you pick exactly which packages get installed.  If you go this route it will leave you with only what you want/need.  Ubuntu has this ability too, but you have to download the server version, install a no GUI system, then add everything manually via the command line.  The Suse and Fedora GUI installers let you do the customization before the install.

---

### Post by ddrichardson on 2007-07-25
As igknighted said, ZenWalk may not care for usb drives, but just to add to the mix I have had problems with Fedora Core 7 on an external USB drive.

---

### Post by RAV TUX on 2007-07-26
> **Somenoob said:**
> I'm planning on making a partition an a external HDD for a distro, or maybe just the main hard drive. I was wondering what are the least resource consuming but still quite modern distros?, only containing the essential, bare-bone components? and easy to install of course(or at least not too difficult)

I got a pretty modern laptop(Intel M processor 1.7 ghz)

Your best bet would be [Wolvix]("http://wolvix.org/") (Zenwalk is great but not as effecient and refined as Wolvix; both are Slackware based).

Wolvix is the most advanced and dependable of the two, you can even install Wolvix on a USB drive. This is all made very simple via the "Wolvix Control Center".

---

### Post by Rumor on 2007-07-26
I'd recommend Vector Linux, the 5.8 Standard Gold edition. It is very light weight and can boot from usb devices.

[http://www.vectorlinux.com/index.php](http://www.vectorlinux.com/index.php)

---

