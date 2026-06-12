---
title: "Portable OS?"
date: 2008-08-07
forum: Other OS Talk
---

### Post by jasex on 2008-08-07
Ok, so my grandfather challenged me... kinda. 

I mentioned linux on the phone while talking to my grandfather, and
he randomly retorts: 'Lye-Nucks, is for tech savvy people who know what they're doing'

I intend to prove him wrong...

however, I'd like to do so with a usb 512 megabyte thumbdrive, with the ability to save the workstate, like if I was shut down the computer, and then turn it back on and have all my documents i just made and stuff still...

I've seen one like this before and can't remember what it was called, but it seemed pretty gritty, I want something more relatively useful, and preferrably, if there's one based on Ubuntu ( which came up in our discussion about Dell), I'd like to use that... so come on, anyone willing to prove my old-old-man wrong with me?

---

### Post by dje on 2008-08-07
definitely [damn small linux]("http://www.damnsmalllinux.org/"), i've got it on my pen drive in qemu (lightweight virtualisation software) or you can run off the pen drive as a "real" os

dje

---

### Post by damis648 on 2008-08-07
Ubuntu can be installed on a flash drive with persistence. Start the Ubuntu installation and install to the flash drive, "Use Entire Disk". When it comes to the final step before the install, click "Advanced" and set the bootloader, GRUB, to install to the flash drive. (the entire drive, not the partition.) That should do it. Just make sure his computer can boot from USB. ;-)

EDIT: Sorry, not for 512MB, you would need a couple GB. For 512MB, try Puppy Linux. When you boot the LiveCD, it has the option to install to a Flash Drive. Hope that helps!

---

### Post by jasex on 2008-08-07
Damn small linux, has save capabilities? I really like that :> I used to use it for my old *** dell laptop... but from CD... I'll also look into Puppy Linux and see which damns/licks me more (pun lol)

---

### Post by jasex on 2008-08-07
uh... now to install this... use dd? I am not sure =D haven't made a thumb-drive in forever, and I would use my 4gig... but that stupid U3 crap that I can't remove doesn't let me boot it.

uh... sorry for double post

---

### Post by dje on 2008-08-07
> **jasex said:**
> uh... now to install this... use dd? I am not sure =D haven't made a thumb-drive in forever, and I would use my 4gig... but that stupid U3 crap that I can't remove doesn't let me boot it.

uh... sorry for double post

download [this]("http://gd.tuwien.ac.at/opsys/linux/damnsmall/current/dsl-4.4.3-embedded.zip") and extract to your pen drive. then run the .bat file

to make a "hard drive" to save things on have a look [here]("http://www.damnsmalllinux.org/wiki/index.php/Qemu")

dje

---

### Post by zmjjmz on 2008-08-08
There is a project called QEMU Puppy, which will run Puppy off of Windows QEMU, allowing for saved states and such.

But, it will just keep him believing that Linux is for tech savvy people.

---

### Post by jasex on 2008-08-08
is there anyway besides the live cd, to put puppy on thumb drive? btw I found a 2gig memory stick... will installing ubuntu on that work just fine?

I kind of want it so that it will be just like installing to an external hd... ? am I asking too much?

---

### Post by jasex on 2008-08-08
oh and would 'sudo apt-get install ubiquity' allow me to install from inside an installed ubuntu

---

### Post by swisscow on 2008-08-08
> **jasex said:**
> is there anyway besides the live cd, to put puppy on thumb drive? btw I found a 2gig memory stick... will installing ubuntu on that work just fine?

I kind of want it so that it will be just like installing to an external hd... ? am I asking too much?

I think you can do it through virtualbox

---

### Post by zmjjmz on 2008-08-08
Ok, what do you mean by saved state and such?
Like a persistent partition where the settings and such are always saved?
Because there's a tutorial on pendrivelinux.com for getting Ubuntu on a flash drive, and a 2GB should provide enough space.

---

### Post by JT9161 on 2008-08-08
DSL embedded: [ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/current/](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/current/)  (8th Item down) 

QEMU Puppy: [http://www.erikveen.dds.nl/qemupuppy/](http://www.erikveen.dds.nl/qemupuppy/)

---

### Post by eeezzzeee on 2008-08-08
Check out Slax. I installed it on a pen drive a while back. It might work for what you are looking for.

It's USB version is under 200 megs, it's slackware based, modular and a pretty complete distro.

---

### Post by Jordanwb on 2008-08-10
> **jasex said:**
> uh... now to install this... use dd? I am not sure =D haven't made a thumb-drive in forever, and I would use my 4gig... but that stupid U3 crap that I can't remove doesn't let me boot it.

uh... sorry for double post

You do know that you can uninstall it right? Really all U3 does it partition your flash drive to have a CD-ROM partition and a fat32 partition.

---

### Post by kk0sse54 on 2008-08-10
I have a 256 MB pen drive that I installed Austrami on and it works like a charm. Used to run DSL but their newest version to me felt like a step backwards.

---

### Post by zmjjmz on 2008-08-11
> **C!oud said:**
> I have a 256 MB pen drive that I installed Austrami on and it works like a charm. Used to run DSL but their newest version to me felt like a step backwards.

Yeah, I don't like the new Firefox version. They could of stripped down an inherently lighter browser, but nyuuu

---

### Post by jasex on 2008-08-15
> **Jordanwb said:**
> You do know that you can uninstall it right? Really all U3 does it partition your flash drive to have a CD-ROM partition and a fat32 partition.

I know, but it doesn't work, I've even tried to try formatting the entire thing.

---

### Post by smartboyathome on 2008-08-15
No, get the uninstaller from their site (google U3 uninstaller, it will find it for you). You need windows to uninstall it, but you can't simply format it. You have to use the tool to uninstall it, as the "space" which the CD partition uses won't be given back. :(

---

