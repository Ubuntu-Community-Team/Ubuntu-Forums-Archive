---
title: "How to add GUI to command line"
date: 2009-10-04
forum: Programming Talk
---

### Post by jase21 on 2009-10-04
Hello,

My problem:
Suppose that there is no GUI front-end to a tool say nmap (nmap has a gui front-end, but lets assume that it doesn't) then, how can I make a gui to the various commands in nmap.
There are various flags (and I could make a check box to add each) but how to connect(communicate) with the command line. 

Another example:
Suppose the windows telnet thing.
I need a gui that have an address field, port field, and a connect button.
When I press connect it should map to 
o (address) (port number)
o 192.168.1.1 23

Which programming language and libraries are to be used.
(Rapid to build)
I hope the questions are clear.
Please help.
Thank You very much.

---

### Post by ApEkV2 on 2009-10-04
You could make one with xmessage.
Type in the terminal "man xmessage".

---

### Post by nvteighen on 2009-10-04
There are two possibilities:

1) When programs are split in two: into a program that just is an interface and a library that is where the whole implementation lies. In this case, you just have create a new interface that uses the library. No need to call the program itself, just the subroutines. Be careful with licensing terms, of course.

2) When not: "Piping" either using xmessage, or using a Python or Perl script that uses system(), fork() or whatever to create a new process which you interact with is the way to go. You don't access the API, but access the program.

Try to get a chance to use #1... as is the best.

Well, the third possibility would be to modify the original source code to replace the interface code... But that option can be a nightmere if the code is not well designed and/or you don't understand the code.

---

### Post by jase21 on 2009-10-04
whois is a command in GNU/Linux.
I want to make a grahical user interface (a GUI program) that does the same as whois. 
I'm much of a noobie.. here

---

### Post by nvteighen on 2009-10-05
> **jase21 said:**
> whois is a command in GNU/Linux.
I want to make a grahical user interface (a GUI program) that does the same as whois. 
I'm much of a noobie.. here

Hum... that GUI already exists... It's even in the menus, but in Debian (which is the OS I use) that program is placed in a different menu than in Ubuntu... It's called something like "Networking tools"...

Anyway, you can access it through the terminal by typing:
```

gnome-nettool

```

---

