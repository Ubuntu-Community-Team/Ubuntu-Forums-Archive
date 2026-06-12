---
title: "NEED ADVISE : Coming from Windows to Ubuntu desktop"
date: 2018-04-11
forum: New to Ubuntu
---

### Post by hbkhari on 2018-04-11
Dear All,

I decided to use Ubuntu Linux desktop OS as primary(keen to use Linux :-). I have been using windows OS ever since I learned about computers, so please allow me to ask some questions.


I have around 350 GB of NTFS files on my old laptop and I already took backup them and anytime ready to erase and install Ubuntu desktop OS completely.


Before doing that I want to clear some doubts.


1. Is it possible to have a separate partition with NTFS format only so that I can access\connect my friends pendrive\hardisk( read\write) whenever I want or keep all my old files?

2. I have few licensed software purchased on windows platform. Is there any way\method to install them on my Ubuntu OS( Eg. MS word, VCE exam )


Please welcome me to Linux world and thanks to advise\guide me.

---

### Post by monkeybrain20122 on 2018-04-11
> **hbkhari said:**
> Dear All,

I decided to use Ubuntu Linux desktop OS as primary(keen to use Linux :-). I have been using windows OS ever since I learned about computers, so please allow me to ask some questions.


I have around 350 GB of NTFS files on my old laptop and I already took backup them and anytime ready to erase and install Ubuntu desktop OS completely.


Before doing that I want to clear some doubts.


1. Is it possible to have a separate partition with NTFS format only so that I can access\connect my friends pendrive\hardisk( read\write) whenever I want or keep all my old files?

2. I have few licensed software purchased on windows platform. Is there any way\method to install them on my Ubuntu OS( Eg. MS word, VCE exam )


Please welcome me to Linux world and thanks to advise\guide me.

1. You can store your old files in drive formatted to ext4 or NTFS. It odesn't matter, Linux can access both.

2. Depends on the software but I think for most such software you need a new license even if you upgrade Windows on same machine or change your hardware configuration (like shrinking or expanding your Win partition), so answer is probably no even if software works in wine or VM (well unless you crack it somehow), but then it may not even run.

---

### Post by Impavidus on 2018-04-11
1: Not sure what you mean by NTFS files. NTFS is a file system, the files themselves don't care whether they're on an NTFS or ext4 partition. So you can simply copy all old files from your backup drive to the internal hard drive (now formatted ext4) after you installed Ubuntu. Ubuntu can read/write NTFS, so you can plug in an NTFS formatted usb drive and access all files on it read/write. However, Ubuntu is not very good at repairing NTFS partitions. It may get damaged, for example by dirty shutdown, and then you need Windows to fix it. So it's not a good idea to use NTFS on the internal hard drive of a computer that has no Windows installed.

2: Usually, you can't. The best thing to do is find a Linux alternative. Libreoffice is installed by default and is quite similar to MS Office (or at least, it was the last time I used it, which is quite a while ago).

---

### Post by kurt18947 on 2018-04-11
Your life will be simpler if you keep a Windows install. There are Windows programs for which there simply isn't a good Linux alternative. In my own case I have a requirement to write data to a proprietary data card. The data vendor doesn't even appear to know that there are desktop operating systems other than Windows and certainly is not about to support them. So I only use Windows about 10 minutes every 28 days but can't practically get along without it.

You could search terms such as "Linux alternative to ________ software" i.e. Linux alternatives to Photoshop" or "Open source alternatives to Photoshop". There is also Wine which seems to work pretty well for Microsoft Office a couple generations old for example. You could look at Winehq.com for supported programs. There is a paid version of Wine at codeweavers.com that should include some support. I have no dealings with them so don't really know.

---

### Post by mastablasta on 2018-04-11
> **Impavidus said:**
> 
2: Usually, you can't. The best thing to do is find a Linux alternative. Libreoffice is installed by default and is quite similar to MS Office (or at least, it was the last time I used it, which is quite a while ago).

Libre Office is not similar at all. you can install it on Windows and see for yourself. however it does provides descent (but not 100%) file compatibility with MS Office files.

A more similar office suite is WPS office, but last time i tried it, it looked similar but the compatibility was worse than with Libre office. 


MS office until 2013 works kind of OK in Wine/Playonlinux (or if you are willing to pay for even better Linux compatibility then get Crossover). 2010 and 2007 work best. maybe 2013 works just as good nowadays.
MS office 365 can work in any browser on any operating system. of course that version is a bit more limited. again depending on what you do in it, the browser version might be more than enough.

in general windows based programs work best on native Windows OS. 

As others suggested Linux occasionally has alternatives available for some applications. while sometimes (particularly the opensource apps) you will find Linux as well as windows version of the app (e.g. VLC, Libre office, blender, kdenlive, shotcut...)

---

### Post by Impavidus on 2018-04-11
> **mastablasta said:**
> Libre Office is not similar at all. you can install it on Windows and see for yourself. however it does provides descent (but not 100%) file compatibility with MS Office files.

Now you see how long I haven't used MS Office. I vaguely remember their user interfaces were similar and neither of them was particularly good at doing what I intended. Anyway, I don't have a Windows box, so I at least won't try. OP can try if he wants.

OP: I suggest you don't try and switch completely to Ubuntu at once. You'll probably be disappointed. Best is if you've got two computers. Keep one Windows, convert the other to Ubuntu. Dual booting is another option, but that hasn't become easier in recent years. But as you say you want to use Ubuntu as primary (implying there will be a secondary), I assume you already thought about that.

---

### Post by monkeybrain20122 on 2018-04-11
> **mastablasta said:**
> 
A more similar office suite is WPS office, but last time i tried it, it looked similar but the compatibility was worse than with Libre office. 



