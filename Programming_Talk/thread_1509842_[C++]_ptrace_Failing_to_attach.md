---
title: "[C++] ptrace Failing to attach"
date: 2010-06-14
forum: Programming Talk
---

### Post by astropirit on 2010-06-14
Greetings all
I am very new to developing in a Linux environment as I switched from windows a few days ago :grin: so please rectify my ignorance.
I was playing around with the source code for Scanmem ([http://taviso.decsystem.org/scanmem.html](http://taviso.decsystem.org/scanmem.html)) and to my surprise I was unable to attach to the target process. The following code is used to attach to the process using ptrace():

```
    
/* attach, to the target application, which should cause a SIGSTOP */
    if (ptrace(PTRACE_ATTACH, target, NULL, NULL) == -1L) {
        fprintf(stderr, "error: failed to attach to %d, %s\n", target,
                strerror(errno));
        return false;
    }

```

errno shows "Operation not permitted". How could this be? I tried the same thing with other processes and it worked fine but not this one. could someone please shed some light on this?

thanks,
Astro

---

### Post by dwhitney67 on 2010-06-14
> **astropirit said:**
> 
errno shows "Operation not permitted". How could this be? I tried the same thing with other processes and it worked fine but not this one. could someone please shed some light on this?

thanks,
Astro

Which processes were you able to attach to, and which were you not?  Are the ones that you attempted to attach to, which subsequently failed, owned by you?

---

### Post by astropirit on 2010-06-14
After reading the man page on ptrace:
> 
EPERM
    The specified process cannot be traced. This could be because the parent has insufficient privileges (the required capability is CAP_SYS_PTRACE); non-root processes cannot trace processes that they cannot send signals to or those running set-user-ID/set-group-ID programs, for obvious reasons. Alternatively, the process may already be being traced, or be init (PID 1). 


I think it has to do something with the permissions, i will play arround with that.

Thanks!

---

### Post by dwhitney67 on 2010-06-14
> **astropirit said:**
> After reading the man page on ptrace:


It is because the process I am trying to attach to is PID 1. Now, that's the problem. How can I go about solving it? I mean is there a work around or another function that I may be able to use?

Try logging in as 'root'.  If you are on an Ubuntu system, try running 'sudo -i'; otherwise 'su - root'.  After you have logged in as root, then try running ptrace.

---

### Post by astropirit on 2012-02-05
I am sorry to awaken this dead beast... but after collecting dust in my backups, I decided to take a look at this project again.

Running under sudo works. But I need the program to run under the current user. Interestingly enough, this runs fine under Fedora but not Ubuntu (i'm running Kubuntu)

I disabled the ptrace hardening Ubuntu has put in place but it didn't do anything.

I tried modifying /etc/sysctl.d/10-ptrace.conf to 0 and rebooting.. and didn't work.

I also tried 
echo 0 > /proc/sys/kernel/yama/ptrace_scope

which also didn't work.  Any other ideas on what might be blocking this?

---

