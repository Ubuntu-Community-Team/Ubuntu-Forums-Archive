---
title: "Accessing Video Directly, no Kernel Help"
date: 2011-11-19
forum: Programming Talk
---

### Post by scu-ba-de-buntu on 2011-11-19
So I have a flat binary that is pulled by emulated floppy (Dos) BootRecord and I want to be able to access video memory without any system help. I understand how to place characters in textmode using:
```

char *TextVideoMemory = (char *) 0xb8000;
...
TextVideoMemory = 
{'L','0x7','E','0x7','A','0x7','R','0x7','N','0x7','I','0x7','N','0x7','G'};
...

```

and I know VGA data is located near 0xa0000, but I am not sure what is the next step. Is it correct to assume that without any system calls, ei no kernel loaded that the screen is 320 by 200 pixels?



Thanks!

---

### Post by Liiiim on 2011-11-19
So this is without a kernel loaded at all?  And now you want to draw stuff on the screen?  This might be of some help - [http://wiki.osdev.org/Drawing_In_Protected_Mode](http://wiki.osdev.org/Drawing_In_Protected_Mode) (assuming you're in protected mode).[URL="http://wiki.osdev.org/Drawing_In_Protected_Mode"]
[/URL]

---

### Post by scu-ba-de-buntu on 2011-11-22
Thanks!

---

