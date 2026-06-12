---
title: "how to know when a terminal is closed"
date: 2013-01-20
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-20
Hello,
Is there a way to know when a terminal is closed? It would have been so easy if we always log out of a terminal using the shell command,**exit**. But the thing is, most times, we just press the GUI 'X' button to close the terminal.  
Is there a way to know when a terminal is closed even when we just close it using GUI ?

Thanks.

---

### Post by ofnuts on 2013-01-20
> **IAMTubby said:**
> Hello,
Is there a way to know when a terminal is closed? It would have been so easy if we always log out of a terminal using the shell command,**exit**. But the thing is, most times, we just press the GUI 'X' button to close the terminal.  
Is there a way to know when a terminal is closed even when we just close it using GUI ?

Thanks.
The question is who/what wants to know? A completely external program?  A process running in that window?

---

### Post by deadflowr on 2013-01-20
You can open up a system monitor and look to see if your terminal is listed or not in the processes section.
I don't know about other DEs, but both gnome and kde have this capability. Look for either gnome-terminal or konsole.
If you're talking about a tty shell(when you ctrl+alt+f1 or f2, etc) then I don't know.

---

### Post by dwhitney67 on 2013-01-20
> **IAMTubby said:**
> Hello,
Is there a way to know when a terminal is closed? It would have been so easy if we always log out of a terminal using the shell command,**exit**. But the thing is, most times, we just press the GUI 'X' button to close the terminal.  
Is there a way to know when a terminal is closed even when we just close it using GUI ?

Thanks.

Most times (that is, 99.44% of the time), I press ctrl-d to exit a terminal.  Removing one's hands from the keyboard to reach for the mouse and then aiming for the X is soooo time consuming.  So is typing 'exit'.

---

### Post by Paddy Landau on 2013-01-20
> **IAMTubby said:**
> Is there a way to know when a terminal is closed?
Yes. It closes. I know that sounds trite, but it really is that easy.

You have several methods:

[LIST=1]
[*]Press the [FONT=Lucida Console]x[/FONT] button.
[*]Use the menu File > Close Window.
[*]Press [FONT=Lucida Console]Shift+Ctrl+Q[/FONT].
[*]Press [FONT=Lucida Console]Ctrl+D[/FONT].
[*]Type [FONT=Lucida Console]exit[/FONT] and press Enter.
[/LIST]
They all work. Numbers 1–3 tell the GUI to close, which closes Bash. Numbers 4 and 5 tell Bash to close, which causes the GUI to close. Subtle difference, same result.

---

### Post by Habitual on 2013-01-20
> **Paddy Landau said:**
> Yes. It closes. I know that sounds trite, but it really is that easy.

You have several methods:

[LIST=1]
[*]Press the [FONT=Lucida Console]x[/FONT] button.
[*]Use the menu File > Close Window.
[*]Press [FONT=Lucida Console]Shift+Ctrl+Q[/FONT].
[*]Press [FONT=Lucida Console]Ctrl+D[/FONT].
[*]Type [FONT=Lucida Console]exit[/FONT] and press Enter.
[/LIST]
They all work. Numbers 1–3 tell the GUI to close, which closes Bash. Numbers 4 and 5 tell Bash to close, which causes the GUI to close. Subtle difference, same result.

Excellent summary!

3.a Use Alt+F4
3.b Use Alt+Spacebar > C
same disclaimer "Subtle difference, same result."
[FONT=Lucida Console]
All these mechanisms work here on my Slackware14_64_multilib > Xfce 4.10 > Terminal 0.4.8, so I'd expect|guess that they'd close another terminal on another OS/distribution in exactly the same way.

Ctrl+[dD] is bar far, the quickest way out.
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) seems apropos ;)

Enjoy!
[/FONT]

---

### Post by IAMTubby on 2013-01-20
> **ofnuts said:**
> The question is who/what wants to know? A completely external program?  A process running in that window?
ofnuts, thanks a lot. you just made me think.
Let's say this is the requirement. I want to maintain a log each time I close a terminal. Something like
```

5:23 pm
6:24 pm
7:39 pm

```
So, I think it should be a daemon running in the background and keeps grep'ping for gnome-terminal. Am I correct ? Please advise.

> **deadflowr said:**
> Look for either gnome-terminal or konsole.

Thanks a lot deadflowr for that, very useful.

> **dwhitney67 said:**
> I press ctrl-d to exit a terminal.  
Thanks dwhitney, didn't know the shortcut.

> **Paddy Landau said:**
> 
You have several methods:

Thanks Paddy for the summary

> **Habitual said:**
> 
Ctrl+[dD] is bar far, the quickest way out.

Thanks for that Habitual

---

### Post by Cheesehead on 2013-01-20
> **IAMTubby said:**
> Is there a way to know when a terminal is closed even when we just close it using GUI ?

Step 1 is to figure out the PID of the terminal window.
Step 2 is to monitor that PID in /proc/$PID. When it vanishes, the terminal is closed.

