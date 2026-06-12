---
title: "Help Downloading handbrake"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by dylan9 on 2014-02-04
I ran this
 
```
sudo add-apt-repository **ppa:stebbins/handbrake-releases**
```

I got the PPA from here: [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

All seems well

I then run ```
Sudo apt-get update
```

I get this response 

```
W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found

W: Failed to fetch https://launchpad.net/~stebbins/+archive/handbrake-releases/dists/saucy/main/binary-amd64/Packages  

W: Failed to fetch https://launchpad.net/~stebbins/+archive/handbrake-releases/dists/saucy/main/binary-i386/Packages  

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by oldos2er on 2014-02-04
There is no saucy repo for Handbrake, it only goes up to raring (13.04). You can go to the URL and manually download the raring packages (I don't know if there's more than one), and double-click it to install it with Software Center.

---

### Post by dylan9 on 2014-02-04
Ahh! Understood thanks.

---

