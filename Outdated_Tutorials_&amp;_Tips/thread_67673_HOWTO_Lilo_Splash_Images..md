---
title: "HOWTO: Lilo Splash Images."
date: 2005-09-20
forum: Outdated Tutorials &amp; Tips
---

### Post by sk545 on 2005-09-20
If you use Lilo instead of grub, and would like to change the default splash screen , then this is the guide for you.

First off, you have to have lilo installed and working.  I am not going to get into that, since this a guide to change the splash screen.  If you have lilo working, then proceed as follows:

1) Backup lilo.conf

```
 $ sudo cp /etc/lilo.conf lilo.confback
```

2) Download the splash screen to some directory:

[Download Splash Screen](http://www.kde-look.org/content/download.php?content=16756&id=1) 

The splash screen looks like this:

[Tux splash screen](http://www.kde-look.org/content/preview.php?preview=1&id=16756&file1=16756-1.jpg&file2=16756-2.jpg&file3=&name=Tux+Lilo+Selection+Screen) 

3) Untar the splash screen

```
 $ tar -zxvf 16756-Lilo-Tux.tar.gz 
```
This will give you two files:

lilo-boot-tux.bmp
README.TXT

4) You can go ahead and read the README.TXT, since that is where i got pretty much all the info for installing it. 

5)  Copy lilo-boot-tux.bmp to /boot

```
$ sudo cp lilo-boot-tux.bmp /boot 
```

6) Open up your /etc/lilo.conf file, and look for this section:

```
# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

```

Remove the entire line that says "#install=menu", then copy and paste these lines there instead:

```
install=bmp
bitmap=/boot/lilo-boot-tux.bmp
bmp-table=48,15,1,12
bmp-colors=250,,,255,,
bmp-timer=300p,184p,250,,

```

So, the entire section should now look like this:

```
# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
install=bmp
bitmap=/boot/lilo-boot-tux.bmp
bmp-table=48,15,1,12
bmp-colors=250,,,255,,
bmp-timer=300p,184p,250,,

```

Other things i left the same.

7) Lastly, run the following command

```
 $ sudo lilo
```
That will update lilo.  DON'T forget to run this command or it wont work!!

Thats it, reboot and enjoy your new bootsplash screen. :)

Yes, you can use any splash screen, but the above is the one i liked and got to work. 

I am also attaching my lilo.conf, in case anyone gets stuck.

Also, if you use grub, its guide is here:

[Grub Splash Guide](http://ubuntuforums.org/showthread.php?t=30341)

---

### Post by rich1889 on 2009-04-17
Managed to follow the above steps however after entering lilo into the shell command I get the following syntax error
Syntax error at or above line 14in file &#8216;/etc/lilo.comf&#8217;
Any help would be greatly appreciated 
Rich

---