Here's one easy way to accomplish Step 1 from within the relevant window:
```
ps | grep bash | cut -d' ' -f2
```

Step 2 is just as easy if you know the PID (step 1) and use any of the many inotify tools.

---

### Post by IAMTubby on 2013-01-20
> **Cheesehead said:**
> Step 2 is to monitor that PID in /proc/$PID. When it vanishes, the terminal is closed.
Step 2 is just as easy if you know the PID (step 1) and use any of the many inotify tools.
Cheesehead, thanks a lot for that. This is the output of step1.
```

$ ps | grep bash | cut -d' ' -f2
pts/0

```

Now my question is, 
what is it that should be monitoring whether pts/0 is running, is it a daemon ? (cuz, a daemon is not associated with a shell and can run even when the shell is not active)

Please advise.
Thanks.

---

### Post by ofnuts on 2013-01-20
> **IAMTubby said:**
> Cheesehead, thanks a lot for that. This is the output of step1.
```

$ ps | grep bash | cut -d' ' -f2
pts/0

```Now my question is, 
what is it that should be monitoring whether pts/0 is running, is it a daemon ? (cuz, a daemon is not associated with a shell and can run even when the shell is not active)

Please advise.
Thanks.
Strange... you should have gotten a process id...

---

### Post by Paddy Landau on 2013-01-20
> **Habitual said:**
> 3.a Use Alt+F4
3.b Use Alt+Spacebar > C
Thanks — I forgot about those obvious ways!

I also forgot about [FONT=Lucida Console]Ctrl+Shift+W[/FONT].

> **IAMTubby said:**
> I want to maintain a log each time I close a terminal.
Hmm, you have a bit of a problem.

[LIST=1]
[*]You can have bash processes that are *not* running as part of a terminal. For example, if a script was started by cron or Alt-F2. So you can't use [FONT=Lucida Console]grep[/FONT] [FONT=Lucida Console]bash[/FONT] as Cheesehead suggested; you need to use the terminal name, namely [FONT=Lucida Console]gnome-terminal[/FONT].
[*]A terminal may have tabs. When one tab closes, the terminal process is still alive.
[*]Worse still, when you have multiple windows of [FONT=Lucida Console]gnome-terminal[/FONT] open, they are all a single process. Therefore, the process ends only when *all* of their windows are closed.
[/LIST]
If you want to record when all processes have closed, instead of a dæmon, you could go for using a script. The script would be something like:
```
#!/bin/bash
gnome-terminal
echo $( date '+%F %T' ) >>${HOME}/gnome-terminal.log
```Use this script instead of the usual method to start [FONT=Lucida Console]gnome-terminal[/FONT].

But:

If [FONT=Lucida Console]gnome-terminal[/FONT] is already running, this script will open a new window but will end immediately, logging closure even though the window was not closed!

So, you need to decide precisely what you want to do! Please be very clear and precise on what you want, and perhaps we can help with it.

---

### Post by ofnuts on 2013-01-20
> **Cheesehead said:**
> Step 1 is to figure out the PID of the terminal window.
Step 2 is to monitor that PID in /proc/$PID. When it vanishes, the terminal is closed.

Here's one easy way to accomplish Step 1 from within the relevant window:
```
ps | grep bash | cut -d' ' -f2
```Step 2 is just as easy if you know the PID (step 1) and use any of the many inotify tools.

Still some fuzziness in the specs:
- Pid of terminal window or of bash instance?
- Bash or sh or whatever?
- How about tabbed terminal windows?
- How about eventual bash child processes

Assuming we want to know only about the bash 'parents',  I would have a bit of code in ~/.bashrc (which is source only by "interactive" bash instances) that sends the notification with the pid to the daemon (or writes it in some known file or creates a $$.pid file in some known directory). Then the daemon checks for only the bash PIDs it has been told about.

---

### Post by Paddy Landau on 2013-01-20
> **ofnuts said:**
> Assuming we want to know only about the bash 'parents',  I would have a bit of code in ~/.bashrc (which is source only by "interactive" bash instances) that sends the notification with the pid to the daemon (or writes it in some known file or creates a $$.pid file in some known directory). Then the daemon checks for only the bash PIDs it has been told about.
That would work!

---

### Post by Cheesehead on 2013-01-20
> **ofnuts said:**
> Still some fuzziness in the specs:
- Pid of terminal window or of bash instance?
- Bash or sh or whatever?
- How about tabbed terminal windows?
- How about eventual bash child processes

Usually a single terminal application can open multiple threads (tabs or windows). But *each* tab or window has a separate TTY assignment.

For example, here's a single terminal window with seven open tabs. It would look the same if it were eight separate terminal windows.
```
me@me:~$ ps -e | grep terminal
13079 ?        00:00:00 xfce4-terminal
me@me:~$ ps -e | grep bash
13086 pts/0    00:00:00 bash
13338 pts/3    00:00:00 bash
13495 pts/4    00:00:00 bash
13629 pts/5    00:00:00 bash
13667 pts/6    00:00:00 bash
13783 pts/7    00:00:00 bash
13950 pts/8    00:00:00 bash
```

