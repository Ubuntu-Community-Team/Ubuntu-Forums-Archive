---
title: "C Help"
date: 2008-08-12
forum: Programming Talk
---

### Post by lapubell on 2008-08-12
I have been battling what I have come to find is a lost cause.  I have a bash script that I need to run as root, and would like to hot key it, so I would like to make it not prompt me for a password.  This led me to learn about the SUID of the file, and thought that it would work, but then i found out that the SUID is ignored for scripts (which makes sense, as the security flaw that it is...)

So the workaround that people have been using is using the SUID on a compiled file as that will still work.  People have been writing a program in C that will launch a script.  I have no idea how to do this.

I do all my programming in interperted languages (Python and PHP mostly) and have virtually no experience with any C languages.

Anyone want to help me out with a tutorial, link, or (if you are way too awesome) some source code?

---

### Post by Java Geek on 2008-08-12
if you need c tutorials, check out cprogramming.com
if you need C++ tutorials, check out cplusplus.com/docs

**Check out the sticky at beginning of forum!**

---

### Post by kpatz on 2008-08-12
You could use visudo to edit your sudoers file to enable you to run your script as root using sudo without prompting for a password.  This is the "standard" way of doing it and safer than making a SUID executable.

---

### Post by lapubell on 2008-08-12
well i am currently reading through laroza's c guide, so please don't think I am doing nothing and leaving this to the ubuntu forums programming group.

Just wondering if anyone has done anything like this in the past, as I don't really want to learn all there is to C, just want a solution.  I'm willing to learn to make this happen, but would also like to have this work ASAP.

---

### Post by lapubell on 2008-08-12
kpatz:
do you have valid syntax for that?  I tried that earlier and broke my sudoers file.  I know how to make a user system wide unprompted for passwords, but that is way too unsecure for my tastes...

---

### Post by Bachstelze on 2008-08-12
Something like:

```

user ALL=(ALL) NOPASSWD: /path/to/script.sh
```

Of course, replace user with the name of the user that will be permitted to run it password-less, and enter the correct path to the script ;)

---

### Post by lapubell on 2008-08-12
wow.  thank you.  I feel like michael bolton from office space right now.  stupid syntax mistakes suck.

thanks a million.

---

