---
title: "Darwin Streaming Server on Ubuntu"
date: 2007-12-27
forum: Outdated Tutorials &amp; Tips
---

### Post by mastermindg on 2007-12-27
**Translated by Google Translator from German to English from source:**

***[http://wiki.ubuntuusers.de/Darwin_Streaming_Server](http://wiki.ubuntuusers.de/Darwin_Streaming_Server)***

Thanks goes out to our German counterparts who took the time to write this guide and to Google for doing a not so bad job of translating, and to myself for light grammar editing :(

[B][SIZE=5]
Darwin Streaming Server[/SIZE][/B]


This article was for the following Ubuntu versions tested:[LIST]
[*]     Feisty Fawn 7.04 Gutsy Fawn 7.04
[*]     Dapper Drake 6.06 (Long Term Support)[/LIST]Darwin Streaming Server is the free version of QuickTime commercial server from Apple. Here are some of it's features:[INDENT][LIST]
[*]Support for open standards: MP3, MPEG-4, H.264/AVC, RTP, RTSP
[*]Open Source pursuant to [Apple Public Source License]("http://www.opensource.apple.com/apsl/")
[*]No term, no user restrictions, etc.
[*]Free[/LIST][/INDENT]In addition, the server through a Web interface, a simple configuration, even from another computer.

[IMG]http://wiki.ubuntuusers.de/Darwin%20Streaming%20Server?action=Thumbnail&target=Screenshot.png&size=250[/IMG]

The Darwin server is suited for on-demand streaming, where the audio / video data is already in coded form as a file and available on demand by a user of each other. In connection with the Live encoder mp4live from mpeg4ip project, but it can also live streaming applications (eg Internet-TV).

The following instructions should assist in the installation and configuration of the Darwin server.

**[SIZE=3]Preparation[/SIZE]**

For the installation of the Darwin Streaming Server, the following two packages need to be installed:

Libstdc + +5 (is already installed by default)
Checkinstall (Dapper) 

To the Darwin streaming server after installation test can also be a good player for playback. This can be either locally on the server, or even better on a second computer to the server network is installed. It is proposed to take this opportunity to install the VLC media player with MPEG-4 support, but there are certainly other players to use.

The Darwin Streaming Server is not as a finished package for Ubuntu or Debian available, but must via Web browser as tar file from [Apple's Web Download]("http://developer.apple.com/opensource/server/streaming/index.html") (registration required). The installation is described here the package [Official Release - DSS 5.5.5 -> Linux -> streaming server]("http://www.opensource.apple.com/projects/streaming/release/DarwinStreamingSrvr5.5.5-Linux.tar.gz") is required, which the Linux binaries. The file is then downloaded and unpacked in the home directory.

**[SIZE=3]Installation[/SIZE]**

After unpacking a terminal is opened and executed the following commands:

cd DarwinStreamingSrvrlinux Linux
sudo addgroup --system qtss
sudo adduser --system --no-create-home --ingroup qtss qtss

[SIZE=2]**Gutsy Fawn**
[/SIZE]
Under Ubuntu 7.04 Dapper Fawn the command is:[INDENT]** sudo. / Install**
[/INDENT]**[SIZE=2]Dapper Drake[/SIZE]**

Under Ubuntu 6.06 Dapper Drake is the call warrant against:[INDENT]** sudo checkinstall - pkgname = darwin-server - pkgversion = 5.5.5. / Install**
[/INDENT]Here is a brief explanation of what the different commands effect:[LIST=1]
[*]Change in the scale when unpacking subdirectory
[*]Creating a user group "qtss" (otherwise the installation doesn't work)
[*]Creating a user "qtss" (as before, but strangely ubuntu not necessary?)
[*]Calling the installation routine[/LIST]After entering the last command line, the installation routine automatically and directed all the necessary directories and so spontaneous. It will also name and password for the administrator of the Darwin server queried. After completing the installation, the Darwin server automatically.

The installation of the server software is closed and the terminal can be closed. 

**[SIZE=3]Directories[/SIZE]**

The following table presents an overview of the most important files and directories of the Darwin server:

/usr/local/sbin/Darwin Streaming Server   ----  Server Software
/usr/local/sbin/streamingadminserver.pl   ----  Web Frontend
/etc/streaming                                           ----  Configuration Dir
/etc/streaming/streamingserver.xml         ----  Configuration File Server
/var/streaming/logs                                   ----  Logs
/usr/local/movies                                       ----  Default directory for video files

Then, the file /etc/streaming/streamingserver.xml must be given write privledges, otherwise no configuration can be saved:[INDENT]**sudo chmod 755 /etc/streaming/streamingserver.xml**
[/INDENT]**[SIZE=3]Configuration and Test[/SIZE]**

The configuration of the Darwin server via a web interface and the following link called:

*http://<Server-IP>:1220*

After signing up as an administrator using the software installation previously elected login information can now be made more settings. When you first call up the site initially queried following information:[LIST]
[*]MP3 Broadcast Password
[*]Secure Administration
[*]Media Folder: /usr/local/movies
[*]Streaming on Port 80 Streaming on Port 80[/LIST]It is important here first is that the path to the video files (Media Folder) correctly specified, all other issues can safely with the "Next" button skipped.In the specified directory /usr/local/movies are already some demo videos, for the first function tests can be used. It is therefore appropriate that this requirement to make changes at any time are on the configuration menu. After defining these four points will eventually configuration mask for the Darwin server, in other settings can be made. Leave the configuration screen by clicking on "Sign Out" (left column bottom).

Now you can test whether the Darwin server works as desired. This is the [VLC media player]("http://wiki.ubuntuusers.de/VLC") opened and the menu "File -> Open Network Stream" stream following address:

*rtsp://<Server-IP>/sample_100kbit.mp4*

 If everything is installed correctly, you should now be a player in the supplied sample videos will be shown. Congratulations! :)

**[SIZE=3]Start Server[/SIZE]**

During power of the computer is not of the Darwin server automatically, but servers and web interface must either in a terminal on the following two lines of command

sudo /usr/local/sbin/DarwinStreamingServer
/usr/local/sbin/streamingadminserver.pl

Or by corresponding entries in the Start menu manually invoked. As servers and web interface can also start automatically, is contributing startup. In addition, there are init scripts for the Darwin server and the admin interface.

**[SIZE=3]MPEG-4 video streaming[/SIZE]**

In order to use the server as streaming video-on-demand server videos must be in MPEG-4 format (file extension .mp4). Using the under video editing or DVD rippin tools. Videos in Quicktime format (. Mov) could also be used, but are probably less interesting.

However, before an MPEG-4 video with the Darwin server can be streamed must have known in advance hint tracks in the data stream added. They are required to fast forward and rewind the video. For inserting the hint tracks use Tool MP4Box in the package:[LIST]
[*]**gpac (multiverse, [2])**[/LIST]The syntax for the command call for inserting the hint tracks reads:

*MP4Box -hint dateiname.mp4*

With the option-unhint can be inserted information may also be removed.

Alternatively, can the hint tracks with the tool mp4creator from the [MPEG4IP project]("http://mpeg4ip.sourceforge.net/").

After inserting the hint tracks, the video file only in the video directory of the Darwin server will be copied or moved, immediately thereafter, the video for the call may be accessed via the web interface also includes a playlist can be created.

**[SIZE=3]MP3 audio streaming[/SIZE]**

With the Darwin server can not only MPEG-4 videos, but also MP3 audio files stream. As you can create MP3 files, for example, in the contribution rip CDs. To existing MP3 files on stream, must first play lists, which, thanks to the existing web interfaces but made relatively quickly. (Guide in German, not included)

The MP3 player, the create play lists at the address:[INDENT]***http://<Server-IP>:8000/Mountpunkt***[/INDENT]

---

### Post by amoore on 2007-12-28
GREAT Tutorial!!! I have been wondering how to set up DSS/QTSS for a very long time!!! This also tutorial also works for 7.10. Gpac works like a charm, just use it to convert your mp4s for hint!:KS

---

### Post by mikko.ohtamaa on 2008-04-23
Command

```
/usr/local/sbin/streamingadminserver.pl 

```
must be run as root too

```
sudo /usr/local/sbin/streamingadminserver.pl 
```

or otherwise you'll get an error

```
Couldn't find the en language messages file! at /usr/local/sbin/streamingadminserver.pl line 2167.
```

Killing the server

```
root@mansikki:~# ps -Af | grep -i stream
root      5857     1  0 11:28 ?        00:00:00 /usr/local/sbin/DarwinStreamingServer
qtss      5858  5857  0 11:28 ?        00:00:00 /usr/local/sbin/DarwinStreamingServer
qtss      6061     1  0 11:32 ?        00:00:00 /usr/bin/perl /usr/local/sbin/streamingadminserver.pl
root      6233  6205  0 11:35 pts/9    00:00:00 grep -i stream

killall DarwinStreamingServer 
kill 6061
```

---

### Post by www.rzr.online.fr on 2008-07-18
Hi,
I just build latest version (6.0.3)  * , It works on mp4 files, but are you able to start the playlist feature ?

It fails to start :

  Error 
  An error occurred while starting or stopping your playlist.


* get the dss package at [http://rzr.online.fr/q/apt](http://rzr.online.fr/q/apt)

---

### Post by skliarie on 2008-10-26
I created necessary files (find attached) to produce debian package of the Darwin Streaming Server using debuild program. The rules are for building the DSS for amd64, but should be trivial to adopt for i386 arch. The checkinstall approach was not working properly, as the original Install script is too interactive for that.

The files should be unpacked inside of the DarwinStreamingSrvr6.0.3-Source directory, that is automatically created by dss.sh script from following URL:
[http://dss.macosforge.org/trac/ticket/6]("http://dss.macosforge.org/trac/ticket/6")

---

### Post by www.rzr.online.fr on 2008-10-28
Hi,

I build it for amd64 on hardy too :
[http://rzr.online.fr/ubuntu/pool/main/d/dss/](http://rzr.online.fr/ubuntu/pool/main/d/dss/)

But maybe we can merge out works since it's needed to be patched ...

I plan also to fill a bug on debian side

-- 
[http://rzr.online.fr/q/rtp](http://rzr.online.fr/q/rtp)

---

### Post by bishop942 on 2008-11-10
Can you help? the amd 64 package installed well but the password is not the same as the one I set in using the source. or can you tell me where the password is stored so that I can change it, TIA

---

### Post by skliarie on 2008-11-10
There is file /etc/streaming/qtusers

to manage the file use qtpasswd tool as follows:

/usr/bin/qtpasswd -c -p password administrator

---

### Post by bishop942 on 2008-11-11
Thanks for the reply, I did find that. When I tried that it created a new password file and still wouldn't allow me to log in with the newly created u/p, the streamingadmin page. I even killed the two servers "Darwinstream and streamingadmin" any other help would be appreciated.

---

### Post by bishop942 on 2008-11-11
I found the answer disabling all authentication.
 
[http://www.vague.tv/howtos/broadcast/servers/darwin/howto_setup_darwin_streaming_server_on_linux.html]("http://www.vague.tv/howtos/broadcast/servers/darwin/howto_setup_darwin_streaming_server_on_linux.html")

---

### Post by jaysazua on 2008-12-04
> **mastermindg said:**
> 
**[SIZE=3]Start Server[/SIZE]**

During power of the computer is not of the Darwin server automatically, but servers and web interface must either in a terminal on the following two lines of command

sudo /usr/local/sbin/DarwinStreamingServer
/usr/local/sbin/streamingadminserver.pl

Or by corresponding entries in the Start menu manually invoked. As servers and web interface can also start automatically, is contributing startup. In addition, there are init scripts for the Darwin server and the admin interface.



I downloaded and followed the instructions in the tutorial but I got stuck in the part where I can view the server on the *ipaddress:1220* part.  I'm using Ubuntu JeOS 8.04 and I think it has something to do with that... I'm not sure though... I've tried to use the above instructions in starting the server but there's no file there that says DarwinStreamingServer or the other one.  All it says is:

root@ubuntu-jeos:~# ls /usr/local/bin/
createuserstreamingdir    PlaylistBroadcaster  StreamingLoadTool
MP3Broadcaster        qtpasswd

Any ideas?

Edit:

I got it to work by using:

useradd -g qtss qtss

thanks anyways!

---

### Post by www.rzr.online.fr on 2008-12-12
Let me link this post to : [http://bugs.debian.org/508353](http://bugs.debian.org/508353)
-- 
[http://rzr.online.fr/q/rtp](http://rzr.online.fr/q/rtp)

---

### Post by metaphorz on 2008-12-24
With the Darwin Server,
can one insert dynamically created audio content and
send it to the streamed mp3 file? This would be useful
in broadcasting one's voice (from a mic) or even
inserting output from a text-to-speech translator
into the stream. Thanks!

---

### Post by skliarie on 2008-12-25
Yes, you can use the Darwin as a reflector, in which case it can accept broadcast of rtp stream (produced by vlc) and rebroadcast it as an rtsp stream. For that vlc can be run as follows (for broadcasting both video and audio):

/usr/local/bin/vlc $VideoFile -Irc --sout '#transcode{vcodec="H263",width='$width',height='$height',vb="'$vbitrate'",fps="'$fps'",acodec="samr",ab="'$abitrate'",samplerate="8000",channels="1"}:rtp{dst="'$LocalIP'",port-audio="22002",port-video="22000",ttl="6",sdp="file:///usr/local/movies/vlc.sdp"}'

---

### Post by arstanj on 2009-06-12
Here's working tutorial getting Darwin Streaming Server up and running on hardy - [http://www.jusupov.com/2009/06/13/how-to-install-darwin-streaming-server-on-ubuntu-hardy/]("http://www.jusupov.com/2009/06/13/how-to-install-darwin-streaming-server-on-ubuntu-hardy/")

---

### Post by ruman on 2009-06-26
I simplified the start/stop script to make it work for DSS 6.0.3 on Ubuntu 9.04 (no need to start DSS and admin separatly as pl script is doing it).

```
#!/bin/sh
#
# chkconfig: 35 92 12
# description: Quicktime Streaming Media Server
#
# init script to start up the quicktime (Darwin) streaming server

case "$1" in
        start)
        if test -r /var/lock/dssd
        then
                echo "Lockfile /var/lock/dssd exists. Server not started."
                failure
        else
                echo "Starting Darwin Streaming Server: "
                /usr/local/sbin/streamingadminserver.pl
                touch /var/lock/dssd
                echo "Darwin Streaming Server started..."
        fi
        ;;

        stop)
        echo "Stopping Darwin Streaming Server: "
        [ -f /var/lock/dssd ] || exit 0
        echo "stopping..."
        killall streamingadminserver.pl
        rm -f /var/lock/dssd
        echo
        ;;

        restart)
        $0 stop
        sleep 1
        $0 start
        ;;

        *)
        echo "Usage: $0 [start|stop|restart]"
        exit 1
esac
exit 0
```

---

### Post by skubix on 2009-08-23
Hi,

I have a problem with DSS, I'm unable to stream over internet but i have no problem to stream into a my local lan.

 I have installed DSS versions 5.5.5 and 6.0.3 on a Ubuntu 9.04 Server and
 Desktop editions. I try combinatiosn over 4 diferent servers.

 The streaming works's fine with this clients on a local lan:

 Quicktime ( Windows )
 Mplayer ( Linux 1.0rc2-4.3.3 )
 Vlc ( Linux 0.9.9a)
 MP4Player ( Linux 1.6 )

 But DSS only works fine with VLC client over internet ( with artifacts),
 all other clients fail.

 Is not a ports problem.


 == Mplayer log when fail. ==

 ---------------------

 mplayer rtsp://[94.75.232.225/sample_h264_100kbit.mp4]("http://94.75.232.225/sample_h264_100kbit.mp4")
 MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
 CPU: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz (Family: 6, Model:
 23, Stepping: 6)
 CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
 Compiled with runtime CPU detection.
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote
 control.

 Playing rtsp://[94.75.232.225/sample_h264_100kbit.mp4]("http://94.75.232.225/sample_h264_100kbit.mp4").
 Resolving 94.75.232.225 for AF_INET6...
 Couldn't resolve name for AF_INET6: 94.75.232.225
 Connecting to server 94.75.232.225[94.75.232.225]: 554...
 A single media stream only is supported atm.
 rtsp_session: unsupported RTSP server. Server type is 'DSS/6.0.3
 (Build/526.3; Platform/Linux; Release/Darwin Streaming Server;
 State/Development; )'.
 STREAM_LIVE555, URL: rtsp://[94.75.232.225/sample_h264_100kbit.mp4]("http://94.75.232.225/sample_h264_100kbit.mp4")
 Stream not seekable!
  file format detected.
 Initiated "video/H264" RTP subsession on port 50260
 Initiated "audio/MPEG4-GENERIC" RTP subsession on port 34514
 demux_rtp: Failed to guess the video frame rate
 VIDEO:  [H264]  0x0  0bpp  0.000 fps    0.0 kbps ( 0.0 kbyte/s)
 FPS not specified in the header or invalid, use the -fps option.
 ==========================================================================
 Forced audio codec: mad
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 FAAD: compressed input bitrate missing, assuming 128kbit/s!
 AUDIO: 16000 Hz, 2 ch, s16le, 128.0 kbit/25.00% (ratio: 16000->64000)
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio)
 decoder)
 ==========================================================================
 AO: [pulse] 16000Hz 2ch s16le (2 bytes per sample)
 Video: no video
 Starting playback...
 A:   0.0 (unknown) of 70.0 (01:10.0) ??,?%

 Exiting... (End of file)

 ------------------------


 == Mp4player log when fail ==


 16:59:05.320-plugin-6: Adding video plugin rawv
 /usr/local/lib/mp4player_plugin/raw_video_plugin.so
 16:59:05.321-plugin-6: Adding RTP plugin enc-mpeg4-generic:audio
 /usr/local/lib/mp4player_plugin/isma_enc_rtp_plugin.so
 16:59:05.321-plugin-6: Adding video plugin xvid-10
 /usr/local/lib/mp4player_plugin/xvid10_plugin.so
 16:59:05.321-plugin-6: Adding audio plugin rawa
 /usr/local/lib/mp4player_plugin/raw_audio_plugin.so
 16:59:05.322-plugin-6: Adding RTP plugin mpeg4-generic
 /usr/local/lib/mp4player_plugin/isma_rtp_plugin.so
 16:59:05.322-plugin-6: Adding RTP plugin h264
 /usr/local/lib/mp4player_plugin/h264_rtp_plugin.so
 16:59:05.322-plugin-6: Adding audio plugin a52dec
 /usr/local/lib/mp4player_plugin/a52_audio_plugin.so
 16:59:05.323-plugin-6: Adding RTP plugin isma-href
 /usr/local/lib/mp4player_plugin/href_rtp_plugin.so
 16:59:05.323-plugin-6: Adding audio plugin g711
 /usr/local/lib/mp4player_plugin/g711_audio_plugin.so
 16:59:05.323-plugin-6: Adding RTP plugin rfc3267
 /usr/local/lib/mp4player_plugin/rfc3267_plugin.so
 16:59:05.324-plugin-6: Adding audio plugin celp
 /usr/local/lib/mp4player_plugin/celp_plugin.so
 16:59:05.326-plugin-6: Adding audio plugin mp3
 /usr/local/lib/mp4player_plugin/mp3_plugin.so
 16:59:05.331-plugin-6: Adding video plugin MPEG4 ISO
 /usr/local/lib/mp4player_plugin/mpeg4_iso_plugin.so
 16:59:05.335-plugin-6: Adding audio plugin ffmpeg audio
 /usr/local/lib/mp4player_plugin/ffmpeg_audio_plugin.so
 16:59:05.335-plugin-6: Adding audio plugin aac
 /usr/local/lib/mp4player_plugin/aac_plugin.so
 16:59:05.336-plugin-6: Adding video plugin ffmpeg
 /usr/local/lib/mp4player_plugin/ffmpeg_video_plugin.so
 16:59:05.336-plugin-6: Adding video plugin h261
 /usr/local/lib/mp4player_plugin/h261_plugin.so
 16:59:05.337-plugin-6: Adding RTP plugin enc-mpeg4-generic:video
 /usr/local/lib/mp4player_plugin/isma_enc_video_rtp_plugin.so
 16:59:05.337-plugin-6: Adding RTP plugin rfc-2429
 /usr/local/lib/mp4player_plugin/rfc2429_rtp_plugin.so
 16:59:05.337-plugin-6: Adding RTP plugin h261
 /usr/local/lib/mp4player_plugin/h261_rtp_plugin.so
 16:59:05.337-plugin-6: Adding text plugin plaintext
 /usr/local/lib/mp4player_plugin/plaintext_text_plugin.so
 16:59:05.338-plugin-6: Adding text plugin href
 /usr/local/lib/mp4player_plugin/href_text_plugin.so
 16:59:05.338-plugin-6: Adding audio plugin wav
 /usr/local/lib/mp4player_plugin/wav_plugin.so
 16:59:05.338-plugin-6: Adding RTP plugin mpeg4-latm
 /usr/local/lib/mp4player_plugin/latm_rtp_plugin.so
 16:59:05.459-videosync-6: Max Window resolution 1680x1050
 16:59:05.459-videosync-7: Setting video mode 176 144 1 1
 16:59:05.642-my_player-7: Creating streaming
 rtsp://[94.75.232.225/sample_h264_100kbit.mp4]("http://94.75.232.225/sample_h264_100kbit.mp4")
 16:59:05.814-my_player-7: setting control url to
 rtsp://[94.75.232.225/sample_h264_100kbit.mp4/]("http://94.75.232.225/sample_h264_100kbit.mp4/")
 16:59:05.869-ffmpeg-7: codec value 0x7f42eb726420
 16:59:05.869-plugin-7: Found matching video plugin ffmpeg
 16:59:05.870-plugin-7: Found matching audio plugin aac
 16:59:05.870-videosync-7: persistence is 0x2373790
 16:59:05.870-my_player-7: First port is 1024
 16:59:05.870-my_player-7: Ip ports are 1024 1025
 16:59:05.957-media-6: Transport returned is
 RTP/AVP;unicast;source=94.75.232.225;client_port=1024-1025;server_port=6970-6971;ssrc=11C9A3CA
 16:59:05.957-media-6: setting default source address from rtsp
 94.75.232.225
 16:59:06.021-my_player-7: First port is 1026
 16:59:06.021-my_player-7: Ip ports are 1026 1027
 16:59:06.107-media-6: Transport returned is
 RTP/AVP;unicast;source=94.75.232.225;client_port=1026-1027;server_port=6970-6971;ssrc=4BA978DF
 16:59:06.107-media-6: setting default source address from rtsp
 94.75.232.225
 16:59:06.204-my_player-7: rtp info is
 'url=rtsp://[94.75.232.225/sample_h264_100kbit.mp4/trackID=3;seq=53704;rtptime=739307306,url=rtsp://94.75.232.225/sample_h264_100kbit.mp4/trackID=4;seq=19711;rtptime=977869175]("http://94.75.232.225/sample_h264_100kbit.mp4/trackID=3;seq=53704;rtptime=739307306,url=rtsp://94.75.232.225/sample_h264_100kbit.mp4/trackID=4;seq=19711;rtptime=977869175")'
 16:59:36.206-avsync-2: No media has been initialized or received
 16:59:36.207-avsync-2: Fatal error while initializing hardware
 16:59:36.207-avsync-6: sync changed state Init to Done
 16:59:36.208-avsync-6: sync changed state Done to Exit
 16:59:36.293-media-7: closing down media 0
 16:59:36.332-media-5: Video decoder skipped 0 frames
 16:59:36.332-media-7: closing down media 1
 16:59:36.829-video-5: video Sync Stats:
 16:59:36.829-video-5: Displayed-behind frames 0
 16:59:36.829-video-5: Total frames displayed 0
 16:59:36.829-video-5: Max behind time 0
 16:59:36.829-video-5: Skipped rendering 0
 16:59:36.829-video-5: Filled frames 0
 16:59:36.829-avsync-7: grabbed persist
 16:59:36.829-audiobuf-6: total samples played: 0
 16:59:36.829-audiobuf-6: sync samples added  : 0
 16:59:36.829-audiobuf-6: sync samples removed: 0

---

### Post by slhawk98 on 2009-09-20
moved

---

### Post by DAFORZE on 2010-05-12
I can't get this to work in ubuntu 9.10 server.
At the end of the installation; after the administrator username and password is entered, 
I get the message: 

./Install: line 408: /usr/local/bin/qtpasswd: No such file or directory                                                                                                            
./Install: line 416: /usr/local/bin/qtpasswd: No such file or directory 

also my usr/local/sbin only contains a map called StreamingServerModules with nothing in it..

The /etc/streaming/streamingserver.xml and the binarys to start the server are also nowhere to be found...:'(

---

### Post by DAFORZE on 2010-05-14
Okay so i tried it again, but this time on ubuntu desktop 9.10 and desktop 10.04.
But i get the exact same errors as i mentioned above??
I don't understand what am I doing wrong....? anyone?

---

### Post by mysoogal on 2010-06-04
how to install and use DSS? on ubuntu 10.04 ? I'm sick from reading about old tutorials :confused:

---

### Post by DataJohan on 2010-06-06
> **mysoogal said:**
> how to install and use DSS? on ubuntu 10.04 ? I'm sick from reading about old tutorials :confused:

Hi there

+1 for this one!

By The Way, it is commonly known that AKAMAI is using Darwin to provide the mobile version of Youtube.

Does anyone know what version they use and under what OS (and version)?

If AKAMAI have "In house modded" DSS, do they then have to offer modifications or do they get away with it cause of the "SaaS loophoole"?

Just some thoughts because knowledge of what they manageded to deploy so largely would be interesting even in smaller scale.:popcorn:

/Johan

---

### Post by blackjackjester on 2010-08-13
> **mysoogal said:**
> how to install and use DSS? on ubuntu 10.04 ? I'm sick from reading about old tutorials :confused:

I as well am having this problem.  Ubuntu 10.04

Couldn't find the en language message file!

I've tried everything from DSS 5.5.5 to 6.0.3 special builds.  The ones that work.

Has anyone succeeded?

---

### Post by pajarraco on 2010-11-22
Hi I use this script

#!/bin/bash

sudo apt-get install build-essential wget
sudo addgroup --system qtss
sudo adduser --system --no-create-home --ingroup qtss qtss

wget [http://static.macosforge.org/dss/downloads/DarwinStreamingSrvr6.0.3-Source.tar](http://static.macosforge.org/dss/downloads/DarwinStreamingSrvr6.0.3-Source.tar)
tar -xvf DarwinStreamingSrvr6.0.3-Source.tar
mv DarwinStreamingSrvr6.0.3-Source DarwinStreamingSrvr6.0.3-Source.orig
wget [http://dss.macosforge.org/trac/raw-attachment/ticket/6/dss-6.0.3.patch](http://dss.macosforge.org/trac/raw-attachment/ticket/6/dss-6.0.3.patch)
patch -p0 < dss-6.0.3.patch
mv DarwinStreamingSrvr6.0.3-Source.orig DarwinStreamingSrvr6.0.3-Source
wget [http://dss.macosforge.org/trac/raw-attachment/ticket/6/dss-hh-20080728-1.patch](http://dss.macosforge.org/trac/raw-attachment/ticket/6/dss-hh-20080728-1.patch)
patch -p0 < dss-hh-20080728-1.patch
#need to answer n then y
cd DarwinStreamingSrvr6.0.3-Source
mv Install Install.orig
wget [http://dss.macosforge.org/trac/raw-attachment/ticket/6/Install](http://dss.macosforge.org/trac/raw-attachment/ticket/6/Install)
chmod +x Install
./Buildit
sudo ./Install

---

