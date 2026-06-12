---
title: "LiveCD Terminal"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by ajdrew06 on 2012-12-18
Hi All

Is there a way to use the LiveCD's terminal to make adjustments to an installed version of Ubuntu? I am having issues with my nvidia driver, and I can't see anything through the video output. I need to get into the installed terminal to remove the nvidia drivers, but I can't see anything. Can I use LiveCD's terminal to remove the drivers? Please help. Very frustrated.

Thank you!
-Drew

---

### Post by Sealbhach on 2012-12-18
You don't necessarily need a Live CD to do that. Try doing Ctrl+Alt+F1 to bring up another screen. 

Or you can hold down the Shift key during boot up to bring up a grub menu and boot into recovery or root terminal mode.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Then do apt-get --purge autoremove nivdia-current

Then apt-get install nvidia-current

You don't need to use sudo if you are in the root terminal

.

---

### Post by ajdrew06 on 2012-12-18
I can't see any other screen. When I go CTRL+ALT+F1, my monitor says MODE NOT SUPPORTED. I get nothing. I can boot fine in LiveCD. It seems to be the only way. When I hold SHIFT, I don't seem to get the GRUB menu. Maybe I'm hitting too late? Unfortunately, I can't see to know when to push it.

---

### Post by Sealbhach on 2012-12-18
Try to get the grub menu , you need to keep the shift key held down, the opportunity goes by very fast at bootup.

If you use a live cd you need to chroot which is more complicated.

.

---

### Post by ajdrew06 on 2012-12-18
I think that might be my only option. When I press & hold the shift key, I briefly see GRUB MENU STARTING, then nothing. Please advise as to use chroot thank you!

---

### Post by Sealbhach on 2012-12-18
If you have to use the liveCD you need to know which disk to mount. Follow instructions 1,2, and 3 on [this page]("http://opensource-sidh.blogspot.co.uk/2011/06/recover-grub-live-ubuntu-cd-pendrive.html") and make a note of your linux drive.

So, let's assume for the sake of example your main linux partition is on /dev/sda1 then you need to 

```
sudo mount /dev/sda1 /mnt 
```The password is blank so just hit ENTER when prompted for a password.

Then do 

```
sudo chroot /mnt
```Now you can install or remove packages as if you were using the system normally.

When you are finished do

```

sudo umount /mnt
```Quit the terminal and reboot the normal desktop.

.

---

### Post by ajdrew06 on 2012-12-18
Thank you!!!!!!!

---

