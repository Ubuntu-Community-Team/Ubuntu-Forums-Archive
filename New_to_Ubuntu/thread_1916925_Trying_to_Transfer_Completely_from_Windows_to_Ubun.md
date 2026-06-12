---
title: "Trying to Transfer Completely from Windows to Ubuntu..."
date: 2012-01-29
forum: New to Ubuntu
---

### Post by chughes27 on 2012-01-29
So, at the moment I'm running the newest Ubuntu 11.10 and I absolutely love it. The UI is awesome, and I like how it runs in general. But I do have a few problems with it that I need help with solving...

I use MS Office 2010 a lot in my Windows, and it would be great if I could have that in Ubuntu. I've tried several times to get Office programs with Wine, but haven't found any solutions that would properly install the software.

Along with my Office problem is Adobe software. I use many programs included in Adobe's Master Collection CS5.5, like Flash Builder, Flash Pro, Flash Catalyst, Photoshop, and Illustrator. 

Some help with this would be awesome because I would love to be able to run these programs in my new favorite operating system. :)

---

### Post by 2F4U on 2012-01-29
The path to go for you depends on what hardware you have. If you have a powerful enough computer, a virtual environment such as VirtualBox ([https://www.virtualbox.org/](https://www.virtualbox.org/)) may be the right thing for you. You can install Windows in VirtualBox along with all the applications you need and you can start VirtualBox from Ubuntu, so that Windows runs on top of Ubuntu but you can still use Ubuntu in parallel with Windows.
Another option may be a dual boot configuration with both operating systems installed side by side. In that case you can use just one OS at a particular time and you have to explicitly boot into the other OS.
I've been running Windows XP a couple of time on top of Linux and this is not too bad if you do just some work in Windows but spend the majority of time in Linux.

---

### Post by sanscents on 2012-01-29
Can your Office needs be met by OpenOffice?

---

### Post by sanscents on 2012-01-29
> Another option may be a dual boot configuration with both operating systems installed side by side.

Trouble with this is it takes time to boot up if you switch often, and also Windows can't see the Linux drive, so you can't leave any files on it you may need in Windows.

---

### Post by TheFu on 2012-01-29
To be clear, you love Ubuntu 11.10, but would like to run a few programs that are not native to Ubuntu/Linux?
Those programs are commercial offerings from Microsoft and Adobe.

I'm sorry to say, but some programs designed to run under other operating systems do not run under the stock WINE available.  I'm certain that commercial versions of WINE - either Bordeaux or Crossover-Office are working on these, but may not have solved them for your specific versions.

When it comes to getting programs working under WINE, the WineHQ website is a great resource.  For example, they have instructions for installing MS-Office 2010 32-bit here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336)

and for Photoshop here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)

