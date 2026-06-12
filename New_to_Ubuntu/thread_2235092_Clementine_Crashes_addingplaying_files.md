---
title: "Clementine Crashes adding/playing files"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by ian52 on 2014-07-18
I read some reviews and chose Clementine to be my music player, installed and loads fine. When I attempted to add files to my library I got an backend file error - don't remember exactly and haven't been able to get the program to stay live long enough to reproduce it again. It hangs up in menus and whenever i try to play or add anything. 

Where do I begin to diagnose this?

Thanks 

-Ian

---

### Post by nerdtron on 2014-07-18
How did you install clementine? What version is it and what version is you ubuntu?

---

### Post by ian52 on 2014-07-19
> **nerdtron said:**
> How did you install clementine? What version is it and what version is you ubuntu?

I used the Ubuntu software center to install Clementine - Clementine itself is version 1.2. Ubuntu is 14.04 LTS.

---

### Post by ian52 on 2014-07-21
Its pretty hard to get a feel for what is making things mess up because accessing menus is making it crash. However when it does lock up I noticed several tagreader processes on the task manager and think they might relate to the problem.


[ATTACH=CONFIG]254903[/ATTACH]

---

### Post by ian52 on 2014-07-21
The backend error I was talking about. [ATTACH=CONFIG]254904[/ATTACH]

---

### Post by nerdtron on 2014-07-22
killall the clementine processes by killing the PID of clementine.

sudo kill -9 <PID>

Then run clementine from the terminal so that it will ouput any error on the terminal.

Open a terminal. Type clementine, hit Enter and see the output errors.

---

### Post by ian52 on 2014-07-22
Ran it from terminal but the errors do not seem to be posting to the terminal... Did this several times and the program would become unresponsive and even threw an unidentified error (see screenshot) but nothing showed in terminal.

 [ATTACH=CONFIG]254938[/ATTACH]

---

### Post by nerdtron on 2014-07-23
Ha. This is one problematic program. Have you tried reinstalling? Let's try to purge everthing.

sudo apt-get purge clementine
sudo apt-get autoremove
sudo apt-get autoclean

Then on your home folder, show the hidden files and if you see any clementine related (example: .clementine folder) try to delete them.
Now install again.

sudo apt-get update && sudo apt-get upgade
sudo apt-get install clementine

I don't know any next step in case this one fails as I have always been successful installing clementine on every version I have.

Also, have you installed any other programs before clementine? Perhaps some have conflicts?

---

### Post by RedRat on 2014-07-23
I have been running Clementine for some time, same version as you, and have had no problems. However, I installed it from Synaptic and not the Software Center, I am also running the Gnome Desktop. BTW, I do like it.

---

### Post by ian52 on 2014-07-23
Well I really appreciate your help up to this point... but unfortunately it didn't work. I must have missed something though when purging all the files during uninstall because when I re-opened after I installed it again it had my library folder already mapped. I didn't see anytihng obviously "clementine" but that doesn't mean it wasn't there. Threw same database error when I tried to play a file. Sound has worked in online video already so I assume I have the correct drivers installed?

One thing that is nagging me is that I did NOT do an md5sum check on the image I downloaded before install... I was rushing and I should have done it but there it is. I have my Home folder backed up onto a storage drive using the backups program packaged with Ubuntu. 

So I suppose my next question would be should I just re install clean and checked to see if that fixes the issue, or try and fix it some other way. If I do end up having to re-install, are the errors I am seeing going to propegate into the new system when I retrieve that backup?

Thanks again

-Ian[ATTACH=CONFIG]254970[/ATTACH]

---

### Post by ian52 on 2014-07-23
> **RedRat said:**
> I have been running Clementine for some time, same version as you, and have had no problems. However, I installed it from Synaptic and not the Software Center, I am also running the Gnome Desktop. BTW, I do like it.

You like Clementine or Gnome? I believe I am using Unity... I have not  altered it from the standard offering that came with the download and I  don't see it under system info. Overall I like it, although there are  some features from Mint that I would like to add to this desktop. The  "desktop panes" were nice and I'm not totally sold on the ads in the  menu search, but the overall feel and speed is better on my laptop than  the Mint demo I ran. Did not try any specific media player..

-Ian

---

### Post by grumblebum2 on 2014-07-24
Try 
```
killall clementine
```
and then in your file browser delete the folders **~/.cache/Clementine**  and **~/.config/Clementine**
Start clementine.

