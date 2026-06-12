---
title: "Check for Root User"
date: 2006-08-25
forum: Programming Talk
---

### Post by whitewizardcoder on 2006-08-25
Hi,

I'm fairly new to programming in linux (I've done some GTK stuff, but that's about it) and I was wondering how I would go about checking to see if the current user is the root user in a C program.  Any help is greatly appreciated!

Thanks,

WhiteWizardCoder

---

### Post by JonahRowley on 2006-08-26
The geteuid system call is what you're looking for.  Be careful with getuid (not geteuid) as the effective uid and real uid of a process can differ.  A process with a uid of 0 is running as the superuser.

---

