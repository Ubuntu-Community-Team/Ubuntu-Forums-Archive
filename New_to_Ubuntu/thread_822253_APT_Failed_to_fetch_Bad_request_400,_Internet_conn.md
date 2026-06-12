---
title: "APT Failed to fetch Bad request 400, Internet connection is fine. Help!"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Kecheri on 2008-06-08
I am unable to use apt or synaptic to update my system.

/etc/network/interfaces is as follows
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.22
network 192.168.1.0
broadcast 192.168.1.255
netmask 255.255.255.0
gateway 192.168.1.1
metric 0
```

ping request to router and google.com works fine, I am able to browse the net, and post this problem.

However, when i do
sudo apt-get update, I get

```
Ign http://in.archive.ubuntu.com hardy Release.gpg
Ign http://in.archive.ubuntu.com hardy/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates Release.gpg
Ign http://in.archive.ubuntu.com hardy-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-security Release.gpg
Ign http://in.archive.ubuntu.com hardy-security/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-security/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-security/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-security/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy Release
Ign http://in.archive.ubuntu.com hardy-updates Release
Ign http://in.archive.ubuntu.com hardy-security Release
Ign http://in.archive.ubuntu.com hardy/main Packages
Ign http://in.archive.ubuntu.com hardy/restricted Packages
Ign http://in.archive.ubuntu.com hardy/multiverse Packages
Ign http://in.archive.ubuntu.com hardy/universe Packages
Ign http://in.archive.ubuntu.com hardy-updates/main Packages
Ign http://in.archive.ubuntu.com hardy-updates/restricted Packages
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Packages
Ign http://in.archive.ubuntu.com hardy-updates/universe Packages
Ign http://in.archive.ubuntu.com hardy-security/main Packages
Ign http://in.archive.ubuntu.com hardy-security/restricted Packages
Ign http://in.archive.ubuntu.com hardy-security/multiverse Packages
Ign http://in.archive.ubuntu.com hardy-security/universe Packages
Err http://in.archive.ubuntu.com hardy/main Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy/restricted Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy/multiverse Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy/universe Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy-updates/main Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy-updates/restricted Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy-updates/multiverse Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy-updates/universe Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy-security/main Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy-security/restricted Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy-security/multiverse Packages
  400 Bad Request
Err http://in.archive.ubuntu.com hardy-security/universe Packages
  400 Bad Request
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  400 Bad Request

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  400 Bad Request

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

The same happens on synaptic. Yes, I tried changing the mirror to India and US(Main).

---

### Post by Xiong Chiamiov on 2008-06-09
Can you post your /etc/apt/sources.list please?

---

### Post by Kecheri on 2008-06-09
Hi,

 Attaching /etc/apt/sources.list 

 Thanks for your willingness to look into the problem. I really dont want to downgrade to Gutsy, which I'd say didn't give me as many awkward problems as hardy.

---

### Post by guilly on 2008-06-09
I didn't take a look at your sources.list but I know that I was having issues last night as well and it was caused by the CA server. I simply changed which server I was contacting and everything seems to be working now.

---

### Post by Kecheri on 2008-06-12
Problem persists. Update / Install works fine on my laptop. The sources.list are the same on both laptop and Desktop.

So, the problem is only with the Desktop. What else should I Check ? 

1) sources.list seems fine
2) Internet connection is alright - I am able to browse the net and post this problem.
3) ping response is fine to archive.ubuntu.com
4) Tried changing Mirror servers (India/Main)
5) tried to get a sources.gz file manually.
```
wget http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz 

```
That works absolutely fine.

What else should I check  ? Please help!

---

### Post by Malfet on 2008-08-07
> **Kecheri said:**
> Problem persists. Update / Install works fine on 
What else should I check  ? Please help!

Don't know it you still care, but I had exactly same problem today and solved it by adding proxy server information. Do you have one? It looks like, still you've put gateway 192.168.1.1. 
Go to Synaptic, then Settings, Network. Choose there Manual proxy settings and type your proxy adress. That should help.

Regards,
M.

---

