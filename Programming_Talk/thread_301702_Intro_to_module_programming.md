---
title: "Intro to module programming"
date: 2006-11-17
forum: Programming Talk
---

### Post by DrObviousSo on 2006-11-17
Are there any good introductions to module programming out there?  I'm an experienced C programmer, but I'm new to linux, and I want to play around with module programming.

Among other things, I wanted to play around with security modules, so if there is a repository of existing modules that I could look at / play around with, a link to those would be very helpful too.

My end goal is to create a module that will sandbox a program, and cut it off from the rest of the OS, so again, any links to anything like that would be great.

Thanks

---

### Post by THaugland on 2006-11-17
[http://www.tldp.org/LDP/lkmpg/2.6/html/index.html](http://www.tldp.org/LDP/lkmpg/2.6/html/index.html) 

By the way: I am not sure that you can sandbox any process using a module. I am afraid, that you will have to make some changes to the kernel - specifically the implementation of "fork". How do you plan to implement this?

---

### Post by lloyd mcclendon on 2006-11-17
user mode linux is what you should use to do module development.  if you make one mistake in your module have fun turning your pc off.  user mode linux is like a whole linux os running as a user-level prorgram in real linux.  which is coincedentially what you're trying to write a module for.  maybe you could just use that.  it's pretty neat, you type the command and you see all the bootup messages and such.  if your module segfaults or anything you just kill the process and start it up again.  if it segfaults in regular linux you're holding in the power button

i got it all setup years ago, unfortunately i have no idea what i did.  i remember there were some good guides out there.  at the time it had a few annoying bugs, i'm sure they've been fixed by now.

which reminds me i should get back into that because i sometimes run a server.  if someone is pissing around all they can do is piss in the sandbox and not screw anything important up

---

### Post by amo-ej1 on 2006-11-20
Linux Device Drivers third edition ( [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/) ) is probably what you want it gives a great introduction to modules and more generic kernel stuff.

What your initial goal is ... i have my doubts about it, if you want to sandbox things, use java ;-) in fact regular processes are 'already' sandboxed and i think trying to sandbox it through a module will only introduce additional issues.

---

### Post by fct on 2006-11-20
Linux Kernel Development by Robert Love is a good book for that too.

---

### Post by amo-ej1 on 2006-11-20
true, but love's book focuses more on the foundations of the linux kernel and hardly on any practical things like how do i interact with /proc, how does a /dev/ entry work what is a module uberhaupt ... love's book is more like 'how is memory internally allocated' and 'how does process scheduling work' the best solution would be putting both books in a blender ;)

---

