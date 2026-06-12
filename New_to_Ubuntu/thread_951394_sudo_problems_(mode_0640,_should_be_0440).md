---
title: "sudo problems (mode 0640, should be 0440)"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Tetenterre on 2008-10-18
I've been trying to get *Firestarter* to install at startup. The instructions at:  [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php) state that I should add the line:
> username ALL= NOPASSWD: /usr/bin/firestarter
at the end of the file */etc/sudoers*

I attempted to do this with gedit, but was unable to do so. I managed in *Terminal* by typing:
> sudo gedit /etc/sudoers
but was still unable to save it (read-only file). In order to change this, I hit <Alt-F2> and typed
> gksudo nautilus
in order that I could access the file permissions as *root* and change the mode to read and write.

All seemed to go successfully but, now when I log in, I cannot do any administrator tasks. When, for example, I attempt to add a program, the "Starting Administatio..." tab appears briefly on the bottom panel, then disappears. Similarly if I try to start, say, *Firestarter* manually. <Alt-F2> no longer works. I suspected the problem was probably the */etc/sudoers* file modification, so I tried to get to it through *Terminal*. Any sudo command throws up this response:
> sudo: /etc/sudoers is mode 0640, should be 0440

Presumably this is the source of my woes; I seem to be in a position where I cannot retrieve my administrator privileges unless I can first retrieve my administrator privileges. :(

Is there a solution to this other than reinstalling.

In case it's relevant, I'm using v8.04 LTS (Hardy Heron).

Thanks in advance for any assistance!

---

### Post by Tetenterre on 2008-10-18
More fiddling solved it. I rebooted in recovery mode, went to 
> Drop to root shell prompt
typed
> chmod 0440 /etc/sudoers
continued into normal boot, and all seems well.

Leaving it here in case it is of use to others....

---

### Post by Nepherte on 2008-10-18
The documentation of /etc/sudoers clearly states you have to edit that file with the command visudo. Next time, use:
```
sudo visudo
```
or if you're not familiar with the command line editor, you can use:
```
gksudo EDITOR=gedit visudo
```

visudo makes sure the permissions and ownership of /etc/sudoers is correct.

---

### Post by Tetenterre on 2008-10-18
Thanks, Nepherte -- saw that at the top of the file , but didn't have a clue what "visudo" meant, so went blithely ahead and screwed up :-) . The upside is that I have learned a lot about changing modes and (owing to another thing I tried that didn't work quite as I expected) changing owner:group of files.

...but I will use Visudo next time!

---

