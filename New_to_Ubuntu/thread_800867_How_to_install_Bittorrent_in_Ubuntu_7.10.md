---
title: "How to install Bittorrent in Ubuntu 7.10"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by elord on 2008-05-20
Im experiencing some problem in installing the Bittorent.. Can u guys give me the link where i can download the bittorrent? can u teach me the step by step in installing the software..

---

### Post by pedro_orange on 2008-05-20
If you just need a bit torrent client; Ubuntu comes with Transmission by default.

Otherwise search for bit torrent in Synaptic.

---

### Post by Joeb454 on 2008-05-20
What exactly are you trying to do?

Transmission will open (and download) the torrent files for you :)

---

### Post by vishzilla on 2008-05-20
Tranmission is there by default. You can also try Deluge ```
sudo apt-get install deluge-torrent
```

---

### Post by jtibau on 2008-05-20
Well if you are using gutsy, then you don't have transmission. Transmission is new in hardy. Previous to that we had gnome-bittorrent-client, which is way too basic. But, it may just do it for you if you don't have special needs, or just want to give bittorrent a try to learn what its all about.

If that's the case you need to get a .torrent file. You can download one from mininova, then just double click it and ubuntu will automatically open gnome-bittorrent-client for you. That's it...

If you want to upgrade to hardy, Transmission is awesome!!! I came to know of it in hardy, but in retrospect would've installed it before had I known. I'm not sure it is on the gutsy repos...

You could also try Azureus. Now that I think of it, the new Azureus client (I think its called Vuze now) allows you to search, download and view videos as if it where a media portal.

---

### Post by elord on 2008-05-20
tnxs guys.. i think i have to update 1st my OS..

---

### Post by T-Virus on 2008-05-20
If you are using KDE or have all the KDE libraries - try Ktorrent.

---

### Post by elord on 2008-05-20
honestly speaking sir im new to this OS.. i stop using linux when i resigned in my previous work..right now im using UBUNTU 7.10.. how do i know if its KDE by the way?

---

### Post by bartcramer on 2008-05-20
I find Transmission more stable and intuitive than any other torrent client, so worth a try! But maybe not worth an OS upgrade, and it is available in Gutsy/7.10 as well, it's just not installed standard. 

```
sudo apt-get install transmission
```

edit: concerning KDE: Ubuntu uses Gnome as its window manager, Kubuntu uses KDE. A window manager just determines how your windows look like, and comes bundled with some standard applications, like KTorrent. I suppose for the majority of people, standard Ubuntu with Transmission should do the job very well. 

HTH :)

---

### Post by T-Virus on 2008-05-20
Was about to write reply but bartcramer answered everything, cheers. :)

---

### Post by hyper_ch on 2008-05-20
you want a guied torrent client or a command line based one?

---

### Post by elord on 2008-05-20
ic i got the point now.. im using UBUNTU so its Gnome right? tnxs guys.. maybe tomorrow i will install the bittorrent.... can u give me the link so that its easy for me to download..

---

### Post by Joeb454 on 2008-05-20
[apt://transmission]("apt://transmission") Click that to install transmission (note that you'll need to be in Ubuntu for that to work, and I only tested it with Firefox :))

---

### Post by elord on 2008-05-20
> **Joeb454 said:**
> [apt://transmission]("apt://transmission") Click that to install transmission (note that you'll need to be in Ubuntu for that to work, and I only tested it with Firefox :))

there was an error "cannot find the transmission"

---

### Post by Joeb454 on 2008-05-20
Odd, you're using Ubuntu now right?

If so then are your repo's updated? from a terminal run ```
sudo apt-get update
```

---

### Post by hyper_ch on 2008-05-20
> **elord said:**
> can u give me the link so that its easy for me to download..

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by elord on 2008-05-20
> **Joeb454 said:**
> [apt://transmission]("apt://transmission") Click that to install transmission (note that you'll need to be in Ubuntu for that to work, and I only tested it with Firefox :))

there was an error "cannot find the transmission"

---

### Post by zvacet on 2008-05-20
[Here.]("http://www.getdeb.net/search.php?keywords=transmission")Downloads both files.

You can download source code from [here.]("http://www.transmissionbt.com/download.php") Download it in your home directory and go to the applications>accessories>terminal and type

```
tar xvjf transmission-1.20.tar.bz2
cd transmission-1.20
./configure -q && make -s
sudo make install
```

Type one line at the time and you will have latest Transmission.

---

### Post by elord on 2008-05-22
> **pedro_orange said:**
> If you just need a bit torrent client; Ubuntu comes with Transmission by default.

Otherwise search for bit torrent in Synaptic.

where i can find the Synaptic? what is Synaptic

---

### Post by elord on 2008-05-22
> **Joeb454 said:**
> Odd, you're using Ubuntu now right?

If so then are your repo's updated? from a terminal run ```
sudo apt-get update
```

this is what happen to after i type the code sir..

elord@elord-desktop:~$ sudo apt - get update
[sudo] password for elord:
sudo: apt: command not found
elord@elord-desktop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_PH
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_PH
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [44.0kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [14B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [12.5kB]         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_PH       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_PH             
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_PH      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_PH            
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_PH     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_PH           
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_PH                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release [58.5kB]                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages [6150B]    
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages [57.5kB]         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Fetched 179kB in 12s (14.6kB/s)                                                
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
elord@elord-desktop:~$

---

### Post by Living2007 on 2008-05-22
Some people say > [FONT=monospace]Transmission.[/FONT] Seems OK, maybe try ```
sudo apt-get install deluge-torrent
```Or just go for Azureus Vuse if you can get it?

---

### Post by elord on 2008-05-22
thanks a lot.. now i can download some software to be used..

---

### Post by elord on 2008-05-22
> **Living2007 said:**
> Some people say  Seems OK, maybe try ```
sudo apt-get install deluge-torrent
```Or just go for Azureus Vuse if you can get it?

The Case is solve now.. thank you.. and to the rest of you guys who replied to my problems thank you so much..

---

### Post by killbubble on 2011-06-20
Hey guys, i just downloaded and installed ubuntu 11.04 and i want to install bittorrent,but since i have used windows till now i even had a bit of a hard time finding the terminal (how lame), so i just didnt get what u all said, if anyone could just explain everything step by step that would be great. thx

---

### Post by TenPlus1 on 2011-06-20
killbubble: Ubuntu 11.04 comes with a program called Transmission that IS your bittorrent client, test it by going to [http://www.legittorrents.info/](http://www.legittorrents.info/) and finding something you like, click on the torrent link to download and Transmission will open and let you download it...

---

