---
title: "[SOLVED] KPPP problems..."
date: 2008-05-11
forum: New to Ubuntu
---

### Post by ardvark71 on 2008-05-11
Hi...

I installed a copy of Kubuntu 6.06 on spare system I have and am having problems getting KPPP to do anything.:mad:

I have two modems installed on the system, one internal and the other, external. I very much doubt that the internal is supported out of the box, hence my installation of the external.

When I first ran KPPP, it complained about not having the /etc/resolv.conf file. I took care of that. However, it cannot open my external modem....it doesn't even try to look for it! When I tried Ubuntu 6.06, it worked fine.:confused:

Does anyone have any ideas on how to go about fixing this? This is an older system, so the 7th and 8th releases are out of the question. I'm surprised 6.06 works as well as it does.

Thanks!

---

### Post by spiderbatdad on 2008-05-11
Could you post the model of your external modem? The internal is likely a winmodem, if it is, it may never work reliably under linux. The external probaly requires a driver, also, many tend to have two modes of operation...data/modem.
Have you downloaded scanModem? You should run that and read the output file. There are two files in particular...the names of which I can't remember, but the instructions for scanModem will tell you.

---

### Post by ardvark71 on 2008-05-11
> **spiderbatdad said:**
> Could you post the model of your external modem? The internal is likely a winmodem, if it is, it may never work reliably under linux. The external probaly requires a driver, also, many tend to have two modes of operation...data/modem.
Have you downloaded scanModem? You should run that and read the output file. There are two files in particular...the names of which I can't remember, but the instructions for scanModem will tell you.

Hi...

The external is a U.S. Robotics 56k Sportster. The internal is indeed a winmodem, with a Conexant chipset.

I don't have a way of getting scanModem onto the Kubuntu system.

Thanks...

---

### Post by spiderbatdad on 2008-05-11
US Robotics is supossed to provide excellent linux support. I will see if I can find a driver for you. If it is small enough I will upload it. Can you copy to a usb stick and transfer the files?

---

### Post by ardvark71 on 2008-05-11
Hi...

I really don't believe this is a problem with my modem as it worked fine with Ubuntu. What I am seeing is that KPPP is not even trying or is able to look for the modem to begin with.

Thanks...

---

### Post by RJARRRPCGP on 2008-05-11
> **ardvark71 said:**
> Hi...

I installed a copy of Kubuntu 6.06 on spare system I have and am having problems getting KPPP to do anything.:mad:

Same type of thing, here, back in 2006 or 2007, when I used to have POTS. (56k) 

Before I gotten DSL, I decided to try KPPP after installing Kubuntu 6.06. 
But, hold it! I noticed that I was ALWAYS getting disconnected right after it was done dialing and handshaking. 

Also, the message about the PPP daemon dying unexpectedly and the KPPP log was complaining about some "secret password" nonsense, obviously authentication problems.

I finally gotten DSL on May 17 of last year.

---

### Post by spiderbatdad on 2008-05-11
The bug report below may be the key. You might be missing the directory needed by kppp. Read the whole report.

 [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/22119](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/22119)

---

### Post by ardvark71 on 2008-05-11
> **spiderbatdad said:**
> The bug report below may be the key. You might be missing the directory needed by kppp. Read the whole report.

 [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/22119](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/22119)

Hi...

Thank you but I didn't see the directory you mentioned. Also, this was for gnome. 

I don't have a working knowledge of commands for Kubuntu. I know a bit for Ubuntu, as I had it installed on my personal system for a few months.

Thanks...

---

### Post by spiderbatdad on 2008-05-11
using gksu nautilus is an easy way to graphically edit your system config files, like wvdial.conf, and to make directories. When you have any missing directories added. try running sudo wvdialconf again, the edit /etc/wvdial.conf to contain the correct info. You can launch wvdial from the terminal by running sudo wvdial. Also kppp uses wvdial.

---

### Post by RJARRRPCGP on 2008-05-11
> **spiderbatdad said:**
> US Robotics is supossed to provide excellent linux support. I will see if I can find a driver for you. If it is small enough I will upload it. Can you copy to a usb stick and transfer the files?

Yep, but I found a new problem before getting DSL, you will always get hanged up on with the 5686s.  Thus, impossible to access the internet.

Stay away from US Robotics 5686 modems!

---

### Post by spiderbatdad on 2008-05-11
> **RJARRRPCGP said:**
> Yep, but I found a new problem before getting DSL, you will always get hanged up on with the 5686s.  Thus, impossible to access the internet.

Stay away from US Robotics 5686 modems!

Unfortunately it seems to be the model not to have.

---

### Post by ardvark71 on 2008-05-11
Hi...

Ok, wvdial sees the modem just fine, however, how do I add my username, password and phone number to the config file? What is the exact command I need to put to do this?

