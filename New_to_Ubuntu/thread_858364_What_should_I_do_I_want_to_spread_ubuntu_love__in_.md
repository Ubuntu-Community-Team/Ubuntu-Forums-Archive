---
title: "What should I do?? I want to spread ubuntu love  in my towv"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by rushikesh988 on 2008-07-13
hello friends I am not new to ubuntu cause I am using it  from 2 monts ago 
I am heartly empressed By its productivity level and secury features..
I Got ubuntu free CD .. Bt now  I decided to spred ubuntu love into my town I just insatlled on my friends computers , I have also told some internet cafe keepers to use ubuntu and they promised me that they will use it since it is virus free and you don't to install  any other software for PDF's and offie suite too.. 
Bt.........
I am getting some problem in installing it on home computers which are always offline(don't have an internet connection) and thay wanna play and listen muzic (ubuntu don't come with suitable  audio video codecs) and yes thay want to connect the mobiles too like nokia for file transfer plz tell me any options  so that I can get success in making my town more open !!

---

### Post by ibuclaw on 2008-07-13
I would suggest you having a look at [KiwiLinux]("http://kiwilinux.org/kiwi/en/") then.
It is, essentially, exactly the same as Ubuntu, except restricted audio and video codecs are installed by default.
The Bootsplash and login prompt are different. But pretty much everything else is left intact.

Regards
Iain

---

### Post by YaroMan86 on 2008-07-13
> **rushikesh988 said:**
> hello friends I am not new to ubuntu cause I am using it  from 2 monts ago 
I am heartly empressed By its productivity level and secury features..
I Got ubuntu free CD .. Bt now  I decided to spred ubuntu love into my town I just insatlled on my friends computers , I have also told some internet cafe keepers to use ubuntu and they promised me that they will use it since it is virus free and you don't to install  any other software for PDF's and offie suite too.. 
Bt.........
I am getting some problem in installing it on home computers which are always offline(don't have an internet connection) and thay wanna play and listen muzic (ubuntu don't come with suitable  audio video codecs) and yes thay want to connect the mobiles too like nokia for file transfer plz tell me any options  so that I can get success in making my town more open !!

First and foremost, respect their decision to stay with what they have. One of the most important Linux philosophies is choice, after all.

Next off, you should probably prepare yourself to deflect and assuage FUD and misconceptions about Linux: That it's hard, that it's too reliant on the command line, that it is illegal, that only geeks use it, etc.

A LiveCD or a LiveUSB Drive are excellent for demonstrating Linux... if you have a laptop, you have an even better way of showing it off.

Next, you gotta remember your audience. If they're gamers, show them things like Neverball or run Orange Box games on WINE, if they're average users, show them firefox or evolution... if they're technical, show them the BASH terminal, use a lot of pipes! Demonstrate the GCC compilers, etc.

I would avoid talking down competing operating systems.

---

### Post by rushikesh988 on 2008-07-13
yes!!
thanks friends for your suggestions!!
do you have any Idea about connecting mobiles for file tranfers 
I know how to make dial up with it bt don't know how to prepare for file transfers!!

and how to make a liveUsb so that I can demostrate the ubuntu before installing it

---

### Post by aimpau on 2008-07-13
As far as I know, the Nokia PC suite is just a group of programs that is intended to recode music, organize pics, manage your phone. Since it is propriety, you have to install wine and run it from there.

For simple file transfers, meaning you need to transfer file A from your Nokia to your hard disk:

I believe when you plug your nokia to the PC using USB, the phone will give you an option whether to use the PC suite or just have a data transfer. Data transfer means that the memory card of your phone will be shown to linux as a temporary storage device.

---

### Post by Joeb454 on 2008-07-13
I gave up on the Nokia PC Suite (I only used it for sending text messages from my laptop ;))

Now when I want something from my phone, or want to add stuff to it, I use bluetooth :)

And spreading the Ubuntu Love: casually drop it into conversation ;)

---

### Post by rushikesh988 on 2008-07-13
The mobiles like nokia N72 73 6681 3230etc and SONY ERICSON  MOBILES LIKE K800 K790 W200 etc don't have that option only few mobiles (mostly having micro SD memory card ) have that option.

