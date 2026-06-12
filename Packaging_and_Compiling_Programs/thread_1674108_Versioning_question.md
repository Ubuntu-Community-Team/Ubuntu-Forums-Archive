---
title: "Versioning question"
date: 2011-01-23
forum: Packaging and Compiling Programs
---

### Post by fredp on 2011-01-23
Hello

I'm the developer of the Ejecter utility, of which I just released version 0.4.1.
I would like to set up a PPA for distributing this release on Maverick, so I would like to know which version should I give to it: in Ubuntu's repository there is version 0.3.1-0ubuntu3, is it more correct to name it 0.4.1-0ppa1 or 0.4.1-0ubuntu1ppa1? Or what else?

Thank you very much
Federico

---

### Post by SevenMachines on 2011-01-23
I'm certainly no authority on these things but i'd say you want
0.4.1-0~ppa1

-0, since its not in debian
~ppa1, first ppa release

I tend to think of the 'ubuntu' tag as representing ubuntu specific changes, principally to stop the package being auto-synched from debian and so preserve the changes until they can be dropped or ported to the new debian package. Whether it should be used in this case i couldnt say.
 
0.4.1-0~ppa1 means that your ppa version will be superceeded by...

* The first version if it were synched from debian,  0.4.1-1
* The first version if it were uploaded directly to ubuntu, 0.4.1-0ubuntu1

You can look at 
[http://people.canonical.com/~cjwatson/ubuntu-policy/policy.html/ch-controlfields.html#s-f-Version]("http://people.canonical.com/%7Ecjwatson/ubuntu-policy/policy.html/ch-controlfields.html#s-f-Version")

and decide for yourself, generally i think you want to defer to the main repositories for equivalent versions

[EDIT] Note, the tilda ~ is special and means that 
hello-1.2-1ubuntu1 is a higher versioned package than hello-1.2-1ubuntu1~ppa1
which i think is generally what you want

---

### Post by fredp on 2011-01-23
Thank you, I just have one doubt left: whouldn't I get the same behaviour without using the tilda?

0.4.1-0ppa1 will be superceeded by both 0.4.1-1 and 0.4.1-0ubuntu1, or am I wrong?

---

### Post by SevenMachines on 2011-01-23
It certainly will, but it is sorted alphabetically, whereas ~ sorts before everything so it guarantees the order. i.e.

0.4.1-0ubuntu1 > 0.4.1-0ppa1 > 0.4.1-0otherthing1 > 0.4.1-0~ppa1

---

### Post by fredp on 2011-01-23
Very clear, thank you!

---

