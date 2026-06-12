---
title: "Boots only through recovery mode"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by Jay Tee on 2013-02-25
Every time I want to use Ubuntu I can only boot through the Recovery Mode option and this is fine for a temporary fix but I want to learn how to fix the start up so that I wont have to do this anymore. If I don't go through the Recovery Mode then there is a purplish screen then it goes black and you hear the bongo login sound.

Here is how I start it up to get to the login screen where I can see it.
1. Power on Dual Boot (windows 7 or Ubuntu)
2. Select Ubuntu and hold shift while there is still writing on the screen
3. Grub screen come up and I select Ubuntu with linux 3.2.0-38 generic (Recovery Mode)
4. Select Resume - Resume Normal Boot
5. Accept that I will be leaving recovery mode
6. Log in screen pops up.


What could be causing this and what will I have to do to fix it?

---

### Post by rcayea on 2013-02-25
Sounds like a video card driver problem. Do you know what video card you have?

I don't know off the top of my head what command line you could run, but I do know that the program called hardinfo will tell you what you need to know, once installed.

---

### Post by Bashing-om on 2013-02-25
Jay Tee; Hi Welcome to the forum.

Seems a graphics issue. From the recovery login, have you tried to install the recommended driver from the "Additional Drivers" utility (and do you have 3rd party software sources enabled )?

[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by ACubed10 on 2013-02-25
yes this a graphics card problem.  boot into recovery mode and install the additional drivers in system settings for your graphics card.  Bingo!

---

### Post by thomas2013 on 2013-02-28
I had a similar problem after recently installing 12.10.  (My computer is a Toshiba Satellite L875D with Radeon HD Graphics (HD 7520 G).

Here is a description of my problem:  After logging off, my first attempt to log back in would result in a puple screen followed by a black screen then nothing ...
Then I would turn off the computer using the power button and then turn it back on using the power button.  I would then be presented with a grub menu and have to choose recovery mode for a successful login.

bashing-om's suggestion above is what clued me into the solution.  I'm only filling in the details as I implemented them in case they may also help you.
Also as bashing-om you need to enable 3rd party sources when installing 12.10 because these drivers are proprietary (so you'll never be able to modify them if that is of interest) 

step 1.  Open System Tools
step 2.  Open System Settings
step 3.  Open Software Sources -- go to the additional drivers tab and select the radio button for 'Using video driver for the AMD graphics accelerator from fglrx-updates (propriety)

A couple of things -- I'm not sure if Ubuntu will detect your particular graphics card and helpfully display it as a choice under the additional drivers tab as it did for me.  If my details don't work for you I'm still pretty sure the other guys in this thread nailed the root problem so you're almost there.
good luck
TM

---

### Post by Princess Bernice on 2013-03-01
> **rcayea said:**
> Sounds like a video card driver problem. Do you know what video card you have?

I don't know off the top of my head what command line you could run, but I do know that the program called hardinfo will tell you what you need to know, once installed.

The command line command that I use for this is ```
lshw
```

Then, in the output, look for something similar to this: (basically, it will have the words "*-display
                description: VGA compatible controller")
```

           *-display
                description: VGA compatible controller
                product: RV770 [Radeon HD 4850]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:29 memory:e0000000-efffffff(prefetchable) memory:f7c20000-f7c2ffff ioport:e000(size=256) memory:f7c00000-f7c1ffff(prefetchable)

```

I hope that helps the original poster. ^_^

---

### Post by audiomick on 2013-03-01
> **Princess Bernice said:**
> The command line command that I use for this is ```
lshw
```


Yes, that is one. 
```
lspci
```
reads out everything in the PCI slots, so that can be useful sometimes too.

You should start lshw with sudo. I don't really know why, but it complains if you don't. You can restrict the output, which can be rather long, by using the -c option and naming a hardware class. For instance

```
sudo lshw -c network
```

will show you just the network adaptors, and

```
sudo lshw -c video
```

will show you just the graphics card(s).

---

