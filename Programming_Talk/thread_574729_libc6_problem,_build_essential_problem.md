---
title: "libc6 problem, build essential problem"
date: 2007-10-13
forum: Programming Talk
---

### Post by joebanana on 2007-10-13
Hi
I just started programming in ubuntu. When I try to compile a code it can't find stdio and other header. I followed some tutorials, updated libc6 by mistake(should have install libc6-dev) but then if i try to install libc6-dev i get an error, which states that libc6 has to be version 2.5 and i have now 2.6. 
If I try to remove libc6 in synaptic (so I could then install correct version) it tries to remove also 3GB of data...

Of course I didn't know back then for apt-get install build-essential and now it doesn't work.

pls help a poor wanna be programmer

---

### Post by Natr0n on 2007-10-13
> **joebanana said:**
> 
Of course I didn't know back then for apt-get install build-essential and now it doesn't work.
What do you mean by "doesn't work" i.e. what kind of error messages are you getting, if any?

---

### Post by joebanana on 2007-10-14
sudo apt-get install build-essential

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

---

### Post by joebanana on 2007-10-14
OK I fixed the problem. I downgraded in synaptic libc6 to version 2.5 and now I can install build-essential. 

thx for tring to help

---

