---
title: "[SOLVED] Streamtuner"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-08
I'm trying to play some streams in this, and every time i try i get the following error:

```

Unable to tune in

Failed to execute child process
"xmms"(no such file or directory)

```

---

### Post by ibuclaw on 2008-07-08
what does this command output?
```
which xmms
```

Regards
Iain

---

### Post by adobrakic on 2008-07-08
nothing, this just happens:

```

ado@ado-desktop:~$ which xmms
ado@ado-desktop:~$ 

```

---

### Post by avtolle on 2008-07-08
If you are using 8.04, xmms no longer is offered in the repositories. If using a release prior to 8.04, you may install xmms from the repositories by Synaptic.

EDIT: Forgot this part; if running 8.04, it is possible to compile xmms from source. There are some threads on the forum about xmms, and perhaps a search will give you what you need.

---

### Post by adobrakic on 2008-07-08
I'm using 8.04 :/
is there a website that i can get it from or something?

--edit--

I've found the site, but i got the result I was hoping not to run into.
The file comes as a tar.gz, and I have absolutely no idea what to do with those.
:/

---

### Post by ibuclaw on 2008-07-08
xmms2 is in the repositories.

```
sudo apt-get install xmms2 xmms2-plugin-all
```

Then in streamtuner, go into **Edit>Preferences** and under "Applications", change all "xmms %q" lines to "**xmms2 %q**"

There also appears to be a line with "realplay" in too...
That may need replacing with a mediaplayer that can handle rm files, or you'll need to install realplay.

[EDIT]
Check out the [Complete Streaming Thread.]("http://ubuntuforums.org/showthread.php?t=766683")
It has all the info and more on how to get your PC setup for streaming audio.

Regards
Iain

---

### Post by nufros on 2008-07-26
Hey Iain, I was having the same problem as adobrakic so I entered your code and this happened:
 
user@user-desktop:~$ sudo apt-get install xmms2 xmms2-plugin-all 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libxine1-misc-plugins libxcb-xv0 libxine1-bin ruby1.8 ruby
  libxine1-ffmpeg libxcb-shape0 libtunepimp5 libifp4 libxine1-plugins libxvmc1
  libpq5 libruby1.8 libxcb-shm0 libnjb5 libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdiscid0 libresid-builder0c2a libsidplay2 libxmmsclient-glib1
  libxmmsclient2 xmms2-client-cli xmms2-core xmms2-plugin-alsa xmms2-plugin-ao
  xmms2-plugin-asx xmms2-plugin-avcodec xmms2-plugin-avformat
  xmms2-plugin-cdda xmms2-plugin-cue xmms2-plugin-curl xmms2-plugin-daap
  xmms2-plugin-flac xmms2-plugin-gnomevfs xmms2-plugin-ices
  xmms2-plugin-icymetaint xmms2-plugin-id3v2 xmms2-plugin-jack
  xmms2-plugin-lastfm xmms2-plugin-m3u xmms2-plugin-mad xmms2-plugin-mms
  xmms2-plugin-modplug xmms2-plugin-mp4 xmms2-plugin-musepack xmms2-plugin-ofa
  xmms2-plugin-oss xmms2-plugin-pls xmms2-plugin-rss xmms2-plugin-sid
  xmms2-plugin-smb xmms2-plugin-vocoder xmms2-plugin-vorbis xmms2-plugin-wma
  xmms2-plugin-xml xmms2-plugin-xspf
The following NEW packages will be installed:
  libdiscid0 libresid-builder0c2a libsidplay2 libxmmsclient-glib1
  libxmmsclient2 xmms2 xmms2-client-cli xmms2-core xmms2-plugin-all
  xmms2-plugin-alsa xmms2-plugin-ao xmms2-plugin-asx xmms2-plugin-avcodec
  xmms2-plugin-avformat xmms2-plugin-cdda xmms2-plugin-cue xmms2-plugin-curl
  xmms2-plugin-daap xmms2-plugin-flac xmms2-plugin-gnomevfs xmms2-plugin-ices
  xmms2-plugin-icymetaint xmms2-plugin-id3v2 xmms2-plugin-jack
  xmms2-plugin-lastfm xmms2-plugin-m3u xmms2-plugin-mad xmms2-plugin-mms
  xmms2-plugin-modplug xmms2-plugin-mp4 xmms2-plugin-musepack xmms2-plugin-ofa
  xmms2-plugin-oss xmms2-plugin-pls xmms2-plugin-rss xmms2-plugin-sid
  xmms2-plugin-smb xmms2-plugin-vocoder xmms2-plugin-vorbis xmms2-plugin-wma
  xmms2-plugin-xml xmms2-plugin-xspf
