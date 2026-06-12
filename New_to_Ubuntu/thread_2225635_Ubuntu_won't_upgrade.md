---
title: "Ubuntu won't upgrade"
date: 2014-05-22
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2014-05-22
Hi all, Software Updater is saying Ubuntu 14.04 is now available (you have 13.10). So i go for the upgrade as normal. 

First i get

[ATTACH=CONFIG]253371[/ATTACH]

  which i guess is ok, 

but then as it carries on a bit i get

[ATTACH=CONFIG]253370[/ATTACH]

Close that at it restores original settings.

Can anyone help ? as i dont normally have problems with upgrades and have no idea whats going wrong. Many thanks in advance ;)

---

### Post by Bashing-om on 2014-05-22
MadMonkey1966; Hi ;

Maybe #3 in the advisory applies ?
Take a look at the software sources and disable all that the package manager can not manage.
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
(or in the ubuntu Software Center)

With the 3rd party software sources disabled what returns now from terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

sometimes, even the Package Manager
[INDENT][INDENT][INDENT]needs a little help
[/INDENT][/INDENT][/INDENT]

---

### Post by MadMonkey1966 on 2014-05-22
Thanks for your reply Bashing-om

loads and loads of stuff went by at apt-get update....
then got this at apt-get upgrade

madmonkey@madmonkey-MM061:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
madmonkey@madmonkey-MM061:~$ 

Shall i go for the upgrade now then you think ? :P

---

### Post by Impavidus on 2014-05-22
Those unofficial software packages could also be separate .deb packages you downloaded and installed, like Chrome, Google Earth, a tax form program... It's easy the find them in synaptic, under status > installed (obsolete or manually installed).

---

### Post by MadMonkey1966 on 2014-05-22
Thanks impavidus.....

In Status > obsolete there are 3 linux image ones

but 

In Status > Manually there are hundreds & hundreds.....i am sure i didnt instal them, i dont know how to lol

i think i have only ever installed a couple of things of stuff i wanted to try

oh, i tried the upgrade anyway and still get the same error message

---

### Post by Impavidus on 2014-05-22
There is status > installed (manually), which contains all manually installed packages from the repositories. Many of these were not really manually installed, but were installed during Ubuntu installation. You can leave these alone.

There is also status > installed (obsolete or manually installed), which contains packages that are no longer available from the repositories or did not even come from the repositories, but from manually downloaded and installed .deb files. These may be your three linux images. Which packages are they exactly? You may have to uninstall them first. I'm not sure this will solve your problem though.

---

### Post by Bashing-om on 2014-05-22
MadMonkey1966; Humm....
This:
> 
In Status > Manually there are hundreds & hundreds.....

is cause for concern, let's see what Impavidus' thoughts are.
And in the meantime post back to us - between code tags - the outputs of the terminal codes:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

``` and clear this item as a possible cause.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We have changed nothing, so the result of attempting the release upgrade will be the same as before. We will find the cause.

got to be a reason ->
[INDENT][INDENT]package manager does not lie
[/INDENT][/INDENT]

---

### Post by MadMonkey1966 on 2014-05-22
ok i tried uninstalling them packages that Impavidus suggested and it had no effect.

so trying your suggestion Bashing-om (hope i get this code bit right) :)

```
madmonkey@madmonkey-MM061:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
     6    deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    11    deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://gb.archive.ubuntu.com/ubuntu/ saucy universe
    17    deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy universe
    18    deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe
    19    deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
    27    deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
    28    deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    29    deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    37    deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu saucy-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
    41    deb http://security.ubuntu.com/ubuntu saucy-security universe
    42    deb-src http://security.ubuntu.com/ubuntu saucy-security universe
    43    deb http://security.ubuntu.com/ubuntu saucy-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu precise partner
    51    # deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu saucy main
    56    deb-src http://extras.ubuntu.com/ubuntu saucy main
