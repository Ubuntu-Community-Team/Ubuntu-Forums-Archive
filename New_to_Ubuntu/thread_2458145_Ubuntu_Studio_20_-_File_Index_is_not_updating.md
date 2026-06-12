---
title: "Ubuntu Studio 20 - File Index is not updating"
date: 2021-02-17
forum: New to Ubuntu
---

### Post by arvadana on 2021-02-17
Betriebssystem: Ubuntu Studio 20.10
KDE-Plasma-Version: 5.19.5
KDE-Frameworks-Version: 5.74.0
Qt-Version: 5.14.2
Kernel-Version: 5.8.0-43-lowlatency
Art des Betriebssystems: 64-bit
Prozessoren: 8 × Intel® Core™ i5-8300H CPU @ 2.30GHz
Speicher: 7,6 GiB Arbeitsspeicher
Grafikprozessor: Mesa Intel® UHD Graphics 630

Dear Ubuntu Users,

I have Ubuntu Studio installed for a month now and I noticed, that some lately created files don't show up when I search for them via Dolphin search or in the search bar of the menu.
I have set "full index search" for the concerning folders in the search section of the system settings.
It seems to update once every few days, but not that's not enough for me.
I need an up to date searchable database of my files.

Does anybody have a hint for a noob like me?

Thanks.

---

### Post by TheFu on 2021-02-19
I don't use dolphin, but **locate** and **updatedb**are the standard tools for file searching by-name.
If you want deeper searches, **recoll** is pretty great.  Recoll has a GUI.

Both update daily, but we can cause the updates more often. 
```
sudo apt install mlocate recoll
```
I'll look at dolphin's manpage. maybe there's something in that.
[https://docs.kde.org/stable5/en/applications/dolphin/quick-tips.html](https://docs.kde.org/stable5/en/applications/dolphin/quick-tips.html) says Baloo is the search tool.
It doesn't say anything about search indexing that I saw.
[https://wiki.archlinux.org/index.php/Baloo](https://wiki.archlinux.org/index.php/Baloo) has more information about Baloo and the config.

If you want 100% current searching, use 'find'.  But it is not very user friendly. find is one of the tools where seeing lots off examples is very useful for understanding.  explainshell.com would be helpful too. CLI only. No GUI.

---

### Post by deadflowr on 2021-02-19
KDE/Dolphin uses baloo for indexing.
See: [https://community.kde.org/Baloo/Configuration]("https://community.kde.org/Baloo/Configuration")

Edit:
If it's not finding certain files check the baloofilerc's exclude lists as it has a number of file types excluded by default.

---

### Post by arvadana on 2021-02-20
Hey folks!

Thanks for the replies.
I checked out
[https://community.kde.org/Baloo/Configuration](https://community.kde.org/Baloo/Configuration)
and as far as I noobly understood what's going on, I tried:
balooctl check
in the terminal, where it said that it "started search for unindexed files"
but after about four minutes didn't manage to update so that i couldn't find a test file.
BUT
I just disabled the file search in the system configuration
and searched again.
Dolphin did find the new file in about a 30 seconds
So that works for me ...
It's weird.
One  would think, that if you disable the file search and then enable it  again, that it would start searching for new files, but... it doesn't  obviously, or at least at a much slower rate, then when I just disable  it (the indexing)
So whatever... I'm still too new to Linux to get too involved in this.

Thanks again
Have a good day

---

### Post by TheFu on 2021-02-20
baloo uses inotify, but the watch directories has to be configured.  Stopping and restarting the service wouldn't cause a full reindex.  inotify watches for any changes to directories (directories are just files that contain a list of children objects - files, subdirectories, and links.  You can learn more about it in the inotify manpage.  Be certain to check the user AND system config file for baloo. There **are** controls inside it for these things.  There is also a system-wide limit for how many "watches" that inotify can have setup.  The link I provided explains how to modify that limitation.

If you want a 100% current search, then use 'find', as said above.  But it runs a search by scanning the entire target directory tree live.  This can be hard on storage and can take multiple minutes.  Which is why we have other tools that perform indexing daily.  Perhaps you remember on another OS that the indexing service was running all the time and it would show up in complaints all the time about services that slowed everything on the system.

But none of this is helpful if you want a point-n-click answer.  OTOH, understand how things actually work means you'll be able to configure things to be the most advantageous for your needs.

---

