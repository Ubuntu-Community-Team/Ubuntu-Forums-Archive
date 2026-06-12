---
title: "Unable to Install Wine"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by TechnoSparks on 2012-11-03
Hello!
I have searched for tutorials on how to install Wine. Yes I found them and I know, it has a special way to install it. However when I tried to install wine using the terminal, it returns an error. When I get into Wine's forum, the moderator asks me to get to Ubuntu Forum. So here I am. I've attached a screenshot of terminal. Oh and I am a really really new Ubuntu user. Please tell me in detail about something. Thank you! :)

---

### Post by newb85 on 2012-11-03
Welcome!

My guess is you don't have the Universe and Multiverse repositories enabled.

Please give the output of 
```
cat /etc/apt/sources.list
```

When you post an output from the terminal, copy and paste, rather than using a screenshot.  (The keyboard shortcut for copy in the terminal is Ctrl+Shift+C.)  Also, surround it with code tags, like this:

[noparse]```
Output
Here
```[/noparse]

---

### Post by ibjsb4 on 2012-11-03
Or just go to your software sources and make sure they are checked.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by TechnoSparks on 2012-11-04
> **newb85 said:**
> Welcome!

My guess is you don't have the Universe and Multiverse repositories enabled.

Please give the output of 
```
cat /etc/apt/sources.list
```

When you post an output from the terminal, copy and paste, rather than using a screenshot.  (The keyboard shortcut for copy in the terminal is Ctrl+Shift+C.)  Also, surround it with code tags, like this:

[noparse]```
Output
Here
```[/noparse]

I copied the result manually. It seems the CTRL+SHIFT+C is not working in the terminal :-? Here it is:
```
technosparks@ubuntu:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse
technosparks@ubuntu:~$ 

```

---

### Post by TechnoSparks on 2012-11-04
> **ibjsb4 said:**
> Or just go to your software sources and make sure they are checked.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

I've tried added a new repository:
```
ppa:ubuntu-wine/ppa
```
But the Software Sources does not seems to be adding that repository. Is that the cause of all of this mess?

---

### Post by newb85 on 2012-11-04
So, did you use the
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
command?  If so, you also need to run
```
sudo apt-get update
```
so that the contents of that PPA are included in the available software cache.

---

### Post by TechnoSparks on 2012-11-04
> **newb85 said:**
> So, did you use the
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```command?  If so, you also need to run
```
sudo apt-get update
```so that the contents of that PPA are included in the available software cache.

Yes, I  have done that. In the end, it returns as what in the screenshot shows. This what it gives when performing command
```
technosparks@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for technosparks: 
You are about to add the following PPA to your system:
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: https://launchpad.net/~ubuntu-wine/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmplizviq/secring.gpg' created
gpg: keyring `/tmp/tmplizviq/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmplizviq/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```
```
technosparks@ubuntu:~$ sudo apt-get update
Ign http://security.ubuntu.com quantal-security InRelease                      
Ign http://archive.ubuntu.com quantal InRelease                                
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://security.ubuntu.com quantal-security Release.gpg                    
Ign http://archive.ubuntu.com quantal-updates InRelease                        
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://deb.opera.com stable InRelease                                      
Hit http://security.ubuntu.com quantal-security Release                        
Hit http://archive.ubuntu.com quantal Release.gpg                              
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://greenwap.tk quantal InRelease                                       
Hit http://security.ubuntu.com quantal-security/main amd64 Packages            
Hit http://archive.ubuntu.com quantal-updates Release.gpg                      
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://deb.opera.com stable Release                                        
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages      
Hit http://archive.ubuntu.com quantal Release                                  
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Ign http://greenwap.tk quantal Release.gpg                                     
Hit http://security.ubuntu.com quantal-security/universe amd64 Packages        
Hit http://archive.ubuntu.com quantal-updates Release                          
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://security.ubuntu.com quantal-security/multiverse amd64 Packages      
Hit http://archive.ubuntu.com quantal/main amd64 Packages                      
Hit http://ppa.launchpad.net quantal/main Sources                              
Ign http://greenwap.tk quantal Release                                         
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages                
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://security.ubuntu.com quantal-security/main Translation-en            
Hit http://archive.ubuntu.com quantal/universe amd64 Packages                  
Err http://greenwap.tk quantal/main Sources                                    
  
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages                
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Hit http://archive.ubuntu.com quantal/main Translation-en_GB                   
Hit http://ppa.launchpad.net quantal/main Sources                              
Err http://greenwap.tk quantal/main Sources                                    
  
Hit http://archive.ubuntu.com quantal/main Translation-en                      
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Err http://greenwap.tk quantal/main Sources                                    
  
Hit http://archive.ubuntu.com quantal/multiverse Translation-en_GB             
Hit http://archive.ubuntu.com quantal/multiverse Translation-en                
Hit http://security.ubuntu.com quantal-security/universe Translation-en        
Hit http://archive.ubuntu.com quantal/restricted Translation-en_GB             
Err http://greenwap.tk quantal/main Sources                                    
  
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Hit http://archive.ubuntu.com quantal/restricted Translation-en                
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://archive.ubuntu.com quantal/universe Translation-en_GB               
Err http://greenwap.tk quantal/main Sources                                    
  404  Not Found
Hit http://archive.ubuntu.com quantal/universe Translation-en        
Hit http://archive.ubuntu.com quantal-updates/main amd64 Packages    
Hit http://archive.ubuntu.com quantal-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/main Translation-en    
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_GB          
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://security.ubuntu.com quantal-security/main Translation-en_GB
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_GB
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_GB
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_GB
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en
Ign http://security.ubuntu.com quantal-security/universe Translation-en_GB
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_GB
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_GB
W: Failed to fetch http://greenwap.tk/dists/quantal/main/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
```
technosparks@ubuntu:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: ttf-droid
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by ibjsb4 on 2012-11-04
try

