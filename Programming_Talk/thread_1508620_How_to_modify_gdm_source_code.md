---
title: "How to modify gdm source code"
date: 2010-06-13
forum: Programming Talk
---

### Post by alibaba163 on 2010-06-13
Hi all,
       I am running ubuntu 9.10 (with gnome as my desktop environment). I want to modify gdm source code. So do i need to downnload ubuntu source code to do that?? if  yes from where?? or gdm script(which is started by /etc/init.d/gdm script) can be configured to make changes according to our own needs.

The main purpose is to tell gdm to start my GUI application at login screen.

I must say I've been totally disappointed by the kind of responses I've got from my previous posts. I thought there is the forum where people share ideas and knowledge but it seems as if noone is bothered about whats going on and replies look more of a formality rather than passion to explore.

---

### Post by nvteighen on 2010-06-13
> **alibaba163 said:**
> Hi all,
       I am running ubuntu 9.10 (with gnome as my desktop environment). I want to modify gdm source code. So do i need to downnload ubuntu source code to do that?? if  yes from where?? or gdm script(which is started by /etc/init.d/gdm script) can be configured to make changes according to our own needs.

The main purpose is to tell gdm to start my GUI application at login screen.


Hm... not sure... I'd first research for a solution that doesn't imply modifying the source... :P Have you taken a look at this thread: [http://ubuntuforums.org/showthread.php?t=1413240](http://ubuntuforums.org/showthread.php?t=1413240)?

Anyway, you can download the source for whatever package "something" simply by using:

```

mkdir something-source
cd something-source
# The commands above are just to prevent a mess :P
apt-get source something # No sudo needed!

```

---

### Post by iponeverything on 2010-06-13
[http://ubuntuforums.org/showthread.php?t=672423](http://ubuntuforums.org/showthread.php?t=672423)

---

### Post by alibaba163 on 2010-06-13
from what i've relised that I dont want a solution where i need to change source code. since i cannot do it on all the client machines where application will be installed.

so telling gdm in Default script would be an option to try. Also be aware of the fact the my application is a GUI application and I want it to be available to login screen(I think xsession is not started by this point).

---

### Post by alibaba163 on 2010-06-14
I have tried to put following line  /usr/bin/xeyes & (as a test), just before last line(exit 0 ) in script /etc/gdm/Init/Default

This does start xeyes and show xeyes window during bootup but that xeyes seems to disappear (not visible on screen however i can see it running in list of running processes) when login screen arrives.

After I login xeyes dies!!!

Any suggesstions.

---

