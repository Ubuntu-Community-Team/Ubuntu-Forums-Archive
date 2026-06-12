---
title: "what is the reason for &quot;Must be attached to terminal for 'am I' option&quot;"
date: 2007-09-18
forum: Programming Talk
---

### Post by murajashekar2003 on 2007-09-18
Hi Frenz,

I have a written a simple Perl program that Communicates with another host on the network.

I use rsh [Passwordless rsh login enabled between the systems.]

I get the Following error....

I was wondering why an error of this type appears..

**[B]_Must be attached to terminal for 'am I' option_**[/B]

Please clarify me..

thanks in advance 
Rajasekar

---

### Post by PaulFr on 2007-09-18
Check your startup file (.bashrc, .cshrc, etc.) for the user account on the machine on which the rsh command is executing, for a **who am i** command - that cannot run on a remote command, it requires an actual tty terminal association. Remove that from your startup file and I think your error messages will go away.

---