I don't know whether this will actually solve your specific issues, but it is a start.  These commercial offerings tend to be more user friendly if you are having issues with WINE use:
* [http://www.codeweavers.com/](http://www.codeweavers.com/) 
* [http://bordeauxgroup.com/](http://bordeauxgroup.com/)

Good luck!

---

### Post by HermanAB on 2012-01-29
Howdy,

The Codeweavers version of WINE is easy to use and MS Office works quite well on it:
[http://codeweavers.com](http://codeweavers.com)

---

### Post by Azyx on 2012-01-29
> **2F4U said:**
> The path to go for you depends on what hardware you have. If you have a powerful enough computer, a virtual environment such as VirtualBox ([https://www.virtualbox.org/](https://www.virtualbox.org/)) may be the right thing for you. You can install Windows in VirtualBox along with all the applications you need and you can start VirtualBox from Ubuntu, so that Windows runs on top of Ubuntu but you can still use Ubuntu in parallel with Windows.
Another option may be a dual boot configuration with both operating systems installed side by side. In that case you can use just one OS at a particular time and you have to explicitly boot into the other OS.
I've been running Windows XP a couple of time on top of Linux and this is not too bad if you do just some work in Windows but spend the majority of time in Linux.

I have 2,5GHz Core Duo and 4GB RAM on a 32-bit Ubuntu 10.04LTS with PEA-kernel, and Virtualbox plus W7 work perfectly. But the really important are enough RAM to run Ubuntu and W7 at same time. Use Compis and Expo to switch desktop in a 2x2 configuration and have one desktop with W7 in full screen.

---

### Post by rudihawk on 2012-01-29
Could you not run the windows apps you need in a virtual machine if they don't work on WINE?

---

### Post by aykoola on 2012-01-29
Why not use the Ubuntu's office suite? It does the trick for me. 

The only program a photographer friend of mine told me that doesn't have a good equivalent is Photoshop.

---

### Post by nickelbox on 2012-01-29
> **aykoola said:**
> Why not use the Ubuntu's office suite? It does the trick for me. 

The only program a photographer friend of mine told me that doesn't have a good equivalent is Photoshop.

GIMP seems to be a good alternative for this

---

### Post by Drowz0r on 2012-01-29
> **sanscents said:**
> Can your Office needs be met by OpenOffice?

Or Libre office - my favourite out of the two.

---

### Post by chughes27 on 2012-01-29
Thanks for all the replies everyone!

My computer is a netbook which originally came with Windows XP, and on my XP I used all of the MS Office and Adobe products without a problem. These programs are very important for what I do. 

But, being a netbook, my computer doesn't support hardware virtualization and has only a 1.6 GHz processor. I've tried to use virtual machines on it before and it does not work. So installing the applications in a virtual Windows is not going to work.

I am already dual booting with Windows, and as sanscents said, switching between the two OS's takes time, and the Ubuntu drive cannot be accessed in Windows. Even if I saved all of my files on a drive that can be accessed by both operating systems, the time it takes to switch between the two is really a pissoff. 

So my only real option right now is to actually get these programs in Ubuntu without a virtual OS.

Thanks!

---

### Post by Mark Phelps on 2012-01-29
> **chughes27 said:**
> ...my XP I used all of the MS Office and Adobe products without a problem. These programs are very important for what I do... So my only real option right now is to actually get these programs in Ubuntu without a virtual OS.

Thanks!
Wine will run SOME Windows apps, but not the recent Office version (2010) and not most Adobe products.

If you are dependent on these specific apps on a daily basis, moving to Linux is a really bad idea.

---

### Post by chughes27 on 2012-01-29
I think I may have to stay with windows at least for the most part, but I just love my Ubuntu too much. I used to get a lot of viruses and such on windows but I haven't yet gotten one on Ubuntu. And it just looks so much nicer.

---

### Post by Azyx on 2012-01-29
> **chughes27 said:**
> Thanks for all the replies everyone!

My computer is a netbook which originally came with Windows XP, and on my XP I used all of the MS Office and Adobe products without a problem. These programs are very important for what I do. 

But, being a netbook, my computer doesn't support hardware virtualization and has only a 1.6 GHz processor. I've tried to use virtual machines on it before and it does not work. So installing the applications in a virtual Windows is not going to work.

I am already dual booting with Windows, and as sanscents said, switching between the two OS's takes time, and the Ubuntu drive cannot be accessed in Windows. Even if I saved all of my files on a drive that can be accessed by both operating systems, the time it takes to switch between the two is really a pissoff. 

So my only real option right now is to actually get these programs in Ubuntu without a virtual OS.

Thanks!

I don't think you need any special CPU for Virtualbox, as you need för KVM or other virtual-machine software. I have run XP on a P4 1,4 GHz once in a time with virtualbox.

/Cheers.

---

### Post by chughes27 on 2012-01-29
@ Azyx: do you know if you need hardware virtualization though?

---

### Post by Azyx on 2012-01-29
> **chughes27 said:**
> @ Azyx: do you know if you need hardware virtualization though?

I think that one of the benefit with virtualbox, that you don't need speciufic virt-hardware as for other virt-machines.

---

### Post by sanscents on 2012-01-29
> **Mark Phelps said:**
> If you are dependent on these specific apps on a daily basis, moving to Linux is a really bad idea.

I agree. I'm stuck with needing Windows for documents that are completely compatible with MS Office, which are documents created with MS Office.  There can be really ugly formatting glitches trying to switch between OpenOffice and MS Office, so I've found it best just not to do it if the document needs to be widely shared.  I just don't have the resources to try and get Office to work in WINE and get work done on time as well...no crashes allowed lol.

---

### Post by nickelbox on 2012-01-29
I always have much better luck with Libre Office than Open Office but...

you can always use the online version of Windows Office

[https://office.microsoft.com/en-us/web-apps/](https://office.microsoft.com/en-us/web-apps/)

This allows you to create and edit Word, Excel, and Powerpoint docs online all for free

Take a look at it

---

### Post by sanscents on 2012-01-29
> **nickelbox said:**
> you can always use the online version of Windows Office

[https://office.microsoft.com/en-us/web-apps/](https://office.microsoft.com/en-us/web-apps/)

This allows you to create and edit Word, Excel, and Powerpoint docs online all for free

Take a look at it

I have tried it, and the Skydrive.  Working in a limited version of Word on some sever through your browser does not compare to the full version on your HDD.  Especially if you aren't online while wanting to work.  It depends on the size and complexity of the document, I guess.  Another problem is that I can use it, but someone I have a project with has never used the online versions, or cloud services, etc, which means that option is limited in that way too.

Just my experience :) Thanks

---

### Post by chughes27 on 2012-01-29
So right now I'm using the trial version of Crossover to install Office 2007, and it worked great. Unforunately Crossover doesn't support Office 2010, but 2007 is good enough for me.

---

### Post by Mark Phelps on 2012-01-29
> **chughes27 said:**
> So right now I'm using the trial version of Crossover to install Office 2007, and it worked great. Unforunately Crossover doesn't support Office 2010, but 2007 is good enough for me.

It's not Crossover, it's Wine -- that doesn't support it.

Given that it took CodeWeavers three years to get Wine working well enough to support SOME of Office 2007, by that time, Office 2010 was already out.

So, maybe by the time that Office 2012 comes out, 2010 will be supported -- but only some of it.

As said earlier, if you're really dependent MS apps for day-to-day work, migrating to Linux is a bad idea.

---

### Post by dFlyer on 2012-01-29
The only advice I can give is, if you really want to give up on windows, you need to learn linux tools. I've been runing linux only from the mid 90's and have never looked back. I don't dual boot or anything else. It's linux or nothing. LibreOffice works great for me. Gimp works great. AfterShot Pro, bibble5 and lightzone meets my photography needs, they cost a few buck but again meets my needs. If you really want to dump windows, wipe your computer and only run one linux os until you learn it inside and out like you know windows, just don't expect linux to work the same as windows as it's completely a differant os. Good luck.

---

### Post by chughes27 on 2012-01-29
Just a question, will my Ubuntu run faster if I wipe my hard drive completely of Windows and install only Ubuntu?

---

### Post by sanscents on 2012-01-29
> **chughes27 said:**
> Just a question, will my Ubuntu run faster if I wipe my hard drive completely of Windows and install only Ubuntu?

I don't think so.  They don't interfere with one another while running, and I don't think partitioning affects speed much.

---

### Post by chughes27 on 2012-01-30
Well then I honestly have no reason to remove Windows at this time. I think I'm pretty content with what I have right now.

---

