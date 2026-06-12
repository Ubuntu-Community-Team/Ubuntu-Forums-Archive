---
title: "Netbook doesn't boot after installing lubuntu"
date: 2016-07-22
forum: New to Ubuntu
---

### Post by chaoska on 2016-07-22
Hey out there,

I just installed lubuntu and it looked like everything would work. But then it asked me to restart the PC and this is where the problem occured. 
It doesn't boot and says: "/dev/sda1: clean, 121484/15204352 files, 1604719/60790272 blocks".
I have no idea what this means and what I can do about this. 

I would be very gratefuk for some advice!

Sunny greetings!
Chaoska

PS: I don't know if it's importabt, but I installed lubuntu on a netbook of the hp mini series...

---

### Post by leozinho29_eu on 2016-07-22
I suppose your netbook has a Intel Graphics GPU.

The Lubuntu 16.04 ISO is lacking a important package: 

```
xserver-xorg-video-intel
```This package makes the onboard Intel GPU to work. Without it, you won't be able to get to the interface normally. Gladly, just installing it you will solve the issue. To do this I had:

1) Opened the Lubuntu option in GRUB menu
2) Added "nomodeset" in the boot options (generally after "quiet splash") -> "quiet splash nomodeset"
3) Booted the computer
4) Opened synaptic
5) Installed xserver-xorg-video-intel
6) Reboot

On my case, I was unable even to use Ctrl+Alt+F1 because the lightdm was starting and crashing without stop.

Topic with this and different ways to solve the issue: [https://ubuntuforums.org/showthread.php?t=2322111](https://ubuntuforums.org/showthread.php?t=2322111)

Edit: I know that message is related to HD and not video. Every computer that can boot will show a  message like that. 

However, if the installation was made with the Lubuntu  16.04 ISO, then it will never leave that screen.

---

### Post by him610 on 2016-07-22
> "/dev/sda1: clean, 121484/15204352 files, 1604719/60790272 blocks"

This has nothing to do with graphics. It indicates it is in the process of performing a file system check,* fsck.* This is normal: however, post #2 has a valid point.
Which intel graphics chip do you have?
How long did you wait before you killed it?

---

### Post by wildmanne39 on 2016-07-22
I get the same message but my system still boots.

---

