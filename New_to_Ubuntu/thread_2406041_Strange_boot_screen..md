---
title: "Strange boot screen."
date: 2018-11-14
forum: New to Ubuntu
---

### Post by malikiag on 2018-11-14
I went to start up my laptop and at first it shows the ubuntu loading screen. Then it changes to a black screen with a list of code I don't understand. What is going on? I've had nothing but problems since downloading Ubuntu. Even my dad has given up on it.

The first three lines of code from the latest screen to come up is:
[   OK   ] Started daily cleanup of Temporary Directories
[   OK   ] Reached target Timers
[   OK   ] Listening on Avahi mDNS/DNS-SD Activation Socket.

---

### Post by Scary Rob on 2018-11-15
Those messages, so far as I can tell, are completely benign parts of the boot process.

The code that you're getting is just the boot process. It's normally covered by the ubuntu start screen, but if you press a key while the start screen is on, it'll vanish and you will be able to see the boot processes doing their thing. They're displayed in chronological order, with the latest thing appearing at the bottom. If ubuntu is failing to start properly, the last few lines of code (i.e. the ones at the bottom of the screen) will be the ones that'll tell us what's going wrong. Could we have those, please?

---

### Post by malikiag on 2018-11-15
It pops up even when I don't touch anything while I'm booting. How many of the last lines of code do you need? Also, it will stop scrolling and working on anything after a moment. It just sits there. What's worse, I can't find out how much battery I have left.

---

### Post by 23dornot23d on 2018-11-15
> 
What's worse, I can't find out how much battery I have left.                 



Just for information - once you get to see a login and password ............ Ctrl+Alt+(function key 1) - login with your username and password as normal if it allows it.

you will see a

[B]$

then type in the following to get your battery status ............ ( this works on my own and the results are below the instruction )

```


$ upower -i /org/freedesktop/UPower/devices/battery_BAT0


  
```[/B]```
native-path:          BAT0
  vendor:               [MKF_CUSTOMER]
  model:                [MKF_BASEBOARD_ID]
  power supply:         yes
  updated:              Thu 15 Nov 2018 07:06:51 PM CET (116 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              48.2112 Wh
    energy-empty:        0 Wh
    energy-full:         49.4316 Wh
    energy-full-design:  56.16 Wh
    energy-rate:         0 W
    voltage:             12.398 V
    percentage:          97%
    capacity:            88.0192%
    technology:          lithium-ion
    icon-name:          'battery-full-charged-symbolic'


```
Just thought this might help for that part of the problem ....... you may come back to this later on - once you get to a command line at least.

---

### Post by malikiag on 2018-11-15
I don't even get to login. I tried ctrl + alt + F1 on the screen but it does nothing. Help please! It seems the last bit of code is pretty consistent.
[   Ok   ] Reached target Sound Card.' for details.d...details. reporting is enabled. was shut down....

What does this mean?

---

### Post by mp3coldco on 2018-11-15
Same situation for me

---

### Post by NM5TF on 2018-11-15
@malikiag and @mp3coldco

"my laptop won't boot" is so vague as to be virtually worthless

we need more information to be able to help...such as:

laptop model
processors
memory capacity
Ubuntu version 18.04 ???
etc

more information is better than no information

tommy

---

### Post by Scary Rob on 2018-11-16
> **malikiag said:**
> I don't even get to login. I tried ctrl + alt + F1 on the screen but it does nothing. Help please! It seems the last bit of code is pretty consistent.
[   Ok   ] Reached target Sound Card.' for details.d...details. reporting is enabled. was shut down....

What does this mean?

As I said earlier, the code you're seeing is the boot process happening. Or not happening by the looks of things.

So what happens next? Does the laptop just stay with this message as the last thing on the screen?

And as NM5TF said, it would help us to know the make and model of the laptop and the edition of Ubuntu you're using.

---

### Post by malikiag on 2018-11-16
It's a converted Lenovo X131e. It used to have ChromeOS but It was a pain to use so I switched. I'm using Bionic Beaver 18.04. As for the code, I remember once it had sat for almost a half hour and two new sets of code came onto the screen. I can't remember what they said and the laptop is dead so I can't check. I remember the first part, the part of the code on both lines that has brackets were around a set of numbers not OK like the rest.

