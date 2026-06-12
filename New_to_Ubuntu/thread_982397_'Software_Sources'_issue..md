---
title: "'Software Sources' issue."
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Obero on 2008-11-14
Just installed Ubuntu a few days ago, so naturally I'm doing all initial protocol to prepare the system and upgrade it as it's a fresh reboot. So now I'm attempting to enable all repositories (including Universe and Multiverse) that Ubuntu provides. *So*, I put this into the 'Terminal:'

```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list && sudo apt-get update
```

This was the output:

```
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid Release.gpg
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_CA      
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_CA
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid Release                     
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages               
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages         
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages               
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages         
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://packages.medibuntu.org intrepid Release.gpg                                                   
Hit http://archive.canonical.com intrepid Release.gpg                                                    
Ign http://archive.canonical.com intrepid/partner Translation-en_CA                                      
Hit http://security.ubuntu.com intrepid-security Release.gpg                                             
Ign http://security.ubuntu.com intrepid-security/main Translation-en_CA                                  
Hit http://ca.archive.ubuntu.com intrepid Release.gpg                                                    
Ign http://ca.archive.ubuntu.com intrepid/main Translation-en_CA                                         
Hit http://ca.archive.ubuntu.com intrepid/restricted Translation-en_CA                               
Ign http://ca.archive.ubuntu.com intrepid/universe Translation-en_CA                                 
Ign http://ca.archive.ubuntu.com intrepid/multiverse Translation-en_CA                               
Hit http://archive.canonical.com intrepid Release                                                    
Hit http://ca.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://ca.archive.ubuntu.com intrepid-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/restricted Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_CA
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/multiverse Translation-en_CA           
Ign http://packages.medibuntu.org intrepid/free Translation-en_CA                        
Hit http://ca.archive.ubuntu.com intrepid-backports Release.gpg                                          
Ign http://ca.archive.ubuntu.com intrepid-backports/main Translation-en_CA                           
Ign http://ca.archive.ubuntu.com intrepid-backports/restricted Translation-en_CA                     
Ign http://ca.archive.ubuntu.com intrepid-backports/universe Translation-en_CA                       
Ign http://ca.archive.ubuntu.com intrepid-backports/multiverse Translation-en_CA                     
Hit http://ca.archive.ubuntu.com intrepid Release                                                        
Hit http://security.ubuntu.com intrepid-security Release                                                 
Hit http://ca.archive.ubuntu.com intrepid-updates Release                                                
Hit http://archive.canonical.com intrepid/partner Packages                                               
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_CA                                    
Hit http://security.ubuntu.com intrepid-security/main Packages                             
Hit http://archive.canonical.com intrepid/partner Sources                                            
Hit http://security.ubuntu.com intrepid-security/restricted Packages                                 
Hit http://security.ubuntu.com intrepid-security/main Sources                                        
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://ca.archive.ubuntu.com intrepid-backports Release
Hit http://packages.medibuntu.org intrepid Release                  
Hit http://security.ubuntu.com intrepid-security/universe Sources   
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Hit http://packages.medibuntu.org intrepid/free Packages                       
Hit http://packages.medibuntu.org intrepid/non-free Packages                   
Hit http://ca.archive.ubuntu.com intrepid/main Packages
Hit http://ca.archive.ubuntu.com intrepid/restricted Packages
Hit http://ca.archive.ubuntu.com intrepid/main Sources
Hit http://ca.archive.ubuntu.com intrepid/restricted Sources
Hit http://ca.archive.ubuntu.com intrepid/universe Packages
Hit http://ca.archive.ubuntu.com intrepid/universe Sources
Hit http://ca.archive.ubuntu.com intrepid/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid/multiverse Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/main Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/main Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://ca.archive.ubuntu.com intrepid-backports/main Packages
Hit http://ca.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://ca.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://ca.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid-backports/main Sources
Hit http://ca.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://ca.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://ca.archive.ubuntu.com intrepid-backports/multiverse Sources
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

So obviously it failed. I then, by advice I was given here earlier, did this: I went to Software Sources and unchecked "Cdrom with Ubuntu 8.10 Intrepid Ibex." I then put the original sudo for the repository updates. However, it failed again.

So I checked the Software Sources, and the the "Cdrom with Ubuntu 8.10 Intrepid Ibex" was still checked. How come it's not stay unchecked?

---

### Post by jenkinbr on 2008-11-14
Try commenting out the entry in /etc/apt/sources.lst by hand - this sometimes happens to me, too.

---

### Post by Obero on 2008-11-14
> **jenkinbr said:**
> Try commenting out the entry in /etc/apt/sources.lst by hand - this sometimes happens to me, too.

Not sure what "commenting out" means, I'm an Absolute Beginner. How do I go about doing this? So, it's a common problem?

---

### Post by jenkinbr on 2008-11-14
Type ```
gksudo gedit /etc/apt/sources.list
``` [fix made here]
and find the entry(s) that start with ```
deb cdrom:///
``` and put a single '#' at the beginning of those lines.(exclude the single quote marks ('). [fix made here]

---

### Post by Obero on 2008-11-14
> **jenkinbr said:**
> Type ```
gksudo gedit /etc/apt/sources.lst
```
and find the entry(s) that start with ```
cdrom:///
``` and put a single '#' in front of it(them).(exclude the single quote marks (').

I did the gksudo gedit /etc/apt/sources.lst, but it seemed like a blank document popped up. What do I do with that? You're going to have to be more specific.

---

### Post by taurus on 2008-11-14
It should be /etc/apt/sources.**list**.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by binbash on 2008-11-14
> **Obero said:**
> I did the gksudo gedit /etc/apt/sources.lst, but it seemed like a blank document popped up. What do I do with that? You're going to have to be more specific.

System > Administration > Synaptic Package Manager

Then

Setting > Repositories > Ubuntu Software
Untick cdroms there

However that gedit command must fix it, it cant be blank if you wrote the correct filename.

---

### Post by Obero on 2008-11-14
> **taurus said:**
> It should be /etc/apt/sources.**list**.

```
gksudo gedit /etc/apt/sources.list
```

Ah, there seems to be only one with 'cdrom' in front of them:

```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

