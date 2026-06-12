---
title: "Ubuntu on a thumb drive"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Glurf on 2008-10-27
If I was running Ubuntu off of a 1 gig thumb drive, would the OS save my settings onto it? If I moved it to another computer, would the firefox settings/desktop settings/folder settings/every other kind of setting still be set up right?

---

### Post by scorchgeek on 2008-10-27
I can't answer whether it would save your settings for sure, although I assume so, since it's a read-write medium just like a hard drive. A CD, however, would not. If it did (on the thumb drive, as I expect), you would be able to move it to another computer with all your settings still intact.

---

### Post by P13808 on 2008-10-27
The apps themselves usually have their config files in their app folder.  Seeing how the flash drive is essentially a hard drive, I don't see why the OS would have any problem with saving customization files on it, although you may wish to turn OFF most features due to USB being slow.  And USB 1.0 is. . .

---

### Post by meredeth on 2008-10-27
i've currently got ubuntu on a pretty 8 gb sd card, and i can happily report that it saves all settings as normal, and although i haven't tried slapping it in my other computers yet, i can't imagine why it wouldn't work there, too. maybe i'll go try it right now~ (^_^)

---

### Post by scorchgeek on 2008-10-27
If it saves settings onto an SD card, I would be certain that it would also save onto a flash drive, as they are more developed for the purpose of running OS's from and essentially the same technology. Thanks Meredith.

---

### Post by Keen101 on 2008-10-27
.



**You need at least a 4gig flash drive to have a fully installed ubuntu system. **

But, if you wanted to use a 1gig flash drive you could turn it into a live-USB with the "persisitent home" option. It wont let you keep everything configured, but most things will.

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)

---

### Post by sudo_chop on 2008-10-27
> **Glurf said:**
> If I was running Ubuntu off of a 1 gig thumb drive, would the OS save my settings onto it? If I moved it to another computer, would the firefox settings/desktop settings/folder settings/every other kind of setting still be set up right?
 
Well your whole install is on the thumb drive, which includes all your settings and your files that you have in your /home directory. It will be just like taking the whole computer with you.
 
One thing though about moving to another computer is the bootloader. When you install Ubuntu it sets the boot disk and partition in GRUB and there is a good chance that it will not be the same on whatever computer you move it to. If that is the case just come back here and ask for help, we can walk you through a pretty easy way around it.
 
-sudo chop

---

### Post by Glurf on 2008-10-28
Wow, thanks for the info guys, I needed this before tomorrow, after monday night football I take a gander at the thread, and theres all kinds of replies! :) I'll use the LiveUSB option, since I don't have a 4gig at my disposal, live should work fine.

---

### Post by C.S.Cameron on 2008-10-28
A flash drive created using usb-creator has persistence folders called casper-rw and home-rw.
Changes are saved to these folders.
The operating system takes up about 700M leaving about 300M on a 1G drive for settings and downloads.

---

