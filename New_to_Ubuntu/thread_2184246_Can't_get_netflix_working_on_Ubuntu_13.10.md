---
title: "Can't get netflix working on Ubuntu 13.10"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by benandmax on 2013-10-28
Ok, so I just switched from Zorin 7 to Ubuntu 13.10.  I'm still pretty new to linux, but I was able to get netflix working in Zorin.  According to many sources that same method should work for Ubuntu 13.10.  But it doesn't.  I tried using pipelight asexplained on this site: [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html). When I type in the first command:            sudo apt-add-repository ppa:ehoover/compholio
This is what I get: 
Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 91, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/trusty

As I said, I'm new at this so I'm basically copying and pasting these commands with no real idea what they technically do.  I like Ubuntu, and I'm trying to convince my wife to use linux since it speeds up our computer quite a bit.  This is her only hangup really as she loves her netflix. Any help would be appreciated.

---

### Post by oldos2er on 2013-10-28
Make sure you have the package python3-software-properties installed: ```
sudo apt-get update && sudo apt-get install python3-software-properties
```

---

### Post by kozy1e on 2013-10-28
To install on Ubuntu / Mint -
Start terminal

$ sudo apt-add-repository ppa:ehoover/compholio

$ sudo apt-get update

$ sudo apt-get install netflix-desktop

------

For Fedora (only 32 bit systems) 
You need wget first:
su -c  'yum -y install wget'

Installing Netflix:
wget -c [http://sourceforge.net/projects/posti...]("http://sourceforge.net/projects/postinstaller/files/data/Netflixplayer.tar.gz") 

tar -xvzf Netflixplayer.tar.gz

su -c  'sh Netflixplayer.sh'

Running Netflix from cmd line:
sh /usr/bin/Netflix.sh                                     

                   [http://www.youtube.com/watch?feature=player_detailpage&v=Tfte5su5DIA](http://www.youtube.com/watch?feature=player_detailpage&v=Tfte5su5DIA)

---

### Post by benandmax on 2013-10-28
I am still having problems.  I tried installing what you said, oldos2er, but it just gave me this message after it listed a lot of things: Fetched 19.4 MB in 16s (1,198 kB/s)                                            
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Not sure what is going on, I can't even install wine without getting an error message (maybe wine is pre-installed with 13.10?)

---

### Post by benandmax on 2013-10-28
I also tried your suggestion, Kozy1e and I get this:
$  sudo apt-add-repository ppa:ehoover/compholio
Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 91, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/trusty

Is there anything I can do?

---

### Post by cdaver on 2013-10-28
First Step:


[LIST]
[*][How can I get apt to use a mirror close to me?]("http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me")
[*][How do I change which mirror I get updates and software from?]("http://askubuntu.com/questions/53084/how-do-i-change-which-mirror-i-get-updates-and-software-from")
[/LIST]


Then once you have selected the best server to get the updates from , do a sudo apt-get update.

Then use Update manager to check if all pending updates are done and if machine needs a restart.

Once all this is done you can add ppa repository and do a update via term if needed.

---

### Post by oldos2er on 2013-10-28
> **benandmax said:**
> I am still having problems.  I tried installing what you said, oldos2er, but it just gave me this message after it listed a lot of things: Fetched 19.4 MB in 16s (1,198 kB/s)                                            
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Not sure what is going on, I can't even install wine without getting an error message (maybe wine is pre-installed with 13.10?)

Trusty is 14.04, not 13.10, and I hope you're not running it because it's not even alpha yet. Can you post all the terminal output from ```
sudo apt-get update
```

---

### Post by benandmax on 2013-10-28
yep here it is:
$ sudo apt-get update
[sudo] password for max: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates InRelease             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports InRelease          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg [933 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release [49.6 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Sources [1,017 kB]     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Sources [4,759 B]         
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Sources [6,275 kB]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_CA          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_CA    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_CA    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_CA      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_CA                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en    
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Sources [178 kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages [1,249 kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages [9,688 B]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages [5,785 kB]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages [135 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en_CA     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en_CA       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en_CA 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en_CA 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en_CA   
Fetched 14.7 MB in 12s (1,199 kB/s)                                            
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


I have a feeling you are correct. Just installed it last night...I downloaded 13.10, couldn't figure out how to get a boot file to my flash drive using Zorin so I used Unetbootin.  Unetbootin seemed to redownload the OS.  I think I picked "latest version" or something like that.  I wondered if I had done something wrong, but when Ubuntu installed to my HD without a hitch I figured all was okay. :confused:.  Yes, you can definitely tell I'm new at this.  I am a bit of an idiot.

---

### Post by benandmax on 2013-10-28
yep here it is:
$ sudo apt-get update
[sudo] password for max: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates InRelease             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports InRelease          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg [933 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release [49.6 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Sources [1,017 kB]     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Sources [4,759 B]         
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Sources [6,275 kB]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_CA          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_CA    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_CA    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_CA      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_CA                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en    
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Sources [178 kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages [1,249 kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages [9,688 B]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages [5,785 kB]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages [135 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en_CA     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en_CA       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en_CA 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en_CA 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en_CA   
Fetched 14.7 MB in 12s (1,199 kB/s)                                            
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


I have a feeling you are correct. Just installed it last night...I downloaded 13.10, couldn't figure out how to get a boot file to my flash drive using Zorin so I used Unetbootin.  Unetbootin seemed to redownload the OS.  I think I picked "latest version" or something like that.  I wondered if I had done something wrong, but when Ubuntu installed to my HD without a hitch I figured all was okay. :confused:.  Yes, you can definitely tell I'm new at this.  I am a bit of an idiot.

---

### Post by oldos2er on 2013-10-28
I recommend you install 13.10, because I can guarantee 14.04 is going to have many issues.

---

### Post by benandmax on 2013-10-28
Sorry....just noticed you replied.  Ok, so I'm a total noob here, but do I have to do a fresh install of 13.10 or can I "update" (dwongrade) to it?  Really hoping I can just do an update. Thanks for all your help.

---

### Post by oldos2er on 2013-10-29
You'd need to do a fresh install, there's no downgrade path.

---

