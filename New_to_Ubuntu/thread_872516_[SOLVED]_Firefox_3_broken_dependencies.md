---
title: "[SOLVED] Firefox 3 broken dependencies"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Sprogg2001 on 2008-07-28
Hello 

For some reason update manager removed firefox 3 and installed firefox 2 as part of an "update" I tried to upgrade to FF3 but this did not work.

I then uninstalled firefox 2 and now with no existing firefox installation I am trying to install Firefox 3.

However I am getting the following message.

```
$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  firefox-3.0: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
               Depends: xulrunner-1.9 (>= 1.9.0.1) but it is not going to be installed
```

Please can you help with this as Far as I can tell both libpango and xulrunner are installed and showing as such in synaptic

---

### Post by eightmillion on 2008-07-28
Have you tried another full upgrade?

---

### Post by eightmillion on 2008-07-28
What I mean by that is
> 
sudo apt-get update && sudo apt-get upgrade

---

### Post by Sprogg2001 on 2008-07-28
I found out what the problem was I didnt have the correct repositorys enabled so synaptic could not find the packages, I feel like an idiot but thanks for the help.

---

