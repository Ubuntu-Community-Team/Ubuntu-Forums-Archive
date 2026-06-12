---
title: "Need help with screen"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by jnrobinson on 2012-08-04
I recently replaced a tinycore flavor with Ubuntu Server 12 on my dedicated box, and I'm having some trouble getting used to screen (it was all done by scripts before).

I started several processes on the server itself that I would like to be able to view again via ssh.
When I ssh into the server and type screen -r, I can see that there are several screens available, all of which are listed as (Attached).

How do I view these screens from my computer?
Thanks

---

### Post by codemaniac on 2012-08-04
> **jnrobinson said:**
> I recently replaced a tinycore flavor with Ubuntu Server 12 on my dedicated box, and I'm having some trouble getting used to screen (it was all done by scripts before).

I started several processes on the server itself that I would like to be able to view again via ssh.
When I ssh into the server and type screen -r, I can see that there are several screens available, all of which are listed as (Attached).

How do I view these screens from my computer?
Thanks

```
screen -D -R
```

if you are attaching again, after some period of time, specially if you are now on a different pc, this, will detach first the screen session if necessary, and even logout remotely to attach the session for you.

---

### Post by jnrobinson on 2012-08-04
> **codemaniac said:**
> ```
screen -D -R
```

if you are attaching again, after some period of time, specially if you are now on a different pc, this, will detach first the screen session if necessary, and even logout remotely to attach the session for you.

I'm still having some trouble.
I'm supposed to type 'screen -D -R [pid].tty.host' to redisplay the screen?
All that seems to do is go to a new page that says "New Screen..." in the bottom left that then just resets back to the standard terminal.

However, I can see that it creates a new screen, named something like 8659.8515.tty.host

Of course, some of this could be issues with a someone buggy connection I have with the server right now. I'll get back to you on Sunday when I can connect directly.

Thanks

---

### Post by codemaniac on 2012-08-04
> **jnrobinson said:**
> I'm still having some trouble.
I'm supposed to type 'screen -D -R [pid].tty.host' to redisplay the screen?
All that seems to do is go to a new page that says "New Screen..." in the bottom left that then just resets back to the standard terminal.

However, I can see that it creates a new screen, named something like 8659.8515.tty.host

Of course, some of this could be issues with a someone buggy connection I have with the server right now. I'll get back to you on Sunday when I can connect directly.

Thanks

If you are running multiple screens you need to provide the pid of the screen to resume that screen .
something like below .

```
screen -D -R [pid.]tty.host
```

---

### Post by Cheesemill on 2012-08-04
There is a good screen tutorial here:

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

---

### Post by jnrobinson on 2012-08-04
Oh, ok. I figured it out now, I think.

One other question: through my many mishaps I've created lots of screens I would like to get rid of.
Attaching them and pressing Ctrl-A + k doesn't seem to actually get rid of the screen, as it still appears in the list.

How do I get rid of the screens?

---

### Post by codemaniac on 2012-08-04
> **jnrobinson said:**
> Oh, ok. I figured it out now, I think.

One other question: through my many mishaps I've created lots of screens I would like to get rid of.
Attaching them and pressing Ctrl-A + k doesn't seem to actually get rid of the screen, as it still appears in the list.

How do I get rid of the screens?

Whenever I start a new screen i used to give it a meaningful name with -S switch .

```
screen -S dailyJobCodemaniac
```

It's easier to kill a session, when some meaningful name is given .
The below would kill detached sscreen session named dailyJobCodemaniac .

```
screen -S dailyJobCodemaniac -X quit
```

---

### Post by jnrobinson on 2012-08-04
> **codemaniac said:**
> Whenever I start a new screen i used to give it a meaningful name with -S switch .

```
screen -S dailyJobCodemaniac
```

It's easier to kill a session, when some meaningful name is given .
The below would kill detached sscreen session named dailyJobCodemaniac .

```
screen -S dailyJobCodemaniac -X quit
```


Excellent, thank you very much

---