Thanks...

---

### Post by spiderbatdad on 2008-05-11
```
gksu nautilus
```

navigate to /etc/wvdial.conf  way down near the bottom of the directory...add your info. save the file. That bug report did mention something about ATDT vs ADTW or something like that...

Any more problems, paste your wvdial.conf file here...leave out password/username.

---

### Post by ardvark71 on 2008-05-11
Hi...

"gksudo nautilus" is for gnome, not KDE. The "kdesu konqueror" command is what I've just used it to enter my information. I found the command after another search on the 'net for KDE and KPPP related information. 

I'll see how this works and let everyone know. Thanks for all your guy's help!

Thanks...

---

### Post by ardvark71 on 2008-05-11
Hi...

Well, I've managed quite by accident to completely screw up the wvdial config file as well as deleting it afterwords, thinking the wvdial program would create a new one.:mad: Before I deleted it, it kept complaining about not seeing my login information even though I had inserted it and saved it.

Now, I might as well reinstall the OS.

Honestly, I'm trying VERY hard to restrain my temper! ALL I'm trying to do is set up a SIMPLE internet connection and because of bugs and poorly written code, I am unable to accomplish that in what is marketed as a professional grade operating system.

Best Regards...

---

### Post by spiderbatdad on 2008-05-11
running sudo wvdialconf will write a new file. Make sure there are no semicolons at the beginnings of the lines with your username/password etc. These are seen as comments. Dial-up is difficult in linux. If you get it going, you can do almost anything :D
Maybe take a break...before you break something else!

---

### Post by spiderbatdad on 2008-05-11
also. make back up copies of files you are editing, to prevent loss: ```
sudo cp -p /etc/wvdial.conf /etc/wvdial.conf.bak
```
Then is you lose the file, rename the back up to the original.

---

### Post by ardvark71 on 2008-05-11
> **spiderbatdad said:**
> running sudo wvdialconf will write a new file. Make sure there are no semicolons at the beginnings of the lines with your username/password etc. These are seen as comments. Dial-up is difficult in linux. If you get it going, you can do almost anything :D
Maybe take a break...before you break something else!

OK, that would explain it :)

I've set up everything again and I'll give it another whirl. I'll post back with the results.

Thanks...

---

### Post by ardvark71 on 2008-05-11
Hi...

Ok, now my modem dials up but I keep getting a "NO CARRIER" message. What gives? All the information is correct.

:confused:

Thanks...

---

### Post by spiderbatdad on 2008-05-11
can you copy/paste your wvdial.conf here?

or try adding this:

ATZ
ATDT 555-1234

where 555-1234 is replaced with the number you dial.

check also that you're using /dev/ttyS0

[http://www.aboutdebian.com/modems.htm](http://www.aboutdebian.com/modems.htm)

---

### Post by ardvark71 on 2008-05-12
> **spiderbatdad said:**
> can you copy/paste your wvdial.conf here?

or try adding this:

ATZ
ATDT 555-1234

where 555-1234 is replaced with the number you dial.

check also that you're using /dev/ttyS0

[http://www.aboutdebian.com/modems.htm](http://www.aboutdebian.com/modems.htm)

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS1
ISDN = 0
(login information)

When I had wvdialupconf scan the modem, it came up with the ttyS1 address and configured it automatically.

Thanks...

---

### Post by ardvark71 on 2008-05-12
Hi all...

We're in business!:KS

With some help from spiderbatdad and from other resources on the 'net, I am now typing this from my Kubuntu system using wvdial. Had to use a couple hacks I found but we got it!

Thanks for your help!

Best Regards...

---

### Post by EmilyRose on 2008-05-13
Hey, I'd try downloading Gnome PPP - I know you've got Kubuntu, but I ran KPPP in gnome for months cause' it just worked better than gnome ppp with my usb modem, but am now back to gnome since it seems to be working better with the serial.

---

### Post by SlappyPappy on 2008-05-13
Interesting tip Emily, I'm going to have to try that. I use Gnome PPP and it has problems, mostly with realizing when it is connected.

Here goes nothing!......  :popcorn:

---

### Post by SlappyPappy on 2008-05-13
Hey Emily, I downloaded kppp and did some tweaking so it could find my modem. I added the Init 2 line of:

ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Then had to use the PAP setting so my ISP would authenticate my password.

Works great! Better than Gnome PPP. It also leaves a nice little window in the bar which you can disconnect with. Very cool!

Much thanks for the tip. Wish I'd found out about this sooner! Would have saved me a ton of time connecting to my ISP.  :)

---

### Post by ardvark71 on 2008-05-14
Hi all...

Well, no matter anymore. I uninstalled 6.06 because I successfuly screwed up the video driver after realizing 3D rendering no longer worked.:( I will probably try reinstalling it again later.

Thanks anyway!

---

