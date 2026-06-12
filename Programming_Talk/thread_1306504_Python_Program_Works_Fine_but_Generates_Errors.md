---
title: "Python: Program Works Fine but Generates Errors"
date: 2009-10-30
forum: Programming Talk
---

### Post by Penguin Guy on 2009-10-30
I'm new to python and made a short program that allows you to move around a box, the only thing wrong with it is that it spews out some random errors every time I run it - what do they mean? 

**[ERRORS]**
```

Traceback (most recent call last):
  File "./pybox", line 38, in <module>
    curses.wrapper( main )
  File "/usr/lib/python2.6/curses/wrapper.py", line 44, in wrapper
    return func(stdscr, *args, **kwds)
  File "./pybox", line 35, in main
    screen.addstr( y , x , '#' )
KeyboardInterrupt

```
Although it looks like there are multiple errors above, there is only one, [COLOR="Red"]KeyboardInterrupt[/COLOR], the rest it is just debug information. We can fix this by adding a better way of exiting the program than just pressing Ctrl+C:
```
if char == 113:  # q
	exit()
```



**[ERROR: If I go into the bottom right corner]**
```

_curses.error: addstr() returned ERR

```
The reason I got this error was because after printing a character, it would move the cursor to the right (outside of the window).
Fixes:
[LIST]
[*]Put the [COLOR="Green"]addch[/COLOR] command in a [COLOR="green"]try ... except[/COLOR] statement *- this is what I've done in the code below*
[*]Don't allow the player to move there
[*]Hack the curses library
[/LIST]



**[PYTHON]**
[PHP]
#!/usr/bin/python

import curses
import curses.wrapper
import random

def main(screen):
	( screen_height , screen_width ) = screen.getmaxyx()

	x = random.randrange( 0 , screen_width )
	y = random.randrange( 0 , screen_height )

	try: screen.addstr( y , x , '#' )
	except curses.error: pass
	screen.move( 0 , 0 )  # Keep the cursor out of the way

	while 1:
		oldx = x
		oldy = y

		char = screen.getch()

		if char == 113:  # q
			exit()
		if char == curses.KEY_RIGHT:
			x = x+1
		if char == curses.KEY_LEFT:
			x = x-1
		if char == curses.KEY_UP:
			y = y-1
		if char == curses.KEY_DOWN:
			y = y+1

		( screen_height , screen_width ) = screen.getmaxyx()

		# If character is in illegal position, move it:
		if x > screen_width-1:
			x = screen_width-1
		elif x < 0:
			x = 0
		if y > screen_height-1:
			y = screen_height-1
		elif y < 0:
			y = 0

		# If character has moved, redraw it:
		if x != oldx or y != oldy:
			try: screen.addstr( oldy , oldx , ' ' )
			except curses.error: pass
			try: screen.addstr( y , x , '#' )
			except curses.error: pass
			screen.move( 0 , 0 )  # Keep the cursor out of the way

curses.wrapper( main )
[/PHP]


Thanks to everyone to helped!

---

### Post by Can+~ on 2009-10-30
I discovered something.

If you expand the terminal window, then you hit the boundry, but don't get any errors.

If you make the window smaller, it errors before.

So it seems this error is raised, whenever a character is being put outside the visible margin.

---

### Post by Penguin Guy on 2009-10-31
> **Can+~ said:**
> I discovered something.

If you expand the terminal window, then you hit the boundry, but don't get any errors.

If you make the window smaller, it errors before. 

So it seems this error is raised, whenever a character is being put outside the visible margin.
Thanks, I've fixed that now. However it still creates the same error if you go into the bottom right corner, which I can't understand.

---

### Post by dwhitney67 on 2009-10-31
When you add a character, or a string, to a position at the "edge" (ie [screen_width,screen_height]) of the screen, the cursor gets placed right after it.  This is throwing an exception, which you are not catching.  Hence the reason your program ends in disgrace.

