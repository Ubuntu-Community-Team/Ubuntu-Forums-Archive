---
title: "Updating issues"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by pandacookie on 2012-10-29
I have a problem. In the bar at the top of my screen, there is a little red triangle with an exclamation point in the middle. When I click it, it says:

"The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by selecting 'show updates' from the indicator menu, and watching for any failing repositories."

I go to update manually, as it says to do. At first there WAS an update that kept failing but eventually did download and install after a few tries. The update was for Firefox. The triangle went away for a while, then came back. When I went to update manually, I got the message that all the software on the computer is up to date.

Now I'm confused. 

I saw a similar thread [here]("http://ubuntuforums.org/showthread.php?t=2077501") and saw that someone posted [this ]("http://ubuntuforums.org/archive/index.php/t-1879295.html")and the solution there did not help. 

Hopefully the following will also help bring a solution:

```
panda@panda-VPCEH34FX:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for panda: 
Ign http://us.archive.ubuntu.com quantal InRelease                             
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://security.ubuntu.com quantal-security InRelease                      
Hit http://repository.spotify.com stable InRelease                             
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Hit http://extras.ubuntu.com quantal Release.gpg                               
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security Release.gpg                    
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://packages.medibuntu.org quantal InRelease                            
Ign http://us.archive.ubuntu.com quantal-backports InRelease                   
Hit http://extras.ubuntu.com quantal Release                                   
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security Release                        
Hit http://packages.medibuntu.org quantal/free i386 Packages                   
Hit http://us.archive.ubuntu.com quantal Release.gpg                           
Hit http://extras.ubuntu.com quantal/main Sources                              
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security/main Sources                   
Hit http://us.archive.ubuntu.com quantal-updates Release.gpg                   
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Hit http://us.archive.ubuntu.com quantal-backports Release.gpg                 
Hit http://packages.medibuntu.org quantal/non-free i386 Packages               
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security/restricted Sources             
Hit http://us.archive.ubuntu.com quantal Release                               
Hit http://security.ubuntu.com quantal-security/universe Sources               
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://us.archive.ubuntu.com quantal-updates Release                       
Hit http://security.ubuntu.com quantal-security/multiverse Sources             
Hit http://us.archive.ubuntu.com quantal-backports Release                     
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://us.archive.ubuntu.com quantal/main Sources                          
Hit http://security.ubuntu.com quantal-security/main i386 Packages             
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://us.archive.ubuntu.com quantal/restricted Sources                    
Hit http://us.archive.ubuntu.com quantal/universe Sources                      
Hit http://security.ubuntu.com quantal-security/restricted i386 Packages       
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign https://private-ppa.launchpad.net quantal InRelease                        
Hit http://us.archive.ubuntu.com quantal/multiverse Sources                    
Hit http://security.ubuntu.com quantal-security/universe i386 Packages         
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://us.archive.ubuntu.com quantal/main i386 Packages                    
Hit http://security.ubuntu.com quantal-security/multiverse i386 Packages       
Ign http://ppa.launchpad.net quantal Release.gpg                               
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages              
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages                
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages              
Hit http://security.ubuntu.com quantal-security/main Translation-en            
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign https://private-ppa.launchpad.net quantal Release.gpg                      
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://us.archive.ubuntu.com quantal/main Translation-en         
Hit http://ppa.launchpad.net quantal Release                         
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://ppa.launchpad.net quantal Release                                   
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en             
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Ign https://private-ppa.launchpad.net quantal Release                
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://us.archive.ubuntu.com quantal/universe Translation-en               
Hit http://us.archive.ubuntu.com quantal-updates/main Sources                  
Hit http://us.archive.ubuntu.com quantal-updates/restricted Sources            
Hit http://security.ubuntu.com quantal-security/universe Translation-en        
Hit http://ppa.launchpad.net quantal Release                         
Hit http://us.archive.ubuntu.com quantal-updates/universe Sources              
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Sources            
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://us.archive.ubuntu.com quantal-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages      
Hit http://ppa.launchpad.net quantal/main Sources                    
Hit http://us.archive.ubuntu.com quantal-updates/universe i386 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en           
Ign http://packages.medibuntu.org quantal/free Translation-en_US               
Hit http://ppa.launchpad.net quantal/main Sources                    
Hit http://ppa.launchpad.net quantal/main i386 Packages              
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Ign http://packages.medibuntu.org quantal/free Translation-en        
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://packages.medibuntu.org quantal/non-free Translation-en_US 
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Ign http://packages.medibuntu.org quantal/non-free Translation-en    
Hit http://us.archive.ubuntu.com quantal-backports/main Sources      
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Hit http://us.archive.ubuntu.com quantal-backports/restricted Sources
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com quantal-backports/universe Sources
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Sources
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://us.archive.ubuntu.com quantal-backports/main i386 Packages
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://ppa.launchpad.net quantal/main i386 Packages
Err https://private-ppa.launchpad.net quantal/main i386 Packages
  The requested URL returned error: 404 Not Found
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign https://private-ppa.launchpad.net quantal/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign https://private-ppa.launchpad.net quantal/main Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/fluendo-dvd/ubuntu/dists/quantal/main/binary-i386/Packages  The requested URL returned error: 404 Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
panda@panda-VPCEH34FX:~$ 

```

