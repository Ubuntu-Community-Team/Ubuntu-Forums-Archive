---
title: "update"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by vagelism on 2011-12-06
Hello to all!
When I got notice by synaptics packet manager to make an update I got the error
```
W:Failed to fetch http://ppa.launchpad.net/shawn-p-huang/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/shawn-p-huang/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Any idea on how can I fix this?
Thank you!

---

### Post by Bodsda on 2011-12-06
> **vagelism said:**
> Hello to all!
When I got notice by synaptics packet manager to make an update I got the error
```
W:Failed to fetch http://ppa.launchpad.net/shawn-p-huang/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/shawn-p-huang/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```Any idea on how can I fix this?
Thank you!

Whoever that repository belongs to has remove his oneiric repository, if you browse through the repo you can see he only has karmic, lucid and maverick. You'll have to remove the custom repo, or ignore it.

Bodsda

---

### Post by vagelism on 2011-12-06
And how can I do it?
:)
Thank you!

---

### Post by Bodsda on 2011-12-06
> **vagelism said:**
> And how can I do it?
:)
Thank you!

You can do it via one of the menu's in synaptic
or
You can probably do it via a menu in the Software Center
or
You can edit '/etc/apt/sources.list'

Bodsda

---

### Post by vagelism on 2011-12-06
So if I understand write I only need to remove from this list the links that are dead. Correct?

---

### Post by Bodsda on 2011-12-06
> **vagelism said:**
> So if I understand write I only need to remove from this list the links that are dead. Correct?

Correct

Bodsda

---

### Post by Paqman on 2011-12-06
> **vagelism said:**
> So if I understand write I only need to remove from this list the links that are dead. Correct?

In Synaptic go to System > Repositories > Other Software and uncheck the relevant PPA. You could delete it entirely if you wish.

---

### Post by vagelism on 2011-12-06
> **Bodsda said:**
> Correct

Bodsda


```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu oneiric main # disabled on upgrade to oneiric
# deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu oneiric main # disabled on upgrade to oneiric
# deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner
```

I did a search and I can not find them inside!!!

---

### Post by Bodsda on 2011-12-06
> **vagelism said:**
> I did a search and I can not find them inside!!!

Weird, please run this

```

sudo apt-get update && sudo apt-get upgrade

```

Let me know if you get the same error. Also, please see Paqman's post above and check there.

Thanks,
Bodsda

---

### Post by vagelism on 2011-12-06
Yes I have done these steps many times before! Is one of few I know to do in linux! :)

---

### Post by plucky on 2011-12-06
> **vagelism said:**
> Yes I have done these steps many times before! Is one of few I know to do in linux! :)

PPA's are located in /etc/apt/sources.list.d/

Try ```
ls -l /etc/apt/sources.list.d/
``` to see what is there.

If you open Software Sources,it should be on the "Other Software" tag.

Good Luck

---

### Post by Bodsda on 2011-12-06
> **vagelism said:**
> Yes I have done these steps many times before! Is one of few I know to do in linux! :)

... So, did it help or do you still have the issue? Did you check Synaptic as Paqman suggested?


> **plucky said:**
> PPA's are located in /etc/apt/sources.list.d/

Try ```
ls -l /etc/apt/sources.list.d/
``` to see what is there.

If you open Software Sources,it should be on the "Other Software" tag.

Good Luck

When was that changed?

Bodsda

---

### Post by vagelism on 2011-12-06
> **Bodsda said:**
> ... So, did it help or do you still have the issue? Did you check Synaptic as Paqman suggested?




When was that changed?

Bodsda

