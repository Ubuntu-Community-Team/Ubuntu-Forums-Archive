---
title: "[SOLVED] [gnome] switching to an app from a shell script"
date: 2008-10-06
forum: Programming Talk
---

### Post by skotos on 2008-10-06
I have been spending some time on writing a script to check whether an app is already running to avoid running it twice and I have successfully accomplished that.
I use zenity to give some feedback and I believe is really nice, even if it lacks some features I would like such a timeout on a default choice, but this is another question.

Currently I am stuck in front of the problem of switching to the application I have found and that it is already running.
How can do it?

For instance, I launch eclipse on desktop 2, but then I go back working on desktop 1. After a few minutes I launch eclipse and my script tells me it is already running: how can I say it is running on desktop 2 and then switch to desktop 2 and make it the current window?

Is there any already available command or do I have to write it from scratch in a different language to access the APIs?

Thanks in advance for any suggestion that might point me into the right direction.

---

### Post by gnusci on 2008-10-06
I don't know if there is a command to do the switching between desktops in gnome, but you can give a try to:

[http://www.sweb.cz/tripie/utils/wmctrl/](http://www.sweb.cz/tripie/utils/wmctrl/)

I gave a look to the Workspace Switcher applet information:

[http://library.gnome.org/users/user-guide/latest/gosoverview-41.html.en](http://library.gnome.org/users/user-guide/latest/gosoverview-41.html.en)

And I cant find any command-like interaction, perhaps if you give a look in to its code, you will find some ideas.

---

### Post by mssever on 2008-10-07
I find Compiz to be quite handy in this situation. Under the scale plugin, I set the option Initiate Window Picker For All Windows to BottomRight. Then, I just hit the bottom right corner of the screen with my mouse, and see all windows on all desktops.

I also have certain desktops for certain apps. For example, I always put my browser on desktop 1, my primary terminals and any text editors on desktop 2, and miscellaneous stuff (such as special-purpose terminals, VMs, graphics tools, etc.) on desktops 3 and 4.

---

### Post by skotos on 2008-10-07
@gnusci> **gnusci said:**
> ... you can give a try to:

[http://www.sweb.cz/tripie/utils/wmctrl/](http://www.sweb.cz/tripie/utils/wmctrl/) ...
**Yes!** *:) wmctrl* is the solution.
If I have, for instance a job whose pid is 9971 on another desktop, I can switch to it by quickly running wmctrl this way:```
wmctrl -ai `wmctrl -p -l | grep -i 9971 | tail -1 | cut -c 1-10`
```@mssever: yes, I like it, in fact, though luckily I did not have to look at its code coz wmctrl is exactly what I was looking for: something that works in a bash script, and that works inside Compiz too.

**Thank you** guys!

---

