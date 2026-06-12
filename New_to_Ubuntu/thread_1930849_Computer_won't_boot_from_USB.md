---
title: "Computer won't boot from USB?"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by cheatos on 2012-02-24
Hi,

I want to install lubuntu, because ubuntu is too slow on my machine, but somehow my computer fails to boot from the liveUSB I have created and I don't want to "waste" a CD with lubuntu, as I already have a ubuntu one.

Is there a way I can make my computer boot from USB?
I have already looked in the BIOS setup and it has some weird entries there like HDD0-3 but I only have 1 HDD... Furthermore it has 3 types of USB-Peripherals to choose from which are USB-FDD, -HDD and -CDROM

I have already tried booting from any of these three and HDD1 instead of HDD0 but I keep booting ubuntu.

Thanks for any help!

---

### Post by roelforg on 2012-02-24
Three words:
PLOP Boot Disk

---

### Post by cheatos on 2012-02-24
Well, could yu please explain this a bit further?

---

### Post by oldfred on 2012-02-24
Plop is for old systems that do not let you boot from a USB at all from BIOS. It sounds like your system will let you boot from USB.

On my Desktop I had lots of USB boot options and none would work. I was able to boot USB on my laptop so I knew I had a working bootable USB. Then one day in BIOS I was choosing hard drive to boot and happened to have bootable USB plugged in and there it was under hard drives.

USB must be installed and workable as bootable device for BIOS to find it and different BIOS use different ways to boot.

My laptop will only boot from USB flash if I have one flash drive plugged in. If I also have another data drive then it does not work either.

Some experimentation sometimes is required. And some have reported that certain flash drives do not work. I have used Kingston and house brand Microcenter without issue.

---

### Post by roelforg on 2012-02-24
> **oldfred said:**
> Plop is for old systems that do not let you boot from a USB at all from BIOS. It sounds like your system will let you boot from USB.

On my Desktop I had lots of USB boot options and none would work. I was able to boot USB on my laptop so I knew I had a working bootable USB. Then one day in BIOS I was choosing hard drive to boot and happened to have bootable USB plugged in and there it was under hard drives.

USB must be installed and workable as bootable device for BIOS to find it and different BIOS use different ways to boot.

My laptop will only boot from USB flash if I have one flash drive plugged in. If I also have another data drive then it does not work either.

Some experimentation sometimes is required.
It still works on my 1 yr old laptop.

---

### Post by cheatos on 2012-02-24
Hmm, okay, I already had the same USB-Stick to install lubuntu to my laptop, but I reused the Startup Disk Creator, so maybe something went wrong during this process, I'll try it on my laptop now and if it boots there I'll try booting from HDD1-3.

Where can I get PLOP?
I have looked in the software center, but I couldn't find something.

---

### Post by ohadcn on 2012-02-24
you don't need to install everything from scrach
you can install lxde from ubuntu

sudo apt-get install lubuntu-desktop
logout
choose lxde
login

---

### Post by cheatos on 2012-02-24
But isn't the "slow" ubuntu system still running then?

---

### Post by cortman on 2012-02-24
> **cheatos said:**
> But isn't the "slow" ubuntu system still running then?

Not necessarily.  The only thing that's lighter about Lubuntu is the DE (LXDE) and some of the programs. Lubuntu-desktop will install the lightweight environment and the DE, but you'll still have a bunch of standard Gnome apps cluttering things up, so it uses less disk space and is a little cleaner to do a re-installation.

---

### Post by arochester on 2012-02-24
If you then want to remove Ubuntu look here: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by cheatos on 2012-02-24
Okay, so I've been on the PLOP home page but I don't know which is the right program for me. Can someone specify the right tool any further?

Thanks to cortman for your info, though!

---

### Post by roelforg on 2012-02-24
> **arochester said:**
> If you then want to remove Ubuntu look here: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)
Or, if you don't mind the added difficulty, use ubuntu server and go from there

---

### Post by roelforg on 2012-02-24
> **cheatos said:**
> Okay, so I've been on the PLOP home page but I don't know which is the right program for me. Can someone specify the right tool any further?

Thanks to cortman for your info, though!
[http://download.plop.at/files/bootmngr/plpbt-5.0.14.zip](http://download.plop.at/files/bootmngr/plpbt-5.0.14.zip)

---

### Post by cheatos on 2012-02-24
I've been following the link given by arochester now, I'll see if it is what I like ;)

Thanks for all your quick replies!

---

### Post by cheatos on 2012-02-24
So, I copied all the code on that website to my terminal and it all went well in installing and removing, but at some point my desktop was just gone. I think that this had to do with the removal of the ubuntu/gnome desktop and the lubuntu-desktop not being installed yet, but I then hit Ctrl+Alt+F2 and rebooted the computer.
I am currently running a lubuntu session and all the ubuntu stuff was removed, but I still wanted to be sure everything installed right.

---

