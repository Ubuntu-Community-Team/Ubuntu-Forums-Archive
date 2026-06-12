---
title: "Ubuntu Studio 16.04 buggy after app crash"
date: 2017-08-14
forum: New to Ubuntu
---

### Post by kc10hydroman on 2017-08-14
I have been using Ubuntu Studio for just over a year now and really like it. About a month ago I was watching a movie on Xine video player when it locked up on me.  After 20 minutes of not being able to do anything with the computer I hit the reset button to start over.  A couple weeks went by and everything looked ok when I noticed the software was not updating.  I tried to change servers in the software and update settings and got this error:  Failed to download repository information. Check your internet connection.  This happened to every repository I tried.  Here are the details it gave me: 

```

 W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/ehoover-ubuntu-compholio-xenial.list:2 and /etc/apt/sources.list.d/ehoover-ubuntu-compholio-xenial.list:3,
 W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/ehoover-ubuntu-compholio-xenial.list:2 and /etc/apt/sources.list.d/ehoover-ubuntu-compholio-xenial.list:4, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:3, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:4, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:5, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:6, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:7, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list:8, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/skunk-ubuntu-pepper-flash-xenial.list:2 and /etc/apt/sources.list.d/skunk-ubuntu-pepper-flash-xenial.list:3,
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-xenial.list:2 and /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-xenial.list:3, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list:2 and /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list:3, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list:2 and /etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list:3, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list:2 and /etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list:3, 
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list:2 and /etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list:4, 
W:An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551, 
W:The repository 'http://ppa.launchpad.net/skunk/pepper-flash/ubuntu xenial Release' does not have a Release file., Wata from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
W:The repository 'http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu xenial Release' does not have a Release file., Wata from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., W:Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551,
E:Failed to fetch [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/xenial/main/source/Sources)  404  Not Found, E:Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/xenial/main/source/Sources)  404  Not Found, 
W:Some index files failed to download. They have been ignored, or old ones used instead.

```

In the last few days I have been getting random "Ubuntu has encountered a problem" errors.  Is this an easy fix or would I be better off installing a newer version?

---

### Post by Perfect Storm on 2017-08-15
Clean up the wall of text and added code tags.

---

### Post by kc10hydroman on 2017-08-15
After scouring the interweb for the last few hours I can not find a command for cleaning the text and added code.  I tried all the clean commands I could find with no joy (a first I might add).  What do I do to clean up this mess?

---

### Post by Andreyshel on 2017-08-15
There is nothing dangerous.
> ...
W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/ehoover-ubuntu-compholio-xenial.list:2 and /etc/apt/sources.list.d/ehoover-ubuntu-compholio-xenial.list:3
...
This lines mean that you have some repositories added twice.

> W:An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551, 





Yoiu have to import security key for google repository.

Use this command
wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -> 
E:Failed to fetch [http://ppa.launchpad.net/skunk/peppe...source/Sources](http://ppa.launchpad.net/skunk/peppe...source/Sources)  404  Not Found, E:Failed to fetch [http://ppa.launchpad.net/ubuntu-audi...source/Sources](http://ppa.launchpad.net/ubuntu-audi...source/Sources)  404  Not Found, 



This repository does not include source packages, so you should uncheck respective line in software sources.
Hope it helps

---

### Post by kc10hydroman on 2017-08-15
Ok, I figured it out.  Updates working fine now.  Just hope that fixes the unexpected thingy.  Thank you so much for your help.

Signed,
A very satisfied customer  :D

---

