---
title: "Kubuntu APt-geT problem"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by mjunaiddar on 2008-09-01
Hello All,

I am totally new to kubuntu, I was dreaming if I would ever be able to install some packages at mu KUbuntu system installed via the live CD within the Windows XP right. Now the issue is here that after a fresh install and configuring my network settings I tried to install MySQL using apt-get, "sudo apt-get install mysql-server" this is the command I searched from google, but it failed saying mysql-server not found ..... 

some forum says i have to run "sudo apt-get update" and then it will run but when i run it the following errors come:

sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
......
Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
........
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


NOTE I have omited some text to shorten the lenth of the post.

I would highly thankful to u all if i get a reply very very quick 

A detailed one will be more good :D as m very very new to linux world

Regards
Junaid

---

### Post by Archmage on 2008-09-01
It looks like you don't have any internet conection at all for the update.

---

### Post by mjunaiddar on 2008-09-01
oh no dear m right now using the same system !!! even i am writing the reply from it

---

### Post by mjunaiddar on 2008-09-01
I have internet connection running well, there might be any other configuration problem, please help me somebuddy ...

---

### Post by mjunaiddar on 2008-09-01
I just found this command 

sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a

but it is also not working for any install I tried this command now:

apt-get install libxine1-ffmpeg
and this is the error
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by emshains on 2008-09-01
Are you typing ```
apt-get install
``` or ```
sudo apt-get install
``` ?

---

### Post by t0p on 2008-09-01
> **mjunaiddar said:**
> I tried this command now:

apt-get install libxine1-ffmpeg
and this is the error
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

That command failed because you didn't prefix it with "sudo".  apt-get needs to be run with admin privileges.  So the command should have been:

```
sudo apt-get install libxine1-ffmpeg
```

When you are doing an apt-get command, always use sudo.

---

### Post by mjunaiddar on 2008-09-01
OK sorry last time error was because I write it without sudo

but now this is the result with sudo 

# sudo apt-get install libxine1-ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libxine1-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine1-ffmpeg has no installation candidate

and this is what i get for another package 

sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mysql-server

---

### Post by mjunaiddar on 2008-09-01
Hello guys I found the answer at the other community and I want to share it with u ppl to..

I am thankful to ThaRabbit for the help.

[http://ubuntuforums.org/showthread.php?p=5705498&posted=1#post5705498](http://ubuntuforums.org/showthread.php?p=5705498&posted=1#post5705498)

---

