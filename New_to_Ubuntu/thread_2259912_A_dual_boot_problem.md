---
title: "A dual boot problem"
date: 2015-01-07
forum: New to Ubuntu
---

### Post by Tony_Aimer on 2015-01-07
I would appreciate some guidance or direction on the following problem.  I had an almost unused win7 64 bit machine that I had prepared in 2012 but never got around to using. I had loaded AutoCAD / Inventor 2014 onto it. I assume it worked at that time.

Last year I installed CAE Linux (kubuntu) and succeeded in creating a dual boot machine with 500Gb hard drive available each. In order to do this I had to reduce the Win 7 partition size in which the Autocad was installed and CAELinux gave me the option to boot into Win 7 if I wished.

I then discovered that Autocad and Inventor 2014 would not then run and suspected, but was unable to confirm, that the change of partition size might have been the problem. I also discoverd that the organisation that had originally built the machine for me had added some extra software and I had so many adverts when I ran firfox, that I suspected a malware infection.

Today I have done the following.

I reset the BIOS to boot from the DVD.

I reloaded Win7 from scratch. All old files were put in a directory callied Windows.old.

The reinstallation went fine and I deleted Windows.old at the earliest opportunity.

I then reloaded Acad 2014 without trouble and it runs fine again. On resetting the BIOS to hard drive as intital boot, I still end up in Windows 7 and I am at a loss to figure out how to change the situation to get back to my CAE Linux boot screen with options.

I do not believe I have overwritten my Linux partition because all the files in Windows.old were Windows 7 stuff.

Any advice as to where to go from here would be welcome.

Could BOOT.ini be a possibility - I could not find it on the Windows 7 machine but I might not be looking in the right place.

Regards

Tony Aimer

---

### Post by QIII on 2015-01-07
Hello!

Installing Windows after a Linux distribution is installed overwrites the MBR.  Windows doesn't know about other OSes and naively thinks it is all there is.

[This ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")should help you get things back.

Cheers!

---

### Post by yancek on 2015-01-08
> Could BOOT.ini be a possibility - I could not find it on the Windows 7 machine but I might not be looking in the right place.


No, that's not part of the problem.  The last version of windows to use a boot.ini file was xp.  Now its bcdedit, I think.
You may have overwritten your Kubuntu installation with windows.  It's been a long time since I installed windows so I can't be sure.  Did you have options during the install of windows 7 to select a partition on which to install?  You can use any Linux on a Live CD or flash drive to check partitions.  You should also be able to check from windows, I think its called Disk Management.  See if there are any non-windows partitions.  Windows doesn't recognize Linux partitions so if you see a partition which is not identified as ntfs but just as a primary or logical partition, that might be Kubuntu.

---

### Post by oldfred on 2015-01-08
If you have two physical drives, not two partitions, you want grub installed to the second drive.

Otherwise it is just reinstall grub to MBR. You will get the warning about Flexnet and sector 32, but grub has be rewritten to work around it. Flexnet is used by many Windows applications that have DRM to prevent copying.

---

### Post by Tony_Aimer on 2015-01-08
Thanks to you guys who have taken the trouble to reply

It seems the problem is that Win 7 overwrote the boot record that previously held the Linux info

This You tube clip is why I think M****S*** stinks these days.

 [https://www.youtube.com/watch?v=wvsboPUjrGc](https://www.youtube.com/watch?v=wvsboPUjrGc)

I stopped drinking the Kool-Aid last year and feel very much better for it 
although I am still very new to Ubuntu and CAELinux.

I will never buy another M****S*** product again in my life!

I shall follow the various steps to recreate the boot record.

Thanks Again

---

### Post by Tony_Aimer on 2015-01-09
Thanks to all for your suggestions

I resolved my problem by using boot-repair-disk whihc resorted
the MBR that Win 7 had trampled over.

Best Wishes

Tony Aimer

---

