---
title: "[General] Advanced Terminal Output"
date: 2010-11-03
forum: Programming Talk
---

### Post by Pyro.699 on 2010-11-03
Hey,

So i know about a few functions that are out there that can do some different tasks when sent to the command prompt or terminal. The 2 that i know of are:

[php]
ESC = chr(27) //Hex code: 1B

ClearLine = ESC + "[2K"+ ESC +"[G" //Which clears the current line
//And
ClearScreen = ESC + "[0" + ESC + "[2J" //Which clears the whole screen
[/php]

The question i have for you is.... What do those mean exactly? Those cant be it and i would like to learn what kind of format they are in so I'm able to make different ones. I would use google but im not exactly sure what this process is called or even where i should begin ^^

Thanks
~Cody

---

### Post by spjackson on 2010-11-03
> **Pyro.699 said:**
> 
So i know about a few functions that are out there that can do some different tasks when sent to the command prompt or terminal. The 2 that i know of are:

[php]
ESC = chr(27) //Hex code: 1B

ClearLine = ESC + "[2K"+ ESC +"[G" //Which clears the current line
//And
ClearScreen = ESC + "[0" + ESC + "[2J" //Which clears the whole screen
[/php]The question i have for you is.... What do those mean exactly? Those cant be it and i would like to learn what kind of format they are in so I'm able to make different ones. I would use google but im not exactly sure what this process is called or even where i should begin ^^

Thanks
~Cody
Those codes might well do what you think they do on the particular terminal you are using, but they might not be the right thing to use on other terminal types.

The ncurses library is portable across different terminal types and uses the terminfo database (used to be termcap a long time ago) to find the right codes for a particular function.

The terminfo database installed on Linux is in compiled form (not human readable), but you can get the sources for these. (I'm not sure which package without searching.)

"man terminfo", "man tput" should get you started. e.g. this will show you the codes for your current terminal to position the cursor at top left.
```

tput cup 0 0 | od -c

```

---

### Post by worksofcraft on 2010-11-03
These are terminal control strings: special sequences, usually starting in the ESC character that would make old fashioned serial line terminals do special actions like clear the screen, or move the cursor.

Usually one strives for vt100 compatibility which was a very basic model.

If you type the command infocmp it will show you all the escape strings that your terminal understands, but the syntax is a bit obscure and you will have to google "terminfo" or "termcaps" if you want to learn all about it.

p.s. a good place to start is the [standard ansi escape sequences]("http://en.wikipedia.org/wiki/ANSI_escape_code") wiki

---

