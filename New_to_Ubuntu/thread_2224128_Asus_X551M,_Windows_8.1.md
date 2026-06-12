---
title: "Asus X551M, Windows 8.1"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by ashley6 on 2014-05-14
Does anyone know how I can just delete Windows 8.1 from my computer and install Ubuntu.  I am a little computer literate but just cant figure out how to install Ubuntu without Virtual Box.

---

### Post by Magnezone150 on 2014-05-14
A couple of questions you may want to answer first before installing it on your computer:

1. What Computer do you have? Or Make/Model? (For Example Lenevo Thinkpad T400)

2. Which Version of Ubuntu will you be installing? Or Why can't you get it working on Virtual Box?

---

### Post by The Cog on 2014-05-14
You need to create a boot DVD or boot memory stick. Then boot that with your computer. The installer has an option to erase the entire disk.

[https://www.google.co.uk/search?q=how+to+create+ubuntu+installer](https://www.google.co.uk/search?q=how+to+create+ubuntu+installer)

---

### Post by ashley6 on 2014-05-14
I have an Asus X551M.  I can't get my computer to boot from disk. I have disabled uefi.  I havent installed virtual box yet.  I just want to rid myself of Microsoft for good.

---

### Post by verymadpip on 2014-05-14
Hi there.
Before you get rid of Microsoft for good I'd suggest you make *absolutely certain *there's nothing you can *only *do with Microsoft or applications that will only run in Windows.

I dual boot for exactly this reason.

---

### Post by monkeybrain20122 on 2014-05-14
> **verymadpip said:**
> Hi there.
Before you get rid of Microsoft for good I'd suggest you make *absolutely certain *there's nothing you can *only *do with Microsoft or applications that will only run in Windows.

I dual boot for exactly this reason.

Well if OP can install Ubuntu in VM he can do the same for Windows if he needs it. Forget about dualboot "just in case", it is a pain to maintain a dualboot with Windows 8 because you have to tiptoe around all these secure boot uefi bs. I would give OP a high five instead of a warning. :)

---

### Post by oldfred on 2014-05-14
See this thread with a similar Asus and Intel chip.
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)

Best to make a full image backup of Windows. Then if you want to sell system you can restore it to Windows. Or if you have some application, work, school or game that only works with Windows you have a way to restore it without having to pay for a new copy of Windows that costs almost as much as your entire computer.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by monkeybrain20122 on 2014-05-14
> **oldfred said:**
> 
Best to make a full image backup of Windows. Then if you want to sell system you can restore it to Windows. 


Hmm.. that is very thoughtful but I am not sure if I sell a computer I have to put an OS on it. I am not an OEM. I sold a few either with Ubuntu or no OS, some guy got a used computer on criaglist with XP on it plus the virus and porn, ended up having to erase the whole thing. :)  And I bet many people who sell used windows laptops on craiglist etc with bundled Office and what not got the software and probably even the OS from torrent. :)

---

### Post by whitesmith on 2014-05-14
I took the Linux plunge back in 2008 and never looked back. I didn't back anything up (except music and documents) because everything else was discardable. The problem with dual boot is that it creates technical problems as well as psychological dependency. Dual boot PCs are obviously more likely to develop problems than 100% pure Linux systems--additional complexity assures that. Even systems that don't are a crutch that whispers "You can do it in Windows!" to those who should be looking for a native Linux solution to their problem. After a while, newcomers will simply ignore the Linux installation in favor of the more familiar Windows. I keep a Windows box around for the occasional program that requires it. Otherwise I'm pure Linux and never looked back. I don't have to worry about viruses or malware or adware or rootkits because I'm using an OS that keeps the bad guys at bay. Computing is fun again. What more could one ask for? Viva Ubuntu!

---

### Post by Magnezone150 on 2014-05-15
Hi Ashley,

First things first. to get rid of Windows for Ubuntu.
Find out the boot menu or go into your Computers BIOS with either the Esc or F2 button
Then look for any of the following:

- Enable Boot Menu
- Enable CSM

And in the boot tab look for:

- Boot Order and make the system boot CD and USB first before Hard drive
- Disable Fast Boot

Then F10 Save and Quit
Then Reboot Computer and boot on to the Ubuntu and continue with install

---

### Post by stalkingwolf on 2014-05-15
if this is a new computer and you bought it at Best Buy installing Ubuntu could void your warrenty.

---

### Post by verymadpip on 2014-05-15
> **monkeybrain20122 said:**
> Well if OP can install Ubuntu in VM he can do the same for Windows if he needs it. Forget about dualboot "just in case", it is a pain to maintain a dualboot with Windows 8 because you have to tiptoe around all these secure boot uefi bs. I would give OP a high five instead of a warning. :)

I tend to agree on the whole.
I was going to suggest win8.1 in a VM - do we know if OP has install media for that?

However, I do some gaming.  If someone can help me to get Call of Duty Ghosts, MW3, MW2 & CoD4 to run in Ubuntu, plus my handful of other games not available on the Linux platform, then we're away ;)

How many times have we seen people erase a Windows install only to find they can no longer do something mission critical?
All of my "everyday" computing is done with Ubuntu (or Xubuntu).
I expect when I tire of playing the "problem" games Windows will be a thing of the past for me too.

I don't mean to be an a@*$, please accept my I apology if I have.

---

### Post by monkeybrain20122 on 2014-05-15
> **stalkingwolf said:**
> if this is a new computer and you bought it at Best Buy installing Ubuntu could void your warrenty.

That is a toughy. Well if you dual boot it would void your warranty too so what do you suggest? I suppose you can make a restore disc just in case but it is rather tedious. Personally I never do that.

---

### Post by monkeybrain20122 on 2014-05-15
> **verymadpip said:**
> 

I don't mean to be an a@*$, please accept my I apology if I have.

No need for apology, I am the one who often behave badly. :) We are just expressing opinions here. 

Personally I will never recommend dual boot unless there is a real need for it and the vm route for some reasons is not feasible (games, not enough ram etc) I don't agree with the idea of keeping Windows around "just in case you may need it " and especially for Windows8. MS doesn't like dualboot and does everything to make it difficult,--and when things blow up on their faces some users of course will blame Linux for it, see many hreads here. So instead of tip toeing around all the problems and restrictions that dualbooting with Windows entails I would just erase Windows from the hard disk if it is not needed

---

### Post by The Cog on 2014-05-15
> **monkeybrain20122 said:**
> Hmm.. that is very thoughtful but I am not sure if I sell a computer I have to put an OS on it. I am not an OEM. 
You don't have to be an OEM to sell a second hand computer with the same os (serial munber, activation code etc.) that it was bought with. 

oldfred is suggesting taking an image of the disk to restore later, not installing a different copy of windows. Seems like a good idea to me to be able to restore the computer to its original state. For sale, warranty return, or just a change of heart. I still have the original image of my netbook as delivered, just in case. Not that I expect to ever use it.

---

### Post by monkeybrain20122 on 2014-05-15
> **The Cog said:**
> You don't have to be an OEM to sell a second hand computer with the same os (serial munber, activation code etc.) that it was bought with. 

oldfred is suggesting taking an image of the disk to restore later, not installing a different copy of windows. Seems like a good idea to me to be able to restore the computer to its original state. For sale, warranty return, or just a change of heart. I still have the original image of my netbook as delivered, just in case. Not that I expect to ever use it.

I was half joking with the OEM reference. My point still stands though, I don't think I am obliged or expected to sell my old computer with the OS it came with or any OS at all.

---

