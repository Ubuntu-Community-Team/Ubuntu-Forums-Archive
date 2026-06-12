---
title: "My grub bootloader menu just got a lot shorter... hmmmmm"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by BTXNick on 2011-10-25
So I accidentally deleted my ubuntu hard drive partition while in windoze. This has happened before and it's not that big of a deal so I just reinstalled ubuntu from USB to reinstall grub. But when I restarted my computer I noticed that I was missing an item or two from my grub menu.

More specifically, I think there was a windows 7 option besides the loader one? What is the loader one? I'm using it right now and other than the time being wrong when I first got on it seemed pretty normal. 

So what gives? Am I missing something? Or am I just being paranoid? And is the windows loader something different than what is normally used?



[IMG]http://i13.photobucket.com/albums/a259/Btxnick/IMG_8301.jpg[/IMG]

---

### Post by BeRA on 2011-10-25
your windows recovery partition is probably not included as an item in your grub menu (11.04 and previous versions displayed it, but not 11.10)- it's the same case on my laptop. Nothing to worry about as it's still there, but just not in grub anymore (you can start it as you used to before installing linux) :D

edit: ok, I see know from your screenshot you use 11.04. Then I have no explanation :S

---

### Post by kemtnbkr on 2011-10-25
No, that looks fine to me..

At least, my install w/ Win 7 looks exactly like yours.  Perhaps you think it looks shorter because when you reinstalled Ubuntu, you may have had two or more kernel versions before, which all show up as GRUB entries.  In which case you're still fine.  

If i were you, I'd try booting to Win 7 just to make sure before you write too much data to your HD.

---

### Post by hansdown on 2011-10-25
> **kemtnbkr said:**
> No, that looks fine to me..

At least, my install w/ Win 7 looks exactly like yours.  Perhaps you think it looks shorter because when you reinstalled Ubuntu, you may have had two or more kernel versions before, which all show up as GRUB entries.  In which case you're still fine.  

If i were you, I'd try booting to Win 7 just to make sure before you write too much data to your HD.

+1.

Hi,BTXNick.

kemtnbkr, is right. when you reinstall, you'll only get the newest kernel.

---

### Post by Mark Phelps on 2011-10-26
Unless your recovery partition is bootable (i.e., has boot loader files stored in it), os_prober will not see an OS there, so, it will not add an entry to GRUB for it.  What you see is the usual case.

---

### Post by philinux on 2011-10-26
11.10

Just checked this on my laptop.

```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found linux image: /boot/vmlinuz-3.0.0-11-generic
Found initrd image: /boot/initrd.img-3.0.0-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

```

---

