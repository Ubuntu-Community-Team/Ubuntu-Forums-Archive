---
title: "How to mount second drive via HD caddy"
date: 2014-12-06
forum: New to Ubuntu
---

### Post by snowmobiler on 2014-12-06
I have a Dell Latittude lD830 aptop running Ubuntu 14.04 on an SSD (love it!). I found a HD caddy to replace the DVD drive on Amzn for real cheap and wanted to put the original Sata drive I was running on this laptop in the caddy to expand capacity. RIght now the spare drive has ubuntu but I can erase it/reformat it using windows PCs. What is the best way to format/mount this HD? Erase it using windows and make it FAT first, then use Ubuntu to format as EFT4? Or just boot from SSD and reformat using . . .??

Thanks!

---

### Post by nerdtron on 2014-12-06
You can format it in Ubuntu of course. If you plan to make it permanent on the laptop and will not use on a windows computer, you can format it on a native Linux file system such as EXT4.

As for mounting, you can do manual or automatic. Depends on what you want. But first let's format the drive and test it on Ubuntu.

---

### Post by fantab on 2014-12-07
Plug in your HDD, boot ubuntu.
Run the following command and see if the new HDD is being detected:
```
sudo parted -l
```
... post the output here if in doubt.

If its being detected then using Gparted (you may have to install it in ubuntu if you don't have it already).
Using gparted delete all the partitions... and create new ones as needed. If you intend to use the HDD only in Linux then Ext4 is a good choice, but if you want it in both Windows and Ubuntu then format it with NTFS.
Linux can read and write to NTFS but Windows cant understand linux filesystems.

[Gparted tutorial]("http://www.dedoimedo.com/computers/gparted.html").

---

