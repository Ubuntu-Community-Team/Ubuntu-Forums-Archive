---
title: "Package 'browser-plugin-freshplayer-pepperflash' has no installation candidate"
date: 2020-09-27
forum: New to Ubuntu
---

### Post by sosabz on 2020-09-27
I have tried [this]("https://linoxide.com/linux-how-to/install-adobe-flash-player-linux-terminal/") site instruction for installing the adobe flash browser plugin for my Ubuntu 20 as you can see here:


```

so@sosa:~$ sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"


Repository: 'deb http://archive.canonical.com/ groovy partner'
Description:
Archive for codename: groovy components: partner
More info: http://archive.canonical.com/
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.Found existing deb entry in /etc/apt/sources.list
Updating existing entry instead of using /etc/apt/sources.list.d/archive_uri-http_archive_canonical_com_-groovy.list
Found existing deb-src entry in /etc/apt/sources.list
Adding disabled deb-src entry to /etc/apt/sources.list
Get:1 http://mirror.rasanegar.com/ubuntu/archive groovy InRelease [267 kB]
Hit:2 http://mirror.rasanegar.com/ubuntu/archive groovy-updates InRelease      
Hit:3 http://mirror.rasanegar.com/ubuntu/archive groovy-backports InRelease    
Hit:4 http://mirror.rasanegar.com/ubuntu/archive groovy-security InRelease     
Get:5 http://mirror.rasanegar.com/ubuntu/archive groovy/main i386 Packages [713 kB]
Get:6 http://mirror.rasanegar.com/ubuntu/archive groovy/main amd64 Packages [965 kB]
Get:7 http://mirror.rasanegar.com/ubuntu/archive groovy/main Translation-en [506 kB]
Get:8 http://mirror.rasanegar.com/ubuntu/archive groovy/main amd64 DEP-11 Metadata [472 kB]
Get:9 http://mirror.rasanegar.com/ubuntu/archive groovy/main DEP-11 48x48 Icons [106 kB]
Get:10 http://mirror.rasanegar.com/ubuntu/archive groovy/main DEP-11 64x64 Icons [169 kB]
Get:11 http://mirror.rasanegar.com/ubuntu/archive groovy/main DEP-11 64x64@2 Icons [15.8 kB]
Get:12 http://mirror.rasanegar.com/ubuntu/archive groovy/universe amd64 Packages [8,838 kB]
Get:13 http://archive.canonical.com groovy InRelease [11.4 kB]                 
Hit:14 http://dl.google.com/linux/chrome/deb stable InRelease                  
Get:15 http://archive.canonical.com groovy/partner amd64 Packages [1,296 B]    
Get:16 http://archive.canonical.com groovy/partner Translation-en [540 B]      
Ign:17 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu groovy InRelease         
Ign:18 http://ppa.launchpad.net/fixnix/netspeed/ubuntu groovy InRelease        
Hit:19 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu groovy InRelease   
Ign:20 http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu groovy InRelease
Hit:21 https://repo.skype.com/deb stable InRelease                             
Ign:22 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu groovy InRelease   
Ign:23 http://ppa.launchpad.net/uget-team/ppa/ubuntu groovy InRelease          
Ign:24 http://ppa.launchpad.net/upubuntu-com/sdk/ubuntu groovy InRelease       
Err:25 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu groovy Release 
  404  Not Found [IP: 91.189.95.83 80]
Err:26 http://ppa.launchpad.net/fixnix/netspeed/ubuntu groovy Release
  404  Not Found [IP: 91.189.95.83 80]
Err:27 http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu groovy Release
  404  Not Found [IP: 91.189.95.83 80]
Err:28 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu groovy Release
  404  Not Found [IP: 91.189.95.83 80]
Err:29 http://ppa.launchpad.net/uget-team/ppa/ubuntu groovy Release  
  404  Not Found [IP: 91.189.95.83 80]
Err:30 http://ppa.launchpad.net/upubuntu-com/sdk/ubuntu groovy Release         
  404  Not Found [IP: 91.189.95.83 80]
Get:31 http://mirror.rasanegar.com/ubuntu/archive groovy/universe i386 Packages [4,705 kB]
Get:32 http://mirror.rasanegar.com/ubuntu/archive groovy/universe Translation-en [5,260 kB]
Err:33 http://ftp.osuosl.org/pub/mariadb/repo/10.0/ubuntu precise InRelease    
  Temporary failure resolving ‘ftp.osuosl.org’
Get:34 http://mirror.rasanegar.com/ubuntu/archive groovy/universe amd64 DEP-11 Metadata [3,702 kB]
Get:35 http://mirror.rasanegar.com/ubuntu/archive groovy/universe DEP-11 48x48 Icons [3,136 kB]
Get:36 http://mirror.rasanegar.com/ubuntu/archive groovy/universe DEP-11 64x64 Icons [7,865 kB]
Get:37 http://mirror.rasanegar.com/ubuntu/archive groovy/universe DEP-11 64x64@2 Icons [43.3 kB]
Get:38 http://mirror.rasanegar.com/ubuntu/archive groovy/universe amd64 c-n-f Metadata [271 kB]
Get:39 http://mirror.rasanegar.com/ubuntu/archive groovy/multiverse amd64 DEP-11 Metadata [44.4 kB]
Get:40 http://mirror.rasanegar.com/ubuntu/archive groovy/multiverse DEP-11 48x48 Icons [28.3 kB]
Get:41 http://mirror.rasanegar.com/ubuntu/archive groovy/multiverse DEP-11 64x64 Icons [170 kB]
Get:42 http://mirror.rasanegar.com/ubuntu/archive groovy/multiverse DEP-11 64x64@2 Icons [214 B]
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/deadsnakes/ppa/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/fixnix/netspeed/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/uget-team/ppa/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/upubuntu-com/sdk/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


so@sosa:~$ sudo apt-get update
0% [Working]
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease                 
Get:2 http://ftp.osuosl.org/pub/mariadb/repo/10.0/ubuntu precise InRelease [2,489 B]
Err:2 http://ftp.osuosl.org/pub/mariadb/repo/10.0/ubuntu precise InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBCB082A1BB943DB
Ign:3 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu groovy InRelease  
Ign:4 http://ppa.launchpad.net/fixnix/netspeed/ubuntu groovy InRelease         
Hit:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu groovy InRelease    
Ign:6 http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu groovy InRelease
Ign:7 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu groovy InRelease    
Ign:8 http://ppa.launchpad.net/uget-team/ppa/ubuntu groovy InRelease           
Ign:9 http://ppa.launchpad.net/upubuntu-com/sdk/ubuntu groovy InRelease        
Err:10 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu groovy Release           
  404  Not Found [IP: 91.189.95.83 80]
Err:11 http://ppa.launchpad.net/fixnix/netspeed/ubuntu groovy Release          
  404  Not Found [IP: 91.189.95.83 80]
Err:12 http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu groovy Release
  404  Not Found [IP: 91.189.95.83 80]
Err:13 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu groovy Release     
  404  Not Found [IP: 91.189.95.83 80]
Err:14 http://ppa.launchpad.net/uget-team/ppa/ubuntu groovy Release            
  404  Not Found [IP: 91.189.95.83 80]
Err:15 http://ppa.launchpad.net/upubuntu-com/sdk/ubuntu groovy Release         
  404  Not Found [IP: 91.189.95.83 80]
Hit:16 http://mirror.rasanegar.com/ubuntu/archive groovy InRelease             
Hit:17 http://mirror.rasanegar.com/ubuntu/archive groovy-updates InRelease     
Hit:18 http://mirror.rasanegar.com/ubuntu/archive groovy-backports InRelease   
Hit:19 http://mirror.rasanegar.com/ubuntu/archive groovy-security InRelease    
Hit:20 http://archive.canonical.com groovy InRelease                   
Err:21 https://repo.skype.com/deb stable InRelease     
  Temporary failure resolving ‘repo.skype.com’
Reading package lists... Done    
W: GPG error: http://ftp.osuosl.org/pub/mariadb/repo/10.0/ubuntu precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBCB082A1BB943DB
E: The repository 'http://ftp.osuosl.org/pub/mariadb/repo/10.0/ubuntu precise InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/deadsnakes/ppa/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/fixnix/netspeed/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/uget-team/ppa/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/upubuntu-com/sdk/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
so@sosa:~$ 
```

