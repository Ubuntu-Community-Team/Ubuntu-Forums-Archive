---
title: "Ubuntu 5.04 i386 addon zip"
date: 2005-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by mrbass on 2005-04-27
This uses dpkg -i to install apps locally so if your without an internet connection.
It installs the following apps:

java, flash-player + firefox plugin, adobe reader + firefox plugin, gFTP, multimedia codecs, mplayer, dvdplayback, xine, realplayer 10, thunderbird, gnomebaker, firestarter, nvidia 3D driver, samba server, ssh server, Japanese input.

Each one you can decide to install it or not.  Download from [http://mrbass.org/linux/ubuntu](http://mrbass.org/linux/ubuntu) it's about 85MB.

a few notes:
for Japanese input use CTRL-space to start.  Also in SCIM setup go to IM Engines and uncheck all languages except those you plan on inputting in.  Then in Japanese uncheck all but UIM-Anthy.

For [http://www.apple.com/trailers](http://www.apple.com/trailers) to watch quicktime movies I've had to **killall -9 esd** otherwise mplayer would just hang.

---

### Post by mrbass on 2005-04-28
Changelog 
1.3 Apr 28th 112MB removed fireflysung, added fix sound in GNOME now apple.com/trailers works without freezing mplayer in firefox and added xfce4 install, added turn on DMA mode for CD-ROM and DVD-ROM
1.1 Apr 28th 119MB added XFCE4 4.2.1 Desktop Environment, Azureus (automatically adds menu item), menueditor, fireflysung chinese font, Chinese Input, msttcorefonts, fixed a few minor things
1.0 Apr 27th 85MB first version
Plan to add xfce4 next version
I really could use someones help as I feel I'm violating the msttcorefonts license by just zipping up all the fonts.  Could someone tell me how to get the script for the deb for instance or just email me the script so I could modify it so it'll extract the .exe archives of the fonts.

XFCE4...wow never did so much copying and pasting...phew

edit: 1.3 is now up

---

### Post by thedman on 2005-04-29
Love the addon zip, saves me a bunch of time and headaches.  Thank you.  Just have one problem yet.  Should the RealPlayer install be placed in the default locatons (home...) ?  I thought I read somewhere here on the forums that it should go in /opt/RealPlayer.    I took the defaults and it doesn't seem to work in firefox.  I'm testing on foxnews.com video for realplayer.   It just seems to lock up.  Also I cannot even start it from the applications menu.  Any help would be greatly appreciated.

---

### Post by mrbass on 2005-04-29
When you rip through that script go a tad slower..hehe.
```
echo "RealPlayer 10 installation path type /opt/RealPlayer"
echo "For everything else just press ENTER"
read -p "Install Real Player 10? [Y/n/q]"
if [ "--$REPLY" == "--q" -o "--$REPLY" == "--Q" ]; then exit 0; fi
if [ "--$REPLY" == "--y" -o "--$REPLY" == "--Y" -o "--$REPLY" == "--" ]; then
sudo chmod +x realplay-10.0.4.750-linux-2.2-libc6-gcc32-i586.bin
sudo ./realplay-10.0.4.750-linux-2.2-libc6-gcc32-i586.bin
else
echo "Skipped"
fi

```
So it shows the first three lines in quotes.  Now as soon as you hit enter the screen clears to the top so you have to remember /opt/RealPlayer.  But it is there.  Just nuke your directory you installed it to in your home directory and reinstall it.

---

### Post by thedman on 2005-04-29
Thanks, for the quick reply.  I really must have flew threw that script.  I never noticed that.  I followed your suggestions, but I still seem to have the same problem.

Firefox just sort of hangs without any errors, or suggestions for plugins, and simply clicking on RealPlayer 10 in the applications menu doesn't seem to do anything but use a little cpu time, but nothing ever opens.  

I applied your sound fix as well.  I'm sure I'm missing something obvious.

Thanks again for your help.

---

### Post by thedman on 2005-04-29
Okay, I made some progress.  I did apply the sound fix in the script, but apparently that must not affect RealPlayer.  As soon as I did "killall -9 esd", about 10 RealPlayer setup windows opened.  (I guess I tried starting it a few times :))  Anyway after going through the setup it all works fine now.  One question though will I need to run that kill esd every time?

Maybe the only fix is to wait until ubuntu goes completely alsa.

Thanks

---

### Post by mrbass on 2005-04-29
ok well the sound fix (look at the code in the script).  I did apt-get install from the net I think it's libesd-alsa0 or something like that and it worked.  However, when I tried it locally via dkpg it wouldn't install since libesd couldn't be removed and had tons of dependecies (sp?).  So I was just testing mplayer and after doing the esd.conf modification the mplayer would play the quicktime movies at apple.com/trailers so I thought it was fixed....hmmm I'll have to do more testing on this sound issue.  Thanks so much for the feedback.  I think your the only user who's actually used the ubuntu addon zip...hehe.

ok if you opened up realplayer or mplayer and then went back to apply the sound fix (after the fact)...hmm I can't remember if I have killall esd or killall -9 esd.  But the fix won't be applied unless that esd sound daemon is killed.  In enemy territory I always had to do killall -9 esd for it to start.  Yeah ubuntu sound isn't anything to rave about at the moment.

---

### Post by thedman on 2005-04-29
Once again thank you for all your help.  I love your ubuntuaddon.zip and all the guides, I think because of these I just may make Ubuntu my distro of choice.  It makes everything else in Ubuntu (the non-free stuff) "just work!".  I am very thankful of people like you that are so willing to contribute to the community.

I am also a big fan of your website, and check it daily.  To be honest it is one of the few sites that I can get the files I need and actually utilize all of my 3Mbs cable connection.  Who do you use for hosting by the way?  

I work for an IS department at a hospital in Nebraska, and I also point all my coworkers to your site for the goods.  Keep up the good work and thanks again.

 O:)

