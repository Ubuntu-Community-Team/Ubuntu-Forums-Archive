---
title: "Is the a GUI or browser available to start from Ubuntu server 12 command line?"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by lbrown7868 on 2012-11-26
Is there a GUI or browser available to start from Ubuntu server 12 command line?

---

### Post by zombifier25 on 2012-11-26
No. You need to install the X server, a window manager, etc. first. [Here be instructions](https://help.ubuntu.com/community/ServerGUI#X11_Server_Installation)

---

### Post by lbrown7868 on 2012-11-26
Thank you.  I'll check them out.

---

### Post by Wim Sturkenboom on 2012-11-26
There are some command line browsers; *_links_* is installed by default if I'm not mistaken. Another one is *_lynx_*.

Fun to play with but no support for a number of frequently used technologies (e.g. javascript).

---

### Post by audiomick on 2012-11-26
Do you mean a web browser for the internet? If you do, and you do not want to install a graphical desktop on your server, you might want to look at elinks. It is not a GUI application, but it will get you into the internet in a useful way.

[http://www.elinks.cz/]("http://www.elinks.cz/")

It should be available from the Ubuntu repositories, I think.

---

### Post by lbrown7868 on 2012-11-26
Elinks was a very quick install and gets me on the web.  Thank you.  

Working on getting the the Openbox to open.

---

### Post by audiomick on 2012-11-26
> **lbrown7868 said:**
> Elinks was a very quick install and gets me on the web.  Thank you.  

Great. Good luck with openbox.

---

### Post by DuckHook on 2012-11-26
links2 with the -g switch will give you frames and graphics, but no cookies, flash or java. I prefer it even in my desktop environments because it is fast, lightweight and much more secure than the standard browsers. However, not for everyone as it won't run youtube, etc.

---

