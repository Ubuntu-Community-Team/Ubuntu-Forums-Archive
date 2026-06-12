---
title: "Installed Eclipse, now Firefox3 won't start"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by AntonyG on 2008-10-22
Hi, last night I installed Eclipse IDE from the standard add/remove programmes, and now I can't start Firefox.

I made no other changes, so must be something the standard eclipse install did.

The firefox icon bounces around for a while and then disappears.

When I try to run firefox from the command line I get "Segmentation fault (core dumped)" and that it, I've no clue where to look next.

Anyone got any ideas?

Thanks in advance.

Antony

P.S. I'm Running:
Firefox 3.0.1
Kubuntu 7.10
just installed Eclipse 3.0.1 I think it was

---

### Post by AntonyG on 2008-10-22
More info:

Just tried to run firefox as root and got this, and wondering if its any help.


```
antony@antony-desktop:/usr/lib/firefox$ sudo ./firefox
Password:
You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:6820): Gtk-WARNING **: cannot open display:

```

---

### Post by Crandom on 2008-10-22
Firstly, **never** run firefox as root. It will must likely break everything. Even then, you should run graphical programs as root with gksudo (or gksu - same thing), and command line programs as root with sudo, not just sudo all the time.

I can't think why eclipse would have destroyed firefox unless it was some java related fault. Try removing firefox in synaptic and reinstalling it. You could try the same for eclipse, but the you would have to download all 400mb of it again, so maybe best not to. If you are really stuck, you can install opera and use that instead.

From [http://web.mit.edu/answers/unix/unix_bus_or_seg.html](http://web.mit.edu/answers/unix/unix_bus_or_seg.html) segmentation fault means:

"If the program displays this message:

	Bus error
or
	Segmentation fault

... then the program was trying to access a memory location outside its
address space.  The computer detected this problem and sent a signal to your
program, which caused it to abort."

---

### Post by AntonyG on 2008-10-22
Got it thanks.

Reinstalled Firefox and its all fine now.

Thanks

Antony

---

