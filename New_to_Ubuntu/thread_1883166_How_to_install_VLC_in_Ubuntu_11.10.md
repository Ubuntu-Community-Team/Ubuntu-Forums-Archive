---
title: "How to install VLC in Ubuntu 11.10"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by Wilfred Padambo on 2011-11-18
Is there any other way of installing aplications in Ubuntu 11.10 successfully than using Terminal? My Terminal doesn't work. It always gives me errors like this: 
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  407  Proxy Authentication Required

Please help me coz I can't play any media file.

Wilfred

---

### Post by tartalo on 2011-11-18
Are you using a proxy?
[http://www.linuxforums.org/forum/debian-linux/55599-configuring-proxy-synaptic-package-manager-ubuntu.html](http://www.linuxforums.org/forum/debian-linux/55599-configuring-proxy-synaptic-package-manager-ubuntu.html)

---

### Post by corncob on 2011-11-18
> **Wilfred Padambo said:**
> Is there any other way of installing aplications in Ubuntu 11.10 successfully than using Terminal? My Terminal doesn't work. It always gives me errors like this: 
 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  407  Proxy Authentication Required

Please help me coz I can't play any media file.

Wilfred

Why not use the Ubuntu Software Center?  It looks like a grocery bag in that stack of launchers on the left of your screen.  When it opens, search for VLC or whatever.  If your terminal is working (I can't get to that URL either) you might want to download Synaptic Package Manager as another software source
```
sudo apt-get install synaptic
```
I haven't gotten into 11.10 but in the past I followed instructions at
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
to get my media running.

---

### Post by Daveth on 2011-11-18
this gives you a graphical way to add VLC
[HTML]http://www.videolan.org/vlc/download-ubuntu.html[/HTML]

---

### Post by Wilfred Padambo on 2011-11-27
Thanks for the suggestions but the problem I think its because am working behind a proxy server and I can't get the proxy settings working on my machine. I can't update using terminal and install synaptic. If you have a way to get my terminal install synaptic.

Thanks

Wilfred

---

### Post by Corporation on 2011-11-27
You probably need to set your proxy up globally.

Go into Settings > Network > Network Proxy and input your authentication details in there.

Alternatively, if your proxy is a Windows NTLM proxy, you should grab [CNTLM](http://cntlm.sourceforge.net/) and use that to set it up.

---

