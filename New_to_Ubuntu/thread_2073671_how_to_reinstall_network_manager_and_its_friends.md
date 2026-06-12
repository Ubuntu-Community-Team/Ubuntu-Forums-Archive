---
title: "how to reinstall network manager and its friends"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by kruget on 2012-10-20
One day my pdnsd stopped working. 
sudo netstat -lpn |grep:53 implied that the port used by dnsmasq.
So I mindlessly apt-get remove the dnsmasq because it refused to be killed.

Unfortunately some important packages wiped out automatically in the process. 
Right now, the network icon on upper right screen is lost.
And my netbook can't browse the internet although it can ping google correctly.

How to cure this without reinstalling the Xubuntu from the scratch?

Update:
Marked as solved.

After doing some stuff that i don't really understand, i can reinstall the network-manager and get it back to its previous condition.

---

