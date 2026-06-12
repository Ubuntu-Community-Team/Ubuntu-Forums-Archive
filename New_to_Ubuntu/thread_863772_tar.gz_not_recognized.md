---
title: "tar.gz not recognized"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by no-1-uno on 2008-07-18
Sorry to ask but I have been unable to find info in this issue. I have downloaded a flash player to try and get yahoo pool work. I am running hardy and am able to unrar but when I try to open the tar.gz the installer is unknown type and a box opens that is titled open files which is just blank with nothing in the boxes.

There are a couple of other tar.gz I have tried to open and it is the same thing, when I click on the installer it does not know what to do with it.

the file is 
```

install_flash_player_9_linux.tar.gz
```

I found this through one of the other threads to get the yahoo pool to work. Any help would be great as this is the end of week two I think in Linux land.

---

### Post by t0p on 2008-07-18
I'm puzzled as to why Archive Manager can't open that archive for you.  But I feel I ought to point out that you can get flash player through Synaptic, which will be a much simpler install.

---

### Post by SunnyRabbiera on 2008-07-18
Eh dont install flashplayer that way, use the repositories.
If you are unsure how to use repositories, use this guide to start off with:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by sdowney717 on 2008-07-18
file-roller is the name of the archive manager.
I wonder if you open synaptic package manager
search for file-roller
do a complete uninstall and reinstall
Perhaps the file associations will be restored

---

### Post by no-1-uno on 2008-07-18
I have looked at the java and the flash packages in the SM but have not a clue which one to use.

---

### Post by tramir on 2008-07-18
You need to install flashplugin-nonfree.

---

### Post by sharks on 2008-07-18
install flashplugin-nonfree or install ubuntu-restricted-extras. it will install codecs also.

---

### Post by no-1-uno on 2008-07-18
Did that the pool works now, my son will be happy.

What about a Java pack?

I removed and reinstalled the file roller but still shows the installer as unknown. I am not going to use this one but would like to be able to use tar.gz in the future if need be.

Other dumb question while I have your assistance. I have read about the security and no need for virus software or spyware progs. The problem I have is that I like to watch and download movies and programs off the net. Is there anyway to check them? In the windows world I used Avast pro and it would even catch problems when downloading compressed files. I want to make sure I do not get a bug this way. I also want to know if there is a spyware tool and if we need to use one.

ThanX

---

### Post by sdowney717 on 2008-07-19
Avast has a linux version
Linux has clam antivirus
Unless you use WINE, you wont have any trouble. Although you could spread the virus to others.

---

### Post by sdowney717 on 2008-07-19
open up this file

 gksudo gedit /usr/share/applications/defaults.list

