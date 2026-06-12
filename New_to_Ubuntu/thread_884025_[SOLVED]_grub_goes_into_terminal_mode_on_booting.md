---
title: "[SOLVED] grub goes into terminal mode on booting"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by vamsibethapudy on 2008-08-08
whenever i boot grub goes into terminal mode , that is , it does not give me options of OSs , but shows me a command prompt.
I have dual-boot with Xp SP3,& hardy.
I have restarted from windows & it suddenly went into this mode without me doing anything.I had updated kernels in ubuntu , booting into ubuntu after a long time,the previous night & used the 3-way experimental merge for menu.lst.It said it couldnot update the kernel & I shut my computer.
Today i used windows & when i restarted it , i had encountered this problem.
please help.


THE SOLUTION TO THE PROBLEM IS THAT SINCE MY MENU.LST CHANGED TO GIBBERISH , I CHANGED A BACK-UP OF MENU.LST (MENU.LST~) IN THE SAME FOLDER AS THE ORIGINAL.THAT DID IT! 
I REINSTALLED GRUB AFTER DOING THIS TO MAKE SURE, WHICH MIGHT NOT BE REQUIRED.THANKS TO unutbu!!

---

### Post by Black Hawk on 2008-08-08
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot

Worked for me

---

### Post by lordadi on 2008-08-08
Hi,

Folow this link side by side with your regular boot and you should be back in Ubuntu in no time! [Grub boot command line]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot."). Also please be sure to make backups of menu.lst etc before playing with them.


Cheers,


Lordadi.

A bit late!

---

### Post by vamsibethapudy on 2008-08-08
> **Black Hawk said:**
> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot

Worked for me

can I use an older version Live CD??
I dont have a new one
& I already has grub's terminal running when i boot.so ,can i start off from the 4th step directly??

edit:
The last step didnot work.
I tried the process from 4th step ,but with no luck.

---

### Post by vamsibethapudy on 2008-08-08
I had put in the live CD & did all till the 4th step.But then it says ERROR 21: selected disk does not exist.I used hd0,0 as I am sure I had ubuntu in it.I even tried others like hd0,1:2:3 so on ,to make sure , but with the same result.
This error does not occur when I do the steps from the original GRUB terminal during booting.It even says 'succeeded' to every thing.
what did I get into!!??

---

### Post by st33med on 2008-08-08
Wait, you have to mount the partition first. What order did you install your OS's? If you installed Ubuntu as the third OS, do this:
```
sudo mount /dev/sda3
```
Then proceed with the Grub install. If you installed Ubuntu in a different order, replace '/sda3' with '/sda1' or '/sda2'.

---

### Post by vamsibethapudy on 2008-08-08
ubuntu first thenn XP.
anyway I have only one harddisk with only 3 partitions & i tried all the combinations hd0,0 hd0,1 hd0,2 hd0,3 & still the same error.

---

### Post by vamsibethapudy on 2008-08-11
I tried the following commands--
sudo fdisk -lu
It showed the different partitions correctly.

But when i tried 
sudo mount /dev/sda1 or /dev/sda2 , it says it does not find those disks.
someone help

---

### Post by vamsibethapudy on 2008-08-11
I think the problem is with my computer not able to make contact with the hard disk.
where does grub exist?? is it in the hard disk? if not , then my prediction may be correct.But then, using 'sudo fdisk -lu' in live CD shows the different partitions!
And also i use EXT2IFS ,with write ability ,to access linux partitions in windows.Is there a possibility that windows damaged files in linux partitions particulaly the ones needed for booting by GRUB???

---

### Post by vamsibethapudy on 2008-08-11
someone please help
I cant use my laptop from 4 days.I need to apply for internships in the following days.I borrowed my friend's for this day.
Pleasssssssssse

---

### Post by caljohnsmith on 2008-08-11
Vamsibethapudy, you don't need to mount your Ubuntu partition to use the Grub CLI. When you get the Grub CLI on startup, just do the following commands:
```
grub> find /boot/grub/stage1
[should return the partition that your Ubuntu exists on, in the form (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX)
grub> reboot
```
If you get any errors with the above commands, then please paste the output of:
```
sudo fdisk -l
```
Which you can do from a Live CD if you need to.

---

### Post by unutbu on 2008-08-11
Boot from the LiveCD (it's alright if it is old)
Open terminal. Type

```
sudo fdisk -l
```

Since you say Ubuntu was on (hd0,0),
```

sudo mkdir /U
sudo mount /dev/sda1 /U
cat /U/boot/grub/menu.lst
```

Please post the output to fdisk and the cat commands.

If you have a working network connection while using the LiveCD, then posting should be easy. If not, perhaps save the terminal output on a floppy or a USB flash drive and tote the info to Windows (you can still boot Windows, right?) If you can still boot Windows and Windows has a connection, you can mount Windows with

```
sudo mkdir /W
sudo mount /dev/sdx /W
```

(changing the x in sdx to the appropriate partition number for your Windows partition). Then save the terminal output to a file in /W.

Also, when you boot up without the LiveCD, do you see any GRUB error messages?

---

### Post by vamsibethapudy on 2008-08-11
> **unutbu said:**
>  (you can still boot Windows, right?) 

no, i cant.
grub does not show the splash screen at all.
it directly goes into its mini terminal kinda mode..
i dont know what to do then

I will be posting the results to the above commands.

---

### Post by vamsibethapudy on 2008-08-14
hi guys 
I found out finally that my menu.lst has been sabotaged. 
I opened the menu.lst in live cd mode & its gibberish.
how to get it back??

---

### Post by unutbu on 2008-08-14
Boot from the LiveCD.
Mount your linux partition at /U.
Check in /U/boot/grub for any backup menu.lst files. If one exists, try using it as your menu.lst. If not, type
```

sudo chroot /U
cd /boot/grub
mv menu.lst menu.lst-20080814-broken
sudo update-grub
```

From the update-grub man page:
```

       update-grub  is  a  program  used to generate the menu.lst file used by the grub
       bootloader.  It works by looking  in  /boot  for  all  files  which  start  with
       "vmlinuz-".  They will be treated as kernels, and grub menu entries will be cre&#8208;
       ated for each.** It will also create the initial menu.lst if  none  exists**,  after
       prompting the user.
```

---

### Post by vamsibethapudy on 2008-08-14
Thanks 
there is a back-up file.
I will try to reboot & post u on any updates.thanks again

---

### Post by vamsibethapudy on 2008-08-14
Its working!!

---

### Post by James780 on 2010-06-10
do you remember what the backup was called and where i can make a live cd

---

### Post by oldfred on 2010-06-11
James780 welcome to the forums.

But this is an old solved thread. Only those looking for answeres will look here so you will not get much help. If the answer is not here you should start you own new thread. Grub legacy will recreate menu.lst if it is missing. But now new installs since 9.10 use grub2 adn there is no menu.lst but grub.cfg that you do not edit but update from scripts and config files.

---

