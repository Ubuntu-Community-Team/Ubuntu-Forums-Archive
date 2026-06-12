---
title: "Missing public keys when updating"
date: 2020-10-21
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-10-21
Edit: Just discovered 'apt-key' which does list the keys under 'trusted.gpg.d/'. I'm a little confused now...

Edit 2: '/etc/apt/trusted.gpg' does not exist. is this a problem?

Hi everyone,

Apparently I'm missing some public keys so APT cannot verify the signatures of the package lists provided by some of my sources? correct me if I'm wrong, PGP/GPG always confuses me

When I run 'gpg --list-keys' I get nothing at all, even though '/etc/apt/trusted.gpg.d/' does contain six .gpg files. do I need to add these to my keyring in '~/.gnupg'? as an experiment I added one of the keys using 'gpg --import /etc/apt/trusted.gpg.d/<key file>' and ran 'gpg --list-keys' again, at which point it did list that key. is my problem an empty keyring?

The output of 'apt update' is as follows...

```
sudo apt update
Hit:1 http://ppa.launchpad.net/teejee2008/timeshift/ubuntu focal InRelease
Get:2 http://es-mirrors.evowise.com/ubuntu focal InRelease [265 kB] 
Get:3 http://repository.spotify.com stable InRelease [3,316 B]              
Err:3 http://repository.spotify.com stable InRelease                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D1742AD60D811D58
Get:4 http://debian.drdteam.org stable InRelease [2,966 B]
Get:5 http://es-mirrors.evowise.com/ubuntu focal-updates InRelease [111 kB]
Hit:6 http://es-mirrors.evowise.com/ubuntu focal-backports InRelease
Err:4 http://debian.drdteam.org stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 392203ABAF88540B
Hit:7 http://es-mirrors.evowise.com/ubuntu focal-security InRelease
Ign:8 http://es-mirrors.evowise.com/ubuntu focal-updates/main amd64 Packages
Get:9 http://es-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages [351 kB]
Get:9 http://es-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages [351 kB]
Get:9 http://es-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages [351 kB]
Get:9 http://es-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages [351 kB]
Get:9 http://es-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages [351 kB]
Ign:9 http://es-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages
Ign:15 http://es-mirrors.evowise.com/ubuntu focal-updates/main amd64 DEP-11 Metadata
Ign:16 http://es-mirrors.evowise.com/ubuntu focal-updates/universe i386 Packages
Ign:17 http://es-mirrors.evowise.com/ubuntu focal-updates/universe amd64 Packages
Ign:18 http://es-mirrors.evowise.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata
Ign:19 http://es-mirrors.evowise.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata
Get:8 http://es-mirrors.evowise.com/ubuntu focal-updates/main amd64 Packages [610 kB]
Err:8 http://es-mirrors.evowise.com/ubuntu focal-updates/main amd64 Packages
  File has unexpected size (615288 != 610432). Mirror sync in progress? [IP: 104.22.5.179 80]
  Hashes of expected file:
   - Filesize:610432 [weak]
   - SHA256:3e905a9c2d729ef8173340a5cbfbbde9ef77d44ea6b42aa3906172270e15f9f5
   - SHA1:3aa098c7c876e88fb76516983eacdf43ceb96d1e [weak]
   - MD5Sum:0437d603e7875ea0d185afb5f102ecdc [weak]
  Release file created at: Sat, 17 Oct 2020 18:45:56 +0000
Get:9 http://es-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages [351 kB]
Err:9 http://es-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages
  
Get:15 http://es-mirrors.evowise.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [229 kB]
Err:15 http://es-mirrors.evowise.com/ubuntu focal-updates/main amd64 DEP-11 Metadata
  
Get:16 http://es-mirrors.evowise.com/ubuntu focal-updates/universe i386 Packages [504 kB]
Err:16 http://es-mirrors.evowise.com/ubuntu focal-updates/universe i386 Packages
  
Get:17 http://es-mirrors.evowise.com/ubuntu focal-updates/universe amd64 Packages [669 kB]
Err:17 http://es-mirrors.evowise.com/ubuntu focal-updates/universe amd64 Packages
  
Get:18 http://es-mirrors.evowise.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [202 kB]
Err:18 http://es-mirrors.evowise.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata
  
Get:19 http://es-mirrors.evowise.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Err:19 http://es-mirrors.evowise.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata
  
Fetched 274 kB in 3s (103 kB/s)           
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D1742AD60D811D58
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://debian.drdteam.org stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 392203ABAF88540B
W: Failed to fetch http://debian.drdteam.org/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 392203ABAF88540B
W: Failed to fetch http://repository.spotify.com/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D1742AD60D811D58
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/main/binary-amd64/Packages.xz  File has unexpected size (615288 != 610432). Mirror sync in progress? [IP: 104.22.5.179 80]
   Hashes of expected file:
    - Filesize:610432 [weak]
    - SHA256:3e905a9c2d729ef8173340a5cbfbbde9ef77d44ea6b42aa3906172270e15f9f5
    - SHA1:3aa098c7c876e88fb76516983eacdf43ceb96d1e [weak]
    - MD5Sum:0437d603e7875ea0d185afb5f102ecdc [weak]
   Release file created at: Sat, 17 Oct 2020 18:45:56 +0000
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/main/binary-i386/Packages.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/main/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/universe/binary-i386/Packages.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/universe/binary-amd64/Packages.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/universe/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/multiverse/dep11/Components-amd64.yml.xz  
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by ActionParsnip on 2020-10-22
```
 
