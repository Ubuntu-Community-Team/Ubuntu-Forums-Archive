---
title: "only show login after bootup"
date: 2020-05-27
forum: New to Ubuntu
---

### Post by desdan on 2020-05-27
Hi:
Running Ubuntu 18.04 server.  After some recent updates there are lots of device driver messages on the console after bootup.  I have to hit the enter key to get the login prompt.  Is there a way to automatically clear the screen and leave me with the message from /etc/issue and the login prompt only?   I would like to keep this clear and uncluttered as I have many unsophisticated users who see those messages from time to time and panic. This generates unnecessary calls to our support line.
Thanks!

---

### Post by desdan on 2020-05-27
After looking at this a little closer what I am seeing is that the login prompt does appear, but then additional messages are coming (sometimes lots of them) appear and push the login up and off screen.  The user then has to "know" to hit the enter key to get the login again.
Yikes this is annoying.  Is there a way to make sure the login prompts comes after everything else?

---

### Post by TheFu on 2020-05-27
If you haven't hit ESC, then no messages should display, rather a splash screen should show up.  If messages are showing at boot, I'd quickly look for failures in the system logs.  Hardware failures never get better and fixing a smallish issue today is better than having a system that won't boot at all tomorrow.

And if you are running 18.04 Server, not a desktop, then nobody should be watching it boot who isn't a server admin.

---

### Post by desdan on 2020-05-28
Thanks - yeah, running server.  Problem is that regardless of whether they should be watching isn't relevant because scary messages generate unnecessary calls to support.  This is an appliance in a broadcast TV infrastructure and not typically in the realm of computer system administrators who are rarely on-site.   My need is simply to keep the TTY1 console clean and pretty.  Happy to let the system puke all over TTY2+ though... :-)

---

### Post by TheFu on 2020-05-28
I'd tape a little sign over the monitor saying **not to worry, don't touch** or just turn the monitor off. I've actually done this a few places.

Have you looked at grub options to show a splash screen instead? [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

