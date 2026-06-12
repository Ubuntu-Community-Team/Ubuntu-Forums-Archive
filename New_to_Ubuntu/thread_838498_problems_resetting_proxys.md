---
title: "problems resetting proxys"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by simon303 on 2008-06-23
I have just returned from university for the summer and am having a few problems changing the proxy settings.
At university I had to set it up to connect to the internet through proxys.
At home I don't, I have managed to change some of the programs and and the network proxys back to nothing through the gui, but at university to set it up properly I was required to change http_proxy, ftp_proxy, gopher_proxy and no_proxy.
I have tried setting these to "" but every time I run apt-get it tries to connect through my universities proxys and so fails
Any ideas on how to reset these/change the setting for apt (I have changed the settings in synaptic)
Thanks
Simon

---

### Post by simon303 on 2008-06-24
I can set the http_proxy to "" and it works, then when I restart bash it goes back to the old settings.
Also there are things that are there to be installed but it is not installing them
```
simon@simon-desktop:~$ export http_proxy=""
simon@simon-desktop:~$ sudo apt-get upgrade
[sudo] password for simon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

---

