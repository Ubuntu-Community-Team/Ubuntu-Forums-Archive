---
title: "Asus laptop only boots into bios set up"
date: 2019-06-02
forum: New to Ubuntu
---

### Post by swangnation on 2019-06-02
Hi guys. I thought i would start this thread because i still haven't got an answer yet from Ask Ubuntu.

My laptop is a little old i must say but still fairly functional. Amd 64 quad core, 4gm ram, 250gb hd (not ssd).

In a nutshell i put Ubuntu onto a usb and decided to re install as i believed the laptop was taking too long to boot and i knew instinctively that the original install was not done properly. I re installed with full encryption and LVM. It was pretty good and it resulted in 1minutes 9 seconds boot up from powering on, to login screen. Now I'm not sure if recent updates of ubuntu have changed all that much but i ultimately i still tried to tweak grub config. Grub default timeouts were changed from 0 to 2 and i uncommented grub style=hidden. I'm not sure if this was the culprit however i don't believe that i did all that much to get the result that i got the next day (i could be wrong so please correct me if you think i am) when i powered on again because all i got was a bootloop into the bios set up screen.

After that, i had to go into boot section of bios, allocate the usb as priority 1, power off and reboot into usb stick and re install. However, the install wizard would not allow me to re install with full encryption and LVM option. At 3am this morning it was getting frustrating....and then....all other options also failed. I would get a quick error message on the screen which would not stay on the screen long enough for me to read and then the installation process would be aborted. 

I powered off and watched a movie....then turned it on again only a couple of hours ago. Clicked install from usb and this time, although i could not install with full encryption and LVM....the 'something else section' did work and i created my own partitions and here i am. Still frustrated because i was relatively happy with the initial LVM and full encryption setup and cannot get it back. Why i liked the initial set up was simply because i like the idea of LVM and compared to my old boot up time of 59 seconds....it was only taking 10seconds more to boot up and that included a 10 word encryption key. It ran quite smoothly, The lagging of apps was considerably lower and the longer i had the ubuntu up and running, the lagging would not increase as compared to before, which to me is indicative of a gnome memory leak of some sort.

In any case guys, sorry to bore you with the above but can you guys think of any way that i can format this hd and re install the full encryption with LVM option? Oh...the message i would get when trying to re install with the encryption and lvm was something along the lines of "LVM volume already in use, lowered priority to find alternative" the message was something like that.

Thank you guys in advance if you read and if you can help

---

### Post by TheFu on 2019-06-02
Sounds like there is some left over data that the new install is seeing, that you don't want seen.

I would wipe the partition table away completely using dd and /dev/null as the input, then repartition with slightly different settings.  Then do an install as normal, choosing the LVM+LUKS option.

If that isn't sufficient, then I'd use a vgremove and pvremove first, then to the dd wipe as above.

---

### Post by swangnation on 2019-06-02
would you mind providing the instruction for that?

---

### Post by CatKiller on 2019-06-02
> **swangnation said:**
> all i got was a bootloop into the bios set up screen.
I don't think there was necessarily anything wrong with your initial configuration, since it was going into the BIOS rather than failing to boot.

One thing that might have been a configuration issue, but not really of your install, would be if your BIOS couldn't find the MBR (or EFI if you were using UEFI, but I suspect that computer might be too old for that) because it was trying to boot the wrong drive.

However, one thing that *could* cause that issue in an elderly computer is a flat watch battery. If it can no longer hold a charge, then the BIOS can't remember its settings. All sorts of peculiar things can happen then.

---

### Post by swangnation on 2019-06-02
> However, one thing that *could* cause that issue in an elderly  computer is a flat watch battery. If it can no longer hold a charge,  then the BIOS can't remember its settings. All sorts of peculiar things  can happen then.

There is something in that as i have heard that before in relation to other devices and machines however right now, i have ubuntu working again from the laptop. The only disappointment i have is that i am unable to re install with full encryption and LVM option unless i wipe the volumes completely, i just need instructions on how to do that

---

### Post by swangnation on 2019-06-03
Problem is resolved.

Had to power off for a few hours then re install via 'something else' option, re configured partitions. Reboot again and download lvm2.....reboot and check for volumes in which there was none...then reboot and install via bootable usb. All seems to be working well with only one difference. With the original install of full encryption and LVM there was a loop device. Now it's no longer there, i'm not sure if its because of the latest updates, it might be but all seems to be working well. In fact this boots up quicker than last time, last time was 1m9s, now it's 1m913ms. I'm pleased with that. In the "slow booting of ubuntu" thread, i was getting boot up times of over a minute with no encryption and the bare minimum of apps. Now i have a small number of snaps, 1 game and about 35 desktop themes plus a few other bits and pieces for tweaking this system.

Hope this helps. Marking this as solved

Cheers.

---

