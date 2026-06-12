---
title: "(Ubuntu 16.04) Boot issues with ACPI and touchscreen on Lenovo Yoga 710"
date: 2016-06-21
forum: New to Ubuntu
---

### Post by Harry_H on 2016-06-21
I've been trying to get an install of Ubuntu 16.04 running on a new Lenovo Yoga 710, from a USB drive. At first the laptop would only boot inconsistently, and would often hang (usually irrecoverably) at random intervals during the boot.
So I changed the boot line (grub bootloader) to remove ```
quiet splash
``` to see debug info and try to find the error. Apparently, there's some kind of routing conflict during boot that causes a bunch of modules to be linked in when they shouldn't be (they don't seem to be consistent over multiple boots, but some such as hid_multitouch hid_force_sensor and a whole group of "snd" modules are always present when the error comes up). In any case, its an error in "kmem cache alloc" that causes some kind of recursive fault and hangs the CPU.

Following advice from other posts on this forum and installation guides for Ubuntu on other Lenovo models, I experimented booting with various ACPI options as on this page: [https://01.org/linux-acpi/documentation/debug-how-isolate-linux-acpi-issues](https://01.org/linux-acpi/documentation/debug-how-isolate-linux-acpi-issues). I quickly discovered that ```
acpi=off
``` allowed the laptop to boot consistently, but ```
acpi=ht
``` still had errors. Based on this page: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) I would have concluded that "[COLOR=#333333][FONT=&amp]the issue is in the ACPI table parsing code itself, or perhaps the SMP code" (and this may still be true, I'm still very new to Linux!), but I've also found that ```
acpi=noirq
``` allows consistent booting.

[/FONT][/COLOR]Since turning off ACPI IRQ routing is a lot less important to me than turning off ACPI power/fan management for a successful boot, I would normally be content to edit the grub command line to include acpi=noirq and leave it there. However using this option also seems to disable the Yoga's touchscreen, which is something I'd very much like to keep. I've read a lot of threads suggesting that this is just a kernel/hardware compatibility issue, i.e. there's nothing I can do about it. But if that's the case then why does a clean boot occasionally work just fine? (touchscreen included!) And why do all the other input devices on the laptop work with acpi=off or acpi=noirq? Maybe these are foolish questions, but while I'm at it, is there no way to enable the touchscreen post-boot?

In fact, on the rare occasions when the system does boot normally the only mention of a touchscreen I can find using ```
dmesg | grep -i touch
``` is a single line referencing the fact that the module hid_multitouch has received input from SYNA750 and assigned it to port so and so, which is apparently the name of my Synaptics touchscreen (it shows up as this in "xinput," though not in "lsusb" when its working). When its working, I can also probe the port its connected to (usually /dev/event9) from a VM using evtest and get a satisfying response whenever I touch the screen, but when booting with acpi=noirq its as if it doesn't exist. It doesn't show up in xinput, lsusb, or lspci so far as I can tell, and probing every serial port at /dev/tty# doesn't get any response. Is it just not turning on?

Someone with a different system and different touchscreen suggests on this thread: [https://bbs.archlinux.org/viewtopic.php?id=133851](https://bbs.archlinux.org/viewtopic.php?id=133851) that hid_multitouch itself might be causing boot problems, but trying the solution posted there (blacklist hid_multitouch and reload it later on during boot) didn't work. However, based on posts like this one: [http://ubuntuforums.org/archive/index.php/t-2082116.html](http://ubuntuforums.org/archive/index.php/t-2082116.html) I have hope that I can just write some kind of script to enable the touchscreen with modprobe and ? I've tried and failed to do so using the touchscreen ID numbers retrieved from dmesg during a successful boot, but I'm pretty sure I'm using the wrong ones...

Other things I've tried: Booting with pci=biosirq, nomodeset, acpi_osi=Linux acpi_osi=Windows etc. etc.
Any advice would be greatly appreciated! Please pardon any newbie mistakes/not enough info, I'll try to provide whatever else I can.

---

### Post by Harry_H on 2016-06-27
On the rare occasions that I do get a successful boot without using acpi=noirq, these are the exact lines I find in the output of dmesg:

[    3.471532] input: SYNA7501:00 06CB:16D1 as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-6/i2c-SYNA7501:00/0018:06CB:16D1.0002/input/input14
[    3.472170] hid-multitouch 0018:06CB:16D1.0002: input,hidraw0: I2C HID v1.00 Device [SYNA7501:00 06CB:16D1] on i2c-SYNA7501:00

---

### Post by steelers743 on 2016-07-18
Bump. I have the same problem and hope there is a fix. It usually lags up on boot but will work perfectly fine 10% of the time so I cant see how it is a hardware issue. Adding ACPI=off allows it to boot up fine but touch screen does not work. Hope someone can figure out a fix!

---

### Post by steelers743 on 2016-07-20
Also tested and confirmed doing the same debugging acpi=ht fails to boot, is a apci parsing bug fixable? Is there any other test I can do to help diagnose the problem?

---

### Post by gordintoronto on 2016-07-21
I have a seven-year-old Gigabyte motherboard with AMD Phenom II processor, which also requires acpi=off. I am lead to believe that it's actually a bug in the BIOS, which is avoided when I disable ACPI. If that is true, you should watch for "BIOS" (EUFI?) updates. Or you could try the beta version, 16.10. (But not for production work!)

---

### Post by Scamentology on 2016-08-18
Just bought a 710 yoga 15" last week on the assumption that Lenovo has a good reputation with Linux.

I am seeing the same issues you see with Mint. I am stuck in the same place using - acpi=noirq, 

Any update to your research to get the touchscreen working would be appreciated.

---

### Post by steelers743 on 2016-08-23
I was able to fix the acpi issue by updating kernels but now I hit a bigger problem with that killing the wireless [https://ubuntuforums.org/showthread.php?t=2334040](https://ubuntuforums.org/showthread.php?t=2334040)

---

### Post by Scottix on 2016-08-26
I am wonder if you are hitting the Ubuntu bug for wireless. I am running Ubuntu Mate and haven't had any issues with the wireless on the 710. The only outstanding issue I have is the touchscreen.

---

### Post by eiriklade93gmail. on 2016-08-28
I'm also having problems, running Mint. It takes between 10-20 forced reboot attempts before I get through to the login screen. I will try the in-thread-suggested acpi for boot with no touch. Can manage without it for now..

---

### Post by jerry.radwick on 2016-10-31
Same peoblem with Asus Q304UA. I can at least boot with "acpi=noirq" but it also disables my touchpad. I wonder what the solution might be. After installation, during first run and during live boot from USB, Ubuntu works perfectly along with touch screen, touch pad and everything else. When I boot from HDD later, I get weird errors like "Fixing recursive fault but requires reboot". Tue system came preinstalled with Win10. I wonder if formatting the whole drive and inatalling only Ubuntu 16.04 would be of any use - anyone tried that?

---

### Post by gordintoronto on 2016-11-02
I'm quite sure that removing Windows will have no effect on this situation, unless you are running Ubuntu in a VM.

> **jerry.radwick said:**
> Same peoblem with Asus Q304UA. I can at least boot with "acpi=noirq" but it also disables my touchpad. I wonder what the solution might be. After installation, during first run and during live boot from USB, Ubuntu works perfectly along with touch screen, touch pad and everything else. When I boot from HDD later, I get weird errors like "Fixing recursive fault but requires reboot". Tue system came preinstalled with Win10. I wonder if formatting the whole drive and inatalling only Ubuntu 16.04 would be of any use - anyone tried that?

---

### Post by spiros.mrg on 2017-01-04
I have had the same issue with Yoga 700-11ISK and Ubuntu 16.04 on that.
There are several threads in the internet, and it all leads to the HID multitouch module being the root cause (changing your ACPI setting disables that module).
**The only thing that worked for me is upgrading to the latest kernel (4.10).**
There is another thread mentioning that this has caused wireless failures for some setups:
[https://bugzilla.redhat.com/show_bug.cgi?id=1297188](https://bugzilla.redhat.com/show_bug.cgi?id=1297188)
but I didn't notice that to be the case for me (I also used newer kernel, that thread is stuck on 4.7).

---

### Post by jamieg2 on 2017-01-16
I think I found a workaround for this, while still using the standard 4.4.0 kernel.

I noticed that [FONT=courier new]hid_sensor_hub[/FONT] was always the first listed module in the kernel error dumps when I booted without "quiet" and "splash".

Edit /etc/defaults/grub and make the following change,

[FONT=courier new]-GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
+GRUB_CMDLINE_LINUX_DEFAULT="modprobe.blacklist=hid_sensor_hub quiet splash"[/FONT]

then run [FONT=courier new]sudo update-grub[/FONT].

It has booted up several times for me, and the touchscreen works. I don't know if the fingerprint sensor works, but I don't care about that.

---

### Post by twildawnight on 2017-01-30
OK,

That last proposed solution works well for me.

Thanks a lot

---

### Post by twildawnight on 2017-01-30
OK,

That last proposed solution works well for me. It is actually better than acpi=noirq.

Thanks a lot

---

### Post by stevefdriscoll on 2017-04-02
1Perfect thank> **jamieg2 said:**
> I think I found a workaround for this, while still using the standard 4.4.0 kernel.

I noticed that [FONT=courier new]hid_sensor_hub[/FONT] was always the first listed module in the kernel error dumps when I booted without "quiet" and "splash".

Edit /etc/defaults/grub and make the following change,

[FONT=courier new]-GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
+GRUB_CMDLINE_LINUX_DEFAULT="modprobe.blacklist=hid_sensor_hub quiet splash"[/FONT]

then run [FONT=courier new]sudo update-grub[/FONT].

It has booted up several times for me, and the touchscreen works. I don't know if the fingerprint sensor works, but I don't care about that.

I just bought the "Lenovo Yoga 710 2-in-1 15.6" Touch-Screen Laptop - Intel Core i5 - 8GB Memory - NVIDIA GeForce 940MX - 256GB SSD - Pearl black"

I was stuck at the Ubuntu 16.04 boot hangup until I saw this thread. I used GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq" solution initially and the install went smooth from there.

I wasn't interested in microsoft so I made a recovery usb first and wiped it clean.  Then I wanted to post a thank you to Swetha and noticed the follow on suggestion of "modprobe.blacklist=hid_sensor_hub" which indeed leaves the touch screen enabled and seems to be working.

At this point, everything (including wifi) seems to be working just fine.

Thank you all!

---

