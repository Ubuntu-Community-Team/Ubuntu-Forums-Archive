---
title: "Ubuntu Software shows no search results"
date: 2022-01-23
forum: New to Ubuntu
---

### Post by solidaire on 2022-01-23
Using fully updated 20.04 LTS GUI, when I go to search for something in Ubuntu Software by clicking the magnifying glass in the upper left and typing any search term, e.g. "calendar", the result is always "No Application Found".

I have gotten results this way in the past.  This install has always been on a network behind a VPN in case that matters.

How might I troubleshoot this?

---

### Post by schragge on 2022-01-24
Just to be sure. Does it work in terminal, with **apt search**?
```
apt search calendar
```
Further, does it work in Synaptic?

And finally, does it work in terminal with **pkcon search**?
```
pkcon search name calendar
```

---

### Post by solidaire on 2022-01-24
```
apt search calendar
``` yields plenty of results.

```
pkcon search name calendar
``` does as well

Synaptic Package Manger is not installed by default.  After installing, I get lots of calendar search results.  

In the course of installing it, this happened:

```
~$ sudo apt update
Err:1 http://security.ubuntu.com/ubuntu focal-security InRelease               
  Temporary failure resolving 'security.ubuntu.com'
Err:2 https://download.docker.com/linux/ubuntu focal InRelease                 
  Temporary failure resolving 'download.docker.com'
Err:3 http://us.archive.ubuntu.com/ubuntu focal InRelease                      
  Temporary failure resolving 'us.archive.ubuntu.com'
Get:4 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Fetched 222 kB in 51s (4,367 B/s) 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/focal/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch https://download.docker.com/linux/ubuntu/dists/focal/InRelease  Temporary failure resolving 'download.docker.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by solidaire on 2022-01-26
Conclusion: Disabling the VPN restored normal Ubuntu Software search results.

Even after changing the VPN servers several times, 
security.ubuntu.com

and

download.docker.com

would not resolve.

---

### Post by ActionParsnip on 2022-01-27
Try:
```

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
sudo apt update 

```

Is it OK then?

---

