---
title: "[SOLVED] my public key is not available? what does that mean?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-11-09
hola!
im trying to reload my synaptic list and this appeared:

[IMG]http://i38.tinypic.com/aau7ex.png[/IMG]

and after that one, this another one:

[IMG]http://i36.tinypic.com/mrppp5.png[/IMG]

so i went to terminal trying to do it from there but it seems to be afecting both:

```
julio@julio-laptop:~$ sudo apt-get update
[sudo] password for julio:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net gutsy/main Translation-en_US                      
Ign http://dl.google.com stable/non-free Translation-en_US                     
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [189B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:3 http://packages.medibuntu.org hardy Release.gpg [189B]                   
Hit http://dl.google.com stable Release                                        
Err http://dl.google.com stable Release                                        
  
Get:4 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://ppa.launchpad.net gutsy Release                                     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Get:5 http://dl.google.com stable Release [1300B]                              
Ign http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net gutsy/main Packages                               
Hit http://archive.ubuntu.com gutsy Release                                    
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://dl.google.com stable/non-free Packages                              
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Err http://ppa.launchpad.net gutsy/main Packages                               
  404 Not Found
Hit http://archive.ubuntu.com gutsy/main Sources                               
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://security.ubuntu.com gutsy-security/universe Sources 
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://packages.medibuntu.org hardy Release                                
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://packages.medibuntu.org hardy/non-free Packages      
Get:6 http://cl.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://cl.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://cl.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://cl.archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://cl.archive.ubuntu.com gutsy/universe Translation-en_US              
Get:7 http://cl.archive.ubuntu.com gutsy-updates Release.gpg [189B]            
Ign http://cl.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://cl.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Ign http://cl.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Ign http://cl.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Get:8 http://cl.archive.ubuntu.com gutsy-backports Release.gpg [189B]          
Ign http://cl.archive.ubuntu.com gutsy-backports/main Translation-en_US        
Ign http://cl.archive.ubuntu.com gutsy-backports/restricted Translation-en_US  
Ign http://cl.archive.ubuntu.com gutsy-backports/universe Translation-en_US    
Ign http://cl.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US  
Get:9 http://cl.archive.ubuntu.com gutsy-proposed Release.gpg [189B]           
Ign http://cl.archive.ubuntu.com gutsy-proposed/restricted Translation-en_US   
Ign http://cl.archive.ubuntu.com gutsy-proposed/main Translation-en_US         
Ign http://cl.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US   
Ign http://cl.archive.ubuntu.com gutsy-proposed/universe Translation-en_US     
Hit http://cl.archive.ubuntu.com gutsy Release                                 
Hit http://cl.archive.ubuntu.com gutsy-updates Release                         
Hit http://cl.archive.ubuntu.com gutsy-backports Release                       
Hit http://cl.archive.ubuntu.com gutsy-proposed Release                        
Hit http://cl.archive.ubuntu.com gutsy/main Packages                           
Hit http://cl.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://cl.archive.ubuntu.com gutsy/multiverse Packages                     
Hit http://cl.archive.ubuntu.com gutsy/restricted Sources                      
Hit http://cl.archive.ubuntu.com gutsy/main Sources                            
Hit http://cl.archive.ubuntu.com gutsy/multiverse Sources                      
Hit http://cl.archive.ubuntu.com gutsy/universe Sources                        
Hit http://cl.archive.ubuntu.com gutsy/universe Packages                       
Hit http://cl.archive.ubuntu.com gutsy-updates/main Packages                   
Hit http://cl.archive.ubuntu.com gutsy-updates/restricted Packages             
Hit http://cl.archive.ubuntu.com gutsy-updates/multiverse Packages             
Hit http://cl.archive.ubuntu.com gutsy-updates/restricted Sources              
Hit http://cl.archive.ubuntu.com gutsy-updates/main Sources                    
Hit http://cl.archive.ubuntu.com gutsy-updates/multiverse Sources              
Hit http://cl.archive.ubuntu.com gutsy-updates/universe Sources                
Hit http://cl.archive.ubuntu.com gutsy-updates/universe Packages               
Hit http://cl.archive.ubuntu.com gutsy-backports/main Packages                 
Hit http://cl.archive.ubuntu.com gutsy-backports/restricted Packages           
Hit http://cl.archive.ubuntu.com gutsy-backports/universe Packages             
Hit http://cl.archive.ubuntu.com gutsy-backports/multiverse Packages           
Hit http://cl.archive.ubuntu.com gutsy-backports/main Sources                  
Hit http://cl.archive.ubuntu.com gutsy-backports/restricted Sources            
Hit http://cl.archive.ubuntu.com gutsy-backports/universe Sources              
Hit http://cl.archive.ubuntu.com gutsy-backports/multiverse Sources            
Hit http://cl.archive.ubuntu.com gutsy-proposed/restricted Packages            
Hit http://cl.archive.ubuntu.com gutsy-proposed/main Packages                  
Hit http://cl.archive.ubuntu.com gutsy-proposed/multiverse Packages            
Hit http://cl.archive.ubuntu.com gutsy-proposed/universe Packages              
Hit http://cl.archive.ubuntu.com gutsy-proposed/restricted Sources             
Hit http://cl.archive.ubuntu.com gutsy-proposed/main Sources                   
Hit http://cl.archive.ubuntu.com gutsy-proposed/multiverse Sources             
Hit http://cl.archive.ubuntu.com gutsy-proposed/universe Sources               
Fetched 1496B in 13s (111B/s)                                                  
[COLOR="Red"]Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  404 Not Found
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR]

```

