---
title: "should bash completion be installed by make?"
date: 2012-07-24
forum: Packaging and Compiling Programs
---

### Post by PGScooter on 2012-07-24
When installing using configure; make; sudo make install

should this also install the bash completion script to /etc/bash_completion.d/ ?

Or is this the job of the packager? If so, why? Because the directory could be different depending on the distribution?

Thanks

---

### Post by SevenMachines on 2012-07-25
Personally I would have thought it's a packaging thing, it's a thing relating to integration  into a distribution, rather than intrinsic to the software itself. I've no idea if theres a policy on it, a quick survey of a few packages in the repository sees that they do both.

Note theres a debhelper for it installed from the bash-completion package that installs from debian/package.bash-completion


dh_bash-completion

---

### Post by PGScooter on 2012-07-25
ok thanks for the reply. Thats good to know.

---

