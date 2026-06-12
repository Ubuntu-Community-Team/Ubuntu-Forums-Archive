---
title: "After dist-upgrade QuickSynergy slows"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by mevets on 2008-04-25
I use QuickSynergy cause I have two computers and I simply want to use one mouse and one keyboard. While I ran gutsy on both machines, the process ran smoothly. After updating both machines, one thru the update manager, to hardy the interaction between machines became very laggy. When I would use my server's mouse and keyboard on the other client the mouse would lag and mouse clicks would hold for too long. I dont think this is a problem with synergy, but rather of the networking between the two after the update.

Is there something I should be aware of that would slow the networking down between two hardy machines?

---

### Post by dracnor on 2008-04-26
Hi mevets,

I was having the same problem, and fixed it by making sure that synergy is running as root.  

When running it as my normal user I would received stuttering and freezes - but monitoring the background processes showed that everything seemed to run OK (no 100% CPU usage, etc.).  I also ran some ping tests and found that connectivity was never disrupted.  I'm not sure how to run this as a normal user yet.  Anyone know a solution?

---

### Post by mevets on 2008-04-26
should both the server and client be run as root?

---

### Post by jlapier on 2008-04-26
Thanks dracnor - that worked for me. I just upgraded one computer (the synergy client) to Hardy and my other computer (the synergy server) is still Gutsy. I only had to run the client as root (but as I said, the server is still gutsy...)

Apparently it's a problem in the kernel:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194029/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194029/)

- Jason

---

### Post by Travisty on 2008-05-02
It appears that the slowness is due to the completely fair scheduler. You can circumvent this by manually changing the nice value of the synergyc process.

There are 2 ways you can find the process ID.

**_GUI_**: Go to system -> Administration -> System Monitor.
look for synergyc in the list of processes on the processes tab.
You'll notice the ID number and the nice number to the right. In non-Hardy versions of ubuntu you could right click and change the value but there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/206583") in launchpad right now that will cause the process manager to crash. You'll need to change the value on the command line. Read Down.

_**CLI**_: Launch the terminal Applications -> Accessories -> Terminal.
type _ps -ux_ and look for synergyc. It will list your username and the next column has the process number. you'll use the process number next.

**_Changing Nice Value_**: in the terminal we're going to put in _renice <nice value> <process ID>_.

The nice values go from -20 to +20 with 0 being standard. I increase the value to -10 and everything is running great. I entered _renice -10 7056_. You'll want to change the nice value to what is fitting for you and change the process to ID to the process number you found from the earlier steps.

---

