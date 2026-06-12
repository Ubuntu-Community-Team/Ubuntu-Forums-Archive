---
title: "Building an snes emulator..."
date: 2012-03-22
forum: Programming Talk
---

### Post by roelforg on 2012-03-22
...and the documentation-shortage is getting an problem.

Preface:
I was always interested in emulation.
So after (successfully) programming emulators for several game consoles (and some other stuff),
i wanted to create one able to play an alltime favorite of mine:
Super Mario World and Super Mario Bros.
So i needed either 2 emulators or 1 snes emulator that can do both.
So after finding out that the SNES is the best documented system,
i decided to use the SNES.

Problem:
However,
i'm having problems finding documents regarding the SNES memory layout, stack, gfx and addressing modes.
I do, however, have build in enough abstraction between the virtual CPU and memory to allow me to continue implementing opcodes.
Currently my emu assumes code starts at 0x0000 and implements only direct,implicit and immidiat addressing (though the direct is just what you feed in as i didn't find any docs describing what is was, so i don't get how it's different from the direct mem).
My overal plan is:
1. get a 65c816 cpu emulated in full
2. get the gfx implemented (problem...)
3. load roms (i'm still figuring out how you get the offsets)

Anybody any docs or stuff?
I'll use this thread for any problems i can't solve myself and need help with so anyone with the same problems doesn't have to search all over.

---

### Post by CynicRus on 2012-03-23
[http://sourceforge.net/directory/language:c/os:linux/freshness:recently-updated/?q=NES]("http://sourceforge.net/directory/language:c/os:linux/freshness:recently-updated/?q=NES")

[http://en.wikibooks.org/wiki/Category:Super_NES_Programming]("http://en.wikibooks.org/wiki/Category:Super_NES_Programming")

---

### Post by roelforg on 2012-03-23
I don't get how the first one's gonna help me...
The second one does.
The memory diagram issue is solved [X]

Thx

Ps. For some reason the snes has addressing modes not in the cpu manual.

EDIT:
I thought it was odd that i missed that wikibooks as it showed on my phone (where i viewed the response).
Now i'm back at my desktop and it's gone! In a hunch i check adblock...
Turns out adblock was blocking the url... Woops...

---

