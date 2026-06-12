---
title: "Error while doing full install of 11.04"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by Mila on 2012-04-14
This morning I created an 11.04 live usb using unetbootin and tried to install it on a laptop I have. It got most of the way through and then gave me this error message:

An error occurred while installing packages:
E:Sub-process /usr/bin/dpkg returned an error code (1)
The following packages are in a broken state:

Then it printed some blank lines on the popup, so I really don't know which, if any, packages were broken. It also gave a message about checking the syslog and said it would attempt to continue the install. I clicked "ok."

Then I got another popup saying that the installer crashed and to file a bug report and include the syslog and the /var/log/partman file and to include the following details (blank lines). 

Since I fished this laptop out of the dumpster, I was thinking this is probably a hardware issue instead of a software issue, so I decided to *not* file a bug report and instead post here. I booted up the live usb so I could try to find the files in question. They don't exist. There are plenty of files and folders in the /var/log directory, just not partman or syslog. 

The laptop in question is a Toshiba Satellite A305-S6858.

Any suggestions? If at all possible, I'd like to figure out if (a) this *is* a hardware issue (and if it is, what I need to replace) and/or (b) if I can fix this install and end up with a usable computer.

Thanks, Mila

---

### Post by mörgæs on 2012-04-14
Why did you install 11.04 and not 11.10?

---

### Post by yeats on 2012-04-14
> Since I fished this laptop out of the dumpster,...

So have you done any sort of evaluation of the hardware, aside from attempting this install?  

> The laptop in question is a Toshiba Satellite A305-S6858.

Can you provide the specs? (Memory, processor model, hard disk?)

Broken package errors can have different causes.  If you really want to chase this down, you'll probably want to open a terminal and do

```
sudo apt-get update
sudo apt-get -f install
```

Then share what the errors are from there.

But I would take a few steps back and try to determine why the previous owner would've tossed it ;-).

---

### Post by Mila on 2012-04-14
> **mörgæs said:**
> Why did you install 11.04 and not 11.10?
I picked 11.04 because from what I understand the *.04 releases are the ones that are supported in the long term. Or was I incorrect in that assumption? In my experience, I've found the *.04 releases to be much more stable and tend to pick those when doing an install unless I have reason to go to the *.10. 

> **yeats said:**
> So have you done any sort of evaluation of the hardware, aside from attempting this install? 
Prior to installing this, I booted it up. It had Vista installed natively but the installation was corrupted and it wouldn't boot all the way. (I assume this is why the previous owner chucked it. Or it could be that they graduated and were getting a newer model, since I fished it out of the dumpster behind the dorms.) I used the live cd and verified that all the peripherals work, including the wireless network, usb, hdmi and firewire ports, cd/dvd drive, and so on.

After booting from the live cd after the failed install, I called fsck on all the new partitions. (The specific command I used was sudo fsck -t ext4 /dev/sda#). It gave me an error on the swap partition:

fsck from util-linux-ng 2.17.2
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5

All the other partitions checked out normally. I don't know if this is a normal response for the swap partition.

> **yeats said:**
> Can you provide the specs? (Memory, processor model, hard disk?)

This thing is running an Intel Core 2 Duo T5750. The CPU is 64bit but it's running 32bit Ubuntu. 3 GB of RAM. The hard drive is a Toshiba MK3252GSX, 320 GB. 

I will reply back shortly after running the commands above with the results.

Mila

---

### Post by yeats on 2012-04-14
> I picked 11.04 because from what I understand the *.04 releases are the ones that are supported in the long term. Or was I incorrect in that assumption? In my experience, I've found the *.04 releases to be much more stable and tend to pick those when doing an install unless I have reason to go to the *.10.


LTS releases are every 2 years (8.04, 10.04, 12.04).  11.04 is a standard release, but it's supported through October, so you're fine for the moment.  You will be prompted to upgrade to 11.10 as soon as the installation works, so you can decide then if that's what you'd like to do.

---

### Post by Mila on 2012-04-14
> **yeats said:**
> LTS releases are every 2 years (8.04, 10.04, 12.04).  11.04 is a standard release, but it's supported through October, so you're fine for the moment.  You will be prompted to upgrade to 11.10 as soon as the installation works, so you can decide then if that's what you'd like to do.

I guess I *was* mistaken then. My apologies. I guess I'll downgrade to 10.04 since I find that funky access bar in 11.* to be ridiculous and annoying.

All that aside, I attempted to boot the Ubuntu install directly and it wouldn't boot. I don't even think we hit grub. When the computer turns on, it shows the screen that prompts me to enter the BIOS setup, and then goes to a black screen. Not even a command prompt or anything. I'm going to go out on a limb and assume the installation failed miserably and this isn't just a package issue.

Am I right in assuming that if I run the apt-get commands from two posts up while running the live cd, this will not diagnose issues the issues correctly?

---

### Post by mörgæs on 2012-04-14
I would stop focusing on the operative system for now. Better to try running [www.killdisk.com](www.killdisk.com) or [www.dban.org](www.dban.org) to erase everything on the hard drive as a first step. 

If you have physical errors on the hard drive you will get a warning here. 

When such a (fairly) new portable is dumped you should expect some hardware errors.

If everything works I would install 11.10, not upgrade from 11.04. If you don't like Ubuntu 11.10 then Xubuntu is a good option.

---