I got this result
```
unknown@unknown-DURABOOK:~$ ls -l /etc/apt/sources.list.d/
&#963;&#973;&#957;&#959;&#955;&#959; 68
-rw-r--r-- 1 root root   0 2011-08-20 21:33 jd-team-jdownloader-natty.list
-rw-r--r-- 1 root root  67 2011-08-20 21:33 jd-team-jdownloader-natty.list.save
-rw-r--r-- 1 root root 194 2011-10-27 23:31 loneowais--natty.list
-rw-r--r-- 1 root root 120 2011-10-24 21:10 loneowais--natty.list.distUpgrade
-rw-r--r-- 1 root root 194 2011-10-27 23:31 loneowais--natty.list.save
-rw-r--r-- 1 root root 200 2011-10-27 23:31 loneowais-ppa-natty.list
-rw-r--r-- 1 root root 126 2011-10-24 21:10 loneowais-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 200 2011-10-27 23:31 loneowais-ppa-natty.list.save
-rw-r--r-- 1 root root 220 2011-10-27 23:31 loneowais-renamethemall-natty.list
-rw-r--r-- 1 root root 146 2011-10-24 21:10 loneowais-renamethemall-natty.list.distUpgrade
-rw-r--r-- 1 root root 220 2011-10-27 23:31 loneowais-renamethemall-natty.list.save
-rw-r--r-- 1 root root 226 2011-10-27 23:31 mozillateam-firefox-stable-natty.list
-rw-r--r-- 1 root root 152 2011-10-24 21:10 mozillateam-firefox-stable-natty.list.distUpgrade
-rw-r--r-- 1 root root 226 2011-10-27 23:31 mozillateam-firefox-stable-natty.list.save
-rw-r--r-- 1 root root 138 2011-10-27 23:31 shawn-p-huang-ppa-oneiric.list
-rw-r--r-- 1 root root 200 2011-10-27 23:31 user-ppa-name-natty.list
-rw-r--r-- 1 root root 126 2011-10-24 21:10 user-ppa-name-natty.list.distUpgrade
-rw-r--r-- 1 root root 200 2011-10-27 23:31 user-ppa-name-natty.list.save

```
And now ? What I need to do?
Thank you!

---

### Post by matt_symes on 2011-12-06
Hi

Open a terminal and type (or copy and paste ***case is important****)

```
grep -ZErl "shawn-p-huang" /etc/apt/sources.list.d | sudo xargs -0 rm
```Enter your password. It will not be echoed to the screen.

The type

```
sudo apt-get update
```That should detele it for you.

Kind regards

---

### Post by vagelism on 2011-12-06
> **matt_symes said:**
> Hi

Open a terminal and type (or copy and paste ***case is important****)

```
grep -ZErl "shawn-p-huang" /etc/apt/sources.list.d | sudo xargs -0 rm
```Enter your password. It will not be echoed to the screen.

The type

```
sudo apt-get update
```That should detele it for you.

