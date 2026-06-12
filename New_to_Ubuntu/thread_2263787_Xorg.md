---
title: "Xorg"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by hmiersch on 2015-02-03
Hi.
Every time I log into my admin account, I get a dialog box saying "system program problem detected" or something like that. When I dig a little deeper, it tells me that something called Xorg has crashed. So the question is, what is Xorg, why do I need it and why does it keep crashing in my admin account but not in my user account?

---

### Post by Impavidus on 2015-02-03
Xorg is the thing that makes it possible to run a GUI. When it crashes you get a black screen and are logged out. It will be restarted automatically, bringing you back to the login screen. So you definitely need it (for now, replacements are being developed), unless you want command line only, like on a server.

Maybe it only crashed once, but as long as the crash report isn't cleared you will be informed every time it has crashed when using the admin user. The other user doesn't get the crash reports as he doesn't have permission for that.

---

### Post by mastablasta on 2015-02-03
admin account? you mean root which is disabled by default?

xorg is the one drawing the graphical interface. it is super important for desktop. 

we would need to know more about the setup and also the exact message you get, as well as the GPU chip you are using. because something is wrong with your graphics card driver setup. or perhaps even a file permissions issue. depends on the exact error that makes the OS crash.

when it crashes can you still login to another tty (using crtl+alt+F2 through F6)?

---

### Post by hmiersch on 2015-02-04
I have 2 accounts. One admin account I use for system administration, things I can't do from a user account (I can use sudo) and a user account for everything else (can't use sudo). 

Hardware is a mid-2012 MacBook Pro with 16GB RAM. Ubuntu is booted from an external 250GB HD. 
As for the GPU and error message, I'll check that out when I get home...

---

### Post by hmiersch on 2015-02-04
BTW, sometimes I try to wake the mac up but all I get is a black screen with a mouse pointer. No login screen, nothing. Is that related to this problem?

---

