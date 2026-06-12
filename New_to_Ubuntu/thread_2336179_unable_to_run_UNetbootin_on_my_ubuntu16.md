---
title: "unable to run UNetbootin on my ubuntu16"
date: 2016-09-05
forum: New to Ubuntu
---

### Post by walterwhite on 2016-09-05
i am trying to make bootable usb of windows 7 but UNetbootin is not working i have .bin file of it in downloads 
```
user@walter-white:~$ cd Downloadsuser@walter-white:~/Downloads$ chmod +x unetbootin-linux-494
user@walter-white:~/Downloads$ ./unetbootin-linux-494
./unetbootin-linux-494: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory



```

PS- i've already checked 'allow executing as program'

---

### Post by jimmy-frydkaer on 2016-09-05
```
sudo apt install unetbootin
```

You can try installing it from the repos

---

### Post by walterwhite on 2016-09-05
> **jimmy-frydkaer said:**
> ```
sudo apt install unetbootin
```

You can try installing it from the repos
already done that bro , but it isn't working the new update is not working that's why i'm sticking with v494

---

### Post by sudodus on 2016-09-05
> **walterwhite said:**
> i am trying to make bootable usb of windows 7 but UNetbootin is not working i have .bin file of it in downloads 
```
user@walter-white:~$ cd Downloadsuser@walter-white:~/Downloads$ chmod +x unetbootin-linux-494
user@walter-white:~/Downloads$ ./unetbootin-linux-494
./unetbootin-linux-494: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory



```

PS- i've already checked 'allow executing as program'

Unetbootin can create USB boot drives from linux iso files. I don't think it works with Windows iso files. You need some other tool or method to do that, and I think you have better chances to find such a tool at a Windows web site.

---

### Post by walterwhite on 2016-09-05
> **sudodus said:**
> Unetbootin can create USB boot drives from linux iso files. I don't think it works with Windows iso files. You need some other tool or method to do that, and I think you have better chances to find such a tool at a Windows web site.
v494 used to work and some users are saying it's still working besides for the last two hours i am banging my head to find such program (found few such as winusb i guess, didn't work too)
i have downloaded this .bin file it is not executing

---

### Post by sudodus on 2016-09-05
I searched the internet for** install window 7 from usb** and found several links, that look promising.

