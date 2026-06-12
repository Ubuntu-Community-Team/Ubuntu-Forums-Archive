---
title: "KDevelop 3.2"
date: 2005-03-22
forum: Programming Talk
---

### Post by santo on 2005-03-22
How can I install KDevelop v3.2 in Kubuntu ?

The latest version available in the repositories seems to be v3.1.2 and I really need v3.2

I already tried to install using the debian/sid unstable repository, but then I get som error messages about broken packages:

```

santo@desktop01:~$ sudo apt-get -s install kdevelop3
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdevelop3: Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu4 is to be installed
             Depends: libidn11 (>= 0.5.13) but 0.5.2-3 is to be installed
             Depends: kdevelop3-plugins (>= 4:3.2.0) but 4:3.1.2-1ubuntu2 is to be installed
E: Broken packages

```

Any help appreciated

---

### Post by lao_V on 2005-03-22
Have you tried installing the missing packages?

---

### Post by santo on 2005-03-22
Actually, they are already installed:

```

santo@desktop01:~$ sudo apt-get -s install libfontconfig1 libidn11 kdevelop3-plugins
Reading Package Lists... Done
Building Dependency Tree... Done
libfontconfig1 is already the newest version.
libidn11 is already the newest version.
kdevelop3-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I suppose they were installed with the previous version of KDevelop  :roll:

---

### Post by Grock on 2005-04-03
When I try to install mplayer-powerpc the same thing that happened to you happens to me.
mplayer-powerpc:
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed

Where Can I Get The Newest Versions!

Maybe it's ppc only problem, I saw 86 libs with that vers. but it's a ppc mplayer package so I don't get it.

Anyway I get the same error.

---

### Post by lyeinyoureye on 2005-04-05
I'm using x86 arch and I'm having the same problem, I think it might be related to one of the debian repositories being down?

---

### Post by Nez7165 on 2005-04-05
I have the same prob anyone sort it. Please tell me so i can. Thanks

---

