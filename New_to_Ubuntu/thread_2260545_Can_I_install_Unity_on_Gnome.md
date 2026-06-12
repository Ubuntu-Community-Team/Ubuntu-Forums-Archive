---
title: "Can I install Unity on Gnome?"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by anbu-s on 2015-01-12
I tried to install ubuntu-desktop on my gnome ubuntu 14.04LTS and got the following error msg:

anbu@Terminatore:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: ubuntu-session but it is not going to be installed
                  Depends: unity-control-center but it is not going to be installed
                  Depends: unity-settings-daemon but it is not going to be installed
                  Recommends: xul-ext-webaccounts but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

What can i do to fix this? - I'm new to ubuntu - so please pardon my ignorance

---

### Post by prestotron7 on 2015-01-12
An easy way to do this is simply by opening a Terminal (Ctrl + T)

Then type the following: sudo apt-get install ubuntu-desktop

It'll ask you to type a password, and press enter after you have done so. (remember, passwords dont show as you type them)

Then, reboot and before you are allowed to login (enter the password, and if you do not have one, it'll prompt you), it will ask you to choose between Gnome and Unity.

Cheers,
Preston Cammarata
- Computer and Software Engineer

---

### Post by Bucky Ball on 2015-01-12
> **prestotron7 said:**
> An easy way to do this is simply by opening a Terminal (Ctrl + T)

Then type the following: sudo apt-get install ubuntu-desktop



This is exactly what the OP has done and they are getting the error they report. That command is in the first line of their posted terminal output. ;)

@anbu-s: Did you want the whole ubuntu-desktop? That pretty much equates to installing a full Ubuntu and ALL its defaults, i.e. apps, dependencies, window managers, sceensaver, etc. etc. This can cause unwanted bloat, duplication and redundancy.

Why not just install Unity if you only want to try that desktop environment? You can do that with Software Centre, Synaptics or the terminal. Once installed, log out, choose the Unity session from the Sessions pop-up, log in. ;)

PS: You can use this method for other DEs also. xfce4 will install the Xubuntu DE, lxde the Lubuntu DE, etc. Good luck.

---

### Post by anbu-s on 2015-01-13
> **Bucky Ball said:**
> This is exactly what the OP has done and they are getting the error they report. That command is in the first line of their posted terminal output. ;)

@anbu-s: Did you want the whole ubuntu-desktop? That pretty much equates to installing a full Ubuntu and ALL its defaults, i.e. apps, dependencies, window managers, sceensaver, etc. etc. This can cause unwanted bloat, duplication and redundancy.

Why not just install Unity if you only want to try that desktop environment? You can do that with Software Centre, Synaptics or the terminal. Once installed, log out, choose the Unity session from the Sessions pop-up, log in. ;)

PS: You can use this method for other DEs also. xfce4 will install the Xubuntu DE, lxde the Lubuntu DE, etc. Good luck.

I don't want the whole ubuntu- desktop . I just want the unity desktop. I nstalled unity 8 from software centre. After install i logged out and tried to log back in with unity settings. but it doesnt appear in the list. I only have gnome, system default and gnome classic. How do i get this listed as an option? I looked around tweak tools and settings menu - nothing seem to be there in regards to this.

---

### Post by Bucky Ball on 2015-01-13
Hmm, odd. Should be there. What do you get with:

```
sudo apt-get install unity
```

? Tell us if it says anything other than 'newest version already installed'. Perhaps try a complete reboot rather than logging out, then 'Sessions' when you get to the login screen. Any different?

---

### Post by plucky on 2015-01-13
> E: Unable to correct problems, you have held broken packages.

What can i do to fix this? - I'm new to ubuntu - so please pardon my ignorance 
You need to fix this problem first.

Open a terminal and

What does ```
sudo apt-get install -f
``` show you?

Good Luck