Here's a modified version of your code, where I have attempted to remove redundancies in the code in an effort to streamline it, and also to handle the error(s) described above.
```

#!/usr/bin/python

import curses
import curses.wrapper
import random
import console

def main(screen):
    (screen_width, screen_height) = console.getTerminalSize()

    x = random.randrange( 0 , screen_width )
    y = random.randrange( 0 , screen_height )

    screen.addch( y , x , '#' )
    screen.move( 0 , 0 )

    while 1:
        oldx = x
        oldy = y

        char = screen.getch()

        # In case the user changes the screen size
        (screen_width, screen_height) = console.getTerminalSize()

        if char == curses.KEY_RIGHT and x < screen_width-1:
            x = x+1
        elif char == curses.KEY_LEFT and x > 0:
            x = x-1
        elif char == curses.KEY_DOWN and y < screen_height-1:
            y = y+1
        elif char == curses.KEY_UP and y > 0:
            y = y-1
        else:
            continue

        if oldx == x and oldy == y:
            continue

        # Redraw the character in the new position
        try: screen.addch( oldy , oldx , ' ' )
        except curses.error: pass
        try: screen.addch( y , x , '#' )
        except curses.error: pass

        screen.move( 0 , 0 )  # Keep the cursor out of the way

curses.wrapper( main )

```

---

### Post by nvteighen on 2009-10-31
First, you don't need the console module. Use screen.getmaxyx()... which does exactly the same and it's from curses itself.

Second, the occurs when the condition is (x = screen_width - 1 and y = screen_height - 1). I've been checking the code but I can't see anything that may crash only on that specific situation...

Third, you aren't refreshing your screen. That's a fatal mistake.

This doesn't work yet, but reflects the changes I tell you.
```

#!/usr/bin/python

import curses
import random

def main(screen):
        # curses.nonl() ???
        (screen_height, screen_width) = screen.getmaxyx()
        x = random.randrange(0, screen_width)
        y = random.randrange(0, screen_height)
        screen.addch(y, x, '#')
        screen.move(0, 0)

        while True:
                screen.refresh()
                oldx = x
                oldy = y
                char = screen.getch()
                if char == curses.KEY_RIGHT:
                        if x < screen_width - 1:
                                x = x+1
                elif char == curses.KEY_LEFT:
                        if x > 0:
                                x = x-1
                elif char == curses.KEY_UP:
                        if y > 0:
                                y = y-1
                elif char == curses.KEY_DOWN:
                        if y < screen_height - 1:
                                y = y+1

                (screen_height, screen_width) = screen.getmaxyx()

                # If character is in illegal position, move it:
                if x > screen_width - 1:
                        x = screen_width-1
                elif x < 0:
                        x = 0

                if y > screen_height - 1:
                        y = screen_height-1
                elif y < 0:
                        y = 0

                # If character has moved, redraw it:
                if x != oldx or y != oldy:
                        if (oldx >= 0 and oldx < screen_width and 
                            oldy >= 0 and oldy < screen_height):
                                screen.addch(oldy, oldx, ' ')

                screen.addch(y, x, '#')
                screen.move(0, 0)  # Keep the cursor out of the way

curses.wrapper(main)

```

---

### Post by dwhitney67 on 2009-10-31
> **nvteighen said:**
> First, you don't need the console module. Use screen.getmaxyx()... which does exactly the same and it's from curses itself.

I tried this; it resulted in an un-handled exception on the very first addch() call.

> 
Second, the occurs when the condition is (x = screen_width - 1 and y = screen_height - 1). I've been checking the code but I can't see anything that may crash only on that specific situation...


See my post; it answers this.

---

### Post by nvteighen on 2009-11-01
> **dwhitney67 said:**
> I tried this; it resulted in an un-handled exception on the very first addch() call.


That's because the window.getmaxyx() method returns (height, width), the inverse of what console.getTerminalSize() returns: (width, height).

