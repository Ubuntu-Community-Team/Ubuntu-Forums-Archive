---
title: "shell command to open new terminal...."
date: 2009-07-17
forum: Programming Talk
---

### Post by darkwing_duck on 2009-07-17
Hi and thanks for your help,

I'm trying to port a .bat file that was developed on a Windows machine to start an application.  The application runs in multiple command prompts (and multiple threads).  I've got the application ported to linux now.  However, I want the application to be started the same way as it was on the Windows platform... which is... the user runs the .bat file which then spawns several command prompts; one command prompt for each of the threads in the application.

(One of) my problem(s):
I can't figure out how to write my linux shell script to spawn other terminals and have those terminals execute a command to start its thread while the parent script continues to run in the original/parent terminal.

I've tried to use "gnome-terminal -x <command>" but the terminal that gets spawned just disappears after about 100 milliseconds.

Any help is much appreciated.  I'll continue to check this thread since I've been trying to figure this out for a couple days now.

---

### Post by scorp123 on 2009-07-17
> **darkwing_duck said:**
> I've tried to use "gnome-terminal -x <command>" but the terminal that gets spawned just disappears after about 100 milliseconds. That's because the program in there terminated, so the shell window you spawned will terminate as well.

I'd suggest you call a shell script via "gnome-terminal -x" or "xterm -e" instead of the main program directly. That shell script should of course contain some command towards the end that would keep the terminal window from closing ... maybe something like the "sleep" command? Or some "while 1 > 0" loop that would keep the shell script busy ....

---

### Post by dwhitney67 on 2009-07-17
You need to explain your terminology with respect to your usage of the word "thread".

In the Unix/Linux world, a thread is a Light Weight Process (LWP).  When running a thread, a parent thread is required.  Each thread, including the parent thread, share the same program space.

Now, AFAIK, there is no way to run threads as separate processes.  If one did that, then each of these would not be an LWP, but a full-blown process themselves, with their own program space that is independent of the others.

Anyhow, without further information about the application(s) you are attempting to run, I cannot elaborate more on what can be done to solve your request.

Perhaps you can consider prompting the user for input before the application terminates; this will keep the gnome-terminal open until the operator intervenes.

---

### Post by darkwing_duck on 2009-07-30
Thanks to both of you,

here is an example of the old script commands:

```
#!/bin/csh
xterm -e myProcess1 &
xterm -e myProcess2 &
xterm -e myProcess3 &
```

here is how it is now; how I want it to be:

```
#!/bin/csh
xterm -e ./myProcess1 &
xterm -e ./myProcess2 &
xterm -e ./myProcess3 &
```

I was forgetting the './' in front of the program name.

Thanks for your help!

---

