---
title: "Software updater fails because of error in signature verification."
date: 2017-04-22
forum: New to Ubuntu
---

### Post by JuanNZ on 2017-04-22
Hi Everyone, 

Apologies if this is already a duplicated thread . 

I have Ubuntu 16.04 LTS installed on my laptop. A few months ago I noticed the automatic updates stopped. I then noticed that I had two different versions of the software updater installed and one of them was not working at all. I un installed both of them and installed again only the newest version. 

The new updater works and notifies me about the updates needed to install, but the process gets killed after I enter the authentication password.

Same happens in the terminal when I type: 

```
sudo apt-get update && sudo apt-get install 
```

this is the terminal output:


```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:2 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease
Ign:3 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease
Get:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1,189 B]
Get:5 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release [2,136 B]
Hit:6 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release
Get:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [916 B]
Err:8 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release.gpg
  At least one invalid signature was encountered.
Get:9 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release.gpg [916 B]
Err:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg  
  At least one invalid signature was encountered.
Err:9 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release.gpg
  At least one invalid signature was encountered.
Get:10 [https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian) jessie InRelease [23.5 kB]
Ign:10 [https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian) jessie InRelease
Get:11 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]
Get:12 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease [11.5 kB]
Err:12 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease            
  At least one invalid signature was encountered.
Get:13 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Ign:11 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial InRelease   
Get:14 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Ign:13 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Get:15 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Ign:14 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Ign:15 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-security InRelease
Fetched 590 kB in 5s (103 kB/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release: At least one invalid signature was encountered.
W: GPG error: [https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian) jessie InRelease: At least one invalid signature was encountered.
W: The repository 'https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease: At least one invalid signature was encountered.
W: GPG error: [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial InRelease: At least one invalid signature was encountered.
W: The repository 'http://de.archive.ubuntu.com/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates InRelease: At least one invalid signature was encountered.
W: The repository 'http://de.archive.ubuntu.com/ubuntu xenial-updates InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-backports InRelease: At least one invalid signature was encountered.
W: The repository 'http://de.archive.ubuntu.com/ubuntu xenial-backports InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-security InRelease: At least one invalid signature was encountered.
W: The repository 'http://de.archive.ubuntu.com/ubuntu xenial-security InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)  At least one invalid signature was encountered.
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  At least one invalid signature was encountered.
W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg](http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg)  At least one invalid signature was encountered.
W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  At least one invalid signature was encountered.
W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 425 not upgraded.
```

Any ideas as how to fix this?

Thanks for you help

---

### Post by Xian on 2017-04-30
```
[COLOR=#000000][FONT=&amp]GPG error: [/FONT][/COLOR][https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian)[COLOR=#000000][FONT=&amp] jessie InRelease: At least one invalid signature was encountered[/FONT][/COLOR]
```

Some of these mirrors appear to be 404/out of date. 

Verify they are still active and replace if needed ...

---

### Post by JuanNZ on 2017-05-02
Thanks Xian,

I modified the Software Updater settings, leaving checked only the important security updates and the recommended updates for Xenial. No change. System still does not update.

---

### Post by JuanNZ on 2017-05-02
Actually, I was able to solve my issue by looking at this post:
[URL="https://askubuntu.com/questions/769925/please-help-sudo-apt-get-update-error-ubuntu-16-04-lts-version"]
[/URL]https://askubuntu.com/questions/769925/please-help-sudo-apt-get-update-error-ubuntu-16-04-lts-version

So problem solved

---