0 upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
Need to get 1495kB of archives.
After this operation, 4465kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libdiscid0 0.1.0-1 [10.9kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libresid-builder0c2a 2.1.1-6 [38.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libsidplay2 2.1.1-6 [111kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libxmmsclient2 0.2DrJekyll-4ubuntu4 [42.5kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libxmmsclient-glib1 0.2DrJekyll-4ubuntu4 [9352B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-client-cli 0.2DrJekyll-4ubuntu4 [33.1kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-core 0.2DrJekyll-4ubuntu4 [825kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-alsa 0.2DrJekyll-4ubuntu4 [13.7kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-id3v2 0.2DrJekyll-4ubuntu4 [14.2kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-mad 0.2DrJekyll-4ubuntu4 [15.7kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-vorbis 0.2DrJekyll-4ubuntu4 [11.8kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2 0.2DrJekyll-4ubuntu4 [10.8kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-ao 0.2DrJekyll-4ubuntu4 [10.8kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-asx 0.2DrJekyll-4ubuntu4 [9222B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-avcodec 0.2DrJekyll-4ubuntu4 [11.0kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-avformat 0.2DrJekyll-4ubuntu4 [12.8kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-cdda 0.2DrJekyll-4ubuntu4 [11.9kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-cue 0.2DrJekyll-4ubuntu4 [10.4kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-curl 0.2DrJekyll-4ubuntu4 [12.4kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-daap 0.2DrJekyll-4ubuntu4 [22.5kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-flac 0.2DrJekyll-4ubuntu4 [12.8kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-gnomevfs 0.2DrJekyll-4ubuntu4 [10.0kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-ices 0.2DrJekyll-4ubuntu4 [13.5kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-icymetaint 0.2DrJekyll-4ubuntu4 [9876B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-jack 0.2DrJekyll-4ubuntu4 [13.3kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-lastfm 0.2DrJekyll-4ubuntu4 [13.0kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-m3u 0.2DrJekyll-4ubuntu4 [9098B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-mms 0.2DrJekyll-4ubuntu4 [9346B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-modplug 0.2DrJekyll-4ubuntu4 [10.1kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-mp4 0.2DrJekyll-4ubuntu4 [28.6kB]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-musepack 0.2DrJekyll-4ubuntu4 [13.1kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-ofa 0.2DrJekyll-4ubuntu4 [10.1kB]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-oss 0.2DrJekyll-4ubuntu4 [10.5kB]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-pls 0.2DrJekyll-4ubuntu4 [9578B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-xml 0.2DrJekyll-4ubuntu4 [9436B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-rss 0.2DrJekyll-4ubuntu4 [9664B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-sid 0.2DrJekyll-4ubuntu4 [16.6kB]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-smb 0.2DrJekyll-4ubuntu4 [10.1kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-vocoder 0.2DrJekyll-4ubuntu4 [13.8kB]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-wma 0.2DrJekyll-4ubuntu4 [6734B]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-xspf 0.2DrJekyll-4ubuntu4 [10.8kB]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xmms2-plugin-all 0.2DrJekyll-4ubuntu4 [6778B]
Fetched 1495kB in 3s (391kB/s)          
Extracting templates from packages: 100%
Selecting previously deselected package libdiscid0.
(Reading database ... 131140 files and directories currently installed.)
Unpacking libdiscid0 (from .../libdiscid0_0.1.0-1_i386.deb) ...
Selecting previously deselected package libresid-builder0c2a.
Unpacking libresid-builder0c2a (from .../libresid-builder0c2a_2.1.1-6_i386.deb) ...
Selecting previously deselected package libsidplay2.
Unpacking libsidplay2 (from .../libsidplay2_2.1.1-6_i386.deb) ...
Selecting previously deselected package libxmmsclient2.
Unpacking libxmmsclient2 (from .../libxmmsclient2_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package libxmmsclient-glib1.
Unpacking libxmmsclient-glib1 (from .../libxmmsclient-glib1_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-client-cli.
Unpacking xmms2-client-cli (from .../xmms2-client-cli_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-core.
Unpacking xmms2-core (from .../xmms2-core_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-alsa.
Unpacking xmms2-plugin-alsa (from .../xmms2-plugin-alsa_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-id3v2.
Unpacking xmms2-plugin-id3v2 (from .../xmms2-plugin-id3v2_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-mad.
Unpacking xmms2-plugin-mad (from .../xmms2-plugin-mad_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-vorbis.
Unpacking xmms2-plugin-vorbis (from .../xmms2-plugin-vorbis_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2.
Unpacking xmms2 (from .../xmms2_0.2DrJekyll-4ubuntu4_all.deb) ...
Selecting previously deselected package xmms2-plugin-ao.
Unpacking xmms2-plugin-ao (from .../xmms2-plugin-ao_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-asx.
Unpacking xmms2-plugin-asx (from .../xmms2-plugin-asx_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-avcodec.
Unpacking xmms2-plugin-avcodec (from .../xmms2-plugin-avcodec_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-avformat.
Unpacking xmms2-plugin-avformat (from .../xmms2-plugin-avformat_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-cdda.
Unpacking xmms2-plugin-cdda (from .../xmms2-plugin-cdda_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-cue.
Unpacking xmms2-plugin-cue (from .../xmms2-plugin-cue_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-curl.
Unpacking xmms2-plugin-curl (from .../xmms2-plugin-curl_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-daap.
Unpacking xmms2-plugin-daap (from .../xmms2-plugin-daap_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-flac.
Unpacking xmms2-plugin-flac (from .../xmms2-plugin-flac_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-gnomevfs.
Unpacking xmms2-plugin-gnomevfs (from .../xmms2-plugin-gnomevfs_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-ices.
Unpacking xmms2-plugin-ices (from .../xmms2-plugin-ices_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-icymetaint.
Unpacking xmms2-plugin-icymetaint (from .../xmms2-plugin-icymetaint_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-jack.
Unpacking xmms2-plugin-jack (from .../xmms2-plugin-jack_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-lastfm.
Unpacking xmms2-plugin-lastfm (from .../xmms2-plugin-lastfm_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-m3u.
Unpacking xmms2-plugin-m3u (from .../xmms2-plugin-m3u_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-mms.
Unpacking xmms2-plugin-mms (from .../xmms2-plugin-mms_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-modplug.
Unpacking xmms2-plugin-modplug (from .../xmms2-plugin-modplug_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-mp4.
Unpacking xmms2-plugin-mp4 (from .../xmms2-plugin-mp4_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-musepack.
Unpacking xmms2-plugin-musepack (from .../xmms2-plugin-musepack_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-ofa.
Unpacking xmms2-plugin-ofa (from .../xmms2-plugin-ofa_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-oss.
Unpacking xmms2-plugin-oss (from .../xmms2-plugin-oss_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-pls.
Unpacking xmms2-plugin-pls (from .../xmms2-plugin-pls_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-xml.
Unpacking xmms2-plugin-xml (from .../xmms2-plugin-xml_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-rss.
Unpacking xmms2-plugin-rss (from .../xmms2-plugin-rss_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-sid.
Unpacking xmms2-plugin-sid (from .../xmms2-plugin-sid_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-smb.
Unpacking xmms2-plugin-smb (from .../xmms2-plugin-smb_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-vocoder.
Unpacking xmms2-plugin-vocoder (from .../xmms2-plugin-vocoder_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-wma.
Unpacking xmms2-plugin-wma (from .../xmms2-plugin-wma_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-xspf.
Unpacking xmms2-plugin-xspf (from .../xmms2-plugin-xspf_0.2DrJekyll-4ubuntu4_i386.deb) ...
Selecting previously deselected package xmms2-plugin-all.
Unpacking xmms2-plugin-all (from .../xmms2-plugin-all_0.2DrJekyll-4ubuntu4_all.deb) ...
Setting up libdiscid0 (0.1.0-1) ...

Setting up libresid-builder0c2a (2.1.1-6) ...

Setting up libsidplay2 (2.1.1-6) ...

Setting up libxmmsclient2 (0.2DrJekyll-4ubuntu4) ...

Setting up libxmmsclient-glib1 (0.2DrJekyll-4ubuntu4) ...

Setting up xmms2-client-cli (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-core (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-alsa (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-id3v2 (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-mad (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-vorbis (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2 (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-ao (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-asx (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-avcodec (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-avformat (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-cdda (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-cue (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-curl (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-daap (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-flac (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-gnomevfs (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-ices (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-icymetaint (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-jack (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-lastfm (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-m3u (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-mms (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-modplug (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-mp4 (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-musepack (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-ofa (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-oss (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-pls (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-xml (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-rss (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-sid (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-smb (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-vocoder (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-wma (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-xspf (0.2DrJekyll-4ubuntu4) ...
Setting up xmms2-plugin-all (0.2DrJekyll-4ubuntu4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
user@user-desktop:~$ 


I then made the changes you suggested to Edit>Preferences... now I don't get the error dialogue anymore, but nothing happens (ie: it doesn't connect to any streams)

...any suggestions on what might be causing that, or how to make it better?

Thanks,
Aaron

---

### Post by cariboo on 2008-07-26
After all you went through that  in your post just above, may I suggest installing audacious then got Edit-->Preferences and change the xmms %q to audacious %q as in the attached screen shot.

Jim

---

### Post by nufros on 2008-07-26
Thanks that helped!

---

### Post by markbuntu on 2008-07-26
If you still want xmms, you can get it here:


[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

---

### Post by Levitation on 2008-08-09
> **tinivole said:**
> xmms2 is in the repositories.

```
sudo apt-get install xmms2 xmms2-plugin-all
```

Then in streamtuner, go into **Edit>Preferences** and under "Applications", change all "xmms %q" lines to "**xmms2 %q**"

There also appears to be a line with "realplay" in too...
That may need replacing with a mediaplayer that can handle rm files, or you'll need to install realplay.

[EDIT]
Check out the [Complete Streaming Thread.]("http://ubuntuforums.org/showthread.php?t=766683")
It has all the info and more on how to get your PC setup for streaming audio.

Regards
Iain

Hey there Iain,
When I changed the xmms to xmms2, still would not play stream (no error message...just silence). Then after closing and reopening Streamtuner, it was xmms again. 

Any ideas?

Thanks, 
Doug

---

### Post by markbuntu on 2008-08-09
Streamtuner is very picky about how you change those things. You need to hit enter after making the change while the little cursor is in the box after the %q.

---

### Post by Levitation on 2008-08-10
> **markbuntu said:**
> Streamtuner is very picky about how you change those things. You need to hit enter after making the change while the little cursor is in the box after the %q.
Yes, I did that and it does keep the change, however, I am still not getting anything playing. What happens when I select a station and press "tune in" is that the "stop" icon flashes briefly... and nothing. Am I missing something? Is Streamtuner self contained or does it work in conjunction with another media player? I should mention that my OS is Hardy 64 bit.

Cheers

---

### Post by markbuntu on 2008-08-10
Oh, 64 bit. I never got streamtuner to work with anything but xmms in my 64 bit install and I seem to remeber some problem with xmms2 crashing on startup. I installed xmms in  a somewhat confusing manner due to some weird missing deps problem that I can't remember how I got around. I just remeber thinking wow, that was weird, after I got it working.

You can try to use audacious, it might work now, a few months ago it was starting up and then crashing, but it was doing a lot of that back then and appears more stable now.

You could also get tunapie which is very similar to streamtuner and works with rythmbox and/or audaciuos.

---

### Post by Levitation on 2008-08-13
Thanks for your help:
I tried Tunapie and while it does play, it does not record (I do have streamripper)... do you think that could be a 64 bit issue?

I'll check out audacious next. 

BTW do you still have a 64-bit OS? I just installed Hardy 8.04 and so far the only issues are minor...

---

### Post by markbuntu on 2008-08-13
You can try streamripper for that. I think it is in the 64 repos.

I have 64 which I just changed to ubuntustudio to use the rt kernel and i386generic and i386ubuntustudio which I could not get working with the rt kernel, some amd processor problem I hear. I use all three and switch between them every few days. Right now I am on my i386 generic but all weekend I was on my 64 bit. The 64 seems faster and better for audio work. Far less cpu loading and much better processing with a working rt kernel

I had a lot of problems with 64 when it came out but things have gotten far better, it seems extremely stable now.

---

