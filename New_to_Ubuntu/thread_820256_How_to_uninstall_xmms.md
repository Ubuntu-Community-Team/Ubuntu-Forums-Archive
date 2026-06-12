---
title: "How to uninstall xmms?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by plucesiar on 2008-06-06
After installing xmms and flac plugin in Ubuntu Hardy (btw, is it necessary to remove flac as well?) from this site:
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)
and discovering that it interferes with flash audio in firefox, i want to remove it with the command:

```
sudo apt-get remove --purge xmms
```

but the terminal's returning this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 120 not upgraded.

```

What should I input instead then?

Thanks!

---

### Post by Trail on 2008-06-06
I haven't used xmms myself, but try looking at the output of
```

aptitude search xmms

```
(no sudo needed by the way).
Any lines beginning with "i" are installed packages. Any lines with "c" are packages previously installed and now removed, but the configuration still exists (ie, not purged). Lines with "p" are not installed.

If you find similarly named, installed packages, try removing those.

EDIT: Maybe xmms2?

---

### Post by plucesiar on 2008-06-06
Okay I ran a aptitude search xmms and it returned the following:

```
p   gkrellxmms2                     - GKrellM plugin to control xmms2           
v   gxmms-xmms                      -                                           
p   gxmms2                          - xmms2 client for the GNOME desktop        
p   libaudio-xmmsclient-perl        - XMMS2 - perl client library               
p   libxmmsclient++-dev             - XMMS2 - client library for c++ - developme
p   libxmmsclient++-glib-dev        - XMMS2 - glib client library for c++ - deve
p   libxmmsclient++-glib1           - XMMS2 - glib client library for c++       
p   libxmmsclient++1                - XMMS2 - client library for c++            
p   libxmmsclient-dev               - XMMS2 - client library devel files        
p   libxmmsclient-glib-dev          - XMMS2 - glib client library - development 
p   libxmmsclient-glib1             - XMMS2 - glib client library               
p   libxmmsclient-ruby              - XMMS2 - Ruby client library               
p   libxmmsclient-ruby1.8           - XMMS2 - Ruby bindings                     
p   libxmmsclient2                  - XMMS2 - client library                    
p   logjam-xmms                     - Command-line XMMS song title retriever    
p   playground-plugin-xmms          - XMMS control plugin for playground GNOME a
p   python-xmmsclient               - XMMS2 - Python bindings                   
p   rep-xmms                        - rep language bindings for XMMS            
p   sawfish-xmms                    - sawfish bindings for XMMS                 
p   smpeg-xmms                      - SDL MPEG Player Library - XMMS plugin     
p   xmms-dbmix                      - XMMS output interface to the DBMix audio s
p   xmms-festalon                   - XMMS Input plugin for playing NSF music fi
p   xmms-gbs                        - Gameboy sound player plugin for XMMS      
p   xmms-itouch                     - iTouch keyboard control plugin for XMMS   
p   xmms-kjofol                     - XMMS remote that uses K-Jofol's skins     
p   xmms-kjofol-skins               - Skins for the xmms-kjofol package         
p   xmms-midi                       - MIDI plugin for XMMS                      
p   xmms-oggre                      - ogg disk output plugin for XMMS           
p   xmms-openspc                    - SPC file player plugin for XMMS           
p   xmms-osd-plugin                 - XMMS plugin using xosd                    
p   xmms-volnorm                    - XMMS plugin that gives all songs the same 
p   xmms-wma                        - WMA input plugin for XMMS                 
p   xmms-xmmplayer                  - XMMS plugin that uses MPlayer to play vide
p   xmms2                           - Client/server based media player system   
p   xmms2-client-avahi              - XMMS2 - avahi client                      
p   xmms2-client-cli                - XMMS2 - cli client                        
p   xmms2-client-medialib-updater   - XMMS2 - medialib-updater client           
p   xmms2-core                      - XMMS2 - core package                      
p   xmms2-dev                       - XMMS2 - plugin development files          
p   xmms2-et                        - XMMS2 - phone home package                
p   xmms2-plugin-all                - XMMS2 - all plugins                       
p   xmms2-plugin-alsa               - XMMS2 - ALSA output                       
p   xmms2-plugin-ao                 - XMMS2 - libao output plugin               
p   xmms2-plugin-asx                - XMMS2 - ASX playlist plugin               
p   xmms2-plugin-avcodec            - XMMS2 - avcodec decoder                   
p   xmms2-plugin-avformat           - XMMS2 - avformat demuxer                  
p   xmms2-plugin-cdda               - XMMS2 - CDDA plugin                       
p   xmms2-plugin-cue                - XMMS2 - CUE playlist plugin               
p   xmms2-plugin-curl               - XMMS2 - curl transport for HTTP           
p   xmms2-plugin-daap               - XMMS2 - daap plugin                       
p   xmms2-plugin-flac               - XMMS2 - flac decoder                      
p   xmms2-plugin-gnomevfs           - XMMS2 - GnomeVFS transport                
p   xmms2-plugin-ices               - XMMS2 - ogg streaming output              
p   xmms2-plugin-icymetaint         - XMMS2 - shoutcast metadata plugin         
p   xmms2-plugin-id3v2              - XMMS2 - ID3v2 plugin                      
p   xmms2-plugin-jack               - XMMS2 - JACK output                       
p   xmms2-plugin-lastfm             - XMMS2 - Last.FM plugin                    
p   xmms2-plugin-m3u                - XMMS2 - M3U playlist plugin               
p   xmms2-plugin-mad                - XMMS2 - libmad based mp3 decoder          
p   xmms2-plugin-mms                - XMMS2 - MMS transport                     
p   xmms2-plugin-modplug            - XMMS2 - modplug decoder                   
p   xmms2-plugin-mp4                - XMMS2 - MPEG-4 plugin                     
p   xmms2-plugin-musepack           - XMMS2 - mpc decoder                       
p   xmms2-plugin-ofa                - XMMS2 - OFA plugin                        
p   xmms2-plugin-oss                - XMMS2 - OSS output                        
p   xmms2-plugin-pls                - XMMS2 - PLS playlist plugin               
p   xmms2-plugin-rss                - XMMS2 - RSS podcast plugin                
p   xmms2-plugin-sid                - XMMS2 - libsidplay2 based decoder         
p   xmms2-plugin-smb                - XMMS2 - Samba transport                   
p   xmms2-plugin-vocoder            - XMMS2 - vocoder plugin                    
p   xmms2-plugin-vorbis             - XMMS2 - vorbis decoder                    
p   xmms2-plugin-wma                - XMMS2 - wma decoder                       
p   xmms2-plugin-xml                - XMMS2 - XML plugin                        
p   xmms2-plugin-xspf               - XMMS2 - XSPF playist plugin               
p   xmms2-scrobbler                 - Audioscrobbler/Last.FM client for xmms2   
p   xmms2tray                       - systray integration for XMMS2             
p   xmp-xmms                        - An experimental XMP plugin for XMMS      

