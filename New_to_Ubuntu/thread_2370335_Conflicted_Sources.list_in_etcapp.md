---
title: "Conflicted Sources.list in /etc/app"
date: 2017-09-02
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2017-09-02
Hey everyone,


I dont know whats happening when I try to run sudo apt-get update

It says at the end of the update those files could be potentially dangerous.

And then I googled and got new sources.list which i added at EOF. 

now it shows me this..


```

: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target Translations (partner/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: The repository 'https://download.01.org/gfx/ubuntu/16.04/main xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/main/binary-amd64/Packages  503  Service Unavailable
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target Translations (partner/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:66



```


I don't like to have the conflicted and manual one for updating updates

 can anyone give me the new sources.list as it comes like default in ubuntu 16.04 LTS

---

### Post by johnerin22 on 2017-09-02
just add this on /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
```

---

### Post by deadflowr on 2017-09-02
Post back the out for the /etc/apt/sources.list file.
The duplicate entries are all in one file.
(It seems to be telling you the lines 46 and 66 in the file are the same)

You also need to remove the 01.org repo.
Open Software and Updates and go to Other Software and locate the 01.org, or Intel repo and uncheck it or highlight it and selct remove (or delete)
There is no repo for xenial for the Intel Driver version you would be trying to use, currently; there might have been, but not anymore.

---

### Post by Yellow Pasque on 2017-09-03
> can anyone give me the new sources.list as it comes like default in ubuntu 16.04 LTS 

[http://www.configserverfirewall.com/ubuntu-linux/etc-apt-sources-list-ubuntu-16-xenial/](http://www.configserverfirewall.com/ubuntu-linux/etc-apt-sources-list-ubuntu-16-xenial/)

---