sudo dpkg --configure -a

---

### Post by TechnoSparks on 2012-11-05
> **ibjsb4 said:**
> try

sudo dpkg --configure -a

Done this command. The terminal returns nothing, so I proceed to **sudo apt-get update** then **sudo apt-get install wine1.4** but the same problem occured. Can I ask something, is this have to do with incompatible OS version? Mine is Ubuntu 12.10.

---

### Post by newb85 on 2012-11-05
Seems to me that the issue at hand is the fact that wine1.4 has wine1.4-i386 listed as a dependency (also true of 12.04), and wine1.4-i386 isn't available in the amd64 repositories.

---

### Post by SBMN7 on 2012-11-05
why, share your problems with details.

---

### Post by TechnoSparks on 2012-11-05
> **newb85 said:**
> Seems to me that the issue at hand is the fact that wine1.4 has wine1.4-i386 listed as a dependency (also true of 12.04), and wine1.4-i386 isn't available in the amd64 repositories.
So does this mean I have to wait until a compatible development? :(

---

### Post by TechnoSparks on 2012-11-05
> **SBMN7 said:**
> why, share your problems with details.

I can't install Wine via Terminal nor Software Center :( I am new user to Ubuntu, so I can't tell more about my problem.

---

### Post by newb85 on 2012-11-05
> **TechnoSparks said:**
> So does this mean I have to wait until a compatible development? :(

It's a bug.
[https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/1004217](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/1004217)
Mark it as affecting you.

Oh, actually, I just found this.
[http://askubuntu.com/questions/153907/dependency-problems-installing-wine-1-5-on-ubuntu-12-04-x64](http://askubuntu.com/questions/153907/dependency-problems-installing-wine-1-5-on-ubuntu-12-04-x64)
Pay attention to the first answer.

---

### Post by TechnoSparks on 2012-11-05
> **newb85 said:**
> It's a bug.
[https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/1004217](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/1004217)
Mark it as affecting you.

Oh, actually, I just found this.
[http://askubuntu.com/questions/153907/dependency-problems-installing-wine-1-5-on-ubuntu-12-04-x64](http://askubuntu.com/questions/153907/dependency-problems-installing-wine-1-5-on-ubuntu-12-04-x64)
Pay attention to the first answer.

Marked it. The first answer doesn't overcome my problem :( It gives something that makes me really more scared
```
Unknown configuration key `foreign-architecture' found in your `dpkg'
configuration files.  This warning will become a hard error at a later
date, so please remove the offending configuration options and replace
them with `dpkg --add-architecture' invocations at the command line.
```
What should I do?

---

### Post by newb85 on 2012-11-05
Sorry, I should have checked that solution out a little more before linking it.  On my system, the line that solution added was already present in the file, so it very likely added a second occurrence of the line.

If you run
```
sudo gedit /etc/dpkg/dpkg.cfg.d/multiarch
```
does the file show duplicates of the line
```
foreign-architecture i386
```
?

If so, you should probably remove one of them.

As for the chmod part of that answer, it shouldn't have changed anything, as those are the default permissions of that file.

---

### Post by TechnoSparks on 2012-11-06
> **newb85 said:**
> Sorry, I should have checked that solution out a little more before linking it.  On my system, the line that solution added was already present in the file, so it very likely added a second occurrence of the line.

If you run
```
sudo gedit /etc/dpkg/dpkg.cfg.d/multiarch
```does the file show duplicates of the line
```
foreign-architecture i386
```?

If so, you should probably remove one of them.

As for the chmod part of that answer, it shouldn't have changed anything, as those are the default permissions of that file.

Nope, there's no duplication. :)

---

### Post by newb85 on 2012-11-06
> **TechnoSparks said:**
> Nope, there's no duplication. :)

What exactly does /etc/dpkg/dpkg.cfg.d/multiarch contain?

---

### Post by TechnoSparks on 2012-11-06
> **newb85 said:**
> What exactly does /etc/dpkg/dpkg.cfg.d/multiarch contain?
It contains ```
foreign-architecture i386
``` only. In one line.

---

