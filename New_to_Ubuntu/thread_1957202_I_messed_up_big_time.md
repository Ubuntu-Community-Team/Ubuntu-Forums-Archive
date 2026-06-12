---
title: "I messed up big time"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by Keithhollis on 2012-04-12
Hi all ):P please be gentle im new to linux,

I was runnung vista 32 bit and decided i wanted to  try linux out so i partitioned my harddrive downloaded kubuntu bish bash bos loved it by the way but decided to delete it (wanted to try another distro)so i deleted the partition and thought nothing of it .turned on my laptop this morning and all i see is

Error: unknown file sytem 
Grub rescue.

I cant get to recovery  as its on my hard drive in the d partition or was i have no way knowing i have no disks. ,i didnt touch this when creating or deleting the partition though,i do have the live  usb boot of kubuntu so i tried to reinstall ,i get to the install kubuntu from the usb select boot then black screen ive done this so many times now and each time black screen.
I have followed other fixes that i found on this site about grub 2 repair to no avail. ](*,)

1. Can i get past this grub rescue screen so i can atleast have vista.how do i do this ? Or 
2. Can i just dedicate the whole drive to kubuntu and overwrite vista . How do i do this? I would like to replace vista with kubuntu if thats possible .

I really appreciate any help you can give me

---

### Post by moody_mark on 2012-04-12
You shouldnt have lost any data. What usually happens is that the MBR of the disc (which used to have just a pointer to the windows OS) now points to the Linux partition. Grub would then load up and then list the operating systems on the disc so really to boot windows it does so via grub.

Usually installing your new distro to the partition this should re-install grub and then allow you to use your new distro and windows. Before you do this though make sure your backup your data. Boot using a live CD if you can to do this. Can you still boot from the live CD?

When your machine boots you should have a option to select a boot device, perhaps you'll get an option to boot the recovery partition? If you do then you should be able to create the partition again and install?

If you want to just have windows then you should have a recovery disc or recovery partition. Use the windows MBR recovery tool:

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Heres some useful resources too:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Zorael on 2012-04-12
I think the easiest way to fix booting into Vista is to first boot a live image of Kubuntu (CD/USB), if you still have one around.

Choose to try out the distro (not install it). Install the **testdisk** package, either via the Muon package manager or via a terminal (Konsole).
```
sudo apt-get install testdisk
```

When it's installed, run it in a terminal with sudo.
```
sudo testdisk
```
Choose **No Log**, then select your disk. If you only have one, it's probably **/dev/sda**. Then choose **Intel/PC partition** in the next menu.
```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk **/dev/sda** - *<blahblah>*

 [ Analyse  ] Analyse current partition structure and search for lost partitions
>[ Advanced ] Filesystem Utils
 [ Geometry ] Change disk geometry
 [ Options  ] Modify options
 [ MBR Code ] Write TestDisk MBR code to first sector
 [ Delete   ] Delete all data in the partition table
 [ Quit     ] Return to disk selection
```
First pick **Advanced** to show the partition table. Confirm that you've chosen the right disk (**/dev/sda** etc); it should list your Vista partition. If it doesn't, choose **Quit**, then **Quit**, then pick another disk and try again.

If it *is* the correct disk, choose **Quit** to get back to the main menu. Pick **MBR Code** and let it do its thing.

Once that's done, go back to the main menu and into **Advanced** again, select your Vista partition and choose **Boot** to mark it as the active/boot partition.

When that's done, just exit everything and try rebooting.

---

### Post by Keithhollis on 2012-04-12
Thanks for the quick  response guys, 

Zorael i have done as tou suggested but the only options i have is 
Run kubuntu from this usb 
Test memeory 
Boot from first harddrive 
Advanced options
Help


Selected run kubuntu from this usb and nothing happens i mean  get the kubuntu splash screen starts to loads then goes black and stays there.
Im asuming now that i have the wrong instalation usb as there is no option to try out just run from this usb
Sorry if i sound like an idiot

---

### Post by Keithhollis on 2012-04-12
:p thank god i managed to sort it myself
Thanks for the help moody_mark and zorael 
Out of intrest what one would you recommed for a newbie ive tried ubuntu and thought the taablet style was annoying i have an i pad thats enough for me tryed kubuntu and it kept crashing what stable OS would tou recommend for a newbie to replace vista on a laptop 

Thanks in advance

---

