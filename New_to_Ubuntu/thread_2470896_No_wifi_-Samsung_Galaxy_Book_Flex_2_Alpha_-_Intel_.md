---
title: "No wifi -Samsung Galaxy Book Flex 2 Alpha - Intel wifi6 AX201"
date: 2022-01-15
forum: New to Ubuntu
---

### Post by mgarnold86 on 2022-01-15
Hi everyone, Im still pretty new to Linux as a whole and this one has me stumped. I bought a Flex2 Alpha and when I install Ubuntu it doesn't see the wifi card. I plugged in a usb ethernet adapter which got me online and I found a walk through at github for this issue ([https://gist.github.com/jrmysvr/32bb08bb2e1e4cd12c96675b64e17e48](https://gist.github.com/jrmysvr/32bb08bb2e1e4cd12c96675b64e17e48)). I was able to DL Ubuntu 21.04 to mimic the walk through, but the walk through says to load kernel 5.11.0-2x from "Advanced options" in the GRUB loader and the copy of 21.04 I downloaded only has kernels 5.11.0-46 and 5.11.0-16(I'm not sure if the kernel version has anything to do with my overall issue but i wanted to point out the differences in my attempt vs the walk through). After picking the 5.11.0-16 kernel I follow all of the steps until I get to "reboot" where my experience differs again from the walk through. When I reboot I'm prompted to register a new key to my UEFI which I do  (I only mention it because it's NOT mentioned in the walk through). After booting back into the 5.11.0-16 kernel I enter the next command to purge the 5.13.4 kernel and get a response telling me it cant find the 5.13.4  package/kernel to purge. I assume I'm having this issue because I don't have the exact same version of Ubuntu 21.04 that the person who wrote this had but unfortunately I don't know how to find the info I need to correct the issue. If anyone would help me by correcting these instructions or help me understand how to know what to change myself to make this walk through work with any of the versions of Ubuntu currently available on their site I would be greatly appreciative.

---

