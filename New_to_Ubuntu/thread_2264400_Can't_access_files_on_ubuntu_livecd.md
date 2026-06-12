---
title: "Can't access files on ubuntu livecd?"
date: 2015-02-07
forum: New to Ubuntu
---

### Post by hugalouz on 2015-02-07
Hi, so I'm currently using a ubuntu livecd to try and transfer my files as windows 7 isn't booting. I've mounted my harddrive and found my user folder but when I actually try to open it I get this error:[ATTACH=CONFIG]259783[/ATTACH]

How do I get around this?

Thanks :)

---

### Post by yancek on 2015-02-07
It might be a corrupt filesystem on windows which would prevent mounting.  What happened with windows?  Did you get any warnings/error messages when trying to boot?

---

### Post by Mark Phelps on 2015-02-07
Windows filesystem corruption will typically prevent mounting NTFS partitions in Linux; so, it's more likely that you are encountering hard drive failure as manifested in corrupted sectors.

You would probably do better recovering the files using Windows data recovery apps, but to do that, you'll need to connect the hard drive to a working Windows PC, download and install a data recovery app (like "recuva"), and use that.

---

### Post by Bucky Ball on 2015-02-07
Welcome. You don't mention which version of Windows you are using, but I guess another possibility is you have Win hibernating which locks up the drive (think Win needs to be booting UEFI for this, but not familiar). Perhaps reboot to the BIOS and switch of fastboot or faststart, whatever it's called (not familiar with Win names for things, either!) and try again. This will maybe unlock the drive on the next boot.

This only applies if you are trying to access files on the Windows partition. Bit confused because your title says 'Can't access files on the ubuntu livecd', though. We could be barking up the wrong tree if you are trying to access files from the livecd.  

Good luck. ;)

---

### Post by newb85 on 2015-02-07
There are Linux tools that can be used for recovery of Windows partitions, but as Mark pointed out, Windows tools are generally better suited for this.

---

### Post by hugalouz on 2015-02-07
I get a message that says something like 'Disk read error press ctrl alt del to restart' whenever I try to boot it. I'm not sure how serious the problem is yet but I want to copy my stuff over just to be safe.

---

### Post by Bucky Ball on 2015-02-07
> **hugalouz said:**
> I get a message that says something like 'Disk read error press ctrl alt del to restart' whenever I try to boot it. I'm not sure how serious the problem is yet but I want to copy my stuff over just to be safe.

This is when you're booting Win? Have you tried ctl+alt+del and you circle back to the same error message? You could try [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), but if you have a Win Repair cd I'd try that first.

---

### Post by hugalouz on 2015-02-07
Apparently I have 729 bad sectors so I guess you're right. And okay I'll look into a Windows recovery app, thanks!

---

### Post by JeQhdMD on 2015-02-07
You might try the Knoppix Live linux distro.   Has several tools to repair disks & bad sectors of any OS including windows.   Grab the image (just goto distrowatch.com), burn it to DVD or flash stick.

[http://www.cgsecurity.org/wiki/Damaged_Hard_Disk](http://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

Edit:  additonal info below:  (from  [http://www.brighthub.com/computing/linux/articles/64736.aspx](http://www.brighthub.com/computing/linux/articles/64736.aspx))

[h=3]Knoppix Cannot Fix Physical Hard Drive Errors[/h][COLOR=#000000][FONT=Arial]Almost all computer users know that physical errors cannot be repaired by hard drive utility software. Severe errors on any of the platters may make hard drive replacement necessary. The software that comes with this[ Debian-based distribution]("http://www.brighthub.com/computing/linux/reviews/8683.aspx") can repair boot sectors, write 0s to the hard drive to remove the most persistent viruses, and partition existing hard drives. The GUI based interface makes this task straightforward. You do not need to be a PC expert to use Knoppix&#8217;s utilities. The utilities are straightforward, although a user should know the consequences of what he intends to do before making any changes.[/FONT][/COLOR]

---

### Post by hugalouz on 2015-02-07
> **JeQhdMD said:**
> You might try the Knoppix Live linux distro.   Has several tools to repair disks & bad sectors of any OS including windows.   Grab the image (just goto distrowatch.com), burn it to DVD or flash stick.

[http://www.cgsecurity.org/wiki/Damaged_Hard_Disk](http://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

Edit:  additonal info below:  (from  [http://www.brighthub.com/computing/linux/articles/64736.aspx](http://www.brighthub.com/computing/linux/articles/64736.aspx))

**Knoppix Cannot Fix Physical Hard Drive Errors**

[COLOR=#000000][FONT=Arial]Almost all computer users know that physical errors cannot be repaired by hard drive utility software. Severe errors on any of the platters may make hard drive replacement necessary. The software that comes with this[ Debian-based distribution]("http://www.brighthub.com/computing/linux/reviews/8683.aspx") can repair boot sectors, write 0s to the hard drive to remove the most persistent viruses, and partition existing hard drives. The GUI based interface makes this task straightforward. You do not need to be a PC expert to use Knoppix’s utilities. The utilities are straightforward, although a user should know the consequences of what he intends to do before making any changes.[/FONT][/COLOR]


So should I use the Knoppix thing to recover my data? (apparently my hard drive's status is now 'SOON TO FAIL' so I'm getting worried haha)

---

### Post by hugalouz on 2015-02-07
> **Bucky Ball said:**
> This is when you're booting Win? Have you tried ctl+alt+del and you circle back to the same error message? You could try [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), but if you have a Win Repair cd I'd try that first.

Yeah when I boot Windows 7. Ctrl alt del just takes me to the same screen. For some reason Windows repair disk just stops loading after I choose my language settings so I'll try that link instead.

---

### Post by hugalouz on 2015-02-07
> **Mark Phelps said:**
> Windows filesystem corruption will typically prevent mounting NTFS partitions in Linux; so, it's more likely that you are encountering hard drive failure as manifested in corrupted sectors.

You would probably do better recovering the files using Windows data recovery apps, but to do that, you'll need to connect the hard drive to a working Windows PC, download and install a data recovery app (like "recuva"), and use that.

How do I connect my hard drive to my PC?

---

### Post by JeQhdMD on 2015-02-08
Knoppix has many utility tools.   Check the Knoppix website and forums for additional info (maybe checking youtube also for tutorials).

---

### Post by SeijiSensei on 2015-02-08
> **hugalouz said:**
> How do I connect my hard drive to my PC?

I use a SATA to USB adapter: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002](http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002)

---

