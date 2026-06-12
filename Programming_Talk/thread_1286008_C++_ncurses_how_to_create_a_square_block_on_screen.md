---
title: "C++ ncurses: how to create a square block on screen"
date: 2009-10-08
forum: Programming Talk
---

### Post by whoop on 2009-10-08
I am wondering how I can create a square block in the terminal using ncurses.

I found the ACS_BLOCK constant but that just gives me a "#", and even if it would be a real square it would probably be a rectangle (height being longer than width). Am I missing something? Do I need to change fonts or something?

I want to be able to create squares (preferably of different colour) on screen.
Maybe I should be using another library ?

---

### Post by wmcbrine on 2009-10-08
Yeah, ACS_BLOCK is poorly implemented for most terminals. :( There are at least two alternatives:

1. Space + A_REVERSE, or just flip the foreground and background colors.
2. If you have a Unicode-capable terminal (like Ubuntu's Gnome Terminal), try character 0x2588.

---

### Post by whoop on 2009-10-09
> **wmcbrine said:**
> Yeah, ACS_BLOCK is poorly implemented for most terminals. :( There are at least two alternatives:

1. Space + A_REVERSE, or just flip the foreground and background colors.
2. If you have a Unicode-capable terminal (like Ubuntu's Gnome Terminal), try character 0x2588.

Thanks for your response I tried to test your suggestions, but it didn't work as suspected (maybe I did something wrong):
```

#include <ncurses.h>

int main()
{
        
	char cBlock = (char)0x2588;
	initscr();

	printw("A_REVERSE: "); addch(A_REVERSE); printw("\n");
	printw("0x2588:"); addch(cBlock); printw("\n");

        refresh();
        getch();
        endwin();

	return 0;
}

```

The A_REVERSE gives me a block with "^@" inside it, 0x2588 gives me a rectangle (height is longer than width) again. You can see the attachment, a screenshot of the results.
Maybe I did something wrong, or forgot something, maybe there's another method?

---

### Post by wmcbrine on 2009-10-09
Like I said, Space + A_REVERSE, not just A_REVERSE. You're printing character 0 there. Also, printw() won't do for this.

```
addch(' '|A_REVERSE);
```

As for 0x2588, I don't understand your objection. Of course the height is greater than the width. The character cells are taller than they are wide. I thought you wanted to fill a cell... that's what ACS_BLOCK is supposed to do. If you really want it *square*, you can try printing two of them in a row. But there's no real way to guarantee a square shape, because the cell shape varies depending on the font. Or, if you want it to be square while fitting within a cell, there are other characters you can use, but they'll leave space around the character. (This can happen with 0x2588, too, depending on the font.)

---

