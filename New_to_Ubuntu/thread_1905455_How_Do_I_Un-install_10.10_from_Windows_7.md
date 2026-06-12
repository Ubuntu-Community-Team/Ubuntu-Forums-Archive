---
title: "How Do I Un-install 10.10 from Windows 7"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by BNZBKK on 2012-01-06
I installed Ubuntu 10.10 via a USB in a computer running Windows 7 and now there are a few problems and I would like to un-install 10.10
How do I do it ?

---

### Post by madjr on 2012-01-06
hi, well is a bit tricky if you dont have experience.

anyway which problems were you having ?

---

### Post by BNZBKK on 2012-01-06
Firstly Ubuntu presents itself as the prime OS rather than Windows  and needs to be 'arrowed' down to Windows and as it is not my computer I would prefer it to boot straight into Windows. Can I change that somewhere ..maybe in the BIOS ?


In past installations Windows would automatically boot unless the alternative selection ..Ubuntu was manually made.


WARNING: I am not very good with too much technicality or lines of code

---

### Post by 2F4U on 2012-01-07
Is that a Wubi installation inside Windows? If yes, here is how to uninstall

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by Mark Phelps on 2012-01-07
IF, as you say, it is not your computer, then why did you install Ubuntu on it?

To give you details, we first need to know HOW you installed Ubuntu, as the removal steps are very different, depending on the install.

You have already been given a link for removing a Wubi install -- but since it boots directly into Ubuntu, it's likely you installed to a separate partition.

In that case, the first thing you need to do is remove GRUB from the MBR.  To do that, use Boot-Repair as indicated below:

