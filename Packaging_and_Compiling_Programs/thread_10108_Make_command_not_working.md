---
title: "Make command not working"
date: 2005-01-04
forum: Packaging and Compiling Programs
---

### Post by poccetbud on 2005-01-04
I'm fairly new to linux, and there are a few minor problems I'm experiencing. I can't seem to get this command to work properly.
 
  ./configure
  make
  su (to become root)
  make install
 these are the commands I need to install edonkey
this is what happens:

lee@Lee:/lib/Programs/edoney_UZ/ed2k-gtk-gui-0.6.3 $ ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH


and the make command simply doesn't work either

lee@Lee:/lib/Programs/edoney_UZ/ed2k-gtk-gui-0.6.3 $ make install
make: *** No rule to make target `install'.  Stop.

also, my sound doesn't work, I have an SB audigy 2 7.1 sound card, which is recognised in the device manager... But will not work, any help will be appreciated
Thank you all very much.

---

### Post by twisted_steel on 2005-01-04
The gcc compiler and other development tools are packaged in build-essential, which you can get from Synaptic.

---

