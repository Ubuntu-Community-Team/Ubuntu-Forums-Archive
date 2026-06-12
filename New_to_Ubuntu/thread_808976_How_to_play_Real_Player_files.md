---
title: "How to play Real Player files?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by ralphygarfield on 2008-05-27
I need helping finding and installing a codec or player to play Real Player videos. 

Please give me a link and/or instructions of where to DL it. 

I've tried searching in Applications but couldn't find anything.

---

### Post by adobrakic on 2008-05-27
What extention is it?
You could probably play it in VLC Player

---

### Post by kpkeerthi on 2008-05-27
> **ralphygarfield said:**
> I need helping finding and installing a codec or player to play Real Player videos. 

Please give me a link and/or instructions of where to DL it. 

I've tried searching in Applications but couldn't find anything.

VLC will be your best bet. There is also [helix-player]("https://help.ubuntu.com/community/HelixPlayer")

---

### Post by ralphygarfield on 2008-05-27
Guys, I need you to be a little more specific than that.

I am not good with computers. 

I went to that link, but Linux said that it could not open the installer. 

As with any post I make, I need direct instructions. 

Where and how do I download the player?

...

---

### Post by adobrakic on 2008-05-27
go to system > admin > synaptic package manager and click on search at the top right.
type in 'VLC' and scroll down to where it says vlc. then click on the box and press "mark for installation" and press 'apply' at the top.

---

### Post by alienexplorers on 2008-05-27
I use the linux version of Real Player 10.

---

### Post by ralphygarfield on 2008-05-27
sorry guys, but none of that is working to open the one player I need.

I tried searching for Real Player 10 in Synaptic manager... it didn't find it. 

How do I download Real Player?

Please be more specific this time.

---

### Post by Samurai Penguin on 2008-05-27
you can download RealPlayer by clicking on the following link ...

