---
title: "Can't uninstall Tor Browser after installing it with Ubuntu Software"
date: 2021-01-13
forum: New to Ubuntu
---

### Post by lelolelo on 2021-01-13
When I try to uninstall Tor Browser I get a message saying 

[I]Unable to remove "Tor Browser":
The following packages have unmet dependencies:[/I]

Now I don't know what I should do to uninstall it.

---

### Post by ActionParsnip on 2021-01-13
How did you install it?
What steps did you take? 
Which release of Ubuntu?

---

### Post by lelolelo on 2021-01-13
> **ActionParsnip said:**
> How did you install it?
What steps did you take? 
Which release of Ubuntu?



I installed it with Ubuntu Software, I just searched for Tor Browser and clicked Install. Version is Ubuntu 20.04 LTS.

---

### Post by mIk3_08 on 2021-01-13
Go to Ubuntu Software again and select installed apps then click Remove button to the said TOR you installed.

---

### Post by ActionParsnip on 2021-01-13
what is the output of:
```

dpkg -l | grep -i tor | grep -i brow

```
Thanks

---

### Post by lelolelo on 2021-01-13
> **mIk3_08 said:**
> Go to Ubuntu Software again and select installed  apps then click Remove button to the said TOR you installed.
This was the first thing I tried and that's how I got this error message.

> **ActionParsnip said:**
> what is the output of:
```

dpkg -l | grep -i tor | grep -i brow

```
Thanks

The output:
```
ii  torbrowser-launcher                        0.3.2-9ubuntu1                      amd64        helps download and run the Tor Browser Bundle
```

---

### Post by Impavidus on 2021-01-14
Something about your package management is messed up and you package manager refuses to do anything until you tell it how to fix it. So, let's find out what exactly is going on:```
sudo apt update
sudo apt install -f
```Can you post the full output of those commands?

---

### Post by lelolelo on 2021-01-14
> **Impavidus said:**
> Something about your package management is messed up and you package manager refuses to do anything until you tell it how to fix it. So, let's find out what exactly is going on:```
sudo apt update
sudo apt install -f
```Can you post the full output of those commands?

sudo apt update output:

```
Hit:1 http://br.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://br.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]                                                       
Get:3 http://br.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]                                                     
Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [109 kB]                                                        
Hit:5 http://ppa.launchpad.net/papirus/papirus/ubuntu focal InRelease                                                            
Ign:6 http://br.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages                                                       
Ign:7 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages                                  
Ign:8 http://br.archive.ubuntu.com/ubuntu focal-updates/main Translation-en                                  
Ign:9 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata                           
Ign:10 http://br.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages                           
Ign:11 http://br.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en                           
Ign:12 http://br.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata                                          
Ign:13 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata                                        
Get:6 http://br.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [406 kB]                                              
Get:7 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [760 kB]                         
Get:8 http://br.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [186 kB]                           
Err:8 http://br.archive.ubuntu.com/ubuntu focal-updates/main Translation-en                           
  File has unexpected size (185340 != 186456). Mirror sync in progress? [IP: 2801:82:80ff:8000::5 80]
  Hashes of expected file:
   - Filesize:186456 [weak]
   - SHA256:3d61ceb986298990cda64e675d1c62b28c097446d83d5c0e5b16a690fcc046ff
   - SHA1:babcbd3e623461c201e776092cda94c2091648dc [weak]
   - MD5Sum:4853b43f8f0c9eadd16764c21e9fa05c [weak]
  Release file created at: Thu, 14 Jan 2021 12:21:23 +0000
Hit:14 https://updates.signal.org/desktop/apt xenial InRelease                                                                   
Get:9 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [264 kB]
Err:9 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata
  
Get:15 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [24.3 kB]
Get:10 http://br.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [130 kB]       
Get:11 http://br.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [18.9 kB]
Err:11 http://br.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en
  
Get:16 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [56.6 kB]
Get:12 http://br.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [281 kB]
Err:12 http://br.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata
  
Get:13 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Err:13 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata
  
