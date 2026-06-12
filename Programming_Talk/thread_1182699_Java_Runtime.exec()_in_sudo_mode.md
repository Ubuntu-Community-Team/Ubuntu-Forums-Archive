---
title: "Java Runtime.exec() in sudo mode"
date: 2009-06-09
forum: Programming Talk
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

### Post by froggyswamp on 2009-06-09
gksudo works but still asks for a password during runtime (in GUI mode):

```

public static void main(String[] args) {
    try {
        Runtime r = Runtime.getRuntime();
        r.exec("gksudo gedit /etc/X11/xorg.conf");
    } catch( Exception exc ) {
        exc.printStackTrace();
    }
}

```If you google I'm pretty sure you'll find how to specify the password silently if you don't want the user to be asked for it.

---

