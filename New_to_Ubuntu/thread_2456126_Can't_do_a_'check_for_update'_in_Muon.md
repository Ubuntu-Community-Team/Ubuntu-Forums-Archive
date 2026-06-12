---
title: "Can't do a 'check for update' in Muon"
date: 2021-01-04
forum: New to Ubuntu
---

### Post by squill2 on 2021-01-04
Hey everyone, 

When I try to check for updates in Muon, i get an error message saying:

```
http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu/dists/groovy/Release
 404  Not Found [IP: 91.189.95.85 80]


```

when I try to do a sudo apt update, I get this:

```
[FONT=monospace][COLOR=#000000]sudo apt update [/COLOR]
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease 
Hit:2 http://deb.xanmod.org releases InRelease                                                                     
Hit:3 http://us.archive.ubuntu.com/ubuntu groovy InRelease                                                         
Hit:4 https://dl.winehq.org/wine-builds/ubuntu focal InRelease                                                     
Hit:5 http://apt.pop-os.org/proprietary groovy InRelease                                                           
Hit:6 http://us.archive.ubuntu.com/ubuntu groovy-security InRelease                                                
Hit:7 https://download.sublimetext.com apt/stable/ InRelease                              [COLOR=#b26818]                        [/COLOR][COLOR=#000000] [/COLOR]
Hit:8 http://us.archive.ubuntu.com/ubuntu groovy-updates InRelease  [COLOR=#b26818]                      [/COLOR][COLOR=#000000] [/COLOR]
Hit:9 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu groovy InRelease 
Hit:10 http://us.archive.ubuntu.com/ubuntu groovy-backports InRelease                           
Hit:11 http://repository.spotify.com stable InRelease                    [COLOR=#b26818]                      [/COLOR][COLOR=#000000] [/COLOR]
Hit:12 http://ppa.launchpad.net/lutris-team/lutris/ubuntu groovy InRelease 
Hit:13 http://ppa.launchpad.net/system76/pop/ubuntu groovy InRelease 
Ign:14 http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu groovy InRelease 
Err:15 http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu groovy Release 
  404  Not Found [IP: 91.189.95.85 80] 
Reading package lists... Done[COLOR=#b26818]                      [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]The repository 'http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu groovy Release' does not have a Relea[/COLOR]
se file. 
[COLOR=#b26818]N: [/COLOR][COLOR=#000000]Updating from such a repository can't be done securely, and is therefore disabled by default. [/COLOR]
[COLOR=#b26818]N: [/COLOR][COLOR=#000000]See apt-secure(8) manpage for repository creation and user configuration details.[/COLOR]
[/FONT]
```

Can someone help me with this? Did something I installed mess something up?

Thanks in advance!

---

### Post by deadflowr on 2021-01-05
Remove the ubuntu make ppa.
There are no archives for 20.10 in it.

---

### Post by squill2 on 2021-01-05
> **deadflowr said:**
> Remove the ubuntu make ppa.
There are no archives for 20.10 in it.

How would I do that?

---

### Post by deadflowr on 2021-01-05
> **squill2 said:**
> How would I do that?

On a server run
```
sudo add-apt-repository -r ppa:ubuntu-desktop/ubuntu-make
sudo apt update
```

On a Desktop open Software and Updates ( also known as Software Sources) go to Other Software and uncheck the ubuntu make entry.
Closing the window automatically runs the apt update.

---

### Post by ActionParsnip on 2021-01-05
[http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu/dists/)

PPA doesn't support Groovy. Not all PPAs support all releases. Please check PPAs before you add them to be sure yours is supported

---

