---
title: "Teamspeak server"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Tsu on 2008-10-16
Hi everyone, having the following problems.

Current setup -

Ubuntu 8.04 LTS Server Edition OS has been installed with LAMP services.

I wish to install Teamspeak2 server onto ubuntu. I first tried to follow the instructions shown in this link "https://help.ubuntu.com/community/TeamSpeak"

When I type in "sudo ./setup.sh"

I get the following error

"./setup.sh: line 19: ./setup.data/installer/installer: No such file or directory"

I could not work out what the error ment so I tried the get-apt route.

I ran the following command -

"sudo apt-get install teamspeak-client"

The following output appeared.

"Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libasound2 lib
Suggested packages:
  libasound2-plugins
Recommended packages:
  lib32nss-mdns
The following NEW packages will be installed
  ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libasound2 lib
  teamspeak-client
0 upgraded, 9 newly installed, 0 to remove and 4 not upgraded.
Need to get 33.3MB of archives.
After this operation, 130MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main libasound2 1.0.15-3ubuntu4 [400kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main libc6-i386 2.7-10ubuntu4 [369
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main lib32asound2 1.0.15-3ubuntu4 [317kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main lib32gcc1 1:4.2.3-2ubuntu7 [23.3kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main lib32ncurses5 5.6+20071124-1ubuntu2 [
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main lib32stdc++6 4.2.3-2ubuntu7 [332kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main lib32z1 1:1.2.3.3.dfsg-7ubuntu1 [74.3
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe ia32-libs 2.2ubuntu11 [20
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse teamspeak-client 2.0.32-2 [7372
Fetched 33.3MB in 2min43s (203kB/s)
Selecting previously deselected package libasound2.
(Reading database ... 19123 files and directories currently installed.)
Unpacking libasound2 (from .../libasound2_1.0.15-3ubuntu4_amd64.deb) ...
Selecting previously deselected package libc6-i386.
Unpacking libc6-i386 (from .../libc6-i386_2.7-10ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32asound2.
Unpacking lib32asound2 (from .../lib32asound2_1.0.15-3ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package lib32ncurses5.
Unpacking lib32ncurses5 (from .../lib32ncurses5_5.6+20071124-1ubuntu2_amd64.deb) ...
Selecting previously deselected package lib32stdc++6.
Unpacking lib32stdc++6 (from .../lib32stdc++6_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package lib32z1.
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3.3.dfsg-7ubuntu1_amd64.deb) ...
Selecting previously deselected package ia32-libs.
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu11_amd64.deb) ...
Selecting previously deselected package teamspeak-client.
Unpacking teamspeak-client (from .../teamspeak-client_2.0.32-2_amd64.deb) ...
Setting up libasound2 (1.0.15-3ubuntu4) ...
You may need to execute the asoundconf(1) set-default-card macro.

Setting up libc6-i386 (2.7-10ubuntu4) ...

Setting up lib32asound2 (1.0.15-3ubuntu4) ...

Setting up lib32gcc1 (1:4.2.3-2ubuntu7) ...

Setting up lib32ncurses5 (5.6+20071124-1ubuntu2) ...

Setting up lib32stdc++6 (4.2.3-2ubuntu7) ...

Setting up lib32z1 (1:1.2.3.3.dfsg-7ubuntu1) ...

Setting up ia32-libs (2.2ubuntu11) ...

Setting up teamspeak-client (2.0.32-2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place"

I was hoping someone could instruct me on how to install team speak in both methods and point out where I am going wrong.

Thank for your time.

---

### Post by NullHead on 2008-10-16
I just downloaded the pre-packaged server files off of [their website](http://www.goteamspeak.com/?page=downloads). The client isn't needed for running the server. To access the configuration of the server after you've started it, put the ipaddress:14534 into firefox. The superadmin password will be in server.log

---

### Post by Tsu on 2008-10-16
Sorry, just noticed that I had installed the client and not the server via the get apt method.


Performing the following command

"sudo apt-get install teamspeak-server"

I have the following output

"Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  teamspeak-server
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 1094kB of archives.
After this operation, 2998kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse teamspeak-server 2.0.23.19-1 [1                            094kB]
Fetched 1094kB in 6s (176kB/s)
Selecting previously deselected package teamspeak-server.
(Reading database ... 20647 files and directories currently installed.)
Unpacking teamspeak-server (from .../teamspeak-server_2.0.23.19-1_amd64.deb) ...
Setting up teamspeak-server (2.0.23.19-1) ...
Adding system user/group teamspeak-server."

Team speak server is working.

I also want to port over all the sqlite files to this server. So that the previous members don't have to reregister.

I found the main log in /var/log/teamspeak-server.log

---

### Post by hyper_ch on 2008-10-16
logfiles are normally in /var/log

to search for certain files run
```

sudo updatedb

```
--> to re-index the files

and then
```

locate FILENAME

```

---

### Post by Tsu on 2008-10-16
I love you all. using locate on the super admin html page.

superadmin_manager.html

I was able to locate the root folder to "/usr/share/teamspeak-server/"

All I need assistance with now is why when I type in "sudo ./setup.sh"

I get the following error

"./setup.sh: line 19: ./setup.data/installer/installer: No such file or directory"

---

