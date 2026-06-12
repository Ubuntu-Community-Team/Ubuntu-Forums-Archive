---
title: "Unable to play wmv files in Ubuntu 8.04. Pls help."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by hack12 on 2008-05-20
Hi, I am an absolute beginner in Linux. I have successfully managed to install ubuntu 8.04 64-bit and its working like a charm. I am trying to play some wmv files and I am seeing the video however no audio. These files are not encrypted I am certain of that. I have gone through quite a few sites that show how to add something called a repository and than installing w32codec, w64codec and libvdcss. I have quite a few media applications installed like mplayer, vlc, totem movie player (default) however none of them play the audio. I can see the video no problem. I can play avi files without any issues. Can someone please help by providing step by step instructions. I have been following stuff blindly by just copying and pasting and now am not sure if I have messed anything else up. 

Also can someone please help with some basic stuff like 

What is a repository?
How to install packages?
Why can't I go through add/remove to install some apps or the synaptics package manager?


Thanks for your help.

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> What is a repository?
How to install packages?
Why can't I go through add/remove to install some apps or the synaptics package manager?I think this page will help you with these questions: [https://help.ubuntu.com](https://help.ubuntu.com)

Install ubuntu-restricted-extras -- that should get wmv files going for you.

---

### Post by Maestro23 on 2008-05-20
Synaptic: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by jtibau on 2008-05-20
> **HotShotDJ said:**
> I think this page will help you with these questions: [https://help.ubuntu.com](https://help.ubuntu.com)

Install ubuntu-restricted-extras -- that should get wmv files going for you.

I don't think ubuntu-restricted-extras includes support for wmv (might be wrong). What I am sure of, is that you can easily install w32codecs using these lines:

```

wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb;
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb

```

I'm pretty sure that will allow you to watch wmv files...

As for encrypted dvds, the following should do the trick:

```

wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb;
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

```

Well actually I should say both of those are for the 32bit architecture (which is most likely what you have installed)...

those lines are from Medibuntu, which is a third party repository that distribute multimedia packages that can't be hosted at ubuntu's official repos... Link here; [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by HotShotDJ on 2008-05-20
> **jtibau said:**
> I don't think ubuntu-restricted-extras includes support for wmv (might be wrong). What I am sure of, is that you can easily install w32codecsw32codecs are not necessary... and are inappropriate for the OP's system which is 64 bit.  Full support for wmv is included in ubuntu-restricted-extras. I do, however, agree with using Medibuntu for other reasons, but lets not overwhelm our new user with that just yet. :)

---

### Post by hack12 on 2008-05-20
Thank you all for your help. I had followed a youtube video when installing my O/S and at the end it showed me how to install the restricted extras package. I am pretty sure I have it installed as while researching this issue on the web I came across that suggestion as well. Is there any way for me to confirm if I have it installed? Also tried the other suggestions of installing w32 codec's even though I have a 64-bit version installed but still no go. I can watch and listen to avi files no problem. Its only the wmv files that I am having issues with and that also the video is showing up fine but I just can't hear the audio. Thanks for your help.

---

### Post by avtolle on 2008-05-20
To confirm if the ubuntu restricted extras package is installed, go to Synaptic (System-->Administration-->Synaptic Package Manager), search for ubuntu-restricted-extras (I think that's what it's named), and when the search is over, if the box before the name is a solid color, it is installed; if it is "empty" (box is white), check it for installation, hit apply, and it will be installed.

---

### Post by hack12 on 2008-05-20
Hi, thx for your reply. I have confirmed that I have version 15 of the Ubuntu restricted extras package installed. The color in the box is green. Could you please suggest any other fixes for this issue. Thx

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> Hi, thx for your reply. I have confirmed that I have version 15 of the Ubuntu restricted extras package installed. The color in the box is green. Could you please suggest any other fixes for this issue. ThxHack12:  If you've been following random advice from YouTube and/or elsewhere, you have probably applied "fixes" that don't apply to your system, such as installing win32codecs on a 64 bit system.  So, what we need to do is work backwards.  I need you to go into Synaptic Package Manager and REMOVE some of these packages... especially win32codecs AND win64codecs.  We can always put something back later if necessary.

---

### Post by hack12 on 2008-05-20
Hi HotShotDJ,

I removed the w64 codec. I did not have the w32 codec installed. When I do a search for w32 in synaptics it came back with non-free codec and it was not installed so I am assuming that I had not installed it. I did have the w64 codec which I removed per your post but I still cannot hear audio for wmv files. Do I need to install any other codec's? Thx for your help.

---

### Post by phoenix_abhi on 2008-05-20
If u installed all necessary codecs and still audio is down, check the alsamixer 

type alsamixer in terminal and increase the level of all required field using arrows and select the channel to 8

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> I did have the w64 codec which I removed per your post but I still cannot hear audio for wmv files. Do I need to install any other codec's? Thx for your help.Ok.  Thats good.  I didn't expect the removal of this stuff the actually fix the problem (although one can hope!).  I just wanted to get us back to baseline.  Now, I'd like you to open your volume control.  If you do not have a volume control on your panel, please add it by right-clicking on an empty part of either your top or bottom panel, clicking on Add to Panel, and selecting "Volume Control"

Once you have this on your panel, Right click on the volume control and select "Open Volume Control."  What tabs and sliders do you see?  Are any muted (red x at the bottom)?  What are the volume levels?

Remember, right now, we are just diagnosing.  :)

