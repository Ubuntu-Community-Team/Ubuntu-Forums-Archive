---
title: "Trying to download snaps via Ubuntu linux... FAIL."
date: 2018-07-30
forum: New to Ubuntu
---

### Post by tylerhelton on 2018-07-30
I'm not neeew to ubuntu, but I do not know much of anything about it. It's been a struggle..

So I would like to get Anbox, the android sort-of-emulator-but-better, and I need snaps to download it. 

I downloaded snaps and it is telling me I cannot connect to server when I try installing Anbox with the command that is posted on their website. 

Here is the terminal info.. note, this data log has everything from me first installing snaps, to enabling it, to attempting to download anbox and being told I cannot connect to server. (i couldn't log onto these forums via ubuntu browser and I wouldn't download firefox because I'm worried this is a memory issue, so I emailed myself the log and copied it from my email after I exited ubuntu and posted it on the forums, so that's why it's colored and such...)

also I should mention that after this happened the first time, I powerwashed my chromebook, reinstalled ubuntu, and this is the log of my second attempt. 

```
(xenial)tyler@localhost:~$ sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]
Fetched 216 kB in 1s (122 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
(xenial)tyler@localhost:~$ sudo apt install snapd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  apparmor libapparmor-perl liblzo2-2 openssh-client squashfs-tools
Suggested packages:
  apparmor-profiles apparmor-profiles-extra apparmor-docs apparmor-utils
  ssh-askpass libpam-ssh keychain monkeysphere zenity | kdialog
The following NEW packages will be installed:
  apparmor libapparmor-perl liblzo2-2 openssh-client snapd squashfs-tools
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.4 MB of archives.
After this operation, 87.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 liblzo2-2
amd64 2.08-1.2 [48.7 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64
libapparmor-perl amd64 2.10.95-0ubuntu2.9 [31.5 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64
apparmor amd64 2.10.95-0ubuntu2.9 [450 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64
openssh-client amd64 1:7.2p2-4ubuntu2.4 [589 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64
squashfs-tools amd64 1:4.3-3ubuntu2.16.04.2 [105 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 snapd
amd64 2.34.2 [14.2 MB]
Fetched 15.4 MB in 4s (3336 kB/s)
Preconfiguring packages ...
Selecting previously unselected package liblzo2-2:amd64.
(Reading database ... 69901 files and directories currently installed.)
Preparing to unpack .../liblzo2-2_2.08-1.2_amd64.deb ...
Unpacking liblzo2-2:amd64 (2.08-1.2) ...
Selecting previously unselected package libapparmor-perl.
Preparing to unpack .../libapparmor-perl_2.10.95-0ubuntu2.9_amd64.deb ...
Unpacking libapparmor-perl (2.10.95-0ubuntu2.9) ...
Selecting previously unselected package apparmor.
Preparing to unpack .../apparmor_2.10.95-0ubuntu2.9_amd64.deb ...
Unpacking apparmor (2.10.95-0ubuntu2.9) ...
Selecting previously unselected package openssh-client.
Preparing to unpack .../openssh-client_1%3a7.2p2-4ubuntu2.4_amd64.deb ...
Unpacking openssh-client (1:7.2p2-4ubuntu2.4) ...
Selecting previously unselected package squashfs-tools.
Preparing to unpack .../squashfs-tools_1%3a4.3-3ubuntu2.16.04.2_amd64.deb ...
Unpacking squashfs-tools (1:4.3-3ubuntu2.16.04.2) ...
Selecting previously unselected package snapd.
Preparing to unpack .../snapd_2.34.2_amd64.deb ...
Unpacking snapd (2.34.2) ...
Processing triggers for systemd (229-4ubuntu21.2) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up liblzo2-2:amd64 (2.08-1.2) ...
Setting up libapparmor-perl (2.10.95-0ubuntu2.9) ...
Setting up apparmor (2.10.95-0ubuntu2.9) ...
update-rc.d: warning: start and stop actions are no longer supported;
falling back to defaults
diff: /var/lib/apparmor/profiles/.apparmor.md5sums: No such file or directory
Setting up openssh-client (1:7.2p2-4ubuntu2.4) ...
Setting up squashfs-tools (1:4.3-3ubuntu2.16.04.2) ...
Setting up snapd (2.34.2) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for systemd (229-4ubuntu21.2) ...
Processing triggers for ureadahead (0.100.0-19) ...
(xenial)tyler@localhost:~$ sudo systemctl enable snapd.socket
(xenial)tyler@localhost:~$ sudo snap install --classic anbox-installer
&& anbox-installer
error: cannot communicate with server: Post
[http://localhost/v2/snaps/anbox-installer](http://localhost/v2/snaps/anbox-installer): dial unix
/run/snapd.socket: connect: no such file or directory
(xenial)tyler@localhost:~$ 
```

---

### Post by QIII on 2018-08-01
Bump

---

### Post by howefield on 2018-08-01
Does this page help ?

[https://github.com/anbox/anbox/blob/master/docs/install.md](https://github.com/anbox/anbox/blob/master/docs/install.md)

---

### Post by tylerhelton on 2018-08-01
yes thank you very much.

---

