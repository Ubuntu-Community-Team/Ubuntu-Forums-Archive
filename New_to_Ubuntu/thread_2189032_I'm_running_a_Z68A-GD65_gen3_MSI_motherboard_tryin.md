---
title: "I'm running a Z68A-GD65 gen3 MSI motherboard trying to get ANY Linux OS instead of W7"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by botrytisanathema on 2013-11-20
Hello everyone, I'm running a custom computer with 8 gigs of RAM, 2k sandybridge cpu (intel), some X2 series GPU from NVIDIA i forget exactly atm, but its like 1g memory, and a Z68A-GD65 gen3 MB from MSI (which I'm assuming some kernel issue or issue from the NVIDIA may be the problem but i doubt the latter).

I'm completely new to linux and this community as a whole, I have some simple errors that I tried endlessly to find others asking about it in the same way but couldn't find a solution.  I kept trying to do a full install of Ubuntu 13.01, got to splashscreen then did a bizarro shattered blue/green/black checkers in place of my monitor, so I tried installing 12.04 and got the same results. (I used the USB install method each time)

Upon trying to find a solution, I discovered there's a linux distro called Winki 3 which is made by MSI, and for MSI's new gen3 motherboards, which I use on my tower (currently under ubuntu splashscreen for eternity), so I was wondering if anyone on this board has any feedback pertaining to MSI's Winki3 (I also can't find Winki3 for the life of me) and if this is an option I should go for on my tower, and what option I should choose for my laptop that I'm on now, here are it's complete specs:
DirectX: 10.1
phys memory: 3947 MB
min gfx memory: 128 MB
max gfx memory: 1760 MB
Gfx memory in use: 257 MB
Processor: Intel64 Family 6 Model 42
               Stepping 7
Processor Speed: 2095 MHz
Intel(R) HD Graphics 3000
Video BIOS: 2098.0
current mode: 1366 by 768


TL;DR - I'm new to Linux though I'm having troubles installing! Found out about Winki3 finding solutions for my Ubuntu issues I still haven't solved. Was wondering if Winki3 is a good option for the peculiar motherboard I have (can't find a download for it I looked everywhere) and if I am to install Linux on this laptop I'm using AFTER I get Linux happy and situated on my tower, which would you recommend to me? 

PPS Though I'm not sure if needed basically my story is I built a decent computer a good time ago and very slowly overtime just slowing down and when I got back from vacation recently it was so slow I couldn't right click anything without win.explorer freezing so I finally said darn windows I'm going to try linux and I've been trying for a decent while (tired of having to reformat and clean/wipe stuff out regularly and still slowness persists); also I play a lot of games and this is semi-important but not really since all I've played for some great amount of time is Dota2, so I'd just need to make sure Steam still works is all.):P

---

### Post by botrytisanathema on 2013-11-20
After a little more looking, it seems that I'm wanting UbuntuStudio for my tower and Lubuntu possibly for this laptop; though what do I do about the odd installation issues I've been facing with my gen3 MSI board most likely being the issue and probably my NVIDIA gpu.. I've read something pertaining to changing something in the BIOS and the problem I'm facing goes away but I need a little more specified help...thanks in advance!

---

### Post by philinux on 2013-11-20
> **botrytisanathema said:**
> After a little more looking, it seems that I'm wanting UbuntuStudio for my tower and Lubuntu possibly for this laptop; though what do I do about the odd installation issues I've been facing with my gen3 MSI board most likely being the issue and probably my NVIDIA gpu.. I've read something pertaining to changing **** in the BIOS and the problem I'm facing goes away but I need a little more specified help...thanks in advance!

Try Lubuntu or ubuntustudio of a live usb stick .

---

### Post by oldfred on 2013-11-20
Is system UEFI or BIOS?

Are you booting with nVidia or Intel chip? and can you control that in UEFI/BIOS or does it just default to one or the other.
With nVidia you normally need nomodeset as a boot parameter. But Intel may need other parameter or just work?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

