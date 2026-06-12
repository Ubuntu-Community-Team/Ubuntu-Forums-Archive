---
title: "Windows XP on HDD#1 &amp; Ubuntu on HDD#2"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by b0yd07 on 2008-06-25
I went out and bought and external enclosure for a sata drive that I never actually found a use for. So here I was with 320 gigs of space doing nothing.

I remembered hearing about Ubuntu so I thought I'd give it a whirl on this external drive. My plan is to have Ubuntu load if this external drive if turned on and have windows xp load off the internal disk if the external enclosure is off. So I install the newest release on it and everything seems to be working fine. Awesome. Now I power down the computer and turn off the enclosure to make sure that XP still works.

Apparently this "Grub" pos overwrote the boot sector or whatever on the other drive. This pc now will only start up if the external drive is on and a list comes up to select the operating system. That would be fine and all but the idea is to have this enclosure portable. i.e. will not always be attached. With it off, grub error 21 comes up upon startup. So I read on the internet about loading the xp installation disk and recovery and then typing fixmbr. That took care of it so I decided to format the external drive and forget about it.

Today though, I get the clever idea to unplug the internal drive while installing Ubuntu. Aha! There's no way it can overwrite the windows boot loader this time if it's off... So I do it and everything seems to be fine... Awesome.

I turn off the pc and plug the internal one back up, and then turn off the external enclosure. Works. Now what happens though if I leave the internal on and leave the external on? Will it give me the choice of which one I want loaded? No it just boots straight into Ubuntu. Ok I say, that works out alright. I'm the only one who'd be using it so if I want Ubuntu I'll turn on the drive and when I'm away I'll turn it off. Sounds good to me.

NOT. Again, P.O.S. grub thought it would mess with my other hard drive again when both were on in the previous paragraph. If I sound irritated with grub, it's because I am. (This paragraph is with external turned off.) The grub error 21 didn't come on this time though. Now it's "NTLDR couldn't open drive multi..."

Alright, present tense now. I can only get into Ubuntu now with the internal drive unplugged and the external turned on(obviously). I'm about to format the internal drive because fixmbr doesn't do anything now for some reason and fixboot didn't fix it.

What do you guys suggest I do? Is there a way to get Grub to stop doing this? I'd like Ubuntu to load if the external drive is on, and windows to load with it off, like normal. I can't seem to do it on my own.

Any help would be GREATLY appreciated.
Thanks. -Mike

---

### Post by avtolle on 2008-06-25
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs) may have some information for you.

---

### Post by bumanie on 2008-06-25
Have a look at this link, it should give you all the info. you are looking for - by the way - it works! [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

---

### Post by b0yd07 on 2008-06-25
> **bumanie said:**
> Have a look at this link, it should give you all the info. you are looking for - by the way - it works! [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

I pretty much did exactly that. Though I am using an eSATA hook-up for the external drive instead of USB.
That guide ends where I thought I had everything perfect. However when I reattached the power to the internal drive, left the external on, and then booted up, the ubuntu did something again to my windows drive. This is where that NTLDR message comes up.

I can not get ubuntu to stop messing around with the other drive. Whether during installation or normal boot up it still insists on fubar'ing the other drive. It is beyond frustrating...

Avtolle, I'm looking into that one. It's a little more complicated than what I'd like to hear but I'm trying. I'd still have a problem though if the external drive was off... no ubuntu, NTLDR error.

---

### Post by kansasnoob on 2008-06-25
I've never done an eSATA set-up, but one thing I'm sure of is that for your original XP os/drive to boot with the removable drive removed you need to restore XP's mbr:

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

Now, just as a matter of personal preference, I'd create a separate GRUB partition on your permanent/XP drive. But that's only due to my preference, so don't just jump into it, OK?

Read the "How to make a dedicated  GRUB Partition" below if you decide to go that route:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

Since I don't know about eSATA and have no knowledge of your mobo's BIOS I can't say for sure but another option might be to change boot sequence in your BIOS to pick up GRUB from the eSATA drive if it's plugged in before it "connects" to the system drive.

But please run this by a few other folks before jumping into it, OK?

---

### Post by b0yd07 on 2008-06-25
Alright guys... Figured it out.
Bumanie's link does work out after all.

It was actually my fault that it did this to me. When trying to fix the error 21 yesterday, one of the recommendations was to change the settings for the hard disk in the bios. I had it set on LBA(whatever that means) and forgot to set it back to auto when it didn't work.

Oh man it's been a day. My thanks go out to you two who tried to help. EDIT: three :)

---

