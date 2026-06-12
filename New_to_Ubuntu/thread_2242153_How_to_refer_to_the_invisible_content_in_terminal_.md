---
title: "How to refer to the invisible content in terminal mode?"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by Maverickor on 2014-08-30
When turning my ubuntu into command-line mode (via <Ctrl+Alt+F6>), I cannot use the mouse to refer to the invisible contents above. How can I do that with keyboard alternatively?

---

### Post by grahammechanical on 2014-08-30
I think that you are referring to a Linux command printout on screen that is more than one screen full of information. so, that some or much of the information disappears off screen. I think that you need to understand the Linux pipe command and its use with the less command.

> [COLOR=#000000][FONT=monospace]A very simple example of the benefits of piping is provided by the [*dmesg*]("http://www.linfo.org/dmesg.html") command, which repeats the startup messages that scroll through the [*console*]("http://www.linfo.org/console.html") (i.e., the all-text, full-screen display) while Linux is [*booting*]("http://www.linfo.org/boot.html") (i.e., starting up). dmesg by itself produces far too many lines of output to fit into a single screen; thus, its output scrolls down the screen at high speed and only the final screenful of messages is easily readable. However, by piping the output of dmesg to the filter *less*, the startup messages can conveniently be viewed one screenful at a time, i.e.,[/FONT][/COLOR][INDENT]dmesg | less
[/INDENT]
[COLOR=#000000][FONT=monospace]less allows the output of dmesg to be moved forward one screenful at a time by pressing the SPACE bar and back one screenful at a time by pressing the *b* key. The command can be terminated by pressing the *q* key. (The *more* command could have been used here instead of less; however, less is newer than more and has additional functions, including the ability to return to previous *pages*of the output.)[/FONT][/COLOR]


[http://www.linfo.org/pipes.html](http://www.linfo.org/pipes.html)

Regards.

---

