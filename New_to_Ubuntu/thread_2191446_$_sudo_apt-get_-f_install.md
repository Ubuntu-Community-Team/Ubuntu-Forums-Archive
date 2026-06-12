---
title: "$ sudo apt-get -f install"
date: 2013-12-02
forum: New to Ubuntu
---

### Post by josephhowarth on 2013-12-02
Hello All

I am trying to understand the above command line a little. I have downloaded/installed google chrome and I have done so succesfully using the instructions from [http://www.cyberciti.biz/faq/how-to-install-google-chrome-in-ubuntu-linux-12-xx-13-xx/](http://www.cyberciti.biz/faq/how-to-install-google-chrome-in-ubuntu-linux-12-xx-13-xx/)

one of the instructions (Subject of thread) is to fix an error and I am not to sure what it is doing to correct the error. 

If anyone could shed any light on this it would be greatly appreciated.

thanks
joe

---

### Post by moffa on 2013-12-02
the -f option tries to fix any broken packages for example with missing dependencies etc.  From the apt-get manual (man apt-get) here is the description:
```
   -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dselect(1) or dpkg --remove to eliminate some of the
           offending packages). Use of this option together with -m may
           produce an error in some situations. Configuration Item:
           APT::Get::Fix-Broken.
```

---