```

Hmm I'm still kind of stuck because I can't find any install packages.

Also, I forgot to include the site which i got the commands from (it's been editted in the first post now), which might help. I'll just paste the commands here:

```

First Step:
We need to download the required packages to compile XMMS
# sudo apt-get install autotools-dev automake1.9 libtool gettext libasound2-dev libaudiofile-dev \
libgl1-mesa-dev libglib1.2-dev libgtk1.2-dev libesd0-dev libice-dev libmikmod2-dev libogg-dev \
libsm-dev libvorbis-dev libxxf86vm-dev libxml-dev libssl-dev build-essential make

Depending on your internet connection and your machine this may take some minutes.

Second Step:
Prepare the XMMS for compiling
Create a directory in your HOME directory:
# mkdir ~/build
Change the working directory to it:
# cd ~/build
Download XMMS sources:
# wget [http://xmms.org/files/1.2.x/xmms-1.2.11.tar.gz](http://xmms.org/files/1.2.x/xmms-1.2.11.tar.gz)
Unpack it:
# tar xvf xmms-1.2.11.tar.gz
Change the working directory to the source directory:
# cd xmms-1.2.11/
Third Step:
Compiling it:
This generates the necessary files, and checks your system:
# ./configure --prefix=/usr
The actually compiling
# make
Fourth Step:
Install it:
# sudo make install
After install we no longer need the source directory:
# cd
# rm -rf ~/build
```

---

### Post by Perfect Storm on 2008-06-06
you stil have the files? If so;

```
cd <into directory>
sudo make uninstall
```

You can't use synaptic, add/remove apt-get/aptitude/dpkg on source installation.

---

### Post by Trail on 2008-06-06
Ah, so you didn't use a package manager but you compiled it on your own. You can try this:

```

# mkdir ~/build
Change the working directory to it:
# cd ~/build
Download XMMS sources:
# wget http://xmms.org/files/1.2.x/xmms-1.2.11.tar.gz
Unpack it:
# tar xvf xmms-1.2.11.tar.gz
Change the working directory to the source directory:
# cd xmms-1.2.11/
Third Step:
Compiling it:
This generates the necessary files, and checks your system:
# ./configure --prefix=/usr
The actually compiling
# make
Fourth Step:
Install it:
# sudo make install

after installing, uninstall:
#sudo make uninstall

After uninstall we no longer need the source directory:
# cd
# rm -rf ~/build

```

If you notice, it does everything that the previous instructions do, which one change. It compiles and installs everything, then uninstalls it. That is because the previous instructions deleted the folder in which the compiled files were, which also deleted the instructions on how to uninstall. So if you re-create them, and the makefile supports it, uninstalling should work.

Give this a try.

---

### Post by plucesiar on 2008-06-06
It worked!  Thanks so much!

---

