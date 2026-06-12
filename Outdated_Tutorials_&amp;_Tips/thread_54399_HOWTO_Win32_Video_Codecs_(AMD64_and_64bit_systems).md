---
title: "HOWTO: Win32 Video Codecs (AMD64 and 64bit systems)"
date: 2005-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-08-04
This HOWTO is mainly aimed at all the users of Ubuntu 64bit (although it would work also on a 32bit system) who can't (obviously) install these codecs using the repositories.

If you want to watch your movies (avi and wmv) or listen to your music files (wma) which require Win32 codecs this is what you need:

1)You have to OWN A LEGAL COPY of Windows, because these are proprietary codecs (somebody correct me if I'm wrong)

2)Install &#8220;xine-ui&#8221; and &#8220;totem-xine&#8221; in Synaptic or type in the command line: 
sudo apt-get install xine-ui ; totem-xine

3) Launch Xine (or Totem) and try to play a video (this will create a .config file)

4) Download the codecs from this website:

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the &#8220;essential codecs package&#8221;)

5) Open the command line(&#8220;Konsole&#8221; if you are using KDE, &#8220;Terminal&#8221; if you are using GNOME) and follow these steps:

a) Get to the directory where you have downloaded the file (/home/alberto/downloads in my case)

cd /home/alberto/downloads

b) Create the directory in which you are going to put the codecs (/usr/lib/win32) 

sudo mkdir /usr/lib/win32

c) Now, assuming the file you downloaded is &#8220;essential-20050412.tar.bz2&#8221;:

tar -xjf essential-20050412.tar.bz2 (this will extract the file)

