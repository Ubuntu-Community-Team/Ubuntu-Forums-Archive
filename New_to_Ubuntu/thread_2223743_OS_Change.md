---
title: "OS Change"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by jonathan71381 on 2014-05-12
If I erased Windows 8 and put Ubuntu on a laptop Bestbuy will not accept the return.  If I deleted Ubuntu and put Windows 8 back on it, will the Geek Squad be able to boot into bios and tell what has happened?

---

### Post by Vladlenin5000 on 2014-05-12
Yes, they will. BTW, you probably can't find any store worse than BB: Abusive practices and the self-titled geek squad must be a (really bad) joke. Geeks all over the world should file a class action against the store for giving them a bad name.

---

### Post by Impavidus on 2014-05-12
You could try taking the hard drive out and storing it on a shelf, putting a new (maybe better) hard drive in and installing Ubuntu. If you want to return it, put the original hard drive back in.

Best Buy doesn't seem to be active in Europe. Should I be happy?

---

### Post by jonathan71381 on 2014-05-12
And there is no possible way to erase the data on the bios?

---

### Post by Danger_Monkey on 2014-05-12
Impavidus, in the US, we don't go to BB unless we absolutely can't find it anywhere else.  I'd rather wait for something to come from the UK or China rather than go to BB up the street.  You really aren't missing anything, except a lot of headaches.  ;)

---

### Post by jonathan71381 on 2014-05-12
Is the data about the OS being wiped out and others installed on the bios, or on the harddrive?  If on the harddrive, wouldn't a complete harddrive wipe destroy all evidence of any type of OS modification?

---

### Post by jonathan71381 on 2014-05-12
Bestbuy does suck!  Salesmen tell you it is okay to put Linux on a machine, and when you try to return it Geeksquad tells you that you voided the warranty.  Then corporate headquarters tells you to go to hell.

---

### Post by NM5TF on 2014-05-12
> **jonathan71381 said:**
> Is the data about the OS being wiped out and others installed on the bios, or on the harddrive?  If on the harddrive, wouldn't a complete harddrive wipe destroy all evidence of any type of OS modification?

I don't believe that BIOS has ***ANY*** information as to what OS is installed....that info is in GRUB...Grand Unified Boot...

curious as to why you want to return the machine...does it have problems ???

did it work under WIN 8 ???

just wondering...:-k

tommy

---

### Post by WoodenWalker on 2014-05-12
> **Vladlenin5000 said:**
> you probably can't find any store worse than BB: Abusive practices and the self-titled geek squad must be a (really bad) joke. Geeks all over the world should file a class action against the store for giving them a bad name.

I whole-heartedly agree with this statement. I was working on a former coworker's computer a few weeks back. He had gone to BB/Geek Squad for help and they could not discover the problem. He could not find or connect to any networks. The problem was that the wifi switch was set to off. Any "geek" should know to check that first and foremost when they do not see any networks listed. They are just bad on so many levels....

---

### Post by mcduck on 2014-05-13
> **NM5TF said:**
> I don't believe that BIOS has ***ANY*** information as to what OS is installed....that info is in GRUB...Grand Unified Boot...

curious as to why you want to return the machine...does it have problems ???

did it work under WIN 8 ???

just wondering...:-k

tommy

I agree with this, I've never, ever seen a BIOS that would even attempt to store that kind of data. As long as simply make a full install of Windows (so that it removes Grub and uses ntloader instead) nobody will be able to tell if there's ever been any other operating system on the machine or not.

