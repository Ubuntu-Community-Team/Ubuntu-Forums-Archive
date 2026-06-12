---
title: "Solving the perllocal.pod problem"
date: 2014-02-25
forum: Packaging and Compiling Programs
---

### Post by oliwel on 2014-02-25
Hi,

I am running a project based on perl and we are having a stupid issue with dh-make-perl - google has a lot of people with the same problems but solutions are rare and none of those given helped us out =(

We use dh-make-perl to build some dependencies from cpan, unfortunately some of them require MakeMaker and Module::Build in versions newer than shipped with the distro and install those packages from cpan. As a result we get multiple packages providing the file "/usr/lib/perl/5.14/perllocal.pod" and apt/dpkg complaining about those duplicates. The file itself is a leftover of earlier perl packaging tools and not really required so it wont hurt to just leave it out if the packet. 

Can anybody point me to a solution how to advice dh-make-perl to not produce this file? I am unfortunatly a real noob regarding Makefiles and just want to make that build, so please give verbose answers :P

For a detailed insight, check the project on github: [https://github.com/openxpki/openxpki/tree/master/package/debian](https://github.com/openxpki/openxpki/tree/master/package/debian)

best regards 

Oliver

---

### Post by TheFu on 2014-02-25
Never use the distro provided perl or perl modules if you are a hard-core perl programmer. 
ALWAYS use **perlbrew** to control the environment for your programs. This is a best practice for all the "p/r*" languages. Each has a perlbrew-like solution.

I've never used dh-make-perl - since we deploy to production using clones of our perlbrew areas.

Sorry, this wasn't the answer you are seeking ... there isn't an answer, only a complete change in process will solve it for good.

---

