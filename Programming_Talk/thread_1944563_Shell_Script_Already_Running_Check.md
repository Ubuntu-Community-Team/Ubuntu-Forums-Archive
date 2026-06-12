---
title: "Shell Script Already Running Check"
date: 2012-03-21
forum: Programming Talk
---

### Post by CrusaderAD on 2012-03-21
Is there something I can put at the beginning of my shell scripts to say "If this script is already running, do not run it again.", or does the system only allow one instance of a shell script to run at once?

---

### Post by matt_symes on 2012-03-21
Hi

> **CerealCypher said:**
> Is there something I can put at the beginning of my shell scripts to say "If this script is already running, do not run it again.", or does the system only allow one instance of a shell script to run at once?

The classic way to do it is to create a temporary file somewhere in the filling system at script start up.

Something along these lines

* At startup, the script must test to see if the temporary file exists. 
* If it does then exit then exit. (Another instance running)
* If it does not exist then create the temporary file.
* Delete the temporary file at end of script.

It's not foolproof but has been used before.

Kind regards

---

### Post by ksa618 on 2012-03-21
You could use a lock file.
Put
```

if [ -f /tmp/mylockfile ]; then exit 1; fi
touch /tmp/mylockfile

```at the beginning of the script and
```
rm /tmp/mylockfile
```at the end.

This is vulnerable to race-conditions though.

---

### Post by Lars Noodén on 2012-03-21
Lock files would be one way to do it.  But rather than trying to invent your own system for managing lock files, you can use the built-in function, [flock](http://manpages.ubuntu.com/manpages/oneiric/en/man1/flock.1.html).

---

### Post by SeijiSensei on 2012-03-21
> **ksa618 said:**
> This is vulnerable to race-conditions though.

How exactly?  Got a link I can read?

---

### Post by ksa618 on 2012-03-21
> **SeijiSensei said:**
> How exactly?  Got a link I can read?
Say that one process runs first and gets interrupted just before the touch command. Then another process starts and runs past the touch command. When the first one wakes up again, it will continue with the touch command as if nothing happened, and both are running at the same time.
I don't think flock, as recommended by Lars Noodén above,  has this problem.

---

### Post by SeijiSensei on 2012-03-21
I usually create the lock file as the very first thing the script does before anything else.  I suppose it could die before the file is created, but it doesn't seem very likely in practice.

---

### Post by ksa618 on 2012-03-21
I didn't mean interrupted as in dying, but being interrupted by the scheduler. I should have made that clear.
Anyway, I agree that it's unlikely, but if there is an alternative (flock) that doesn't have this possibility, it's probably better to use it. If your scripts are released to the public and used by many people, you can count on it happening to at least one of them, however small the chance of it happening is.

---

### Post by matt_symes on 2012-03-21
Hi

> **ksa618 said:**
> Anyway, I agree that it's unlikely, but if there is an alternative (flock) that doesn't have this possibility, it's probably better to use it. If your scripts are released to the public and used by many people, you can count on it happening to at least one of them, however small the chance of it happening is.

Flock is a great choice if it is available. Not every environment has it though.

The last script i wrote where i needed a lock file was for my router and it was not available there.

Kind regards

---

### Post by Habitual on 2012-03-21
```
touch /tmp/$$
do something
rm /tmp/$$
```

---

### Post by CrusaderAD on 2012-03-22
Thanks for all the help! I did ksa618's solution:

```
if [ -f /tmp/mylockfile ]; then exit 1; fi
touch /tmp/mylockfile
```

```
rm /tmp/mylockfile
```

Seems to work just fine for my purposes.

---

