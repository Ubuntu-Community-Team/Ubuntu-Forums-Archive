---
title: "Failed to fetch when I want to update package"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by biela on 2011-12-02
Im using Ubuntu Server 10.10

whenever I try to upgrade
sudo apt-get update

it reply with failed to fetch file

w : Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz). temporary failure resolving 'security.ubuntu.com'

w : Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_SG.bz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_SG.bz). temporary failure resolving 'security.ubuntu.com'

w : Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz). temporary failure resolving 'archive.ubuntu.com'

w : Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_SG.bz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_SG.bz). temporary failure resolving 'archive.ubuntu.com'

---

### Post by wolfen69 on 2011-12-02
It's probably just that the server is temporarily down.

---

### Post by Rubi1200 on 2011-12-02
Hi and welcome to the forums biela :)

As wolfen69 suggested, the server could be temporarily down.

Wait a few hours and then try again.

If that still doesn't resolve the issue then try switching your download mirror to the Main Server (accessed via either Synaptic or the Ubuntu Software Center).

---

### Post by biela on 2011-12-02
Hi.Thank you for the reply.I've been trying to find the solution.

Im using command line.
Can you teach me how to change the mirror.
Is it at the /etc/apt/sources.list

---

### Post by biela on 2011-12-07
Anyone can help me.

I am still having this issues.
I try all the solution regarding 'failed to fetch' from this forum.
I changed the url for the server but still the error 'Failed to fetch' come out.


:(

---