madmonkey@madmonkey-MM061:~$ cat /etc/apt/sources.list.d/*.list
deb http://ppa.launchpad.net/irie/blender/ubuntu saucy main
# deb-src http://ppa.launchpad.net/irie/blender/ubuntu saucy main
deb http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu saucy main
# deb-src http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu saucy main
madmonkey@madmonkey-MM061:~$ 

```

---

### Post by Bashing-om on 2014-05-22
MadMonkey1966; Well ...

I do not see a problem,
both 
[http://ppa.launchpad.net/irie/blender/ubuntu](http://ppa.launchpad.net/irie/blender/ubuntu)
[http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu](http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu)
support trusty and "/etc/apt/sources.list" file is in order.

Let's see what the terminal output relates in making the release upgrade:
```

sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade -d

``` where "do-release-upgrade -d" is valid to upgrade to 14.04 until that 1st point release (July 24) of 14.04.1; then the -d option will point to the next "development" release of 14.10.

At this point, pending additional information;

[INDENT][INDENT][INDENT]all I know to do
[/INDENT][/INDENT][/INDENT]

---

### Post by MadMonkey1966 on 2014-05-22
ok thanks did all that, but the terminal would only let me copy so much, so i started from the bottom and copied what i could.

```
Get:14 http://security.ubuntu.com saucy-security/universe Sources [8,836 B]
Get:15 http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages [3,881 B]
Get:16 http://security.ubuntu.com saucy-security/multiverse Sources [1,826 B]      
Hit http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB       
Hit http://gb.archive.ubuntu.com saucy-updates/main Translation-en      
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB
Get:17 http://security.ubuntu.com saucy-security/main i386 Packages [125 kB]
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB         
Hit http://gb.archive.ubuntu.com saucy-updates/universe Translation-en            
Hit http://gb.archive.ubuntu.com saucy-backports/main Sources                     
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Sources               
Hit http://gb.archive.ubuntu.com saucy-backports/universe Sources                 
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Sources               
Hit http://gb.archive.ubuntu.com saucy-backports/main i386 Packages               
Hit http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages         
Hit http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages           
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages         
Hit http://gb.archive.ubuntu.com saucy-backports/main Translation-en             
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en
Get:18 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en  
Hit http://gb.archive.ubuntu.com saucy-backports/universe Translation-en
Get:19 http://security.ubuntu.com saucy-security/universe i386 Packages [42.1 kB]
Get:20 http://security.ubuntu.com saucy-security/multiverse i386 Packages [3,619 B]
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB 
Hit http://security.ubuntu.com saucy-security/main Translation-en       
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en 
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Hit http://security.ubuntu.com saucy-security/universe Translation-en
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB
Fetched 898 kB in 4s (216 kB/s)
Reading package lists... Done
madmonkey@madmonkey-MM061:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
madmonkey@madmonkey-MM061:~$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                                               
Get:2 Upgrade tool [1,148 kB]                                                                      
Fetched 1,148 kB in 0s (0 B/s)                                                                     
authenticate 'trusty.tar.gz' against 'trusty.tar.gz.gpg' 
extracting 'trusty.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Ign http://gb.archive.ubuntu.com saucy InRelease                                                   
Ign http://security.ubuntu.com saucy-security InRelease                                            
Ign http://gb.archive.ubuntu.com saucy-updates InRelease                                           
Ign http://ppa.launchpad.net saucy InRelease                                                       
Ign http://extras.ubuntu.com saucy InRelease                                                       
Get:1 http://security.ubuntu.com saucy-security Release.gpg [933 B]                                
Ign http://gb.archive.ubuntu.com saucy-backports InRelease                                         
Ign http://ppa.launchpad.net saucy InRelease                                                       
Hit http://extras.ubuntu.com saucy Release.gpg                                                     
Hit http://gb.archive.ubuntu.com saucy Release.gpg                                                 
Get:2 http://security.ubuntu.com saucy-security Release [49.6 kB]                                  
Hit http://ppa.launchpad.net saucy Release.gpg                                                     
Hit http://extras.ubuntu.com saucy Release                                                         
Hit http://gb.archive.ubuntu.com saucy-updates Release.gpg                                         
Hit http://gb.archive.ubuntu.com saucy-backports Release.gpg                                       
Hit http://ppa.launchpad.net saucy Release.gpg                                                     
Hit http://gb.archive.ubuntu.com saucy Release                                                     
Hit http://ppa.launchpad.net saucy Release                                                         
Hit http://gb.archive.ubuntu.com saucy-updates Release                                             
Hit http://extras.ubuntu.com saucy/main Sources                                                    
Hit http://gb.archive.ubuntu.com saucy-backports Release                                           
Hit http://ppa.launchpad.net saucy Release                                                         
Hit http://extras.ubuntu.com saucy/main i386 Packages                                              
Get:3 http://security.ubuntu.com saucy-security/main Sources [47.7 kB]                             
Err http://extras.ubuntu.com saucy/main Translation-en_GB                                          
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/main Sources                                                
Err http://extras.ubuntu.com saucy/main Translation-en                                             
                                                                                                   
Get:4 http://security.ubuntu.com saucy-security/restricted Sources [14 B]                          
Hit http://gb.archive.ubuntu.com saucy/restricted Sources                                          
Err http://extras.ubuntu.com saucy/main Translation-en_GB                                          
                                                                                                   
Hit http://ppa.launchpad.net saucy/main i386 Packages                                              
Get:5 http://security.ubuntu.com saucy-security/universe Sources [8,836 B]                         
Hit http://gb.archive.ubuntu.com saucy/universe Sources                                            
Err http://extras.ubuntu.com saucy/main Translation-en                                             
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en_GB                                          
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/multiverse Sources                                          
Get:6 http://security.ubuntu.com saucy-security/multiverse Sources [1,826 B]                       
Err http://ppa.launchpad.net saucy/main Translation-en                                             
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/main i386 Packages                                          
Err http://extras.ubuntu.com saucy/main Translation-en_GB                                          
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en_GB                                          
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/restricted i386 Packages                                    
Get:7 http://security.ubuntu.com saucy-security/main i386 Packages [125 kB]                        
Hit http://gb.archive.ubuntu.com saucy/universe i386 Packages                                      
Err http://extras.ubuntu.com saucy/main Translation-en                                             
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en                                             
                                                                                                   
Err http://extras.ubuntu.com saucy/main Translation-en_GB                                          
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en_GB                                          
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/multiverse i386 Packages                                    
Err http://extras.ubuntu.com saucy/main Translation-en                                             
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en                                             
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/main Translation-en_GB                                      
Get:8 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]                    
Ign http://extras.ubuntu.com saucy/main Translation-en_GB                                          
Err http://ppa.launchpad.net saucy/main Translation-en_GB                                          
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/main Translation-en                                         
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en_GB                                
Get:9 http://security.ubuntu.com saucy-security/universe i386 Packages [42.1 kB]                   
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en                                   
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en_GB                                
Get:10 http://security.ubuntu.com saucy-security/multiverse i386 Packages [3,619 B]                
Ign http://extras.ubuntu.com saucy/main Translation-en                                             
Err http://ppa.launchpad.net saucy/main Translation-en                                             
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en                                   
Err http://security.ubuntu.com saucy-security/main Translation-en_GB                               
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en_GB                                  
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                                          
Hit http://security.ubuntu.com saucy-security/main Translation-en                                  
Hit http://ppa.launchpad.net saucy/main i386 Packages                                              
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en                                     
Err http://security.ubuntu.com saucy-security/multiverse Translation-en_GB                         
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/main Sources                                        
Err http://ppa.launchpad.net saucy/main Translation-en_GB                                          
                                                                                                   
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en                            
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Sources                                  
Err http://security.ubuntu.com saucy-security/restricted Translation-en_GB                         
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/universe Sources                                    
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Sources                                  
Hit http://gb.archive.ubuntu.com saucy-updates/main i386 Packages                                  
Err http://ppa.launchpad.net saucy/main Translation-en                                             
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/restricted i386 Packages                            
Ign http://ppa.launchpad.net saucy/main Translation-en                                             
Hit http://security.ubuntu.com saucy-security/restricted Translation-en                            
Hit http://gb.archive.ubuntu.com saucy-updates/universe i386 Packages                              
Err http://security.ubuntu.com saucy-security/universe Translation-en_GB                           
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en_GB                                          
                                                                                                   
Hit http://security.ubuntu.com saucy-security/universe Translation-en                              
Err http://ppa.launchpad.net saucy/main Translation-en                                             
                                                                                                   
Err http://security.ubuntu.com saucy-security/main Translation-en_GB                               
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en_GB                                          
                                                                                                   
Err http://security.ubuntu.com saucy-security/multiverse Translation-en_GB                         
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en                                             
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages                            
Err http://security.ubuntu.com saucy-security/restricted Translation-en_GB                         
                                                                                                   
Err http://security.ubuntu.com saucy-security/universe Translation-en_GB                           
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB                              
Err http://ppa.launchpad.net saucy/main Translation-en_GB                                          
                                                                                                   
Err http://security.ubuntu.com saucy-security/main Translation-en_GB                               
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/main Translation-en                                 
Err http://security.ubuntu.com saucy-security/multiverse Translation-en_GB                         
                                                                                                   
Err http://ppa.launchpad.net saucy/main Translation-en                                             
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB                        
Err http://security.ubuntu.com saucy-security/restricted Translation-en_GB                         
                                                                                                   
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                                          
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en                           
Err http://security.ubuntu.com saucy-security/universe Translation-en_GB                           
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB                        
Ign http://ppa.launchpad.net saucy/main Translation-en                                             
Err http://security.ubuntu.com saucy-security/main Translation-en_GB                               
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en                           
Err http://security.ubuntu.com saucy-security/multiverse Translation-en_GB                         
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB                          
Err http://security.ubuntu.com saucy-security/restricted Translation-en_GB                         
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-updates/universe Translation-en                             
Err http://security.ubuntu.com saucy-security/universe Translation-en_GB                           
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-backports/main Sources                                      
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB                               
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Sources                                
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB                         
Hit http://gb.archive.ubuntu.com saucy-backports/universe Sources                                  
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB                         
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Sources                                
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB                           
Hit http://gb.archive.ubuntu.com saucy-backports/main i386 Packages                                
Hit http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages                          
Hit http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages                            
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages                          
Err http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB                            
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-backports/main Translation-en                               
Err http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB                      
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en                         
Err http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB                      
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en                         
Err http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB                        
                                                                                                   
Hit http://gb.archive.ubuntu.com saucy-backports/universe Translation-en                           
Err http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB                            
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB                      
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB                      
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB                        
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB                            
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB                      
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB                      
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB                        
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB                            
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB                      
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB                      
                                                                                                   
Err http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB                        
                                                                                                   
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB                            
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB                      
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB                      
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB                        
Fetched 280 kB in 0s (0 B/s)                                                                       
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

To continue please press [ENTER]

Ign http://gb.archive.ubuntu.com trusty InRelease                                                  
Ign http://extras.ubuntu.com trusty InRelease                                                      
Ign http://gb.archive.ubuntu.com trusty-updates InRelease                                          
Get:1 http://extras.ubuntu.com trusty Release.gpg [72 B]                                           
Ign http://gb.archive.ubuntu.com trusty-backports InRelease                                        
Get:2 http://gb.archive.ubuntu.com trusty Release.gpg [933 B]                                      
Get:3 http://extras.ubuntu.com trusty Release [11.9 kB]                                            
Get:4 http://gb.archive.ubuntu.com trusty-updates Release.gpg [933 B]                              
Get:5 http://gb.archive.ubuntu.com trusty-backports Release.gpg [933 B]                            
Get:6 http://gb.archive.ubuntu.com trusty Release [58.5 kB]                                        
Get:7 http://extras.ubuntu.com trusty/main Sources [14 B]                                          
Ign http://security.ubuntu.com trusty-security InRelease                                           
Get:8 http://extras.ubuntu.com trusty/main i386 Packages [14 B]                                    
Get:9 http://gb.archive.ubuntu.com trusty-updates Release [58.5 kB]                                
Err http://extras.ubuntu.com trusty/main Translation-en_GB                                         
                                                                                                   
Err http://extras.ubuntu.com trusty/main Translation-en                                            
                                                                                                   
Get:10 http://gb.archive.ubuntu.com trusty-backports Release [58.6 kB]                             
Err http://extras.ubuntu.com trusty/main Translation-en_GB                                         
                                                                                                   
Get:11 http://security.ubuntu.com trusty-security Release.gpg [933 B]                              
Err http://extras.ubuntu.com trusty/main Translation-en                                            
                                                                                                   
Get:12 http://gb.archive.ubuntu.com trusty/main Sources [1,064 kB]                                 
Err http://extras.ubuntu.com trusty/main Translation-en_GB                                         
                                                                                                   
Err http://extras.ubuntu.com trusty/main Translation-en                                            
                                                                                                   
Err http://extras.ubuntu.com trusty/main Translation-en_GB                                         
                                                                                                   
Get:13 http://security.ubuntu.com trusty-security Release [58.5 kB]                                
Err http://extras.ubuntu.com trusty/main Translation-en                                            
                                                                                                   
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                                         
Ign http://extras.ubuntu.com trusty/main Translation-en                                            
Get:14 http://gb.archive.ubuntu.com trusty/restricted Sources [5,433 B]                            
Get:15 http://gb.archive.ubuntu.com trusty/universe Sources [6,399 kB]                             
Get:16 http://security.ubuntu.com trusty-security/main Sources [15.6 kB]                           
Get:17 http://security.ubuntu.com trusty-security/restricted Sources [14 B]                        
Get:18 http://security.ubuntu.com trusty-security/universe Sources [4,212 B]                       
Get:19 http://security.ubuntu.com trusty-security/multiverse Sources [687 B]                       
Get:20 http://security.ubuntu.com trusty-security/main i386 Packages [47.5 kB]                     
Get:21 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]                  
Get:22 http://security.ubuntu.com trusty-security/universe i386 Packages [17.7 kB]                 
Get:23 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,404 B]               
Err http://security.ubuntu.com trusty-security/main Translation-en_GB                              
                                                                                                   
Get:24 http://security.ubuntu.com trusty-security/main Translation-en [23.1 kB]                    
Err http://security.ubuntu.com trusty-security/multiverse Translation-en_GB                        
                                                                                                   
Get:25 http://security.ubuntu.com trusty-security/multiverse Translation-en [587 B]                
Err http://security.ubuntu.com trusty-security/restricted Translation-en_GB                        
                                                                                                   
Get:26 http://security.ubuntu.com trusty-security/restricted Translation-en [14 B]                 
Err http://security.ubuntu.com trusty-security/universe Translation-en_GB                          
                                                                                                   
Get:27 http://gb.archive.ubuntu.com trusty/multiverse Sources [174 kB]                             
Get:28 http://security.ubuntu.com trusty-security/universe Translation-en [8,850 B]                
Get:29 http://gb.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]                           
Err http://security.ubuntu.com trusty-security/main Translation-en_GB                              
                                                                                                   
Err http://security.ubuntu.com trusty-security/multiverse Translation-en_GB                        
                                                                                                   
Get:30 http://gb.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]                      
Err http://security.ubuntu.com trusty-security/restricted Translation-en_GB                        
                                                                                                   
Get:31 http://gb.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]                       
Err http://security.ubuntu.com trusty-security/universe Translation-en_GB                          
                                                                                                   
Err http://security.ubuntu.com trusty-security/main Translation-en_GB                              
                                                                                                   
Err http://security.ubuntu.com trusty-security/multiverse Translation-en_GB                        
                                                                                                   
Err http://security.ubuntu.com trusty-security/restricted Translation-en_GB                        
                                                                                                   
Err http://security.ubuntu.com trusty-security/universe Translation-en_GB                          
                                                                                                   
Err http://security.ubuntu.com trusty-security/main Translation-en_GB                              
                                                                                                   
Err http://security.ubuntu.com trusty-security/multiverse Translation-en_GB                        
                                                                                                   
Err http://security.ubuntu.com trusty-security/restricted Translation-en_GB                        
                                                                                                   
Err http://security.ubuntu.com trusty-security/universe Translation-en_GB                          
                                                                                                   
Ign http://security.ubuntu.com trusty-security/main Translation-en_GB                              
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_GB                        
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_GB                        
Ign http://security.ubuntu.com trusty-security/universe Translation-en_GB                          
Get:32 http://gb.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]                       
Get:33 http://gb.archive.ubuntu.com trusty/main Translation-en_GB [96.8 kB]                        
Get:34 http://gb.archive.ubuntu.com trusty/main Translation-en [762 kB]                            
Get:35 http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB [98.3 kB]                  
Get:36 http://gb.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]                      
Get:37 http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB [3,483 B]                  
Get:38 http://gb.archive.ubuntu.com trusty/restricted Translation-en [3,457 B]                     
Get:39 http://gb.archive.ubuntu.com trusty/universe Translation-en_GB [7,557 B]                    
Get:40 http://gb.archive.ubuntu.com trusty/universe Translation-en [4,089 kB]                      
Get:41 http://gb.archive.ubuntu.com trusty-updates/main Sources [40.5 kB]                          
Get:42 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [14 B]                       
Get:43 http://gb.archive.ubuntu.com trusty-updates/universe Sources [25.7 kB]                      
Get:44 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [2,234 B]                    
Get:45 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [92.5 kB]                    
Get:46 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]                 
Get:47 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [66.5 kB]                
Get:48 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [7,273 B]              
Err http://gb.archive.ubuntu.com trusty-updates/main Translation-en_GB                             
                                                                                                   
Get:49 http://gb.archive.ubuntu.com trusty-updates/main Translation-en [45.4 kB]                   
Err http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en_GB                       
                                                                                                   
Get:50 http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en [3,811 B]             
Err http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en_GB                       
                                                                                                   
Get:51 http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en [14 B]                
Err http://gb.archive.ubuntu.com trusty-updates/universe Translation-en_GB                         
                                                                                                   
Get:52 http://gb.archive.ubuntu.com trusty-updates/universe Translation-en [31.4 kB]               
Get:53 http://gb.archive.ubuntu.com trusty-backports/main Sources [14 B]                           
Get:54 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [14 B]                     
Get:55 http://gb.archive.ubuntu.com trusty-backports/universe Sources [2,842 B]                    
Get:56 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [14 B]                     
Get:57 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [14 B]                     
Get:58 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]               
Get:59 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [2,777 B]              
Get:60 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [14 B]               
Err http://gb.archive.ubuntu.com trusty-backports/main Translation-en_GB                           
                                                                                                   
Get:61 http://gb.archive.ubuntu.com trusty-backports/main Translation-en [14 B]                    
Err http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en_GB                     
                                                                                                   
Get:62 http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en [14 B]              
Err http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en_GB                     
                                                                                                   
Get:63 http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]              
Err http://gb.archive.ubuntu.com trusty-backports/universe Translation-en_GB                       
                                                                                                   
Get:64 http://gb.archive.ubuntu.com trusty-backports/universe Translation-en [1,719 B]             
Err http://gb.archive.ubuntu.com trusty-updates/main Translation-en_GB                             
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en_GB                       
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en_GB                       
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/universe Translation-en_GB                         
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/main Translation-en_GB                           
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en_GB                     
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en_GB                     
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/universe Translation-en_GB                       
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/main Translation-en_GB                             
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en_GB                       
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en_GB                       
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/universe Translation-en_GB                         
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/main Translation-en_GB                           
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en_GB                     
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en_GB                     
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/universe Translation-en_GB                       
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/main Translation-en_GB                             
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en_GB                       
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en_GB                       
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-updates/universe Translation-en_GB                         
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/main Translation-en_GB                           
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en_GB                     
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en_GB                     
                                                                                                   
Err http://gb.archive.ubuntu.com trusty-backports/universe Translation-en_GB                       
                                                                                                   
Ign http://gb.archive.ubuntu.com trusty-updates/main Translation-en_GB                             
Ign http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en_GB                       
Ign http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en_GB                       
Ign http://gb.archive.ubuntu.com trusty-updates/universe Translation-en_GB                         
Ign http://gb.archive.ubuntu.com trusty-backports/main Translation-en_GB                           
Ign http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en_GB                     
Ign http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en_GB                     
Ign http://gb.archive.ubuntu.com trusty-backports/universe Translation-en_GB                       
Fetched 20.9 MB in 6s (0 B/s)                                                                      

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Could not determine the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
madmonkey@madmonkey-MM061:~$ 

```

at tha bottom, we have the same outcome though.

---

### Post by Bashing-om on 2014-05-22
MadMonkey1966; Ummphh,

I have looked about, the errors are all in respect to 'translation' and I am stumped as to what it means.
> 
authenticate 'trusty.tar.gz' against 'trusty.tar.gz.gpg' 
extracting 'trusty.tar.gz'

The means to release upgrade appear to be present, I do not know what is hindering the procedure.

What can I say
[INDENT][INDENT][INDENT]I hate when this happens
[/INDENT][/INDENT][/INDENT]

---

### Post by MadMonkey1966 on 2014-05-23
Not to worry, many thanks for all your help. I will leave it another couple of days here and see if anyone else has an idea, if not i will just have to stay with this version i guess.

That maybe for the best as it is running on an oldish laptop and since Unity has been in (although it runs fine) and Ubuntu getting more resource hungry it will get to the stage where i will have to stop anyway. I have already had to take Ubuntu off my main computer as its so slow compared to windows (which i hate saying, but sadly its the truth), and Blender which i love is know where near as quick.

Lets see if anyone else has an idea.

Thanks again for your help :)

---

### Post by Impavidus on 2014-05-23
> **Bashing-om said:**
> MadMonkey1966; Humm....
This:
[QUOTE=MadMonkey1966;13030715]In Status > Manually there are hundreds & hundreds.....
is cause for concern, let's see what Impavidus' thoughts are.[/QUOTE]
Not really a cause for concern. These are all packages manually installed (as opposed to automatically as a dependencie) from the repositories, including the packages installed by default during installation of Ubuntu.

I can't say what causes your problem.

If you cannot upgrade, you can always do a clean install. Maybe you have to move to a lighter flavour of Ubuntu, that is, Xubuntu or Lubuntu. That is better than running an end-of-life release. 13.10 reaches end-of-life in July.

---

### Post by kansasnoob on 2014-05-23
I'd file a new bug report using:

```
ubuntu-bug ubuntu-release-upgrader-core
```

That will collect all of the applicable logs, then if you post the link to that bug report here we might be able to parse that info and figure out what the problem is.

---

### Post by Bashing-om on 2014-05-23
Thanks guys,

I am still stumped on this one - It is a relieve to see others are in a similar situation.

I do want to know and understand what is taking place and have requested another to take a look at this thread.

See what we can come up with.

[INDENT][INDENT]I think maybe this;
[INDENT][INDENT][INDENT]that 1st time for everything
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MadMonkey1966 on 2014-05-24
Impavidus, thanks again, i have tried a few different versions (OSLinux, Mint, Puppy and more lol) but always end up back with Ubuntu. Maybe i will try Xubuntu or Lubuntu, if this doesnt get resolved or i dont do a fresh intall of 14.10.

Kansasnoob, i think i will do that anyway, then maybe it can get resolved and it may stop it happening again, thanks.

Bashing-om, thanks, glad it isnt just me doing something stupid lol. Lets hope :)

Thanks again folks for your help.

---

