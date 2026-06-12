---
title: "Several ubuntu versions at boot up"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Mariane on 2008-10-23
Hi, 

I have a dual boot Ubuntu / Vista but strange things happened with the boot menu. I used to have the choice between Ubuntu, Ubuntu in safe mode or Vista, full stop. Now I have 3 choices for each of Ubuntu and Ubuntu safe, one of which does not function. The default choice is memory check. This option just appeared one or two months ago. I don't mind having the memory check but I would like Ubuntu to be the default and not the memory check. 

I am worried that if I try to remove the 2 extras Ubuntus I'll remove the good versions and I'll be left with the not functionning one. 

When I look at the folders, I see only one Ubuntu (ie I have only one "usr" folder, etc). 

How can I get rid of the unwanted bootup options, please? 

BTW, what does "usr" mean? I thought it was "user" but "user" would be "/home/username", no? 

Mariane

---

### Post by drs305 on 2008-10-23
What you are seeing is normal when a new kernel is introduced. I have written a tutorial that explains it and how to manage what you see and what is stored on the computer:

[Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Essentially you can hide the number of kernel displayed and/or you can remove older kernels completely from your computer. I recommend StartUp-Manager to manage your grub menu and the tutorial covers how to install and use this gui-based application to tweak your settings.

Added: usr stands for 'unix system resources'

---

### Post by Duck2006 on 2008-10-23
You can edit your menu.lst and # out the old kernel's and leave the new one or your and delete the old ones from the menu.lst. In the eterminal type,

gksudo gedit /boot/grub/menu.lst

---

### Post by Christmas on 2008-10-23
You can get rid of any unwanted entries there easily. Just edit with super user privileges the /boot/grub/menu.lst file.

Here's how mine looks like (for Intrepid Ibex beta):
```
title           Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=2651e4c6-4feb-4493-aece-77d6ce7e54d2 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=2651e4c6-4feb-4493-aece-77d6ce7e54d2 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.27-4-generic root=UUID=2651e4c6-4feb-4493-aece-77d6ce7e54d2 ro quiet splash
initrd          /boot/initrd.img-2.6.27-4-generic
quiet

title           Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.27-4-generic root=UUID=2651e4c6-4feb-4493-aece-77d6ce7e54d2 ro  single
initrd          /boot/initrd.img-2.6.27-4-generic

title           Ubuntu intrepid (development branch), memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
Now, to edit it use *sudo nano /boot/grub/menu.lst*, or, if you are more comfortable with a text editor, use *gksudo gedit /boot/grub/menu.lst* or *kdesu kate /boot/grub/menu.lst* for Kubuntu.

And edit it by deleting an entire section, like the one below:
```
title           Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.27-4-generic root=UUID=2651e4c6-4feb-4493-aece-77d6ce7e54d2 ro  single
initrd          /boot/initrd.img-2.6.27-4-generic

```
Just make sure you don't mess up with it, so first make a backup:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

After removing any of the sections, that option won't appear there when booting up. Also, you can put Windows XP as the first option by moving it up in that file, or play with other parameters too, just be careful. I'm not sure whether this is the recommended way to do it though. Also, there was a graphical tool for editing this file too, but I recommend a text editor. You can find a graphical editor [here](http://grubconf.sourceforge.net/), it's called GrubConf.

Edit:
[quote=Mariane]BTW, what does "usr" mean? I thought it was "user" but "user" would be "/home/username", no? [/quote]
/usr is a standard Linux (and UNIX) directory which contains application directories, like /usr/bin for binary executables, or /usr/share/man/ for man pages etc.

/home is another standard directory which provides individual directories for all the users on the system. Usually, /home/your_username and /tmp are the only two directories which give you write permissions, unless you set other permissions with root privileges or depending on which groups users are in.

I strongly recommend that you read [this](http://www.tuxfiles.org/linuxhelp/linuxdir.html) friendly tutorial on [tuXfiles.org](http://www.tuxfiles.org/).

---

### Post by Duck2006 on 2008-10-23
> Also, you can put Windows XP as the first option by moving it up in that file,

Do not do this. Edit the line

default		0

If you have four entry count down (start at 0 not one) so you will have to enter that number there ie if you have for then you would edit to read.

default		3

---

### Post by Christmas on 2008-10-23
> **Duck2006 said:**
> Do not do this. Edit the line

default		0

If you have four entry count down (start at 0 not one) so you will have to enter that number there ie if you have for then you would edit to read.

default		3
That's nice to know, I never wandered what other parameters meant. Thanks for sharing it!

---

### Post by alphaniner on 2008-10-23
> **drs305 said:**
> Added: usr stands for 'unix system resources'

Hey cool!  Do you know what etc stands for?

> If you have four entry count down (start at 0 not one) so you will have to enter that number there ie if you have for then you would edit to read.

Keeping in mind that you have to count the 'Other Operating Systems' line as well as the actual OS lines.

---

### Post by sethvath on 2008-10-23
GUI friendly way to editing grub files:

[http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

Screenshots 
[http://web.telia.com/~u88005282/sum/screenshots.html](http://web.telia.com/~u88005282/sum/screenshots.html)

---

### Post by philinux on 2008-10-23
Yep nice gui. 

startupmanager is in synaptic or

sudo apt-get install startupmanager

---

### Post by Duck2006 on 2008-10-23
> **philinux said:**
> Yep nice gui. 

startupmanager is in synaptic or

sudo apt-get install startupmanager

+1 Yep very nice

---

