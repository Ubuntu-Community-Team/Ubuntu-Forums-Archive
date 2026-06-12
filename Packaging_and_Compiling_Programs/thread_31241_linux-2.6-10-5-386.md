---
title: "linux-2.6-10-5-386"
date: 2005-05-02
forum: Packaging and Compiling Programs
---

### Post by Rorqual on 2005-05-02
Hello,
I m french ubuntu user... beginner and more ... :D
and I m looking for package linux-2.6.10-5.386 ...I need it to compile my wifi card driver...
The problem is that i haven't got connection on the needed computer..:/ and I m still looking for this package...big thx for every helper...and really sorry for my ugly english

---

### Post by muhcashin on 2005-05-25
[QUOTE=Rorqual]Hello,
I m french ubuntu user... beginner and more ... :D
and I m looking for package linux-2.6.10-5.386 ...I need it to compile my wifi card driver...
The problem is that i haven't got connection on the needed computer..:/ and I m still looking for this package...big thx for every helper...and really sorry for my ugly english[/QUOTE]
 I want to do the same thing. I have a StarTech.com wireless network card and wish to compile the drivers for them. However, the Makefile is that of RedHat 9.0 and includes sources files that I cannot find in Ubuntu. Where can I find those files? The /usr/src directory seems empty.

---

### Post by Gandalf on 2005-05-25
[QUOTE=muhcashin]I want to do the same thing. I have a StarTech.com wireless network card and wish to compile the drivers for them. However, the Makefile is that of RedHat 9.0 and includes sources files that I cannot find in Ubuntu. Where can I find those files? The /usr/src directory seems empty.[/QUOTE]
 you can't do it without internet connection, try to connect at least with LAN

once connected type
```

sudo apt-get install linux-headers-`uname -r`

```

---

### Post by FatherDale on 2005-08-27
Thank you, Gandalf. Every time I try to install the build-essentials, I have to google it. Wonder why they don't just include it in the distro?

---

