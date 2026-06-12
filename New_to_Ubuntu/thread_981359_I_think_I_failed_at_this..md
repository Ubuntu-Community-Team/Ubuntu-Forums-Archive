---
title: "I think I failed at this."
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Obero on 2008-11-13
I think I screwed something up.

I did this in the terminal:

```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list && sudo apt-get update
```

and this was the output:

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
Hit http://ca.archive.ubuntu.com intrepid Release.gpg                          
Ign http://ca.archive.ubuntu.com intrepid/main Translation-en_CA               
Hit http://ca.archive.ubuntu.com intrepid/restricted Translation-en_CA         
Ign http://ca.archive.ubuntu.com intrepid/universe Translation-en_CA           
Get:1 http://archive.canonical.com intrepid Release.gpg [189B]                 
Ign http://archive.canonical.com intrepid/partner Translation-en_CA            
Ign http://ca.archive.ubuntu.com intrepid/multiverse Translation-en_CA         
Hit http://ca.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://ca.archive.ubuntu.com intrepid-updates/main Translation-en_CA       
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_CA        
Ign http://ca.archive.ubuntu.com intrepid-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-updates/multiverse Translation-en_CA
Get:2 http://ca.archive.ubuntu.com intrepid-backports Release.gpg [189B]       
Get:3 http://archive.canonical.com intrepid Release [7007B]                    
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_CA  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_CA    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_CA  
Ign http://ca.archive.ubuntu.com intrepid-backports/main Translation-en_CA     
Ign http://ca.archive.ubuntu.com intrepid-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com intrepid-backports/universe Translation-en_CA 
Ign http://ca.archive.ubuntu.com intrepid-backports/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com intrepid Release                              
Hit http://ca.archive.ubuntu.com intrepid-updates Release                      
Get:4 http://ca.archive.ubuntu.com intrepid-backports Release [44.0kB]         
Hit http://security.ubuntu.com intrepid-security Release                       
Ign http://packages.medibuntu.org intrepid/free Translation-en_CA              
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Get:5 http://archive.canonical.com intrepid/partner Packages [1470B]           
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Get:6 http://archive.canonical.com intrepid/partner Sources [668B]             
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_CA          
Hit http://security.ubuntu.com intrepid-security/universe Sources           
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Hit http://packages.medibuntu.org intrepid Release                             
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
Get:7 http://ca.archive.ubuntu.com intrepid-backports/main Packages [60.6kB]   
Get:8 http://ca.archive.ubuntu.com intrepid-backports/restricted Packages [14B]
Get:9 http://ca.archive.ubuntu.com intrepid-backports/universe Packages [1703B]
Get:10 http://ca.archive.ubuntu.com intrepid-backports/multiverse Packages [14B]
Get:11 http://ca.archive.ubuntu.com intrepid-backports/main Sources [10.0kB]   
Get:12 http://ca.archive.ubuntu.com intrepid-backports/restricted Sources [14B]
Get:13 http://ca.archive.ubuntu.com intrepid-backports/universe Sources [415B] 
Get:14 http://ca.archive.ubuntu.com intrepid-backports/multiverse Sources [14B]
Fetched 126kB in 16s (7618B/s)                                                 
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I think it failed, any reason why?

---

### Post by CLomax on 2008-11-13
If your 'Software Sources -> Third Party Software' section has the CD ticked you'd need the CD in the drive for it to be any use. If it isn't there it complains.

Since you don't need that box ticked, untick it... assuming it is ticked.

Now give that command another go and let us know if it helped ;)

EDIT: By the looks of what you've given, the CD box is definitely ticked.

EDIT2: After trying that command for myself it failed in pretty much the same way even with the CD box unticked :(

Try sticking your Ubuntu CD in and giving it another go.

---

### Post by mapes12 on 2008-11-13
What is it that you are trying to accomplish please?

---

### Post by Obero on 2008-11-13
> **mapes12 said:**
> What is it that you are trying to accomplish please?

I'm reading this off an ubuntu website, but I'm trying to "enable all repositaries (including all universal and mediubuntu ones)."

---

### Post by Crafty Kisses on 2008-11-13
I'm pretty sure you have to disable the CD, in Synaptic uncheck the CD icon, and refresh or you can run the following:
```
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Obero on 2008-11-13
> **CLomax said:**
> If your 'Software Sources -> Third Party Software' section has the CD ticked you'd need the CD in the drive for it to be any use. If it isn't there it complains.

Since you don't need that box ticked, untick it... assuming it is ticked.

Now give that command another go and let us know if it helped ;)

EDIT: By the looks of what you've given, the CD box is definitely ticked.

EDIT2: After trying that command for myself it failed in pretty much the same way even with the CD box unticked :(

Try sticking your Ubuntu CD in and giving it another go.

You mean this, if so, what do I do?

[[img]http://localhost/images/1275290458.png[/img]](http://localhost/)

---

### Post by Obero on 2008-11-13
> **Codename said:**
> I'm pretty sure you have to disable the CD, in Synaptic uncheck the CD icon, and refresh or you can run the following:
```
sudo apt-get update && sudo apt-get upgrade

```

How do I go about doing this exactly? Where do I check off the CD icon in Synaptic?

---

### Post by CLomax on 2008-11-13
> **Obero said:**
> You mean this, if so, what do I do?

[[img]http://localhost/images/1275290458.png[/img]](http://localhost/)

I'd ignore that and do what Codename suggested.

---

### Post by Obero on 2008-11-13
> **CLomax said:**
> I'd ignore that and do what Codename suggested.

Not too sure how to uncheck the CD icon in Synaptic. I should probably note, I'm a newbie at Ubuntu.

---

### Post by jimv on 2008-11-13
Go to System > Administration > Software Sources and uncheck the CD-Rom option near the bottom.

---

### Post by oldos2er on 2008-11-13
"Not too sure how to uncheck the CD icon in Synaptic."

 It's under Settings, Repositories.

---

### Post by Therion on 2008-11-13
Go to **System/Software Sources**:

[IMG]http://www.mattcutts.com/images/ubuntu-dvdrom-package.png[/IMG]

Uncheck the box at the bottom as shown in the pic above.  Don't worry that it says "Gutsy Gibbon" in the pic.  
That's the "CD box" you are looking for and it needs to be "unchecked".

Open at Terminal and type in (or use Cut and Paste):```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by doas777 on 2008-11-13
for medibuntu, follow these directions: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

good luck,
franklin

---

