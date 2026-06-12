---
title: "cant update, ubuntone errors - 11.04"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by iconmaroon on 2012-10-02
Hi all

Recently I've had trouble updating Ubuntu 11.04. The problem is that I cannot install the updates, the installer can't find files. These files actually exist as I have looked them up.

How do I fix the problem and install the updates successfully?

Below is the terminal output of the errors:

meenee@meenee-laptop ~ $ sudo apt-get update
[sudo] password for meenee: 
Ign file: binary/ InRelease
Ign file: binary/ Release.gpg                                                  
Ign file: binary/ Release                                                      
Ign file: binary/ Translation-en_GB                                            
Ign file: binary/ Translation-en                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release                            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources/DiffIndex                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages/DiffIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick InRelease                                
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) katya Release.gpg [197 B]                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse i386 Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex                
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse i386 Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_GB                 
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg [489 B]                    
Get:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) katya Release [16.5 kB]                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Get:4 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release [2,605 B]                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_GB               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Get:5 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages [1,029 B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_GB             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Get:6 [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/main i386 Packages [8,581 B]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main TranslationIndex                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:7 [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/upstream i386 Packages [16.0 kB]     
Get:8 [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/import i386 Packages [5,944 B]       
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/import TranslationIndex                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/main TranslationIndex        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/upstream TranslationIndex    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_GB                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_GB
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en_GB                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/import Translation-en_GB
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/import Translation-en
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/main Translation-en_GB
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/main Translation-en
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/upstream Translation-en_GB
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) katya/upstream Translation-en
Fetched 51.3 kB in 4s (10.3 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
meenee@meenee-laptop ~ $ sudo dpg --configure -a
sudo: dpg: command not found
[B]meenee@meenee-laptop ~ $ sudo dpkg --configure -a
Setting up libdbus-1-3 (1.4.6-1ubuntu6.2) ...
Setting up python-support (1.0.10ubuntu3) ...
Sorry [Errno 6] No such device or address: '/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_notifications.pyc'
Sorry [Errno 6] No such device or address: '/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/fsm/__init__.pyc'
Sorry [Errno 6] No such device or address: '/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/fsm/fsm_draw.pyc'
Sorry [Errno 6] No such device or address: '/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interfaces.pyc'[/B]

---

### Post by 2F4U on 2012-10-03
Not sure where and how you are looking, but at least these two no longer exist

> W: Failed to fetch [http://ppa.launchpad.net/mozillateam...source/Sources]("http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/natty/main/source/Sources")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam...-i386/Packages]("http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/natty/main/binary-i386/Packages")  404  Not Found

and it is probably best to remove them.

---

### Post by iconmaroon on 2012-10-03
What does the installer mean when it says it can't find those files? It's telling downright lies as these files do exist. Is there any way of fixing it as I have to quit the terminal in the end as it does nothing in the end. I can't open Synaptic or install any software, or update the system obviously!

ETA: I've kicked the old Mozilla email update sources too.

---

### Post by iconmaroon on 2012-10-03
ETA - again: When I shut the terminal down and relaunch the update process, I get another error about a lock.

TERMINAL OUTPUT:

Fetched 1,282 kB in 8s (157 kB/s)                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by cway00 on 2012-10-03
> **iconmaroon said:**
> ETA - again: When I shut the terminal down and relaunch the update process, I get another error about a lock.

TERMINAL OUTPUT:

Fetched 1,282 kB in 8s (157 kB/s)                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Trying shutting down and booting in recovery mode and also try to repair broken packages and other stuffs from recovery mode..hope it helps

---

### Post by newb85 on 2012-10-03
Those files all appear to be associated with the UbuntuOne client(specifically, the python modules), so I would try reinstalling.

```
sudo apt-get remove python-ubuntuone-client
```

Pay attention to what all is being removed with it, and make sure you reinstall all those packages.

Before reinstalling, check to see if those "missing" files are still there.

---

### Post by NikTh on 2012-10-03
Hi , 

I can see you have multiple mistakes in your sources.list file. 

First with mozilla , corrected OK , but I can see these 

> **iconmaroon said:**
> 
```
Ign file: binary/ InRelease
Ign file: binary/ Release.gpg                                                  
Ign file: binary/ Release                                                      
Ign file: binary/ Translation-en_GB                                            
Ign file: binary/ Translation-en                                               
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg [489 B]                    
Get:4 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release [2,605 B]                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
  404  Not Found
Get:5 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages [1,029 B]           
I
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main TranslationIndex                    

```

Can you post the results of this command ? 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
```Please put the results between the brackets so can be readable **[noparse]```
Here
```[/noparse]**

Thanks

---

### Post by iconmaroon on 2012-10-03
Here's the output of  $ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; below:

meenee@meenee-laptop ~ $ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/dockbar-main-ppa-natty.list

     1    # deb [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu) natty main

/etc/apt/sources.list.d/kubuntu-ppa-beta-natty.list

     1    # deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) natty main

/etc/apt/sources.list.d/libreoffice-libreoffice-3--natty.list


/etc/apt/sources.list.d/screenlets-ppa-natty.list

     1    # deb [http://ppa.launchpad.net/screenlets/ppa/ubuntu](http://ppa.launchpad.net/screenlets/ppa/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/screenlets/ppa/ubuntu](http://ppa.launchpad.net/screenlets/ppa/ubuntu) natty main

/etc/apt/sources.list.d/libreoffice-libreoffice-3-5-natty.list

     1    # deb [http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu) natty main

/etc/apt/sources.list.d/google-talkplugin.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

/etc/apt/sources.list.d/szymonw-ppa-natty.list

     1    deb [http://ppa.launchpad.net/szymonw/ppa/ubuntu](http://ppa.launchpad.net/szymonw/ppa/ubuntu) natty main
     2    deb-src [http://ppa.launchpad.net/szymonw/ppa/ubuntu](http://ppa.launchpad.net/szymonw/ppa/ubuntu) natty main

/etc/apt/sources.list.d/local-repository.list

     1    deb file:///usr/share/local-repository binary/
     2    

/etc/apt/sources.list.d/libreoffice-ppa-natty.list

     1    # deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) natty main

/etc/apt/sources.list.d/playdeb.list

     1    # deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) katya-getdeb games

/etc/apt/sources.list.d/andy753421-aweather-natty.list

     1    # deb [http://ppa.launchpad.net/andy753421/aweather/ubuntu](http://ppa.launchpad.net/andy753421/aweather/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/andy753421/aweather/ubuntu](http://ppa.launchpad.net/andy753421/aweather/ubuntu) natty main

/etc/apt/sources.list.d/gandalf-pspp-natty.list

     1    # deb [http://ppa.launchpad.net/gandalf/pspp/ubuntu](http://ppa.launchpad.net/gandalf/pspp/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/gandalf/pspp/ubuntu](http://ppa.launchpad.net/gandalf/pspp/ubuntu) natty main

/etc/apt/sources.list.d/mixxx-mixxx-natty.list

     1    # deb [http://ppa.launchpad.net/mixxx/mixxx/ubuntu](http://ppa.launchpad.net/mixxx/mixxx/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/mixxx/mixxx/ubuntu](http://ppa.launchpad.net/mixxx/mixxx/ubuntu) natty main

/etc/apt/sources.list.d/mozillateam-thunderbird-stable-natty.list

     1    # deb [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu) natty main

/etc/apt/sources.list.d/kubuntu-ppa-backports-natty.list

     1    # deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) natty main
     2    # deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) natty main

/etc/apt/sources.list.d/dropbox.list

     1    deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) maverick main

/etc/apt/sources.list

     1    deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) katya main upstream import
     2    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty main restricted universe multiverse
     3    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates main restricted universe multiverse
     4    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse
     5    deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty partner
     6    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
     7    deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
     8    
     9    # deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
    10    # deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
meenee@meenee-laptop ~ $ 

I'll remove Ubuntu One and reinstall to see what happens. I have the lock file error cleared after restarting, so that's one sorted!

Thanks for all the help so far, it's much appreciated.

---

### Post by iconmaroon on 2012-10-03
When I try to get rid of Ubuntu One the same old problem comes back and I get stuck in the endless Python/UbuntuOne loop:

meenee@meenee-laptop ~ $ sudo apt-get purge ubuntuone\*
[sudo] password for meenee: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
meenee@meenee-laptop ~ $ 

If I follow the instructions it gives me I just go back to the original fault.

---

### Post by NikTh on 2012-10-03
In your position I would do .. 

```
sudo rm  /etc/apt/sources.list.d/local-repository.list
sudo rm  /etc/apt/sources.list.d/dropbox.list
```Then 
```
sudo apt-get -qq update 
sudo apt-get install -f 
sudo apt-get autoremove 
sudo apt-get clean all
sudo apt-get dist-upgrade
sudo dpkg --configure -a
```My opinion is that some of the many PPAs you have added caused this fault. I don't know which of , but so many ext.PPAs can cause such problems with packages.

Also maybe its time to consider a Version upgrade cuz Ubuntu 11.04 will E.O.L in a few days , so no support will exists.

Thanks

---

### Post by iconmaroon on 2012-10-03
Yes I forgot about that - I might actually do that from a clean install as that will most likely solve both problems. Should I mark this as solved?

---

### Post by NikTh on 2012-10-03
If you decided to upgrade to a newer version of Ubuntu , then yes mark the thread as solved. 

Fresh installation is the best way , I agree.

---

### Post by iconmaroon on 2012-10-03
Upgrading is a Very Bad Idea - I did that once before many moons ago with 9.X and oh dear me! Ever since then it's been clean install every time. I've marked it as solved.

Thanks for all your help :KS

---

