---
title: "Can't access Software Sources 8.10"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by DanielSimpson on 2008-11-10
Hi, since updating to 8.10 I've been unable to open software sources, from System>Admin>Software Sources.

I believe, though I'm not certain, i need to go to there to enable third party drivers, to get my nvidia drivers, to allow me to run certain desktop effects, as well as to change my screen reso to 1280/1024.

I tried to access through the terminal using,

```
gksu /usr/bin/software-properties-gtk
```

This gives, 

```
daniel@danputer:~$ gksu /usr/bin/software-properties-gtk
Traceback (most recent call last):
t/__init__.py:18: FutureWarning: apt API not stable yet
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException
daniel@danputer:~$ 

```

If anyone could help, I'd appreciate it. 
Thanks.

---

### Post by philinux on 2008-11-10
Wow this is the launcher on my system, never imagined it needed that lot. :lolflag:

```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

---

### Post by DanielSimpson on 2008-11-10
Sorry, i don't understand. I put that line through Terminal, and got an error again. 
Thanks for the reply though.

---

### Post by Elfy on 2008-11-10
> **philinux said:**
> Wow this is the launcher on my system, never imagined it needed that lot. :lolflag:

```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

Neither did I :)


DanielSimpson - it should work without the path - does it give the same error

```
gksu software-properties-gtk
```

If it still cause an error, which it probably will,  we can deal with the sources the other way, run this and post the output

```
cat /etc/apt/sources.list
```

---

### Post by DanielSimpson on 2008-11-10
```
gksu software-properties-gtk
```
This gives the same error. 
```
daniel@danputer:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
daniel@danputer:~$ 

```

Thanks.

---

### Post by DanielSimpson on 2008-11-10
Bump?

---

### Post by Elfy on 2008-11-10
I look slike they are all enabled - from a terminal

```
sudo apt-get update &&sudo apt-get upgrade
```

Once that's done - restart if required - if not open Hardware Drivers in System Admin menu - your nvidia should be in there - enable that and it should install it for you.

---

### Post by DanielSimpson on 2008-11-10
Right ok, i did the upgrade, then went to Hardware Drivers. Clicked 'enable' then nothing seemed to happen. It didn't change to green, just stayed red.

---

### Post by Elfy on 2008-11-10
what card is it?

---

### Post by DanielSimpson on 2008-11-10
It's a MSI nVidia GeForce NX8600Gt.

---

### Post by DanielSimpson on 2008-11-10
bump? anyone?

---

### Post by Elfy on 2008-11-11
You could try to reinstall software-properties-gtk

```
sudo apt-get update &&sudo apt-get remove --purge software-properties-gtk &&sudo apt-get install software-properties-gtk
```

> Right ok, i did the upgrade, then went to Hardware Drivers. Clicked 'enable' then nothing seemed to happen. It didn't change to green, just stayed red. Did it appear to download the driver?

---

### Post by DanielSimpson on 2008-11-11
I recieved another error when entering that. 

When i chose enable, it pauses for a second or two, then just remains in the 'red' state.
Nonetheless, thanks for your help.

---

### Post by Elfy on 2008-11-11
> I recieved another error when entering that. Up to a point this is quite helpful - to make it really helpful could you post the error that you actually receive - run the commands singly

```
sudo apt-get update
sudo apt-get remove --purge software-properties-gtk
sudo apt-get install software-properties-gtk
```

If there is an error after the first command stop and post it before continuing.

---

