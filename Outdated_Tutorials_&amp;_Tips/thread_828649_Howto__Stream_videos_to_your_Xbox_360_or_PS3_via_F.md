---
title: "Howto:  Stream videos to your Xbox 360 or PS3 via Fuppes"
date: 2008-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by PorchSong on 2008-06-13
***I originally posted this in this thread: 

[http://ubuntuforums.org/showthread.php?p=3898464]("http://ubuntuforums.org/showthread.php?p=3898464")

But the thread got corrupted and my post vanished.  So, I just went ahead and started a new thread altogether to help those out.

Please note that I have turned video transcoding OFF as you do not need to transcode to your gaming device anymore as recent updates handle most avi's now.  But, I turn off the transcoding via my fuppes.cfg file--not by disabling transcoding via fuppes install.  So the fuppes install is pure, just my fuppes.cfg turns things off.

For some reason people are having trouble installing Fuppes.  Following directions on Fuppes site, wiki, and others was not working properly, etc.  Thus my solution was to remove all the components that install Fuppes and start from scratch.  This has helped many of those who could not install.

Do this: (I like to run these individually rather than all at once to watch what is going on).

```
$ sudo apt-get remove autoconf
$ sudo apt-get remove automake
$ sudo apt-get remove gettext
```


Go to your /home/**your user name**/ directory and delete your /fuppes directory if you see it in there.  NOT the hidden .fuppes directory as this only contains your fuppes.cfg and vfolder.cfg files. (no need to).  

So, now you are "clean."

Now start over.  

```
$ sudo apt-get update

$ sudo apt-get install autoconf
$ sudo apt-get install automake
$ sudo apt-get install gettext
```

Now get the latest release of fuppes v611 (Again, I run these one line at a time)

```
$ svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure --enable-video-transcoding
$ make
$ sudo make install
$ sudo ldconfig
```

This should do it.  

The tricky part is getting a proper fuppes.cfg file in order.  I blended mine so that I am NOT transcoding vids to my Xbox 360--no need to.  I took Octaganol's fuppes.cfg file but it would not run on its own (even modifying it for my system). So, I took the "meat" of his and blended it into mine.  

Here is my fuppes.cfg file.  You will have to change / direct to your personal folders up top, and in network section set up to your ip addy and port.  Just cut and paste my whole file over your whole file (after making a backup copy of yours in case it does not work), make changes in folder area and network area, and save it.  Also, place this in your home/**your user name**/.fuppes directory. You will need admin rights to do this.

My fuppes.cfg file:


```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
 <shared_objects>
   <dir>/media/sdb1/Sci-fi/Movies</dir>
   <dir>/media/My Book/Movies</dir>
   <dir>/media/My Book/Incoming</dir>
 </shared_objects>

<network>
   <!--empty = automatic detection-->
   <interface>eth0</interface>
   <!--empty or 0 = random port-->
   <http_port>9137</http_port>
   <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
   <allowed_ips>
     <!--<ip>192.168.0.1</ip>-->
     <ip>192.168.0.20</ip>
     <ip>192.168.0.10</ip>
   </allowed_ips>
 </network>
 <content_directory>
   <!--a list of possible charsets can be found under:
     http://www.gnu.org/software/libiconv/-->
   <local_charset>UTF-8</local_charset>
   <!--libs used for metadata extraction when building the database. [true|false]-->
   <use_imagemagick>true</use_imagemagick>
   <use_taglib>true</use_taglib>
   <use_libavformat>true</use_libavformat>
 </content_directory>
 <transcoding>
   <!--[lame|twolame]-->
   <audio_encoder>lame</audio_encoder>
   <!--[true|false]-->
   <transcode_vorbis>true</transcode_vorbis>
   <transcode_musepack>true</transcode_musepack>
   <transcode_flac>true</transcode_flac>
 </transcoding>
 <device_settings>
   <!--"default" settings are inhertied by specific devices and can be overwritten-->
   <device name="default">
     <!--specify the maximum length for file names (0 or empty = unlimited)-->
     <max_file_name_length>0</max_file_name_length>
     <!--[file|container]-->
     <playlist_style>file</playlist_style>
     <show_childcount_in_title>false</show_childcount_in_title>
     <enable_dlna>false</enable_dlna>
     <transcoding_release_delay>4</transcoding_release_delay>
     <file_settings>
       <!--audio files-->
       <file ext="mp3">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/mpeg</mime_type>
         <dlna>MP3</dlna>
       </file>
       <file ext="ogg">
         <type>AUDIO_ITEM</type>
         <mime_type>application/octet-stream</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>vorbis</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="mpc">
         <type>AUDIO_ITEM</type>
         <mime_type>application/octet-stream</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>musepack</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="wav">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-wav</mime_type>
       </file>
       <file ext="flac">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-flac</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>flac</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="wma">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-ms-wma</mime_type>
         <dlna>WMAFULL</dlna>
       </file>
       <!--image files-->
       <file ext="jpg">
         <ext>jpeg</ext>
         <type>IMAGE_ITEM</type>
         <mime_type>image/jpeg</mime_type>
         <convert enabled="false">
           <!--<dcraw enabled="true">-q 0</dcraw>-->
           <ext>png</ext>
           <mime_type>image/png</mime_type>
           <height>0</height>
           <width>0</width>
           <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
           <greater>false</greater>
           <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
           <less>false</less>
           <!--set "less" and "greater" to "false" if you always want to resize-->
         </convert>
       </file>
       <file ext="bmp">
         <type>IMAGE_ITEM</type>
         <mime_type>image/bmp</mime_type>
       </file>
       <file ext="png">
         <type>IMAGE_ITEM</type>
         <mime_type>image/png</mime_type>
       </file>
       <file ext="gif">
         <type>IMAGE_ITEM</type>
         <mime_type>image/gif</mime_type>
       </file>
       <!--video files-->
       <file ext="mpg">
         <ext>mpeg</ext>
         <type>VIDEO_ITEM</type>
         <mime_type>video/mpeg</mime_type>
       </file>
       <file ext="mp4">
         <type>VIDEO_ITEM</type>
         <mime_type>video/mp4</mime_type>
       </file>
       <file ext="avi">
         <type>VIDEO_ITEM</type>
         <mime_type>video/avi</mime_type>
       </file>
       <file ext="wmv">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-wmv</mime_type>
       </file>
       <file ext="vob">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-vob</mime_type>
       </file>
       <file ext="vdr">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-extension-vdr</mime_type>
         <transcode enabled="true">
           <ext>vob</ext>
           <mime_type>video/x-ms-vob</mime_type>
         </transcode>
       </file>
       <file ext="flv">
         <type>VIDEO_ITEM</type>
         <mime_type>application/x-flash-video</mime_type>
       </file>
       <file ext="asf">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-asf</mime_type>
       </file>
       <!--playlists-->
       <file ext="pls">
         <type>PLAYLIST</type>
         <mime_type>audio/x-scpls</mime_type>
       </file>
       <file ext="m3u">
         <type>PLAYLIST</type>
         <mime_type>audio/x-mpegurl</mime_type>
       </file>
     </file_settings>
   </device>
   <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
   <device name="PS3" enabled="false">
     <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
     <user_agent>PLAYSTATION3</user_agent>
     <!--<ip></ip>-->
     <enable_dlna>true</enable_dlna>
     <transcoding_release_delay>50</transcoding_release_delay>
     <file_settings>
       <file ext="ogg">
         <type>AUDIO_ITEM_MUSIC_TRACK</type>
         <transcode enabled="true">
           <http_encoding>stream</http_encoding>
         </transcode>
       </file>
     </file_settings>
   </device>
   <device name="Xbox 360" virtual="Xbox 360" enabled="true">
       <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
       <user_agent>Xenon</user_agent>
       <xbox360>true</xbox360>
       <file_settings>
           <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
           <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
           <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
       </file_settings>
<description_values>
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
<model_name>Windows Media Connect compatible (%s)</model_name>
<model_number>2.0</model_number>
</description_values>
   </device>
   <device name="Telegent TG 100" virtual="default" enabled="false">
     <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
     <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
     <playlist_style>file</playlist_style>
     <max_file_name_length>101</max_file_name_length>
   </device>
 </device_settings>
</fuppes_config>
```



Also, grab someone's vfolder.cfg file in this thread and drop in same directory.

Here is mine:



```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

<vfolder_layout device="default" enabled="false">

   <vfolder name="Genre">
     <vfolders property="genre">
       <items type="audioItem" />
     </vfolders>
   </vfolder>

   <vfolder name="Genre/Artists">
     <vfolders property="genre">
       <vfolders property="artist">
         <items type="audioItem" />
       </vfolders>
     </vfolders>
   </vfolder>

   <vfolder name="Artists/Albums">
     <vfolders property="artist">
       <vfolders property="album">
         <items type="audioItem" />
       </vfolders>
     </vfolders>
   </vfolder>
   
   <vfolder name="ABC/Artists/Albums">
     <vfolders split="ABC">
       <vfolders property="artist">
         <vfolders property="album">
           <items type="audioItem" />
         </vfolders>
       </vfolders>
     </vfolders>
   </vfolder>
     
   <vfolder name="Photos">
     <vfolder name="All">
       <items type="imageItem" />
     </vfolder>
     <vfolder name="Folders">
       <folders filter="contains(imageItem)" />
     </vfolder>      
   </vfolder>

   <vfolder name="Videos">
     <vfolder name="All">
       <items type="videoItem" />
     </vfolder>
     <vfolder name="Folders">
       <folders filter="contains(videoItem)" />
     </vfolder>
   </vfolder>
   
   <vfolder name="shared dirs">
     <shared_dirs full_extend="true" />
   </vfolder>
   
 </vfolder_layout>

 <vfolder_layout device="Xbox 360" enabled="true">

   <vfolder name="Music" id="1">
     <vfolder name="Album" id="7">
       <vfolders property="album" type="container.album.musicAlbum">
         <items type="audioItem" />
       </vfolders>
     </vfolder>
           
     <vfolder name="All Music" id="4">
       <items type="audioItem" />
     </vfolder>
     
     <vfolder name="Artist" id="6">
       <vfolders property="artist" type="container.person.musicArtist">
         <items type="audioItem" />
       </vfolders>
     </vfolder>
     
     <vfolder name="Folders" id="20">
       <folders filter="contains(audioItem)" />
     </vfolder>
     
     <vfolder name="Genre" id="5">
       <vfolders property="genre" type="container.genre.musicGenre">
         <items type="audioItem" />
       </vfolders>
     </vfolder>
     
     <vfolder name="Playlist" id="15" />
   </vfolder>
 
   <vfolder name="Pictures" id="3">
     <vfolder name="Album" id="13" />
     
     <vfolder name="All Pictures" id="11">
       <items type="imageItem" />
     </vfolder>
     
     <vfolder name="Date Taken" id="12" />
     
     <vfolder name="Folders" id="22">
       <folders filter="contains(imageItem)" />
     </vfolder>
   </vfolder>

   <vfolder name="Playlists" id="18">
     <vfolder name="All Playlists" id="19" />
     <vfolder name="Folders" id="23" />
   </vfolder>

   <vfolder name="Video" id="2">
     <vfolder name="Actor" id="10" />
     <vfolder name="Album" id="14" />
     <vfolder name="All Video" id="8">
<items type="videoItem" />
</vfolder>
     <vfolder name="Folders" id="21" />
     <vfolder name="Genre" id="9" />
   </vfolder>
   <vfolder name="Browse Folders" id="21">  
<shared_dirs full_extend="true" />  
</vfolder>

 </vfolder_layout>

</fuppes_vfolder_config>
```



Once you finish setting up you .cfg files, open terminal and type

```
$ sudo fuppes
```

Once you have it running, type "r" (no quotes) and wait as your directories get built. After you get back to prompt, hit "v" to rebuild your virtual directories.

And you know all is well if you can go to your browser and type in your computer's ip addy and get the fuppes config screen.  With my fuppes.cfg this would be:

[http://192.168.0.10:9137](http://192.168.0.10:9137)  <--your's will be specific to your computer's ip addy.

PM me if you have any additional questions.

---

### Post by random1027 on 2008-06-19
Gah.  This is killing me.  Ushare was working perfectly but then just stopped.  Couldn't get it to work so now I'm trying fuppes.  I don't understand what's wrong, but my 360 just can't seem to recognize Ushare or Fuppes.

Fuppes install goes fine, up to (and including) rebuilding the virtual directories.  I can even get to Fuppes' web interface [http://192.168.1.105:54123](http://192.168.1.105:54123).

But nothing shows up on my 360.  It doesn't even give me the option of "Change Software Source" no matter how many times I restart it.  When I go to my 360's media tab all it says is "Console"  "Current Disc" (grayed out) and "Portable Device" (grayed out).  Below there (where, for two glorious weeks, it said "uShare") there is nothing.

Help me PorchSong, you're my only hope.

---

### Post by random1027 on 2008-06-19
sorry for the double post but I meant to subscribe to this thread

---

### Post by xXx 0wn3d xXx on 2008-06-19
> **random1027 said:**
> Gah.  This is killing me.  Ushare was working perfectly but then just stopped.  Couldn't get it to work so now I'm trying fuppes.  I don't understand what's wrong, but my 360 just can't seem to recognize Ushare or Fuppes.

Fuppes install goes fine, up to (and including) rebuilding the virtual directories.  I can even get to Fuppes' web interface [http://192.168.1.105:54123](http://192.168.1.105:54123).

But nothing shows up on my 360.  It doesn't even give me the option of "Change Software Source" no matter how many times I restart it.  When I go to my 360's media tab all it says is "Console"  "Current Disc" (grayed out) and "Portable Device" (grayed out).  Below there (where, for two glorious weeks, it said "uShare") there is nothing.

Help me PorchSong, you're my only hope.

I had the same problem, add follow this post and add it to your fuppes config. [[Here]](http://ubuntuforums.org/showpost.php?p=3888138&postcount=9)

I have it working now but sometimes it flashes weird colors and it eventually times out. :(

---

### Post by random1027 on 2008-06-19
I wish that had been my problem.  My actual problem was much, much dumber.

I had forgotten to add my Xbox to my Firestarted.  Whoops.

Thanks so much for your help anyway, but everything is working fine now.

---

### Post by buddyd16 on 2008-06-22
is there any reason why the web interface would work using my external ip but not my internal ip? 
**Nevermind I left the network device portion of the config blank thinking it would auto pick my wireless card, long story short it did not so I edited the config with the write network device and all is well now. thank you for making this how-to.**

---

### Post by spiney_norm on 2008-07-24
Ignore this

---

### Post by spiney_norm on 2008-07-24
I got as far as

```
kent@dell-desktop:~/fuppes$ autoreconf -vfi

```
then it spits out

```
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal --force 
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf --force
configure.in:10: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:12: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

i'm pretty new to this but i'm pretty sure thats not a good thing, this probably tells me how to fix it somewhere, but i still can't figure it out... I've already tried using uShare but it won't recognise my xbox, so if I could get some help getting Feppes to work i'd be very happy.

---

### Post by daffinito on 2008-09-14
Little late, but that error can be fixed with

sudo apt-get install libtool

---

### Post by Blippo on 2008-09-21
nevermind... sorry

Just another noob

---

### Post by Yaka on 2008-09-21
tried this and what i get is this 


[ERROR] failed to bind socket to : 192.168.0.6:0
[exiting]

als tried this tut [http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04](http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04) and got the same thing

need help:confused:

---

### Post by glymph on 2008-10-19
I finally got fuppes to work to connect to my 360, many thanks to the developers :D

Originally, my firewall was stopping the connection, and I hadn't allowed my PC as an IP address, stopping me from accessing the web-based interface, once this was sorted, all I was seeing in the logs was a "NTS: ssdp:byebye" message being repeated...

The reason I couldn't connect was that I was looking in the media section trying to connect to a WMP11 PC, when I should have been searching the video section itself, and choosing the fuppes server as an alternate source.

Top stuff, many thanks to everyone involved :D

Dom

---

### Post by infallible on 2008-11-13
So, fuppes is working smoothly for me. this guide has been invaluable, thanks to the contributors here.

I have but oe complaint: it takes a long time to add new content to my large database. updating the database takes a half hour, and the virtual container takes even longer. amending source is beyond my expertise, so i thought running multiple instances of the fuppes server would give me more flexibility with new content. How would I go about this? is there a simpler, or even different, way to solve my problem? i want to stick with fuppes b/c of vitual folders and transcoding.

---

### Post by PorchSong on 2008-11-16
FYI fuppes was just upped to v627.  When I made this guide it was v611.  I think it watches your folders for new files so that you do not have to rebuild, but I might be mistaken.  

As for multiple instances, hmmm, not sure.

One thing to pay attention to:  I think, no, I know the Xbox 360 caches the directories on its hard drive, and it will not update accordingly.  The only solution I have for that is to have the Xbox 360 connect to the fuppes server when the server is not on.  It will fail to connect and then essentially give you the  "Test Your Connection" screen.  Do this, and I believe it will flush the cache so that when you load up fuppes again, it shows the new files within the directory.  

I know this happens on the windows side when connecting via media player 11.  And I am pretty sure this happens on the linux/fuppes side as well.

So, your directories and files are being updated, it is just that your Xbox 360 isn't acknowledging it.

Hope this helps.  Also, if you have trouble with fuppes once moving over to Ubuntu 8.10, I essentially reposted the guide with some tweaks to get it going on 8.10.  Just do a search for "Fuppes"

---

### Post by technosinner on 2008-11-22
Thanks so much for this.  I wasn't even able to compile Fuppes before this!  But I still have two questions:

1- I get some strange behavior with my xbox and Fuppes.  The xbox sees the fuppes server, and all the files.  But when I try to actually play them, it says it can't...

I get an error code: 19-14-80004005.  I called 1-800-4MYXBOX and I might as well have called Martha Stewart or a half-witted monkey with a banana up the...

All that to say, I can see the files, put them in a playlist (mp3) or open the player (video and pics) but I can't actually watch/listen to any of them.

Any ideas?  I tried tweaking the config files but then it just stopped working all together (couldn't connect to the server from the xbox).

2- It seems that I can't adequatly update the db.  When I connect with the web interface, I click on update and then it just hangs.  I don't know if it's doing anything, but without a progress indicator it's kind of hard to guess.  However, before I moved the config files and db outside of the home folder (for the init.d startup method) I could start and update via command line, which has a progress meter and worked like a charm.  Now I can't do that anymore...?

Thanks!
~ts, slowly unbecoming a noob.

---

### Post by TripitakaUK on 2008-11-22
Superb thread so far...

I had fuppes working using the deb package but that doesn't do the video transcoding so I wanted to rebuild to do that. Followed the thread down, got the same error as in post #8, fixed it with the solution in post #9 but now get another error:

> mark@hardy-svr:~/Public/ubuntu_storage/fuppes-SVN-578/fuppes$ autoreconf -vfi
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal --force 
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy --force
Putting files in AC_CONFIG_AUX_DIR, `..'.
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
configure.in:51: required file `../config.rpath' not found
Makefile.am: installing `./INSTALL'
autoreconf: automake failed with exit status: 1
mark@hardy-svr:~/Public/ubuntu_storage/fuppes-SVN-578/fuppes$ 


Any ideas how I can fix this and move onto the next stage?

Many thanks.

---

### Post by technosinner on 2008-11-22
TripitakaUK, I'm by no means an expert and I might be stating the obvious, but in this line 

```
"configure.in:51: required file `../config.rpath' not found"
```

your build is looking for the config.rpath, which is a building lib/script.  It should be in the SVN package, and should be in the /fuppes/ directory where you downloaded the SVN.  Just make sure it's not missing.

When I installed I put the source all in /src/fuppes/ and had no problems building.

Hope this helps a bit...
~ts

---

### Post by TripitakaUK on 2008-11-22
Yeah, I'd have thought that too, but what puzzles me is that I have followed the instructions yet this isn't doing what the OP intended it to do. Either something has changed in the release that I have grabbed or something on my machine is causing it to go screwy.

doing $ whereis config.rpath returns the following:

> mark@hardy-svr:~/Public/ubuntu_storage/fuppes-SVN-578/fuppes$ whereis config.rpath
config: /usr/share/config.kcfg /usr/share/man/man5/config.5ssl.gz


leads me to think that this file wasn't in the package and it isn't listed in the files grabbed during the earlier instruction.

---

### Post by TripitakaUK on 2008-11-23
turns out after much googling that this is an error caused by missing or out of date Gettext.

In the end, I solved my problems by looking at the various errors each time I ran the OPs original instructions and searching for what I thought was the missing or related item on synaptic. I had to install a lot of extra stuff, including g++ but eventually I got it all complete.

Just rebuilding database now and I'll see if it will run.

---

### Post by J_Gat on 2008-11-23
> **Yaka said:**
> tried this and what i get is this 


[ERROR] failed to bind socket to : 192.168.0.6:0
[exiting]

als tried this tut [http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04](http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04) and got the same thing

need help:confused:
Yaka, did you ever figure out how to fix this, or does anyone else know how to? I built everything from the source and everything seemed to go as planned. When I try to start fuppes though I get:

>             FUPPES - 0.627
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ERROR] can't resolve ip from interface "eth0".

This is my current fuppes.cfg if it somehow matters:
> <?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="true">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
	<file ext="mpg">
          <type>VIDEO_ITEM</type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <mime_type>video/mpeg</mime_type>
            <ext>mpg</ext>
            <video_codec>copy</video_codec>
            <audio_codec>mp2</audio_codec>
            <audio_samplerate>44100</audio_samplerate>
            <audio_bitrate>192000</audio_bitrate>
          </transcode>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-divx</mime_type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <ext>mpg</ext>
            <mime_type>video/mpeg</mime_type>
            <video_codec vcodec="msmpeg4">mpeg1video</video_codec>
            <video_bitrate>1800000</video_bitrate>
            <audio_codec acodec="wmav2">mp2</audio_codec>
            <audio_samplerate>44100</audio_samplerate>
            <audio_bitrate>192000</audio_bitrate>
          </transcode>
        </file>
        <file ext="mkv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-matroska</mime_type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <ext>mpg</ext>
            <mime_type>video/mpeg</mime_type>
            <video_codec>mpeg2video</video_codec>
            <video_bitrate>1800000</video_bitrate>
            <audio_codec>mp2</audio_codec>
            <audio_samplerate>44100</audio_samplerate>
            <audio_bitrate>192000</audio_bitrate>
          </transcode>
        </file>
       </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <show_empty_resolution>true</show_empty_resolution>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
  </device_settings>
</fuppes_config>

---

### Post by TripitakaUK on 2008-11-24
Try replacing "eth0" in your fuppes.cfg with you machine IP address. That worked for me.

---

### Post by J_Gat on 2008-11-24
> **TripitakaUK said:**
> Try replacing "eth0" in your fuppes.cfg with you machine IP address. That worked for me.

I have actually tried it both ways. With the ip in there I get:

```
            FUPPES - 0.627
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

== lib/Plugins/Plugin.cpp (110) :: Mon Nov 24 08:08:38 2008 ==
registered dlna profile plugin

[ERROR] failed to bind socket to : 192.168.0.3:9137
[exiting]

```

Thanks for the response though!

---

### Post by TripitakaUK on 2008-11-24
I had this one time, when I tries to start fuppes when it was already running.

Check the system monitor to see if fuppes is running in the background. If it is, kill it and try running the fuppes command again and see what happens.

I'm only a week into Ubuntu myself so still very much a newbie trying to figure out this app like you.

---

### Post by J_Gat on 2008-11-24
Nope, it's not running in the background either. I've also Googled the heck out of this and I've seen other people with the problem, but haven't found any solutions yet.

---

### Post by PorchSong on 2008-11-24
Ubuntu has a firewall that installs with version 8.10; called ufw (Uncomplicated Firewall). That is probably blocking you.

@J_Gat:

I think I found your problem.  In the fuppes.cfg you have under your ip addresses your router address.  You need and MUST put your actual computer's address not the the gateway/router address. So, look again at my fuupes.cfg file and you will see that I have mutilple addys in there.

You have 192.168.0.1  <-- usually the router gateway address.

You need:  192.168.0.10  <-- this is my specific ASSIGNED address for my computer.  

To access fuppes via browser the command is:  [http://192.168.0.10:9137](http://192.168.0.10:9137)  

I got the 9137 as an arbitrary port number and placed that value in my fuppes.cfg file.  You can choose whatever.  It is critcal that you do not allow your system to assign you an ip number unless it assigns you the same number everytime.  I have multiple computers connected, thus I assign my computer a specific address 192.168.0.10 and my Xbox360 is 192.168.0.20.  Again, look at my fuppes.cfg at the top and it will make sense.

[http://ubuntuforums.org/showthread.php?t=984325](http://ubuntuforums.org/showthread.php?t=984325)

Lastly, make sure your router is now port forwarding your Xbox 360 addy to your static ip now.  Again, with my system I port forward port 9137 to 192.168.0.10.

Hope this helps.

---

### Post by J_Gat on 2008-11-25
No, the 192.168.0.1 that is in my fuppes.cfg is in the comment for the allowed ip section. For the interface I have eth0, although I have also tried it with 192.168.0.3 which is my PC's static IP address. Neither of these will work because it won't bind to the interface. I was leaving the allowed ip address area blank right now to allow everything just because I didn't set a static address on the PS3 yet.

I also did "sudo ufw status" and it says "Firewall not loaded".

Thanks again for the help though! Maybe someday I will find an answer for this. I have tversity and the playon servers running in XP in a virtual box...but like most people here I would rather have an Ubuntu solution.

---

### Post by Kalifornia909 on 2008-11-27
i have a compiling problem. i get the make: *** No targets specified and no makefile found.  Stop. ive ran this how to like 10 times. my autoconf and gettext is up to date. please help

---

### Post by TripitakaUK on 2008-11-27
can you post your console output here? I'm a definate noob at ubuntu but have been round the mill with it over the last two weeks.

What version of ubuntu?
What version of fuppes?

I could't get it to work on Intrepid so I dropped back to Hardy and got fuppes 0.627.

---

### Post by PorchSong on 2008-11-27
> **Kalifornia909 said:**
> i have a compiling problem. i get the make: *** No targets specified and no makefile found.  Stop. ive ran this how to like 10 times. my autoconf and gettext is up to date. please help

This is a common install problem people are having.  Completely clean your system off and start fresh.  The automake and gettext programs were causing all sorts of headaches--so the only solution I found was to uninstall them and reinstall them again.

Use the guide:

[http://ubuntuforums.org/showthread.php?t=984325](http://ubuntuforums.org/showthread.php?t=984325)

---

### Post by exz on 2008-12-15
Hi.. Thanks for a good article.. Just wanted to share some things that needed to be done in order to get fuppes to compile on 8.10 (intrepid). 
```
apt-get install libmp4v2-dev libmp4v2-0 pkg-config libtool
```

I might have missed something but these were some key steps for getting it to compile.

---

### Post by k33bz on 2008-12-20
nvm found it in synaptic

---

### Post by TheProdigy2215 on 2008-12-31
Still at the first bit of instructions.  Trying to run autoreconf but I think it fails; can't get next steps to work.  Utter newb, new Windows convert.
Thanks.

user@user-desktop:~/Desktop/Fuppes/fuppes-SVN-578$ autoreconf -vfi
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal --force 
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy --force
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
autoreconf: Leaving directory `.'
user@user-desktop:~/Desktop/Fuppes/fuppes-SVN-578$ ./configure --enable-video-transcoding
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for off_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PCRE... configure: error: Package requirements (libpcre >= 5.0) were not met:

No package 'libpcre' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PCRE_CFLAGS
and PCRE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by TripitakaUK on 2009-01-01
Are you running it on Ubuntu 8.10 Intrepid? I got the same error when I tried that and never got around it so moved to Hardy and the problem went away.

If you are a noob (like me), I'd definately suggest that Hardy is the better install to begin with.

Also, what are you streaming to, 360 or PS3? If it's a 360, make sure that you have access to Xbox Live.

---

### Post by DonovanM11 on 2009-01-02
I have an XBOX 360. I was having the same problem with libpcre, so I downloaded a .deb of the FUPPES. I can stream music perfectly but when I go to my video library, it just says "No videos found." How can I get it to show my videos?

---

### Post by jowilkin on 2009-01-03
I had the libpcre error on Ubuntu 8.10 but it went away after 'sudo aptitude install libpcre3-dev'

---

### Post by TripitakaUK on 2009-01-03
DonovanM11:

My guess is that the .deb package is not compiled with video transcoding built in and your videos are not in a format that the 360 understands natively. To test this, drop a .wmv file into one of the folders, redo the database and vconfig on fuppes, restart the xbox and see if it finds the .wmv file.

---

### Post by DonovanM11 on 2009-01-03
No, I tried sticking in a .wmv file and it still says no videos found. I don't know if this is important, but it gives me a parser warning.
```
:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"

```

---

### Post by DonovanM11 on 2009-01-07
I looked at my 192.168.1.100:9137, and went to status. Under transcoding it says "Neither LAME nor TwoLame found. Transcoding disabled!". In my fuppes.cfg I see a line commented out <!--[lame|twolame]-->. Do I have to uncomment this line?

---

### Post by enginuysal on 2009-01-12
You're the man PorchSong. I had tried to install this 3 times with no chance, but with your instructions it was smooth, even for a noob like me. THANK YOU VERY MUCH...

I've got 3 problems now;

1. The wife knows how to use xbox but not ubuntu. Since she can only switch the computer to get xbox ready to watch her damn tv series, I need a way to automate this process so fuppes starts and rebuilds its database when computer starts. Do you think this is possible?

2. I think I need transcoding (even if you say it's not necessary in your instructions) because I'm not able to play some content such as .dat, .3gp and .wmv files. (yes, wife needs them indeed) How can I enable transcoding? Can I choose which file types to be transcoded and let xbox play whatever she can play?

3. My dir list contains 3 directories; videos, pictures and music. When I go to xbox 360 and select, say, my videos, all these 3 directories are listed there. (Yes, this confuses the wife). Is there a way to see only corresponding directory in xbox menus?

I'm on Ubuntu 8.04 and wireless connection.

Thanks again for all your efforts, I really appreciate it...

Engin Uysal

---

### Post by Skooj on 2009-01-14
first of all, a quick solution to this:

> **enginuysal said:**
> 
1. The wife knows how to use xbox but not ubuntu. Since she can only switch the computer to get xbox ready to watch her damn tv series, I need a way to automate this process so fuppes starts and rebuilds its database when computer starts. Do you think this is possible?


[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d) here is a link to the wiki explaining how to setup an auto-starting init.d script. should help.

now I have a question of my own. of the countless threads about this, I chose this one due to it having the most recent activity that I could find. I am currently running the most up-to-date version of fuppes (rev 627) from the subversion repository on ubuntu 7.10. I started with 576 or something like that and removed it to try the most up to date. I have not been able to get my 360 to see the fuppes server. I have used the cfg file from the wiki, the cfg file posted in the OP, and also tried the fix from this post: [http://ubuntuforums.org/showthread.php?p=3888138](http://ubuntuforums.org/showthread.php?p=3888138) but all to no avail on either version.

when I start up fuppes, I see this:
```
            FUPPES - 0.UNKNOWN
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

== lib/Plugins/Plugin.cpp (139) :: Wed Jan 14 10:17:17 2009 ==
registered transcoder plugin "ffmpeg"

== lib/Plugins/Plugin.cpp (110) :: Wed Jan 14 10:17:17 2009 ==
registered dlna profile plugin

== lib/Plugins/Plugin.cpp (117) :: Wed Jan 14 10:17:17 2009 ==
registered metadata plugin "libavformat"

== lib/Plugins/Plugin.cpp (124) :: Wed Jan 14 10:17:17 2009 ==
registered audio decoder plugin "vorbis"

== lib/Plugins/Plugin.cpp (117) :: Wed Jan 14 10:17:17 2009 ==
registered metadata plugin "taglib"

<insert watch listing crap>

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

== lib/Fuppes.cpp (346) :: Wed Jan 14 10:17:50 2009 ==
new device: Xbox 360 :: MediaRenderer

new UPnP device:
Xbox 360 (MediaRenderer)


```

so it obviously sees my 360, but my 360 will not find it in the system settings or anywhere. 

here's my fuppes.cfg (note: I used the IP instead of interface name to see if that worked, which it did not):
```
<?xml version="1.0" encoding="UTF-8"?>

<fuppes_config version="0.7.2.3">

 <shared_objects>

   <dir>/home/leech/downloads</dir>

 </shared_objects>



<network>

   <!--empty = automatic detection-->

   <interface>192.168.1.4</interface>

   <!--empty or 0 = random port-->

   <http_port>9137</http_port>

   <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->

   <allowed_ips>

     <!--<ip>192.168.0.1</ip>-->

     <ip>192.168.1.8</ip>

   </allowed_ips>

 </network>

 <content_directory>

   <!--a list of possible charsets can be found under:

     http://www.gnu.org/software/libiconv/-->

   <local_charset>UTF-8</local_charset>

   <!--libs used for metadata extraction when building the database. [true|false]-->

   <use_imagemagick>true</use_imagemagick>

   <use_taglib>true</use_taglib>

   <use_libavformat>true</use_libavformat>

 </content_directory>

 <transcoding>

   <!--[lame|twolame]-->

   <audio_encoder>lame</audio_encoder>

   <!--[true|false]-->

   <transcode_vorbis>true</transcode_vorbis>

   <transcode_musepack>true</transcode_musepack>

   <transcode_flac>true</transcode_flac>

 </transcoding>

 <device_settings>

   <!--"default" settings are inhertied by specific devices and can be overwritten-->

   <device name="default">

     <!--specify the maximum length for file names (0 or empty = unlimited)-->

     <max_file_name_length>0</max_file_name_length>

     <!--[file|container]-->

     <playlist_style>file</playlist_style>

     <show_childcount_in_title>false</show_childcount_in_title>

     <enable_dlna>false</enable_dlna>

     <transcoding_release_delay>4</transcoding_release_delay>

     <file_settings>

       <!--audio files-->

       <file ext="mp3">

         <type>AUDIO_ITEM</type>

         <mime_type>audio/mpeg</mime_type>

         <dlna>MP3</dlna>

       </file>

       <file ext="ogg">

         <type>AUDIO_ITEM</type>

         <mime_type>application/octet-stream</mime_type>

         <transcode enabled="true">

           <ext>mp3</ext>

           <mime_type>audio/mpeg</mime_type>

           <dlna>MP3</dlna>

           <http_encoding>chunked</http_encoding>

           <decoder>vorbis</decoder>

           <encoder>lame</encoder>

           <bitrate>192</bitrate>

           <samplerate>44100</samplerate>

         </transcode>

       </file>

       <file ext="mpc">

         <type>AUDIO_ITEM</type>

         <mime_type>application/octet-stream</mime_type>

         <transcode enabled="true">

           <ext>mp3</ext>

           <mime_type>audio/mpeg</mime_type>

           <dlna>MP3</dlna>

           <http_encoding>chunked</http_encoding>

           <decoder>musepack</decoder>

           <encoder>lame</encoder>

           <bitrate>192</bitrate>

           <samplerate>44100</samplerate>

         </transcode>

       </file>

       <file ext="wav">

         <type>AUDIO_ITEM</type>

         <mime_type>audio/x-wav</mime_type>

       </file>

       <file ext="flac">

         <type>AUDIO_ITEM</type>

         <mime_type>audio/x-flac</mime_type>

         <transcode enabled="true">

           <ext>mp3</ext>

           <mime_type>audio/mpeg</mime_type>

           <dlna>MP3</dlna>

           <http_encoding>chunked</http_encoding>

           <decoder>flac</decoder>

           <encoder>lame</encoder>

           <bitrate>192</bitrate>

           <samplerate>44100</samplerate>

         </transcode>

       </file>

       <file ext="wma">

         <type>AUDIO_ITEM</type>

         <mime_type>audio/x-ms-wma</mime_type>

         <dlna>WMAFULL</dlna>

       </file>

       <!--image files-->

       <file ext="jpg">

         <ext>jpeg</ext>

         <type>IMAGE_ITEM</type>

         <mime_type>image/jpeg</mime_type>

         <convert enabled="false">

           <!--<dcraw enabled="true">-q 0</dcraw>-->

           <ext>png</ext>

           <mime_type>image/png</mime_type>

           <height>0</height>

           <width>0</width>

           <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->

           <greater>false</greater>

           <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->

           <less>false</less>

           <!--set "less" and "greater" to "false" if you always want to resize-->

         </convert>

       </file>

       <file ext="bmp">

         <type>IMAGE_ITEM</type>

         <mime_type>image/bmp</mime_type>

       </file>

       <file ext="png">

         <type>IMAGE_ITEM</type>

         <mime_type>image/png</mime_type>

       </file>

       <file ext="gif">

         <type>IMAGE_ITEM</type>

         <mime_type>image/gif</mime_type>

       </file>

       <!--video files-->

       <file ext="mpg">

         <ext>mpeg</ext>

         <type>VIDEO_ITEM</type>

         <mime_type>video/mpeg</mime_type>

       </file>

       <file ext="mp4">

         <type>VIDEO_ITEM</type>

         <mime_type>video/mp4</mime_type>

       </file>

       <file ext="avi">

         <type>VIDEO_ITEM</type>

         <mime_type>video/avi</mime_type>

       </file>

       <file ext="wmv">

         <type>VIDEO_ITEM</type>

         <mime_type>video/x-ms-wmv</mime_type>

       </file>

       <file ext="vob">

         <type>VIDEO_ITEM</type>

         <mime_type>video/x-ms-vob</mime_type>

       </file>

       <file ext="vdr">

         <type>VIDEO_ITEM</type>

         <mime_type>video/x-extension-vdr</mime_type>

         <transcode enabled="true">

           <ext>vob</ext>

           <mime_type>video/x-ms-vob</mime_type>

         </transcode>

       </file>

       <file ext="flv">

         <type>VIDEO_ITEM</type>

         <mime_type>application/x-flash-video</mime_type>

       </file>

       <file ext="asf">

         <type>VIDEO_ITEM</type>

         <mime_type>video/x-ms-asf</mime_type>

       </file>

       <!--playlists-->

       <file ext="pls">

         <type>PLAYLIST</type>

         <mime_type>audio/x-scpls</mime_type>

       </file>

       <file ext="m3u">

         <type>PLAYLIST</type>

         <mime_type>audio/x-mpegurl</mime_type>

       </file>

     </file_settings>

   </device>

   <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->

   <device name="PS3" enabled="false">

     <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>

     <user_agent>PLAYSTATION3</user_agent>

     <!--<ip></ip>-->

     <enable_dlna>true</enable_dlna>

     <transcoding_release_delay>50</transcoding_release_delay>

     <file_settings>

       <file ext="ogg">

         <type>AUDIO_ITEM_MUSIC_TRACK</type>

         <transcode enabled="true">

           <http_encoding>stream</http_encoding>

         </transcode>

       </file>

     </file_settings>

   </device>

   <device name="Xbox 360" virtual="Xbox 360" enabled="true">

       <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>

       <user_agent>Xenon</user_agent>

       <xbox360>true</xbox360>

       <file_settings>

           <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>

           <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>

           <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>

       </file_settings>

<description_values>

<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>

<model_name>Windows Media Connect compatible (%s)</model_name>

<model_number>2.0</model_number>

</description_values>

   </device>

   <device name="Telegent TG 100" virtual="default" enabled="false">

     <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>

     <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>

     <playlist_style>file</playlist_style>

     <max_file_name_length>101</max_file_name_length>

   </device>

 </device_settings>

</fuppes_config>
```

and my vfolder.cfg:
```
<?xml version="1.0" encoding="UTF-8"?>

<fuppes_vfolder_config version="0.2">



<vfolder_layout device="default" enabled="false">



   <vfolder name="Genre">

     <vfolders property="genre">

       <items type="audioItem" />

     </vfolders>

   </vfolder>



   <vfolder name="Genre/Artists">

     <vfolders property="genre">

       <vfolders property="artist">

         <items type="audioItem" />

       </vfolders>

     </vfolders>

   </vfolder>



   <vfolder name="Artists/Albums">

     <vfolders property="artist">

       <vfolders property="album">

         <items type="audioItem" />

       </vfolders>

     </vfolders>

   </vfolder>

   

   <vfolder name="ABC/Artists/Albums">

     <vfolders split="ABC">

       <vfolders property="artist">

         <vfolders property="album">

           <items type="audioItem" />

         </vfolders>

       </vfolders>

     </vfolders>

   </vfolder>

     

   <vfolder name="Photos">

     <vfolder name="All">

       <items type="imageItem" />

     </vfolder>

     <vfolder name="Folders">

       <folders filter="contains(imageItem)" />

     </vfolder>      

   </vfolder>



   <vfolder name="Videos">

     <vfolder name="All">

       <items type="videoItem" />

     </vfolder>

     <vfolder name="Folders">

       <folders filter="contains(videoItem)" />

     </vfolder>

   </vfolder>

   

   <vfolder name="shared dirs">

     <shared_dirs full_extend="true" />

   </vfolder>

   

 </vfolder_layout>



 <vfolder_layout device="Xbox 360" enabled="true">



   <vfolder name="Music" id="1">

     <vfolder name="Album" id="7">

       <vfolders property="album" type="container.album.musicAlbum">

         <items type="audioItem" />

       </vfolders>

     </vfolder>

           

     <vfolder name="All Music" id="4">

       <items type="audioItem" />

     </vfolder>

     

     <vfolder name="Artist" id="6">

       <vfolders property="artist" type="container.person.musicArtist">

         <items type="audioItem" />

       </vfolders>

     </vfolder>

     

     <vfolder name="Folders" id="20">

       <folders filter="contains(audioItem)" />

     </vfolder>

     

     <vfolder name="Genre" id="5">

       <vfolders property="genre" type="container.genre.musicGenre">

         <items type="audioItem" />

       </vfolders>

     </vfolder>

     

     <vfolder name="Playlist" id="15" />

   </vfolder>

 

   <vfolder name="Pictures" id="3">

     <vfolder name="Album" id="13" />

     

     <vfolder name="All Pictures" id="11">

       <items type="imageItem" />

     </vfolder>

     

     <vfolder name="Date Taken" id="12" />

     

     <vfolder name="Folders" id="22">

       <folders filter="contains(imageItem)" />

     </vfolder>

   </vfolder>



   <vfolder name="Playlists" id="18">

     <vfolder name="All Playlists" id="19" />

     <vfolder name="Folders" id="23" />

   </vfolder>



   <vfolder name="Video" id="2">

     <vfolder name="Actor" id="10" />

     <vfolder name="Album" id="14" />

     <vfolder name="All Video" id="8">

<items type="videoItem" />

</vfolder>

     <vfolder name="Folders" id="21"> 

  <folders filter="contains(videoItem)" /> 

</vfolder>

     <vfolder name="Genre" id="9" />

   </vfolder>

   <vfolder name="Browse Folders" id="21">  

<shared_dirs full_extend="true" />  

</vfolder>



 </vfolder_layout>



</fuppes_vfolder_config>
```

I have no idea what's going wrong or where, but nothing wants to work.

---

### Post by PorchSong on 2009-01-15
> **enginuysal said:**
> You're the man PorchSong. I had tried to install this 3 times with no chance, but with your instructions it was smooth, even for a noob like me. THANK YOU VERY MUCH...

I've got 3 problems now;

1. The wife knows how to use xbox but not ubuntu. Since she can only switch the computer to get xbox ready to watch her damn tv series, I need a way to automate this process so fuppes starts and rebuilds its database when computer starts. Do you think this is possible?

2. I think I need transcoding (even if you say it's not necessary in your instructions) because I'm not able to play some content such as .dat, .3gp and .wmv files. (yes, wife needs them indeed) How can I enable transcoding? Can I choose which file types to be transcoded and let xbox play whatever she can play?

3. My dir list contains 3 directories; videos, pictures and music. When I go to xbox 360 and select, say, my videos, all these 3 directories are listed there. (Yes, this confuses the wife). Is there a way to see only corresponding directory in xbox menus?

I'm on Ubuntu 8.04 and wireless connection.

Thanks again for all your efforts, I really appreciate it...

Engin Uysal

You are welcome.  I do see people having problems with the libpcre3-dev error but the fix is:

```
sudo aptitude install libpcre3-dev
```

I think I just already had that installed so I never got that error.  I will edit my instructions to help others with that problem.

Now to address your problems:

1.  Follow the wiki link Skooj provided for making startup scripts.  I just do not like having scripts run at startup that open a console with sudo commands, etc. So, I just open a console when I boot up and do the sudo fuppes command and leave it on all the time--I just minimize it.

2. For the .dat, .3gp and .wmv files, the .wmv's should work as the xbox360 can handle those.  Those vids might have old codecs installed, thus failing.  You will run into this with your older divx (.avi's) as well.  Not a fuppes issue, but an Xbox360 issue.  As for the others, I do not think fuppes is set up to handle those extensions.  And, surely the xbox360 cannot.  So, you might be SOL. Fuppes also cannot handle .mkv files either. But then again, it's not the .mkv, it really is the audio streams within the .mkv that mucks it up from I have researched and found.  I think some coders are working on that.

3.  No work around on those directories.  If you actually go into them, you will see that they contain vids that are with your audio and picture files--not actual pictures or .mp3's.  There might be a way to disable via messing with the vfolder.cfg code, but I have not bothered.  I might mess around with that this weekend and report back. 

So, I guess I really have not answered your questions, but at least gave you my thoughts.  Sorry.

---

### Post by PorchSong on 2009-01-15
BTW, I several weeks ago updated this guide for an install on 8.10 and addressed the libpcre issue.  I have tried to edit this post, but keep getting sql errors, so here is the link to the new install guide.

This will work on 8.10 with fuppes version 627.

Enjoy.

[http://ubuntuforums.org/showthread.php?t=984325]("http://ubuntuforums.org/showthread.php?t=984325")

---

### Post by wolf4914 on 2009-01-25
> **PorchSong said:**
> You are welcome.  I do see people having problems with the libpcre3-dev error but the fix is:

```
sudo aptitude install libpcre3-dev
```

I think I just already had that installed so I never got that error.  I will edit my instructions to help others with that problem.

Now to address your problems:

1.  Follow the wiki link Skooj provided for making startup scripts.  I just do not like having scripts run at startup that open a console with sudo commands, etc. So, I just open a console when I boot up and do the sudo fuppes command and leave it on all the time--I just minimize it.

2. For the .dat, .3gp and .wmv files, the .wmv's should work as the xbox360 can handle those.  Those vids might have old codecs installed, thus failing.  You will run into this with your older divx (.avi's) as well.  Not a fuppes issue, but an Xbox360 issue.  As for the others, I do not think fuppes is set up to handle those extensions.  And, surely the xbox360 cannot.  So, you might be SOL. Fuppes also cannot handle .mkv files either. But then again, it's not the .mkv, it really is the audio streams within the .mkv that mucks it up from I have researched and found.  I think some coders are working on that.

3.  No work around on those directories.  If you actually go into them, you will see that they contain vids that are with your audio and picture files--not actual pictures or .mp3's.  There might be a way to disable via messing with the vfolder.cfg code, but I have not bothered.  I might mess around with that this weekend and report back. 

So, I guess I really have not answered your questions, but at least gave you my thoughts.  Sorry.

I have exactly the same issue with folders as in 3. Will keep an eye on the post, Compiled on Jaunty alpha 3 64 bit. The only one server that I saw showing all multimedia correctly is Twonky Media bit their v 5 does not work right on linux and costs $$.
    So will stick with open source solutions

---

### Post by wolf4914 on 2009-01-25
I also wondered how do I recompile with transcoding and all the codecs enabled that are listed here :

i
general information:
  version     : 0.628
  hostname    : Jaunty-64
  OS          : Linux 2.6.28-5-generic
  build at    : Jan 25 2009 01:58:45
  build with  : 4.3.3 20090119 (prerelease)
  address     : 192.168.1.2
  sqlite      : 3.5.9
  log-level   : 1 (normal)
  webinterface: [http://192.168.1.2:9139/](http://192.168.1.2:9139/)

configuration file:
  /root/.fuppes/fuppes.cfg

faad: disabled
flac: disabled
iconv: enabled
ImageMagick++: disabled
ImageMagick Wand: disabled
inotify: enabled
lame: disabled
libavformat: disabled
libnotify: disabled
mad: disabled
mp4ff: disabled
mpeg4ip: enabled
musepack: disabled
simage: disabled
inotify: enabled
taglib: disabled
tremor: disabled
twolame: disabled
uuid: disabled
vorbis: disabled
[VirtualContainer] create virtual container layout started at Sun Jan 25 03:59:22 2009

   Half of my music collection is in flac so no wonder it won't play it but why would mp3's won't play ?

---

### Post by rattking on 2009-01-25
I had to install these packages to get fuppes to compile with all codec support
I have the Medibuntu repository enabled or you may need to recompile ffmpeg as well 

sudo apt-get install libpcre3-dev libxml2-dev libsqlite3-dev libtag1-dev libmp3lame-dev libflac-dev libmpcdec-dev libfaac-dev libfaad-dev liba52-0.7.4-dev libxvidcore4-dev libx264-dev ffmpeg libavutil-dev libogg-dev libtheora-dev libvorbis-dev libavcodec-dev libmad0-dev libtwolame-dev libsimage-dev libavformat-dev libmp4v2-dev libmagick9-dev libmagick++9-dev libexiv2-dev

---

### Post by wolf4914 on 2009-01-25
I will try tonight ans post the results. It won't straight out the folders mess though. What is the right way to recompile so I pass all the codecs for it ?

---

### Post by PorchSong on 2009-01-31
> **wolf4914 said:**
> I will try tonight ans post the results. It won't straight out the folders mess though. What is the right way to recompile so I pass all the codecs for it ?

I don't use fuppes to stream my music, but did some searching and apparently the music sort feature is broken.  Some guy found a solution and I sent him a private message asking for solution.  Apparently fuppes was coded incorrectly when looking up mp3 tags and just clumps them all together.  He was able to get fuppes to sort by artist, album, etc.  But, for vids, fuppes is tight.  

Here is a link to Karlhm76's posts #38 & #39 --  if someone knows how to install his solution please post the solution:

"the second problem of the music not being categorised was solved by installing the taglib development files and recompiling"

[http://ubuntuforums.org/showthread.php?t=618781&page=4](http://ubuntuforums.org/showthread.php?t=618781&page=4)

PorchSong

---

### Post by sh0x12 on 2009-02-07
I installed taglib and used Karlhm76's fuppes.cfg and vfolder.cfg and now my music is categorized right in xbox360. Excellent!

[http://developer.kde.org/~wheeler/taglib.html](http://developer.kde.org/~wheeler/taglib.html)

---

### Post by orthod0ks on 2009-02-16
After playing around with it for a long time and trying about 300 config files, I've finally gotten Fuppes working to stream both audio and video. I did just discover another issue - I'm not able to rewind/fast forward/skip tracks on my videos. Any reason why that might be?

**Update**
I used the config files posted by Ensign R in [this thread]("http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37"), and all my problems appear to be magically resolved.

---

### Post by foolsgold7 on 2010-02-01
hi im a noob and getting mesage below after entering sudo fuppes

foolsgold@foolsgold-laptop:~$ sudo fuppes
WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.661
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de]("http://fuppes.ulrich-voelkel.de/")

[ERROR] can't resolve ip from interface "eth0".
foolsgold@foolsgold-laptop:~$ 

any help greatly appreciated

---

