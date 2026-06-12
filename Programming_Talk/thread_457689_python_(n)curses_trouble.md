---
title: "python (n)curses trouble"
date: 2007-05-28
forum: Programming Talk
---

### Post by DirtDawg on 2007-05-28
I have been working on a 'learning' project in Python using the [curses module]("http://docs.python.org/lib/module-curses.html"). I have created a mainscreen (stdscr), then a smaller window on that called win2. I've created a coordinate system and I'm trying to get string characters to print on win2 in corrispondance to the coordinates system. 

```

##this is psuedo code, just to get the idea across##
class win2:
    def__init__(self):
        self.rows= 20 
        self.cols= 64

    def drawstuff(self):
        for y in range(self.rows):
            for x n range(self.cols):
                win2.addstr(y, x, '.')


```
This should produce a grid of '.'s 20 rows deep and 64 columns across, covering the whole of win2. However, when I run the code, I get the enormously uninformative error:
```
 _curses.error: addstr() returned ERR
```
If I trim the cols back to 63, the error disappears, but my window is missing the last column of characters, so it seems to me this is likely the equivalent of an IndexError(out of range). But I dont understand why!!?
 
This the code I used to create win2. It should read "20 rows, 64 columns, start y=0(top left corner), start x=1(1 character to the right of the left edge of the screen):
```
win2= curses.newwin(20, 64, 0, 1)
```

The only thing I can think of is that somehow starting win2 at x=1 is screwing something up? I don't see how, though, since I thought the x-start-position was relative to the base screen (stdscr), and not itself?

Any ideas why things are behaving this way or how to fix it? 
Thanks.

---

### Post by DirtDawg on 2007-05-29
Changing the line 
```
win2= curses.newwin(20, **64**, 0, 1)
```
to
```
win2= curses.newwin(20, **65**, 0, 1)
```
fixes the problem, but I have absolutely no idea why.

If anyone happens to have a clue, please enlighten me.

---

### Post by carrara47 on 2007-08-17
Try this

```

try:
       win2.addstr(y, x, '.')
except curses.error:
       pass

```

Curses raises an error if you add a char or a string in the position (19,63) to notify the ending of win2.
Anyway, although it raises an error, it adds the char in that position.

Bye

---

