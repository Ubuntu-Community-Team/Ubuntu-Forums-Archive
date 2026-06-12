---
title: "Need help on OpenSUSE"
date: 2008-06-26
forum: Other OS Talk
---

### Post by Sain on 2008-06-26
I've asked this question on OpenSUSE forums, but they were less than helpful so far...

I've just installed OpenSUSE 11, and I'm still learnin it, it's quite different from Ubuntu that I'm used to.

One thing I loved about Ubuntu is it's sudo policy. It seems different from other distros including SUSE.

In Ubuntu when I edit sudoers, and type NOPASSWD: ALL in the "Users that may gain root privileges" line, it stops bothering me with passwords... This does not seem to work with SUSE. Why? Is there a way to make it work that way? :)

I am very well of security risk that does, but thats the way I like to work. I like to have full control of my computer, but still use my account and not login as root. 

So is there a way to gain root privileges in SUSE without typing passwords. At least make it remember password for longer than 5 sec.

---

### Post by dca on 2008-06-26
Try (at your own risk) and access YaST.  Bear with me, I haven't used SuSE in ages: under one of the management areas there is an option to activate 'sudo' which makes it operate like Ubuntu.  Once you activate and possibly restart THEN go and change the sudoers file.

---

### Post by Frak on 2008-06-26
The OpenSUSE uses a special modified version of sudo that doesn't accept the NOPASSWD argument.

---

### Post by ibutho on 2008-06-26
To mimic what Ubuntu does, try
```
username ALL=(ALL) NOPASSWD: SETENV: ALL
```
That should all commands without a password if executed as the user "username".

---

### Post by cardinals_fan on 2008-06-26
> **Sain said:**
> I've asked this question on OpenSUSE forums, but they were less than helpful so far...

I've just installed OpenSUSE 11, and I'm still learnin it, it's quite different from Ubuntu that I'm used to.

One thing I loved about Ubuntu is it's sudo policy. It seems different from other distros including SUSE.

In Ubuntu when I edit sudoers, and type NOPASSWD: ALL in the "Users that may gain root privileges" line, it stops bothering me with passwords... This does not seem to work with SUSE. Why? Is there a way to make it work that way? :)

I am very well of security risk that does, but thats the way I like to work. I like to have full control of my computer, but still use my account and not login as root. 

So is there a way to gain root privileges in SUSE without typing passwords. At least make it remember password for longer than 5 sec.
You might as well login as root if you're going to do that...

---

