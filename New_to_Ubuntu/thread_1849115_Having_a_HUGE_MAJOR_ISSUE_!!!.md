---
title: "Having a HUGE MAJOR ISSUE !!!"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by User2011 on 2011-09-23
[FONT=Tahoma][SIZE=2]Okay. Let's avoid drama !!! 

I've just installed Ubuntu 11.04 (for the 3rd time today) I've been having A LOT of problems. For example, I can't update, download software, manually function the terminal or do anything else without being interrupted by a pop up window informing me that something is wrong therefore I cannot proceed with my actions! etc.

I downloaded Ubuntu 11.04 from Ubuntu's website and burned it on a dvd and installed Ubuntu inside windows because it was the only way I was able to install it. The installation is process is okay, but I want to know if the Ubuntu isn't functioning right because I was using Windows XP or because it still has the Windows XP installed or maybe it has something to do with the FAT, FAT32, NTFS...

Can anybody please help me??? I'm getting tired of troubleshooting Ubuntu all the time. I've never used it before, but I already got familiar with this distro and I would love to use Ubuntu from now on (instead of Windows) 

So please help me, thank you!!!!
[/SIZE][/FONT]

---

### Post by sircurmudgeon on 2011-09-23
You mentioned an error window. It might be useful if you could tell us what that says. Also, there are usually details available in errors (bottom left of popup). That might be helpful as well.

---

### Post by mmsmc on 2011-09-23
you say that you can only install ubuntu from windows, is this because you cant access your BIOS to choose how you want to boot?

---

### Post by LowSky on 2011-09-23
you keep posting the similar problems, each stating you have install Ubuntu a few times one states the issue fixed.

please post the pop up.

---

### Post by User2011 on 2011-09-23
[SIZE=2][FONT=Arial]Yes. I've been having pop up windows with bottom details. 

*[SIZE=3]EXAMPLES:[/SIZE]*

[/FONT][/SIZE][FONT=Arial][SIZE=2]whenever I open the Update Manager, a error window pops up saying[/SIZE][/FONT] [SIZE=2]*NOT ALL UPDATES CAN BE INSTALLED - RUN A PARTIAL UPGRADE, TO INSTALL AS MANY UPDATES AS POSSIBLE*[/SIZE]  and when I do so it doesn't work either, and not even the SYNAPTIC  PACKAGE MANAGER works as well because every time I try to open it, I  recieve an error message telling me to [B]manually run 'sudo dpkg -- configure-a' correct the problem


[/B][SIZE=2][FONT=Arial][ - And then I do so, but nothing really happens... - ]

[/FONT][/SIZE][FONT=Arial Narrow][SIZE=2]every software that I try to download on the **Ubuntu Software  Center** is consequently being interrupted by a pop up error window that  says:

***An unhandlable error occured -*** [I]There seems to be a   programming error in aptdaemon, the software that allows you to   install/remove software and to perform other package management related   tasks

[B]Details:
[FONT=Courier New]
[/FONT][/B][/I][FONT=Courier New]Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the  ttf-mscorefonts-installer package. This might mean you need to manually  fix this package.
[/FONT][/SIZE][/FONT]

[SIZE=2][FONT=Arial][ - And that's not just it. In closing I don't have any sound at all! I've downloaded the extra packages before[/FONT][/SIZE] and everything is leveled on the alsa mixer but I still don't hear anything
[SIZE=2][FONT=Arial]
[/FONT][/SIZE]

---

### Post by westie457 on 2011-09-23
> **User2011 said:**
> [SIZE=2][FONT=Arial]Yes. I've been having pop up windows with bottom details. 

*[SIZE=3]EXAMPLES:[/SIZE]*

[/FONT][/SIZE][FONT=Arial][SIZE=2]whenever I open the Update Manager, a error window pops up saying[/SIZE][/FONT] [SIZE=2]*NOT ALL UPDATES CAN BE INSTALLED - RUN A PARTIAL UPGRADE, TO INSTALL AS MANY UPDATES AS POSSIBLE*[/SIZE]  and when I do so it doesn't work either, and not even the SYNAPTIC  PACKAGE MANAGER works as well because every time I try to open it, I  recieve an error message telling me to [B]manually run 'sudo dpkg -- configure-a' correct the problem


[/B][SIZE=2][FONT=Arial][ - And then I do so, but nothing really happens... - ]

[/FONT][/SIZE][FONT=Arial Narrow][SIZE=2]every software that I try to download on the **Ubuntu Software  Center** is consequently being interrupted by a pop up error window that  says:

***An unhandlable error occured -*** [I]There seems to be a   programming error in aptdaemon, the software that allows you to   install/remove software and to perform other package management related   tasks

[B]Details:
[FONT=Courier New]
[/FONT][/B][/I][FONT=Courier New]Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the  ttf-mscorefonts-installer package. This might mean you need to manually  fix this package.
[/FONT][/SIZE][/FONT]

[SIZE=2][FONT=Arial][ - And that's not just it. In closing I don't have any sound at all! I've downloaded the extra packages before[/FONT][/SIZE] and everything is leveled on the alsa mixer but I still don't hear anything
[SIZE=2][FONT=Arial]
[/FONT][/SIZE]


Hi, open a terminal (Ctrl+Alt+t) then run these commands one at a time. ```
sudo dpkg --configure -a

sudo apt-get install -f
```

Post any error messages so we can have a better clue of what is happening.

Thank you.

---

