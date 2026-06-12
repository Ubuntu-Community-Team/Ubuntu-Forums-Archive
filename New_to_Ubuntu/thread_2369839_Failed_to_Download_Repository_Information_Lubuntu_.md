---
title: "Failed to Download Repository Information Lubuntu 16.04.3 LTS"
date: 2017-08-27
forum: New to Ubuntu
---

### Post by gabe-l on 2017-08-27
New to Linux and Ubuntu, recently installed Lubuntu 16.04 after the 17.04 release wouldn't work. Software updater worked only a few times before the message "Failed to Download Repository Information Check your Internet Connection" started appearing. sudo apt-get update outputs the following: 

```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://ppa.launchpad.net/snwh/pulp/ubuntu](http://ppa.launchpad.net/snwh/pulp/ubuntu) xenial InRelease               
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Ign:4 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial InRelease           
Hit:6 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                     
Ign:7 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial Release
Ign:8 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Sources
Ign:9 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main amd64 Packages
Ign:10 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main i386 Packages
Ign:11 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main all Packages
Ign:12 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en
Ign:8 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Sources
Ign:9 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main amd64 Packages
Ign:10 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main i386 Packages
Ign:11 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main all Packages
Ign:12 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en
Ign:8 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Sources
Ign:9 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main amd64 Packages
Ign:10 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main i386 Packages
Ign:11 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main all Packages
Ign:12 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en
Ign:8 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Sources
Ign:9 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main amd64 Packages
Ign:10 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main i386 Packages
Ign:11 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main all Packages
Ign:12 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en
Ign:8 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Sources
Ign:9 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main amd64 Packages
Ign:10 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main i386 Packages
Ign:11 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main all Packages
Ign:12 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en
Err:8 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Sources
  404  Not Found
Ign:9 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main amd64 Packages
Ign:10 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main i386 Packages
Ign:11 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main all Packages
Ign:12 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) xenial/main Translation-en
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/source/Sources)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Any info on how this can be fixed in my case would be much appreciated :)

---

### Post by yetimon_64 on 2017-08-27
First comment is please use "code tags" when posting terminal output. The third link in my signature line will show you how to use the tags needed to avoid all those url links in your post.

You can simply disable the tualatrix ppa in "Software and Updates". [s]Search dash for "Software and updates" and open it and go to the "other software" tab and deselect any entries for "tualatrix". Use the "reload" option after closing the "Software and updates" window to complete the process.

Then rerun the sudo apt-get update command you first tried to check if ok. [/s]

**Edit:** just noted the "Lubuntu" in your thread title : I am unsure of how to use or if Software and Updates is available in Lubuntu. My response was assuming a unity install (which was wrong for Lubuntu :-))
You will need to disable the tualatrix ppa in Lubuntu still, but I am totally unsure of how to do so in Lubuntu.

---

### Post by gabe-l on 2017-08-27
```

Thanks so much this fixed my issue, and I was curious how to post code

```

---

### Post by deadflowr on 2017-08-27
Simply run
```
sudo add-apt-repository -r ppa:tualatrix/ppa
```
and
```
sudo apt-get update
```
from the terminal.
This should clear the tualatrix ppa and reload the updates clean this time.
No version of the ppa exists for 16.04.

---

### Post by vasa1 on 2017-08-28
> **yetimon_64 said:**
> ...
**Edit:** just noted the "Lubuntu" in your thread title : I am unsure of how to use or if Software and Updates is available in Lubuntu. ...
I'm nearly certain it is available in Lubuntu as well. Lubuntu 16.04 does have a *different* software center.

---

