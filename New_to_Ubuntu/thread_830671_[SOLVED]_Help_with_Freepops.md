---
title: "[SOLVED] Help with Freepops"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-16
I've installed Freepops from Synaptic. However I can find any icon on Application or System. I also set my Hotmai incoming server   (in Evolution) as localhost:2000 but when click Send/Receive, i got this message;
Error while Fetching Mail.

Could not connect to localhost: Connection refused

Does it mean Freepops does not start yet or I need to update Lua (i've installed LUA Updater as well). If that is the case, how do i do it?

---

### Post by alexandremrj on 2008-06-19
It seems to me that freepops simply didn't install a shortcut.

See what happens when you type in a terminal:

freepops


Does it say that program is not installed or it starts to run the daemon?

If it works then you can right-click in the menus and select "edit menus" and then add that shortcut, or start it with your session

If you have question in doing this lets us know in this thread.

---

### Post by vikramaditya on 2008-06-19
Might have to use Paypops, instead.

Sorry, couldn't resist! :oops:

---

### Post by wariskampar on 2008-06-19
Actually I already solved this problem (I should marked this thread SOLVED). Freepops is good and once configured it does it job satisfactory. Steps taken:
1) Update freepops; freepops-updater-fltk
2) Run freepops; freepopsd (run in 'Run Application' because if run in terminal it will only run when terminal is on) 
3) Cofigured Evolution as per instructions.
Hope these simple steps will help anyone who read this thread. Thanks

---

