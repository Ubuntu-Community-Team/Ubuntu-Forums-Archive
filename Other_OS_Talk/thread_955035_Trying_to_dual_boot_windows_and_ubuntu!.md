---
title: "Trying to dual boot windows and ubuntu!"
date: 2008-10-21
forum: Other OS Talk
---

### Post by dj_ee3 on 2008-10-21
Hi people... I am new user of ubuntu (install it before 2 weeks) and everything goes well so far and I like it. But, there are things that can't be done in ubuntu for example play games or watch password protected mms:// streams. So before few days I sit down and I decide to install windows xp on small part of the hard drive to fill up my gaming addictions. So the first thing I did is to boot the ubuntu disc I run the live cd from which I made a 50 gb partition for windows. Everything great so far I start the installation but after 2-3 minutes that error came up [http://img370.imageshack.us/img370/7094/19xa.png](http://img370.imageshack.us/img370/7094/19xa.png)   ... I know that many people say that normaly I have to install ubuntu under windows but I have ubuntu already and I don't want to delete it. Can you help me avoid this error. Thank you in advice.

---

### Post by PoopyTheJ on 2008-10-21
Windows is bizarre, if It's not the very first partition on the disk it freaks out, also if you have partitions created after, the ubuntu partitions Windows won't see it. To make life easy for you the easiest way to go about this is, backup whatever you want from Ubuntu and wipe the HDD, reinstall windows as the first partition on the drive FIRST. Then install Ubuntu, I'm going through the same thing here and since I had created an additional area of free space for an NTFS partition after my Ubuntu install windows refused to see or use it. When I tried to format the partition through the windows CD it erased every other partition on the drive. Just make life easy for you and make windows the primary partition. Just my 2 cents.

---

### Post by dj_ee3 on 2008-10-21
One very noob question how can I wipe out my hard drive when I can't access my windows cd?

---

### Post by dj_ee3 on 2008-10-22
I erase the whole hard disc and the result was that same error showed up so I had to reinstall ubuntu again.....

---

### Post by Battie on 2008-10-22
> **dj_ee3 said:**
> I erase the whole hard disc and the result was that same error showed up so I had to reinstall ubuntu again.....

This error looks like a driver issue, especially if it keeps happening after a clean installation.

Attach your c:\windows\memory.dmp or your c:\windows\minidump\* file here and I'll take a look to see if a driver is at fault.

Edit: I know it *says* ntfs.sys, but when it names a core Windows driver like that it's usually wrong.  Ntfs.sys might have been the one to call whatever was screwed up, but wasn't actually the problem itself.  The debugger will give a more accurate picture of what happened.

---

### Post by regor210 on 2008-10-23
Assuming your Windows CD is not bad, you could try this. 

Windows does not play nice with the Ubuntu file system. Well it can not read ext3. More over Windows does not play nice with Grub. When a hard drive has been formatted with ext3 and Grub has been placed in the hard dives MBR (Master Boot Recored) It may take A little work to install Windows on that hard drive. Here is what I do.

**WARNNING!!!! THIS WILL WIPE YOUR HARD DRIVE CLEAN!!!!**
  
In short you just boot your computer using a Windows Boot Disk (if needed) to bring up a DOS prompt. type 

FDISK /MBR 

Hit Enter. This should fix your MBR. Now Windows should find your hard drive when you restart your computer. 

You know the rest if needed.
Run fdisk, restart, format c: ,e:\ , setup

You can find Boot Disks here
[http://www.bootdisk.com/](http://www.bootdisk.com/)

---

### Post by Battie on 2008-10-23
> **regor210 said:**
> Assuming your Windows CD is not bad, you could try this. 

Windows does not play nice with the Ubuntu file system. Well it can not read ext3. More over Windows does not play nice with Grub. When a hard drive has been formatted with ext3 and Grub has been placed in the hard dives MBR (Master Boot Recored) It may take A little work to install Windows on that hard drive. Here is what I do.

**WARNNING!!!! THIS WILL WIPE YOUR HARD DRIVE CLEAN!!!!**
  
In short you just boot your computer using a Windows Boot Disk (if needed) to bring up a DOS prompt. type 

FDISK /MBR 

Hit Enter. This should fix your MBR. Now Windows should find your hard drive when you restart your computer. 

You know the rest if needed.
Run fdisk, restart, format c: ,e:\ , setup

You can find Boot Disks here
[http://www.bootdisk.com/](http://www.bootdisk.com/)

This might have to be done, but I'm not sure it's necessary yet.  It sounds like he is successfully booting into Windows and starting to operate it, and the BSOD in the image is usually caused by a faulty driver.  If it were a problem with the boot configuration I think he would see a different error (0x7b, perhaps) much earlier in the boot process.

The presence of an ext3 partition should not be an issue, unless he is using an unstable driver to read it.  In my experience, Windows simply marks the area as unknown and does not try to map it unless the driver is installed.

If the OP would be so kind as to post the crash dump we might get a better clue whether brain surgery is necessary here.

---

### Post by regor210 on 2008-10-23
I have a friend that owns a mobile computer repair business that gives me old computers. I place Ubuntu on them and give them away. Sometime someone will bring me a system in need of repair. Not only do I fix it but I make sure there computer is dual Boot Ubuntu/Windows. Most of the time that means giving them more hard drive space. So I end up pulling a hard drive out of a good computer that is already setup with Ubuntu. I would say 3 out of the seven times I have dun this I have had MBR issues. All 3 times this has been a problem windows has given me a different Error messages. To the Windows installation possess its like there is no hard drive at all.

So seeing how he has no problem installing Ubuntu, It seems to me that the hardware is not to blame. Next I would look at the Windows CD is it dirty, scratched or broken? Last thing to check is how has his system changed? Hence trying to clear the MBR of GRUB and see if this helps Windows to install properly.  This may not solve the problem but it would not hurt to give it a try.

---

### Post by PoopyTheJ on 2008-10-25
If I get this straight you cannot install to your windows install after a clean install and get a BSOD. If that's the case run memtest off the Ubntu LiveCD in those instances where a clean install gives me issues with windows I've found it to be 90% of the time a memory issue. Of course you might say Ubuntu runs fine, I've actually had errors show in my ram windows will crash but ubuntu runs fine. Make sure all hardware is working fine then start examining other possibilities take care of the simple answers first.

---

