---
title: "Update causes error,that compromises all installations, Lubuntu 12.04"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by darkdragonlon on 2012-08-08
Hello,

When I first installed Lubuntu 12.04 everything worked fine and I was able to install software from the excellent Software Centre.

By running the update manager, I of course found many updates available, I chose to update the system with all available updates selected (very long list).

The update dets to the "configuring ntp" stage and gives me the following error:

* Starting NTP server ntpd
*** glibc detected *** lockfile-create free (): invalid text size (fast): 0x081d2008 ***
*** glibc detected *** lockfile-create: malloc (): memory corruption (fast): 0x081d2048

Now, I understand that the NTP server is related to the time and date of the system, but why should this block tha update installation? Moreover, the application freezes and I can do nothing but restart.

From then onward, all application installations from the Software centre give me the same error, so I cannot install anything.

I have checked both the HDD drive and the Ram for errors and they're fine, I have reinstalled the OS once already (just in case) but have no idea how to proceed further. I also tried running an "install NTP" command line (sorry for not reporting it but I can't remember it) but gett the same error.

Can anyone give me any suggestions on what to do? I haven't been able to find anything similar on this or any other forum.

Thank you all.

---

### Post by Wim Sturkenboom on 2012-08-08
Can you still do normal work with your system? Recovery mode?

If so, you might be able to uninstall the ntpd server. I'm however not sure how (*sudo apt-get remove some-package*).

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366) might help to find installed packages; check for stuff starting with ntp and uninstall with apt-get or synaptic.

Use at own risk !

---

### Post by NikTh on 2012-08-08
Hi , 
please open a terminal(ctrl+alt+t) and post the results of these commands 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
  	 	 	 	 	 	   Put the results inside [CODE] tags by highlighting the output and then click on the  [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.
Thanks

---

### Post by darkdragonlon on 2012-08-08
Thank you both for your responses.

I can work on everything with no problem, I am actually posting from the same PC. Only installation does not work, giving aforementioned errors and then resulting unclosable unless I kill the job.

About the feedback from the two commands, here they are:

First

```
darkdragonlon@darkdragonlon-HP-Compaq-6510b-GR690ET-ABZ:~$ sudo apt-get update
Ign http://it.archive.ubuntu.com precise InRelease
Ign http://it.archive.ubuntu.com precise-updates InRelease                                             
Ign http://it.archive.ubuntu.com precise-backports InRelease                                            
Hit http://it.archive.ubuntu.com precise Release.gpg                                                    
Hit http://it.archive.ubuntu.com precise-updates Release.gpg                                            
Ign http://security.ubuntu.com precise-security InRelease            
Hit http://it.archive.ubuntu.com precise-backports Release.gpg       
Ign http://extras.ubuntu.com precise InRelease 
Hit http://it.archive.ubuntu.com precise Release
Hit http://it.archive.ubuntu.com precise-updates Release                                    
Hit http://security.ubuntu.com precise-security Release.gpg                                 
Hit http://extras.ubuntu.com precise Release.gpg                     
Hit http://it.archive.ubuntu.com precise-backports Release
Hit http://it.archive.ubuntu.com precise/main Sources                                       
Hit http://it.archive.ubuntu.com precise/restricted Sources          
Hit http://it.archive.ubuntu.com precise/universe Sources
Hit http://it.archive.ubuntu.com precise/multiverse Sources
Hit http://it.archive.ubuntu.com precise/main i386 Packages
Hit http://it.archive.ubuntu.com precise/restricted i386 Packages
Hit http://it.archive.ubuntu.com precise/universe i386 Packages
Hit http://security.ubuntu.com precise-security Release              
Hit http://it.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://it.archive.ubuntu.com precise/main TranslationIndex       
Hit http://it.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://extras.ubuntu.com precise Release                         
Hit http://it.archive.ubuntu.com precise/restricted TranslationIndex  
Hit http://it.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://it.archive.ubuntu.com precise-updates/main Sources        
Hit http://it.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://it.archive.ubuntu.com precise-updates/universe Sources    
Hit http://it.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://it.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://security.ubuntu.com precise-security/main Sources         
Hit http://it.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://it.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://it.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://extras.ubuntu.com precise/main Sources                    
Hit http://it.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://it.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://it.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://it.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://it.archive.ubuntu.com precise-backports/main Sources      
Hit http://it.archive.ubuntu.com precise-backports/restricted Sources
Hit http://it.archive.ubuntu.com precise-backports/universe Sources  
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages              
Ign http://extras.ubuntu.com precise/main TranslationIndex           
Hit http://it.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://it.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://it.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://it.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://it.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://it.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://it.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://it.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://it.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://it.archive.ubuntu.com precise/main Translation-en
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://it.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://it.archive.ubuntu.com precise/restricted Translation-en   
Hit http://it.archive.ubuntu.com precise/universe Translation-en     
Hit http://it.archive.ubuntu.com precise-updates/main Translation-en 
Hit http://it.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://it.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://security.ubuntu.com precise-security/main Translation-en  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://it.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://it.archive.ubuntu.com precise-backports/main Translation-en
Hit http://it.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://it.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://it.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

second

```
darkdragonlon@darkdragonlon-HP-Compaq-6510b-GR690ET-ABZ:~$ sudo apt-get dist-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

I have run the commands straight after reboot.

I then proceeded to execute the command specified in the error message:

```
darkdragonlon@darkdragonlon-HP-Compaq-6510b-GR690ET-ABZ:~$ sudo dpkg --configure -a
Setting up pulseaudio-utils (1:1.1-0ubuntu15.1) ...
Setting up ntp (1:4.2.6.p3+dfsg-1ubuntu3.1) ...
 * Starting NTP server ntpd                                                                                                                                  *** glibc detected *** lockfile-create: free(): invalid next size (fast): 0x0a030008 ***
*** glibc detected *** lockfile-create: malloc(): memory corruption (fast): 0x0a030048 ***
```

Any ideas on what the problem may be?

Thanks again.

---

### Post by NikTh on 2012-08-08
Hi , 
I searched your error message and found this bug --> [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/971314](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/971314). 
It is a specific bug to ntp package. Take a look on commends , maybe help you. 

Thanks

---

### Post by darkdragonlon on 2012-08-08
Ok, Thanks!

The problem, in the end, was having a hostname longer than 16 characters.

Thank you everyone!

---