Thanks to whomever can sort this out! I'd really like to lose that little triangle! 

[]("http://ubuntuforums.org/archive/index.php/t-1879295.html")
[]("http://ubuntuforums.org/showthread.php?t=2077501")

---

### Post by NikTh on 2012-10-29
> **pandacookie said:**
> ```

W: Failed to fetch http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/fluendo-dvd/ubuntu/dists/quantal/main/binary-i386/Packages  The requested URL returned error: 404 Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
panda@panda-VPCEH34FX:~$ 

```

Hi , 

above messages means that the repositories apt-get attempted to take informations are not exits. 

The only way I know to correct such errors is the removal of the specific repositories.

Give the results of this command and I(or someone else) will give the commands to correct the error.

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
```

Thanks

---

### Post by pandacookie on 2012-10-29
Here you go:

```
panda@panda-VPCEH34FX:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_fluendo-dvd_ubuntu.list

     1    deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/fluendo-dvd/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf

/etc/apt/sources.list.d/medibuntu.list

     1    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
     2    deb http://packages.medibuntu.org/ quantal free non-free #Medibuntu - Ubuntu 12.10 "quantal quetzal"
     3    # deb-src http://packages.medibuntu.org/ quantal free non-free #Medibuntu (source) - Ubuntu 12.10 "quantal quetzal"

/etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list

     1    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu quantal main
     2    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu quantal main

/etc/apt/sources.list.d/gnome3-team-gnome3-quantal.list

     1    deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu quantal main
     2    deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu quantal main

/etc/apt/sources.list.d/noobslab-swar-themes-quantal.list

     1    deb http://ppa.launchpad.net/noobslab/swar-themes/ubuntu quantal main
     2    deb-src http://ppa.launchpad.net/noobslab/swar-themes/ubuntu quantal main

/etc/apt/sources.list.d/noobslab-themes-quantal.list

     1    deb http://ppa.launchpad.net/noobslab/themes/ubuntu quantal main
     2    deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu quantal main

/etc/apt/sources.list.d/noobslab-icons-quantal.list

     1    deb http://ppa.launchpad.net/noobslab/icons/ubuntu quantal main
     2    deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu quantal main

/etc/apt/sources.list.d/satyajit-happy-themes-quantal.list

     1    deb http://ppa.launchpad.net/satyajit-happy/themes/ubuntu quantal main
     2    deb-src http://ppa.launchpad.net/satyajit-happy/themes/ubuntu quantal main

/etc/apt/sources.list.d/ricotz-testing-quantal.list


