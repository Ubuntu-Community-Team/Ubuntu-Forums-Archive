---
title: "Running a Itunes server on Unbutu Hoary"
date: 2005-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by goudiemark on 2005-06-16
This is my first ever how-to so go easy on me.

Before starting this you need to visit the ubuntu guide at [http://ubuntuguide.org/](http://ubuntuguide.org/) and add the extra repositories.  While your add it go ahead and update your ubuntu completly. 

-------------------- Notice that some commads have sudo in front-------------------------------------
-----------------------------If your root you dont need sudo --------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------
1.  Download Daapd the software that controlls everything at [http://ftp.us.debian.org/debian/pool/contrib/d/daapd/daapd_0.2.4a-1_i386.deb](http://ftp.us.debian.org/debian/pool/contrib/d/daapd/daapd_0.2.4a-1_i386.deb)

If you notice it is a deb package so we can use dpkg to install it.  Before we install this we must install these packages either with apt-get or synaptic package manager

```
 sudo apt-get install libhowl0 libid3tag0 mdnsresponder
``` 

Once this is done there is no more setup with the dependecies.  Now we need to install the package we previously downloaded

```
sudo dpkg -i /home/admin/Desktop/daapd_0.2.4a-1_i386.deb
``` 

This will automaticly start the itunes server.


2.  Config

Now we must config the server

```
sudo vi /etc/daapd.conf
``` 

Inside this file we want it to look like

```

 Port            3689        
 ServerName      athens
 DBName          athens music
 Password
 Root            /mnt/media/music/mp3s/
 Cachef
 Timescan        2
 Rescan          60

``` 

Most of this is self explanitory, Root is where the music is located.  Cachef is a location for a file to store a cache of all the music on the server, i have yet to test or configure this option.  Id assume you would only need it for large servers.

Timescan controls the way daapd estimates the duration of variable bitrate audio files; see man daapd for details.
Rescan is how often it rescans the root directory for new music.



3. Starting it up
If you open itunes right now you should see a music server called localhost, beacuse this was what was in the config file when it was started up.

First we must kill the daapd server that was started when we installed daapd.

```
sudo killall daapd
``` 

now we need to start the new daapd server

```
daapd -d
```

------------------------------------------------------------------------------------------------------------------------------------

Warnings 
The password for the server is kept in plain txt.

---

### Post by dclaridge on 2005-07-22
what do you mean if you 'start up itunes' itunes is available only for windows & mac?? isnt it??

---

### Post by mrcbrown on 2005-07-22
[QUOTE=dclaridge]what do you mean if you 'start up itunes' itunes is available only for windows & mac?? isnt it??[/QUOTE]
 Yeah, its for setting up a shared music library for a network - users like myself who have 2 linux workstations, 2 windows pc and a mac under this roof, comes in handy for windows and mac boxen as they now can have their audio dropped on the big drive on my ubuntu workstation, and stream things over the network using iTunes, in iTunes it shows up as a Shared Library of music, so Windows and Mac users of iTunes can browse/listen to mp3's without having to copy a 8GB+ library of mp3's to their drives.

---

### Post by horsefactory on 2005-07-27
[QUOTE=mrcbrown]Yeah, its for setting up a shared music library for a network - users like myself who have 2 linux workstations, 2 windows pc and a mac under this roof, comes in handy for windows and mac boxen as they now can have their audio dropped on the big drive on my ubuntu workstation, and stream things over the network using iTunes, in iTunes it shows up as a Shared Library of music, so Windows and Mac users of iTunes can browse/listen to mp3's without having to copy a 8GB+ library of mp3's to their drives.[/QUOTE]
 You may also want to try MT-daapd from [http://www.mt-daapd.org/](http://www.mt-daapd.org/) - Same sort of server but with a webadmin front end you can change settings from and manually update the playlist.

---

### Post by malachakla on 2005-08-08
[QUOTE=goudiemark]This is my first ever how-to so go easy on me.

Before starting this you need to visit the ubuntu guide at [http://ubuntuguide.org/](http://ubuntuguide.org/) and add the extra repositories.  While your add it go ahead and update your ubuntu completly. 

-------------------- Notice that some commads have sudo in front-------------------------------------
-----------------------------If your root you dont need sudo --------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------
1.  Download Daapd the software that controlls everything at [http://ftp.us.debian.org/debian/pool/contrib/d/daapd/daapd_0.2.4a-1_i386.deb](http://ftp.us.debian.org/debian/pool/contrib/d/daapd/daapd_0.2.4a-1_i386.deb)

If you notice it is a deb package so we can use dpkg to install it.  Before we install this we must install these packages either with apt-get or synaptic package manager

```
 sudo apt-get install libhowl0 libid3tag0 mdnsresponder
``` 

Once this is done there is no more setup with the dependecies.  Now we need to install the package we previously downloaded

```
sudo dpkg -i /home/admin/Desktop/daapd_0.2.4a-1_i386.deb
``` 

This will automaticly start the itunes server.


2.  Config

Now we must config the server

```
sudo vi /etc/daapd.conf
``` 

Inside this file we want it to look like

```

 Port            3689        
 ServerName      athens
 DBName          athens music
 Password
 Root            /mnt/media/music/mp3s/
 Cachef
 Timescan        2
 Rescan          60

``` 

Most of this is self explanitory, Root is where the music is located.  Cachef is a location for a file to store a cache of all the music on the server, i have yet to test or configure this option.  Id assume you would only need it for large servers.

Timescan controls the way daapd estimates the duration of variable bitrate audio files; see man daapd for details.
Rescan is how often it rescans the root directory for new music.



3. Starting it up
If you open itunes right now you should see a music server called localhost, beacuse this was what was in the config file when it was started up.

First we must kill the daapd server that was started when we installed daapd.

```
sudo killall daapd
``` 

now we need to start the new daapd server

```
daapd -d
```

------------------------------------------------------------------------------------------------------------------------------------

Warnings 
The password for the server is kept in plain txt.[/QUOTE]
 I would not use vi.... it's not easy to use for beginners and some people (like me!) wouldn't know the command to save the config file and exit...
I used gedit and it was a lot easier and friendlier.
Otherwise, a great tutorial!
I had tried to get this to work before, but couldn't.
It was almost automatic with your guide.
Thanks!

---

### Post by odyssey on 2005-10-22
What sources does one need in Breezy for mDNSResponder and libhowl?

---

### Post by thekurst on 2005-10-22
Same question apt-get doesn't find libhowl in breezy I have all my repos enabled except the backports (they seem to cause a problem).

A Breezy Badger how-to for an iTunes Music Server would be great.

Thanks

---

### Post by kurokikaze on 2005-12-29
Hi, everybody. I've found a great, simple and working How-to on the internet and now I'd like to share my experience with you.

1 - Download the file howl-1.0.0.tar.gz from [http://www.porchdogsoft.com/products/howl/](http://www.porchdogsoft.com/products/howl/)

2 - Untar and install by doing
>    #./configure
   #make
   #sudo make install (or, I suggest, sudo checkinstall)

3 - In the console type:
   > #sudo apt-get install libgdbm-dev libid3tag0-dev

4 - Download mt-daapd-0.2.3.tar.gz from [http://www.mt-daapd.org/](http://www.mt-daapd.org/)

5 - Untar and install by doing
   > #./configure
   #make
   #sudo make install (or, I suggest, sudo checkinstall)

6 - In the folder where you untarred mt-daapd there is a subfolder named "contrib". Here you can find the file "mt-daapd.conf". It is a sample file, so open it and edit as you prefer following the precise directions given into it.

7 - Once done editing, copy it into the /etc/ folder.

8 - In the console type
>    #sudo killall mt-daapd
   #sudo mt-daapd

9 - Check out the log (at the path you've chosen in the mt-daapd-conf file) and, if there isn't any error, you could check by typing
>    #ps aux | grep mt-daapd

There should be two processes running.

10 - Open iTunes on the client machine and, after a while, you should see the name of the server in the playlist section (on the left). By clicking it you'll mount the shared music and then have a good fun!!

I hope this will work for you guys too.

---

### Post by chele on 2006-01-10
Don't you mean iTUNES? :-)

Just install the mt-daapd package from [http://sourceforge.net/project/showfiles.php?group_id=98211&package_id=105189&release_id=356415]("http://sourceforge.net/project/showfiles.php?group_id=98211&package_id=105189&release_id=356415")

It already includes the mdns/howl system. There is work in progress to allow it use the Avahi mdns responder, which is the newest/latest/greatest libre package. [http://avahi.org/]("http://avahi.org/")

mt-daapd works with the latest Rhythmbox 0.9.2 as a client as well. [http://gridpt1.fe.up.pt/mlopes/blog/index.php/2005/12/24/rhythmbox-092-deb-for-ubuntu-breezy/]("http://gridpt1.fe.up.pt/mlopes/blog/index.php/2005/12/24/rhythmbox-092-deb-for-ubuntu-breezy/")

---

