---
title: "Help need to clean up sources.list !"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by yuri-weinstein on 2019-01-28
I am still on shaky grounds when issues relate to PPA etc.

I need help to fix and make my ubuntu 16.04 installation capable to update packages.

Here is output from 


```
sudo apt-get updateIgn:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                                                                    
Ign:3 http://linux.dropbox.com/ubuntu xenial InRelease                                                                        
Hit:4 http://linux.dropbox.com/ubuntu xenial Release                                                                          
Hit:7 http://ppa.launchpad.net/jcfp/nobetas/ubuntu xenial InRelease                                                           
Hit:8 http://archive.ubuntu.com/ubuntu xenial InRelease                                                                       
Hit:9 http://apt.sonarr.tv master InRelease                                                                                   
Hit:10 https://downloads.plex.tv/repo/deb ./public InRelease                                                                  
Hit:11 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                                                         
Ign:12 http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  InRelease            
Hit:13 http://ppa.launchpad.net/jcfp/sab-addons/ubuntu xenial InRelease                         
Hit:14 http://archive.ubuntu.com/ubuntu xenial-backports InRelease                             
Hit:15 http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04  Release                                         
Hit:16 http://archive.ubuntu.com/ubuntu xenial-security InRelease                                                          
Hit:17 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease
Hit:19 http://ppa.launchpad.net/transmissionbt/ppa/ubuntu xenial InRelease     
Reading package lists... Done 



```

When I run Software Updater I get 

