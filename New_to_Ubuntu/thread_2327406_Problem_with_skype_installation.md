---
title: "Problem with skype installation"
date: 2016-06-10
forum: New to Ubuntu
---

### Post by dimitris13 on 2016-06-10
Hello everyone, I'm a new ubuntu user. I currently use 14.04 LTS (64 bit) for a few months.
So, I'm trying to figure out a way to install skype since yesterday. I've tried every way described in various topics I've found but still with no luck.

I've tried to install via Software center but libqtwebkit4:i386 cannot be installed.

In terminal after I give "**sudo apt-get update**" and then "**sudo apt-get install skype**" 
"The following packages have unmet dependencies:
skype : Depends: skype-bin E: Unable to correct problems, you have held broken packages." is what I get.

I've also tried "**sudo apt-get -f install"**, an installation with **Gdebi, **pretty much everything described in this [topic's]("http://askubuntu.com/questions/504689/cant-install-skype-4-3-on-ubuntu-14-04-64-bit") most upvoted answer but nothing works.

**I haven't installed skype before and canonical partners are enabled**. 

I know this has been answered before but I think each "case" is different so that's why I decided to create a new account and ask you to give me advice
and hopefully a solution. I wouldn't like to format my laptop preferably.

I don't know what else information should I provide, so please ask me and I will give it to you.

---

### Post by X-RED_Tech on 2016-06-10
Have you enabled the Partners repository?

If I remember correctly, for an English language 14.04, it's in System Settings -> Software & Updates -> Other... (tab). Make sure it is enabled then do sudo apt-get update again and post here the errors if any.

---

### Post by Bucky Ball on 2016-06-10
As above. Once you have enabled the Canonical Partner repository in Software and Updates> Other Software tab, update and it will be available in Ubuntu Software (Software Centre), Synaptic or the terminal install method.

Remove whatever other Skype stuff you tried to install first might be a good idea, but might not make any difference either.

---

### Post by dimitris13 on 2016-06-10
Yes I have. As I described in OP

"The following packages have unmet dependencies:
skype : Depends: skype-bin 
E: Unable to correct problems, you have held broken packages." is what I get.

I haven't installed Skype before either.

---

### Post by Bucky Ball on 2016-06-10
Open a terminal. Give it this.

```
sudo apt-get -f install
```

Post back the output using code tags, please. 

If you have broken packages and you haven't installed anything, then perhaps you had broken packages prior to trying this and that is a problem not related to Skype installation. 

Also run these in terminal after running the one above, regardless of its output:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

Post back whatever that spits out, between code tags.

---

### Post by dimitris13 on 2016-06-10
(I'm sorry it took me this long to answer, had to change the system's default language and reboot)
Here is the outcome of every command.

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get -f install
[sudo] password for shady13axd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get update
Ign http://gr.archive.ubuntu.com trusty InRelease
Hit http://repo.steampowered.com precise InRelease                             
Hit http://gr.archive.ubuntu.com trusty-updates InRelease                      
Hit http://gr.archive.ubuntu.com trusty-backports InRelease                    
Hit http://gr.archive.ubuntu.com trusty Release.gpg                            
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://gr.archive.ubuntu.com trusty Release                                
Ign http://dl.google.com stable InRelease                                      
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://repo.acestream.org raring InRelease                                 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://gr.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release                                
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://gr.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://gr.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://gr.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://gr.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://gr.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://repo.acestream.org raring/main amd64 Packages                       
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://gr.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://gr.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://gr.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://gr.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://gr.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://repo.acestream.org raring/main i386 Packages                        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://gr.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://gr.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://gr.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://gr.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://gr.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://gr.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://gr.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://gr.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://gr.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://gr.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://gr.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://gr.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://gr.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://gr.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://gr.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://gr.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://gr.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://gr.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://gr.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://gr.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://gr.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://gr.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://gr.archive.ubuntu.com trusty/restricted Sources                     
Hit http://gr.archive.ubuntu.com trusty/universe Sources                       
Hit http://gr.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://gr.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://gr.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://gr.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://gr.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://gr.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://gr.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://gr.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://gr.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://gr.archive.ubuntu.com trusty/main Translation-en                    
Hit http://gr.archive.ubuntu.com trusty/main Translation-el                    
Hit http://gr.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://gr.archive.ubuntu.com trusty/multiverse Translation-el              
Hit http://gr.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://gr.archive.ubuntu.com trusty/restricted Translation-el              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://gr.archive.ubuntu.com trusty/universe Translation-en                
Hit http://gr.archive.ubuntu.com trusty/universe Translation-el                
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-el                        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Ign http://repo.acestream.org raring/main Translation-en_US                    
Ign http://repo.acestream.org raring/main Translation-en                       
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Ign http://gr.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://gr.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://gr.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://repo.acestream.org raring/main Translation-el                       
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Ign http://gr.archive.ubuntu.com trusty/universe Translation-en_US             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Ign http://repo.steampowered.com precise/steam Translation-el                  
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-el                            
Reading package lists... Done
```
                                                  
```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bucky Ball on 2016-06-10
Have you tried doing:

