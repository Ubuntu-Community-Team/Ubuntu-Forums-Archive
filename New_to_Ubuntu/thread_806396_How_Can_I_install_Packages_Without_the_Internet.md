---
title: "How Can I install Packages Without the Internet?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Bob_12 on 2008-05-24
My friend just installed Ubuntu and wants to play mp3s, DVDs, and have a few programs but right now she doesn't have the internet to get the packages from the repositories. Is there any way I can just download the .deb files, put them on a flash drive and then bring them to her so she can do all the things she wants with Ubuntu? Thanks!

---

### Post by CloudFX on 2008-05-24
I know it is possible to get the source code from Launchpad.net for most packages in the repository.

---

### Post by amingv on 2008-05-24
Try:

```
sudo apt-get -d install <package>
```

and then look for the deb in /var/cache/apt/archives

---

### Post by cosine352 on 2008-05-24
I like this 
[http://linuxappfinder.com/all]("http://linuxappfinder.com/all")

---

### Post by Bob_12 on 2008-05-24
Thanks for the help! I hope these work!

---

### Post by joshedmonds on 2008-05-24
If you are running Ubuntu, try an application called AptOnCD. It creates a CD containing all of your installed apps that can be used as a CD repository in Synaptic (Settings->Repositories->[Third Party Software]->Add CD-ROM).

Unfortunately it does not appear to work for DVDs or USB flash drives (feel free to correct me if I'm wrong!)

---

### Post by sam_delta on 2008-05-24
you can always download a .deb package from ubuntu archives and install it in any ubuntu system

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

sam

---

