---
title: "Running Windows XP and Ubuntu on a PC"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-01-30
I am new to all of this, although I have used Fedora 14 for about 3 years because I could not reinstall Windows XP, probably due to bad sectors on my hard drive. I recently installed Ubuntu 12.04 LTS. I like Ubuntu very much and would like to keep using it. But I want to run Windows XP sometimes as well, because Linux is not fully supported on some websites. Specifically I seem to be having trouble with JAVA browser plug-ins while in the Ubuntu operating system. And I am just learning about Linux terminal commands, like sudo, etc.

It looks like I have two options: 1) dual booting Ubuntu & Windows XP or 2) a Windows XP Virtual Box in Ubuntu. My questions are mostly about system requirements to do 1) or 2). I want to buy a new hard drive and maybe go up from my current 40 GB to 60 GB. 40 GB with either Windows XP or Ubuntu alone works fine for me. I am not into games or photography or CAD/CAM, so I don't need a lot of memory.

QUESTIONS: Will a 40 or 60 GB hard drive allow me to 1) dual boot Windows XP & Ubuntu 12.04 LTS or 2) Virtual Box WIndows XP in Ubuntu? Or do I need even more hard drive space?

Is 1.25 GB of RAM enough to Virtual Box WIndows in Ubuntu? 1.25 GB of RAM is all I have. 

Is it difficult for a new Ubuntu user to 1) dual boot Windows XP & Ubuntu 12.04 LTS or 2) Virtual Box WIndows XP in Ubuntu?

Thank you,

R.

---

### Post by sudodus on 2014-01-30
Welcome to the Ubuntu Forums :-)

> **RMcGinnis said:**
> I am new to all of this, although I have used Fedora 14 for about 3 years because I could not reinstall Windows XP, probably due to bad sectors on my hard drive. I recently installed Ubuntu 12.04 LTS. I like Ubuntu very much and would like to keep using it. But I want to run Windows XP sometimes as well, because Linux is not fully supported on some websites. Specifically I seem to be having trouble with JAVA browser plug-ins while in the Ubuntu operating system. And I am just learning about Linux terminal commands, like sudo, etc.

It looks like I have two options: 1) dual booting Ubuntu & Windows XP or 2) a Windows XP Virtual Box in Ubuntu. My questions are mostly about system requirements to do 1) or 2). I want to buy a new hard drive and maybe go up from my current 40 GB to 60 GB. 40 GB with either Windows XP or Ubuntu alone works fine for me. I am not into games or photography or CAD/CAM, so I don't need a lot of memory.

Windows XP reaches end of life in April 2014, and after that there will be no security updates. You can keep the system, if you isolate it from the internet, but you can expect a lot of virus and other malware to take the opportunity to attach XP after end of life.
> 
QUESTIONS: Will a 40 or 60 GB hard drive allow me to 1) dual boot Windows XP & Ubuntu 12.04 LTS or 2) Virtual Box WIndows XP in Ubuntu? Or do I need even more hard drive space?

Disk space is rather cheap per gigabyte nowadays. I would say at least 80 GB for a dual boot system or Virtual Box system, if possible at least 120 GB.
> 
Is 1.25 GB of RAM enough to Virtual Box WIndows in Ubuntu? 1.25 GB of RAM is all I have. 

It is enough for dual boot but not for a virtual machine with Window XP. I have run it with 2GB, which was possible, but would actually recommend even more.
> 
Is it difficult for a new Ubuntu user to 1) dual boot Windows XP & Ubuntu 12.04 LTS or 2) Virtual Box WIndows XP in Ubuntu?

Thank you,

R.

There is a learning curve, but if you ask us at the Ubuntu Forums, you will get excellent help ;-) so no worries :-P

I think dual boot is easier than Virtual Box, but not that much. If you cannot get more RAM, Virtual Box is a bad choice anyway.

---

### Post by squakie on 2014-01-30
+1 on the Windows XP warning.  I have just converted a few people from XP to xubuntu (just Ubuntu with a different desktop manager).  So far for them (none are into playing games, cad, etc.) that has worked well for them.

As sudous stated, then end of life for XP is very close, and the proverbial "flood gates" will be open then for all kinds of attacks - viri, trojans, rootkits, etc. - to infest any XP installation.  Sudous mentioned keeping it isolated from the internet as about the only way to stop this.  However, since you are talking about websites not working correctly, this may not be an option for you.  Either way, I would try my hardest to stay away from XP at the end of March onward. 

