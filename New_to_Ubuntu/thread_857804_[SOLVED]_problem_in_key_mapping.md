---
title: "[SOLVED] problem in key mapping"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-07-12
I think I have found a bug. Please correct me I you have a solution. Please try following. 
Open some text file in vim or gedit (these two are the one on which I have tried). Now press right or left arrow key and keep pressed. Now press Ctrl key with your arrow key pressed. 
Congratulation you have hanged your keyboard.
On my laptop no key works except Alt+Ctrl+F1, Alt+Ctrl+backspace after this event.
Please provide me a solution for this which does not envolve restarting gdm.

---

### Post by Dr Small on 2008-07-12
It doesn't happen with my system.

---

### Post by _sphinx_ on 2008-07-12
I have tried this on two of my systems. And both of them yielded same results.

---

### Post by Bodsda on 2008-07-12
Please try to recreate and double check your instructions, this does 'not' hang my keyboard!!

/me wants a hung keyboard....

---

### Post by _sphinx_ on 2008-07-12
I just tried it one more time and unfortunately I have to relogin.

---

### Post by madsmeg on 2008-07-12
you say you tried with 2 systems, did you use the same keyboard?

---

### Post by unutbu on 2008-07-12
I doesn't happen on my system either. 

Does the hanging problem occur only in gedit and vim, or does it happen with any app?

---

### Post by rraj.be on 2008-07-12
It nothing wrong with any of our system Amit.

I think it may be some other bug.

---

### Post by _sphinx_ on 2008-07-12
Why is this happeing on my laptop. Any clue anybody?

---

### Post by _sphinx_ on 2008-07-12
I have tried changing keyboard. I have used three keyboard till now. Same results.

---

### Post by _sphinx_ on 2008-07-12
First I tried this for vim on my PC in lab, which is intel R dual core with hardy. 
Today I tried this on my laptop with intel core 2 duo with hardy, first for vim and then for gedit.
Just now while replying for this in firefox I tried, and it happened again.
My cursor just vanishes after pressing Ctrl (keeping arrow key pressed).
Each time I have to restart gdm.

---

### Post by unutbu on 2008-07-12
What window manager are you using?
Have you set any keyboard shortcuts? (Check System>Preferences>Keyboard shortcuts)
Are you using Compiz? (If so, perhaps try turning it off just to see if it is related to the problem).

---

### Post by _sphinx_ on 2008-07-12
I am using gnome with no compiz running. I don't have any shortcut which envolves only Ctrl and arrow key. 
My mouse works fine even after this. And I have found that scrolling on firefox after this event changes the font size which gives the hint of Ctrl key remaining pressed.

---

### Post by _sphinx_ on 2008-07-12
Hurray, I found the trick.
If you turn on the "Show the pointer when the Control key is pressed" in mouse preferences, this event will occur, please confirm this by trying.
I just turned that thing off and all is fine now.
:guitar:

---

### Post by unutbu on 2008-07-12
Glad you fixed it!

---

### Post by kansasnoob on 2008-07-12
> **_sphinx_ said:**
> Hurray, I found the trick.
If you turn on the "Show the pointer when the Control key is pressed" in mouse preferences, this event will occur, please confirm this by trying.
I just turned that thing off and all is fine now.
:guitar:

So mark it solved! I was trying to duplicate your problem with no luck.

---

### Post by _sphinx_ on 2008-07-12
Did you guys tried this thingy after turning on the "Show the pointer when the Control key is pressed" in mouse preferences. I am excited to see that this happens on yours boxes also.
:lolflag:

---

### Post by Dr Small on 2008-07-12
> **_sphinx_ said:**
> Did you guys tried this thingy after turning on the "Show the pointer when the Control key is pressed" in mouse preferences. I am excited to see that this happens on yours boxes also.
:lolflag:
Haven't got Ubuntu nor Gnome, so I can't try it. If it really is a bug though, you all could report it.

---

### Post by _sphinx_ on 2008-07-12
> **Dr Small said:**
> Haven't got Ubuntu nor Gnome, so I can't try it. If it really is a bug though, you all could report it.
Yes but first I have to confirm that this thing happens on other boxes also.

---