---

### Post by hack12 on 2008-05-20
Hi Phoenix_abhi,

I went into alsamixer. The master slider is set to 100 and so is the pcm slider. the headphone slider I cannot move. All the other sliders are 0. How do i check the channel? I can't see anything for channel.

Hi HotShotDJ,

The volume control icon is next to the battery, clock and network icon. On opening it up I see 2 tabs. Playback and Switches. In the playback tab master and pcm are set to full and the microphone is disabled (has a cross). In the switches tab I have headphone and speaker and both are checked. 

Just to reconfirm I can hear avi and other format's fine. The only format I am having trouble with is .wmv. 

Thanks for all your help.

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> The volume control icon is next to the battery, clock and network icon. On opening it up I see 2 tabs. Playback and Switches. In the playback tab master and pcm are set to full and the microphone is disabled (has a cross). In the switches tab I have headphone and speaker and both are checked. 

Just to reconfirm I can hear avi and other format's fine. The only format I am having trouble with is .wmv. Yes. I understand the symptoms. :)  Please, lets stick to ONE line of diagnostics.  I realize that there are others who might have valuable information and ideas to add, but if you keep going back and forth, and applying random fixes suggested by several people all at once, we'll never get to the bottom of this.

I'd now like you to again, open your Volume Control.  This time, click on File and select "Change Device."  Please tell me what you see in the pop-up menu and, if there are several options, which one is selected.

---

### Post by phoenix_abhi on 2008-05-20
U just follow hotshotdj. he is correct, donot get mixup, follow him in the line and he may reveal how to change the chanel also

---

### Post by hack12 on 2008-05-20
Sorry about that. Will respond to every post separately but will only try 1 fix at a time. 

I opened up Volume control and I have 5 options numbered 0 to 4. The one selected is the first option #0 which is HDA intel (Alsa Mixer).

The other options are:

1. analog devices ad1984 (oss mixer)
2. playback: alsa pcm on front:0 (AD198x Analog) via DMA (Pulse audio mixer)
3. Capture
4. Capture

Thx for your help.

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> I opened up Volume control and I have 5 options numbered 0 to 4. The one selected is the first option #0 which is HDA intel (Alsa Mixer)Ok.  That is set correctly.  We've made progress by ruling out problems with the sound system settings. :)

Now, I'd like you to open one of the offending files.  You said that you have VLC installed, so lets use that.  As the file is playing, I'd like you to go to the VLC media player's Settings --> Preferences and highlight Audio all the way at the top of the left pane.  Make sure the setting there are sane.

Also, if you could... would you either post a link to a file that you are having trouble with or actually attach one to your next post?

---

### Post by HotShotDJ on 2008-05-20
OK!!  Before we proceed any further, please stand by.  I think I may be on to something, but I need to test before posting about it.

---

### Post by HotShotDJ on 2008-05-20
GOT IT!  Newer wmv formats do NOT play properly (no sound, but I have picture, just like you!)

HOWEVER, this is fixable... I know this, because I just fixed it on my system. LOL. (Others, earlier in the thread seemed to be onto the proper solution, but it got lost in the noise -- including my noise ... but credit where credit is due!)

[LIST=1]
[*]Follow CAREFULLY the steps for Medibuntu repositories at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[*]BE SURE to use the instructions for HARDY (8.10)
[*]Once completed, and you've updated your system, install win64codecs (for others, who may be running 32 bit version of Ubuntu, use win32codecs)
[*]Now, install mplayer
[*]Try playing the file using mplayer.  The others won't work (well, they didn't work for me)
[/LIST]