[Maybe you can try according to this link](http://www.howtogeek.com/howto/9585/how-to-setup-a-usb-flash-drive-to-install-windows-7/)

---

### Post by walterwhite on 2016-09-05
> **sudodus said:**
> I searched the internet for** install window 7 from usb** and found several links, that look promising.

[Maybe you can try according to this link]("http://www.howtogeek.com/howto/9585/how-to-setup-a-usb-flash-drive-to-install-windows-7/")
thank you so much for your effort sir, but the like you've given me redirects to a software which is for windows os and my hardware is running only on ububtu right now :confused:

---

### Post by yancek on 2016-09-05
> v494 used to work and some users are saying it's still working 

Magic?  Did you read the first line on the unetbootin home page quoted below.  No mention of windows or any other OS.

> [LEFT][COLOR=#000000][FONT=verdana]UNetbootin allows you to create bootable Live USB drives for Ubuntu and other Linux distributions without burning a CD.[/FONT][/COLOR][/LEFT]


Scrolling further down the page you will see the quote below.  So if you or someone else got it to work it could be magic or just luck as it certainly isn't designed to work with windows. 

> [B][LEFT][COLOR=#000000][FONT=verdana]Also, ISO files for non-Linux operating systems have a different boot mechanism, so don't expect them to work either.[/FONT][/COLOR][/LEFT]
[/B]



You can easily use Ubuntu to create a usb with a windows installer on it from Ubuntu and boot it from Grub.  The link below explains it in detail but make sure you read it carefully because there are a number of steps which are 'required'.  If the 'Disk Image Mounter' doesn't work for you because the windows iso is to large, you can loop mount instead and then copy the windows files to the flash drive.  The windows iso I had was a little over 3GB and I had to do that.  You can but don't need to install Grub on the usb.  You can simply put a menu entry modified to fit your situation from the example grub.cfg on the page in your grub.cfg.  If you plan to use this just once and I don't know why you would not, you can put the menuentry in the Ubuntu grub.cfg file.  Do not run update-grub.  When you have finished the windows install, run update-grub and it will remove the entry. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by sudodus on 2016-09-05
I am not sure that there is a good tool in linux, so I suggest that you borrow a computer with Windows for this task.

Maybe, only maybe, it is possible to run some tool via Wine or similar. For example: maybe [YUMI](http://www.pendrivelinux.com/yumi-multiboot-usb-creator) works also in linux, but it was made primarily to run in Windows.

---

### Post by Geoffrey_Arndt on 2016-09-05
This tool works great - - much better and more flexible than unetbootin (although for Linux bootables, mkusb is just excellent)

Etcher will create Windows, OS X or Linux bootable usb thumb drives.

[https://www.etcher.io/](https://www.etcher.io/)

---

### Post by walterwhite on 2016-09-05
> **Geoffrey_Arndt said:**
> This tool works great - - much better and more flexible than unetbootin (although for Linux bootables, mkusb is just excellent)

Etcher will create Windows, OS X or Linux bootable usb thumb drives.

[https://www.etcher.io/](https://www.etcher.io/)
i installed it , it installed os on usb but it's not working either i thought it would work :sad:
[IMG]http://i.imgur.com/n3ikVRq.png[/IMG]
it made it bootable but its still not booting :(

> **yancek said:**
> Magic?  Did you read the first line on the unetbootin home page quoted below.  No mention of windows or any other OS.



Scrolling further down the page you will see the quote below.  So if you or someone else got it to work it could be magic or just luck as it certainly isn't designed to work with windows. 



You can easily use Ubuntu to create a usb with a windows installer on it from Ubuntu and boot it from Grub.  The link below explains it in detail but make sure you read it carefully because there are a number of steps which are 'required'.  If the 'Disk Image Mounter' doesn't work for you because the windows iso is to large, you can loop mount instead and then copy the windows files to the flash drive.  The windows iso I had was a little over 3GB and I had to do that.  You can but don't need to install Grub on the usb.  You can simply put a menu entry modified to fit your situation from the example grub.cfg on the page in your grub.cfg.  If you plan to use this just once and I don't know why you would not, you can put the menuentry in the Ubuntu grub.cfg file.  Do not run update-grub.  When you have finished the windows install, run update-grub and it will remove the entry. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)
thanks for your illustrious reply bro but the thing is i don't know much about this stuff , i just got ubuntu on my pc,i don't understand grub or any of these other terms thats my i was talking about unetbootin

---

### Post by Geoffrey_Arndt on 2016-09-05
Has any usb bootable thumb drive worked on this PC?   What are the specs?  Are you certain the bios/uefi settings allow for usb boot . . sometimes there is a special key combo for enabling boot from usb thumbdrives.   I like to check the vendors website and download the user manual pdf or technical manual to verify how to manipulate the firmware.

---

### Post by walterwhite on 2016-09-06
> **Geoffrey_Arndt said:**
> Has any usb bootable thumb drive worked on this PC?   What are the specs?  Are you certain the bios/uefi settings allow for usb boot . . sometimes there is a special key combo for enabling boot from usb thumbdrives.   I like to check the vendors website and download the user manual pdf or technical manual to verify how to manipulate the firmware.
wow thanks for the interest ant yes i have installed many OSes in past using bootable USB , specs are pretty much disappointing , its an old machine , compaq510 2gigs of ram with core2duo, you can get the manual from official site ,

i never wanted to say this Ubuntu still lacks some really essential software :(

---

### Post by yancek on 2016-09-06
> thanks for your illustrious reply bro but the thing is i don't know much  about this stuff , i just got ubuntu on my pc,i don't understand grub  or any of these other terms thats my i was talking about unetbootin                 

You don't need to know much about this stuff you just need to be able to read, which you obviously do, and follow the instructions.  You don't need to understand how Grub works any more than you need to know how the windows BCD bootloader works to use it.  If the instructions aren't clear to you at some specific point just post a question here and someone should respond.

---

### Post by Geoffrey_Arndt on 2016-09-06
WalterWhite (..ok) . . ,



Re software options, are you familiar with the site [http://alternativeto.net/]("https://craftedflash.com/info/how-boot-computer-from-usb-flash-drive")  ??   

Also, perhaps these sites can will provide some additional things to try:   [URL="https://craftedflash.com/info/how-boot-computer-from-usb-flash-drive"]https://craftedflash.com/info/how-boot-computer-from-usb-flash-drive

[http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html](http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html)


[/URL]

---

### Post by sudodus on 2016-10-15
It seems difficult to find a linux tool that can create USB boot drives with Windows, so I added this feature to ***mkusb-nox***. It is still only available in the unstable PPA, because it is not tested much yet. Try it if you still need it. See this link,

[mkusb-nox 11.1.2: added feature: make USB install drive for Windows](https://ubuntuforums.org/showthread.php?t=1958073&page=22&p=13554330#post13554330)

It works with Windows 7 - 10, but you have to cope with a command line interface ;-)

---

### Post by colmax on 2016-10-15
I think LinuxLiveUsb works for windows
Cheers

---

