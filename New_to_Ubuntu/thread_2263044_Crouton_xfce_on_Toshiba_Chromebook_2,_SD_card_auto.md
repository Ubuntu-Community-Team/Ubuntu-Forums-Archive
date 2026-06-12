---
title: "Crouton: xfce on Toshiba Chromebook 2, SD card automount problems?"
date: 2015-01-29
forum: New to Ubuntu
---

### Post by connor-jolley1980 on 2015-01-29
Hi,

I've been tinkering with this set up for the last 2 weeks but do not know where to begin troubleshooting this issue.

I run Chrome OS on a Toshiba Chromebook 2. I installed an xfce chroot in order to use a torrent client and install VLC. I have a 128 GB SD card in the SD card slot of the device to which I directly save files that I am downloading.

It's been working fine except that Transmission seemed to be responsible for the CPU overloading and freezing the system. So I started experimenting with different torrent clients, some of which work fine and don't cause the same problem I was having with Transmission. However, now a new problem has emerged whereby I am getting read errors with the SD card. Now even when I go back to Transmission every so often it will tell me that it can't download to the SD because it is read only. I've tried to keep track of what could be causing it by looking at error messages that appear in crosh, every so often (but not always) there has been a 'USB device not recognised' type error. Once the problem occurs it isn't just on the chroot, when I try to transfer within files Chrome OS tells me that it is unable to. I'm guessing it is probably something to do with the automounting going wrong but have no idea how to troubleshoot potential errors beyond looking at what shows up on crosh while I am running my chroot.

Can anyone give advice on how to begin troubleshooting so that I can provide more useful information than I've been able to so far?

Thanks.

---

