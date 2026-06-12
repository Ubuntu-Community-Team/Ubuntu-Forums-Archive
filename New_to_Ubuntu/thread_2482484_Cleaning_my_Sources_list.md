---
title: "Cleaning my Sources list"
date: 2023-01-01
forum: New to Ubuntu
---

### Post by karthik82 on 2023-01-01
Hi,

I am getting the below errors and need to clean my sources list. How do i do this please? I am using a Jetson ORIN with ARM 64 Architecture.

I need to remove the incorrect entries from **etc/apt/sources.list**
```
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-amd64/Packages' as repository 'https://repo.download.nvidia.com/jetson/common r35.1 InRelease' doesn't support architecture 'amd64'
N: Skipping acquire of configured file 'main/binary-amd64/Packages' as repository 'https://repo.download.nvidia.com/jetson/t234 r35.1 InRelease' doesn't support architecture 'amd64'
N: Skipping acquire of configured file 'main/binary-arm64/Packages' as repository 'http://deb.anydesk.com all InRelease' doesn't support architecture 'arm64'
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/focal/main/binary-amd64/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/focal/main/binary-amd64/Packages)  404  Not Found [IP: 185.125.190.39 80]
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/focal-updates/main/binary-amd64/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/focal-updates/main/binary-amd64/Packages)  404  Not Found [IP: 185.125.190.39 80]
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/focal-backports/main/binary-amd64/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/focal-backports/main/binary-amd64/Packages)  404  Not Found [IP: 185.125.190.39 80]
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/focal-security/main/binary-amd64/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/focal-security/main/binary-amd64/Packages)  404  Not Found [IP: 185.125.190.39 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
exiting installation script.
```
**The below is my sources list**
```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade
# newer versions of the distribution.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal main restricted
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-updates main restricted
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal universe
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-updates universe
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal multiverse
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-updates multiverse
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-backports main restricted universe multiverse
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-security main restricted
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-security main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-security universe
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-security universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-security multiverse
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) focal-security multiverse
```

---

### Post by deadflowr on 2023-01-01
It has nothing to do with your sources, which are perfectly fine.
It has to do with the apt package manager thinks you want packages for the amd64 architecture which those repositories listed do not have packages for.
It's also an incomplete list as you should have two other source .lists files most likely in /etc/apt/sources.list.d folder for an nvidia repository and an anydesk repository.
look at what
```
ls /etc/apt/sources.list.d
```
shows.

Anyway what do
```
dpkg --print-architecture
and
dpkg --print-foreign-architectures
```
show.

From a cursory look of things, anydesk does not provide any arm packages except for raspberry pi specifically. 
So that repository might need to be removed.

---

### Post by grahammechanical on 2023-01-02
To Add; Edit and Remove repositories without using the command line open Software and Updates utility and click on the Other Software tab.That will show you any non standard repositories and along side will be a check box.

The Ubuntu Software tab lists standard Ubuntu repositories.

Regards

---

### Post by karthik82 on 2023-01-02
Thanks. I ran 

$ ls /etc/apt/sources.list.d
anydesk-stable.list
anydesk-stable.list.save
appimagelauncher-team-ubuntu-stable-focal.list
nvidia-l4t-apt-source.list
nvidia-l4t-apt-source.list.save
ros-latest.list
ros-latest.list.save
teamviewer.list.dpkg-new
ubuntu-toolchain-r-ubuntu-test-focal.list
ubuntu-toolchain-r-ubuntu-test-focal.list.save


future@ubuntu:~$ dpkg --print-architecture
arm64
future@ubuntu:~$ dpkg --print-foreign-architectures
amd64

---

### Post by deadflowr on 2023-01-03
Run
```
sudo dpkg --remove-architecture amd64
sudo mv /etc/apt/sources.list.d/anydesk-stable.list /etc/apt/sources.list.d/anydesk-stable.list.old
sudo apt update
```

---

### Post by karthik82 on 2023-01-03
Thanks a lot ! That worked :eek:

---

### Post by ActionParsnip on 2023-01-04
Please mark as solved if all is well

---

### Post by mIk3_08 on 2023-01-05
> **karthik82 said:**
> Thanks a lot ! That worked :eek:

On how to mark this thread as solve,
Please Click the "[COLOR=#ff0000]**Solve thread**[/COLOR]" link below. Regards and cheers.

---

