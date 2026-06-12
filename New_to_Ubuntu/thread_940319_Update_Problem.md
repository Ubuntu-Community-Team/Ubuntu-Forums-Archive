---
title: "Update Problem"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by blacksmithforlife on 2008-10-06
Dear fellow Ubuntu users,

I am fairly new to Ubuntu and have installed  version 8.04, now after some time the update manager does not seem to work. I have tried in vain to get it to work by installing, reinstalling and removing several packages which I believed to be causing the problem. Then I used the command sudo apt-get update and here is the output I get: 

john@IronMan:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US        
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US      
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release [65.9kB]                         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release [65.9kB]                         
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]                 
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]                 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                           
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources                 
Fetched 1319B in 16s (80B/s)                                                   
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures were invalid: NODATA 2

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: NODATA 2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures were invalid: NODATA 2

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
john@IronMan:~$ 


Can anyone help me? I would really like to know is going on and how to fix it so if it happens again I can do it myself. Thank you for all the help.

~John

---

### Post by seagullplayer77 on 2008-10-06
Only time I've ever gotten that kind of output is when my Internet connection is down, although that wouldn't seem to be the case (assuming you're posting from the same computer you're trying to update). The only other thing I can think of is that maybe the web addresses for the repositories are somehow corrupted. If you go into Synaptic and press the key labeled "Origin," it lists all your repos. Maybe post those and see if they match up with what other people have? 

Sorry I couldn't be of more help...

---

### Post by robalcorn on 2008-10-06
What about changing your source for download by going to system/administration/software sources and change the Download from option?

---

### Post by blacksmithforlife on 2008-10-06
ok here are the ones that I got: 
local/main
archive.ubuntu.com/main
archive.ubuntu.com/multiverse
archive.ubuntu.com/restricted
archive.ubuntu.com/universe

~John

---

### Post by blacksmithforlife on 2008-10-07
Any new ideas?

---

### Post by Keen101 on 2008-10-07
try:

```
sudo apt-get upgrade

```

not sure if it will help, but it's something to try.

---

### Post by blacksmithforlife on 2008-10-07
Every time I try that I get the same output that is listed in my first post. Thanks for the idea though.

---

### Post by Ryadt on 2008-10-07
Try to change your server.
Go System > Administration > Software Sources
Click the 'Download From' menu and select 'Other'
Click the 'Select Best Server' button.
Then Choose Server
Retry to update.

---

### Post by blacksmithforlife on 2008-10-07
here is what I get:

GPG error: [http://ftp.tiscali.nl](http://ftp.tiscali.nl) hardy-updates Release: The following signatures were invalid: NODATA 2GPG error: [http://ftp.tiscali.nl](http://ftp.tiscali.nl) hardy-security Release: The following signatures were invalid: NODATA 2Failed to fetch [http://ftp.tiscali.nl/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://ftp.tiscali.nl/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ftp.tiscali.nl/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://ftp.tiscali.nl/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ftp.tiscali.nl/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://ftp.tiscali.nl/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ftp.tiscali.nl/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://ftp.tiscali.nl/ubuntu/dists/hardy/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ftp.tiscali.nl/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://ftp.tiscali.nl/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

although it did seem to download them all this time...

---