---

### Post by rushikesh988 on 2008-07-13
ya you are right bro .. we can use bluetooth

---

### Post by jimi_hendrix on 2008-07-13
well i love ubuntu but i cant give up my vista because im an avid gamer

my solution:

help them dual boot and if you dont know how to dual boot then google it and help them...if they still have xp/vista/macOS/whatever they can still listen to their music play games and do what ever when they need to but when they want to simply browse the web or write something ubuntu is fast/easy to use and they wont have to cough up money for microsoft office

---

### Post by rushikesh988 on 2008-07-13
ya i am doing that too..... I am providing ubuntu ebooks too to them so that they will learn it.. I am trying to give the ubuntu free of cost (when microsoft Xp/VIsta get corrupted in their computer they have to pay RS 300 to Shop for formatting their computer. ) Most of  people reinstall their software of computer due to virus problem I think this will be the good point for me that I can tell them that I can tell them that thier computer will be virus free after installation of ubuntu ...

---

### Post by anjilslaire on 2008-07-13
I use moto4lin to manage my motorola phones via usb. Works great, if anyone needs to manage their moto..

---

### Post by rushikesh988 on 2008-07-13
can you tell me its site ?

---

### Post by anjilslaire on 2008-07-13
> **rushikesh988 said:**
> can you tell me its site ?

It's in the repo's:

```

sudo apt-get install moto4lin

```

---

### Post by rushikesh988 on 2008-07-13
well thanks bt this will work only with that computers which are connected to internet . can you give me its web site so that I can download it & I can install it on that computers whhich are not connected to internet

---

### Post by rushikesh988 on 2008-07-13
i have installed it by terminal Bt I am unable to find it on my applications menu

---

### Post by AnLGP on 2008-07-13
I don't use the program you're speaking of but have you tried this?

```
moto4lin
```

?

or 

```
sudo moto4lin
```

?

By the way, I think it's fantastic that you want to mention linux to people who are looking for something different.  Might I suggest to mention this forum if they are connected to the internet?  That would help them with the system and transition, too.

---

### Post by Inxsible on 2008-07-14
> **rushikesh988 said:**
> i have installed it by terminal Bt I am unable to find it on my applications menu```
sudo aptitude -d install *package-name*
``` This will only download the deb package and not install it.

you can use the -d flag to download the packages and then use a USB flash drive or something to take those packages to any other computer without internet.

When you use the above command, the package is dowloaded under /var so you can use the locate command to find it under /var

Hope that helps !

---

### Post by anjilslaire on 2008-07-14
open a terminal & type 

```

sudo moto4lin

```
I say this because I've found the phones don't play well unless you are using root.

Most Ubuntu apps are pulled from the repositories, not individual websites. However, after downloading it, you can also grab the .deb out of your system from
/var/cache/apt/archives/

Otherwise, you can find an online listing of the repositories [here]("http://http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=moto4lin")

---

### Post by vikramaditya on 2008-07-14
Most of the resistance I've met during my *buntu crusade is that folks are already overwhelmed by the learning curve of modern life & just aren't inclined to abandon familiar platforms.  As **jimi_hendrix** already suggested, you could help them set up a dual boot configuration.  To encourage usage, you might then offer to be their personal telephone support technician as they learn the ropes.  I've been doing that for my Dad & brother-in-law, with encouraging results. :)

---

### Post by Inxsible on 2008-07-14
> **vikramaditya said:**
> Most of the resistance I've met during my *buntu crusade is that folks are already overwhelmed by the learning curve of modern life & just aren't inclined to abandon familiar platforms.  As **jimi_hendrix** already suggested, you could help them set up a dual boot configuration.  To encourage usage, you might then offer to be their personal telephone support technician as they learn the ropes.  I've been doing that for my Dad & brother-in-law, with encouraging results. :)
I put my parents on Ubuntu a while back....now they actually feel out of place in Vista ( which came pre-installed on the laptop that my father bought ;) )

---