---

### Post by mrbass on 2005-04-30
thanks...I use theplanet and servermatrix.  I'll try to get to the sound issue on Monday and add a few more packages most likely.

---

### Post by ykpaiha on 2005-04-30
I really enjoy to see you here Mrbass.
You most probably better than I with Linux boxes (mepis) and therefore you will find the way...
I had no movie at all and sound issues in firefox but working well on konqueror until I install Mozilla 1.7 and then it worked fine??
A bit strange is n't it ? :roll:

---

### Post by jtsai256 on 2005-04-30
This is really great! Thanks!

I have a question about mplayer and xine though...

Whenever I select a video to be fullscreen, the video doesn't stretch to fill the rest of the screen... it stays in its original smaller resolution. Is there a way around this?

Also is there a way I can make videos open in the same mplayer or xine window? Right now when I have Xine open and I click on a video, it opens a new Xine instead of playing in the original window. 

Thanks for your help!

---

### Post by inlivingcolour on 2005-05-01
Hey
Since Im new to linux, I dled the addon to my desktop.  I was just wondering how to move the addon folder since its locked.

---

### Post by mrbass on 2005-05-01
Well the instructions say (assuming you downloaded it to your desktop)
cd Desktop/
unzip ubuntuaddon.zip
cd ubuntaddon/
sh ubuntuaddon.sh 

well if you wanted to move the folder
sudo mv /Desktop/ubuntuaddon/ someplace/somedir/

Not sure why you'd want to move it...once you install it just delete it..just hang on to the 114MB zip file for other installs perhaps.

---

### Post by inlivingcolour on 2005-05-01
I dont want to delete any installed software.  I just want to move the ubuntuaddon.zip folder off the desktop.  I wasnt sure how to since its a locked folder.

---

### Post by mrbass on 2005-05-02
forgive me as I could be totally misunderstanding you but won't you install the software through the script then just nuke the directory as it's installed.  The .debs are just installation files but once installed are no longer needed.

---

### Post by adrislayer on 2005-05-02
very very nice addon

I've seen it, I've downloaded it, installed it and it works so now, happy me :d:d:d:d

---

### Post by kickinmhl on 2005-05-04
STILL NO JAVA 
If you go to the [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) page, shouldn't I expect to see a window there?  I get puzzle pieces that prompt me to install the java runtime.

I have tried 4 times now to get this working, to no avail.  Unfortunately your installer didn't work either.  the /usr/java/jre1.5.0_02 folder already exists and the installer fails.

Any help would be GREATLY appreciated.

---

### Post by mrbass on 2005-05-04
yes you should see it with the little icon dancing.  I believe if you install it after you've intsalled it already it'll ask if you wish to overwrite...IIRC just press A to overwrite all.

Basically just press spacebar four times to read license agreement then type yes and it'll install.  I've tested it over 50 times at least.  Not sure what would be different.  Your running ubuntu i386 not ubuntu ppc or ubuntu amd64 correct?

---

### Post by kickinmhl on 2005-05-04
Yes, I am using the i386 version.

Ok I tried this on another install I have and it failed there too the difference here is that I get a red x in the corner instead of the puzzle thing.

After the JRE install is complete is shows this:
Done.
mkdir: cannot create directory `/usr/java': File exists
mv: cannot overwrite directory `/usr/java/jre1.5.0_02'
ln: `/usr/bin/java': File exists
ln: `/usr/bin/java_vm': File exists


