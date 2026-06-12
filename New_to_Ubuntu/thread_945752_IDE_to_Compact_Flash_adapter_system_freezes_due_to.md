---
title: "IDE to Compact Flash adapter: system freezes due to 100% disk activity."
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Rinusch on 2008-10-12
Hi all,

I'm new here so forgive me if this is not the most suitable forum for this subject.

I installed Ubuntu (actually Xubuntu) on a solid state system, based on the Intel Atom processor. Instead of a hard drive, I'm using an IDE->CF adapter with a 2Gb compact flash card acting as a hard drive. The system has 1 Gb of memory.

This is working fine, however, every now and then, the system freezes for a moment and the CF adapter shows 100% activity (I can tell from the LED being on continuously).
I bought the cheapest card I could find, not thinking the memory (CF) speed would be a bottleneck, but clearly it is. I measured the throughput being around 10 Mb/sec (read speed).

I use the system for web browsing only (using Firefox). I know CF isn't the best medium to write to a lot, so I told Firefox not to cache any data to the drive. So here I am, browsing the web and only having Firefox open (of course except for some default background processes that are running). The system becomes non-responsive (freezes) from time to time. I want to know what is going on, because in theory, nothing should be written to disk by Firefox (or am I wrong??). The System Monitor tells me no swap memory is being used.

Does anyone know a tool or method to be able to find out what is causing the disk activity that in turn causes the system to freeze?

I hope someone is able to help me out here or at least point me in some direction.

Kind regards!

---

### Post by durand on 2008-10-12
I recently found a tool that may help.
```
sudo aptitude install iotop
```
It's kinda like top, but for disk usage.

---

### Post by Rinusch on 2008-10-20
Thanks!

Can't find it, however.

I think it's only in Intrepid. I'm using Hardy.

Any more clues?

Regards!

---

### Post by durand on 2008-10-20
Yeah I just realised that it is but the intrepid version apparently works flawlessly in hardy: [http://packages.ubuntu.com/intrepid/all/iotop/download](http://packages.ubuntu.com/intrepid/all/iotop/download)

---

### Post by marco.caminati on 2009-01-20
> **Rinusch said:**
> Hi all,

I'm new here so forgive me if this is not the most suitable forum for this subject.

I installed Ubuntu (actually Xubuntu) on a solid state system, based on the Intel Atom processor. Instead of a hard drive, I'm using an IDE->CF adapter with a 2Gb compact flash card acting as a hard drive. The system has 1 Gb of memory.

This is working fine, however, every now and then, the system freezes for a moment and the CF adapter shows 100% activity (I can tell from the LED being on continuously).
I bought the cheapest card I could find, not thinking the memory (CF) speed would be a bottleneck, but clearly it is. I measured the throughput being around 10 Mb/sec (read speed).

I use the system for web browsing only (using Firefox). I know CF isn't the best medium to write to a lot, so I told Firefox not to cache any data to the drive.


I digress from your point, just to note that for such cases (solid state - aiming to reduce writes) a live linux distribution might be quite advisable: all changes would be written in ram and disappear on poweroff.
You could try Slax 6: [www.slax.org](www.slax.org), which is the springer of many such distros. Just frugal-install it on your CF. One con is that Slax 6 is still limited to 32-bit archs, though.

Apart from that, I come back to your issue, but to ask rather than to answer: I'm as well interested in putting up a solid-state-only system, and would like to know your experiences with CF or IDE-Flash mass storage (like those on this page: [http://mini-itx.com/store/?c=16](http://mini-itx.com/store/?c=16) ), especially regarding read/write throughput (is it comparable to a IDE or SATA classical hard disk?) and write cycles wearing.

Thanks, Marco.

---

### Post by durand on 2009-01-21
If you do buy an IDE -> CF adapter, I would recommend using ebay. It was the only time I've ever used ebay but the prices on there were so much cheaper than in other shops. I think I bought mine for about £3.50. Unfortunately, the laptop I was using completely died so I didn't get to test it properly but it seemed to work..

---

### Post by eco-ants on 2010-11-06
Hi I'm new to this, but have sucessfully installed Xubuntu 9.10 onto a 16g CF card, using a IDE to CF adapter board bought off E-Bay. (I was careful to buy a high speed flash drive)
It's running on an old Compaq presario V2000, in fact I'm typing this on it now :)
Today I did a test of the speed:

                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         Disk /dev/sda: 16.0 GB, 16039018496 bytes
    [LEFT]255 heads, 63 sectors/track, 1949 cylinders[/LEFT]
    [LEFT]Units = cylinders of 16065 * 512 = 8225280 bytes[/LEFT]
    [LEFT]Disk identifier: 0x000d1481[/LEFT]
    [LEFT][/LEFT]
    [LEFT]   Device Boot      Start         End      Blocks   Id  System[/LEFT]
    [LEFT]/dev/sda1   *           1        1861    14948451   83  Linux[/LEFT]
    [LEFT]/dev/sda2            1862        1949      706860    5  Extended[/LEFT]
    [LEFT]/dev/sda5            1862        1949      706828+  82  Linux swap / Solaris[/LEFT]
    [LEFT]

ants@ants-laptop:~$ sudo hdparm -Tt /dev/sda1[/LEFT]
    [LEFT][/LEFT]
    [LEFT]/dev/sda1:[/LEFT]
    [LEFT] Timing cached reads:   1096 MB in  2.00 seconds = 547.53 MB/sec[/LEFT]
    [LEFT] Timing buffered disk reads:  126 MB in  3.00 seconds =  41.97 MB/sec[/LEFT]
    [LEFT][/LEFT]
   
  
Performance is good, I will soon plug in the old failing HDD to do a comparison speed test.

I have tonight added this

                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         ants@ants-laptop:~$ sudo sysctl vm.swappiness=1
    [LEFT]

vm.swappiness = 1[/LEFT]
   
  

I'm very happy with it, totally silent, and hopefully much better battery life too :)

My only request is if someone could help me find where the config file is to permantly change the swappiness, and also explian a way to turn journeling off in ext4.

Many thanks
Ants

---