---

### Post by avtolle on 2008-05-20
+1 on that; same "cure" here as well.

---

### Post by hack12 on 2008-05-20
Hi,

I uninstalled mplayer than I followed the instructions on the site to install the repository. After that I installed the codec using the command line specified on the site. Than I reinstalled mplayer but still no go. I cannot play the file. The file I am trying to play is too big to post over here. It works fine in windows (I don't know if that helps). I have a dual boot laptop. Also I tried playing a couple of wmv files that are on the web and I was able to play them without any issues. They may be of the old format. This wmv file that I have on my hard disk locally was made probably using camtasia or some other software.

---

### Post by HotShotDJ on 2008-05-20
Just to be sure... please verify using Synaptic Package Manager that you have both the win64codecs and mplayer installed from the Medibuntu repositories (based on what you wrote, I'm sure you do, but I always like to double check).  Also, are there any updates that you haven't applied yet.  If so, please apply them (an icon in your notification area on the panel should tell you if you have updates).

Finally, try playing the sample wmv file on this page: [http://support.microsoft.com/kb/316992](http://support.microsoft.com/kb/316992)
Download it to your desktop and then play it in mplayer.  Let me know what happens.

---

### Post by Exsecrabilus on 2008-05-20
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) says:

> NOTE 2: the w64codecs is only made for feisty and gutsy, so not for dapper or edgy

It doesn't mention Hardy, so I'm assuming it's not fully compatible yet.

---

### Post by hack12 on 2008-05-20
I reconfirmed via synaptics that I have the w64codecs package installed. The version is 20071007-0medibuntu1 and it says that is the latest version. Also confirmed that mplayer is installed and the version is 2:1.0~rc2-0ubuntu13+medibuntu1 and it says that's the latest version. I remember doing updates yesterday and I can't see anything next to the battery icon for updates hence guessing that there are no updates needed.

Tried playing the file on the microsoft site and I can see the video but no audio. I played the file in windows and I can hear it say "support.microsoft.com". Thx

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> Tried playing the file on the microsoft site and I can see the video but no audio. I played the file in windows and I can hear it say "support.microsoft.com". ThxThere may be issues with w64codec..  I know that by installing w32codec on a 32 bit system solves the problem.  Just to be sure, when you say that you are playing the file, are you playing it using mplayer or are you using one of the other players?

---

### Post by Skeet on 2008-05-20
I'm fairly sure VLC runs without codec packs. It plays pretty much anything you throw at it.

```
sudo apt-get install vlc
```

I know that during the Windows installation it gives you the option of installing the Mozilla plugin, to make vlc handle web movies. Not sure if its the same with the Linux version.

Edit:
Checked the vlc site, it does support the mozilla plugin

```

% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```

*Note: You need to check that a "universe" mirror is listed in your /etc/apt/sources.list.*

---

### Post by HotShotDJ on 2008-05-20
> **Skeet said:**
> I'm fairly sure VLC runs without codec packs.Unfortunately, vlc will not play the files in question correctly.  However, it handles older wmv formats brilliantly.

---

### Post by hack12 on 2008-05-20
I have a few applications installed under Applications - Sound & video.

1. Totem Movie Player
2. MPlayer Movie Player

I was using Totem Movie Player as that was the default application. Now I tried using MPlayer and it gave me the error "Cannot find codec for audio format 0xA". I click on OK and I can see the video however no audio.

Sorry about that goofup I for some reason assumed that Totem was the player you were referring to when you said MPlayer. I had a brainfreeze. However either ways it doesn't work so atleast that part is right :-)

Any other suggestions. thx for your help.

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> I was using Totem Movie Player as that was the default application. Now I tried using MPlayer and it gave me the error "Cannot find codec for audio format 0xA". I click on OK and I can see the video however no audio.That error suggests that the issue is in w64codec.  I'm afraid you may have to wait until Medibuntu updates it.  I'm sorry I couldn't give you a better outlook.

EDIT:  UNLESS....   Stand by again... LOL.  Sorry, I want to check something before I quit on this problem...

EDIT #2:  I'd like you to check something.  Go to Places --> Computer and click on Filesystem.  Open the "usr" folder.  Then open the "lib" folder (wait for a little bit while it loads.. it could take a few moments).  Is there a folder called "codecs" in there?  If so, open it and tell me what you see.  Can you find files that begin with wmv and end in .dll?

---

### Post by hack12 on 2008-05-20
Hi HotShotDJ,

This was funny. I am actuall reading the post on this url and was trying to follow it.

[http://lj4newbies.blogspot.com/2007/11/install-win32-codecs-for-mplayer-in.html](http://lj4newbies.blogspot.com/2007/11/install-win32-codecs-for-mplayer-in.html)


Per that post it says something similar to what you were saying except it says to copy the files to /usr/lib/win32. I did that and it didn't work however there is a corresponding README file that came with the package I downloaded and I read that and it said that put the files in the /usr/local/lib/codecs folder. there was no codecs folder under /usr/local/lib hence I created it and copied the files over there however the readme file is saying something like "The default directory is /usr/local/lib/codecs/ ($prefix/lib/codecs/) if you are compiling from source". I am not quite sure what they mean when they say $prefix. Can you help.

Also I checked and there are no files under the location you specified which was /usr/lib/codecs. the folder is there. 

Closely reading the readme file I think it says that if you are using a built in version than copy it to that location you specified. I am going to try and copy the files to that location. Please let me know if you think its incorrect and I can always delete them. thx

---

### Post by hack12 on 2008-05-20
Nope that didn't help either. just to confirm I have approx 4 files when I extract the tar.bz2 file. I extracted the files and than moved them over to that folder. Is that it means when it says to "unpack the file". The 4 files I have are

cook.so
drvc.so
README
sipr.so

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> Closely reading the readme file I think it says that if you are using a built in version than copy it to that location you specified. I am going to try and copy the files to that location. Please let me know if you think its incorrect and I can always delete them. thxACK!  Remember what I told you about following random advise from all over the place!?!?!?!?  Although you ARE on the right track, the implementation is rather haphazard.  We need to do this STEP by STEP or you could end up with a pooched system.   So whatever it is you are doing (we MIGHT end up doing it anyway, but lets not risk it) please stop and wait for my next post, which I'll start typing the instant I post this.

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> Nope that didn't help either. just to confirm I have approx 4 files when I extract the tar.bz2 file. I extracted the files and than moved them over to that folder. Is that it means when it says to "unpack the file". The 4 files I have are

cook.so
drvc.so
README
sipr.so
I think I'm going to cry.:(  Please undo what you did.

---

### Post by hack12 on 2008-05-20
Sorry I got a bit excited when I saw your post about the location. I have reverted everything back to as it was about 25 minutes ago.

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> Sorry I got a bit excited when I saw your post about the location. I have reverted everything back to as it was about 25 minutes ago.Phew.  You scared me there for a moment. <HotShotDJ takes a deep breath and pulls himself together>  :)

Now... the next step... I'd like you to go back to Places --> Computer and open Filesystem.  This time, please open user, and then local, and then lib.  If there is a folder called codecs there, please open it and see if those files I asked about are there.  DON'T do anything with them yet.  Just report back.

---

### Post by hack12 on 2008-05-20
:-). There is a folder however there are no files in it. I moved the files after you told me to undo what I had done. This folder was empty 25 minutes ago just to confirm and is empty now as well.

Edit: Reading your post previously "EDIT #2: I'd like you to check something. Go to Places --> Computer and click on Filesystem. Open the "usr" folder. Then open the "lib" folder (wait for a little bit while it loads.. it could take a few moments). Is there a folder called "codecs" in there? If so, open it and tell me what you see. Can you find files that begin with wmv and end in .dll?"

The folder u had asked me to check at that time was usr/lib/codecs however in ur last post u are asking me to check /usr/local/lib/codecs. Pls confirm

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> :-). There is a folder however there are no files in it. I moved the files after you told me to undo what I had done. This folder was empty 25 minutes ago just to confirm and is empty now as well.Just to be sure (you KNOW how I like to double check) you are looking at /usr/local/lib/codecs and NOT /usr/lib/codecs

