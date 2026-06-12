---
title: "If not Ubuntu, then what?"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Noor1101 on 2012-11-01
Hi,

I'm having problem after problem installing (X)ubuntu on my new internal HDD.

I'm getting desperate, I really need my laptop for my studies.

My question: If Xubuntu won't work, what is the best alternative? 
I've read a lot about Debian, Mint, Squeeze, but it's all very confusing to me. Too much information, I have little time.

My notebook is a Packard Bell Easynote MH35, about 5 years old. 
My graphics card: 
```
ubuntu@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

```Audio:
```
ubuntu@ubuntu:~$ lspci | grep Audio
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
ubuntu@ubuntu:~$ 

```Memory:
```

ubuntu@ubuntu:~$ cat /proc/meminfo
MemTotal:        2966572 kB
MemFree:          245452 kB
Buffers:          318076 kB
Cached:          1786640 kB
SwapCached:          336 kB
Active:          1330660 kB
Inactive:        1137516 kB
Active(anon):     269272 kB
Inactive(anon):    98300 kB
Active(file):    1061388 kB
Inactive(file):  1039216 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       2102856 kB
HighFree:          85376 kB
LowTotal:         863716 kB
LowFree:          160076 kB
SwapTotal:       5858300 kB
SwapFree:        5857956 kB
Dirty:             31240 kB
Writeback:            76 kB
AnonPages:        363132 kB
Mapped:            51000 kB
Shmem:              4116 kB
Slab:             217540 kB
SReclaimable:     205152 kB
SUnreclaim:        12388 kB
KernelStack:        2176 kB
PageTables:         5332 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7341584 kB
Committed_AS:    1190436 kB
VmallocTotal:     122880 kB
VmallocUsed:       23556 kB
VmallocChunk:      94440 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB
ubuntu@ubuntu:~$ 

```My HDD is 500GB (don't know how to get the specs of that)


Who has an opinion? I need my laptop for my studies: internet browsing, text editing (Open/LibreOffice is great)
I don't do any gaming
In my freetime I like to watch/download videos (youtube, silverlight/moonlight (I know this can be problematic-doesn't matter), torrents), use GIMP, play a little online poker.
I don't want/need a very slick desktop - I really like XFCE in Ubuntu.

I can only install from USB flash - my CD-ROM drive doesn't work properly

I'm looking for something as compatible (light?) as possible, can't really afford to spend the whole weekend trying to configure hardware settings etc.

Thanks for any thoughts you'd like to share with me!!

---

### Post by teward on 2012-11-01
Try [_Lubuntu_]("http://lubuntu.net/").  It's lighter than Xubuntu, its just with LXDE (which is a lighter DE than Unity/GNOME, KDE, or XFCE)

It's not the XFCE interface, but its still Ubuntu (Libre/Open Office is pretty resource-heavy though)

---

### Post by hakermania on 2012-11-01
I read your post and I don't find a reason why LUbuntu wouldn't suit you.

You didn't tell us what the problem is with XUbuntu, though....

---

### Post by hakermania on 2012-11-01
> **Lord of Time said:**
> Try [_Lubuntu_]("http://lubuntu.net/").  It's lighter than Xubuntu, its just with LXDE (which is a lighter DE than Unity/GNOME, KDE, or XFCE)

It's not the XFCE interface, but its still Ubuntu (Libre/Open Office is pretty resource-heavy though)

I guess you just went back in time with the sole purpose on commenting just one second before.... :D

---

### Post by dannyboy79 on 2012-11-01
is it because after you perform an install from a USB stick that you have a black screen? Whats the problem with Xubuntu?

---

### Post by teward on 2012-11-01
> **hakermania said:**
> I guess you just went back in time with the sole purpose on commenting just one second before.... :D

I'm the Lord of Time.  That is my prerogative, to go back in time and ninja you :P

No, but seriously, in all actuality, Lubuntu is really the lightest flavor of Ubuntu there is.  I have confirmed this (Xubuntu didn't run smoothly on a 5 year old laptop, but Lubuntu did.  Same with my 4 year old netbook :P)


And i'm now intrigued, what issues are you having with Xubuntu...?

---

### Post by Noor1101 on 2012-11-01
No, I didn't explain the problem with Xubuntu and Ubuntu (sorry), but it's [here, in this thread]("http://ubuntuforums.org/showthread.php?t=2078750&page=2"). NikTh is trying to help..

I'm just so desperate ](*,) because I tried 5 different types of installation (Ubuntu 12.04 desktop, Ubuntu 12.04 alternate, Xubuntu 12.04 desktop, Xubuntu 12.04 alternate, Ubuntu 11.10 desktop), all multiple times, but it doesn't work..

If you have any thoughts...

---

### Post by Noor1101 on 2012-11-01
dannyboy, the installer(s) crash(es), see my other thread... :(

---

### Post by teward on 2012-11-01
> **Noor1101 said:**
> If you have any thoughts...

Scroll up.  If Xubuntu's too heavy for your system, try Lubuntu, there's a link to its site in my initial post on this thread.  (me and hakermania said this)


I also commented on the thread you linked, you may want to take a look there.

---

### Post by Noor1101 on 2012-11-01
It's not too heavy.. It just won't install. The installer crashes time after time.

Before my HDD broke down, Ubuntu Unity/Kde/Xfce/Gnome all worked fine. It's just that the installation breaks down before finishing. But that's in my other thread..

---

### Post by teward on 2012-11-01
I'm still waiting to hear that you've tested Lubuntu.  For all intents and purposes the crashes could be unrelated to the HDD, but could be related to the graphics card or some other hardware.  Your stats on yoru drive look to be fine, in the other thread, so I'm still curious why you're hung up on "Oh, its the HDD"

And define "crash".  The other thread is strangely ambiguous when you define "crashes"

---

### Post by Noor1101 on 2012-11-01
I don't think it's the HDD. Never was 'hung up' on that. It was just strange that the installer _did_ work on my last HDD, and _not_ on the new one.
I'm just trying to get my computer to work, that's all. 

And the 'crash', that's what the computer calls it.

"We're sorry, but the installer has crashed."

All this (plus more error messages are in the other thread..


My question in _this thread_ is,
what kind of non-Ubuntu could I choose to replace my former Xubuntu?

I'm a noob OK. Bear with me

---

### Post by rburkartjo on 2012-11-01
you could also try snow linux it is based on  xfce lightweight


[http://www.snowlinux.de/blog/458-snowlinux-3-qcrystalq-xfce-released](http://www.snowlinux.de/blog/458-snowlinux-3-qcrystalq-xfce-released)

---

### Post by Noor1101 on 2012-11-01
Rburkartjo, that sounds really good! Thank you :)

I'll go try it now

---

### Post by CharlesA on 2012-11-01
Could always try the LXDE spin of Fedora. ;)

Where does the installer crash, exactly?

EDIT: Link: [http://fedoraproject.org/en/get-fedora-options#spins](http://fedoraproject.org/en/get-fedora-options#spins)

---

### Post by rburkartjo on 2012-11-01
noor let me know how you fared have other options and charles just gave you another lxde

---

### Post by Noor1101 on 2012-11-01
Charles, (it's all in the other thread, but) here are the (error) messages:


(while installing the system - somewhere around "creating user" / "Configuring Apt" / "scanning the CD-ROM".) 
1 ->  "Apt Configuration Problem
An attempt to configure apt to install additional packages from the CD failed"directly after that:
2- > "Installation finished - [Continue Testing] [Restart Now]"+/- 5 seconds later:
3- > "We're sorry, the installer has crashed"  I tried removing the ubiquity-slideshow, because apparently that sometimes causes a crash, no luck.

This happens in all the three desktop-versions I tried
In the 2 alternate versions it just gives a "can't find CD-ROM, check integrity" (or something like that)

----

I'll have a look at the Fedora, too. The snowlinux download is very slow (50kb/s)..

--- I will let you know what happens rburkartjo! :)

Thanks everyone!

---

### Post by CharlesA on 2012-11-01
Odd. I would try verifying the MD5SUM of the ISO and burning it again and see what happens.

Otherwise, Fedora is a good choice. ;)

---

