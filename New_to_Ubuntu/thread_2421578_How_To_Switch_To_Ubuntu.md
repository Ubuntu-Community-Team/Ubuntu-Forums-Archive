---
title: "How To Switch To Ubuntu?"
date: 2019-06-24
forum: New to Ubuntu
---

### Post by yuvi19 on 2019-06-24
What is the best way to switch from windows to Ubuntu and what are the limitations and advantages of Ubuntu over windows?

Yuvi

---

### Post by Impavidus on 2019-06-24
That's a very broad question. It may be best if you have more than one computer. Convert one to Ubuntu, keep the other on Windows as you may encounter some tasks that you can't solve in Ubuntu – at least, not yet.

On Ubuntu you'll have more freedom to use the computer as you please, the system is less heavy (depending on configuration), leaving more resources for your application, and it's far more resistant to malware, even without devoting half your resources to anti-malware stuff. The downsides: Ubuntu (or Linux in general) has less support from hardware manufacturers, which often means poorer drivers for exotic hardware, commercial software is often unavailable for Ubuntu and to effectively use your new freedom, you need some technical knowledge. Note that there are also applications that run on Ubuntu, but not on Windows. Those applications are rare though, mostly limited to obscure scientific software.

For most software you can find acceptable open source alternatives, but there may be cases where your co-workers/boss have allowed themselves to get locked-in in some commercial application that's unavailable for Ubuntu. That's not very wise, but hard to fix. I've even heard of cases (not in my country) where the tax service required people to use software that only runs on Windows (and possibly Mac), so that could be a problem.

---

### Post by crip720 on 2019-06-24
With Ubuntu and most Linux they have a 'try' mode on the ISOs, so you can download and put it on a USB stick and see if you like it and everything works with your computer.  You don't have to install anything to your hard drive, till you are happy.  Linux updates the OS and all of your software when needed for you, and the updates usually only take a minute or two to complete.  You will be asked to restart sometimes, but it will only be when you want and it only takes about a minute to shutdown and restart and you are ready to go.  Non of this nonsense of having to install updates before shutdown and configure everything after restart, ubuntu is down and up in a minute, ready to go.

---

### Post by grenic on 2019-06-24
Good afternoon Yuvi,

I have just done what you are asking and have done so successfully! I have upgraded from Windows 10 PRO to Ubuntu 18.04 this morning.

Here is a useful tutorial that you can follow to create a bootable Ubuntu USB stick: [URL="https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows"]https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows
[/URL]
If you are on Ubuntu you can use this tutorial: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)

I am yet to explore all the useful technologies available to me via Ubuntu. @Impavidus does have extremely valid points regarding software integration Windows VS Ubuntu.

Good-luck and most importantly, enjoy!

Greg

---

### Post by mastablasta on 2019-06-24
Limitations:
 - it can run only some windows software; most windows software won't work
- it has worse hardware support (drivers) than windows
- it often requires user to solve (what should be trivial) problems on their own or with the help of community
- it can feel unpolished, rough, clunky (e.g. upgrades won't work, insane defaults in some cases, it doesn't behave as intended or predicted)
...


Advantages:
- it gives user freedom to do what they want with their hardware
- amazingly, it can even run some Windows software
- community as well as developers will help new users; you are encouraged to file bugs (see filing bugs on how to do it), so that they can fix them for everyone
- it is a lot lighter on system resources and works a lot faster than windows (even on old PC); software developed for linux OS is also a lot faster it seems.
- no restarts needed after updates (see Ubuntu Livepatch for more info), but if you do them, they are super fast even on regular HDD; updates can be deferred or simply turned off (not recommended --> at least keep security patches on)
- EXT4 file system doesn't require any defragmentation; more advanced file systems that offer imaging (& restore) can be used (e.g. BTRFS, ZFS4Linx...)
- proper file encryption
- desktop can be turned easily into server OS and vice versa
- open source
- if properly configured (Ubuntu hardening), it can be a lot safer OS than windows (more barriers, lower exposure...)
...


If you have a PC that is relatively capable i would suggest you try a virtualbox install first (go with the 18.04 LTS version, if you have a very new PC then try the 19.04). see how it works, what it can do. next try a live session, to see if it works reasonably well on your PC. note that there are several flavours to try out (several desktops). i prefer KDE (Kubuntu) since it is similar in look&feel to windows and provides a GUI for most system and other settings. i really like a good GUI on a desktop PC.

when you are ready for install, backup your current files and OS (you can use clonezilla to create an image) and if possible make an install as dual boot (i assume you are using windows) on a separate hard disk (e.g. secondary hard disk or external drive). if this is not possible, prepare a part of unformated disk space in windows and install there. in any case read up on dual boot before you do that.

