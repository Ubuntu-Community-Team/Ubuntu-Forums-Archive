---
title: "[SOLVED] Problems with update manager"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by RoyHobbs on 2008-09-03
Hi

I have been getting the following problem when I run update manager, any ideas?

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by iaculallad on 2008-09-03
> **RoyHobbs said:**
> Hi

I have been getting the following problem when I run update manager, any ideas?

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Try changing your Download server. System->Administration->Software Sources, "Ubuntu Software' tab, "Download From:" Change it to Main Server.

---

### Post by RoyHobbs on 2008-09-03
> **iaculallad said:**
> Try changing your Download server. System->Administration->Software Sources, "Ubuntu Software' tab, "Download From:" Change it to Main Server.
Hi

Thanks for the quick reply, I changed the server and still got this message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by iaculallad on 2008-09-03
Ok. Now on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

EDIT: My Error, I didn't check the link you posted. You can do a clean install on later versions of Ubuntu as Edgy reached it's End-Of-Life.

---

### Post by annatar on 2008-09-03
According to the link in your error message, you are still using Ubuntu Edgy / 6.10, right?

Please upgrade ASAP as no more updates will be provided and existing edgy packages have been removed from repository.

---

### Post by Malac on 2008-09-03
> **RoyHobbs said:**
> Hi
 
I have been getting the following problem when I run update manager, any ideas?
 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.
That's because it's not there nor anything for edgy.?????
Check the URL in a browser there is no edgy branch for some reason.
See here:
[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)
 
Don't know why, perhaps it'll come back eventually.

---

### Post by irrdev on 2008-09-03
Edgy was no longer supported as of April 25th, 2008. Ubuntu 6.04 "Dapper" is still in the repositories, however, because it was a Long-Term-Support (LTS) release. [Check out this page to see a list of Ubuntu releases and their support durations]("http://en.wikipedia.org/wiki/Ubuntu#Release_history"). Sorry, but you really are going to have to upgrade in order to install new software from the repositories. :wink:

**EDIT:** Actually, you won't have to upgrade to still access the repositories! All old repositories are moved here -> [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) . Simply add the dapper repositories to your software sources list, and everything should work fine. I would still recommend you upgrade, though, as Hardy does offer a lot of new and interesting features.

---

### Post by RoyHobbs on 2008-09-03
> **irrdev said:**
> Edgy was no longer supported as of April 25th, 2008. Ubuntu 6.04 "Dapper" is still in the repositories, however, because it was a Long-Term-Support (LTS) release. [Check out this page to see a list of Ubuntu releases and their support durations]("http://en.wikipedia.org/wiki/Ubuntu#Release_history"). Sorry, but you really are going to have to upgrade in order to install new software from the repositories. :wink:

**EDIT:** Actually, you won't have to upgrade to still access the repositories! All old repositories are moved here -> [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) . Simply add the dapper repositories to your software sources list, and everything should work fine. I would still recommend you upgrade, though, as Hardy does offer a lot of new and interesting features.

Hi

I am using the latest version (ubuntu 8.04) and I am still having this problem????

---

### Post by RoyHobbs on 2008-09-03
> **iaculallad said:**
> Ok. Now on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

EDIT: My Error, I didn't check the link you posted. You can do a clean install on later versions of Ubuntu as Edgy reached it's End-Of-Life.

Hi

I am using Ubuntu 8.04 so I am using the latest version?  I ran your script and got the following:
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg                              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg                           
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_AU               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_AU                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_AU               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_AU                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_AU               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_AU                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_AU               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by iaculallad on 2008-09-03
RoyHobbs,

It would be better if you comment out those lines containing the Edgy (Repository) in your sources.list file since you are into Hardy's repository and you won't be needing it either.

To comment it out, open your sources.list file for editing:

```
gksudo gedit /etc/apt/sources.list
```

Save and Close, and on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Elfy on 2008-09-03
Edit your sources list and remove all the lines which have edgy in them

```
gksudo gedit /etc/apt/sources.list
```

All you should be left with are hardy references - if you have 3rd party repos - ie not ubuntu check them, once done save and close the file and run

```
sudo apt-get update
```
Come back with errors or any questions, if you are not sure about what to remove run this and paste the result

```
cat /etc/apt/sources.list
```

---

### Post by RoyHobbs on 2008-09-03
> **iaculallad said:**
> RoyHobbs,

It would be better if you comment out those lines containing the Edgy (Repository) in your sources.list file since you are into Hardy's repository and you won't be needing it either.

To comment it out, open your sources.list file for editing:

```
gksudo gedit /etc/apt/sources.list
```

Save and Close, and on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

THANKYOU THANKYOU THANKYOU!  This worked perfectly!

---

