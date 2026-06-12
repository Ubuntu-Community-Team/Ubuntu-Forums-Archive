---
title: "Outdated Update Information"
date: 2015-03-26
forum: New to Ubuntu
---

### Post by Daveski17 on 2015-03-26
Hello, I get a red triangle in the systems tray after the computer has been run for some time claiming my update information is outdated. Can this be removed at all? It is an old Belnea notebook that originally ran Vista.

Thanks, Dave.

[ATTACH=CONFIG]260913[/ATTACH]

---

### Post by deadflowr on 2015-03-26
What happens when you run Software Updater?

---

### Post by Daveski17 on 2015-03-26
> **deadflowr said:**
> What happens when you run Software Updater?

Thanks for your reply. First it informs me that it has failed to download repository information, then when I click 'OK' it goes ahead and updates if there are any.

Dave

[ATTACH=CONFIG]260915[/ATTACH]

---

### Post by DuckHook on 2015-03-26
Please post error output (and only error output) from:```
sudo apt-get update
```Generally, running the command line app will give you error info that the graphical app won't. If no errors, then:```
sudo apt-get dist-upgrade
```...and post any error output from that.

---

### Post by Daveski17 on 2015-03-26
> **DuckHook said:**
> Please post error output (and only error output) from:```
sudo apt-get update
```Generally, running the command line app will give you error info that the graphical app won't. If no errors, then:```
sudo apt-get dist-upgrade
```...and post any error output from that.

Erm ... OK, I'm not good with the terminal, could you tell me exactly how to get the error output. Thanks.

---

### Post by oldos2er on 2015-03-26
You should be able to copy/paste text from terminal into a post here.

---

### Post by grahammechanical on 2015-03-26
You have repositories that are no longer accessible. As you have found out Update Manager can deal with this and continue the Update. But we get the warning message. Have you enabled any repositories such as Personal Package Archives (PPA)?

Yes you have. Disable each of those repositories in turn until you find the one that is causing the warning. The others might be OK.

Regards.

---

### Post by DuckHook on 2015-03-26
> **Daveski17 said:**
> Erm ... OK, I'm not good with the terminal, could you tell me exactly how to get the error output. Thanks.When you bring up a terminal, just copy and paste my commands into the terminal using a right click of your mouse. When you execute the command, it will ask you for your password. Password entry provides no feedback, no ******* placeholders, but it is accepting your entry anyway. After hitting the enter button, a whole set of responses will scroll upward. This is the info that is hidden from you in the graphical app. You are looking for lines that have "WARNING" or "ERROR" in them. You can drag your mouse across the whole mess within the terminal app, right click to copy and then right click again to paste into the response box of this thread.

**Edit**
GrahamMechanical has already Ninja'd the issue. You indeed have a whole bunch of PPAs that are likely causing the problem. If I were you, I would get rid of every one of them and not add any back in until I was more familiar with how Ubuntu works and the security holes that PPAs bring with them.

---

### Post by Daveski17 on 2015-03-26
OK, thanks DuckHook. IIRC I think I tried to update Pinta at some stage. I'm still a noob with Ubuntu and I often experiment on this old Belnea notebook. I have a new Lenovo preinstalled with Ubuntu that I deliberately don't mess with due to the fact that I'm not sure what I'm doing. They say a little knowledge is a dangerous thing lol.

> **grahammechanical said:**
> You have repositories that are no longer accessible. As you have found out Update Manager can deal with this and continue the Update. But we get the warning message. Have you enabled any repositories such as Personal Package Archives (PPA)?

Yes you have. Disable each of those repositories in turn until you find the one that is causing the warning. The others might be OK.

Regards.

Thanks, I'm pretty sure it is the Pinta PPA that's causing this. I'll experiment disabling it.

---

### Post by DuckHook on 2015-03-26
> **Daveski17 said:**
> OK, thanks DuckHook. IIRC I think I tried to update Pinta at some stage. I'm still a noob with Ubuntu and I often experiment on this old Belnea notebook. I have a new Lenovo preinstalled with Ubuntu that I deliberately don't mess with due to the fact that I'm not sure what I'm doing. They say a little knowledge is a dangerous thing lol.Ahh. So it's your play box. If so, feel free to go nuts. No better way to learn than to break and fix.

---

### Post by Geoffrey_Arndt on 2015-03-26
Also, on rare occasions, if the "mirror" server is down temporarily (maint. or planned outage), then you can also see this type of error.    What I usually like to do first (assuming PPA's were all working in recent past), is to go to the first tab of Software Updates and click on "download from" and choose "other" so it finds the best (fastest) available server.   If this doesn't fix, then I disable the ppas one by one.

---

### Post by Daveski17 on 2015-03-27
> **DuckHook said:**
> Ahh. So it's your play box. If so, feel free to go nuts. No better way to learn than to break and fix.

Yeah lol! Reformatting is such a PITA though. ;)

I unchecked the Pinta PPA and ran the Terminal and got this:

```
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://repo.vivaldi.com](http://repo.vivaldi.com) stable InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://repo.vivaldi.com](http://repo.vivaldi.com) stable Release.gpg                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release                                
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release                        
Hit [http://repo.vivaldi.com](http://repo.vivaldi.com) stable Release                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [http://repo.vivaldi.com](http://repo.vivaldi.com) stable/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Ign [http://repo.vivaldi.com](http://repo.vivaldi.com) stable/main Translation-en_GB                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Ign [http://repo.vivaldi.com](http://repo.vivaldi.com) stable/main Translation-en                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Reading package lists... Done
```                     

As of yet the red triangle in the systems tray has not returned.

> **Geoffrey_Arndt said:**
> Also, on rare occasions, if the "mirror" server is down temporarily (maint. or planned outage), then you can also see this type of error.    What I usually like to do first (assuming PPA's were all working in recent past), is to go to the first tab of Software Updates and click on "download from" and choose "other" so it finds the best (fastest) available server.   If this doesn't fix, then I disable the ppas one by one.

OK thanks. I think I know what the culprit PPA is though.

---

### Post by DuckHook on 2015-03-27
> **Daveski17 said:**
> Yeah lol! Reformatting is such a PITA though. ;)

I unchecked the Pinta PPA and ran the Terminal and got this...Output looks fine. Pinta PPA is therefore the culprit. Already said, but PPAs should be avoided unless *absolutely* needed.

Re: re-installing after ****-up:

As you get more comfortable with Linux, you may wish to explore installing a guest OS into a virtual machine. Provided you have a dual-core CPU with 4GB RAM and a discrete GPU with more than 500MB of DRAM, you should be able to run such a VM just fine. It's the best way to experiment with an OS until it breaks. You just roll back to a previous snapshot and everything is fine again. No more need to re-install. Google to learn more.

---

### Post by Daveski17 on 2015-03-27
> **DuckHook said:**
> Output looks fine. Pinta PPA is therefore the culprit. Already said, but PPAs should be avoided unless *absolutely* needed.

Re: re-installing after ****-up:

As you get more comfortable with Linux, you may wish to explore installing a guest OS into a virtual machine. Provided you have a dual-core CPU with 4GB RAM and a discrete GPU with more than 500MB of DRAM, you should be able to run such a VM just fine. It's the best way to experiment with an OS until it breaks. You just roll back to a previous snapshot and everything is fine again. No more need to re-install. Google to learn more.

Thanks, I'll have to chalk this up as a learning curve experience. I've learned not to mess with stuff I don't understand lol. I may look at virtual machines in the future. They look very interesting. I have a Win 7 box and have an image (Macrium Reflect) to go back to in emergency scenarios (bad malware infection, malicious or damaging signature update causing catastrophic false-positives, Patch Tuesday etc ) and I'm pretty sure there is an Ubuntu equivalent. That may be an option too.

[ATTACH=CONFIG]260931[/ATTACH]

I've had the Belnea on for several hours now and it seems fine. No systems tray icon returning either! Thanks again for the help.

Dave

---

### Post by deadflowr on 2015-03-27
You can still try the pinta-daily ppa if you want.
Seems from the screenshot you posted that the ppa was wrong.
The line should have said
```
http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu trusty main
```
but your says
```
http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu ubuntu *<I cannot make out the rest, but does not matter, the second ubuntu entry broke the ppa anyway>*
```
there is no such version of ubuntu called ubuntu.;)

---

### Post by Daveski17 on 2015-03-28
> **deadflowr said:**
> You can still try the pinta-daily ppa if you want.
Seems from the screenshot you posted that the ppa was wrong.
The line should have said
```
http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu trusty main
```
but your says
```
http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu ubuntu *<I cannot make out the rest, but does not matter, the second ubuntu entry broke the ppa anyway>*
```
there is no such version of ubuntu called ubuntu.;)

Oh right, thanks. This is a classic case of GIGO on my part then lol. Or possibly PIBKAC (Problem Is Between Keyboard And Chair)!  :biggrin:

---

### Post by Daveski17 on 2016-03-19
I've pretty well much solved this now, and the culprit was almost certainly Google Chrome.

---

### Post by deadflowr on 2016-03-19
> **Daveski17 said:**
> I've pretty well much solved this now, and the culprit was almost certainly Google Chrome.
Chrome's update problems are more recent, as Google has removed 32-bit versions but the way Google's repository design it caused problems.
People, including myself, had an error occur that stated it could not find the chrome i386-binary packages.
The simple fix was to edit the google-chrome.list file and add [arch=amd64] in between the deb and the http,
like [I]deb [arch=amd64] http ://ubuntu-repo/stuff
[/I]
I think Google fixed it, so you only need to add that once, if using chrome from an older installation.
New, fresh installations of Chrome should not have the problem at all and do not need the quick fix.

---

### Post by Daveski17 on 2016-03-19
> **deadflowr said:**
> Chrome's update problems are more recent, as Google has removed 32-bit versions but the way Google's repository design it caused problems.
People, including myself, had an error occur that stated it could not find the chrome i386-binary packages.
The simple fix was to edit the google-chrome.list file and add [arch=amd64] in between the deb and the http,
like [I]deb [arch=amd64] http ://ubuntu-repo/stuff
[/I]
I think Google fixed it, so you only need to add that once, if using chrome from an older installation.
New, fresh installations of Chrome should not have the problem at all and do not need the quick fix.

Interestingly I started getting the red triangle systems tray alert on my Lenovo (x64). When I checked on the problem it seemed to indicate an issue with Chrome's updating. I've uninstalled Chrome and replaced it with Chromium from the repo. I've had my laptop running for approximately five hours now with no sign of the red triangle. Also there are no failed downloads either now. So, I should have stuck to Chromium lol.

---