```

[Default Applications]
application/csv=ooo-calc.desktop
application/excel=ooo-calc.desktop
application/msexcel=ooo-calc.desktop
application/msword=ooo-writer.desktop
application/ogg=totem.desktop
application/pdf=evince.desktop
application/postscript=evince.desktop
application/rtf=ooo-writer.desktop
application/tab-separated-values=ooo-calc.desktop
application/vnd.lotus-1-2-3=ooo-calc.desktop
application/vnd.ms-excel=ooo-calc.desktop
application/vnd.ms-word=ooo-writer.desktop
application/vnd.rn-realmedia=totem.desktop
application/vnd.sun.xml.calc=ooo-calc.desktop
application/vnd.sun.xml.calc.template=ooo-calc.desktop
application/vnd.sun.xml.draw=ooo-draw.desktop
application/vnd.sun.xml.draw.template=ooo-draw.desktop
application/vnd.sun.xml.math=ooo-math.desktop
application/vnd.sun.xml.writer=ooo-writer.desktop
application/vnd.sun.xml.writer.template=ooo-writer.desktop
application/vnd.sun.xml.writer.global=ooo-writer.desktop
application/vnd.oasis.opendocument.formula=ooo-math.desktop
application/vnd.oasis.opendocument.graphics=ooo-draw.desktop
application/vnd.oasis.opendocument.graphics-template=ooo-draw.desktop
application/vnd.oasis.opendocument.presentation=ooo-impress.desktop
application/vnd.oasis.opendocument.presentation-template=ooo-impress.desktop
application/vnd.oasis.opendocument.spreadsheet=ooo-calc.desktop
application/vnd.oasis.opendocument.spreadsheet-template=ooo-calc.desktop
application/vnd.oasis.opendocument.text=ooo-writer.desktop
application/vnd.oasis.opendocument.text-template=ooo-writer.desktop
application/vnd.oasis.opendocument.text-web=ooo-writer.desktop
application/vnd.oasis.opendocument.text-master=ooo-writer.desktop
application/vnd.sun.xml.impress=ooo-impress.desktop
application/vnd.sun.xml.impress.template=ooo-impress.desktop
application/vnd.stardivision.calc=ooo-calc.desktop
application/vnd.stardivision.draw=ooo-draw.desktop
application/vnd.stardivision.impress=ooo-impress.desktop
application/vnd.stardivision.math=ooo-math.desktop
application/vnd.stardivision.writer=ooo-writer.desktop
application/mspowerpoint=ooo-impress.desktop
application/vnd.ms-powerpoint=ooo-impress.desktop
application/vnd.wordperfect=ooo-writer.desktop
application/wordperfect=ooo-writer.desktop
application/x-123=ooo-calc.desktop
application/x-abiword=abiword.desktop
application/x-applix-spreadsheet=ooo-calc.desktop
application/x-ar=file-roller.desktop
application/x-arj=file-roller.desktop
application/x-bzip-compressed-tar=file-roller.desktop
application/x-bzip=file-roller.desktop
application/x-cd-image=nautilus-cd-burner-open-iso.desktop
application/x-compressed-tar=file-roller.desktop
application/x-compress=file-roller.desktop
application/x-deb=gdebi.desktop
application/x-debian-package=gdebi.desktop
application/x-dos_ms_excel=ooo-calc.desktop
application/x-ear=file-roller.desktop
application/x-excel=ooo-calc.desktop
application/x-extension-m4a=totem.desktop
application/x-extension-mp4=totem.desktop
application/x-flac=totem.desktop
application/x-glade=glade-2.desktop
application/x-gnumeric=gnumeric.desktop
application/x-gtar=file-roller.desktop
application/x-gzip=file-roller.desktop
application/x-gzpostscript=evince.desktop
application/xhtml+xml=firefox.desktop
application/x-jar=file-roller.desktop
application/x-java-archive=file-roller.desktop
application/x-lha=file-roller.desktop
application/x-lhz=file-roller.desktop
application/xls=ooo-calc.desktop
application/x-lzop=file-roller.desktop
application/x-matroska=totem.desktop
application/x-mps=ooo-calc.desktop
application/x-ms-excel=ooo-calc.desktop
application/x-msexcel=ooo-calc.desktop
application/x-ogg=totem.desktop
application/x-oleo=ooo-calc.desktop
application/x-perl=gedit.desktop
application/x-planperfect=ooo-calc.desktop
application/x-quattropro=ooo-calc.desktop
application/x-rar-compressed=file-roller.desktop
application/x-rar=file-roller.desktop
application/x-rpm=file-roller.desktop
application/x-sc=ooo-calc.desktop
application/x-shockwave-flash=totem.desktop
application/x-sylk=ooo-calc.desktop
application/x-tar=file-roller.desktop
application/x-war=file-roller.desktop
application/x-xbase=ooo-calc.desktop
application/x-xls=ooo-calc.desktop
application/x-zip-compressed=file-roller.desktop
application/x-zip=file-roller.desktop
application/x-zoo=file-roller.desktop
application/zip=file-roller.desktop
audio/mpeg=totem.desktop
audio/mpegurl=totem.desktop
audio/vnd.rn-realaudio=totem.desktop
audio/x-flac=totem.desktop
audio/x-m4a=totem.desktop
audio/x-mp3=totem.desktop
audio/x-mpeg=totem.desktop
audio/x-mpegurl=totem.desktop
audio/x-ms-asf=totem.desktop
audio/x-ms-asx=totem.desktop
audio/x-ms-wax=totem.desktop
audio/x-pn-aiff=totem.desktop
audio/x-pn-au=totem.desktop
audio/x-pn-realaudio-plugin=totem.desktop
audio/x-pn-realaudio=totem.desktop
audio/x-pn-wav=totem.desktop
audio/x-pn-windows-acm=totem.desktop
audio/x-real-audio=totem.desktop
audio/x-scpls=totem.desktop
audio/x-wav=totem.desktop
image/bmp=eog.desktop
image/gif=eog.desktop
image/jpeg=eog.desktop
image/jpg=eog.desktop
image/pjpeg=eog.desktop
image/png=eog.desktop
image/svg+xml=eog.desktop
image/tiff=eog.desktop
image/vnd.rn-realpix=totem.desktop
image/x-bmp=eog.desktop
image/x-gray=eog.desktop
image/x-icb=eog.desktop
image/x-ico=eog.desktop
image/x-png=eog.desktop
image/x-portable-anymap=eog.desktop
image/x-portable-bitmap=eog.desktop
image/x-portable-graymap=eog.desktop
image/x-portable-pixmap=eog.desktop
image/x-psd=gimp-2.2.desktop
image/x-xbitmap=eog.desktop
image/x-xpixmap=eog.desktop
inode/directory=nautilus-folder-handler.desktop
misc/ultravox=totem.desktop
multipart/x-zip=file-roller.desktop
text/abiword=abiword.desktop
text/comma-separated-values=ooo-calc.desktop
text/csv=ooo-calc.desktop
text/html=firefox.desktop
text/plain=gedit.desktop
text/richtext=abiword.desktop
text/rtf=ooo-writer.desktop
text/spreadsheet=ooo-calc.desktop
text/tab-separated-values=ooo-calc.desktop
text/x-comma-separated-values=ooo-calc.desktop
text/x-chdr=gedit.desktop
text/x-csrc=gedit.desktop
text/x-dtd=gedit.desktop
text/x-java=gedit.desktop
text/mathml=gedit.desktop
text/x-python=gedit.desktop
text/x-sql=gedit.desktop
text/xml=firefox.desktop
video/dv=totem.desktop
video/mp4=totem.desktop
video/mpeg=totem.desktop
video/msvideo=totem.desktop
video/quicktime=totem.desktop
video/vnd.rn-realvideo=totem.desktop
video/x-anim=totem.desktop
video/x-avi=totem.desktop
video/x-flc=totem.desktop
video/x-fli=totem.desktop
video/x-mpeg=totem.desktop
video/x-ms-asf=totem.desktop
video/x-msvideo=totem.desktop
video/x-ms-wmv=totem.desktop
video/x-nsv=totem.desktop
x-directory/normal=nautilus-folder-handler.desktop
x-content/blank-cd=nautilus-cd-burner.desktop
x-content/blank-dvd=nautilus-cd-burner.desktop
x-content/blank-bd=nautilus-cd-burner.desktop
x-content/blank-hddvd=nautilus-cd-burner.desktop
x-content/video-dvd=totem.desktop
x-content/video-vcd=totem.desktop
x-content/video-svcd=totem.desktop
x-content/video-blueray=totem.desktop
x-content/video-hddvd=totem.desktop
x-content/audio-cdda=rhythmbox.desktop
x-content/audio-dvd=rhythmbox.desktop
x-content/audio-player=rhythmbox.desktop
x-content/image-dcf=f-spot-import.desktop
x-content/image-picturecd=f-spot-import.desktop
zz-application/zz-winassoc-xls=ooo-calc.desktop

```

