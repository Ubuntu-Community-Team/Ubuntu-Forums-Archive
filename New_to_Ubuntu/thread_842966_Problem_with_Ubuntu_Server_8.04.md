---
title: "Problem with Ubuntu Server 8.04"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by wak_wak on 2008-06-27
I have a fairly new Inspiron 530 desktop with a an Intel Duo processor.

I'm running Ubuntu 8.04 work station with VirtualBox.

Currently I'm running Windows Vista and Debian Studio 64 within Vbox and both work great.

I downloaded the x86 server edition of Ubuntu Server and after completing the whole set up process I get this message:

[IMG]http://williamkilmartin.com/photos/Screenshot.jpg[/IMG]

I seem to recall running in to this problem once before but ended up solving it by just using Ubuntu server 7.04 but would rather not do that again...  The last time it wasn't in a virtual machine and I got the exact same error so I'm pretty sure it not Vbox...

Any ideas?

Thanks in advance...

---

### Post by dominiquec on 2008-06-27
Enable PAE on the virtual machine.  It's on the Advanced Settings tab of the General configuration.

---

### Post by wak_wak on 2008-06-27
Wow.  You're guite the genius:

[IMG]http://williamkilmartin.com/photos/worksnow.jpg[/IMG]

What is PAE and why did it all of a sudden work?

Thank you very much!

---

### Post by dominiquec on 2008-06-27
Heh. Not so much a genius as someone who's muddled his way through the same thing.  PAE is Physical Address Extensions, essentially, this allows more than 4GB of addressable space.  The Ubuntu server kernel is compiled with this option, hence it looks for this capability.

---

### Post by wak_wak on 2008-06-27
Ahhh.  Makes sense.  Thanks!!!

---

