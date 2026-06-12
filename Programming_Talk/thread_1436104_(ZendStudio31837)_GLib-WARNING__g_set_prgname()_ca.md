---
title: "(ZendStudio:31837): GLib-WARNING **: g_set_prgname() called multiple times"
date: 2010-03-22
forum: Programming Talk
---

### Post by Almeida1 on 2010-03-22
Hi

Im not sure if this is to do with Zend Studio or with Ubuntu itself but when I try and open Zend Studio fom the command line, it opens but in the command line it says:

(ZendStudio:31837): GLib-WARNING **: g_set_prgname() called multiple times

If I then try and close the terminal window, I get a popup message saying:

"There is still a process running in this terminal. Closing the terminal will kill it."

If I click Close Terminal this then closes Zend Studio! 

Any idea what the problem is and how I can fix it?

Thanks

---

### Post by n0dix on 2010-03-22
See the [Bug report]("https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/501670"), maybe shows a solution.

---

### Post by Almeida1 on 2010-03-22
> **n0dix said:**
> See the [Bug report]("https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/501670"), maybe shows a solution.

Thanks for the reply, I looked at the report before posting here because I couldnt find a fix.

---

### Post by Almeida1 on 2010-03-22
Anyone know a fix for this?? :(

---

### Post by HellBoz on 2010-03-23
You need to udate glib ( 2.22.3 - bug fixed ).

---

### Post by phrostbyte on 2010-03-23
If you close a Terminal any applications launched from that Terminal will also be closed, even those which are background run (using the '&' operator).

---

### Post by Almeida1 on 2010-03-24
> **HellBoz said:**
> You need to udate glib ( 2.22.3 - bug fixed ).

Sorry I am a bit of a noob to linux. How do I update glib???

Thanks

---

### Post by Almeida1 on 2010-03-24
I have checked the Synaptic Package Manager and searched for libglib.

Then looking at libglib2.0 I have 2.22.3-0ubuntu1 installed. It says the latest version is also 2.22.3-0ubuntu1.

libglib2.0-data is also set to 2.22.3-0ubuntu1.

---

### Post by n0dix on 2010-03-24
Try reinstalling the package, but it seems the bug isn't fix.

---

### Post by Hellkeepa on 2010-03-24
HELLo!

First the GLIB warning is just a warning, doesn't need to be a problem.

Secondly, as **phrostbyte** pointed out: The fact that an application, that you've started from the terminal, closes when you close the terminal is not a bug. It's the expected behavior.

So, do you have any bugs, or side effects, that can be described to the warning. Or was it just that Zend Studio closed when you closed the terminal window?

Happy codin'!

---

### Post by HellBoz on 2010-03-25
> **Almeida1 said:**
> I have checked the Synaptic Package Manager and searched for libglib.

Then looking at libglib2.0 I have 2.22.3-0ubuntu1 installed. It says the latest version is also 2.22.3-0ubuntu1.

libglib2.0-data is also set to 2.22.3-0ubuntu1.

The only way to update it on Jaunty is PPA.

---

