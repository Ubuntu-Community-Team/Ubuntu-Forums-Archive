---
title: "GPG Error on Update"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by gunksta on 2011-09-27
Looked through the list and I don't see anything that looks similar, but I am getting a strange set up errors when updating.

```
 sudo aptitude update 
```

For the record, I also tested apt-get update, and the errors are the same.

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I'm not sure how this could have happened. I did some googling and this seems to have directions for fixing the problem, but I thought I would make sure these were solid directions before following them. I don't want to mess up the security on my system.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I'm also curious to see if anyone has any idea regarding how this could have happened.

---

### Post by dino99 on 2011-09-27
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

---

### Post by gunksta on 2011-09-27
That did it. Thanks.

---

