---
title: "WICD message at boot"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-10-13
I am running Ubuntu 10.04 on a laptop and it always asks for a password at login it syas "WICD needs to access your computers network cards" and to enter a password. This is a public library machine set to auto login.We really don't want to type in a password at every boot. I tried the fix listed here
[http://ubuntuforums.org/showthread.php?t=885761](http://ubuntuforums.org/showthread.php?t=885761)
but I have the x in the correct boxes already. I need more help to fix this bug. This laptop got mixed up by an interrupted natty install and the only way I could get it working was with a 10.04 install. Even though I run 8 other laptops with the same specs and no problem with Natty upgrade.It runs 10.04 OK except for this bug. I gave up installing natty on it. Even with a clean reformat it would install Natty successfully then totally freeze at splash screen when restarted to I downgraded to 10.04.

---

### Post by beew on 2011-10-13
Why do you use WICD???It looks like it is long dead. Nm is much better anyway. Tried WICD a year ago for a few times because I didn't know better. :) it never worked. It conected and then dropped off and then could not reconnect without rebooting, and  it always asked for password at startup and then would throw some error message.

I know there are some old forum posts saying that nm is buggy and WICD worked better but check the date, they were from centuries ago, nm has caught up and WICD is no longer developed. :)

---

### Post by cmcanulty on 2011-10-13
I didn't install WICD it started with the new switch to 10.04 can I safely delete it?

---

### Post by beew on 2011-10-13
> **cmcanulty said:**
> I didn't install WICD it started with the new switch to 10.04 can I safely delete it?


  You can remove it if you have other ways to access the internet other than wifi because otherwise if you remove it  you wouldn't be able to download and install the gnome-nm, but you can't install nm when wicd is still running.

So, if you have wired connection, go ahead and remove WICD and then install the nm.

If not open synaptic and download the gnome-nm without installing, then remove WICD , reboot and install gnome-nm from the cache.

---

### Post by cmcanulty on 2011-10-14
OK thanks I got it restarted and connected but still no wireless even though all the identical machines wireless worked without any tweaks at allnd the wireless light is on.

---