sudo mv essential-20050412/* /usr/lib/win32 (this command will move the files to the desired folder)

d) Now restart xine (if you were using it)

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!

Alberto

UPDATE: It seems wmv9 don't work with my HOWTO.

---

### Post by Tamir on 2005-08-04
Wow! is this realy working on 64bit? cool.

---

### Post by tseliot on 2005-08-04
Yes, this is one more reason not to switch back to Ubuntu 32bit. C'mon let's improve Ubuntu 64 support!

---

### Post by poofyhairguy on 2005-08-04
Someone, please add this to the wiki.

---

### Post by tseliot on 2005-08-04
This would be an honour for me. Thanks

---

### Post by tseliot on 2005-08-05
I meant it would be an honour for me if someone put it in the Wiki. I don't know how to do it.

---

### Post by Kuolio on 2005-08-05
Thank you for this  \\:D/

---

### Post by kostkon on 2005-08-05
Impressive!!

Let's try to reach 100% equallity between 32 and 64 bit!! We can do it!!

---

### Post by Tamir on 2005-08-05
[QUOTE=kostkon]Impressive!!

Let's try to reach 100% equallity between 32 and 64 bit!! We can do it!![/QUOTE]
 That's the spirit :)

---

### Post by etitor on 2005-08-05
[QUOTE=tseliot]

/home/.xine/config

[/QUOTE]

Thank you tseliot, but I think you lack something there between "/home" and "/.xine". Maybe you can say just ~/.xine/config.

By the way, even with that corrected, after following your directions I tried to play a WMV (version 9) in my AMD64 K8 Ubuntu, to no avail. :(

---

### Post by Pcghost on 2005-08-05
Have I mentioned lately how much you rule for this tseliot?  :) 

I didn't expect this to be accomplished until they finally pushed Windows Media Player to 64-bit.  

And for the record, I never get the urge to go 32-bit, no matter what 64-bit is lacking.  \\:D/

---

### Post by Ephack on 2005-08-05
That's greeeeaaaattttt! Thank you so much!!!

Yes, something's lacking between "/home/" and "/.xine/" and that's your login. The right path is:

/home/your_login/.xine/config

---

### Post by DancingSun on 2005-08-05
Can this be done with gstreamer as well?

---

### Post by negatory on 2005-08-05
It did not work for me...I've installed totem-xine and no luck with that (playing a wmv complains not having the codec needed) ...even installed gxine and still no luck....
Don't know what I'm doing wrong...please post your entire config.
Thanks
Pedro Carrico

---

### Post by Jet2k5 on 2005-08-05
lol hey don't forget who wanted to start getting Ubuntu 64-bit better!


... Tarmir you started with the packages :P

---

### Post by Corbelius on 2005-08-06
Work fine for me, tnx ;)

---

### Post by tseliot on 2005-08-06
[QUOTE=negatory]It did not work for me...I've installed totem-xine and no luck with that (playing a wmv complains not having the codec needed) ...even installed gxine and still no luck....
Don't know what I'm doing wrong...please post your entire config.
Thanks
Pedro Carrico[/QUOTE]

Well, I would if I could. My system crashed (thanks to my SATA disk with WinXP which made freeze my computer, and now also the PATA drive with Ubuntu has problems) and I have to bring my computer to a computer shop ("fortunately" it's still under warranty) because (after several attempts to save it) I've come to think that somthing happened to the motherboard too. I've lost all my datas and I haven't managed to reinstall Ubuntu or any other distro (they go to kernel panic). At the moment I'm writing from Kurumin Linux Livecd 4.2, the only one which seems to work on my PC now (even Knoppix 4.0 has stopped working on my PC and Winxp reboots everytime I try to install it ).

In conclusion:
I'm sorry, I can't help you right now. I hope fixing my computer up doesn't take too much time.

P.S.: thanks for the corrections

---

### Post by Octane on 2005-08-07
hate to be "that guy" but it doesn't work for me :X

Perhaps I need to try a different wmv

---

### Post by losing.virginia on 2005-08-09
I don't have /home/<user name>/.xine/config. There is nothing there. I have totem-xine installed as well as xine-ui. Do I need to do something?

---

### Post by DancingSun on 2005-08-10
[QUOTE=losing.virginia]I don't have /home/<user name>/.xine/config. There is nothing there. I have totem-xine installed as well as xine-ui. Do I need to do something?[/QUOTE]
The directories with "." in front of the name are hidden, did you select View -> Show Hidden Files from the File Browser?

---

### Post by tseliot on 2005-08-10
The folder /.xine/ is hidden, for this reason you can't see it. If this is your problem select "show hidden files" in your navigator (konqueror, nautilus or rox) and you should be able to see it.

I hope it helps you

---

### Post by Ephack on 2005-08-10
[QUOTE=losing.virginia]I don't have /home/<user name>/.xine/config. There is nothing there. I have totem-xine installed as well as xine-ui. Do I need to do something?[/QUOTE]
 Another solution if the one of tseliot doesn't solve your problem: if like me you installed xine for the first time at this occasion, you have to launch totem before going further. Launching Totem will create the folder .xine (but not the file config in my case, but then I created it). Don't forget to close Totem before going on.

---

### Post by losing.virginia on 2005-08-10
No offense but I am not that new.. :grin: 

I have run totem-xine but when I go to the location /home/<usr>/.xine/ all I have is a catalog.cache file. I have run totem-xine but not xine....

HAHA just ran Xine and now the config file is there. For some reason when I installed xine it didn't show up in the gnome menus or from the the terminal but did appear after a reboot.  ](*,)

Is this supposed to do Windows Media 9? I only get audio for wmv files that are encoded as version 9.

---

### Post by losing.virginia on 2005-08-11
As a follow up if I add the line for the win32codecs it disappears after I run Xine or Totem-xine. It seems to regenerate the config file automatically.

---

### Post by tseliot on 2005-08-11
[QUOTE=losing.virginia]As a follow up if I add the line for the win32codecs it disappears after I run Xine or Totem-xine. It seems to regenerate the config file automatically.[/QUOTE]

Don't you worry this is normal, it just moves up the line with win32 codecs path but it doesn't delete it and the videos keep on working.

As far as wmv9 are concerned, as I said before now I'm stuck with my notebook with Ubuntu32. I can't help you until Compaq gives me my computer (AMD64) back. Then I'm sure I'll find a way to make wmv9 work.

---

### Post by losing.virginia on 2005-08-11
After a bit of hunting I found the totem_config in /home/<usr>/.gnome2 which seems to be the same as the xine config file. When I looked in the totem-addons it seems that it is full of symlinks to the files /usr/lib/win32. So it seems that the line in the config worked but I just happen to have troublesome files.

Good luck with the machine  :)

---

### Post by jon_gunnar on 2005-08-14
[QUOTE=tseliot]This HOWTO is mainly aimed at all the users of Ubuntu 64bit (although it would work also on a 32bit system) who can't (obviously) install these codecs using the repositories.

If you want to watch your movies (avi and wmv) or listen to your music files (wma) which require Win32 codecs this is what you need:
[/QUOTE]

Works like a charm :-) Then I can watch my beloved Sherlock Holmes movies again  \\:D/

---

### Post by tseliot on 2005-08-14
About the problems with wmv9 videos. 

Could anybody try to open them (for example you can go ti ign.com and download a video trailer of any game) in kaffeine and mplayer after having followed my guide?

Please, tell me if it work, as I can't try it myself without my computer.

---

### Post by Corbelius on 2005-08-15
[QUOTE=tseliot]About the problems with wmv9 videos. 

Could anybody try to open them (for example you can go ti ign.com and download a video trailer of any game) in kaffeine and mplayer after having followed my guide?

Please, tell me if it work, as I can't try it myself without my computer.[/QUOTE]

Mmm... sound work but no video  :-?

---

### Post by tseliot on 2005-08-15
Ok, thanks for the information.

---

### Post by Steve1961 on 2005-08-17
> **tseliot]This HOWTO is mainly aimed at all the users of Ubuntu 64bit (although it would work also on a 32bit system) who can't (obviously) install these codecs using the repositories.

If you want to watch your movies (avi and wmv) or listen to your music files (wma) which require Win32 codecs this is what you need:

1)You have to OWN  A LEGAL COPY of Windows, because these are proprietary codecs (somebody correct me if I'm wrong)

2)Install “xine-ui” and “totem-xine” in Synaptic or type in the command line: 
sudo apt-get install xine-ui  said:**
> http://www.mplayerhq.hu/homepage/design7/dload.html[/url]
     (just download the “essential codecs package”)

4)Open the command line(“Konsole” if you are using KDE, “Terminal” if you are using GNOME) and follow these steps:

a) Get to the directory where you have downloaded the file (/home/alberto/downloads  in my case)

cd /home/alberto/downloads

b) Create the directory in which you are going to put the codecs (/usr/lib/win32 in my case)

sudo mkdir /usr/lib/win32

c) Now, assuming the file you downloaded is  “essential-20050412.tar.bz2”:

sudo tar jxvf essential-20050412.tar.bz2  /usr/lib/win32

d) Then, if you are using KDE type: (alberto is my username and the name of my folder, so remember to put YOURS)

kate /home/alberto/.xine/config

Otherwise if you are using GNOME type:

gedit /home/alberto/.xine/config

(please don't forget to put the dot “.” before the word “xine”)

e) Get to the end of the document and add the following line:

decoder.external.win32_codecs_path:/usr/lib/win32

Here's an example (part of my config file):

# percentage of skipped frames to tolerate
# numeric, default: 10
#engine.performance.warn_skipped_threshold:10

# allow implicit changes to the configuration (e.g. by MRL)
# bool, default: 0
#misc.implicit_config:0

[COLOR=Red]decoder.external.win32_codecs_path:/usr/lib/win32[/COLOR]

f) Save the file (yes, overwrite it) and exit.

g) Now restart xine (if you were using it)

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!


P.S.:Unfortunately I didn't get Amarok to play wma files although I installed its xine engine and I set it as its default engine.
Well, better than nothing!  :-P

Alberto

UPDATE: It seems wmv9 don't work with my HOWTO. I promise to find a way to make them work as soon as I have my computer back from Compaq.
 I got as far as sudo tar jxvf essential-20050412.tar.bz2 /usr/lib/win32 but keep getting the error message:
tar: /usr/lib/win32: Not found in archive
tar: Error exit delayed from previous errors

I've checked that /usr/lib/win32 has been created, and it has.  What am I doing wrong?

---

### Post by s_p_a_r_k_y on 2005-08-17
wont there soon also be 64bit windows codecs once those proprietary guys start recompiling their code for amd64?

---

### Post by tseliot on 2005-08-17
Are you in the folder where you have the tar file when you prompt the command "sudo tar jxvf essential-20050412.tar.bz2 /usr/lib/win32"?

---

### Post by Steve1961 on 2005-08-17
[QUOTE=tseliot]Are you in the folder where you have the tar file when you prompt the command "sudo tar jxvf essential-20050412.tar.bz2 /usr/lib/win32"?[/QUOTE]

I was and I don't know why it didn't work.  But I copied the tar file to /urs/lib/win32 and uncompressed from there.  Seems to be fine now??

---

### Post by tseliot on 2005-08-17
[QUOTE=Steve1961]I was and I don't know why it didn't work.  But I copied the tar file to /urs/lib/win32 and uncompressed from there.  Seems to be fine now??[/QUOTE]

Yes, it's the same. Sorry if I didn't suggested this way, but I'm tired (I've been studying all day and helping users during the breaks).

---

### Post by Steve1961 on 2005-08-17
[QUOTE=tseliot]Yes, it's the same. Sorry if I didn't suggested this way, but I'm tired (I've been studying all day and helping users during the breaks).[/QUOTE]

No problem. Strangely, neither totem or xine will play wma files, but mplayer now can??  I prefer mplayer anyway.  All I now need is a copy of the codec to allow it to play DVDs in ubuntu64.

---

### Post by jamesrw on 2005-08-22
seems I have a problem with xine to begin with. when I run it, it crashes and bring me back to login. I tried to play with the multimedia sys selector in the system > preferences tab but no luck. Any clues?

---

### Post by duffman25 on 2005-08-22
[QUOTE=Steve1961]No problem. Strangely, neither totem or xine will play wma files, but mplayer now can??  I prefer mplayer anyway.  All I now need is a copy of the codec to allow it to play DVDs in ubuntu64.[/QUOTE]

Ubuntu comes with a script to install it. There's no need for a .deb
goto : /usr/share/doc/libdvdread3/examples
run the install-css.sh script that's in there.

bye

---

### Post by tseliot on 2005-08-22
[QUOTE=jamesrw]seems I have a problem with xine to begin with. when I run it, it crashes and bring me back to login. I tried to play with the multimedia sys selector in the system > preferences tab but no luck. Any clues?[/QUOTE]

I know it might sound a little naive, but have you tried to reinstall it in Synaptic or apt-get?

---

### Post by jamesrw on 2005-08-22
[QUOTE=tseliot]I know it might sound a little naive, but have you tried to reinstall it in Synaptic or apt-get?[/QUOTE]
  I only extracted the codecs in /usr/lib/win32, but nothing further.

I ended up finding a driver for my video card and now it works fine. I haven't even completed the install howto and can play avi mpeg dvd!!!. Is it using the codecs extracted in the file?

Also totem is slow but xine is great. Is it safe to uninstall totem or does xine rely on it?

>> nevermind.. i see its the other way around

---

### Post by tseliot on 2005-08-22
[QUOTE=jamesrw]I only extracted the codecs in /usr/lib/win32, but nothing further.

I ended up finding a driver for my video card and now it works fine. I haven't even completed the install howto and can play avi mpeg dvd!!!. Is it using the codecs extracted in the file?
[/QUOTE]
Yes it is. I'm happy it works for you too.

---

### Post by DancingSun on 2005-08-22
Hmm ... I don't have win32codec installed.  But I can play avi files. I haven't tried DVDs yet, but I think that'll work too, since gstreamer has plugins for that.  I believe win32codec is mostly for wmv, asf, and related audio and video encodings (maybe real video and quick time as well[?]).  Many AVI files have video streams encoded using the DivX, Xvid, MPEG-4 encoding, so you can actually view those AVI files without having win32codec installed.

Also, older wmv files can be viewed without the win32codec because there are open source implementations of it.  Only wmv3 (windows media 9) or higher needs the win32codecs.

---

### Post by tseliot on 2005-08-22
[QUOTE=DancingSun]Hmm ... I don't have win32codec installed.  But I can play avi files. I haven't tried DVDs yet, but I think that'll work too, since gstreamer has plugins for that.  I believe win32codec is mostly for wmv, asf, and related audio and video encodings (maybe real video and quick time as well[?]).  Many AVI files have video streams encoded using the DivX, Xvid, MPEG-4 encoding, so you can actually view those AVI files without having win32codec installed.

Also, older wmv files can be viewed without the win32codec because there are open source implementations of it.  Only wmv3 (windows media 9) or higher needs the win32codecs.[/QUOTE]
I would really like to know what makes the difference between my method and win32codec package, it's likely only the creator of the package know the answer (about wmv3)

---

### Post by DancingSun on 2005-08-22
[QUOTE=tseliot]I would really like to know what makes the difference between my method and win32codec package, it's likely only the creator of the package know the answer (about wmv3)[/QUOTE]
Ok, here an excerpt from Mplayer's README:
> MPlayer and libavcodec have builtin support for the most common audio and video formats, but some formats require external codecs. Examples include Real, Indeo and QuickTime audio formats. Support for Windows Media formats except WMV9 exists but still has some bugs, your mileage may vary. This step is not mandatory, but recommended for getting MPlayer to play a broader range of formats. Please note that most codecs only work on Intel x86 compatible PCs.
Reguarding the Windows Media part, I'm interpreting it as "MPlayer comes with support for Windows Media format up to but not including WMV9, although some bugs still exists".  Which means the MPlayer's win32codecs package will allow you to decode WMV9 videos.  Makes sense, since win32codecs are directly copied off of a Windows installation anyway.

I am under the impresssion that the win32codec package in the Ubuntu repository is the same package that MPlayer uses, so, if your method worked, both methods should yield the same results.  However, some users are reporting the they couldn't view wmv9 videos using your how-to, so perhaps there is more work involved to get win32codecs working on AMD64?

I guess a better way to make sure that win32codecs work is to play some .MOV (Quicktime) files.  Since, there are multiple versions of WMV out there and the older versions have already been reversed engineered by the open source community.

---

### Post by DancingSun on 2005-08-22
FYI, Ubuntu has gstreamer0.8-ffmpeg plugin in the repositries, and [ffmpeg](http://sourceforge.net/projects/ffmpeg/)  includes libavcodec, which is the codec mentioned in the Mplayer README.  So that means Totem-gstreamer can also play "some" wmv files, which I can confirm with my experience, although I must agree the playback experience was horrible.

---

### Post by liquidfire on 2005-08-22
[QUOTE=tseliot]I would really like to know what makes the difference between my method and win32codec package, it's likely only the creator of the package know the answer (about wmv3)[/QUOTE]
Lol, when i try to install them i'm getting an error

I did sudo tar jxvf essential-20050412.tar.bz2 /usr/lib/win32
then it says /usr/lib/win32 not found in the archive  ](*,)

---

### Post by tseliot on 2005-08-23
[QUOTE=liquidfire]Lol, when i try to install them i'm getting an error

I did sudo tar jxvf essential-20050412.tar.bz2 /usr/lib/win32
then it says /usr/lib/win32 not found in the archive  ](*,)[/QUOTE]
If the folder exists copy the tar file to /urs/lib/win32 and uncompress it from there.

You can do it with:

sudo cp essential-20050412.tar.bz2 /usr/lib/win32

cd  /usr/lib/win32

tar jxvf essential-20050412.tar.bz2

Or if you prefer to do it using a graphical inteface:

sudo nautilus (if you use GNOME) or sudo konqueror (in KDE)

Then drag and drop the file to the new folder and extract it (or just open the file and extract the file to the correct path  /usr/lib/win32.

Tell me if it works.

---

### Post by liquidfire on 2005-08-23
[QUOTE=tseliot]If the folder exists copy the tar file to /urs/lib/win32 and uncompress it from there.

You can do it with:

sudo cp essential-20050412.tar.bz2 /usr/lib/win32

cd  /usr/lib/win32

tar jxvf essential-20050412.tar.bz2

Or if you prefer to do it using a graphical inteface:

sudo nautilus (if you use GNOME) or sudo konqueror (in KDE)

Then drag and drop the file to the new folder and extract it (or just open the file and extract the file to the correct path  /usr/lib/win32.

Tell me if it works.[/QUOTE]
That worked, but when I start Xine it can't open my avi file: " Cannot find right demuxer" I assume this has to do something with my sound?

---

### Post by tseliot on 2005-08-23
[QUOTE=liquidfire]That worked, but when I start Xine it can't open my avi file: " Cannot find right demuxer" I assume this has to do something with my sound?[/QUOTE]

1) have you followed every step of my guide?

2) have you tried Mediaplayer?

---

### Post by liquidfire on 2005-08-23
[QUOTE=tseliot]1) have you followed every step of my guide?

2) have you tried Mediaplayer?[/QUOTE]

1) Yes
2) Yes, i tried but i'm thinking to begin my file is corrupt.
I keep getting errors like no stream information ](*,)

---

### Post by tseliot on 2005-08-23
[QUOTE=liquidfire]1) Yes
2) Yes, i tried but i'm thinking to begin my file is corrupt.
I keep getting errors like no stream information ](*,)[/QUOTE]

Try to install Kaffeine and Totem-Xine and try again.

And try other files

---

### Post by liquidfire on 2005-08-23
[QUOTE=tseliot]Try to install Kaffeine and Totem-Xine and try again.

And try other files[/QUOTE]
What do you mean under "other files"

---

### Post by tseliot on 2005-08-23
[QUOTE=liquidfire]What do you mean under "other files"[/QUOTE]
I mean videoclips, films, etc.

---

### Post by liquidfire on 2005-08-26
[QUOTE=tseliot]I mean videoclips, films, etc.[/QUOTE]

I've a new problem I just freshly installed everything but my totem-xine isn't generating a config file which I can edit :/
Any idea's?

---

### Post by tseliot on 2005-08-26
[QUOTE=liquidfire]I've a new problem I just freshly installed everything but my totem-xine isn't generating a config file which I can edit :/
Any idea's?[/QUOTE]
I think another user had the same problem.

1) Install "Xine"

2) Launch it and try to play a video

3) Now check if it has created the config file

4) Edit the file

---

### Post by bagatonovic on 2005-08-26
[QUOTE=tseliot]I think another user had the same problem.

1) Install "Xine"

2) Launch it and try to play a video

3) Now check if it has created the config file

4) Edit the file[/QUOTE]


This is not working for me.  I followed the guide exactly.  I was able to edit the config.  When I try to play a WMV, I can hear the sound, but nothing else.  Located below is my whole config file.  I want to point out that it keeps moving the line you want us to add over to the real media section.  No matter how many times I move the line to the bottom, it moves it up the the real section.  I also tried with gxine and same problem.

I am using essential-20050412.tar.bz2
I have extracted the contents to /usr/lib/win32
I noticed it kept the folder name of the archive, so I moved the files over to /usr/lib/win32 from /usr/lib/win32/essentiail-20050412/

Now I have to go hang with my wife or I'll be in trouble.  See you guys later.  And even though this didn't work for me, I totally respect you Tseliot.  You rule sir.

***EDIT*** LOL Some parts of the config turned into smiles!!! LOL
------------------------------------------------------------------------------------------------------------------------

#
# xine config file
#
.version:2

# Entries which are still set to their default values are commented out.
# Remove the '#' at the beginning of the line, if you want to change them.

# Enable deinterlacing by default
# bool, default: 0
#gui.deinterlace_by_default:0

# Configuration experience level
# { Beginner  Advanced  Expert  Master of the known universe }, default: 0
#gui.experience_level:Beginner

# Enable OSD support
# bool, default: 1
#gui.osd_enabled:1

# Dismiss OSD time (s)
# numeric, default: 3
#gui.osd_timeout:3

# Ask user for playback with unsupported codec
# bool, default: 0
#gui.play_anyway:0

# Automatically reload old playlist
# bool, default: 0
#gui.playlist_auto_reload:0

# Audio visualization plugin
# { goom  oscope  fftscope  fftgraph }, default: 0
#gui.post_audio_plugin:goom

# gui skin theme
# { xinetic }, default: 0
#gui.skin:xinetic

# Change xine's behavior for unexperienced user
# bool, default: 1
#gui.smart_mode:1

# Snapshot location
# string, default: /home/bagatonovic
#gui.snapshotdir:/home/bagatonovic

# Display splash screen
# bool, default: 1
#gui.splash:1

# Subtitle autoloading
# bool, default: 1
#gui.subtitle_autoload:1

# Visual animation style
# { None  Post Plugin  Stream Animation }, default: 1
#gui.visual_anim:Post Plugin

# Windows stacking (more)
# bool, default: 0
#gui.always_layer_above:0

# Audio mixer control method
# { Sound card  Software }, default: 0
#gui.audio_mixer_method:Sound card

# Visiblility behavior of panel
# bool, default: 0
#gui.auto_panel_visibility:0

# Visibility behavior of output window
# bool, default: 0
#gui.auto_video_output_visibility:0

# Deinterlace plugin.
# string, default: tvtime:method=LinearBlend,cheap_mode=1,pulldown=0,use_progressive_frame_flag=1
#gui.deinterlace_plugin:tvtime:method=LinearBlend,cheap_mode=1,pulldown=0,use_progressive_frame_flag=1

# Event sender behavior
# bool, default: 1
#gui.eventer_sticky:1

# Windows stacking
# bool, default: 0
#gui.layer_above:0

# Use unscaled OSD
# bool, default: 1
#gui.osd_use_unscaled:1

# Screensaver wakeup
# numeric, default: 10
#gui.screensaver_timeout:10

# Menu shortcut style
# { Windows style  Emacs style }, default: 0
#gui.shortcut_style:Windows style

# Stream information
# bool, default: 0
#gui.sinfo_auto_update:0

# Skin Server Url
# string, default: [http://xine.sourceforge.net/skins/skins.slx](http://xine.sourceforge.net/skins/skins.slx)
#gui.skin_server_url:[http://xine.sourceforge.net/skins/skins.slx](http://xine.sourceforge.net/skins/skins.slx)

# Chapter hopping
# bool, default: 1
#gui.skip_by_chapter:1

# New stream sizes resize output window
# bool, default: 1
#gui.stream_resize_window:1

# tips timeout (ms)
# numeric, default: 500
#gui.tips_timeout:500

# gui tips visibility
# bool, default: 1
#gui.tips_visible:1

# Name of video display
# string, default: 
#gui.video_display:

# Synchronized X protocol (debug)
# bool, default: 0
#gui.xsynchronize:0

# Double size for small streams (require stream_resize_window)
# bool, default: 0
#gui.zoom_small_stream:0

# Logo mrl
# string, default: file:/usr/share/xine/skins/xine-ui_logo.mpv
#gui.logo_mrl:file:/usr/share/xine/skins/xine-ui_logo.mpv

# use XVidModeExtension when switching to fullscreen
# bool, default: 0
#gui.use_xvidext:0

# Amplification level
# [0..200], default: 100
#gui.amp_level:100

# gui panel visibility
# bool, default: 1
#gui.panel_visible:1

# numeric, default: 200
#gui.panel_x:200

# numeric, default: 100
#gui.panel_y:100

# brightness value
# [0..65535], default: -1
#gui.vo_brightness:-1

# contrast value
# [0..65535], default: -1
#gui.vo_contrast:-1

# saturation value
# [0..65535], default: -1
#gui.vo_saturation:-1

gui.setup_x:105

gui.setup_y:124

# palette (foreground-border-background) to use for subtitles and OSD
# { white-black-transparent  white-none-transparent  white-none-translucid  yellow-black-transparent }, default: 0
#ui.osd.text_palette:white-black-transparent

# notify changes to the hardware mixer
# bool, default: 1
#audio.alsa_hw_mixer:1

# audio driver to use
# { auto  null  alsa  oss  arts  esd  none  file }, default: 0
#audio.driver:auto

# use A/52 dynamic range compression
# bool, default: 0
#audio.a52.dynamic_range:0

# downmix audio to 2 channel surround stereo
# bool, default: 0
#audio.a52.surround_downmix:0

# A/52 volume
# [0..200], default: 100
#audio.a52.level:100

# device used for mono output
# string, default: default
#audio.device.alsa_default_device:default

# device used for stereo output
# string, default: plug:front:default
audio.device.alsa_front_device:default

# alsa mixer device
# string, default: PCM
#audio.device.alsa_mixer_name:PCM

# sound card can do mmap
# bool, default: 0
#audio.device.alsa_mmap_enable:0

# device used for 5.1-channel output
# string, default: iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2
#audio.device.alsa_passthrough_device:iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2

# device used for 4-channel output
# string, default: plug:surround40:0
#audio.device.alsa_surround40_device:plug:surround40:0

# device used for 5.1-channel output
# string, default: plug:surround51:0
#audio.device.alsa_surround51_device:plug:surround51:0

# speaker arrangement
# { Mono 1.0  Stereo 2.0  Headphones 2.0  Stereo 2.1  Surround 3.0  Surround 4.0  Surround 4.1  Surround 5.0  Surround 5.1  Surround 6.0  Surround 6.1  Surround 7.1  Pass Through }, default: 1
#audio.output.speaker_arrangement:Stereo 2.0

# offset for digital passthrough
# numeric, default: 0
#audio.synchronization.passthrough_offset:0

# method to sync audio and video
# { metronom feedback  resample }, default: 0
#audio.synchronization.av_sync_method:metronom feedback

# always resample to this rate (0 to disable)
# numeric, default: 0
#audio.synchronization.force_rate:0

# enable resampling
# { auto  off  on }, default: 0
#audio.synchronization.resample_mode:auto

# startup audio volume
# [0..100], default: 50
#audio.volume.mixer_volume:50

# restore volume level at startup
# bool, default: 0
#audio.volume.remember_volume:0

# video driver to use
# { auto  dxr3  aadxr3  xv  xshm  caca  aa  none  fb }, default: 0
#video.driver:auto

# pitch alignment workaround
# bool, default: 0
#video.device.xv_pitch_alignment:0

# autopaint colour key
# bool, default: 0
#video.device.xv_autopaint_colorkey:0

# video overlay colour key
# [0..16777215], default: 66046
#video.device.xv_colorkey:66046

# enable double buffering
# bool, default: 1
#video.device.xv_double_buffer:1

# disable exact alpha blending of overlays
# bool, default: 0
#video.output.disable_exact_alphablend:0

# disable all video scaling
# bool, default: 0
#video.output.disable_scaling:0

# horizontal image position in the output window
# [0..100], default: 50
#video.output.horizontal_position:50

# vertical image position in the output window
# [0..100], default: 50
#video.output.vertical_position:50

# deinterlace method (deprecated)
# { none  bob  weave  greedy  onefield  onefield_xv  linearblend }, default: 4
#video.output.xv_deinterlace_method:onefield

# MPEG-4 postprocessing quality
# [0..6], default: 3
#video.processing.ffmpeg_pp_quality:3

# DXR3 device number
# numeric, default: 0
#dxr3.device_number:0

# swap odd and even lines
# bool, default: 0
#dxr3.encoding.swap_fields:0

# add black bars to correct aspect ratio
# bool, default: 1
#dxr3.encoding.add_bars:1

# use smooth play mode for mpeg encoder playback
# bool, default: 1
#dxr3.encoding.alt_play_mode:1

# Domains, where to ignore the HTTP proxy
# string, default: 
#input.http_no_proxy:

# device used for CD audio
# string, default: /dev/cdrom
#media.audio_cd.device:/dev/cdrom

# slow down disc drive to this speed factor
# numeric, default: 4
#media.audio_cd.drive_slowdown:4

# query CDDB
# bool, default: 1
#media.audio_cd.use_cddb:1

# CDDB cache directory
# string, default: /home/bagatonovic/.xine/cddbcache
#media.audio_cd.cddb_cachedir:/home/bagatonovic/.xine/cddbcache

# CDDB server port
# numeric, default: 8880
#media.audio_cd.cddb_port:8880

# CDDB server name
# string, default: freedb.freedb.org
#media.audio_cd.cddb_server:freedb.freedb.org

# directory for saving streams
# string, default: 
#media.capture.save_dir:

# Number of dvb card to use.
# numeric, default: 0
#media.dvb.adapter:0

# Remember last DVB channel watched
# bool, default: 1
#media.dvb.remember_channel:1

# Last DVB channel viewed
# numeric, default: -1
#media.dvb.last_channel:-1

# default language for DVD playback
# string, default: en
#media.dvd.language:en

# region the DVD player claims to be in (1 to 8)
# numeric, default: 1
#media.dvd.region:1

# device used for DVD playback
# string, default: /dev/dvd
#media.dvd.device:/dev/dvd

# read-ahead caching
# bool, default: 1
#media.dvd.readahead:1

# unit for seeking
# { seek in program chain  seek in program }, default: 0
#media.dvd.seek_behaviour:seek in program chain

# unit for the skip action
# { skip program  skip part  skip title }, default: 0
#media.dvd.skip_behaviour:skip program

# file browsing start location
# string, default: /home/bagatonovic
media.files.origin_path:/home/bagatonovic/Documents/www/archive

# list hidden files
# bool, default: 0
#media.files.show_hidden_files:0

# network bandwidth
# { 14.4 Kbps (Modem)  19.2 Kbps (Modem)  28.8 Kbps (Modem)  33.6 Kbps (Modem)  34.4 Kbps (Modem)  57.6 Kbps (Modem)  115.2 Kbps (ISDN)  262.2 Kbps (Cable/DSL)  393.2 Kbps (Cable/DSL)  524.3 Kbps (Cable/DSL)  1.5 Mbps (T1)  10.5 Mbps (LAN) }, default: 10
#media.network.bandwidth:1.5 Mbps (T1)

# HTTP proxy host
# string, default: 
#media.network.http_proxy_host:

# HTTP proxy password
# string, default: 
#media.network.http_proxy_password:

# HTTP proxy port
# numeric, default: 80
#media.network.http_proxy_port:80

# HTTP proxy username
# string, default: 
#media.network.http_proxy_user:

# MMS protocol
# { auto  TCP  HTTP }, default: 0
#media.network.mms_protocol:auto

# automatically advance track/entry
# bool, default: 1
#media.vcd.autoadvance:1

# default type to use on VCD autoplay
# { track  entry  segment  playlist }, default: 3
#media.vcd.autoplay:playlist

# device used for VCD playback
# string, default: /dev/cdrom
media.vcd.device:

# position slider range
# { auto  track  entry }, default: 0
#media.vcd.length_reporting:auto

# show 'rejected' LIDs
# bool, default: 0
#media.vcd.show_rejected:0

# format string for stream comment field
# string, default: %P - Track %T
#media.vcd.comment_format:%P - Track %T

# debug flag mask
# numeric, default: 0
#media.vcd.debug:0

# format string for display banner
# string, default: %F - %I %N%L%S, disk %c of %C - %v %A
#media.vcd.title_format:%F - %I %N%L%S, disk %c of %C - %v %A

# v4l radio device
# string, default: /dev/v4l/radio0
#media.video4linux.radio_device:/dev/v4l/radio0

# v4l video device
# string, default: /dev/v4l/video0
#media.video4linux.video_device:/dev/v4l/video0

# device used for WinTV-PVR 250/350 (pvr plugin)
# string, default: /dev/video0
#media.wintv_pvr.device:/dev/video0

# path to RealPlayer codecs
# string, default: 
#decoder.external.real_codecs_path:

decoder.external.win32_codecs_path:/usr/lib/win32

# subtitle size
# { tiny  small  normal  large  very large  huge }, default: 1
#subtitles.separate.subtitle_size:small

# subtitle vertical offset
# numeric, default: 0
#subtitles.separate.vertical_offset:0

# font for subtitles
# string, default: sans
#subtitles.separate.font:sans

# encoding of the subtitles
# string, default: iso-8859-1
#subtitles.separate.src_encoding:iso-8859-1

# use unscaled OSD if possible
# bool, default: 1
#subtitles.separate.use_unscaled_osd:1

# default duration of subtitle display in seconds
# numeric, default: 4
#subtitles.separate.timeout:4

# frames per second to generate
# numeric, default: 10
#effects.goom.fps:10

# goom image height
# numeric, default: 240
#effects.goom.height:240

# goom image width
# numeric, default: 320
#effects.goom.width:320

# colorspace conversion method
# { Fast but not photorealistic  Slow but looks better }, default: 0
#effects.goom.csc_method:Fast but not photorealistic

# number of audio buffers
# numeric, default: 230
#engine.buffers.audio_num_buffers:230

# number of video buffers
# numeric, default: 500
#engine.buffers.video_num_buffers:500

# priority for a/52 decoder
# numeric, default: 0
#engine.decoder_priorities.a/52:0

# priority for bitplane decoder
# numeric, default: 0
#engine.decoder_priorities.bitplane:0

# priority for dts decoder
# numeric, default: 0
#engine.decoder_priorities.dts:0

# priority for dvaudio decoder
# numeric, default: 0
#engine.decoder_priorities.dvaudio:0

# priority for dxr3-mpeg2 decoder
# numeric, default: 0
#engine.decoder_priorities.dxr3-mpeg2:0

# priority for dxr3-spudec decoder
# numeric, default: 0
#engine.decoder_priorities.dxr3-spudec:0

# priority for faad decoder
# numeric, default: 0
#engine.decoder_priorities.faad:0

# priority for ffmpeg-wmv8 decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpeg-wmv8:0

# priority for ffmpegaudio decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpegaudio:0

# priority for ffmpegvideo decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpegvideo:0

# priority for flacdec decoder
# numeric, default: 0
#engine.decoder_priorities.flacdec:0

# priority for gsm610 decoder
# numeric, default: 0
#engine.decoder_priorities.gsm610:0

# priority for image decoder
# numeric, default: 0
#engine.decoder_priorities.image:0

# priority for mad decoder
# numeric, default: 0
#engine.decoder_priorities.mad:0

# priority for mpeg2 decoder
# numeric, default: 0
#engine.decoder_priorities.mpeg2:0

# priority for nsf decoder
# numeric, default: 0
#engine.decoder_priorities.nsf:0

# priority for pcm decoder
# numeric, default: 0
#engine.decoder_priorities.pcm:0

# priority for real decoder
# numeric, default: 0
#engine.decoder_priorities.real:0

# priority for realadec decoder
# numeric, default: 0
#engine.decoder_priorities.realadec:0

# priority for rgb decoder
# numeric, default: 0
#engine.decoder_priorities.rgb:0

# priority for speex decoder
# numeric, default: 0
#engine.decoder_priorities.speex:0

# priority for spucc decoder
# numeric, default: 0
#engine.decoder_priorities.spucc:0

# priority for spucmml decoder
# numeric, default: 0
#engine.decoder_priorities.spucmml:0

# priority for spudec decoder
# numeric, default: 0
#engine.decoder_priorities.spudec:0

# priority for spudvb decoder
# numeric, default: 0
#engine.decoder_priorities.spudvb:0

# priority for sputext decoder
# numeric, default: 0
#engine.decoder_priorities.sputext:0

# priority for theora decoder
# numeric, default: 0
#engine.decoder_priorities.theora:0

# priority for vorbis decoder
# numeric, default: 0
#engine.decoder_priorities.vorbis:0

# priority for yuv decoder
# numeric, default: 0
#engine.decoder_priorities.yuv:0

# media format detection strategy
# { default  reverse  content  extension }, default: 0
#engine.demux.strategy:default

# memcopy method used by xine
# { probe  libc }, default: 0
engine.performance.memcpy_method:libc

# percentage of discarded frames to tolerate
# numeric, default: 10
#engine.performance.warn_discarded_threshold:10

# percentage of skipped frames to tolerate
# numeric, default: 10
#engine.performance.warn_skipped_threshold:10

# allow implicit changes to the configuration (e.g. by MRL)
# bool, default: 0
#misc.implicit_config:0

---

### Post by DancingSun on 2005-08-26
[QUOTE=bagatonovic]This is not working for me.  I followed the guide exactly.  I was able to edit the config.  When I try to play a WMV, I can hear the sound, but nothing else.  Located below is my whole config file.  I want to point out that it keeps moving the line you want us to add over to the real media section.  No matter how many times I move the line to the bottom, it moves it up the the real section.  I also tried with gxine and same problem.

I am using essential-20050412.tar.bz2
I have extracted the contents to /usr/lib/win32
I noticed it kept the folder name of the archive, so I moved the files over to /usr/lib/win32 from /usr/lib/win32/essentiail-20050412/

Now I have to go hang with my wife or I'll be in trouble.  See you guys later.  And even though this didn't work for me, I totally respect you Tseliot.  You rule sir.

***EDIT*** LOL Some parts of the config turned into smiles!!! LOL
(...)[/QUOTE]
Ok, here's a tip, you'll need to use the "CODE" tags to get rid of those smilies.  Push the "#" button to insert the "CODE" tags.

Can you try to play a Quicktime movie?  Was the wmv file encoded in wmv3 (Windows Media 9)?

---

### Post by tseliot on 2005-08-27
[QUOTE=bagatonovic]This is not working for me.  I followed the guide exactly.  I was able to edit the config.  When I try to play a WMV, I can hear the sound, but nothing else.  Located below is my whole config file.  I want to point out that it keeps moving the line you want us to add over to the real media section.  No matter how many times I move the line to the bottom, it moves it up the the real section.  I also tried with gxine and same problem.[/QUOTE]
1) the fact that the line you add is being moved by xine is not a problem at all. I happened the same to me.

2) I think DancingSun hit the mark. I think you're trying to play a wmv9 (however the file extension is "wmv"). As I wrote at the end of the guide I didn't manage to make wmv9 play properly.

3) Please try to play an avi, or mpg, asf (or anything apart from wmv9) file and see if you can play it.

---

### Post by liquidfire on 2005-08-27
[QUOTE=tseliot]1) the fact that the line you add is being moved by xine is not a problem at all. I happened the same to me.

2) I think DancingSun hit the mark. I think you're trying to play a wmv9 (however the file extension is "wmv"). As I wrote at the end of the guide I didn't manage to make wmv9 play properly.

3) Please try to play an avi, or mpg, asf (or anything apart from wmv9) file and see if you can play it.[/QUOTE]
I've found another option  totem generates a config file similar too xine config in its own directory. I just copied that changed the name and added the lines. Its working now.

---

### Post by Xappe on 2005-09-22
another way is to put the files in ~/.gnome2/totem-addons , that's what I've always done (well, not on 64-bit systems, but I would guess there's no difference. It even works to a great extent on my ibook) :)

---

### Post by GTvulse on 2005-09-22
[QUOTE=liquidfire]Lol, when i try to install them i'm getting an error

I did sudo tar jxvf essential-20050412.tar.bz2 /usr/lib/win32
then it says /usr/lib/win32 not found in the archive  ](*,)[/QUOTE]

```
tar jxf essential-20050412.tar.bz2 **-C** /usr/lib/win32
``` certainly works.  :)

---

### Post by EPOX123 on 2005-10-09
Hi i just install Ubuntu 5.10 when i go to the terminal and do sudo apt-get install xine-ui ; totem-xine

I get an error:
////////////////////////////
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate
bash: totem-xine: command not found

The file is missing why do you have it and why dont i have it?
What can i do to make it work?

---

### Post by sanmadjack on 2005-10-20
I'm not so sure that installing these codecs is actualy doing anything. From what I've learned, 64-bit programs are incapable of using 32-bit libraries, which is what w32codecs contains. I might be wrong, but I want to test this theory out. Could someone point out a few videos on the net that I shouldn't be able to play without w32codecs that y'all can after having installed them on your 64-bit systems?

Also, for the guy above, in the **xine-ui ; totem-xine** part of your command, the ; means start a new command, just eliminate the ;. Also, Xine is not installable from a default Ubuntu install. You need to add the universe and multiverse repositories first. Check ubuntuguide.com on how to do that, the instructions there are still relevent to 5.10.

---

### Post by DancingSun on 2005-10-20
[QUOTE=sanmadjack]I'm not so sure that installing these codecs is actualy doing anything. From what I've learned, 64-bit programs are incapable of using 32-bit libraries, which is what w32codecs contains. I might be wrong, but I want to test this theory out. Could someone point out a few videos on the net that I shouldn't be able to play without w32codecs that y'all can after having installed them on your 64-bit systems?

Also, for the guy above, in the **xine-ui ; totem-xine** part of your command, the ; means start a new command, just eliminate the ;. Also, Xine is not installable from a default Ubuntu install. You need to add the universe and multiverse repositories first. Check ubuntuguide.com on how to do that, the instructions there are still relevent to 5.10.[/QUOTE]
If you can play quicktime and windows media 9 (identified as wmv3 codec) files then your win32codecs is working.

---

### Post by YR600 on 2005-10-24
Hi i've followed the instructions and totem still does not recognise any codecs. all the codecs are in the usr/lib/win32 folder.

Any advice im totally new to linux!

---

### Post by tseliot on 2005-10-25
[QUOTE=YR600]Hi i've followed the instructions and totem still does not recognise any codecs. all the codecs are in the usr/lib/win32 folder.

Any advice im totally new to linux![/QUOTE]

Check if you installed "xine-ui" and "totem-xine".

Try to open the file with Xine.

---

### Post by YR600 on 2005-10-25
how do i install xine-ui and totem-xine they are not in my apps list?

---

### Post by t_ras on 2005-10-26
Grate thing!!
but how do I make Xine defaul media player?

---

### Post by Vulpus on 2005-10-27
Thank you VERY much for this!  You have now removed the last reason I need XP for!:)

---

### Post by tseliot on 2005-10-27
[QUOTE=YR600]how do i install xine-ui and totem-xine they are not in my apps list?[/QUOTE]
Enable all the repositories (see the Unofficial Starter's guide) and open Synaptic/kynaptic, press "search" and put the names in that field. Then install them

---

### Post by tseliot on 2005-10-27
[QUOTE=t_ras]Grate thing!!
but how do I make Xine defaul media player?[/QUOTE]

In GNOME: right click on the file with the extension you want to open with xine (e.g. .avi or mpg, etc), "Properties", "Open with", and select the application you want (Xine).

Do it with every kind of file you want to open in Xine

---

### Post by tseliot on 2005-10-27
[QUOTE=Vulpus]Thank you VERY much for this!  You have now removed the last reason I need XP for!:)[/QUOTE]
This really makes me proud :) .

I really suffer when I have to use Winxp (on other computers, because I don't use it any more)

---

### Post by joris.brus on 2005-10-30
This doesn't work for me for some reason.

Xine always gives me the same error stating windows media is unsupported. 
even if I rename the while /usr/lib/win32 folder, making it non-existent, I get the same error and xine still plays sound but no video. It seems to make no difference whether that folder exists or not.
How does xine determine what codecs to use?

I really need this to work

---

### Post by tseliot on 2005-10-30
[QUOTE=joris.brus]This doesn't work for me for some reason.

Xine always gives me the same error stating windows media is unsupported. 
even if I rename the while /usr/lib/win32 folder, making it non-existent, I get the same error and xine still plays sound but no video. It seems to make no difference whether that folder exists or not.
How does xine determine what codecs to use?

I really need this to work[/QUOTE]
Ok, delete the folder (win32) and try this:

[http://www.ubuntuforums.org/showthread.php?t=81577]("http://www.ubuntuforums.org/showthread.php?t=81577")

---

### Post by joris.brus on 2005-10-30
I remember Plf being pretty reliable back when I used mandrake.
This repository doesn't work though, I'll give it a try again some other time. 
Does anyone know how Mandrake does with it's 64 bit version? same issues i imagine.

---

### Post by tseliot on 2005-10-30
[QUOTE=joris.brus]I remember Plf being pretty reliable back when I used mandrake.
This repository doesn't work though, I'll give it a try again some other time. 
Does anyone know how Mandrake does with it's 64 bit version? same issues i imagine.[/QUOTE]
You can try Easy Ubuntu (for Hoary?) and Automatix (for Breezy ONLY)

---

### Post by joris.brus on 2005-11-01
What does this mean? I set Xine as default application then double click a wmv file
I get the error

Cannot open 11921.wmv

The filename "11921.wmv" indicates that this file is of type "Microsoft WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Microsoft ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

---

### Post by tseliot on 2005-11-02
[QUOTE=joris.brus]What does this mean? I set Xine as default application then double click a wmv file
I get the error

Cannot open 11921.wmv

The filename "11921.wmv" indicates that this file is of type "Microsoft WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Microsoft ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.[/QUOTE]
It's weird, perhaps the file doesn't work. However I have some questions:

1) Did you rename the file as .asf (try it)?
2) Are you sure the file works (try it in Windows or in Mepis or PCLinuxOS Livecd and see if it works)
3) Do you use Ubuntu 64bit?

---

### Post by vgeddes on 2005-11-15
The Howto does not fix my sound problem with mp4's. This is  a quicktime format. Have any of you other AMD64 guys been able to get sound playback with mp4's using xine/totem-xine?

---

### Post by tseliot on 2005-11-16
[QUOTE=vgeddes]The Howto does not fix my sound problem with mp4's. This is  a quicktime format. Have any of you other AMD64 guys been able to get sound playback with mp4's using xine/totem-xine?[/QUOTE]
I knew that only wmv9 didn't work in 64bit systems. Maybe I'm wrong

---

### Post by Mike Eckman on 2005-12-17
I was hoping to bring this to the top again to see if anyone has made any progress in getting WMV9 files to play under Ubuntu 64?

I have all the other codecs working except these...

---

### Post by mural on 2007-01-24
Hi, 

I was not able to download anything from this site. I get the following error: The requested URL /homepage/design7/dload.html was not found on this server.

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the “essential codecs package”)

Will this also play *.rm videos.  Now I have to go back to XP to play them in Real Player.

Thanks

---

