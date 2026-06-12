---
title: "problems playing wav files in Guayadeque with Ubuntu 12.10"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by chirs p on 2012-10-21
Hi
I am brand-new to Ubuntu; I have always used Windows.  I decided to try Ubuntu and downloaded 12.10 (63-bit) alongside Windows 7.  Since I have no clue how to manually install things, I installed Guayadeque from Ubuntu software "store" (can't remember name; it looks like iTunes) to play my audio files and set up my library.  Library set up just fine, found all albums, regardless of format of audio files.  However, whenever I try to play a .wav file, I get the following error: "Gstreamer error; could not determine type of stream".  Can anyone explain (in really simple (linux-idiot) language) how I can fix this issue?  Rhythmbox plays all files fine, but doesn't recognize about half of my albums as "albums", they simply got tagged onto the end in a list of unknown files, so I'd like to use Guayadeque if possible.
Thanks so much
Chris

---

### Post by westie457 on 2012-10-21
Welcome

Install 'ubuntu-restricted-extras'. Available in the Software Centre

---

### Post by chirs p on 2012-10-21
Hi Westie
Thanks so much.  When I click on "install", it gives me a warning message saying "to install this you must remove:
libav codec library
libav codec 53
Libav utility library
libav util 51
What does this mean, and how do I do this?  Can I just click "install anyway" (I'm guessing this is not a good idea)?
Thanks so much for your help
Chris

---

### Post by westie457 on 2012-10-22
Go ahead and install. Without that package you will not be able to play the .wmv files or .mp3 files. Also you will get replacements for those that get removed.

---

### Post by chirs p on 2012-10-23
Hi Westie
Still no luck after install of package.  Removed Guayadeque and installed from terminal using:
sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque
everything works on new install, except .wav files.  Still get same gstreamer error.
Do you have any other suggestions?
Thanks so much
Chris

---

### Post by anonbeat on 2012-10-24
> **chirs p said:**
> Hi Westie
Still no luck after install of package.  Removed Guayadeque and installed from terminal using:
sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque
everything works on new install, except .wav files.  Still get same gstreamer error.
Do you have any other suggestions?
Thanks so much
Chris

Try with this

```

sudo apt-get install gstreamer0.10-plugins-good
sudo apt-get install gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-nice
sudo apt-get install gstreamer0.10-ffmpeg
sudo apt-get install gstreamer0.10-gnonlin

```

Regards

---

### Post by chirs p on 2012-10-24
Hi Anonbeat,
Thanks so much.  All but the last line returned a message in terminal saying the version I had was already the newest version.  After installing the last code, I'm more confused because some .wav files now play in Guayadeque, but others still return the gstreamer error.  Do you have any further suggestions?  I know the files are fine because they open in Rhythmbox and Audacity (and in J River in Windows), and they play without problems in the linux-based Auraliti music player in my stereo system.  Do you have any other thoughts/suggestions as to how I can get the files to play?
Thanks so much
Chris

---

### Post by anonbeat on 2012-10-25
> **chirs p said:**
> Hi Anonbeat,
Thanks so much.  All but the last line returned a message in terminal saying the version I had was already the newest version.  After installing the last code, I'm more confused because some .wav files now play in Guayadeque, but others still return the gstreamer error.  Do you have any further suggestions?  I know the files are fine because they open in Rhythmbox and Audacity (and in J River in Windows), and they play without problems in the linux-based Auraliti music player in my stereo system.  Do you have any other thoughts/suggestions as to how I can get the files to play?
Thanks so much
Chris

Can you run guayadeque from console and send me the output from the console while trying to play one of this files ?
Also can you email me one or two files so I can check if the wav are encoded and how ? email it to anonbeat at gmail dot com

Regards

---

### Post by chirs p on 2012-10-26
Hi anonbeat,
Thanks so much.  Being a complete newbie, I'm not sure how to "run guayadeque from console and send the output from the console while trying to play one of these files". Could you walk me through what I would need to type in terminal to run Guayadeque and how I can copy the output text to send it to you?
Thanks so much again
Chris

---

### Post by anonbeat on 2012-10-26
> **chirs p said:**
> Hi anonbeat,
Thanks so much.  Being a complete newbie, I'm not sure how to "run guayadeque from console and send the output from the console while trying to play one of these files". Could you walk me through what I would need to type in terminal to run Guayadeque and how I can copy the output text to send it to you?
Thanks so much again
Chris

Start the console terminal from accesories. Once you are at the prompt of the console just type guayadeque and press enter. Guayadeque will start and try to play one of the files that fails.
Now come back to the console and select the text on the console and copy it.
Then post it here.

---

### Post by chirs p on 2012-10-26
[COLOR=#000000]Hi anonbeat,[/COLOR]
 [COLOR=#000000]here is what I got when I tried to open my library:[/COLOR]
 

 [COLOR=#000000](guayadeque:2667): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed [/COLOR]
 [COLOR=#000000]05:39:35 PM: guPrefDialog::OnLibCollectSelected( -1 ) [/COLOR]
 [COLOR=#000000]05:39:41 PM: OnCollectionCommand 13115  0 15  0 [/COLOR]
 [COLOR=#000000]05:39:41 PM: Doing Library Update in /media/chris/Western Digital/Hi-RES MUSIC/ [/COLOR]
 [COLOR=#000000]05:39:41 PM: Could not open the dir '/media/chris/Western Digital/Hi-RES MUSIC/' [/COLOR]
 [COLOR=#000000]05:39:58 PM: Destroying the volume monitor object... [/COLOR]
 [COLOR=#000000]05:39:58 PM: >> ~guGIO_VolumeMonitor() [/COLOR]
 [COLOR=#000000]05:39:58 PM: << ~guGIO_VolumeMonitor() [/COLOR]
 [COLOR=#000000] [/COLOR]
 [COLOR=#000000](guayadeque:2667): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent. [/COLOR]
 

 [COLOR=#000000]I then deleted the library, and then added it again; played one track that worked and then one of the ones that will not:[/COLOR]
 

 [COLOR=#000000]chris@chris-B75A-G43:~$ guayadeque [/COLOR]
 [COLOR=#000000]05:45:18 PM: Deleted stale lock file '/home/chris/.guayadeque/.guayadeque-chris'. [/COLOR]
 [COLOR=#000000]05:45:18 PM: Initialized locale ( en_US ) [/COLOR]
 [COLOR=#000000]05:45:18 PM: Mount Added... [/COLOR]
 [COLOR=#000000]05:45:18 PM: Mount Path: /media/chris/Western Digital/ [/COLOR]
 [COLOR=#000000]05:45:18 PM: IconStr: '. GThemedIcon drive-harddisk drive' [/COLOR]
 [COLOR=#000000]05:45:18 PM: MediaViewer 'My Music' => '5082BD90' ==>> 00000000 [/COLOR]
 [COLOR=#000000]05:45:18 PM: Library Db Version 21 [/COLOR]
 [COLOR=#000000]05:45:18 PM: SetViewMode -1 => 0 [/COLOR]
 [COLOR=#000000]05:45:18 PM: guLibPanel::IniPanelData( 13101 ) [/COLOR]
 [COLOR=#000000]05:45:18 PM: guLibPanel::DoTextSearch( '' ) [/COLOR]
 [COLOR=#000000]05:45:18 PM: Mount: 'Western Digital' => '/media/chris/Western Digital/' [/COLOR]
 [COLOR=#000000]05:45:18 PM: OnCollectionCommand 13100  0 0  1 [/COLOR]
 [COLOR=#000000]05:45:18 PM: Mount: 'Western Digital' => '/media/chris/Western Digital/' [/COLOR]
 [COLOR=#000000]05:45:19 PM: Volume Added... [/COLOR]
 [COLOR=#000000]05:45:19 PM: Volume Added... [/COLOR]
 [COLOR=#000000]05:45:19 PM: Volume Added... [/COLOR]
 [COLOR=#000000]05:45:19 PM: Volume Added... [/COLOR]
 [COLOR=#000000]05:45:19 PM: Volume Added... [/COLOR]
 [COLOR=#000000]05:45:19 PM: Mount Added... [/COLOR]
 [COLOR=#000000]05:45:19 PM: Mount already added? [/COLOR]
 [COLOR=#000000]05:45:19 PM: guMainFrame::OnVolumeMonitorUpdated [/COLOR]
 [COLOR=#000000] [/COLOR]
 [COLOR=#000000](guayadeque:3068): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed [/COLOR]
 [COLOR=#000000] [/COLOR]
 [COLOR=#000000](guayadeque:3068): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed [/COLOR]
 [COLOR=#000000] [/COLOR]
 [COLOR=#000000](guayadeque:3068): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed [/COLOR]
 [COLOR=#000000] [/COLOR]
 [COLOR=#000000](guayadeque:3068): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed [/COLOR]
 [COLOR=#000000] [/COLOR]
 [COLOR=#000000](guayadeque:3068): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed [/COLOR]
 [COLOR=#000000] [/COLOR]
 [COLOR=#000000](guayadeque:3068): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed [/COLOR]
 [COLOR=#000000]05:45:19 PM: Mount: 'Western Digital' => '/media/chris/Western Digital/' [/COLOR]
 [COLOR=#000000]05:45:19 PM: OnCollectionCommand 13114  0 14  0 [/COLOR]
 [COLOR=#000000]05:45:19 PM: Doing Library Update in /media/chris/Western Digital/Hi-RES MUSIC/ [/COLOR]
 [COLOR=#000000]05:45:19 PM: Updating the podcasts... [/COLOR]
 [COLOR=#000000]05:45:19 PM: playlist active 0 [/COLOR]
 [COLOR=#000000]05:45:28 PM: OnCollectionCommand 13115  0 15  0 [/COLOR]
 [COLOR=#000000]05:45:28 PM: Doing Library Update in /media/chris/Western Digital/Hi-RES MUSIC/ [/COLOR]
 [COLOR=#000000]05:47:21 PM: SetViewMode 0 => 1 [/COLOR]
 [COLOR=#000000]05:47:21 PM: Got 245 albums [/COLOR]
 [COLOR=#000000]05:47:21 PM: Got 245 albums [/COLOR]
 [COLOR=#000000]05:47:35 PM: TracksDClicked... [/COLOR]
 [COLOR=#000000]05:47:36 PM: OnMediaLoaded Cur: 0 1   2668324836 [/COLOR]
 [COLOR=#000000]05:47:36 PM: Track starts at 0 with length 217000 [/COLOR]
 [COLOR=#000000]05:47:36 PM: StatusChanged( 0, 0, 0, 0 ) [/COLOR]
 [COLOR=#000000]05:47:36 PM: Trying to get url: [http://lyrics.wikia.com/Unknown:01_-_Indian_Summer](http://lyrics.wikia.com/Unknown:01_-_Indian_Summer) [/COLOR]
 [COLOR=#000000]05:47:37 PM: Trying to get url: [http://www.azlyrics.com/lyrics/unknown/01indiansummer.html](http://www.azlyrics.com/lyrics/unknown/01indiansummer.html) [/COLOR]
 [COLOR=#000000]05:47:38 PM: Trying to get url: [http://www.coveralia.com/letras/01---indian-summer-unknown.php](http://www.coveralia.com/letras/01---indian-summer-unknown.php) [/COLOR]
 [COLOR=#000000]05:47:39 PM: Trying to get url: [http://www.directlyrics.com/unknown-01---indian-summer-lyrics.html](http://www.directlyrics.com/unknown-01---indian-summer-lyrics.html) [/COLOR]
 [COLOR=#000000]05:47:39 PM: Trying to get url: [http://www.elyrics.net/read/U/unknown-lyrics/01---indian-summer-lyrics.html](http://www.elyrics.net/read/U/unknown-lyrics/01---indian-summer-lyrics.html) [/COLOR]
 [COLOR=#000000]05:47:40 PM: Trying to get url: [http://letras.terra.com.br/winamp.php?musica=01%2B-%2Bindian%2Bsummer&artista=unknown](http://letras.terra.com.br/winamp.php?musica=01%2B-%2Bindian%2Bsummer&artista=unknown) [/COLOR]
 [COLOR=#000000]05:47:42 PM: Trying to get url: [http://www.loudson.gs/U/unknown/a-thousand-kisses-deep/01---indian-summer](http://www.loudson.gs/U/unknown/a-thousand-kisses-deep/01---indian-summer) [/COLOR]
 [COLOR=#000000]05:47:43 PM: Trying to get url: [http://www.lyrics.com/lyrics/unknown/01---indian-summer.html](http://www.lyrics.com/lyrics/unknown/01---indian-summer.html) [/COLOR]
 [COLOR=#000000]05:47:43 PM: StatusChanged( 2, 0, 0, 0 ) [/COLOR]
 [COLOR=#000000]05:47:44 PM: Trying to get url: [http://www.lyrics007.com/Unknown+Lyrics/01+-+Indian+Summer+Lyrics.html](http://www.lyrics007.com/Unknown+Lyrics/01+-+Indian+Summer+Lyrics.html) [/COLOR]
 [COLOR=#000000]05:47:45 PM: Trying to get url: [http://www.lyricsbay.com/01_-_indian_summer_lyrics-unknown.html](http://www.lyricsbay.com/01_-_indian_summer_lyrics-unknown.html) [/COLOR]
 [COLOR=#000000]05:47:45 PM: Trying to get url: [http://www.lyricsdownload.com/unknown-01---indian-summer-lyrics.html](http://www.lyricsdownload.com/unknown-01---indian-summer-lyrics.html) [/COLOR]
 [COLOR=#000000]05:47:47 PM: Trying to get url: [http://www.lyricsmania.com/01_-_indian_summer_lyrics_unknown.html](http://www.lyricsmania.com/01_-_indian_summer_lyrics_unknown.html) [/COLOR]
 [COLOR=#000000]05:47:47 PM: Trying to get url: [http://www.lyricsmode.com/lyrics/U/unknown/01_-_indian_summer.html](http://www.lyricsmode.com/lyrics/U/unknown/01_-_indian_summer.html) [/COLOR]
 [COLOR=#000000]05:47:48 PM: Trying to get url: [http://www.lyricsreg.com/lyrics/unknown/01%2B-%2Bindian%2Bsummer/](http://www.lyricsreg.com/lyrics/unknown/01%2B-%2Bindian%2Bsummer/) [/COLOR]
 [COLOR=#000000]05:47:49 PM: Trying to get url: [http://www.lyricstime.com/unknown-01---indian-summer-lyrics.html](http://www.lyricstime.com/unknown-01---indian-summer-lyrics.html) [/COLOR]
 [COLOR=#000000]05:47:49 PM: Trying to get url: [www.lyricsvip.com/Unknown/01---Indian-Summer-Lyrics.html](www.lyricsvip.com/Unknown/01---Indian-Summer-Lyrics.html) [/COLOR]
 [COLOR=#000000]05:47:50 PM: Trying to get url: [http://www.lyriki.com/unknown:01_-_indian_summer](http://www.lyriki.com/unknown:01_-_indian_summer) [/COLOR]
 [COLOR=#000000]05:47:53 PM: Trying to get url: [http://www.metrolyrics.com/01---indian-summer-lyrics-unknown.html](http://www.metrolyrics.com/01---indian-summer-lyrics-unknown.html) [/COLOR]
 [COLOR=#000000]05:47:54 PM: Trying to get url: [http://www.mp3lyrics.org/U/unknown/01---indian-summer/](http://www.mp3lyrics.org/U/unknown/01---indian-summer/) [/COLOR]
 [COLOR=#000000]05:47:54 PM: Trying to get url: [http://www.seeklyrics.com/lyrics/Unknown/01---Indian-Summer.html](http://www.seeklyrics.com/lyrics/Unknown/01---Indian-Summer.html) [/COLOR]
 [COLOR=#000000]05:47:54 PM: Trying to get url: [http://www.songlyrics.com/unknown/01---indian-summer-lyrics/](http://www.songlyrics.com/unknown/01---indian-summer-lyrics/) [/COLOR]
 [COLOR=#000000]05:47:55 PM: Trying to get url: [http://vagalume.uol.com.br/unknown/01---indian-summer.html](http://vagalume.uol.com.br/unknown/01---indian-summer.html) [/COLOR]
 [COLOR=#000000]05:47:56 PM: TracksDClicked... [/COLOR]
 [COLOR=#000000]05:47:56 PM: Error: Gstreamer error 'Could not determine type of stream.' [/COLOR]
 [COLOR=#000000]05:47:56 PM: OnMediaLoaded Cur: 0 1   2668345172 [/COLOR]
 [COLOR=#000000]05:47:56 PM: Trying to get url: [http://vagalume.uol.com.br/unknown/01---indian-summer-traducao.html](http://vagalume.uol.com.br/unknown/01---indian-summer-traducao.html)[/COLOR]


[COLOR=#000000]These files are stored on my local hard drive (western digital), so I don;t understand all the html references...[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Thanks for any help,[/COLOR]
[COLOR=#000000]Chris
[/COLOR]

---

### Post by anonbeat on 2012-10-26
This are links trying to find lyrics for this track.

One latest thing I can ask you is if you can email me one or two of this tracks that dont play so I can take a look. If you want you can email it to anonbeat at gmail dot com

Regards

---

### Post by chirs p on 2012-10-28
Hi Anonbeat,
Yesterday I sent you an e-mail (to the g-mail address you provided) and an invitation to share a Dropbox folder into which I uploaded a few of the files (they are >100MB each, so I could not e-mail them directly).  Whenever you have a chance, please let me know what you find once you've tried the files.
Thanks so much for your help; Guayadeque seems like a really great player, and I'd like to be able to use it to listen to all my music files, if possible.
Chris

---

### Post by anonbeat on 2012-10-28
> **chirs p said:**
> Hi Anonbeat,
Yesterday I sent you an e-mail (to the g-mail address you provided) and an invitation to share a Dropbox folder into which I uploaded a few of the files (they are >100MB each, so I could not e-mail them directly).  Whenever you have a chance, please let me know what you find once you've tried the files.
Thanks so much for your help; Guayadeque seems like a really great player, and I'd like to be able to use it to listen to all my music files, if possible.
Chris

I just did a test with one of the files and its a gstreamer problem. With all the plugins installed it cant determine the type of media.

```

gst-launch-0.10 --gst-debug-level=2 playbin2 uri="file:///home/jrios/Downloads/05%20-%20Mellow%20Yellow%20(Mono).wav"
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
0:00:00.020415281  5306      0x23bb9e0 WARN                    riff riff-media.c:1531:gst_riff_create_audio_caps: failed to add channel layout
0:00:00.020453854  5306      0x23bb9e0 WARN                    riff riff-media.c:1632:gst_riff_create_audio_caps: Unknown WAVE_FORMAT_EXTENSIBLE audio format
0:00:00.020481551  5306      0x23bb9e0 WARN                wavparse gstwavparse.c:1669:gst_wavparse_stream_headers:<wavparse0> error: No caps found for format 0x0, 0 channels, 0 Hz
ERROR: from element /GstPlayBin2:playbin20/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstWavParse:wavparse0: Could not determine type of stream.
0:00:00.020664561  5306      0x23bb9e0 WARN                wavparse gstwavparse.c:2110:gst_wavparse_loop:<wavparse0> error: Internal data flow error.
0:00:00.020691010  5306      0x23bb9e0 WARN                wavparse gstwavparse.c:2110:gst_wavparse_loop:<wavparse0> error: streaming task paused, reason error (-5)
Additional debug info:
gstwavparse.c(1669): gst_wavparse_stream_headers (): /GstPlayBin2:playbin20/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstWavParse:wavparse0:
No caps found for format 0x0, 0 channels, 0 Hz
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...

```

You should submit the bug report to gstreamer developers

---

### Post by chirs p on 2012-10-29
Hi anonbeat,
Thanks so much for all your help.  If it's not too much trouble, could you explain how I submit a bug report?  I'm still a complete Ubuntu newbie and have not yet learned how to do these things.
Thanks again!
Chris

---

### Post by anonbeat on 2012-10-30
> **chirs p said:**
> Hi anonbeat,
Thanks so much for all your help.  If it's not too much trouble, could you explain how I submit a bug report?  I'm still a complete Ubuntu newbie and have not yet learned how to do these things.
Thanks again!
Chris

You can go to [https://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer&component=gst-plugins-base](https://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer&component=gst-plugins-base) and create a bug report indicating that the command I posted (gst-launch) fails with that kind of files. 
You should make available one file so developers can check with that kind of files.

---

### Post by monkeybrain2012 on 2012-10-30
You need to install w32codecs or w64codecs from medibuntu to play .wav files.

Add the repository following instructions here
[http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/](http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/)


Then install nonfree-codecs and w64codecs(w32codecs if your machine is 32 bits) and upgrade. You may also want to install libdvdcss2 if you want to play DVDs.

---

### Post by chirs p on 2012-10-31
Hi Monkey brain 2012
Thanks so much. I added the repository following the directions on the link you provided.  How do I " install nonfree-codecs and w64codecs (my machine is 64 bits) and upgrade"?
Sorry if this is a dumb question, but I'm a complete linux-newbie...
Thanks again
Chris

---

### Post by monkeybrain2012 on 2012-10-31
In the terminal type
```

sudo apt-get update

sudo apt-get install w64codecs
```

You should also be able to find it in the Software Center and use it to install the codecs, since you have added the repository.

---

### Post by chirs p on 2012-11-02
Hi Monkeybrain,
Thanks for all the help.  Unfortunately, that does not seem to have helped either.  The same files still will not play and give the same gstreamer error.  Do you have any other suggestions?
Thanks again
Chris

---

### Post by mc4man on 2012-11-03
Maybe install mediainfo & open the file in it, see what is shows. 
After opening switching to the html or text view for C&P will provide  a bit more info.

---

