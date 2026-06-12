---
title: "No public key error"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by gunashekar on 2012-07-04
I use ubuntu 12.04. I get the following error when I sudo apt-get update
> Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

can someone tell me if there is a problem?

---

### Post by matt_symes on 2012-07-04
Hi

Open a terminal and type (or copy and paste)

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```Enter your password. It will not be echoed to the screen.

Then type

```
sudo apt-get update
```Kind regards

---

### Post by gunashekar on 2012-07-04
Thank you Matt. 
I did as you instructed.
I now get the following error message at the end when I sudo apt-get update
> ....
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

thak you for the support. Do I still have a problem? 
guna

---

### Post by matt_symes on 2012-07-04
Hi 

It's imported the key so that is progress.

Pick a different mirror and then update again. That may help.

I am just about to sleep though.

Kind Regards

---

### Post by gunashekar on 2012-07-04
Thank you matt. I chose different servers.
I still get the BADSIG error. 
Just wondering if there is a problem at all. 
have a good night
regards
Guna

---

### Post by gunashekar on 2012-07-04
Got rid of the problem with Method one from here [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)
These are the steps
```
$ sudo -i

    # apt-get clean

    # cd /var/lib/apt

    # mv lists lists.old

    # mkdir -p lists/partial

    # apt-get clean

    # apt-get update
```

---

