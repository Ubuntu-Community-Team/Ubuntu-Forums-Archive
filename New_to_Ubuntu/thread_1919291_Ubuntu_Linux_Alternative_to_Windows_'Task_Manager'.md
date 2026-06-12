---
title: "Ubuntu Linux Alternative to Windows 'Task Manager'"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by LinuXofArabiA on 2012-02-02
[COLOR=Navy]Hello Everyone,

I have been using Ubuntu for a while now, but noticed lately that more and more demand is being placed on my CPU. With all the updates and changes, much more is being added to my system, and at a much quicker pace than I could keep up with, and especially to keep my Ubuntu clean, organized and efficient... I was wondering if - as a starting point - there is an application in Ubuntu similar to 'Task Manager' in Windows that would allow me to view what on earth is going on in the background, why am I hearing my HD working all the time, and whether I would be able to view daemons, scripts, etc... running and perhaps shut the ones that I dont need.

Any help or tips are highly appreciated. Also feel free to refer me to any good reading material on the subject.

Thanks![/COLOR]

---

### Post by drmrgd on 2012-02-02
I believe in Ubuntu it's called "System Monitor" (hopefully they didn't change the name...been a while).  Try searching for that in the Dash.  If you're running Gnome 2D, it'll be located under System Tools.

---

### Post by ajgreeny on 2012-02-02
Use system monitor.  It's the nearest to task manager.

You can also use the command ```
top
``` in terminal.  Press upper case P to rank by cpu, or M for memory.

---

### Post by LinuXofArabiA on 2012-02-02
[COLOR=Navy]Thank you very much. You all deserve your beans![/COLOR]

---

### Post by Chronon on 2012-02-03
I prefer htop over top.
> NAME
       htop - interactive process viewer

SYNTAX
       htop

DESCRIPTION
       This program is a free (GPL) ncurses-based process viewer.

       It  is similar to top, but allows to scroll the list vertically and horizontally to
       see all processes and their full command lines.

       Tasks related to processes (killing, renicing) can be done without  entering  their
       PIDs.


---

### Post by Nixarter on 2012-02-03
Don't forget iotop for read/write info!  (once installed, "gksudo iotop")

---