---

### Post by hack12 on 2008-05-20
Its like u can read my mind. I edited my last post but you replied sooner. Yes I checked /usr/local/lib/codecs and there are no files however 25 minutes ago there was no codecs folder also in this location. Remember I said I created a codec's folder. It was in this location. If you confirm I can go ahead and delete it.

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> If you confirm I can go ahead and delete it.Yes, you can go ahead and delete it, since it is empty and you are the one that created it.  But now the mystery is... where did w64codecs put the damned codecs. :confused:   You told me which package is installed.  Let me look at it.  Don't do anything until I post again... or I'll cry! :)

---

### Post by hack12 on 2008-05-20
K i will go ahead and delete the folder and not touch anything else. But I have to run now. Will check back in a couple hours if you are available otherwise will try whatever suggestions you post and if they don't work than will pick it up tomorrow. Thx so much for all your help. TTYL

---

### Post by HotShotDJ on 2008-05-20
> **hack12 said:**
> Thx so much for all your help. TTYLWell... I've wracked my brain to no avail.  The w64codecs package makes no sense to me whatsoever.  I've searched the web for a solution and have found none.  So I'm back to my original comment... you'll need to wait until the w64codecs package is updated.  Medibuntu is pretty good about keep things as up to date as possible, so hopefully it won't be long.

