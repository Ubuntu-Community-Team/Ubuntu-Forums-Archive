---
title: "Certain Programs Can't Access My Files"
date: 2020-06-01
forum: New to Ubuntu
---

### Post by oscarstomberg on 2020-06-01
So I just installed Ubuntu on my computer alongside Windows. I have an SSD boot drive that I partitioned, one for Windows and one for Linux. I also have a hard drive where I keep my personal files. When I installed Linux, I mounted the root in the Linux partition, and I mounted my hard drive to /data. However, in created /home separately so I replaced the folders with links to folders in /data. This seemed to work just fine. The problem arose when I installed some programs (Arduino IDE and ONLYOFFICE), and when I tried to open files it showed the links to not work, and when I went to the root it did not show /data. However, other programs such as VLC and OBS had no problems. Why might this be? Any help is appreciated. If it helps, the file opening interface VLC and OBS use looks just like the basic file manager, but for Arduino and ONLYOFFICE it looks different.

---

### Post by TheFu on 2020-06-02
Snap packages are the likely problem.
Check which are snaps using 
```
snap list
```

[https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022](https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022)

People who only access data in their HOMEs probably will never have any issues.  People who place data anywhere else are basically screwed.  Some packages have both snap and the older APT/deb packages.  Remove the snaps, install the package using "apt install" and be happy.  

Unfortunately, the snap team hasn't provided any solution for people who don't behave in the way they think we should.  If you use /tmp/ - snaps will never be able to access that storage. NEVER.
If you use NFS - snaps are broken.  They've known about this for over 3 yrs.  If your company uses NFS for HOME directories, you are doubly screwed.

There is some good news for you, maybe.  If you move your mount from /data to /media/data, then if you ask each snap package nicely AND the package creator agrees that you should be allowed to ask, then they may have enabled "removable storage" to be accessed.  The link above has the command.  If the snap package team decided nobody would ever use storage outside their HOME, you are screwed.

If you'd like to know more about this issue, there are a few snap threads in these forums with 25+ posts.  But because the devs don't look here, the best we can do is provide possible work-arounds.

Some of the simpler programs inside snaps can be run directly.  Oddly, chromium browser seems to work fine that way even though only a snap package is available.  To run it, use:
```
/snap/chromium/current/usr/lib/chromium-browser/chrome &
```

Snaps aren't all bad if your system has plenty of storage, lots of CPU and lots of RAM.  But if you are on a more limited system, like my 2G RAM, Celeron, with 16G of RAM, snaps make it so I have to use external storage for data ... but cannot actually access that data unless the package creator agrees.  IMHO, snaps are broken by design and should never have been part of a shipping LTS release.  Canonical screwed up on this.

Snaps are supposed to "just work" on any Linux system.  I've found that is not the situation.  About 80% of snaps I've installed on my more powerful 16.04 laptop fail to work at all.  A few work perfectly, the first time and every time after. It is really quite nice.
Snaps auto update without asking.  They keep 2-3 version around. There's no way to keep just 1 version. I've tried. Canonical decided that MSFT was right NOT to ask about upgrades.
Snaps bring all the dependencies that the developer thinks we need. They get that wrong, sometimes.  Some packages that worked perfectly over remote X11 stopped working when the snap came.  I don't know why. Makes no sense to me.

I'll let someone else cover the great things about snaps - which definitely do exist.  It just hasn't been my experience.

Here's someone that likely has the snap problem too: [https://ubuntuforums.org/showthread.php?t=2434651](https://ubuntuforums.org/showthread.php?t=2434651)

---

