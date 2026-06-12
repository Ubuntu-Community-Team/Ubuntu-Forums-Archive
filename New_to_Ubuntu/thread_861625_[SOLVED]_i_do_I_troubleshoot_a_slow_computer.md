---
title: "[SOLVED] i do I troubleshoot a slow computer?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-16
here's what i know.  I got my air card working last night.  now this morning it says there is already an instance of it running.  I don't see this though.   so It's getting stuck when i try and connect.  
also to note.  I have a couple op systems on virtual box and well yesturady in addition to getting my aircard working for ubuntu I also got it working for mandriva.  I ended up updating everything.   I have had my alotted disk space made well before yesturday so I don't think VB is the problem.  but these are the two things i know about recent events preceding my real slow system.  for example I open a terminal and it taks 129 secondsto come to screen.  how do I figure this out?

---

### Post by Het Irv on 2008-07-16
What specs do you have on that computer?  VB takes alot of RAM and that could slow down your computer.

---

### Post by MatthewPlanchard on 2008-07-16
Definitely consider upgrading your RAM if it's low, but to speed things up a bit, [this link]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/") has an excellent guide that can be downloaded either as a Zim Wiki or an HTML file.

For boot speeds there is also an excellent guide on how to speed up boot time using readahead [here]("http://ubuntuforums.org/showthread.php?t=565651").

Blessings.

---

### Post by adamogardner on 2008-07-16
ok  what is the command formula to discover where my memory has gone?   and what is whith this other instance running; how do I stop it?  The specs on my computer are somewhere around awesome, but Like we know I have virtual box bogged down with basically all it's stock options.  However I remember reading that what is inside the VB is partitioned from host, and since I've had this box (except for yesturdays upgrades) for a few weeks now, I don;t think it's that, but the aircard/kppp error jam.  I could investigate this a bit if I knew my way aroiund the CLI better.

---

### Post by Het Irv on 2008-07-16
I know in Gnome you can see a list of the running processes in the system monitor.  It shows mem usage and all that great stuff.  But I am not sure where that utility is in KDE, It should be there, but I am not familiar with KDE.

---

### Post by adamogardner on 2008-07-16
thanks   I'm in windows presently so I can be here right now.  before I go over to look at that I'd like to have some CLI manuevers at my disposal,because thats where I really want to be (i don't know why)  Anybody?
I have gnome too btw

---

### Post by unutbu on 2008-07-16
```
ps axuw | less
```
   ps axuw will show you all the processes running
   'less' allows you to page through the output

The second column in the output are process ID numbers (PIDs).
To kill a process that you own type:
```

kill PID
```

Sometimes they refuse to die, in which case you can type
```

kill -9 PID
```

This sends the signal directly to the kernel, so it always works, though it is not a good way to terminate programs in general. (It might leave a memory leaks which won't be fixed until you reboot?)

To kill a process owned by root:
```

sudo kill PID
``` or
```

sudo kill -9 PID
```
Of course, think carefully before you do this. In general, unless the root process is writing something to disk (in which case killing can be very bad), killing even root processes will at most only screw up your current session and can be fixed with a reboot.

To view the processes that are consuming the most CPU time:

```
top
```

---

### Post by Het Irv on 2008-07-16
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)
a bit old, but I think it is still applicable.

As a side note: Ubuntu and its derivatives are trying to get away from the CLI some.  Everything is still available thought the terminal as always.  But many things also have GUI's.  Personally I am more familiar with GUI than CLI.

---

### Post by adamogardner on 2008-07-16
Thats interesting because I am so hooked on the CLI, and learning it's intricacies, My ubuntu is a finely crafted sportscar and the CLI is like manual tranmission.  Who wants to drive a ferrari automatic?  No for the real driving experience I go with manual CLI I just discovered it too and linux and all so forgive my childish delight in the kingdom of bash and my loyal commands who work for me to build file village.

nice link btw.
oh hi unutbu.  Thanks for all that!  I didn't even see you down there.

---

### Post by adamogardner on 2008-07-17
unutbu, that was just what I was looking for.  I have one question I cant find info or a man page on axuw.  What is that?

---

### Post by unutbu on 2008-07-17
Try 
```

man ps
```

auxw are options sent to the ps command.
For some reason unbeknownst to me ps accepts these options without the usual dash:

```
ps axuw
```
and
```
ps -axuw
```
are equivalent.

---

### Post by cariboo on 2008-07-17
The man page you are looking for is ps:

```
man ps
```

Jim

---

