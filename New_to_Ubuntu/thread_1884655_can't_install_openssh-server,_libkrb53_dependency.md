---
title: "can't install openssh-server, libkrb53 dependency"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by toadvine1 on 2011-11-21
Running 11.04. Whenever I try to install openssh-server, I get this error:

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:

The following packages have unmet dependencies: openssh-server : Depends: libkrb53 (>= 1.6.dfsg.2) but it is not going to be installed Depends: openssh-client (= 1:4.7p1-8ubuntu3) but 1:5.8p1-1ubuntu3 is to be installed

E: Broken packages

If I get libkrb53, it removes 389 packages and I lose the GUI. Please, for the love of god, explain this to me. I am very new to Linux and this is making me want to kick my monitor in the face.

---

### Post by fdrake on 2011-11-21
> **toadvine1 said:**
> Running 11.04. Whenever I try to install openssh-server, I get this error:

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:

The following packages have unmet dependencies: openssh-server : Depends: libkrb53 (>= 1.6.dfsg.2) but it is not going to be installed Depends: openssh-client (= 1:4.7p1-8ubuntu3) but 1:5.8p1-1ubuntu3 is to be installed

E: Broken packages

If I get libkrb53, it removes 389 packages and I lose the GUI. Please, for the love of god, explain this to me. I am very new to Linux and this is making me want to kick my monitor in the face.
what doews it says when you try to install openssh-client?
```
sudo aptitude install openssh-client
```

---

### Post by ken631 on 2011-11-21
I used 
sudo apt-get install ssh and it worked fine.

---

### Post by toadvine1 on 2011-11-21
I don't have access to the machine right now, so this is just from memory. openssh-client installed fine, and it still gives me the depdendency error even though it is installed. When I install I use ```
sudo apt-get install openssh-server
``` and I've tried ```
sudo apt-get -f install
``` which did not resolve the issue.

---

### Post by fdrake on 2011-11-21
> **ken631 said:**
> I used 
sudo apt-get install ssh and it worked fine.

> ~$ sudo aptitude show ssh
Package: ssh
State: not installed
Version: 1:5.3p1-3ubuntu7
Priority: optional
Section: net
Maintainer: Colin Watson <cjwatson@ubuntu.com>
Uncompressed Size: 45.1k
_**Depends: openssh-client, openssh-server**_
Description: secure shell client and server (metapackage)
 This metapackage is a convenient way to install both the OpenSSH client and the OpenSSH server. It provides nothing in and
 of itself, so you may remove it if nothing depends on it
he will have the same problem since ssh has the same dependencies.

---

### Post by fdrake on 2011-11-21
@toadvine1
when you get home can you post the result of
```

ssh -v

```
i 'd remove all my previous installation of ssh-client and update reinstall it again. do not attempt a forced install it does not provide good results.

---

### Post by toadvine1 on 2011-11-22
> **fdrake said:**
> @toadvine1
when you get home can you post the result of
```

ssh -v

```i 'd remove all my previous installation of ssh-client and update reinstall it again. do not attempt a forced install it does not provide good results.


i gets:

```
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
```

---

### Post by toadvine1 on 2011-11-22
> **fdrake said:**
> @toadvine1
when you get home can you post the result of
```

ssh -v

```i 'd remove all my previous installation of ssh-client and update reinstall it again. do not attempt a forced install it does not provide good results.

i removed openssh-client and now when i try to install it i get the same unmet dependency for libkrb53.

---

### Post by toadvine1 on 2011-11-22
i am several steps closer to kicking my monitor. all i'm wanting to do is be able to connect through ssh from outside my home network.

---

### Post by fdrake on 2011-11-22
can you try this:
```

sudo apt-get purge ssh-krb5 libapache2-mod-auth-kerb libapache-mod-auth-kerb; 
sudo apt-get update && sudo apt-get upgrade;
sudo apt-get install libkrb5-3; sudo apt-get install openssh-client openssh-server

```

---

### Post by toadvine1 on 2011-11-23
> **fdrake said:**
> can you try this:
```

sudo apt-get purge ssh-krb5 libapache2-mod-auth-kerb libapache-mod-auth-kerb; 
sudo apt-get update && sudo apt-get upgrade;
sudo apt-get install libkrb5-3; sudo apt-get install openssh-client openssh-server

```

you want the whole printout? in the end, i get the same errors.

The following packages have unmet dependencies:
 openssh-client : Depends: libkrb53 (>= 1.6.dfsg.2) but it is not going to be installed
 openssh-server : Depends: libkrb53 (>= 1.6.dfsg.2) but it is not going to be installed
E: Broken packages

---

