---
title: "ubuntu apt-get update error"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by remy06 on 2008-10-06
Hello all,

I'm using ubuntu hardy for short while now.Previously, I have no problem updating with the following commands:
sudo apt-get update
apt-get upgrade

Until recently I had to reinstall everything on my pc,and now Im beginning to face some errors when updating (Please see below)

I've searched the forum and found something similar but not sure if it apply to my problem -> [http://ubuntuforums.org/showthread.php?t=283268]("http://ubuntuforums.org/showthread.php?t=283268")

I have tried changing the default server(which is "Server for Singapore") under system>administration>software sources to other servers(eg. Main server) and have no problem with updating(but rather slow this time)

I am wondering what is the cause of this error and how to fix it since previously i have no problems with the default server and it is significantly faster as well.

Appreciate any help :)

(here is the partial list generated from apt-get update):

Get:1 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy Release.gpg [189B]
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy/main Translation-en_SG
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy/restricted Translation-en_SG
  Error reading from server. Remote end closed connection
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy/universe Translation-en_SG              
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy/multiverse Translation-en_SG            
  Error reading from server - read (104 Connection reset by peer)
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-updates/main Translation-en_SG
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-updates/restricted Translation-en_SG
  Error reading from server - read (104 Connection reset by peer)
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-updates/universe Translation-en_SG
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-updates/multiverse Translation-en_SG
  Error reading from server - read (104 Connection reset by peer)
Get:3 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-security/main Translation-en_SG
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-security/restricted Translation-en_SG
  Error reading from server - read (104 Connection reset by peer)
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-security/universe Translation-en_SG     
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-security/multiverse Translation-en_SG
  Error reading from server. Remote end closed connection
Get:29 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-security/multiverse Packages [8222B] 
Get:30 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hardy-security/multiverse Sources [14B]    
Fetched 8254kB in 14s (568kB/s)                                                
W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_SG.bz2](http://sg.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_SG.bz2)  Error reading from server. Remote end closed connection

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_SG.bz2](http://sg.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_SG.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_SG.bz2](http://sg.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_SG.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_SG.bz2](http://sg.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_SG.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_SG.bz2](http://sg.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_SG.bz2)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_SG.bz2](http://sg.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_SG.bz2)  Error reading from server. Remote end closed connection

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pro-reason on 2008-10-06
If I understand you correctly, you're saying there's that the Singapore mirror is down.  The solution is not to use the Singapore mirror.  Use one for a neighbouring country.

If you wish to report the problem (although I imagine it is already being worked on), then I'm not sure of the correct procedure.  I presume that a report to [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) would get the ball rolling.

---

### Post by remy06 on 2008-10-07
Im not exactly sure if the mirror is down as im not sure where the problem lies.Guess I will use other servers then, and will check out launchpad first as well.Thanks

---

