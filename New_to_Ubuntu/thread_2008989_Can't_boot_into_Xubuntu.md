---
title: "Can't boot into Xubuntu"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by fluffy283 on 2012-06-23
I have Xubuntu 11.10 installed on my USB hard drive. I couldn't install it onto this laptop because it's my boyfriend's and he doesn't use anything but Windows. I thought that if I installed it onto my USB drive, I could just take it around with me.

But now I can't use Xubuntu on his laptop. When I installed it, it went just fine and ran with no hangups. Now when I try to boot into Xubuntu, I get an error message. Something to the effect of:

Windows failed to start. Windows could not find the file /ubuntu/winboot/wubildr.

Please insert your repair disc, etc, etc.

Well there is no repair disc and Windows starts up just fine. I tried all 3 of his USB ports and none of them can make it work. I even plugged in my USB multi-port and tried all the ports on that, and it still gave the same message.

Right now, I know that the hard drive is in the right place because I have other shortcuts on his desktop that point to the USB port that I used when installing Xubuntu. I am trying to get familiar with Linux because I'm in my second quarter at ITT Tech so I have time before we get to Linux and I want to be ahead of the game a little bit.

What can I do?

---

### Post by HiImTye on 2012-06-23
thats the message you receive when you try to boot from the LiveUSB?

I'd rewrite the LiveUSB, it shouldn't be trying to 'boot Windows' at all

---

### Post by fluffy283 on 2012-06-23
thats the message you receive when you try to boot from the LiveUSB?

I'm assuming it would qualify as LiveUSB, yes. It's a 300GB USB hard drive and the Xubuntu installation is 30 GB. I used "install inside Windows" because I don't know how to partition for a full install and I'm not giving Xubuntu my whole hard drive or risking any ill effects to his laptop because I don't know what I'm doing.

I can uninstall and reinstall Xubuntu if that would possibly fix it.

---

### Post by audiomick on 2012-06-23
> **fluffy283 said:**
>  I used "install inside Windows" because I don't know how to partition for a full install and I'm not giving Xubuntu my whole hard drive or risking any ill effects to his laptop because I don't know what I'm doing.

I don't think that was the right way to go about it. Here are a few links about setting up a USB drive/ stick as a bootable device. I haven't tried any of them, but I gather they are about what you want, i.e. a USB pen drive that you can use to boot into Linux on a computer where Linux is not  installed.

[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")
[http://www.bluewhaleseo.com/blog/bootable-xubuntu-linux-os-usb-flash-drive-improve-productivity-mobility/]("http://www.bluewhaleseo.com/blog/bootable-xubuntu-linux-os-usb-flash-drive-improve-productivity-mobility/")
[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/")
[http://www.informationweek.com/news/software/infrastructure/207800392]("http://www.informationweek.com/news/software/infrastructure/207800392")
[http://en.wikipedia.org/wiki/UNetbootin]("http://en.wikipedia.org/wiki/UNetbootin")

I hope there is something useful in there.

---

