---
title: "Hello"
date: 2019-05-17
forum: New to Ubuntu
---

### Post by karozagorus on 2019-05-17
Hey, I'm a very recent convert to Ubuntu, this year I have began experimenting with moving my daily life onto Ubuntu, most of the time Steam goes not seem to work properly but I managed to get past most of the issues that are present and I'm ever increasingly happy with the outcome, although I already went 2 weeks with Ubuntu I can say I'm really enjoying it. Although there are some problems I usually face is that I use caps lock a lot I kind of grown up with using caps all the time and the switch off from Caps is way too slow and leaves THe SEcond LEtter of EVery word in capital, is there a way to fix this or should I just learn how to use shift? xD

Also it been quite a pain to get discord, telegram, steam and other apps to auto start, while keybase was able to properly auto-start. I do really like Linux, I certainly feel a lot more safer on the operating system, although I would also prefer some Anti-Virus software like ClamAV to properly function, I've been trying to set up it but the installation is so overwhelming sometimes. I so far really enjoy Disco Dingo, the refreshed UI is very good, feels a lot better, I just wish LTS would be able to pick up some of these better functionalities over time but not just remain the same old as I would perceive it.

Also I've been running into problems in the past with Xenial regarding Nvidia Drivers, they been making the screen entirely dark in the past but since I only have a old Nvidia card right now I'm not having the same issues. I find it shameful that Nvidia doesn't take more due care to keep things updated and functioning on Ubuntu or other Linux operating systems. The onboard Intel GPU also functions for me fine, sometimes when an app can not be run with the dedicated car I plug over into that one temporarily.

Second Life with Firestorm Viewer is also struggling really hard on Ubuntu, on Windows for example the GTX260 is able to run SL just fine with 70-80 fps on certain settings but while same settings on Ubuntu produce sub-30 frames. Any idea how this could be fixed?

Also auto-mounting NTSF file systems seems to be problematic for Ubuntu because I have to always manually mount it when I boot up, any ways to fix this also?

---

### Post by Autodave on 2019-05-17
Can you please give us some specs on you equipment?

What driver did you install for your Nvidia card and where did you get it from?

As far as an anti-virus, don't waste your time: it is not needed for Ubuntu.  All it is doing is scanning for Windows' viruses which will not bother Linux at all.

---

### Post by oldrocker99 on 2019-05-17
Actually, IF you download the nVidia drivers from the PPA, you'll have them stay updated.```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

ATI drivers and Intel drivers, both being open source, are built in to the system. There is an open source nVidia driver, but it is currently inferior to nVidia's excellent (IMHO) drivers and service for we Linux users.

Once it automatically updates, you can open Synaptic and search for nvidia (that package manager is NOT case-sensitive).  The current version is 430. Installing the drivers this way is the official Ubuntu way to install the drivers. Do NOT download the drivers from the nVidia website; you'll have to download them each time a new version comes out. 
[code]sudo apt install nvidia-xxx 
(xxx is the version number)

If you DID install the version from nVidia, let is know in this thread.

---

### Post by oldrocker99 on 2019-05-17
Also, the only reliable way to install Steam is to use the repositories:
```
sudo apt install steam
```

This will pull in all the libraries and other dependencies, and Steam should run flawlessly. It certainly does for me.

---

### Post by Impavidus on 2019-05-17
You ask quite a lot of questions.

> **karozagorus said:**
> I use caps lock a lot I kind of grown up with using caps all the time and the switch off from Caps is way too slow and leaves THe SEcond LEtter of EVery word in capital, is there a way to fix this or should I just learn how to use shift? xDUbuntu makes capslock behave like on the old mechanical typewriters it was invented for: Capslock is activated on the first press and deactivated on the second release. You may be relying on a bug in another OS, where capslock is deactivated on the second press. I think most people type a single capital with shift. For capitals on the left side of the keyboard, typing them with the right shift is much faster than with capslock – and I don't know your language, but in mine most capitals are single and on the left side of my qwerty keyboard.

> I just wish LTS would be able to pick up some of these better functionalities over time but not just remain the same old as I would perceive it.But remaining the same is the main feature of an LTS release. Two years is still quite short compared to other OSs, but if you really like large changes every 6 months, nobody stops you from using the interim releases. I do, although I don't really care for regular overhauls of the graphical interface.

> Also auto-mounting NTSF file systems seems to be problematic for Ubuntu because I have to always manually mount it when I boot up, any ways to fix this also?How do you try to automount your ntfs filesystem? The normal way to mount things automatically during boot is by putting them in /etc/fstab. This should work, provided the ntfs filesystem is clean. Unfortunately, Windows doesn't always leave a clean ntfs filesystem after shutdown. Windows considers this a feature: by not properly unmounting the filesystem, it can boot faster. But Linux can't deal with that.

---

### Post by TheFu on 2019-05-17
Too many questions in 1 thread.

To mount ntfs with control over the permissions and good performance, use either the ftab file or autofs.  There are some options needed.

Complaining about hardware and poor drivers isn't much we can do, but there are some snippets of knowledge for how to work around many issues. Just need to search here using exact chips to find the kernel module option.

As for security of a desktop Ubuntu system.  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)  My profile in the "visitor messages" has many more links.  For a normal desktop, not running any network services, there isn't much you should do besides 
* staying patched on a currently supported release.
* perform daily or weekly, versioned backups.
* avoid doing dumb things on the internet. Stay away from the seedy parts.
You'll see links to other how-do-i-run-linux in my profile.

Never forget that the GUI is just another program on Unix-like OSes.  There are about 50 to choose from, so if you don't like the one you have, take a look around.  I still use a GUI from the mid 1990s sometimes. When I show it off, people think it looks extremely modern with opaque windows, plenty of eye candy monitoring, etc.  But most of the time, I use a very simple, no menu, no panel, setup.  Whatever you like is what matters for the GUI.  With just a few tweaks to a config file, some GUIs can appear to be drastically different.

And welcome.

---

### Post by deadflowr on 2019-05-17
> should I just learn how to use shift?
Yes.
It's how typing was and has been done for a hundred years.

---

### Post by QIII on 2019-05-17
I can demonstrate this with my great-uncle's WWI era Corona typewriter.

---

