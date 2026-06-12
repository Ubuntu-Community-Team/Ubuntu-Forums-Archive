---
title: "keyboard shortcut for suspend"
date: 2023-08-29
forum: New to Ubuntu
---

### Post by ubiwerks on 2023-08-29
Hello, I am running a Ubuntu 22.04.3 LTS system for about a week on my desktop pc and I am very happy with everything. A minor issue which I could not resolve is
the possibility to bring the computer to suspend using a keyboard shortcut. 
I tried in the settings menu to setup a new shortcut with the command: **systemctl suspend**
This works only for 1 second and then the computer restarts by itself.
I tried the same command in a terminal window and it works perfectly.
Alternatively I tried to make the shortcut with the command: **systemctl suspend -i**  achieving the same result as before.
I assigned a variety of different key combinations to the command in order to avoid conflicts but nothing I did changed the result.

I did some google searches and searched in this forum but I could not find an answer that is resolving my question.
I know it is only a minor thing, but I like to get to the bottom of the problem.

Thanks a lot for your help
Ub

---

### Post by TheFu on 2023-08-29
Do you have the system configured to wake if the mouse moves?  If so, ensure the mouse cannot move.  If it were me, I'd delay the suspend of a desktop for 10 seconds to give me time to leave the room.

I don't suspend my desktop systems, only a laptop.  For a laptop, I had a script that does a system backup, then suspends it.  I haven't booted that laptop in some years (with everyone working from home, there's little need for a laptop).  

Ok, found it.  
```
$ more ~/bin/**zb**ack-suspend
#!/bin/bash

sudo /root/bin/backup-to-rom
sudo pm-suspend
```

So, does 22.04 support pm-suspend?  I think that's an alias/link to systemctl suspend (probably).
There's a way using the WM (window manager) to call any program/script you like using a keyboard shortcut. I'd show mine, but it is very unlikely that you use fvwm as your window manager.  Not exactly useful to 99% of the people in these forums.

---

### Post by ubiwerks on 2023-08-29
First of all thanks TheFu for the fast reply. I had the same thought as you. I was very careful not to touch anything after the shortcut input. I even switched the mouse off. 
I had even the thought that the keyboard shortcut apart from suspending the system is waking it up at the same time !?
Unfortunately the pm-suspend command is not supported. I have no fvwm window manager installed.

---

### Post by TheFu on 2023-08-29
> **ubiwerks said:**
> First of all thanks TheFu for the fast reply. I had the same thought as you. I was very careful not to touch anything after the shortcut input. I even switched the mouse off. 
I had even the thought that the keyboard shortcut apart from suspending the system is waking it up at the same time !?
Unfortunately the pm-suspend command is not supported. I have no fvwm window manager installed.

My mouse moves just by walking near the room.  With a laptop, we can setup the suspend to be tied to the laptop lid being closed.  That's in /etc/systemd/logind.conf The manpage for logind.conf is good too.  I think that file only gets read at boot time.  It does have a way to have the power key become the suspend key for a quick press.  Again, the manpage is quite extensive, full of excellent information.

---

### Post by maglin2 on 2023-08-29
A systemctl suspend keyboard shortcut works on 22.04.3 on my machine.
Perhaps try searching the logs for 'suspend' to see if anything is reporting 'failed to suspend' or similar?
nvidia graphics seem to get a mention elsewhere in relation to immediately waking after suspend problem. So does bluetooth.
I don't know why there should be a difference in behaviour between a command issued from terminal and one issued by keyboard shortcut, assuming there was no use of elevated privileges in the terminal.

---

### Post by ubiwerks on 2023-08-29
Thanks again TheFu but I did not find the problem in /etc/systemd/logind.conf. The mouse was switched of for the trials.

 maglin2 you saved my day instead. Reading through the log files I found out that there was indeed  a hardware problem, that was created by a PS-2 to USB adapter that I use to connect the keyboard.
I removed the adapter and the problem was solved !! Seems that the adapter has a time lag that works as a wake up signal.
Thanks

---

### Post by ajgreeny on 2023-08-29
I don't use Ubuntu, Xubuntu being my choice now for many years but setting a keyboard shortcut to command ***xfce4-session-logout --suspend*** to the Pause key on my keyboard immediately put my machines into suspend mode.
Changing the keyboard shortcut command to ***xfce4-session-logout --halt*** and linking that to he Winkey+Pause will immediately power off the machines.

It might be worth seeing if there is a similar command that you could use in your Ubuntu system; is there a similar **ubuntu-session-logout** command that you can use with the **--halt** or **--suspend** options as I can with Xubuntu?

---

### Post by MAFoElffen on 2023-08-29
```

systemctl suspend

```

---

### Post by maglin2 on 2023-08-30
> **ajgreeny said:**
> I don't use Ubuntu, Xubuntu being my choice now for many years but setting a keyboard shortcut to command ***xfce4-session-logout --suspend*** to the Pause key on my keyboard immediately put my machines into suspend mode.
Changing the keyboard shortcut command to ***xfce4-session-logout --halt*** and linking that to he Winkey+Pause will immediately power off the machines.

It might be worth seeing if there is a similar command that you could use in your Ubuntu system; is there a similar **ubuntu-session-logout** command that you can use with the **--halt** or **--suspend** options as I can with Xubuntu?

We have gnome-session-quit  with options [--logout|--power-off|--reboot]. I use a gnome-session-quit --power-off keyboard shortcut for routine shutdown.
I don't know of an equivalent suspend option, but systemctl suspend has always worked perfectly for me.

---

### Post by ajgreeny on 2023-08-30
> **maglin2 said:**
> We have gnome-session-quit  with options [--logout|--power-off|--reboot]. I use a gnome-session-quit --power-off keyboard shortcut for routine shutdown.
I don't know of an equivalent suspend option, but systemctl suspend has always worked perfectly for me.

Good to know!
I've been using those shortcut commands that I mentioned for many years, before systemd and systemctl was used I think, and it is still working in Xfce so I see no reason to change it at the moment, though I might just try it out for future reference.

---

