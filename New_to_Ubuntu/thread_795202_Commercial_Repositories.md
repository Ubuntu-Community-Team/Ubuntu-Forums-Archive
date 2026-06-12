---
title: "Commercial Repositories"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by lisar915 on 2008-05-15
Hello everyone,

I'm brand new to using Ubuntu, and so far it's been very interesting.  I'm using version 8.04

The thing is, I'm unable to play a Real Player file.  However, I read on another website that Real Player for Linux is available on the commercial repository.  However, when I go into the administration menu, I can't find anything about enabling the commercial repository.  

Also, is there any way to manually download Real Player for Linux without going through the Synaptic Manager, or the Commercial Repository? 

Thank you very much.

lisar915

---

### Post by rlsharpton on 2008-05-15
lisar915 here is a good howto for setting up an ubuntu desktop replacement:
[http://www.howtoforge.net/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.net/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

also with debian based linux the main installer is apt which is detailed here:
[http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents](http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents)

however the short answer to enabling the commercial repository is:
type this in a terminal window
sudo vi /etc/apt/sources.list 
then uncomment by deleting the # character then you exit vi by hitting esc then : then type wq

the file should look like: 

# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by drs305 on 2008-05-15
If you really need or want realplayer, you can go to the realplayer site to download the installation file:
[http://www.real.com/linux](http://www.real.com/linux)

It is a bin file. I installed it within the past 3 days, using guides from a thread on one of the ubuntu forums. It is a very easy process.

Even easier, here is a thread in which the OP made a .deb file, which you would just have to click to install. He didn't know how long the deb file would be available. Check it out:
[http://ubuntuforums.org/showthread.php?t=758024&highlight=realplayer+11+hardy](http://ubuntuforums.org/showthread.php?t=758024&highlight=realplayer+11+hardy)

---

### Post by lisar915 on 2008-05-15
> however the short answer to enabling the commercial repository is:
type this in a terminal window
sudo vi /etc/apt/sources.list
then uncomment by deleting the # character then you exit vi by hitting esc then : then type wq

Thank you for your quick reply.  Now please bear with me, as I am very new to all of this.  

First off, how do I access the terminal window?

Also, what exactly is meaning of "uncomment?"  

Thanks again.
lisar915

---

### Post by Inxsible on 2008-05-15
> **lisar915 said:**
> Thank you for your quick reply.  Now please bear with me, as I am very new to all of this.  

First off, how do I access the terminal window?

Also, what exactly is meaning of "uncomment?"  

Thanks again.
lisar915There is something called as Universe and Multiverse repositories. rlsharpton has given you one way to do it.

You can also do it via GUI. Go to System>>Administration>>Software Sources. Check mark the universe and multiverse boxes and then hit Ok (or is it Close).

BTW...if you still plan on doing it via terminal...its under Applications>>Accessories>>Terminal.


Having said all that...I don't think realplayer is in any of those repos. But I have been wrong before. So please check them. 

You can download realplayer from their website and then install it. That way you will get the latest version.

---

### Post by lisar915 on 2008-05-15
> You can go to the realplayer site to download the installation file:
[http://www.real.com/linux](http://www.real.com/linux)

It is a bin file. I installed it within the past 3 days, using guides from a thread on one of the ubuntu forums. It is a very easy process.

Thank you for your quick reply.  So how exactly do you install a bin file after you have manually downloaded it?  

lisar915

---

### Post by drs305 on 2008-05-15
It would be easiest to see if the deb file is still available from the thread I referenced. If it is, you just click on it. If it's not, let me know.

Added: to install a bin file, go to the directory the bin file is in (probably ~/Desktop ) and:
```

cd ~/Desktop
chmod +x RealPlayer11GOLD.bin && ./RealPlayer11GOLD.bin
```
Type the filename exactly as it appears in your folder, including capitalization.

---

### Post by rlsharpton on 2008-05-15
uncommenting is the deleting of the # character in the conf file, anything after the # is ignored by the system

---

### Post by lisar915 on 2008-05-15
> There is something called as Universe and Multiverse repositories. rlsharpton has given you one way to do it.

You can also do it via GUI. Go to System>>Administration>>Software Sources. Check mark the universe and multiverse boxes and then hit Ok (or is it Close).

Thanks.  I believe I have already enabled the Universe and Multiverse repositories (Ubuntu is installed on my home laptop).  However, I did not see Real Player there.

---

### Post by Inxsible on 2008-05-15
> **lisar915 said:**
> Thank you for your quick reply.  So how exactly do you install a bin file after you have manually downloaded it?  

lisar915

Download the file on to your desktop. Then go to a terminal and then type in```
cd ~/Desktop && chmod +x *<filename.bin>*
```The file name should be RealPlayerGold11.bin. Make sure it is the same and if not replace it with whatever the file name is of the one that you downloaded. Also make sure of the appropriate case. Then type in```
./*filename.bin*
```

---

### Post by lisar915 on 2008-05-15
So, DRS305, if I click on that .deb file link once I get home, will Real Player automatically be installed on my system?  Or is there anything else I have to do afterwards?

Thanks.
lisar915

---

### Post by drs305 on 2008-05-15
> **lisar915 said:**
> So, DRS305, if I click on that .deb file link once I get home, will Real Player automatically be installed on my system?  Or is there anything else I have to do afterwards?

Thanks.
lisar915

Once you have downloaded it, clicking on the downloaded .deb file should be all that is necessary. Follow any installation instructions. Easy!

---

### Post by lisar915 on 2008-05-15
What great service here!  Thanks for your quick replies.

Inxsible, I just want to make sure I understand you.  Are you saying I should insert <RealPlayerGold.11.bin> (or whatever the downloaded file is called where it says <filename.bin>?

Then am I supposed to hit "enter"?  

Or do I just add a space then type in ./filename.bin on the same line, right after <realplayergold.11.bin>?  

Thanks again.

---

### Post by lisar915 on 2008-05-15
> Once you have downloaded it, clicking on the downloaded .deb file should be all that is necessary. Follow any installation instructions. Easy!

Thanks DRS305.  I'll give it a try when I get home.

---

### Post by bodhi.zazen on 2008-05-15
Realplayer is a little tricky to install.

The easiest way, IMO is to use the .deb form here :

[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb)

Make a directory in your home directory src (to saev the deb)

To install :

```
sudo dkpg -i realplayer*
```

Then to install the dependencies :

```
sudo apt-get install -f
```

You may need to install additional packages to play some formats. 

I had to :```
sudo apt-get install mplayer
```

See this link for additional formats (mp3, way, etc)

See also : [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by drs305 on 2008-05-15
bodhi.zazen,

I'm pretty sure I didn't have to do any of that. It is possible that the creator of the deb package that I used had already done what was required so users of his deb wouldn't have to.

In any case, lisar915, if just clicking on the deb package doesn't work, bodhi.zazen has been kind enough to provide more detailed instructions for the standard .deb file.

---

### Post by ubuntu-freak on 2008-05-15
> **lisar915 said:**
> Hello everyone,

I'm brand new to using Ubuntu, and so far it's been very interesting.  I'm using version 8.04

The thing is, I'm unable to play a Real Player file.  However, I read on another website that Real Player for Linux is available on the commercial repository.  However, when I go into the administration menu, I can't find anything about enabling the commercial repository.  

Also, is there any way to manually download Real Player for Linux without going through the Synaptic Manager, or the Commercial Repository? 

Thank you very much.

lisar915

Take a look at my [how-to](http://ubuntuforums.org/showthread.php?t=766683), it's quite detailed, explains where the Terminal is, how to enable extra repositories, enable multimedia formats etc. Leave a message there if you need help. I doubt you will really need RealPlayer.

Nathan

---

### Post by kamitsukai on 2008-05-15
Why do you need realplayer? Mplayer (go to add/remove prgrams and search) will play any non-drm realplayer file just fine...

---

### Post by ubuntu-freak on 2008-05-15
> **kamitsukai said:**
> Why do you need realplayer? Mplayer (go to add/remove prgrams and search) will play any non-drm realplayer file just fine...

 
Exactly, and the Gecko Media Player plugin (dev behind the now dead mplayerplug-in) streams them wonderfully. 
 
Nathan 
 
P.S. I presume it's dead, it uses MPlayer still, but works better than mplayerplug-in and doesn't need configuring.

---

### Post by bodhi.zazen on 2008-05-15
> **drs305 said:**
> bodhi.zazen,

I'm pretty sure I didn't have to do any of that. It is possible that the creator of the deb package that I used had already done what was required so users of his deb wouldn't have to.

In any case, lisar915, if just clicking on the deb package doesn't work, bodhi.zazen has been kind enough to provide more detailed instructions for the standard .deb file.

Thank you for your kind words.

> **reassuringlyoffensive said:**
> Take a look at my [how-to]("http://ubuntuforums.org/showthread.php?t=766683"), it's quite detailed, explains where the Terminal is, how to enable extra repositories, enable multimedia formats etc. Leave a message there if you need help. I doubt you will really need RealPlayer.

Nathan

wow, that is one heck of a detailed how-to, I will have to look at it later.

> **kamitsukai said:**
> Why do you need realplayer? Mplayer (go to add/remove prgrams and search) will play any non-drm realplayer file just fine...

My wife has a stream she listens to. The only way I have been able to get it to work is by installing RealPlayer + mplayer, as outlined. I have tried *all* the alternates as I am not a big fan of RealPlayer :rolleyes:

I may look into Nathan's how to, but at first glance nothing new stands out (ie been there , done that).

---

### Post by ubuntu-freak on 2008-05-15
> **bodhi.zazen said:**
> wow, that is one heck of a detailed how-to, I will have to look at it later.

My wife has a stream she listens to. The only way I have been able to get it to work is by installing RealPlayer + mplayer, as outlined. I have tried *all* the alternates as I am not a big fan of RealPlayer :rolleyes:

I may look into Nathan's how to, but at first glance nothing new stands out (ie been there , done that).

 
Thanks. It was only a streaming how-to when I first wrote it, but I'm obsessive, so it grew and changed. :-)
 
So, even Gecko Media Player didn't work with the stream your wife likes to play? Might be worth telling the dev, as almost all the streams I've tested worked.
 
Nathan

---

### Post by bodhi.zazen on 2008-05-15
yea, no ...

We have been trying to stream this for my wife for a long time (over a year). My brother-in-law is a Windows geek (my understanding is he manages a server farm for IBM). Neither of us could get the stream to work on any OS, however I crawled through obscure google hits for what seemed like the 10th time a few nights ago and was able to get it up and running by the method I posted.

Proud to say Ubuntu geek beat Windows geek ...

There is something very odd about this stream, all I know is how to hack it at this point.

I will let you know if I find more ...

---

### Post by ubuntu-freak on 2008-05-15
Ah okay. So it's an exceptionally poorly implemented stream, instead of just poorly implemented. I understand.
 
Nathan

---

### Post by lisar915 on 2008-05-15
Hi folks, 

It looks like I managed to install Real Player using that original link for the .deb file.  And everything seemed to work.  However, I am still unable to play rm audio files.  

Any suggestions will be greatly appreciated.

Thanks.

---

### Post by drs305 on 2008-05-15
> **lisar915 said:**
> Hi folks, 

It looks like I managed to install Real Player using that original link for the .deb file.  And everything seemed to work.  However, I am still unable to play rm audio files.  

Any suggestions will be greatly appreciated.
Thanks.

Is there an online link you are trying to play?

Added: And what exactly happens when you try to play it?

---

### Post by lisar915 on 2008-05-15
Hi,

Now I have both Mplayer and RealPlayer installed, and when I try playing the rm file I get this error message:

"G Streamer encountered a general stream error."

Hope that helps.

Thanks.

---

### Post by lisar915 on 2008-05-15
I should also add that before I installed Mplayer, the Totem player automatically came up when I tried playing the file, even though I had just installed Real Player.  When I clicked play, nothing happened.

---

### Post by lisar915 on 2008-05-15
Also, I just noticed something else that's odd.  

When I click on "Add/Remove Programs" and then click "installed programs" Real Player doesn't even show up on the list.  

However, when I go into the Synaptic Manager, and click on "installed programs" Real Player is listed.  

Does anyone know why that is, or what I'm doing wrong?

Thanks again.

---

### Post by drs305 on 2008-05-15
Is it listed in the main menu under 'Sound & Video'?

Are you opening a file on the internet or on your drive? If from your drive, right click on the file and select play with realplayer. Then what happens?

Can you play the Eric Clapton video on the RealPlayer site here:
[http://www.rhapsody.com/clapton/commercials/1](http://www.rhapsody.com/clapton/commercials/1)

Are you using firefox? If so, a great add-on is MediaPlayerConnectivity, which will let you choose what player you wish to play a given link.

---

### Post by lisar915 on 2008-05-15
> [QUOTE]Are you opening a file on the internet or on your drive?
Can you play the Eric Clapton video on the RealPlayer site here:
[http://www.rhapsody.com/clapton/commercials/1](http://www.rhapsody.com/clapton/commercials/1)

Are you using firefox? If so, a great add-on is MediaPlayerConnectivity, which will let you choose what player you wish to play a given link.
[/QUOTE]

Dear DRS305,

I'm trying to play the rm file on my hard drive.  

And I was unable to play that Eric Clapton video.  :confused:

---

### Post by drs305 on 2008-05-15
I'm going to send you a PM. Maybe we can get this resolved. You send a PM by clicking on the poster's name.

In the meantime, anyone else who would like to chime in here please feel free.

---

### Post by ubuntu-freak on 2008-05-15
> **drs305 said:**
> I'm going to send you a PM. Maybe we can get this resolved. You send a PM by clicking on the poster's name.

In the meantime, anyone else who would like to chime in here please feel free.

 
Have you completed Part 1 and 2 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683)? That's all you need to do. 
 
Nathan

---

### Post by billgoldberg on 2008-05-15
I made an VERY easy to follow guide on it (pictures included):

[http://linuxowns.wordpress.com/2008/04/15/real-player-11/](http://linuxowns.wordpress.com/2008/04/15/real-player-11/)

and you don't need to go messing in the terminal (cli).

[I]note: some posters here don't seem to understand that this is the absolute beginners forum.

The first answer to the OP's question is a good example on how not to give advise in this subforum.[/I]

---

