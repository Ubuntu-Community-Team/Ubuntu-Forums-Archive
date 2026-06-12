---
title: "Double Log In Required"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by David Oxland on 2008-06-06
Every time I log in I'm being asked to do it twice.
First time and password  then on  to black screen and a few fast lines of code, then do it again with a normal opening.

Any clues what's happened here?

Second question; might it be connected to a HUGE login screen which I've had since upgrade to Hardy/Gnome and I've not been able to fix yet?
All updates done

Thanks

---

### Post by shifty_powers on 2008-06-06
is the first log in on a balck screen with white writing?

---

### Post by cariboo on 2008-06-06
You might want to check and see if your hostname is in /etc/hosts. Hostname=computername. in a terminal type:

```
cat /etc/hosts
```

You should see something like this:

```
127.0.0.1	localhost
127.0.0.1	intrepid
<------------cut--------------->

```

If you don't have something similar to the second line with your computername. Open your favorite editor as root and add it to the file.

Jim

---

### Post by Hospadar on 2008-06-06
I would assume there might be some connection.  You could try re-installing gdm (the component which manages graphical login) when the machine boots up, do a Ctrl-Alt-F1 to get a text terminal
First be sure gdm is stopped```
sudo /etc/init.d/gdm stop
```
Now purge it```
sudo apt-get remove --purge gdm
```
Now re-install```
sudo apt-get install gdm
```
It should now start automatically, if not, reboot or ```
sudo /etc/init.d/gdm start
```

---

### Post by lazyart on 2008-06-06
I've seen this before, but I noticed that if I just wait the graphical login screen would show up on it's own.

---

### Post by David Oxland on 2008-06-06
Thanks to all

Hospadar; your solution did it
Makes me wonder if there is something in /etc/init.d/gdm which might be edited to help with the log in screen size which remains huge?  It is large enough that only the top left 1/4 of the intended log in screen appears which shows only part of the ubuntu logo.
I am able to login just knowing that the cursor is set in name and proceed

Thanks again

---

### Post by cybergrue on 2008-11-05
I am having a similar problem, but I think it has a different cause.
I am asked for my password twice when logging on in gnome, and when using sudo on the command line.  From experimenting with the logon screen, the first password box seems to be ignored (I can just hit enter) and the second password box is the one that is used.  Same with the sudo, the first password can be anything, and as long as the second one is correct, then it works.

Furthermore, Update manager does not work (I type in my password, the "reading package information" window pops-up, the status bar progresses, the window closes, and nothing else happens and I'm back at the main update manager with a list of updates that are ready to be installed)  From reading some (now closed) threads, I suspect that this is a related issue.

I upgraded from 8.04 to 8.10 last week and have been having the double password issue ever since.

---

