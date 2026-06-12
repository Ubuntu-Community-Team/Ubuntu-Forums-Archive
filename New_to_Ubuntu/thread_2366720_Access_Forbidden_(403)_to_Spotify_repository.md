---
title: "Access Forbidden (403) to Spotify repository"
date: 2017-07-21
forum: New to Ubuntu
---

### Post by niconicoj on 2017-07-21
Hi,

I am trying to get Spotify for Linux but I can get around an error 403 when trying to access the repository.

I followed the official tutorial :

# 1. Add the Spotify repository signing key to be able to verify downloaded packages
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886

# 2. Add the Spotify repository
echo deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list

# 3. Update list of available packages
sudo apt-get update

# 4. Install Spotify
sudo apt-get install spotify-client
Everything goes smoothly in the beginning :

```
woodbrass@STAGEDEVINFO:~$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886
Executing: /tmp/tmp.inQF5VJ813/gpg.1.sh --keyserver
hkp://keyserver.ubuntu.com:80
--recv-keys
BBEBDCB318AD50EC6865090613B00F1FD2C19886
gpg: requesting key D2C19886 from hkp server keyserver.ubuntu.com
gpg: key D2C19886: public key "Spotify Public Repository Signing Key <operations@spotify.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
woodbrass@STAGEDEVINFO:~$ echo deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
```


but errors appears on step 3 : 

```
woodbrass@STAGEDEVINFO:~$ sudo apt-get update
Ign:1 [http://repository.spotify.com](http://repository.spotify.com) xenial InRelease
Ign:2 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                                                                                  
Ign:3 [http://repository.spotify.com](http://repository.spotify.com) xenial Release                                                                                    
Ign:4 [http://repository.spotify.com](http://repository.spotify.com) stable Release                                                                                    
[...]                                                                           
Ign:20 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free DEP-11 64x64 Icons                                                                                 
Err:5 [http://repository.spotify.com](http://repository.spotify.com) xenial/main amd64 Packages                                                                                          
  403  Forbidden [IP: 52.222.174.9 80]
Ign:6 [http://repository.spotify.com](http://repository.spotify.com) xenial/main i386 Packages                                                                                           
[...]                                                                                
Ign:12 [http://repository.spotify.com](http://repository.spotify.com) xenial/main DEP-11 64x64 Icons                                                                                     
Err:13 [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages                                                                                     
  403  Forbidden [IP: 52.222.174.9 80]
Hit:28 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial-updates InRelease                                                                                     
[...]
Ign:34 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease
Fetched 147 kB in 0s (194 kB/s)
Reading package lists... Done
W: The repository 'http://repository.spotify.com xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://repository.spotify.com stable Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://security.debian.org/debian-security](http://security.debian.org/debian-security) wheezy/updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9D6D8F6BC857C906  NO_PUBKEY 8B48AD6246925553
W: The repository 'http://security.debian.org/debian-security wheezy/updates InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
W: The repository 'https://repo.skype.com/deb stable InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://repository.spotify.com/dists/xenial/main/binary-amd64/Packages](http://repository.spotify.com/dists/xenial/main/binary-amd64/Packages)  403  Forbidden [IP: 52.222.174.9 80]
E: Failed to fetch [http://repository.spotify.com/dists/stable/non-free/binary-amd64/Packages](http://repository.spotify.com/dists/stable/non-free/binary-amd64/Packages)  403  Forbidden [IP: 52.222.174.9 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```
I see several 403 forbidden and also two instance of spotify repository (stable and xenial). I don't know where the error come from but if I understand correctly the repository refuses to let me access it.

I tried the last step anyway but without any surprise :
```

woodbrass@STAGEDEVINFO:~$ sudo apt-get install spotify-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package spotify-client
```Can anyone help me with this ?

---

### Post by TheFu on 2017-07-21
Error 403 is from the server, not the client.
There could be any number of reasons why the server would return a 403 error.  I cannot speak for Spotify, but I return 403 errors for requests that are
* for files not available to the public - login.php - anyone asking for php files from my domain are automatically blocked, since they are clearly attackers.
* from clients that I've found to be abusive - mainly RSS feed readers that hit every 1-5 minutes 
* from subnets that have been abusive - subnets that host web attacks I block.
* include referrers that have been abusive - like when a client directly asks for an image without starting at one of my webpages first.  This is bandwidth stealing.
* Blocked when files are being updated to prevent corrupt downloads.
* misconfiguration.  It happens.  Mistakes are made. Try again later.
* 'non-free' - does that mean paid?  Did you pay for access?

Hope this is helpful.  You can try a different client - use a normal web browser to access the files.  Does that work?

Basically it means to wait a few hrs or a few days and try again.

I visited  [http://repository.spotify.com/dists/](http://repository.spotify.com/dists/) and didn't see any 403 errors from here. I did NOT use APT for my tests.

---

### Post by oldos2er on 2017-07-21
You can add your missing keys with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8B48AD6246925553 9D6D8F6BC857C906 1F3045A5DF7587C3

sudo apt update
```

---

