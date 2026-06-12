---
title: "Bash - checking whether a specific key on keyboard is pressed."
date: 2010-06-15
forum: Programming Talk
---

### Post by marllowe on 2010-06-15
Hi,

Is there any way to check whether a specific key (e.g. 'Q') on the keyboard is pressed ?
Script will run without using console - command like 'read' or 'stty raw-echo' can't be used. 
The idea is to check directly whether specific key is pressed.
I know about /dev/input/by-path/*kbd, but I don't know how to analyze it.
[COLOR=#000000]Is there a program that works this way? :
[/COLOR]./keyboardtest q
Anser: true or false
Regards,
Artur

---

### Post by ajgreeny on 2010-06-15
Have a look and good read about **xev** which may help you, though I am not sure exactly how you could use it to do what you want.

Maybe something like ```
xev | grep 'q'
``` will do it for you; it certainly gives output to terminal only if Q is pressed, but I can't quite make out what you want.

---

### Post by marllowe on 2010-06-15
> **ajgreeny said:**
> xev | grep 'q'
[COLOR=#000000]Thank you for your reply. [/COLOR]
I already tested xev, but it captures what we introduce in a particular window, not directly check the state of the keyboard. This is not a good solution for me. I don't want to open any windows (Event tester too). I want the script to work in the background.

---

