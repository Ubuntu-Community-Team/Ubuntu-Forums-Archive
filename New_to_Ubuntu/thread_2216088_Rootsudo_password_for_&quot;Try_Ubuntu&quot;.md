---
title: "Root/sudo password for &quot;Try Ubuntu&quot;"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by cameroncono on 2014-04-09
I want to use Ubuntu to disinfect and wipe infected Windows machines.  I have Ubuntu on a DVD that I boot from, and then I use the 'Try Ubuntu' option.  However, I can't run root commands.  I don't have a user account, as it Ubuntu isn't installed on my Hard Drive.

What is the root password in this situation?

---

### Post by Bashing-om on 2014-04-09
cameroncono; Ho ! Welcome to the forum.

To execute a command with the elevated privilege of "root" precede the command with the term 'sudo' (Super User DO). In the liveDVD no password is required for authentication.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by papibe on 2014-04-09
Hi cameroncono.

Just like any version of Ubuntu, the live version ('Try Ubuntu' option) has the root account disable. 

The default user is 'ubuntu' and it has admin privileges, i.e., can run sudo. Open a terminal and run any restricted command.

For instance:
```
sudo apt-get update
``` 
If you'd like to have a more permanent super user prompt, run this:
```
sudo -i
```
Hope it helps. Let us know how it goes.

P.S.: at this moment I don't remember if the password for the user 'ubuntu' is either blank (press enter), or not even set (then not asked).

---

### Post by coldcritter64 on 2014-04-10
> **papibe said:**
> ...P.S.: at this moment I don't remember if the password for the user 'ubuntu' is either blank (press enter), or not even set (then not asked).

I can't actually test here at the moment on Ubuntu but from memory user is ubuntu and the password is the Enter button (no password). I've regularly set the user ubuntu to the group root so as to access (write to) my partitions (due to their 775 permissions set, I can write folders to the root of a partition when in the group root) from the live cd. 

This requires logging out then back in to set the user ubuntu into the group root, hence my using the user ubuntu and the blank password regularly. Same in terminal when using sudo or sudo -i, just hit the enter button, no password is set for the live cd/dvd sudo usage. Cheers, coldcritter64.

---