```
sudo apt-get install skype
```

now? Incidentally, wouldn't advise a reinstall for something like this. Killing a mosquito with an elephant gun, and what difference would it make? It is not the OS that is broken, it is a package that is required by Skype, that is all, and out there somewhere is an answer to a fix no doubt.

(From what I've found so far, enable Canonical Repos, update, upgrade and install has fixed this as the install has been attempted before an update. I'll keep looking.)

---

### Post by dimitris13 on 2016-06-10
Again.... :(

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
```

---

### Post by Bucky Ball on 2016-06-10
Try the instructions at [this link]("http://ubuntuhandbook.org/index.php/2014/06/skype-4-3-install-in-ubuntu-1404/"). Go down to number '1' and you need steps a, b, and c.

Any luck?

---

### Post by QIII on 2016-06-10
Let's try to simulate installing skype-bin and see what we get.

```
sudo apt-get install -s skype-bin
```

---

### Post by QDR06VV9 on 2016-06-10
I have seen this a few times you will need to choose a diffrent download server from software and updates.(Main Server)
Then run "sudo apt-get update" again try again with the above suggestions.

---

### Post by dimitris13 on 2016-06-10
Outcome of the skype bin installation command
```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get install -s skype-bin
[sudo] password for shady13axd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype-bin:i386 : Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386
E: Unable to correct problems, you have held broken packages.
```

---

### Post by QDR06VV9 on 2016-06-10
Suborn little critter.:)
Let see what this dose
```
sudo dpkg --add-architecture i386
```
Again posting back any errors

---

### Post by dimitris13 on 2016-06-10
It gives back nothing.

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo dpkg --add-architecture i386
[sudo] password for shady13axd: 
shady13axd@shady13axd-HP-G62-Notebook-PC:~$
```

---

### Post by Bucky Ball on 2016-06-10
> **dimitris13 said:**
> It gives back nothing.

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo dpkg --add-architecture i386
[sudo] password for shady13axd: 
shady13axd@shady13axd-HP-G62-Notebook-PC:~$
```

Maybe not, but have you tried installing Skype now? If still nothing, as suggested earlier, open Software and Updates and change to the main server, update, try again. That worked for someone else I found earlier.

---

### Post by dimitris13 on 2016-06-10
I changed to main server and repeated all the steps. Still depends on skype bin and i386 architecture installation command gives back nothing

---

### Post by QDR06VV9 on 2016-06-10
Did you remember to to first run "sudo apt-get update"?
And this is just a switch no installation "sudo dpkg --add-architecture i386"

---

### Post by dimitris13 on 2016-06-10
Yes I did

---

### Post by QDR06VV9 on 2016-06-10
Forgot to have you show any errors from this
```
sudo apt-get upgrade --fix-missing
```
Post all back

---

### Post by dimitris13 on 2016-06-10
```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get upgrade --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by QDR06VV9 on 2016-06-10
Well ok then lets see if we can trick it a bit run the below one line at a time
```
wget -O skype-install.deb http://www.skype.com/go/getskype-linux-deb
sudo dpkg -i skype-install.deb
```
If still complains about missing packages run this again
```
[SIZE=3]sudo apt-get -f install[/SIZE]
```

---

### Post by dimitris13 on 2016-06-10
Is there a way to download and install i386 architecture manually?

---

### Post by dimitris13 on 2016-06-10
Check this out. Should I run **sudo apt-get -f install **now?

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ wget -O skype-install.deb http://www.skype.com/go/getskype-linux-deb
--2016-06-10 22:27:07--  http://www.skype.com/go/getskype-linux-deb
Resolving www.skype.com (www.skype.com)... 40.115.34.155
Connecting to www.skype.com (www.skype.com)|40.115.34.155|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://www.skype.com/go/getskype-linux-deb [following]
--2016-06-10 22:27:13--  https://www.skype.com/go/getskype-linux-deb
Connecting to www.skype.com (www.skype.com)|40.115.34.155|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://get.skype.com/go/getskype-linux-deb [following]
--2016-06-10 22:27:13--  https://get.skype.com/go/getskype-linux-deb
Resolving get.skype.com (get.skype.com)... 157.56.198.10
Connecting to get.skype.com (get.skype.com)|157.56.198.10|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://get.skype.com/go/getskype-linux-deb-32 [following]
--2016-06-10 22:27:14--  https://get.skype.com/go/getskype-linux-deb-32
Reusing existing connection to get.skype.com:443.
HTTP request sent, awaiting response... 302 Found
Location: https://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb [following]
--2016-06-10 22:27:14--  https://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb
Resolving download.skype.com (download.skype.com)... 104.107.146.182, 2a02:26f0:c000:18e::11f1, 2a02:26f0:c000:189::11f1
Connecting to download.skype.com (download.skype.com)|104.107.146.182|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20118938 (19M) [application/octet-stream]
Saving to: &#8216;skype-install.deb&#8217;

100%[======================================>] 20118938     124KB/s   in 90s    

2016-06-10 22:28:49 (218 KB/s) - &#8216;skype-install.deb&#8217; saved [20118938/20118938]

shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo dpkg -i skype-install.deb
[sudo] password for shady13axd: 
Selecting previously unselected package skype.
(Reading database ... 270663 files and directories currently installed.)
Preparing to unpack skype-install.deb ...
Unpacking skype (4.3.0.37-1) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqtwebkit4 (>= 2.1.0~2011week13).
 skype depends on libxss1; however:
  Package libxss1 is not installed.
 skype depends on libxv1; however:
  Package libxv1 is not installed.

dpkg: error processing package skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 skype
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get upgrade --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 skype:i386 : Depends: libqtwebkit4:i386 (>= 2.1.0~2011week13) but it is not installed
              Depends: libxss1:i386 but it is not installed
              Depends: libxv1:i386 but it is not installed
E: Unmet dependencies. Try using -f.
```

---

### Post by QDR06VV9 on 2016-06-10
> **dimitris13 said:**
> Check this out. Should I run **sudo apt-get -f install **now?

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ wget -O skype-install.deb http://www.skype.com/go/getskype-linux-deb
--2016-06-10 22:27:07--  http://www.skype.com/go/getskype-linux-deb
Resolving www.skype.com (www.skype.com)... 40.115.34.155
Connecting to www.skype.com (www.skype.com)|40.115.34.155|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://www.skype.com/go/getskype-linux-deb [following]
--2016-06-10 22:27:13--  https://www.skype.com/go/getskype-linux-deb
Connecting to www.skype.com (www.skype.com)|40.115.34.155|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://get.skype.com/go/getskype-linux-deb [following]
--2016-06-10 22:27:13--  https://get.skype.com/go/getskype-linux-deb
Resolving get.skype.com (get.skype.com)... 157.56.198.10
Connecting to get.skype.com (get.skype.com)|157.56.198.10|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://get.skype.com/go/getskype-linux-deb-32 [following]
--2016-06-10 22:27:14--  https://get.skype.com/go/getskype-linux-deb-32
Reusing existing connection to get.skype.com:443.
HTTP request sent, awaiting response... 302 Found
Location: https://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb [following]
--2016-06-10 22:27:14--  https://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb
Resolving download.skype.com (download.skype.com)... 104.107.146.182, 2a02:26f0:c000:18e::11f1, 2a02:26f0:c000:189::11f1
Connecting to download.skype.com (download.skype.com)|104.107.146.182|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20118938 (19M) [application/octet-stream]
Saving to: ‘skype-install.deb’

100%[======================================>] 20118938     124KB/s   in 90s    

2016-06-10 22:28:49 (218 KB/s) - ‘skype-install.deb’ saved [20118938/20118938]

shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo dpkg -i skype-install.deb
[sudo] password for shady13axd: 
Selecting previously unselected package skype.
(Reading database ... 270663 files and directories currently installed.)
Preparing to unpack skype-install.deb ...
Unpacking skype (4.3.0.37-1) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqtwebkit4 (>= 2.1.0~2011week13).
 skype depends on libxss1; however:
  Package libxss1 is not installed.
 skype depends on libxv1; however:
  Package libxv1 is not installed.

dpkg: error processing package skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 skype
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get upgrade --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 skype:i386 : Depends: libqtwebkit4:i386 (>= 2.1.0~2011week13) but it is not installed
              Depends: libxss1:i386 but it is not installed
              Depends: libxv1:i386 but it is not installed
E: Unmet dependencies. Try using -f.
```
Yes Sir.:)

