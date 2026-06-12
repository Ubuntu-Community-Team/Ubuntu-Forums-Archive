---
title: "C++ update console output instead of adding to it"
date: 2009-09-23
forum: Programming Talk
---

### Post by whoop on 2009-09-23
I have been adding output to the console via the following method
```

std::cout << "Hello World!\n";

```
This command adds new output to the console. In various tools the console content seems to be updated/changed instead of new output being added to it. An example is the command "top".

How would I go about updating console content instead of just adding new content to it?

---

### Post by TheBuzzSaw on 2009-09-23
I may be mistaken, but it sounds like you need to use ncurses.

[http://en.wikipedia.org/wiki/Ncurses](http://en.wikipedia.org/wiki/Ncurses)

---

### Post by wmcbrine on 2009-09-23
curses is a good way to go, but not necessarily the only way. (It can be overkill.)

The first thing to understand is that C++ has no conception of a screen, as a standard part of the language. Standard output could be anything -- a file, a printer -- and cout doesn't care, or know the difference.

The screen "device" itself, however, is typically a little smarter, and recognizes some commands. The most widely-implemented of these are '\r' -- the carriage return -- and '\n' -- the line feed. '\r' moves the cursor to the beginning of the line, and '\n' advances to the next line. A bare '\n' often implies a '\r', but the reverse is not true -- you can send just a '\r', and return the cursor to the beginning of the line, where you overwrite your old output with new. Many programs do this for simple status updates. Alternatively, you might send some '\b' (backspace) characters to move back just a few spaces before overwriting.

To go beyond this, you have to send control sequences that vary depending on the terminal type. That's where termcap and terminfo come in; they're databases of terminal control sequences for various capabilities, along with functions to look them up.

curses (of which ncurses is only one implementation, though the standard one in Linux) builds on terminfo. It presents you with a virtual screen, further broken up (optionally) into windows, with various commands to update them. It then takes only the changed portions, and updates the terminal, in an optimized way, using the sequences from terminfo. Oh, and it handles input, too.

---

### Post by whoop on 2009-09-24
Ok guys, this looks very helpful, thanks. I will look into this. 

If I understand it correctly the ncurses solution (provided by TheBuzzSaw) is an API that you can use to create quite complex gui solutions on the cli, and for a large part hide the complexity on how data is written and updated to the screen. It will be smart to use for more complex gui's as you could otherwise create a mess or end up writing something similar as ncurses itself. 
The "fomatting characters" solution (hope this is a good name)(provided by wmcbrine) is a very basic (possibly the most basic) way to update the cli.

For now I think I'll try the "formatting character" solution and see if it fits my needs (for now). But I will be also looking into ncurses.

Is ncurses platform independent like I can imagine the "formatting characters" are? I am just writing something small for my own linux machines but I was just wondering if using ncurses in the code would result in problems during compilation under other platforms.

---

### Post by nvteighen on 2009-09-24
> **whoop said:**
> 
Is ncurses platform independent like I can imagine the "formatting characters" are? I am just writing something small for my own linux machines but I was just wondering if using ncurses in the code would result in problems during compilation under other platforms.

ncurses is generally available by default at Unix-like systems and is available for Windows too. So there should be little issues if they happen to occur...

---

