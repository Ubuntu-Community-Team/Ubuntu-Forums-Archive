---
title: "Nautilus crashes at startup and clock gets reset"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Devesh R on 2008-05-27
Hi, I loaded ubuntu fiesty on my Mac and it was working alright until a few days ago when it started giving error messages at startup. The nautilus would crash and the error message would be to kill the bonobo activation server.
Funnily enough, even the date would be reset everytime to Fri 1st of Jan, 1904. 
So in order to get things working, what i do is to reset the date and then in the terminal i type *killall bonobo activation server* and then use Alt+F2 to start nautilus (this i learnt from the forum:)). But now this has become a recurring thing. Every morning when i start the computer i have to go through this charade of reseting the time and restarting nautilus. Can anyone please suggest a permanent solution? 

An additional constraint on my computer is that I cant have NTPdate installed because one of my friends deleted the *var/lib/apt/lists/** from the repository in a bid to help me. :) So i cant set the date on auto nor can i update/upgrade any stuff. 

 I would really like your help  on this problem. Thank you

---

### Post by sharks on 2008-05-27
Just download from [http://www.psychocats.net/ubuntu/restorenautilus.sh](http://www.psychocats.net/ubuntu/restorenautilus.sh) and save it in desktop:

and paste these in terminal one by one:

cd ~/Desktop
chmod +x restorenautilus.sh
./restorenautilus.sh

---

### Post by Devesh R on 2008-05-27
Thanks for the tip.. i did that, but now i am getting this message

[I]You're missing a Computer .desktop backup file--nothing to restore
You're missing a Nautilus .desktop backup file--nothing to restore
You're missing a folder handler .desktop backup file--nothing to restore
You're missing a Home .desktop backup file--nothing to restore
You're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.
Nautilus should now be your new default file manager in Gnome again
[/I]

Is that ok? i have not tried restarting my computer after giving these commands. Should i try that as well?

---

### Post by sharks on 2008-05-27
yes. try restarting it.

---

### Post by Devesh R on 2008-05-27
:(

---

### Post by Devesh R on 2008-05-29
Oops! opened the champagne bottle too soon!
The problem has resurfaced even after using restorenautilus and now I am back to square one.

Yesterday morning when i started my computer, i had the same problem. The clock was reset. Nautilus had crashed and i had to use killall. I thought that it must have been a one off incident,but today morning when i started the comp, again i faced the same problem.

Any solutions? I have a screenshot of the startup, with all the error messages arrayed and can mail it if you want. Thanks.

reg,
D

---

### Post by Devesh R on 2008-06-02
This is what my desktop looks like every morning when i start the comp. Also, the date is reset to Jan 1st, 1904. Any clues as to what to do? Tried replacing Thunar instead of nautilus, still i got the same problem. 
reg,
D

---