---

### Post by dimitris13 on 2016-06-10
I did.
```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo -s
root@shady13axd-HP-G62-Notebook-PC:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxss1:i386 libxv1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxss1:i386 libxv1:i386
The following packages will be REMOVED:
  skype:i386
The following NEW packages will be installed:
  libxss1:i386 libxv1:i386
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 18,7 kB of archives.
After this operation, 44,2 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libxss1 i386 1:1.2.2-1 [8566 B]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main libxv1 i386 2:1.0.10-1 [10,2 kB]
Fetched 18,7 kB in 0s (61,3 kB/s)     
(Reading database ... 270811 files and directories currently installed.)
Removing skype (4.3.0.37-1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Selecting previously unselected package libxss1:i386.
(Reading database ... 270664 files and directories currently installed.)
Preparing to unpack .../libxss1_1%3a1.2.2-1_i386.deb ...
Unpacking libxss1:i386 (1:1.2.2-1) ...
Selecting previously unselected package libxv1:i386.
Preparing to unpack .../libxv1_2%3a1.0.10-1_i386.deb ...
Unpacking libxv1:i386 (2:1.0.10-1) ...
Setting up libxss1:i386 (1:1.2.2-1) ...
Setting up libxv1:i386 (2:1.0.10-1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
```

Then this happened
```
root@shady13axd-HP-G62-Notebook-PC:~# wget -O skype-install.deb http://www.skype.com/go/getskype-linux-deb
--2016-06-10 22:35:14--  http://www.skype.com/go/getskype-linux-deb
Resolving www.skype.com (www.skype.com)... 40.115.34.155
Connecting to www.skype.com (www.skype.com)|40.115.34.155|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://www.skype.com/go/getskype-linux-deb [following]
--2016-06-10 22:35:14--  https://www.skype.com/go/getskype-linux-deb
Connecting to www.skype.com (www.skype.com)|40.115.34.155|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://get.skype.com/go/getskype-linux-deb [following]
--2016-06-10 22:35:14--  https://get.skype.com/go/getskype-linux-deb
Resolving get.skype.com (get.skype.com)... 157.56.198.10
Connecting to get.skype.com (get.skype.com)|157.56.198.10|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://get.skype.com/go/getskype-linux-deb-32 [following]
--2016-06-10 22:35:15--  https://get.skype.com/go/getskype-linux-deb-32
Reusing existing connection to get.skype.com:443.
HTTP request sent, awaiting response... 302 Found
Location: https://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb [following]
--2016-06-10 22:35:15--  https://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb
Resolving download.skype.com (download.skype.com)... 104.107.146.182, 2a02:26f0:c000:189::11f1, 2a02:26f0:c000:18e::11f1
Connecting to download.skype.com (download.skype.com)|104.107.146.182|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20118938 (19M) [application/octet-stream]
Saving to: &#8216;skype-install.deb&#8217;

100%[======================================>] 20118938     457KB/s   in 92s    

2016-06-10 22:36:47 (214 KB/s) - &#8216;skype-install.deb&#8217; saved [20118938/20118938]

root@shady13axd-HP-G62-Notebook-PC:~# sudo dpkg -i skype-install.deb
Selecting previously unselected package skype.
(Reading database ... 270668 files and directories currently installed.)
Preparing to unpack skype-install.deb ...
Unpacking skype (4.3.0.37-1) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqtwebkit4 (>= 2.1.0~2011week13).

dpkg: error processing package skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 skype
```

