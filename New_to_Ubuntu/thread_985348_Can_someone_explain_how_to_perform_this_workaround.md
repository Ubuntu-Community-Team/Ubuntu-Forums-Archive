---
title: "Can someone explain how to perform this workaround?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by putanitsa on 2008-11-17
Hi,

I have this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153) Thanks to this great forum, I can now boot by typing exit after waiting for a while.

They indicate in the bug report that there is a workaround. However, I don't understand how to do it (newbie here). Can someone explain it in step-by-step simple language please?

Thanks,
-putanitsa.

---

### Post by Het Irv on 2008-11-17
When you boot up you should see GRUB's prompt, I think its "e" to go into the edit mode...

Once there you can add that line "rootdelay=90" to the end of the line for the option you want to boot to.

If that works like you want it to, you can edit the file at /boot/grub/menu.lst to make the change permanent.

To edit the file you will need root privliges, so in a terminal type
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by binbash on 2008-11-17
sudo gedit /boot/grub/menu.lst

you will see some lines like : 

title		Debian GNU/Linux, kernel 2.6.26-1-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda1 ro quiet
initrd		/boot/initrd.img-2.6.26-1-686


add rootdelay=90 after quiet

---

### Post by Coreigh on 2008-11-17
The file called menu.1st contains instructions for the system on where to find files and how to initialize your computer for start up. It is the file that shows the kernel choices when you first start the computer after the BIOS but before boot up starts.

menu.1st is found in the directory /boot/grub


First make a copy of the files for back up purposes use command line:
```
sudo cp /boot/grub/menu.1st /boot/grub/menu-1st.bak
```
sudo asks for a password, this is your password.

then open the menu.1st in gedit to add the delay command:
```
sudo gedit /boot/grub/menu.1st
```

near the top of the file you will find a line starting with 'default' and it will probably be 'default 0' (no quotes). This is the default setting, if it is 0 the the first set (1 is the second set and so on). Near the bottom you will find some sets of lines similar to this:
> title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=0cb89576-903f-42b4-be33-bef7d90910c4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=0cb89576-903f-42b4-be33-bef7d90910c4 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

Mine is an older one so not exactly the same. At the end of the line that starts with kernel add the delay 'rootdelay=90' Make sure to leave a space and do not use the quotes.

Save the file and reboot

If that does not solve the issue choose the recovery mode from the grub screen at boot time and un-do the changes.

---

### Post by Reno II on 2008-12-17
Pefect workaround!
Thanks all.

I performed a backup, gedit and set rootdelay=90
After reboot, everything booted well :-)

I typed rootdelay=90 twice:

> title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ede7a630-d383-41cb-9c9f-22686d9ed42b ro quiet splash [COLOR="Red"]rootdelay=90[/COLOR] 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ede7a630-d383-41cb-9c9f-22686d9ed42b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ede7a630-d383-41cb-9c9f-22686d9ed42b ro quiet splash[COLOR="Red"] rootdelay=90 [/COLOR]
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ede7a630-d383-41cb-9c9f-22686d9ed42b ro  single
initrd		/boot/initrd.img-2.6.24-22-generic


---

### Post by ShawnB391 on 2010-01-18
> add rootdelay=90
 
90 seconds wouldn't work for me, 600 seconds wouldn't work either, I'll have to try the other steps tomorrow...
 
Is there a way to retrive my files so that I could wipe everything clean and start again? My copy of Ubuntu is only a few weeks old, but I need to access my homework before I delete everything...

---

### Post by audiomick on 2010-01-18
> **ShawnB391 said:**
> 90 seconds wouldn't work for me, 600 seconds wouldn't work either, I'll have to try the other steps tomorrow...

can't help with that at all, sorry.
 
> **ShawnB391 said:**
> Is there a way to retrive my files so that I could wipe everything clean and start again? 

Boot into the live cd (the "try without changing option") and copy them off onto and external drive or something.

If you set up your system with a separate /home partition, you don't even need to do that (although having a backup is always a good idea), because you can simply re-mount it during a new install.

So, if your /home isn't a separate partition:
boot into the live cd and copy the home folder out to an external medium. I think there are arguments for doing this by creating an archive of the folder and copying that out, rather than just copying the files.

If you run into permission problems, which you shouldn't, try starting the file manager with
```
gksu nautilus
``` in a terminal.

If your home is a separate partition, do a backup of anything really important, then re-install. When you get to the partitioning tool during the installation, choose manual and re-mount the /home partition without formatting back to /home.

When you re-install, if you haven't had a separate home till now, maybe you want to think about making one....

---

### Post by ShawnB391 on 2010-01-19
> Boot into the live cd (the "try without changing option") and copy them off onto and external drive or something.

 
I've booted into a live cd but I'm unable to locate my files, how can I access my desktop?

---

### Post by PenguinInside on 2010-01-19
> **ShawnB391 said:**
> I've booted into a live cd but I'm unable to locate my files, how can I access my desktop?

When you boot from a live CD, the live CD desktop is a temporary one in computer memory.

Your desktop from your Ubuntu installation is on the hard disk.

There should be some or another menu option under Places (on the top taskbar) to get to your hard disk partition.

Try that and reply back here.

---

