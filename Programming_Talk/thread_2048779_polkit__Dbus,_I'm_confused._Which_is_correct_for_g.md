---
title: "polkit / Dbus, I'm confused. Which is correct for granting root access?"
date: 2012-08-27
forum: Programming Talk
---

### Post by RichardUK on 2012-08-27
I've got my self confused with a simple task of giving my app root access to preform some disk access. It does not need root until all the configuration has been done. Once you press the GO button then I need the root access.

My first attempt was to respawn my app as root, using gksudo but that is messy and the dialog has my full program path and command line so is unreadable. Not user friendly. 

With some google I've found references to DBus and Polkit. Some demos use DBus in the app but talk as if it is a polkit thing. I've also managed to install two dev libs for polkit. 

libgksu-polit-dev
libpolkit-qt-1-dev

Documentation I have found seems out of date or incomplete which makes me wonder if there is a better system now in use?

As you can see I'm got in a bit of a mess. 

So, what I need is someone to say "Use X for new ubuntu apps, here is a link on how to do it in Ubuntu".

Thanks. :)

---

### Post by andrewc6l on 2012-08-28
You haven't said what your app is written in. If it's C/C++, then setuid/seteuid (or setgid/setegid) is what you should be using:

[http://www.gnu.org/software/libc/manual/html_node/Users-and-Groups.html#Users-and-Groups](http://www.gnu.org/software/libc/manual/html_node/Users-and-Groups.html#Users-and-Groups)

Be warned that you should set root, do your thing, and relinquish it as soon as possible.

---

### Post by RichardUK on 2012-09-01
Thanks for the link, will read now. Sorry for late reply, working on site at the moment so not at home during the week.

Yes I'm using C/C++ and Qt Creator for my IDE. 

When I was looking at this whole authentication issue I did see some talk on setuid seteuid but it was about security issues in code using it. Did I miss understand what they were talking about? Something about rights escalation.

Many thanks,
Richard e Collins.

---

### Post by gnometorule on 2012-09-01
Exploiting entire programs that had the setuid bit set used to be at the core of older hacking attacks. To understand how this might work, google real user id, effective user id, and, for more color, smashing the stack for fun and profit. It boiled down to feeding assembly code to programs that allowed a user to run with admin privileges; hence the other reply's comment to relinquish such control as soon as possible. However, those old attacks at least are long patched up in ubuntu, using security measures such as canary values, randomization of the memory space, and setting a certain bit in memory to make it non-executable. 

So just read up on the commands mentioned by the above reply,  and you're probably fine.

---

### Post by diesch on 2012-09-01
DBus is a daemon enables communication between multiple processes. PolicyKit uses DBus for the communication between your program, an authentication agent and the privileged processes offering the services your program wants to use.

---

