---
title: "Partitioning"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by Jaeman on 2013-01-26
I have an HP, a nice laptop. It went through some water damage about a year ago. I booted it up today and the windows operating system was erased. So I went on my other laptop, made an installation cd, and now I have ubuntu running on my water damaged laptop, but I need help petitioning for space for the installation, any ideas? thanks everyone who reads this

---

### Post by darkod on 2013-01-26
So what is the question exactly?

If you want to run only ubuntu on it, you can use the Erase and use whole disk option, it will set the partitions automatically.

If you want to set them up manually select Something Else and create your own partitions with the sizes you want. That gives you more control of the layout.

---

### Post by Jaeman on 2013-01-26
Awesome, yea that's what I would like to do, how do i do that?

---

### Post by Jaeman on 2013-01-26
Sorry still not specific. How do I go about doing either of those? preferably the first of the two solutions listed

---

### Post by Jaeman on 2013-01-26
The problem starts when I run the installation. Three things are required. 1. internet, 2. a power source, and what I am missing is 3. 4.4gb available drive space. How do I increase my drive space? or is it that the water damage ruined the drive? or is petition needed?

---

### Post by darkod on 2013-01-26
Well, boot with the ubuntu cd and it will show a main menu with Try Ubuntu and Install Ubuntu options.

It's best to Try is first to see if it will load the live session working from the cd correctly. But it's not necessary. You can start the Install right away if you want to.

In the live session you will also have Install icon on the desktop.

Once the install starts, after a few basic screens about language etc, it will get to a menu with options like:
Install along side windows (if it can still detect it on the hdd)
Erase and use whole disk
Something Else

Just select the whole disk option if that's what you want, and that's it. There will be further screens for entering your full name, selecting user name, password, computer name, etc. Just enter the data you want.

And that should be it.

---

### Post by darkod on 2013-01-26
> **Jaeman said:**
> The problem starts when I run the installation. Three things are required. 1. internet, 2. a power source, and what I am missing is 3. 4.4gb available drive space. How do I increase my drive space? or is it that the water damage ruined the drive? or is petition needed?

You should have said that earlier. :)

Select the Try option first, when it loads the live session open terminal (you can click the ubuntu logo on the left side menu to open the so called Dashboard, and type terminal in the search line. It will find the program for you.

In the terminal, execute:
sudo parted -l (that's small L)

That will show if the disk is detected and what partitions you have on it. Post the output here.

The hdd might be dead, or you might have all 4 primary partitions used.

---

### Post by lisati on 2013-01-26
> **Jaeman said:**
> The problem starts when I run the installation. Three things are required. 1. internet, 2. a power source, and what I am missing is 3. 4.4gb available drive space. How do I increase my drive space? or is it that the water damage ruined the drive? or is petition needed?

The best procedure for increasing available space can depend on which OS (and sometimes which version of your OS) you already have, how the exisiting partitions are organized, and what, if anything you want to keep from whatever is already on your disk.

Some people recommend using the tools that come with Windows to resize existing partitions, because Windows sometimes throws a hissy fit if you use another method to tinker with partition size.

I notice in the first post in this thread that Windows has been erased. Yhe installation disks I have used generally have an option to help you with the process.

---

### Post by Jaeman on 2013-01-26
> **darkod said:**
> You should have said that earlier. :)

Select the Try option first, when it loads the live session open terminal (you can click the ubuntu logo on the left side menu to open the so called Dashboard, and type terminal in the search line. It will find the program for you.

In the terminal, execute:
sudo parted -l (that's small L)

That will show if the disk is detected and what partitions you have on it. Post the output here.

The hdd might be dead, or you might have all 4 primary partitions used.




=The response was
warning: Unable to open /dev/sr0 read-write (Read-only file system).   dev/sr0 has been opened read-only.
Error:can't have a partition outside the disk!

---

### Post by darkod on 2013-01-26
> **Jaeman said:**
> =The response was
warning: Unable to open /dev/sr0 read-write (Read-only file system).   dev/sr0 has been opened read-only.
Error:can't have a partition outside the disk!

If it didn't report a device like /dev/sda that means it can't see the hdd.

Have you checked in bios whether it can see the hdd correctly?

---

### Post by Jaeman on 2013-01-26
> **lisati said:**
> The best procedure for increasing available space can depend on which OS (and sometimes which version of your OS) you already have, how the exisiting partitions are organized, and what, if anything you want to keep from whatever is already on your disk.

Some people recommend using the tools that come with Windows to resize existing partitions, because Windows sometimes throws a hissy fit if you use another method to tinker with partition size.

I notice in the first post in this thread that Windows has been erased. Yhe installation disks I have used generally have an option to help you with the process.

What disks have you used?

---

### Post by Jaeman on 2013-01-26
no, I haven't. To be honest I'm not sure what bios is. The only response i had similar to yours was  /dev/sr0

---

### Post by Jaeman on 2013-01-26
> **darkod said:**
> If it didn't report a device like /dev/sda that means it can't see the hdd.

Have you checked in bios whether it can see the hdd correctly?

I haven't, I'm not entirely sure what bios is either :/

---

### Post by darkod on 2013-01-26
> **Jaeman said:**
> no, I haven't. To be honest I'm not sure what bios is. The only response i had similar to yours was  /dev/sr0

That is the cd-rom, that response was normal. But there is no hdd reported.

If you don't have experience with these things you might ask a friend to help you look around in the computer/bios, and see if the disk is reported at all. My guess is that it's dead after the accident, but I might be wrong. The damage might be on the motherboard so even buying a new hdd might not help you. That's why it's best to test with a borrowed hdd from a friend or something.

---

### Post by Jaeman on 2013-01-26
thanks, i'll prolly repost the question in a better format to see if I get any other responses. you've been a huge help though, thanks!

---

### Post by Jaeman on 2013-01-26
I'm installing Ubuntu on my former laptop. It's a good HP laptop and use to have windows, then  it underwent some water damage and no longer has it. I can run the Try  version of Ubuntu, but in order to install it permanently I need three  things: Power source, internet, and 4.4gb of disc space. I can't seem to  get the disk space. Do I need to petition> if so how? Could it be it  doesn't recognize the hard drive> how do I change this? Could it be  the hard drive is shot? or anything else? Thoughts and ideas are greatly  appreciated :)

---

### Post by Jaeman on 2013-01-26
> **darkod said:**
> That is the cd-rom, that response was normal. But there is no hdd reported.

If you don't have experience with these things you might ask a friend to help you look around in the computer/bios, and see if the disk is reported at all. My guess is that it's dead after the accident, but I might be wrong. The damage might be on the motherboard so even buying a new hdd might not help you. That's why it's best to test with a borrowed hdd from a friend or something.

are hd's typically the same? Can I use the hard drive from this current laptop? although they are two different manufacturers..

---

### Post by oldfred on 2013-01-26
Threads merged.
Please do not start a new thread on the same issue.

---

