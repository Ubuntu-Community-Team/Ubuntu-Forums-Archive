---
title: "[SOLVED] trouble updating"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Xovan on 2008-09-22
[FONT="Courier New"]I keep getting this error when I go into synaptic.
[/FONT]
[FONT="Lucida Console"]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Sub-process report-mirror-failure returned an error code (1)Couldn't report problem to ''[/FONT]

This happened after I went into software sources and added a few third party sources and included that I wanted recommended updates as well as the long term updates.  I tried to run an update and got the error.   _But_ when I removed the ones I added and put everything back the way it was (US server, long term updates) it kept giving me the same error.  So I suppose that there is something wrong with my configuration.  Since both the US and Main servers shouldn't be down.  So what did I do wrong or is nothing wrong?

*edit*
I can still download and install stuff from synaptic so as those kids say "LOL WUT?"

I'm suspicious that this error is nothing to be worried about but can somebody tell me if I did anything wrong?

---

### Post by Ryadt on 2008-09-22
Can you try ```
sudo apt-get update
```

---

### Post by Xovan on 2008-09-22
I get the following stuff

Ign mirror://www.getdeb.net hardy/ Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign mirror://www.getdeb.net hardy/ Translation-en_US                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign mirror://www.getdeb.net hardy/ Release                           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign mirror://www.getdeb.net hardy/ Packages                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release               
61% [Waiting for headers] [Waiting for headers] [Waiting for headers]Traceback (most recent call last):
  File "/usr/lib/apt/apt-report-mirror-failure", line 8, in <module>
    url = apt_pkg.Config.Find("Acquire::Mirror::ReportFailures", None)
TypeError: argument 2 must be string, not None
Err mirror://www.getdeb.net hardy/ Packages                          
  403 Forbidden [IP: 208.209.50.16 80]
E: Sub-process report-mirror-failure returned an error code (1)      
W: Couldn't report problem to ''
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by fuhrysteve on 2008-09-22
if ```
sudo apt-get update
``` doesn't work, maybe your repository file is messed up or something..

if that's the case, you could try replacing it:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup && sudo cp /usr/share/doc/apt/examples/sources.list /etc/apt/sources.list
```

and check out System => Administration => Software Sources to see what's up

---

### Post by fuhrysteve on 2008-09-22
> **Xovan said:**
> 
E: Sub-process report-mirror-failure returned an error code (1)      
W: Couldn't report problem to ''
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

that means you have another instance of apt running (or synaptic). make sure you close Synaptic Package manager, and make sure you don't have apt running.

if you're absolutely sure it's not running anywhere, you could remove the lock manually like so:

```
sudo rm /var/lib/dpkg/lock
```

---

### Post by Ryadt on 2008-09-22
Can you close synaptic or any package manager that you have opened and then re-run the command.

---

### Post by Xovan on 2008-09-22
lol closed synaptic and it changed slightly

Ign mirror://www.getdeb.net hardy/ Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Ign mirror://www.getdeb.net hardy/ Translation-en_US                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources            
Ign mirror://www.getdeb.net hardy/ Release                                  
Ign mirror://www.getdeb.net hardy/ Packages           
95% [Working]Traceback (most recent call last):
  File "/usr/lib/apt/apt-report-mirror-failure", line 8, in <module>
    url = apt_pkg.Config.Find("Acquire::Mirror::ReportFailures", None)
TypeError: argument 2 must be string, not None
Err mirror://www.getdeb.net hardy/ Packages
  403 Forbidden [IP: 208.209.50.16 80]
E: Sub-process report-mirror-failure returned an error code (1)
W: Couldn't report problem to ''

---

### Post by Xovan on 2008-09-22
> **fuhrysteve said:**
> if ```
sudo apt-get update
``` doesn't work, maybe your repository file is messed up or something..

if that's the case, you could try replacing it:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup && sudo cp /usr/share/doc/apt/examples/sources.list /etc/apt/sources.list
```

and check out System => Administration => Software Sources to see what's up

I tried that no change.

---

### Post by Ryadt on 2008-09-22
Try this command a few times ```
sudo apt-get -f install
``` and then retry to update ```
sudo apt-get update
```

---

### Post by fuhrysteve on 2008-09-22
> **Xovan said:**
> 
Ign mirror://www.getdeb.net hardy/ Packages           
95% [Working]Traceback (most recent call last):
  File "/usr/lib/apt/apt-report-mirror-failure", line 8, in <module>
    url = apt_pkg.Config.Find("Acquire::Mirror::ReportFailures", None)
TypeError: argument 2 must be string, not None
Err mirror://www.getdeb.net hardy/ Packages
  403 Forbidden [IP: 208.209.50.16 80]
E: Sub-process report-mirror-failure returned an error code (1)
W: Couldn't report problem to ''

go into **System => Administration => Software Sources** and disable getdeb.net under Third party software.. sounds like something's wrong with the way that repository is set up.

---

### Post by Xovan on 2008-09-22
Hey that did it.

---

### Post by gsimpson on 2008-09-22
Fixed my update problems, thanks fuhrysteve post #4

---

