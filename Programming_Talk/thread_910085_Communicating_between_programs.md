---
title: "Communicating between programs"
date: 2008-09-04
forum: Programming Talk
---

### Post by FrankL on 2008-09-04
Dear all,

I want to be able to send commands from the console to specific programs. So, for example, send a play command to amarok or text to kate. Is there a way to send commands from the console to running processes? And between programs?

I need this for a Java program I am making which uses an external neural network program (written in C++). I want to be able to send commands from my program to the neural network (which actually has a console of its own). The portability of the program is not relevant, so native Linux commands can be used.

Hopefully someone can help me,

      kind regards,

               Frank

---

### Post by Zugzwang on 2008-09-04
You can communicate at least with console programs you execute as a child - All other cases will be more complicated. For non-console programs, this will be very complicated, no idea how to do that.

See Python's/C's popen or Java's Runtime.exec, for which you can get Input- and Output Streams from the Process object it creates. Writing to this Output Stream is like sending keystrokes to the executed program (well, almost) and you can read the program's output from the provided InputStream.

---

### Post by .nedberg on 2008-09-04
> **FrankL said:**
> Dear all,

I want to be able to send commands from the console to specific programs. So, for example, send a play command to amarok or text to kate. Is there a way to send commands from the console to running processes? And between programs?

I need this for a Java program I am making which uses an external neural network program (written in C++). I want to be able to send commands from my program to the neural network (which actually has a console of its own). The portability of the program is not relevant, so native Linux commands can be used.

Hopefully someone can help me,

      kind regards,

               Frank


Communicationg with amarok/kate can be done with dcop (or later dbus). How to do dcop/dbus with java I have no idea...

---

### Post by Tomosaur on 2008-09-04
Sounds like you want dbus. Dbus has Java bindings, which you can read about [here](http://dbus.freedesktop.org/doc/dbus-java/).

---

### Post by themusicwave on 2008-09-04
Another option is too use TCP/IP for this using loopback.

The IP address 127.0.0.1 is known as loopback because it seems basically sends messages out of the machine and back in.  I think it is all internal to the NIC though and nothing actually leaves the machine.

What you would do is pick a port like say 4567.  Now, you make your two programs communicate over this port on IP Address 4567.

From here you can pass all kinds of information.  This method is also platform independent.  The major snag is some firewalls and anti-virus programs might not like it.

---

### Post by Zugzwang on 2008-09-04
Wait, wait, wait! We have been stated a lot of possibilities how two programs could communicate but as far as I understand it, the OP doesn't want to modify the existing C++ program (neural network simulator), so he has to use what he got - and it's unlikely that dbus is included. So we have to wait until the statement "which actually has a console of its own" by the OP is explained, because this could either mean that that's a program running in terminal (in which case I've already posted a solution) or it is some GUI having some text field to type in some commands (AutoCAD-like), in which case none of the solutions posted so far help him.

---

### Post by Reiger on 2008-09-04
In Java: [http://java.sun.com/j2se/1.4.2/docs/api/java/lang/Process.html](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/Process.html)

---

