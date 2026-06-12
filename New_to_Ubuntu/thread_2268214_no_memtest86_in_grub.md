---
title: "no memtest86 in grub"
date: 2015-03-07
forum: New to Ubuntu
---

### Post by allen11 on 2015-03-07
I have recently rebuilt this pc, had to replace the motherboard, and it is operational but does get relatively frequent crashes any time I run a movie in flash etc.  I suspect the memory is bad because I confirmed one of four sticks is inoperable.  Currently I am running 2 sticks of memory and it is good enough to boot into ubuntu and web browse but a crash seems inevitable after a couple hours or so.  

It past the system benchmark feature related to memory but I would like to run memtest86 or something similar.  This gets to my problem, apparently memtest86 is available in grub.  Sadly I don't have memtest86 as an option in grub, all I have is 1)Ubuntu 2)Ubuntu safe mode options.  I am not even certain if memtest86 is installed or not.  If anyone has a solution or recommendation I would appreciate it.  I have read through many threads related to this topic, and it was quite a few, but all of them are quite old and related to older versions of ubuntu.  

I should add that my Bios is a uefi.  I am obviously a new user with this MB (and to ubuntu) so unsure of options so far.  Running all settings as default.

i5 750
asrock p67 transformer
4gb corsair ddr3
wd green 1tb
radeon hd 5850
generic 700 psu

Thank you.

---

### Post by yetimon_64 on 2015-03-07
You don't mention what Ubuntu version you are on, but if memtest is not installed you may be on 14.04 or higher. I read somewhere recently Canonical was considering it for removal from the default install, but I don't know if that was followed through with.

To check if a package is available open a terminal (ctrl + alt + t, keyboard combination in Unity), 
For memtest86+
```
apt-cache policy memtest86+
```
For example : from my Debian install I get

> ```
 $ apt-cache policy memtest86+
memtest86+:
  Installed: 4.20-1.1
  Candidate: 4.20-1.1
  Version table:
 *** 4.20-1.1 0
        990 http://ftp.au.debian.org/debian/ wheezy/main amd64 Packages
        100 /var/lib/dpkg/status
```

