---
title: "passport?"
date: 2015-08-01
forum: New to Ubuntu
---

### Post by mohamedm on 2015-08-01
i installed sachesi it open but doesnot connect to  my blackberry passport .can some one help me to make it connect to my phone? i installed wine and i tried to install links but faild .is there any way to install blackberry drivere or sync to make my phone connect to sachesi?

---

### Post by Vladlenin5000 on 2015-08-01
Hi and welcome.

Sachesi has native versions for all major OS families: Windows, MacOs and Linux: [https://github.com/xsacha/Sachesi/releases](https://github.com/xsacha/Sachesi/releases)
Why are you trying to use the Windows version (with Wine)? It won't work...

---

### Post by mohamedm on 2015-08-01
becouse i tried a native version it does not recognize my phne .i do not know why my be i should install addetional dependends or open sync or drivere?

thank u

---

### Post by Vladlenin5000 on 2015-08-01
> **mohamedm said:**
> becouse i tried a native version it does not recognize my phne .i do not know why my be i should install addetional dependends or open sync or drivere?

thank u

Possibly... Perhaps you should read the build instructions before anything else: [https://github.com/xsacha/Sachesi/wiki/Build-Instructions](https://github.com/xsacha/Sachesi/wiki/Build-Instructions)
If it doesn't work you should contact the developer. It's a third party tool/software after all.

---

### Post by mohamedm on 2015-08-01
yes and i did 


[LIST=1]
[*]In the same directory as Sachesi.pro: qmake && make -j4
[/LIST]
with many attempts  the result
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ qmake && make -j4
qmake: could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/qmake': No such file or directory
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ pro: qmake && make -j4
No command 'pro:' found, did you mean:
 Command 'proj' from package 'proj-bin' (universe)
 Command 'prof' from package 'profphd' (universe)
pro:: command not found
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ qmake && make -j4
qmake: could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/qmake': No such file or directory
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ 


how can i install bz2 or tar?

---

### Post by Vladlenin5000 on 2015-08-01
1. The instructions are for Ubuntu 14.04 and the installation script requires QMake (and its dependencies) which _must_ be installed before anything else. 
2. The software is provided as a tarball. In layman's terms this is just a container, similar to ZIP or RAR. You don't install those, you _extract_ them somewhere and use what's contained, never the container directly. You can extract simply by right-clicking and "extract here..." (or open it and extract wherever you like. 
Then, in the same directory (folder) where you extracted it, is where you should be before issuing the qmake commands.

---

### Post by sandyd on 2015-08-02
Try this
```

cd ~/Downloads
# Download latest release
wget http://github.com/$(curl -s https://github.com/xsacha/Sachesi/releases | grep "Linux.tar.bz2" | head -n 1 | sed -e 's/^.*"\///;s/".*//') -O Sachesi_latest.Linux.tar.bz2
# Extract it
tar xvf Sachesi_latest.Linux.tar.bz2
mkdir -p ~/bin
mv Sachesi ~/bin
# Install dependencies
sudo apt-get install libusb-1.0 libqt5quick5 libqt5widgets5

```

Tested in docker container, may have to run
```

sudo apt-get install curl
```
if curl is missing on your system

After you log off, Sachesi should simply run if you type "Sachesi" in terminal.
If you don't want to log off, run
```

~/bin/Sachesi
```

---

### Post by mohamedm on 2015-08-02
[COLOR=#000000]2. The software is provided as a tarball. In layman's terms this is just a container, similar to ZIP or RAR. You don't install those, you [/COLOR]_extract_[COLOR=#000000] them somewhere and use what's contained, never the container directly. You can extract simply by right-clicking and "extract here..." (or open it and extract wherever you like. [/COLOR]
[COLOR=#000000]Then, in the same directory (folder) where you extracted it, is where you should be before issuing the qmake commands.


fore this reason i asked u how to install bz2  there are many files inside



[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by mohamedm on 2015-08-02
[[COLOR=#C61919]sandyd[/COLOR]]("http://ubuntuforums.org/member.php?u=717412")[COLOR=#000000] 

[/COLOR][COLOR=#000000]cd ~/Downloads
# Download latest release
wget http://github.com/$(curl -s [https://github.com/xsacha/Sachesi/releases](https://github.com/xsacha/Sachesi/releases) | grep "Linux.tar.bz2" | head -n 1 | sed -e 's/^.*"\///;s/".*//') -O Sachesi_latest.Linux.tar.bz2
# Extract it
tar xvf Sachesi_latest.Linux.tar.bz2
mkdir -p ~/bin
mv Sachesi ~/bin
# Install dependencies
sudo apt-get install libusb-1.0 libqt5quick5 libqt5widgets5

wonderfull thank u verymuch i will try and tell u
[/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by mohamedm on 2015-08-02
```
mohamed@mohamed-LIFEBOOK-AH530:~$ cd ~/Downloads
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ tar xvf Sachesi2.0.2-Linux.tar.bz2
Sachesi
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ mkdir -p ~/bin
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ mv Sachesi ~/bin
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ Install dependencies
No command 'Install' found, did you mean:
 Command 'install' from package 'coreutils' (main)
Install: command not found
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ sudo apt-get install libusb-1.0 libqt5quick5 libqt5widgets5
[sudo] password for mohamed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libusb-1.0-0' for regex 'libusb-1.0'
Note, selecting 'libusb-1.0-0-dbg' for regex 'libusb-1.0'
Note, selecting 'libusb-1.0-0-dev' for regex 'libusb-1.0'
Note, selecting 'libusb-1.0-doc' for regex 'libusb-1.0'
libqt5quick5 is already the newest version.
libusb-1.0-0 is already the newest version.
libqt5widgets5 is already the newest version.
The following NEW packages will be installed:
  libusb-1.0-0-dbg libusb-1.0-0-dev libusb-1.0-doc
0 upgraded, 3 newly installed, 0 to remove and 5 not upgraded.
Need to get 246 kB of archives.
After this operation, 1,819 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) vivid/main libusb-1.0-0-dev amd64 2:1.0.19-1 [57.6 kB]
Get:2 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) vivid/main libusb-1.0-doc all 2:1.0.19-1 [115 kB]
Get:3 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) vivid/main libusb-1.0-0-dbg amd64 2:1.0.19-1 [73.2 kB]
Fetched 246 kB in 13s (18.6 kB/s)                                              
Selecting previously unselected package libusb-1.0-0-dev:amd64.
(Reading database ... 230504 files and directories currently installed.)
Preparing to unpack .../libusb-1.0-0-dev_2%3a1.0.19-1_amd64.deb ...
Unpacking libusb-1.0-0-dev:amd64 (2:1.0.19-1) ...
Selecting previously unselected package libusb-1.0-doc.
Preparing to unpack .../libusb-1.0-doc_2%3a1.0.19-1_all.deb ...
Unpacking libusb-1.0-doc (2:1.0.19-1) ...
Selecting previously unselected package libusb-1.0-0-dbg:amd64.
Preparing to unpack .../libusb-1.0-0-dbg_2%3a1.0.19-1_amd64.deb ...
Unpacking libusb-1.0-0-dbg:amd64 (2:1.0.19-1) ...
Processing triggers for doc-base (0.10.6) ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Setting up libusb-1.0-0-dev:amd64 (2:1.0.19-1) ...
Setting up libusb-1.0-doc (2:1.0.19-1) ...
Setting up libusb-1.0-0-dbg:amd64 (2:1.0.19-1) ...
W: Duplicate sources.list entry [http://download.mono-project.com/repo/debian/](http://download.mono-project.com/repo/debian/) wheezy-libjpeg62-compat/main amd64 Packages (/var/lib/apt/lists/download.mono-project.com_repo_debian_dists_wheezy-libjpeg62-compat_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://download.mono-project.com/repo/debian/](http://download.mono-project.com/repo/debian/) wheezy-libjpeg62-compat/main i386 Packages (/var/lib/apt/lists/download.mono-project.com_repo_debian_dists_wheezy-libjpeg62-compat_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ sudo apt-get install curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  curl
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 129 kB of archives.
After this operation, 339 kB of additional disk space will be used.
Get:1 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) vivid-updates/main curl amd64 7.38.0-3ubuntu2.2 [129 kB]
Fetched 129 kB in 2s (60.5 kB/s)
Selecting previously unselected package curl.
(Reading database ... 230596 files and directories currently installed.)
Preparing to unpack .../curl_7.38.0-3ubuntu2.2_amd64.deb ...
Unpacking curl (7.38.0-3ubuntu2.2) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up curl (7.38.0-3ubuntu2.2) ...
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ Sachesi
Sachesi: command not found
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ ~/bin/Sachesi
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$ ~/bin/Sachesi
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
"Communication Error: 1 (Connection refused) from 192.168.1.103" 
mohamed@mohamed-LIFEBOOK-AH530:~/Downloads$

```

---

### Post by sandyd on 2015-08-02
Is your phone connected?

Not sure about this part as it attempts to connect to the phone, and I've never used it.

---

