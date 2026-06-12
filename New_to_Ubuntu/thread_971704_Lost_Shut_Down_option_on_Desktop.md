---
title: "Lost Shut Down option on Desktop"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Cjmkee on 2008-11-05
I have recently installed 8.04 on a Acer Aspire One. I don't know how I did this but when I click the shutdown button on the panel or hit Control+Alt+Delete I only get the options to Hibernate or Suspend the computer and not Restart or Shut down. Does anyone know how this could have happened and what I can do to get it back? thanks

---

### Post by tchoklat on 2008-11-05
> **Cjmkee said:**
> I have recently installed 8.04 on a Acer Aspire One. I don't know how I did this but when I click the shutdown button on the panel or hit Control+Alt+Delete I only get the options to Hibernate or Suspend the computer and not Restart or Shut down. Does anyone know how this could have happened and what I can do to get it back? thanks
 
Have you tried Ctr Alt Bksp as this is the way to restart X and you should get shutdown and restart options!

---

### Post by Cjmkee on 2008-11-05
I tried Control+Alt+Backspace then logged in again. It still doesn't have the Restart and Shutdown options though. :( could it be a Permissions issue? How do you adjust what is shown when you click the Shutdown button on the panel? 

btw I assume your location is Adelaide...I was there for 5 months doing a study abroad. small world :)

---

### Post by Nostalos on 2008-11-05
I've encountered this problem only twice.  Once was when starting kdm instead of gdm, but still booting into gnome.

The other was the upgrade from 8.04 to 8.10.  I had to rename my old home folder to username.old  and create a new empty directory for my user.   Gnome rebuilds the desktop to default.  Then copy my important folders like .mozilla and .ssh from the old directory to the new.

---

### Post by Cjmkee on 2008-11-05
I'm not quite sure I follow you. So your saying you had to rename your home folder, recreate a new home folder, then reboot and import your old info into the new one? How and why would that change the shutdown option? 

ps-I am very new to Linux so please bear with me, I am trying to learn the inner workings of it :)

---

### Post by philinux on 2008-11-05
System>Admin>Login Window. Click the local tab. Tick the option show actions menu. It's near the bottom.

---

### Post by a2lkulkarni on 2008-11-05
See if your System->Administration->Login Window->Local Tab

Check "Show Actions Menu" under the "Menu Bar" title. If it is disabled, try enabling it and see if it works.


-Atul

---

### Post by Cjmkee on 2008-11-05
It worked!! thanks guys that was the problem. It must have gotten unselected during my tinkering. I appreciate the help guys! :)

---

### Post by Unstuck on 2008-11-05
I had this problem before upgrading to 8.10.  I worked around this buy running the Update Manager (rather than sudo apt-get update...) before logging off.  It's stupid and defies my simple reasoning abilities and doesn't solve the problem.  But it worked for me.  GL

---

### Post by inearlygaveup on 2008-11-07
> **philinux said:**
> System>Admin>Login Window. Click the local tab. Tick the option show actions menu. It's near the bottom.

Thanks for that tip - it just happened to me

---

### Post by -kg- on 2008-12-13
I'd like to add my thanks to philinux and a2lkulkarni as well.

I had recently pulled up the Login Options and did some experimentation (not with the "Show Action Menu" option, but anyway...) and the box was definitely unchecked.  I had noticed this upon looking through the tabs and did not uncheck it as an experiment.

I wonder if this might be some kind of "bug" in this specific congfiguration panel?  Obviously, by default it is on, so if you can uncheck that box by just launching the configuration panel, that could cause problems.  It doesn't uncheck it now by launching it, but I'm quite sure that I didn't uncheck it.

Anyway, my thanks!

---