Did I do something wrong? I can't understand...

---

### Post by QDR06VV9 on 2016-06-10
You forgot "sudo"
```
sudo apt-get -f install
```
Holy cow you move fast.
Now we need to clean up a bit with:
```
sudo apt-get autoremove
```

---

### Post by dimitris13 on 2016-06-10
I'm really lost right now hahaha. It just refuses to be installed. Maybe I should give up...

---

### Post by QDR06VV9 on 2016-06-10
If you do  not give the outputs or errors we can not solve this.
and only issue the commands given per post.
Post back what this shows now
```
dpkg -l skype
```
And just to check you did run "sudo apt-get autoremove"?

---

### Post by dimitris13 on 2016-06-10
Yes I ran sudo apt-get autoremove.

---

### Post by QDR06VV9 on 2016-06-10
Hummm? This baby just dose not want to cooperate with us..:confused:

open terminal. When it opens, run commands one by one to remove old skype and .skype folder:

```
sudo apt-get remove skype skype-bin

rm -rf ~/.skype
```
Post back any errors

---

### Post by dimitris13 on 2016-06-10
No errors. Everything got removed.

---

### Post by QDR06VV9 on 2016-06-10
Hooray it is starting to go our way..:)
```
sudo apt-get update
 sudo apt-get install skype
```
Fingers Crossed