Honestly I didn't notice your post... :P What I don't like too much from your solution is that you're actually just bypassing the error with an exception... I guess there's another way, though as I can't think of any alternative, yours is oficially the best available right now ;)

---

### Post by dwhitney67 on 2009-11-01
> **nvteighen said:**
> That's because the window.getmaxyx() method returns (height, width), the inverse of what console.getTerminalSize() returns: (width, height).

:D  That explains it!

> 
I guess there's another way, though as I can't think of any alternative, yours is oficially the best available right now ;)

It's because of the leading cursor that "falls" off the edge of the screen.  If that could be prevented, then the issue would go away.  An alternative would be to exclude the line before the bottom edge, thus creating a "null" zone.

Anyhow, if you want to see the cursor position, just comment out the move() function call at the end of the while-loop.

---

### Post by Penguin Guy on 2009-11-01
@ dwhitney67:
The except works well - I've included it in my code. However your 'streamlining' broke the ability to resize the terminal window.

@ nvteighen:
I've updated my code to use screen.getmaxyx, but I don't understand what refreshing the screen does, or why it's important.

---

### Post by dwhitney67 on 2009-11-01
> **Penguin Guy said:**
> @ dwhitney67:
The except works well - I've included it in my code. However your 'streamlining' broke the ability to resize the terminal window.


Recheck my post again; I believe I fixed that issue (with a post-edit yesterday).  I have tested my change and it works.

---

### Post by Penguin Guy on 2009-11-01
> **dwhitney67 said:**
> Recheck my post again; I believe I fixed that issue (with a post-edit yesterday).  I have tested my change and it works.
I tested it and it doesn't work: When you move to the bottom edge, then resize the terminal so that it's vertically smaller, the # is still at the bottom edge (as expected). But then if you press the up arrow, the # disappears.

---

### Post by dwhitney67 on 2009-11-01
> **Penguin Guy said:**
> I tested it and it doesn't work: When you move to the bottom edge, then resize the terminal so that it's vertically smaller, the # is still at the bottom edge (as expected). But then if you press the up arrow, the # disappears.

You're right; I only tested by making the terminal bigger.  I neglected to test the other possibility.  Thus the code I posted has a deficiency.  It seems your updated code meets the requirements.

Btw, update your code to use if-elif statements when checking the user's inputted value.  Right now you use if-statements only, and obviously if the user presses the down-arrow, it cannot also be the up-arrow, left-arrow, right-arrow (etc).

Also, if you are done with the thread, mark it as closed.

---

### Post by Penguin Guy on 2009-11-01
Although everything works as expected, I'm still getting the errors described in the first post.

---

### Post by dwhitney67 on 2009-11-01
> **Penguin Guy said:**
> Although everything works as expected, I'm still getting the errors described in the first post.

I re-copied your code from the original post, and re-ran it; it does not produce the errors anymore.

Are you still getting these errors, or are you merely trying to understand them?  If the latter, I explained in an earlier post that it is the result of attempting to display the cursor at a position that is not within your window's boundaries.  This error is still occurring, however this time with the modified code, you are handling that exception (and ignoring it).

If you want to see the behavior of the cursor after each arrow-key entry, remove the move() function call within the while-loop.  When you move the # to the lower-right edge of the screen, the cursor has nowhere to go... but off the screen.

---

### Post by Penguin Guy on 2009-11-02
@ dwhitney67

When I run it I get the output below, the red-highlighted parts I am assuming are non-fatal errors, whatever they are, I want to know why they're there.
```
$ ./pybox.py 
Traceback (most recent call last):
[COLOR="Red"]  File "./pybox.py", line 51, in <module>
    curses.wrapper( main )
  File "/usr/lib/python2.6/curses/wrapper.py", line 44, in wrapper
    return func(stdscr, *args, **kwds)
  File "./pybox.py", line 20, in main
    char = screen.getch()[/COLOR]
KeyboardInterrupt
```

---

### Post by Can+~ on 2009-11-02
[FONT="Courier New"]KeyboardInterrupt[/FONT] is raised when you do Ctrl+C (I'm guessing you're exiting the app this way).

