---
title: "HOWTO: MPlayer"
date: 2005-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2005-01-02
[http://www.mplayerhq.hu/homepage/design7/info.html](http://www.mplayerhq.hu/homepage/design7/info.html)

From disposable's thread [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) 

**[COLOR=Red]Be aware that *MPlayer* has no support for DVD menus, so you cannot access the additional features of your DVD with MPlayer [/COLOR](like Chapter / Scene selection, Languages, Sound, Zoom, Extras, etc. [COLOR=Blue]If you wish to have DVD Menu support, install Xine or Ogle.[/COLOR])**
[COLOR=Red]
**For a different version using "Sarge" codecs (more up to date) go to page 5.**[/COLOR]

Copy/Paste the code into your favourite editor, save it as [COLOR=RED]mplayer.sh[/COLOR] (Find an Attachment at bottom).
```

sudo mkdir mplyr
cd mplyr
# get & install Ubuntu packages
apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y
#
# get mplayer program
wget http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5try2.tar.bz2
#
# get codecs
wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2
#
# get fonts
wget http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2 
#
# get skin (my default skin is "phony")
# ***********************************
# go to http://www.mplayerhq.hu/homepage/design7/dload.html to choose a 
# different skin. Right Click your favourite *** [HTTP] *** skin, Copy Link Location, 
# paste it over the following line after wget)
# ***********************************
wget http://ftp5.mplayerhq.hu/mplayer/Skin/phony-1.1.tar.bz2 
#
tar -xjf MPlayer-1.0pre5try2.tar.bz2
cd MPlayer-1.0pre5try2
./configure --enable-gui
make
make install
#
cd ..
tar -xjf essential-20041107.tar.bz2
mkdir -p /usr/local/lib/codecs
cp essential-20041107/* /usr/local/lib/codecs/
#
tar -xjf font-arial-iso-8859-1.tar.bz2
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
#
# ***********************************
# If you decide on a different skin, you'll have to change the name "phony" 
# (after tar -xfj) to your skin file name 
# ***********************************
tar -xjf phony-1.1.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
# ***********************************
# change the word "phony" with the name of your preferred skin
# ***********************************
cp -r phony/* /usr/local/share/mplayer/Skin/default/
#
cp MPlayer-1.0pre5try2/etc/* /usr/local/etc/mplayer/
#
# get dvd codecs
wget http://www.las.ic.unicamp.br/pub/debian.d/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb
#
# install dvd codecs
dpkg -i libdvdcss2_1.2.8-0.0_i386.deb 
#
cd ..
# start gmplayer program
gmplayer
#
exit

```

Now exectute the shell script:
```
sudo sh mplayer.sh
```
If you see the program start up - [COLOR=Red]SUCCESS[/COLOR].
Insert a DVD. Push the[COLOR=Red] DVD[/COLOR] play button (not the |> button).
The movie should start to play. Check the sound quality. Close out the MPlayer program. The Root Terminal window will close.

To put MPlayer into your Applications Menu:
```

[COLOR=Blue]Applications[/COLOR] -> [COLOR=Blue]Multimedia[/COLOR] -> (go to the right pane, right click) -> [COLOR=Blue]Entire Menu[/COLOR] -> [COLOR=Blue]Add New Item To This Menu[/COLOR] ->
Name: [COLOR=Red]MPlayer[/COLOR]
Generic Name: [COLOR=Red]Media Player[/COLOR]
Comment: [COLOR=Red]The Media Player[/COLOR]
Command: [COLOR=Red]/usr/local/bin/gmplayer[/COLOR]

Hit the "[COLOR=Red]No Icon[/COLOR]" button

Find the "[COLOR=Blue]media-player-48.png[/COLOR]" picture, select it, hit the "[COLOR=Red]OK[/COLOR]" button.
Hit the "[COLOR=Red]OK[/COLOR]" button

```

.

---

### Post by wallijonn on 2005-01-02
Post Clean Up:

Since we used a sudo batch (shell) script, the created mplyr directory will have the owner as root.

We need to change it back to the user.

Open a Root Terminal and issue the following command, where "usrname" is your user account name.

```

chown -R usrname mplyr

```

This will allow you to delete any files that need deleting through the Nautilus  desktop GUI. You may not want to delete the .bz2 & .deb files, just delete the folders that were created and backup the compressed source files for future use. You could then issue commands manually, negating the need to download the files again.

```

tar -xjf MPlayer-1.0pre5try2.tar.bz2
cd MPlayer-1.0pre5try2
./configure --enable-gui
make
make install
cd ..
tar -xjf essential-20041107.tar.bz2
mkdir -p /usr/local/lib/codecs
cp essential-20041107/* /usr/local/lib/codecs/
tar -xjf font-arial-iso-8859-1.tar.bz2
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
tar -xjf phony-1.1.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
cp -r phony/* /usr/local/share/mplayer/Skin/default/
cp MPlayer-1.0pre5try2/etc/* /usr/local/etc/mplayer/
dpkg -i libdvdcss2_1.2.8-0.0_i386.deb 

```

---

### Post by kral on 2005-01-02
very fine HowtO :D

---

### Post by wallijonn on 2005-01-02
Thank Disposable, he did all the work. I'm just trying to clean up the code a little, make it almost painless by making it into a shell script. 

The only hard part will be for people to be patient as it does its thing. That and their having to edit the shell script should they decide on a different player skin.

---

### Post by kibbea on 2005-01-05
That was a great script.  It executed and the MPlayer came up and played a non- commercial DVD.  I put in a commercial DVD and it gave me an error.
"Playing /media/cdrom0/VIDEO_TS/VIDEO_TS.VOB.
Seek failed" error.

Any idea on how to go about finding the problem.  It would seem that libdvdcss2 was set up.  I saved some of the output to the terminal window from the executing script.
This is what it said when it reached the part about the libdvdcss2.


"Selecting previously deselected package libdvdcss2.
(Reading database ... 67205 files and directories currently installed.)
Unpacking libdvdcss2 (from libdvdcss2_1.2.8-0.0_i386.deb) ...
Setting up libdvdcss2 (1.2.8-0.0) ...

MPlayer 1.0pre5try2-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred 1667 MHz (Family: 6, Stepp ing: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE"

Reading config file /usr/local/etc/mplayer/mplayer.conf: No such file or directo ry
Creating config file: /home/andrei/.mplayer/config
Reading config file /home/andrei/.mplayer/config
[cfg] read config file: /home/andrei/.mplayer/gui.conf
Reading config file /home/andrei/.mplayer/gui.conf: No such file or directory
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
Disabling DPMS
Reading /home/andrei/.mplayer/codecs.conf: Can't open '/home/andrei/.mplayer/cod ecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: 73 audio & 180 video codecs
font: can't open file: /home/andrei/.mplayer/font/font.desc
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using Linux hardware RTC timing (1024Hz).
Can't open input config file /home/andrei/.mplayer/input.conf: No such file or d irectory
Input config file /usr/local/etc/mplayer/input.conf parsed: 53 binds
SKIN dir 1: '/home/andrei/.mplayer/Skin'
SKIN dir 2: '/usr/local/share/mplayer/Skin'
font: can't open file: /home/andrei/.mplayer/font/font.desc
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)

I don't know if this gives any hints as to what may be wrong but since it works with a regular DVD and not a commercial one I would think that something may be wrong with the libdvdcss2.

I am running Warty.
 
Thanks for any help.

---

### Post by wallijonn on 2005-01-06
First I would try another DVD to make sure that it isn't a bad DVD.

Next you will probably want to manually re-install from another directory (see the second script), from a Root Terminal. Chances are that they did not execute because the mplyr directory was locked. Sometimes you have to log out and log back in when an application gets locked. Check every file in the mplyr directory and sub directories. Are there any emblems attached to any files? If there is then you'll need to ```
chown -R andrei mplyr
```

I believe the .deb should still be in /var/cache/apt/archives. If not, download them manually and save them with all the other .bz2 and .deb packages. Then do a manual re-installation.

btw, it looks like the codecs did install correctly. It started to mess up when it tried to access your hidden mplayer folder, .mplayer.

download the codecs to the same directory where you have all the mplayer associated directories, like mplyr, then open a Root Terminal and cd over to mplyr:
```

cd MPlayer-1.0pre5try2
./configure --enable-gui
make
make install
cd ..
mkdir -p /usr/local/lib/codecs
cp essential-20041107/* /usr/local/lib/codecs/
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
mkdir -p /usr/local/share/mplayer/Skin/default
cp -r phony/* /usr/local/share/mplayer/Skin/default/
**[COLOR=Red]cp MPlayer-1.0pre5try2/etc/* /usr/local/etc/mplayer/[/COLOR]**
dpkg -i libdvdcss2_1.2.8-0.0_i386.deb

```

btw, you did go to your desktop, right click the dvd and "eject" after stopping MPlayer, right?

---

### Post by kibbea on 2005-01-06
Wallijonn:  Thanks for the quick reply.  Before I venture off to do a manual installation I would like to make sure that I understand your instructions.  Following your script was a no brainer, but doing this by hand for me is not something I am experienced in doing.
However, your instructions are very explicit and should not be hard to follow.

Firstly, I would like to answer some of the questions you raised.  I did try another DVD and received the same message.  The non-commercial DVD works and the two movie DVDs do not work.  You also asked if I ejected the DVD from the Desktop after stopping MPlayer and I did do that when I was done trying to get it to play.  There is however, some unusual behavior with MPlayer.  When MPlayer is running and I insert a DVD, Nautilus brings up a window with the contents of the DVD.  MPlayer does not see the DVD until I press the Eject button on the GUI and a window appears that allows me to browse to the cdrom directory and manually load the the .VOB file.  The eject button on the GUI does not seem to work as one would expect.  Nevertheless, I would like to try the manual reinstallation to see what will happen after a new install.

Which files in the /var/cache/apt/archives directory should I try to re-install?  Are they  .deb files that were listed in your script?  Here are the files that are in my mplyr directory.

essential-20041107.tar.bz2     MPlayer-1.0pre5try2.tar.bz2
font-arial-iso-8859-1.tar.bz2  phony-1.1.tar.bz2
libdvdcss2_1.2.8-0.0_i386.deb

When I re-install I will have to use the "dpkg -i" command for the .deb files, right?.  Will it install if they have already been installed?  Do I need to uninstall anything first, or is there a way to force them to install over themselves?

Lastly, I hope you don't take offense to my having so many questions, but if I don't know something I can't think of anything else to do other than ask questions.

Thanks,

---

### Post by wallijonn on 2005-01-06
kibbea,

Okay, the first thing to do when you insert a DVD and Totem / Nautilus pops up a window listing all the files (vobs, etc.) is to _close that window_. 

Next start up MPlayer.

No matter what the controls say on any player skin (and this goes for Xine, also), right click on the dvd player. A side menu bar should come up. [COLOR=Red]Open -> Play DVD [/COLOR] or [COLOR=Red]DVD -> Open Disc[/COLOR]. 

------------------------------------------------------------------------------------------------------------

You can do a google search for [COLOR=Blue]libdvdcss2_1.2.8-0.0_i386.deb[/COLOR]. Once you find a site you can download it from,  download it, then open a Root Terminal, change directory over to that folder, then you can [COLOR=Red]dpkg -x libdvdcss2_1.2.8-0.0_i386.deb .[/COLOR] . That period after the file name is very important. It means "to here". This will create a folder called "usr". Inside this folder will be two other folders: "lib" and "share". You will copy the contents of "lib" to "/usr/lib" and copy the contents of "share" to "/usr/share".

So, let's say you create a folder called "test" in your home directory. You down load the libdvdcss file to a certain folder. You copy or move that file to your test folder.

You then open a root terminal and:

```

cd test
dpkg -x  libdvdcss2_1.2.8-0.0_i386.deb .
[COLOR=Red]cd usr
cd lib
cp * /usr/lib
cd ..
cd share
cd bug
cd libdvdcss
mkdir /usr/share/bug/libdvdcss
cp * usr/share/bug/libdvdcss
cd ..
cd ..
cd doc
cd libdvdcss
mkdir /usr/share/doc/libdvdcss2 
cp * /usr/share/doc/libdvdcss2 [/COLOR]
cd ..
cd ..
cd ..
cd ..

```
exit

That is basically what [COLOR=Red]dpkg -i libdvdcss2_1.2.8-0.0_i386.deb [/COLOR] does (in the color red, above).

If you were doing it for the first ttime you would then issue the "mkdir" commands. If you were just re-installing it then you would omit the "mkdir" commands.

[quote=kibbea]Will it install if they have already been installed?[/QUOTE]
Yes

[quote=kibbea]Do I need to uninstall anything first?[/quote]
No

[quote=kibbea]Is there a way to force them to install over themselves?[/quote]
Root Terminal copy commands or just install them via [COLOR=Red]dpkg -i[/COLOR].

---

### Post by wallijonn on 2005-01-06
You can download extra skins.

Untar or unzip them. Then copy them (the whole folders and their contents) to /usr/local/share/mplayer/Skin/

When you start MPlayer, right click, "Skin browser", select your new skin, ok.

---

### Post by madzzoni on 2005-01-17
Hi there.[COLOR=Red]
Update: I'll do a dist-upgrade and tried one more, then i get the missing files but:[/COLOR]
It seems to be a very nice script, but i won't work for me, i can't start the (g)mplayer.

OK i fixed this problem, i reinstalled the whole Ubuntu, and this time only use the Ubuntu mirrors in source.list for needed packages and upgrades. 
The script work perfectly this time... Big thanks!

My only problem now is, that since i don't use apt-get for install, the mplayer isn't reconized as installed in the package-list when updated. 
That means, if i try too get the mplayerplug-in, apt want too install mplayer-custom too.
I don't think this is good. :-? 
Do i have to manuelly install mplayerplug-in too, or is there a way of telling apt about mplayer?

---

### Post by madzzoni on 2005-01-20
UPDATE: I finally installed mplayerplug-in via apt-get and accept that it want too install mplayer-custom too.
... and now it all works perfect.
I can watch streaming video and listen to varius net-radio stations with mplayerplug-in and the gmplayer stil works for video.

---

### Post by Quest-Master on 2005-01-21
Ah, I didn't know you could do that madzzoni. I just compiled my mplayer-plugin. Works fabulously as well as this shell script. :D

---

### Post by ackbar on 2005-01-23
Hello all,
The HOWTO is great, no problems installing mplayer... wonderful! Thanks a lot.
However, I have a problem when trying to play a .mkv file in mplayer.
The video works fine, but in the terminal I get this message for audio:

Requested audio codec family [faad] (afm=faad) not available.
Enable it at compilation.
Cannot find codec for audio format 0X4134504D
Read DOCS/HTML/en/codecs.html!

Which I proceeded to do, but as its a pretty specific error (and I'm not knowledgeable about codecs and such) I couldn't help myself there.

Google tells me (from the codec status table at mplayerhq.hu):

FAAD AAC (MPEG2/MPEG4 Audio) decoder
0x6134706D
0x4134504D
libfaad2

From some redhat help page I got the hint to get the libfaad2 audio decoder from Synaptic (which I then did... yeah so I'm slow :D  oh also I found the info on AAC and  faad2 in the codecs.html file as well when I looked the second time).

So I installed libfaad2, and it should now work, right? hopefully...
well.. nope. I get the same error.

So do I need to compile mplayer again, or does libfaad2 not give me all of faad2, or am I just really dumb?
Any help would be greatly appreciated :D
Cheers.

Edit: btw its anime that I'm trying to watch, and subs don't appear to be working either.  Is .mkv just not a supported filetype?

---

### Post by ow50 on 2005-01-23
[QUOTE=ackbar]Edit: btw its anime that I'm trying to watch, and subs don't appear to be working either.  Is .mkv just not a supported filetype?[/QUOTE]

Matroska is fully supported, assuming you have the required codecs installed. To cycle through the subtitle tracks avalable on the matroska file, press "b" or "j" (assuming you haven't customized the keyboard shortcuts). The keyboard shortcuts are listed in the mplayer man pages.

---

### Post by apoc on 2005-01-23
[QUOTE=wallijonn]You can download extra skins.

Untar or unzip them. Then copy them (the whole folders and their contents) to /usr/local/share/mplayer/Skin/

When you start MPlayer, right click, "Skin browser", select your new skin, ok.[/QUOTE]

I have got that, and some extre skins in there, but next time I start mplayer it reverts back to the default skin.. if its impossible so save the selected skin how do I make another one default?

Btw, great howto, thanks alot :)

---

### Post by wallijonn on 2005-01-23
Ackbar,

In your case you may wish to download & install the "all" codecs package instead of the "essential" codecs package. It have what you are looking for.

**apoc**,
You'd probably have to do it the hard way and copy the skin to the default folder. I've not had that problem with my skin. Is there a "set to default" button? (I'm on W2KP right now so I can't fire up Ubuntu).

---

### Post by clparker on 2005-01-24
FATAL ERROR!
 Error opening/initializing the selected video_out (-vo) device.
 
 It wont play any video, nothing.

---

### Post by Perfect Storm on 2005-01-24
Did Mplayer show some error doing the compiling?

Try reinstall the codecs.

---

### Post by clparker on 2005-01-24
No, it just does that right away but if i switch drivers it will play just about anything, however it wont remember to use that driver after i close and reopen Mplayer

---

### Post by Perfect Storm on 2005-01-24
Which version of Mplayer do you use? 

You can change the stuff in mplayer.conf

I think it's in /home/<username>/.mplayer

I can't be more specific because I don't have mplayer installed at the moment


.:=The AI Dude=:.

---

### Post by ow50 on 2005-01-24
[QUOTE=clparker]No, it just does that right away but if i switch drivers it will play just about anything, however it wont remember to use that driver after i close and reopen Mplayer[/QUOTE]

Copy '/usr/local/etc/mplayer/example.conf' to '~/.mplayer/config' and edit the file to your liking. I use the line 'vo=xv' to specify the video output.

I you use gmplayer and the preferences window, the settings should be remembered and stored in '~/.mplayer/gui.conf'. I have there the line 'vo_driver = "xv"'.

---

### Post by clparker on 2005-01-25
No Dice, I copied the file, and edited it, and changed it to the driver I need and i wont change to VO=GL2

---

### Post by nocturn on 2005-01-25
[QUOTE=clparker]No Dice, I copied the file, and edited it, and changed it to the driver I need and i wont change to VO=GL2[/QUOTE]

I followed the HOWTO and it works great, thanks.

I changed one step however, I used checkinstall instead of make install to get a Debian package.

---

### Post by senectus on 2005-01-29
Updated to show new versions (and and I prefer "blue" skin) as of 30 jan 2005 GMT +8
```
sudo mkdir mplyr
cd mplyr
# get & install Ubuntu packages
apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y
#
# get mplayer program
wget http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre6a.tar.bz2
#
# get codecs
wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050115.tar.bz2
#
# get fonts
wget http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2 
#
# get skin (my default skin is "blue")
# ***********************************
# go to http://www.mplayerhq.hu/homepage/design7/dload.html to choose a 
# different skin. Right Click your favourite *** [HTTP] *** skin, Copy Link Location, 
# paste it over the following line after wget)
# ***********************************
wget http://ftp5.mplayerhq.hu/mplayer/Skin/Blue-1.4.tar.bz2
#
tar -xjf MPlayer-1.0pre6a.tar.bz2
cd MPlayer-1.0pre6a
./configure --enable-gui
make
make install
#
cd ..
tar -xjf essential-20050115.tar.bz2
mkdir -p /usr/local/lib/codecs
cp essential-20050115/* /usr/local/lib/codecs/
#
tar -xjf font-arial-iso-8859-1.tar.bz2
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
#
# ***********************************
# If you decide on a different skin, you'll have to change the name "phony" 
# (after tar -xfj) to your skin file name 
# ***********************************
tar -xjf Blue-1.4.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
# ***********************************
# change the word "blue" with the name of your preferred skin
# ***********************************
cp -r Blue/* /usr/local/share/mplayer/Skin/default/
#
cp MPlayer-1.0pre6a/etc/* /usr/local/etc/mplayer/
#
# get dvd codecs
wget http://www.las.ic.unicamp.br/pub/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb
#
# install dvd codecs
dpkg -i libdvdcss2_1.2.8-0.0_i386.deb 
#
cd ..
# start gmplayer program
gmplayer
#
exit
```

---

### Post by rapala61 on 2005-02-02
wouldnt it be better to firs install the codecs before installing mplayer,  that would make mplayer compile with support for the installed codecs .. right??

---

### Post by ctt1wbw on 2005-02-02
Yes, according to MPlayer's website, you compile and install the codecs first, then the player itself.

---

### Post by Eastlake on 2005-02-02
for those who hav already installed the w32codecs pkg (ubuntu unofficial guide) can we just compile mplayer using --with-codecsdir=/usr/lib/win32 and forget about install the essencial pkg.. ?

and.. do we really need to install all of those pkgs?! manpages-dev.. x-window-system-dev... why? R they required to install mplayer?

tks in advnc..


east.

---

### Post by rapala61 on 2005-02-02
[QUOTE=Eastlake]for those who hav already installed the w32codecs pkg (ubuntu unofficial guide) can we just compile mplayer using --with-codecsdir=/usr/lib/win32 and forget about install the essencial pkg.. ?

and.. do we really need to install all of those pkgs?! manpages-dev.. x-window-system-dev... why? R they required to install mplayer?

tks in advnc..


east.[/QUOTE]

i was wondering that as well.. pesonally i didnt install x-window-dev... and no problems that i can tell with mplayer..

---

### Post by Caesar on 2005-02-06
Does this script works for PPC-Ubuntu users too?

---

### Post by sdn on 2005-02-06
That's really cool man! Thank you so much for the script....but i don't know why, but it doesn't run on my ibook.

I have tried it on my ibook, and sure it doesn't work. So i forward you the question of Caesar:

Does this script works for PPC-Ubuntu users too?

---

### Post by Caesar on 2005-02-07
[QUOTE=sdn]That's really cool man! Thank you so much for the script....but i don't know why, but it doesn't run on my ibook.

I have tried it on my ibook, and sure it doesn't work.[/QUOTE]

Thanks, i'm going to dl and compile everithing from zero. Actually i've successfully installed VLC and it works quite well.

I want to test mplayer too... just to see which one runs best on my oldy iBook :D

---

### Post by DJ_Max on 2005-02-07
I can tell by looking at th script it won't for for the PPC, since you need different codecs, PPC users can't use the "essential" codecs, you have to use "XAnim PPC". If I have sometime I'll make a script, in either Python or plain shell.

---

### Post by Arktis on 2005-02-08
I just wanted to say that I have a problem with being able to save the settings for mplayer too.  My solution was to run sudo gmplayer and then make the needed settings changes, and then they save just fine.

---

### Post by Perfect Storm on 2005-02-08
Try look in /home/<username>/.mplayer check if there are some conf files there. Eg. mplayer.conf

If not you have to make one or copy it from mplayer root folder.

---

### Post by grakhul on 2005-02-08
[QUOTE=wallijonn]Post Clean Up:

Since we used a sudo batch (shell) script, the created mplyr directory will have the owner as root.

We need to change it back to the user.

Open a Root Terminal and issue the following command, where "usrname" is your user account name.

```

chown -R usrname mplyr

```

This will allow you to delete any files that need deleting through the Nautilus  desktop GUI. You may not want to delete the .bz2 & .deb files, just delete the folders that were created and backup the compressed source files for future use. You could then issue commands manually, negating the need to download the files again.

```

tar -xjf MPlayer-1.0pre5try2.tar.bz2
cd MPlayer-1.0pre5try2
./configure --enable-gui
make
make install
cd ..
tar -xjf essential-20041107.tar.bz2
mkdir -p /usr/local/lib/codecs
cp essential-20041107/* /usr/local/lib/codecs/
tar -xjf font-arial-iso-8859-1.tar.bz2
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
tar -xjf phony-1.1.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
cp -r phony/* /usr/local/share/mplayer/Skin/default/
cp MPlayer-1.0pre5try2/etc/* /usr/local/etc/mplayer/
dpkg -i libdvdcss2_1.2.8-0.0_i386.deb 

```[/QUOTE]

I dont like the mplyr directory on my desktop.  Can I delete it if I want to?  I did a "locate mplayer" and all the neccessary files seemed to be installed in other directories.  By the way thanks, wallijonn.  On the first try executing your scirpt worked like a charm.  I had MPlayer working, but couldn't get GMplayer to work at all.

---

### Post by Arktis on 2005-02-10
You can definately delete the mplyr folder; it's totally safe and it certainly won't break MPlayer.

---

### Post by RastaMahata on 2005-02-10
How could I enable SMB support in mplayer? :S
And maybe have it with gtk2?

---

### Post by alexrait1 on 2005-02-12
I didn't like this tutorial... Why? Because it says to install  the mplayer in a dirty way, so that one won't be able to delete it afterwards (or to upgrade it).
The best way is to install mplayer is to create a debian package. When you untar the mplayer archive, you can see there is already a debian folder inside it, so all the work to be done hence is simple enough for anyone:
apt-get install fakeroot
cd MPlayer-*******/
dpkg-buildpackage -rfakeroot

and that's it, now you have a debian package ready to install with 
dpkg -i packagename

---

### Post by wallijonn on 2005-02-18
alex,

I'll have to try your method tomorrow. Could you be more verbose with your instructions? I don't remember seeing a Debian package in the downloaded tar file.

---

### Post by Avi on 2005-02-18
Excellent, excellent job.
Thank you so much!

One quick comment though - Although mplayer opened-up, I've noticed that the last stage of installation issued:
```
[http://www.las.ic.unicamp.br/pub/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb](http://www.las.ic.unicamp.br/pub/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb)
           => `libdvdcss2_1.2.8-0.0_i386.deb'
Resolving [www.las.ic.unicamp.br](www.las.ic.unicamp.br)... 143.106.60.116
Connecting to [www.las.ic.unicamp.br](www.las.ic.unicamp.br)[143.106.60.116]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
02:22:16 ERROR 404: Not Found.
```

After a quick lookup, I've discovered that there was a small change with the URL. It's now:
http://www.las.ic.unicamp.br/pub/**debian.d**/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb

So I guess there were a number of people that didn't even notice this was lacking in the installation... You should probably update the HowTo...

And thanks again!

---

### Post by Avi on 2005-02-18
Oh and another question:
Why install libdvdcss2_1.2.8-0.0?
What's wrong with libdvdcss2_1.2.8-sarge0.0?

(The log defines this as "downgrading")

Thanks.

---

### Post by ixus_123 on 2005-02-18
[QUOTE=wallijonn]alex,

I'll have to try your method tomorrow. Could you be more verbose with your instructions? I don't remember seeing a Debian package in the downloaded tar file.[/QUOTE]

I got this from the Mplayer manual located on their site.  I was actually looking to see if I could find out how to ecode to H.264 with mencoder. ..

> **6.1.1. Debian packaging**

To build a Debian package, run the following command in the MPlayer source directory:

*fakeroot debian/rules binary*

If you want to pass custom options to configure, you can set up the DEB_BUILD_OPTIONS environment variable. For instance, if you want GUI and OSD menu support you would use:

*DEB_BUILD_OPTIONS="--enable-gui --enable-menu" fakeroot debian/rules binary*

You can also pass some variables to the Makefile. For example, if you want to compile with gcc 3.4 even if it's not the default compiler:

*CC=gcc-3.4 DEB_BUILD_OPTIONS="--enable-gui" fakeroot debian/rules binary*

To clean up the source tree run the following command:

*fakeroot debian/rules clean*

As root you can then install the .deb package as usual:

*dpkg -i ../mplayer_version.deb*

Christian Marillat has been making unofficial Debian packages of MPlayer, MEncoder and our bitmap fonts for a while, you can (apt-)get them from his homepage.

---

### Post by wallijonn on 2005-02-21
[QUOTE=Avi]Why install libdvdcss2_1.2.8-0.0?
What's wrong with libdvdcss2_1.2.8-sarge0.0?

(The log defines this as "downgrading")[/QUOTE]

It just happened that that is the one which I found. (I actually got the link from a posted desktop picture. :wink: )Have you tried the Sarge package and found it to work okay? [http://ftp2.de.freesbie.org/mirror/mplayer/testing/main/binary-i386/](http://ftp2.de.freesbie.org/mirror/mplayer/testing/main/binary-i386/)

"Sarge" to me is the same as "Hoary". I don't like to mix Hoary and Warty so I also would not like to mix Sarge and Woody. A Sarge script file follows below. I will also be trying the pre6a version versus the pre5try2 version.

I have never had any success downloading from nerim.net; at least adding the ftp to my sources.list didn't help. So I had to google for that file and found listings like this:

[http://sft.if.usp.br/debian-marillat/dists/stable/main/binary-i386/](http://sft.if.usp.br/debian-marillat/dists/stable/main/binary-i386/) 

You may want to scroll down that list. :wink: After all, someone may want to download and play with an mplayer-586, mplayer-686, mplayer-k7 .deb version, transcode or w32codec file. Too bad all those packages have dependency problems, as alexrait1 said.

So, basically I didn't even know that a Sarge version was available. :-\"

---

### Post by wallijonn on 2005-02-21
[QUOTE=Avi] there was a small change with the URL. It's now:

[http://www.las.ic.unicamp.br/pub/](http://www.las.ic.unicamp.br/pub/)**debian.d**/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb

[/QUOTE]

Avi, thanks. Good 'looking out'. I've updated the script. (Has anyone tried the pre6 instead of the pre5a files?)

[edit]
Whatever you do - if you open up the preferences and you go to the video tab, do NOT select any of the drivers (even to check to see if you can configure the driver). To do so will cause it to fail to find and open the correct video device. You should select the top driver listed. Then MPlayer should work fine.


.

---

### Post by wallijonn on 2005-02-21
[COLOR=Red][SIZE=4]**Sarge Version**[/SIZE][/COLOR]:

[http://www.mplayerhq.hu/homepage/design7/info.html](http://www.mplayerhq.hu/homepage/design7/info.html)

From disposable's thread [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) 

**[COLOR=Red]Be aware that *MPlayer* has no support for DVD menus, so you cannot access the additional features of your DVD with MPlayer [/COLOR](like Chapter / Scene selection, Languages, Sound, Zoom, Extras, etc. [COLOR=Blue]If you wish to have DVD Menu support, install Xine or Ogle.[/COLOR])**

Copy/Paste the code into your favourite editor, save it as [COLOR=RED]mplayer.sh[/COLOR] 
```

#
sudo mkdir mplyr
cd mplyr
# get & install Ubuntu packages
apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y
#
# get [COLOR=Red]SARGE[/COLOR] dvd codecs
wget http://ftp2.de.freesbie.org/mirror/mplayer/testing/main/binary-i386/libdvdcss2_1.2.8-sarge0.0_i386.deb
#
# install dvd codecs
dpkg -i libdvdcss2_1.2.8-sarge0.0_i386.deb
#
# get mplayer program
wget http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5try2.tar.bz2
#
# get codecs
wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2
#
# get fonts
wget http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2 
#
# get skin (my default skin is "phony")
# ***********************************
# go to http://www.mplayerhq.hu/homepage/design7/dload.html to choose a 
# different skin. Right Click your favourite *** [HTTP] *** skin, Copy Link Location, 
# paste it over the following line after wget)
# ***********************************
wget http://ftp5.mplayerhq.hu/mplayer/Skin/[COLOR=Blue]phony-1.1[/COLOR].tar.bz2 
#
tar -xjf MPlayer-1.0pre5try2.tar.bz2
cd MPlayer-1.0pre5try2
./configure --enable-gui
make
make install
#
cd ..
tar -xjf essential-20041107.tar.bz2
mkdir -p /usr/local/lib/codecs
cp essential-20041107/* /usr/local/lib/codecs/
#
tar -xjf font-arial-iso-8859-1.tar.bz2
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
#
# ***********************************
# If you decide on a different skin, you'll have to change the name "phony" 
# (after tar -xfj) to your skin file name 
# ***********************************
tar -xjf [COLOR=Blue]phony-1.1[/COLOR].tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
# ***********************************
# change the word "phony" with the name of your preferred skin
# ***********************************
cp -r [COLOR=Blue]phony[/COLOR]/* /usr/local/share/mplayer/Skin/default/
#
cp MPlayer-1.0pre5try2/etc/* /usr/local/etc/mplayer/
#
cd ..
# start gmplayer program
gmplayer
#
exit

```

Now exectute the shell script:
```
sudo sh mplayer.sh
```
If you see the program start up - [COLOR=Red]SUCCESS[/COLOR].
Insert a DVD. Push the[COLOR=Red] DVD[/COLOR] play button (not the |> button).
The movie should start to play. Check the sound quality. Close out the MPlayer program. The Root Terminal window will close.

To put MPlayer into your Applications Menu:
```

[COLOR=Blue]Applications[/COLOR] -> [COLOR=Blue]Multimedia[/COLOR] -> (go to the right pane, right click) -> [COLOR=Blue]Entire Menu[/COLOR] -> [COLOR=Blue]Add New Item To This Menu[/COLOR] ->
Name: [COLOR=Red]MPlayer[/COLOR]
Generic Name: [COLOR=Red]Media Player[/COLOR]
Comment: [COLOR=Red]The Media Player[/COLOR]
Command: [COLOR=Red]/usr/local/bin/gmplayer[/COLOR]

Hit the "[COLOR=Red]No Icon[/COLOR]" button

Find the "[COLOR=Blue]media-player-48.png[/COLOR]" picture, select it, hit the "[COLOR=Red]OK[/COLOR]" button.

```

Post Clean Up:

Since we used a sudo batch (shell) script, the created mplyr directory will have the owner as root.

We need to change it back to the user.

Open a Root Terminal and issue the following command, where "usrname" is your user account name.

```

chown -R usrname mplyr

```

This will allow you to delete any files that need deleting through the Nautilus  desktop GUI. You may not want to delete the .bz2 & .deb files, just delete the folders that were created and backup the compressed source files for future use. You could then issue commands manually, negating the need to download the files again.

.

---

### Post by chapterthree on 2005-02-21
Edit: Error on my part :)

---

### Post by uberlinux on 2005-02-23
didnt work for me

```
 MPlayer 1.0pre5try2-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred 800.4 MHz (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE

Reading config file /usr/local/etc/mplayer/mplayer.conf: No such file or directory
Reading config file /root/.mplayer/config
[cfg] read config file: /root/.mplaMPlayer 1.0pre5try2-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred 800.4 MHz (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE

Reading config file /usr/local/etc/mplayer/mplayer.conf: No such file or directory
Reading config file /root/.mplayer/config
[cfg] read config file: /root/.mplayer/gui.conf
Reading config file /root/.mplayer/gui.conf: No such file or directory
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

vo: couldn't open the X11 display (:0.0)!
MPlayer GUI requires X11.
Reading /root/.mplayer/codecs.conf: Can't open '/root/.mplayer/codecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: 73 audio & 180 video codecs
Usage:   mplayer [options] [url|path/]filename
yer/gui.conf
Reading config file /root/.mplayer/gui.conf: No such file or directory
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

vo: couldn't open the X11 display (:0.0)!
MPlayer GUI requires X11.
Reading /root/.mplayer/codecs.conf: Can't open '/root/.mplayer/codecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: 73 audio & 180 video codecs
Usage:   mplayer [options] [url|path/]filename

```

---

### Post by RastaMahata on 2005-02-25
so...
how can I uninstall it?

---

### Post by wallijonn on 2005-02-25
In my SPM it showed 1.0pre5try2-3.3.4 as installed and I could click it to uninstall it.

Which version failed, the one in the front page or the Sarge version? If it is the Sarge version, then just use the one from the front page. It should rewrite everything.

---

### Post by RastaMahata on 2005-02-25
[QUOTE=wallijonn]In my SPM it showed 1.0pre5try2-3.3.4 as installed and I could click it to uninstall it.

Which version failed, the one in the front page or the Sarge version? If it is the Sarge version, then just use the one from the front page. It should rewrite everything.[/QUOTE]
 what? where?

---

### Post by ixus_123 on 2005-03-01
worked great for me, thanks.  Only grip is I now have to install Mplayer-mozilla plug in by hand also

---

### Post by wallijonn on 2005-03-01
[QUOTE=RastaMahata]what? where?[/QUOTE]

On the left side of the SPM window change it to status view. You should find a local installed subheading.

---

### Post by self0 on 2006-02-14
i follow this but I cannot install it =/


Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.8-0.0) ...

mplayer.sh: line 58: gmplayer: command not found

---

### Post by wallijonn on 2006-02-20
What does line 58 of the shell script say?

---

### Post by envis on 2011-03-28
> **wallijonn said:**
> Ackbar,

In your case you may wish to download & install the "all" codecs package instead of the "essential" codecs package. It have what you are looking for.

**apoc**,
You'd probably have to do it the hard way and copy the skin to the default folder. I've not had that problem with my skin. Is there a "set to default" button? (I'm on W2KP right now so I can't fire up Ubuntu).

Hey im having that problem too!!

mencoder says > Audio format 0x4134504d is incompatible with '-oac copy', please try '-oac pcm' instead or use '-fafmttag' to override it. when trying to make a chunk of a certain very Hi-Fi video.. im not too sure what thats about...

Yet ive succesfully followed the [Install FFmpeg and x264 on Ubuntu Hardy Heron 8.04 LTS]("http://ubuntuforums.org/showpost.php?p=6963607&postcount=360") guide (note im on feisty ubuntu 7 64bits but it worked)

i just reinstalled ffmpeg 3 different ways actually, times 1 and 3 like mentionned above, time 2 using option "C" from the [Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283") guide (note: found in [Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413624") how to enable Medibuntu on Feisty)

anyways after each install everything appeared to work but always that problem with "Audio format 0x4134504d"

How can i make my ffmpeg recognize that codec?

-----------------------
ive found a workaround for that problem, making the chunk of the video using ffmpeg with this syntax worked:
```
ffmpeg -i input.mpg -ss 00:00:10 -t 00:00:30 out1.mpg
```

---

