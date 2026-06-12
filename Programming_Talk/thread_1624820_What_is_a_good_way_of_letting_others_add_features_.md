---
title: "What is a good way of letting others add features to your application?"
date: 2010-11-18
forum: Programming Talk
---

### Post by TheHimself on 2010-11-18
One difficult way is to develop a script language for your application (like emacs lisp) but I'm too lazy for that!! One way I can think of is that the user uses a pipe to send arguments and commands to the application  and receive its response.

I use C as a matter of fact.

---

### Post by dv3500ea on 2010-11-18
Why develop your own scripting language when you can embed something like [lua]("http://www.lua.org/about.html")?

---

### Post by nvteighen on 2010-11-18
> **TheHimself said:**
> One difficult way is to develop a script language for your application (like emacs lisp) but I'm too lazy for that!! One way I can think of is that the user uses a pipe to send arguments and commands to the application  and receive its response.

I use C as a matter of fact.

Hm... I can't see how a pipe would allow to do such a thing. Pipes are just for I/O.

No, the alternative to a scripting language would be a plugin architecture. You can dynamically load a shared library using the ld linker API and do stuff from there... Think of Adobe Flash, for example. It has its inconveniencies, though.

---

### Post by TheHimself on 2010-11-20
The user's program can run my application in a pipe and use the pipe to send command line options to my application and receive its output. Can't? Although this would be more like a script language.

Could you elaborate more on the following?
 > dynamically load a shared library using the ld linker API 

Thanks.

---

### Post by StephenF on 2010-11-20
> **TheHimself said:**
> The user's program can run my application in a pipe and use the pipe to send command line options to my application and receive its output. Can't? Although this would be more like a script language.

Could you elaborate more on the following?

There already exist "pipe based" systems for controlling and communicating with other programs. Others have gone in the past, the one people are using right now is called [D-Bus]("http://www.freedesktop.org/wiki/Software/dbus").

If you go the D-Bus route the two programs will be separate unlike a true plug-in architecture (where the plug-in code can run in the same process) and you will have to maintain two API's the internal one between application layers which currently exists (to whatever degree you decided to bother) and also manually expose interfaces to D-Bus as well.

There are libraries built upon D-Bus which can handle things like argument passing to functions. It is at this level that programmers generally use it.

Edit:
Going the dll route with run-time linking.
[http://www.opengroup.org/onlinepubs/009695399/functions/dlopen.html](http://www.opengroup.org/onlinepubs/009695399/functions/dlopen.html)

Typically you would have a directory to put your plug-ins inside that would be scanned by the main program and would check the plug-in has certain symbols relating to name, purpose, version number, API versions supported. The plug-ins would be run on a schedule controlled by the main program and would have certain functions of a set name, at the very least a register and unregister function.

---

### Post by nvteighen on 2010-11-20
> **TheHimself said:**
> The user's program can run my application in a pipe and use the pipe to send command line options to my application and receive its output. Can't? Although this would be more like a script language.

I'm still not sure about what you want. A pipe is used as an I/O channel between different programs... That's it and you barely can add a feature to a program (isn't this what you want?) using a pipe: all you can do is pass data.

Dynamic loading of libraries (don't confuse with dynamic **linking**) consists in opening a library at runtime, compared to the usual case where you link to libraries at compile-time. For example, dynamic loading allows you to choose between alternative libraries depending on information available at runtime, such as user input or whatever. Check the manpage for dlopen(), there you'll see a basic and useful example.

---

