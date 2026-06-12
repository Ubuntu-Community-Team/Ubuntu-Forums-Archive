---
title: "Where  IS the source..."
date: 2005-01-07
forum: Repositories &amp; Backports
---

### Post by FXWGBill on 2005-01-07
I am a newbie, and  I am completely stumped.....

Where in Ubuntu is the Source code?

 I have searched and searched.... And I have NO clue....   


I am tryin to install my winmodem and I run the .setup /   and I get:


checking /usr/src/linux-headers-2.6.8.1-3-386/include/linux/modversions.h usability... no        <<<<<<<<<<<
checking /usr/src/linux-headers-2.6.8.1-3-386/include/linux/modversions.h presence... no          <<<<<<<<<<<<<<
checking for /usr/src/linux-headers-2.6.8.1-3-386/include/linux/modversions.h... no   <<<<<<<<<<
configure: error: modversions.h is missing - you should configure your kernel first!


It says I need to        "Configure my Kernal"

I can't find a thing that says  HOW!~        Much less WHERE IT EVEN IS!!!!

THEN!!!!!!!

I keep gettin THISSSSSSSS :


root@MrEccentric:~ # uname -r
2.6.8.1-3-386
root@MrEccentric:~ # cd /pctel-0.8.6
root@MrEccentric:/pctel-0.8.6 # ./configure --with-hal=pct789
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing                        <<<<<<<<<<<<<<<<<<
checking for working autoconf... missing                  <<<<<<<<<<<<<<
checking for working automake... missing           <<<<<<<<<<<
checking for working autoheader... missing                     <<<<<<<<
checking for working makeinfo... missing                 <<<<<<<<<<<
checking build driver for... HAL_PCT789
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking whether make sets ${MAKE}... (cached) yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for mawk... mawk
checking for /usr/src/linux/include/linux/modversions.h... no   <<<<<<<<<

configure: error: modversions.h is missing - you should configure your kernel fi rst!
root@MrEccentric:/pctel-0.8.6 #

and there it is AGAIN :   modversions.h     is missing...........

CONFIGURE YOUR KERNAL.......

Some help please, before I am bald     :confused: 


Thanx....

FX

---

### Post by tiiim on 2005-01-07
firstly if your compiling you need to get the basic compiling software this is done by:

```
sudo apt-get install build-essential
```


does that make a difference? i mean its helpful to have anyway cos it the basic tools to making software like your doing. it may or may not help let us know. Also anybody else knows Linux better than i do PLEASE post here.

---

### Post by tiiim on 2005-01-07
[QUOTE=tiiim]firstly if your compiling you need to get the basic compiling software this is done by:

```
sudo apt-get install build-essential
```


does that make a difference? i mean its helpful to have anyway cos it the basic tools to making software like your doing. it may or may not help let us know. Also anybody else knows Linux better than i do PLEASE post here.[/QUOTE]
 also wot modem are you trying to install and wot software? its true you may need to actually add your module to the kernel which case someone else needs to reply here and help but get that thing anymore... but it maybe a case where you may have to do some manually work... depends on your setup.

---

### Post by FXWGBill on 2005-01-07
I figured that part out.... and I think I found the other anwer I was looking for....

Correct me if I am wrong, but

apt-get install linux-source-2.6.8.1

that was the missing piece to the puzzle....

and it's a HSP 56  modem and I've seen it all over the board, but I think I can get it working now, with the info I found....


INCIDENTALLY!!

Are there  ANY other  'apt-get'  type things that I may need to go ahead and installl, whether I need them or not right now....  ????

Thanx!

FX


FX

---

### Post by tiiim on 2005-01-07
[QUOTE=FXWGBill]I figured that part out.... and I think I found the other anwer I was looking for....

Correct me if I am wrong, but

apt-get install linux-source-2.6.8.1

that was the missing piece to the puzzle....

and it's a HSP 56  modem and I've seen it all over the board, but I think I can get it working now, with the info I found....


INCIDENTALLY!!

Are there  ANY other  'apt-get'  type things that I may need to go ahead and installl, whether I need them or not right now....  ????

Thanx!

FX


FX[/QUOTE]
 glad you sorted that one then!  yeah that sounds about right what you done... silly me...

there are lots of stuff on apt-get just done an upgrade every so oftern to keep your system with the latest security issues. Also if you enable the unverse source you will get a lot more stuff for example totem-xine for playing dvds.

if you want the latest version of software but dont wont to go to hoary development there is an unofficial source you can add which will let you get firefox 1.0 and things. that info is all over the forum.

---

