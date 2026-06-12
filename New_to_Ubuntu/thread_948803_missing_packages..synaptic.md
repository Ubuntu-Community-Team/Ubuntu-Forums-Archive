---
title: "missing packages..synaptic"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by mike22 on 2008-10-15
I'm missing many packages from synaptic package manager. Is there any option in which it shows the packages that aren't installed? Because I only see the packages that are installed in the 'all' category. For instance I tried searching for nmap and kismet. Now I know for sure that it's listed on synaptic, since it shows it on my other computer. Any help would be appreciated, thanks.

---

### Post by jerome1232 on 2008-10-15
What does your sources.list look like?

```
cat /etc/apt/sources.list
```

May also just to make sure update your package list and check again

```
sudo apt-get update
apt-cache show nmap
```

---

### Post by SoftwareExplorer on 2008-11-02
I'm also having this problem. I want to install all the packages related to xcb before I compile git compiz, but search only shows a few installed packages when I know there are about 20 when I search for the same hardy. I checked my sources list and it looks to me like a sources list should. I installed partimage (one of the packages that I tried to find in synaptic) by downloading it from packages.ubuntu.com, and the installer said that the same version was available from a software channel so I know that it is there, but just not showing up in a synaptic search. As a workaround, I'm downloading Kpackage (sudo apt-get install kpackage)as we speek, but it's big, ~50 mb.

---

