---
title: "Autostart programs"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by jwn-2 on 2014-02-25
I have recently installed ubuntu 13.10, and I am totally new to ubuntu, so this might sound like a stupid question.

I want some programs to autostart when I boot my computer. I have searched the forums, but could not find out how. I did find two possibilities.

1) system>preferences>autostart (or something like that). What on earth does that mean??? How do I go there??? Where is this system-thing???

2) create autostart folder in .config and copy your programs there. I have created this folder, but how in heavens name do one copy programs there??? Where is the programs anyway??? I have tried draging it from the launcher there, but it just jumps back to the launcher when released.

Pleae help!!! I would noy ask if I knew the answer (there are no such thing as a stupid question, only stupid answers).

---

### Post by deadflowr on 2014-02-25
Those methods are old and arcane.

Instead use the Start-up Applications program.
It's an actual program that comes with Ubuntu.
All you need to do is launch that program and give the autostart app a name and a command.(comment optional)
The command is whatever the command you would use to start the app if used in a terminal.

For the record, you can usually find the executable(what launches the app) in the system folder, /usr/bin.
Example, to launch firefox at start up, open the startup applications program, click add, name it firefox and make the command /usr/bin/firefox
click to save/ok and next time you start Ubuntu it'll start firefox when you log in.
 
It's actually easier to do than I can explain.

---

### Post by jwn-2 on 2014-02-25
Thanks deadflowr, I have tried that and it works. I notice that those programs now also appear in /.config/autostart/. So I could have just draged and dropped them from /usr/bin/ and that should also have worked.

---

