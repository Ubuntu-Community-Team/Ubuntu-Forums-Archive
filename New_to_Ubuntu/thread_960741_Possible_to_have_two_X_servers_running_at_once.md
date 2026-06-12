---
title: "Possible to have two X servers running at once?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by cknight on 2008-10-27
I'm playing around with new desktop environments and was wondering if its possible to get two x-sessions running at once?  I've tried zipping over to another session (Ctrl-alt-F1) and running startx.  But alas, it says I've already got an active X-server.

So, is it not possible to run two x-server sessions at once? And no, I'm not really interested in VM ware as a potential solution.  Just wanted something quick and easy. Thanks in advance!

---

### Post by Gwijde on 2008-10-27
I'm not sure whether there's an easy way to do this is Gnome, I think KDM lets you run different sessions as different users, but I'm not sure so don't take my word for it :)

Check this out, seems useful:

[http://ubuntuforums.org/showthread.php?t=213756]("http://ubuntuforums.org/showthread.php?t=213756")

---

### Post by starcannon on 2008-10-27
I think you'll find this tutorial to be of use:
[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

GL and Have fun

---

### Post by louieb on 2008-10-27
> **Gwijde said:**
> ... an easy way to do this is Gnome,..  you run different sessions as different users,..

Just choose switch user  login as a different user. Use Alt+ F7 and Alt+F8 to toggle back and forth.  The 1st time you toggle you'll have to enter user one's password again. After the 1st time you  don't have to enter the password.

---

### Post by cknight on 2008-10-30
> **starcannon said:**
> I think you'll find this tutorial to be of use:
[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

GL and Have fun

Fantastic.  Just what I was looking for.  Works a charm!

---

### Post by cknight on 2008-10-30
> **louieb said:**
> Just choose switch user  login as a different user. Use Alt+ F7 and Alt+F8 to toggle back and forth.  The 1st time you toggle you'll have to enter user one's password again. After the 1st time you  don't have to enter the password.

This is probably an even easier method, except that I'm not running any of the easy graphical desktop environments and don't know how to switch user (which is probably an easy command line task)

---

### Post by cknight on 2008-10-30
For the curious, my main Desktop environment is Fluxbox, but I'm playing around with Awesome (a tiling window manager) and was trying to get both up and running at the same time.  This is because Awesome has a rather steep learning curve and I wanted easy access to something familiar and comfortable.  Here's what I did:

1) Ctrl-Alt-F1 to switch to tty1 (virtual terminal)
2) log in
3) enter the following command
```
startx /usr/local/bin/awesome -- :1
```

startx starts a new X server
/usr/local/bin/awesome is the path to the executable for my window manager
-- :1 directs this to the virtual X session located on Ctrl-Alt-F8 (in this instance).
0 is Ctrl-Alt-F7 and default X session.  Don't use this as its already in use!
-- :1 is accessed by Ctrl-Alt-F8
-- :2 is accessed by Ctrl-Alt-F9
etc...

---

### Post by bodhi.zazen on 2008-10-30
I was going to give you the link to my "Virtual X" thread.

I also have one on Xephyr if you like to ssh -X (although you can also use the first method as well).

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

---

