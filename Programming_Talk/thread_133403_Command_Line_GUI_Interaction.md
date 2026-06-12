---
title: "Command Line GUI Interaction"
date: 2006-02-20
forum: Programming Talk
---

### Post by IanWright on 2006-02-20
I asked a question about a GUI a while back and realised it was a bit vague and probably didn't explain what I needed to do, so heres another attempt...

I'm looking to program a GUI, that directly interacts with the command line. I know this is easy in windows to integrate with DOS, but haven't got a clue how to do it in Linux, and being relativley new would appreciate any advice anyone can offer.

The typical kinda thing I'm after doing, is dragging a slider bar which in turns alters a value (such as % packet loss) and will then run a netem command and change the packet loss.

I'm very new to Linux, and only programming experience is with C, VB and a little bit of Java (which I'm not too great at! :S)

Any suggestions would be great guys, thanks!

Ian

---

### Post by dee.dw on 2006-02-20
What do you mean with interact exactly? If you use C, you can type
```
system(string);
``` where string is a char-array. It's just the same as you typed it in a terminal.

Greetings, Dee

---

### Post by Basu on 2006-02-21
If you're using KDE you might want to try an app called Kommander which allows you to create a simple GUI with a shell script as a back end

---

