---
title: "How do I restart X programmatically?"
date: 2007-01-22
forum: Programming Talk
---

### Post by WakkiTabakki on 2007-01-22
Hi all
I've had this up here before but haven't managed to solve it properly...
Original post: 
[http://ubuntuforums.org/showthread.php?t=267015]("http://ubuntuforums.org/showthread.php?t=267015")

I'm writing on a small app to edit and manage xorg.conf:s. 
Idea is:
I use my laptop for a lot of things, as a work comp, presentations, media player etc... Sometimes with TV-out, a projector, an external monitor a few different keyboards and mice depending on where I am. Now setting up X for each situation is a bit of a hazzle, right.
Enter the XConfig Manager.

The app is quite simple, the only thing causing trouble is restarting X nicely.
Currently it's simply doing
```
gksu /etc/init.d/gdm restart
```
That did work "nicely" on a fresh Edgy install. But then I set up wireless, with server mounts on the desktop etc. Now it's getting increasingly dodgy... Desktop won't show on restart, and sometimes the wireless is totally dead ](*,) 
In short, a bad solution.

The suggestion (from the original post above) to send a HUP (or something) to all children of the Xorg-process just seems to unstable (e.g. it'd be really hard to guarantee the order signals are sent). And there must be a way to issue a controlled shutdown of X already in there. I mean, how does gnome do it? Can't you ask gnome-session to do a proper logout and then tell gdm to restart?

How about switching runlevels, that'd at least run the shutdown scripts, right? But, then with the switch to 'upstart', runlevels doesn't really apply anymore?

Any suggestions, please [-o< 
/N

BTW, I will ofcourse post the app here if it gets finished...

---

### Post by Tomosaur on 2007-01-23
Kill whichever process pgrep returns for Xorg:

```

pgrep Xorg

```
will return the PID of Xorg.

Alternatively you can just
```

pkill Xorg

```

Using sudo, obviously :)

---

### Post by WakkiTabakki on 2007-01-23
Just ran a few quick tests, and it seems much more stable than the gdm-variant!

Great tip, thanks!
/N

---

### Post by WakkiTabakki on 2007-02-05
Well, a first test version is ready!

Check it out:
[http://ubuntuforums.org/showthread.php?t=353103]("http://ubuntuforums.org/showthread.php?t=353103")


/N

---