this is my list of files and association. If you search it, you will see gz associated with file-roller

gksudo gedit /usr/share/applications/mimeinfo.cache

is similar and I think the first one is which one to edit. 

```

[MIME Cache]
image/jpeg=thunderbird.desktop;gimp.desktop;eog.desktop;firefox.desktop;firefox-2.desktop;gthumb.desktop;f-spot-view.desktop;
image/x-pcx=gimp.desktop;eog.desktop;gthumb.desktop;f-spot-view.desktop;
text/x-csrc=bluefish.desktop
application/x-cue=kde-k3b.desktop;brasero.desktop;
audio/x-ape=gnome-mplayer.desktop;banshee.desktop;totem.desktop;
application/vnd.google-earth.kmz=googleearth.desktop
video/x-avi=vlc.desktop;miro.desktop;mplayer.desktop;totem.desktop;
application/x-debian-package=gdebi.desktop
application/x-chess-pgn=glchess.desktop
application/x-musepack=gnome-mplayer.desktop;banshee.desktop;
x-content/audio-player=banshee.desktop;rhythmbox.desktop;
x-device/floppy=gfloppy.desktop
video/x-theora=mplayer.desktop;smplayer.desktop;smplayer_enqueue.desktop;
application/x-annodex=gxine.desktop
application/x-java-archive=openjdk-6-java.desktop;sun-java6-java.desktop;file-roller.desktop;sun-java5-java.desktop;
application/x-compress=file-roller.desktop
application/xml=amaya.desktop;thunderbird.desktop;firefox.desktop;firefox-2.desktop;
image/gif=thunderbird.desktop;gimp.desktop;eog.desktop;firefox.desktop;firefox-2.desktop;gthumb.desktop;f-spot-view.desktop;
application/x-extension-mp4=vlc.desktop;totem.desktop;
audio/x-16sv=gxine.desktop
application/vnd.google-earth.kml+xml=googleearth.desktop
image/x-xcf=gimp.desktop
application/x-iso=kde-k3b.desktop
audio/x-speex=gxine.desktop;totem.desktop;
image/vnd.rn-realpix=vlc.desktop;miro.desktop;totem.desktop;
image/svg+xml=inkscape.desktop;eog.desktop;gthumb.desktop;f-spot-view.desktop;
application/x-ear=file-roller.desktop
image/png=thunderbird.desktop;gimp.desktop;eog.desktop;firefox.desktop;gxine.desktop;firefox-2.desktop;gthumb.desktop;f-spot-view.desktop;
application/x-quicktimeplayer=gnome-mplayer.desktop;gxine.desktop;totem.desktop;
application/x-toc=brasero.desktop
image/jpg=gimp.desktop;eog.desktop;f-spot-view.desktop;
video/dv=vlc.desktop;miro.desktop;Kino.desktop;totem.desktop;
application/x-cpio=file-roller.desktop
application/exe=wine.desktop
application/smil=gnome-mplayer.desktop;Kino.desktop;mplayer.desktop;totem.desktop;
application/x-quattropro=ooo-calc.desktop
application/x-bittorrent=miro.desktop;transmission.desktop;gnome-btdownload.desktop;
x-content/image-dcf=f-spot-import.desktop
application/x-lzop=file-roller.desktop
application/vnd.sun.xml.writer=ooo-writer.desktop
audio/x-ms-asf=vlc.desktop;miro.desktop;totem.desktop;
application/x-brasero=brasero.desktop
x-content/blank-dvd=nautilus-cd-burner.desktop;brasero.desktop;
application/x-ogg=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;banshee.desktop;gxine.desktop;rhythmbox.desktop;totem.desktop;
video/fli=gnome-mplayer.desktop;totem.desktop;
application/x-dvi=evince.desktop
application/x-ar=file-roller.desktop
application/x-gzip=file-roller.desktop
application/zip=file-roller.desktop
application/x-vorbis+ogg=gnome-mplayer.desktop
application/x-ms-dos-executable=wine.desktop
video/x-msvideo=gnome-mplayer.desktop;xine.desktop;vlc.desktop;miro.desktop;mplayer.desktop;smplayer.desktop;gxine.desktop;totem.desktop;smplayer_enqueue.desktop;
image/ilbm=gxine.desktop
audio/musepack=gnome-mplayer.desktop;banshee.desktop;
application/rdf+xml=thunderbird.desktop;firefox.desktop;firefox-2.desktop;
application/x-mplayer2=gnome-mplayer.desktop;gxine.desktop;
audio/mpc=gnome-mplayer.desktop;banshee.desktop;
image/g3fax=gimp.desktop
application/pgp-keys=seahorse-pgp-keys.desktop
application/x-gzpdf=evince.desktop
application/vnd.openxmlformats-officedocument.presentationml.presentation=ooo-impress.desktop
application/x-font-type1=kde-kfontview.desktop;gnome-font-viewer.desktop;
application/pdf=AdobeReader.desktop;evince.desktop;
application/x-font-pcf=kde-kfontview.desktop;gnome-font-viewer.desktop;
application/x-nsv-vp3-mp3=gnome-mplayer.desktop
application/vnd.sun.xml.draw.template=ooo-draw.desktop
application/dos-exe=wine.desktop
application/vnd.stardivision.chart=ooo-calc.desktop
video/anim=gxine.desktop
audio/x-aac=mplayer.desktop
audio/mpg=mplayer.desktop
video/x-ms-afs=mplayer.desktop
image/x-xwindowdump=gimp.desktop
text/x-apt-sources-list=software-properties.desktop
image/x-mrw=f-spot-view.desktop
audio/x-mpegurl=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;gxine.desktop;rhythmbox.desktop;totem.desktop;serpentine.desktop;
x-content/video-vcd=totem.desktop
application/vnd.ms-powerpoint.slideshow.macroEnabled.12=ooo-impress.desktop
video/x-ms-wm=gnome-mplayer.desktop;totem.desktop;
text/css=bluefish.desktop
video/x-ms-wmp=gnome-mplayer.desktop
application/x-netshow-channel=totem.desktop
video/flv=totem.desktop
application/vnd.adobe.xfdf=AdobeReader.desktop
image/x-pict=totem.desktop
video/x-nsv=vlc.desktop;miro.desktop;totem.desktop;
application/wordperfect=ooo-writer.desktop
text/csv=ooo-calc.desktop
text/spreadsheet=ooo-calc.desktop
application/x-war=file-roller.desktop
application/x-miro=miro.desktop
application/x-rar-compressed=file-roller.desktop
application/x-lzma-compressed-tar=file-roller.desktop
image/x-tga=gimp.desktop;gthumb.desktop;
image/x-portable-bitmap=gimp.desktop;eog.desktop;f-spot-view.desktop;
application/vnd.oasis.opendocument.graphics-template=ooo-draw.desktop
audio/mpeg=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;banshee.desktop;smplayer.desktop;gxine.desktop;rhythmbox.desktop;totem.desktop;smplayer_enqueue.desktop;
application/x-flac=gnome-mplayer.desktop;vlc.desktop;banshee.desktop;rhythmbox.desktop;totem.desktop;
audio/x-ms-asx=vlc.desktop;miro.desktop;totem.desktop;
audio/x-mp=gnome-mplayer.desktop;banshee.desktop;
video/x-ms-wmv=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;smplayer.desktop;gxine.desktop;totem.desktop;smplayer_enqueue.desktop;
misc/ultravox=vlc.desktop;miro.desktop;totem.desktop;
application/bluefish-project=bluefish-project.desktop
application/vnd.oasis.opendocument.text=ooo-writer.desktop
audio/x-musepack=gnome-mplayer.desktop;banshee.desktop;totem.desktop;
video/x-ms-wmx=mplayer.desktop;totem.desktop;
audio/ogg=gnome-mplayer.desktop;banshee.desktop;totem.desktop;
application/x-gtar=file-roller.desktop
application/x-shorten=totem.desktop
application/x-php=bluefish.desktop
application/x-extension-txt=ooo-writer.desktop
audio/x-scpls=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;rhythmbox.desktop;totem.desktop;serpentine.desktop;
video/x-mng=gxine.desktop
application/vnd.adobe.pdx=AdobeReader.desktop
text/x-sql=bluefish.desktop
application/x-hcidump=bluetooth-analyzer.desktop
x-content/software=nautilus-autorun-software.desktop
video/vivo=totem.desktop
video/mkv=gxine.desktop
application/x-ape=gnome-mplayer.desktop;banshee.desktop;
image/vnd.wap.wbmp=eog.desktop
application/vnd.sun.xml.writer.global=ooo-writer.desktop
application/x-bzpdf=evince.desktop
audio/x-mpeg=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;banshee.desktop;gxine.desktop;rhythmbox.desktop;totem.desktop;
application/vnd.ms-excel=ooo-calc.desktop
audio/x-pn-au=vlc.desktop;miro.desktop;gxine.desktop;totem.desktop;
image/x-ilbm=gxine.desktop
image/x-xpixmap=gimp.desktop;eog.desktop;f-spot-view.desktop;
audio/x-xm=gnome-mplayer.desktop;banshee.desktop;totem.desktop;
video/vnd.vivo=gnome-mplayer.desktop;totem.desktop;
application/x-bzip=file-roller.desktop
application/vnd.ms-excel.sheet.macroEnabled.12=ooo-calc.desktop
application/vnd.sun.xml.writer.template=ooo-writer.desktop
application/x-dbf=ooo-calc.desktop
application/vnd.stardivision.writer=ooo-writer.desktop
x-content/video-svcd=gxine.desktop;totem.desktop;
application/x-compressed-tar=file-roller.desktop
image/x-raf=f-spot-view.desktop
image/*=evince.desktop
video/x-m4v=totem.desktop
image/x-compressed-xcf=gimp.desktop
fonts/package=kde-kfontview.desktop
image/x-bmp=gimp.desktop;eog.desktop;gthumb.desktop;f-spot-view.desktop;
application/vnd.oasis.opendocument.formula=ooo-math.desktop
audio/scpls=mplayer.desktop
audio/x-vorbis+ogg=gnome-mplayer.desktop
audio/x-m4a=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;banshee.desktop;gxine.desktop;totem.desktop;
application/vnd.stardivision.calc=ooo-calc.desktop
application/vnd.ms-powerpoint.template.macroEnabled.12=ooo-impress.desktop
video/x-matroska=mplayer.desktop;smplayer.desktop;totem.desktop;smplayer_enqueue.desktop;
video/mp4v-es=vlc.desktop;totem.desktop;
text/x-dtd=bluefish.desktop
application/x-gnome-theme-installed=themus-theme-applier.desktop
video/mpeg=gnome-mplayer.desktop;xine.desktop;vlc.desktop;miro.desktop;mplayer.desktop;smplayer.desktop;gxine.desktop;totem.desktop;smplayer_enqueue.desktop;
audio/x-wavpack=totem.desktop
video/x-ogm+ogg=totem.desktop
audio/wav=gnome-mplayer.desktop;mplayer.desktop;gxine.desktop;
audio/x-adpcm=smplayer.desktop;smplayer_enqueue.desktop;
application/vnd.sun.xml.calc=ooo-calc.desktop
application/vnd.stardivision.impress=ooo-impress.desktop
application/vnd.stardivision.writer-global=ooo-writer.desktop
application/vnd.stardivision.draw=ooo-draw.desktop
image/x-sgi=gimp.desktop
application/x-exe=wine.desktop
text/x-csv=ooo-calc.desktop
application/x-cgi=bluefish.desktop
application/vnd.oasis.opendocument.text-master=ooo-writer.desktop
application/vnd.sun.xml.draw=ooo-draw.desktop
audio/x-mpeg2=gnome-mplayer.desktop;gxine.desktop;
application/x-gzpostscript=file-roller.desktop;evince.desktop;
audio/mpegurl=mplayer.desktop;gxine.desktop;totem.desktop;
audio/x-mpeg3=gnome-mplayer.desktop;gxine.desktop;
audio/ape=gnome-mplayer.desktop;banshee.desktop;
application/x-zip=file-roller.desktop
application/vnd.oasis.opendocument.text-template=ooo-writer.desktop
image/bmp=gimp.desktop;eog.desktop;gthumb.desktop;f-spot-view.desktop;
application/ram=totem.desktop
text/google-video-pointer=totem.desktop
application/x-bzip-compressed-tar=file-roller.desktop
audio/AMR-WB=totem.desktop
application/x-java-jnlp-file=openjdk-6-javaws.desktop;sun-java5-javaws.desktop;sun-java6-javaws.desktop;
video/x-ms-asf-plugin=gnome-mplayer.desktop;gxine.desktop;
application/pgp-signature=seahorse-pgp-signature.desktop
inode/directory=kde-kfmclient_dir.desktop;Thunar-folder-handler.desktop;nautilus-folder-handler.desktop;
video/x-flic=gxine.desktop;totem.desktop;
application/vnd.ms-excel.sheet.binary.macroEnabled.12=ooo-calc.desktop
application/vnd.ms-asf=gxine.desktop
audio/x-mp1=mplayer.desktop
audio/x-mp2=xine.desktop;mplayer.desktop;smplayer.desktop;smplayer_enqueue.desktop;
application/vnd.oasis.opendocument.graphics=ooo-draw.desktop
application/vnd.openxmlformats-officedocument.spreadsheetml.template=ooo-calc.desktop
audio/mpeg2=gnome-mplayer.desktop;gxine.desktop;
application/vnd.wordperfect=ooo-writer.desktop
audio/x-mp3=gnome-mplayer.desktop;xine.desktop;vlc.desktop;miro.desktop;mplayer.desktop;banshee.desktop;smplayer.desktop;gxine.desktop;rhythmbox.desktop;totem.desktop;smplayer_enqueue.desktop;
video/x-anim=xine.desktop;vlc.desktop;miro.desktop;gxine.desktop;totem.desktop;
audio/mpeg3=gnome-mplayer.desktop;banshee.desktop;gxine.desktop;
video/x-quicktime=gnome-mplayer.desktop;gxine.desktop;
application/x-webarchive=kde-kfmclient_war.desktop
audio/x-sbc=totem.desktop
application/vnd.fdf=AdobeReader.desktop
application/vnd.ms-powerpoint.presentation.macroEnabled.12=ooo-impress.desktop
application/vnd.openxmlformats-officedocument.wordprocessingml.template=ooo-writer.desktop
text/html=amaya.desktop;thunderbird.desktop;kde-kfmclient_html.desktop;kde-quanta.desktop;firefox.desktop;bluefish.desktop;firefox-2.desktop;lynx.desktop;
application/x-cbr=evince.desktop
audio/x-it=gnome-mplayer.desktop;banshee.desktop;totem.desktop;
video/x-theora+ogg=totem.desktop
audio/flac=gnome-mplayer.desktop;banshee.desktop;
audio/x-mpeg-3=gnome-mplayer.desktop;banshee.desktop;
audio/rn-mpeg=mplayer.desktop
image/x-dcraw=f-spot-view.desktop
audio/x-pn-windows-acm=vlc.desktop;miro.desktop;gxine.desktop;totem.desktop;
application/mspowerpoint=ooo-impress.desktop
image/x-nef=f-spot-view.desktop
application/x-remote-connection=vinagre.desktop
application/x-font-otf=kde-kfontview.desktop;gnome-font-viewer.desktop;
application/vnd.mozilla.xul+xml=thunderbird.desktop;firefox.desktop;firefox-2.desktop;
audio/vorbis=gnome-mplayer.desktop;banshee.desktop;smplayer.desktop;smplayer_enqueue.desktop;
audio/x-ms-wax=gnome-mplayer.desktop;vlc.desktop;miro.desktop;totem.desktop;
text/x-perl=bluefish.desktop
application/msdos-windows=wine.desktop
application/x-btsnoop=bluetooth-analyzer.desktop
audio/x-pn-wav=vlc.desktop;miro.desktop;gxine.desktop;totem.desktop;
application/vnd.sun.xml.impress.template=ooo-impress.desktop
application/vnd.openxmlformats-officedocument.presentationml.template=ooo-impress.desktop
application/vnd.oasis.opendocument.chart=ooo-calc.desktop
application/x-tar=file-roller.desktop
application/x-pktlog=bluetooth-analyzer.desktop
x-content/blank-hddvd=nautilus-cd-burner.desktop;brasero.desktop;
application/x-konsole=kde-konsolesu.desktop
application/x-cbz=evince.desktop
video/msvideo=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;gxine.desktop;totem.desktop;
video/avi=smplayer.desktop;smplayer_enqueue.desktop;
x-content/image-picturecd=f-spot-import.desktop
audio/aac=mplayer.desktop
application/x-zoo=file-roller.desktop
audio/x-flac=gnome-mplayer.desktop;vlc.desktop;banshee.desktop;totem.desktop;
text/x-google-video-pointer=totem.desktop
video/vnd.divx=totem.desktop
text/javascript=bluefish.desktop
application/x-winexe=wine.desktop
application/vnd.oasis.opendocument.spreadsheet-template=ooo-calc.desktop
application/x-cisco-vpn-settings=nm-vpnc.desktop
application/x-rpm=file-roller.desktop
application/vnd.openxmlformats-officedocument.wordprocessingml.document=ooo-writer.desktop
application/earthviewer=googleearth.desktop
video/x-ms-asf=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;smplayer.desktop;gxine.desktop;totem.desktop;smplayer_enqueue.desktop;
application/x-zip-compressed=file-roller.desktop;wine.desktop;
application/x-jar=openjdk-6-java.desktop;sun-java6-java.desktop;file-roller.desktop;sun-java5-java.desktop;
application/vnd.stardivision.math=ooo-math.desktop
application/vnd.sun.xml.calc.template=ooo-calc.desktop
application/vnd.adobe.xdp+xml=AdobeReader.desktop
application/vnd.oasis.opendocument.presentation-template=ooo-impress.desktop
application/x-streamingmedia=mplayer.desktop
audio/x-mod=gnome-mplayer.desktop;banshee.desktop;totem.desktop;
application/x-lha=file-roller.desktop
video/x-flc=vlc.desktop;miro.desktop;totem.desktop;
application/vnd.sun.xml.math=ooo-math.desktop
application/vnd.rn-realmedia-vbr=mplayer.desktop
application/x-drm-v2=gnome-mplayer.desktop
text/x-chdr=bluefish.desktop
image/tiff=gimp.desktop;eog.desktop;evince.desktop;gthumb.desktop;f-spot-view.desktop;
audio/8svx=gxine.desktop
audio/x-s3m=gnome-mplayer.desktop;banshee.desktop;
text/x-python=bluefish.desktop
image/x-eps=evince.desktop
audio/x-basic=gnome-mplayer.desktop;gxine.desktop;
image/x-icb=eog.desktop;f-spot-view.desktop;
x-directory/normal=Thunar-folder-handler.desktop;nautilus-folder-handler.desktop;
application/xspf+xml=totem.desktop
image/svg+xml-compressed=eog.desktop
application/x-cdrdao-toc=brasero.desktop
application/x-k3b=kde-k3b.desktop
application/x-msi=wine.desktop
audio/ac3=smplayer.desktop;totem.desktop;smplayer_enqueue.desktop;
video/x-fli=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;totem.desktop;
application/vnd.ms-excel.template.macroEnabled.12=ooo-calc.desktop
image/x-portable-graymap=gimp.desktop;eog.desktop;f-spot-view.desktop;
image/x-gzeps=evince.desktop
application/x-lzma=file-roller.desktop
application/x-shockwave-flash=vlc.desktop
application/rss+xml=thunderbird.desktop;firefox.desktop;firefox-2.desktop;
application/x-onboard=onboard.desktop
audio/x-ms-wma=gnome-mplayer.desktop;mplayer.desktop;smplayer.desktop;gxine.desktop;totem.desktop;smplayer_enqueue.desktop;
video/x-mpeg2=gnome-mplayer.desktop;mplayer.desktop;
x-content/blank-bd=nautilus-cd-burner.desktop;brasero.desktop;
application/vnd.ms-word.template.macroEnabled.12=ooo-writer.desktop
application/xhtml+xml=amaya.desktop;thunderbird.desktop;kde-kfmclient_html.desktop;firefox.desktop;bluefish.desktop;firefox-2.desktop;
audio/x-real-audio=vlc.desktop;miro.desktop;gxine.desktop;totem.desktop;
application/x-smil=mplayer.desktop;totem.desktop;
audio/x-8svx=gxine.desktop
video/x-mpeg=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;gxine.desktop;totem.desktop;
x-content/video-dvd=gxine.desktop;totem.desktop;
audio/x-vorbis=gnome-mplayer.desktop;banshee.desktop;smplayer.desktop;totem.desktop;smplayer_enqueue.desktop;
image/xpm=gthumb.desktop
audio/basic=gnome-mplayer.desktop;gxine.desktop;totem.desktop;
application/x-arj=file-roller.desktop
application/x-7z-compressed=file-roller.desktop
application/asx=gnome-mplayer.desktop
image/x-ico=eog.desktop;gthumb.desktop;f-spot-view.desktop;
application/java-archive=openjdk-6-java.desktop;sun-java6-java.desktop;sun-java5-java.desktop;
application/x-vnc=vinagre-file.desktop
x-content/audio-dvd=banshee.desktop
application/msword=ooo-writer.desktop
video/x-flv=gnome-mplayer.desktop;gxine.desktop;
application/vnd.openxmlformats-officedocument.presentationml.slideshow=ooo-impress.desktop
application/x-gnome-theme-package=gnome-theme-installer.desktop
application/x-emerald-theme=emerald-theme-manager.desktop
image/x-ciff=f-spot-view.desktop
audio/m4a=mplayer.desktop
application/streamingmedia=mplayer.desktop
print/manager=kde-printers.desktop
application/x-rar=file-roller.desktop
application/x-lhz=file-roller.desktop
image/x-sun-raster=gimp.desktop
text/rtf=ooo-writer.desktop
image/x-xbitmap=gimp.desktop;eog.desktop;f-spot-view.desktop;
application/vnd.openxmlformats-officedocument.spreadsheetml.sheet=ooo-calc.desktop
application/x-qtconfig=qt3config.desktop
application/postscript=evince.desktop
video/mng=gxine.desktop
application/x-msdos-program=wine.desktop
video/x-ogm=smplayer.desktop;smplayer_enqueue.desktop;
image/x-fits=gimp.desktop
text/plain=ooo-writer.desktop;kde-kwrite.desktop;kde-kate.desktop;gedit.desktop;mousepad.desktop;
image/x-bzeps=evince.desktop
audio/x-mpc=gnome-mplayer.desktop;banshee.desktop;
image/x-portable-pixmap=gimp.desktop;eog.desktop;f-spot-view.desktop;
application/x-matroska=vlc.desktop;miro.desktop;totem.desktop;
audio/midi=gnome-mplayer.desktop;totem.desktop;
audio/x-ms-wmv=gnome-mplayer.desktop
audio/x-tta=totem.desktop
application/x-bzpostscript=evince.desktop
application/x-javascript=bluefish.desktop
audio/x-mpg=mplayer.desktop
audio/x-pls=mplayer.desktop
application/x-stopmotion=stopmotion.desktop
image/x-cr2=f-spot-view.desktop
application/vnd.sun.xml.impress=ooo-impress.desktop;evince.desktop;
application/x-ace=file-roller.desktop
application/x-ktheme=kde-installktheme.desktop
application/x-python=bluefish.desktop
application/x-font-bdf=kde-kfontview.desktop
text/xml=amaya.desktop;thunderbird.desktop;kde-kfmclient_html.desktop;firefox.desktop;bluefish.desktop;firefox-2.desktop;
video/mp4=gnome-mplayer.desktop;vlc.desktop;smplayer.desktop;totem.desktop;smplayer_enqueue.desktop;
application/x-quicktime-media-link=totem.desktop
audio/3gpp=totem.desktop
application/vnd.oasis.opendocument.formula-template=ooo-math.desktop
application/x-dbase=ooo-calc.desktop
audio/mp1=mplayer.desktop
x-content/blank-cd=nautilus-cd-burner.desktop;brasero.desktop;
application/x-gzdvi=evince.desktop
application/ogg=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;banshee.desktop;gxine.desktop;rhythmbox.desktop;totem.desktop;
audio/mp2=mplayer.desktop
application/vnd.rn-realmedia=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;gxine.desktop;totem.desktop;
audio/mp3=gnome-mplayer.desktop;mplayer.desktop;banshee.desktop;gxine.desktop;
audio/mp4=gnome-mplayer.desktop;vlc.desktop;smplayer.desktop;totem.desktop;smplayer_enqueue.desktop;
application/msexcel=ooo-calc.desktop
application/x-id3=gnome-mplayer.desktop;banshee.desktop;
application/x-deb=gdebi.desktop;hubackup.desktop;file-roller.desktop;
application/x-onboardsettings=onboard-settings.desktop
application/x-kommander=kde-kmdr-editor.desktop
vms/exe=wine.desktop
image/x-orf=f-spot-view.desktop
application/vnd.lotus-1-2-3=ooo-calc.desktop
audio/x-pn-aiff=vlc.desktop;miro.desktop;gxine.desktop;totem.desktop;
audio/x-ogg=gnome-mplayer.desktop;banshee.desktop;gxine.desktop;
application/x-flash-video=totem.desktop
application/keyhole=googleearth.desktop
multipart/x-zip=file-roller.desktop
text/x-javascript=bluefish.desktop
image/pjpeg=gimp.desktop;eog.desktop;f-spot-view.desktop;
audio/x-realaudio=gnome-mplayer.desktop;mplayer.desktop;gxine.desktop;totem.desktop;
text/x-php=bluefish.desktop
application/sdp=mplayer.desktop;totem.desktop;
application/vnd.oasis.opendocument.chart-template=ooo-calc.desktop
text/mathml=bluefish.desktop;ooo-math.desktop;
application/x-perl=bluefish.desktop
application/musepack=gnome-mplayer.desktop;banshee.desktop;
application/vnd.ms-works=ooo-writer.desktop
image/vnd.djvu=evince.desktop
audio/x-pn-realaudio=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;gxine.desktop;totem.desktop;
audio/x-pn-windows-pcm=mplayer.desktop
application/vnd.rn-realaudio=gnome-mplayer.desktop
audio/aiff=gxine.desktop
application/vnd.ms-word.document.macroEnabled.12=ooo-writer.desktop
image/x-psd=gimp.desktop;f-spot-view.desktop;
application/x-extension-m4a=totem.desktop
application/x-ms-wmv=gnome-mplayer.desktop
application/vnd.sun.xml.base=ooo-base.desktop
image/x-x3f=f-spot-view.desktop
x-directory/gnome-default-handler=Thunar-folder-handler.desktop;nautilus-folder-handler.desktop;
video/vnd.rn-realvideo=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;smplayer.desktop;totem.desktop;smplayer_enqueue.desktop;
video/x-ms-wvx=gnome-mplayer.desktop;gxine.desktop;totem.desktop;
x-content/audio-cdda=sound-juicer.desktop;banshee.desktop;rhythmbox.desktop;
application/x-gnome-saved-search=nautilus-folder-handler.desktop
image/x-portable-anymap=gimp.desktop;eog.desktop;f-spot-view.desktop;
audio/x-matroska=smplayer.desktop;totem.desktop;smplayer_enqueue.desktop;
audio/x-pn-realaudio-plugin=gnome-mplayer.desktop;vlc.desktop;miro.desktop;gxine.desktop;totem.desktop;
video/x-ms-wax=gxine.desktop
application/x-font-ttc=kde-kfontview.desktop
application/x-democracy=miro.desktop
audio/AMR=totem.desktop
video/3gpp=gnome-mplayer.desktop;totem.desktop;
application/x-t602=ooo-writer.desktop
application/x-bzdvi=evince.desktop
video/quicktime=gnome-mplayer.desktop;xine.desktop;vlc.desktop;miro.desktop;mplayer.desktop;smplayer.desktop;gxine.desktop;totem.desktop;smplayer_enqueue.desktop;
application/vnd.oasis.opendocument.spreadsheet=ooo-calc.desktop
application/x-font-ttf=kde-kfontview.desktop;gnome-font-viewer.desktop;
application/x-ksysguard=kde-ksysguard.desktop
audio/x-wav=gnome-mplayer.desktop;vlc.desktop;miro.desktop;mplayer.desktop;smplayer.desktop;gxine.desktop;totem.desktop;smplayer_enqueue.desktop;
application/vnd.oasis.opendocument.database=ooo-base.desktop
application/x-executable=wine.desktop
audio/x-aiff=gxine.desktop
application/rtf=ooo-writer.desktop
audio/vnd.rn-realaudio=vlc.desktop;miro.desktop;mplayer.desktop;smplayer.desktop;totem.desktop;smplayer_enqueue.desktop;
audio/168sv=gxine.desktop
application/x-webprj=kde-quanta.desktop
application/vnd.oasis.opendocument.presentation=ooo-impress.desktop;evince.desktop;
application/x-cd-image=brasero.desktop;file-roller.desktop;nautilus-cd-burner-open-iso.desktop;
application/x-msdownload=wine.desktop
image/x-png=gimp.desktop;eog.desktop;gxine.desktop;gthumb.desktop;f-spot-view.desktop;
video/x-ms-wvxvideo=mplayer.desktop
text/x-apport=apport-gtk-mime.desktop
image/x-gray=gimp.desktop;eog.desktop;f-spot-view.desktop;
audio/mp=gnome-mplayer.desktop;banshee.desktop;
application/vnd.ms-powerpoint=ooo-impress.desktop
text/x-java=bluefish.desktop
application/pgp-encrypted=seahorse-pgp-encrypted.desktop

```