The easiest test to see if some config or database in your home directory is causing an application error
is to test in the guest or a new user account.

---

### Post by ian52 on 2014-07-24
OK so we have a little improvement - thanks to a little direction from [**[COLOR=#000000]grumblebum2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1910493") on finding the .conf and cache folders I repeated nerdtron's proceedure and restarted from terminal. Added one song from one folder in my main music collection to clementine and it played. So far so good. I then tried to map the parent folder that houses all my music and the problems began there. Hanging up again and not letting me remove either of the folders from the library, nor play that song I played first.

Could this potentially be a problem with Clementine not being able to read my protected iTunes files? The library is mixed but there are a good number of the protected ones and I don't really know a efficient way to tell them apart. Really a terrible thing Apple did there and one of the main reasons I'm switching.

I will post the output of the installation and errors.

```
ian@ian-ThinkPad-X131e:~$ sudo apt-get purge clementine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  clementine*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 15.1 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 234636 files and directories currently installed.)
Removing clementine (1.2.0+dfsg-2build1) ...
Purging configuration files for clementine (1.2.0+dfsg-2build1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
ian@ian-ThinkPad-X131e:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gstreamer0.10-plugins-ugly libechonest2.1 libftgl2 liblastfm1 libprojectm2
  libqjson0 libqxt-core0 libqxt-gui0 projectm-data ttf-dejavu-core
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
After this operation, 6,871 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 234614 files and directories currently installed.)
Removing gstreamer0.10-plugins-ugly:amd64 (0.10.19-2ubuntu5) ...
Removing libechonest2.1:amd64 (2.1.0-2) ...
Removing libprojectm2 (2.1.0+dfsg-1build2) ...
Removing libftgl2:amd64 (2.1.3~rc5-4+nmu1) ...
Removing liblastfm1:amd64 (1.0.8-2) ...
Removing libqjson0:amd64 (0.8.1-3) ...
Removing libqxt-gui0:amd64 (0.6.2-1) ...
Removing libqxt-core0:amd64 (0.6.2-1) ...
Removing projectm-data (2.1.0+dfsg-1build2) ...
Removing ttf-dejavu-core (2.34-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
ian@ian-ThinkPad-X131e:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ian@ian-ThinkPad-X131e:~$ sudo apt-get install clementine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gstreamer0.10-plugins-ugly libechonest2.1 libftgl2 liblastfm1 libprojectm2
  libqjson0 libqxt-core0 libqxt-gui0 projectm-data ttf-dejavu-core
The following NEW packages will be installed:
  clementine gstreamer0.10-plugins-ugly libechonest2.1 libftgl2 liblastfm1
  libprojectm2 libqjson0 libqxt-core0 libqxt-gui0 projectm-data
  ttf-dejavu-core
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,599 kB of archives.
After this operation, 21.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libftgl2 amd64 2.1.3~rc5-4+nmu1 [49.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main libqjson0 amd64 0.8.1-3 [63.7 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libqxt-core0 amd64 0.6.2-1 [162 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libqxt-gui0 amd64 0.6.2-1 [256 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libechonest2.1 amd64 2.1.0-2 [212 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty/universe liblastfm1 amd64 1.0.8-2 [220 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty/universe projectm-data all 2.1.0+dfsg-1build2 [225 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty/main ttf-dejavu-core all 2.34-1ubuntu1 [2,956 B]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libprojectm2 amd64 2.1.0+dfsg-1build2 [215 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty/universe gstreamer0.10-plugins-ugly amd64 0.10.19-2ubuntu5 [262 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty/universe clementine amd64 1.2.0+dfsg-2build1 [3,933 kB]
Fetched 5,599 kB in 3s (1,480 kB/s)      
Selecting previously unselected package libftgl2:amd64.
(Reading database ... 234205 files and directories currently installed.)
Preparing to unpack .../libftgl2_2.1.3~rc5-4+nmu1_amd64.deb ...
Unpacking libftgl2:amd64 (2.1.3~rc5-4+nmu1) ...
Selecting previously unselected package libqjson0:amd64.
Preparing to unpack .../libqjson0_0.8.1-3_amd64.deb ...
Unpacking libqjson0:amd64 (0.8.1-3) ...
Selecting previously unselected package libqxt-core0:amd64.
Preparing to unpack .../libqxt-core0_0.6.2-1_amd64.deb ...
Unpacking libqxt-core0:amd64 (0.6.2-1) ...
Selecting previously unselected package libqxt-gui0:amd64.
Preparing to unpack .../libqxt-gui0_0.6.2-1_amd64.deb ...
Unpacking libqxt-gui0:amd64 (0.6.2-1) ...
Selecting previously unselected package libechonest2.1:amd64.
Preparing to unpack .../libechonest2.1_2.1.0-2_amd64.deb ...
Unpacking libechonest2.1:amd64 (2.1.0-2) ...
Selecting previously unselected package liblastfm1:amd64.
Preparing to unpack .../liblastfm1_1.0.8-2_amd64.deb ...
Unpacking liblastfm1:amd64 (1.0.8-2) ...
Selecting previously unselected package projectm-data.
Preparing to unpack .../projectm-data_2.1.0+dfsg-1build2_all.deb ...
Unpacking projectm-data (2.1.0+dfsg-1build2) ...
Selecting previously unselected package ttf-dejavu-core.
Preparing to unpack .../ttf-dejavu-core_2.34-1ubuntu1_all.deb ...
Unpacking ttf-dejavu-core (2.34-1ubuntu1) ...
Selecting previously unselected package libprojectm2.
Preparing to unpack .../libprojectm2_2.1.0+dfsg-1build2_amd64.deb ...
Unpacking libprojectm2 (2.1.0+dfsg-1build2) ...
Selecting previously unselected package gstreamer0.10-plugins-ugly:amd64.
Preparing to unpack .../gstreamer0.10-plugins-ugly_0.10.19-2ubuntu5_amd64.deb ...
Unpacking gstreamer0.10-plugins-ugly:amd64 (0.10.19-2ubuntu5) ...
Selecting previously unselected package clementine.
Preparing to unpack .../clementine_1.2.0+dfsg-2build1_amd64.deb ...
Unpacking clementine (1.2.0+dfsg-2build1) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up libftgl2:amd64 (2.1.3~rc5-4+nmu1) ...
Setting up libqjson0:amd64 (0.8.1-3) ...
Setting up libqxt-core0:amd64 (0.6.2-1) ...
Setting up libqxt-gui0:amd64 (0.6.2-1) ...
Setting up libechonest2.1:amd64 (2.1.0-2) ...
Setting up liblastfm1:amd64 (1.0.8-2) ...
Setting up projectm-data (2.1.0+dfsg-1build2) ...
Setting up ttf-dejavu-core (2.34-1ubuntu1) ...
Setting up libprojectm2 (2.1.0+dfsg-1build2) ...
Setting up gstreamer0.10-plugins-ugly:amd64 (0.10.19-2ubuntu5) ...
Setting up clementine (1.2.0+dfsg-2build1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ian@ian-ThinkPad-X131e:~$ clementine
17:44:45.299 WARN  unknown                          QFileSystemWatcher: failed to add paths: /home/ian/Music/iTunes Music/6gig/Tincan Experiment 
^C
ian@ian-ThinkPad-X131e:~$ clementine
17:46:34.199 WARN  unknown                          QFileSystemWatcher: failed to add paths: /home/ian/Music/iTunes Music/6gig/Tincan Experiment 
^C
ian@ian-ThinkPad-X131e:~$ clementine
17:50:39.059 WARN  unknown                          QFileSystemWatcher: failed to add paths: /home/ian/Music/iTunes Music/6gig/Tincan Experiment 
^C
ian@ian-ThinkPad-X131e:~$ clementine
17:54:30.795 WARN  unknown                          QFileSystemWatcher: failed to add paths: /home/ian/Music/iTunes Music/6gig/Tincan Experiment 


```

---

### Post by ian52 on 2014-07-24
Definitely the .m4a files... I'm not expecting to be able to keep those but how can I separate them from my .mp3s? The folder structure of iTunes broke the collection down into probably thousands of folders.

---

### Post by grumblebum2 on 2014-07-24
Never used itunes but maybe this thread will help if you still have a windows/mac install.
[https://discussions.apple.com/thread/4788743?tstart=0](https://discussions.apple.com/thread/4788743?tstart=0)

---

### Post by nerdtron on 2014-07-24
If you no longer use iTunes, you can consolidate all your music files and separate all the mp3s into a dedicated folder.

---

### Post by ian52 on 2014-07-24
> **nerdtron said:**
> If you no longer use iTunes, you can consolidate all your music files and separate all the mp3s into a dedicated folder.

I would love to but how do I copy just the contents of these folders without copying the folders themselves.... is it really as tedious as opening each folder on the tree and copying the contents one by one, for thousands of folders?

---

### Post by ian52 on 2014-07-24
> **grumblebum2 said:**
> Never used itunes but maybe this thread will help if you still have a windows/mac install.
[https://discussions.apple.com/thread/4788743?tstart=0](https://discussions.apple.com/thread/4788743?tstart=0)

THIS is good... Thank you for that link. I hadn't seen anything that indicated apple was doing this.

---

### Post by nerdtron on 2014-07-24
> **ian52 said:**
> I would love to but how do I copy just the contents of these folders without copying the folders themselves.... is it really as tedious as opening each folder on the tree and copying the contents one by one, for thousands of folders?

Assuming your files have extensions .mp3 and .m4, we can separate them like this.
I have here three folder with mixed .mp3 an .m4a files. I want to move the .mp3 on the mp3folder and the .m4a on the m4afolder.

```
[kenneth@nerdtron Music]$ tree
.
|-- folder1
|   |-- file1.m4a
|   `-- file1.mp3
|-- folder2
|   |-- file2.m4a
|   `-- file2.mp3
|-- folder3
|   |-- file3.m4a
|   `-- file3.mp3
|-- m4afolder
`-- mp3folder

5 directories, 6 files

```

The command would to find all *mp3 files and move them to the mp3 folder.
```
find . -iname *.mp3 -exec mv {} mp3folder/ \;
```

Let's see the result:
```
[kenneth@nerdtron Music]$ tree
.
|-- folder1
|   `-- file1.m4a
|-- folder2
|   `-- file2.m4a
|-- folder3
|   `-- file3.m4a
|-- m4afolder
`-- mp3folder
    |-- file1.mp3
    |-- file2.mp3
    `-- file3.mp3

5 directories, 6 files

```

Looks good. Now let's try them on the m4a files:
```
find . -iname *.m4a -exec mv {} m4afolder/ \;
```

Let's see what has done so far.
```
[kenneth@nerdtron Music]$ tree
.
|-- folder1
|-- folder2
|-- folder3
|-- m4afolder
|   |-- file1.m4a
|   |-- file2.m4a
|   `-- file3.m4a
`-- mp3folder
    |-- file1.mp3
    |-- file2.mp3
    `-- file3.mp3

5 directories, 6 files
```

Look's good to me.

---

### Post by milhouse86 on 2014-11-13
Hi. I'm runing clementine 1.2.3 un ubuntu 14.04 with gnome. 
It crashes while reproducing certain mp3 files. It plays fine most of the time but it suddenly stops and the process is not running anymore. I found to happen especifically with certain mp3 file. I did a clean installation of clementine as suggested by other users, but the problem is still there. 
I executed clementine from the terminal and made it play the particular file this is what I got:



```
mauricio@mauricio-Satellite-C55-B:~$ clementine
14:34:15.812 INFO  main:309                         Clementine 1.2.3 
14:34:15.919 DEBUG WorkerPool<HandlerType>:281      Starting worker 0x7f9a7bffe710 "/usr/bin/clementine-tagreader" "/tmp/clementine_512607057" 
14:34:15.922 DEBUG WorkerPool<HandlerType>:281      Starting worker 0x7f9a7bffe710 "/usr/bin/clementine-tagreader" "/tmp/clementine_1146164523" 
14:34:15.924 DEBUG WorkerPool<HandlerType>:281      Starting worker 0x7f9a7bffe710 "/usr/bin/clementine-tagreader" "/tmp/clementine_482858884" 
14:34:15.927 DEBUG WorkerPool<HandlerType>:281      Starting worker 0x7f9a7bffe710 "/usr/bin/clementine-tagreader" "/tmp/clementine_2106510607" 
14:34:15.932 INFO  main:46                          TagReader worker connecting to "/tmp/clementine_512607057" 
14:34:15.935 INFO  main:46                          TagReader worker connecting to "/tmp/clementine_1146164523" 
14:34:15.939 INFO  main:46                          TagReader worker connecting to "/tmp/clementine_482858884" 
14:34:15.942 INFO  main:46                          TagReader worker connecting to "/tmp/clementine_2106510607" 
14:34:15.953 DEBUG WorkerPool<HandlerType>:301      Worker 0x7f9a7000c8e0 connected to "/tmp/clementine_512607057" 
14:34:15.954 DEBUG WorkerPool<HandlerType>:301      Worker 0x7f9a7000dd60 connected to "/tmp/clementine_1146164523" 
14:34:15.954 DEBUG WorkerPool<HandlerType>:301      Worker 0x7f9a7000c780 connected to "/tmp/clementine_482858884" 
14:34:15.954 DEBUG WorkerPool<HandlerType>:301      Worker 0x7f9a700106c0 connected to "/tmp/clementine_2106510607" 
14:34:15.979 INFO  Player:561                       Registered URL handler for "di" 
14:34:15.980 DEBUG InternetModel:124                Adding internet service: "DigitallyImported" 
14:34:16.024 DEBUG InternetModel:124                Adding internet service: "Icecast" 
14:34:16.047 DEBUG InternetModel:124                Adding internet service: "Jamendo" 
14:34:16.066 INFO  Player:561                       Registered URL handler for "lastfm" 
14:34:16.066 DEBUG CoverProviders:34                Registered cover provider "last.fm" 
14:34:16.066 DEBUG InternetModel:124                Adding internet service: "Last.fm" 
14:34:16.067 INFO  Player:561                       Registered URL handler for "googledrive" 
14:34:16.067 DEBUG InternetModel:124                Adding internet service: "Google Drive" 
14:34:16.071 INFO  Player:561                       Registered URL handler for "grooveshark" 
14:34:16.072 DEBUG InternetModel:124                Adding internet service: "Grooveshark" 
14:34:16.072 INFO  Player:561                       Registered URL handler for "jazzradio" 
14:34:16.072 DEBUG InternetModel:124                Adding internet service: "JazzRadio" 
14:34:16.073 INFO  Player:561                       Registered URL handler for "magnatune" 
14:34:16.073 DEBUG InternetModel:124                Adding internet service: "Magnatune" 
14:34:16.074 DEBUG InternetModel:124                Adding internet service: "Podcasts" 
14:34:16.074 INFO  Player:561                       Registered URL handler for "radiogfm" 
14:34:16.074 DEBUG InternetModel:124                Adding internet service: "Radio GFM" 
14:34:16.075 INFO  Player:561                       Registered URL handler for "rockradio" 
14:34:16.075 DEBUG InternetModel:124                Adding internet service: "RockRadio" 
14:34:16.083 DEBUG InternetModel:124                Adding internet service: "SavedRadio" 
14:34:16.083 INFO  Player:561                       Registered URL handler for "sky" 
14:34:16.084 DEBUG InternetModel:124                Adding internet service: "SKY.fm" 
14:34:16.084 INFO  Player:561                       Registered URL handler for "somafm" 
14:34:16.085 DEBUG InternetModel:124                Adding internet service: "SomaFM" 
14:34:16.086 DEBUG InternetModel:124                Adding internet service: "SoundCloud" 
14:34:16.087 DEBUG SpotifyService:76                Spotify system blob path: "/usr/bin/clementine-spotifyblob" 
14:34:16.087 DEBUG SpotifyService:77                Spotify local blob path: "/home/mauricio/.config/Clementine/spotifyblob/version14-64bit/blob" 
14:34:16.087 DEBUG InternetModel:124                Adding internet service: "Spotify" 
14:34:16.088 INFO  Player:561                       Registered URL handler for "subsonic" 
14:34:16.098 DEBUG InternetModel:124                Adding internet service: "Subsonic" 
14:34:16.100 INFO  Player:561                       Registered URL handler for "ubuntuonefile" 
14:34:16.100 DEBUG InternetModel:124                Adding internet service: "Ubuntu One" 
14:34:16.101 INFO  Player:561                       Registered URL handler for "dropbox" 
14:34:16.101 DEBUG InternetModel:124                Adding internet service: "Dropbox" 
14:34:16.103 INFO  Player:561                       Registered URL handler for "skydrive" 
14:34:16.103 DEBUG InternetModel:124                Adding internet service: "OneDrive" 
14:34:16.104 INFO  Player:561                       Registered URL handler for "box" 
14:34:16.104 DEBUG InternetModel:124                Adding internet service: "Box" 
14:34:16.110 DEBUG NetworkProxyFactory:30           Detected system proxy URLs: ("", "", "", "") 
14:34:16.110 DEBUG CoverProviders:34                Registered cover provider "Amazon" 
14:34:16.110 DEBUG CoverProviders:34                Registered cover provider "Discogs" 
14:34:16.110 DEBUG CoverProviders:34                Registered cover provider "MusicBrainz" 
14:34:16.118 WARN  DeviceKitLister:56               Error enumerating DeviceKit-disks devices: "org.freedesktop.DBus.Error.ServiceUnknown" "The name org.freedesktop.UDisks was not provided by any .service files" 
14:34:16.138 DEBUG GnomeGlobalShortcutBackend:50    registering 
14:34:16.255 DEBUG MainWindow:191                   Starting 
14:34:16.353 DEBUG MainWindow:243                   Initialising player 
14:34:16.356 DEBUG MainWindow:249                   Creating models 
14:34:16.417 DEBUG MainWindow:269                   Creating UI 
14:34:16.454 DEBUG MainWindow:630                   Creating equalizer 
14:34:16.456 DEBUG MainWindow:655                   Creating now playing widget 
14:34:16.633 DEBUG MainWindow:699                   Loading settings 
14:34:16.637 WARN  unknown                          "sni-qt/17788" WARN  14:34:16.637 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE  
14:34:16.640 INFO  NetworkRemote:87                 Starting network remote 
14:34:16.641 INFO  NetworkRemote:95                 Listening on port  5500 
14:34:16.729 DEBUG MainWindow:756                   Started 
14:34:16.997 DEBUG GnomeGlobalShortcutBackend:93    registered 
14:34:17.023 DEBUG {anonymous}:61                   QDBusError("", "") 
14:34:17.026 DEBUG {anonymous}:107                  Remote interface published on Avahi: QDBusError("", "") 
14:34:30.313 INFO  MoodbarLoader:144                Creating moodbar data for "/media/win8/Miki/Música/Disturbed - Prayer.mp3" 
14:34:30.726 DEBUG Playlist:1532                    Setting metadata for  QUrl( "file:///media/win8/Miki/Música/Disturbed - Prayer.mp3" )  to "Disturbed" "Prayer" 
14:34:30.730 DEBUG MainWindow:1143                  position 0 scrobble point 119 status 0 
Violación de segmento (`core' generado)
mauricio@mauricio-Satellite-C55-B:~$

```
Any suggestions, other than erasing that mp3?

---

### Post by RedRat on 2014-11-14
Ian
Sorry for the late reply but I never got a notice of your comment, in fact this is the first notice I have gotten from Ubuntu forums in a while. I like both Clementine and Gnome. Really don't care for the Unity interface, but hey whatever floats your boat. Since both interfaces are quite different, it may be that Clementine may have been originally designed to work under Gnome and it takes a bit before the bugs are worked out with Unity (since it is new). I guess my opinion of Unity is rooted in the idea that it is an interface for those who like "magic", I started out with Windows 1 (believe it or not) and a sort of windows interface within MSDOS. Went to a Mac SE and went back to Windows. So I guess I prefer those approaches to my GUI.

---

### Post by Rob Sayer on 2014-12-10
> **RedRat said:**
> ...  I started out with Windows 1 ...

Wow.  I started windows with 3.1 and I thought I was old school ...

I agree the OP's problem is likely with iTunes DRM crap.

Too bad others are having so much trouble with clementine ... I have specific playlist wants and only clementine really does what I want, with vlc a close second.

It worked OK when I ran Kubuntu 12.04 except the visualization (ie  projectm) crashed every time.  That machine is running mint 17 cinnamon now, and clementine works fine so far.

---

### Post by RedRat on 2014-12-10
I just found out that Clementine is available for Windows so I just installed it on my Windows machine. I actually prefer it to my older Windows player, WinAmp.

---

### Post by mc4man on 2014-12-10
> **milhouse86 said:**
> Hi. I'm runing clementine 1.2.3 un ubuntu 14.04 with gnome. 
It crashes while reproducing certain mp3 files. It plays fine most of the time but it suddenly stops and the process is not running anymore. I found to happen especifically with certain mp3 file. I did a clean installation of clementine as suggested by other users, but the problem is still there. 
I executed clementine from the terminal and made it play the particular file this is what I got:

Any suggestions, other than erasing that mp3?
If still having issues then start a new thread. This one concerned protected apple  itunes files (.m4a) & was likely solved by post 16 quite some time ago.
(- so nothing to do with .mp3's nor unity/gnome/mint whatever..

---

