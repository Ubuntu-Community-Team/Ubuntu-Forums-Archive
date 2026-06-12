---
title: "Error While Updating System Packages."
date: 2011-12-03
forum: New to Ubuntu
---

### Post by ravi sharan on 2011-12-03
Hello There, 
           I am using ubuntu 11.10 at present. I could not update my system packages since last 8 days. When I try to Update via terminal I get this message. Please help out !

ERROR MESSAGE :


W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG 928C86FE5879C434 Launchpad PPA for Claudio Novais
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG 73AD8184264CE9C6 Launchpad PPA for Simon Schneegans
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by navaleshubham10 on 2011-12-04
just download ubuntu 11.10 from [www.ubuntu.com](www.ubuntu.com) and nurn image to cd and while installing just click on the ption which says "update while installing ubuntu"

---

### Post by Dubslow on 2011-12-04
Try using different repositories to update the packages. There are literally tons of mirrors around the world, and in the US, lots of Universities as well as some Government institutions have excellent Ubuntu mirrors. It is odd that you would get an invalid signature key from Canonical, but there's not much you can do to fix it. 

(I can't provide step by step directions because my Ubuntu is conked at the moment and my thread here has gone nowhere.)

You might also try running 
```
apt-get update
``` first before changing repositories. You'll probably need to sudo that.

---

### Post by enjoijesus94 on 2011-12-04
open a terminal and type 
sudo apt-get update

or 

sudo apt-get upgrade

give the output

---

### Post by ravi sharan on 2011-12-04
> **enjoijesus94 said:**
> open a terminal and type 
sudo apt-get update

or 

sudo apt-get upgrade

give the output
I get Same Message when I tried those Commands ! :P

---

### Post by ravi sharan on 2011-12-18
That was just a GPG error( I resolved the problem) : I am pasting the useful(easiest commands) to resolve the problem



$ sudo -i

# apt-get clean

# cd /var/lib/apt

# mv lists lists.old

# mkdir -p lists/partial

# apt-get clean

# apt-get update




This will rebuild the cache !

---

### Post by ravi sharan on 2011-12-18
ant the problem is solved

---