If yours shows "Installed:none", then issue the following command in terminal, enter your password (it won't show, a security measure) then press enter,
```
sudo apt-get install memtest86+
``` this should automatically add a grub menu entry for it. Then you can use it from the next boot up. Cheers, yeti.

Edit: I just realized this post is in "New to Ubuntu", alternatively you could search in Software Center for "memtest86" and install from there if not already installed (note there may be 2 possible downloads, memtest86 and memtest86+, you only need to install 1, afaik)

---

### Post by ajgreeny on 2015-03-07
Your grub menu has an Advanced entry at the bottom and I think memtest86+ is in there, not on the first screen you see.

This makes for a cleaner grub menu and means you don't see all the old kernels either, though they are all there if you need them.

Use command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-82
``` and you will see what exactly is in your grub menu, even if you can't see all of it immediately.

EDIT:
I have just looked and it appears that, as you thought,  memtest is no longer in the grub menu.  I was not aware of this and admit to being surprised.
 I wonder why it was removed?

I never see the grub menu any more so I may be quite wrong about all this.

EDIT 2:
I have just looked on another machine with Lubuntu 14.04 and memtest is certainly on that grub menu, so I am a bit baffled about what is happening on your machine.

---

### Post by allen11 on 2015-03-07
> **yetimon_64 said:**
> You don't mention what Ubuntu version you are on, but if memtest is not installed you may be on 14.04 or higher. I read somewhere recently Canonical was considering it for removal from the default install, but I don't know if that was followed through with.

To check if a package is available open a terminal (ctrl + alt + t, keyboard combination in Unity), 
For memtest86+
```
apt-cache policy memtest86+
```
For example : from my Debian install I get



If yours shows "Installed:none", then issue the following command in terminal, enter your password (it won't show, a security measure) then press enter,
```
sudo apt-get install memtest86+
``` this should automatically add a grub menu entry for it. Then you can use it from the next boot up. Cheers, yeti.

Edit: I just realized this post is in "New to Ubuntu", alternatively you could search in Software Center for "memtest86" and install from there if not already installed (note there may be 2 possible downloads, memtest86 and memtest86+, you only need to install 1, afaik)

Thank you for your quick response.  Sorry for not being specific before, I am running 14.04 new install.
So I performed the terminal command you suggested and it does show memtest is installed, I assume it is version 4.20-1.1.

allen@HTPC:~$ apt-cache policy memtest86+
memtest86+:
  Installed: 4.20-1.1ubuntu8
  Candidate: 4.20-1.1ubuntu8
  Version table:
 *** 4.20-1.1ubuntu8 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status

It is interesting that something like memtest would be considered for removal especially since it has been present for some time in the os.  I have not read that bit of information yet, like I said most of the threads I have been reviewing were dated a a year or more ago.

Thanks for the help.
Allen

---

### Post by allen11 on 2015-03-07
Thank your for the response Ajgreeny.  I ran the command and it doesn't appear to be present in the grub.

allen@HTPC:~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-82
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuen
    menuentry 'Ubuntu, with Linux 3.16.0-31-generic' --class ubuntu --class gnu-linux
    menuentry 'Ubuntu, with Linux 3.16.0-31-generic (recovery mode)' --class ubuntu -
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic' --class ubuntu --class gnu-linux
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode)' --class ubuntu -

So with Yeti's post I confirmed memtest86+ is installed yet with your post I confirmed it isn't in grub.  I'm baffled as well but considering this is a new world to me that doesn't surprise me.  

Thanks for the help.  Any other comments or suggestions would be appreciated.

---

### Post by grahammechanical on 2015-03-07
The Grub boot menu is based on what is in /boot/grub/grub.cfg and grub.cfg is composed from what is in a series of files in /etc/grub.d/. One of those files is called 20_memtest86+. That file has to have its properties set to allow the file to execute as program otherwise there will not be an entry for memtest in the Grub boot menu.

All of the files in /etc/grub.d should have their permissions set by default to allow the file to execute as program. By removing that permission we effectively disable that file from working.

Regards

---

### Post by allen11 on 2015-03-07
> **grahammechanical said:**
> The Grub boot menu is based on what is in /boot/grub/grub.cfg and grub.cfg is composed from what is in a series of files in /etc/grub.d/. One of those files is called 20_memtest86+. That file has to have its properties set to allow the file to execute as program otherwise there will not be an entry for memtest in the Grub boot menu.

All of the files in /etc/grub.d should have their permissions set by default to allow the file to execute as program. By removing that permission we effectively disable that file from working.

Regards

Thanks for the response Grahammechanical.
I just installed this 14.04 3 days ago.  Are you suggesting that possibly it is not set to execute as program or are you saying I should confirm the setting in the properties of the file?  I can't determine from what you said if it was instructions to do something or if you were stating a point of fact?

If it is set to execute as program by default wouldn't it currently be in the proper configuration already considering this is a new install?  I found the location that you are referencing, at least I believe so, this is what it shows....


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


This is a pretty obscure folder and at the top it says "DO NOT EDIT THIS FILE."  I don't know what to make of this though.

---

### Post by allen11 on 2015-03-07
Reading other threads has given me some more info and some conflicting points as well.  

Memtest86 =closed source, can be run on uefi bios
memtest86+ =open source, can not be run on uefi bios
according to this thread....   [https://ask.fedoraproject.org/en/question/45248/memtest86-does-it-support-uefi/](https://ask.fedoraproject.org/en/question/45248/memtest86-does-it-support-uefi/)

Others have said the above is not correct.  Obviously I don't know which is correct.  I can say at this point I wish I had a basic BIOS and not the UEFI, which btw is not helpful (the mouse doesn't work in it anyway).  

During rebooting I noticed that "c" will open a command line in GRUB 2.02.  I do not know what text or command would run my installed Memtest86+ program though.  **Does anyone know what command would run memtest86+ in the grub 2.02 command line?  **I pressed TAB for the list of common commands but nothing related to memory was present.

---

### Post by yetimon_64 on 2015-03-07
> This is a pretty obscure folder and at the top it says "DO NOT EDIT THIS FILE."  I don't know what to make of this though
You'll have trouble trying to edit that file, it is read only for root. ;) /etc/grub.d/20_memtest86+ is the one to look at. 

> ### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###
The file /etc/grub.d/20_memtest86+ is the one to check the permissions of. 
In terminal issue the following command to check
```
ls -l /etc/grub.d/20_memtest86+
```

Again, from my install ...
> ```
:~ $ ls -l /etc/grub.d/20_memtest86+
-rw-r--r-- 1 root root 1570 Nov 14  2011 /etc/grub.d/20_memtest86+
```

You can see from the "-rw-r--r--" that NO execute permissions are set. In other words I've turned memtest86+ off from showing here using the permissions of the file. (I like to have it available with two terminal commands, but don't like it cluttering up my grub screen when not in use :))

If they were set then "-rw-r--r--" would look like "-rwxr-xr-x". 

Check out how yours is. If it is NOT set executable then issue the next command in terminal to turn on the executable bit on the file.
```
sudo chmod +x /etc/grub.d/20_memtest86+
```
then follow that up with the command
```
sudo update-grub
```
to update the grub.cfg file.

After updating grub run ajgreeny's command again to look at the menuentries, you should now see a couple of entries added. Good luck, yeti.

EDIT: just noted your last post, try the permissions above and see if memtest86+ works, if not uninstall it and try again with memtest86.

---

### Post by allen11 on 2015-03-07
Thank you for the explanations Yeti.  It makes sense.  I followed your latest instructions and found that execute permissions are set with my version.  Below is the result of the command....
allen@HTPC:~$ ls -l /etc/grub.d/20_memtest86+
-rwxr-xr-x 1 root root 1992 Mar 12  2014 /etc/grub.d/20_memtest86+

Considering it is installed properly and set to execute with grub2, yet it doesn't, I tried the next option.  
I uninstalled memtest86+ and proceeded to try to install memtest86 but I failed to do so.  86 isn't an option for install in the software center.  So I went to the memtest website, followed the instructions and downloaded a usb version from the website directly, which I did, but i wasn't able to get it to be recognized during boot (after several attempts).  I suspect the uefi may play a role in this problem but I am not sure of that.  

To be honest I think I have spent too much time trying to get this to work in this pc.  I am going to swap the memory out of another system that runs windows 7 and give it a try there.  It has been a couple years since I used memtest86 on the other system however I remember it being very simple and effective.  I would have liked to have memtest available on this pc because it would have been a potentially handy tool if I start getting stability issues in the future but sometimes you gotta take the other road to reach your destination. 

I greatly appreciate your help on this though.  Thank you.
Allen

---

### Post by ajgreeny on 2015-03-08
I was certainly totally unaware of the UEFI and memtest problem, but it explains why I do not find it in my main Xubuntu 14.04.2 installation on a UEFI machine but it is in the grub menu in my Lubuntu 14.04.2 on another machine that's not UEFI.

---

