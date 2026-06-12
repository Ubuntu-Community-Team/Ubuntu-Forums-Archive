---
title: "White screens and root access"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by d_swordfish on 2008-06-05
I've been running Ubuntu and dual booting for a couple of months now, and recently updated to version 8.

After noticing updates were not downloading, I browsed these forums and found out that I in fact had no root access and upon trying any sudo command I got a message about unable to resolve host. The forum told me I should try using the recovery console to regain root access. So I restarted, selected recovery mode from grub and attempted running various commands, these did not work so I went back to the recovery menu. Stupidly I managed to run the "Fix xServer" option. Now upon login I get a blank white screen and nothing happens. 

I've tried searching around but have not yet found a solution. Can anyone help?

---

### Post by phidia on 2008-06-05
Try pressing the Alt+Ctrl+F1 (other function keys up to F7 should work too)
from the CLI that comes up you can hopefully login and then type > startxand press enter. If that doesn't bring you a desktop it should at least give you some error output you can search and/or post here.

---

### Post by Baelus on 2008-06-05
See if you have sudo rights.

If you do then try this:

```
sudo X -configure
```

That will generate a new xorg.conf file. Your current xorg.conf file is still untouched. This just puts a new one together. Then use this:

```
sudo X -config xorg.conf.new
```

At least that may get you a gui to work with.

- B

---

### Post by d_swordfish on 2008-06-05
Ok, tried both of these. I still do not have root access and simply receive the message
```
Unable to resolve host: KAYE-OS-2
```

Using the startx command after logging in gives me this:
```
hostname: Unknown host
xauth: (argv):1: bad display name "KAYE-OS-2:0" in "list" command
xauth: (stdin):1: bad display name "KAYE-OS-2:0" in "add" command

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again

xauth: (argv):1: bad display name "KAYE-OS-2:0" in "remove" command

```

I had to copy that by hand and type, so there may be some errors.

---

### Post by Baelus on 2008-06-05
Ah. Looks like a known bug in Hardy:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

The sudo problem is at the top of the list. It also looks like there's a workaround and a fix.

Hope it's something you can use. And let's hope X figures itself out after that. :)

- B

---

### Post by d_swordfish on 2008-06-07
Alright, we're getting somewhere. I'd already found the thread about the root access problem, that's why I was messing around in the recovery console to begin with. I obviously didn't read it well enough however, as this time I was able to get back my root access. Which of course allowed me to do the x config thing. However this has not really worked yet, as I am simply led to a flickering grey screen with a mouse cursor and nothing else.

Thanks for the help so far.

---

### Post by Baelus on 2008-06-07
I admit I broke a rule of troubleshooting. I charged head first into the more complex stuff. Start simple and work from there. :oops:

Did you try phidia's suggestion of 

```
startx
```

I'm thinking if you now have sudo and the 'resolve host' issue is solved, then startx could very well work.

- B

---

### Post by d_swordfish on 2008-06-11
I'm still getting this:

```
Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again
```

Any thoughts?

---

### Post by Baelus on 2008-06-11
That lock file is set when an X server starts. It's supposed to stop other instances of X starting (on the same terminal I think).

This will shutdown any instances of X for sure:
```
sudo killall Xorg
```

That may kick the desktop manager into gear and you'll get your gui back.

If not then you can manually get rid of the X lock file with this:
```
sudo rm /tmp/.X0-lock
```

Now you should be able to run:
```
sudo /etc/init.d/gdm start
```

which will start the X server, activate gnome and either drop you at the login screen or it will take you straight to your desktop if auto-login is set.

That's for Gnome. I think KDE uses kdm and Xfce I guess would be xdm. 

- B

---

### Post by d_swordfish on 2008-06-24
Sorry for taking so long to try these, I have been very busy. killall seems to have some effect, I get thrown back to the login screen, and upon logging in actually get a few seconds of my desktop befor the white screen returns. Trying the manual method gets me this:
```

david@KAYE-OS-2:~$ sudo /etc/init.d/gdm start
 * Starting GNOME Display Manager...                  [OK]
david@KAYE-OS-2:~$
```

Nothing else happens. I tried running startx again, but was left with a black screen with the cursor in the centre.

---

### Post by d_swordfish on 2008-06-30
Could use an answer on this if at all possible.
Thanks.

---

