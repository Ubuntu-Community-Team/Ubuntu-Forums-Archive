---
title: "Ubuntu does not boot in Alienware M14xR1, just black screen"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by commonsensekim on 2013-02-23
I have a Alienware M14xR1 with 16 gigs of ram and nVidia GT555M with Optimus + Intel HD3000.

I *installed* my Ubuntu from a USB stick to another USB stick. Did not use the startup disk utility, and literally installed it on the USB stick after wiping it with diskpart in windows. I have a need for Installing Ubuntu on USB, not a LiveCD Startup disk or installation on the HDD.

When I try to boot it normally, it won't boot. No boot splash screens, no reports. No crashes, or something. Just a plain black screen. However, LiveCD USB would boot well.

I put into some efforts with trying some answers in the community, such as appending nomodeset to grub parameters, appending "console=tty1 acpi_backlight=vendor acpi_osi=Linux". I tried CTRL+ALT+F1-6 after some time letting my notebook to boot, and no signs.

I also tried booting into GRUB screen by holding SHIFT on boot, but it just shows "GRUB LOADING." and stops there.

Is there probably a solution for solving this problem and letting me into booting Ubuntu?

P.S. I have succeeded booting into Ubuntu in my USB using VMWare before, so I'm suspecting on my hardwares.

EDIT: I'm using Ubuntu 12.10.

---

### Post by commonsensekim on 2013-02-23
Bump.
Anybody willing to answer?

---

### Post by sanderj on 2013-02-23
You say:

> I installed my Ubuntu from a USB stick to another USB stick.

What does that mean? Were you able to boot Ubuntu  from the first USB stick?

---

### Post by QIII on 2013-02-23
> **commonsensekim said:**
> Bump.
Anybody willing to answer?

Welcome to the forums, commonsensekim!

Everyone's issues are very important to them and we certainly understand that.  Nobody is ignoring you.

This is a volunteer community of users from all around the world.  Not everyone here can answer every question immediately.  The person with just the right answer may live in Kolkata and be asleep at the time you post, or in Geneva having dinner with his/her family or Des Moines at work.  Sometimes it takes a bit for us to get to the forums and answer questions.

So please do not take it as a snub if you question is not answered immediately.

Give it 24 hours to make the rounds before bumping.  Sometimes an odd bump at 36 hours or something might catch other people in a different time zone at their computers.

Again, welcome to the forums.

Best wishes!

---

### Post by commonsensekim on 2013-02-23
> **sanderj said:**
> You say:


What does that mean? Were you able to boot Ubuntu  from the first USB stick?

Let my clarify.

I have a USB Stick (2GiB). Let me call this USB-A.
and I have another one (8GiB), which I'll call it USB-B.

I used unetbootin to copy the files of ubuntu-12.10-amd64 on USB-A.
Then I booted into USB-A, plugged it into USB 2.0 port.

I plugged USB-B into another USB port (3.0, though I think this does not care), and used the Installer from USB-A to install ubuntu to USB-B.

I created just one partition formated into Ext4 and mounted it to /, and installed ubuntu on it, having GRUB on USB-B(and it being sdb.)

Installation successfully completed, and I turned my PC off. I plugged USB-A from USB 2.0 port, and plugged USB-B instead. I booted it off.

My screen loaded GRUB, and it got into grub rescue, saying it could not find /boot/grub/i386-pc/normal.mod. There was x86_64-efi folder, but not i386-pc. I tried insmod'ing the x86_64-efi one, and GRUB rescue has hung.

I returned to USB-A, and booted the Installer. I reinstalled the GRUB bootloader to sdb(which is USB-B) with grub-install, and rebooted into USB-B.

This time, nothing had showed up, and it remained the same after waiting for some time, so I tried pressing CTRL+ALT+F1-6 to get the console, however the screen remained blank, plain black.

I rebooted to USB-B, and holded SHIFT. "GRUB loading." message showed up, and it hung. I waited for some time, and tried pressing some keys, but it stopped right there.

P.S
I do not know, and presume that it is not relavant to this situation, but I have UEFI boot enabled from the BIOS, and also EFI device first on boor devices. And Acpi version 3.0.

I tried to disable them(except Acpi), and tried to boot into USB-A, however it did not move from blank screen.

When I enable those features, and go into boot options prompt, I get a device named Acpi(~some numbers and blah~), and when I boot from that option, USB-A boots successfully without flaw.

btw, QIII, thanks for information. I was a little anxious at the moment.

---

### Post by QIII on 2013-02-23
No problem!

---

### Post by sanderj on 2013-02-23
Running live-Ubuntu from a USB stick works quite well, especially if you enough RAM.

However, *installing* Ubuntu to a USB stick or other flash memory as if it were a harddisk, works really bad in my experience.

My conclusion is that a live-Ubuntu on a USB stick has special (filesystem?) features to handle the slow USB stick (slow compared to a harddisk).

So, even if you could make your install-to-USB-stick work, it will be terribly slow.

So: why don't you use USB-stick "A"? That works, right?

---

### Post by commonsensekim on 2013-02-23
Yeah... I think the LiveCD uses RAM emulated disk.
However, I am trying to test drive ubuntu before wiping my PC (which is currently running on Windows 8) and selecting ubuntu as my main OS, and I can't use wubi or install ubuntu on another partition. I want to test some packages and apps before installing it to my HDD, so I'm willing to do this thing.

Besides, I want a real conclusion for this situation, as it may happen again even if I install it on my PC.

---

### Post by sanderj on 2013-02-23
Well, the question is if GRUB can work with an OS on a USB stick...

If the USB stick Ubuntu works well (network, GPU, etc), you can easily install it to your harddisk. The Ubuntu installer will take care of shrinking an existing partition.

If that is a bridge too far, you can temporarily remove your current harddisk, and put in some other harddisk and install Ubuntu to that.

---

### Post by commonsensekim on 2013-02-23
I do think the GRUB works on USB.
I actually tried booting the USB on VMWare, and it successfully booted into Unity.

---

### Post by bogan on 2013-02-24
HI1, **commonsensekim**,

I gather you have an Efi set-up, together with hybrid graphics nvidia/Intel Optimus.

For the later you need Bumblebee, for the former, my understanding is you need to have the 64 bit version of Ubuntu, and the efi version of Grub.

But I am not expert on either and hopefully someone who is can confirm that - or dispute it - and give you details. Or perhaps a search in the forums can find it/them for you.

Chao!, **bogan**.

---

