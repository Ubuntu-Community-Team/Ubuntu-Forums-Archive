---
title: "Codeweavers Crossover and Ubuntu 14.04 issue ..."
date: 2014-07-12
forum: New to Ubuntu
---

### Post by cwmoser on 2014-07-12
I think Codeweavers is having a little difficulty with their Crossover product and Ubuntu 14.04.
For those who don't know, Crossover is a product that allows Windows applications to run on Ubuntu.
Very nice product.  I use Crossover in order to run Quicken, Quickbooks, and Spider Solitaire.

I note that Crossover works great with Ubuntu 14.04 **Linux Kernel 3.13.0-24-generic**
but not so with the **-30-generic** update.  I tried uninstalling and reinstalling Crossover on both **-24** and **-30**.  I found
that the Crossover application works properly on **-24** but not the **-30** kernel.  I note in the **-30** kernel Process Table that 
process **wineboot.exe** hogs the CPU.

Both my kernels have the _i386 architecture_ installed as required.

For me to run Quicken and Quickbooks I have to reboot, select grub2 menu Advanced and select the **-24** kernel.

Out of curiousity, were there any Linux kernels issued betweened **-24** and **-30**?
Anyone else experience this?  Are there any fixes for this?  I've posted a ticket on the Codeweavers forum.

---

### Post by cwmoser on 2014-07-13
Anyone else on this forum using the Crossover product?

I pondering on the stability and compatibility of 14.04 Ubuntu as compared to 12.04.
I did not have problems with Crossover or Compiz on 12.04 but there seem to be
some "issues" on 14.04.  Perhaps its not Ubuntu but the internal Linux kernel????

Carl

---