### Post by DanielSimpson on 2008-11-12
When entering the first command, i get 
```
daniel@danputer:~$ sudo apt-get update
[sudo] password for daniel: 
Hit http://gb.archive.ubuntu.com intrepid Release.gpg
Get: 1 http://gb.archive.ubuntu.com intrepid/main Translation-en_GB [27.0kB]
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
Get: 2 http://packages.medibuntu.org intrepid Release.gpg [189B]               
Hit http://security.ubuntu.com intrepid-security Release                       
Get: 3 http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB [1135B]
Get: 4 http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB [8049B]
Get: 5 http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB [46.0kB]
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB 
Ign http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB 
Hit http://gb.archive.ubuntu.com intrepid Release                              
Ign http://packages.medibuntu.org intrepid/free Translation-en_GB              
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://gb.archive.ubuntu.com intrepid-updates Release                      
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Hit http://gb.archive.ubuntu.com intrepid/main Packages                        
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid/main Sources
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid/universe Packages
Hit http://gb.archive.ubuntu.com intrepid/universe Sources
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages                
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages          
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources                 
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources           
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources           
Get: 6 http://packages.medibuntu.org intrepid Release [11.7kB]                 
Ign http://packages.medibuntu.org intrepid Release       
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Fetched 82.3kB in 1s (74.3kB/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

---

### Post by DanielSimpson on 2008-11-12
When entering the first command, i get 
```
daniel@danputer:~$ sudo apt-get update
[sudo] password for daniel: 
Hit http://gb.archive.ubuntu.com intrepid Release.gpg
Get: 1 http://gb.archive.ubuntu.com intrepid/main Translation-en_GB [27.0kB]
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
Get: 2 http://packages.medibuntu.org intrepid Release.gpg [189B]               
Hit http://security.ubuntu.com intrepid-security Release                       
Get: 3 http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB [1135B]
Get: 4 http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB [8049B]
Get: 5 http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB [46.0kB]
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB 
Ign http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB 
Hit http://gb.archive.ubuntu.com intrepid Release                              
Ign http://packages.medibuntu.org intrepid/free Translation-en_GB              
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://gb.archive.ubuntu.com intrepid-updates Release                      
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Hit http://gb.archive.ubuntu.com intrepid/main Packages                        
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid/main Sources
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid/universe Packages
Hit http://gb.archive.ubuntu.com intrepid/universe Sources
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages                
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages          
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources                 
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources           
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources           
Get: 6 http://packages.medibuntu.org intrepid Release [11.7kB]                 
Ign http://packages.medibuntu.org intrepid Release       
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Fetched 82.3kB in 1s (74.3kB/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

---

### Post by Elfy on 2008-11-12
Run this command 

```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Once that has finished - run the other 2 commands from post #14

---

### Post by DanielSimpson on 2008-11-12
I ran that and it was fine: 
```
daniel@danputer:~$ sudo apt-get install medibuntu-keyring && sudo apt-get update
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxml++2.6c2a libcanberra-gnome python2.5-dev python-dev libx264-57
  libschroedinger-1.0-0 libkbluetooth0 gstreamer0.10-schroedinger
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 336 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y
Get: 1 http://packages.medibuntu.org intrepid/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 0s (6013B/s)           
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 225831 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Get: 1 http://gb.archive.ubuntu.com intrepid Release.gpg [189B]
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB
Hit http://security.ubuntu.com intrepid-security Release.gpg         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB 
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB
Get: 2 http://gb.archive.ubuntu.com intrepid Release [65.9kB]        
Get: 3 http://packages.medibuntu.org intrepid Release.gpg [189B]         
Hit http://security.ubuntu.com intrepid-security Release                       
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://gb.archive.ubuntu.com intrepid-updates Release                      
Ign http://packages.medibuntu.org intrepid/free Translation-en_GB              
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Get: 4 http://gb.archive.ubuntu.com intrepid/main Packages [1254kB]            
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_GB          
Get: 5 http://packages.medibuntu.org intrepid Release [11.7kB]                 
Hit http://packages.medibuntu.org intrepid/free Packages                       
Hit http://packages.medibuntu.org intrepid/non-free Packages
Get: 6 http://gb.archive.ubuntu.com intrepid/restricted Packages [8420B]
Get: 7 http://gb.archive.ubuntu.com intrepid/main Sources [505kB]
Get: 8 http://gb.archive.ubuntu.com intrepid/restricted Sources [3113B]        
Get: 9 http://gb.archive.ubuntu.com intrepid/universe Packages [4516kB]        
Get: 10 http://gb.archive.ubuntu.com intrepid/universe Sources [1981kB]        
Get: 11 http://gb.archive.ubuntu.com intrepid/multiverse Packages [192kB]      
Get: 12 http://gb.archive.ubuntu.com intrepid/multiverse Sources [95.8kB]      
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages                
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages          
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources                 
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources           
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources           
Fetched 8621kB in 36s (236kB/s)                                                
Reading package lists... Done

```

But when i go and run 
```
sudo apt-get remove --purge software-properties-gtk
```
i get 
```
daniel@danputer:~$ sudo apt-get remove --purge software-properties-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxml++2.6c2a libcanberra-gnome python2.5-dev python-dev libx264-57
  libschroedinger-1.0-0 libkbluetooth0 gstreamer0.10-schroedinger
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  software-properties-gtk*
0 upgraded, 0 newly installed, 1 to remove and 336 not upgraded.
After this operation, 397kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 225834 files and directories currently installed.)
Removing software-properties-gtk ...
Unknown media type in type 'chemical/x-alchemy'

Unknown media type in type 'chemical/x-cache'

Unknown media type in type 'chemical/x-cactvs-ascii'

Unknown media type in type 'chemical/x-cactvs-binary'

Unknown media type in type 'chemical/x-cactvs-table'

Unknown media type in type 'chemical/x-cdx'

Unknown media type in type 'chemical/x-cdxml'

Unknown media type in type 'chemical/x-chem3d'

Unknown media type in type 'chemical/x-cif'

Unknown media type in type 'chemical/x-cml'

Unknown media type in type 'chemical/x-daylight-smiles'

