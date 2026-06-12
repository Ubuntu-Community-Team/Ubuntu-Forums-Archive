---
title: "Update Manager Stuck"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by fidgaf on 2008-06-23
I get update requests every time I start up and always the same fail:

> GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

Failed to fetch [http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

It downloads about 58 files and fails on these and keeps trying to fetch them every time.

What do I need to do to get this to work right?

PS - My Updates show that they are 15 days out-of-date.

Thanks in advance.



Hardy Heron Ubuntu installed Ubuntu 8.04 LTS (Info from FF start-up - Is there a better place to find out what version I have?)

---

### Post by Zulu-Zeffir on 2008-06-23
What are the results of performing an apt-get update?
Try this then see if the update fails still.  Also, take note that this may occur during archive updates as well and maybe resolved by simply trying again a little later.

---

### Post by plucky on 2008-06-23
> GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://www.mirror.ac.uk/mirror/archi...86/Packages.gz](http://www.mirror.ac.uk/mirror/archi...86/Packages.gz) 404 Not Found

Failed to fetch [http://www.mirror.ac.uk/mirror/archi...86/Packages.gz](http://www.mirror.ac.uk/mirror/archi...86/Packages.gz) 404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead. 


Try changing your server System > Administration > Software Sources and select the **Main Server** and **Reload**.

Good Luck

---

### Post by fidgaf on 2008-06-23
> **Zulu-Zeffir said:**
> What are the results of performing an apt-get update?
Try this then see if the update fails still.  Also, take note that this may occur during archive updates as well and maybe resolved by simply trying again a little later.

Similar stuff:

```
XXXXX@ubuntu:~$ sudo apt-get update
Hit http://archive.ubuntu.com hardy Release.gpg
Hit http://archive.ubuntu.com hardy/main Translation-en_GB                     
Hit http://archive.ubuntu.com hardy/restricted Translation-en_GB               
Hit http://archive.ubuntu.com hardy/universe Translation-en_GB                 
Hit http://archive.ubuntu.com hardy/multiverse Translation-en_GB               
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_GB             
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_GB       
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_GB         
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_GB       
Hit http://archive.ubuntu.com hardy-security Release.gpg                       
Ign http://www.mirror.ac.uk hardy Release.gpg                                  
Ign http://www.mirror.ac.uk hardy/main Translation-en_GB             
Ign http://www.mirror.ac.uk hardy/universe Translation-en_GB
Ign http://archive.ubuntu.com hardy-security/main Translation-en_GB
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_GB
Get: 1 http://packages.medibuntu.org hardy Release.gpg [189B]
Ign http://packages.medibuntu.org hardy/free Translation-en_GB               
Ign http://www.mirror.ac.uk hardy Release                            
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://archive.ubuntu.com hardy Release    
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy-security Release
Ign http://www.mirror.ac.uk hardy/main Packages
Get: 2 http://packages.medibuntu.org hardy Release [9335B]          
Ign http://www.mirror.ac.uk hardy/universe Packages                       
Hit http://archive.ubuntu.com hardy/main Packages                    
Err http://www.mirror.ac.uk hardy/main Packages                      
  404 Not Found
Ign http://packages.medibuntu.org hardy Release
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/main Sources                     
Hit http://archive.ubuntu.com hardy/restricted Sources               
Hit http://archive.ubuntu.com hardy/universe Packages
Err http://www.mirror.ac.uk hardy/universe Packages                  
  404 Not Found
Hit http://archive.ubuntu.com hardy/universe Sources                 
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/universe Sources
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Fetched 190B in 0s (279B/s)
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
XXXXX@ubuntu:~$ 

```

As this has been happening for 15 days I guess that it has nothing to do with archive updates.

BWT: Just installed Sysinfo and have my details:

[I][INDENT]Release:Ubuntu 8.04 (hardy)

GNOME: 2.22.2 (Ubuntu 2008-06-03)

Kernel: 2.6.24-17-generic (#1 SMP Thu May 1 14:31:33 UTC 2008)

GCC Version: 4.2.3 (i486-linux-gnu)[/INDENT][/I]

---

### Post by fidgaf on 2008-06-23
> **plucky said:**
> Try changing your server System > Administration > Software Sources and select the **Main Server** and **Reload**.

Good Luck

Tried Main and United Kingdom and got:

```
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

---

### Post by Zulu-Zeffir on 2008-06-23
Nevermind... see below.

---

### Post by Nepherte on 2008-06-23
Try removing the [http://www.mirror.ac.uk](http://www.mirror.ac.uk) and medibuntu entries in /etc/apt/sources.list and update
```
gksudo gedit /etc/apt/sources.list
sudo apt-get update
```

And try this:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by fidgaf on 2008-06-23
> **Nepherte said:**
> Try removing ....

And try this:

Well that was fascinating. :)

I have tried Software Sources and Update Manager and neither have given me any problems.

It looks like you have solved it for me. 

Pity I haven't a clue what I did. :):)

Thanks to everyone for their help.

Appreciated.

---