Each bash process is, of course, a child process of the terminal. If your favorite shell is different, then that shell will appear instead. But let's stick to basics.

In turn, each bash process is the parent of whatever you run in that tab. 

That ps listing shows both the TTY assignment and the PID of each tab or window. When the window closes, the corresponding PID entry in /proc changes.

To discover the change, you can use inotify to watch /proc. That's easy - one command. Or you can write a daemon to monitor some other way. I think that's harder, but your mileage may vary.

The only problem left is to discover which tab/window corresponds to which TTY entry. They are usually assigned in the order opened, so if you are clever you can track it that way. But it's usually easier to simple have each tab or window find out, and pass that information to your tempfile or socket or whatever.

For example, here's how to discover one tab's TTY assignment. (Hint: this tab is "pts/8"):
```
me@me:~$ ps
  PID TTY          TIME CMD
13950 pts/8    00:00:00 bash
15282 pts/8    00:00:00 ps
```
As you can see, it doesn't matter what else is running on this tab or window - all we need is the TTY assignment, which will be the same for all processes in this listing.


Er, does that make things clearer? Or confuse further?
Since you already have a script to do this stuff, I'm sure you know it already.

---

### Post by ofnuts on 2013-01-21
> **Cheesehead said:**
> As you can see, it doesn't matter what else is running on this tab or window - all we need is the TTY assignment, which will be the same for all processes in this listing.

At that point, do we really care about actual pts/process associations? Just do periodically a brute force
```

ps -ea | grep -o -Ee '[[:space:]]pts/[[:digit:]]+[[:space:]]' | sort -u | wc -l

```
to count the  active terminals and compare with the previous count...

---

### Post by Paddy Landau on 2013-01-21
> **Cheesehead said:**
> Usually a single terminal application can open multiple threads (tabs or windows). But *each* tab or window has a separate TTY assignment…
Cheesehead, I've learned two new things from your post, thank you.

---

### Post by Cheesehead on 2013-01-21
> **ofnuts said:**
> Just do periodically a brute force
```

ps -ea | grep -o -Ee '[[:space:]]pts/[[:digit:]]+[[:space:]]' | sort -u | wc -l

```
to count the  active terminals and compare with the previous count...

That's a clever way to do it!
I like it.

---

### Post by Paddy Landau on 2013-01-21
> **Cheesehead said:**
> To discover the change, you can use inotify to watch /proc.
I have tried to use the command inotifywait, but it seems to have a problem with /proc. To illustrate…

This works:
```
[COLOR=DimGray]$[/COLOR] mkdir newdir
[COLOR=DimGray]$[/COLOR] inotifywait --event delete_self newdir
Setting up watches.  
Watches established.
*[FONT=Arial]# The inotifywait command waits until I run the following command from another terminal:[/FONT]*
[COLOR=DimGray]$[/COLOR] rmdir newdir
*[FONT=Arial]# The inotifywait command terminates:[/FONT]*
newdir/ DELETE_SELF
[COLOR=DimGray]$[/COLOR] 
```However, when you use inotifywait to watch a process in [FONT=Lucida Console]/proc[/FONT], it no longer works. [FONT=Lucida Console]inotifywait[/FONT] just hangs:
```
[COLOR=DimGray]$[/COLOR] ps -e | grep -F gcalctool
24897 ?        00:00:00 gcalctool
[COLOR=DimGray]$[/COLOR] inotifywait --event delete_self /proc/24897
Setting up watches.  
Watches established.
*[FONT=Arial]# The inotifywait command waits forever, even after I close gcalctool and /proc/24897 no longer exists.[/FONT]*
```So, I cannot use inotifywait to watch for a process.

Any ideas how to fix this?

---

### Post by IAMTubby on 2013-01-21
I have read your suggestions. 
I am writing a daemon which does the following

Step1 : Look for **ps -u myname | grep bash | cut -d' ' -f2**. This will give me the PID of the bash shell I'm using right. 

Step2 : After every 2 mins, repeat the above command and see if the PID still exists, 

Step3 : If yes, repeat Step2, 
        If no, write to a file with time.

Shall get back to all of you.

Thanks. :)

---

### Post by ofnuts on 2013-01-21
> **IAMTubby said:**
> I have read your suggestions. 
I am writing a daemon which does the following

Step1 : Look for **ps -u myname | grep bash | cut -d' ' -f2**. This will give me the PID of the bash shell I'm using right. 

Step2 : After every 2 mins, repeat the above command and see if the PID still exists, 

Step3 : If yes, repeat Step2, 
        If no, write to a file with time.

Shall get back to all of you.

Thanks. :)

No, this will give you the pid of one of the shells. If you have several you won't see the others.

---

