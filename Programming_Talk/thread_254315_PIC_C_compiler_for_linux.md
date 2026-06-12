---
title: "PIC C compiler for linux"
date: 2006-09-09
forum: Programming Talk
---

### Post by rekahsoft on 2006-09-09
Hey i was wondering if there is a PIC chip C Compiler for linux...I know that C compilers for PIC chips exist but i do not know of any for linux.
Note: I would prefer OpenSource if Possable :) Thanks.

Edit: Also i would be nice if some one could let me know of a programmer (and possably an IDE that does it all). Thanks once again.

---

### Post by toojays on 2006-09-09
What device are you using? For the PIC16 and PIC18 series, the most popular Free compiler is [SDDC](http://sdcc.sourceforge.net/), although I haven't used it myself. The mid-range PICs are also supported by the GPASM toolchain, which does not include a compiler, but is worth mentioning if you hadn't heard of it before.

For the PIC30 devices, I ported Microchip's C30 toolchain back to GNU/Linux. The "support files" (header, linker scripts and libraries) are AFAIK not Free Software or redistributable, but you can find out what to do at the [Debian templates for dsPIC build toolchain 2.01](http://thread.gmane.org/gmane.comp.hardware.microcontrollers.gnupic/3768/focus=3768). Newer versions of the C30 toolchain could be ported to support the PIC33 and PIC24 devices, but nobody seems to have done this yet.

You can find out more about PICs on GNU by asking at the [GNUPIC mailing list](http://www.gnupic.org/).

---

### Post by toojays on 2006-09-09
A couple of IDEs which come to mind are [Piklab](http://piklab.sourceforge.net/index.php) and [PiKdev](http://pikdev.free.fr/). Personally I use Emacs.

---

### Post by rekahsoft on 2006-09-10
Thanks for the info...i will check into what PIC i will be using and see if i can use the information given :) I will report back.

---

### Post by rekahsoft on 2006-09-14
I am looking for a C compiler for the PIC 16F877 with a bootloader. I am looking for a circuit diagram that uses a usb serial interface to connect to the bootloader on PIC 16F877 (with device drivers).

---

### Post by rekahsoft on 2006-09-17
ok...just for the info of somebody else looking for a C Compiler for PIC chips i will report what i found: SDCC (Small Device C Compiler) which works for both PIC 16F and 18F series chips and some mcu's. More info can be found at [http://sdcc.sourceforge.net/](http://sdcc.sourceforge.net/)

---

