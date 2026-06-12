---
title: "Unable to find a package with apt and dpkg"
date: 2019-08-19
forum: New to Ubuntu
---

### Post by smart14 on 2019-08-19
Hi everyone..

I am struggling with one package on my OS Ubuntu 16.04. For some reason, Ubuntu search (toolbar) is finding application Teamviewer but apt and dpkg are not ! 
I tried to apt and dpkg remove and purge and force, and nothing helped. First I thought that icon is only because some configuration file left, but that icon really opens Teamviewer application. For some reason, that application do not have any information about what version is about, strange.... but I have no clue how to search that package. Probably it could be Teamviewer version 10. Do you have any idea why that package is not found by apt and dpkg ?

Thanks.

---

### Post by DuckHook on 2019-08-19
Did you install the snap version of Teamviewer? If so, then neither apt nor dpkg will find it because snaps are a completely different animal from regular packages.

If you installed Teamviewer through a different method entirely, both apt and dpkg will not work either. Apt and dpkg only work with regular apps installed from the standard repos.

---

### Post by cruzer001 on 2019-08-19
Also check your software sources for teamviewer.
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```
To check installed snap packages.
```
snap list
```

---

### Post by Yellow Pasque on 2019-08-20
In addition to above suggestions, I'd like to add:
1. Be careful with case on the command line. "teamviewer" and "Teamviewer" are two different things in Linux shells.
2. Make use of auto-complete. For example, type "dpkg-query --list team" and then hit tab twice to see if you get any matches.
3. Consider Synaptic as an easier GUI option for this type of search.

---

### Post by cruzer001 on 2019-08-20
+1 for synaptic package manager, it will show all installed .deb packages regardless of their source.

[https://geek-university.com/linux/synaptic/](https://geek-university.com/linux/synaptic/)

---

### Post by smart14 on 2019-08-20
Hi everyone. Thank you so much for helping! :)
I found a package. Finally! And I was shocked when I found out that Teamviewer icon was google chrome extension! So strange and confusing :D 

I found a package with following:
*locate -i "*teamviewer*"  *and just remove extension in Chrome itself.

---