---

### Post by dimitris13 on 2016-06-10
Same old same old.

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get update
Hit http://repo.steampowered.com precise InRelease
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://dl.google.com stable InRelease                                      
Hit http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://repo.acestream.org raring InRelease                                 
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://archive.ubuntu.com trusty-backports InRelease                       
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.ubuntu.com trusty-security InRelease                        
Hit http://repo.acestream.org raring/main amd64 Packages                       
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://repo.acestream.org raring/main i386 Packages                        
Hit http://archive.ubuntu.com trusty-updates/main Sources                      
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.ubuntu.com trusty-updates/restricted Sources                
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://archive.ubuntu.com trusty-updates/universe Sources                  
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources                
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages               
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages         
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages           
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages         
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages                
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages          
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages            
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages          
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Ign http://extras.ubuntu.com trusty/main Translation-el                        
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://archive.ubuntu.com trusty-backports/main Sources                    
Hit http://archive.ubuntu.com trusty-backports/restricted Sources              
Hit http://archive.ubuntu.com trusty-backports/universe Sources                
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources              
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Ign http://repo.acestream.org raring/main Translation-en_US                    
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Ign http://repo.acestream.org raring/main Translation-en                       
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://repo.acestream.org raring/main Translation-el                       
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages     
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages 
Ign http://dl.google.com stable/main Translation-el                            
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-backports/main Translation-en
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en 
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://archive.ubuntu.com trusty-security/main Sources              
Hit http://archive.ubuntu.com trusty-security/restricted Sources 
Hit http://archive.ubuntu.com trusty-security/universe Sources    
Hit http://archive.ubuntu.com trusty-security/multiverse Sources 
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-security/main i386 Packages   
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-security/main Translation-en  
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en  
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en  
Hit http://archive.ubuntu.com trusty-security/universe Translation-en    
Hit http://archive.ubuntu.com trusty Release                            
Hit http://archive.ubuntu.com trusty/main Sources
Hit http://archive.ubuntu.com trusty/restricted Sources
Hit http://archive.ubuntu.com trusty/universe Sources
Hit http://archive.ubuntu.com trusty/multiverse Sources           
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages    
Hit http://archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/main Translation-el
Hit http://archive.ubuntu.com trusty/multiverse Translation-en     
Hit http://archive.ubuntu.com trusty/multiverse Translation-el     
Hit http://archive.ubuntu.com trusty/restricted Translation-en     
Hit http://archive.ubuntu.com trusty/restricted Translation-el     
Hit http://archive.ubuntu.com trusty/universe Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-el
Ign http://archive.ubuntu.com trusty/main Translation-en_US        
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US  
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US  
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Ign http://repo.steampowered.com precise/steam Translation-el                  
Reading package lists... Done                                                  
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get update
Hit http://repo.steampowered.com precise InRelease
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://repo.acestream.org raring InRelease                                 
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports InRelease                       
Hit http://repo.acestream.org raring/main amd64 Packages                       
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://archive.ubuntu.com trusty-security InRelease                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://repo.acestream.org raring/main i386 Packages                        
Hit http://archive.ubuntu.com trusty Release.gpg                               
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-updates/main Sources                      
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-updates/restricted Sources                
Hit http://archive.ubuntu.com trusty-updates/universe Sources                  
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources                
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages               
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages         
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages           
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages         
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages                
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages          
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages            
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages          
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-el                        
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://archive.ubuntu.com trusty-backports/main Sources                    
Hit http://archive.ubuntu.com trusty-backports/restricted Sources              
Ign http://repo.acestream.org raring/main Translation-en_US                    
Hit http://archive.ubuntu.com trusty-backports/universe Sources                
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources              
Ign http://repo.acestream.org raring/main Translation-en                       
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Ign http://repo.acestream.org raring/main Translation-el                       
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages          
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                   
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://archive.ubuntu.com trusty-security/main Sources                     
Ign http://dl.google.com stable/main Translation-el                            
Hit http://archive.ubuntu.com trusty-security/restricted Sources               
Hit http://archive.ubuntu.com trusty-security/universe Sources    
Hit http://archive.ubuntu.com trusty-security/multiverse Sources 
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-security/main i386 Packages   
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-security/main Translation-en  
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en  
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en  
Hit http://archive.ubuntu.com trusty-security/universe Translation-en    
Hit http://archive.ubuntu.com trusty Release                            
Hit http://archive.ubuntu.com trusty/main Sources
Hit http://archive.ubuntu.com trusty/restricted Sources
Hit http://archive.ubuntu.com trusty/universe Sources
Hit http://archive.ubuntu.com trusty/multiverse Sources           
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/main Translation-el
Hit http://archive.ubuntu.com trusty/multiverse Translation-en     
Hit http://archive.ubuntu.com trusty/multiverse Translation-el     
Hit http://archive.ubuntu.com trusty/restricted Translation-en     
Hit http://archive.ubuntu.com trusty/restricted Translation-el     
Hit http://archive.ubuntu.com trusty/universe Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-el
Ign http://archive.ubuntu.com trusty/main Translation-en_US        
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Ign http://repo.steampowered.com precise/steam Translation-el                  
Reading package lists... Done
```

```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$  sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
```

At this point I don't think anything could be done. Only a clean installation would sort things out it seems.

---

### Post by QDR06VV9 on 2016-06-10
Welp there is always hope! I see PPA [U][B]repo.acestream.org raring/main Translation-en

[/B][/U]Lets see if we remove that one from /etc/apt/sources.list and add the correct one for Trusty a bit later.
Or just comment it out by putting a "#" in front of it with out the Quotes.
Then remove skype the way i showed earlier
```
sudo apt-get remove skype skype-bin  
rm -rf ~/.skype 

