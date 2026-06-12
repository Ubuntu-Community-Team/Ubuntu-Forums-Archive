---
title: "Exiting the Terminal"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Majiq on 2008-11-12
So, this is a somewhat hard to explain question, but it goes something like this:

When you start a command in the background from the terminal using the & after the command, you force the command to the background. From here, if you click the x on the gnome-terminal window, the terminal closes and the program you were running also closes. However, if you instead type exit in the terminal, it will close but the processes it spawned remain running.

What does the terminal do to pass these commands up to the system, and is there any way to do that without exiting the terminal? Said another way, what is the exact execution of the exit command, and can the commands used in exiting be used in other contexts?

---

### Post by Titan8990 on 2008-11-12
> 
What does the terminal do to pass these commands up to the system, and is there any way to do that without exiting the terminal?

Are you talking about killing the program?

---

### Post by eolson on 2008-11-12
I'm a little confused ... could you explain it another way please.

---

### Post by eolson on 2008-11-12
Let me try a guess ...

When you type exit in the terminal it exits leaving the system with the status of the last command executed which would be putting the process in the background.

If you click on the x the last command executed in the one before you put the process in the background.

Like I said, just a guess.   I know the first part is correct, not sure of the second.

---

### Post by Titan8990 on 2008-11-12
Still a bit confused but if you don't want the process to end when you click the "x" you need to do:

COMMAND & disown


Example:

gedit & disown


Then you can click the X and gedit will remain open.

---

### Post by bodhi.zazen on 2008-11-12
Usually when you start an application from a terminal it will close when you close the terminal (even if it was started in the background with a &).

You have several options if you want the command  to continue to run :


[LIST=1]
[*]Use screen.
[*]use nohup (nohup <command>).
[*]use () (<command>) (not as reliable).
[*]use detach.
[*]deamonize the process (as in the init scripts).
[/LIST]
Edit: And disown :twisted:

