---
title: "Help! error message when booting into OS"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by liamr_spencer on 2008-05-30
Hi, 

I was having problems trying to get my onboard soundcard to work after just installing ubuntu, so after reading the comprehensive guide i rebooted to go into the bios settings and check that everything was A ok. It showed that the soundcard was working so i rebooted to get back to the main os

however this keeps failing and i get a message saying 

kinit: no resume image, doing normal boot...

I then am asked for my login and password, this then activates what I would consider a full version of the terminal. 

is there anyone who can tell me how to get back into ubuntu without reinstalling?

---

### Post by spiderbatdad on 2008-05-30
I'm thinking from the terminal prompt:
```
sudo update-initramfs -c
```The -u flag attempts to update an existing image. The -c flag would create an image. Sudo assumes you are booting into userspace...You might check this with the command: ```
id
```to make sure your username and id=1000 comes up.

---

### Post by liamr_spencer on 2008-05-30
hey! 

thanks for the response! I tried the command but it has just given me a list of options and no reboot into the system!

---

### Post by cdtech on 2008-05-30
When your in the CLI mode (command line) give us the output of:

cat /boot/grub/menu.lst

That will help....

---

### Post by liamr_spencer on 2008-05-30
i get:
## end default options ##
title      ubuntu 8.04, kermel 2.6.24-16-generic
root       (hd0,0)
kernel     /boot/vmlinuz-2.624-16-generic root=UUID=2117ded9-4324-467e-a9f4-0a28e1b2fe65 ro quiet splah
initrd     /boot/initrd.img-2.6.24-16generic
quiet    

title      ubuntu 8.04, kermel 2.6.24-16-generic (recovery mode)
root       (hd0,0)
kernel     /boot/vmlinuz-2.624-16-generic root=UUID=2117ded9-4324-467e-a9f4-0a28e1b2fe65 ro single 
initrd     /boot/initrd.img-2.6.24-16generic

title      ubuntu 8.04, memtest86+
root       (hd0,0)
kernel     /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

sorry guys i am a total no0b!

---

### Post by spiderbatdad on 2008-05-30
So...are you still stuck with only a terminal after boot?
Perhaps try:```
startx
```

or ```
sudo apt-get install ubuntu-desktop
```

When you ran update-initramfs -c did you select any option, or just shut down because you didn't know what to do? Little bit of a lack of feedback there.

---

### Post by cdtech on 2008-05-30
can you post your fstab file:

cat /etc/fstab

---

### Post by cdtech on 2008-05-30
This is a problem with the resume UUID of the swap partition:

```
cat /etc/initramfs-tools/conf.d/resume
```

should be the same as:
```
blkid
```
under the swap block id #

The fstab file under the swap partition should show 0 2, and then type:
```
sudo update-initramfs -u
```

This is another method if the above dosen't work:

```
edit /etc/usplash.conf to use your laptop's true resolution.
```
then run the following commands:
```
$ sudo swapoff /dev/sda2 <--your swap dev
to turn off the swap partition
$ sudo mkswap /dev/sda2 <--your swap dev
this rebuilds the swap partition
$ sudo update-initramfs -u
to rebuild the initial boot image to use your new, rebuilt swap partition
```

---

### Post by liamr_spencer on 2008-05-30
cheers spiderbatdad.
the very simple solution you offered worked a treat! I am back on and operational. 

cheers guys very much for your help!

:) :) :)

---

### Post by liamr_spencer on 2008-06-01
hey,

was having this problem (see thread) a couple of days ago and used the 

startx command to get me back into the os system. I thought the problem had gone away but whenever i restart i boot into (what i think is) the command line. i have to use the startx command everytime to boot into the os. 

is there a way around this?

any help would be very appreciated.

---

### Post by spiderbatdad on 2008-06-01
did you understand what cdtech wrote?

Run the command, after login, ```
sudo blkid
```write down the id for the swap partition. Then run ```
cat /etc/initramfs-tools/conf.d/resume
```see if they match.

If not, edit the file /etc/fstab:
```
gksu gedit /etc/fstab
```make the swap uuid= match the blkid. Save the file. Run:```
sudo update-initramfs -u
```Reboot.

---

### Post by liamr_spencer on 2008-06-01
i didnt really understand it cos i was panicking. the quick fix solved the problem but didnt fix it. will have a go now.

thanks.

---