However, lest we forget, we DID accomplish something:  We now know the problem is with the w64codecs and not anything you did or did not do. That is, at least, something. :)

---

### Post by hack12 on 2008-05-21
Thx for all your help. I will keep checking and hopefully the codec's will get updated soon. Thx

---

### Post by hack12 on 2008-05-21
Hi HotShotDJ,

I know you said not to follow random advice on webpages however I have been researching this issue and per a post on this forum 
[http://bbs.archlinux.org/viewtopic.php?pid=360641](http://bbs.archlinux.org/viewtopic.php?pid=360641)

it seems there is no support for wma/wmv3 64-bit. However they mention that there is something called 64bit fluendo that has the codec.

Can you please explain what is fluendo. A quick google search says fluendo is the name of some company and the application is gstreamer. It seems gstreamer is installed in the gnome desktop which is what I have. How can I launch gstreamer as I don't see it installed. Pls let me know if you think this might be a fix. thx for your help.

---

### Post by Maestro23 on 2008-05-21
Take a look at Restricted Formats.

[https://help.ubuntu.com/community/RestrictedFormats?highlight=(Restricted)|(Formats)#head-79bfba9a0e96d62a622a47430239a1d49454c953](https://help.ubuntu.com/community/RestrictedFormats?highlight=(Restricted)|(Formats)#head-79bfba9a0e96d62a622a47430239a1d49454c953)

---

### Post by hack12 on 2008-05-21
I have the restricted package installed already. It seems that I am missing the audio codec's required to play wmv9. I know that the codec is there in w32codec however I have a 64bit system and besides when I had installed w32codec before it didn't work. I am just wondering if I download w32 codec and extract the files where can i put them on my 64 bit system so mplayer can use it. I can't seem to figure out where mplayer looks to find the codec's on a 64-bit system. Currently there are no files in either /usr/local/lib/codec or usr/lib/codec. Can someone please confirm what directory are the codec's installed in on a 64 bit system. Thx

---

### Post by HotShotDJ on 2008-05-21
> **hack12 said:**
> it seems there is no support for wma/wmv3 64-bit. However they mention that there is something called 64bit fluendo that has the codec.

Can you please explain what is fluendo.In addition to their open-source gstreamer plugin, you are able to purchase proprietary plugins through fluendo.  The gstreamer plugin that is in the repositories is NOT what your looking for, it only handles MPEG -- but THAT is already being handled by other plugins, so it won't help you to install.

gstreamer is the multimedia framework that is used by other applications.  You don't start it.  It is a collection of libraries used by your other applications.

---

### Post by HotShotDJ on 2008-05-21
> **hack12 said:**
> Currently there are no files in either /usr/local/lib/codec or usr/lib/codec. Can someone please confirm what directory are the codec's installed in on a 64 bit system. ThxThe question is not where they are supposed to be... we already know that answer.  They are supposed to be in /usr/lib/codecs.  However, some versions of the w32codecs and w64codecs are known to put them in /usr/local/lib/codec.  MPlayer does not know to look there.

However, in the package you installed, that wasn't the problem.  The files (such as they were) went to the correct place.  Its just there were none of the typical files that I'm used to seeing.  As it stands right now, it appears that the w64codecs do not support some of the latest wmv formats.  It has been a long, slow road getting some of these proprietary formats supported in 64 bit Linux, but they are coming along.  I can only recommend patience.

---

### Post by mc4man on 2008-05-21
if your so inclined you can do this
[http://ubuntuforums.org/showthread.php?t=739011](http://ubuntuforums.org/showthread.php?t=739011)
or look and see if if someone has built a 32 bit mplayer for 64 bit ubuntu as here [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)  -1.3.9.1.1 (seems somewhat dated)

---

### Post by HotShotDJ on 2008-05-21
> **mc4man said:**
> if your so inclined you can do this
[http://ubuntuforums.org/showthread.php?t=739011](http://ubuntuforums.org/showthread.php?t=739011)
or look and see if if someone has built a 32 bit mplayer for 64 bit ubuntu as here [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)  -1.3.9.1.1 (seems somewhat dated)I just took a quick look.  Seems like a reasonable work-around for now.  I know similar strategies were used for other formats, such a flash, before the 64 bit plugins were released.

Hack12: just be careful.  There will be some very non-Newbie stuff that you will be doing if you follow those threads.  Document everything you do so that if something goes wrong, you can get things back to the way they were.  Best of luck!

---

### Post by phinn on 2008-06-22
The ubuntu-restricted-extras handled most of the stuff for me.

I added the repositories and got w32codecs and installed it and the other required packages and that messed up everything until i reinstalled restricted-extras.  Basically it didn't work at all. And the same WMV files that didn't play before, don't play now. I'm guessing it's just fully supported on Linux codecs as I haven't found one to work perfectly yet.

---

### Post by scotthep on 2008-08-07
FYI for anyone following this thread. I was also running a 64bit system and having problems playing Windows Media 9 files.  I would get a picture and no sound.

I decided to take the leap and buy the Fluendo GStreamer codecs and now Totem plays all the files I had problems with just fine. All it took was some copying of files to the /usr/lib64/gstreamer-0.10 directory.

Not sure of any other affects yet, but if I find anything I'll update.

---

### Post by jornlux on 2008-08-22
> **jtibau said:**
> 
...
```

wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb;
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb

```

I'm pretty sure that will allow you to watch wmv files...
...


jtibau : big up for solving this one. Been trying different other recommended approaches, but this was the only one I could get to work.

---

### Post by muks on 2008-09-08
> **jtibau said:**
> I don't think ubuntu-restricted-extras includes support for wmv (might be wrong). What I am sure of, is that you can easily install w32codecs using these lines:

```

wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb;
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb

```

When I run the second command, I get the following error:
```

 sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
(Reading database ... 117777 files and directories currently installed.)
Preparing to replace w32codecs 20071007-0medibuntu2 (using w32codecs_20071007-0medibuntu2_i386.deb) ...
Unpacking replacement w32codecs ...
dpkg: dependency problems prevent configuration of w32codecs:
 w32codecs depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing w32codecs (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 w32codecs

```
> **jtibau said:**
> 
I'm pretty sure that will allow you to watch wmv files...

As for encrypted dvds, the following should do the trick:

```

wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb;
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

```

Well actually I should say both of those are for the 32bit architecture (which is most likely what you have installed)...

those lines are from Medibuntu, which is a third party repository that distribute multimedia packages that can't be hosted at ubuntu's official repos... Link here; [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
These worked fine.

But now when i try to plat the wmv file i get the following error:
```
The playback of this movie requires the following decoders which are not installed:

video/x-asf-unknown decoder
Windows Media Speech decoder
```

I am running Ubuntu 8.04 32-bit

---

### Post by DroBuddy on 2008-11-07
> 

Install ubuntu-restricted-extras -- that should get wmv files going for you.
I don't think ubuntu-restricted-extras includes support for wmv (might be wrong). What I am sure of, is that you can easily install w32codecs using these lines:

Code:

wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb;](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb;)
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb

I'm pretty sure that will allow you to watch wmv files...

As for encrypted dvds, the following should do the trick:

Code:

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb;](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb;)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

Well actually I should say both of those are for the 32bit architecture (which is most likely what you have installed)...

those lines are from Medibuntu, which is a third party repository that distribute multimedia packages that can't be hosted at ubuntu's official repos... Link here; [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Okay, so I have all of my repos up-to-date and when I searched Synaptic for w32 and ubuntu-restricted-extras, neither of them show up. However, we all have to love the terminal!

After I following JTib's advice I can finally watch my .wmv's. And, oddly enough, the original author of this thread was able to see his vids, but not hear them. I wasn't able to do either. But, after I copied and pasted the above cmds into the term, everything worked like a charm. So, thank you very much for your advice and may it help several others, as well.

And, as a brief side note, the movies only play in MPlayer and not VLC (which is no big deal, I prefer MPlayer over VLC anyway). 

((Oh, and I don't normally login unless I'm extremely satisfied or pissed off... And, I must say, I am enthralled at the moment! So, thanks again.))


Peace, Love and Respect unto All,



Dro Buddy

---

