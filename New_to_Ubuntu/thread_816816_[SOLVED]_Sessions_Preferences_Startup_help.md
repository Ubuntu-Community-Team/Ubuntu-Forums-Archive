---
title: "[SOLVED] Sessions Preferences Startup help"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Sawubona on 2008-06-03
I'm having trouble disabling programs that are running on startup. I've looked through the sessions preferences in the startup tab and have disabled these programs (I have also deleted them from the list). I have also disabled the function that remembers programs that are running on logout.

Programs that are loading that I don't want to are:
-Amarok (loads twice)
-nautilus
-firefox
-pidgin
-thunderbird

Is there another way to disable these programs?

Thanks in advance I'm new to ubuntu so the solution will probably be really simple.

---

### Post by ad_267 on 2008-06-03
How did you get them all to start up in the first place? If you added them to sessions then removing them from sessions should work.

---

### Post by Sawubona on 2008-06-03
> **ad_267 said:**
> How did you get them all to start up in the first place? If you added them to sessions then removing them from sessions should work.

I added them to sessions, i've disabled them and removed them. I don't even remember enabling nautilus or terminal (another program that starts). I've checked sessions a million times and they're not there. I'm definitely confused

---

### Post by iaculallad on 2008-06-03
Navigate to System->Preferences->Sessions->"Session Options" tab, uncheck (if checked) "Automatically save changes to session".

---

### Post by Sawubona on 2008-06-03
> **iaculallad said:**
> Navigate to System->Preferences->Sessions->"Session Options" tab, uncheck (if checked) "Automatically save changes to session".

I've already unchecked that box. just checked again and it's still unchecked...

---

### Post by Sawubona on 2008-06-03
see attached

---

### Post by ad_267 on 2008-06-03
Could it be that they are being started by another script?

---

### Post by Sawubona on 2008-06-03
That's what i'm thinking. But what? I'm running Avant Window Navigator which loads on startup, and that loads the launchers for firefox and thunderbird, not the actual programs...

---

### Post by iaculallad on 2008-06-03
You could try looking /etc/rc.local file for autostart scripts.

---

### Post by ad_267 on 2008-06-03
Go to System - Administration - Login Window and check that default session is ticked and set to "Run Xclient script"

You could also try changing this to GNOME, I'm not sure what the default is but mine is set to run xclient script.

And check that there isn't a .xinitrc or .xsession file in your home directory which is starting these programs. You will have to turn on showing hidden files.

---

### Post by Sawubona on 2008-06-03
Thanks, i'll give that a go. Just had to get off my ubuntu machine, but i'll try it when i log back in and let you know how i go

---

### Post by sayakb on 2008-06-03
Navigate to /home/username/.nautilus folder and delete all *saved-session-** files.

---

### Post by Sawubona on 2008-06-03
> **ad_267 said:**
> Go to System - Administration - Login Window and check that default session is ticked and set to "Run Xclient script"

You could also try changing this to GNOME, I'm not sure what the default is but mine is set to run xclient script.

And check that there isn't a .xinitrc or .xsession file in your home directory which is starting these programs. You will have to turn on showing hidden files.

Ok, the Run Xclient was already selected. However i found a xsession-error file in my home dir. I can post the contents if that helps?

thanks LinuxIsInnovation i've deleted those files. I'll have to see if that did anything

---

### Post by Sawubona on 2008-06-04
Still haven't solved this. Does anyone know of another program that i may have forgotten about that i may have put these settings in?

Anyone have other ideas?

---

### Post by ad_267 on 2008-06-04
When you log in there should be a menu down at the bottom left or somewhere else depending on what theme your login window is. Try changing the session option to different things and see what works. It might be set on last session or something. Try using the default GNOME session.

---

### Post by Sawubona on 2008-06-04
Well I have solved it...by solved it i mean i've created a work around. I ended up ticking the "automatically remember running applications when logging out" box in the sessions preferences. Seemed to instantly solve it. Would've been nice not to have that box ticked so every time i logged in i'd have the same result, but oh well. 

Thanks for all the help and quick responses.

---

