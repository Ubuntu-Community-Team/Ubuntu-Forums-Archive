---
title: "File sharing in Ubuntu for a Windows 7 machine"
date: 2015-04-15
forum: New to Ubuntu
---

### Post by fangorn2 on 2015-04-15
Hi,

I have Ubuntu 14.04 LTS. Samba is installed by default.
I am able to see my Ubuntu machine from my Windows 7 machine and vice-versa. I also able to access to the files and folders that Windows share by default.
I would like to know how to share files and folders in Ubuntu in order to make them accessible from my Windows 7 machine. I found these following guides:

[http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7](http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7)
[http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/](http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/)

The point is that if I right click on any file or folder in my Ubuntu machine there is not any 'Sharing options' in the contextual menu, and if I chose 'Properties' no 'share' tabs appear. Are these choices obsolete for security reasons? Am I perhaps supposed to edit the smb.conf file somewhere in order to make these options available?

Many thanks in advance for your help

---

### Post by yancek on 2015-04-15
The links you posted are for earlier versions of Ubuntu.  The official Ubuntu docs for Samba are at the link below, a lot of reading.  I've only set it up once so can't be of any more help.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by bab1 on 2015-04-15
> **fangorn2 said:**
> Hi,

I have Ubuntu 14.04 LTS. Samba is installed by default.

Only the Samba client is installed by default.

I'm surprised that you don't have the ability to  "right click" and setup user shares.  You should be able to highlight the folder and  *right click >> properties* then you select the *local network share*.

You can see what Samba and CIFS packages you have install with these 2 commands```
dpkg -l samba* | grep ^ii

dpkg -l cifs
```
Here is what I get from the 2 commands```

 dpkg -l samba*|g ^ii
ii  samba                                                 2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        SMB/CIFS file, print, and login server for Unix
ii  samba-common                                          2:4.1.6+dfsg-1ubuntu2.14.04.7                       all          common files used by both the Samba server and client
ii  samba-common-bin                                      2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba common files used by both the server and the client
ii  samba-dsdb-modules                                    2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba Directory Services Database
ii  samba-libs:amd64                                      2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba core libraries
ii  samba-vfs-modules                                     2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba Virtual FileSystem plugins

```
...and ```
 dpkg -l cifs*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version       Architecture  Description
+++-=================-=============-=============-========================================
ii  cifs-utils        2:6.0-1ubuntu amd64         Common Internet File System utilities
bruce@maui:~$ 

```
> 
The point is that if I right click on any file or folder in my Ubuntu machine there is not any 'Sharing options' in the contextual menu, and if I chose 'Properties' no 'share' tabs appear. Are these choices obsolete for security reasons? Am I perhaps supposed to edit the smb.conf file somewhere in order to make these options available?

Many thanks in advance for your help
I would just install what you need and go from there.  You can install all the Samba packages with these commands (for Samba)```
sudo apt-get install samba
```
...(for CIFS)```
sudo apt-get install cifs-utils
```

Reboot the machine and then try to share a folder.  Let us know what happens.

---

