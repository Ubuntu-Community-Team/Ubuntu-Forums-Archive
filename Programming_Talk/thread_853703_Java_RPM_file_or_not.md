---
title: "Java RPM file or not"
date: 2008-07-08
forum: Programming Talk
---

### Post by Natilator3 on 2008-07-08
I'm learning how to use java, but when i got to the scanner utility Eclipse said that it cannot be resolved. I look around and this means that my java is too old and that I have 1.4.2

I install the non-RPM file since from past experience I believe that RPM files replace the system's java. should I install the RPM because I don't want to take another 3 hours to download ubuntu *again*

oops, the tags are messed up

---

### Post by tinny on 2008-07-08
> **Natilator3 said:**
> I'm learning how to use java, but when i got to the scanner utility Eclipse said that it cannot be resolved. I look around and this means that my java is too old and that I have 1.4.2

I install the non-RPM file since from past experience I believe that RPM files replace the system's java. should I install the RPM because I don't want to take another 3 hours to download ubuntu *again*

oops, the tags are messed up

Ummm??? Not sure what you are asking, but I think this will help.

```

sudo apt-get install sun-java6-jdk

```

Installs Java 6.

---

### Post by kavon89 on 2008-07-08
Ubuntu doesn't use RPM packages. Being Debian based, it uses deb packages.

Use the Synaptic Package Manager (System -> Administration) and search for sun-java6, then install the JDK and JRE.

After that I believe you need to change Eclipse's settings to use the correct Java version.

---

