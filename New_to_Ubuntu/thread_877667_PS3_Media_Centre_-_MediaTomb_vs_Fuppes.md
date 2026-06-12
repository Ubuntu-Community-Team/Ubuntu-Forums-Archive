---
title: "PS3 Media Centre - MediaTomb vs Fuppes"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Fajman on 2008-08-02
Well I've finally set up a media center (Fuppes) on Ubuntu 8.04 that seems as good as (if not better) than TVersity (on windows). I should point out that DivX is the main purpose for my media center. I'm an Ubuntu noob so I may have put a few steps wrong... but it was all fun.

I tried pretty much every linux media center option available except for Twonky (because you have to fork out cash)

Me experiences are below
1. GMediaServer - Doesn't even seem to do DivX...waste of time for me. Might be ok for audio though.

2. UShare - Kept getting 'Unsupported Data' for DivX files and after a lot of searching/playing I finally gave up.

3. MediaTomb - This seems to be the one everyone is raving about for the PS3. I got it working after a few minor problems. 
[INDENT]First Prob - 2 configuration files, basically it loads up ~\.mediatomb\config.xml instead of \etc\mediatomb\config.xml as i was expecting. [/INDENT]
[INDENT]Second Prob - Unsupported Data comes up for divX files so I needed to tweak my config.xml (see below) and got it working[/INDENT]

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlnssi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
<server>
<ui enabled="yes">
<accounts enabled="no" session-timeout="30">
<account user="mediatomb" password="mediatomb"/>
</accounts>
</ui>
<name>MediaTomb</name>
<udn>uuid:c4425c07-a131-403b-88a6-e1e2dc163b7f</udn>
<home>/var/lib/mediatomb</home>
<webroot>/usr/share/mediatomb/web</webroot>
<storage>
<sqlite3 enabled="yes">
<database-file>sqlite3.db</database-file>
</sqlite3>
<mysql enabled="no">
<host>localhost</host>
<username>mediatomb</username>
<database>mediatomb</database>
</mysql>
</storage>
<protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
<!--
Uncomment the lines below to get rid of jerky avi playback on the
DSM320 or to enable subtitles support on the DSM units
-->
<!--
<custom-http-headers>
<add header="X-User-Agent: redsonic"/>
</custom-http-headers>

