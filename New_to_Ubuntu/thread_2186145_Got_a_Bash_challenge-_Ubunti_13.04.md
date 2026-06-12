---
title: "Got a Bash challenge:- Ubunti 13.04"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by Timmoore001 on 2013-11-06
Trying to put a binary file into /bin but it forgotten how to get to root and bin directory  

Doesn't let me out of 'home' directory *LOL*

This has to be easy, and I'm goung to kick myself for having to ask.... but I'm stuck at the moment.

Any thoughts very welcome...

[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

### Post by Lars Noodén on 2013-11-06
In Ubuntu you need sudo to escalate to root privileges for a task.  So you would still use [cp](http://manpages.ubuntu.com/manpages/trusty/en/man1/cp.1posix.html) but with sudo.

```

sudo cp /home/timmoore/somefile /bin/

```

If you want graphics you can use nautilus (or whatever your file manager is)

```

gksudo nautilus

```

But if you do that, be sure to quit once you have transfered your file.  Otherwise it is too easy to forget and make a real mess.

---

### Post by Timmoore001 on 2013-11-06
Mega Brilliant !

I used nautilus and am about to find if my application works !

Many many thanks !

[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

### Post by Lars Noodén on 2013-11-06
Great. 

Thinking a bit more about it, if it's a home made script then [/usr/local/bin](http://manpages.ubuntu.com/manpages/trusty/en/man7/hier.7.html) might be a better location.  That's still in your $PATH.

---

### Post by Timmoore001 on 2013-11-06
I'd hoped I put it in both..   but my exit from Nautilus was less than elegant.

How do you quit Nautulus gracefully ?

Many many thanks.

[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

### Post by drmrgd on 2013-11-06
If you don't need the script to be system wide, you can also create a 'bin' directory in your home directory and add the script there.  Upon reboot or the launch of a new shell instance (if you're working from the terminal), /home/<user_name>/bin will be added to your path and you can run scripts from there.  It's the easy way to do it on a network system for which you do not have admin rights.

Not sure about your question about quitting Nautilus gracefully.  Did it not close when you clicked the 'x'?  You may have to kill it with **xkill**.  Just hit Alt+F2 and launch xkill, then click on the nautilus window to kill that process.

---

