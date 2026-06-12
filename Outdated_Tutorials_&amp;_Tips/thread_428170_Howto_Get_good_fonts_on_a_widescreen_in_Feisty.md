---
title: "Howto: Get good fonts on a widescreen in Feisty"
date: 2007-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by ericdsr on 2007-04-30
I did a clean install of Feisty on my system with a widescreen monitor, everything looked shiny. That is, until I installed nvidia-glx-new for my GeForce 7300 pci-x card. After reboot the fonts looked, as another post described,  "like a  printer running out of ink had printed them" I looked around here, tried various fixes to no avail. 

After a few reinstall cycles, I decided to try something different. Before installing the nvidia driver, I backed the resolution down from 1680x1050 down to 1440x900 *then* installed the driver. After the reboot, things were looking good again but I wanted my 1680x1050 back and looking good *with* accelerated graphics!!! So with fingers crossed I tried it. IT WORKED! The fonts were back and looking good. Since I use both gnome and kde on different boxes, I had to try it with a Kubuntu install as well. It worked, but with one gotcha. My 1680x1050 modeline disappeared from xorg.conf. No biggie, "man gtf" gave me the info I needed to replace it. 

This isn't a very elegant solution but it worked for me. Not sure if it'll work for others with this issue but anyone with that font problem will likely be as desperate as I was. 

Good Luck!

---

