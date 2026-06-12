---
title: "assembly program"
date: 2006-04-28
forum: Programming Talk
---

### Post by vijayanand_sodadasi on 2006-04-28
Hello!

Can somebody explain me this statement: times 510-($-$$) db 0 .  The comment says that it fills the file with 0's.  what is ($-$$)?
The program is written for NASM assembler, can you give the "as" (linux assembler) equivalent for it.

```
A minimal bootstrap
-------------------
This bootstrap just hangs:

    ; HANG.ASM
    ; A minimal bootstrap

    hang:                   ; Hang!
            jmp hang

    times 510-($-$$) db 0   ; Fill the file with 0's
    dw 0AA55h               ; End the file with AA55


```

---

### Post by fireshell on 2006-06-20
NASM has been ported to linux, just download it from the repositories. tho i cant help with $-$$ thing

---

### Post by nythrix on 2006-06-20
The code is a boot sector for a floppy disc (or maybe even a normal disc, not sure). The $-$$ is the length of the program. 
So the whole 512B sector looks like this:

|<- ($-$$) bytes of code ->|<- 510-($-$$) zero bytes ->|<- two bytes with AA55 ->|

As far as I can tell it doesn't really need to be there. The boot attempt goes on just fine even without the 510-($-$$) and AA55 stuff. I was able to boot without them.

---

