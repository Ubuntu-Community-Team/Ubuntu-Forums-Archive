---
title: "Delayed start"
date: 2008-04-25
forum: Programming Talk
---

### Post by henchman on 2008-04-25
Hi there.

Because I am unsatisfied with my hardy heron booting time, I had to think of a solution. I could write a program which will start after gnome starts and waits for the cpu load to drop down under a certain percentage for a certain time.

After than it can load the wished software later on, like apache, mysql, perhaps usb-driver (on a laptop with included keyboard and touchpad, i usually never use usb), and so on after gnome finished loading and is in idle... With a nice configuration dialogue, one could tell the program which daemons could be started 'delayed'

At first, what do you think about this idea? Useless or not? 

Could someone please point me out where the 'autostart' files for these daemons or programs are lying, or are they scattered around the system? 

Sorry for my bad english, hoping not to ask a to simple or difficult question :-)

---

### Post by tseliot on 2008-04-25
First of all you will have to study Debian's system run levels and init.d scripts.

Furthermore you can have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=727224") about Upstart ([COLOR="Red"]WARNING: this can break your system[/COLOR])

---

