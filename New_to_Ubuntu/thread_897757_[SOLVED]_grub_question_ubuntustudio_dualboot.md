---
title: "[SOLVED] grub question: ubuntu/studio dualboot"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by smokingwreckage on 2008-08-22
I just assembled a new box for the purpose of some audio production. Before shelling out hundreds of dollars on DAW software for windows i decided to see what the open source community had to offer, so i skipped windows and installed hardy. 

As a first time linux user i was pretty amazed (and distracted) by the amount of customization and all of the free software packages. A few days into my "ubuntu awakening" i read about ubuntu studio. 

My rig has a 160 gig drive that my install is on, and 2 80 gig drives that aren't doing anything right now. i'd like to install ubuntu studio on one of the spare 80 gig hdd's and keep my initial install where its at. 

i'd appreciate any help, my experience with linux very minimal and i dont want to botch my original installation.

---

### Post by Diabolis on 2008-08-22
You can install any number of operating systems in a computer. At boot up a menu will show up from where you can pick which operating system you want to use. The bootloader, software like grub, lilo, super grub, is responsible for managing that menu.

The only way that you can mess up your original installation is by overwriting it with the new install.

---

### Post by Elfy on 2008-08-22
Shouldn't be a problem to just install it there, grub will get installed again by studio, but it should have both on it.

You won't need another swap - so it might be best to use manual partition and just have the one / .

---

### Post by Too Late on 2008-08-22
> **forestpixie said:**
> Shouldn't be a problem to just install it there, grub will get installed again by studio, but it should have both on it.
But what will happen, when the initial Ubuntu upgrades its kernel, and runs the update-grub script? It updates the menu.lst, but not the one which is read by grub. Therefore, I would install grub in the MBR of that 80 G "spare disc" (where the Studio will be installed), or in the beginning of the root partition of that installation. Then I'd chainload that from the existing grub. The grub installation location can be specified at the end of Ubuntu installation process (by pressing "Advanced..." button).

---

### Post by snowpine on 2008-08-22
There is no need to install Studio on a separate partition. You can just add the audio applications and real-time kernel to your existing Ubuntu with 'sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt'.

I understand if you want to keep it completely separate--and that is valid--just letting you know you have an easier alternative. :)

---

### Post by WRDN on 2008-08-22
Rather than dual booting Ubuntu and Ubuntu Studio, you could just install the ubuntustudio-desktop package in Ubuntu. Search for "ubuntustudio" in Synaptic as there are some other packages you may be interested in.

---

### Post by Diabolis on 2008-08-22
Updates take care of grub too, you don't have to worry about that. Your menu will be always up to date.

---

### Post by Elfy on 2008-08-22
You are right - only 1 set will be updated, those between the automagic lines - if grub is set up by studio it will update it's entries but the hardy outside the lines won't be.

The update grub uises the groot line to see where it is - so if hardy is on one drive and studio on another they would need different groots.

I have no idea whether it's possible to get both updated - check out hermanzone grub pages - there are a lot :) [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I have the same scenario at the moment - running hardy and intrepid - as I didn't want intrepid running grub - I just copy the lines as they get updated onto my hardy menu.lst - takes a couple of minutes.

That is my understanding of how it works at least.

---

### Post by Too Late on 2008-08-22
What's wrong with chainloading? Notice that grub does not have to be installed in MBR. It can be installed on any partition, from where it can be chainloaded by the "real" grub. That grub stored in a single partition will be updated perfectly by its "host OS". If you set the timeout to zero, you won't even notice the chainloading, but you will always have access to up-to-date system.

---

### Post by Elfy on 2008-08-22
Nothing at all - I've never done it so wouldn't be able to talk about it.

---

### Post by smokingwreckage on 2008-08-24
For the sake of simplicity i think i will just install the ubuntustudio desktop package. before i do though, are there any drawbacks/side effects of doing this?

---

### Post by Elfy on 2008-08-25
The only drawback I can see is that you will get both sets of apps in your menus and maybe a few extra libs.

---

### Post by smokingwreckage on 2008-08-25
installed the studio package and all is well. had to run envy again to get my video card recognized after switching to the real-time kernel, but that was the extent of my trouble. thanks for all of your help gents!

---

