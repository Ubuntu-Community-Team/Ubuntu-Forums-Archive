---
title: "Problem with Skype Video in Unbutu 11.10"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by bobnrx on 2011-11-09
Hi --Name is Bob --absolutely new to this --but here is my problem

Skype Video --is not working in Ubuntu 11.10--connection and Audio are OK --but Webcam is not sceen 

--but I'm told that the starter line can be changed -----sh -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype "$@"'&#65279; "

I have no idea how to do this whatsoever --I just started using Ubuntu 2 days ago and all I can do is point and click---so can someone walk me thru how, where and when to add the above line to-----also i am told you have to do this each time you want to use skype -- so --is there something I can add (again how -where and when) so you do not have to run the above text each time you want to start Skype.  Thanks for all your help.

Bob Nicolella
[email]bobnrx@aol.com[/email]

---

### Post by rosencrantz on 2011-11-09
Hi Bob,
I think you have to run the line
[FONT="Courier New"]LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype[/FONT]
in a terminal to preload the v4l1compat library before you start skype. 
So try that first. 
Make sure the libv4l-0 package is installed and the path for v4l1compat.so is correct (use synaptic and nautilus), and adjust the path if necessary.
Type 'terminal' in the search field in the Ubuntu program menu, which should give you a terminal.
Paste the line, which should give you a running skype instance and see whether your webcam works.
If that solves your problem, there are several ways to make starting skype easier. I'd suggest a shell script.
Open gedit and paste the following into a new file:
```
#!/bin/sh
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
```
Make it executable (right-click in nautilus) and place it on your desktop or in another convenient location. Skype should start with a double click now.

---

