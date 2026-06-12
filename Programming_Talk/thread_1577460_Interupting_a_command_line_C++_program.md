---
title: "Interupting a command line C++ program"
date: 2010-09-18
forum: Programming Talk
---

### Post by ownaginatious on 2010-09-18
So here's my situation:

I recently created a 5 x 11 LED matrix with shift registers that I can control using the parallel port. Right now I'm writing a 'driver' (if you can even call it that) to write to it. The information written to it scrolls across the screen.

Anyway, the idea is that I would want this to run like a daemon when the computer starts up (just displaying the time I suppose).

What I would like to do is be able to 'feed' the program information while running. For example, if suddenly I would rather it scroll a message, I would like to be able to just somehow tell the already running program to stop displaying time, and instead display this message I'm giving it. This program would have no graphical interface.

Now the problem I'm having is, how do I talk to an already running program? Initially I thought I would just maybe make a python front-end that would kill the program and reload it with different parameters any time I want it to do something different... but I think that causes problems because then the 'lp0' hardware file I'm writing to is never closed (which seems a little unclean).

What does everyone else think/suggest? I'm relatively new to C/C++, so I don't know a lot about the flexibility of the language.

Any help/feedback would be greatly appreciated.

Thanks!

---

### Post by worksofcraft on 2010-09-18
Presumably your program sits in some kind of loop doing something and so you could use non blocking input from input stream.
IDK if this might get you started but here is how you can do it in C++.

```

	// do non-blocking input while we run some kind of idle.
	ios_base::sync_with_stdio(false); // don't try to synchronise with C stdio
	char _; // somewhere to store input, but we don't care what it is 
	// readsome returns the number of characters it could read 
	while (!cin.readsome(&_, sizeof _)) do_idle_activity();

```

---

### Post by ownaginatious on 2010-09-18
Oh thanks, that seems a bit complicated, lol.

While searching non-blocking input though, I came upon the ncurses library. I think I'll try messing around with that first.

Thanks!

---

### Post by psusi on 2010-09-18
> **ownaginatious said:**
> Oh thanks, that seems a bit complicated, lol.

While searching non-blocking input though, I came upon the ncurses library. I think I'll try messing around with that first.

Thanks!

Ummm... (n)curses is for building ASCII based GUIs.

I'd suggest that you put the message you want it to display in a text file, and send it a SIGUSR1 signal to tell it to re-read that text file.

---

### Post by ownaginatious on 2010-09-18
> **psusi said:**
> Ummm... (n)curses is for building ASCII based GUIs.

I'd suggest that you put the message you want it to display in a text file, and send it a SIGUSR1 signal to tell it to re-read that text file.

Oh I know ncurses is for ASCII GUIs and I think it would be useful here... but unfortunately I've yet to find a tutorial that doesn't suck. I'll keep it in mind in case I ever want to build an actual interface later on.

Anyway, how do I send signals to the program? And also, is there a way to send information with these signals?

Thanks.

---

### Post by ownaginatious on 2010-09-19
Ahh, okay I think I understand now. I'll just have the daemon writing process run as an infinite loop based on some variable being true. If the SIGUSR1 signal is received, I'll set the variable to false and get the program to read whatever the new parameters are.

I'm guessing I should create a different command line program for controlling the "daemon" by signalling it. I was just wondering though, is there a way to store variables readable between two separate programs?

I mean for example, when the daemon starts up I was thinking of creating a bunch of environmental variables through unix commands which contain it's current settings. The 'interface' program could write over these environmental variables using a unix command, and then send the SIGUSR1 signal to break the daemon's "writer" loop and have everything be reread.

Is that the proper way to go about doing it? I just thought rewriting a file over and over for new settings sounded a little lame.

Thanks!

---

### Post by psusi on 2010-09-19
You can just use kill to send the signal, or the more typical thing to do is to add an option to the existing program to update rather than create another program.  When starting up normally you write your pid out to a .pid file somewhere, and when given the update switch, find the pid file and send the signal to that pid.

---

### Post by SledgeHammer_999 on 2010-09-19
Or use D-Bus to send messages to your deamon from another program.

---

### Post by NovaAesa on 2010-09-19
You could have a server program (your driver) and a client program (which tells the driver what to display). You could let them communicate with each other via ports - you could even send the exact text you wanted to display via a port. This would then also have the added advantage that you could change the text remotely.

---

