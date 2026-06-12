---
title: "Problem running sudo apt-get update"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by simi123 on 2013-02-23
Whenver i try to run sudo apt-get update i am getting the following output:
```

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources   
  407  Proxy Authentication Required
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages
  407  Proxy Authentication Required
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
  407  Proxy Authentication Required
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/mai Sources
  407  Proxy Authentication Required
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  407  Proxy Authentication Required
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  407  Proxy Authentication Required
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages
  407  Proxy Authentication Required
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  407  Proxy Authentication Required

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

When i try to play any audio file i am getting following error:
Required plugin could not be found Python (v2.7) required to install plugins to play media files of the following type: MPEG-1 Layer 3 (MP3) decoder

For this when i try to run:  sudo apt-get install ubuntu-restricted-extras, i am getting error:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras

Moreover, I am unable to install any software from ubuntu software center. 

I have tried all answers which i got when i searched in google but nothing worked for me.
I have been trying this since the last 2-3 days with no fruitful result.

---

### Post by alphacrucis2 on 2013-02-23
You are connecting to the internet via a proxy server that requires authentication?

---

### Post by Roskow on 2013-02-23
Could this be a DNS problem?  

When I have a fail to fetch issue I'll try editing /etc/resolv.conf and adding "nameserver 8.8.8.8" which is Google. 

This is only a temporary patch to do a test. When you reboot the Resolv.conf will be overwritten.

---

### Post by simi123 on 2013-02-23
yes i am using internet via proxy that requires authentication

---

### Post by simi123 on 2013-02-23
i edited the resolv.confg file but getting the same error

---

### Post by alphacrucis2 on 2013-02-23
> **simi123 said:**
> i edited the resolv.confg file but getting the same error

Nothing to do with DNS. The error message you are getting is telling you what is wrong. You need to configure apt to use your proxy server:

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

---

### Post by simi123 on 2013-02-23
After  configuring the apt file, atleast something is happening but still m getting few errors.

On executing sudo apt-get update I m getting the following error now:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by plucky on 2013-02-23
> **simi123 said:**
> After  configuring the apt file, atleast something is happening but still m getting few errors.

On executing sudo apt-get update I m getting the following error now:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

If you click on that link it goes [Here](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources) ,and it looks as though the line in your sources list has main spelt as mai , which is causing the 404 error.

Edit the list in sources.list.d directory to correct the spelling.

If you need further help,post output for ```
ls /etc/apt/sources.list.d/*.list
```

Good luck

---

### Post by alphacrucis2 on 2013-02-23
> **simi123 said:**
> After  configuring the apt file, atleast something is happening but still m getting few errors.

On executing sudo apt-get update I m getting the following error now:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/precise/mai/source/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

The ../mai/source...  part of the URL looks to be an error. Should be ../main/source/... Looks like you have been manually editing your sources and have typo'd it. I would just disable that ppa in software sources for the time being and try again.

---

### Post by simi123 on 2013-02-23
I corrected the spelling now getting just 1 error:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5

---

### Post by schragge on 2013-02-23
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5

```

---

