---
title: "Can't install any dev packages"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by willigan1 on 2008-04-29
Hi -
This is my first post but I have received a lot of help from the community.  Hopefully I learn enough to help someone else someday.

What my problem is I have done a fresh Hardy install (kept my home partition don't know if this could cause this).  I have been trying to compile some apps from source but cannot install any of the dev packages to do so.  

Example: Kiba-Dock

Dependencies are

```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev subversion
```

Instalation returns:

```

willigan@willigan-desktop:~$ sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev subversion
[sudo] password for willigan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
subversion is already the newest version.
libcairo2 is already the newest version.
libgtop2-7 is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnomeui-0 is already the newest version.
librsvg2-2 is already the newest version.
libgstreamer0.10-0 is already the newest version.
subversion is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgconf2-dev: Depends: gconf2 (= 2.22.0-0ubuntu2) but 2.22.0-0ubuntu3 is to be installed
                 Depends: libgconf2-4 (= 2.22.0-0ubuntu2) but 2.22.0-0ubuntu3 is to be installed
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.12.9-2ubuntu2) but 2.12.9-3ubuntu2 is to be installed
  python-gtk2-dev: Depends: python-dev but it is not going to be installed
                   Depends: python-gobject-dev (>= 2.14) but it is not going to be installed
E: Broken packages

```

I've tried installing the packages through the terminal and synaptic and keeps coming back saying that the version "is to be installed".  I've read a lot of posts on similar situations and most just say the universe and multiverse need to be enabled which I believe they are.

```
willigan@willigan-desktop:~$ sudo apt-get update
[sudo] password for willigan: 
Hit http://archive.ubuntu-rocks.org hardy Release.gpg
Ign http://archive.ubuntu-rocks.org hardy/main Translation-en_US               
Ign http://archive.ubuntu-rocks.org hardy/restricted Translation-en_US         
Ign http://archive.ubuntu-rocks.org hardy/universe Translation-en_US           
Ign http://archive.ubuntu-rocks.org hardy/multiverse Translation-en_US         
Hit http://archive.ubuntu-rocks.org hardy-updates Release.gpg                  
Ign http://archive.ubuntu-rocks.org hardy-updates/main Translation-en_US       
Ign http://archive.ubuntu-rocks.org hardy-updates/restricted Translation-en_US 
Ign http://archive.ubuntu-rocks.org hardy-updates/universe Translation-en_US   
Ign http://archive.ubuntu-rocks.org hardy-updates/multiverse Translation-en_US 
Hit http://archive.ubuntu-rocks.org hardy-security Release.gpg                 
Ign http://archive.ubuntu-rocks.org hardy-security/main Translation-en_US      
Ign http://archive.ubuntu-rocks.org hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu-rocks.org hardy-security/universe Translation-en_US  
Ign http://archive.ubuntu-rocks.org hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu-rocks.org hardy Release                              
Hit http://archive.ubuntu-rocks.org hardy-updates Release                      
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://archive.ubuntu-rocks.org hardy-security Release                     
Hit http://archive.ubuntu-rocks.org hardy/main Packages                        
Hit http://archive.ubuntu-rocks.org hardy/restricted Packages                  
Hit http://archive.ubuntu-rocks.org hardy/restricted Sources                   
Hit http://archive.ubuntu-rocks.org hardy/main Sources                         
Hit http://archive.ubuntu-rocks.org hardy/multiverse Sources                   
Hit http://archive.ubuntu-rocks.org hardy/universe Sources                     
Hit http://archive.ubuntu-rocks.org hardy/universe Packages                    
Hit http://archive.ubuntu-rocks.org hardy/multiverse Packages                  
Hit http://archive.ubuntu-rocks.org hardy-updates/main Packages                
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://archive.ubuntu-rocks.org hardy-updates/restricted Packages          
Hit http://archive.ubuntu-rocks.org hardy-updates/restricted Sources           
Hit http://archive.ubuntu-rocks.org hardy-updates/main Sources                 
Hit http://archive.ubuntu-rocks.org hardy-updates/multiverse Sources           
Hit http://archive.ubuntu-rocks.org hardy-updates/universe Sources             
Get:1 http://wine.budgetdedicated.com hardy Release.gpg [191B]                 
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Hit http://archive.ubuntu-rocks.org hardy-updates/universe Packages            
Hit http://archive.canonical.com hardy Release                                 
Hit http://archive.ubuntu.com hardy Release.gpg                                
Hit http://archive.ubuntu-rocks.org hardy-updates/multiverse Packages          
Hit http://archive.ubuntu-rocks.org hardy-security/main Packages               
Hit http://archive.ubuntu-rocks.org hardy-security/restricted Packages         
Hit http://archive.ubuntu-rocks.org hardy-security/restricted Sources          
Hit http://archive.ubuntu-rocks.org hardy-security/main Sources                
Hit http://archive.ubuntu-rocks.org hardy-security/multiverse Sources          
Hit http://archive.ubuntu-rocks.org hardy-security/universe Sources            
Hit http://archive.ubuntu-rocks.org hardy-security/universe Packages           
Hit http://archive.ubuntu-rocks.org hardy-security/multiverse Packages         
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://archive.canonical.com hardy/partner Packages                        
Get:3 http://wine.budgetdedicated.com hardy Release [1013B]          
Ign http://wine.budgetdedicated.com hardy Release                              
Hit http://archive.ubuntu.com hardy Release                                    
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://archive.canonical.com hardy/partner Sources               
Ign http://wine.budgetdedicated.com hardy/main Packages              
Hit http://archive.ubuntu.com hardy/main Sources                     
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://wine.budgetdedicated.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Fetched 193B in 1s (133B/s)
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
```

I hope this makes sense to someone (I'm very new to all this) because I don't seem to be getting anywhere.

Thanks for any help.

Willigan

---

### Post by spiderbatdad on 2008-04-29
It appears the last two dependencies are not to be installed because they are broken. Have you tried ```
sudo apt-get install -f
``` or going to synaptic and fixing broken packages (under the edit menu, I believe)?

It may be that those libs are no longer used. I don't know. I haven't heard anyone running kiba-dock on compiz-fusion in Hardy. It was big (and I used it for a while) back in Beryl times. Perhaps checkout AWN if you can't resolve the dependencies.

---

### Post by willigan1 on 2008-04-29
Thanks for the reply.  I tried both or your suggestions with no luck.  As for a dock I'll probably stick with AWN.  Was just gonna try something different.  

But I still have the problem of not being able to install dev packages.  I came across the same problem trying to set up btnx with [this tutorial]("http://cad.cx/blog/2008/04/25/howto-install-btnx-for-better-mouse-control-in-ubuntu-hardy/").  When trying to install libgtk2.0-dev I get:

```
willigan@willigan-desktop:~$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.12.9-2ubuntu2) but 2.12.9-3ubuntu2 is to be installed
E: Broken packages

```

---

