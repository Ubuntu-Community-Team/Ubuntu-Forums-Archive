---
title: "installing wine"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by hobbes23 on 2008-07-18
Ok so I am trying to install wine. Here is my problem. I have downloaded the repositories from the winehq website by doing the terminal thing. I click on the link there and it brings up the first attachment shown. I go to applications>add/remove and search for wine click on the checkbox and I get second attachment seen. So i go to synaptic manager, search for wine, mark for installation comes up with screen to be installed winbind click on mark and get third attachment seen. So I come to the forums and check to see if anyone else has had the same problem and found a few that have so I went to terminal and did what is seen in fourth attachment seen. Still unable to download. Any suggestions? :confused: :( I am wanting to download itunes so I can purchase music and mess around with my ipod.  And the nokia PC suite so I can update my nokia phone with cool applications.

Thanks.

I am using a 500 mhz pentium III compaq 5722 with 384 MBs RAM, Voodoo 5 5500 AGP video card and 19.0 GB hard drive bought on Christmas 1999 with 96 MB of RAM.

---

### Post by hyper_ch on 2008-07-18
run```

sudo apt-get update && sudo apt-get install wine

```

and post the output.

---

### Post by hobbes23 on 2008-07-18
output:

hobbes23@melissa-desktop:~$ sudo apt-get update && sudo apt-get install wine
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy Release.gpg
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy/main Translation-en_US                    
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy/restricted Translation-en_US              
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy/multiverse Translation-en_US              
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy/universe Translation-en_US                
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates Release.gpg                       
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates/main Translation-en_US            
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates/restricted Translation-en_US      
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates/multiverse Translation-en_US      
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates/universe Translation-en_US        
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security Release.gpg                      
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security/main Translation-en_US           
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security/restricted Translation-en_US     
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security/multiverse Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security/universe Translation-en_US       
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed Release.gpg            
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed/main Translation-en_US 
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed/multiverse Translation-en_US
Ign [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed/universe Translation-en_US
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy Release                         
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates Release                 
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security Release                
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed Release                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) etch Release.gpg                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) etch/main Translation-en_US      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) etch Release                     
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy/main Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy/restricted Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy/multiverse Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy/universe Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates/main Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates/restricted Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates/multiverse Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-updates/universe Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security/main Packages        
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security/restricted Packages  
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security/multiverse Packages  
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-security/universe Packages    
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed/restricted Packages  
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed/main Packages        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed/multiverse Packages    
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) hardy-proposed/universe Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) etch/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) etch/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) etch/main Packages
Reading package lists... Done
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
  wine: Depends: libldap2 (>= 2.1.17-1) but it is not installable
E: Broken packages

---

### Post by houbysoft.xf.cz on 2008-07-18
Could you maybe try sudo apt-get install libldap2, and post the ouput, so we could see what's the reason for it to being "not installable"?

---

### Post by houbysoft.xf.cz on 2008-07-18
Oh, and by the way, I'm not sure, but I think that I heard that iPods don't work in Ubuntu + iTunes. But I said that I'm not sure. And if it doesn't there's still gtkpod, which I use :)

---

### Post by hobbes23 on 2008-07-18
Output:

hobbes23@melissa-desktop:~$ sudo apt-get install libldap2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libldap2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  slapd libldap-2.4-2
E: Package libldap2 has no installation candidate

Does this mean i need to delete the libldap-2.4.2? Cuz it seems like that would be counterproductive?

---

### Post by hobbes23 on 2008-07-18
however i went back to the forums and saw something about wine and did this:

hobbes23@melissa-desktop:~$ sudo apt-get install winesetuptk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package winesetuptk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  wine
E: Package winesetuptk has no installation candidate

So I guess that means i shouldn't delete libldp-2.4.2?

---

### Post by hyper_ch on 2008-07-18
```

cat /etc/apt/sources.list

```

---

### Post by hobbes23 on 2008-07-18
output:

hobbes23@melissa-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.ccs.neu.edu/archive.ubuntu.com/](http://mirrors.ccs.neu.edu/archive.ubuntu.com/) hardy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.ccs.neu.edu/archive.ubuntu.com/](http://mirrors.ccs.neu.edu/archive.ubuntu.com/) hardy-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirrors.ccs.neu.edu/archive.ubuntu.com/](http://mirrors.ccs.neu.edu/archive.ubuntu.com/) hardy-security main restricted multiverse universe
deb [http://mirrors.ccs.neu.edu/archive.ubuntu.com/](http://mirrors.ccs.neu.edu/archive.ubuntu.com/) hardy-proposed restricted main multiverse universe

---

