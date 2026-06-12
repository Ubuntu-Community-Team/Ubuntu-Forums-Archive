---
title: "devkitadvance help"
date: 2006-06-11
forum: Programming Talk
---

### Post by grimdaze on 2006-06-11
So I'm following [this]("http://home.no/neogeo/HOVEDSIDE_INDEX/GBA_HOVEDSIDE_INDEX_ENGELSK/index.html") gameboy advance development tutorial.
I need the linux equivalent to 
> 1 Open notepad
2 Write this:
  path=c:\devkitadv\bin
  gcc  -o Test.elf Test.cpp  -lm
  objcopy -O binary Test.elf Test.bin
3 Store this file as Make.bat
from Lesson 1.
My devkitadv directory is located at /home/grimdaze/devkitadv/bin so I went a head and made a Make.bat with the contents
> path=/home/grimdaze/devkitadv/bin
gcc -o test.elf test.c  -lm
objcopy -O binary test.elf test.bin
and ran it with sh Make.bat. It all seemed to compile ok(the first gba program from Lesson 3) but I didn't get the red screen when I loaded it into visualboyadvance so I'm assuming that something isn't going right here.

Any help? Sorry if I'm not being clear enough.

---

