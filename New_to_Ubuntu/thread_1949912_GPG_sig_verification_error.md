---
title: "GPG sig verification error"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by oscillator on 2012-03-31
I noticed after trying to add Tor to my repositories (which I have abandoned) that I get the following message when reloading my software sources:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B6C6326781C0BE11

This obviously doesn't affect my updates as I've never had a problem, but I think it might be something to do with my ip tables and I'd prefer to get the error sorted. I've had a browse of some relevant threads but don't know enough to glean much from them. I'm thinking maybe some of the following things might help?

'After doing the apt-key command (which fetches the key).  You need to tell the system that you trust it.  

gpg --armor --export KEYID | apt-key add -'

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
I'm guessing if I run these commands relevant to the key I need to verify/get then it will possibly do this due to my iptables: 

Output: gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

but first I need to try this out so what commands should I run?

---

### Post by arochester on 2012-03-31
[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

2nd Page...

---

### Post by oscillator on 2012-03-31
Ok so I've done this: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B6C6326781C0BE11

got this:
 Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys B6C6326781C0BE11
gpg: requesting key 81C0BE11 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

so you mean I should do this next? 
$ sudo -i  # apt-get clean  # cd /var/lib/apt  # mv lists lists.old  # mkdir -p lists/partial  # apt-get clean  # apt-get update

I don't know what cache to clear out, much of it means zilch to me.

---

### Post by oldos2er on 2012-03-31
> **oscillator said:**
> 
gpgkeys: HTTP fetch error 7: couldn't connect to host


The server might be down temporarily. You don't need to run the /var/lib/apt commands.

---

