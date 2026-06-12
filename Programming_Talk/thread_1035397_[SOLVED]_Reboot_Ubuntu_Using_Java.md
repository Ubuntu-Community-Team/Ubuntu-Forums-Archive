---
title: "[SOLVED] Reboot Ubuntu Using Java"
date: 2009-01-09
forum: Programming Talk
---

### Post by deltaromeo on 2009-01-09
Hi, I'm trying to reboot from java using: 

> Process p = Runtime.getRuntime().exec("shutdown -r 5");

which basically just executes the **shutdown** command from command line / shell.  The problem is that it needs su rights and I'm getting the following output:

shutdown: Need to be root

just as would happen when executing the same command in terminal.  So, it's not really a programming question, but does anyone khow would I be able to get this to run?

Thanks.

---

### Post by dwhitney67 on 2009-01-09
```

sudo java MyShutdown

```
where MyShutdown is located within the .class file generated from MyShutdown.java.

If your Java app has a user interface, then replace 'sudo' with 'gksudo'.

---

### Post by deltaromeo on 2009-01-09
Thanks for replying.

That may work although I do not run my java program from the terminal, it gets executed using "Sessions" to start when my computer starts up (the reboot code being placed in a conditional in the java code).

sudo prompts for a password, but I'm not there to type it in (the pc is functioning as a server).

Any other ideas please?

---

### Post by deltaromeo on 2009-01-09
I finally found out how to do it.

I added the following line to /etc/sudoers

```
*myusername* ALL = NOPASSWD: java MyShutdown
```

then in Gnome Sessions I created an entry with the following command

```
sudo java MyShutdown
```

this works.  The entry in sudoers means that sudo doesn't prompt for a password for that specific command.

---

### Post by ashraful on 2009-06-09
Hi
I want to run command line program such as,
# ifconfig eth0 up/down
# route add default gw

from a Java program using the Runtime.exec() command. But when I run the program, no message is showing and silently discarded and have no impact on the system.
Plz tell me, how is can be done.
From other commands, such as, ifconfig, route, I can capture the output.

And how can a program be run in privileged mode without any user interaction?

Thanks in advance.

Regards,
Ashraf.

---

