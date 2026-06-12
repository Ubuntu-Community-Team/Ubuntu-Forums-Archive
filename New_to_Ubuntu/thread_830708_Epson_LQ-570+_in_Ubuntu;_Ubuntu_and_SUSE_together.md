---
title: "Epson LQ-570+ in Ubuntu; Ubuntu and SUSE together"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by robinatsia on 2008-06-16
Hello everyone! I installed Ubuntu a couple of days ago nearly without problems and I already like it very much! :) So I think Windows XP is the very last Windows I'll ever use.
A little problem arose, though: Ubuntu does not see my Epson LQ-570+ printer (while Xeros Phaser 6110 works fine). As much as I understood, this printer should work under Linux well. I looked for suitable package for it using Synaptic Package Manager - but did not find anything . Actually, later I did found a file named  Epson-LQ-570plus-epson.ppd and downloaded it - but I don't have a slightest idea what should I do with it. Could anyone help me out of this trouble? I definitely need this printer working.

An another question: I'd like to install SUSE next to Ubuntu. Not that I definitely need this - but I'm just curious to get to know more than one Linux distribution. As much as I've understood, I need to repartition the hard disk to get room for SUSE. SUSE installer wanted to install itself instead of Ubuntu, so I tried to use Ubuntu's partition editor for resizing the /dev/sdb1. Without a success... Am I right thinking that I am able to repartition the hard disk only before Ubuntu uploads? How can I do this? 

Unfortunately, I do not know much of computers yet - actually not much more than press buttons in my favourite programs to get things done. And I have zero experience in working with partitioning tools...

---

### Post by prshah on 2008-06-16
> **robinatsia said:**
> 
A little problem arose, though: Ubuntu does not see my Epson LQ-570+ printer  later I did found a file named  Epson-LQ-570plus-epson.ppd but I don't have idea what should I do

Am I right thinking that I am able to repartition the hard disk only before Ubuntu uploads? How can I do this? 




To use the PPD, open your firefox browser, and type the following address in the address bar:```
http://127.0.0.1:631
```

That will open CUPS (Common unix printing system) administration page. CUPS will allow you to use a custom PPD file (see attached screenshot) when setting up a printer. I can't give you more specifics, but post back here if you run into any trouble.

== Part 2

Any partitions cannot be altered when they are loaded ("mounted") or in use. To resize your ubuntu partition, boot off the original live CD, then click system-administration-partition manager. When the partition manager screen loads, right click each partition and choose "Unmount" if the option is not greyed out. (For a "swap" partition, the option will be "swapoff" instead of "Unmount". If you have less than 256Mb RAM, better _not_ to "swapoff", but you can make any changes to the swap partition in this case).

You can then resize it as you feel suitable.

But why not let SUSE do the resizing? I don't have any experience of knowledge of SUSE, but I'm sure it will have partition resizing capabilities built in.

---

### Post by robinatsia on 2008-06-16
Greatest thanks, prshah! I managed already install SUSE.

And to my own surprise, I also succeeded in adding the printer. Under Windows, I was not able to set a custom sized paper for it and it seems so that I can not do this under Ubuntu either. Is there any work-around? 

Harri.

---

### Post by robinatsia on 2008-06-16
Well, the printer is added and does print, too - but not what it should. Instead of the content of a file, it prints a senseless row of various symbols...
Harri.

---

### Post by prshah on 2008-06-16
> **robinatsia said:**
> Well, the printer is added and does print, too - but not what it should. Instead of the content of a file, it prints a senseless row of various symbols...


Which indicates that the driver is wrong; eg. wrong PPD. Try to use the PPD you've downloaded, or switch to a standard driver like Epson LX800 (Works on practically every dotmatrix printer known to man).

---

### Post by robinatsia on 2008-06-16
Hmm, I used just this downloaded ppd-file (Epson-LQ-570plus-epson.ppd)... I tried once more, this time choosing the printer name from the drop-down list - with the same result (prints only rows of senseless symbols). :confused:

Is this all OK on this page:

[http://saaretalu.fie.ee/maatriks]("http://saaretalu.fie.ee/maatriks")

Harri.

---

### Post by prshah on 2008-06-16
> **robinatsia said:**
> 
Is this all OK on this page:



Looks OK... try installing a new printer in CUPS, and this time, use Epson LX-800 as the printer driver. Is the printing OK now?

---

### Post by cariboo on 2008-06-16
If you use the printer install wizard you may not have this problem. Go to System-->Administration-->Printing it may detect your printer from the get go. If not just follow the prompts and you should be able to get it working correctly.

Jim

---

### Post by robinatsia on 2008-06-16
> **cariboo907 said:**
>  System-->Administration-->Printing it may detect your printer 
Jim

Unfortunately, it did not. :( Only Phaser 6110 was detected (and as said earlier, works properly)

What about LX 800 driver - it did not make things better. Now the printer refuses to print anything, even senseless symbols.

Picture in CUPS: 

[http://saaretalu.fie.ee/LX800]("http://saaretalu.fie.ee/LX800")

Meanwhile, I tried the printer in WinXP: it works...

Harri.

---

### Post by prshah on 2008-06-17
> **robinatsia said:**
> 
What about LX 800 driver - it did not make things better. Now the printer refuses to print anything, even senseless symbols.



OK change it back to the original PPD you had downloaded. No new ideas...

---

### Post by robinatsia on 2008-06-18
Thanks to prshah for the time and good advices dedicated to the printer problem - but though I learned several useful things, I am still in trouble with my Epson LQ-570+.

It works under WinXP normally, but refuses to print under Ubuntu: prints senseless symbols while using LQ-570+ driver ([http://saaretalu.fie.ee/maatriks](http://saaretalu.fie.ee/maatriks)) and refuses to print anything while using driver for LX-800 ([http://saaretalu.fie.ee/LX800](http://saaretalu.fie.ee/LX800)). Also, I was not able to get it printing under SUSE (I recently bought an another hard disk and now, I have three op-systems installed).

An another printer, Xerox Phaser 6110, was detected without problems and works fine.

Has anyone some more advices? As far as I can not use this printer under Ubuntu, I can not conclusively abandon Windows (which I'm planning to do).
Harri.

---

### Post by prshah on 2008-06-18
> **robinatsia said:**
> 
Has anyone some more advices? As far as I can not use this printer under Ubuntu, 


Just a thought; maybe you should try using the PPD from a mac driver, instead of a windows driver. As far as I understand, the mac is like a second cousin to linux. In fact, the CUPS technology seems to have originated with the mac. (Look at bottom of CUPS admin page).

Just a thought.

---

