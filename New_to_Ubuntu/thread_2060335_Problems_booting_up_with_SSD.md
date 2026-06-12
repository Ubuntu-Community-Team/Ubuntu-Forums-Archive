---
title: "Problems booting up with SSD"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by herbertportillo on 2012-09-19
I bought an SSD last week and I decided to do a clean install of Ubuntu on it.

I created a Live USB, took out the old HDD, and put in the new SSD.

Booted up into the USB, installed in onto the SSD, and restarted.

Now, the computer only starts with the USB plugged in. If I take it out, the computer won't boot from the SSD.

I know for a fact that the operating system installed onto the SSD, I didn't install it onto the USB.

I need help, thank you.

---

### Post by jrog on 2012-09-19
> **herbertportillo said:**
> I bought an SSD last week and I decided to do a clean install of Ubuntu on it.

I created a Live USB, took out the old HDD, and put in the new SSD.

Booted up into the USB, installed in onto the SSD, and restarted.

Now, the computer only starts with the USB plugged in. If I take it out, the computer won't boot from the SSD.

I know for a fact that the operating system installed onto the SSD, I didn't install it onto the USB.

I need help, thank you.
What about grub? Did you install it to the USB? It defaults to the USB in some cases.

---

### Post by herbertportillo on 2012-09-19
I have no idea, but if I can't boot without the USB in, that's probably where it went.

---

### Post by jrog on 2012-09-19
> **herbertportillo said:**
> I have no idea, but if I can't boot without the USB in, that's probably where it went.
Here's one bug report about it, for example (though this bug report says that it won't boot to Ubuntu even when the USB is inserted, so I'm not sure whether it's the same problem you're having): [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1044887](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1044887)

The only sure way I know of to fix this would be to recreate the Live USB and re-install, making sure that grub and everything else is installed to the right drive (you may have to do this manually). On the other hand, it *may* be that you can boot into Ubuntu (with the USB inserted, since you have to do that in your case) and then use Boot Repair to move grub from the USB to the SSD, if that is in fact your problem.

Boot Repair is available in a PPA, so you can install it using these commands:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair
```

---

### Post by pqwoerituytrueiwoq on 2012-09-19
it installed the MBR to the USB drive (i had this happen to me this morning on a old box with a 160gb wd hdd)
boot it with the usb plugged in and remove the usb
run ```
sudo grub-install /dev/sda
```

---

### Post by herbertportillo on 2012-09-19
Screw this, I'll just reinstall it from scratch again.

Obviously if I do what I did again it won't install right. So, how do I make sure that it installs everything onto the stupid SSD and not some parts on the USB?

---

### Post by herbertportillo on 2012-09-19
Never mind, boot repair fixed it. installed 

I was able to install GRUB onto the SSD, and now it boots without the USB drive. The only difference now is that I have to manually pick the kernel when I turn on the computer, where it just went straight into the operating system before. Whatever, not a big deal.

Thanks a lot!

---

### Post by pqwoerituytrueiwoq on 2012-09-19
> **herbertportillo said:**
>  how do I make sure that it installs everything onto the stupid SSD and not some parts on the USB?
choose custom install and make sure the correct device is selected for install the MBR to

---

### Post by YannBuntu on 2012-09-20
Hello

> **herbertportillo said:**
> The only difference now is that I have to manually pick the kernel when I turn on the computer, where it just went straight into the operating system before.

You can reduce the timeout of the GRUB menu via the "Unhide boot menu" option of Boot-Repair:

[IMG]http://pix.toile-libre.org/upload/img/1335263156.png[/IMG]

---

### Post by jrog on 2012-09-20
> **herbertportillo said:**
> Never mind, boot repair fixed it. installed 

I was able to install GRUB onto the SSD, and now it boots without the USB drive. The only difference now is that I have to manually pick the kernel when I turn on the computer, where it just went straight into the operating system before. Whatever, not a big deal.

Thanks a lot!
Excellent, glad it worked! You're welcome. (And see YannBuntu's comment about the other thing.)

---

