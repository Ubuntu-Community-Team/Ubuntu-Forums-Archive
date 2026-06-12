---
title: "What it means"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by czgirb on 2012-05-17
This morning, when update manager was run, it showed:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8

What it means? How can it be solved?
Please guide me ...

---

### Post by critin on 2012-05-18
Hello, I found a couple of links for you.  They should help.

[http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/  ]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/%20%20http://ubuntuforums.org/showthread.php?t=1869890")

[http://ubuntuforums.org/showthread.php?t=1869890]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/%20%20http://ubuntuforums.org/showthread.php?t=1869890")

---

### Post by idoitprone on 2012-05-18
> **czgirb said:**
> This morning, when update manager was run, it showed:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8

What it means? How can it be solved?
Please guide me ...

You need your keys keys keeeyyys

Every package in ubuntu is signed and you need keys to fetch and Install them. I do not understand how this process work because it get compilcate for an idoit like meeeeeeeeeeeeeeeeeee

```


sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FB8BEE0A1F196A8
```[COLOR=Black]

Does it do the trick?
[/COLOR]

---

### Post by czgirb on 2012-05-21
> **idoitprone said:**
> [COLOR=Black]
... Does it do the trick?
[/COLOR]

How can we know **does it do the trick or not?** Please help

---

### Post by Bucky Ball on 2012-05-21
> **czgirb said:**
> How can we know **does it do the trick or not?** Please help

Open a terminal (Applications>Accessories>Terminal) and paste in the command idiotprone provided, hit return and it should do the trick ... ;)

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FB8BEE0A1F196A8
```

---

### Post by czgirb on 2012-05-21
**Application > Accessories > Terminal** and paste the given code > **Enter**.
**System > Administration > Update Manager**, when it was 78 of 80, the following information showed up:
> 
[I]The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/I]
What it means?

---

### Post by Bucky Ball on 2012-05-21
I would open your Software Sources and untick the repository that is giving the error:

[I][http://ppa.launchpad.net/sevenmachin...86/Packages.gz]("http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz")

[/I]It is longer than that, obviously. The error is telling you:

> *The repository may no longer be available or could not be contacted because of network problems.* 

I gather the repository at fault you installed sometime? They may just be having problems with their server/mirror and you might want to try again tomorrow or just untick it for awhile and try again in a few days ...

---

### Post by czgirb on 2012-05-22
> **Bucky Ball said:**
> 
I would open your Software Sources and untick the repository that is giving the error:

[I][http://ppa.launchpad.net/sevenmachin...86/Packages.gz]("http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz")
[/I]It is longer than that, obviously. The error is telling you:

I gather the repository at fault you installed sometime? They may just be having problems with their server/mirror and you might want to try again tomorrow or just untick it for awhile and try again in a few days ...

Currently, I guess the **ERROR** was caused by my missing **GIMP**.
For about a week, I unable to find my **GIMP** within **Application > Graphic**
I tried to re-install with both **Software Center** and **Terminal**, but all said the **GIMP was installed**. When I try to re-install, they said since the **GIMP** was **never installed**, so they cannot to make any **uninstall**.
Do anybody have a clue?

---

### Post by idoitprone on 2012-05-22
> **czgirb said:**
> Currently, I guess the **ERROR** was caused by my missing **GIMP**.
For about a week, I unable to find my **GIMP** within **Application > Graphic**
I tried to re-install with both **Software Center** and **Terminal**, but all said the **GIMP was installed**. When I try to re-install, they said since the **GIMP** was **never installed**, so they cannot to make any **uninstall**.
Do anybody have a clue?
```
 sudo apt-get reinstall gimp
```

---

### Post by Bucky Ball on 2012-05-22
> **czgirb said:**
> 
I tried to re-install with both **Software Center** and **Terminal**, but all said the **GIMP was installed**. When I try to re-install, they said since the **GIMP** was **never installed**, so they cannot to make any **uninstall**.
Do anybody have a clue?

Uninstall it and then reinstall and see if that makes any difference.

---

### Post by czgirb on 2012-05-23
> **Bucky Ball said:**
> Uninstall it and then reinstall and see if that makes any difference.

I tried to **re-install** GIMP, both with **Software Center** and **Terminal**, but all said the **GIMP was installed**.
*** So, the system say ... re-install is not allowed.

So, I wish to do an **uninstall** and **reinstall** proses.
*** Once again, the system say ... since it was **never installed**, it's impossible to do any **uninstall** proses

Do anybody have a clue?

---

