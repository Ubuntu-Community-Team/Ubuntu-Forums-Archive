---
title: "Execute with system() - But as child-process"
date: 2006-10-10
forum: Programming Talk
---

### Post by daller on 2006-10-10
I'm working on a HOTSPOT daemon for wizardpen tablets.

Everything works like a charm, except some annoying thing.

* Using system() to execute a command, makes the whole daemon stall, if the command execution stalls

* The daemon, which I named **wzpscd** does not function as a daemon ATM. - How do I make it start automatically?
 - It should only start if a tablet is present. - I have a script in /etc/rc.local that checks for a present tablet - If found, it adds the tablet to the xorg serverlayout. - Should I start the daemon from /etc/rc.local?

See /etc/rc.local here:

[https://help.ubuntu.com/community/TabletSetupWizardpen#head-ce41a09dcf6ce1242f2efd0accf875b127f64598](https://help.ubuntu.com/community/TabletSetupWizardpen#head-ce41a09dcf6ce1242f2efd0accf875b127f64598)

Please help, this is the only things I need to offer the HOTSPOT daemon to the community!

---

### Post by foxylad on 2006-10-10
Assuming you are using c, you should check out fork() (or spawn() or exec()). The system call is designed to stop until the child process finishes, which makes programming easy because it is essentially a single process.  

With fork(), the child process and the parent become completely independant. You have to manage the relationship very carefully of course - what happens if the parent dies before the child? How do the parent and child communicate?

There is a good introduction to fork() here:

[http://www.erlenstar.demon.co.uk/unix/faq_2.html#SEC2](http://www.erlenstar.demon.co.uk/unix/faq_2.html#SEC2)

Cheers!
Greg.

---

