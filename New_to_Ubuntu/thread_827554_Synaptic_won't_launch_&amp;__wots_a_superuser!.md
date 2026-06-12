---
title: "Synaptic won't launch &amp;  wots a superuser!"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by reezam on 2008-06-12
When I try to launch Synaptic it tells me: E: dpkg was interrupted, you must run 'dpkg --configure - a' to correct the problem. 
E: _cache->open() failed, please report.

Now that I have figured out where the Terminal is (!) and run the command the response is 'requested operation requires superuser privilege'. This doesn't sound promising as I do not feel remotely as though I should have any of those.
Anyway I have to get it sorted - please let me know what to do next

---

### Post by Joeb454 on 2008-06-12
If you've found the terminal run ```
sudo dpkg --configure -a
``` It will ask for your password.

When you enter your password in a terminal, it will not show anything being entered, rest assured your password ***is*** being read :)

---

### Post by aysiu on 2008-06-12
And don't forget to close Synaptic before running that command.

---

### Post by Xiong Chiamiov on 2008-06-12
Superuser is a term meaning a user with, well, super powers!

When you do things normally, they run with limited priviledges, so as to prevent applications from doing things they shouldn't.  When you prepend "sudo" to a command, it will run it as root (with no restrictions).

For the future, there are two nifty things about sudo.
a) If you run a command and it complains about priviledges, entering
```

sudo !!

```
will run the previous command as root.
b) Whenever you run a graphical application (like Nautilus or Gedit) as root, use gksudo instead of sudo, like so:
```

gksudo nautilus

```
This prevents some annoying permissions issues from occuring.

---

### Post by cariboo on 2008-06-13
Just to make it even clearer sudo = superuser do

Jim

---

### Post by Xiong Chiamiov on 2008-06-13
Ah yes.  Most of the seemingly random linux commands actually *do* make sense; they're just shortened far too much to make sense of them by guessing.

For instance, fsck stands for file-system check, but is more generally used as an expression of annoyance when your computer isn't doing what you think it should be.

---

### Post by cariboo on 2008-06-13
Remember if you're every in doubt about a command you can always run

```
man <command>
```

in a terminal to find out what it is and how to use it. Some of the manuals even have example commands.

enter man man and you get a whole page of info
enter man woman and you get No manual entry for woman

Jim

---

### Post by Trail on 2008-06-13
> **Xiong Chiamiov said:**
> 
sudo !!

Hmm why had I never thought of that? Heh. Nice.

---

### Post by Cadmus on 2008-06-13
I once heard the reson for why so many commands have truncated names is during development the link between the computer and the developer's terminal was so slow that it was taking an appreciable amount of time for commands to be typed. So they just truncated the commands to two or three letters. [citiation needed]

---

