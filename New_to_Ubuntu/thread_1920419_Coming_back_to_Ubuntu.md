---
title: "Coming back to Ubuntu"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by PhibreOptix on 2012-02-04
Hi All,

I am coming back to ubuntu after a few years of not using it.
I have grown accustomed to playing 3D games, so I have been taking a look into hypervisor software Xen to see if it's possible to run both OS's at the same time.

If anyone here has experience with Xen that would be great.

* What kind of performance hit is to be expected from this kind of setup?

* Is XP currently the best windows to virtualize for better performance or will windows 7 be fine as well?

Thanks,

---

### Post by durand on 2012-02-04
You might have better luck with Virtual Box rather than Xen, which is designed for servers rather than desktops. Does Xen support opengl or directx?

---

### Post by PhibreOptix on 2012-02-04
I'm steering away from virtualbox because it is a userland VM solution. Xen has got PCI passthrough which allows one of the virtualized guests to natively communicate with the graphics adapter. Was looking to see if anyone here had any experience with using it.

---

### Post by durand on 2012-02-04
Yeah, I thought it did something like that. I know that Xen used to be pretty popular a couple of years ago but I think most people find vbox easier and suited to their needs. You could post this in a more relevant forum to get more attension. Gaming perhaps?

---

### Post by cap10devnull on 2012-02-05
if you are looking at Xen then probably you should look at KVM too ;)

---

### Post by wildmanne39 on 2012-02-05
Hi, vm's do not play most 3D games very well but it depends on the game so you may want to use a dual boot.

Also many games play well in wine or cross over but I have not used either of them personally I only know what friends have told me.
Thanks

---

