---
title: "Python subprocess.Popen Permissions?"
date: 2010-12-17
forum: Programming Talk
---

### Post by ngrieb on 2010-12-17
I recently wrote a python applet that uses a subprocess pipe to open some long running background processes. When I run the applet from the home directory from the terminal and in a windowed mode everything seems fine..everything works well, but when I run the actual applet from the /opt/ directory it seems that the applet fails to open the subprocesses. 

So the question is does the subprocess.Popen routine fail due to some sort of permissions error? For instance if I try and move the applet to a different directory...say /usr/share/ will it help? or is it better to simply install it in a home directory? Or do these subprocesses need to be somehow contained within the python applet file as well somehow (right now I am calling separate python files)?

Thanks.

---

### Post by The Cog on 2011-01-03
Moved to programming talk. It shouldn't get buried so quickly there.

---

### Post by ngrieb on 2011-01-11
Still nothing? Does everyone develop applets in C++ or something?
 
The applets work fine when running from the terminal in a windowed mode. Why do they fail when running under bonobo? Is there some python permission that is causing this?

Another thing that is really bothering me is that the server files for the two applets are the same...only the names and paths to the applets have been changed. One of them will show up on the panel, but doesn't call child processes, and the other fails to load altogether. I am so confused.  :confused:

---

### Post by ngrieb on 2011-02-02
Should I post the code for one or both? Is there anyone else out there that is trying to develop apps in pygtk? I really want these applets working because although there are good desklets, they either get in the way of or covered by open windows.

---

### Post by Zugzwang on 2011-02-02
Ok, here's one idea: Instead of using absolute directories for calling a python script using the subprocess module from another python script, use sys.path[0] to find out where your script resides and concatenate the name of the other script you want to call to it (e.g., "/outerScript.py"). Does this help? I assume that you did check whether all of your scripts have the executable bit set for the user?

---

