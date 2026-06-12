---
title: "memory help"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by atopthemountain on 2008-10-06
how do i free up memory...my 3 g cpu is down 2 20 mbs....and deleting things doesnt work like it does inwindows

---

### Post by Zzl1xndd on 2008-10-06
Are you trying to free up hard drive space? if so after you delete something you have to empty the trash much like you would empty the recycle bin in Windows.

---

### Post by jerome1232 on 2008-10-06
jast an fyi for the op, when people say 'memory' they often are refering to system RAM, not hard disk space. Try to make it clear whether you are talking about system ram or hard disk space as the two are very different from each other.

---

### Post by OutOfReach on 2008-10-06
> **atopthemountain said:**
> how do i free up memory...my 3 g cpu is down 2 20 mbs....and deleting things doesnt work like it does inwindows

What do you mean by 'deleting things'?

---

### Post by Helios1276 on 2008-10-06
Try using the 'top' command in the terminal to see what processes are running. From there you can decide(with a bit of research) what might be hogging your resources.

---

### Post by seagullplayer77 on 2008-10-06
I'm also curious as to what "deleting things" refers to...but I'll second Helios' post. If you go into a terminal and run "top," it'll list the most memory/CPU intensive processes. You can then determine what program or process is hogging your resources and then kill it...just make sure what you're killing isn't an important process!

---

### Post by atopthemountain on 2008-10-06
how do i free up memory...my 3 g cpu is down 2 20 mbs....and deleting things doesnt work like it does inwindows

---

### Post by OutOfReach on 2008-10-06
Don't double post. [http://ubuntuforums.org/showthread.php?t=940290](http://ubuntuforums.org/showthread.php?t=940290)

---

### Post by Helios1276 on 2008-10-06
Take a little time and state clearly and precisely what you want to achieve, this will speed up the help you get. also, why don't you post the results of 'top' and we might be able to point you in the right direction?

P.s. double posting is frowned upon ;)

---

### Post by overdrank on 2008-10-06
> **atopthemountain said:**
> how do i free up memory...my 3 g cpu is down 2 20 mbs....and deleting things doesnt work like it does inwindows

Hi and please do not make multiple threads on the same issue. Threads merged :)

---

### Post by drowner on 2008-10-06
Atopthemountain:

Do mean free up Hard drive space, and that you have a 3 gig drive which is down to 20 MB?

Or do you mean you have 3gig or RAM which is being used up?

---

### Post by atopthemountain on 2008-10-06
i didnt mean to double post....my bad.........i want to free up my hard disk but cannot locate my trash.....i searched 4 it and only found icons

---

### Post by OutOfReach on 2008-10-06
Right click on the trash icon on the bottom panel and click 'Empty Trash'.

---

### Post by drowner on 2008-10-07
type the following into a terminal:
```

nautilus trash:///
```

That should show you your trash. There should be an option to empty it.

Also, you could click on an empty space on your panel (taskbar) and select 'add to panel', then you can add an icon to quickly access your garbage bin. It should have one in there by default. I assume you have removed it.

---

