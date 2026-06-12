---
title: "Drivers / installing softwares / newbie !"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by Sobirvs on 2012-04-18
hey Hi pros.

i am just new to linux , a friend suggested me to install ubuntu 10.04 LTS and i did by seeing some tut in google.

now everything is right , i can use ubuntu.

now i have a laptop Lenevo z570 and when i try to connec. to wireless it seems its disabled , i mean my sliding button(hardware) is ON , but stil wireless is disabled. idk , may be we need to install drivers n all , but hell i dont even know where to get em from and how to install , so anyone please guide me ?

another problem is , i needed to install google chrome / VLC 
now i did got a .deb file of google chrome from google itself and was so easy to install but when i tried to get VLC , i didnt got any deb file , instead i got like some .tar file , ok now i do know that it is kinda rar file so i did extracted it , but still where is the installer now ? i dont know

also , just to inform , i am dual booting ubuntu/win7 .

i dont know how to execute commands from terminal .
any info will be gladly given , please help :) and in return :popcorn: for you guys :D

---

### Post by ronaldbrijo on 2012-04-18
Not a pro here, but lets see. 

Regarding the wireless network i cannot assist, im not that clued up.

Go to the Ubuntu software centre or synaptics package manager, search for vlc player, and install it directly from there.

---

### Post by Sobirvs on 2012-04-18
i cant install from software center because my college have blocked the downloading things, thats why i downloaded it from phone(from win 7 internet.) but now that i am in ubuntu i cant connect any phone / wifi and **** , soo.... i would be wanting wifi drivers. i guess.

---

### Post by codemaniac on 2012-04-18
Ubuntu comes with all the drivers bundled within it , rerely you need to compile them manually .Still if 10.04 does not include Lenevo z570 wireless drivers , you can consider upgrading to newer versions of Ubuntu , ie 11.10.
The missing drivers might have been included in the newer ubuntu versions .

---

