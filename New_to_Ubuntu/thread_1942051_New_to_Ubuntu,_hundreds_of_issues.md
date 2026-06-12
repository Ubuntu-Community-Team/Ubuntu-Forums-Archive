---
title: "New to Ubuntu, hundreds of issues"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by beefybish on 2012-03-16
Hey there. I heard good stuff about Ubuntu and finally decided to try it, so I've installed it on my desktop computer (Fresh copy, completely wiped Windows 7.) But I've had a couple of issues;

- The system information only recognises 3.2 gb of RAM when I actually have 6gb installed. (I'm using 32 bit Ubuntu), but I was told that it's only windows that needs to have 64 bit to recognise more RAM. Will I need 64-bit Ubuntu to recognise all my RAM?

-My system seems to be going quite slow, even though I have 6GB of RAM (or 3.2 according to system info ;)), A 60GB Solid state hard drive, and an AMD fx 6100 6 core processor.

- Can't connect to my wired connection. I have a wireless dongle and If i use that it works perfectly, but if I try and use the wired connection the little connection logo spins for ages then nothing happens. I'm thinking i may need to install my chip set drivers; which leads me on to my next question.

- On windows, there is the auto play option for discs. However, I have inserted my motherboard chip set driver disc, and nothing happens. How do I install the drivers? I have selected the files inside called setup etc but nothing happens and i can't find a way to do anything with them.

Please help me guys! Ubuntu seems really good it's just so frustrating! I'm used to everything being setup and ready to go for me :(

---

### Post by jerome1232 on 2012-03-16
> **beefybish said:**
> 
- The system information only recognises 3.2 gb of RAM when I actually have 6gb installed. (I'm using 32 bit Ubuntu), but I was told that it's only windows that needs to have 64 bit to recognise more RAM. Will I need 64-bit Ubuntu to recognise all my RAM?

Yes, and no, you can install a pae kernel, which will allow greater than 4 GB's of ram on a 32 bit system, but doesn't play well with wireless drivers or proprietary graphics drivers (nvidia). Your better off just going 64 bit, there is almost no reason to limit yourself to 32 bit.

> **beefybish said:**
> 
-My system seems to be going quite slow, even though I have 6GB of RAM (or 3.2 according to system info ;)), A 60GB Solid state hard drive, and an AMD fx 6100 6 core processor.

What graphics card do you have? Have you check additional drivers to see if there is a driver needed for your card? (Gear Icon top right, System Settings, Additional Drivers), this is mostly likely a video issue.


> **beefybish said:**
> 
- Can't connect to my wired connection. I have a wireless dongle and If i use that it works perfectly, but if I try and use the wired connection the little connection logo spins for ages then nothing happens. I'm thinking i may need to install my chip set drivers; which leads me on to my next question.

Now that's a reverse! Generally it's the other way around, what is your ethernet controller? Post the output of these commands, press ctrl+alt+t to open a terminal, ctrl+shift+c to copy out of a terminal, make sure to wrap the output in code tags when you post it, go advanced, highlight the output, press the # button on toolbar.

```
lspci
sudo lshw -C network
```


> **beefybish said:**
> 
- On windows, there is the auto play option for discs. However, I have inserted my motherboard chip set driver disc, and nothing happens. How do I install the drivers? I have selected the files inside called setup etc but nothing happens and i can't find a way to do anything with them.

Those files are windows executables, not Linux executables, linux executables will generally be named *.bin. Most drivers are included with the linux kernel by default, some things you might have to fiddle with (like your ethernet controller)

---

### Post by Rodney9 on 2012-03-16
Help Guide to Ubuntu Oneiric version 11.10

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

Linux is Not Windows

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)


Rodney
_________

---

### Post by QIII on 2012-03-16
PAE, by the way, is Physical Address Extension and even Windows 32 bit needs it enabled

If you have a 64 bit machine, just use a 64 bit OS.  Before you go hacking to get your wired connection and such working (and that is definitely ODD!) I'd install 64 bit and work from there..

---

### Post by d4m1r on 2012-03-16
64 bit is NOT a requirement if you don't want to reinstall. I have 8GB of RAM and I use the 32 bit version. My next upgrade will be to a 64 bit version but even then I see very little point because my usage on Ubuntu barely even gets above 1GB....the OS is too efficient and my rig is too quick for 64 bit to make a difference in my case (and same for 6GB I am thinking).

---

### Post by grahammechanical on 2012-03-16
@d4m1r

Could you please explain how your 32bit Ubuntu is able to access this 8GB of RAM? The OP would like to know this I am sure?

Could please explain how he can do the same? It seems that he is using a non-pae kernel. Do you know if it is possible to bring in a pae kernel without re-installing? Is it something a very new user could do without getting into a greater mess?

Regards.

---

### Post by bodhi.zazen on 2012-03-16
> **grahammechanical said:**
> @d4m1r

Could you please explain how your 32bit Ubuntu is able to access this 8GB of RAM? The OP would like to know this I am sure?

Could please explain how he can do the same? It seems that he is using a non-pae kernel. Do you know if it is possible to bring in a pae kernel without re-installing? Is it something a very new user could do without getting into a greater mess?

Regards.

You simply install and boot to the pae kernel

```
sudo apt-get install linux-generic-pae
```

Then reboot.

The installer *should* have installed the pae kernel by default though. You can check if your cpu supports pae with

```
grep --color=always -i PAE /proc/cpuinfo
```

See also [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

In general, with a fresh install, I would also tend to advise re-installing 64 bit ubuntu rather then working through all the other problems on 32 bit.

---

### Post by OGpmpdog on 2012-03-16
> **grahammechanical said:**
> @d4m1r

Could you please explain how your 32bit Ubuntu is able to access this 8GB of RAM? The OP would like to know this I am sure?

Could please explain how he can do the same? It seems that he is using a non-pae kernel. Do you know if it is possible to bring in a pae kernel without re-installing? Is it something a very new user could do without getting into a greater mess?

Regards.

No need to reinstall.

OP could probably run synaptic, and type "pae' in the search box...and install latest PAE kernel...all subsequent system kernel updates will automatically be to PAE.

OP, FYI, if you havent installed synaptic, 1.open your terminal:

type:

*sudo apt-get install synaptic*

(enter password, and agree :)

I had this same situation on a recent build...8 GB RAM, 32-bit, and fresh install recognized only 3.2 GB....it took me a little more time to figure this out than for you to read this:guitar:

Welcome to Ubuntu, OP.

---

### Post by bogan on 2012-03-17
Hi!, **BeefyBish**,

The code that** Jerome** asked you to Post the results of, has a slight error in it.

It should read: ```

lspci
 sudo [COLOR=Red]lshw [/COLOR]-C network
```Chao!, **bogan**.

---

