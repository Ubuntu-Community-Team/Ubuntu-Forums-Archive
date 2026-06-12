---
title: "Software update fails"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by hiikeeba on 2008-10-21
I have been trying to update Ubuntu for a few weeks, and keep getting this error message:

Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.

How can I tell what is running, and how can I close it?  Should I just reinstall?

Thanks in advance

---

### Post by wolfen69 on 2008-10-21
you can check what processes are running by going to system>administration>system monitor. then highlight the offending process and click "end process".

---

### Post by hiikeeba on 2008-10-21
> **wolfen69 said:**
> you can check what processes are running by going to system>administration>system monitor. then highlight the offending process and click "end process".

Neither are listed in the system monitor. I just start the computer, go to the update menu and get the error.  Any ideas?

---

### Post by Kevbert on 2008-10-21
Without running either item, try going to System-Preferences-Sessions Current Session Tab and see if either are there. If one, or both are, try selecting the item and then click on Remove (you may then need to click on Apply - I'm not sure).

---

### Post by hiikeeba on 2008-10-21
> **Kevbert said:**
> Without running either item, try going to System-Preferences-Sessions Current Session Tab and see if either are there. If one, or both are, try selecting the item and then click on Remove (you may then need to click on Apply - I'm not sure).

Neither are listed in the process list, as far as I can tell.  When I went to the update manager, I got the same error.  Would Synaptic or Aptitude be labeled something else on the list?

---

### Post by k3lt01 on 2008-10-21
The Process List and Current Sessions List ar two different things. Check th screen shots below.

---

### Post by hiikeeba on 2008-11-01
I went to the sessions menu.  Neither Synaptic nor aptitude are listed.  I still cannot update.

---

### Post by cosmoshell on 2008-11-01
deleted

---

### Post by cosmoshell on 2008-11-01
you might want to make sure your running the program as root. if have been and if you are completely sure you do not have synaptic add/remove aptitude apt-get dpkg or any other programs running that use the portage you could try "sudo rm /var/lib/apt/lists/lock" its worked for me. dont know if its a good idea or not to do this.

---

