---
title: "Ubuntu not mounted to usb drive?"
date: 2014-08-21
forum: New to Ubuntu
---

### Post by somehavecalledme on 2014-08-21
I've booted computers of ubuntu using a usb stick before, but for some reason when I boot it on a Dell Xps that used to run Windows Vista (the hard drive crashed) it's booting to the command line with a message saying "can not mount /dev/loop1 on /cow. I've booted ubuntu on this computer before without any issues, but for some reason, I can't just boot it now, so I'm hoping someone can help. I also don't know anything about the command line, so if you know how I can actually run ubuntu from here, please try to explain it to me like I'm five. Thanks.

---

### Post by somehavecalledme on 2014-08-21
I've been typing in many words that I don't know the purpose of, and I haven't accomplished much. I did at one point enter grub or something like that, and I have rebooted the system many times, but I haven't actually accomplished what I'm trying. I would greatlyappreciate any sort of help as I will never figure this out since I actually never use the command line. I'm seriously 100% clueless.

---

### Post by grahammechanical on 2014-08-21
How did you create the Ubuntu live session? From what OS? What program? And what version of Ubuntu are you putting on that USB stick? A Ubuntu live session does not use Grub.

---

### Post by somehavecalledme on 2014-08-21
I made the flashdrive bootable (if that's what you're asking) from [this]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") program using Windows 8 (not 8.1 if that makes a difference). I put Ubuntu v12.04.3 on the flash drive. In order to boot from the flashdrive I just changed my boot setting and set usb devices before the hard drive and rebooted. I didn't do anything to open that command line, it just did it automatically. Also, I don't think that grub thing is default, I just got to it by entering some command I probably shouldn't have, and when I tried entering something nothing happened anyways.

---

### Post by sudodus on 2014-08-22
Welcome to the Ubuntu Forums :-)

1. Have you checked with md5sum, that the download was good? See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Can you boot another computer from your USB flash drive=

3. I suggest that you try another tool to make your USB flash drive bootable, for example ***Unetbootin***. See this link which contains several tips howto make booting from USB work

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by somehavecalledme on 2014-08-22
Thank you, sudodus, I just wiped the flashdrive and used that Unetbootin program instead, and was able to boot Ubuntu without any problems.

---

### Post by sudodus on 2014-08-23
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

