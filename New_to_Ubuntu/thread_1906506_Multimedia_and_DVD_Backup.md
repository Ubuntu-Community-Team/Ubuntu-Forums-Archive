---
title: "Multimedia and DVD Backup"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by DGINSD on 2012-01-09
It's the last bastion of windows dominance in my house, so I went to work on it yesterday. The windows programs I use are  DVD Shrink and DVDfab, so the Ubuntu equivalent are DVD95 and K9Copy with K3B. I started with DVD95 it started the backup and all seemed to go well but when it started K3B to burn a message popped up saying there was a problem loading the files into the project, so I checked with my file browser and sure enough no DVD files no title folder no VideoTS folder, I've messed with the settings trying various combinations but nothing seems to change this. DVD95 will however produce an iso. file which K3B will burn to disc just fine  which leads me to believe I have all the codec's and all I need (I followed the guide in the multimedia section of the forum). There is one setting I didn't understand and  couldn't find info on, that was "trace level" I read in one post it should be set to "*" but with no explanation, could this be my issue? I'd love to get DVD95 working 100%.

K9Copy seemed to work right off the bat I only mention it because I've had issues with it in the past but K9Copy produced a title directory and a VideoTS directory as DVD95 is supposed to do. I'm short on time so I'll cut it shot there snd get back to it later but if any one has any insight into why DVD95 isn't working correctly I'd really appreciate it.

---

### Post by DGINSD on 2012-01-09
I forgot one of the biggest issues, Brasero the defaulf burning app tries to open up but shuts down before a window can even open, whats that about?

---

### Post by DGINSD on 2012-03-19
When I started this thread I was using my old (ancient really) laptop now I'm using my new one I got exactly one back up made and every one after that one has failed.

On my new machine both DVD95 and K9 copy will make the back up file and all looks normal a couple of BUP and IFO files and five VOB files.

If I burn these to disc it burns fine all the files are on the disc, they will play on both Ubuntu and Windows but not on my Bluray player. I tested the discs by making a few backups on windows and all was fine. I even tried using my outboard burner in Ubuntu which had the same result (unplayable discs).

I got a disc to play by dropping VOB files into Devede and having it make an ISO and burning it to disc, this however leaves the audio and video out of sync. This is a step that I tried 
after searching for solutions and really shouldn't be nessessary.

I bought some DVD+RWs so I can experiment a bit without going through a ton of discs (I've already gone through about 10 or so regular +R's) I'm sure it's something simple I'm missing or am unaware of?

Any and all help is greatly appreciated I'm really trying very hard to make my house a Linux only zone but this one area is a big hang up.

---

### Post by DGINSD on 2012-03-20
K I just tried to open K9 copy without K9 copy assistant and open a disc with it and it crashed and gave me this developer information when asking me if I wanted to file a bug.

```
Application: k9copy (k9copy), signal: Segmentation fault
[Current thread is 1 (Thread 0x7ff60cbd2780 (LWP 23190))]

Thread 3 (Thread 0x7ff5f37ed700 (LWP 23193)):
#0  0x00007ff607975473 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ff601497f68 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007ff601498792 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007ff5fa3c5516 in ?? () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#4  0x00007ff6014bd2b6 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007ff605615efc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#6  0x00007ff60798159d in clone () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7ff5e9a46700 (LWP 23194)):
#0  0x00007ff60798f88e in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ff60791e62f in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#2  0x00007ff60791c9c1 in free () from /lib/x86_64-linux-gnu/libc.so.6
#3  0x00007ff608bfb665 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#4  0x00007ff601497734 in g_main_context_check () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007ff601497f82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#6  0x00007ff601498429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#7  0x00007ff608bfbed6 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#8  0x00007ff608bcfcf2 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007ff608bcfef7 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#10 0x00007ff608ae727f in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#11 0x00007ff608bb2cbf in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#12 0x00007ff608ae9d05 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#13 0x00007ff605615efc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#14 0x00007ff60798159d in clone () from /lib/x86_64-linux-gnu/libc.so.6
#15 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7ff60cbd2780 (LWP 23190)):
[KCrash Handler]
#6  0x00007ff60791a039 in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x00007ff60791c3cd in malloc () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x00000000004bf3d2 in ___ifoRead_VTS_PTT_SRPT ()
#9  0x00000000004c181c in ?? ()
#10 0x00000000004c19a2 in ___ifoOpen ()
#11 0x00000000004a1151 in ?? ()
#12 0x000000000049c3cf in ?? ()
#13 0x00000000004959dd in ?? ()
#14 0x00000000004539b3 in ?? ()
#15 0x00000000004250cc in _start ()

```

Hopefully this helps, this thread has a lot of views so I'm assuming theres a lot of people with a similar issue.