<manufacturerURL>redsonic.com</manufacturerURL>
<modelNumber>105</modelNumber>
-->
<!-- Uncomment the line below if you have a Telegent TG100 -->
<!--
<upnp-string-limit>101</upnp-string-limit>
-->
</server>
<import hidden-files="no">
<scripting script-charset="UTF-8">
<common-script>/usr/share/mediatomb/js/common.js</common-script>
<playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
<virtual-layout type="builtin">
<import-script>/usr/share/mediatomb/js/import.js</import-script>
</virtual-layout>
</scripting>
<mappings>
<extension-mimetype ignore-unknown="no">
<map from="mp3" to="audio/mpeg"/>
<map from="ogg" to="application/ogg"/>
<map from="asf" to="video/x-ms-asf"/>
<map from="asx" to="video/x-ms-asf"/>
<map from="wma" to="audio/x-ms-wma"/>
<map from="wax" to="audio/x-ms-wax"/>
<map from="wmv" to="video/x-ms-wmv"/>
<map from="wvx" to="video/x-ms-wvx"/>
<map from="wm" to="video/x-ms-wm"/>
<map from="wmx" to="video/x-ms-wmx"/>
<map from="m3u" to="audio/x-mpegurl"/>
<map from="pls" to="audio/x-scpls"/>
<map from="flv" to="video/x-flv"/>
<!-- Uncomment the line below for PS3 divx support -->
<map from="avi" to="video/divx"/>
<map from="divx" to="video/divx"/>
<!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
<!-- <map from="avi" to="video/avi"/> -->
</extension-mimetype>
<mimetype-upnpclass>
<map from="audio/*" to="object.item.audioItem.musicTrack"/>
<map from="video/*" to="object.item.videoItem"/>
<map from="image/*" to="object.item.imageItem"/>
</mimetype-upnpclass>
<mimetype-contenttype>
<treat mimetype="video/x-divx" as="avi"/>
<treat mimetype="audio/mpeg" as="mp3"/>
<treat mimetype="application/ogg" as="ogg"/>
<treat mimetype="audio/x-flac" as="flac"/>
<treat mimetype="image/jpeg" as="jpg"/>
<treat mimetype="audio/x-mpegurl" as="playlist"/>
<treat mimetype="audio/x-scpls" as="playlist"/>
<treat mimetype="audio/x-wav" as="pcm"/>
<treat mimetype="video/x-msvideo" as="avi"/>
</mimetype-contenttype>
</mappings>
</import>
<transcoding enabled="no">
<mimetype-profile-mappings>
<transcode mimetype="video/x-flv" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="oggflac2raw"/>
<transcode mimetype="audio/x-flac" using="oggflac2raw"/>
<transcode mimetype="video/x-divx" using="video-common"/>
</mimetype-profile-mappings>
<profiles>
<profile name="oggflac2raw" enabled="no" type="external">
<mimetype>audio/L16</mimetype>
<accept-url>no</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>no</accept-ogg-theora>
<agent command="ogg123" arguments="-d raw -f %out %in"/>
<buffer size="1048576" chunk-size="131072" fill-size="262144"/>
</profile>
<profile name="vlcmpeg" enabled="no" type="external">
<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25, aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,ch annels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
<buffer size="14400000" chunk-size="512000" fill-size="120000"/>
</profile>
</profiles>
</transcoding>
</config>
```

Why not MediaTomb for me (may be fine for others) -
- I have about 100Gig worth sorted in folders. MediaTomb puts all videos under one 'Video' folder which makes it too difficult to search on the PS3 for what i want to watch. 
- It seems to freeze or lag every few mins when i watch a divX... and i have no idea why. I'm thinking it has something to do with playing a divX on the PS3.

4. Fuppes - This is the one I'm now using
It solves the MediaTomb problems above 
- It keeps my directory structure
- It doesn't freeze up. It seems to work for me when I transcode divX to mpeg2, with no visible loss of quality. If I don't set transcoding on divX files i get the same freeze up's i get on MediaTomb. I've seen forums where people talk about getting similar problems on the PS3 but no solutions... pretty sure the transcoding option did it for me.

There are a few guides to get Fuppes set up, so search away. I used some points from the following link and played with the config file to get it working 

(below)

[http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04]("http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04")

Located in ~/.fuppes/config.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
    <dir>/home/pfajou/Video</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>192.168.1.3</interface>
    <!--empty or 0 = random port-->
    <http_port>8765</http_port>
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
    <!--do NOT remove the "default" device settings-->
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
    <!--It is safe to remove unneeded devices-->
<device name="PS3" enabled="true">
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<user_agent>PLAYSTATION3</user_agent>
<ip>192.168.1.2 </ip>
<enable_dlna>true</enable_dlna>
<transcoding_release_delay>80</transcoding_release_delay>
<file_settings>
<file ext="ogg">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
<transcode enabled="true">
<http_encoding>stream</http_encoding>
</transcode>
</file>
<file ext="mpg">
<ext>mpeg</ext>
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
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
<mime_type>video/divx</mime_type>
<!--<mime_type>video/x-divx</mime_type>-->
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec acodec="wmav2">mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
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
<file ext="vob">
<ext>mpeg</ext>
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
</file>

</file_settings>
</device>    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
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

Let me know if this was a waste of a read or if it actually helped someone.... (my first post).

---

### Post by collinp on 2008-08-02
You should put this in the How Tos section of the forums, as this could help alot of people most likely.

---

### Post by Fajman on 2008-08-02
Thanks Hellow. I reposted in the multimedia section... not so sure about the HowTo's just yet, I'll wait to see what feedback I get if any. A link to the new post is below

[http://ubuntuforums.org/showthread.php?p=5511558#post5511558]("http://ubuntuforums.org/showthread.php?p=5511558#post5511558")

---

### Post by claypole on 2008-08-06
I would highly recommend Twonky, it works out of the box, I regularly stream hi-def video to my PS3 over a 802.11g wifi connection!  And although you have to pay, its very low cost and easier to configure (including a mobile browser).

---

### Post by GumbyX on 2008-08-09
I can't seem to get fuppes to install correctly at all. I got all its dependencies installed, but when I try to start it, I says it can't bind to the IP address I gave it. Weird.

Does anyone else know of any other UPnP software servers other then the ones listed here? I tried FreeNAS and that went horribly. Mediatomb is working, but most videos skip or jump during playback. I do not want to have to install windows on my laptop just to get a UPnP server that "just works". I don't really care that much about thumbnails and stuff like that. What I do care about it being able to watch my movies without any lag over wifi (802.1g).

Sorry if I kinda sound angry, but I just wasted 6+ hours getting my files up on a UPnP share. I tried FreeNAS and I ended up with many, *many* problem (including me accidentally installing it on my Hard drive and losing everything on it). I really want to serve my videos over my network due to the fact that I have switched to a laptop (and my 22" LCD TV is much better then a 15" laptop screen), but I do not want to have to cough up $300+ for a NAS, esp when I have a Thinkpad T60p collecting dust that had more then enough power to run a SMB and UPnP server.

---

### Post by claypole on 2008-08-11
GumbyX, as I said I would recommend TwonkyMedia, it works out of the box.  I have been using it for months with no problems at all :)

---

### Post by Fajman on 2008-08-13
GrumbyX
If you used my config for Fuppes it lists the IP address in it ie
    <interface>192.168.1.3</interface>
So you'll probably need to change it to whatever the IP your running it on.

Claypole
I just checked out the price of Twonky and it's roughly $50... not that cheap. I'd personally fork out a little extra and just replace my ps3 hard drive before I paid that much.

---

### Post by kernel tom on 2008-12-03
> **Fajman said:**
> 
2. UShare - Kept getting 'Unsupported Data' for DivX files and after a lot of searching/playing I finally gave up.


Not to say you should walk away from your working setup, but unless you haven't updated your PS3 recently, you should definitely be able to play DivX files without a problem.  I've done it before on my brothers PS3 off of a thumb drive, so it must work.

Incase your fuppes starts getting buggy switch to uShare, I use it with my 360 and it never has a hiccup... and I mean never

-kt

---

### Post by claypole on 2008-12-04
Would still recommend TwonkyMedia,  I regularly stream divx and HD content to my PS3, has worked without a hitch and barely any configuring since I installed it many many months ago :D

---