---

### Post by j2ee on 2019-06-25
> **Impavidus said:**
> That's a very broad question. It may be best if you have more than one computer. Convert one to Ubuntu, keep the other on Windows as you may encounter some tasks that you can't solve in Ubuntu – at least, not yet.

On Ubuntu you'll have more freedom to use the computer as you please, the system is less heavy (depending on configuration), leaving more resources for your application, and it's far more resistant to malware, even without devoting half your resources to anti-malware stuff. The downsides: Ubuntu (or Linux in general) has less support from hardware manufacturers, which often means poorer drivers for exotic hardware, commercial software is often unavailable for Ubuntu and to effectively use your new freedom, you need some technical knowledge. Note that there are also applications that run on Ubuntu, but not on Windows. Those applications are rare though, mostly limited to obscure scientific software.

For most software you can find acceptable open source alternatives, but there may be cases where your co-workers/boss have allowed themselves to get locked-in in some commercial application that's unavailable for Ubuntu. That's not very wise, but hard to fix. I've even heard of cases (not in my country) where the tax service required people to use software that only runs on Windows (and possibly Mac), so that could be a problem.

For a lot of Microsoft Word/Excel/PointPower document, it would be totally broken everything move to wrong place if using open source stuff to open it. That is not something Ubuntu can do. For over 90% people go to office to work that is something we need to deal with every single day. Yeah Ubuntu is great for personal use, for office...not really except the whole office is like a lab a lot of people use Linux for research, that kind of working environment.

---

### Post by QIII on 2019-06-25
There are many, many companies that use Linux in the Enterprise.

It's not the fault of the Linux community that Microsoft Office does not work on Linux, nor is it the Linux community's fault that the open source alternatives to Microsoft Office cannot perfectly deal with proprietary Office document formats.

Do you have any purpose here other than being a provocateur, j2ee?

---

### Post by cruzer001 on 2019-06-25
"*switching from windows to ubuntu*
Search that phrase, that will keep you busy for a while :)

Also your computer specifications are a consideration.  You can have a OS that is tailored to operate on your computer specs.

Live DVD/USB will allow you to try whatever OS you want without installing anything to your system.

---

### Post by j2ee on 2019-06-25
> **QIII said:**
> There are many, many companies that use Linux in the Enterprise.

It's not the fault of the Linux community that Microsoft Office does not work on Linux, nor is it the Linux community's fault that the open source alternatives to Microsoft Office cannot perfectly deal with proprietary Office document formats.

Do you have any purpose here other than being a provocateur, j2ee?

I am just telling the truth, it doesn't matter who's fault or why. More than 90% of people who go to work would need to get work done with Microsoft documents. It is just a fact. I cannot work on a complicated word document with open source office and expect my boss seeing the same format with his Microsoft word.

---

### Post by cruzer001 on 2019-06-25
@j2ee
"?Open source office?"  How can you comment on software without even knowing the package name?

I have used MS Word at the office and LibreOffice at home, they interact for me just fine.

My reason for MS at work is simple.  Linux support is not included in the IT contract and therefore not allowed on the office network.

---

### Post by QIII on 2019-06-25
> **j2ee said:**
> I am just telling the truth, it doesn't matter who's fault or why. More than 90% of people who go to work would need to get work done with Microsoft documents. It is just a fact. I cannot work on a complicated word document with open source office and expect my boss seeing the same format with his Microsoft word.

And?

Does this mean that Linux cannot be used in the office or in the enterprise by others?  What about as a web server?  Internet backbone servers?  CNC manufacturing? Big iron?  Supercomputers?  Your cell phone?  Bank servers? Robotics?  Steam OS?  Roku?  Smart TVs?  Smart watches?  Amazon's Kindle?  In-car entertainment?  In-flight entertainment?  Signage?  Your car's computers?  Air Traffic Control?  

What about some organizations like the New York Stock Exchange?  Google.  IBM.  Twitter. Amazon. McDonald's. London Stock Exchange.  Oracle (a billion dollar company).  Novell.  Facebook.  NASA.  CERN.  Burlington Coat Factory. Peugeot.  Dreamworks Animation. The Chicago Mercantile Exchange.  [Do you ever interact with any of these companies]("https://www.linuxfoundation.org/membership/members/")?

Many have a bias towards thinking "computer" = "desktop" because that is the tip of the iceberg they see.  The desktop is only a small part of the world of computing.  And of that small part, office productivity suites are a small subset. But it is certainly true that people have come to rely on many applications that have been designed for Windows.  So?  Is there anything in any law that forbids using both?

