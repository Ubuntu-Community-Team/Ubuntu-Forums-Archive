---
title: "Whats the best download for deleting unnecessary files?"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by vegas89 on 2012-11-21
I am running Ubuntu 12.4 and would like to know the best download the clean up my OS, unnecessary files, or duplicate files and things I don't need or use.  :-k

---

### Post by sffvba[e0rt on 2012-11-21
First thing that comes to mind is to look at what software you have installed that you don't use and remove it via the Ubuntu Software Center.

Secondly in the terminal you can run: ***sudo apt-get clean***

> To clear the cache you can use either the clean or the auto-clean op for a command-line program called apt-get. The clean command will remove every single cached item, while the auto-clean command only removes cached items that can no longer be downloaded (these items are often unnecessary).



as well as: ***sudo apt-get autoremove***

> packages can also become unused over time. If a package was installed to assist with running another program- and that program was subsequently removed-you no longer need the supporting package. You can remove it with autoremove


[Source]("http://www.ubuntugeek.com/how-do-i-cleanup-ubuntu.html")

Also keep in mind that Linux != Windows so many of the pardigms that held true for Windows don't apply to Linux.


404

---

### Post by ibjsb4 on 2012-11-21
Bleachbit

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

Its in the software center.

---

### Post by snowpine on 2012-11-21
Hi, why do you think you have unnecessary files? Are you having performance issues? Hard drive getting full?

---

### Post by vegas89 on 2012-11-21
All my apps are running fine but I am having boot issues. My OS will not boot sometimes it will just stay paused on the purple screen at start up. I was thinking I may have redundant files that are causing problems.

---

### Post by houseworkshy on 2012-11-21
bleachbit is good but be sure of it's setup, it can take too much out such as other languages and bookmarks.  Fslint is a handy one too, it has several extra options to bleachbit such as the option to look for and remove duplicate files.  The above command line advise is also good "apt-get" has several disk clean up options, autoclean, autoremove, purge for when one wants to remove the settings of a program as well as the program itself.  For more details type "man apt-get" in the terminal to see the commands manual page.

---

### Post by ibjsb4 on 2012-11-21
> **vegas89 said:**
> All my apps are running fine but I am having boot issues. My OS will not boot sometimes it will just stay paused on the purple screen at start up. I was thinking I may have redundant files that are causing problems.

Maybe your bootlogd would shed some light on that, you need to turn it on.  In terminal:

sudo gedit /etc/default/bootlogd

and change BOOTLOGD_ENABLE=No to:

BOOTLOGD_ENABLE=yes

Your bootlogd is located at /var/log/boot

And its a good idea to turn it off when finished with it so not to create unnecessary log files.

---

### Post by snowpine on 2012-11-21
> **vegas89 said:**
> All my apps are running fine but I am having boot issues. My OS will not boot sometimes it will just stay paused on the purple screen at start up. I was thinking I may have redundant files that are causing problems.

I don't follow your logic in reaching that conclusion. Linux includes useful tools to diagnose boot problems; take a look in **/var/log/messages** next time you have this freeze, and then you'll be able to analyze the *actual* system messages, instead of randomly deleting files to see if it solves the problem.

Also see here for some older (but possibly still helpful) info: [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

### Post by DuckHook on 2012-11-21
+1 to snowpine. Very useful to ask why OP was enquiring. "Unnecessary files" are sometimes a jumped-to conclusion for unrelated and deeper seated problems.

To OP: your boot hangs are almost certainly due to something like misbehaving video modules or improper HDD settings, etc. Please follow snowpine's procedures before deleting anything at all. Linux is far less susceptable to choking from cruft than Windows, so look for other causes.

---

### Post by vegas89 on 2012-11-21
Thank you snowpine and ibjsb4 for that valuable reply. I was not aware of the Linux boot issue tools and how to use them. I also installed bleachbit and did a system clean.  I have not done a reboot yet.  The information provided in the forum link, I believe will  be very useful once I study on it and figure out how to use it.  I am always learning. Thanks again  ):P

---

