---
title: "Freeze in Ubuntu Gnome 3"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by ihasbedhead on 2012-03-29
------------------PROBLEM----------------
Gnome 3 freezes, apparently at random. Using Ubuntu 11.10 on Dell Studio. 
-Cursor moves
-Top dash buttons will change on mouse clicks but without effect. example: The top right "activities" button lights up with the underline but doesn't open the launcher
-Windows are unresponsive
-keyboard has no effect
-can use [$ killall] on programs, they will shut down but without fixing the problem

---------------SOLUTIONS--------------
Solutions that work but are with some problems
- [$ killall gnome] in the tty (ctrl+alt+f1) will bring the computer back to the login screen. To reenter the gui: (ctrl+alt+f7)
   -all running programs go away

-[$ gnome-shell --display :0 --replace] in the tty. Fixes the freeze, very useful and quick. It saves all the running programs. BEST METHOD I have found so far.
   -The tty can no longer be used. It initially complains about mounted externals and the has other messages. Other tty s can be used (ctrl+alt+f1 thru f6). 

If some one could help perfect these methods, it would be greatly appreciated. Thank You

---

### Post by ihasbedhead on 2012-04-26
-[$ gnome-shell --display :0 --replace&disown] in the tty. Same as other but the tty remains usable.

---