If you want to make it close "gracefully", add a global try..except that will catch it and terminate the application.

---

### Post by nvteighen on 2009-11-02
> **Penguin Guy said:**
> 
@ nvteighen:
I've updated my code to use screen.getmaxyx, but I don't understand what refreshing the screen does, or why it's important.

I'm not sure how Python ncurses handles refreshing, but if you were doing this in C ncurses (i.e. the original library), your program wouldn't be showing **any** update after the initial state. ncurses works by writing stuff to a temporary screen and then dumping that temporary screen's contents to the current screen or "stdscr". Maybe Python does refreshing automatically, but I assure I have never heard about such a design in Python ncurses and I've used this module a lot... so it's probable that your program is refreshing by chance just because of some weird side-effect from some procedure.

---

### Post by Penguin Guy on 2009-11-03
> **Can+~ said:**
> [FONT="Courier New"]KeyboardInterrupt[/FONT] is raised when you do Ctrl+C (I'm guessing you're exiting the app this way).

If you want to make it close "gracefully", add a global try..except that will catch it and terminate the application.
I'm fine with that, but want to know about the bit I **[COLOR="Red"]highlighted in red[/COLOR]**:
```

[SIZE="1"]$ ./pybox.py 
Traceback (most recent call last):[/SIZE]
[B][COLOR="Red"]  File "./pybox.py", line 51, in <module>
    curses.wrapper( main )
  File "/usr/lib/python2.6/curses/wrapper.py", line 44, in wrapper
    return func(stdscr, *args, **kwds)
  File "./pybox.py", line 20, in main
    char = screen.getch()[/COLOR][/B]
[SIZE="1"]KeyboardInterrupt[/SIZE]

```

---

### Post by nvteighen on 2009-11-03
If I were you, I'd start coding a way to exit... like typing 'q' or whatever. If you do Ctrl+C, you'll always get the KeyboardInterrupt exception and catching that generically through

```

try:
    curses.wrapper(main)
except KeyboardInterrupt:
    pass

```

though that's possible it reveals you haven't designed a proper way to exit the program. Make main() return after typing something or some other event.

---

### Post by Can+~ on 2009-11-03
> **Penguin Guy said:**
> I'm fine with that, but want to know about the bit I **[COLOR="Red"]highlighted in red[/COLOR]**:
```

[SIZE="1"]$ ./pybox.py 
Traceback (most recent call last):[/SIZE]
[B][COLOR="Red"]  File "./pybox.py", line 51, in <module>
    curses.wrapper( main )
  File "/usr/lib/python2.6/curses/wrapper.py", line 44, in wrapper
    return func(stdscr, *args, **kwds)
  File "./pybox.py", line 20, in main
    char = screen.getch()[/COLOR][/B]
[SIZE="1"]KeyboardInterrupt[/SIZE]

```

Again, is the same Keyboad interrupt, the red part indicated where it happend first:

[PHP]#!/usr/bin/env python

input("This is the first input>")

input("This is the second input>")

input("This is the third input>")[/PHP]

[PHP]This is the first input>
This is the second input>^C
Traceback (most recent call last):
  File "asdf.py", line 5, in <module>
    input("This is the second input>")
KeyboardInterrupt
[/PHP]

---

### Post by Penguin Guy on 2009-11-04
> **Can+~ said:**
> Again, is the same Keyboad interrupt, the red part indicated where it happend first:

[PHP]#!/usr/bin/env python

input("This is the first input>")

input("This is the second input>")

input("This is the third input>")[/PHP]

[PHP]This is the first input>
This is the second input>^C
Traceback (most recent call last):
  File "asdf.py", line 5, in <module>
    input("This is the second input>")
KeyboardInterrupt
[/PHP]
Ahh I see, so it's basically just debug information, I've marked this topic as solved and updated the first post to show what I've learnt from this topic. Thanks for the help all of you!

---

