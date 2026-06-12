---
title: "debugger for teaching"
date: 2008-03-01
forum: Programming Talk
---

### Post by rplantz on 2008-03-01
I've taught assembly language for over 20 years. I have students use a debugger mostly as a learning tool -- to see what is going on in registers, memory, etc.

Since I've started teaching under Linux 9 years ago, I've had my students use gdb. Most of them hate it. They grew up in a gui world. (I grew up in a front panel switch world, so command line gdb is "high level" for me.)

I know that gdb has several gui frontends. For example, I've installed ddd, xxgdb, and insight. So far, it seems like insight would be the best one for my teaching purposes. You can display a memory area and the registers, then single-step through the code and watch things change. This is precisely what beginning assembly language programmers need to see.

But I am a newcomer to Linux gui debuggers. I would like to hear others' opinions about which gui debugger is the best for these teaching purposes.

Keep in mind that these are very simple teaching programs, so there is no real debugging. Just using the debugger to watch changes. And it would be nice if the program is "desktop agnostic."

---

### Post by NathanB on 2008-03-01
I haven't used it, but Evan's debugger looks promissing in the GUI arena:

[http://www.codef00.com/projects.php#Debugger](http://www.codef00.com/projects.php#Debugger)

Okay, the rest of these are not GUI sugestions, but I am pretty sure that I am not alone in thinking that the old DOS DEBUG was a 'really good' learning tool.  In fact, there is a script "floating around" which causes gdb to respond to DOS-DEBUG-type commands.  I'll look it up if you are interested.

Also, someone has written a clone:

[http://modest-proposals.com/Furball.htm](http://modest-proposals.com/Furball.htm)

Some people think ALD is friendly:

[http://ald.sourceforge.net](http://ald.sourceforge.net)

And then there is something that is not GUI nor exactly CUI... it is part of Jeff Owen's AsmIDE:

[http://members.save-net.com/jko@save-net.com/asm/asmbug.htm](http://members.save-net.com/jko@save-net.com/asm/asmbug.htm)

Nathan.

---

