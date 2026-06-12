---
title: "Close, Min, and Max Icons vanished"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-06-20
I was trying to customize some things and my min, close, and max, icons on the top right corner of windows disappeared. I dont know how to get them back. Ive tried changing the theme back to the way it was but no luck. 

Also, the title bar got tucked underneath the task bar and I cant move the window. Its actually kind of infuriating. I set up the "hold alt+left mouse button" to try and move it without the title bar but it doesnt work. :(

Its gotta be something simple but when you dont know what that simple solution is it gets tough.

---

### Post by sdennie on 2008-06-20
I'm not sure about the window moving thing but, you might be able to get your buttons back by hitting Alt-F2 and typing gconf-editor.  Navigate to /apps/metacity/general and change the button_layout to: "menu:minimize,maximize,close".

---

### Post by Bigtime_Scrub on 2008-06-20
I really screwed my Ubuntu up this time :(

Alt-F2 doesnt work anymore either! It doesnt do anything. I just noticed.

---

### Post by sdennie on 2008-06-20
You can just open a terminal and type "gconf-editor".  I'm not sure what the rest of your problems are related to though.

---

### Post by Duck2006 on 2008-06-20
Can you boot in to recover mode?

---

### Post by alienexplorers on 2008-06-20
Are you running compiz.  If so you need the line:
> Option         "AddARGBGLXVisuals" "True"
put in the screen section of your xorg.conf file.

---

### Post by Bigtime_Scrub on 2008-06-20
I cannot boot into recover mode. I made a lot of weird changes and I guess it's finally catching up. I'm going to reinstall. I had been meaning to do it but I was being lazy and putting bandaides on a lot of things. I know I can fix it, but the Windows guy in me always says if there are problems, back up and reinstall. Old habits never die I suppose.

---

### Post by Duck2006 on 2008-06-20
When you reinstall make a home partition, so if you have to reinstall you still have your home partition.

---

