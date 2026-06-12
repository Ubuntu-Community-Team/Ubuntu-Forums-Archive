---
title: "Compiz CPU Usage"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jlward4th on 2011-07-30
When my new T420s Sandy Bridge laptop is idle the compiz process continually uses 3% - 8% of the CPU.  I'm using the integrated Intel video card but I've also tried switching to the NVidia card (didn't work either). This is degrading battery life so I'd like to fix it.  Any ideas?

---

### Post by donniezazen on 2011-07-31
> **jlward4th said:**
> When my new T420s Sandy Bridge laptop is idle the compiz process continually uses 3% - 8% of the CPU.  I'm using the integrated Intel video card but I've also tried switching to the NVidia card (didn't work either). This is degrading battery life so I'd like to fix it.  Any ideas?

I get best battery life and low temperature by turning off discrete graphic card through BIOS. Use kernel power regression workaround, TLP and thinkfan.

---

### Post by jerrylamos on 2011-07-31
> **jlward4th said:**
> When my new T420s Sandy Bridge laptop is idle the compiz process continually uses 3% - 8% of the CPU.  I'm using the integrated Intel video card but I've also tried switching to the NVidia card (didn't work either). This is degrading battery life so I'd like to fix it.  Any ideas?
Compiz keeps churning away even when it has nothing to do.  When I'm on full screen applications it still uses 3% to 8% (give or take) calculating shadows and 3D effects that don't display at all.  Useless work that soaks up processor cycles and who knows what all else.

My fix, Ubuntu-2D which doesn't use Compiz.  At all.  Borders are nice and crisp, not fuzzy.  Nice quick response.  If unity-2d is not in your login choices, use synaptic to install it and choose it at login.

Jerry

---

### Post by jfernyhough on 2011-08-01
If I remember correctly this is down to a plugin. Install compizconfig-settings-manager, run ccsm, and have a play with the plugins. For example, disable mipmapping, change the blur settings, ...

---

