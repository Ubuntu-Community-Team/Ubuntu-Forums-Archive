---
title: "oropo repositories"
date: 2010-12-09
forum: Repositories &amp; Backports
---

### Post by risen75 on 2010-12-09
Ok so i've found a software package that i want to give a try... but i can't seem to get ahold of the package.. it's in a repository that i can't seem to get ubuntu (10.10 or 9.04) to accept.  

the repository is

deb [http://students.mimuw.edu.pl/~ms209495/oropo/debian](http://students.mimuw.edu.pl/~ms209495/oropo/debian) sid main

and every time i put it in.. synaptic geeks out.. says:

W: GPG error: [http://students.mimuw.edu.pl](http://students.mimuw.edu.pl) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 73A272A933D81F67

And i have no clue as to how to fix it.. the site its on has the key but i'm not sure how to use it to get access

any help would be appreciated..
thanks

---

### Post by ms209495 on 2011-02-02
You need to add the key to apt:
apt-key add Release.gpg

---