Kind regards
And now?
It hit some pages and ignored other ```
unknown@unknown-DURABOOK:~$ sudo apt-get update
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com oneiric InRelease
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com oneiric-updates InRelease                                                                               
Hit http://gr.archive.ubuntu.com oneiric Release.gpg                                                                                         
Hit http://gr.archive.ubuntu.com oneiric-updates Release.gpg                                                                                 
Hit http://gr.archive.ubuntu.com oneiric Release                                                                                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.canonical.com oneiric InRelease                                                                                       
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.canonical.com lucid InRelease                                                                                         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://extras.ubuntu.com oneiric InRelease                                                                                           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com oneiric-security InRelease                                                                                
Hit http://gr.archive.ubuntu.com oneiric-updates Release                                                                                     
Hit http://archive.canonical.com oneiric Release.gpg                                                                                         
Hit http://extras.ubuntu.com oneiric Release.gpg                                                                                             
Hit http://security.ubuntu.com oneiric-security Release.gpg                                                                      
Hit http://gr.archive.ubuntu.com oneiric/main Sources                                                                            
Hit http://gr.archive.ubuntu.com oneiric/restricted Sources                                                                      
Hit http://gr.archive.ubuntu.com oneiric/universe Sources                                                                        
Hit http://gr.archive.ubuntu.com oneiric/multiverse Sources                                                                      
Hit http://gr.archive.ubuntu.com oneiric/main i386 Packages                                                                      
Hit http://gr.archive.ubuntu.com oneiric/restricted i386 Packages                                                                
Hit http://gr.archive.ubuntu.com oneiric/universe i386 Packages                                                                  
Hit http://gr.archive.ubuntu.com oneiric/multiverse i386 Packages                                                                
Hit http://gr.archive.ubuntu.com oneiric/main TranslationIndex                                                                   
Hit http://gr.archive.ubuntu.com oneiric/multiverse TranslationIndex                                                             
Hit http://archive.canonical.com lucid Release.gpg                                                                               
Hit http://extras.ubuntu.com oneiric Release                                                                                     
Hit http://security.ubuntu.com oneiric-security Release                                                                                      
Hit http://gr.archive.ubuntu.com oneiric/restricted TranslationIndex                                                                         
Hit http://gr.archive.ubuntu.com oneiric/universe TranslationIndex                                                                           
Hit http://gr.archive.ubuntu.com oneiric-updates/main Sources                                                                                
Hit http://gr.archive.ubuntu.com oneiric-updates/restricted Sources                                                                          
Hit http://gr.archive.ubuntu.com oneiric-updates/universe Sources                                                                            
Hit http://gr.archive.ubuntu.com oneiric-updates/multiverse Sources                                                                          
Hit http://gr.archive.ubuntu.com oneiric-updates/main i386 Packages                                                                          
Hit http://gr.archive.ubuntu.com oneiric-updates/restricted i386 Packages                                                                    
Hit http://gr.archive.ubuntu.com oneiric-updates/universe i386 Packages                                                                      
Hit http://gr.archive.ubuntu.com oneiric-updates/multiverse i386 Packages                                                                    
Hit http://archive.canonical.com oneiric Release                                                                                             
Hit http://extras.ubuntu.com oneiric/main Sources                                                                                            
Hit http://gr.archive.ubuntu.com oneiric-updates/main TranslationIndex                                                                       
Hit http://gr.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex                                                                 
Hit http://gr.archive.ubuntu.com oneiric-updates/restricted TranslationIndex                                                                 
Hit http://gr.archive.ubuntu.com oneiric-updates/universe TranslationIndex                                                                   
Hit http://gr.archive.ubuntu.com oneiric/main Translation-el                                                                                 
Hit http://gr.archive.ubuntu.com oneiric/main Translation-en                                                                                 
Hit http://gr.archive.ubuntu.com oneiric/multiverse Translation-el                                                                           
Hit http://gr.archive.ubuntu.com oneiric/multiverse Translation-en                                                                           
Hit http://gr.archive.ubuntu.com oneiric/restricted Translation-el                                                                           
Hit http://gr.archive.ubuntu.com oneiric/restricted Translation-en                                                                           
Hit http://security.ubuntu.com oneiric-security/main Sources                                                                                 
Hit http://gr.archive.ubuntu.com oneiric/universe Translation-el                                                                 
Hit http://gr.archive.ubuntu.com oneiric/universe Translation-en                                                                 
Hit http://gr.archive.ubuntu.com oneiric-updates/main Translation-en                                                             
Hit http://gr.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                                       
Hit http://gr.archive.ubuntu.com oneiric-updates/restricted Translation-en                                                       
Hit http://gr.archive.ubuntu.com oneiric-updates/universe Translation-en                                                         
Hit http://archive.canonical.com lucid Release                                                                                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                                                                      
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://extras.ubuntu.com oneiric/main TranslationIndex                                                                               
Hit http://security.ubuntu.com oneiric-security/restricted Sources                                                                           
Hit http://security.ubuntu.com oneiric-security/universe Sources                                                                 
Hit http://security.ubuntu.com oneiric-security/multiverse Sources                                                               
Hit http://security.ubuntu.com oneiric-security/main i386 Packages                                                               
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages                                                         
Hit http://archive.canonical.com oneiric/partner i386 Packages                                                                   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.canonical.com oneiric/partner TranslationIndex                                                            
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages                                                           
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages                                                         
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex                                                            
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex                                                      
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex                                                      
Hit http://archive.canonical.com lucid/partner Sources                                                                           
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex                                                        
Hit http://security.ubuntu.com oneiric-security/main Translation-en                                                              
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en                                                        
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en                                                        
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                                                          
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://extras.ubuntu.com oneiric/main Translation-el_GR                                                                  
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.canonical.com oneiric/partner Translation-el_GR                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://extras.ubuntu.com oneiric/main Translation-el                           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.canonical.com oneiric/partner Translation-el                    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://extras.ubuntu.com oneiric/main Translation-en                           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.canonical.com oneiric/partner Translation-en                    
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;      
unknown@unknown-DURABOOK:~$ 

```

THANKS!

---

### Post by matt_symes on 2011-12-06
Hi

> And now?And now you're good to go. :D

Kind regards

---

### Post by vagelism on 2011-12-06
Thank you!!!

---

