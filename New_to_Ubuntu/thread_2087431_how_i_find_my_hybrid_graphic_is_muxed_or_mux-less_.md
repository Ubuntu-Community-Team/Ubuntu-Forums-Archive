---
title: "how i find my hybrid graphic is muxed or mux-less ? (to use vga_switcheroo)"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by snifer7 on 2012-11-23
i bought hp dv3 2360ee notebook.
it has hybrid graphic
1: intel graphics media accelerator
2: ati mobility radeon HD 4550

is it mux-less ? can i use vga_switcheroo to enable discrete card?

thanks :)

---

### Post by snifer7 on 2012-11-23
is someone knows about hybrid or switchable graphics !??

---

### Post by QIII on 2012-11-23
It is almost certainly muxed.  Mux-less setups showed up with the HD 6XXX series ATI hybrids.

vga-switcheroo is your only option, and it is not guaranteed to work.

Please do not bump your thread so quickly.  Give it 24 hours.  Remember the community is worldwide and your post may not be seen right away.

---

### Post by snifer7 on 2012-11-24
> **QIII said:**
> It is almost certainly muxed.  Mux-less setups showed up with the HD 6XXX series ATI hybrids.
vga-switcheroo is your only option, and it is not guaranteed to work.
Please do not bump your thread so quickly.  Give it 24 hours.  Remember the community is worldwide and your post may not be seen right away.

ok , sorry
i am using a program written by benjamim gois (VGAsw)
when i press high performance lightdm do restart and the garphic card changes to : Gallium , so is it means that i'm doing right ?

i know that in mux-less systems IGP connected to displays and descrete graphic only do rendering.

i read in x.org that X server doesnt support hybrid graphics :
**"At the moment the X server does not support rendering and display from different cards so the discrete card can not be used with MUX-less systems at the moment."**

so the question is how [this guide]("http://ubuntuforums.org/showthread.php?t=1930450") helps when X server does not support !!!!??? how it works?
plz explain what happens

thanks :)

---