read thru this maybe it will help out
[http://ubuntuforums.org/archive/index.php/t-594220.html](http://ubuntuforums.org/archive/index.php/t-594220.html)

---

### Post by daimaru on 2008-07-19
> **sdowney717 said:**
> Avast has a linux version
Linux has clam antivirus
Unless you use WINE, you wont have any trouble. Although you could spread the virus to others.

UMM even if you use wine it won't be able to infect your linux partition would it? it would only run a virus in the wine environment, but it would not be able to spread to your linux distro would it? at least that is what i heard once upon a time .

---

### Post by sdowney717 on 2008-07-19
editing the first file changed my file association for totem to vlc.
So, then this works.

---

### Post by sdowney717 on 2008-07-19
> 
UMM even if you use wine it won't be able to infect your linux partition would it? it would only run a virus in the wine environment, but it would not be able to spread to your linux distro would it? at least that is what i heard once upon a time .


yes, it wont be a virus that can run or do anything. I did read some post where someone claimed a virus copied a whole lot of stuff all over his filesystem, but none of the viruses were able to run.

there is something about linking your linux filesystem as drive letter z: that can be a problem

---

### Post by daimaru on 2008-07-19
> **sdowney717 said:**
> yes, it wont be a virus that can run or do anything. I did read some post where someone claimed a virus copied a whole lot of stuff all over his filesystem, but none of the viruses were able to run.

there is something about linking your linux filesystem as drive letter z: that can be a problem
thx

---

