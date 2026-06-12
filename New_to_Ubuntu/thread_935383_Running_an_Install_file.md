---
title: "Running an Install file"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by skarosg3 on 2008-10-01
Hi all,
I am trying to install Matlab on my linux box but i have a problem.
I insert the cd, and follow the instructions (copy a file to the directory that i want the installation) but when i run the command
```

/media/cdrom/install*

```
as is on the help file i get this error
[b]
cp: cannot stat `/media/cdrom0/update/bin/glnxa64/*': No such file or directory
Error writing to /tmp/6615tmwinstall
The installer is unable to copy files to /tmp.
Make sure that /tmp exists, is writable, and has
at least 5 megabytes of available space.
[/b]

I checked the tmp file as root and i have the permision to create and delete files. I also created a dumb file as not root.

and ofcourse i do have enough space.
Any help pls?

---

### Post by roquefilipe on 2008-10-01
from [this Fedora forum]("https://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=55205&forum=10&move=next&topic_time=1207946243"), I would say to try this: "install -glnx86 -nocp"

---

### Post by skarosg3 on 2008-10-03
Thanks for the replay man
but the link is not working. I got a

Secure Connection Failed

I tried the command you said but then i got this error
[b]
    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        Can't open display.

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .
[/b]

I have no idea why this is not working!

---

