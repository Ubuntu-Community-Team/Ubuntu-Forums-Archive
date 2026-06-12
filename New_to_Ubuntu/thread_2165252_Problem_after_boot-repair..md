---
title: "Problem after boot-repair."
date: 2013-08-04
forum: New to Ubuntu
---

### Post by Yuliyan_Hristov on 2013-08-04
Hi there. I've got a little problem after i reinstalled GRUB using boot-repair. When i restarted the computer a black screen came up with a lot of numbers and letters on it. I really don't know what is that mean and how to fix. Could you please tell me what this is and how to fix it. Thank you in advance!

I forgot to say that the reinstalling went well. the boot-repair told me that reinstalling is succesfull and to restart...and there - a problem came up.

---

### Post by carl4926 on 2013-08-04
You were reinstalling grub why..?

I'd be inclined to use the original install media to chroot the installed system and work a fix from there

---

### Post by Yuliyan_Hristov on 2013-08-04
Well i reinstalled it because Ubuntu didnt wanted to boot after the install...So what i have to do from now?

---

### Post by carl4926 on 2013-08-04
Tell us about the computer. Does it have windows, what version?

---

### Post by Yuliyan_Hristov on 2013-08-04
Ah im sorry...i forgot to mention that. Wll it has WIndows 7 on it. Yesterday i found an old hard drive in the closet :) and mounted it in the computer. So im trying to run Ubuntu on the second drive which is 80 GB. The main drive is 1 TB with Windows in it. I just wanted the OS's to be independent. Maybe the different drives are the problem?

---

### Post by Muhammad_Ahmad_Mujtaba on 2013-08-04
you proposed the same situationi was into last days! **Yulian_Htistov . **You're directed to ubuntu GRUB 2 terminal. If you want have dual boot then this solution might not work for you becox i am newbie too and in my case i didn't wanted a dual boot so in partition menu i removed Windows 7 Ultimate and removed also a tiny partition labeled as 'Windows Loader' and on this partition i installed new partitition and mounted that at \boot\efi . This worked for me and i went into ubuntu 13.04 directly & facing no issue! cheers! Moreover i have the same PC Spec like you told i mean 64bit architecture! and in my studies this problem is espcially for 64bit motherboard systems invlovinf UEFI/EFI problem which in my case i have EFI may be not with you. . . .

---

### Post by ant2 on 2013-08-04
Can you select the drive with Ubuntu on to boot from the bios. Does that work?

---

### Post by Yuliyan_Hristov on 2013-08-04
I want dual boot. Dont like Windows but loooove Ubuntu but some things (mostly games) dont work on linux...well they do but its much more complicated to install. Actually i reinstalled GRUB before and there was no problem...this morning as explained i tried to run fresh install on Ubuntu and something goes wrong...i tnink it is because i installed it on another drive...Another thing i didnt mention - the second drive (Ubuntu) is with Ultra ATA cable and the main drive is with Serial. It that a problem?

---

### Post by Yuliyan_Hristov on 2013-08-04
The GRUB works now but when i select Ubuntu it gives me a Black screen with letters and numbers on it...thats the problem

---

### Post by Relsig on 2013-08-04
I'm kinda new here too, but if you installed GRUB2 on the 80gb disk and you are booting from the disk you originally had ubuntu & windows 7 on you would run into serious issues. Be sure your primary boot is the hard drive you installed grub on most recently. You should be able to change this in your bios settings at boot.

---

### Post by Yuliyan_Hristov on 2013-08-04
Actually i dont know where grub is installed but ubuntu and windows are installed on a different drives. There is no problem with the GRUB. The problem comes after i select which OS i want to start.

---

### Post by 5l4y3r on 2013-08-04
> **Yuliyan_Hristov said:**
> The GRUB works now but when i select Ubuntu it gives me a Black screen with letters and numbers on it...thats the problem

What if you try to reinstall Ubuntu, this time without changing anything related to GRUB?

---

### Post by Yuliyan_Hristov on 2013-08-04
It probably wont start again...i dont know why but every time i install Ubuntu there is a problem with GRUB so i have to fix it with boot-repair. Maybe im doing something wrong?

Edit: If i post a picture of what im getting would it be helpful?

