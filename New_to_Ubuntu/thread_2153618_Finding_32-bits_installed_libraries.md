---
title: "Finding 32-bits installed libraries"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by _0R10N on 2013-06-11
Hi! A few days I installed a couple of 32 bits libraries on my 64 bits Ubuntu so I could get a 32-bits application running. The thing is it didn't work and I'd like to get rid of all 32-bits libraries I installed.

Is there a way to find which 32-bits libraries have been installed?

Thanks!

---

### Post by Frogs Hair on 2013-06-11
If they are un-needed packages the following should work. ```
sudo apt-get autoremove
```

---

### Post by sanderj on 2013-06-11
> **_0R10N said:**
> Hi! A few days I installed a couple of 32 bits libraries on my 64 bits Ubuntu so I could get a 32-bits application running. The thing is it didn't work and I'd like to get rid of all 32-bits libraries I installed.

Is there a way to find which 32-bits libraries have been installed?

Thanks!

If you installed with "sudo apt-get install <blabla>", remove with ... "sudo apt-get remove <blabla>".

HTH

---

### Post by _0R10N on 2013-06-11
Thanks for the replies! I know how to remove unnecessary packages. The thing is they weren't autoremoved when running this command, they where installed as dependencies of openjdk-7-jdk:i386 and some other package.

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]_0R10N; Hi !

How about this approach:
```
apt-cache show openjdk-7-jdk:i386 
```
In the output is a list of dependencies
do:
```
dpkg -l <dependency>
```to see that status,version and other info ?

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-06-11
well I would think if autoremove doesn't remove the then they are still required by some other package - but how about

```
apt-cache depends openjdk-7-jdk:i386
```

or for a more general list of i386 packages

```
dpkg -l | awk '$2 ~ /:i386/ {print}'
```

---

### Post by _0R10N on 2013-06-13
Thanks to all of you! The @steeldriver and @Bashing-om suggestions work great!

---