There are more devices running Linux than Windows by at least an order of magnitude.

Here's someone who could not do without Linux:  You.  In point of fact, the content you are receiving on your PC would not be getting to you without Linux.  Whether they know it or not, everyone uses Linux.

So let's just stop being disingenuous.  Such behavior attracts the attention of the Forum Staff.

---

### Post by j2ee on 2019-06-25
> **QIII said:**
> And?

Does this mean that Linux cannot be used in the office or in the enterprise by others?  What about as a web server?  Internet backbone servers?  CNC manufacturing? Big iron?  Supercomputers?  Your cell phone?  Bank servers? Robotics?  Steam OS?  Roku?  Smart TVs?  Smart watches?  Amazon's Kindle?  In-car entertainment?  In-flight entertainment?  Signage?  Your car's computers?  Air Traffic Control?  

What about some organizations like the New York Stock Exchange?  Google.  IBM.  Twitter. Amazon. McDonald's. London Stock Exchange.  Oracle (a billion dollar company).  Novell.  Facebook.  NASA.  CERN.  Burlington Coat Factory. Peugeot.  Dreamworks Animation. The Chicago Mercantile Exchange.  [Do you ever interact with any of these companies]("https://www.linuxfoundation.org/membership/members/")?

Many have a bias towards thinking "computer" = "desktop" because that is the tip of the iceberg they see.  The desktop is only a small part of the world of computing.  And of that small part, office productivity suites are a small subset. But it is certainly true that people have come to rely on many applications that have been designed for Windows.  So?  Is there anything in any law that forbids using both?

There are more devices running Linux than Windows by at least an order of magnitude.

Here's someone who could not do without Linux:  You.  In point of fact, the content you are receiving on your PC would not be getting to you without Linux.  Whether they know it or not, everyone uses Linux.

So let's just stop being disingenuous.  Such behavior attracts the attention of the Forum Staff.

The post starter also asked about gaming in another post which means he or she just wants to install the desktop version. For a non IT person it is good for him or her to know the Microsoft stuff issue for daily life before he or she makes a choice.

---

### Post by mastablasta on 2019-06-26
i agree that users installing at home are likely interested in desktop version, and they are likely not contemplating to setup a supercomputer in their room. though you never know.

Office suite:
- Office 365 works on Linux (in browser).
- Some office versions can also be installed in wine (2013 and older).
- MS office can save in open office format and should be the same when you open it in Libre. On the other hand not everyone in the world is using MS Office. In Asia they often have other Office suites. so best way to exchange files is in PDF. while excel files do not really need design. while the formulas should be translatable. all in all there are compatibility test files, so one can see what translates perfectly (form MS office forma to open format) and what does not.

---

### Post by Impavidus on 2019-06-26
> **j2ee said:**
> For a lot of Microsoft Word/Excel/PointPower document, it would be totally broken everything move to wrong place if using open source stuff to open it. That is not something Ubuntu can do. For over 90% people go to office to work that is something we need to deal with every single day. Yeah Ubuntu is great for personal use, for office...not really except the whole office is like a lab a lot of people use Linux for research, that kind of working environment.That's precisely what I mean by getting locked-in in some commercial application. But as long as you don't use too fanciful layouts in Word (which tend to give poor results anyway), it seems to work reasonably well.

> **mastablasta said:**
> i agree that users installing at home are likely interested in desktop version, and they are likely not contemplating to setup a supercomputer in their room. though you never know.

Office suite:
- Office 365 works on Linux (in browser).
- Some office versions can also be installed in wine (2013 and older).
- MS office can save in open office format and should be the same when you open it in Libre. On the other hand not everyone in the world is using MS Office. In Asia they often have other Office suites. so best way to exchange files is in PDF. while excel files do not really need design. while the formulas should be translatable. all in all there are compatibility test files, so one can see what translates perfectly (form MS office forma to open format) and what does not.I'm all for exchanging in pdf as long as no further editing is required. If further editing is required, I prefer plain text.

---

### Post by ajgreeny on 2019-06-26
And what about the old RTF filetype?

A huge percentage of text documents presently saved as .docx could very easily use RTF instead and lose practically nothing in layout or formatting, yet I seldom see such files these days, and I'm as guilty as the next person.  I do not generally save documents as .doc or .docx, however, as I never have reason to do so unless sending files to MS-Office users.

---

### Post by uRock on 2019-06-26
> **cruzer001 said:**
> I have used MS Word at the office and LibreOffice at home, they interact for me just fine.

Same here.

---

