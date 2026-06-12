---
title: "Set up VNC server in 3 steps, accessible with browsers and other viewers"
date: 2007-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by se2131 on 2007-10-15
EDIT: Ok, I lied, I meant 4 steps (w/ an optional 5th)

I just did this on Gutsy, and I thought that it might be worth sharing as a simple way to set up a persistent VNC server. This is accessible using regular vnc viewers, and through java-enabled browsers. That's right, you can work on your computer through a browser.

**1) Install packages**
```
sudo aptitude install x11vnc vnc-java
```

**2) Set up password to allow clients to view**
```
x11vnc -storepasswd
```

**3) Open up ports 5800 and 5900 on your firewall**

**4) Run this command: x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800**

That's it!

And an optional step 5:

**5) Add the command from 4) to your sessions, so that it starts at each login**

If you want to test it out on a browser, type this in the URL field:

25.542.161.414:**5800**

Of course, replace the 25.etc. w/ your external IP address.

Addendums to this are welcome, such as how to make it more secure. I just thought it'd be nice to have a quick and dirty tutorial for getting this set up easily.

---

### Post by ryansinn on 2008-02-19
x11vnc* doesn't exist in gutsy .. you want to use vncserver and vnc-java

but FYI this method is very insecure and doesn't actually work as advertised.

If you want to run a persistant VNC server -- you should really look more at tunneling the VNC connection via SSH if at all possible.

---

### Post by krunge on 2008-02-19
> **ryansinn said:**
> x11vnc* doesn't exist in gutsy .. you want to use vncserver and vnc-java
I think it is available in the universe repository.
> 
but FYI this method is very insecure and doesn't actually work as advertised.

Recent versions of x11vnc are SSL enabled and you could run it like:
```
x11vnc -http_ssl -ssl SAVE -display :0 ...
```
then point the browser at the https URL:
```
https://hostname:5900
```
You may need to download x11vnc's java viewer jar files separately because Debian doesn't include them.

---

### Post by sasagundul on 2010-07-11
nice tutorial :D
thanks
it helped me to set my home server

---

