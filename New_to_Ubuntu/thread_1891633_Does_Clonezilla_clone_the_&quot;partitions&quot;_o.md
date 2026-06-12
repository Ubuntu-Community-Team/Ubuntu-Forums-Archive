---
title: "Does Clonezilla clone the &quot;partitions&quot; on a drive?"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by mikodo on 2011-12-06
Hi,

Will Clonezilla, clone my HD, with all the "**same partitons"** when I put it on another drive to hold, while I replace out the original, with a new one? I just want to be sure!

The Drive: (sudo fdisk -l)

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432       38914   293038081    5  Extended
/dev/sda5            2432       38119   286658067+  83  Linux
/dev/sda6           38184       38914     5859328   82  Linux swap / Solaris
mikodo@mikodo-desktop:~$ 

Thanks!

---

### Post by Bucky Ball on 2011-12-06
"... allows you to do bare metal backup and recovery."

I'm thinking so but hopefully an experienced Clonezilla user can chime in ...

---

### Post by lukeiamyourfather on 2011-12-06
Clonezilla will do whatever you ask it to. If you ask it to clone all of the partitions then that's what it will do. Are you wanting to know how to do that?

[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

---

### Post by mikodo on 2011-12-06
> **lukeiamyourfather said:**
> Clonezilla will do whatever you ask it to. If you ask it to clone all of the partitions then that's what it will do. Are you wanting to know how to do that?

[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

[http://www.whenpicsfly.com]("http://www.whenpicsfly.com/")



Thanks!

I will read your links very carefully! First time switching out a drive and using Clonezilla too.

I also thought, [this ]("http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/")newbish guide, would be helpful.

Edit: I guess the second link is in your sig. LOL

Mike

---

### Post by oklokl on 2011-12-06
No..
backup mbr -> Clonezilla
Husks
Achieve
Some error ->partitions

[http://drbl.org/faq/fine-print.php?path=./2_System/23_Missing_OS.faq#23_Missing_OS.faq](http://drbl.org/faq/fine-print.php?path=./2_System/23_Missing_OS.faq#23_Missing_OS.faq)
&#54620;&#44397;&#50612;&#47196;&#46020; &#50416;&#44192;&#49845;&#45768;&#45796;..
&#50756;&#51204;&#54616;&#44172; partitions&#51012; &#48373;&#44396; &#54616;&#51648; &#47803;&#54633;&#45768;&#45796;.. &#51068;&#48512; &#48520;&#47049; &#54616;&#44172; &#51105;&#55184;&#49688;&#46020; &#51080;&#49845;&#45768;&#45796;..
&#44536;&#44163;&#51008; sysresccd &#46041;&#51068; &#54633;&#45768;&#45796; &#49324;&#50857;&#51088;&#44032; &#49688;&#51089;&#50629;&#51004;&#47196; &#48373;&#44396; &#54616;&#50668;&#50556; &#54633;&#45768;&#45796;..
&#54805;&#53468;&#47564; &#51060;&#47344;&#49688; &#51080;&#49845;&#45768;&#45796;..

&#54616;&#46300;&#51032; &#44221;&#50864; &#47932;&#47532;&#51201;&#51064; &#45796;&#47480; &#54616;&#46300;&#50668;&#50556; &#44032;&#45733; &#54633;&#45768;&#45796;.. another hdd

---

### Post by mikodo on 2011-12-06
> **oklokl said:**
> No..
backup mbr -> Clonezilla
Husks
Achieve
Some error ->partitions

[http://drbl.org/faq/fine-print.php?path=./2_System/23_Missing_OS.faq#23_Missing_OS.faq](http://drbl.org/faq/fine-print.php?path=./2_System/23_Missing_OS.faq#23_Missing_OS.faq)
&#54620;&#44397;&#50612;&#47196;&#46020; &#50416;&#44192;&#49845;&#45768;&#45796;..
&#50756;&#51204;&#54616;&#44172; partitions&#51012; &#48373;&#44396; &#54616;&#51648; &#47803;&#54633;&#45768;&#45796;.. &#51068;&#48512; &#48520;&#47049; &#54616;&#44172; &#51105;&#55184;&#49688;&#46020; &#51080;&#49845;&#45768;&#45796;..
&#44536;&#44163;&#51008; sysresccd &#46041;&#51068; &#54633;&#45768;&#45796; &#49324;&#50857;&#51088;&#44032; &#49688;&#51089;&#50629;&#51004;&#47196; &#48373;&#44396; &#54616;&#50668;&#50556; &#54633;&#45768;&#45796;..
&#54805;&#53468;&#47564; &#51060;&#47344;&#49688; &#51080;&#49845;&#45768;&#45796;..

&#54616;&#46300;&#51032; &#44221;&#50864; &#47932;&#47532;&#51201;&#51064; &#45796;&#47480; &#54616;&#46300;&#50668;&#50556; &#44032;&#45733; &#54633;&#45768;&#45796;.. another hdd
Sorry, I don't follow. 

Are you saying to backup the MBR first with Clonezilla, then use Clonezilla to back up the rest of the drive?

How about installing to the new drive?

Install the MBR first?

Thanks.

---

### Post by oklokl on 2011-12-06
Yes.. new hdd
mbr Recovery ->Clonezilla tools..
Manual Clonezilla Options
Clonezilla Options -> make a partition ->partition Recovery and..next.. Recovery..
&#50696; &#47582;&#49845;&#45768;&#45796;.. Clonezilla &#51060;&#44163;&#51004;&#47196; mbr&#51012; &#48373;&#44396; &#54644;&#50556; &#49324;&#50857;&#51060; &#44032;&#45733; &#54633;&#45768;&#45796;..
&#51200;&#46020; &#54644;&#48372;&#50520;&#45716;&#45824; &#46104;&#51648; &#50506;&#45908;&#44400;&#50836;..

---

### Post by mikodo on 2011-12-06
> **oklokl said:**
> Yes.. new hdd
mbr Recovery ->Clonezilla tools..
Manual Clonezilla Options
&#50696; &#47582;&#49845;&#45768;&#45796;.. Clonezilla &#51060;&#44163;&#51004;&#47196; mbr&#51012; &#48373;&#44396; &#54644;&#50556; &#49324;&#50857;&#51060; &#44032;&#45733; &#54633;&#45768;&#45796;..
&#51200;&#46020; &#54644;&#48372;&#50520;&#45716;&#45824; &#46104;&#51648; &#50506;&#45908;&#44400;&#50836;..
Thank you!

I definitely have to read a little about this first. I do see what you are directing me to do.

Ah! I saw your addition!

:)

---

### Post by mastablasta on 2011-12-06
clonezilla is really powerfull tool, but it's not very user friendly. you will see that when you try it out ;)
 
there are other tools out there that will do the same thing but with a nice GUI, such as Kleo Bare metal backup or Redo backup (both are Ubuntu based)

---

### Post by mikodo on 2011-12-06
> **mastablasta said:**
> clonezilla is really powerfull tool, but it's not very user friendly. you will see that when you try it out ;)
 
there are other tools out there that will do the same thing but with a nice GUI, such as Kleo Bare metal backup or Redo backup (both are Ubuntu based)

Hey, I was just finding out about the complexity of Clonezilla, by following the link posted earlier by oklokl.

Thanks, for the hopefully easier imaging solutions.

---

### Post by mikodo on 2011-12-06
[This]("http://redobackup.org/") looks hopeful; As long as it reproduces a boot-able replica.

---

### Post by mikodo on 2011-12-06
Redo Backup & Recovery, [here]("http://redobackup.org/") is supposed to return the backup to identical hardware. If I change out the drive, will that disqualify using it, because it is different hardware?

I dunno?

---

### Post by Bucky Ball on 2011-12-06
Think identical hardware may mean hard drive same size as old one or larger. Same with Clonezilla. But you better find that out.

---

### Post by Bodsda on 2011-12-06
> **mikodo said:**
> Redo Backup & Recovery, [here]("http://redobackup.org/") is supposed to return the backup to identical hardware. If I change out the drive, will that disqualify using it, because it is different hardware?

I dunno?

This usually means the same PC, same gfx card, same sound card, same RAM same motherboard etc. rather than same hard drive manufacturer. This is so they can more or less expect that if the hardware is the same, the system should boot successfully after a bare metal restore.

Bodsda

---

### Post by mastablasta on 2011-12-06
The backup is just a bit-by-bit image of previous drive. you clone it. so if you clone it for example to external drive and then back to new drive and leave all other hardware intact, it should boot up ok. especially with linux that doesn't have any DRM. windows might get tricky since it checks if you changed any hardware and can nag about it (though not necessarily).

---

### Post by Paddy Landau on 2011-12-06
I have used CloneZilla several times to back up and restore individual partitions, and once to back up and restore an entire disk.

If you ask CloneZilla to back up and restore the entire disk, that is exactly what it will do.

It is not the most intuitive package to use, but it works and is very reliable.

It's not exactly a bit-by-bit clone, as it backs up only the parts of disk that are actually in use. You may have to reformat your swap partition; I'm not sure of that.

---

### Post by mikodo on 2011-12-06
Thank you everyone, for your insights and links.

I had found a web-page about imaging/cloning drives last night, (I don't know the difference between the two; yet) that explained that "different hardware" did not include the drives and listed what it did include, but alas, I cannot find it today. What is important, is that it concurs what you have told me here. It would have been nice to provide a link for it, for anyone else reading this thread, who had the same question, though.

As, I use FLOSS :>) and can afford it, I am going to buy another external HD, to experiment with, to learn [Clonezilla]("http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone") or [Redo]("http://redobackup.org/") to reload my system, on to my new internal HD. Even if I fail this time, it will a good learning experience for the future, as I do more and more networking, where imaging of drives, will be very helpful.

In the event, that I mess up my first imaging to the new internal drive, I will go to plan B; and reinstall 10.04 and bring my /home partition data back using my [Back in Time]("http://backintime.le-web.org/") backup from my other external HD. 

Again; Thank you!

---

### Post by Paddy Landau on 2011-12-06
Good luck! It will be a learning experience, but actually I found Clonezilla to be easy to use.

---

### Post by Shazaam on 2011-12-06
A couple of things...
If you are doing a direct disk-to disk clone make sure the target drive is the same size OR bigger. When done you can resize larger if you need to.
If you do a Linux clone- zero to minor fixable problems going to different hardware (custom video card drivers, maybe lan/wlan too).

---

### Post by mastablasta on 2011-12-07
> **Paddy Landau said:**
> Good luck! It will be a learning experience, but actually I found Clonezilla to be easy to use.
 
 
yah if you don't read all the warnings and just pretend you understand them (if oyu don't). also if you do it right the first time through. if however you make a wrong choice int he process you might need to  do the whole procedure again. setting all the settings. because it uses modules to load.
 
Nothing beats the 2 button (backup & restore) interface. And then a GUI wizzard that shows in the end what you set and where at any point you can return back to previous setting and change it if you feel like it.
 
clonezilla is similary just a set of various porgrammes stuck together. it works, but you need some knowledge about disks and all that. they really do need a better interface and saving on the image size is poinless as if you use a CD you would have 2/3 of it blank (free).

---

