---
title: "cowbuilder (pbuilder) how to keep chroot build results?"
date: 2014-10-15
forum: Packaging and Compiling Programs
---

### Post by russkubik on 2014-10-15
I am using cowbuilder to build debian packages (debuild). The resulting debian packages are dumped in a folder I specify and I can do whatever I like with them. Perfect, but, I would also like to run my unit-tests (single binary) and transfer the results (*.xml) along with the debians. The only way I can think of doing it (which has limitation which I need help with) is:

- Some obscure option to pbuilder/cowbuilder to prevent it from removing the "cow.PID" folder where the build is being performed. There is a preserve-build option but it is not what is seems to be.

- pbuilder post-build hook to login to the chroot. I fall short where, after running the unit tests, I have no idea how to transfer the resulting xml file(s). I have no idea where people go for pbuilder hook help, I find random examples here and there but no informative full documentation.

My build command:

```
/usr/sbin/cowbuilder --build build/*.dsc --buildresult results --basepath ${base_path} --buildplace cow_build
```

Is this possible to do?

---