BUT HERE IS ANOTHER ISSUE, that may be related.
The JRE install that I attempted before I found your addon install was jre1.5.0_03.
Should I try to remove that release and then rerun your addon install?

If so how do I remove it?  just delete the /usr/java/jre1.5.0_03 folder and the associated links?

BY THE WAY.... I am new to linux (again, trying to make it stick this time), and I really appreciate your help!!

---

### Post by mrbass on 2005-05-05
> The JRE install that I attempted before I found your addon install was jre1.5.0_03.

That would have been nice to have known...hehe
yes nuke 'em then try again
sudo rm -rf /usr/java
sudo rm -f /usr/bin/java
sudo rm -f /usr/bin/java_vm

---

### Post by Rodrigo on 2005-05-05
Thanks mrbass for the EXELENT work, many many thanks :D

---

### Post by kickinmhl on 2005-05-05
Well I tried this again after doing this:

sudo rm -rf /usr/java
sudo rm -f /usr/bin/java
sudo rm -f /usr/bin/java_vm

Then I ran the ubuntoaddon install again...

Still it doesn't work .
I checked my firefox settings which have java and javascript enabled

WHAT AM I DOING WRONG.  this is KILLING ME! 

Any other ideas?  Is there some info that I can post that would help.

Thanks again for any help you can provide. ](*,)

---

### Post by Overdrive_5000 on 2005-05-07
Does this version contain the msttcorefonts ?

---

### Post by mrbass on 2005-05-07
yes it does

---

### Post by sb73542 on 2005-05-15
Mrbass, THANK YOU very much for putting this together!!!  And for your bandwidth!  

This is an absolutely essential tool for Ubuntu, in my opinion.   O:)

---

### Post by mrbass on 2005-05-16
I'm gonna totally redo this since now the Unofficial Ubuntu add-on cd is out that allows pressing enter.  Sweet.   I will add Chinese, Japanese and Korean input and just a few basic ones java, flash, etc.  Try to get to it tomorrow (Monday).

---

### Post by Heliode on 2005-05-16
May I suggest you add the backport versions of Firefox (1.0.4) and Thunderbird (1.0.2)? I'm using them all the time and they seem very stable. The server where they have to come from is mostly heavily overloaded though so including them in your addon file might be very useful. 

Just my 2c ;)

---

### Post by rromie on 2005-05-30
Hi, nice addon zip! Due to the excitement, for managing to download it, (it took me many attempts to download it, since it stops many time, must be my problems here) I've tried and install many programs at one go, but not my totem can't display my avi files. Previously, it can display pictures but not sound, so I was hoping that by adding wincodecs will make it works.

Now, my question is how do I uninstall the program I install using the addon zip. I hope my totem will turn back on, and I plan to try to install one program at a time to isolate the cause. 

Thanks.

---

### Post by mrbass on 2005-05-31
just look at the script with gedit or vi and see which packages are there....try to remember which ones you installed then 
sudo apt-get remove somepackage1.deb somepackage2.deb

---

### Post by jobezone on 2005-05-31
[QUOTE=mrbass]just look at the script with gedit or vi and see which packages are there....try to remember which ones you installed then 
sudo apt-get remove somepackage1.deb somepackage2.deb[/QUOTE]
 that would be

sudo apt-get remove package-name other-package

---

### Post by Poldi on 2005-06-22
I cannot get throgh my companies firewall [referrer information gets lost). does anybody else host this file?

how can I get this?

thanks and regards,
Carsten

---

### Post by themoddingden on 2005-06-22
Hi;
I found this somewhere and it's 127 meg  also mplayer in it crashes along with firefox not knowing that javas installed.
How Do I fix this I'm useing Kubuntu 5.04
besides this all is well.

---

### Post by action09 on 2005-06-28
Thanks a lot MrBass for your great job and ideas on DVDShrink & DVDDecrypter Guides !
And for addon !  great idea !
IS there a way to include this in a Ubuntu CD ? is it polotically correct ? legal ? possible?

Thanks anyway

---

### Post by alvinpd on 2005-07-18
nice job...thnx...

---

### Post by yorick on 2005-09-05
First of all, thanks for your zip addon, Mr Bass. I downloaded your zip file because is much smaller than the addon cd (planning on downloading it also later, tho) and it contains most of the packages I need.

I installed Ubuntu yesterday than played a little with it before installing your addon. When I launched it I had two terminals open, one in root mode and one in user mode. I'm not sure from which terminal I ran your script. 

In that session everything worked ok. I listened a little to music, a started a movie, they played ok.

