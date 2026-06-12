---
title: "synaptic and apt-get problems with install"
date: 2006-04-14
forum: Repositories &amp; Backports
---

### Post by pixel80r on 2006-04-14
I have a squid - squidGuard - apache 2 ubuntu system running for basic web proxy and reporting. So far this is working well. Now I want to set up authentication with our windows server active directory. I found the ActiveDirectoryHowTo wiki page and tried to install the required packages. Heres the problem. I get the error:

krb5-user:
  Depends: libkrb53 but 1.3.4-3ubuntu0.2 is to be installed
  Depends: libkadm55 but 1.3.4-3ubuntu0.2 is to be installed

I get the same error using synaptic and apt-get.
can anyone explain what this means and how to resolve it?

thanks

---

### Post by aysiu on 2006-04-14
Usually, dependency errors result from having conflicting repositories.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

