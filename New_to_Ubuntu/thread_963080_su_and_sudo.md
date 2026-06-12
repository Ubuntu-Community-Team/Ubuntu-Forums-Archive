---
title: "su and sudo"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by jsshere on 2008-10-29
whats the difference between su and sudo

---

### Post by snova on 2008-10-29
Really quickly: su won't work. :)

su is "switch user". It logs you in as somebody else, usually root. Since the root account is disabled on Ubuntu though, it's useless for this purpose.

sudo is similar, but rather than logging you in and giving you a shell, it just runs a single command (though this can be a shell). It also allows for more fine-grained control over who can run what.

---

### Post by k33bz on 2008-10-29
sudo lets you temporarily as root, and su puts you as root.

---

### Post by Sam on 2008-10-29
If you have multiple users, you can switch to any with```
su *USER*
``` or run a command```
su *USER* -c *COMMAND*
```

If you invoke "su" with no parameters, it means "su root", but it's not available by default on Ubuntu. One trick to circumvent this is```
sudo su
```

---

### Post by k33bz on 2008-10-29
> **snova said:**
> Really quickly: su won't work. :)

su is "switch user". It logs you in as somebody else, usually root. Since the root account is disabled on Ubuntu though, it's useless for this purpose.

sudo is similar, but rather than logging you in and giving you a shell, it just runs a single command (though this can be a shell). It also allows for more fine-grained control over who can run what.

correction, Ubuntu disables for you to "login" as root, but you can su root.

---

### Post by mfarquhar on 2008-10-29
> **k33bz said:**
> correction, Ubuntu disables for you to "login" as root, but you can su root.

possibly a little off topic but: Can You enable Root Logins (on the regular GUI desktop) normally in the current version?

I found out how to allow it a few years ago when I was first getting started with Ubuntu. Now I'm a newbie again and I've skipped ahead a few versions. I was able to let myself Login as Root on the terminals, but not the desktop...

---

### Post by Sam on 2008-10-29
> **mfarquhar said:**
> possibly a little off topic but: Can You enable Root Logins (on the regular GUI desktop) normally in the current version?

I found out how to allow it a few years ago when I was first getting started with Ubuntu. Now I'm a newbie again and I've skipped ahead a few versions. I was able to let myself Login as Root on the terminals (just hand set the password in the users and groups setting), but not the desktop...

Login as root on a terminal is one thing, using X as root is one other. And a very very bad idea.....

---

### Post by MRM0607 on 2008-10-30
> **Sam said:**
> Login as root on a terminal is one thing, using X as root is one other. And a very very bad idea.....

Dear forum user,

I would like to know how to login as root temporarily, to install a software (MATLAB) which require root login.

I got a failure message saying you are not login as root.

Thank you.
mrm0607

---

### Post by snova on 2008-10-30
Simply prefix the necessary command with sudo. Don't quote.

---

### Post by earthpigg on 2008-10-30
its against forum rules to tell you how to do that, mrm0607 (the 'why' is a debate unto itself)... i suggest using google :)

---

### Post by snova on 2008-10-30
He didn't ask how to reenable the root account, though you'd be right if he had.

I answered incorrectly anyway.

If you run "sudo -i", it will give you a root shell, which is functionally equivalent to logging in. Type "exit" when you're done with it.

---

### Post by bodhi.zazen on 2008-10-30
At their most basic, both su and sudo give access to root. Both can allow you to run commands as other users as well.

The major difference (in the default behavior) is that su uses the target's password (su rot -> enter root password, su joe -> use joe's password) and sudo uses the user's password.

The other major difference is that su is all or none (ie you su to root and have full access) while sudo allows you to have a finer gradation of contol (allow some users root assess for apache, but not the entire system).

See also : [uhelp]community/RootSudo[/uhelp]

---

### Post by MRM0607 on 2008-10-31
> **earthpigg said:**
> its against forum rules to tell you how to do that, mrm0607 (the 'why' is a debate unto itself)... i suggest using google :)

Dear Forum User,

Thank you for informing me about the forum rule.  

I do not want to know how to become root user. Sole reason for the question is to install the software.

I was able to install the software using sudo as prefix to commands.

Thank you.
mrm0607

---

### Post by crjackson on 2008-10-31
> **MRM0607 said:**
> Dear Forum User,

Thank you for informing me about the forum rule.  

I do not want to know how to become root user. Sole reason for the question is to install the software.

I was able to install the software using sudo as prefix to commands.

Thank you.
mrm0607

Dear Ubuntu user,

I HAVE ran across a few packages/programs that wouldn't install with the simple prefix of sudo at the command line. One of the other members listed below beat me to the punch line, but this ALWAYS works for ME.

> **snova said:**
> 
If you run "sudo -i", it will give you a root shell, which is functionally equivalent to logging in. Type "exit" when you're done with it.

---