The problem is this: after restarting the computer, Xmms and MPlayer do not work anymore. Every time I press the play button they freeze. Could the problem be because maybe I ran the script from the root console, and I after the restart I entered from the user account? How can it be solved?

Thanks.

---

### Post by mrbass on 2005-09-05
hmmmm well ..hmmm well...not sure.  I guess it could be you ran it from root console.  Just try it again reinstalling it like it says in the instructions.

---

### Post by mwdowns on 2005-09-10
I love this add-on zip.  It's definitely one of the things that makes Ubuntu the best of the Gnome/Debian-oriented distros.

One question:  I am downloading the Breezy Badger release client now, so will the addon work with that version of Ubuntu?

---

### Post by ichnation on 2005-09-22
Just because the MrBass download is quite full, I set up a copy. Maybe someone will try to download from here?
[ftp://reiger.intern.voeten.com/pub/ubuntu/ubuntuaddon.zip](ftp://reiger.intern.voeten.com/pub/ubuntu/ubuntuaddon.zip)

Oh by the way, when will ubuntu officially start an "addon" mirror facility?

---

### Post by unknowndev on 2005-09-23
please anyone provide us an working link for the ubuntuaddon.zip we cannot able to download the file...tnx in advance!

---

### Post by dr.drake on 2005-10-02
hello mrbass.

first of all: **thanks a lot for the addons.zip !!!!!!!!!!!**
as a newb to linux I have troubles installing stuff outside synaptic, but this zip did just most of it all in one go!!!!!! all, I say? well, not all...

**Java**
like the user *kickinmhl* before in this thread, I cannot get Java working...
I had previously tried to install Java jre1.5.0_04 and I can see it sitting in the folder */home/eric/* but it doesn't work, and I'm really stuck here. no dancing icon at: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) is there anyway how you can help me with this?

**Nvidia**
the package couldn't install the nVidia drivers:

Install Graphics Driver (NVIDIA)? [Y/n/q]y
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.7174-0ubuntu1_i386.deb (--install):
cannot access archive: No such file or directory
Selecting previously deselected package nvidia-settings.
(Reading database ... 78249 files and directories currently installed.)
Unpacking nvidia-settings (from nvidia-settings_1.0-3ubuntu2_i386.deb) ...
Setting up nvidia-settings (1.0-3ubuntu2) ...

Errors were encountered while processing:
/var/cache/apt/archives/nvidia-glx_1.0.7174-0ubuntu1_i386.deb
fbe9fd8c1eb099ec02735eac00304ed1  /etc/X11/xorg.conf
sudo: nvidia-glx-config: command not found

**Samba**
the same with samba:

Install Samba Server for file sharing service? [Y/n/q]y
dpkg: error processing /var/cache/apt/archives/samba_3.0.10-1ubuntu3_i386.deb (--install):
cannot access archive: No such file or directory
Selecting previously deselected package smbfs.
(Reading database ... 78263 files and directories currently installed.)
Unpacking smbfs (from smbfs_3.0.10-1ubuntu3_i386.deb) ...
Setting up smbfs (3.0.10-1ubuntu3) ...

Errors were encountered while processing:
/var/cache/apt/archives/samba_3.0.10-1ubuntu3_i386.deb

and a **not so serious note**:
on your page [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/) in the install guide for the zip this command is missing a "u": *cd ubuntaddon/*
not serious, but a lot of people copy/paste most commands.

thanks, eric.

PS: I still have no clue where to download the install files to, and how to activate them (like the 'SafePeer' plugin for Azureus)...

---

### Post by mrbass on 2005-10-04
this addon zip is for hoary 5.04 not Breezy.  hoary has samba and nvidia in the cache look at the script.  I'm guessing your trying to install this on breezy is my best guess.

thanks for correcting my typo...fixed it.

---

### Post by dr.drake on 2005-10-06
nope,

I am running hoary...

I'll wait for the official release of breezy (the 13th ???) until then I'll keep trying to tweak hoary.
I reckon your reply means that most addons will work there too?

thanks, eric.

---

### Post by grimmson on 2005-10-06
Your a good man Mr. Bass. A million thanks. Im a noob and was having a tough time. =D&gt;

---

### Post by LXer on 2005-10-13
[QUOTE=mrbass]this addon zip is for hoary 5.04 not Breezy.[/QUOTE]

Are you trying to migrate this to breezy?

bye
LXer

---

### Post by rado_london on 2005-10-13
I just donwloaded breezy. im still suprized that there is no XMMS and mplayer in it. Howevere i tried to install ubuntuaddon.zip.It installed everything but most of the packages are brocken(including mplayer). The only good working one is XMMS. Can someone tell me is it fgoing to be ubuntuaddon.zip for Breezy.
Cheers in advance

---

### Post by dr.drake on 2005-10-14
[QUOTE=rado_london]I just donwloaded breezy. im still suprized that there is no XMMS and mplayer in it. Howevere i tried to install ubuntuaddon.zip.It installed everything but most of the packages are brocken(including mplayer). The only good working one is XMMS. Can someone tell me is it fgoing to be ubuntuaddon.zip for Breezy.
Cheers in advance[/QUOTE]

I am guessing mrbass will do so soon...

maybe could give a list of the apps that we *can* use in breezy for the time being??? (from this hoary cd/zip)

I'm only asking this because I just had a long upgrade to breezy.
did an update (also very long), rebooted, and lost my way into my desktop. just got the black screen saying: login - eric@computer: $ , not reacting to startx or anything...
so I decided to do a clean install and am once again stuck without realplayer, mplayer, flashplayer and all the other goodies that came with the disc.

ehrm.... HELP! :)

---

### Post by mrbass on 2005-10-14
I'll try to do it within a week or two weeks (migrate it to breezy 5.10).  I just got the .iso today downloaded but haven't even got around to burning it yet.

---

### Post by webbie180 on 2005-10-16
Download ubuntuaddon.zip version 1.3 112MB released Apr 28, 2005 

Is the link dead for the zip?  Cant download.

---

### Post by poptones on 2005-10-16
FWIW, I have found the deb package of mplayer broken for some time. First it was packaged without half the fucntionality (the mencoder functions were all completely missing) and lately it seems every time I have tried the one in synaptic it has had broken sound and crashes when trying to play a video with sound. 

I made an installation script some time ago and it has worked perfectly every time I have used it. In fact, I keep it and the tars it grabs in a folder and use it every time I rebuild the system. It installs a complete build system, headers and an updated x system and then builds an mplayer optimized to the machine its on. 

Just make a folder, put this script in it, and enter the folder and type "sudo su" and then run the script.

```

wget -c http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre7.tar.bz2
wget -c http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2
wget -c http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-7.tar.bz2
wget -c http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2
apt-get install -y autoconf
apt-get install -y automake
apt-get install -y libtool
apt-get install -y flex
apt-get install -y bison
apt-get install -y gcc-doc
apt-get install -y g++
apt-get install -y x-window-system-dev
apt-get install -y libgtk1.2-dev
apt-get install -y libpng12-dev
apt-get install -y libxxf86vm-dev
tar -xjf essential-20050412.tar.bz2
mkdir -p /usr/lib/win32
cp essential-20050412/* /usr/lib/win32/
rm -rf essential-20050412
tar -xjf MPlayer-1.0pre7.tar.bz2
cd MPlayer-1.0pre7
./configure --enable-gui
make
make install
cd ..
tar -xjf font-arial-iso-8859-7.tar.bz2
cp font-arial-iso-8859-7/font-arial-14-iso-8859-7/* /usr/local/share/mplayer/font/
tar -xjf Blue-1.4.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
cp -r Blue/* /usr/local/share/mplayer/Skin/default/
cp MPlayer-1.0pre7/etc/* /usr/local/etc/mplayer/
/usr/share/doc/libdvdread3/examples/install-css.sh
rm -rf MPlayer-1.0pre7
rm -rf Blue
rm -rf font-arial-iso-8859-7

```

---

### Post by onfyreforjesus on 2005-11-06
Yeah the download link is dead. pls mrbass pls update. and get it functional.

---

### Post by tOpEzz on 2005-11-22
[QUOTE=webbie180]Download ubuntuaddon.zip version 1.3 112MB released Apr 28, 2005 

Is the link dead for the zip?  Cant download.[/QUOTE]
yeahh agree with u br0... i really need it, mrbass pls fix it for us... kekekeke.. since my home no internet connection, i have to use my office line to download all the addon and look for some ubuntu guide... :)

---

### Post by mrbass on 2005-11-24
Time isn't an issue...more of a lack of motivation is.  I guess I just got burnt out on linux..computers in general.  Anyway my offer is still valid as I posted in this thread (see last post).
[http://www.ubuntuforums.org/showthread.php?t=68956&page=2](http://www.ubuntuforums.org/showthread.php?t=68956&page=2)

Basically if "Easy Ubuntu" makes a version for download I'll be glad to host it.  I never got a response so I guess it's up to someone else to modify and test.  I remember when I did the first ubuntuaddon I spent about 10 or more hours testing it with vmware till I got it right.

---

