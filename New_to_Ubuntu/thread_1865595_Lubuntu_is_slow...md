---
title: "Lubuntu is slow.."
date: 2011-10-20
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2011-10-20
PC Specs:
1.8ghz Pentium 4
512 ram 
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)


Wonder if you all can help me. I've used Linux in the past but not a lot. 
I have an older PC that has Windows XP and wanted to try Linux. The cd drive is flaky in this machine so I wanted to use Wubi.

Here's what I did. 
Downloaded Wubi and installed Ubuntu 10.04 Super slow.....
Then used Psychocats tutorial to remove Ubuntu, kubuntu, Xubuntu and Edbuntu
 
So now I'm at Lubuntu Lxde  and it's still slow. 
When I run free -m I get this:
```

buzz@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        485         10          0        159        241
-/+ buffers/cache:         83        411
Swap:          255         75        180

```

and when i run top I get
```

top - 08:34:30 up 8 min,  0 users,  load average: 0.39, 0.69, 0.46
Tasks:  91 total,   1 running,  89 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.0%us,  1.0%sy,  0.0%ni, 97.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    507324k total,   497324k used,    10000k free,   154764k buffers
Swap:   262140k total,    74964k used,   187176k free,   247204k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                             
  866 root      20   0 42904 7452 4656 S  1.0  1.5   0:17.02 Xorg                                
 1305 buzz      20   0 95780  11m 8912 S  1.0  2.2   0:01.50 lxterminal                          
 1263 buzz      20   0  403m  72m  28m S  0.7 14.6   1:13.36 firefox                             
 1054 ntp       20   0  3676 1208 1104 S  0.3  0.2   0:00.05 ntpd                                
 1361 buzz      20   0  2792 1100  852 R  0.3  0.2   0:00.17 top                                 
    1 root      20   0  3324 1176 1176 S  0.0  0.2   0:00.86 init                                
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                            
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                         
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.46 kworker/0:0                         
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.57 kworker/u:0                         
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                         
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset                              
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper                             
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns                               
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers                         
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                         
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd                         
   13 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd                             
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ata_sff                             
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.03 khubd                               
   16 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 md                                  
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd                          
   20 root      20   0     0    0    0 S  0.0  0.0   0:01.06 kswapd0  

```

Can anyone help speed up the machine?                 
To me it looks like all the memory is being used.. But by what?

---

### Post by snowpine on 2011-10-20
Welcome to the forums!

Can you be more specific about "slow"? There are many different ways a computer can be slow (booting, browsing the web, watching videos, opening applications, ripping multimedia, etc) and each will have a different solution. Are you sure it's not just slow because it's an old computer? :)

According to the outputs of free and top, you are barely using your RAM or CPU, so neither one of those is the culprit. 

[http://linuxatemyram.com](http://linuxatemyram.com)

Have you tried other Linux options, such as a regular (non-WUBI) install of Lubuntu, or a lightweight distro such as Puppy Linux?

(edit) I suggest using the forum Search feature for your specific video card. Other users have suggested some tips & tricks to improve video performance.

---

### Post by BuzzStPoint on 2011-10-20
Slow as in if I launch an application, Chrominium or firefox, it takes awhile for it to load up. 
I created a new text document from right clicking on the desktop and about a minute later it loaded up. 

Web browsing is slow, just any general use of the os seems at least 1.5 times slower then my XP install. 

The link was great.. Explained alot. 

Other installs?
Other then the Ubuntu no. I'm looking into how to install lubuntu from a USB because my CD drive seems to overheat. It will quit working if it's been used for awhile. Sometimes doesn't read any cd's. 

Would a direct cd/usb install be better then a Wubi ubuntu downgraded install?

---

### Post by LinuxFan999 on 2011-10-20
> **BuzzStPoint said:**
> Slow as in if I launch an application, Chrominium or firefox, it takes awhile for it to load up. 
I created a new text document from right clicking on the desktop and about a minute later it loaded up. 

Web browsing is slow, just any general use of the os seems at least 1.5 times slower then my XP install. 

The link was great.. Explained alot. 

Other installs?
Other then the Ubuntu no. I'm looking into how to install lubuntu from a USB because my CD drive seems to overheat. It will quit working if it's been used for awhile. Sometimes doesn't read any cd's. 

**Would a direct cd/usb install be better then a Wubi ubuntu** **downgraded install?**
Yes, that would work better than Wubi. What is the Capacity of your computer's hard drive? How old is it?

---

### Post by snowpine on 2011-10-20
> **BuzzStPoint said:**
> Slow as in if I launch an application, Chrominium or firefox, it takes awhile for it to load up. 
I created a new text document from right clicking on the desktop and about a minute later it loaded up. 

Web browsing is slow, just any general use of the os seems at least 1.5 times slower then my XP install. 

The link was great.. Explained alot. 

Other installs?
Other then the Ubuntu no. I'm looking into how to install lubuntu from a USB because my CD drive seems to overheat. It will quit working if it's been used for awhile. Sometimes doesn't read any cd's. 

Would a direct cd/usb install be better then a Wubi ubuntu downgraded install?

Your install-Ubuntu-and-convert-to-Lubuntu method is odd. I recommend you just do a plain regular install of Lubuntu and see what happens. A full install will take advantage of Linux filesystems and therefore speed up disk activity like launching an application or caching a web page. You should be able to create a Lubuntu Live USB from your current Lubuntu install using the "usb-creator" application available in the repos. 

It is normal for Ubuntu to be slower than Windows XP. It's been 10 years since XP was released and it has much lower hardware requirements than modern Linux. :)

---

### Post by LinuxFan999 on 2011-10-20
> **machineheadbush said:**
> no **windows is just coded more** **efficent than linux**
Seriously? I don't think so. For me, Linux is usually faster than Windows, except in Virtualbox.

---

### Post by Maro848 on 2011-10-20
I just set up an old dell with a pentium 3 500mhz cpu and 256mb of ram and dual booted Debian 6.03 and Xubuntu 11.04. Both are working faster than win XP ever did on this machine and Debian is even faster than Xubuntu (its the KDE interface if that helps). So for a lighter install I would say that one of those two would help. I know that a lot of people say the XFCE interface is not really "light" but it seems to work better than Lubuntu did on my machine. And the KDE even better than that. Hope this helped

---

### Post by BuzzStPoint on 2011-10-20
OK update time..

Someone asked how big is the hard drive. 
30 gigs

I booted back to Windows, and uninstalled Ubuntu. 
Borrowed a cd drive, burnt Lubuntu to cd and just got done installing from CD.

Worlds of difference. 
Boot up is faster
application launch is faster
Even as I type, the text is keeping up with me. before I would type a sentence and when I was done it was still typing. 
Running now like I was expecting it to before.

---

### Post by verymadpip on 2011-10-20
Niiiiiiiiiice.

Lubuntu rocks.

---

### Post by amjjawad on 2011-10-20
Hello there and Thanks for choosing Lubuntu :)