---

### Post by oldfred on 2013-08-04
Do you get grub menu? If not post link from BootInfo report that Boot-Repair creates.

If you do get grub menu, then what video card do you have. And have you tried nomodeset or tried booting with the recovery mode or second line in boot menu?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Yuliyan_Hristov on 2013-08-05
[http://askubuntu.com/questions/293032/boot-problems-on-ubuntu13-04-recursive-fault-timeout-killing-sbin-modprobe](http://askubuntu.com/questions/293032/boot-problems-on-ubuntu13-04-recursive-fault-timeout-killing-sbin-modprobe) This is the same problem as mine...and as i can see this couldnt fix it. Maybe i should try reinstalling Ubuntu without turning on automatic update while instaling?

---

### Post by Tom 6 on 2013-08-05
Hi :)
I think a fair bit of confusion has arisen here.  

Each physical hard-drive has an "Mbr" which has the job of pointing to which partition the boot-loader is on.  When you install a new OS it replaces whatever was in the Mbr with it's own pointer.  This is called "fixing" the Mbr.  It might not be that the Mbr was broken so "fix" is used more in way way it's used when someone tries to "fix" a horse race or something.  

With this type of set-up i suspect you want the Windows drive to be able to boot into Windows if the 2nd drive is removed but that if the 2nd drive is plugged in then the machine boots into Ubuntu.  i've done this sort of thing quite often.  You just need to be very logical about it.  

Since it's probably a bit of a muddle right now it might be best to reinstall just the Grub2 boot-loader
[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_)
During that process make sure the boot drive is the 2nd drive, the one with your new version of Ubuntu on it.  The one that has the new Ubuntu boot-loader (called Grub2 = GRand Unified Boot-loader2) on it.  

Then boot into Windows and "fix" the Mbr for that one.  Sadly you can't unplug the Ubuntu drive once you have the machine on so the fixing the Windows bootloader will 'break' part of the Ubuntu one.  But you already know how to fix that and it's fairly easy to do now, right?  

Now it should be possible to unplug either drive and the other will boot just into the one it's supposed to.  The Ubuntu one still gives a menu that lists Windows but that option only works if you already had the Windows drive pluggged in.  


Actually fixing the Windows boot-loader can be really tough.  So, many people get around that by creating a small (like 200Mb is probably waay more than you need) "boot partition" and install either Grub2, Grub-legacy or even Lilo to it.  If i was goign that route i would do that to the Windows drive first, set it up to only boot into Windows and to hide the boot-menu so that no-one except you knew about it.  Then plug in the 2nd drive and reinstall grub2 to that but make sure it's the Mbr on that 2nd drive, not sda, that gets it's Mbr 'fixed'.  

Note that unplugging or plugging in hard-drives if the machine is plugged in can easily result in significant damage to your drives and may even make them unable to hold anything or may drop an 80Gb drive down to 40Gb of usable space.  So, take care!!  Also at the back under-side of many hard-drives is a green pcb board.  Again, avoid touching that.  Static and natural oils on your skin could easily damage that.  

Regards from 
Tom :)

---

### Post by Yuliyan_Hristov on 2013-08-08
Wll i found a solution after another reinstall of Ubuntu. When i installed Ubuntu on the 1TB drive i had the same problem...so i decided to remove the 80GB drive to see what is going to happend. So i removed it and Ubuntu started just fine. I think there was something wrong with the priority of the drives! I think i was the problem. And now im only with the 1TB drive...and everything is fine. Dont want to do anything else cause im sick  of trying to "fix" everything. Thank you all for your help and posts! 

Regards from 
Bulgaria

---

### Post by Tom 6 on 2013-08-08
Hi :)
Ouch!  I know the feeling.  

Err, was one drive using a GPT partitoning system and the other a normal MBR one?  If so i had the same problem and did the same thing.  ie just left the older drive unconnected.  I went for GPT because the new drive was over 1Tb and i knew i would never want Windows on it.  So, Gpt gave me full access to the entire drive.  I'm not sure how my problems eventual resolved themselves tbh.  I think i used the old MBR drive in a different machine

Apols for not remembering this sooner!  :(
Apols and regards from 
Tom :)

---

