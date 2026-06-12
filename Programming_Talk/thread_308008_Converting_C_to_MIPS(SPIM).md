---
title: "Converting C to MIPS(SPIM)"
date: 2006-11-27
forum: Programming Talk
---

### Post by utopia14 on 2006-11-27
Hey guys I know little of C (specializing in JAVA) and my data structures course asked that I transfer this into MIPS using $a and $v registers... any help would be awesome!
#include <stdlib.h>

void *(memset)(void *s, int c, size_t n) {
    const unsigned char uc = c;
    unsigned char *su;

    for (su = s; 0 < n; ++su, --n) {
        *su = uc;
    }

    return s;
}    

void *(a_memmove)(void *dest, const void *src, size_t n) {
    char *sc1;
    const char *sc2;

    sc1 = dest;
    sc2 = src;

    if (sc2 < sc1 && sc1 < sc2 + n) {
        for (sc1 += n, sc2 += n; 0 < n; --n) {
            *--sc1 = *--sc2;
        }
    } else {
        for (; 0 < n; --n) {
            *sc1++ = *sc2++;
        }
    }

    return (dest);
}

char *(a_strcat)(char *dest, const char *src, size_t n) {
    char *s;

    for (s = dest; *s != '\0'; ++s)
        ;
    for (; 0 < n && *src != '\0'; --n) {
        *s++ = *src++;
    }

    *s = '\0';

    return (dest);
}

---

### Post by Godspeed! mux on 2006-11-27
Don't really have the time to translate this into MIPS, but here's some sites that may help a bit:

[http://en.wikipedia.org/wiki/MIPS_architecture](http://en.wikipedia.org/wiki/MIPS_architecture)
[http://www.mrc.uidaho.edu/mrc/people/jff/digital/MIPSir.html](http://www.mrc.uidaho.edu/mrc/people/jff/digital/MIPSir.html)
[http://vip.cs.utsa.edu/classes/cs2734s98/code.html](http://vip.cs.utsa.edu/classes/cs2734s98/code.html)

It shouldn't be too hard. MIPS is fairly simple.

---

### Post by utopia14 on 2006-11-27
So, this is the progress I've made for memset:

memset:
move $v1, $a0

L2:
beq $a2, $0, L3
addiu $a2, $a2, -1
lbu $v0, 0($a1)
addiu $a1, $a1, 1
sb $v0, 0($v1)
j L2

L3:
j $ra
move $va, $a0


The others seem to be quite a bit harder, but maybe you can check over this and see where my problems lie.

---

### Post by utopia14 on 2006-11-28
haha I will actually pay someone for help... I'm getting desperate and the tutoring center here is just awful.... lol anybody?

---

### Post by b1g4L on 2006-11-28
You may find that a forum dedicated to programmers is a little more helpful, given almost everyone there are coders.

Possibly try the forum over at [www.programmingforums.org](www.programmingforums.org)

---

