---
title: "Re: Software Installation Error"
date: 2015-09-03
forum: New to Ubuntu
---

### Post by steve3332 on 2015-09-03
Earlier today I got an error during a package update about /boot being too full so I installed Synaptic in order to clean out the older kernels. While installing Synaptic I saw an error message about something wrong with "postfix" but Synaptic did install. In fact, in Dash I now have two Synaptic icons though only one responds to a mouse click. If I right click on the non-responsive one it is linked to Synaptic-pkexec. I opened a terminal window, installed Synaptic from there and got the following:

newaliases: warning: valid_hostname: numeric hostname: 73015
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 73015
dpkg: error processing package postfix (--configure):
subprocess installed post-installation script returned error exit status 75
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
E: Sub-process /usr/bin/dpkg returned an error code (1)

I did let the update procede which installed the new kernel and at the end of that process there was a similar error but the update did complete just fine.

I'm running 14.04 LTS by the way.

Sound familiar to anyone?

Thanks.
+

Did a little more reading and this may be due to the numeric host name but it seems to me that if Ubuntu didn't want a numeric host name, it could have said so at the beginning. I'll research into changing the host name to a non-numeric and see if that works.

The installation error was due to the numeric host name so I went through the process and changed the name to an alphabetical one and all is well there but, I'm still left with two Synaptic icons in Dash. One icon launches Synaptic and one does not.

Major problem solved, minor one I'll re-post in it's own thread.

---

