---
title: "Sound in assembly"
date: 2011-09-07
forum: Programming Talk
---

### Post by CoffeeRain on 2011-09-07
I've read many articles and forum threads on making noise through the speaker using assembly. None of them have been in intel x86 though. Is there a way to do this using intel x86? If so, I would like to know how. Thanks.

---

### Post by cgroza on 2011-09-07
I don't know if this helps, but see if you can use the "\a" ASCII character.
I remember that it made a beep when it was sent on stdout. It may not work on all platforms though.
This works on my Arch install:
```
#include <stdio.h>

int main()
{
    printf("\a");
}

```

---

### Post by snip3r8 on 2011-09-07
> **CoffeeRain said:**
> I've read many articles and forum threads on making noise through the speaker using assembly. None of them have been in intel x86 though. Is there a way to do this using intel x86? If so, I would like to know how. Thanks.
Post the AT&T syntax for it and I'll see if i can find intel alternative.

---

### Post by CoffeeRain on 2011-09-14
OK, here is the article I read.

[http://www.intel-assembler.it/portale/5/make-sound-from-the-speaker-in-assembly/8255-8255-8284-asm-program-example.asp](http://www.intel-assembler.it/portale/5/make-sound-from-the-speaker-in-assembly/8255-8255-8284-asm-program-example.asp)

---

### Post by NathanB on 2011-09-14
> **CoffeeRain said:**
> OK, here is the article I read.

[http://www.intel-assembler.it/portale/5/make-sound-from-the-speaker-in-assembly/8255-8255-8284-asm-program-example.asp](http://www.intel-assembler.it/portale/5/make-sound-from-the-speaker-in-assembly/8255-8255-8284-asm-program-example.asp)

That code will not work on any modern Operating System ( Protected-Mode prevents user-land code from directly accessing the hardware [http://en.wikipedia.org/wiki/Protected_mode](http://en.wikipedia.org/wiki/Protected_mode) ).

The easiest approach is to use the sound functions from 'libsdl':
[http://wiki.libsdl.org/moin.cgi/CategoryAudio](http://wiki.libsdl.org/moin.cgi/CategoryAudio)

---

