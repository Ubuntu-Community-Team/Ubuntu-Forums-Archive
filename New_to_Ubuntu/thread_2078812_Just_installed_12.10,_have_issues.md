---
title: "Just installed 12.10, have issues"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by jcpahman77 on 2012-10-31
I'm a bit new to Linux, I played with it a bit when Redhat 7.1 was the hot thing, but never go really into it. A friend gave me a link to a usb installer which I used and I like what I see so far, however, it isn't without issue. First, it will not boot to the gui unless I select advanced options first, then select continue with normal boot. If I don't to that it dumps me to a command prompt and I'm linux dump at a command prompt, I keep reaching back to my DOS days and can't get anywhere. Second, it seems to think I'm using a laptop, which couldn't be farther from the truth. I'm running an AMD 64 dual core setup that has been frankenstiened out of an old HP machine.

Those are my issues right now. The objective is to set this up as an HTPC. I have an ATI Radeon 5500 video card installed with 1Gb of video RAM and HDMI so I'm hoping to be able to connect this to my A/V receiver and use it to play movies and whatnot over my home theatre.

Thanks in advance for any help,

Jesse.

---

### Post by Pilot6 on 2012-10-31
The easiest way is to install 12.04.1. 12.10 is still buggy on many comps. It is possible to fix your issues, but do you really need that?

---

### Post by jcpahman77 on 2012-10-31
Actually I only installed 12.10 because it was linked to my via Facebook. Can you point me to an installer and/or ISO for 12.04?

---

### Post by Pilot6 on 2012-10-31
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by jcpahman77 on 2012-10-31
Thank you, I'm downloading 12.04 now. Another newbie question though, when I did the 12.10 install it was via a thumb drive using an installer I ran on windows. Will I need a "program" or something to install 12.04?

---

### Post by Pilot6 on 2012-10-31
It is not a good idea to install Ubuntu from Windows. You need to write iso to a flash drive or CD, boot from it and choose 'Install Ubuntu'. You can find details at the official site, where you downloaded the iso.
But you still can install 12.10 same way using wubi.

---

### Post by jcpahman77 on 2012-10-31
I checked, after posting of course lol, and the installer I used the first time, here: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
will work for 12.04. Should I use this and install like I did for 12.10?

---

### Post by Bashing-om on 2012-10-31
jcpahman77; Hi !

If I may offer my input ...the referenced link is to install ubuntu onto a usb device, not what you want for your end purpose (media server on your desk top box)..

On the referenced link-on the left side- are other links for alternate install methods, choose to make a DVD from windows option (if you must use a windows machine).

You want to install to the hard disk for performance and storage !

Here are some additional guides:
[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

Let us know further how we can help <== BDQ

---

### Post by jcpahman77 on 2012-10-31
Ok, now running 12.04 via a thumb drive. I like it better already, it booted without any issue. Now for a couple newb questions. How do I install new hardware? I'm using the onboard video card right now but I have an AMD Radeon video card installed that I don't see (or perhaps know how to see) and I use a USB wifi adapter that doesn't seem to want to power up with Ubuntu. I'll also want to know how to do audio over HDMI, but that's secondary to getting the video card to work of course.

---

### Post by pqwoerituytrueiwoq on 2012-10-31
to see it in a terminal run ```
lspci | grep VGA
```
lspci gives you every chip and pci card on the motherboard
lsusb list all usb devices (if you are wondering)

here is a guide for installing amd drivers
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

connect your monitor to the amd card for it to work, you may have to boot using nomodeset (google it) for it to work before you install the driver

---

### Post by jcpahman77 on 2012-10-31
hmm the video card doesn't seem to be on that list, but then, it's not a pci card, it's AGP (I think). The lsusb does show my wireless usb adapter, a Linksys AE2500 and I'm Googling to see how to install it.

---

### Post by jcpahman77 on 2012-11-01
I thought I had a handle on this and now I'm lost again. I've been running 12.04 from my thumb drive and liked it, but noticed that installed software (i.e. chomium) would go away after a reboot, so I decided to install to the internal drive. Now I've got issues again. It will not boot to the gui without selected advanced options at the first boot menu and then continue with normal boot at the next menu, except then it sees my display as a laptop screen and has the wrong resolution. Any idea what I'm doing wrong? I made sure to download ALL 172 update too just in case it was a driver issue, still no. I like the way it runs on the thumb drive, but I'd like it to be a bit more permanent.

---

