---
title: "Howto (almost) fix Firefox &quot;already running&quot;"
date: 2010-02-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Telecaster72 on 2010-02-15
On and off i have had this annoying bug in Firefox where if i have closed FF it wont start again because it is already running. Looking around the web i have only found tips to remove the .lock and .parentlock files (that gets recreated anyway next session) or how to kill the firefox process still running.

Here is my workaround, note that this will make FF start everytime, but not kill the process that won't shut down so if you get error messages when shutting down, log out or switch user,  you will also have the same messages after this and the good ol' alt+f2 "killall firefox" will do.

Create an empty file for example in your home directory, open it and write:
```
killall firefox
firefox
```

Save as killfirefox.sh (or other name.sh)

Make it executable:
```
chmod +x killfirefox.sh
```
(If you created the file somewhere else you must write the complete path to the script)

Now change the properties of your FF launcher. In Gnome, right click the launcher (or rightclick gnome-menu, choose "edit menus", find the launcher, edit it.

As command you simply replace firefox %u with:
```
/home/yourname/killfirefox.sh
```
(assuming you created it in your home dir)

Now it will kill any running FF processes before it starts FF and you will not get that error.

I am sure this could be done better and smoother with some knowledge in scripting, i am but a mere noob when it comes to this, you can probably make it remove the .lock and .parentlock files to make it shut down properly, i might try to do that later, if any script-God has any suggestions please chime in!

---

