---
title: "Ubuntu 14.04 Update Manager Error"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by johan-t on 2014-05-29
Hey while i was trying to update this happened. (In attachment)



Could anyone explain to me what happened and show me how to fix it?

Thanks, Johan

---

### Post by tripp98 on 2014-05-29
please open a terminal and type
sudo apt-get update
sudo apt-get upgrade

report any errors if you get any back to this post

ps welcome to the forums

---

### Post by johan-t on 2014-05-30
Hey, Thanks for the reply.
when i typed sudo apt-get update 

Fetched 18.1 MB in 14min 58s (20.1 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.nus.edu.sg_ubuntu_dists_trusty_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

When I typed sudo apt-get upgrade

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.nus.edu.sg_ubuntu_dists_trusty_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

I think that was about it.
Thanks, Johan

---

### Post by plucky on 2014-05-30
> Fetched 18.1 MB in 14min 58s (20.1 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.nus.edu.sg_ubuntu_dists_trusty_universe_i18 n_Translation-en
E: The package lists or status file could not be parsed or opened.

Open a terminal and type ```
sudo rm /var/lib/apt/lists/* -vf
``` and then ```
sudo apt-get update
```

The first command will delete all the files in the /var/lib/apt/lists/ directory in which the file that is giving the error will be deleted, and then the second command will reload the files from the repositories.

If there are still errors,you should change your download server in "Software and Updates" and run the two commands again.

Good Luck.

---

### Post by bapoumba on 2014-05-30
In addition to what plucky said, sometimes there is also a /var/lib/apt/lists/partial sub-directory that may need to be removed.

---

### Post by johan-t on 2014-05-30
Hey, I did what you said and this happened.

Fetched 19.5 MB in 26min 34s (12.2 kB/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.200 80]


W: Failed to fetch [http://mirror.nus.edu.sg/ubuntu/dists/trusty/universe/binary-i386/Packages](http://mirror.nus.edu.sg/ubuntu/dists/trusty/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://mirror.nus.edu.sg/ubuntu/dists/trusty/main/i18n/Translation-en_US](http://mirror.nus.edu.sg/ubuntu/dists/trusty/main/i18n/Translation-en_US)  Connection failed


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by bapoumba on 2014-05-30
Is this an error to **sudo apt-get update** ?
Please post the complete output.
In addition, please post :
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
ls /var/lib/apt/lists/
ls /var/lib/apt/lists/partial 
```

---

### Post by johan-t on 2014-05-30
Hey, i typed these commands into the terminal. The commands are on the top and the results on the bottom.
```
cat /etc/apt/sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) trusty main restricted multiverse
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) trusty main restricted multiverse


## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) trusty universe
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) trusty universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.




## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib # disabled on upgrade to precise
# deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib # disabled on upgrade to precise
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security restricted main universe multiverse
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) trusty-updates restricted main universe multiverse


```



```
ls /etc/apt/sources.list.d

atareao-atareao-trusty.list
atareao-atareao-trusty.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
fingerprint-fingerprint-gui-precise.list
fingerprint-fingerprint-gui-precise.list.distUpgrade
fingerprint-fingerprint-gui-precise.list.save
google-chrome.list
google-chrome.list.save
google-earth.list
google-earth.list.distUpgrade
google-earth.list.save
nilarimogard-webupd8-trusty.list
oneiric-partner.list
oneiric-partner.list.distUpgrade
oneiric-partner.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-50_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-50_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-50_ubuntu.list.save
webupd8team-java-precise.list
webupd8team-java-precise.list.distUpgrade
webupd8team-java-precise.list.save
```




```
ls /var/lib/apt/lists/

dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages
dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages
dl.google.com_linux_chrome_deb_dists_stable_Release
dl.google.com_linux_chrome_deb_dists_stable_Release.gpg
lock
mirror.nus.edu.sg_ubuntu_dists_trusty_main_binary-amd64_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty_main_binary-i386_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty_main_i18n_Translation-en
mirror.nus.edu.sg_ubuntu_dists_trusty_main_source_Sources
mirror.nus.edu.sg_ubuntu_dists_trusty_multiverse_binary-amd64_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty_multiverse_binary-i386_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty_multiverse_i18n_Translation-en
mirror.nus.edu.sg_ubuntu_dists_trusty_multiverse_source_Sources
mirror.nus.edu.sg_ubuntu_dists_trusty_Release
mirror.nus.edu.sg_ubuntu_dists_trusty_Release.gpg
mirror.nus.edu.sg_ubuntu_dists_trusty_restricted_binary-amd64_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty_restricted_binary-i386_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty_restricted_i18n_Translation-en
mirror.nus.edu.sg_ubuntu_dists_trusty_restricted_source_Sources
mirror.nus.edu.sg_ubuntu_dists_trusty_universe_binary-amd64_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty_universe_i18n_Translation-en
mirror.nus.edu.sg_ubuntu_dists_trusty_universe_source_Sources
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_main_binary-amd64_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_main_binary-i386_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_main_i18n_Translation-en
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_multiverse_binary-amd64_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_multiverse_i18n_Translation-en
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_Release
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_Release.gpg
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_restricted_binary-amd64_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_restricted_i18n_Translation-en
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_universe_binary-amd64_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_universe_binary-i386_Packages
mirror.nus.edu.sg_ubuntu_dists_trusty-updates_universe_i18n_Translation-en
partial
ppa.launchpad.net_atareao_atareao_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_atareao_atareao_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_atareao_atareao_ubuntu_dists_trusty_Release
ppa.launchpad.net_atareao_atareao_ubuntu_dists_trusty_Release.gpg
ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_main_binary-amd64_Packages
ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_main_binary-i386_Packages
ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_Release
ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_trusty_Release.gpg
security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_main_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_trusty-security_Release
security.ubuntu.com_ubuntu_dists_trusty-security_Release.gpg
security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_restricted_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_universe_i18n_Translation-en
```



```
ls /var/lib/apt/lists/partial

mirror.nus.edu.sg_ubuntu_dists_trusty_universe_binary-i386_Packages

```



Hope this help's :D

---

### Post by bapoumba on 2014-05-31
Sorry, I'm not sure why I asked all that, the first 2 ones were enough, I must have copy/pasted from another post and did not remove the unnecessary parts..

The mirrors from your source.list give 404 errors, even here. Please try using another mirror or the main repositories to test.
You can do this from Administration > Software Sources : [https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

Once done, I *think* it offers to reload the sources.list. In any case, please run :
```
sudo apt-get update
sudo apt-get upgrade
```
And post any error you get. Please use code tags to help the reading long outputs on the forums : [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by LastDino on 2014-05-31
Generally speaking errors like 
```
''404''
''connection failed''
''connection times out'' 
```
are usually indications that you need to update your mirror list, if then you get any specific errors like 
```
''ppa source not available''
''xyz package is not available''
''xyz package is failed to download and hence ignored or used older'' 
```

usually translate to; you need to check your resource list. And when this is the case, track the packages mentioned in errors and remove/fix those PPA or whatever sources you might be having there.

---

### Post by johan-t on 2014-05-31
Hey, I think I need the Ubuntu software center to change the mirror. But the software center crash's when I try to launch it.

---

### Post by LastDino on 2014-05-31
You need to go into settings> and click on Software&Update manager>

. Software centre is just the GUI wrapper, not the real deal.   

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Look under the section saying ''Download server''.

---

### Post by Bashing-om on 2014-05-31
Guys:

There may be more going on here than meets my eyes.

[http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/i18n/Translation-en_US)
does indeed yield a 404 Not Found ->
BUT, but 
[http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/i18n/](http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/i18n/)
is valid But, but but
looking in the Translation-en directory .....
there is no listing for Translation-en_US as the source.list requires.
So what gives ?

Is there a rat in the wood pile ?

Similar results for the other two sources.

[INDENT][INDENT]I find it hard to believe
[INDENT][INDENT][INDENT]my suspicions [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by LastDino on 2014-05-31
@Johan-T; At the end of selecting best server you will be asked to download new resource list (or w/e list). Click yes/now, whatever positive it might have. If what Bashing-om is thinking, is correct, then you will get some errors, click on details if shown the button in error message, and then post those here.

---

### Post by johan-t on 2014-06-05
Hey, sorry it took me a while to reply.
well i changed the location of where i update from and that fixed the problem like you guys said right?
any way it worked and thanks a lot
Thanks, Johan

---

### Post by bapoumba on 2014-06-05
Please mark your thread as solved (under Thread tools), thanks.

---

