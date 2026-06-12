---
title: "Update Fail in 14.04 LTS"
date: 2015-06-28
forum: New to Ubuntu
---

### Post by jack117 on 2015-06-28
Automatic updates tries to dowload files but some files don't dowload and it eventually shows failed to download updates. 

How do I resolve this?

and can I upgrade from 14.04 to 15.04 with out formatting?

---

### Post by Bashing-om on 2015-06-28
jack117; Hello .

Show us what the situation is by posting the output of terminal commands :
```

sudo apt-get update
sudo apt-get upgrade

```
That output will give us clues and hints where the problem may lie.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

As to a in-release upgrade; That provision is available in the update manager. make sure 
a) the system is fully updated with the current operating system;
b) All 3rd party sources are disabled/reverted to standard
c) screen-saver is disabled
d) in update manager the check box for "next release" is checked.

This will take you to 14.10 -> repeat the process to get 15.04 .

Then in the update manager choose to do the release upgrade, and you are well on your way.

Keep aware:
14.04 is a Long Term support release with support 'till April of 2019
15.04 only has support for 9 months from time of release. it's support will cease Jan 2016 .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT][INDENT]can do[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-06-28
You would not be the first person in recent weeks to think that upgrading to a newer release would fix problems only to find that it was not fixed. If Update Manager is unable to download files to update the system, then it is likely that the upgrade to the next version will also be broken.

Unless, of course, you are thinking about doing a fresh installation of a newer release. Doing that can often fix problems. Depending on the kind of problem.

Regards.

---

### Post by Geoffrey_Arndt on 2015-06-28
I've had good luck in handling the "could not download all packages" message is by choosing another download server, then reloading the repository database.   This is easy and non-technical.   Just open "System Settings>Software & Updates>Download From>Other>Select Best Server>Close>Reload" . . . . every time you choose a new download server, you need to reload the package database and then you should get a new popup window with the updates.   Run that process again, and you should see a full update completed with no errors.

Re upgrading 14.04 . . . unless you have a pressing reason (e.g., newer kernel provides better hw support (or worse sometimes)) . . . . I wouldn't do it on a "production" type PC . . . On a test or sandbox PC, experiment as much as you want, although there are just a couple things to do to better the odds of no errors (such as disabling any 3rd party PPA's, things like Wine, etc.).   In other words, the system should be as "Vanilla" as possible, all updates installed (nothing outstanding pending), and all sources should be same as the original install.   (plus fast ethernet or very stable wireless connection).

---

### Post by acmfiroz on 2015-06-29
I too have problems with updating ubuntu 14.04 LTS 64 bit.  When I run the command 'sudo apt-get update', I get the following output.
```

acmf@acm:~$ sudo apt-get update
sudo: /var/lib/sudo writable by non-owner (040777), should be mode 0700
[sudo] password for acmf: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease            
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release.gpg [933 B]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [63.5 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release [63.5 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [3,433 B]    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [212 kB]           
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [122 kB]       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [5,151 B]    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages [11.8 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages [562 kB]   
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages [290 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [11.8 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [548 kB]    
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [291 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en           
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Sources [28.4 kB]   
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Sources [28 B]    
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Sources [5,851 B]       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B] 
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe amd64 Packages [32.6 kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main amd64 Packages [6,256 B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1,571 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages [32.6 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages [6,285 B] 
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_IN                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_IN              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_IN              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_IN                
Fetched 2,328 kB in 38s (60.2 kB/s)                                            
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages)  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
acmf@acm:~$ ^C
acmf@acm:~$ 
```

Please help me solve the problem.  Thanks in advance.
FirozACM

---

### Post by matt_symes on 2015-06-29
Hi

@acmfiroz

To fix your package manager error, first try rebooting or close any other program using the package manager.

If that does not fix it then..,

```
sudo rm /var/lib/dpkg/lock
```

```
sudo apt-get update
```

However, there are problems with sudo on your system.

```
sudo chmod 700 /var/lib/sudo
```

If sudo does not work you'll have to fix it from a root shell from the grub menu.

Also try to find out why the permissions were changed for sudo.

EDIT:

Next time please start your own thread as opposed to hijacking another.

Kind regards

---

### Post by jack117 on 2015-06-29
@Bashing-om

"All 3rd party sources are disabled/reverted to standard"

I only have Cairo dock apart from that no other 3rd party sources 

"15.04 only has support for 9 months from time of release. it's support will cease Jan 2016"

I was not aware of this, I just wanted to try it cuz I am anyway having issues with 14.04 update. 

@Geoffrey_Arndt

"System Settings>Software & Updates>Download From>Other>Select Best Server>Close>Reload"

It totally worked but while installing it went not responding screen shot in-line. I closed everything while it was updating and waited for an hour still no use. Logged out and restarted. I don't know whether the update installation was successful.  

 [ATTACH=CONFIG]262917[/ATTACH]

@grahammechanical

Yes! upgrade was only to fix update problem but I guess it was solved.

---

### Post by Geoffrey_Arndt on 2015-06-29
As Ubuntu is pretty darn stable, MOST of the time failed updates are related to a server not available state.    So,  letting the system ping all servers as you did will find an available server that loops back quickest.    You can always check if update succeeded by running the update tool (app) manually via the Dash.   If response is your system is up to date, well, you're good.

Glad it worked out for you - - best to show this thread as solved as this happens on rare occasion to many "Buntu" users.

****************8

Acmfiroz:   your situation is different than the original poster, so, just a suggestion, opening a separate thread may capture attention of more folks - but Matt's suggestions should be tried first, he's on the right track.

---

### Post by jack117 on 2015-06-29
@Geoffrey_Arndt

"You can always check if update succeeded by running the update tool (app) manually via the Dash. If response is your system is up to date, well, you're good"

yes after restart, I immediately clicked on about this computer and checked for updates it showed software up to date. I guess I am fine.
 
solved straight away!

and I have difficulty with some sites eg: news website (link below)..etc they don't load in Firefox neither Chrome just keeps on loading, is it a kind of bug?

[http://thenextweb.com/insider/2015/06/29/tuesday-has-one-extra-second-and-that-could-be-dangerous-for-the-internet/](http://thenextweb.com/insider/2015/06/29/tuesday-has-one-extra-second-and-that-could-be-dangerous-for-the-internet/)

---

### Post by acmfiroz on 2015-07-11
That seems to have solved my problem.  Thank you very much for your help.

---

