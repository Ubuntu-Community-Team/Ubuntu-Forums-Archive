---
title: "Alternative to the shutdown command?"
date: 2013-10-07
forum: New to Ubuntu
---

### Post by Meowcenary on 2013-10-07
I was screwing around in terminal and wanted to see about turning my computer off before I went to bed, I typed in shutdown as a guess and to my surprise it was actually a command. It then asked for a time (in minutes as I found out) and for root user (so I used sudo) so the final command I sent was sudo shutdown 1, which then sent out a message saying there was one minute until the server would go down for maintenance. So it looked as though things were shutting down as they would in a normal situation, except that the power button on the front of my computer was still glowing green and the monitor did not have the idling orange glow on the power button it normally has when the computer is off. Is this because shutdown is an alternative command to something that turns everything off? Furthermore are there other alternative commands for things such as restarting and shutting down that I can use and have them enact instantaneously?

---

### Post by deadflowr on 2013-10-07
```
sudo reboot
``` 

will restart the system.

---

### Post by UlTroX2000 on 2013-10-07
Normally shutdown does turn of your computer completely (at least with mine it does), but mabe someone else has more details on that.
To turn your computer off immediately try "shutdown now", to reboot try "shutdown -r now" (both require root privileges).

---

### Post by Meowcenary on 2013-10-07
> **UlTroX2000 said:**
> Normally shutdown does turn of your computer completely (at least with mine it does), but mabe someone else has more details on that.
To turn your computer off immediately try "shutdown now", to reboot try "shutdown -r now" (both require root privileges).

Ok. For the sake of learning syntax do you know what -r now applies to? Im slowly trying to develop an understanding of the terminal, im getting the commands but finding things on syntax of commands seems to be harder.

---

### Post by Bucky Ball on 2013-10-07
This:

[https://help.ubuntu.com/community/UsingTheTerminal#Commands](https://help.ubuntu.com/community/UsingTheTerminal#Commands)

... and this:

[https://help.ubuntu.com/community/CommandlineHowto#Command_Syntax](https://help.ubuntu.com/community/CommandlineHowto#Command_Syntax)

... might help. There is a ton of info available about commands and syntax. ;)

PS: This is also handy but no explanations. You could research each.

[http://fosswire.com/post/commands/](http://fosswire.com/post/commands/)

Another:

[http://beginlinux.com/desktop_training/ubuntu/ubuntu-terminal-guide](http://beginlinux.com/desktop_training/ubuntu/ubuntu-terminal-guide)

Incidentally, type this: 
```

man shutdown
```

... in a terminal and you will find, first on the list:

> -r ... Requests that the system be rebooted after it has  been  brought down.

'-r' is an option (there's a heap and they can do different things in different situations) and they come after a command. You can also string them together.

Just a note: I have never heard of this timing thing with shutdown you mention. I just tried it and get nothing like it. Hmm. You learn something everyday, hopefully. :-k ;)

---

### Post by mcduck on 2013-10-07
Shutdown command, on it's own, only shuts the *system* down. If you want it to also power off, you need to use the "-p" option.

...or save yourself some typing, and instead of "*sudo shutdown -p now*" just use "*sudo poweroff*". :) ("*poweroff*", "*halt*" and "*reboot*" commands invoke shutdown with different options. They might be easier to remember and quicker to type if you don't need to specify a time or shutdown message...)

---

### Post by Lars Noodén on 2013-10-07
> **mcduck said:**
> Shutdown command, on it's own, only shuts the *system* down. If you want it to also power off, you need to use the "-p" option

I use [shutdown -h](http://manpages.ubuntu.com/manpages/raring/en/man8/shutdown.8.html) on my systems, which is probably just calling  for the system to be powered off.  AFAIK on Ubuntu there is no -p option.  Though there is a -P for powering down.  

```

sudo shutdown -h 23:59 "Time to go to bed" &

```

---

### Post by fantab on 2013-10-07
Even I use *sudo shutdown -h 02:15* and it does 'Power Downs' my computer.

---

### Post by 3rdalbum on 2013-10-07
Although I knew about 'shutdown', I didn't know it could also poweroff the computer.

I've always used:

```
sudo halt
```

or

```
sudo reboot
```

---

### Post by mcduck on 2013-10-07
-h option might or might not actually power off the machine, depends on the power management (and BIOS settings) of the system.

Indeed, it does power off most of the systems I've used, but not all of them, so poweroff (or the -P) option is more universal solution.

(And yes, my bad, it's -P not -p. I usually just use "halt" as it's the shortest one and does power off my laptop)

---

### Post by Bucky Ball on 2013-10-07
From 'man shutdown':

> -h     Requests  that  the system be either halted or powered off after it has been brought down, _with the choice as to which left up to the system._

Pretty straightforward explanation. Up to the system which. It's all there in 'man shutdown'. ;)

---

### Post by Meowcenary on 2013-10-07
> **Bucky Ball said:**
> This:

[https://help.ubuntu.com/community/UsingTheTerminal#Commands](https://help.ubuntu.com/community/UsingTheTerminal#Commands)

... and this:

[https://help.ubuntu.com/community/CommandlineHowto#Command_Syntax](https://help.ubuntu.com/community/CommandlineHowto#Command_Syntax)

... might help. There is a ton of info available about commands and syntax. ;)

PS: This is also handy but no explanations. You could research each.

[http://fosswire.com/post/commands/](http://fosswire.com/post/commands/)

Another:

[http://beginlinux.com/desktop_training/ubuntu/ubuntu-terminal-guide](http://beginlinux.com/desktop_training/ubuntu/ubuntu-terminal-guide)

Incidentally, type this: 
```

man shutdown
```

... in a terminal and you will find, first on the list:



'-r' is an option (there's a heap and they can do different things in different situations) and they come after a command. You can also string them together.

Just a note: I have never heard of this timing thing with shutdown you mention. I just tried it and get nothing like it. Hmm. You learn something everyday, hopefully. :-k ;)

This is very helpful information! Hopefully I can come back with better questions after some more experimentation.

---

### Post by heir4c on 2013-10-07
You can also use:
man reboot  (or man halt or man poweroff, this 3 had the same man-page) 
All of them (and even shutdown) have different options and do different things.

---

