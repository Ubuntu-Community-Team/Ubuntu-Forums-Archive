---
title: "Fuppes wont install"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by timstone on 2008-10-05
after configuring and running the make command i ran sudo make install and it ran for a bit, then it stops and this is what shows at the end...

```

Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'fuppes' '/usr/local/bin/fuppes'
/usr/bin/install -c .libs/fuppes /usr/local/bin/fuppes
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'fuppesd' '/usr/local/bin/fuppesd'
/usr/bin/install -c .libs/fuppesd /usr/local/bin/fuppesd
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/tim/Desktop/fuppes/src'
make[2]: Leaving directory `/home/tim/Desktop/fuppes/src'
make[1]: Leaving directory `/home/tim/Desktop/fuppes/src'
Making install in src/gnome
make[1]: Entering directory `/home/tim/Desktop/fuppes/src/gnome'
make[2]: Entering directory `/home/tim/Desktop/fuppes/src/gnome'
test -z "/usr/local/libexec" || /bin/mkdir -p "/usr/local/libexec"
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
make[2]: Leaving directory `/home/tim/Desktop/fuppes/src/gnome'
make[1]: Leaving directory `/home/tim/Desktop/fuppes/src/gnome'
make[1]: Entering directory `/home/tim/Desktop/fuppes'
make[2]: Entering directory `/home/tim/Desktop/fuppes'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/tim/Desktop/fuppes'
make[1]: Leaving directory `/home/tim/Desktop/fuppes'

```

can someone help me out?
[I]
this is cross-posted from another section...just hoping to get an answer[/I]

---

### Post by jrothwell97 on 2008-10-05
It's not an error message: it's finished! The 'nothing to be done' thing just means it's finished and there's no more compiling for it to do. So Fuppes is now installed.

---

### Post by timstone on 2008-10-05
if that is the case...where did install to?   i looked for the config file and couldnt find it

---

### Post by jrothwell97 on 2008-10-05
hmm... have you looked in /etc? /usr/local/lib?

---

### Post by timstone on 2008-10-05
yea i used the search program, there is no fuppes.cfg

---

### Post by jrothwell97 on 2008-10-05
OK, a quick swoosh of a FWSE revealed this: [http://ubuntuforums.org/showthread.php?t=597650](http://ubuntuforums.org/showthread.php?t=597650)

If you want to use the file manager to find this file, you will have to enable "Show Hidden Files" (anything with a full stop [.] before it in Linux is a 'hidden' file). It will be in your home folder. Failing that, open up a terminal and run

```
gedit ~/.fuppes/fuppes.cfg
```

If you're using Kubuntu, replace gedit with kedit or kate. On Xubuntu, replace it with mousepad.

Good luck.

---

### Post by timstone on 2008-10-05
ok, well i pulled up the config file...the little "howto" i was reading didnt say i had to do that....if i run into more problems ill post here or PM you, instead of making a new thread

---

### Post by jrothwell97 on 2008-10-05
Please post to this thread, so everyone can read it and learn how to install Fuppes.

Glad it worked :-)

---

### Post by timstone on 2008-10-05
alright...fuppes is installed but my 360 wont see the computer at all...ive tried other peoples configs and still nothing.....

here are my config files if it helps anyone solve my mystery...

fuppes.cfg
```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/tim/Desktop/Media</dir>
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>wlan0</interface>
    <!--empty or 0 = random port-->
    <http_port>9567</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <ip>192.168.2.1</ip>
      <ip>192.168.2.2</ip>
      <ip>192.168.2.3</ip>
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
            <file ext="avi">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="true">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
<description_values>
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
<model_name>Windows Media Connect compatible (%s)</model_name>
<model_number>2.0</model_number>
</description_values> 
        </file_settings>
    </device>
    <device name="Noxon audio" virtual="default" enabled="false">
      <!--Please enter the address of your Noxon. Automatic detection is impossible because the Noxon does not send a "user-agent" in it's requests-->
      <!--<ip></ip>-->
      <playlist_style>container</playlist_style>
      <show_childcount_in_title>true</show_childcount_in_title>
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

vfolder.cfg
```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="Xbox 360" enabled="true" create_references="true">

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
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21">
			   <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>

```

Now I'm not completly sure if I did this right, but in that Fuppes howto it said to put the vfolder.cfg in the same folder as fuppes.cfg.

Well since fuppes.cfg is hidden (i dont know how to unhide it) I just typed gedit ~/.fuppes/vfolder.cfg  which brought up a clean window, and I just pasted the vfolder contents and saved it.

Also...this is what happens when I run fuppes

```

            FUPPES - SVN-r578
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

webinterface: http://192.168.2.3:9567

r = rebuild database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

r
[ContentDatabase] create database at Sun Oct  5 20:27:36 2008
read shared directories
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Sun Oct  5 20:27:36 2008
v
[VirtualContainer] create virtual container layout started at Sun Oct  5 20:27:44 2008
[VirtualContainer] virtual container layout created at Sun Oct  5 20:27:44 2008
:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
                                                                               ^
== lib/Fuppes.cpp (336) :: Sun Oct  5 20:28:11 2008 ==
new device: Xbox 360 :: MediaRenderer

new UPnP device:
Xbox 360 (MediaRenderer)

```

I also enabled port forwarding on the port i would like to use (9567)

---

### Post by timstone on 2008-10-05
[SIZE="7"]omg!![/SIZE]   i got it working, xbox sees it, and the media :)  yay

if anyone is having a problem send me a message and i can send you my fuppes.cfg and vfolder.cfg

---

### Post by blackhole82 on 2008-10-17
My compile fails.  Does anyone know what I need to do to fix this?

```
/usr/bin/ld: cannot find -ldts
collect2: ld returned 1 exit status
make[2]: *** [libfuppes.la] Error 1
make[2]: Leaving directory `/home/jason/fuppes-SVN-578/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jason/fuppes-SVN-578/src'
make: *** [all-recursive] Error 1
```

---