and get this error:
```


so@sosa:~$ sudo apt install adobe-flashplugin browser-plugin-freshplayer-pepperflash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package browser-plugin-freshplayer-pepperflash is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'browser-plugin-freshplayer-pepperflash' has no installation candidate
so@sosa:~$ ^C



```

My OS Version is:
```

so@sosa:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Groovy Gorilla (development branch)
Release:	20.10
Codename:	groovy




```

Thanks for your attention.

---

### Post by ajgreeny on 2020-09-27
Flash is just about dead and very nearly buried.

Is there a specific site you visit that still requires flash instead of html5, which most websites now use?
If so you may be able to get flash by installing flashplugin-installer, though using 20.10, you may still be unlucky as that version has not yet been released.  There is a 20.04 version so you may do better with that version of Ubuntu but I suggest you forget about using flash and move on.

---

### Post by Impavidus on 2020-09-27
You posted in New to Ubuntu, suggesting you're new. Ubuntu 20.10 hasn't been released yet, so new users are recommended to stay away. Actually, even after release, new users are recommended to stay with the latest LTS release, which is 20.04.

You've got a lot of PPAs installed and many of those give errors. Not really surprising, as you're running the development version of Ubuntu. I prefer to keep PPAs to a minimum (usually 0).

There's no need to add the partner repository. It's already there in the software sources, you only have to enable it. Click the checkbox in the GUI or remove the hash sign in /etc/apt/sources.list.

