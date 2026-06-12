---
title: "update-alternatives for java."
date: 2006-01-19
forum: Programming Talk
---

### Post by lvgandhi on 2006-01-19
I had two options for java in update-alternatives --config java. I wanted to add sun jdk path unzipped in /usr/local. I did 
sudo update-alternatives --install /usr/bin/java java /usr/local/jdk1.5.0_06/bin/java 3
of course in single line. After that I wanted to do update-alternatives --config java. even then I did not get the installed alternative. What am I doing wrong?

---

### Post by pertti on 2006-01-20
[QUOTE=lvgandhi]I had two options for java in update-alternatives --config java. I wanted to add sun jdk path unzipped in /usr/local. I did 
sudo update-alternatives --install /usr/bin/java java /usr/local/jdk1.5.0_06/bin/java 3
of course in single line. After that I wanted to do update-alternatives --config java. even then I did not get the installed alternative. What am I doing wrong?[/QUOTE]

I didn't install Java that way, so I don't know what's wrong with that. I installed Java following [these instructions]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca") from the Ubuntu Wiki. In short, you make a .deb package out of Sun's .bin Java installer, install it with dpkg, and the select it using update-alternatives --config java (no need for --install). Plus, you can uninstall it later using dpkg -r.

---