Nevermind I see you have already done this [http://ubuntuforums.org/showthread.php?t=2260517](http://ubuntuforums.org/showthread.php?t=2260517)

---

### Post by Bucky Ball on 2015-01-13
As plucky mentions. Seems like you fixed it in the link they provided.

So, try:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install unity
```

Any different now? If not, report any and all errors.

---

### Post by grahammechanical on 2015-01-13
> [COLOR=#000000]I nstalled unity 8 from software centre. [/COLOR]

That is only complicating matters. Did you also install unity8-desktop-session-mir? Without that we will not get a Unity8 login screen option. Besides, at the moment the Unity 8 session is still the Ubuntu phone user interface. We get a few phone apps such as the Music app, which is very nice and would be even better when it is modified to import audio files from other partitions.

Ubuntu+Unity uses unity-control-center which is a fork of gnome-control-center. I am not sure if the two can co-exist. Perhaps they cannot co-exist and that is why unity-control-center and the other stuff is not being installed. Maybe.

Regards

---

### Post by anbu-s on 2015-01-13
> **Bucky Ball said:**
> As plucky mentions. Seems like you fixed it in the link they provided.

So, try:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install unity
```

Any different now? If not, report any and all errors.

Still no luck. please find all the messages from terminal when i executed these commands

```
anbu@Terminatore:~$ sudo apt-get update
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy InRelease
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat InRelease          
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty InRelease                              
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy/main amd64 Packages                
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release                                    
Hit [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy/main i386 Packages                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main amd64 Packages                        
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB]             
Get:3 [https://download.01.org](https://download.01.org) trusty InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [https://download.01.org](https://download.01.org) trusty InRelease                                   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main i386 Packages                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:4 [https://download.01.org](https://download.01.org) trusty/main amd64 Packages/DiffIndex             
Ign [https://download.01.org](https://download.01.org) trusty/main amd64 Packages/DiffIndex               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main i386 Packages 
Ign [https://download.01.org](https://download.01.org) trusty/main i386 Packages/DiffIndex                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release.gpg                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [192 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release [62.0 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release                      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [8,875 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main amd64 Packages                    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [82.2 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy/main Translation-en_CA             
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy/main Translation-en                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe amd64 Packages                
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [1,157 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages                     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [183 kB]  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_CA                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages                 
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en                    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [82.2 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,409 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en              
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [97.0 kB]
Hit [https://download.01.org](https://download.01.org) trusty/main amd64 Packages                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [https://download.01.org](https://download.01.org) trusty/main i386 Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA             
Get:18 [https://download.01.org](https://download.01.org) trusty/main Translation-en_CA                   
Ign [https://download.01.org](https://download.01.org) trusty/main Translation-en_CA                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en                
Ign [https://download.01.org](https://download.01.org) trusty/main Translation-en                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main amd64 Packages [396 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [12.7 kB]           
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [12.7 kB]            
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [8,875 B]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe amd64 Packages [236 kB]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [9,370 B]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages [388 kB] 
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [4,477 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages [8,846 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages [237 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,553 B]
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en [187 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en_CA           
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en_CA           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Fetched 2,310 kB in 11s (196 kB/s)                                             
W: GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: Failed to fetch [http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found 
Some index files failed to download. They have been ignored, or old ones used instead.
anbu@Terminatore:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  highlight highlight-common libcryptui0a liblua5.1-0 seahorse-daemon
  signon-keyring-extension wine-compholio wine-compholio-amd64
  wine-compholio-i386:i386
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libyaml-0-2 python-yaml
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 150 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main libyaml-0-2 amd64 0.1.4-3ubuntu3.1 [48.1 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates/main python-yaml amd64 3.10-4ubuntu0.1 [102 kB]
Fetched 150 kB in 0s (187 kB/s)      
(Reading database ... 414998 files and directories currently installed.)
Preparing to unpack .../libyaml-0-2_0.1.4-3ubuntu3.1_amd64.deb ...
Unpacking libyaml-0-2:amd64 (0.1.4-3ubuntu3.1) over (0.1.4-3ubuntu3) ...
Preparing to unpack .../python-yaml_3.10-4ubuntu0.1_amd64.deb ...
Unpacking python-yaml (3.10-4ubuntu0.1) over (3.10-4build4) ...
Setting up libyaml-0-2:amd64 (0.1.4-3ubuntu3.1) ...
Setting up python-yaml (3.10-4ubuntu0.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

anbu@Terminatore:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  highlight highlight-common libcryptui0a liblua5.1-0 seahorse-daemon
  signon-keyring-extension wine-compholio wine-compholio-amd64
  wine-compholio-i386:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anbu@Terminatore:~$ sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity is already the newest version.
The following packages were automatically installed and are no longer required:
  highlight highlight-common libcryptui0a liblua5.1-0 seahorse-daemon
  signon-keyring-extension wine-compholio wine-compholio-amd64
  wine-compholio-i386:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anbu@Terminatore:~$
```

---

### Post by anbu-s on 2015-01-13
Some more info..
If i type "unity" in the terminal, it switches to unity desktop. So it seems like it has been installed. But the option doesn't show up in the login screen

---

### Post by mc4man on 2015-01-13
> **anbu-s said:**
> I don't want the whole ubuntu- desktop . I just want the unity desktop. I nstalled [COLOR="#FF0000"]unity 8 from software centre[/COLOR]. After install i logged out and tried to log back in with unity settings. but it doesnt appear in the list. I only have gnome, system default and gnome classic. How do i get this listed as an option? I looked around tweak tools and settings menu - nothing seem to be there in regards to this.

you all may want to clear this up - unity8 is pretty much worthless on the 14.04 Desktop install, also see comment #8

---

### Post by anbu-s on 2015-01-13
> **mc4man said:**
> you all may want to clear this up - unity8 is pretty much worthless on the 14.04 Desktop install, also see comment #8

Yes - I removed unity 8 now.

---

### Post by arminstar-star on 2015-09-18
I typed 
sudo apt-get install unity  in terminal now my ubuntu gnome is crashed but i can use terminal what code i must to type in terminal to remove unity
please help

---

### Post by Bucky Ball on 2015-09-18
Did you reboot the machine and it crashed?

---