Screen :

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

    [http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

    [http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

Can you give us more information about the process you are talking about ?

---

### Post by psusi on 2008-11-12
If you try to exit with background jobs running the shell will warn you that you still have background jobs running.  If you try to exit a second time, the background jobs don't keep running -- they die.

---

### Post by Majiq on 2008-11-12
I guess the best way to re explain this is a walkthrough of what I do. Let me assume for the moment that everyone has vlc. Open a new gnome-terminal window, and type in
```

vlc &

```

You'll probably see some debugging startup information in the terminal and then elsewhere, a GUI for VLC will popup. At this point, click the x on the gnome-terminal window. This (for me at least) will close both the terminal window and the vlc.

However, if you startup a terminal window, then tell it to start vlc the same way, and then type in
```

exit

```
in the terminal, the vlc window stays open.

This difference in behavior where the process seems to get passed up to the system is what I'm referring to and wanting to emulate.

---

### Post by aysiu on 2008-11-12
Just type ```
*nameofcommand* &
``` and then hit **Enter** and then closing the terminal should not close the program.

---

### Post by Majiq on 2008-11-12
Interesting. I notice that when I use the disown command and leave the window open, the application stays associated with the pts that it started from, at least when you issue the ps -e command. Then, when I quit the terminal, it then has a '?' under the TTY column. 

Is there a way to force this disassociation earlier? Also, what if you have a process that you already started and want to send it there without closing out of the terminal (i.e. if you were also running things in those terminals)?

---

### Post by ncanna1 on 2008-11-12
Why not just use a tabbed terminal (like yakuake) and run different processes in different terminals?

---

### Post by Majiq on 2008-11-12
> **bodhi.zazen said:**
> Usually when you start an application from a terminal it will close when you close the terminal (even if it was started in the background with a &).

You have several options if you want the command  to continue to run :


[LIST=1]
[*]Use screen.
[*]use nohup (nohup <command>).
[*]use () (<command>) (not as reliable).
[*]use detach.
[*]deamonize the process (as in the init scripts).
[/LIST]
Edit: And disown :twisted:

Screen :

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

    [http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

    [http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

Can you give us more information about the process you are talking about ?
Thanks for that list. Just some things about them though:

2. nohup doesn't seem to disassociate it from the terminal, so if I click the x, it still closes the associated processes

3. Why is this unreliable? Also, why does it start it up as a background process?

4. I don't know what you mean by detach, unless you mean using the ampersand. Is that what you mean?



So, the reason I ask, aside from just being interested, is because I do have a habit of starting up programs from terminals and then sometimes I want some programs to last longer than others, and I don't think as I Alt+F4 through the windows and hit a terminal. I'm still unsure as to how to detach the process while it is running.

Edit: I mean I don't know how to disassociate the process from the terminal while it is running.

Also, this just came up because of another post, is it possible to (for lack of knowing terminology) tether a background process to a terminal? For example, if you do a ps -e, is there any way to grab the process running under '?' and have them output to the current terminal?

---

### Post by Majiq on 2008-11-12
> **ncanna1 said:**
> Why not just use a tabbed terminal (like yakuake) and run different processes in different terminals?
I'm liberal with my use of Ctrl+Q and Alt+F4. I mean, I could change my habits, but this is more inspiring for discussion and my understanding of what's going on.

---

### Post by aysiu on 2008-11-12
> **Majiq said:**
> I'm still unsure as to how to detach the process while it is running. Did you totally ignore my post? Or am I way out of my league, and my post actually has nothing to do with what you're talking about?

---

### Post by Majiq on 2008-11-12
Sorry aysiu, I'm talking about something else. It's not just detaching it, it's detaching and disassociating it. Your help was appreciated, but it's not what I'm looking for, because if I just detach it like you said, I can accidentally Alt-F4 my terminal and there goes my detached program with it.

---

### Post by aysiu on 2008-11-12
Whoops. You're totally right. Sorry!

---

### Post by bodhi.zazen on 2008-11-12
> **aysiu said:**
> Did you totally ignore my post? Or am I way out of my league, and my post actually has nothing to do with what you're talking about?

Hey, that is my league :)

Actually Aysiu it is somewhat dependent on the application. Try starting something like xeyes with a & and then close the terminal. I am not sure about xeyes specifically, the two applications that I have had trouble with are abiword and vmware-tools.

The other common usage is for example when you ssh into a (server) and wish a command to continue once you exit the ssh session.

> **Majiq said:**
> Thanks for that list. Just some things about them though:

2. nohup doesn't seem to disassociate it from the terminal, so if I click the x, it still closes the associated processes.

Interesting, I can not recall that ever happening to me with nohup.

Again, try ```
nohup xeyes &
```> 3. Why is this unreliable? Also, why does it start it up as a background process?(foo&) starts foo in a sub shell. It *usually* works. Try

```
(xeyes&)
```> 4. I don't know what you mean by detach, unless you mean using the ampersand. Is that what you mean?No, detach is a command. And I, of course, typed it wrong, try dtach (so sorry).

[http://linux.die.net/man/1/dtach](http://linux.die.net/man/1/dtach)

> So, the reason I ask, aside from just being interested, is because I do have a habit of starting up programs from terminals and then sometimes I want some programs to last longer than others, and I don't think as I Alt+F4 through the windows and hit a terminal. I'm still unsure as to how to detach the process while it is running.

Edit: I mean I don't know how to disassociate the process from the terminal while it is running.

Also, this just came up because of another post, is it possible to (for lack of knowing terminology) tether a background process to a terminal? For example, if you do a ps -e, is there any way to grab the process running under '?' and have them output to the current terminal?This is also a nice link

[http://www.nslu2-linux.org/wiki/HowTo/KeepRemoteConsoleSessionRunning](http://www.nslu2-linux.org/wiki/HowTo/KeepRemoteConsoleSessionRunning)

---

### Post by psusi on 2008-11-12
> **bodhi.zazen said:**
> 
```
(xeyes&)
```No, detach is a command. And I, of course, typed it wrong, try dtach (so sorry).

[http://linux.die.net/man/1/dtach](http://linux.die.net/man/1/dtach)



Seems to be a stripped down version of screen.  Overkill if you don't need to reconnect later.

The reason that hitting X kills the background job is because it sends a SIGHUP to the shell attached to the terminal, which relays it to all background jobs that have not been detached, which causes them to exit by default.  I swear this is supposed to be done no matter how the terminal is closed, but it appears it is NOT being sent when you exit from the shell.  You can set the shell to ignore SIGHUP and this will be inherited by whatever you run:

trap "" HUP
xeyes &

Then close the terminal and xeyes keeps running.  This is what nohup does, as well as redirect output to a file.

xeyes & disown also keeps it running after closing the window.

---

