---
title: "I can't input code into command terminal"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by muggs13 on 2013-01-21
Recently I input commands to run tor and popilo and ever since my command terminal   opens  but I can't  input any code as it's just a blank black screen. Any help would be much appreciated as google could not.
Cheers!:D

---

### Post by alexii on 2013-01-22
Which terminal program? Does xterm work (alt-f2 for run dialog, enter 'xterm')?

---

### Post by muggs13 on 2013-01-22
I'm using gnome terminal and byobu neither of which will let me input codes. 
When I  press alt f2 the dash pops up. Ctrl alt f2 brings up a full screen terminal, xterm brings up lots of codes?? 
:(

---

### Post by sudodus on 2013-01-22
Welcome to the Ubuntu Forums :-)

> **muggs13 said:**
> I'm using gnome terminal and byobu neither of which will let me input codes. 
When I  press alt f2 the dash pops up. Ctrl alt f2 brings up a full screen terminal which  asks me to login and password. Is this xterm?
:(
No, it is not xterm, but a text screen, that you can log in to an run 'any' command lines.

***ctrl + alt + F7***

will usually bring you back to the graphics screen.
--
Did you launch the commands with that particular terminal?
Can you open a new terminal that works with

***ctrl + alt + t***

Try to log out and log in again!
Reboot and see what happens!

---

### Post by muggs13 on 2013-01-24
Yes I used byobu  and logging out and rebooting didn't change a thing. :(

---

### Post by Bashing-om on 2013-01-24
What results from the key combination ctl+alt+t  ???

---

### Post by muggs13 on 2013-01-25
ctrl -alt -t brings up gnome terminal and like byobu, I can't input any codes.

---

### Post by sudodus on 2013-01-25
Go to a text screen with

***ctrl + alt + F2***

Purge gnome-terminal
```
sudo apt-get purge gnome-terminal
```
and reinstall it
```
sudo apt-get install gnome-terminal
```

Go to the graphics screen again and see if gnome-terminal will work. If not try after rebooting.

---

### Post by Impavidus on 2013-01-25
It could be that you simply have black text on a black background. Open the preferences of your terminal and check the colours.

---

### Post by muggs13 on 2013-02-02
Definitely not black text

---

### Post by sudodus on 2013-02-02
1. Can you write in a text screen?

***ctrl + alt + F2***

2. Can you write in an ***xterm*** window?

Run xterm (use the Run window to enter [FONT="Courier New"][SIZE="3"]xterm[/SIZE][/FONT]

---

