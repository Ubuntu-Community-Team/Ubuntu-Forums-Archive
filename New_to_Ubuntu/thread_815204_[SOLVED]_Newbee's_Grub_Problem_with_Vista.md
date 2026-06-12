---
title: "[SOLVED] Newbee's Grub Problem with Vista"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by dkc.com on 2008-06-01
Plz read my query carefully friends.

I am a common user of windows and because of curiosity I installed Ubuntu 8.10 on my system with multiboot option. I like that very much but it was installed on a very small partition of 4.5 gb so i felt it wasn't enouh. As a result I bought a 320 GB external hard drive and decided to install ubuntu on it. so I deleted the ubuntu partition from hard drive.

One more thing, I haven't received any installation cd from my laptop manufacturer but they have provided the os files on a small partition of the hard drive itself.

So, after uninstalling ubuntu from my hard drive, i faced the GRUB error.I couldn't find a way, so I installed ubuntu again on the same partition and then it worked. Then checked linuxquestions.org through google which suggested to have a bootable disc for Vista, which I haven't got.

I also downloaded and tried auto_super_grub_disk_1.0.exe, as per suggested in that forum, but it is very difficult for the primary user like me.

The situation now is first of all I have to face grub and afterwards I have to face another option menu for vista and auto super grub disc.

Is there any way out? Can I make a bootacle cd rom from my os? Is there any easy method for removing ubuntu and Grub? Preferably no command lines, step by step information to follow.

I will be very thankful.

---

### Post by kansasnoob on 2008-06-01
Can you download and burn the downloadable disc listed below? Or have a friend do it for you?

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

It should work just like the Vista "recovery center".

You can then follow the directions below to FixMBR:

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

---

### Post by kansasnoob on 2008-06-01
Oh just thought of something. Once you get the Vista MBR problem worked out you'll want the following tutorial to continue with your new Ubuntu drive:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372)

NOTE: that calls for unplugging your internal hard drive so if you're not comfortable doing that I'd suggest something entirely different, which is creating a separate GRUB partition on your internal hard drive.

Of course that will, once again, mess up your Vista MBR. But you'll end up with GRUB on the internal drive and you'll always see the boot options (you'll want to make Vista the default boot), but you'll always see the boot screen so you can choose to boot the OS(s) on the external drive just by pressing the esc button and selecting what you want.

If you decide you'd like to do this give a shout! Maybe in a new thread if need be.

---

### Post by meierfra. on 2008-06-01
Check out [hermanzone]("http://www.users.bigpond.net.au/hermanzone/p18.htm") for various ways  to fix your MBR.

---

### Post by dkc.com on 2008-06-01
Thanks for these many replies in such a short time. I didn't expect that honestly. Probably, that is the reason why Ubuntu is preferred over other distributions.
I will try and let you know what happened.
Thanks.

---

### Post by dkc.com on 2008-06-05
> **kansasnoob said:**
> Can you download and burn the downloadable disc listed below? Or have a friend do it for you?

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

It should work just like the Vista "recovery center".

You can then follow the directions below to FixMBR:

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)
Thanks. I will try this and let you know what happens.

---

### Post by dkc.com on 2008-06-05
> **kansasnoob said:**
> Oh just thought of something. Once you get the Vista MBR problem worked out you'll want the following tutorial to continue with your new Ubuntu drive:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372)

NOTE: that calls for unplugging your internal hard drive so if you're not comfortable doing that I'd suggest something entirely different, which is creating a separate GRUB partition on your internal hard drive.

Of course that will, once again, mess up your Vista MBR. But you'll end up with GRUB on the internal drive and you'll always see the boot options (you'll want to make Vista the default boot), but you'll always see the boot screen so you can choose to boot the OS(s) on the external drive just by pressing the esc button and selecting what you want.

If you decide you'd like to do this give a shout! Maybe in a new thread if need be.
Thanks. Using this method I have alreday installed Ubuntu 8.04 on my external hard drive.

---

### Post by Flimm on 2008-06-05
> **dkc.com said:**
> Plz read my query carefully friends.
As a result I bought a 320 GB external hard drive and decided to install ubuntu on it.
Before you install Ubuntu on an external hard drive make sure you know enough to ensure that GRUB is installed on the internal hard drive, not the external one. GRUB is the bootloader that allows you to choose between Windows and Ubuntu on bootup. You can run into problems if you install it on an external hard drive: your system might not boot, or only when the external hard drive is plugged in.

---

### Post by Duck2006 on 2008-06-05
> **Flimm said:**
> Before you install Ubuntu on an external hard drive make sure you know enough to ensure that GRUB is installed on the internal hard drive, not the external one. GRUB is the bootloader that allows you to choose between Windows and Ubuntu on bootup. You can run into problems if you install it on an external hard drive: your system might not boot, or only when the external hard drive is plugged in.

You have to make sure that your external usb drive, can be booted from in your BOIS. If it can then yes, you can have grub in the USB drive and not the internal drive, so you will not need the USB drive in to boot to windoze.

---

### Post by dkc.com on 2008-06-05
> **kansasnoob said:**
> Can you download and burn the downloadable disc listed below? Or have a friend do it for you?

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

It should work just like the Vista "recovery center".

You can then follow the directions below to FixMBR:

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Thanks mate. It worked for me completely. The link from the support  of microsoft was fabulous. I have had many suggestions to use fixmbr but nobody pointed out that I have to use it under "bootrec.exe" command. I found it from your link to microsoft. :KS

What I did was like that:

Booted from dvd
went for system recovery
went to command prompt
typed in "bootrec.exe/fixmbr" without quotes and in 1 second I received the message that the thing was done successfully.  

Newbees should be given instructions like that microsoft provided. Step by step and easy to understand.

Thanks vey much.

---

### Post by dkc.com on 2008-06-05
> **Flimm said:**
> Before you install Ubuntu on an external hard drive make sure you know enough to ensure that GRUB is installed on the internal hard drive, not the external one. GRUB is the bootloader that allows you to choose between Windows and Ubuntu on bootup. You can run into problems if you install it on an external hard drive: your system might not boot, or only when the external hard drive is plugged in.

Hi friend,
What I wanted was done by the instructions given on the following link:
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372)
I wanted to install in such a way that I never receive any selection menu of OS, unless I attach my external hard drive to my laptop and choose to boot from there, and that Vista should remain my default OS because my other family members are also using my laptop and they shouldn't get confused. I could do that by that link.
Thanks for your reply.

---

### Post by dkc.com on 2008-06-05
> **kansasnoob said:**
> Oh just thought of something. Once you get the Vista MBR problem worked out you'll want the following tutorial to continue with your new Ubuntu drive:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372)

NOTE: that calls for unplugging your internal hard drive so if you're not comfortable doing that I'd suggest something entirely different, which is creating a separate GRUB partition on your internal hard drive.

Of course that will, once again, mess up your Vista MBR. But you'll end up with GRUB on the internal drive and you'll always see the boot options (you'll want to make Vista the default boot), but you'll always see the boot screen so you can choose to boot the OS(s) on the external drive just by pressing the esc button and selecting what you want.

If you decide you'd like to do this give a shout! Maybe in a new thread if need be.
Hi Buddy,
I followed the link and did what was suggested.
[One more think my external hard drive has four primary partitions 
1 is 75 gb in ext3 format for Linux
2 is 75 gb in ntfs format for my windows back up
3 is 149 gb for my media storage
4 is 512 mb linux swap partition]
When I boot my pc as normal everything is fine.
When I fress F12 and go for one time boot menu, and try to boot from my USB external hard drive, it returned the error 22. What is this mate?
Can you help?

---

