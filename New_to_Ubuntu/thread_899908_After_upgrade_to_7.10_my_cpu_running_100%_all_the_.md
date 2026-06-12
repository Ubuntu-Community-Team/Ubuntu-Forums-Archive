---
title: "After upgrade to 7.10 my cpu running 100% all the time"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Milan Josipovic on 2008-08-24
Hi all

J have dell latitude d400 laptop,with cpu on 1.6 ghz,512 mb ram.....
J upgraded my ubuntu from 7.04 to 7.10.
But my cpu is running 100% all the time.
Why is this happenig?
Btw J used system monitor.
Here is screenshot.

Please help

Thanks

---

### Post by zamadatix on 2008-08-24
your network looks like its being used alo (mine rarely goes that high) but how about a screenshot of processes ordered by cpu usuage?

---

### Post by Milan Josipovic on 2008-08-24
Here it goes...
U have two pics because my monitor is to small to prewiev all processes in one pic.
But all processes are there...:)

---

### Post by Milan Josipovic on 2008-08-24
btw

J am downloading k3b so thats why network is looking like that

---

### Post by Milan Josipovic on 2008-08-24
btw

J am downloading k3b so thats why network is looking like that

---

### Post by zamadatix on 2008-08-24
you could have hti %cpu and it wouldve shown processes by the cpu usuage which wouldve shown all using yourcpu. from the looks of it your using 23%... but you are missing a bit at the end (a little scroll on that last image) but im assumeing thats 0cpu. strange

---

### Post by Milan Josipovic on 2008-08-24
Sorry about that 
here it goes...

---

### Post by zamadatix on 2008-08-24
hmm weird. my ubuntu (8.10 alpha) runs about 10% with pidgin firefox and system monitor open on a 2ghz machine with less ram. seeing the listed processes i wonder if there are rocesses not shown on that lit. also is it always like that or just when your downlaoding stuff? and do you have the latest driver.

---

### Post by Milan Josipovic on 2008-08-24
well it is allways like that.
how can j check and update drivers?
j am noob...

---

### Post by zamadatix on 2008-08-24
i think the updater might check but you should be able to locate your driver in a package manager (add remove works) and there you can see. 


though im interested as to why you upgraded to 7.10 not 8.04?

---

### Post by Milan Josipovic on 2008-08-24
few days ago j bought a book called Official Ubuntu book,and dvd with 7.04 came with it.
so j notice in update manager upgrade to 7.10 and voila...
Could J upgraded it directly to 8.04?

About drivers update...J have restricted drivers manager...is that it?
From there j cant see update of drivers.
Please explain me step by step how to chek drivers?
Sorry to bug you..

---

### Post by zamadatix on 2008-08-24
ya. i upgraded directly from 8.04 (takes an hour...) to 8.0 alph but i dont recommend going that far (not very stable) but you should be able to jsut follow this link [here]("http://ubuntu-tutorials.com/2008/04/23/how-to-upgrade-ubuntu-710-to-ubuntu-804/").

---

### Post by bruno.braga on 2008-10-09
I kind a have the same problem here. After upgrading from 8.04 to 8.10, my System Monitor Resources displays 100% of CPU, but when I check the list of processes, none is using not even close to that (all of them around zero). However this seems more like a display problem, since I dont feel my computer slower because of that.

This thread is about the 7.10, but I notice a strange coincidence here... Does anyone know what could it be?

Thanks in advance.

---

### Post by Enternald on 2008-10-09
I think there is one terminal command that show all processes i can't REMEMBER it, it shows how many processor uses in example compiz, when spining cube etc.

---

### Post by Enternald on 2008-10-09
Write "ps" (without ") if you wnt to know more about ps, write "man ps"

---

### Post by Enternald on 2008-10-10
somewhere in properties of system monitor should be graph enable to show processes by all users not only yours.

---

### Post by olmecnz on 2008-11-08
I encountered this issue when I upgraded (via auto update) from 8.04 to 8.10

Processor shows 90-100% at all times when viewing graph in system monitor however all active processes only add to about 30%

If system monitor is removed from the panel bar it seems like processor usage drops back to a more actual level because when I start process manager / system monitor graph it shows an immediate jump on the graph and then stays level round 100%

Actual performance / user experience seems basically fine although the fan on my laptop seems to work harder.

Note:
When starting gnome system monitor from terminal I see the following warning - SELinux was found but is not enabled

---

### Post by jpoRS on 2008-11-08
olmecnz: Here is a discussion that is more up to date: [LINK]("http://ubuntuforums.org/showthread.php?t=973992")

Good luck
jim

---