---

### Post by DGINSD on 2012-05-13
I think I got my issue in K9 fixed, I started messing around with the configuration. I also forgot to mention the backups I'm trying to make, I want to be feature and main audio/subtitle only. So heres a screen shot of the config that finally worked.

[[img]http://s19.postimage.org/ro7ft44pf/Screenshot_from_2012_05_13_08_48_20.png[/img]](http://postimage.org/)
[hosting images](http://postimage.org/)

The only thing I think I changed from default was to untick the "use dvdAuthor for copy without menus" after this the program is working good so far.

So this would lead me to believe there is an issue with dvdAuthor so I did a bit of research on this and found the config file for this program is /usr/share/dvdauthor/dvdauthor.xsd so looking through this file I noticed a few things

```
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">

  <xsd:annotation>
    <xsd:documentation xml:lang="en">
     XML Schema Definition for dvdauthor.
     Author: Alan Canon (acanon@bellsouth.net)
     Date: Jan 8 2005
     This Schema is made available under the terms of the GNU GPL.
     See http://www.gnu.org/ for details.
     // TODO Copy the dvdauthor man page documentation as xsd:annotations to the below.
    </xsd:documentation>
  </xsd:annotation>

  <xsd:element name="dvdauthor" type="DvdauthorType"/>

  <xsd:complexType name="DvdauthorType">
    <xsd:sequence>
      <xsd:element name="vmgm" type="VmgmType" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="titleset" type="TitlesetType" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
    <xsd:attribute name="dest" type="xsd:string"/>
    <xsd:attribute name="jumppad" type="xsd:string"/>
  </xsd:complexType>

  <xsd:complexType name="VmgmType">
    <xsd:sequence>
      <xsd:element name="menus" type="MenusType" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name="TitlesetType">
    <xsd:complexContent>
      <xsd:extension base="VmgmType">
        <xsd:sequence>
          <xsd:element name="titles" type="TitlesType" minOccurs="0" maxOccurs="1"/>
        </xsd:sequence>
      </xsd:extension>
    </xsd:complexContent>
  </xsd:complexType>

  <xsd:complexType name="TitlesType">
    <xsd:sequence>
      <xsd:element name="video" type="VideoType" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="audio" type="AudioType" minOccurs="0" maxOccurs="8"/>
      <xsd:element name="subpicture" type="SubpictureType" minOccurs="0" maxOccurs="32"/>
      <xsd:element name="pgc" type="PgcType" minOccurs="0" maxOccurs="unbounded"/>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name="MenusType">
    <xsd:complexContent>
      <xsd:extension base="TitlesType">
        <xsd:attribute name="lang" type="xsd:string"/> 
      </xsd:extension>
    </xsd:complexContent>
  </xsd:complexType>

  <xsd:complexType name="VideoType">
    <xsd:attribute name="format" type="VideoFormatType"/>
    <xsd:attribute name="aspect" type="VideoAspectType"/>
    <!-- XxY -->
    <xsd:attribute name="resolution" type="xsd:string"/>
    <xsd:attribute name="caption" type="VideoCaptionType"/>

    <xsd:attribute name="widescreen" type="VideoWidescreenType"/>
  </xsd:complexType>

  <xsd:simpleType name="VideoFormatType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="ntsc"/>
      <xsd:enumeration value="pal"/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:simpleType name="VideoAspectType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="4:3"/>
      <xsd:enumeration value="16:9"/>
    </xsd:restriction>
  </xsd:simpleType>
  
  <xsd:simpleType name="VideoCaptionType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="field1"/>
      <xsd:enumeration value="field2"/>
    </xsd:restriction>
  </xsd:simpleType>
  

  <xsd:simpleType name="VideoWidescreenType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="nopanscan"/>
      <xsd:enumeration value="noletterbox"/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:complexType name="AudioType">
    <xsd:attribute name="format" type="AudioFormatType"/>
    <xsd:attribute name="channels" type="xsd:integer"/>
    <xsd:attribute name="dolby" type="AudioDolbyType"/>
    <xsd:attribute name="quant" type="AudioQuantType"/> 
    <xsd:attribute name="samplerate" type="AudioSamplerateType"/> 
    <xsd:attribute name="lang" type="xsd:string"/> 
  </xsd:complexType>

  <xsd:simpleType name="AudioSamplerateType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="48khz"/>
      <xsd:enumeration value="96khz"/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:simpleType name="AudioDolbyType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="surround"/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:simpleType name="AudioFormatType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="mp2"/>
      <xsd:enumeration value="ac3"/>
      <xsd:enumeration value="dts"/>
      <xsd:enumeration value="pcm"/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:simpleType name="AudioQuantType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="16bps"/>
      <xsd:enumeration value="20bps"/>
      <xsd:enumeration value="24bps"/>
      <xsd:enumeration value="drc"/>
    </xsd:restriction>
  </xsd:simpleType>
  
  <xsd:simpleType name="PgcEntryType">
    <xsd:restriction base="xsd:string">
      <xsd:enumeration value="title"/>
      <xsd:enumeration value="root"/>
      <xsd:enumeration value="subtitle"/>
      <xsd:enumeration value="audio"/>
      <xsd:enumeration value="angle"/>
      <xsd:enumeration value="ptt"/>
    </xsd:restriction>
  </xsd:simpleType>
  
  <xsd:complexType name="PgcType">
    <xsd:sequence>
      <xsd:element name="pre" type="xsd:string" minOccurs="0" maxOccurs="1"/>
      <xsd:element name="vob" type="VobType" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="button" type="ButtonType" minOccurs="0" maxOccurs="unbounded"/>
      <xsd:element name="post" type="xsd:string" minOccurs="0" maxOccurs="1"/>
    </xsd:sequence> 
    <xsd:attribute name="palette" type="xsd:string"/>
    <xsd:attribute name="pause" type="PauseType"/> 
    <xsd:attribute name="entry" type="PgcEntryType"/>
  </xsd:complexType>

  <xsd:simpleType name="PauseType">
    <xsd:annotation>
      <xsd:documentation>for pgc {entry} attibute</xsd:documentation>
    </xsd:annotation>
    <xsd:union>
      <xsd:simpleType>
        <xsd:restriction base="xsd:integer">
          <xsd:minInclusive value="1"/>
          <xsd:maxInclusive value="254"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType>
        <xsd:restriction base="xsd:NMTOKEN">
          <xsd:enumeration value="inf"/>
        </xsd:restriction>
      </xsd:simpleType>
    </xsd:union>
  </xsd:simpleType>

  <xsd:complexType name="ButtonType">
	<xsd:simpleContent>
      <xsd:extension base="xsd:string">
        <xsd:attribute name="name" type="xsd:string"/>
      </xsd:extension>
    </xsd:simpleContent>    
  </xsd:complexType>

  <xsd:complexType name="SubpictureType">
    <xsd:attribute name="lang" type="xsd:string"/>
  </xsd:complexType>

  <xsd:complexType name="VobType">
    <xsd:attribute name="file" type="xsd:string"/>
    <xsd:attribute name="chapters" type="xsd:string"/>
    <xsd:attribute name="pause" type="PauseType"/>
  </xsd:complexType>
  
</xsd:schema>
```

In the section marked <xsd:complexType name="VideoType"> there's a faded line reading <!-- XxY --> its the only one of this type in the whole document, secondly theres a line in the section <xsd:simpleType name="VideoFormatType"> containing the line <xsd:enumeration value="pal"/> all my dvds being region 1 and playing on NTSC equipment this line would seen quite useless to me. My real question is how can I have this file rewritten to work properly for my set up/needs can I just edit out those sections I find that conflict? Google has produced few useful results in fact most of the info I got on this file came from "man dvdauthor". Just seems odd the creator of K9 would include an option that would cause unplayable discs so I assume theres something wrong with my dvdauthor configuration.

As for DVD95 as long as I select for it to output a .iso file, and leave the default output directories at their defaults it works fine, this did not work before because for some reason my system was set to hide files in the desktop directory from showing up in the physical desktop, so the program was producing the .iso but I couldn't see it, I had to go to the actual directory. For some reason this program doesn't like having it's defaults changed.

Since having these issues I have experimented with some other programs, I got dvdshrink and dvdfab working in wine the main problem with those was I needed to add an line to fstab to permanatly mount my dvd drive to /media/cdrom and then obviously add the cdrom directory in the media one. The best bennifit of this experimentation was the discovery of xdvdshrink it can be found for download here. 

[http://linuxappfinder.com/package/xdvdshrink]("http://linuxappfinder.com/package/xdvdshrink")

This program is a little hard to use as it doesn't list your selection items nice and neat like K9 or some of the other programs, the subtitles for whatever reason don't seem to work, and there's no progress bar so you just have to have faith it's doing what it's suppose to. However xdvdshrink will succeed where all others fail, dvds with encryption that crashes even the best and up to date windows programs seem to present no problem for xdvdshrink. If it were a little clearer to use and could grab subtitles it could be a one stop for all your back up needs.

Anyway hope this helps out someone else, it's been one of my biggest gripes with Linux/Ubuntu since I started using it at 10.10. If someone has a fix or a work around for either dvdAuthor or xdvdshrink I'd love to hear it. I'm open to experimenting and would love to get everything working 100% correctly.

---

