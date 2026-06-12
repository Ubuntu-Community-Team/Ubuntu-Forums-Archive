---
title: "Failure to boot into Ubuntu (wubi)"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by direwolf6 on 2012-09-19
Hi there

I recently installed ubuntu using wubi. Everything was going fine until I edited my /etc/default/grub file by adding radeon.audio=1 to the GRUB_CMDLINE_LINUX variable because my HDMI sound wasn't working. 
When I unplugged the HDMI cable the screen went black and stayed like that. I then restarted my laptop and attempted to boot into ubuntu without success. 
Resarting and trying a few times ended with different screens, one was blank, and sometimes I would get into the grub prompt. 
I couldn't boot from the grub prompt following these instructions either [http://ubuntuforums.org/showpost.php?p=10264157&postcount=33](http://ubuntuforums.org/showpost.php?p=10264157&postcount=33)  

I have tried four fixes to date in the following order 
1. Replace the wubildr with a new file, didn't help my problems

2. I have tried solution #2 from: [http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp -p /media/win/wubildr /media/win/wubildr.save
sudo cp -p /media/win/ubuntu/winboot/wubildr /media/wi
```

3. I have tried solution #1 from the same link which causes the following on booting into ubuntu "Failre to load_video" "Could not load /lib/modules/3.2.0-24-generic/modules.dep"

```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```

Remove all lines in the file from the start of the file up to, but not including, the following menuentry
```
### BEGIN /etc/grub.d/10_lupin ###
```

4. I have used boot repair the output of which is here:
[http://paste.ubuntu.com/1212958]("http://paste.ubuntu.com/1212958") 

I am at a loss as I have never used Linux before. 
I don't have any important info on my ubuntu is it best to re-install and try a partitioned install? But then how do I get around the problem of Radeon not being recognized? 

Thank you for your help

---

### Post by blade4 on 2012-09-20
You could try reverting your grub file to its previous config : 

```
sudo nano /etc/default/grub 
 
```
and remove the line you added before your troubles began , 
```
sudo update-grub 
```

But at this point I fear it would be more like a shot in the dark .

---

### Post by YannBuntu on 2012-09-20
Hello

You can try to fix your Wubi like this:
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
gksudo gedit /mnt/boot/grub/grub.cfg
```

Remove the 'radeon.audio=1' occurrences, then save the file.
Reboot the PC, and tell us if you can boot Ubuntu. If yes, you will need to recover, from the WUbi session, the /etc/default/grub file.

Anyway, I don't recommend using Wubi as it is less reliable than a [normal install]("https://help.ubuntu.com/community/GraphicalInstall"). Please consider using a standard Ubuntu install instead of Wubi.

---

### Post by direwolf6 on 2012-09-20
Thanks blade4, unfortunately when I do that the line I edited is no longer there. I'll try yannubuntu suggestion now.

---

### Post by direwolf6 on 2012-09-20
Thanks yannbuntu but when I run  

```

sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```I get the error 
```

/media/win/ubuntu/disks/root.disk: No such file or directory

```I have made doubly sure that I have entered the right commands...

Edit1:
Ok, so it turns out that the grub folder was in sda3, is this going to be a problem? And how do I recover the etc/default/grub file from the wubi session?

Edit2:
When I reboot I came up to the grub prompt screen but I cannot boot into ubuntu this way as I get file not found errors when running

```

insmod ntfs
set root=(hd0,2)
loopback (loop0) /ubuntu/disks/root.disk #errors at this point#
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot

```

---

### Post by direwolf6 on 2012-09-20
Now when I reboot I cannot boot into windows 7 when I previously could and get this error "an error occured while attempting to read the boot configuration data". Now I cannot choose to boot into ubuntu either. I have the windows installation DVD but that does not recognise my C drive when I try to repair using bootrec /fixmbrn from the command prompt. 

What can I do from this point? Can I fix windows using the ubuntiu cd?

---

### Post by YannBuntu on 2012-09-20
> **direwolf6 said:**
> /media/win/ubuntu/disks/root.disk: No such file or directory

That means you haven't checked where your Wubi was.
Please indicate your Boot-Info URL ( [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) )

---

### Post by direwolf6 on 2012-09-20
Boot info report is here:
[http://paste.ubuntu.com/1212958 ]("http://paste.ubuntu.com/1212958")

Thanks

---

### Post by YannBuntu on 2012-09-21
ok. Your Wubi is on sda3, not sda1.
So please replace sda1 by sda3 in the procedure I gave you previously.

---

### Post by direwolf6 on 2012-09-21
Hi Yann

I have repeated your steps using sda3 but that did not help. I now cannot even boot into windows. When I restart my computer I get the message bootmgr missing. When I boot using my windows installation disk there are no drivers present only the xdrive so I cannot even do a complete reinstall. 

What do you suggest now as a way to fix everything? I just want to start again from scratch. I am worried I have just broken my new computer!

Update: Changing my SATA from 'Intel Response Technology' to 'AHCI' let the disk partitions show up. I am now reinstalling windows 7.

---

### Post by YannBuntu on 2012-09-21
ok.
Here what i would do:
1) backup the documents you can still access if you haven't yet
2) try to recover access to Windows this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) . If it fails, reinstall Windows.
3) reduce Windows partition to 50GB via WIndows partitionning tools.
4) install Ubuntu the standard way (no Wubi!): [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

if any problem, please indicate the URL provided by Boot-Repair

---

### Post by direwolf6 on 2012-09-21
Hi Yann 

2) does not work for me. bootrec /fixboot and bootrec /fixmbr say 
"the system cannot find the path specified"

When I try to reinstall windows, no drivers appear and I cannot choose where to install it. 

When I am in ubuntu my harddrives are all there, they are also there in the BIOS. 
What do you recommend?

---

### Post by YannBuntu on 2012-09-22
If i were you, i would format the disk in NTFS via Gparted, then reinstall Windows, then install Ubuntu.

---

