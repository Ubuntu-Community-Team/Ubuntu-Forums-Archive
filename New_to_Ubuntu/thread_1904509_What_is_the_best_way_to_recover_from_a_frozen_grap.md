---
title: "What is the best way to recover from a frozen graphical system?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2012-01-04
As I am experimenting, I am finding that my system freezes every once and awhile.
What is the best way to recover from that?

In Windows I'm use to using the infamous three finger salute: Ctrl + Alt + Del
In Linux (my version anyway 11.04 currently) that brings up the "Shutdown" or "Suspend" or "Restart" options only.  But there is no option to kill a process or recover in another way (like logging out or something?).
Do I have another option?

I am mostly referring to the GNOME desktop freezing I guess.  I've heard you can open a terminal and kill a process that way, but sometimes the system is too frozen to do that.

I guess, in general how do I do this?  How do I kill an errant program, and especially one that freezes my computer?

Mind you, I'm not blaming Linux or Ubuntu, the things I'm doing frequently involve WINE and trying to run Windows programs inside Linux for example, but not exclusively.

---

### Post by hopelessone on 2012-01-04
Its called "System Monitor" in Ubuntu

Cheers.

---

### Post by Basher101 on 2012-01-04
press ctrl + alt + F1 to enter tty1 (when you press ctrl + alt + F1-F6 you will reach 6 different consoles, tty1 - tty6 respectiveley. On ctrl + alt + F7 you will return to your graphical desktop) there you must first login with your username and type in the password. From there on the easiest way is to just type ```
sudo reboot
``` and reenter your password.


regards


edit:  > Its called "System Monitor" in Ubuntu

 Cheers. how is he supposed to use it when his whole GUI froze up?

---

### Post by amingv on 2012-01-04
Ctrl + Esc brings up the task manager, from where you can kill/term/suspend/etc processes. Could that be what you're looking for?

---

### Post by Learning Linux 2011 on 2012-01-04
Basher: Yes, thanks, that is the type of thing I am looking for.  
Can I kill graphical processes from the command line that way? Like if I know exactly what is was that crashed my system?  
I'm not too familiar with how to do it if there is a way.  Or is the F1/tty1 sort of a separate instance of Linux running side by side? 

Hopeless: True, that's the right idea, but system monitor usually isn't accessible when the system is frozen.

amingv: Control + Escape doesn't seem to do anything on my system.  Could it be something else?  I'm using Ubuntu 11.04.  Are you using Kubuntu?  Is there a task manager?

---

### Post by corrytonapple on 2012-01-04
From the command line, if you know what the process is (and I don't know how to get a list of running processes), just type:
```
sudo kill program
```
it will then kill it if you got the name right.

---

### Post by Basher101 on 2012-01-04
> **Learning Linux 2011 said:**
> Yes, Basher, that is the type of thing I am looking for.  
Can I kill processes from the command line that way?  I'm not too familiar with how to do it if there is a way.  Or is the F1 sort of a separate instance of Linux running side by side? 

Hopeless: True, system monitor usually isn't accessible when the system is frozen.

amingv: Control + Escape doesn't seem to do anything on my system.  Could it be something else?  I'm using Ubuntu 11.04.  Are you using Kubuntu?  Is there a task manager?

task manager is on KDE.

also to kill a certain process you will either need the name or the process ID. IF you know the name you can kill it with ```
killall [process name]
``` example:```
killall conky
``` For the process ID there was some command but i do not know it...

---

### Post by wildmanne39 on 2012-01-04
Hi, this is also a method that is highly recommended for restart a computer safely.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Thanks

---

### Post by mcduck on 2012-01-05
> **wildmanne39 said:**
> Hi, this is also a method that is highly recommended for restart a computer safely.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Thanks

...in addition to that, you can restart the whole graphical desktop using SysRq+k. (works for virtual consoles as well, it simply kills everything in the current virtual console.) That's a bit smoother than a full system reboot, so it's a good idea to try this first and if it doesn't help then the full SysRq+reisub.

---

### Post by Basher101 on 2012-01-05
> **mcduck said:**
> ...in addition to that, you can restart the whole graphical desktop using SysRq+k. (works for virtual consoles as well, it simply kills everything in the current virtual console.) That's a bit smoother than a full system reboot, so it's a good idea to try this first and if it doesn't help then the full SysRq+reisub.

i just pointed at a full reboot due to the lack of knowledge on other commands to achieve a specific deactivation of certain graphical entities, thanks for your more specific commands.

---

### Post by mcduck on 2012-01-05
> **Basher101 said:**
> i just pointed at a full reboot due to the lack of knowledge on other commands to achieve a specific deactivation of certain graphical entities, thanks for your more specific commands.
Both magic key commands are pretty much something you'd use at the point when nothing is responding any more and you aren't able to run a normal shutdown command (or interact with your desktop in any way).

So I really would consider commands like *shutdown* a better option. It's just that these might still work in a situation where your only other option would be a hard reset using the power switch.

---

### Post by Basher101 on 2012-01-05
> **mcduck said:**
> Both magic key commands are pretty much something you'd use at the point when nothing is responding any more and you aren't able to run a normal shutdown command (or interact with your desktop in any way).

So I really would consider commands like *shutdown* a better option. It's just that these might still work in a situation where your only other option would be a hard reset using the power switch.

i had very very bad expiriences with simply ```
shutdown
``` as a command...it would shut down to a point where it hangs. And that happens 100% of the time if just "shutdown" is given as the command. I have to use ```
sudo shutdown -h now
``` to shut down properly without hanging if i shutdown by command..

---

### Post by mcduck on 2012-01-05
> **Basher101 said:**
> i had very very bad expiriences with simply ```
shutdown
``` as a command...it would shut down to a point where it hangs. And that happens 100% of the time if just "shutdown" is given as the command. I have to use ```
sudo shutdown -h now
``` to shut down properly without hanging if i shutdown by command..

That seems to happen on certain hardware setups. It's nothing to worry about, though, the system itself has already shut down, it just doesn't power off aftwerwards. You can safely switch off the power using the power button.

(by the way, a shorter version of "*sudo shutdown -h now*" would be "*sudo halt*" ;))