And indeed, flash is all but gone. Three more months before Adobe officially pulls the plug. Anyone who by then still runs a website depending on flash deserves to get no more visitors.

---

### Post by scorp123 on 2020-09-27
> **sosabz said:**
> I have tried [this]("https://linoxide.com/linux-how-to/install-adobe-flash-player-linux-terminal/") site instruction for installing the adobe flash browser plugin for my Ubuntu 20 as you can see here ... 

Why would you want to install that dead piece of software?? Adobe Flash is as good as dead. 

Official announcement:
[https://www.adobe.com/products/flashplayer/end-of-life.html]("https://www.adobe.com/products/flashplayer/end-of-life.html")

Quote from there:
> As previously announced in July 2017, Adobe will stop distributing and updating Flash Player after December 31, 2020 (&#8220;EOL Date&#8221;). 
[... ]
Adobe will be removing Flash Player download pages from its site and Flash-based content will be blocked from running in Adobe Flash Player after the EOL Date.

If you really really still need Flash for some reasons then you could try using **Google Chrome**. Google Chrome still comes with its own built-in Flash player that does not depend on external software. But per default it is turned off. You need to turn it on and allow the web site to use it. Official instructions here:
[https://support.google.com/chrome/answer/6258784?co=GENIE.Platform%3DDesktop&hl=en]("https://support.google.com/chrome/answer/6258784?co=GENIE.Platform%3DDesktop&hl=en")

But please be aware that Google too could also decide to stop supporting Flash at any moment. So this is a temporary solution at best, it's only a question of time until this workaround will also stop working.
[https://www.blog.google/products/chrome/saying-goodbye-flash-chrome/]("https://www.blog.google/products/chrome/saying-goodbye-flash-chrome/")

---

### Post by deadflowr on 2020-09-27
The pepperflash/freshplayer package was removed for groovy.
Makes sense. As already stated it's going EOL at the end of the year.
> You've got a lot of PPAs installed and many of those give errors. Not really surprising, as you're running the development version of Ubuntu. I prefer to keep PPAs to a minimum (usually 0).

Indeed.
Not a lot of PPAs add support for development releases.
They usually wait until a release comes out.
(This is usually because there are too many unknowns during the development cycle.
It's hard keeping up with a moving target)

I'd recommend disabling them all.

(also, looking at just  a couple of the PPAs for the apt update listing, some seem to be dead, either recently dead or very dead.)

---

### Post by Frogs Hair on 2020-09-27
You can get adobe flash in 2010 , but as stated it goes end of life in January. Odly many sites still require it with just months to go.

Pepper flash is also available though you may have to enable the canonical partners repository in software sources.

---

### Post by deadflowr on 2020-09-27
> **Frogs Hair said:**
> You can get adobe flash in 2010 , but as stated it goes end of life in January. Odly many sites still require it with just months to go.

Pepper flash is also available though you may have to enable the canonical partners repository in software sources.

Looking at it, once they fix the broken PPAs adobe-flashplugin should install without any problems,
but the pepperflash-freshplayer plugin is gone.

And I really don't see what it's purpose would even be anymore,
since it was initially there to provide an updated flash plugin for firefox when the version at the time was stuck at flash 11.
(Flash on Firefox was moved up eventually so it now runs the same version as pepperflash does)

Thinking about it the only real need for freshplayer is if you pull the flashplugin from ChromeOS,
since that is the only flash for linux version that supports drm, so there is that, I guess.
But if that's the case I'd reinstall 20.04 since the package exists there.

---

