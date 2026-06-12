---
title: "Everything is highlighted in the Command Line"
date: 2017-03-16
forum: New to Ubuntu
---

### Post by mbrasseau on 2017-03-16
I am new to Ubuntu, as well as new to Linux. This is my first post.

I have Ubuntu 16.04 set up on AWS. I am taking tutorials and learning how to use the command line. 

One of the tutorials was covering the use of "less". I used the command to attempt to read a file I created to log my command line activity (script). I loaded and kept scrolling like crazy, so I used Ctrl-C to stop it. Now all of the text in the command line is highlighted, perpetually. 

What did I do? And how do I put it back to normal? 

I have googled, and searched a few forums including this one, to no avail. 

Thank you in advance for any assistance.

---

### Post by TheFu on 2017-03-16
type:```

stty sane<enter>
```
even if you can't see it, do it.
If that doesn't work, hit cntl-c about 20 times and try again.

What happened is your 'less' caught some funny printable characters which enabled the reverse text.

Another way to clear it up is to just make a different ssh connection.  Actually, I hope you aren't using a console, always use an ssh connection for this stuff.  Consoles should really only be needed if you break the networking.

---

### Post by mbrasseau on 2017-03-16
It is an ssh connection, through PuTTY. Am I not also accessing the console? Are console and command line not the same thing with Linux? Am I calling it the wrong thing?

The learning curve... it is steep!

I tried your suggestion... nada. But thank you anyways!

Nothing seems "broken", so I'll continue as I am until I get to some magical tutorial that addresses the issue.

Until then, if anyone knows the solution to this, I'd be most obliged.

Here's a screen shot:

---

### Post by The Cog on 2017-03-16
You could try the command **reset** instead. I always use that if a terminal output gets stuck in a strange mode like that.
If you make a new putty connection, does that show the same problem?

The word console would normally imply a local screen and keyboard instead of remote, and often also implies the text-only consoles that are available using Ctrl-Alt-F1 through Ctrl-Alt-F6.
The word terminal is a more general term for a command-line, either console, local GUI terminal window or SSH connection over the network.

---

### Post by TheFu on 2017-03-16
None of this will help. _The Cog_ has some good ideas too. I'm surprised that reconnecting with a new ssh session didn't fix it. With an xterm or other Linux terminal, you have more control that Putty provides.  Check your putty font/color settings too?  I haven't used putty in about 10 yrs, so don't know what it looks like these days.  It doesn't compare to a good terminal on a Unix/Linux machine. So many little things don't work like the X-buffer. Oh well.

ssh and a "console" are different things.  ssh is normally remote.  A console is always "local" and usually a hardware thing.  Often, it is a serial port connection over a tty, not a pty.  There are 8+ consoles on most PCs.  Access them with Alt-F1 thru Alt-F8.  ALT-F7 is normally the X/Windows console these days.  On Unix machines, serial consoles are much more common since nobody puts a GPU into a server.  Serial consoles are used on Linux too - when there isn't a GPU/VGA card. This happens with embedded Linux systems - like most routers these days.

Yes, the learning curve is very steep.  We all worked our way through it. I recall my brain hurting for a few months, but I was learning about 10 different Unix systems concurrently. Fortunately, 90% of Unix and Linux is the same, it is really just the admin stuff that becomes specific to the flavor and hardware.

---

### Post by mbrasseau on 2017-03-16
@The Cog: The **reset** command worked! Thank you! :p

@TheFu: You know, I didn't even notice your suggestion to simply start a new ssh connection. I'm certain that would have worked as well.

Thank you both for your input, I've learned new things today. Now to read up on how to mark this thread as **"solved."**

---

### Post by TheFu on 2017-03-16
People like me forget that for others, starting another ssh isn't 2nd nature. 

I have 10 remote xterms running right now, for example. 2 are local to my machine, but the rest, about 10, are to different systems. Some on the LAN, some in a local data center and some 10K miles away.  ssh is a way of life for me.  Most of my computing doesn't happen on the machine I'm sitting behind. It is almost always remote.

---

