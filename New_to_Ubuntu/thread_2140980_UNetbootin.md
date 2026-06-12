---
title: "UNetbootin"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by kalebud on 2013-05-01
When using UNetbootin I am unable to locate the Vista usb drive displayed ( CD J:,F:,G:,H:,J:, ((K:<which is what the usb is showing) my  UNetbootin is showing drives F:\, G:\, H:\, I:\. Is there a way to make Vista switch the letter for the usb, let's say from K: to F:,G:,H:,I: ?  Also I have formatted the E: drive but only exFat is available not Fat32. Also I want to mount Lubuntu 13 directly to drive E: the exFat format - I am trying LiLi usb creator, UNetbootin and most sites suggest using a DVD or usb to mount to an external hdd with Vista. What happens next, must I buy DVD-Rs?

---

### Post by sudodus on 2013-05-01
Exfat is a proprietary Windows file system, that is difficult to use with linux. So to make a USB boot drive with Unetbootin, you should format it to FAT32, which definitely should be possible with Windows Vista. What kind of drive is it? Pendrive or HDD? USB 2 or 3?

If you specify the computer, at least cpu, ram and graphics chip/card, it will be easier to help.

---

### Post by kalebud on 2013-05-07
So are you saying I should use Unetbootin on Vista to download the .iso and then use Unetbootin to burn to a dvd?, Unetbootin only gives C: as the option for Hd. An external HDD on Win8 is where I want to install the Kubuntu.

---

### Post by linxlimbo on 2013-05-07
just a quick note, unetbootin is a program made for creating bootable usb's not cd's.

---

### Post by Lightning Dragon on 2013-05-07
Hi,

I just installed Lubuntu to a USB Toshiba 16GB last night, so maybe I can help you out. I used LiLi USB Creator, [which is here]("http://www.linuxliveusb.com/"), and then let it download the distro. Once it was finished I then plugged in my USB, clicked the right drive (in my case it was "G") and in Step 4 I checked them all, then pressed the Lightning Bolt image to start the process. It worked like magic!

But if you are wanting to use UNetbootin no matter what, try placing the USB in a different port--like one in the back. Turn the software off and then re-open it. Also, unplug any external hard drives so that one they are not read and two they will not be accidentally selected and erased.

---