wget -O - http://debian.drdteam.org/drdteam.gpg | sudo apt-key add -

sudo apt-get update

```

---

### Post by jcdenton1995 on 2020-10-22
Thanks, I added that key and also managed to sort the problem Spotify was complaining of, however I'm still getting the following errors...```
Fetched 267 kB in 2s (119 kB/s)           
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://debian.drdteam.org stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 392203ABAF88540B
W: Failed to fetch http://debian.drdteam.org/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 392203ABAF88540B
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/main/binary-amd64/Packages.xz  File has unexpected size (615288 != 610432). Mirror sync in progress? [IP: 104.22.5.179 80]
   Hashes of expected file:
    - Filesize:610432 [weak]
    - SHA256:3e905a9c2d729ef8173340a5cbfbbde9ef77d44ea6b42aa3906172270e15f9f5
    - SHA1:3aa098c7c876e88fb76516983eacdf43ceb96d1e [weak]
    - MD5Sum:0437d603e7875ea0d185afb5f102ecdc [weak]
   Release file created at: Sat, 17 Oct 2020 18:45:56 +0000
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/main/binary-i386/Packages.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/main/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/universe/binary-i386/Packages.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/universe/binary-amd64/Packages.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/universe/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://es-mirrors.evowise.com/ubuntu/dists/focal-updates/multiverse/dep11/Components-amd64.yml.xz  
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by CelticWarrior on 2020-10-22
For those I suggest asking the maintainers of those repositories what's the problem. 
I can only suggest removing them if they don't work.

If you aren't experienced in managing additional repositories (PPAs and other third-party) you should avoid adding them.

---

### Post by jcdenton1995 on 2020-10-22
> **CelticWarrior said:**
> For those I suggest asking the maintainers of those repositories what's the problem. 
I can only suggest removing them if they don't work.

If you aren't experienced in managing additional repositories (PPAs and other third-party) you should avoid adding them.

It's sorted now thanks, you are right, I was getting confused as I had removed the key for a PPA that I no longer required, and had removed the package I once used it to retrieve, but I hadn't removed the URL from my 'sources.list' (mainly because I didn't realise what the PPA was). Also I changed the mirror I use to pull all the official repo stuff from it was actually a problem with that particular repository.

But I'm struggling to understand two things:

firstly the info page for apt-key explicitly states one shouldn't use the 'apt-key add' command, and instead should place key files under '/etc/apt/trusted.gpg.d/' with a descriptive name, and one of the file extensions '.gpg' or '.asc'. The former will simply bundle the key into a keyring named 'trusted.gpg' under '/etc/apt/' while the latter will store each public key as a separate file in the 'trusted.gpg.d/' directory. However when you do use the method the info page recommends and then run 'apt-key list' it will complain that the file type of any keys placed under '../trusted.gpg.d/' are not supported.

Secondly, why does 'apt-add-repository' only remove a source from '/etc/apt/sources.list' when the user specifies the long option '--remove' and not when using '-r'?

Basically what I'm saying is why are there directories for both sources and public keys, but also files in their parent directory that also store sources and public keys?...

/etc/apt/sources.list
/etc/apt/sources.list.d/
/etc/apt/trusted.gpg
/etc/apt/trusted.list.d/

Why? And how should they be used?

---