So I would theoretically do this:

```
deb #cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

---

### Post by taurus on 2008-11-14
That is wrong.  The # should go in front.

```

**[COLOR="Blue"]#[/COLOR]**deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

---

### Post by jenkinbr on 2008-11-14
> **Obero said:**
> Ah, there seems to be only one with 'cdrom' in front of them:

```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

So I would theoretically do this:

```
deb #cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

Actually, you'll want to change it to ```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

The '#' is a commenting mark, so the program that comes along and reads this file (apt-get update) will ignore any lines and line segments that have a # in them.  Everything between a '#' and the end of the line will be ignored, and reading will continue at the next line.

Sorry about that, I will go back and fix my earlier post to make it clearer.

---

### Post by Obero on 2008-11-14
> **taurus said:**
> That is wrong.  The # should go in front.

```

**[COLOR="Blue"]#[/COLOR]**deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

Thanks, just tried the original terminal code, and it output "Reading package lists... Done" so I'm pretty sure it worked. This is solved, by any means.

---

### Post by jenkinbr on 2008-11-14
Be sure to mark it as solved in your first post. :)

---

### Post by Francewhoa on 2008-11-14
Adding Repositories in Ubuntu for beginners: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu)

For Ubuntu 7.04 (Feisty Fawn), Ubuntu 7.10 (Gutsy Gibbon), and Ubuntu 8.04 (Hardy Heron)

---

### Post by jenkinbr on 2008-11-14
> **Onopoc said:**
> Adding Repositories in Ubuntu for beginners: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu)

For Ubuntu 7.04 (Feisty Fawn), Ubuntu 7.10 (Gutsy Gibbon), and Ubuntu 8.04 (Hardy Heron)
So far, it's basically the same for all Ubuntu dists, so it should apply to intrepid as well...

---

