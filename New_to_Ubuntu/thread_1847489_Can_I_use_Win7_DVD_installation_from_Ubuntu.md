---
title: "Can I use Win7 DVD installation from Ubuntu?"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by PayPaul on 2011-09-20
I'd like to use my Win7 DVD to reinstall and also reformat the C drive that the installation is going into from Ubuntu. My current Win7 install was a bust. It was a reinstall of Win7 and went Fubar real quickly. The reason for that, I strongly suspect, was that the Win7 installation did not reformat the drive that had the old Windows installation on it. If it had a windows.old file would not have been created. 

I want to be able to simply put the DVD in and do the proper clean install on that C Drive if possible from my current Ubuntu. I know I will have to reinstall Ubuntu or at least repair the grub from a live CD as the dual boot sequence will be off because of the re-installation of Win7. I would like to know if it is possible this way or can I format the C Drive and the E drive in Ubuntu and then insert the Win7 DVD at boot and do the reinstall that way.

I've seen some references to a program called gparted. Will that allow me to format the C & E drives from here?

My alternative plan is the just reformat the entire hard drive and reinvent the partitions. I was hoping to shorten the process a bit though. I'm not abandoning Ubuntu by no means but there are some programs and program functionalities that I miss from the Windows installation. Ubuntu has saved my machine and it did also assist in actually diagnosing some of my problems with Windows on this PC strangely enough. I find it a much cleaner running OS than Windows.

---

### Post by alphacrucis2 on 2011-09-20
> **PayPaul said:**
> I'd like to use my Win7 DVD to reinstall and also reformat the C drive that the installation is going into from Ubuntu. My current Win7 install was a bust. It was a reinstall of Win7 and went Fubar real quickly. The reason for that, I strongly suspect, was that the Win7 installation did not reformat the drive that had the old Windows installation on it. If it had a windows.old file would not have been created. 

I want to be able to simply put the DVD in and do the proper clean install on that C Drive if possible from my current Ubuntu. I know I will have to reinstall Ubuntu or at least repair the grub from a live CD as the dual boot sequence will be off because of the re-installation of Win7. I would like to know if it is possible this way or can I format the C Drive and the E drive in Ubuntu and then insert the Win7 DVD at boot and do the reinstall that way.

I've seen some references to a program called gparted. Will that allow me to format the C & E drives from here?

My alternative plan is the just reformat the entire hard drive and reinvent the partitions. I was hoping to shorten the process a bit though. I'm not abandoning Ubuntu by no means but there are some programs and program functionalities that I miss from the Windows installation. Ubuntu has saved my machine and it did also assist in actually diagnosing some of my problems with Windows on this PC strangely enough. I find it a much cleaner running OS than Windows.


You don't install the Windows DVD from Ubuntu. You have to boot the Windows install DVD. If the Windows DVD does not boot when your machine starts then you may have to change the BIOS boot order settings. And yes it will blow away the GRUB/GRUB2 MBR but you can restore that no problem after windows is installed. Pay careful attention to the formatting options when you install Windows so it doesn't overwrite Ubuntus partitions.

---

### Post by GodlySoup on 2011-09-20
It sounds like you have 2 partitions running on your computer. If this is the case, you can just pop in the Windows 7 cd and install it. I'm assuming you have a cd bought from the store or a recovery disc you made when you got your computer. Just make sure you click "Custom" when installing Windows. This will wipe your old installation. You should be able to choose the "C:" partition. It won't show you the letter, but it will show you the different sizes you have partitioned. Hopefully, if this is the case, you won't even need to reinstall Ubuntu. 

Make sure you back everything up first!

---

### Post by PayPaul on 2011-09-20
> **GodlySoup said:**
> It sounds like you have 2 partitions running on your computer. If this is the case, you can just pop in the Windows 7 cd and install it. I'm assuming you have a cd bought from the store or a recovery disc you made when you got your computer. Just make sure you click "Custom" when installing Windows. This will wipe your old installation. You should be able to choose the "C:" partition. It won't show you the letter, but it will show you the different sizes you have partitioned. Hopefully, if this is the case, you won't even need to reinstall Ubuntu. 

Make sure you back everything up first!
Presently I have 3 partitions on the main drive. One, the "C" drive, has the current bad Win7 installation on it. The second partition has some programs installed in it on the Windows OS and the third has my Ubuntu install on it. When I've put in the Windows 7 DVD in before with the BIOS set to boot to the DVD drive it has simply gone over to the Windows installed already. It doesn't load the setup program at all. That current windows install is as problematic as the original Windows installation. The original Win7 installation was an upgrade from Vista. I do have the option in the Win7 installation setup to do a clean install / Full install despite it being called an "upgrade" DVD. 

So there is no program I can use from Ubuntu to get the Windows7 DVD running?

---

### Post by Mark Phelps on 2011-09-21
> **PayPaul said:**
> So there is no program I can use from Ubuntu to get the Windows7 DVD running?

NO -- you have to boot from the DVD.

Your description indicates that your previous attempt did not boot from the DVD, but rather, booted directly into Windows.  That means either your boot order is set to select the hard drive first, the optical drive is bad, or the DVD is bad.

What you CAN do, when inside Ubuntu, is open the GNome Partition Editor and remove the Windows partitions.  Since Win7 gives you the option to format as part of its installation, that will prevent you booting into Win7 -- but you still have to fix the boot order in the BIOS (if that is the problem).

---

