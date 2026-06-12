---
title: "Using vi in Cutecom on an ARM board"
date: 2010-09-25
forum: Programming Talk
---

### Post by bertszoghy on 2010-09-25
Hello,

I am communicating via serial port from Ubuntu 10.4 to an ARM borad using Cutecom.

Everything is fine, no display issues beyond Cutecom once in a while adding a random carriage return here and there when it displays the test listing of a command.

However, I am unable to use vi. Just doing :

vi newfile
i
type a sentence
:wq

is next to impossible, I get a mess of hexadecimal symbols and only by repeating 
:quit!

am I able to exit to the prompt without any file saved.

As far as I know, the baud rate, parity, etc are fine.

Does anyone have a suggestion?

B

---

### Post by Bachstelze on 2010-09-25
Probably a wrong TERM variable. Try to find out which model of terminal Cutecom emulates, and set TERM accordingly.

---

### Post by gmargo on 2010-09-26
Have you tried using **minicom** from a terminal (or xterm) screen instead of the qt-based **cutecom**?

From cutecom's man page:
> 
 It features a lineoriented interface instead of character-oriented


---

