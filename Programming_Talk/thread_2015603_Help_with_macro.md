---
title: "Help with macro"
date: 2012-07-03
forum: Programming Talk
---

### Post by spanlength1 on 2012-07-03
I need to implement a macro for a byte x , which is represented by 

0        1       2       3         4      5        6       7
blink bg red bg green bg blue intensity fg red fg green fg blue

Each of the bits is having this attribute . I need to implement 3 macros
```

#ifndef TEXTMODE_H
#define TEXTMODE_H
 
 
#define T_BLINK 0x80
#define T_INTENSITY 0x08
#define T_RED 0x04
#define T_GREEN 0x02
#define T_BLUE 0x01
 
/* DESCRIPTION:
 * ------------
 * Modifies the attribute byte x by setting the attribute attr. If the attribute
 * is already set, the attribute byte remains unchanged.
 *
 * The attribute bytes are defined in the beginning of this header file.
 *
 * ARGUMENTS:
 * ------------
 * x: the attribute byte.
 * attr: the attribute bit to set as active (1).
 *
 */
#define SETATTR(x, attr) ((x) |= (attr))
 
 
 
 
 
/* DESCRIPTION:
 * ------------
 * Modifies the attribute byte x by setting the foreground and background color.
 *
 * This has no effect on the blink and intensity bits or the color bits already
 * set. For example, if the color is already red and SETCOLOR is used to set the
 * color to be green, then the attribute byte has both red and green set.
 *
 * See above for the definitions for different colors (T_RED, T_GREEN, T_BLUE).
 * The same definitions are used for both foreground and background colors.
 *
 * ARGUMENTS:
 * ------------
 * x: the attribute byte.
 * bg: the background color.
 * fg: the foreground color.
 *
 */
#define SETCOLOR(x, bg, fg)((x) |= (bg | fg))
 
 
 
 
/* DESCRIPTION:
 * ------------
 * Modifies the attribute byte by setting the color bits to 0 (black color).
 * This has no effect on the blink and intensity bits.
 *
 * ARGUMENTS:
 * ------------
 * x: the attribute byte.
 *
 */
#define RESETCOLOR(x)((x) &= ~(T_GREEN | T_BLUE| T_RED))
 
 
#endif


```

My SETCOLOR macro implementation is giving wrong results. Please give a correct implementation. Also please see that others are implemented properly or not.

---

### Post by Vaphell on 2012-07-03
try shifting bg 4 places to the left (<<4)/multiplying by 16, because now bits modified by bg and fg are the same bits and bits 1,2,3 are never modified.

reset suffers from the same problem (you only reset 3 color bits out of 6), besides you don't need to bother with colors, it's enough to do x &= ( T_BLINK | T_INTENSITY )

---

