---
title: "Black Borders Around GRUB and Splash"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2012-06-23
Here's an interesting one: I recently bought a new monitor capable of a 1920 x 1080 resolution. No problems there. Ubuntu detects it and my video card (nVidia GT640) perfectly. I can load up the proprietary drivers fine. In fact, all is running well. Until I try to replace the vga cable with a DVI-D cable.

What I'm now getting is both a grub screen* and *a boot-splash with a thick black border around it. (Maybe an inch at the bottom/top and two inches at the sides.) 

From studying it, it's not that the resolution is incorrect -- it actually looks as though the screen has been shrunk. So I'm getting a 1920 x 1080 resolution picture, only it's been shrunk by a few inches. As a result, the GRUB text is slightly smaller than you'd expect, and the UBUNTU text on the splash logo is slightly smaller than when using VGA.

It's not a massive problem. I dare say I could either just grin and bear it (since my desktop resolution is perfectly fine), or remove the splash altogether and resize the GRUB text to a lower resolution (thus making it easier to read.) But I would like to fix it if I can. Any ideas?

---

### Post by oklokl on 2012-06-23
Usage
Try the search usage.
Resolution can be changed.
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer?field.series_filter=precise]("https://launchpad.net/%7Edanielrichter2007/+archive/grub-customizer?field.series_filter=precise")


grub-customizer


```
sudo apt-add-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

```

---

### Post by SpongeBob SquarePants on 2012-06-23
Thanks for the link, but I think you're misunderstanding the nature of my problem. It's not that the resolution of the splash image/GRUB is wrong and needs changing – even in grub-customizer it shows up as 1920 x 1080 – it's that the correctly sized image is being squashed by the presence of the black border. It's not that the 1920 x 1080 sized background has been replaced by a, say, 1280 x 1024 background or anything like that. The picture resolution is fine. The black border is the problem. Even if I load a lesser resolution background, the black border remains.

---

### Post by d.atanasov on 2012-06-23
Hi, 

This is just an idea but maybe I am wrong.  Can you update grub while you have your DVI-D cable plugged? Perhaps it matters how the signal were decoded for VGA and DVI by grub !?

---

### Post by SpongeBob SquarePants on 2012-06-23
I've already updated my GRUB numerous times whist trying out different fixes. The black border persists.

---

### Post by oklokl on 2012-06-23
User Monitor
 Menu setting
 Please use the ...
 There are [COLOR=Red]auto button.[/COLOR]
 Look at the monitor.

but 
If you do not have one... [COLOR=Red]auto button.[/COLOR]
 Menu is hidden in the ...

Monitor Menu button
Check the manual.

---

