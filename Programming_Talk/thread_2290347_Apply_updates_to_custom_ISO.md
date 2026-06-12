---
title: "Apply updates to custom ISO"
date: 2015-08-11
forum: Programming Talk
---

### Post by roland-logikalsolutions on 2015-08-11
I have been looking around for this information for days. Tried many things. I have a custom Ubuntu 15.04 64-bit ISO with an application loaded in. All is find. Now someone decides we should load all updates and language packs onto the ISO because machines it gets installed on have less than zero network access.

This link is so horribly out of date it is not funny: [https://help.ubuntu.com/community/LiveCDCustomization#Apt-get](https://help.ubuntu.com/community/LiveCDCustomization#Apt-get)

That link should really be taken down because, basically _nothing_ is correct in it. Wasted a couple of weeks trying to follow that advice for building custom ISO. The real answer is in a comment down at the bottom.

In the middle of my iso build script, which has been working fine for over a week, the following was added

```
chroot "$WDIR/sq-u" ./apply_updates.sh
```

in the file apply_updates.sh:

```
dbus-uuidgen > /var/lib/dbus/machine-id

dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

# Apply all updates
#
apt-get update
apt-get upgrade

# Install all language packs
#
apt-get -y install `check-language-support -l af`
apt-get -y install `check-language-support -l am`

```


Which spits out

```
Err http://archive.ubuntu.com vivid InRelease
  
Err http://security.ubuntu.com vivid-security InRelease
  
Err http://archive.ubuntu.com vivid-updates InRelease
  
Err http://archive.ubuntu.com vivid Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://security.ubuntu.com vivid-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://archive.ubuntu.com vivid-updates Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/vivid-security/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-updates/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/vivid-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-updates/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

I assume there is some magic incantation which has to happen to allow chroot from inside of my shell script to access the network connection of parent process, but cannot find it anywhere.

Help appreciated.

Well I did find my answer. Not as fast as timestamps here would lead one to believe since I was bit by the forum bug where tags can only be 18 characters but the pick list has tags > 18 for you to choose from.

[http://askubuntu.com/questions/590354/after-chroot-apt-get-update-err-and-failed-to-fetch-bootableflashfromharddis](http://askubuntu.com/questions/590354/after-chroot-apt-get-update-err-and-failed-to-fetch-bootableflashfromharddis)

It was the resolve.conf file

---

