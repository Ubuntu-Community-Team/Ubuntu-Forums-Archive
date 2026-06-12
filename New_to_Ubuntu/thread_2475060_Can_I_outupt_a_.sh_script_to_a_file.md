---
title: "Can I outupt a .sh script to a file?"
date: 2022-05-15
forum: New to Ubuntu
---

### Post by Complete on 2022-05-15
I just ran a .sh prebuild file that built a lot of stuff.  There were some highlighted issues that came across the screen in bold.  I wish I could have saved all that data to a file.  Preferably, it would be great to ouptut it to HTML so showcase the bold and hilighted warnings.  In Windows command-line it is done by simpuly using the '>' character to putut a comandline entry to an output file.

---

### Post by GhX6GZMB on 2022-05-15
Sure.
> works in Linux as well. But not as html.

---

### Post by him610 on 2022-05-15
Complete,

Not 100% sure about this, but I think the answer you are looking for may be found here...
```

man bash

```
Look for "Redirecting..."

---

### Post by Holger_Gehrke on 2022-05-15
A better option is to pipe the command through 'tee'.
```

my_stupidly_complex_and_long_running_script | tee output.txt

```
This way the output goes to the screen **and** to output.txt.

The command 'script' allows capturing input and output and playing things back with accurate timing with 'scriptreplay'. See 'man script' for details. The terminal multiplexers 'screen' and 'tmux' also have options for saving the content of a terminal buffer to a file. Again, the respective manual pages have the details.

Also, the output your program did is not lost until you close the terminal (or reset it). There are several hundred lines of scroll-back buffer and most terminal programs have an option to set the size of that buffer. You could mark the interesting part of the output, right click and select 'copy' or even - if your terminal offers it - 'copy as HTML' (I know xfce4-terminal on XUbuntu has that option, not sure about gnome-terminal) and then paste it into your editor of choice for saving. And speaking of xfce4-terminal: there's a menu-item 'Terminal' -> 'Save Content' which I am rather sure gnome-terminal doesn't have.

Holger

---

### Post by GhX6GZMB on 2022-05-15
First time in my life that I've ever heard of "tee". Thanks.

---

### Post by GhX6GZMB on 2022-05-15
@Complete:
This may be helpful:
[https://www.howtogeek.com/439199/15-special-characters-you-need-to-know-for-bash/](https://www.howtogeek.com/439199/15-special-characters-you-need-to-know-for-bash/)

---

