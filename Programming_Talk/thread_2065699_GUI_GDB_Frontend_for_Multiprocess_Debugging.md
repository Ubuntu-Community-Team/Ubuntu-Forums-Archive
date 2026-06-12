---
title: "GUI GDB Frontend for Multiprocess Debugging?"
date: 2012-10-02
forum: Programming Talk
---

### Post by kmand on 2012-10-02
I admit to being used to debugging on Solaris with dbx and the associated "debugger" GUI. This worked well with multiprocess debugging. You got a window with the status of the parent and any children, and you could switch contexts easily (including source and variable displays, etc).

Is there anything like this for gdb on Linux? You can set follow-fork and follow-exec in gdb, but I haven't seen a GUI that really makes it easy to track and switch debugger context and displays easily. I know about gdbtui, ddd, and xxgdb none of which seem to handle this well.

---

### Post by MG&amp;TL on 2012-10-04
*gdb* seems to be absolutely horrible for multiprocess debugging, sorry. 

That said, multiple IDEs seem to include GUI debugging tools, so you might check those out. I'm currently using Eclipse's one, which is quite good, but I confess I haven't actually used it for multiprocess yet.

I'm not familiar with Solaris's executable format, but is there a reason you couldn't run dbx on Linux?

---

### Post by Majorix on 2012-10-04
I believe GDB is ok. Dbx is proprietary and not necessary when you have GDB. You can use Emacs for a GUI.

---

### Post by kmand on 2012-10-04
dbx is not much different gdb for multiprocess debugging. They both can catch fork/execs and let you manipulate contexts. The thing that worked well in Solaris was a gui frontend called "debugger" for dbx which had gui displays and controls specifically that tracked multiprocess context well. The gdb frontends ddd, xxgdb, gdbtui don't do that. 

I don't know about the emacs frontend, I'm a vi guy and use emacs only when forced. Does it do multiprocess debugging well?

I'm also not an IDE guy. I really just want a debugger not a development environment. I was hoping there was some other gdb frontend I didn't know about.

---

### Post by MG&amp;TL on 2012-10-04
> **Majorix said:**
> I believe GDB is ok.

My mistake. Seems I was reading the wrong/outdated tutorial, I just did some googling and it seems to better than I thought. :)

---