[https://snag.gy/5s6IGe.jpg](https://snag.gy/5s6IGe.jpg)
   
[https://snag.gy/k0sXb1.jpg](https://snag.gy/k0sXb1.jpg)

[https://snag.gy/Kmh0Qq.jpg](https://snag.gy/Kmh0Qq.jpg)

[https://snag.gy/3mN9Rf.jpg](https://snag.gy/3mN9Rf.jpg)
 Error authenticating some packages
(
git
git-man
gitk
libsqlite3-0
libsqlite3-0:i386
libwayland-client0
libwayland-cursor0
libwayland-server0
libxapian30
python-twisted-bin
youtube-dl
)

Pls help!

---

### Post by yuri-weinstein on 2019-01-28
Wonder maybe there is a safe way to restore to initial settings ?

---

### Post by again? on 2019-01-28
Rather than linking screenshots that connect to 79 different domains
[ATTACH=CONFIG]282348[/ATTACH]
it would be more informative to post your output from
```
sudo dpkg --configure -a
sudo apt install -f
sudo apt update
sudo apt full-upgrade
```
and enabled repositories...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list | nl
```

---

### Post by yuri-weinstein on 2019-01-29
Here it is:
```

sudo dpkg --configure -a
sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo apt update
Ign:1 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) xenial InRelease
Hit:2 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) xenial Release                                                                          
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                  
Hit:5 [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) ./public InRelease                 
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                    
Hit:7 [http://ppa.launchpad.net/jcfp/nobetas/ubuntu](http://ppa.launchpad.net/jcfp/nobetas/ubuntu) xenial InRelease                                                
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                                                                                                                       
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                    
Hit:7 [http://ppa.launchpad.net/jcfp/nobetas/ubuntu](http://ppa.launchpad.net/jcfp/nobetas/ubuntu) xenial InRelease                                                
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                                                            
Hit:9 [http://apt.sonarr.tv](http://apt.sonarr.tv) master InRelease                                                                             
Ign:11 [http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04)  InRelease                                      
Hit:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease                                                          
Hit:13 [http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04)  Release                                       
Hit:14 [http://ppa.launchpad.net/jcfp/sab-addons/ubuntu](http://ppa.launchpad.net/jcfp/sab-addons/ubuntu) xenial InRelease                        
Hit:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease       
Hit:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease                                    
Hit:18 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) xenial InRelease                  
Hit:19 [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) xenial InRelease     
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


```

egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list | nl
     1    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
     2    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
     3    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
     4    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
     5    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
     6    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse
     7    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
     8    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
     9    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
    10    /etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse
    11    /etc/apt/sources.list.d/dropbox.list:deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) xenial main
    12    /etc/apt/sources.list.d/emby-server.list:deb [http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04/](http://download.opensuse.org/repositories/home:/emby/xUbuntu_16.04/) /
    13    /etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
    14    /etc/apt/sources.list.d/jcfp-ubuntu-nobetas-xenial.list:deb [http://ppa.launchpad.net/jcfp/nobetas/ubuntu](http://ppa.launchpad.net/jcfp/nobetas/ubuntu) xenial main
    15    /etc/apt/sources.list.d/jcfp-ubuntu-sab-addons-xenial.list:deb [http://ppa.launchpad.net/jcfp/sab-addons/ubuntu](http://ppa.launchpad.net/jcfp/sab-addons/ubuntu) xenial main
    16    /etc/apt/sources.list.d/plexmediaserver.list:deb [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) ./public main
    17    /etc/apt/sources.list.d/sonarr.list:deb [http://apt.sonarr.tv/](http://apt.sonarr.tv/) master main
    18    /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-xenial.list:deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) xenial main
    19    /etc/apt/sources.list.d/transmissionbt-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) xenial main
```

---

### Post by again? on 2019-01-29
Not seeing any errors.
Does Software Updater still give errors.

When you reply in advance mode you can use the "#" icon to enclose text in code tags.
[How to use [CODE] tags in your Posts]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by yuri-weinstein on 2019-01-29
Yes

I get: 

"Can't install 'ubuntu-desktop'

It was impossible to install a required package. Please report this as a bug using 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal."

and then the list:

"Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

gitgit-man
gitk
libsqlite3-0
libsqlite3-0:i386
libwayland-client0
libwayland-cursor0
libwayland-server0
libxapian30
python-twisted-bin
youtube-dl
"

---

### Post by again? on 2019-01-29
What's your output for ...
```
sudo apt install ubuntu-desktop
```

---

### Post by yuri-weinstein on 2019-01-29
> **guber2 said:**
> What's your output for ...
```
sudo apt install ubuntu-desktop
```


```
sudo apt install ubuntu-desktopReading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version (1.361.2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by again? on 2019-01-29
You only seem to have problems when using update manager.
Try reinstalling update-manager.
```
sudo apt install --reinstall update-manager
```

I don't really know what's going on.
Some things to look into:
[LIST]
[*]Do you install different versions of python?
[*]Is this an upgrade from 14.04?
[*]Besides the third party repos listed earlier have you used others.
[/LIST]

You should still find empty .list files of removed third party repos in **/etc/apt/sources.list.d**
This will show all disabled and enabled third party ppa's...
```
find /etc/apt/sources.list.d -name \*.list | cut -f 5 -d '/' | sort
```

[ppas and ppa-purge]("https://ubuntuforums.org/showthread.php?t=2297685&p=13368367#post13368367")

---

### Post by yuri-weinstein on 2019-01-30
Did  [COLOR=#000000][FONT=&quot]sudo apt install --reinstall update-manager

It was not 14.04 and not sure about Python

[/FONT][/COLOR]find /etc/apt/sources.list.d -name \*.list | cut -f 5 -d '/' | sort
dropbox.list
emby-server.list
google-chrome.list
jcfp-ubuntu-nobetas-xenial.list
jcfp-ubuntu-sab-addons-xenial.list
plexmediaserver.list
remmina-ppa-team-ubuntu-remmina-next-daily-xenial.list
remmina-ppa-team-ubuntu-remmina-next-xenial.list
sonarr.list
stebbins-ubuntu-handbrake-releases-xenial.list
transmissionbt-ubuntu-ppa-xenial.list

---

### Post by again? on 2019-01-30
It appears you are not the only one having troubles with update manager on 16.04.
May not be related though.
[https://ubuntuforums.org/showthread.php?t=2411297&page=1](https://ubuntuforums.org/showthread.php?t=2411297&page=1)

If you have synaptic installed, try using it's reload button to refresh package information to see if you get any errors.
Then close synaptic, reboot and try update-manager again.

---

### Post by yuri-weinstein on 2019-01-30
After reload I got:

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/xenial-partner.list:4Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/xenial-partner.list:4Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/xenial-partner.list:4Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/xenial-partner.list:4Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/xenial-partner.list:4Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:51 and /etc/apt/sources.list.d/xenial-partner.list:4The repository 'http://archive.getdeb.net/ubuntu xenial-getdeb Release' does not have a Release file.Data from such a repository can't be authenticated and is therefore potentially dangerous to use.See apt-secure(8) manpage for repository creation and user configuration details.GPG error: [http://ftp.debian.org/debian](http://ftp.debian.org/debian) stretch-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553  NO_PUBKEY 7638D0442B90D010The repository 'http://ftp.debian.org/debian stretch-backports InRelease' is not signed.Data from such a repository can't be authenticated and is therefore potentially dangerous to use.See apt-secure(8) manpage for repository creation and user configuration details.Failed to fetch [http://www.getdeb.net/ubuntu/dists/xenial-getdeb/apps/binary-amd64/Packages](http://www.getdeb.net/ubuntu/dists/xenial-getdeb/apps/binary-amd64/Packages)  403  ForbiddenFailed to fetch [http://www.getdeb.net/ubuntu/dists/xenial-getdeb/apps/i18n/Translation-en_US](http://www.getdeb.net/ubuntu/dists/xenial-getdeb/apps/i18n/Translation-en_US)  403  ForbiddenFailed to fetch [http://www.getdeb.net/ubuntu/dists/xenial-getdeb/apps/i18n/Translation-en](http://www.getdeb.net/ubuntu/dists/xenial-getdeb/apps/i18n/Translation-en)  403  ForbiddenFailed to fetch [http://www.getdeb.net/ubuntu/dists/xenial-getdeb/apps/dep11/Components-amd64.yml](http://www.getdeb.net/ubuntu/dists/xenial-getdeb/apps/dep11/Components-amd64.yml)  403  ForbiddenSome index files failed to download. They have been ignored, or old ones used instead.

---

### Post by again? on 2019-01-30
To reset to default repositories:
Open software sources.
```
software-properties-gtk
```
Disable sources in the third party software tab.
[ATTACH=CONFIG]282362[/ATTACH]
Then use the following guide to reset to default sources.
Basically you move the /etc/apt/sources.list (official repos) file and then use the software-properties-gtk gui to recreate.
Your disabled third party repos will be untouched in /etc/apt/sources.list.d/ and can be re-enabled with software-properties-gtk later.
[https://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories](https://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories)
You can ignore the "Updated with inline content" section.

**PS: Code tags, man...not a wall of text...[https://ubuntuforums.org/showthread.php?t=2411319&p=13834146#post13834146](https://ubuntuforums.org/showthread.php?t=2411319&p=13834146#post13834146)**

---

### Post by yuri-weinstein on 2019-02-01
@[[COLOR=#000000]guber2[/COLOR]]("https://ubuntuforums.org/member.php?u=2063040")[COLOR=#000000] 

Thank you for your help![/COLOR]

---