(of course I'd personally recommend just sticking with manufacturers and stores who allow you to use your own computer as you wish, and run your preferred operating system ;))

---

### Post by Mark Phelps on 2014-05-13
This might have something to do with the new UEFI "BIOS" -- as, I believe you have to make changes to it to install another OS, and removing that OS might just leave your changes in place -- but I defer to a UEFI "expert" to comment on this.

---

### Post by HiImTye on 2014-05-13
UEFI can have it's information stored on the motherboard, or a drive. I just use legacy boot as it's the method with the least problems

---

### Post by craig10x on 2014-05-13
I did the very thing you are talking about...bought a laptop from Best Buy and wiped windows and installed ubuntu...the particular hardware at the time had problems on ubuntu and i knew i would need to return it for a refund and purchase another laptop that would have no problems with compatibility...

All you have to do is make the restore discs for the original system on there and if you need to return it, just simple do the restore...it will totally wipe the hard drive and put windows back on....When i returned, all the geek squad does is boot it up and once they see the stock set up on the computer, they will give you no problem....of course, you don't TELL them you had changed it while you had it....I just told them it works fine but didn't meet my needs and i got my refund... :D

---

### Post by jonathan71381 on 2014-06-25
It was just a cheap piece of crap that didn't even run Linux Ubuntu very well, it ran win 8 horribly.

---

### Post by jonathan71381 on 2014-06-25
I will definitely not use Bestbuy Again.  I know this is a Ubuntu forum, but for the purposes of getting this machine back where it belongs so I can go to a decent store and get another machine, how do you install WIN 8 so that it removes Grub (what is Grub) and how do you make it use ntloader (what is ntloader)?
\

---

### Post by Tar_Ni on 2014-06-25
Any mainstream retailers such as Best buy will not accept a refund if they know you have wiped the hardrive and installed another operating system. In their politics, it means you have made significant changes to the item you bought and so they can't be held responsible for malfunctions or insatisfaction.

So if you install Linux, you must be fully aware that your guarantee might be void in case your hardware is defective. Most Linux users find that it is a reasonable risk to be able to use the operating system they prefer. Others might choose not to alter their system until the guarantee expired... It doesn't mean your laptop will have any problem either. It's your choice, just make sure you are well informed.

-- If you didn't make a restore disc of your Windows 8.1 retail installation and installed Ubuntu regardless, I think you are screwed up in terms of refunds. You might try to format the hardrive reinstall Windows 8.1 by getting an iso file of Microsoft with you original W8.1 retail key and booting it on a DVD or USB flashdrive.

Here's a guide how to do it: [http://www.winbeta.org/news/how-download-windows-81-iso-using-your-windows-8-retail-key](http://www.winbeta.org/news/how-download-windows-81-iso-using-your-windows-8-retail-key)

Might be the tech guy at Best buy will notice it though. I just don't know.

---

### Post by oldfred on 2014-06-25
Windows XP used ntldr, you do not have that.
Windows Vista & later use bootmgr for BIOS booting.
But all new Windows UEFI systems use bootmgfw.efi as an efi boot loader.
Grub2 is just the Linux boot loader, Windows does not have a name for their boot loader other than the file name.

There are ways to erase the UEFI entries using efibootmgr from command line in Linux. Better UEFI systems have that built into UEFI to add or subtract entries.

Best to use another hard drive if you think you may sell or return system. Some like to buy a system with a hard drive to save a little but then install SSD just for a fast Ubuntu install.

Otherwise do a full image backup of Windows and make the DVD set of a recovery. If you do not have recovery set you cannot restore to like new.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
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


 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by yancek on 2014-06-25
Retailers generally offer very short term warranties, 30 days is common.  The real warranty is from the manufacturer, HP, Dell, Lenovo, Toshiba or whoever and it is usually for a longer period, 1 year is common.  You can also extend it but that is an extra cost.   Here's an example from an HP warranty:

> [FONT=sans-serif]Warranty does not apply to defects resulting from (a) improper or inadequate maintenance or calibration,
 (b) software, interfacing, parts, or supplies not supplied by HP

The above means they warranty only the software provided when you purchased the machine.  That would obviously include a different operating system.  From what I have read, Dell is fairly liberal about this while HP is not.  Not sure about other manurfacturers.  If you reinstalled the original OS or restored it from a recovery partition or an installation medium, I would not expect you would have any problem with the warranty. 


[/FONT]

---

