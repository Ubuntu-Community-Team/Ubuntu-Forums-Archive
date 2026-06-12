---
title: "startx does not work in Oneiric"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by Arfalarf on 2011-11-06
I just upgraded ubuntu to OO and I cannot get into the GUI as myself.  I created a new username which can log straight in to the GUI at startup, but neither username can run startx from the terminal.  Also, when my original username tries to get into the GUI from startup it flashes text really fast and goes back to the login screen.  The error I get with startx is

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

---

### Post by wojox on 2011-11-06
> **Arfalarf said:**
> I created a new username which can log straight in to the GUI at startup, but neither username can run startx from the terminal.

startx starts the X Window System which is already running. Why would you need to start it again?

---

### Post by apollothethird on 2011-11-06
> **Arfalarf said:**
> I just upgraded ubuntu to OO and I cannot get into the GUI as myself.  I created a new username which can log straight in to the GUI at startup, but neither username can run startx from the terminal.  Also, when my original username tries to get into the GUI from startup it flashes text really fast and goes back to the login screen.  The error I get with startx is

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

Try:

```

startx -- :n

```Let ":n" be a number, in this case, other than "0" which is already running.

I'm sure you want to use the startx option so that you can see what error message you can't see from the graphic login.

By the way, it's unlikely that you'll have Unity (or any other menu manager).  You can start files by running the commands in a terminal.  If you have gnome-panel installed you can run, from a different console:

```

export DISPLAY=:n
gnome-terminal&
gnome-panel&
nautilaus /usr/share/applications

```Those items should get you started in the graphic environment.

You can find your graphic terminal by hitting "F7, F8, F9, etc" until you locate the new one.  You can find your consoles from the graphic window by hitting Alt-FX (with X being the console you want to go to).

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by alphacrucis2 on 2011-11-06
> **Arfalarf said:**
> I just upgraded ubuntu to OO and I cannot get into the GUI as myself.  I created a new username which can log straight in to the GUI at startup, but neither username can run startx from the terminal.  Also, when my original username tries to get into the GUI from startup it flashes text really fast and goes back to the login screen.  The error I get with startx is

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.


Sounds a bit like this:

[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233)

---

### Post by Arfalarf on 2011-11-06
> **wojox said:**
> startx starts the X Window System which is already running. Why would you need to start it again?

Because I cannot log in through the normal graphical procedure.  I cannot get past the login screen so I hit Ctrl-alt f4 to try to get into gnome through the command line.

I think it may have something to do with the fact that I had the system set to log me in automatically (w/o password).  How do I change it so the GUI asks for my password at login?

---

### Post by Arfalarf on 2011-11-06
> **alphacrucis2 said:**
> Sounds a bit like this:

[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233)

You are absolutely right!  I did what they said in that thread (sudo rm .Xauthority) and it works now.  I guess I should have done a better search of previous threads.

---