/etc/apt/sources.list.d/tualatrix-ppa-quantal.list

     1    deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main
     2    deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ quantal universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ quantal universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu quantal-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
    41    deb http://security.ubuntu.com/ubuntu quantal-security universe
    42    deb-src http://security.ubuntu.com/ubuntu quantal-security universe
    43    deb http://security.ubuntu.com/ubuntu quantal-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu quantal partner
    51    # deb-src http://archive.canonical.com/ubuntu quantal partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu quantal main
    56    deb-src http://extras.ubuntu.com/ubuntu quantal main
    57    deb http://repository.spotify.com stable non-free
panda@panda-VPCEH34FX:~$ 

```

---

### Post by Warprunner on 2012-10-29
I would go to the "Software Sources" app and go to "Other". From there Iwouldn't delete the following but uncheck them. The reason I wouldn't delete is that you installed a program that needs them to update. Launchpad doesn't have them "yet" but may in the future. Then you can check those later by checking them and running an Update.
Uncheck these:
W: Failed to fetch [http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/noobslab/swar-themes/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/fluendo-dvd/ubuntu/dists/quantal/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/fluendo-dvd/ubuntu/dists/quantal/main/binary-i386/Packages)  The requested URL returned error: 404 Not Found

---

### Post by jerrrys on 2012-10-29
[FONT=monospace]Swar themes have not been updated to 12.10 yet.  So the easy way would be to just uncheck them ( ones that show 404 error) in software sources and from time to time check the ppa for updates.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

[https://launchpad.net/~noobslab/+archive/swar-themes](https://launchpad.net/~noobslab/+archive/swar-themes)


[/FONT]

---

### Post by pandacookie on 2012-10-29
Okay. I'll do that. If I have any more issues I'll post again. Thanks!

---

### Post by manuelm1 on 2012-11-12
i have new in ubuntu, my problen is the

manuel@manuel-Lenovo:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

```
     1    # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal main restricted
     6    deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
    11    deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal universe
    17    deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal universe
    18    deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal-updates universe
    19    deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal multiverse
    27    deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal multiverse
    28    deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
    29    deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    
    37    
    38    ## Uncomment the following two lines to add software from Canonical's
    39    ## 'partner' repository.
    40    ## This software is not part of Ubuntu, but is offered by Canonical and the
    41    ## respective vendors as a service to Ubuntu users.
    42    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
    43    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
    44    
    45    ## This software is not part of Ubuntu, but is offered by third-party
    46    ## developers who want to ship their latest software.
    47    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
    48    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
    49    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security restricted main multiverse universe
    50    deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal-proposed restricted main multiverse universe
    51    deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) quantal-backports restricted main multiverse universe

/etc/apt/sources.list.d/diesch-testing-quantal.list

     1    deb [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) quantal main
     2    deb-src [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) quantal main

