---
title: "[SOLVED] What is a pseudo terminal?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Sydius on 2008-08-01
I've been writing a script that needs to do some things over SSH without prompting the user for the password (more than once).  It's kind of a one-time-only script, and I was just making it the way I was to see if I could--obviously, since it's a one-time-only thing, I might as well just do all the commands by hand.

I used a program called sshpass (I know I could do the key thing, but it's not really an option for this) to great effect on my Ubuntu work machine.  Unfortunately, when I had perfected it (after many hours) and moved it to the server it was to be executed from, I got an interesting error:

```
[chris@sv054 sshpass-1.01]$ ./sshpass
Failed to get a pseudo terminal: No such file or directory
```

It works fine in Ubuntu, but even after compiling it on the CentOS server, I get the above error.

I don't know what a pseudo terminal is, or why it wouldn't work for this program.  Any hints?

---

### Post by DGortze380 on 2008-08-01
> **Sydius said:**
> I've been writing a script that needs to do some things over SSH without prompting the user for the password (more than once).  It's kind of a one-time-only script, and I was just making it the way I was to see if I could--obviously, since it's a one-time-only thing, I might as well just do all the commands by hand.

I used a program called sshpass (I know I could do the key thing, but it's not really an option for this) to great effect on my Ubuntu work machine.  Unfortunately, when I had perfected it (after many hours) and moved it to the server it was to be executed from, I got an interesting error:

```
[chris@sv054 sshpass-1.01]$ ./sshpass
Failed to get a pseudo terminal: No such file or directory
```

It works fine in Ubuntu, but even after compiling it on the CentOS server, I get the above error.

I don't know what a pseudo terminal is, or why it wouldn't work for this program.  Any hints?

Did you remember to include this line at the top of your script?
#!/bin/bash

Are you running the correct shell? I don't know what the default is in CentOS, could be something other than bash.

---

### Post by Sydius on 2008-08-01
> **DGortze380 said:**
> Did you remember to include this line at the top of your script?
#!/bin/bash

Are you running the correct shell? I don't know what the default is in CentOS, could be something other than bash.

I tried putting the command in a script with that at the top, and it didn't make a difference.

---

### Post by rahmath on 2008-08-01
a pseudo terminal is a pseudo-device pair that provides a text terminal interface without associated virtual console, computer terminal or serial port hardware. Instead, a process replaces the role of the underlying hardware for the pseudo terminal session.


Then for this problem, i guess it is related to the permission. While executing the script, the executing users is not able to open a pseudo terminal...

i feel like so.

---

### Post by Sydius on 2008-08-01
> **rahmath said:**
> a pseudo terminal is a pseudo-device pair that provides a text terminal interface without associated virtual console, computer terminal or serial port hardware. Instead, a process replaces the role of the underlying hardware for the pseudo terminal session.


Then for this problem, i guess it is related to the permission. While executing the script, the executing users is not able to open a pseudo terminal...

i feel like so.

Hey, ya know, I logged in as root, and that fixed the problem! Thanks! How would I go about changing the permissions of who can open one, though (at least in Ubuntu--maybe the principle is the same)?

---

### Post by rahmath on 2008-08-01
Actually i am newbie to Ubuntu. But do have much experience in Red Hat. and RH and CentOS are the almost the same (i heard like that, until now, i didnt tried CentOS).

Anyway i will try to explain for you in terms of Red Hat. Most probably this should be the things in Ubuntu too...

While first user (first means, no one else is loged in to your system) login to Linux through command line, almost all the required device files is been mapped to that user's ID by default. it is done with the help of PAM. So that that user will have access to many devices like cdrom, floppy, pseudo terminals, etc. Then if you change to the second termincal (with the help of Ctrl+Alt+F2 ) and log in as another user, he will not have mapped all these things, bcoz its been already assigned for the first user, and thus this second user will not have permission to access some sort of device files.

I guess this is the same issue which is happened in your situation.

---

