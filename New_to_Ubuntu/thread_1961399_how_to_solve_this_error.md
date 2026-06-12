---
title: "how to solve this error"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by Happykarthi22 on 2012-04-19
Hi
 
I am using ubuntu 10.10 as a virtual machine. I need to install eclipse from ubuntu software centre. its not downloading and giving the message
 
Failed to download repository information. Check your internet connection
 
I am able to browse the net. my proxy is also set. what else should i do? any help?

I ranthis command. this was the output

karthika@ubuntu:~$ sudo apt-get install eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eclipse

---

### Post by HiImTye on 2012-04-19
ctrl+alt+t to open a terminal window then type
```
sudo apt-get update
```
and see if you have any errors, if not, try it again

---

### Post by westie457 on 2012-04-19
Hi welcome to UF.

Open a terminal using Ctrl+Alt+T, Type in ```
sudo apt-get install eclipse
```

Type in your password, nothing will show on the screen. Post any error messages here and we will look further into the issue.


EDIT  Just realised something important. 10.10 went End of Life earlier this month and the repositories have been taken off-line.

---

### Post by iponeverything on 2012-04-19
see this thread:
[http://ubuntuforums.org/showthread.php?p=11855835#post11855835](http://ubuntuforums.org/showthread.php?p=11855835#post11855835)

---

### Post by Happykarthi22 on 2012-04-19
> **westie457 said:**
> Hi welcome to UF.

Open a terminal using Ctrl+Alt+T, Type in ```
sudo apt-get install eclipse
```Type in your password, nothing will show on the screen. Post any error messages here and we will look further into the issue.


EDIT  Just realised something important. 10.10 went End of Life earlier this month and the repositories have been taken off-line.



thanks.. this was the output

karthika@ubuntu:~$ sudo apt-get install eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eclipse

---

### Post by Happykarthi22 on 2012-04-19
This was the output
karthika@ubuntu:~$ sudo apt-get install eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eclipse

---

### Post by josephmills on 2012-04-19
could we see a 
```
apt-cache search eclipse
```
and a 
```
cat /etc/apt/sources.list
```

thanks

---

### Post by Happykarthi22 on 2012-04-19
karthika@ubuntu:~$ apt-cache search eclipse
karthika@ubuntu:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory

---

### Post by josephmills on 2012-04-19
> **Happykarthi22 said:**
> karthika@ubuntu:~$ apt-cache search eclipse
karthika@ubuntu:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory

you have to put the space between cat and / 
like 

cat /etc/apt/sources.list

---

### Post by Happykarthi22 on 2012-04-19
This was the output.. thanks a lot for replying me...

karthika@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by josephmills on 2012-04-19
> **Happykarthi22 said:**
> This was the output.. thanks a lot for replying me...

karthika@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse



please open terminal and enter in 

```
gksudo gedit /etc/apt/sources.list
```

Then please make your list look like this 

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
```

proff read save then close 

then do a ```
sudo apt-get update 
```
then see if is there 
```
apt-cache search eclipse
```
if there cool install and mark as solved 
if not post back 
thanks

---

### Post by Happykarthi22 on 2012-04-19
I got this

karthika@ubuntu:~$ gksudo gedit /etc/apt/sources.list
karthika@ubuntu:~$ apt-cache search eclipse
karthika@ubuntu:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release.gpg                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources/DiffIndex                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages/DiffIndex  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources/DiffIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
  407  Proxy Authorization Required [IP: 10.237.125.73 6050]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
  407  Proxy Authorization Required [IP: 10.237.125.73 6050]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
  407  Proxy Authorization Required [IP: 10.237.125.73 6050]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages     
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
  407  Proxy Authorization Required [IP: 10.237.125.73 6050]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
  407  Proxy Authorization Required [IP: 10.237.125.73 6050]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
  407  Proxy Authorization Required [IP: 10.237.125.73 6050]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
  407  Proxy Authorization Required [IP: 10.237.125.82 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
  407  Proxy Authorization Required [IP: 10.237.125.73 6050]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
  407  Proxy Authorization Required [IP: 10.237.125.73 6050]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                      
  407  Proxy Authorization Required [IP: 10.237.125.82 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources               
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.72 6050]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
  407  Proxy Authorization Required [IP: 10.237.125.88 6050]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
  407  Proxy Authorization Required [IP: 10.237.125.88 6050]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.73 6050]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.73 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.73 6050]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.73 6050]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.73 6050]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.73 6050]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.82 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.73 6050]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.73 6050]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.82 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.72 6050]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  407  Proxy Authorization Required [IP: 10.237.125.88 6050]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  407  Proxy Authorization Required [IP: 10.237.125.88 6050]

E: Some index files failed to download, they have been ignored, or old ones used instead.
karthika@ubuntu:~$ apt-cache search eclipse
karthika@ubuntu:~$

---

### Post by josephmills on 2012-04-19
>  Proxy Authorization Required [IP: 10.237.125.88 6050]

E: Some index files failed to download, they have been ignored, or old ones used instead.
karthika@ubuntu:~$ apt-cache search eclipse
karthika@ubuntu:~$


turn your proxy off

---

### Post by Happykarthi22 on 2012-04-19
If i turn of my proxy i can't access internet.

---

### Post by josephmills on 2012-04-19
try this 
[http://askubuntu.com/questions/7470/how-to-run-sudo-apt-get-update-through-proxy-in-commandline](http://askubuntu.com/questions/7470/how-to-run-sudo-apt-get-update-through-proxy-in-commandline)

[http://askubuntu.com/questions/92464/add-apt-repository-wont-work-on-proxy](http://askubuntu.com/questions/92464/add-apt-repository-wont-work-on-proxy)

hope that this helps

---

### Post by Happykarthi22 on 2012-04-25
Thanks a lot for spending your time. this issue got solved..........:popcorn::guitar:

---

