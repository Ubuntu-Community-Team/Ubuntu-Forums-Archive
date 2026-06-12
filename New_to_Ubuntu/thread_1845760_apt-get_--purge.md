---
title: "apt-get --purge"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by crumple on 2011-09-17
n00bzor question: if i

apt-get --purge <program X running lua>

will it also purge lua and disable <program Y running lua> when i try to run it? or is there a built-in safety net to prevent this from happening?

---

### Post by Frogs Hair on 2011-09-17
More information would help , such as application names and details . :o

---

### Post by gmargo on 2011-09-17
What exactly will happen depends on the "dependencies" of the packages installed, and on the particular program(s) used to interpret that meta-data and perform the install/remove/purge/etc.

One of the most valuable option flags for **apt-get** (or **aptitude**) is the "**-s**" option (also known as "**--dry-run**" and other aliases), which allows you to preview the actions of the program without performing them.  From the **apt-get** man page:
> 
       -s, --simulate, --just-print, --dry-run, --recon, --no-act
           No action; perform a simulation of events that would occur but do not actually change the system.
So, for whatever action you want to perform, you should test it first by adding a "-s" simulation option.  They you'll see exactly what **apt-get** (or **aptitude**) wants to do before you are committed.

So try:
```

apt-get -s purge <program X running lua>

# -and/or-

aptitude -s purge <program X running lua>

```If the process tries to remove **lua**, report back, as there's an easy way to prevent that.

---