[http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

put it on the desktop, double click it and it should install itself

---

### Post by ralphygarfield on 2008-05-27
> **Samurai Penguin said:**
> Or ... how about using RealPlayer ?

download this file

[http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

put it on the desktop, double click it and it should install itself



...

Just an hour ago I said that so far my Linux experiences have been very positive.... now that is wavering. 

That Real Player link keeps failing to install. After installation, a black terminal Windows keeps popping up to say that it failed. 

Could it be because I already installed Helix player? 

Please help me out here.

---

### Post by adobrakic on 2008-05-27
> **ralphygarfield said:**
> sorry guys, but none of that is working to open the one player I need.

I tried searching for Real Player 10 in Synaptic manager... it didn't find it. 

How do I download Real Player?

Please be more specific this time.

Why does it not work? VLC Player plays like every known type of file out there. Maybe it's the file you downloaded?

---

### Post by Samurai Penguin on 2008-05-27
that link doesn't install, it will just download the package. Sounds like a spoiled brat - and controlling - to say "so far my Linux experiences have been very positive.... now that is wavering." Are you stil wavering?

---

### Post by ralphygarfield on 2008-05-27
> **adobrakic said:**
> Why does it not work? VLC Player plays like every known type of file out there. Maybe it's the file you downloaded?



VLC is CRAP and ALWAYS has been for me. 

The Real Player installer does not work. I keep getting a black terminal that pops up to say "failure".

COULD IT BE BECAUSE I HAVE HELIX ALREADY INSTALLED?

What could be going on!?

The installer does not work!

---

### Post by ralphygarfield on 2008-05-27
> **Samurai Penguin said:**
> that link doesn't install, it will just download the package. Sounds like a spoiled brat - and controlling - to say "so far my Linux experiences have been very positive.... now that is wavering." Are you stil wavering?



I insulted your OS so now you're going to cry and insult ME?:popcorn::lolflag::guitar::confused:

I KEEP GETTING A BLACK SCREEN AFTER THE REAL PLAYER INSTALL WHICH SAYS IT FAILED!

---

### Post by adobrakic on 2008-05-27
If VLC is crap for you, then idk what to tell you. :x There is really nothing better. 
But whatever, find mplayer in synaptic and install that. and no, i doubt its because you already have helix installed, but if it makes you feel better, you can go to applications > add/remove programs and uninstall it from there.

btw, no need for caps. we're all trying to be helpful.

---

### Post by Samurai Penguin on 2008-05-27
maybe if you were grateful instead of complaining then it would go much better for you?

---

### Post by alienexplorers on 2008-05-27
[http://www.real.com/dmm/superpass?pcode=cj&ocode=cj&cpath=aff&rsrc=1175270_10301041_14dLP]("http://www.real.com/dmm/superpass?pcode=cj&ocode=cj&cpath=aff&rsrc=1175270_10301041_14dLP")

---

### Post by RSingh on 2008-05-27
Realplayer files require Realplayer

Try this (easier) (Source: [https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealPlayer](https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealPlayer))
Install RealPlayer.deb using dkpg

      Download realplayer_10.0.9-0.1_i386.deb from this [mirror]("http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb").

**Just double click the file and follow the installation procedure.**

      To uninstall RealPlayer, open a Terminal and type:

       $ sudo dpkg -r realplayer

**If that didnt work then do this:**

Go Here:
[URL="http://www.real.com/linux"]
http://www.real.com/linux[/URL]

Download the file to the desktop.

Right click on the file, properties and go the permissions tab and make sure "allow executing as a program" is ticked.

open terminal.
type this one by one and press enter, entering you password when required after the 2nd command:

```

cd Desktop
sudo ./RealPlayer11GOLD.bin

```

After this keep replying yes and keep pressing enter whenever asked.

**Either way you should get realplayer working**

---

### Post by sayakb on 2008-05-27
One who thinks VLC is a crap needs medical attention :lolflag:
VLC is a platform flexible (Runs on Windows, Linux, Mac, BSD with Intel, AMD, PowerPC, SPARC architectures)

It can play EVERYTHING on Linux except for Real media:
[http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)

RSingh told you how to get Real Linux working, and that, exactly is how, even a 5th grade child might do successfully. So if you can't do it, simply install the OS you are capable of "understanding"

DON'T FEED THE TROLL

---

### Post by ralphygarfield on 2008-05-27
Ok. Sorry for getting so mad guys.

So far I've tried everything you told me. I've successfully installed all your programs. I still can't get my file to play. 

it is a .ram file and it says I need a ivr codec.

I have also got this error: 

The playback of this movie requires a Sipro/ACELP.NET Voice decoder plugin which is not installed.

Please help if you can, just bare in mind that I need very detailed instructions. I am new to Linux and have never had good knowledge on computers.

---

### Post by RSingh on 2008-05-27
did u try my method??

---

### Post by ralphygarfield on 2008-05-27
> **RSingh said:**
> did u try my method??


Yes. Your player works fine. It just won't play my file.

So far I've tried everything you told me. I've successfully installed all your programs. I still can't get my file to play.

it is a .ram file and it says I need a ivr codec.

I have also got this error:

The playback of this movie requires a Sipro/ACELP.NET Voice decoder plugin which is not installed.

---

### Post by kpkeerthi on 2008-05-27
> **ralphygarfield said:**
> Yes. Your player works fine. It just won't play my file.

So far I've tried everything you told me. I've successfully installed all your programs. I still can't get my file to play.

it is a .ram file and it says I need a ivr codec.

I have also got this error:

The playback of this movie requires a Sipro/ACELP.NET Voice decoder plugin which is not installed.

I just found this thread [http://ubuntuforums.org/showthread.php?t=539494](http://ubuntuforums.org/showthread.php?t=539494)

The poster seems to have solved it with real player for linux. Did you try real player?

---

### Post by RSingh on 2008-05-27
Try adding the Medibuntu repository:

      Ubuntu 8.04 "Hardy Heron", Enter these in terminal one by one:

      ```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

Then, add the GPG Key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Then install the package (w32codecs) from synaptic and try playing the file.

also make sure u have all of the codecs:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse 
 gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3
```

---

### Post by ralphygarfield on 2008-05-27
> **kpkeerthi said:**
> I just found this thread [http://ubuntuforums.org/showthread.php?t=539494](http://ubuntuforums.org/showthread.php?t=539494)

The poster seems to have solved it with real player for linux. Did you try real player?



Dude, I've said like 3 times now that Real Player is not working either. This is how I get frustrated and start acting like a "Troll". Thanks for trying though. 

My file will still not open, so something else must be wrong. I don't know.

---

### Post by adobrakic on 2008-05-27
[http://ubuntuforums.org/showthread.php?t=477227](http://ubuntuforums.org/showthread.php?t=477227)
try reading through that.
all of it.

---

### Post by ralphygarfield on 2008-05-27
> **RSingh said:**
> Try adding the Medibuntu repository:

      Ubuntu 8.04 "Hardy Heron", Enter these in terminal one by one:

      ```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

Then, add the GPG Key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Then install the package (w32codecs) from synaptic and try playing the file.

also make sure u have all of the codecs:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse 
 gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3
```



The second code you gave does not work.

---

### Post by RSingh on 2008-05-27
What does it say in the terminal

---

### Post by ralphygarfield on 2008-05-27
> **adobrakic said:**
> [http://ubuntuforums.org/showthread.php?t=477227](http://ubuntuforums.org/showthread.php?t=477227)
try reading through that.
all of it.

The terminology and the complicity of that thread makes no sense to me. 

Please summarize.

---

### Post by ralphygarfield on 2008-05-27
> **RSingh said:**
> I would advise you to go through my last post as that should ensure no codec problem would occur again. 

But I am surprised that Realplayer didn't play  the file??


The second code you gave does not work.

---

### Post by RSingh on 2008-05-27
could you post your terminal text.

The third code piece is all one line.

---

### Post by ralphygarfield on 2008-05-27
> **RSingh said:**
> could you post your terminal text.

The third code piece is all one line.


I just realized that I am getting and error after the first code:

... Connection refused.
/etc/apt/sources.list.d/medibuntu.list: Unsupported scheme

 Then after the second code:

E: Couldn't find package medibuntu-keyring

Not trying to be mean or anything, but all of this terminal work is absolutely putrid. There's got to be another way to do and install this stuff. To be perfectly honest, if I have to do much more of this kind of work I will be giving up on Linux. 

Although I appreciate your work here, and you have been the most helpful user so far.

---

### Post by Mr. Svinlesha on 2008-05-27
Might I also hop in here?  I'm having the same problem as **ralphygarfield**.

I've installed realplayer as per the instructions above, sucessfully.  Then I went to this [page]("http://www.democracynow.org/") and tried to view a broadcast.  Using Firefox3 beta 5 I was prompted to select realplayer as the default application.  When I did so, Firefox chose to open Totem instead, and I got the following error message: 

> Sipro/ACELP.NET Voice decoder
RealVideo 4.0 decoder

I'm guessing that garfield's having the same problem, and just hasn't noticed that Totem is opening instead of Realplayer.

**ralphygarfield**, are you sure realplayer opens when you try to play your movie?

---

### Post by RSingh on 2008-05-27
@ralphygarfield

Are you using ubuntu Hardy Heron or an older version?

---

### Post by ralphygarfield on 2008-05-27
> **Mr. Svinlesha said:**
> Might I also hop in here?  I'm having the same problem as **ralphygarfield**.

I've installed realplayer as per the instructions above, sucessfully.  Then I went to this [page]("http://www.democracynow.org/") and tried to view a broadcast.  Using Firefox3 beta 5 I was prompted to select realplayer as the default application.  When I did so, Firefox chose to open Totem instead, and I got the following error message: 



I'm guessing that garfield's having the same problem, and just hasn't noticed that Totem is opening instead of Realplayer.

**ralphygarfield**, are you sure realplayer opens when you try to play your movie?


Well it looks a lot like the real player I use on Windows, and it has the real player logo, so yes, I'm 100% sure. 

I don't know what Totem is. 

An no, I don't think our problems sound similar at all.

---

### Post by ralphygarfield on 2008-05-27
> **RSingh said:**
> @ralphygarfield

Are you using ubuntu Hardy Heron or an older version?



I am using 8.04, yes

I'll be back in about 15 minutes.

---

### Post by billgoldberg on 2008-05-27
> **ralphygarfield said:**
> I need helping finding and installing a codec or player to play Real Player videos. 

Please give me a link and/or instructions of where to DL it. 

I've tried searching in Applications but couldn't find anything.

Ok, I didn't read the whole thread and it could be that your issue is already solved but I'll explain it anyway.

First, if you installed vlc from the normal repository, remove it.

Install the medibuntu repository and then install vlc.

[link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

Check if vlc can play the file then.

If vlc can't play the file (unlikely), you can install real player 11 for linux.

*(on that link, also install the non free codecs and win32 codecs)*

[link]("http://linuxowns.wordpress.com/2008/04/15/real-player-11/")

If you need to view a real player stream online: 

go to synaptic and search for "firefox vlc", install the plugin and use it in firefox. That should fix the streaming issue.

---

### Post by RSingh on 2008-05-27
Well if all of this doesnt work then it is beyond me.

I would advise you not to give up on linux. Keep trying and hopefully some fix should be there.

---

### Post by ralphygarfield on 2008-05-27
> **billgoldberg said:**
> Ok, I didn't read the whole thread and it could be that your issue is already solved but I'll explain it anyway.

First, if you installed vlc from the normal repository, remove it.

Install the medibuntu repository and then install vlc.

[link]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

Check if vlc can play the file then.

If vlc can't play the file (unlikely), you can install real player 11 for linux.

*(on that link, also install the non free codecs and win32 codecs)*

[link]("http://linuxowns.wordpress.com/2008/04/15/real-player-11/")

If you need to view a real player stream online: 

go to synaptic and search for "firefox vlc", install the plugin and use it in firefox. That should fix the streaming issue.


Sorry but I don't understand your instructions at all. And I'm done playing around and trying to guess what people mean cause that just messes things up more.

medibuntu repository?

There are many files of mine that VLC doesn't work for. The file either doesn't play and VLC just sits there, or the audio plays but not video.

---

### Post by ralphygarfield on 2008-05-27
> **RSingh said:**
> Well if all of this doesnt work then it is beyond me.

I would advise you not to give up on linux. Keep trying and hopefully some fix should be there.


What do you mean "if all of this doesn't work"? I've already tried everyone's instructions, and I gave you info on those terminal errors. Do you have further instructions? Why did you ask for info on the terminal errors if you don't?

---

### Post by billgoldberg on 2008-05-27
> **ralphygarfield said:**
> Sorry but I don't understand your instructions at all. And I'm done playing around and trying to guess what people mean cause that just messes things up more.

medibuntu repository?

There are many files of mine that VLC doesn't work for. The file either doesn't play and VLC just sits there, or the audio plays but not video.

If you install an application in ubuntu, the application gets downloaded from a software repository.

The medibuntu repository is a software repository that has media applications that aren't in the normal repositories.

The vlc version you installed from the normal repositories is lacking features the vlc version from the medibuntu repository has.

*(because of copyright issues)*
-----------

wikipedia link for clarification:

[http://en.wikipedia.org/wiki/Linux_repository](http://en.wikipedia.org/wiki/Linux_repository)

---

### Post by Mr. Svinlesha on 2008-05-27
> [I]Well it looks a lot like the real player I use on Windows, and it has the real player logo, so yes, I'm 100% sure.

I don't know what Totem is.

An no, I don't think our problems sound similar at all.[/I]

And yet we get the same error message.  Very strange.

I've solved my problem like this:

I installed realplayer in my home directory, since this seemed to be easiest. When I launched my browser and told Firefox I wanted to use realplayer as the default application for this particular format, it opened Totem instead (as noted earlier).

It occurred to me that maybe Firefox couldn't find the Linux equivalent of the realplayer .exe file; the applications program was trying to open the realplayer folder, and, when that didn't work, fell back to a secondary default player that also didn't work because it didn't have the right codex.

So I opened up my home folder and discovered a file in it named "Realplay", which was labeled under "type" as "Realplayer launch script."  Hmmm... maybe that's the file that Firefox needs to use to launch Realplayer.  So back to Firefox > Edit > Peferences, and then under the Applications tab, I located the file type (RA file) and then under action I "browsed" to the launch script and selected it as the default for handling these sorts of files.

Now Realplayer works fine.

If the file you want is on your hard disk, you can try the same thing: right click, select preferences, "Open with", but don't accept the "Realplayer" choice; instead, try browsing to the launch script and see if that helps.

I'll be glad to go back through these steps one by one if you need me to, and if it helps.

---

