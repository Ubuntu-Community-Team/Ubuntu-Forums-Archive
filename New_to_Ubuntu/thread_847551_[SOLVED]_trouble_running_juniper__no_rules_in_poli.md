---
title: "[SOLVED] trouble running juniper:  no rules in policy policy_4 for Linux"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by lpodkaminer on 2008-07-02
I got juniper installed on ubuntu 8. I noticed that I'd often get disconnected from the vpn connection about a minute after connecting. After looking at the .juniper_network/dsHostChecker_linux1.log I found the following lines which I think are the problem:

HCUtil.java:086 (06/27 13:20:05.221)[main] HostChecker: evaluating HC policies
HCUtil.java:086 (06/27 13:20:05.223)[main] HCPolicy: no rules in policy policy_4 for Linux
HCUtil.java:086 (06/27 13:20:05.224)[main] HostChecker: policy policy_4: NOTOK; error = no rules in policy policy_4 for Linux
HCUtil.java:086 (06/27 13:20:05.224)[main] HCPolicy: no rules in policy policy_5 for Linux
HCUtil.java:086 (06/27 13:20:05.224)[main] HostChecker: policy policy_5: NOTOK; error = no rules in policy policy_5 for Linux

I couldn't find anything on google about these policies or this particular problem.

Anyone else have this problem and find a solution? Any help would be much appreciated!

---

### Post by lpodkaminer on 2008-07-23
turned out to be a conflict between my home network and the vpn. when logging into the vpn juniper would update /etc/resolve.conf, but my home network would overwrite /etc/resolve.conf about a minute later. the vpn connection was still valid, so it was a name resolution issue.

---

### Post by EmaNymton on 2008-11-03
> **lpodkaminer said:**
> turned out to be a conflict between my home network and the vpn. when logging into the vpn juniper would update /etc/resolve.conf, but my home network would overwrite /etc/resolve.conf about a minute later. the vpn connection was still valid, so it was a name resolution issue.


Can you share on how you fixed the problem?  I am actually having the same problem where my home and work network seem to disappear when I connect to the vpn.

---