```

---

### Post by dimitris13 on 2016-06-10
Could you please tell me how to remove PPA?

if I type /etc/apt/sources.list it tells me that access is denied.

---

### Post by QDR06VV9 on 2016-06-10
Yes sorry about that.
```
gksudo gedit /etc/apt/sources.list
```
If you want to show that list first I can show you also how to comment it out.

---

### Post by dimitris13 on 2016-06-10
```
# deb cdrom:[Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty universe
deb-src http://archive.ubuntu.com/ubuntu trusty universe
deb http://archive.ubuntu.com/ubuntu trusty-updates universe
deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb http://archive.ubuntu.com/ubuntu trusty-security universe
deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
#AceStream
# deb http://repo.acestream.org/ubuntu/ raring main
```

---

### Post by QDR06VV9 on 2016-06-10
Yes Perfect! Good Job.
Now run the commands in post # 34 again.

---

### Post by dimitris13 on 2016-06-10
```
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ sudo apt-get remove skype skype-bin [sudo] password for shady13axd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'skype' is not installed, so not removed
Package 'skype-bin:i386' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ rm -rf ~/.skype
shady13axd@shady13axd-HP-G62-Notebook-PC:~$ 
```

---

### Post by QDR06VV9 on 2016-06-10
Ok lets try this method one more time
```
sudo apt-get autoremove
sudo apt-get dist-upgrade
```
If there are no errors proceed to:
```
wget -O skype-install.deb http://www.skype.com/go/getskype-linux-deb
sudo dpkg -i skype-install.deb
```
That .deb is probably already in your home directory but we will do it just to eliminate any possible errors.
Note to self re-add the correct PPA for acestream.org.:D

---

### Post by dimitris13 on 2016-06-10
Still nothing....
There's nothing working. I would like a moderator to lock the thread, thanks to everyone trying to help me. I really appreciate it.

---

### Post by QIII on 2016-06-10
We'll leave it open.  Someone may come along with the exact answer and that might be of use to another person later.

This is a community.  Threads do not serve the originator only.

:)

---

### Post by QDR06VV9 on 2016-06-10
At OP's Request [S]Closed[/S] and Reopened

---

### Post by QIII on 2016-06-10
And reopened.  ;)

---

### Post by dimitris13 on 2016-06-10
Sorry guys, that was so selfish of me.

---

### Post by howefield on 2016-06-11
I'll put money on it being related to [this]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-January/016148.html") ....

---

### Post by QDR06VV9 on 2016-06-11
Well I did not have the same errors as dimitris13 but was having problems installing skype on trusty just different errors.
Then I had seen where howefield posted the link with the package conflict libgles2-mesa-lts-vivid.
So what I ended up doing was installing a bunch of packages that I thought was a part of the enablement stack..which was as follows

```
sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid 
xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid libqt5gui5 libgles1-mesa-lts-vivid libgles2-mesa-lts-vivid libgl1-mesa-glx-lts-vivid
```
Now it still showed some errors and was suggested to use "apt --fix-misssing" be issued but I did not run it at this time.
Now I went to the terminal and ran (**with the parnters repo enabled**)
```
sudo apt install skype
```
And it installed with no errors all. Then I ran 
```
sudo apt update
```
```
sudo apt full-upgrade
```
And everything is now nice and tidy.
Now I do not know if Steam will break with this method because I am just not a gamer at all, so if you proceed with this method I discribed I would be very watchfull as what is being removed.
Hope this helpful.
And thanks to howefield for the link:)
EDIT: to be clear on this I had already had Ubuntu 14.04.4 LTS up to date and was running kernel 4.2.0-38-generic

---

### Post by howefield on 2016-06-12
Good work runrickus :)

---

### Post by dimitris13 on 2016-06-13
Runrickus I haven't tried this method. Instead, I went the hard way and installed 16.04 and now Skype is installed and working fine :)

---

### Post by Bucky Ball on 2016-06-14
> **dimitris13 said:**
> ... I went the hard way and installed 16.04 and now Skype is installed and working fine :)

Good news. Please mark thread as solved to help others using Thread Tools at top right. Enjoy. ;)

---

