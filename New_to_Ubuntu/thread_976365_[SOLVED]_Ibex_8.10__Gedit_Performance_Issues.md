---
title: "[SOLVED] Ibex 8.10 | Gedit Performance Issues"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by MrWES on 2008-11-09
Is anyone else seeing poor, very poor performance issues with gedit? When attempting to open a file for editing, I'm getting 100% CPU usage and open times of ~30 seconds or more.


Thanks,
Bill

---

### Post by drs305 on 2008-11-09
Gedit opens in about 3 seconds for me. Have you tried disabling the gedit plugins to see if it makes a difference?

You could also try opening it from the command line and look for any messages or perhaps open a specific location to see if it starts any faster ( gedit /home/Desktop/somefile ).

---

### Post by asgard_command on 2008-11-09
I had a problem when I first installed 8.10 with gtk apps especially noticed it on gedit, it was connected to the theme I was using. I got a gtk warning error in the terminal saying the ubuntulooks theme engine couldn't be found. There is somekind of conflict issue that prevents it form being installed.
Selecting a theme based on a different engine fixed the problem for me.

---

### Post by MrWES on 2008-11-09
> **drs305 said:**
> Gedit opens in about 3 seconds for me. Have you tried disabling the gedit plugins to see if it makes a difference?

You could also try opening it from the command line and look for any messages or perhaps open a specific location to see if it starts any faster ( gedit /home/Desktop/somefile ).

b00m! that was it.

Thanks

---

### Post by asgard_command on 2008-11-09
The last post reminded me of another problem, I had to disable the File Browser Pane plugin. That was giving me 30 second start up times.

---

