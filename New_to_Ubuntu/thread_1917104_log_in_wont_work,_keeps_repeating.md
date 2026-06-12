---
title: "log in wont work, keeps repeating"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by scott239 on 2012-01-29
Hi, I have been using ubuntu for a few months and has been working find. Yesterday I logged in with name & password and after a few seconds the same log in screen shows up again. This has happened several times during the day. This morning, it is still the same. I tried to reset the password thinking perhaps something was wrong with current password and after restarting it does the same thing. I think I see a quick line of wording when starting up but it goes by so fast I can't see what it says. So at this point I can't log in and am unable to proceed further.
Any ideas on what is wrong or what I should try?
Thanks, Scott

---

### Post by Carborundum on 2012-01-29
Try switching to tty 1 (by pressing ctrl+alt+f1), and try to log in from there. If the log-in attempt fails, you should see some kind of error message. Post it here.

(To get back to the graphical session, press ctrl+alt+f7)

---

### Post by 2F4U on 2012-01-29
My guess would be that the desktop crashes and that this is the reason why you are put back to the login screen. If you are able to get to a virtual console, as suggested in the previous post, look for the file .xsession-errors in your home folder and see if there are errors reported.
Did you install new or updated software since the last successful login?

---

### Post by scott239 on 2012-01-29
hello,  thanks for the tips.  I did try to login using the ctrl, alt & f1.  It does work but does not show any of the normal graphics I usually see.
Above my log in I see:
segmentation fault
ubuntu 2.6.32-28 generic.  #55-ubuntu smp mon jan10 23:42:43 utc 2011 x86_64 gnu/linux
 
Not sure if that helps you but that is what I am seeing.
I had a friend help me load this originally so not very clear on where to find the home folder or updating.
 
Any additional help would be great.
 
Thanks again, Scott

---