Sudous mentioned the support you can get here on the forums.  They are 110% on that.  They, and many others, have provided me with countless answers to my questions and problems.  So each time you run into something that doesn't seem to be working correctly, please open a thread here and just wait for help - it will come.

I am forever grateful for the help I have received here.  I hope your ubuntu experience is as wonderful as mine has been.

---

### Post by AbleTassie on 2014-01-31
Thank you very much Sudodus and Squakie,

I have a better idea what I need now. Looks like I need a lot more RAM or Hard Drive space, unless I can use a peripheral USB hard drive to dual boot (see below). And it looks like Windows XP is a dead end. And there sure are a lot of complaints about Windows 8. I'll have to look hard & double-check to see if there are some Windows work arounds. I'll consult the Ubuntu help and forums to see about this. Maybe I can forget about Windows altogether. If the worst comes I suppose I could upgrade to Windows Vista or Windows 7  ---- I don't want Windows 8.

Since I need a lot more hard drive space to dual boot, would it be possible to dual boot using a peripheral hard drive that connects to a USB port? I have a 160 GB Seagate peripheral drive that connects to a USB port. I use it for back up, but after several years it still has over 100 GB of free space on it. And I could free up even more space on it by cleaning it out and using some other back up methods. 

QUESTION: Is there any way I can use this peripheral 160 GB hard drive to get the extra space needed to dual boot if necessary? 

By the way, the most RAM I can possibly get is 2.05 GB by changing the RAM chips. I have 1.25 GB of RAM now.

Thanks again for your help,

R.

---

### Post by sudodus on 2014-01-31
> **RMcGinnis said:**
> Thank you very much Sudodus and Squakie,

I have a better idea what I need now. Looks like I need a lot more RAM or Hard Drive space, unless I can use a peripheral USB hard drive to dual boot (see below). And it looks like Windows XP is a dead end. And there sure are a lot of complaints about Windows 8. I'll have to look hard & double-check to see if there are some Windows work arounds. I'll consult the Ubuntu help and forums to see about this. Maybe I can forget about Windows altogether. If the worst comes I suppose I could upgrade to Windows Vista or Windows 7  ---- I don't want Windows 8.

If you need Windows after XP end of life, I would recommend Windows 7, which is better on most hardware than Vista.
> 
Since I need a lot more hard drive space to dual boot, would it be possible to dual boot using a peripheral hard drive that connects to a USB port? I have a 160 GB Seagate peripheral drive that connects to a USB port. I use it for back up, but after several years it still has over 100 GB of free space on it. And I could free up even more space on it by cleaning it out and using some other back up methods. 

QUESTION: Is there any way I can use this peripheral 160 GB hard drive to get the extra space needed to dual boot if necessary? 

By the way, the most RAM I can possibly get is 2.05 GB by changing the RAM chips. I have 1.25 GB of RAM now.

Thanks again for your help,

R.

Yes, it is possible to use a USB mass storage device (pendrive, HDD, SSD) to boot your Ubuntu based operating system. A HDD is much better than most pendrives, because the flash memory is often slower than the USB 2 interface. But it will be much slower than an internal disk.

After housecleaning (removing unnecessary files) you can use ***gparted*** booted from an Ubuntu boot CD/DVD/USB pendrive and edit the partition table. And finally, you can install Ubuntu into a partition that you created with gparted.

Many people boot installed linux systems from USB nowadays. That way you can carry your system in a pendrive or small USB disk and boot it into most computers, because Ubuntu and many other linux systems are portable. Due to licensing issues, Windows cannot be installed into a USB disk.

-o-
In order to give really relevant advice, we need more specific data about your computer

- Brand name and model of computer or motherboard
- CPU
- RAM size we know, 1.25 GB, (max possible 2 GB with makes it possible to run Windows in VirtualBox)
- graphics chip/card

And what about your internet connection, is it fast or slow?

This would make it possible to suggest which / how many versions and flavours of Ubuntu to try.

---

### Post by mastablasta on 2014-01-31
> **RMcGinnis said:**
> QUESTION: Is there any way I can use this peripheral 160 GB hard drive to get the extra space needed to dual boot if necessary? 

By the way, the most RAM I can possibly get is 2.05 GB by changing the RAM chips. I have 1.25 GB of RAM now.



it seems you have an older maschine with probably ATA (IDE) disks. newer disk use SATA to connect. you might have a port for those available. hard to say we would need to know the model of motherboard to get that info from internet.

