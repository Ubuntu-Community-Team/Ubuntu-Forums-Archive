---
title: "Update warning 15.04"
date: 2015-08-28
forum: New to Ubuntu
---

### Post by Craig_Price on 2015-08-28
Hi,

I'm a newbie and a bit lost so I'm hoping someone can take a deep breath and look kindly past my lack of knowledge! I've been using 15.04 for a couple of weeks now and over the last week I've started seeing a red warning icon in the top right where the time in displayed. I'm a Windows escapee and I know it as the system tray.

Anyway, it says the update information is outdated which might be caused by network problems or a repository which is no longer available. It also says to update manually by selecting 'Show Updates' from the menu and watch for any failing repositories. When I do it says my computer is up to date but being more used to Windows seeing the warning icon is a bit worrying.

I did try to install f.lux via the terminal to discover on this forum that it's not supported in 15.04 and that might be what started this off. I don't know what repositories are but I've gone through my installations in the software centre and I can't see a way to delete the stuff downloaded for f.lux. Is there a way to undo this operation or is the update warning something else? Like I say, it's just a bit worrying running a computer with a warning showing.

Thanks,

Craig

---

### Post by v3.xx on 2015-08-28
Ok, lets see whats going on :)  Please post the output of ..

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

Edit, also

```
sudo apt-get update
```

---

### Post by Craig_Price on 2015-08-28
Hi,

Thanks for your post, I really appreciate it.

I put the first one in the terminal, is that the place to go?

Anyway, I got this:

```
# deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
/etc/apt/sources.list.d/kilian-ubuntu-f_lux-vivid.list
```

Then the sudo get update:

```
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid InRelease                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid Release.gpg                              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates InRelease                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid Release                                  
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates Release.gpg [933 B]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid Release                                 
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates Release [63.5 kB]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security InRelease                        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release.gpg [933 B]            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release [63.5 kB]              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en                         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Sources [38.8 kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Sources [28 B]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/main Sources [78.5 kB]
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/restricted Sources [1,366 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Sources [15.9 kB]     
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/universe Sources [35.8 kB]   
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/multiverse Sources [1,966 B] 
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/main amd64 Packages [185 kB] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Sources [1,966 B]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/restricted amd64 Packages [3,283 B]
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/universe amd64 Packages [99.8 kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main amd64 Packages [108 kB] 
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/multiverse amd64 Packages [3,496 B]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/main i386 Packages [183 kB]  
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted amd64 Packages [28 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe amd64 Packages [51.9 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse amd64 Packages [3,496 B]
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/restricted i386 Packages [3,273 B]
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/universe i386 Packages [99.9 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main i386 Packages [107 kB]   
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted i386 Packages [28 B]
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/multiverse i386 Packages [3,680 B]
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/main Translation-en [89.7 kB]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe i386 Packages [51.9 kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse i386 Packages [3,680 B]
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/universe Translation-en [58.0 kB]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Translation-en [56.8 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/multiverse Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/main amd64 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/main Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/main Translation-en    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/multiverse Translation-en_GB
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Translation-en [32.4 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/multiverse Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/restricted Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates/restricted Translation-en
Fetched 1,448 kB in 12s (119 kB/s)                                             
W: Failed to fetch [http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/kilian/f.lux/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Thanks,
Craig

---

### Post by v3.xx on 2015-08-28
Ok, an easy fix :)

Remove that ppa and all should be well.  Do this with software sources.

```
software-properties-gtk
```

---

### Post by v3.xx on 2015-08-28
I don't know if this is needed, but ..

[http://askubuntu.com/questions/43345/how-to-remove-a-repository](http://askubuntu.com/questions/43345/how-to-remove-a-repository)

---

### Post by Craig_Price on 2015-08-28
Hi,

Thanks, I found it and removed the tick so hopefully that's sorted now.

I really appreciate your help with this, I think it's a great lesson in being careful with the terminal and sticking to the proper software store. It's a huge relief to be honest.

What an amazing OS though! I love it!

Thanks,

Craig

---

### Post by v3.xx on 2015-08-28
And welcome to the forums :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Craig_Price on 2015-08-28
> **v3.xx said:**
> I don't know if this is needed, but ..

[http://askubuntu.com/questions/43345/how-to-remove-a-repository](http://askubuntu.com/questions/43345/how-to-remove-a-repository)

Great thanks! It's all making sense now. I think I might just get there with Ubuntu!

Thanks again,

Craig

---

### Post by Craig_Price on 2015-08-28
Nice one, thanks again!

---

### Post by Bucky Ball on 2015-08-28
If you haven't already, in a terminal, these commands. These commands will not upgrade your release to a newer one, only the software in the one you're running:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

If those commands run without error you are good to go and you could mark the thread as solved (see first link in my signature). If not, post the error(s).  :)

---

