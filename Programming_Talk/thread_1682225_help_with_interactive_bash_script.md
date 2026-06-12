---
title: "help with interactive bash script?"
date: 2011-02-05
forum: Programming Talk
---

### Post by amaranth13 on 2011-02-05
Hi, 
I'm a relative newbie to bash scripting. I'm trying to create a bash script in order to run a telnet session from the command shell on my webmin interface (I know webmin has a Java telnet/SSH option but I need to run it on a non Java-enabled phone browser). I closed webmin to all ip's except the one of the phone browser and my LAN, so security should not be a big problem. The telnet session needs to be interactive so I can react to emergencies on the Mux game I run if I'm not at my computer. I have managed to create a script so I can automate the telnet session but user interaction is a problem. I know it would be possible to pass on parameters with the calling of the script but I need it to be interactive based on what the emergency is. 

I've been looking into expect() but that doesn't seem to allow me to use keyboard input through the webmin command shell, though it did allow me to write the telnet script without user input. Read won't work either. TTY won't work because the command shell on webmin is not a terminal. I saw that I'll have to look into using a pseudo terminal and maybe forktpty() but I'm afraid I'm in over my head and don't quite understand the man page or the way it works. Telnetd is supposed to offer a telnet session on a pseudo terminal but I'm not managing to work out what the man page means, and how to use it...

I found the following tutorial for pseudo terminals [http://rachid.koucha.free.fr/tech_corner/pty_pdip.html](http://rachid.koucha.free.fr/tech_corner/pty_pdip.html) but the examples don't run on my system (Ubuntu 10.04 LTS). And I am not able to find any examples of how to use telnetd like this, despite lots of Googling. Does any of you know a tutorial with examples that I could use and learn from? Or do you have ideas for me on how to achieve this? Or is this too crazy a project for a newbie to undertake? 

Thank you so much for any help.

---

### Post by v8YKxgHe on 2011-02-06
Just use SSH?

---

### Post by Tcressy on 2011-02-06
> **alexc_ said:**
> just use ssh?

win!

---

### Post by MadCow108 on 2011-02-06
I don't know webmin but does expect's interact not work?
this gives you manual control of the shell and can return control back to expect later

---

### Post by amaranth13 on 2011-02-07
Thank you all so much for your ideas and input! I tried SSH, unfortunately I'm having trouble finding out how to use it to get a telnet type session started without username or password (since muxes don't require this, and it refuses connection through SSH so far with a connection refused message). Using the normal username I have for that server does not let me open the connection on the mux port. 

I tried 'interact' in the script but that  has the problem that webmin doesn't allow interaction during the script  so it only shows the information after the possibility to interact has  already closed. The automatic login part of it is working perfectly, but  after the 'interact' starts the shell interprets any commands that were  supposed to be sent to the tel on interact as normal Linux commands. 

I am going to keep trying to work with SSH, try to find out if it's possible to log in without username, the man file is clear otherwise, but I'm not sure I understand how to do that without causing an authentication type problem. I'm still worried I'm in way over my head :) But your tips were very much appreciated. If someone knows how to make a connection without username on SSH I would love to hear how :) Google hasn't come up with the golden egg yet. Thanks!

---

### Post by v8YKxgHe on 2011-02-07
removed

---

### Post by amaranth13 on 2011-02-07
Sorry if it makes no sense. I'm trying to find a way to log into the mux (text game) I run from my non-java phone browser. I installed webmin, which I can reach through my phone browser, and was trying to make something that would let me log onto the mux through that. Unfortunately scripts and commands through webmin seem to work different than from a command line terminal so 'telnet' doesn't work if not in a fully automated script (I can't give interactive telnet commands during or after the script or command line entry ends), and a script with read, or one with expect and interact don't work either. 

I think I have found a solution though, [www.mosha.net](www.mosha.net) has an interactive http to telnet portal that is in javascript, which works on the phone. They have a whitelisted group of games and sites you can connect to and they have helped me add an 'enter' button to the site (because my phone was just entering editing mode with that key instead of sending the command). Because of the problem with enter I didn't think it was going to be an option but because of their help now it is. 

So I think I'll focus on that for the mux connection instead of trying to write a script to do this through webmin, because I don't understand half of the stuff you need to understand to make it work. Everyone, thank you so much for your suggestions. At least I know a little more Linux now, but I'll need to make some middle level scripts before I work on something this complicated :)

---