### Post by P05TMAN on 2011-09-21
> 
So there is no program I can use from Ubuntu to get the Windows7 DVD running?
If you did want to run windows "inside" Ubuntu, you could set up a virtual machine in Virtual Box to run it. Kind of the same idea, just a little different. You wouldn't be able to use any of your configured partitions, however, as it would be a virtual hard disk.

---

### Post by PayPaul on 2011-09-21
> **Mark Phelps said:**
> NO -- you have to boot from the DVD.

Your description indicates that your previous attempt did not boot from the DVD, but rather, booted directly into Windows.  That means either your boot order is set to select the hard drive first, the optical drive is bad, or the DVD is bad.

What you CAN do, when inside Ubuntu, is open the GNome Partition Editor and remove the Windows partitions.  Since Win7 gives you the option to format as part of its installation, that will prevent you booting into Win7 -- but you still have to fix the boot order in the BIOS (if that is the problem).

So this might allow me to afterwards boot from the Win7 DVD on a restart and then go through the Win7 setup because there would be no Win7 installation present? Of course I always change the boot sequence when booting from disc media. I know, some people don't know that. That solution would be just as good. It would be nice to restore the grub, if that's all I have to do, and then continue with my present installation. Do I do that simply be creating a backup/repair disk in Ubuntu or do I create a live cd from my present installation?

---

### Post by Lisiano on 2011-09-21
Please take  a look at this wiki page for information about reinstalling Grub after installing Windows.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Mark Phelps on 2011-09-21
> **PayPaul said:**
> So this might allow me to afterwards boot from the Win7 DVD on a restart and then go through the Win7 setup because there would be no Win7 installation present? 
This will prevent you from booting into Win7 -- because it will no longer exist.  

To boot from optical disk, sometimes you get a text message at the top of the screen along the lines of "Press any key to boot from CD/CDVD" -- and if you miss that message or wait too long, the PC continues down the list of boot devices, eventually finds the hard drive, and will attempt to boot from it.

So, next time you boot from the DVD, look closely to see if you get this message.

If you then boot from the DVD and get an error message something along the lines of No Operating System -- THAT means that your PC is still trying to boot from the hard drive.

That could mean that the disk itself is damaged (and can't be read) and/or the CD/DVD drive is faulty (and not reading the disk properly).  Both of these can be checked by attempting to boot from a disk that is known to boot successfully in a different PC.

> It would be nice to restore the grub, if that's all I have to do, and then continue with my present installation.
I thought you wanted Win7 back working on the PC.  IF so, you need to get that working before you take the next step to reinstalling GRUB.

Once you do get Win7 working, go to the effort of making the WIn7 Repair CD.

> Do I do that simply be creating a backup/repair disk in Ubuntu or do I create a live cd from my present installation?
IF you're asking about how to restore Ubuntu (presuming you have a working version at present on the PC), you can image off your current Ubuntu install using Clonezilla (to an external drive), and then later, restore from that backup.

---

### Post by PayPaul on 2011-09-21
> **Mark Phelps said:**
> This will prevent you from booting into Win7 -- because it will no longer exist.  

To boot from optical disk, sometimes you get a text message at the top of the screen along the lines of "Press any key to boot from CD/CDVD" -- and if you miss that message or wait too long, the PC continues down the list of boot devices, eventually finds the hard drive, and will attempt to boot from it.

So, next time you boot from the DVD, look closely to see if you get this message.

Oh yeah. Been there, done that. That always comes up whenever I set the BIOS to boot from CD. 

> If you then boot from the DVD and get an error message something along the lines of No Operating System -- THAT means that your PC is still trying to boot from the hard drive.

That could mean that the disk itself is damaged (and can't be read) and/or the CD/DVD drive is faulty (and not reading the disk properly).  Both of these can be checked by attempting to boot from a disk that is known to boot successfully in a different PC.The disk I would be using would be the Win7 install disk. I can only presume that it will treat the drive like a new drive and finally go into the setup program to install a fresh copy of Win7. In that setup I will be able to choose the C drive to install to.


> I thought you wanted Win7 back working on the PC.  IF so, you need to get that working before you take the next step to reinstalling GRUB.

Once you do get Win7 working, go to the effort of making the WIn7 Repair CD.I have made a repair CD from the current installation of Win7. That was the only way to kickstart the Windows 7 startup. All other attempts failed miserably.


> IF you're asking about how to restore Ubuntu (presuming you have a working version at present on the PC), you can image off your current Ubuntu install using Clonezilla (to an external drive), and then later, restore from that backup.Hmmm. I knew there was a way to backup my present installation. In that case I'm guessing I would first reinstall Win7 then reboot again, and go to the backup files of my present Ubuntu installation and have prompts to restore it to its current place/partition on the HD. Would Clonezilla be able to make a bootable CD of a backup of my Ubuntu installation. I would also believe that the LiveCD with its repair function would only need to restore the grub and my present installation with its settings and such remain intact. Would that be so?


Thanks for the tips.

---

### Post by Mark Phelps on 2011-09-22
I don't know that there's a way to tell Clonezilla WHERE on a drive to do a restore.  I think it just starts writing to the first free space it can find.  But if that's not the case, that's a good reason to, BEFORE you reload Ubuntu, do an image backup of your Win7 install. That way, if it does get overwritten by Clonezilla, you can easily restore it.

Suggest going to the Macrium Reflect site, downloading and installing their FREE version, and using the option to make a Linux Boot CD.  Then, image off Win7 to an external drive.

---