Ign:17 http://br.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata
Get:17 http://br.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [1,768 B]
Err:17 http://br.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:1768 [weak]
   - SHA256:2e736336dad0b6511a49b765b5398695b9bda8a6e55728411fc36c6ac0e6b2bb
   - SHA1:6e88e94a85ae058162ce6f56707641b87aec6a3e [weak]
   - MD5Sum:e06d8dc3828bcca1dc2075d039b55c38 [weak]
  Hashes of received file:
   - SHA256:2125dafc9fa79f103ceaf0a71579dff70ba67db16a65e54c721397e9f207add2
   - SHA1:c3a117f055d181f1c4c1de459cf6e15b2879a343 [weak]
   - MD5Sum:0a1833fdaef4a08a0d3d13db9624f943 [weak]
   - Filesize:1768 [weak]
  Last modification reported: Thu, 14 Jan 2021 08:18:12 +0000
  Release file created at: Thu, 14 Jan 2021 12:21:58 +0000
Fetched 1,705 kB in 2s (1,060 kB/s)           
Reading package lists... Done
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/main/i18n/Translation-en.xz  File has unexpected size (185340 != 186456). Mirror sync in progress? [IP: 2801:82:80ff:8000::5 80]
   Hashes of expected file:
    - Filesize:186456 [weak]
    - SHA256:3d61ceb986298990cda64e675d1c62b28c097446d83d5c0e5b16a690fcc046ff
    - SHA1:babcbd3e623461c201e776092cda94c2091648dc [weak]
    - MD5Sum:4853b43f8f0c9eadd16764c21e9fa05c [weak]
   Release file created at: Thu, 14 Jan 2021 12:21:23 +0000
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/main/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/restricted/i18n/Translation-en.xz  
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/universe/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/multiverse/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-backports/universe/dep11/Components-amd64.yml.xz  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:1768 [weak]
    - SHA256:2e736336dad0b6511a49b765b5398695b9bda8a6e55728411fc36c6ac0e6b2bb
    - SHA1:6e88e94a85ae058162ce6f56707641b87aec6a3e [weak]
    - MD5Sum:e06d8dc3828bcca1dc2075d039b55c38 [weak]
   Hashes of received file:
    - SHA256:2125dafc9fa79f103ceaf0a71579dff70ba67db16a65e54c721397e9f207add2
    - SHA1:c3a117f055d181f1c4c1de459cf6e15b2879a343 [weak]
    - MD5Sum:0a1833fdaef4a08a0d3d13db9624f943 [weak]
    - Filesize:1768 [weak]
   Last modification reported: Thu, 14 Jan 2021 08:18:12 +0000
   Release file created at: Thu, 14 Jan 2021 12:21:58 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

sudo apt install -f output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java default-jre-headless fastjar guile-2.2-libs jarwrapper java-common libegl-dev libgc1c2 libgl-dev
  libglu1-mesa libglu1-mesa-dev libglx-dev libllvm10 libllvm10:i386 libpthread-stubs0-dev libqt5concurrent5 libqt5multimedia5
  libqt5multimediawidgets5 libqt5opengl5 libqt5opengl5-dev libvulkan-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxdo3
  libxext-dev libxxf86dga1 openjdk-11-jre-headless qt5-default qt5-qmake qt5-qmake-bin qtbase5-dev qtbase5-dev-tools qtchooser
  x11-apps x11-session-utils x11proto-core-dev x11proto-dev x11proto-xext-dev xbitmaps xinit xorg-sgml-doctools xtrans-dev
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by mIk3_08 on 2021-01-14
Try to use Synaptic Package Manager if you have one to remove the apps, or type ```
apt list
``` in terminal and show us the result here wrap with code.

---

### Post by Impavidus on 2021-01-14
There's some unexpected output from sudo apt update, but, as the tools itself notes, this may be caused by a mirror sync in progress. Trying again may fix it, unless there really is a problem with that server.

The output from sudo apt install -f shows no errors. Is the problem still there?

---

### Post by lelolelo on 2021-01-14
> **mIk3_08 said:**
> Try to use Synaptic Package Manager if you have one to remove the apps, or type ```
apt list
``` in terminal and show us the result here wrap with code.

It shows torbrowser-launcher in there, that's the only relevant thing I could see. Should I sudo apt remove it?

> **Impavidus said:**
> There's some unexpected output from sudo apt  update, but, as the tools itself notes, this may be caused by a mirror  sync in progress. Trying again may fix it, unless there really is a  problem with that server.

The output from sudo apt install -f shows no errors. Is the problem still there?

Still didn't work.

---

### Post by mIk3_08 on 2021-01-15
> **lelolelo said:**
> It shows torbrowser-launcher in there, that's the only relevant thing I could see. Should I sudo apt remove it?

Okay If you might want to remove it coz you might not need it anymore, then go. remove it via terminal command.

---