### Post by jfpolacko on 2019-07-08
Sorry a week late but I have to comment on this as well. I work for Autozone and THEY as well use Linux for our computers! Right now they moved from OpenSuse to Oracle Linux. So many enterprise's use Linux everyday. I also made the complete jump to Ubuntu Mate from Win 10 as I have always loved using Linux over Windows and so far I haven't had a issue opening up a couple of Word doc's I had using Libre Office. Anyways that was my two cents. 



> **QIII said:**
> And?

Does this mean that Linux cannot be used in the office or in the enterprise by others?  What about as a web server?  Internet backbone servers?  CNC manufacturing? Big iron?  Supercomputers?  Your cell phone?  Bank servers? Robotics?  Steam OS?  Roku?  Smart TVs?  Smart watches?  Amazon's Kindle?  In-car entertainment?  In-flight entertainment?  Signage?  Your car's computers?  Air Traffic Control?  

What about some organizations like the New York Stock Exchange?  Google.  IBM.  Twitter. Amazon. McDonald's. London Stock Exchange.  Oracle (a billion dollar company).  Novell.  Facebook.  NASA.  CERN.  Burlington Coat Factory. Peugeot.  Dreamworks Animation. The Chicago Mercantile Exchange.  [Do you ever interact with any of these companies]("https://www.linuxfoundation.org/membership/members/")?

Many have a bias towards thinking "computer" = "desktop" because that is the tip of the iceberg they see.  The desktop is only a small part of the world of computing.  And of that small part, office productivity suites are a small subset. But it is certainly true that people have come to rely on many applications that have been designed for Windows.  So?  Is there anything in any law that forbids using both?

There are more devices running Linux than Windows by at least an order of magnitude.

Here's someone who could not do without Linux:  You.  In point of fact, the content you are receiving on your PC would not be getting to you without Linux.  Whether they know it or not, everyone uses Linux.

So let's just stop being disingenuous.  Such behavior attracts the attention of the Forum Staff.

---

### Post by bunny9000 on 2019-07-11
I'm just going to say for the Ops benefit if they have even the slightest computer knowledge to install Virtualbox. Create a virtual machine, give it 1GB RAM, 2x cpu cores, install Ubuntu from the ISO and play with it on the computer. Install wine, install dosbox (for old games). Play around with the avaialble software for a few months and see if it's possible to live with the new OS. You can't test much gaming in the virtual machine.

Do not wipe out the windows installation unless you do a full image using something like macrium reflect free and make a rescue disk (from reflect) so you can go back to widows if the computer gets messed up or you want to easily revert to windows only. Ubuntu installer is pretty good at shrinking your existing drive to put ubuntu on the same disk 'next' to windows so having windows and Linux dual booted is an option if some games are needed that won't work on Linux. 

I think some older games like doom 3, quake 4, unreal, ut2k4, quake 3 area, etc work in Linux. Probably best to have an nvidia gpu (but those listed games where tested using a low end amd gpu) plus anything that can run in dosbox emulator will probably run in Linux or scummvm (another emulator). Don't think stuff from origin work in Ubuntu, but I've not tried installing the app in Wine so that means no mass effect.

I think with office it's the advanced features like collaboration, etc. Libre does the basic office docs / docx.

As for Linux in Business. While Ldap is OK - I do love active directory and group policies for a windows servers and pcs plus most sysadmins know AD. Ldap is more specialist and people demand more money.

---

### Post by mastablasta on 2019-07-12
> **jfpolacko said:**
> Sorry a week late but I have to comment on this as well. I work for Autozone and THEY as well use Linux for our computers! Right now they moved from OpenSuse to Oracle Linux. So many enterprise's use Linux everyday. I also made the complete jump to Ubuntu Mate from Win 10 as I have always loved using Linux over Windows and so far I haven't had a issue opening up a couple of Word doc's I had using Libre Office. Anyways that was my two cents.

not to mention they also use old MS office version which are also often "incompatible" with current microsoft "open" document "*standard*". in other words if you open old office file things might be misaligned. seen that in the files form my customers as well as old archived .doc or .xls files we sometimes need to open.

aditionally our ERP is exporting in .xls or RTF for the most part. these are also not fully compatible with office 365. yet still i can get the job done. i wonder how...

---

### Post by hk42 on 2019-07-13
Hi
I'm new to Ubuntu too.
First there is no need to switch.
Having 2 or more operating systems on a computer is a real advantage:
Ubuntu ability to be tested without installing is another one.
Recent hardware can be difficult to run on Linux.
Not so old hardware can be impossible to run on recent Windows versions.
Buying something that you don't use is a bad thing.
Linux can be very useful to repair Windows.
The opposite is not true :P

---