### Post by rushikesh988 on 2008-07-14
> **anjilslaire said:**
> open a terminal & type 

```

sudo moto4lin

```
I say this because I've found the phones don't play well unless you are using root.

Most Ubuntu apps are pulled from the repositories, not individual websites. However, after downloading it, you can also grab the .deb out of your system from
/var/cache/apt/archives/

Otherwise, you can find an online listing of the repositories [here]("http://http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=moto4lin")
 
Thanks for suggestion brother i got most of the apckags that I 
 have installed from command promt now I can install them to another computer

---

### Post by rushikesh988 on 2008-07-14
thanks for suggussion Inxsible  


It will definetely help me !!

---

### Post by rushikesh988 on 2008-07-14
I am having some problem in replacing my friends  sm3840 driver with ibsane-sm3840.so.1.0.15 driver can somebody tell me detailed(step by step) process about it 




I have experence installing HP PRINTER bt not about microtek scanner

---

### Post by rushikesh988 on 2008-07-19
friends I am getting problem in installing it on A computer having a configuration  
128Mb RAM 
40 GB HDD
LG CD WRITTER 
 it is giving  error  something saying LOGICAL BLOCK 


Can You plz tell me any solution ??

---

### Post by wpshooter on 2008-07-19
> **rushikesh988 said:**
> friends I am getting problem in installing it on A computer having a configuration  
128Mb RAM 
40 GB HDD
LG CD WRITTER 
 it is giving  error  something saying LOGICAL BLOCK 


Can You plz tell me any solution ??

This is probably due to the small amount of memory on this machine.

You are probably going to have to go with Xubuntu for that machine.

---

### Post by Frenske on 2008-07-19
Ubuntu does not work on 128MB computers and its recommended to have at least 512MB RAM (1GB preferable). You could look into Xubuntu which is lighter - not sure what the specs are.

---

### Post by t0p on 2008-07-19
> **rushikesh988 said:**
> 
I am getting some problem in installing it on home computers which are always offline(don't have an internet connection) and thay wanna play and listen muzic (ubuntu don't come with suitable  audio video codecs) and yes thay want to connect the mobiles too like nokia for file transfer plz tell me any options  so that I can get success in making my town more open !!

A way for you to take on the problem of people having off-line computers is to encourage them to connect their mobile phones - and show them how to use their phones as modems! Then they can get the video and audio codecs and other software.

Check out the link in my sig for a tutorial on how to use a mobile phone as a modem.  It generally isn't too difficult.

---

### Post by t0p on 2008-07-19
> **rushikesh988 said:**
> The mobiles like nokia N72 73 6681 3230etc and SONY ERICSON  MOBILES LIKE K800 K790 W200 etc don't have that option only few mobiles (mostly having micro SD memory card ) have that option.

I have had two sony ericsson phones (w300i and k800i) and they both display a menu offering Phone Mode (for internet access etc) and File Transfer (up/downloading music, photos etc between phone and computer).

As for nokias: there is an app in the repos called **gnokii**, and a graphical front-end called **xgnokii** that acts as a file manager for transfer of files between the nokia phon and computer.

---

### Post by rushikesh988 on 2008-07-19
Yo thanks T0p brother I will download both that apps!and I will try Xbuntu too!

---

### Post by rushikesh988 on 2008-07-19
Can anybody tell me,
Is there is any way for installing AuDio/Video Codecs without connecting to internet???(This is  what coz I can download that but not my all friends have internet connection)

---

### Post by markbuntu on 2008-07-19
You can download the debs and burn them to a cd that can act like a local repository. Then you can install them by directing Synaptic to use the cd for machines that are off line.

---

### Post by dgkalmegh on 2008-07-22
can you tell me its web address to download that codecs/debs ???

---

### Post by hunter2000+ on 2008-09-22
*I know this is a very delayed reply. But someone out there without intnet connection who wants to listen music or watch movies in ubuntu might find this useful.*
[[COLOR="DarkGreen"]Check this post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5697696")

---

### Post by Bucky Ball on 2008-09-22
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

That might help with the live usb install.

---