Unknown media type in type 'chemical/x-dmol'

Unknown media type in type 'chemical/x-gamess-input'

Unknown media type in type 'chemical/x-gamess-output'

Unknown media type in type 'chemical/x-gaussian-input'

Unknown media type in type 'chemical/x-gaussian-log'

Unknown media type in type 'chemical/x-genbank'

Unknown media type in type 'chemical/x-gulp'

Unknown media type in type 'chemical/x-hin'

Unknown media type in type 'chemical/x-inchi'

Unknown media type in type 'chemical/x-inchi-xml'

Unknown media type in type 'chemical/x-jcamp-dx'

Unknown media type in type 'chemical/x-macromodel-input'

Unknown media type in type 'chemical/x-mdl-molfile'

Unknown media type in type 'chemical/x-mdl-rdfile'

Unknown media type in type 'chemical/x-mdl-rxnfile'

Unknown media type in type 'chemical/x-mdl-sdfile'

Unknown media type in type 'chemical/x-mdl-tgf'

Unknown media type in type 'chemical/x-mmcif'

Unknown media type in type 'chemical/x-mol2'

Unknown media type in type 'chemical/x-mopac-graph'

Unknown media type in type 'chemical/x-mopac-input'

Unknown media type in type 'chemical/x-mopac-out'

Unknown media type in type 'chemical/x-msi-car'

Unknown media type in type 'chemical/x-msi-hessian'

Unknown media type in type 'chemical/x-msi-mdf'

Unknown media type in type 'chemical/x-msi-msi'

Unknown media type in type 'chemical/x-ncbi-asn1'

Unknown media type in type 'chemical/x-ncbi-asn1-binary'

Unknown media type in type 'chemical/x-ncbi-asn1-xml'

Unknown media type in type 'chemical/x-pdb'

Unknown media type in type 'chemical/x-shelx'

Unknown media type in type 'chemical/x-vmd'

Unknown media type in type 'chemical/x-xyz'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Purging configuration files for software-properties-gtk ...
Unknown media type in type 'chemical/x-alchemy'

Unknown media type in type 'chemical/x-cache'

Unknown media type in type 'chemical/x-cactvs-ascii'

Unknown media type in type 'chemical/x-cactvs-binary'

Unknown media type in type 'chemical/x-cactvs-table'

Unknown media type in type 'chemical/x-cdx'

Unknown media type in type 'chemical/x-cdxml'

Unknown media type in type 'chemical/x-chem3d'

Unknown media type in type 'chemical/x-cif'

Unknown media type in type 'chemical/x-cml'

Unknown media type in type 'chemical/x-daylight-smiles'

Unknown media type in type 'chemical/x-dmol'

Unknown media type in type 'chemical/x-gamess-input'

Unknown media type in type 'chemical/x-gamess-output'

Unknown media type in type 'chemical/x-gaussian-input'

Unknown media type in type 'chemical/x-gaussian-log'

Unknown media type in type 'chemical/x-genbank'

Unknown media type in type 'chemical/x-gulp'

Unknown media type in type 'chemical/x-hin'

Unknown media type in type 'chemical/x-inchi'

Unknown media type in type 'chemical/x-inchi-xml'

Unknown media type in type 'chemical/x-jcamp-dx'

Unknown media type in type 'chemical/x-macromodel-input'

Unknown media type in type 'chemical/x-mdl-molfile'

Unknown media type in type 'chemical/x-mdl-rdfile'

Unknown media type in type 'chemical/x-mdl-rxnfile'

Unknown media type in type 'chemical/x-mdl-sdfile'

Unknown media type in type 'chemical/x-mdl-tgf'

Unknown media type in type 'chemical/x-mmcif'

Unknown media type in type 'chemical/x-mol2'

Unknown media type in type 'chemical/x-mopac-graph'

Unknown media type in type 'chemical/x-mopac-input'

Unknown media type in type 'chemical/x-mopac-out'

Unknown media type in type 'chemical/x-msi-car'

Unknown media type in type 'chemical/x-msi-hessian'

Unknown media type in type 'chemical/x-msi-mdf'

Unknown media type in type 'chemical/x-msi-msi'

Unknown media type in type 'chemical/x-ncbi-asn1'

Unknown media type in type 'chemical/x-ncbi-asn1-binary'

Unknown media type in type 'chemical/x-ncbi-asn1-xml'

Unknown media type in type 'chemical/x-pdb'

Unknown media type in type 'chemical/x-shelx'

Unknown media type in type 'chemical/x-vmd'

Unknown media type in type 'chemical/x-xyz'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

```

---

### Post by Elfy on 2008-11-12
There would have been an error message at the end - that's needed ;)

Also why does it say there are 336 upgrades - you said you'd done them a day ago?

There has been apparently an update to the package.

---

