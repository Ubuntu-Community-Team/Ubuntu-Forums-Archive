---
title: "Custom CD"
date: 2009-02-09
forum: Packaging and Compiling Programs
---

### Post by joe_91 on 2009-02-09
Hey guys,

I'm making a custom CD for our use and have a question regarding the "correct" way to override existing package configurations.

For example, say want to customise /etc/issue, however it belongs to base_files or /etc/ssh/sshd_config, but that belongs to openssh

What is the correct procedure for packaging up generic changes to files like this so that I can have that as a custom package on my CD without clashing with the origin packages ownership?

Thanks

 -- joe.

---

