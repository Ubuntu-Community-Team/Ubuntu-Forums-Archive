---
title: "GUI problems..."
date: 2014-05-26
forum: New to Ubuntu
---

### Post by Alexis_Rivera on 2014-05-26
Hi Ubuntu gurus,
I was trying to install a vnc server in my Ubuntu 13.xx and now I cannot log in my account anymore...
The login and passwd seem correct. It looks like it is trying to start the graphical interface, but it directly comes back to the login window.  
I updated to 14.xx hoping it would solve the problem, but I still have problems.  The good news is that I can log in the vnc account I created :)


Any ideas??

---

### Post by Alexis_Rivera on 2014-05-26
I also get this message everytime I log in... (probably related!)

> 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory


I get also this error when I log with the vnc account
> 
vnc is not in the sudoers file.  This incident will be reported.


---

### Post by steeldriver on 2014-05-26
if you ran vncserver as sudo, you probably screwed up the permissions on your ~/.Xauthority file - log in at a CLI virtual terminal (e.g. Ctrl-Alt-F2) and fix it

---

### Post by Alexis_Rivera on 2014-05-27
I found the answer right here
[http://ubuntuforums.org/showthread.php?t=2214042](http://ubuntuforums.org/showthread.php?t=2214042)

It was a bug with Samba... Update fixes it.

---