### Post by codemaniac on 2012-04-18
For securities sake institutions often block ssh and ftp ports so that the resources are not misused by people in the wild .
If you cannot download packages online via software center , you might take a look at offline package installation in Ubuntu .
[http://www.tuxgarage.com/2011/07/offline-package-installation-synaptic.html](http://www.tuxgarage.com/2011/07/offline-package-installation-synaptic.html)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Sobirvs on 2012-04-18
ahh a friend told me the same , to install new ubuntu version , k i will look into this , and about VLC installation , can anyone help me to install VLC ?

---

### Post by HiImTye on 2012-04-18
includes instructions for installing from the repos and installing from PPA
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by codemaniac on 2012-04-18
Hello Sobirvs ,
You need to download all the .deb s from a machine which has a working internet connection .Copy them to the machine in which uou dont have internet access .Install the packages using dpkg .You can download vlc and uts dependent packages from the below link .

[http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc)
```
sudo dpkg -i *deb
```

---

### Post by codemaniac on 2012-04-18
> **HiImTye said:**
> includes instructions for installing from the repos and installing from PPA
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

HiImTye ,
The OP is not having access to online repos .

---

### Post by Sobirvs on 2012-04-18
lol i dont even know what;s repos and PPA , guys newbie language plz :P

---

### Post by Sobirvs on 2012-04-18
> **codemaniac said:**
> HiImTye ,
The OP is not having access to online repos .

i do have internet axx but only from win 7 , not ubunutu as because of wifi drivers.

---

### Post by codemaniac on 2012-04-18
Hello Sobirvs , 
as i have mentioned the steps you need to perform in order to install VLC offline in your systems .You just need to download the .deb(they are like exe's in Win platform) from here [http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc) from your win 7 where internet is active.
Put them in a folder say offline_vlc.Transfer to a usb drive .reboot and go to Ubuntu ,copy offline_vlc dir to home partition in ubuntu.

and install it by dpkg .
```
cd offlline_vlc ;sudo dpkg -i *deb
```

---

### Post by Sobirvs on 2012-04-18
ok , here are the 3 files i downloaded from internet 

[img]http://i.imgur.com/wCG7z.png[/img]

now what to do , anyone guide me please?

---

### Post by Sobirvs on 2012-04-18
> **codemaniac said:**
> Hello Sobirvs , 
as i have mentioned the steps you need to perform in order to install VLC offline in your systems .You just need to download the .deb(they are like exe's in Win platform) from here [http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc) from your win 7 where internet is active.
Put them in a folder say offline_vlc.Transfer to a usb drive .reboot and go to Ubuntu ,copy offline_vlc dir to home partition in ubuntu.

and install it by dpkg .
```
cd offlline_vlc ;sudo dpkg -i *deb
```

i cant see any .deb file in here [http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc)

edit: what is dpkg ? sorry i am new , dont know :(

---

### Post by HiImTye on 2012-04-18
> **Sobirvs said:**
> i cant see any .deb file in here [http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc)

edit: what is dpkg ? sorry i am new , dont know :(
at the very bottom of the page, select either i386 or amd64 and then you will get a download link

---

### Post by Sobirvs on 2012-04-18
> **HiImTye said:**
> at the very bottom of the page, select either i386 or amd64 and then you will get a download link

and can u tell me what to select ? i think i should select amd64 , as my ubunutu is 64bit , but still just want to confirm.

---

### Post by HiImTye on 2012-04-18
yes, if you are using 64 bit Ubuntu then you need the amd64 version

---

### Post by codemaniac on 2012-04-18
suppose i want to download the .deb libaa1 package (first one in the list).
go to the link i have shared in my previous post, just navigate and select the architechture .
[http://mirror.pnl.gov/ubuntu//pool/main/a/aalib/libaa1_1.4p5-38build1_i386.deb](http://mirror.pnl.gov/ubuntu//pool/main/a/aalib/libaa1_1.4p5-38build1_i386.deb)

---

### Post by Sobirvs on 2012-04-18
i just downloaded both of [http://packages.ubuntu.com/maverick/amd64/vlc/download](http://packages.ubuntu.com/maverick/amd64/vlc/download)

and 

[http://packages.ubuntu.com/maverick/i386/vlc/download](http://packages.ubuntu.com/maverick/i386/vlc/download) 

from :- [http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc)

i get errors , while clicking on the file when i put it to home folder/newcontent folder

errors :- 

[img]http://i.imgur.com/K09Uq.png[/img]


[img]http://i.imgur.com/lWkJB.png[/img]

---

### Post by HiImTye on 2012-04-18
don't use 'i386' packages, they are not for the Ubuntu you are using

download whatever dependencies you need, in the same way. this is going to be a long, tedious process, without an internet connection

---

### Post by Sobirvs on 2012-04-18
> **HiImTye said:**
> don't use 'i386' packages, they are not for the Ubuntu you are using

download whatever dependencies you need, in the same way. this is going to be a long, tedious process, without an internet connection

so what to download actually now ? link ? so i can download >.< btw that sucks , people say linux is awesome , but for only installation of a single software , it gives me such a bad impression ! just for only 1 software , so many **** to do. rly that sucks.

---

### Post by HiImTye on 2012-04-18
download vlc-nox
[http://packages.ubuntu.com/maverick/amd64/allpackages](http://packages.ubuntu.com/maverick/amd64/allpackages)
all packages will be on that page, follow as previous. it will tell you what ever package it requires next.

installing on linux is generally easier and safer as they come from repositories, so you only use your package manager to download & install software. when you don't have an internet connection, that make it exponentially more difficult. remember, *Linux is not a free version of Windows*, it is a different operating system, with different priorities.

---

### Post by codemaniac on 2012-04-18
mate , first you need to check your machine's architechture and download the debs accordingly .in a terminal do this .
```
uname -m
```
You are facing the above error because of some dependency hell .
Get all deb files in a single directory and issue the dpkg command line as mentioned earlier .

---

### Post by HiImTye on 2012-04-18
remember that all packages that are required are listed on this page
[http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc)
all packages with a red circle are required packages for the package 'vlc'

---

