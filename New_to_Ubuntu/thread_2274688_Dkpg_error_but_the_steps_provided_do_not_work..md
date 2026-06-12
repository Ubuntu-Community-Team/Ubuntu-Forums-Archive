---
title: "Dkpg error but the steps provided do not work."
date: 2015-04-21
forum: New to Ubuntu
---

### Post by nbp-raptor on 2015-04-21
Hello all,

  I am fairly new, however i don't mind getting a lil dirty in terminal. I am running Ubuntu 14.04 on a 32-bit system. I went to open up Synaptic Package Manager and got an error reading "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "  I proceeded to open terminal and run said command (both regular and with sudo) and it did not work. Below is the terminal output.

```
kanti@PandoraPrime:~$ sudo dpkg -configure -a
dpkg: error: unknown option -o

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
```

I am kind of confused because as you can see i did not put in -o so i don't understand the relevance of it being an unknown option.  Thanks in advanced, and sorry if something with this post doesn't jive, i really tried to make sure to follow the rules :)

---

### Post by Impavidus on 2015-04-21
You need two dashes in front of configure, not one. By using one dash you say you want the options c, o, n, f, i, g, u, r and e. This comes from the older convention that single letter options can be grouped together after a single dash, so long options need a double dash.

---

### Post by nbp-raptor on 2015-04-21
Oh, I understand thank you very much I will try that when I get home. Thank you! :)

---