[http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair")

Once you've done that, you should be booting directly into Windows.

You can then use the Win7 Disk Management utility to remove the Ubuntu partition.

---

### Post by BNZBKK on 2012-01-07
> **Mark Phelps said:**
> IF, as you say, it is not your computer, then why did you install Ubuntu on it?
 

Thank you for your response Mark Phelps.

It is my sisters computer and I am staying with her and as a
dedicated Ubuntu user decided to install it in/alongside Windows as I have done on several occasions before successfully on other machines. 
On my own machine back in another country I use only Unbuntu  


> **Mark Phelps said:**
>  
To give you details, we first need to know HOW you installed Ubuntu, as the removal steps are very different, depending on the install.

You have already been given a link for removing a Wubi install -- but since it boots directly into Ubuntu, it's likely you installed to a separate partition.
 

I installed via a USB and pendrivelinux.com and I don't know which of the two partitions it is in as I can't find it which is 'yet' another reason I don't like Windows 7


> **Mark Phelps said:**
>  
In that case, the first thing you need to do is remove GRUB from the MBR.  To do that, use Boot-Repair as indicated below:

[http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair")

Once you've done that, you should be booting directly into Windows.

You can then use the Win7 Disk Management utility to remove the Ubuntu partition.


After reading those threads they led me to this ..

Ubuntu Secured Remix
[http://sourceforge.net/p/ubuntu-secured/home/Home/](http://sourceforge.net/p/ubuntu-secured/home/Home/)

...integrates OS-Uninstaller (tool to uninstall any Operating System from your PC)
integrates Boot-Repair (tool to repair the PC boot)


Would this be a possibility/solution or have I misread something along the way ?

---

### Post by BNZBKK on 2012-01-08
OK it seems an uninstall is problematic how about resolving the first issue... 


[I]"..Ubuntu presents itself as the prime OS rather than Windows and needs to be 'arrowed' down to Windows and as it is not my computer I would prefer it to boot straight into Windows. Can I change that somewhere ..maybe in the BIOS ?


 In past installations Windows would automatically boot unless the alternative selection ..Ubuntu was manually made..[/I]"

**I would prefer it to boot straight into Windows. Can I change that somewhere **  ..and manually select Ubuntu

Any takers ?

---

### Post by JazzPotato on 2012-01-08
grub.conf! I will post another post with instructions once i find grub.conf, but if you know where it is thats how you change the order that appears in grub

---

### Post by JazzPotato on 2012-01-08
/boot/grub/grub.cfg
Edit this file to change the order that the oses appear in grub. BE CAREFUL though, you might screw your system up ALWAYS make a backup.
Live long, and prosper

---

### Post by BNZBKK on 2012-01-08
> **JazzPotato said:**
> /boot/grub/grub.cfg
Edit this file to change the order that the oses appear in grub. BE CAREFUL though, you might screw your system up ALWAYS make a backup.
Live long, and prosper


Thanks for your response JazzPotato and as this is 'Absolute Beginner Talk' ..ahhh where's grub and how/where do I insert this "../boot/grub/grub.cfg .." in Terminal ?

---

### Post by JazzPotato on 2012-01-08
in terminal, "sudo nautilus" so you can edit the files in /
Then MAKE A BACKUP OF GRUB.CFG. Call it something like "grub_backup.cfg" and put it in multiple places. 
Then, with you "sudo nautilus" windows, navigate to /boot/grub/ and find grub.cfg. Inside grub.cfg you will see things like (this is for the windows entry):
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2E686F78686F3DA9
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

Just re-arrange these to get the right order, (i'm guessing, worked in arch ;D) Don't worry, if you backup, it will be fine, but dont reboot until you're absolutely SURE. 

 Maybe you could send me your edited grub.cfg so I can take a look. 

 If you screw up your grub.cfg and you reboot GRUB WILL NOT WORK :-( the you wont be able to boot and I wont be able to help you anymore.

---

### Post by Elfy on 2012-01-08
> 
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
Editing the /boot/grub/grub.cfg is more or less a waste of time - as soon as grub gets an update by anything calling for it to be update - changes that you make will need to be remade.

Have a look here - [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743) for Menu Default Entry.

---

### Post by Mark Phelps on 2012-01-08
There's a reason the grub config file has DO NOT EDIT THIS FILE!

While it's OK to experiment with changes to see what works best, next routine update will wipe out everything you've done.

Changing the default config file is a hold over from the legacy GRUB days, and now, there are different files that need to be changed.

Also, customizing GRUB now can be done easily with Grub-Customizer.

---

### Post by BNZBKK on 2012-01-10
> **BNZBKK said:**
> OK it seems an uninstall is problematic how about resolving the first issue... 


[I]"..Ubuntu presents itself as the prime OS rather than Windows and needs to be 'arrowed' down to Windows and as it is not my computer I would prefer it to boot straight into Windows. Can I change that somewhere ..maybe in the BIOS ?


 In past installations Windows would automatically boot unless the alternative selection ..Ubuntu was manually made..[/I]"

**I would prefer it to boot straight into Windows. Can I change that somewhere **  ..and manually select Ubuntu

Any takers ?





OK ladies I found a simple workaround that worked and no precarious and possibly fatal lines of code to enter, on another thread entitled ..**how to change boot sequence win7 and ubuntu 11.10** and it works for 10.10 

**"..bogan** 
[B]
   [I]
There is a very simple program that changes the default boot order, without the need to edit system files directly: 'Startup Manager', it is available via Ubuntu Software Centre.
 Click on the 'Ubuntu Software Center' & click to run it. Enter "startup" in the search box.
  
 Click on the Startup Manager entry and select 'Install'. 
 
 Run it and select 'Advanced', The default will show in a box with up-down arrows, click on that and select from the list, the entry you want as default, Close and restart to check the entry you want is highlighted.

 { In some rare cases, Startup Manager thinks that deleted entries still exist and gets it wrong, in which case count how many positions you want it to move and re-run Startup Manager[/I][/B]. 

 In 10.10 after installation I went to System/Administration/StartUp-Manager/Boot options - and the default was there and changed, with even a 'Timeout in seconds option which I changed to 5 ( these Linux geniuses think of everything !) 
On restart Windows7 popped up as the default ....easy and a big thank you to **'bogan'**

---

