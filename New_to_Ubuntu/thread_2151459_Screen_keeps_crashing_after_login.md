---
title: "Screen keeps crashing after login"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by Jeroenhu on 2013-06-04
So,

I've installed Xubuntu 13.04 on my old Acer laptop today. Everything went fine during the installation. (Installed from USB stick).
When I did my first boot. I got to the blue login screen, entered my password for decryption.

And then... THIS

[SIZE=4][IMG]http://ubuntuone.com/27bpMRAwQJjkQCDun4sSTl[/IMG][/SIZE]

After waiting for some minutes, the laptop turns off.

I'd appreciate it if someone could put me in the right direction to solve this. In other words, what could possibly be the cause?

Cheers

---

### Post by ohnonot on 2013-06-04
and it only happens *after* you login? that might mean you have the wrong graphic driver.
and what blue screen? can you take a screenshot of that, too?

---

### Post by Jeroenhu on 2013-06-04
I can't take that screenshot. The screen crashes before I can do anything. I get a blue login screen with Xubuntu 13.04. Think that's the default. I also think it's a graphic driver, but is there a way to fix it from the live session?

---

### Post by matt_symes on 2013-06-04
Hi

> my old Acer laptop today

What model acer ? 

What are the hardware specs (in as much detail as possible) ?

Kind regards

---

### Post by Jeroenhu on 2013-06-04
Let's see:

AMD64 Turion X2
4GB ram
ATI Radeon HD 3650

That's all I can gather with the laptop being in this state. It's been quite a while since I've used it, so I must admit I can't remember what's in it, except for the parts listed here. 

What happens:
I boot, I login.
Crypt setup: sda5-crypt set up successfully.
After this, it checks for disk errors and then the crash happens.

Kind regards

---

### Post by ohnonot on 2013-06-05
i'm sorry, wrong lingo. with "screenshot" i meant the same kind of picture you took in the first post.
i asked because i was unsure what this blue login screen is.
i now gather that you have some kind of bios login *before* the bootloader starts.

anyhow, i did a web search for you! search term: "ubuntu ATI Radeon HD 3650".
this bug report seems relevant:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040)
and to me it sounds like you should try the LTS version of xubuntu, that would be 12.04.
since you're at the very start of the installation, have you checked distrowatch.com? there's a lot of choice in the wonderful world of FOSS!

---

### Post by newb85 on 2013-06-05
> **ohnonot said:**
> i asked because i was unsure what this blue login screen is.
i now gather that you have some kind of bios login *before* the bootloader starts.

My guess is that blue login screen is Xubuntu's normal blue login screen.  (I believe it's the GDM login with a blue backdrop.)

The workaround listed in that bug report may or may not work.

When the GRUB screen comes up, select Recovery Mode and then drop to a root prompt.  Then
```
sudo add-apt-repository ppa:makson96/fglrx && sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install fglrx-legacy
exit
```

And boot normally.

Note: if you prefer to be able to copy and paste to and from the forums while doing this, then you can use this approach:

Boot from Xubuntu Live media.  (I assume you still have it.)  Use the "Try Ubuntu" option.
Open a terminal and run
```
sudo chroot /media/xubuntu/*
add-apt-repository ppa:makson96/fglrx && apt-get update && apt-get -y upgrade && apt-get -y install fglrx-legacy
exit
```

(chroot makes you root.  As long as your prompt is "#", caution is advised.)

Also note, that workaround updates all your packages.  If you didn't install updates while installing Xubuntu, this will probably take a while.

---

### Post by Mark Phelps on 2013-06-05
You have one of the Radeon chipsets that AMD dropped support for last summer.  Those chipsets fglrx drivers won't work with any Ubuntu newer than 12.04.1.  While there are "kludges" that can make them work, they run the risk of seriously hosing up your setup and causing more problems down the road.

You didn't mention installing the fglrx drivers, so if you didn't, then don't.  IF you did, you will need to remove them.

---

