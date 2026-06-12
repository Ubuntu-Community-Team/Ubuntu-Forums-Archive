---
title: "I really messed up..and now.."
date: 2013-08-01
forum: New to Ubuntu
---

### Post by rodd2 on 2013-08-01
...I can't even perform a wipe to boot into the base ChromeOS.

I Ubuntu on an Acer C7, I thought that I could repartition some drive space to create from unused space. On reboot, I get the yellow exclamation mark. Ctrl+D doesn't work, nor does Ctrl+U. I clicked tab and found that my dev_boot_usb is set to 1. Now I can't boot to the recovery SD card tht I created under Windows. I am all messed up. 

How do I get to the shell in Developer Mode to change the dev_boot_usb value?
Wiping my hard drive just loops me back to "Missing OS" message. Any help?

Thanks a bunch.

---

### Post by Bashing-om on 2013-08-01
rodd2; Hi ! Welcome to the forum .

Maybe yes, maybe not so yes... show us what there is to work with/from.
Boot up a liveDVD, and post the out put of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```which shows how your disk(s) are partitioned, and related info.[INDENT][INDENT]a tale in the telling
[/INDENT]
[/INDENT]

---

### Post by rodd2 on 2013-08-02
Thanks Bashing. I don't have a DVD drive on the Acer C7 and the dev_boot_usb value is set to 0 so I can't boot to USB (which is my problem). I am really stuck. I thougth that wiping and starting over with the ChromeOS would work but after rebooting, I am back to "Missing OS".

---

### Post by w1ll1am on 2013-08-02
have you looked here?

[https://support.google.com/chromeos/answer/1080595?hl=en](https://support.google.com/chromeos/answer/1080595?hl=en)

I did this to my CR-48 once and was able to restore it but it was a long time ago so I am not sure what needs to be done. I think it will auto boot from the recovery USB if you let it sit there for a minute.

---

### Post by rodd2 on 2013-08-02
w1ll1am, thanks. I used something similiar to create the SD recovery card but CTRL+U doesn't work because the dev_boot_usb parameter isn't set for external boot.

---

