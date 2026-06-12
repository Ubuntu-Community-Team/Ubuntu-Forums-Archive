---
title: "anjuta and glade"
date: 2012-12-06
forum: Programming Talk
---

### Post by jgw on 2012-12-06
I have been trying to get the glade plugin to work.  I have failed.  I have searched and the closest solution was:
copy anjuta-glade.plugin and libanjuta-glade.so from /usr/lib/anjuta to /usr/local/ lib/anjuta
These are root files so you will have to 'sudo' the cp command.
leiphasw@ Acer5552: ~$ cd /usr/lib/anjuta/
leiphasw@ Acer5552: /usr/lib/ anjuta$ sudo cp anjuta-glade.plugin /usr/local/ lib/anjuta/
leiphasw@ Acer5552: /usr/lib/ anjuta$ sudo cp libanjuta-glade.so /usr/local/ lib/anjuta/

It did not work (I suspect the target was wrong)

I have also built a glade file and tried to simply use it in Anjuta but, while Anjuta tries, it fails.

I also noted that anjuta has its own list at gnome.org  I signed up but cannot get in because it tells me that my email and newgroup stuff is wrong (I assumed that by newgroup they were asking about usenet?).  If I could figure out just where they are posting stuff on usenet I would simply go there and post.  Just thought I would throw that one in for the heck of it <g>

Thoughts?

---

### Post by yanes on 2012-12-06
from Software center , 
search for anjuta and then install the addon "glade"
and the other addons if you need

---

### Post by jgw on 2012-12-06
Thank you for the reply.
The problem is that one cannot just do that.  If you edit the anjuta preferences, then goto plugins there is a little box that says; "display only activatable plugins.  If you do not choose this then it will show glade but there is nothing the user can do.  I have no idea how one is supposed to install that plugin and I can find no directions to do that.  

If I open an existing glade file it acts as if its going to deal with it but it does not.  For instance, it will not show an existing menu bar, even though it will show it in the list of existing widgets.  There are other things but, basically, glade is simply not activated or installed.  I actually compiled a program using an existing glade file and it compiled with no problem, no callbacks, and nothing but the top level window.  In other words glade was not really installed or activated.

I could probably just code this stuff but I am trying to build a bunch of menues with, altogether, maybe 100 callbacks so I thought it would be easier to let anjuta deal with it.  I am failing.

---