WPS looks like an Adware to me, never use it on Linux but have tried to install on my Dad's Windows machine, full of ads and nagging to buy license, deleted it later and installed LibreOffice. (**Edited:** but just check out deepen Linux which comes with WPS preinstalled, surprisingly doesn't have the ads and the nagging like the Windows version)

The only way to solve the "compatibility problem" is to ditch MSO. MSO is not even compatible with older versions of itself for crying out loud so why do we have to play MS's stupid captive upgrade game to be "compatible"? It says it supports ODF now, so ODF is what I use and never get any complaint, in fact no one even asked what the hell it is, just assume they are WORD.  Having said that, I have never had a problem with reading docx or xslx in LO. I suspect that it works most of the time unless you have very oddly formatted documents. Only snag I hit was trying to open a very big xlsx file with Calc and it truncated the number of columns to 1024. But I doubt that your average home user will deal with EXCEL sheets with more than 1024 columns. In any case, gnumeric opened the file and exported it to .csv with no issue.

---

### Post by monkeybrain20122 on 2018-04-11
> **kurt18947 said:**
> Your life will be simpler if you keep a Windows install. There are Windows programs for which there simply isn't a good Linux alternative

Setting up and maintaining a Windows dualboot for Win > 7 is anything but simple. If OP must have a Windows install I think VB is the way to go. But keep in mind that any dualboot or VM will likely void the licenses for his Win software as the hardware is modified.

---

### Post by Mark Phelps on 2018-04-12
Some comments ...

1. regarding the old files -- while you certainly CAN keep an NTFS-formatted partition around to retain the Windows files, 350GB is a LOT of files -- and if were me, I would transfer those to an external drive and remove all but the most essential ones from the PC.

2. regarding Windows apps -- as already mentioned, the only MS Office apps that work reasonably well are really old versions.  Office 2007 and 2010 work fairly well in Wine as long as you stick to the basic components like Word and Excel.  Office 2013 takes a lot of work and newer versions simply do NOT work.  So, if you're really going to use Linux as PRIMARY, then you need to say goodbye to the MS Office apps.

Laptops are notoriously BAD choices in terms of Linux compatibility due to the OEMs taking shortcuts with specialized hardware in order to keep their costs down -- and in most cases, there are simply no Linux drivers that work with that hardware.  You need to create Linux install media and use the "Live" mode to boot your laptop to see what actually works.  Anything that does not work is going to range from easy (i.e. Linux drivers exist) to impossible (i.e., Linux drivers do NOT exist) to fix.

---

### Post by monkeybrain20122 on 2018-04-12
> **Mark Phelps said:**
> 
Laptops are notoriously BAD choices in terms of Linux compatibility due to the OEMs taking shortcuts with specialized hardware in order to keep their costs down -- and in most cases, there are simply no Linux drivers that work with that hardware.  You need to create Linux install media and use the "Live" mode to boot your laptop to see what actually works.  Anything that does not work is going to range from easy (i.e. Linux drivers exist) to impossible (i.e., Linux drivers do NOT exist) to fix.

Totally disagree. I have had ONLY laptops all my life (none of my friends own desktops, not for single people who live in a rm and move a lot) and have been using Linux exclusively on all my personal machines since around 2010 and never had a problem. These laptops cover quite a large spectrum  and most of them just work (some required a few tweaks). Now if you say there are some wifi or graphic cards that tend to cause problems or some models are bad for Linux compatibility then no argument from me, but as a general statement, no, totally disagreed.

---

### Post by madtaxman on 2018-04-13
As a relatively new-to-Ubuntu Linux user myself, welcome. I have found that the community is very giving and forgiving. But before you ask a question you must put in some research on your own.  I have wanted to ask the community for help twice. But I did not need to: in researching the question I not only found my answer but learned a heck of a lot from the trip.

---

### Post by kurt18947 on 2018-04-15
Re dual booting, a non-UEFI machine with an SSD works pretty well :D. UEFI (generally machines that came with Win8 or newer) apparently varies a lot by manufacturer. It sounds like some HPs are very difficult for example. I've run Win10 in a VirtualBox VM and it worked pretty well. I only used that setup for a few hours but Win10 was mostly functional without activating it.

---

### Post by Mark Phelps on 2018-04-17
> **kurt18947 said:**
> ... I only used that setup for a few hours but Win10 was mostly functional without activating it.

MS doesn't publicize how often a PC checks with their Activation Servers, but my guess would be no more often than once every 24 hours -- which is probably why yours never complained about activation -- as it was not connected to the Internet long enough.

Eventually, it would have become deactivated, even though that might have taken a couple of days.

Win10 does not come with a "grace period" as did older Windows versions.

---

### Post by bsodx on 2018-04-17
> **Impavidus said:**
> Now you see how long I haven't used MS Office. I vaguely remember their user interfaces were similar and neither of them was particularly good at doing what I intended. Anyway, I don't have a Windows box, so I at least won't try. OP can try if he wants.

OP: I suggest you don't try and switch completely to Ubuntu at once. You'll probably be disappointed. Best is if you've got two computers. Keep one Windows, convert the other to Ubuntu. Dual booting is another option, but that hasn't become easier in recent years. But as you say you want to use Ubuntu as primary (implying there will be a secondary), I assume you already thought about that.

Dualbooting took a week for me to set things up, but works good on me. Indeed, it includes some tough job,but still the best alt for a single PC owner wants to convert.

---

### Post by QIII on 2018-04-17
I'm not sure why, in the normal course of things, a dual boot should take more than at most a couple of hours for a first attempt.

30 minutes for someone who has done it a time or two.

---

