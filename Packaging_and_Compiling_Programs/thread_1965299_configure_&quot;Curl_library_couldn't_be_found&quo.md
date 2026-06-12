---
title: "configure: &quot;Curl library couldn't be found&quot;"
date: 2012-04-25
forum: Packaging and Compiling Programs
---

### Post by sanderj on 2012-04-25
The ./configure of a program results in:


```
checking for libcurl... configure: error: 
			Curl library couldn't be found
			*** Try using --with-libcurl_libraries

```

And

```
./configure --with-libcurl_libraries 

```
results in the same error message

I have libcurl3 already installed. Ubuntu 11.10.

I couldn't find the error message with Google

Any tips how to solve this?

---

### Post by dniMretsaM on 2012-04-25
You need the development headers. Run this:
```
sudo apt-get install libcurl-dev
```

---

### Post by oldos2er on 2012-04-25
Moved to Packaging and Compiling Programs.

---

### Post by sanderj on 2012-04-25
> **dniMretsaM said:**
> You need the development headers. Run this:
```
sudo apt-get install libcurl-dev
```


```
sander@R540:~/Downloads/nntpgrab-0.7.1$ sudo apt-get install libcurl-dev
[sudo] password for sander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcurl-dev is a virtual package provided by:
  libcurl4-openssl-dev 7.21.6-3ubuntu3.2
  libcurl4-nss-dev 7.21.6-3ubuntu3.2
  libcurl4-gnutls-dev 7.21.6-3ubuntu3.2
You should explicitly select one to install.

E: Package 'libcurl-dev' has no installation candidate

```

I installed all three of them, but still the same error message.

Tips how to proceed?

.

---

### Post by dniMretsaM on 2012-04-25
What are you trying to compile?

---

### Post by sanderj on 2012-04-25
> **dniMretsaM said:**
> What are you trying to compile?

nntpgrab

There is a ppa for this, but there is a bug in the software, so I want/need to compile from source.

---

### Post by sanderj on 2012-04-25
I also tried the source from the PPA, hoping it would install dependency libs, but no luck: same error message



```
sander@toverdoos:~/kul$ apt-get source nntpgrab
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 2,279 kB of source archives.
Get:1 http://ppa.launchpad.net/openftd/ppa/ubuntu/ oneiric/main nntpgrab 0.7.1-1~oneiric1 (tar) [2,265 kB]
Get:2 http://ppa.launchpad.net/openftd/ppa/ubuntu/ oneiric/main nntpgrab 0.7.1-1~oneiric1 (diff) [12.7 kB]
Get:3 http://ppa.launchpad.net/openftd/ppa/ubuntu/ oneiric/main nntpgrab 0.7.1-1~oneiric1 (dsc) [1,603 B]
Fetched 2,279 kB in 1s (1,725 kB/s)
gpgv: Signature made Thu 10 Nov 2011 09:35:54 PM CET using DSA key ID 51D1AC8A
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./nntpgrab_0.7.1-1~oneiric1.dsc
dpkg-source: info: extracting nntpgrab in nntpgrab-0.7.1
dpkg-source: info: unpacking nntpgrab_0.7.1.orig.tar.gz
dpkg-source: info: applying nntpgrab_0.7.1-1~oneiric1.diff.gz
dpkg-source: info: upstream files that have been modified: 
 nntpgrab-0.7.1/config.guess
 nntpgrab-0.7.1/config.sub
sander@toverdoos:~/kul$

sander@toverdoos:~/kul$ cd nntpgrab-0.7.1/
sander@toverdoos:~/kul/nntpgrab-0.7.1$ 



checking if GLIB >= 2.14.0... yes
checking for libcurl... configure: error: 
			Curl library couldn't be found
			*** Try using --with-libcurl_libraries
		
sander@toverdoos:~/kul/nntpgrab-0.7.1$ 



```

---