so i closed everything, i mean nothing but terminal running on the screen but nada.

so... i need some help here dudes! thanks!

---

### Post by jsf_pp on 2008-11-09
up!
:guitar:

---

### Post by spiderbatdad on 2008-11-09
the problem is in your sources list. Comment out the offending repositories or try to add the missing keys. like this maybe:
```
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
```But not entirely sure regarding the resource. You could just edit your sources list and Comment (#) the source.```
gksu gedit /etc/apt/sources.list
```

---

### Post by jsf_pp on 2008-11-09
ok, when i did it this appeared:

```
julio@julio-laptop:~$ wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
gpg: no valid OpenPGP data found.

```

and about the other one what's in the file is:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-updates universe

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
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) gutsy main
___________________________END OF FILE_____________________________________

now, how do i Comment (#) the source ?

thanks!

---

### Post by jsf_pp on 2008-11-10
help...](*,)

---

### Post by kostkon on 2008-11-10
It seems that this [*PPA*]("https://launchpad.net/~openoffice-pkgs/+archive") stopped providing *OO.O* packages for Gutsy. That's why you are getting the 404 error. You should disable this repository or remove it.

Go to *System -> Administration -> Software Sources* and in the *Third-Party Software* tab you will find the entry for this repository. It will be like this
```
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) gutsy main
```
deselect it to disable or if you want you can delete it. Then press *Close* and *Reload*.

You may also find this line
```
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) gutsy main
```
do the same as above.

Obviously, you will not get updates for OO.O from this PPA from now on.

As for the *Google* key, download it from [here]("http://www.google.com/linuxrepositories/aboutkey.html") and then to import it open *Software Sources* again and go to the *Authentication* tab.

---

### Post by spiderbatdad on 2008-11-10
comment this  line **deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) gutsy main** like so: ```
**# **deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu gutsy main
```

Fix the previous command like so: ```
wget -q -O - https://dl-**ssl**.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
```

---

### Post by jsf_pp on 2008-11-10
two days ago i upgraded to OOo 3.0. does that change sth?

---

### Post by jsf_pp on 2008-11-10
ok, im trying to download my pubkey you kostkon, gave me but when i go to it, i mean, when i clic the download link (this one)

[IMG]http://i36.tinypic.com/mu9z5e.png[/IMG] 


nothing to download appears, only a new page with this info:

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

mQGiBEXwb0YRBADQva2NLpYXxgjNkbuP0LnPoEXruGmvi3XMIxjEUFuGNCP4Rj/a
kv2E5VixBP1vcQFDRJ+p1puh8NU0XERlhpyZrVMzzS/RdWdyXf7E5S8oqNXsoD1z
fvmI+i9b2EhHAA19Kgw7ifV8vMa4tkwslEmcTiwiw8lyUl28Wh4Et8SxzwCggDcA
feGqtn3PP5YAdD0km4S4XeMEAJjlrqPoPv2Gf//tfznY2UyS9PUqFCPLHgFLe80u
QhI2U5jt6jUKN4fHauvR6z3seSAsh1YyzyZCKxJFEKXCCqnrFSoh4WSJsbFNc4PN
b0V0SqiTCkWADZyLT5wll8sWuQ5ylTf3z1ENoHf+G3um3/wk/+xmEHvj9HCTBEXP
78X0A/0Tqlhc2RBnEf+AqxWvM8sk8LzJI/XGjwBvKfXe+l3rnSR2kEAvGzj5Sg0X
4XmfTg4Jl8BNjWyvm2Wmjfet41LPmYJKsux3g0b8yzQxeOA4pQKKAU3Z4+rgzGmf
HdwCG5MNT2A5XxD/eDd+L4fRx0HbFkIQoAi1J3YWQSiTk15fw7RMR29vZ2xlLCBJ
bmMuIExpbnV4IFBhY2thZ2UgU2lnbmluZyBLZXkgPGxpbnV4LXBhY2thZ2VzLWtl
eW1hc3RlckBnb29nbGUuY29tPohjBBMRAgAjAhsDBgsJCAcDAgQVAggDBBYCAwEC
HgECF4AFAkYVdn8CGQEACgkQoECDD3+sWZHKSgCfdq3HtNYJLv+XZleb6HN4zOcF
AJEAniSFbuv8V5FSHxeRimHx25671az+uQINBEXwb0sQCACuA8HT2nr+FM5y/kzI
A51ZcC46KFtIDgjQJ31Q3OrkYP8LbxOpKMRIzvOZrsjOlFmDVqitiVc7qj3lYp6U
rgNVaFv6Qu4bo2/ctjNHDDBdv6nufmusJUWq/9TwieepM/cwnXd+HMxu1XBKRVk9
XyAZ9SvfcW4EtxVgysI+XlptKFa5JCqFM3qJllVohMmr7lMwO8+sxTWTXqxsptJo
pZeKz+UBEEqPyw7CUIVYGC9ENEtIMFvAvPqnhj1GS96REMpry+5s9WKuLEaclWpd
K3krttbDlY1NaeQUCRvBYZ8iAG9YSLHUHMTuI2oea07Rh4dtIAqPwAX8xn36JAYG
2vgLAAMFB/wKqaycjWAZwIe98Yt0qHsdkpmIbarD9fGiA6kfkK/UxjL/k7tmS4Vm
CljrrDZkPSQ/19mpdRcGXtb0NI9+nyM5trweTvtPw+HPkDiJlTaiCcx+izg79Fj9
KcofuNb3lPdXZb9tzf5oDnmm/B+4vkeTuEZJ//IFty8cmvCpzvY+DAz1Vo9rA+Zn
cpWY1n6z6oSS9AsyT/IFlWWBZZ17SpMHu+h4Bxy62+AbPHKGSujEGQhWq8ZRoJAT
G0KSObnmZ7FwFWu1e9XFoUCt0bSjiJWTIyaObMrWu/LvJ3e9I87HseSJStfw6fki
5og9qFEkMrIrBCp3QGuQWBq/rTdMuwNFiEkEGBECAAkFAkXwb0sCGwwACgkQoECD
D3+sWZF/WACfeNAu1/1hwZtUo1bR+MWiCjpvHtwAnA1R3IHqFLQ2X3xJ40XPuAyY
/FJG
=Quqp
-----END PGP PUBLIC KEY BLOCK-----

so my question is: how do i download that?
do i have to copy it and paste in gedit makin a new file named gutsy.is.no.more.deb?
:biggrin:


thanks

---

### Post by jsf_pp on 2008-11-10
up!:-({|=

---

### Post by zvacet on 2008-11-10
gpg --keyserver hkp://subkeys.pgp.net --recv-keys A040830F7FAC5991
gpg --export --armor A040830F7FAC5991 | sudo apt-key add -

In terminal of course.

---

### Post by kostkon on 2008-11-10
> **jsf_pp said:**
> ok, im trying to download my pubkey you kostkon, gave me but when i go to it, i mean, when i clic the download link (this one)

[IMG]http://i36.tinypic.com/mu9z5e.png[/IMG] 


nothing to download appears, only a new page with this info:

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

mQGiBEXwb0YRBADQva2NLpYXxgjNkbuP0LnPoEXruGmvi3XMIxjEUFuGNCP4Rj/a
kv2E5VixBP1vcQFDRJ+p1puh8NU0XERlhpyZrVMzzS/RdWdyXf7E5S8oqNXsoD1z
fvmI+i9b2EhHAA19Kgw7ifV8vMa4tkwslEmcTiwiw8lyUl28Wh4Et8SxzwCggDcA
feGqtn3PP5YAdD0km4S4XeMEAJjlrqPoPv2Gf//tfznY2UyS9PUqFCPLHgFLe80u
QhI2U5jt6jUKN4fHauvR6z3seSAsh1YyzyZCKxJFEKXCCqnrFSoh4WSJsbFNc4PN
b0V0SqiTCkWADZyLT5wll8sWuQ5ylTf3z1ENoHf+G3um3/wk/+xmEHvj9HCTBEXP
78X0A/0Tqlhc2RBnEf+AqxWvM8sk8LzJI/XGjwBvKfXe+l3rnSR2kEAvGzj5Sg0X
4XmfTg4Jl8BNjWyvm2Wmjfet41LPmYJKsux3g0b8yzQxeOA4pQKKAU3Z4+rgzGmf
HdwCG5MNT2A5XxD/eDd+L4fRx0HbFkIQoAi1J3YWQSiTk15fw7RMR29vZ2xlLCBJ
bmMuIExpbnV4IFBhY2thZ2UgU2lnbmluZyBLZXkgPGxpbnV4LXBhY2thZ2VzLWtl
eW1hc3RlckBnb29nbGUuY29tPohjBBMRAgAjAhsDBgsJCAcDAgQVAggDBBYCAwEC
HgECF4AFAkYVdn8CGQEACgkQoECDD3+sWZHKSgCfdq3HtNYJLv+XZleb6HN4zOcF
AJEAniSFbuv8V5FSHxeRimHx25671az+uQINBEXwb0sQCACuA8HT2nr+FM5y/kzI
A51ZcC46KFtIDgjQJ31Q3OrkYP8LbxOpKMRIzvOZrsjOlFmDVqitiVc7qj3lYp6U
rgNVaFv6Qu4bo2/ctjNHDDBdv6nufmusJUWq/9TwieepM/cwnXd+HMxu1XBKRVk9
XyAZ9SvfcW4EtxVgysI+XlptKFa5JCqFM3qJllVohMmr7lMwO8+sxTWTXqxsptJo
pZeKz+UBEEqPyw7CUIVYGC9ENEtIMFvAvPqnhj1GS96REMpry+5s9WKuLEaclWpd
K3krttbDlY1NaeQUCRvBYZ8iAG9YSLHUHMTuI2oea07Rh4dtIAqPwAX8xn36JAYG
2vgLAAMFB/wKqaycjWAZwIe98Yt0qHsdkpmIbarD9fGiA6kfkK/UxjL/k7tmS4Vm
CljrrDZkPSQ/19mpdRcGXtb0NI9+nyM5trweTvtPw+HPkDiJlTaiCcx+izg79Fj9
KcofuNb3lPdXZb9tzf5oDnmm/B+4vkeTuEZJ//IFty8cmvCpzvY+DAz1Vo9rA+Zn
cpWY1n6z6oSS9AsyT/IFlWWBZZ17SpMHu+h4Bxy62+AbPHKGSujEGQhWq8ZRoJAT
G0KSObnmZ7FwFWu1e9XFoUCt0bSjiJWTIyaObMrWu/LvJ3e9I87HseSJStfw6fki
5og9qFEkMrIrBCp3QGuQWBq/rTdMuwNFiEkEGBECAAkFAkXwb0sCGwwACgkQoECD
D3+sWZF/WACfeNAu1/1hwZtUo1bR+MWiCjpvHtwAnA1R3IHqFLQ2X3xJ40XPuAyY
/FJG
=Quqp
-----END PGP PUBLIC KEY BLOCK-----

so my question is: how do i download that?
do i have to copy it and paste in gedit makin a new file named gutsy.is.no.more.deb?
:biggrin:


thanks
Just right-click on it and select *Save Link As*.

---

### Post by jsf_pp on 2008-11-10
ok guys! i have my public key already.
thanks for your time and helpful help. hahahah
no, really, thanks dudes you rule!
should be ubuntu ppl everywhere.
bye

---

