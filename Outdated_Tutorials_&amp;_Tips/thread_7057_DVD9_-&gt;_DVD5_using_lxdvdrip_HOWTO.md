---
title: "DVD9 -&gt; DVD5 using lxdvdrip HOWTO"
date: 2004-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Original Brownster on 2004-12-03
The best program I have found to rip the main feature of a dvd and shrink it to a single dvd is 'lxdvdrip'. Once you have it installed, ripping a dvd is a one command job and has worked extremely well for me.
I have prepared this howto from memory and some notes; I hope it is complete and correct, if not I'll gladly correct any errors.

[Lxdvdrip](http://openfacts.berlios.de/index-en.phtml?title=Lxdvdrip)

Having recently moved to ubuntu, I found that not all the packages required were available, I have prepared this guide in the hope that it helps someone else out there.
It does use packages outside of the standard 'warty' release including mixing packages from various Debian repositories which I am sure is not the wisest thing to do. It does have one advantage however in that your main system will stay as is which in my case is 'warty', I don't want to upgrade huge parts of the system when all I want is this program to work.
Bottom line is 'you break it you fix it'.

You will need cd / dvd writing working before you start.

You will require the universe repository in your sources list also the marillat sources:
[ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)

**Install  mplayer	**
	At the time of writing, mplayer would not install because of broken dependencies so install mplayer from source code, following the howto here works well:
[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

NOTE: This also installs a number of tools required later for compilation so you'll need at least some of the packages listed anyway.

Now download and install the following packages:

**libavc1394-0**		[http://packages.debian.org/testing/libs/libavc1394-0](http://packages.debian.org/testing/libs/libavc1394-0)

Note if your downloading and installing individual packages the command to use is:
dpkg -i packagename. If you try and install them in the wrong order it will complain about failed dependencies so install them in the order required.

Transcode and it's dependencies are fundamental, the transcode package is in the Marillat repository but some of it's dependencies are not:

**libavifile-0.7c102**[http://packages.debian.org/unstable/libs/libavifile-0.7c102](http://packages.debian.org/unstable/libs/libavifile-0.7c102)

**libjasper-1.701-1**[http://packages.debian.org/testing/libs/libjasper-1.701-1](http://packages.debian.org/testing/libs/libjasper-1.701-1)

**libquicktime1**[http://packages.debian.org/testing/libs/libquicktime1](http://packages.debian.org/testing/libs/libquicktime1)

**Install Transcode**	

**libdvdcss1**	[http://butterfly.dm.uniba.it/debian-unofficial/audio-video/dists/sid/main/binary-i386/libdvdcss1_1.0.1-0.1_i386.deb](http://butterfly.dm.uniba.it/debian-unofficial/audio-video/dists/sid/main/binary-i386/libdvdcss1_1.0.1-0.1_i386.deb)

**dvdauthor** (unbuntu universe)
**dvd+rw-tools** (unbuntu warty)
**dvdbackup** (unbuntu universe)
**libdvdread	**	[http://ftp.uk.debian.org/debian/pool/main/libd/libdvdread2/libdvdread2_0.9.2-0.1_i386.deb](http://ftp.uk.debian.org/debian/pool/main/libd/libdvdread2/libdvdread2_0.9.2-0.1_i386.deb)

Now we need to download and compile
**streamdvd**
[http://www.badabum.de/down/streamdvd-0.4.tar.gz](http://www.badabum.de/down/streamdvd-0.4.tar.gz)

place in  /usr/local/src
unpack it 'tar xvfz streamdvd-0.4.tar.gz'
cd into the unpacked directory
enter 'make' command
then as root 'make install'

Finally we can download and install
**lxdvdrip**
[http://download.berlios.de/lxdvdrip/lxdvdrip-1.41-pre2.tgz](http://download.berlios.de/lxdvdrip/lxdvdrip-1.41-pre2.tgz)
unpack it 'tar xvfz lxdvdrip-1.41-pre2.tgz'
cd into the directory
enter 'make' command
then as root 'make install'

Configure lxdvdrip by editing the lxdvdrip-EN file found in /usr/local/src/lxdvdrip/doc-pak/

Mine looks like this (with all the comments removed):

<----- excerpt of lxdvdrip.conf file
```

version=1.40
titel=0
videoformat=0
audio=2
untertitel=0
faktor=0
dvdleser=/dev/dvd
dvdbrenner=/dev/dvd
filmverzeichnis=/root/dvds
file=0
brennprogramm=1
vobplayer=mplayer
vobplay_param=""
language=en
audio-default=0
streamtool=streamdvd
wait-burn=1
tmp=/tmp
delete=0
mplex=tcmplex
chapter=1
free=1
speed=4
dvdcompat=1
mkisofs_param=""
burn_param=""

burnkey=CDR_SECURITY=insert_key_from_homepage
eject=1
rw-format=1
dvdauthor_name=dvdauthor
streamdvd_name=streamdvd
streamanalyze_name=streamanalyze
buffer_name=buffer
tccat_name=tccat
tcextract_name=tcextract
tcrequant_name=tcrequant
mplayer_name=mplayer
mplex_name=mplex
tcmplex_name=tcmplex
spumux_name=spumux
spuunmux_name=spuunmux
dvdbackup_name=dvdbackup
mkisofs_name=mkisofs
cdrecord_prodvd_name=cdrecord-prodvd
growisofs_name=growisofs
dvd+rw-format=dvd+rw-format
dvdunauthor_name=dvdunauthor
tcprobe_name=tcprobe
vamps_name=vamps
eject_name=eject
mpgtx_name=mpgtx
transcode_name=transcode
dvdwizard=0
dvdwizard_name=dvdwizard
dvdwizard_bild1=/usr/share/pixmaps/penguin.jpg
dvdwizard_bild2=/usr/share/pixmaps/penguin.jpg 

```
end of lxdvdrip.conf file ------>

---

### Post by Navin_Johnson on 2005-07-01
With some of the questions about DVD shrink in Wine, perhaps it's good to revisit this native linux solution.  

Anyone using this with success?  I'm away from my home pc so I haven't tried it yet but I will soon.

In addition to lxdvdrip, is anyone using k9copy on ubuntu ([http://k9copy.free.fr/index.php)?](http://k9copy.free.fr/index.php)?)  Vamps Tools ([http://vamps-tools.sourceforge.net/](http://vamps-tools.sourceforge.net/)) looks like it might be neat too but it does not look like there is too much current activity there.

Navin Johnson

---

### Post by TuxCrafter on 2006-12-02
I made a script that installs lxdvdrip, and I tested it.

I also have a config file:
I used it to change a DVD9 on my HDD to DVD5

```
sudo apt-get install mplayer vamps libavc1394-0 libavc1394-dev libavifile-0.7c2 libavifile-0.7-dev libjasper-1.701-1 libjasper-1.701-dev libquicktime0 libquicktime-dev transcode libdvdcss2 dvdauthor dvd+rw-tools dvdbackup libdvdread3 libdvdread3-dev libdvdnav4 libdvdnav-dev

cd ~
mkdir streamdvd
cd streamdvd
wget http://www.badabum.de/down/streamdvd-0.4.tar.gz
tar xvfz streamdvd-0.4.tar.gz
cd StreamDVD-0.4
make
sudo make install

cd ~
mkdir lxdvdrip
cd lxdvdrip
wget http://download.berlios.de/lxdvdrip/lxdvdrip-1.62.tgz
tar xvfz lxdvdrip-1.62.tgz
cd lxdvdrip
make
sudo make install

sudo mousepad /etc/lxdvdrip.conf

```

```
# Einstellungsdatei fuer lxdvdrip.
# Alle Einstellungen werden mit moglichen Werten aufgelistet.
# Ausserdem ist jeweils der entsprechende Kommandozeilenparameter 
# angegeben. 
# Die Parameter muesen immer in der Form "parameter=wert" ohne 
# Leerzeichen angegeben werden.
 
# Version der Config-Datei
version=1.61

# Auswahl des zu rippenden Titels, bestimmen mit "lsdvd".
# Alternative: bei titel=0 bestimmt lxdvdrip den laengsten Titel der DVD
# selbst. titel=l: Auswahl aus Liste. Entspricht "-t=".
titel=0

# 'dvdauthor -v' (aspect ratio, x * y, pal/ntsc)
# 0=nein, 1=ja. Entspricht "-vf=".
videoformat=1

# Auswahl des Audiotracks bzw. der Sprache.
# 1 = deutsch, 2 = englisch, 3 = deutsch und englisch, 4,xx = Sprache xx
# l=Liste, frei waehlbar per Eingabe
# Entspricht "-a=".
audio=l

# Untertitel auswaehlen. Track-Nr. kann man mit "lsdvd" bestimmen.
# Bei "l" erscheint im Programm eine Liste und man kann die Nr. eingeben.
# Bei "f" werden alle "Forced" Untertitel beruecksichtigt.
# Bei "a" werden alle Untertitel gerippt, aber nur bei Vamps moeglich.
# Ansonsten Sprachkuerzel, das waehlt automatisch Untertitel mit der Sprache.
# Also z. B. "untertitel=de".
# Entspricht "-u=".
untertitel=l

# Faktor fuer das Requantisieren/Verkleinerung. 
# Bei "0" berechnet lxdvdrip den Faktor selbst.
# Bei einem Wert groesser als 1 wird der angegebene Wert so uebernommen.
# Bei "-1" wird ein Testrip mit transcode ausgefuehrt und dieser Faktor 
# verwendet. 
# Entspricht "-f=".
faktor=0

# Groesse DVD in Bytes.
# Roh-Kapazitaet sind 4700000000 Bytes. Weil die Faktor-
# berechnung nicht 100 % genau arbeitet, sollte man etwas 
# Reserve einplanen. Abhaengig vom Streamtool kann man
# die Einstellung bei sehr genauer Berechnung auch hoeher setzen.
groesse_dvd=4600000000

# Device fuer DVD-Leselaufwerk.
# Entspricht "-dl=".
dvdleser=/mnt/hda3/downloads/usenet/7672484

# Device fuer DVD-Brenner.
# Beim Brennen mit "growisofs" ist zumeist "/dev/scd0" die richtige Wahl.
# Bei "cdrecord-prodvd" zumeist "0,0,0", testen mit "cdrecord-prodvd -scanbus".
# Entspricht "-db=".
dvdbrenner=/mnt/hda3/downloads/usenet/

# Filmverzeichnis. In diesem Unterverzeichnis legt "dvdauthor" die 
# DVD Struktur an.
# Entspricht "-fv=".
filmverzeichnis=/mnt/hda3/downloads/usenet/film-dvd

# Statt einer DVD-Struktur eine VOB-Datei erstellen fuer weitere 
# Bearbeitung.
# "0": Option ist ausgeschaltet.
# "1": Option eingeschaltet, Name der Datei ist der Name der DVD
# z. B. "/tmp/film.vob": schaltet Option ein mit festem Dateinamen.
# Entspricht "-file=".
file=0

# Brennprogramm. Bei "1" wird growisofs verwendet, bei "2" cdrecord-prodvd.
# Bei "3" wird cdrecord-prodvd mit mkisofs on the fly gestartet.
# "4"=ISO-Image "/tmp/dvdrip.img" durch mkisofs.
# "5"=ISO-Image mit "Volume-ID.img" (=Name der DVD) als Namen.
# 0=kein Brennen.
# Entspricht "-bp=".
brennprogramm=0

# Mehrere Kopien?
# Bei "1" kommt nach jeder Kopie eine Frage, ob noch eine Kopie erfolgen soll.
# Bei "0" wird einmal gebrannt, dann das Programm beendet.
# Kommandozeile: "-mc="
multicopy=1

# Medienplayer fuer Vorschau der gerippten Daten. Echter Programmname.
# Vorschau wird durch "off" ausgeschaltet.
# Entspricht "-mp=".
vobplayer=mplayer

# Zusaetzliche Parameter fuer den "vobplayer".
# Parameter muessen in Hochkommas stehen.
# Beim mplayer kann hier z. B. das Ausgabeziel definiert werden.
vobplay_param=""

# Auswahl der Programmsprache (Meldungen und Abfragen)
# "en"=Englisch, "de"=deutsch, "fr"=franzoesisch.
# Entspricht "-lang=".
language=en

# Auswahl des bevorzugten Audioformates.
# 0=ac3 mit 2 Kanal, 1=ac3 5.1, 2=dts.
# Entspricht "-ad=".
audio-default=1

# Streamtool zum Rippen
# Moegliche Werte: vamps, vamps_menu, mplayer, transcode, trans_par 
# (Transcode parallel), copy, partcopy.
# Entspricht "-st=".
streamtool=vamps

# Sicherheitsabfrage zum Einlegen Rohling vor Brennen?
# 0=nein, Brennen startet direkt, 1=ja, Pause.
# Entspricht "-wb=".
wait-burn=1

# Tmp-Verzeichnis. Wird nur gebraucht bei streamtool mplayer und transcode.
# Entspricht "-tmp=".
tmp=/mnt/hda3/downloads

# Loeschen der VOB-Files bei Programmende?
# 0=nein, 1=ja, dateien werden geloescht.
# Entspricht "-d=".
delete=0

# Multiplexer. Einstellung wird nur fuer streamtool mplayer und transcode
# verwendet. Moegliche Werte: "mplex", "tcmplex".
# Entspricht "-mplex=".
mplex=mplex

# Rippen mit Kapitelunterteilung?
# Moegliche Werte: 0=nein, 1=ja, per lxdvdrip, 2=ja, per tcprobe
# Entspricht "-chap="
chapter=1

# Sound nach Rippen und Brennen.
# 1=an, 0=aus.
playsound=1

# Ueberpruefe freien Platz vorm Rippen.
# Moegliche Werte: 0=nein, 1=ja
# Entspricht "-free="
free=1

# Brenngeschwindigkeit fuer growisofs als auch cdrecord-prodvd.
# Bei speed=0 wird der Parameter beim Brennen nicht uebergeben.
speed=4

# Extra-Parameter fuer growisofs.
# Bei dvdcompat=1 wird "growisofs -dvd-compat" gestartet.
# Beschreibung siehe "man growisofs".
dvdcompat=1

# Extra-Parameter fuer mkisofs.
# Parameter muss in Hochkommas stehen, z. B. 
# mkisofs_param="-input-charset iso8859-1"
# Parameter werden beim Aufruf an mkisofs bzw. growisofs uebergeben.
mkisofs_param=""

# Extra-Parameter fuer cdrecord-prodvd/growisofs.
# Parameter muss in Hochkommas stehen, z. B. 
# burn_param="-tao"
# Parameter werden beim Aufruf an cdrecord-prodvd bzw. growisofs uebergeben.
burn_param=""

# Besondere Parameter fuer cdrecord-prodvd.
# Werden bei growisofs nicht benoetigt.
# Den Key fuer cdrecord-prodvd gibt es auf der Homepage, Adresse siehe README.
burnkey=CDR_SECURITY=key_von_homepage_eintragen

# DVD nach Rippen auswerfen.
# Optionen: 0: nicht auswerfen, 1:auswerfen
eject=1

# DVD RW formatieren vor dem Brennen
# Optionen: 0=nein, 1=ja
rw-format=1

# Name der verwendeten Programme, jeweils "Programm=Programmdateiname".
# Wahlweise kann ein Programm mit vollem Pfad angegeben werden,
# z. B. "dvdauthor=/usr/local/bin/dvdauthor", damit koennen z. B.
# mehrere Versionen parallel auf dem Rechner liegen.
dvdauthor_name=dvdauthor
buffer_name=buffer
#buffer_name=bfr
#buffer_name=mbuffer
tccat_name=tccat
tcextract_name=tcextract
tcrequant_name=tcrequant
mplayer_name=mplayer
mplex_name=mplex
tcmplex_name=tcmplex
spumux_name=spumux
spuunmux_name=spuunmux
dvdbackup_name=dvdbackup_lxdvdrip
# Alternative: dvdbackup_name=vobcopy
mkisofs_name=mkisofs
cdrecord_prodvd_name=cdrecord-prodvd
growisofs_name=growisofs
dvd+rw-format=dvd+rw-format
dvdunauthor_name=dvdunauthor
tcprobe_name=tcprobe
play_cell_name=play_cell_lxdvdrip
vamps_name=vamps_lxdvdrip
eject_name=eject
mpgtx_name=mpgtx
transcode_name=transcode
lxac3scan_name=lxac3scan

# Einstellungen zu dvdwizard.
# Mit dvdwizard kann eine DVD mit einem Menue erzeugt werden.
# "dvdwizard=":       1=eingeschaltet, 0=aus.
# "dvdwizard_name=":  Programmname inkl. Pfad
# "dvdwizard_bild1=": Bilddatei (jpeg, png) als Hintergrund fuer VMGM-Menue (Hauptmenue)
# "dvdwizard_bild2=": Bilddatei (jpeg, png) als Hintergrund fuer VTSM-Menue (Kapitelmenue)
dvdwizard=0
dvdwizard_name=dvdwizard
dvdwizard_bild1=/usr/share/pixmaps/penguin.jpg
dvdwizard_bild2=/usr/share/pixmaps/penguin.jpg

```

---

