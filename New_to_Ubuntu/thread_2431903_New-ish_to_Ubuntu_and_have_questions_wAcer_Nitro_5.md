---
title: "New-ish to Ubuntu and have questions w/Acer Nitro 5 AN515"
date: 2019-11-23
forum: New to Ubuntu
---

### Post by drakaina6600 on 2019-11-23
So I'm not totally new, but its been several years since I've used Ubuntu. So I've got an Acer Nitro 5 AN515-43-R0YM laptop I'd like to use but it's what I take to college, so I have to know I'm doing things right before I start installing. 

So here are the specs:
Ryzen 5
4gb Radeon RX 560X
16gb Kinston DDR4
256bg M.2 ssd
1tb hard drive

So how well will this work and will I still have control of the power settings and performance options of the gpu? I'm lost so any advice is appreciated! :-)

---

### Post by mörgæs on 2019-11-23
Hi, welcome to the fora.

First you could try to see how it works in a live boot of 19.10. Let's not discuss installation yet.

If you click *edit* and *go advanced* you can change the title to something more descriptive, say *Acer Nitro 5 AN515*. It will increase the chances of attracting a good answer.

---

### Post by drakaina6600 on 2019-11-23
Thanks for the warm welcome. I tried that, but I didn't know if it had the drivers for the 560X or not. I used the LiLi USB Creator so that may have had an effect, but I'm a noob again so that's a wild guess.

---

### Post by oldfred on 2019-11-23
Even if new, you may need to update UEFI and update firmware for SSD. You should do that whether installing Ubuntu or not.

Do not know AMD based Acer, but all Acer seem to have an unique requirement of setting "trust" on Ubuntu UEFI boot entry. It trusts Windows, but any other entry the user has to approve.

[SOLVED]Acer Nitro 5 (with Ryzen 7 2700U, RX 560X) Ubuntu 18.10  
[https://ubuntuforums.org/showthread.php?t=2413504](https://ubuntuforums.org/showthread.php?t=2413504) &
[https://ubuntuforums.org/showthread.php?t=2412117](https://ubuntuforums.org/showthread.php?t=2412117) &
[https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42](https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42)
Acer Nitro 7 Missing AHCI mode Ctrl + S in UEFI
[https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969](https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969)
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

