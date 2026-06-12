---
title: "Z80 Assembly in Linux?"
date: 2008-01-20
forum: Programming Talk
---

### Post by Yes on 2008-01-20
I'd like to do some Z80 assembly programming for my TI-83+.  I tried using the Z80asm program in Synaptic but it always says there's something wrong with my code.  I think I remember doing something before compiling the code with TASM in Windows, so I think that might be the problem.  So, how do you all write Z80 programs in Linux?

Here's the code, if you think it might be a problem there:

```
#define B_CALL(xxxx) rst 28h \ .dw xxxx
#define B_JUMP(xxxx) call 50h \ .dw xxxx

_clrlcdfull =4540h
_homeup =4558h

	.org 9D95h
	B_CALL(_homeup)
	B_CALL(_clrlcdfull)
	ret

.end
END
```

The errors are all

```
error: command or comment expected (was _homeup =4558h )
```

It has an error for all the lines of code except for ret and END.

---

### Post by breaking on 2008-01-20
Did you include the ti83-plus include file?

---

### Post by Yes on 2008-01-20
No, how do I do that?  Do I need to get the file from anywhere?

Does anyone also have a Linux equivilant for TI-Connect for Linux?

---

### Post by chickendude on 2012-08-17
I know it's a bit late, but in case anyone else stops by...

Now there are a bunch of tools and resources for z80 (and 68k) calculator programming on Linux.

For starters, there's the Wabbit suite of tools, particularly spasm (a replacement for TASM):
[http://wabbit.codeplex.com/releases/view/45088](http://wabbit.codeplex.com/releases/view/45088)

There's also a Linux IDE (no longer under development):
[http://wabbit.codeplex.com/releases/view/45275](http://wabbit.codeplex.com/releases/view/45275)

And a native Linux emulator (still under development) with lots of features: screenshots, a nice debugger, grayscale emulation, etc.:
[http://lpg.ticalc.org/prj_tilem/](http://lpg.ticalc.org/prj_tilem/)

You can also run [PindurTI](http://sgate.emt.bme.hu/patai/pindurti/) through Wine just fine. I haven't had any luck with WabbitEmu, however.

And instead of TI Connect, Linux has TiLP:
[http://tilp.sourceforge.net/](http://tilp.sourceforge.net/)

For creating tilemaps/sprites, while a bit dated, CalcGS has been the standard for years and works fine under Wine:
[http://www.ticalc.org/archives/files/fileinfo/132/13274.html](http://www.ticalc.org/archives/files/fileinfo/132/13274.html)

And now there's even an online assembler, ORG:
[http://clrhome.org/asm/](http://clrhome.org/asm/)
..which can handle multi-file projects and assemble into a variety of formats (83/+ programs, applications, appvars, etc.) and an online sprite/tilemap editor, Pixelscape (though it only supports 8x8 tiles, i believe):
[http://clrhome.org/pix/](http://clrhome.org/pix/)

That should be more than enough to get you started, things are certainly much easier now than they were ten (or even five) years ago!

EDIT: And to include a file you would write *#include "ti83plus.inc"* at the top of your program. You can find it [here]("http://brandonw.net/calculators/OS2/browser/trunk/extras/ti83plus.inc"). And while your program will start running at $9D95, assembly programs for the 83+ need to start with the AsmPrgm token. The start of a regular 83+ assembly program usually looks like this:
.org $9D93 ;$9D95-2, because the AsmPrgm token takes up two bytes
.db t2ByteTok, tasmCmp

---

