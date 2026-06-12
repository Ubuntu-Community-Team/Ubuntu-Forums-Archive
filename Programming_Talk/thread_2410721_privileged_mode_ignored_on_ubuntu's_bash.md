---
title: "privileged mode ignored on ubuntu's bash"
date: 2019-01-19
forum: Programming Talk
---

### Post by cwmccabe on 2019-01-19
I am working on a bash script that is called by a setuid executable C wrapper.  Because the bash script is called by the setuid C program, it is also run as the setuid user.  This requires that bash be called with the -p flag (/bin/bash -p), to run in "privileged mode".

This works correctly on other systems, but seeming not on ubuntu.  Does the version of bash included with Ubuntu ignore the -p flag?  Or am I overlooking another explanation for why this approach would not work?

And yes, I'm aware that running shell scripts as setuid is a bad idea. :)

---

### Post by TheFu on 2019-01-19
From the bash manpage on a 16.04 system:
```
       If the shell is started with the effective user (group) id not equal to
       the real user (group) id, and the -p option is not supplied, no startup
       files are read, shell functions are not inherited from the environment,
       the SHELLOPTS, BASHOPTS, CDPATH,  and  GLOBIGNORE  variables,  if  they
       appear  in  the  environment, are ignored, and the effective user id is
       set to the real user id.  If the -p option is supplied  at  invocation,
       the  startup  behavior  is  the  same, but the effective user id is not
       reset.
```
and later```

              executed.   If the -p option is given, the search for command is
              performed using a default value for PATH that is  guaranteed  to
              find  all  of  the  standard  utilities.  
```
and later
```
              -p      Turn on privileged mode.  In this  mode,  the  $ENV  and
                      $BASH_ENV  files  are not processed, shell functions are
                      not inherited from the environment, and  the  SHELLOPTS,
                      BASHOPTS,  CDPATH,  and  GLOBIGNORE  variables,  if they
                      appear in the environment, are ignored.  If the shell is
                      started  with the effective user (group) id not equal to
                      the real user (group) id, and the -p option is not  sup&#8208;
                      plied, these actions are taken and the effective user id
                      is set to the real user id.  If the -p  option  is  sup&#8208;
                      plied  at  startup,  the effective user id is not reset.
                      Turning this option off causes the  effective  user  and
                      group ids to be set to the real user and group ids.
```
 

I've written setuid-root programs a few times. Always follow the best practices, especially when using shell scripts.  Definitely capture any signals and have a good cleanup routine. Never called a script from mine, however.

Can you show the 'system()' call from the code?

---

### Post by SagaciousKJB on 2019-01-21
> **cwmccabe said:**
> I am working on a bash script that is called by a setuid executable C wrapper.  Because the bash script is called by the setuid C program, it is also run as the setuid user.  This requires that bash be called with the -p flag (/bin/bash -p), to run in "privileged mode".

This works correctly on other systems, but seeming not on ubuntu.  Does the version of bash included with Ubuntu ignore the -p flag?  Or am I overlooking another explanation for why this approach would not work?

And yes, I'm aware that running shell scripts as setuid is a bad idea. :)

Well, the first thing that pops into my mind in terms of, "This shape is not like the others," is that Ubuntu does not have a password on the root account, meaning a user cannot 'su' to root.  Pretty much every other distro I've used doesn't do this.

I usually run a problematic app under 'strace' if I'm trying to diagnose a permissions problem.  It's a little bit more informative than the generic error messages.

What about the C wrapper itself? Did you compile it on the machine you're running it on, or is it a pre-compiled binary from another machine?  Does it check the setuid() function for error to let you know if it failed for some reason?

I would run your wrapper through strace just to make sure it's actually getting root privileges, and then once you've confirmed that, run 'bash -p' through the C wrapper, also through strace.  You should get a full output of what the system calls are doing and what might be going wrong.

---

### Post by cwmccabe on 2019-01-21
Thanks SagaciousKJB and ThuFu.  Turns it it was the compiled executable after all.  The setuid executable was using a system() call to run the bash script.  This worked on Debian and NetBSD machines, but not on Ubuntu.  I found that if I call the script with execve() instead of system() it now works on Ubuntu as well.  This introduces some other constraints, but ones that I can overcome.

---

