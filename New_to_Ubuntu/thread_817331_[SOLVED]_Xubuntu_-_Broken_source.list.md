---
title: "[SOLVED] Xubuntu - Broken source.list"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by janskey on 2008-06-03
Hi Guys,

I tried installing Xubuntu today and got a problem when I update my system.

#apt-get update
.....
.....
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages                                               
Fetched 767B in 7s (101B/s)                                                                                    
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


Any idea on how to fix this? Just googling arround I found out that this need to import gpg keys. How do i do this?

---

### Post by EXCiD3 on 2008-06-03
Just do this in terminal and that should fix your problems:

```
wget archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg
wget archive.ubuntu.com/ubuntu/dists/hardy-updates/Release2.gpg
wget archive.ubuntu.com/ubuntu/dists/hardy-security/Release3.gpg

sudo apt-key add Release.gpg
sudo apt-key add Release2.gpg
sudo apt-key add Release3.gpg
```

---

### Post by janskey on 2008-06-04
Thanks EXCiD3..but still it doesn't work:

root@test:~# wget archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg
--13:42:51--  [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)
           => `Release.gpg'
Resolving archive.ubuntu.com... 91.189.88.46, 91.189.88.31, 91.189.88.45
Connecting to archive.ubuntu.com|91.189.88.46|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 191 [text/plain]

100%[====================================>] 191           --.--K/s             

13:42:51 (12.72 MB/s) - `Release.gpg' saved [191/191]

root@axis:~# apt-key add Release.gpg 
gpg: no valid OpenPGP data found.


Any hints?

---

### Post by Sef on 2008-06-04
Moved to Absolute Beginners.

---

### Post by bumanie on 2008-06-04
Post output of > cat /etc/apt/sources.list

---

### Post by EXCiD3 on 2008-06-04
In System > Administration > Software Sources > Authentication tab, what entries do you have?

bumanie it doesnt look like it has to do with the sources.list but more an issue with the GPG signatures. I think hes misisng the Ubuntu Archive signature. Wouldnt hurt to help having the sources.list output though! :)

---

### Post by janskey on 2008-06-05
i didn't touch anything on my keys..this is default installation. what i mean is that, after installing xubuntu hardy and tried to update because update manager pop's up for 83updates. but the keys aren't been recognized. 

EXCiD3 -- there are 2 keys in software sources
1. ubuntu archive automatic singning key
2. ubuntu cd image automatic singing key

And btw, this problem doesn't occur on xubuntu it includes ubuntu. I tried re-installing it to ubuntu and same problem on the keys.

CD info - i dowloaded the cd iso's last 3 days ago and verify md5sum to check if the files corrupted. So i think its not an ISO problem, its the gpg keys i guess.

---

### Post by EXCiD3 on 2008-06-05
Thats weird that the gpg keys arent registering...the one you need is the ubuntu archive one. It should be the gpg key for ALL of the ubuntu archive servers and for some reason it wont authenticate.

I'll get back to you once i find anything.

---

### Post by EXCiD3 on 2008-06-06
I found a file related to ubuntu archive that is a gpg file located in /var/lib/apt/keyring. I think this is probably the file that is causing your problem...just not sure what you should do now! :(

---

### Post by janskey on 2008-06-06
EXCiD3, is this a common problem? was it because of the iso that i download? or its a bug? any advice?

---

### Post by EXCiD3 on 2008-06-06
Well to tell you the truth, ive never seen anyone with this problem. Searching for help sure hasn't found anything much either. :(

I guess try removing the Ubuntu archive key from Software Sources and see if it lets you update still. It may complain about the source not being verified with a key but at least you should be able to update.

---

### Post by janskey on 2008-06-07
> **EXCiD3 said:**
> I found a file related to ubuntu archive that is a gpg file located in /var/lib/apt/keyring. I think this is probably the file that is causing your problem...just not sure what you should do now! :(

EXCiD3, is this a possible bug?

---

### Post by EXCiD3 on 2008-06-07
It could be although im not sure what to make of it because nobody else has experienced this problem that i can find. I guess it couldnt hurt to post it as a bug on launchpad. Just make sure to include everything you can, os version, kernel, architecture, sources.list, def include the information about the keys in Software Sources.

Sorry, i cant help too much from here. have you tried removing the "Ubuntu Archive" key from software sources?

---

### Post by donniewiko on 2008-09-17
i too had this problem.

However i fixed this by doing the following:

sudo mv /etc/apt/sources.list /etc/apt/sources.old
sudo cp /etc/apt/sources.list.apt-setup /etc/apt/sources.list
sudo apt-get update

---

