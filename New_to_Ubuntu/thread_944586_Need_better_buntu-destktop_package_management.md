---
title: "Need better *buntu-destktop package management"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-10-11
I was testing various desktop environments (just about every one available) and now I have a machine filled with hundreds of programs that are installed with Kubuntu, Xubuntu, Fluxbuntu...... and so on and so forth.  The auto-remove apt feature doesn't get rid of all the programs because they are installed as programs in their own right when one of the *-desktop packages are installed.  

Wouldn't it be nice if one could simply remove a *-desktop?  with one simple little command or press of a button?  Wouldn't that make life easier?  Am I just being silly?

JTS

---

### Post by jerome1232 on 2008-10-11
I have to agree that the meta packages are a pain to remove, it's always been a gripe of mine. I end up doing 'apt-cache show meta-package-here' then figure out which packages in the list need to go.


But then again apt/aptitude is widely regarded as one of, if not THE best package managers out there.

---

### Post by SunnyRabbiera on 2008-10-11
> **jerome1232 said:**
> I have to agree that the meta packages are a pain to remove, it's always been a gripe of mine. I end up doing 'apt-cache show meta-package-here' then figure out which packages in the list need to go.


But then again apt/aptitude is widely regarded as one of, if not THE best package managers out there.

I agree, for me apt runs circles around urpmi, YAST, YUM and Pacman

---

### Post by DGortze380 on 2008-10-11
I find that 'aptitude' works very well for removing desktop environments. I end up with very few left over apps.

---

### Post by snowpine on 2008-10-13
If you use 'aptitude install ubuntu-desktop' (as opposed to apt-get), then you can 'aptitude remove ubuntu-desktop'.

If you were not thinking ahead and used apt-get instead of aptitude, follow these instructions: 

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

(edit) ps. Fluxbuntu should not be on this list; there is no 'fluxbuntu-desktop' package in the repositories. :)

---

### Post by jerome1232 on 2008-10-13
This hasn't worked for me, it still just removes the meta-package. Worked in gutsy didn't in hardy for me. (installing with aptitude and removing with aptitude)

---

### Post by hyper_ch on 2008-10-13
have a look at [http://www.psychocats.net](http://www.psychocats.net) --> Tutorials --> "Pure *"... there you find a list of all the packages each DE installs.

---

