---
title: "[SOLVED] Shut-down problem"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by colintivy on 2008-07-11
Hi Folks,

I am a very new newby. Installed 8.04 from livecd on clean HD on PentIII 866 MHz 30 GB HD 256 MB memory laptop. Installation went well. Printers found but neither worked (HP845C & Canon i905D). More importantly the shut-down button brought up by button on desktop closes everything off except the computer, display says "system halted". Looked at fora, it seems that others have had similar problems but I have not been able to look at answers. Must be more stupid than I thought, work my ISP forum easily!

Colintivy

---

### Post by dracayr on 2008-07-11
open a terminal(Applications->accessories->terminal) and type

sudo shutdown now

does that shutdown the System? what about

sudo init 0

dracayr

---

### Post by aimpau on 2008-07-11
probably an ACPI problem?

---

### Post by colintivy on 2008-07-17
Hi! aimpau,
Tried various offerings in other threads of adding acpi=force which would seem to be the problem. So far efforts baulked by "unfound commands". Bios now dated which is a potential problem. Going to print all 44 pages of ubuntu wiki guide when I get the printers to behave. Printers (HP845C & Canon i905D) both apperar to be recognised but attempts to Print a Test Page result in a multitude of single line gobbldegook on 845 and an error message on screen (from 905) concerning something to do with CUPS. Any clues ?

---

### Post by MickKi on 2008-07-20
> **colintivy said:**
> Hi! aimpau,
Tried various offerings in other threads of adding acpi=force which would seem to be the problem. So far efforts baulked by "unfound commands". 

Try this:
```
sudo /sbin/shutdown -h now
```

> **colintivy said:**
> 
Bios now dated which is a potential problem. 

There's no shortcut to this - get the latest firmware upgrade for your BIOS from the OEM and flash it.

> **colintivy said:**
> 
. . .and an error message on screen (from 905) concerning something to do with CUPS. Any clues ?

What is the error then?

---