LXDE will dazzle you and I'm talking from experience here, not from any website or any other source. LXDE will run on 64MB RAM and P2 366MHz while even XP will be dead slow on such hardware.
I have tested myself so YES, it's very much capable of that.

Wubi? I don't recommend that at all.
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

I strongly suggest to get rid of Ubuntu (I guess you already did) and install Lubuntu. Here are some useful links:

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)

If you do have any question, please feel free to contact me any time you want.

Enjoy the real speed ;)

---

### Post by amjjawad on 2011-10-20
> **verymadpip said:**
> Niiiiiiiiiice.

Lubuntu rocks.

and beyond ;)

---

### Post by snowpine on 2011-10-20
Hooray! :)

---

### Post by BuzzStPoint on 2011-10-20
Even with my Excel files, I use here at work. They are Xlsx files, the stock Gnumeric programs opens it up and doesn't complain. I made a copy, because I dont know if excel will like it if I open. 

In Windows, Excel would take a bit to open. But not horrible slow. Gnumeric pops quickly. 

Wondering if I shouldn't go for Open Office.

---

### Post by Rex Bouwense on 2011-10-20
It depends upon what you need to do.  I only create documents and spread sheets so I don't need all of the other stuff that Open Office or its replacement offers.  One of the reasons that Lubuntu is so fast even on the older machines is that it doesn't have all of the hot shot programs that Ubuntu has installed.  If you pick and choose what you need then you can keep the blazing fast speed.:D

---

### Post by BuzzStPoint on 2011-10-20
My excel file is pretty detailed. 
It's been my work in progress for about 8 years now. 
I use it for testing and logging swimming pools and whirlpools. It's set up to look like the local state forms so I can just print to PDF and email to the county health.

---

### Post by amjjawad on 2011-10-20
Give Open Office or whatever other alternatives you find a try. 512MB isn't too bad IMHO.

The best way to find out is to install and try, this is how I learned about which choice is better than the other, this is how I learned that, for me, Lubuntu is better than Ubuntu :)

---

### Post by BuzzStPoint on 2011-10-20
I used apt-get install openoffice.org and it installed LibreOffice.
Seems nice and still edits my files. 

Only issue I have is in MS office I have check boxes on 2 of my forms and they don't show. But I think those are MS proprietary code and in windows using OpenOffice they don't show either.

---

### Post by EddiePereira on 2011-11-17
> **amjjawad said:**
>  
LXDE will dazzle you and I'm talking from experience here, not from any website or any other source. LXDE will run on 64MB RAM and P2 366MHz while even XP will be dead slow on such hardware.
I have tested myself so YES, it's very much capable of that.
 
Man, and I was afraid of trying it on my 10yo, 1.3GHz Celeron, 512 RAM and 20GB HD... Feel much more comfortable now :D

---

### Post by Rodney9 on 2011-11-17
> **EddiePereira said:**
> Man, and I was afraid of trying it on my 10yo, 1.3GHz Celeron, 512 RAM and 20GB HD... Feel much more comfortable now :D

Welcome to the forums and Lubuntu.

For How-To's, Information and Screen-Casts on Lubuntu go to the - 

[- Lubuntu One Stop Thread - ]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