---

### Post by malikiag on 2018-11-16
I think it has 15 GB of memory, but it was running low last time I was on. When I turn my laptop on, it show the purple screen, then the ubuntu logo with the 5 loading dots underneath. Then it just changes the the screen full of code.

---

### Post by NM5TF on 2018-11-16
15 GB of RAM is NOT low memory.....specs say max memory of 8 GB DDR3.....I only have 3.4 GB on this machine & have never run low....

at boot it looks like it starts correctly.....purple screen followed by Ubu logo....if the kernel parameter is not 
set to "quiet" you will see lines of code scrolling past...but it doesn't complete the boot sequence it seems...

how did you install Ubuntu...from a DVD or USB stick ???

did you download it yourself...if so, did you run a checksum to be sure it was error free ???

sounds like a re-install could be necessary....but run the checksum to be sure the source is error free...

tommy

---

### Post by malikiag on 2018-11-16
I installed with a usb stick. What is a checksum and how do I run it with this problem?

---

### Post by Scary Rob on 2018-11-16
> **malikiag said:**
> I installed with a usb stick. What is a checksum and how do I run it with this problem?

The checksum should be run on the .iso file you originally downloaded before you put it on the USB stick. Here are instructions: [https://raylin.wordpress.com/downloads/md5-sha-1-checksum-utility/](https://raylin.wordpress.com/downloads/md5-sha-1-checksum-utility/)

Hashes to check against are in text files here: [http://releases.ubuntu.com/18.04.1/](http://releases.ubuntu.com/18.04.1/)

To check the integrity of the stick itself, when you boot the system from USB, the first menu you get should give you an option for the stick to self-check. Just tap the arrow key down to that option and press "enter".

Regarding the Lenovo X131e, I found this website: [http://www.linlap.com/lenovo_thinkpad_x131e_-_amd](http://www.linlap.com/lenovo_thinkpad_x131e_-_amd)

Long story short, it doesn't look good for hardware compatibility. There is little indication on the linlap page of why Gnome crashes (unless EGL is the problem), but if you're getting boot messages instead of a splash screen, this may be what's happening. You could try Kubuntu instead, because the KDE desktop environment is built on a different underlying set of programs to Gnome, and might play more nicely. The lack of 3D acceleration may still pose a problem - you may have to go through the system settings and switch off a load of desktop effects for best results.

And you'll probably have to plug it into your router by ethernet cable to run your first update and install the Broadcom drivers.

EDIT: The linlap page says that MATE worked: [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)
(and the sha256 checksum result is handily provided with the download link)

---

### Post by NM5TF on 2018-11-16
@Scary Rob

good advice you gave +1

but I believe the OP said his laptop is "dead".....if so, how can he do what is suggested.....

he will need a working machine to do any of the above....

tommy

---

### Post by Scary Rob on 2018-11-17
> **NM5TF said:**
> @Scary Rob

good advice you gave +1

but I believe the OP said his laptop is "dead".....if so, how can he do what is suggested.....

he will need a working machine to do any of the above....

tommy

Thank you :)

I was hoping that by "dead" malikiag just meant "out of battery". If it's refusing to turn on at all now, he's got a whole 'nother problem ;)

---

### Post by lisati on 2018-11-17
> **malikiag said:**
> I think it has 15 GB of memory, but it was running low last time I was on. When I turn my laptop on, it show the purple screen, then the ubuntu logo with the 5 loading dots underneath. Then it just changes the the screen full of code.

Side note: According to a [Lenovo website]("https://www.linux-netbook.com/lenovo-thinkpad-x131e-chromebook/") I looked at, the 15Gb (or thereabouts) is more likely to refer to the size of the SSD (similar idea to a "hard drive" or "hard disk" in older machines). The 4-8Gb RAM ("working storage") mentioned by  NM5TF sounds about right.

---

### Post by malikiag on 2018-11-17
Ah. Unfourtunatly, I don't have acces to a computer, or the usb my dad used to put ubuntu on my laptop. Also, my laptop battery is dead not the whole thing. I am also unable to use an Ethernet cable because the router is under lock and key and I'm not alowed acces to it. I like the idea of switching to Kubuntu. If I have a usb with it downloaded on there, will I be able to replace Gnome, or will it still go to that boot screen?

---

### Post by Scary Rob on 2018-11-18
> If I have a usb with it downloaded on there, will I be able to replace Gnome, or will it still go to that boot screen?

Not knowing for certain what's causing the problem, I'd recommend a clean install i.e. just installing Kubuntu from scratch.

---

### Post by NM5TF on 2018-11-18
> **malikiag said:**
> Ah. Unfourtunatly, I don't have acces to a computer, or the usb my dad used to put ubuntu on my laptop. Also, my laptop battery is dead not the whole thing. I am also unable to use an Ethernet cable because the router is under lock and key and I'm not alowed acces to it. I like the idea of switching to Kubuntu. If I have a usb with it downloaded on there, will I be able to replace Gnome, or will it still go to that boot screen?

if it is just the battery dead, do you have the AC power adapter to power up plugged into
wall socket ???

if so, try installing Kubuntu via your USB stick....

tommy

---

### Post by malikiag on 2018-11-18
I've had it sit connected to power, but because I'm on a homestead, we use a generator to get power and because of how much gas is used we don't run it that often. Infrequent charges, it's no wonder it doesn't get a full charge.

---

### Post by angisky on 2018-11-18
I know I'm late but I read this whole thread. I'm also on a X131e but I got the one with an AMD processor that originally came with windows 8 (it's pretty obvious why I'm on Ubuntu now) the issue you seem to be having is because of low disk space as someone vaguely mentioned before. You're gonna have to source a bigger hard drive or a lighter OS. If you use Arch you can get the install size to be pretty dang small but that's an advanced OS. You can try doing some research to get the smallest Ubuntu or Debian based OS that way it's similar to what you already have. I haven't fiddled with Debian but I've heard once you get to the meat of it it can be just as powerful as Arch. Working with such a small amount of hard drive space is difficult to say the least.

---

### Post by angisky on 2018-11-18
> **malikiag said:**
> I don't even get to login. I tried ctrl + alt + F1 on the screen but it does nothing. Help please! It seems the last bit of code is pretty consistent.
[   Ok   ] Reached target Sound Card.' for details.d...details. reporting is enabled. was shut down....

What does this mean?

You can use ctrl+alt+[Any f key 1-12] try the other f keys because they each work almost as separate work spaces and sometimes GDM will grab the f1 space.

---

### Post by NM5TF on 2018-11-18
> **malikiag said:**
> I've had it sit connected to power, but because I'm on a homestead, we [COLOR="#FF0000"]use a generator to get power[/COLOR] and because of how much gas is used we don't run it that often. Infrequent charges, it's no wonder it doesn't get a full charge.

wow does that bring back some memories....I lived off the grid for 5 years in the 1980s & used generator power....I know the pain....

you may want to take a look at Lubuntu which I believe is the lightest of the *buntu distros if you really only have 15 GB of disk/SSD

I really would NOT recommend trying Arch linux until you have much more experience....it can be very daunting for the beginner as
you start with just a basic terminal only system....up to you to build it into what you personally desire and add apps as you go....

tommy

---

### Post by Scary Rob on 2018-11-19
In light of this, I retract my recommendation of Kubuntu, because that recommends 25GB of hard disk space, too. Xubuntu and Lubuntu are your best bets.

---

### Post by malikiag on 2018-11-19
I asked my dad about using kubuntu and he agreed, saying it will use less resources and be more helpful for my laptop.

---

### Post by malikiag on 2018-11-19
Is there a way for me to fix it within 24 hours? I need it by Tommorow!

---

### Post by malikiag on 2018-11-19
Nevermind. My dad has something figured out. Thx though,we'll download Lubuntu.

---

