---
title: "Terminal Server Bug?"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by d4m1r on 2011-10-12
So this is actually related to my original issue of my VPN connection to my work disconnecting randomly every 1-2 hours (cisco VPN, but doesn't disconnect on my Windows partition:-?). Anyway, I use terminal server client because it is a Windows XP machine and when I have the screen maximized and the connection disconnects I have to restart the entire PC](*,)

I can't switch workspaces, use my keyboard shortcut for xkill (because they aren't loaded, cursor is in Windows XP), etc. I know the PC hasn't frozen because I hear my music and the clock on my G15 keyboard still ticks on. There doesn't seem to be a Task Manager like shortcut to System Monitor and Alt+4 (or even Alt+Tab) don't work either.

When it isn't frozen, I hit ctrl+alt+enter and it unmaximizes and then I can switch workspaces etc. Is this a known issue with terminal server (freezing when VPN connection drops)? How can I report bugs I find in Ubuntu?

I can get in some DOS-like screen (ctrl+alt+f1-5) but have no idea what to do from there and my regular account details don't work there either...

---

### Post by decoherence on 2011-10-13
> **d4m1r said:**
> 
I can get in some DOS-like screen (ctrl+alt+f1-5) but have no idea what to do from there and my regular account details don't work there either...

those are consoles. your login credentials for your local ubuntu machine will work to get you in. once you're in, find out the name of your terminal server process and kill it. 'ps aux' will get you a list of all the processes, then 'killall process-name' will kill it. I say 'process name' because I don't know which client you're running -- could be tsclient or freerdp or anything else, so that's the first thing you'll have to find out.

Once you've done that, switch back in to the GUI with ALT F7 and your runaway session should be gone. If not, try repeating the procedure but use 'killall -9 process-name'

I also use the cisco VPN at work and find it drops much less when I disable dead peer detection.

---

### Post by d4m1r on 2011-10-13
> **decoherence said:**
> those are consoles. your login credentials for your local ubuntu machine will work to get you in. once you're in, find out the name of your terminal server process and kill it. 'ps aux' will get you a list of all the processes, then 'killall process-name' will kill it. I say 'process name' because I don't know which client you're running -- could be tsclient or freerdp or anything else, so that's the first thing you'll have to find out.

Once you've done that, switch back in to the GUI with ALT F7 and your runaway session should be gone. If not, try repeating the procedure but use 'killall -9 process-name'

I also use the cisco VPN at work and find it drops much less when I disable dead peer detection.

Hmm, ok you're right, my regular credentials do work and its basically a terminal session. ps -ef will do the same thing, but the trouble is, I have a big list of processes running (takes more than what my screen can show) so how can I scroll up?

Also, if I've got the process #, can't I just use kill #here?

---

### Post by d4m1r on 2011-10-13
> **d4m1r said:**
> Hmm, ok you're right, my regular credentials do work and its basically a terminal session. ps -ef will do the same thing, but the trouble is, I have a big list of processes running (takes more than what my screen can show) so how can I scroll up?

Also, if I've got the process #, can't I just use kill #here?


Nobody knows how to scroll in that console view (ctrl+alt+f1)?! :(

---

### Post by decoherence on 2011-10-13
> **d4m1r said:**
> Hmm, ok you're right, my regular credentials do work and its basically a terminal session. ps -ef will do the same thing, but the trouble is, I have a big list of processes running (takes more than what my screen can show) so how can I scroll up?

Also, if I've got the process #, can't I just use kill #here?

the console isn't smart enough to know about scrolling, so pipe ps to less and it will handle the scrolling for you
```

ps -ef | less
```

and yes, you can use either kill # or killall process-name

---

### Post by d4m1r on 2011-10-13
> **decoherence said:**
> the console isn't smart enough to know about scrolling, so pipe ps to less and it will handle the scrolling for you
```

ps -ef | less
```and yes, you can use either kill # or killall process-name

Thanks, works like a charm and terminal server process is titled with the hostname of my work machine so easy to find :D

---