ram is porbably ddr or ddr2 which is quite expencive these days. but if you can increase it with no investment then do it. otherwise leave it be.

yes you can dual bootusing USB drive. you would need to install (probably Ubuntu) to it. then make sure during install that GRUB is put on external drive and then only set the BIOS to boot from USB first.

another option is to move most data to external drive and do dual boot on internal drive. if you don't have too many programmes installed then winxp will do just fine with about 20 GB disk space and you can leave the rest for Ubutnu. i had (until recently) a 5GB partition with win XP on it. had about 700 MB free. in the end it was corrupted by malware it seems. but i had most programs on other partition.

you could run XP in virtualbox but you would need to use lighter desktop enviromnment (such as the one foiund in lubuntu). it would free up more ram for you to use for XP mashcine + virtualbox.

---

### Post by Rishav khatri on 2014-01-31
I had this same situation and once had mistakenly deleted entire data on my hdd. After the loss all i had left was knowledge and experience to install ubuntu the correct way. Dual boot is helpful rather than running on VM's.

---

### Post by AbleTassie on 2014-01-31
> **sudodus said:**
> If you need Windows after XP end of life, I would recommend Windows 7, which is better on most hardware than Vista.
[SIZE=3]
[COLOR=#0000ff]Thanks Sudodus, I will keep this in mind. Answers to your questions are below in blue.[/COLOR][/SIZE]


Yes, it is possible to use a USB mass storage device (pendrive, HDD, SSD) to boot your Ubuntu based operating system. A HDD is much better than most pendrives, because the flash memory is often slower than the USB 2 interface. But it will be much slower than an internal disk.

After housecleaning (removing unnecessary files) you can use ***gparted*** booted from an Ubuntu boot CD/DVD/USB pendrive and edit the partition table. And finally, you can install Ubuntu into a partition that you created with gparted.

-
In order to give really relevant advice, we need more specific data about your computer

- Brand name and model of computer or motherboard
- CPU
- RAM size we know, 1.25 GB, (max possible 2 GB with makes it possible to run Windows in VirtualBox)
- graphics chip/card
[SIZE=3][COLOR=#0000ff]
Toshiba Satellite L25-S1216 Intel Celeron M Processor 380 1.60 GHZ, 1MBL2, 400MHZ FSB
ATI Radeon Express 200M Chipset, 

Graphics ATI Radeon Xpress 200M 32MB-128MB dynamically allocated shared graphics memory[/COLOR][/SIZE] 

[SIZE=3][COLOR=#0000ff]My external Seagate 160 GB drive is USB 2.0, 5400 RPM compatible with Windows XP and Vista. But I have used it with Fedora 14 and Ubuntu and it seems to work fine. I think I bought it in 2008.[/COLOR][/SIZE]

And what about your internet connection, is it fast or slow?

[SIZE=3][COLOR=#0000ff]DSL, I just checked it today: 1.31 Mbps Download speed, 0.72 Mbps upload speed[/COLOR][/SIZE] 

This would make it possible to suggest which / how many versions and flavours of Ubuntu to try.
 
[SIZE=3][COLOR=#0000ff]I don't want you (and others) to spend a lot of time on this, but if you can give me some answers without spending a lot more time on this, great. It will be nice to know I can dual boot if necessary with Windows 7 and Ubuntu. I am going to look into workarounds using Linux/Ubuntu that do not require Windows. I was doing more research on this and I am more optimistic I can get away without needing Windows. I've been using Fedora 14 for almost 3 years and I really haven't missed Windows XP that much. And I've been using Ubuntu for a few days and I like it even more than Fedora 14.  

Thanks again so much, [/COLOR][/SIZE]
:P[SIZE=3][COLOR=#0000ff]
Bob[/COLOR][/SIZE]

---

### Post by AbleTassie on 2014-01-31
[QUOTE=mastablasta;12915443]it seems you have an older maschine with probably ATA (IDE) disks. newer disk use SATA to connect. you might have a port for those available. hard to say we would need to know the model of motherboard to get that info from internet.

[SIZE=3][COLOR=#0000ff]Hi Mastablasta, Thanks. Yes I have an older machine circa early 2006. Specs just given in my reply to Sudodus.[/COLOR][/SIZE] 

ram is porbably ddr or ddr2 which is quite expencive these days. but if you can increase it with no investment then do it. otherwise leave it be.

[SIZE=3][COLOR=#0000ff]Yes, I think it is DDR2[/COLOR][/SIZE]

yes you can dual bootusing USB drive.

[SIZE=3][COLOR=#0000ff]That's good to know.[/COLOR][/SIZE]

 you would need to install (probably Ubuntu) to it. then make sure during install that GRUB is put on external drive and then only set the BIOS to boot from USB first.
[SIZE=3][COLOR=#0000ff]
Thanks for the link to the manual. I just downloaded the manual. I really like the Linux story, and I think I could work well with the Linux community. Microsoft & Windows is OK, but it has its limitations.

Thanks again, [/COLOR][/SIZE]
;)[SIZE=3][COLOR=#0000ff]
R.[/COLOR][/SIZE]

---

### Post by sudodus on 2014-02-02
> **RMcGinnis said:**
> Toshiba Satellite L25-S1216 Intel [COLOR=#ff0000]Celeron M Processor[/COLOR] 380 1.60 GHZ, 1MBL2, [COLOR=#ff0000]400MHZ FSB[/COLOR]
ATI Radeon Express 200M Chipset, 

Graphics ATI Radeon Xpress 200M 32MB-128MB dynamically allocated shared graphics memory 

My external Seagate 160 GB drive is  USB 2.0, 5400 RPM compatible with Windows XP and Vista. But I have used  it with Fedora 14 and Ubuntu and it seems to work fine. I think I  bought it in 2008.

And what about your internet connection, is it fast or slow?

DSL, I just checked it today: 1.31 Mbps Download speed, 0.72 Mbps upload speed 

-o-

I don't want you (and others) to spend a lot of time on this, but if you can give me some answers without spending a lot more time on this, great. It will be nice to know I can dual boot if necessary with Windows 7 and Ubuntu. I am going to look into workarounds using Linux/Ubuntu that do not require Windows. I was doing more research on this and I am more optimistic I can get away without needing Windows. I've been using Fedora 14 for almost 3 years and I really haven't missed Windows XP that much. And I've been using Ubuntu for a few days and I like it even more than Fedora 14.  

Thanks again so much, 
:P
Bob

I think Celeron M with 400 MHz FSB has PAE capability but might lack a PAE flag. If this is the case, you need a non-pae kernel or to use fake-pae. See these links, that offer ways to install and run current versions of Ubuntu (and Ubuntu community flavours, re-spins and distros based on Ubuntu).

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)[URL="http://ubuntuforums.org/showthread.php?t=2172971"]
One Button Installer, 'OBI'[/URL]

The external drive will work with 'any' linux. There are issues with some Radeon cards, but chances are it will work well either with the built-in driver or a proprietary driver. Some intitial problems can be fixed with a [boot option]("https://help.ubuntu.com/community/BootOptions"), for example nomodeset.

Booting and running from an internal drive is much faster than from a USB 2 drive. But both work the same way with linux (speed is the only difference).

The computer has neither horsepower nor memory enough to run Windows in a virtual machine.

---

### Post by cigtoxdoc on 2014-02-02
All my PCs are setup for dual-boot Ubuntu 12.04 and Win XP Pro SP3.  I need to have the XP for some applications for which there is no good Ubuntu alternative (Avery Design Pro, Adobe Acrobat Pro 9.5, and some meetings that I need to watch live with Adobe Connect.  My basic approach to adding Ubuntu to an XP system is first to make an image backup of the XP system using Macrium Reflect and a 500 GB Passport USB drive.  I then partition the drive to give me enough space for the Ubuntu and all programs and data files I need to use.  Then load the Ubuntu in the unused partition.  I have sometimes had to use the Boot-Repair program to setup Grub correctly.  Ubuntu will still let you access the partition with Win XP.  Mine shows up under /media/OS.  I have the XP side protected with VIPRE Internet Security and Malabytes Anti-Malware.

The big gotcha here is moving files from the XP side to the Ubuntu side.  Ubuntu thinks that you should not be able to use them.  You have to go through excessive (my opinion) contortions to get file ownerships and permissions correct.

John

---

### Post by mörgæs on 2014-02-03
I don't think there's a PAE problem here. In order to be sure please post the results from 
```
sudo lshw -C cpu
```
in CODE tags.

---

### Post by AbleTassie on 2014-02-04
Thanks Sudodus and everybody. You've been very helpful.

R.

---

### Post by AbleTassie on 2014-02-04
> **mörgæs said:**
> I don't think there's a PAE problem here. In order to be sure please post the results from 
```
sudo lshw -C cpu
```
in CODE tags.

See below, pae seems to be included:

*-cpu                   
       description: CPU
       product: Intel(R) Celeron(R) M processor         1.60GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.13.8
       slot: U23
       size: 1600MHz
       capacity: 1600MHz
       width: 32 bits
       clock: 100MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts

---

### Post by sudodus on 2014-02-04
Great, you are not suffering from the non-pae CPU problem :-) I was suspecting it because of the data in red '[COLOR=#ff0000]'Celeron M Processor[/COLOR] 380 1.60 GHZ, 1MBL2, [COLOR=#ff0000]400MHZ FSB[/COLOR]'. So I think it would work well to install Lubuntu 13.10 from the desktop iso file, or a light-weight flavour, re-spin or distro based on Ubuntu 12.04 LTS.

---

### Post by AbleTassie on 2014-02-04
OK great, thanks to everybody.

R.M.

---

### Post by mörgæs on 2014-02-04
If this solves your problem please mark the thread so.

---

### Post by AbleTassie on 2014-02-06
Just a follow-up question on this topic. I think I'd like to get a larger hard drive that will allow a dual boot of Windows 7 and Ubuntu, since Windows XP will no longer be supported soon. Will a new hard drive cache size and RPM speed really matter?

 

 BACKGROUND: I want to buy a new hard drive for my TOSHIBA Satellite L25-S1216 (Intel Celeron M Processor 380 1.6 GHz, IMB L2, 400 MHz FSB, ATI Radeon XPRESS 200M Chipset, 1.25 GB DDR2 SDRAM). I currently have a TOSHIBA MK4026GAX Hard Drive (40 GB 5400RPM, Enhanced IDE ATA-6, Cache 16MB) with 20 bad sectors.

  
 IN THIS THREAD I have been advised that I need a larger hard drive to be able to dual boot Windows 7 and Linux (Ubuntu or Mint): at least 80 GB preferably 120 GB. I only work with small files: Word & PDF docs, email, internet browsing, etc. I am not into games, photography, CAD/CAM, etc.

  
 I am not convinced going up to a 7200 RPM drive will make any noticeable difference in performance. Hard drives larger than 40 GB, especially those larger than 60 GB, all seem to have cache (buffer) sizes of 8MB, less than my current hard drive's 16MB.
  
 QUESTION(S): If I buy a larger hard drive (>40GB) with a smaller cache (8MB) will I notice a decrease in speed?
  
 Does a 7200 RPM drive really offer me any advantages over a 5400 RPM drive?
  
 (I know 7200 drive use more power and wear out faster).
  
 Thanks,
  
 R.

---

### Post by sudodus on 2014-02-06
I would not buy a fancy drive for such an old computer. I think it would be OK with a 5400 RPM HDD. I don't know how much difference the cache size would make.

---

### Post by AbleTassie on 2014-02-06
Thanks Sudodus,

One of my motivations for wanting to dual boot is that some people I sent Open Office (odt) files to (when I was using Fedora 14) could not open them with Windows. It seemed that even if I converted the Open Office files to MS WORD files they still could not open the files.

QUESTION: Do you think that people being unable to open (or use) Libre Office files (Writer, Calc or Impress) in Ubuntu is (or will be) a common problem?

Thanks,

R.

---

### Post by sudodus on 2014-02-07
> **RMcGinnis said:**
> Thanks Sudodus,

One of my motivations for wanting to dual boot is that some people I sent Open Office (odt) files to (when I was using Fedora 14) could not open them with Windows. It seemed that even if I converted the Open Office files to MS WORD files they still could not open the files.

QUESTION: Do you think that people being unable to open (or use) Libre Office files (Writer, Calc or Impress) in Ubuntu is (or will be) a common problem?

Thanks,

R.
My experience is that files written as doc (Microsoft document format) are possible to read with Microsoft Word. Remember that there are several doc format versions (corresponding to several Word versions, and people with old versions of Word cannot read new versions of doc files (and docx files).

It is very easy to ***export the documents as pdf*** files from Libreofffice (and OpenOffice), and I prefer to send documents (as well as publish documents) in pdf format. Then there is almost never any problems to read them.

I have similar experiences with the other open document formats (for spreadsheets and presentations). If you send ***documents, that are not finished, but should be edited by other people***, you cannot send pdf documents. Then it can be a good idea to have dual booting with ***Windows*** or Windows in a virtual machine or Windows in a separate old machine ***in order to test*** that files you want to send can be read by people with [that version of] Windows and Microsoft Office.

---

### Post by mastablasta on 2014-02-07
the compatibility with MS producs is also constantly improving. just a few releases ago i had a strangely imported  .docx file. but now that same file imports just fine.

---

### Post by AbleTassie on 2014-02-07
[SIZE=3]Yes I have used pdf documents when people could not read odt files. But I don't have the software to encrypt pdf files. And sometimes I want to send encrypted odt files, and it is a problem when people can't open these encrypted odt files with MS Word -- I have to forget the encryption. 

So maybe if here is no easy solution to encryption, I will pursue the double boot option. 

Any comments anybody has will be welcomed.

Thanks,

R.
[/SIZE]

---

### Post by mastablasta on 2014-02-07
if PDF is an option then when you go to file->export as PDF you will get a dialog box. you can go to security tab there and then encrypt and lock the file with password. you can also set up different kind of permissions there. for example they can print it but not comment it etc. or printing not allowed etc.

otherwise Office 2007 works nicely in wine. well there are a only a few things that don't work nice, but i don't use them anyway... i think it's those premade organisation graphs (but you can make them yourself) and something in powerpoint. anyway i set up 2007 for a user. they use mostly Word and Excell. And so far no issues reported. it could be that the issues reported on wine appdb were already resolved. as i didn't get them when i tried to replicate them.

Yet another option is Kingsoft office. A Chinese MS Office copy. Beta verison is working well in linux. it looks like MS office 2013, but they do have classic view.

my point is - only for MS office dual boot is not really worth it especially if mostly you only use Excel, Powerpoint and Word. Outlook, Access, Groove and such is a different matter.

but if you have more windows specific widnows programes then it makes sense to dualboot.

---

### Post by sudodus on 2014-02-07
> **RMcGinnis said:**
> [SIZE=3]Yes I have used pdf documents when people could not read odt files. But I don't have the software to encrypt pdf files. And sometimes I want to send encrypted odt files, and it is a problem when people can't open these encrypted odt files with MS Word -- I have to forget the encryption. 

So maybe if here is no easy solution to encryption, I will pursue the double boot option. 

Any comments anybody has will be welcomed.

Thanks,

R.
[/SIZE]

Mastablastas reply is good, and I only want to add a little comment about encryption.

There are many ways to encrypt files. If you send files that need encryption, I suggest that you use a method that is suitable for that particular purpose.

[I][B]- ordinary level of security
[/B][/I]
The encryption of Microsoft Office files is rather simple, and if you consider it enough, you can use some other simple encryption, for example ***zip*** with a password. The intelligence organizations of big countries can easily decrypt it, but maybe you can live with that.

```
man zip
```

The option -e activates encryption.

```

       -e
       --encrypt
              Encrypt  the contents of the zip archive using a password which is entered on the termi&#8208;
              nal in response to a prompt (this will not be echoed; if standard error is  not  a  tty,
              zip  will  exit  with  an error).  The password prompt is repeated to save the user from
              typing errors.
```

Your colleagues can run some ***built-in utility in Windows*** to decrypt/encrypt zip-files, or for example Winzip. But if they encrypt with Winzip's advanced encryption, you will not be able to decrypt it with ***zip***.

***- high level of security***

Otherwise you can use ***gpg***, which is already installed in Ubuntu (and used for installing and updating program packages). There is a terminal window interface (also in Windows) and you can get graphical user interfaces. For example, you and your colleagues can install ***enigmail*** in ***Thunderbird***, and that way you can send and receive encrypted mails in a convenient way. The most difficult part is to make your colleagues install enigmail.

```
man gpg
```

---

### Post by AbleTassie on 2014-02-07
A great big thank you to everybody for their responses! I have saved the responses for future reference as well.

R.

---

### Post by sudodus on 2014-02-08
You are welcome :-)

Please ask again, until you have solved your problems, and then click **Thread Tools** at the top of the page and mark this thread as SOLVED!

---

### Post by AbleTassie on 2014-02-10
I just want to ask one more question. I have weighed everybody's responses about WINE, PlayOnLinux, Virtual Boxing, Dual Booting, Open Office & Word docs, encryption of pdfs, Chinese versions of MS WORD, etc. THANKS TO EVERYBODY!! 

I am at the point of buying a new hard drive. I think I'd like the computer to be able to dual boot, but probably will be using Ubuntu most of the time. 

QUESTION: Would a 100GB hard drive be OK to dual boot Linux and WIndows XP, if I am am not into a lot of fancy stuff? (I've been told 80GB is possible, 120GB preferable-- I think I can get 100GB drive reasonably)

By fancy stuff I mean games, photography, CAD/CAM, etc. It's unlikey I'll be using MS Outlook, etc. I would just pretty much use simple email, internet browsing, Open Office & MS Word docs, PDF docs. 

Thanks,

P.S. It's kind of fun to use Linux, correspond with the forums, etc. and I am close to marking this thread SOLVED per Sudodus's instructions.

Thanks,

R.

---

### Post by sudodus on 2014-02-11
> **RMcGinnis said:**
> 
QUESTION: Would a 100GB hard drive be OK to dual boot Linux and WIndows XP, if I am am not into a lot of fancy stuff? (I've been told 80GB is possible, 120GB preferable-- I think I can get 100GB drive reasonably)


Yes, I think 100 GB will be fine for you dual booting an Ubuntu flavour plus Windows XP. Remember to

- Start by making partitions

- Then install Windows

- Finally install Linux

Good luck :-)

---

### Post by monkeybrain20122 on 2014-02-11
> **RMcGinnis said:**
> I am new to all of this, although I have used Fedora 14 for about 3 years because I could not reinstall Windows XP, probably due to bad sectors on my hard drive. I recently installed Ubuntu 12.04 LTS. I like Ubuntu very much and would like to keep using it. But I want to run Windows XP sometimes as well, because Linux is not fully supported on some websites. Specifically I seem to be having trouble with JAVA browser plug-ins while in the Ubuntu operating system. And I am just learning about Linux terminal commands, like sudo, etc.

.

Which websites are you talking about? Usually all you need to access such websites is a good user-agent-switcher addon for the browser. You can also install Oracle's Java if Openjdk somehow doesn't work for you, though I have never had the need. [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by Bill Tetzeli on 2014-02-11
Can you post links to some of the websites that you say aren't working for you in Ubuntu 12.04 LTS?  It may be either that there is more up to date Java support that allows these sites to be viewed properly that 12.04 isn't privy to (just like GIMP 2.8 can't be installed on any Ubuntu prior to 13.04) or possibly when you installed Ubuntu you forgot to check the box to install third party plugins.  If that's the case then either you can install those plugins from the Software Center or you can upgrade to the latest Ubuntu version; then you would truly be free to give MS the old heave-ho.

---

### Post by monkeybrain20122 on 2014-02-11
> **Bill Tetzeli said:**
> ..just like GIMP 2.8 can't be installed on any Ubuntu prior to 13.04..

You can, with a ppa [https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp) or you can compile it yourself (which I did) :)

---

### Post by Bill Tetzeli on 2014-02-11
I LOVE compiling.  Tracking down a program's dependencies.. and the dependencies' dependencies.. and the dependencies' dependencies' dependencies...  It's like a nonstop Easter egg hunt. :P

---

### Post by AbleTassie on 2014-02-11
Sdodus, thanks for all your help. Thanks also to everybody including Mastablasta, MonkeyBrain and others,

I also used the [http://www.webupd8.org]("http://www.wbeupd8.org") to install Oracle's JAVA and that worked fine. I was able to enter and use the websites in question after using [http://www.webupd8.org]("http://www.wbeupd8.org"). Bill, one of the websites I was having problems with was Webex.com and their online meeting function. You need JAVA to host or join a meeting. You can get a free basic WebEx account and try to host or join a meeting yourself.

I am interested in "giving MS the old heave ho" and I probably won't be using Windows much. But I may give the computer away in a couple of years, and the party I give the computer to may not be as interested in using Ubuntu as I presently am. They may also not have the ability to, or interest in, consulting these type forums and/or really using Ubuntu as I do.  



Thanks,

R.

---

### Post by Bill Tetzeli on 2014-02-11
You're welcome.  Good luck, and enjoy the freedom. :-)

---

### Post by sudodus on 2014-02-11
You are welcome :-)

Remember that Windows XP reaches end of life in April this year. After that it will receive no security updates. Even if *you* can manage it being very careful, I would not give the computer with a vulnerable operating system to someone who might not understand how to avoid getting the computer 'hacked'.

---

