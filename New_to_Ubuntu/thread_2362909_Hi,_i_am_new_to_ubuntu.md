---
title: "Hi, i am new to ubuntu"
date: 2017-06-03
forum: New to Ubuntu
---

### Post by ahmad-nahali on 2017-06-03
I just installed Ubuntu 16.04  and i tried to install wine or any other application and it would halfway download and stop, when I download something of the browser it work.(btw im using a hp probook)

---

### Post by Frogs Hair on 2017-06-03
Hello and Welcome

Open software & Updates and enable the Canonacal partners repository under other software.

---

### Post by ahmad-nahali on 2017-06-03
[IMG]https://ibb.co/mZ4sTF[/IMG] I did this and it still dont work

---

### Post by LastDino on 2017-06-03
See this guide here for details

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


Then try to run

```
sudo apt-get update && sudo apt-get upgrade
```

In your terminal window


After you follow through the instructions and update your system, try installing wine again

---

### Post by QIII on 2017-06-03
Hello!

To give us some diagnostic information, would you please issue the following command in a terminal and post back the results:

```
sudo apt install winetricks
```

---

### Post by ahmad-nahali on 2017-06-03
```
Ign:1 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial InRelease
Ign:2 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial Release
Ign:3 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 Packages
Ign:4 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main i386 Packages
Ign:5 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main all Packages
Ign:6 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en_US
Ign:7 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main Translation-en
Ign:8 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted i386 Packages
Ign:12 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted all Packages
Ign:13 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted Translation-en
Ign:15 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/restricted DEP-11 64x64 Icons
Err:3 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:4 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial/main i386 Packages
Hit:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease            
Hit:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease          
Hit:20 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                    
Hit:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease             
Hit:22 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial InRelease  
Reading package lists... Done                      
W: The repository 'cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)/dists/xenial/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
```
that is what i get when i try 
sudo apt-get update && sudo apt-get upgrade

---

### Post by LastDino on 2017-06-03
Open **Software & Updates** and in the **Ubuntu Software** tab uncheck **Cdrom with Ubuntu 16.04 LTS 'Xenial Xerus'** under the section **Installable from CD-ROM/DVD**.

---

### Post by ahmad-nahali on 2017-06-03
> **LastDino said:**
> Open **Software & Updates** and in the **Ubuntu Software** tab uncheck **Cdrom with Ubuntu 16.04 LTS 'Xenial Xerus'** under the section **Installable from CD-ROM/DVD**.

I dont see it all i see i revert and close
edit:nvm found it :)

---

### Post by LastDino on 2017-06-03
Don't forget to run the update and upgrade command again and then try to install wine from terminal and post output if problem is still there

---

### Post by ahmad-nahali on 2017-06-03
> **QIII said:**
> Hello!

To give us some diagnostic information, would you please issue the following command in a terminal and post back the results:

```
sudo apt install winetricks
```   how do i get past this part?
edit: nvm found it

[ATTACH=CONFIG]275450[/ATTACH]

---

### Post by LastDino on 2017-06-03
Press "Tab" and then click enter when focus is on "ok"

---

