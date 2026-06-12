---
title: "update info"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by oneemw on 2012-08-14
okay so was offline for some time and just got net again but i do my updates and says they are all done but 1 hour later get a red triangle saying out of date so i check again and says nothing need to be updated. running 11.10 because 12.02 I cant get my wifi so is it something I can do to make this stop. think that its bricked when i see red stuff like that. thanks for your help.

---

### Post by ubudog on 2012-08-14
Try running the command:
```
sudo apt-get update
```

Best,
ubudog

---

### Post by oneemw on 2012-08-15
Did not work i got this in return

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG 5A9A06AEF9CB8DB0 Launchpad PPA for Ubuntu Wine Team
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)

---

### Post by ubudog on 2012-08-15
Could you post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by raja.genupula on 2012-08-15
i believe for GPG this will be good

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get  update

```
but OP first have to start with removing duplicate line.

---

