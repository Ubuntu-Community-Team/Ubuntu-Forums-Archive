---
title: "Accidentally erased whole disk"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by ideleted on 2013-02-17
I booted into ubuntu installation and i accidentally checked the "Erase disk and install" option and pressed "next". And then I removed my boot usb disk when the installation start. Does that mean I just lost everything in my computer? What should I do now??? I cannot boot into anything now, the system reserve (100mb win7 recovery is also gone)

---

### Post by omeomi on 2013-02-17
You can use the Ubuntu live cd/usb to boot and then you should be able to see whether there is anything left of your files. However, I suspect that you have indeed lost everything by doing this.

If so, you could look into harddisk recovery software to attempt to restore the files (since you have not written new stuff to the disk this might work)

---

### Post by prodigy_ on 2013-02-17
[TestDisk](http://www.cgsecurity.org/wiki/TestDisk) may help recover the partition table. It's in Ununtu repositories so you can easily get it even in the Live environment with **sudo apt-get install testdisk**.

---

### Post by ideleted on 2013-02-17
is it possible to restore windows?

---

### Post by sudodus on 2013-02-17
> **ideleted said:**
> is it possible to restore windows?
If it works to restore the partition table, everything might be OK, including Windows. It depends if some files were overwritten or not.

But these operations are risky, so make a ***backup*** to an external drive! The best backup in this case would be a clone or image of the whole drive. You can use Clonezilla to do it.

This way you can test different ways to recover without losing the data if the first attempts will damage the partitions even more.

---

### Post by ideleted on 2013-02-17
i have no idea how linux work.How do I install TestDisk? Should I use the usb boot drive and choose the run linux without installaion option? Since I cannot boot into window, am i right?

---

### Post by sudodus on 2013-02-17
You can get testdisk in many ways. One is to install it (temporarily) into your Ubuntu install CD/USB drive. Another is to download a repair iso file, and make a bootable drive from it. Testdisk is included in some repair iso files, as you can find out at this link

[[COLOR="Red"]http://www.cgsecurity.org/wiki/TestDisk_Livecd[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

---

### Post by Mark Phelps on 2013-02-17
If testdisk doesn't work, you will need to consider using MS Windows utilities -- as you are trying to recover MS Windows filesystem partitions.

With a working PC, you should download and burn the ISO file for the Minitool Partition Wizard Boot CD.  Then, boot from that CD and see if it will let you choose the Partition Recovery option -- and if so, see if that restores the original partitions.

If that does not work, you will then need to consider using data recovery software to get your data off the drive -- but you will need an external drive (or another drive) to do that.

---

### Post by ideleted on 2013-02-17
[http://imgur.com/HdlplNR.jpg](http://imgur.com/HdlplNR.jpg)

This is what I see in the mini tool

I am doing a full scan with MiniTool Partition Wizard now and looks promising. Thanks you for all the replies!

P.S. After I boot into TestDisk, I stucked in black screen with no LED light.

---

### Post by sudodus on 2013-02-17
> **ideleted said:**
> [http://imgur.com/HdlplNR.jpg](http://imgur.com/HdlplNR.jpg)

This is what I see in the mini tool

I am doing a full scan with MiniTool Partition Wizard now. Thanks for all the replies!
It gives us hope :-) that you see something. But where is the Windows drive?

---

### Post by ideleted on 2013-02-17
> **sudodus said:**
> It gives us hope :-) that you see something. But where is the Windows drive?

[http://i.imgur.com/TiJogZy.jpg](http://i.imgur.com/TiJogZy.jpg)

Is this good?:confused:

---

### Post by sudodus on 2013-02-17
> **ideleted said:**
> [www.imgur.com/TijogZy.jpg](www.imgur.com/TijogZy.jpg)

Is this good?:confused:
File not found. Please upload it again!

---

### Post by ideleted on 2013-02-17
> **sudodus said:**
> File not found. Please upload it again!

I fixed the link
[http://i.imgur.com/TiJogZy.jpg](http://i.imgur.com/TiJogZy.jpg)

---

### Post by sudodus on 2013-02-17
Now you see more. I think you have an important decision in the near future: To decide which trace is from the current Windows partition, that you want to recover (you need to estimate where it starts).

How big was the linux partition? How big was the Windows partition?

---

### Post by ideleted on 2013-02-17
> **sudodus said:**
> Now you see more. I think you have an important decision in the near future: To decide which trace is from the current Windows partition, that you want to recover (you need to estimate where it starts).

How big was the linux partition? How big was the Windows partition?

I am so confused because I unplugged my usb ubuntu installation drive when it starts. As I said, I picked the "Erase and install" option. I was so panic after the second I noticed it which led to me removing the usb.

---

### Post by sudodus on 2013-02-17
If you have a backup of the drive you can try more than once without destroying anything: If necessary recover from the backup and try again.

---

### Post by ideleted on 2013-02-17
[http://i.imgur.com/F78tCwI.jpg](http://i.imgur.com/F78tCwI.jpg)

Did I do anything wrong?

---

### Post by Mark Phelps on 2013-02-17
> **ideleted said:**
> [http://imgur.com/HdlplNR.jpg](http://imgur.com/HdlplNR.jpg)

This is what I see in the mini tool

I am doing a full scan with MiniTool Partition Wizard now and looks promising. Thanks you for all the replies!

P.S. After I boot into TestDisk, I stucked in black screen with no LED light.

That's what it sees NOW.  You need to see if the Data Recovery option will let you look at previous partitions -- it's those you want to recover.

---

### Post by ideleted on 2013-02-17
> **Mark Phelps said:**
> That's what it sees NOW.  You need to see if the Data Recovery option will let you look at previous partitions -- it's those you want to recover.

[http://i.imgur.com/F78tCwI.jpg](http://i.imgur.com/F78tCwI.jpg)
 
This is what I ended up with. I tried to boot but 0xc000000e error.

---

### Post by ideleted on 2013-02-17
> **Mark Phelps said:**
> That's what it sees NOW.  You need to see if the Data Recovery option will let you look at previous partitions -- it's those you want to recover.

I did recovery but I cannot boot now

---

### Post by ideleted on 2013-02-19
Thank you for helping. I gave up on this and Im sticking with ubuntu now

---