---

### Post by ShadowMage on 2012-01-05
> **Basher101 said:**
> task manager is on KDE.

also to kill a certain process you will either need the name or the process ID. IF you know the name you can kill it with ```
killall [process name]
``` example:```
killall conky
``` For the process ID there was some command but i do not know it...

To kill a process by using the PID, you can use the kill command with the -9 switch, for example
```
kill -9 1234
```To find out the PID of a running process, I usually use the command
```
top
```and then press q to exit "top" and stop it from updating. Note, however, that this'll only show u enough processes to fill up the screen (terminal), so if the process does not show up on the list then there must be a better way of finding it.

Hope this helps.

---

### Post by infinity.quietly on 2012-01-05
You can actually do all of this within the top command. Ctrl+Alt+F1-6 for tty > Log in > Run top > In top, pressing _capital_ M will sort processes by memory usage, while pressing _capital_ P will sort them by CPU usage. Pressing capital R will reverse the sort from hi-lo or lo-hi. Now it should be easy to find the PID of the problem task. > Still in top, you can press k(lower case this time) to show a prompt for killing processes. Then just type in the PID, hit enter, and confirm. > Now you can (q)uit top, exit the console, and Ctrl+Alt+F7 back to the GUI.

---

### Post by 14quartz on 2012-01-05
> **infinity.quietly said:**
> You can actually do all of this within the top command. Ctrl+Alt+F1-6 for tty > Log in > Run top > In top, pressing _capital_ M will sort processes by memory usage, while pressing _capital_ P will sort them by CPU usage. Pressing capital R will reverse the sort from hi-lo or lo-hi. Now it should be easy to find the PID of the problem task. > Still in top, you can press k(lower case this time) to show a prompt for killing processes. Then just type in the PID, hit enter, and confirm. > Now you can (q)uit top, exit the console, and Ctrl+Alt+F7 back to the GUI.
 
[FONT=Comic Sans MS][COLOR=orange]But once the graphic system freezes, I'm unable to goto other consoles too. Even tried magic keys but no luck.[/COLOR][/FONT]
[FONT=Comic Sans MS][COLOR=orange][/COLOR][/FONT] 
[FONT=Comic Sans MS][COLOR=orange]The only option I had is Manual restart.:([/COLOR][/FONT]
[FONT=Comic Sans MS][COLOR=orange][/COLOR][/FONT] 
[FONT=Comic Sans MS][COLOR=orange]If there are any other solution please tell me.[/COLOR][/FONT]

---

### Post by vasa1 on 2012-01-05
> **infinity.quietly said:**
> You can actually do all of this within the top command. Ctrl+Alt+F1-6 for tty > Log in > Run top > In top, pressing _capital_ M will sort processes by memory usage, while pressing _capital_ P will sort them by CPU usage. Pressing capital R will reverse the sort from hi-lo or lo-hi. Now it should be easy to find the PID of the problem task. > Still in top, you can press k(lower case this time) to show a prompt for killing processes. Then just type in the PID, hit enter, and confirm. > Now you can (q)uit top, exit the console, and Ctrl+Alt+F7 back to the GUI.

^^^ Very nice, thank you!

---

### Post by Basher101 on 2012-01-05
my suspicion is a kernel bug. try updating to a newer version or downgrade to one that worked before

---

