---
title: "Need a knowledge boost"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by jhazard112 on 2013-04-15
Hi All,

I am working with Ubuntu 12.04 Server, and I have a question that I am not sure how to research.  I was trying to install something the other day, and provided something like the following:

sudo add-apt-repository ppa:something-blah/whatever

And it would not install.  I am not exactly sure what PPA is, or how it works.  I know that it works on Desktop no issues, but never really know where to look.

As always, any help is much appreciated (pointing in the right direction).

Justin

---

### Post by Bucky Ball on 2013-04-15
Could you be more specific? The PPA you are attempting to install may be down or obsolete and no longer available. Which PPA is it?

Also, you might have more luck if you change your thread title to something that gives some information about and relates to your actual issue, such as 'Can't install PPA', perhaps including the name of the PPA that won't install.

---

### Post by Paqman on 2013-04-15
Without telling us what the PPA was, and what error the machine spat out when you tried to add it, it's pretty much impossible for us to tell you what went wrong.

PPAs are Personal Package Archives. Your machine normally connects to only the official Ubuntu repositories to get software. By adding a PPA you're adding an extra source of software. The PPA could contain anything, by adding the PPA you're saying you trust the people/person that maintains the PPA and the software it contains.

---

### Post by Bucky Ball on 2013-04-15
> **Paqman said:**
> Without telling us what the PPA was, and what error the machine spat out when you tried to add it, it's pretty much impossible for us to tell you what went wrong ... By adding a PPA you're adding an extra source of software. The PPA could contain anything, by adding the PPA you're saying you trust the people/person that maintains the PPA and the software it contains.

+1.

---

### Post by Cheesemill on 2013-04-15
Another issue you may be having is that by default a server installation doesn't have the add-apt-repository command installed.
To install it you need to do...
```
sudo apt-get install python-software-properties
```

---