/etc/apt/sources.list.d/webupd8team-jupiter-quantal.list

     1    deb [http://ppa.launchpad.net/webupd8team/jupiter/ubuntu](http://ppa.launchpad.net/webupd8team/jupiter/ubuntu) quantal main
     2    deb-src [http://ppa.launchpad.net/webupd8team/jupiter/ubuntu](http://ppa.launchpad.net/webupd8team/jupiter/ubuntu) quantal main

/etc/apt/sources.list.d/tiheum-equinox-oneiric.list

     1    # deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) precise main # (desactivado en la actualización a precise)
     2    # deb-src [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) precise main # (desactivado en la actualización a precise)

/etc/apt/sources.list.d/google-earth.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main

/etc/apt/sources.list.d/cairo-dock-team-ppa-precise.list

     1    # deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) quantal main # (desactivado en la actualización a quantal)
     2    # deb-src [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) quantal main # (desactivado en la actualización a quantal)

/etc/apt/sources.list.d/artfwo-ppa-quantal.list

     1    deb [http://ppa.launchpad.net/artfwo/ppa/ubuntu](http://ppa.launchpad.net/artfwo/ppa/ubuntu) quantal main
     2    deb-src [http://ppa.launchpad.net/artfwo/ppa/ubuntu](http://ppa.launchpad.net/artfwo/ppa/ubuntu) quantal main

/etc/apt/sources.list.d/claudiocn-slm-oneiric.list

     1    # deb [http://ppa.launchpad.net/claudiocn/slm/ubuntu](http://ppa.launchpad.net/claudiocn/slm/ubuntu) precise main # (desactivado en la actualización a precise)
     2    # deb-src [http://ppa.launchpad.net/claudiocn/slm/ubuntu](http://ppa.launchpad.net/claudiocn/slm/ubuntu) precise main # (desactivado en la actualización a precise)

/etc/apt/sources.list.d/playdeb.list

     1    # deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games # (desactivado en la actualización a precise)

/etc/apt/sources.list.d/shnatsel-zram-quantal.list

     1    deb [http://ppa.launchpad.net/shnatsel/zram/ubuntu](http://ppa.launchpad.net/shnatsel/zram/ubuntu) quantal main
     2    deb-src [http://ppa.launchpad.net/shnatsel/zram/ubuntu](http://ppa.launchpad.net/shnatsel/zram/ubuntu) quantal main

/etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list

     1    # deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main # (desactivado en la actualización a precise)
     2    # deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main # (desactivado en la actualización a precise)

/etc/apt/sources.list.d/shnatsel-zram-oneiric.list

     1    # deb [http://ppa.launchpad.net/shnatsel/zram/ubuntu](http://ppa.launchpad.net/shnatsel/zram/ubuntu) precise main # (desactivado en la actualización a precise)
     2    # deb-src [http://ppa.launchpad.net/shnatsel/zram/ubuntu](http://ppa.launchpad.net/shnatsel/zram/ubuntu) precise main # (desactivado en la actualización a precise)

/etc/apt/sources.list.d/myunity-ppa-quantal.list

     1    deb [http://ppa.launchpad.net/myunity/ppa/ubuntu](http://ppa.launchpad.net/myunity/ppa/ubuntu) quantal main
     2    deb-src [http://ppa.launchpad.net/myunity/ppa/ubuntu](http://ppa.launchpad.net/myunity/ppa/ubuntu) quantal main

/etc/apt/sources.list.d/tldm217-tahutek_net-oneiric.list

     1    # deb [http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu](http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu) precise main # (desactivado en la actualización a precise)
     2    # deb-src [http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu](http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu) precise main # (desactivado en la actualización a precise)

/etc/apt/sources.list.d/medibuntu.list

     1    ## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
     2    deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free #Medibuntu - Ubuntu 12.10 "quantal quetzal"
     3    deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free #Medibuntu (source) - Ubuntu 12.10 "quantal quetzal"

/etc/apt/sources.list.d/claudiocn-slm-precise.list

     1    # deb [http://ppa.launchpad.net/claudiocn/slm/ubuntu](http://ppa.launchpad.net/claudiocn/slm/ubuntu) quantal main # (desactivado en la actualización a quantal)
     2    # deb-src [http://ppa.launchpad.net/claudiocn/slm/ubuntu](http://ppa.launchpad.net/claudiocn/slm/ubuntu) quantal main # (desactivado en la actualización a quantal)
```

help please, i am spoken spanish...

---

### Post by arpanaut on 2012-11-12
@manuelm1 Without the errors you are getting from the command;
```
sudo apt-get update
```
No one here is going to be able to help you...
please post the output from the terminal when you run the command.

---

### Post by ibjsb4 on 2012-11-12
Hi manuelm1, welcome to the forums  :)

Lines 42 & 43 are oneiric and should be hash (#) out.

/etc/apt/sources.list.d/google-earth.list_deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main_is 404 (not found) hash (#) out

2 deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free #Medibuntu - Ubuntu 12.10 "quantal quetzal"
3 deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free #Medibuntu (source) - Ubuntu 12.10 "quantal quetzal"
Do not look right to me; hash (#) them out

And like arpanaut said, please post the output of:

sudo apt-get update

---

