---
title: "Identifying hard drives"
date: 2007-12-13
forum: Programming Talk
---

### Post by Boule on 2007-12-13
I need to identify the physical hard drives connected to a machine from within a program (under linux). Is there a command/way to do that ?

The language used is C.

Thanks !

---

### Post by pedro_orange on 2007-12-14
Hdparm is the command you're looking for if you want to run a shell command.

Documentation: [http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

You'll probably want to do something along the lines of: sudo hdparm -I

Note there are differences between -I and -i

---

