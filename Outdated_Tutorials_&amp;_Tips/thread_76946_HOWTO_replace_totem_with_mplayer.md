---
title: "HOWTO: replace totem with mplayer"
date: 2005-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Hairy_Palms on 2005-10-16
i find that on 3 installs so far on 3 different machines totem-plugin is broken in firefox, so ive decided to write a howto replace it with mplayer-plugin


1.delete the totem plugins from /usr/lib/mozilla-firefox/plugins
libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt 

2. install mplayer plugin
sudo apt-get install mplayer-386
sudo apt-get install mplayer-fonts
sudo apt-get install mozilla-mplayer

3. then you might need the codecs for quicktime etc, getit from
[http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2)
then extract them to the folder /usr/lib/win32

ive written a script that will do it for you,

---

### Post by Elephantman on 2005-10-16
Hi,

I already have some dependency problems to install mplayer...

mplayer-586: Depends: libfribidi0 (>= 0.10.5-4) but 0.10.5-2 will have to be installed
               Depends: libjack0.100.0-0 (>= 0.100.0) but it is not installable
               Depends: libstdc++6 (>= 4.0.2) mais 4.0.1-4ubuntu9 will have to be installed

I was hoping to meet success in installing mplayer with breezy but seems I'm already too late for the dependencies :???: 

Any way out ?

(Dont beware of the inexact messages, I've translated them from french).

---

### Post by livecdlover on 2005-10-16
My biggest complaint with Ubuntu was it's inability to play movies trailers from the quicktime site.  That's not so bad since it does everything else really well.

I just used the Mplayer instruction above and the repository information at [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html) .  I found this link in the Ubuntu forums.  Mplayer now works perfectly embedded in Firefox.  I can even hit the back button in Firefox while playing a movie and Firefox doesn't shut down.  I don't kow why Ubuntu uses Totem.  :D

---

### Post by WetWilly on 2005-10-17
[QUOTE=livecdlover]I don't kow why Ubuntu uses Totem.  :D[/QUOTE]

I ask myself the same thing. Totem actually sucks =(

---

### Post by unperson on 2005-10-18
[QUOTE=Elephantman]Hi,

I already have some dependency problems to install mplayer...

mplayer-586: Depends: libfribidi0 (>= 0.10.5-4) but 0.10.5-2 will have to be installed
               Depends: libjack0.100.0-0 (>= 0.100.0) but it is not installable
               Depends: libstdc++6 (>= 4.0.2) mais 4.0.1-4ubuntu9 will have to be installed

I was hoping to meet success in installing mplayer with breezy but seems I'm already too late for the dependencies :???: 

Any way out ?

(Dont beware of the inexact messages, I've translated them from french).[/QUOTE]

Elephantman, I  just tried the procedure from the first post on my fresh install of breezy and it worked fine.  What repositories are you using?  Usually those sorts of dependancy issues come from using repositories together that weren't designed to be used together.  I'm using the repositories listed in the first post [here]("http://www.ubuntuforums.org/showthread.php?t=76132"), minus the cipherfunk and wine repositories.

Also, once you get it working, you might like to test out the that the mozilla plugin is working properly.  If you've got all the appropriate codecs (say from w32codecs) then you might try these sites for that purpose:

[http://fredrik.hubbe.net/plugger/test.html]("http://fredrik.hubbe.net/plugger/test.html")
[http://www.apple.com/trailers/]("http://www.apple.com/trailers/")

---

### Post by kris kincaid on 2005-10-19
I'll admit it, I just did everything palms said to do only I checked boxes in the Synaptic Package Manager. Worked awesome and I can see the Quicktime trailers.

Awesome!! :p

---

### Post by Hairy_Palms on 2005-10-19
glad to help :)
i havent tried mplayer-586 i use mplayer-386 under hoary there was no real speed benefit and -386 worked so i didnt change see if mplayer-386 will work for you.

---

### Post by Hairy_Palms on 2005-10-19
hmmm it has the same dependancies, have you enabled the universe and multiverse repos?

---

### Post by manicka on 2005-10-19
nice little how-to, thanks :)

---

### Post by lostdata on 2005-10-19
I tried to do this but when i tried to get the mplayer it couldn't find it in the repositories i'm bruning breezy badger i have uncommented all the repositories but the backports because that one doesn't work... any ideas?

---

### Post by manicka on 2005-10-19
[QUOTE=lostdata]I tried to do this but when i tried to get the mplayer it couldn't find it in the repositories i'm bruning breezy badger i have uncommented all the repositories but the backports because that one doesn't work... any ideas?[/QUOTE]
sudo apt-get update

---

### Post by lostdata on 2005-10-19
i did apt-get update but its still not finding anything...

---

### Post by manicka on 2005-10-19
please post your sources.list

---

### Post by silex on 2005-10-19
So, I've done what you proscribed and it seems to work well, all the way through buffering a movie trailer form apple to 99%.  When it hits 99% it stops and just sits there indefinitely... Has anyone else had this problem or have a workaround?

---

### Post by onesojourner on 2005-10-20
I have the same problem. it loads 99% then stops. 

If I download the script that you posted what do I do with it?

---

### Post by jeffreyvergara.NET on 2005-10-20
will this only install mplayer plugin for firefox and not the whole mplayer? I really don't want to have too many media player installed.

---

### Post by NeoChaosX on 2005-10-20
Some version of mplayer is necessary for it's plugin to work. You can just install mplayer-nogui so you don't have to deal with the player being in your menu, though.

---

### Post by manis on 2005-10-21
Hi,
Our friend said:

  My biggest complaint with Ubuntu was it's inability to play movies trailers from    the quicktime site. That's not so bad since it does everything else really well.:( 

And I suggest you to use Gxine as your browser plugin with Firefox. I have tried this  application - the sound and picture is very good. :p 
 tk

---

### Post by mjukr on 2005-10-21
Thanks for this howto. This guide is the only one that's resulting in successful viewing of embedded videos on [http://trailers.apple.com](http://trailers.apple.com).

THANKS!!!

---

### Post by majkmil on 2005-10-21
Thanks, Works great! I was a little suprised when I went to NFL.COM and RealPlayer was replaced by MPLAYER. I tried the trailers on the apple site and they looked great.

---

### Post by lostdata on 2005-10-21
ok i have tried apt-get update and i am still unable to install mplayer-386 nor 586 i'm running breezey badeger i have already installed the win32 codecs the following is the error i get


```

Fetched 60.9kB in 1s (32.4kB/s)
Reading package lists... Done
lostdata@UPE:~$ sudo apt-get install mplayer-586
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-586
lostdata@UPE:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386
```


the following is my sources.list

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

if someone knows a repository i can add to get this i would appreciate it

---

### Post by lostdata on 2005-10-22
I have ssh'd to my box and found the following repository and added it, i was able to install all the packages now, i will test firefox tonight when i get home...

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) breezy universe multiverse

---

### Post by lostdata on 2005-10-22
woohoo works great thanks

---

### Post by bored2k on 2005-10-22
[http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)
[http://rapidshare.de/files/6593654/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6593654/mplayer_1.0cvs_i386.deb.html)

October 22nd (2005) build of CVS MPlayer with **GTK2 GUI**, OSD support, Big files (>2GB) support and most of the audio/video outputs. Compiled on Ubuntu 5.10 Breezy Badger **for x86 CPU** with extensions: MMX MMX2 SSE SSE2.

[http://www.ubuntuforums.org/showpost.php?p=434710&postcount=72](http://www.ubuntuforums.org/showpost.php?p=434710&postcount=72)

---

### Post by 4linux on 2005-10-23
Works great for me.  :) 

BTW, I installed the win32 codecs this way: According to Tic Toc's instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=79404&highlight=win32")

-Pat

---

### Post by Cl1mh4224rd on 2005-10-24
Ok, so... it all went well. I head on over to check out the Serenity trailer, and it's just peachy. Then I check out the trailer for [New World Order](http://www.apple.com/trailers/newline/the_new_world/) and... *bam bam bam*... As the page loads I get slammed with three popup windows, one for each version/size of the trailer.

I try to close them and they just come right back, because the videos are still being buffered.

What the heck's going on here?

---

### Post by TiMBuS on 2005-10-24
haha, apt-getting mplayer fonts:

Need to get 1337kB of archives.

well there ya go.

---

### Post by coaxx on 2005-11-09
[http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2)

seems to be down at the moment...

---

### Post by agds on 2005-11-09
Thanks for the HowTo.  It's been very useful.  I can finally watch videos without Totem Mozilla Plugin crashing the browser.  Some of the "fancier" trailers on Apple's site don't quite work as expected, but this is a vast improvement.

---

### Post by christooss on 2005-11-09
[QUOTE=coaxx][http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2)

seems to be down at the moment...[/QUOTE]

TRy using deb which bored2k provided in his post

---

### Post by linux_fish on 2005-11-27
Installed everything per instructions and it works. However the video/ audio is choppy. Any ideas?

---

### Post by agds on 2005-11-27
I've noticed this too.  In my experience, it only happens with certain videos.  When that happens, I just use the right-click menu to save the video to disk.  Unfortunately this strategy doesn't work with streaming video.

---

### Post by linux_fish on 2005-11-27
[QUOTE=agds]I've noticed this too.  In my experience, it only happens with certain videos.  When that happens, I just use the right-click menu to save the video to disk.  Unfortunately this strategy doesn't work with streaming video.[/QUOTE]

This seems to happen at all sites. Is there any way to have the option to open mplayer to play the files, instead of keeping them imbedded?

---

### Post by agds on 2005-11-27
I suppose you could go to Edit -> Preferences -> Downloads -> Plug-Ins and disable the relevant media plug-ins.  That would force Firefox to download the files instead of playing them embedded in the browser window.  Or at least it should theoretically have that effect.

---

### Post by Cl1mh4224rd on 2005-12-04
[QUOTE=Cl1mh4224rd]Ok, so... it all went well. I head on over to check out the Serenity trailer, and it's just peachy. Then I check out the trailer for [New World Order](http://www.apple.com/trailers/newline/the_new_world/) and... *bam bam bam*... As the page loads I get slammed with three popup windows, one for each version/size of the trailer.

I try to close them and they just come right back, because the videos are still being buffered.

What the heck's going on here?[/QUOTE]
Anyone else have this problem? It's really quite annoying...

I've also noticed that when watching clips of *The Daily Show* (which are streamed) on Comedy Central's website, at the end of the clip the video will cut out a few seconds before the audio. It's not a synchronization issue, because the video and audio match perfectly throughout the clip.

Totem may not work at all, but MPlayer as a plugin seems to have a slew of problems itself...

---

### Post by nix4me on 2005-12-04
[QUOTE=Cl1mh4224rd]Anyone else have this problem? It's really quite annoying...

Totem may not work at all, but MPlayer as a plugin seems to have a slew of problems itself...[/QUOTE]

Yes it does.  Multimedia on Linux in general is a mess.
mplayerplug-in will also crash firefox if you play some embedded mpg and then try to play an older wmv file.  Crashes every time.

nix4me

---

### Post by bored2k on 2005-12-04
[QUOTE=nix4me]Yes it does.  Multimedia on Linux in general is a mess.
mplayerplug-in will also crash firefox if you play some embedded mpg and then try to play an older wmv file.  Crashes every time.

nix4me[/QUOTE]
That is **your ** experience. My mplayer plugin "3.11 and >" hardly fail on me. I play a lot of videos and there's hardly anything I can't play.

---

### Post by nix4me on 2005-12-04
[QUOTE=bored2k]That is **your ** experience. My mplayer plugin "3.11 and >" hardly fail on me. I play a lot of videos and there's hardly anything I can't play.[/QUOTE]

Well, i have tried 3.11 and cvs 3.16.  Still crashes.  The following sequence will crash mine every time.

Play these in order (they are motorcycle videos):
[ftp://ftp.motorcycle.com/pub/videos/GSXR_Dyno.mpg](ftp://ftp.motorcycle.com/pub/videos/GSXR_Dyno.mpg)
[http://www.motorcycle.com/mo/mcbeware/03_Judgement_Day/Judgement_Day.wmv](http://www.motorcycle.com/mo/mcbeware/03_Judgement_Day/Judgement_Day.wmv)

nix4me

---

### Post by nix4me on 2005-12-04
[QUOTE=nix4me]Well, i have tried 3.11 and cvs 3.16.  Still crashes.  The following sequence will crash mine every time.

Play these in order (they are motorcycle videos):
[ftp://ftp.motorcycle.com/pub/videos/GSXR_Dyno.mpg](ftp://ftp.motorcycle.com/pub/videos/GSXR_Dyno.mpg)
[http://www.motorcycle.com/mo/mcbeware/03_Judgement_Day/Judgement_Day.wmv](http://www.motorcycle.com/mo/mcbeware/03_Judgement_Day/Judgement_Day.wmv)

nix4me[/QUOTE]


Has anyone tried this?  I would love to hear your failures/success.

nix4me

---

### Post by agds on 2005-12-06
[QUOTE=nix4me]Has anyone tried this?  I would love to hear your failures/success.

nix4me[/QUOTE]
Firefox didn't crash.  The only problem I had was choppy sound on the first video.

---

### Post by penguinman007 on 2005-12-06
mplayer is not in my packages and I can't get it.
Is there any other media player.

Totem gives me an error.

I don;t care what is the best media player, I just want something that works.

---

### Post by agds on 2005-12-06
[QUOTE=penguinman007]mplayer is not in my packages and I can't get it.
Is there any other media player.

Totem gives me an error.

I don;t care what is the best media player, I just want something that works.[/QUOTE]
I forget which repository has MPlayer.  Could you post your /etc/apt/sources.list?

---

### Post by frodon on 2005-12-06
Read that if you have questions about source.list : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by penguinman007 on 2005-12-06
system->Preferences->Multimedia System Selector

I selected something else and it now works.
It seems that the windows manager uses a 'device' and the media player needs another one.

mmm how very un obvious and convoluted.

---

### Post by Cl1mh4224rd on 2005-12-06
[QUOTE=bored2k]That is **your ** experience. My mplayer plugin "3.11 and >" hardly fail on me. I play a lot of videos and there's hardly anything I can't play.[/QUOTE]
What's your experience with the [The New World](http://www.apple.com/trailers/newline/the_new_world/) trailer site?

I really would like to get a confirmation, or even a denial, of the issue I've posted about twice already, but everyone seems to ignore it...

---

### Post by bored2k on 2005-12-06
[QUOTE=Cl1mh4224rd]What's your experience with the [The New World](http://www.apple.com/trailers/newline/the_new_world/) trailer site?

I really would like to get a confirmation, or even a denial, of the issue I've posted about twice already, but everyone seems to ignore it...[/QUOTE]
[[IMG]http://img263.imageshack.us/img263/315/newworld3kx.th.jpg[/IMG]](http://img263.imageshack.us/my.php?image=newworld3kx.jpg)

---

### Post by Cl1mh4224rd on 2005-12-06
[QUOTE=bored2k][[IMG]http://img263.imageshack.us/img263/315/newworld3kx.th.jpg[/IMG]](http://img263.imageshack.us/my.php?image=newworld3kx.jpg)[/QUOTE]
Wow. Ok... I wonder what the heck's going on here.

/sigh. Thanks...

---

### Post by agds on 2005-12-07
[QUOTE=Cl1mh4224rd]What's your experience with the [The New World](http://www.apple.com/trailers/newline/the_new_world/) trailer site?

I really would like to get a confirmation, or even a denial, of the issue I've posted about twice already, but everyone seems to ignore it...[/QUOTE]
Sorry, I must have missed your posts.  I tried it just now.  The trailer itself plays fine, but Firefox initially flipped out and opened three, maybe four, new windows.  They were full screen versions of the video that begins with a voice over saying, "As a director…"  They closed almost immediately, maybe because I had already clicked on the trailer link.  It was strange.

---

### Post by ultranet on 2005-12-08
I'm curious if any of you can view yahoo videos:

[http://news.yahoo.com/video;_ylt=AsUFnc5oMc1j2yAlBL9yB62s0NUE;_ylu=X3oDMTA2MnU4czRtBHNlYwNzbg--](http://news.yahoo.com/video;_ylt=AsUFnc5oMc1j2yAlBL9yB62s0NUE;_ylu=X3oDMTA2MnU4czRtBHNlYwNzbg--)

P.S. As far as New World: the window that gets opened by default doesn't play well for  me; perhaps due to bandwidth. But if i close it and open the trailer manually (Small, Medium), it plays fine.

---

### Post by ultranet on 2005-12-08
[QUOTE=ultranet]
P.S. As far as New World: the window that gets opened by default doesn't play well for  me; perhaps due to bandwidth. But if i close it and open the trailer manually (Small, Medium), it plays fine.[/QUOTE]
After i tried the URL again, i saw the multiple windows too, and logged a bug:
[https://bugzilla.mozilla.org/show_bug.cgi?id=319645](https://bugzilla.mozilla.org/show_bug.cgi?id=319645)

---

### Post by agds on 2005-12-09
> **ultranet]I'm curious if any of you can view yahoo videos:

[url]http://news.yahoo.com/video said:**
> 

P.S. As far as New World: the window that gets opened by default doesn't play well for  me; perhaps due to bandwidth. But if i close it and open the trailer manually (Small, Medium), it plays fine.
Nope.  It just sits there as though it's loading, but nothing ever plays.  I'll check out the terminal output if I have time.

---

### Post by christooss on 2005-12-09
Have you tried play lounch extension for Firefox?

---

### Post by agds on 2005-12-09
What's that?  A link would be great, if you have one.

---

### Post by ultranet on 2005-12-09
[QUOTE=agds]What's that?  A link would be great, if you have one.[/QUOTE]
I think he refers to:
[https://addons.mozilla.org/extensions/moreinfo.php?id=593&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=593&application=firefox)

And there's another one mentioned there. I'm not near my Linux box now, so i'll try later...

---

### Post by agds on 2005-12-09
I see.  The Play Launch extension doesn't seem to be under development anymore.

---

### Post by slrafal on 2005-12-09
I was able to set up mplayer, but I'm not sure how to install the codecs. I'm a newbie so could someone lead me step by step. Thank You.

---

### Post by nix4me on 2005-12-09
[QUOTE=slrafal]I was able to set up mplayer, but I'm not sure how to install the codecs. I'm a newbie so could someone lead me step by step. Thank You.[/QUOTE]

The Wiki has step by step.

There are also no less than 50 threads about this on this forum.

nix4me

---

### Post by agds on 2005-12-10
[QUOTE=slrafal]I was able to set up mplayer, but I'm not sure how to install the codecs. I'm a newbie so could someone lead me step by step. Thank You.[/QUOTE]
I didn't have time to read through the whole thing to see if the info is still there, but the [RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats") page in the Wiki might have the instructions you need.  Alternately you could search the forums for "codecs" or "w32codecs" or something like that.

---

### Post by melissawm on 2005-12-10
Any news on the choppy mplayer subject? It's really annoying and since i don't have tv right now it would be really great if i could watch some streaming media in ubuntu, but that's not going to happen unless i can solve the choppy video thing........ :( 

any help appreciated... thanks!

(edit)

this happens when i'm watching dvds in mplayer too. anyone has a clue?

---

### Post by autonomy on 2005-12-10
"Cannot move "/usr/lib/moz...mozilla.xpt" to the trash because you do not have permissions to change it or its parent folder."

---

### Post by agds on 2005-12-10
[QUOTE=autonomy]"Cannot move "/usr/lib/moz...mozilla.xpt" to the trash because you do not have permissions to change it or its parent folder."[/QUOTE]
What is it that you're trying to delete?  You might find [this]("http://livegnudegirls.blogspot.com/2005/11/totem-mozilla-plugin-unplugged.html") useful.

---

### Post by autonomy on 2005-12-10
Does that mean I mark mplayer386 or mark all the rest? Synaptic Package Manager doesn't say what marking will do. Will marking install or not install?

---

### Post by agds on 2005-12-10
If the package isn't installed yet, you can mark it for installation.  Marking the mozilla-mplayer package for installation should cause several others, including mplayer-386 to be marked.  The only reason I removed the mplayer-386 package and replaced it with mplayer-nogui was a desire to not have it cluttering up my Applications menu.  You don't really have to do this step.  Does that answer your question?

---

### Post by autonomy on 2005-12-10
No, I'm asking how one does that. Thanks

---

### Post by agds on 2005-12-10
I see.  This would be easier to explain if I were actually on my Ubuntu box, but maybe I can remember how this would go.

I'm going to assume you've already installed mozilla-mplayer and its dependencies.  You would then mark the mplayer-386 package for removal.  If my memory serves me, you do this by left-clicking on the square next to the package name in the list.  It should be green at the moment.  A pull-down menu should appear, allowing you to choose removal.  ("Complete" removal is probably unnecessary.)  Then left-click on the square next to mplayer-nogui and select install or whatever Synaptic calls it.  Once you have mplayer-386 marked for removal and mplayer-nogui marked for installation, click the Apply button in the toolbar.  It will probably ask you to confirm your selections.  Synaptic should do its thing, and you'll be good to go.

---

### Post by ceti on 2005-12-10
Hi, Hairy Palms,

Just run your script & it worked like a charm with my Firefox 1.5.
Great, thank you.

---

### Post by ultranet on 2005-12-10
[QUOTE=melissawm]Any news on the choppy mplayer subject? It's really annoying and since i don't have tv right now it would be really great if i could watch some streaming media in ubuntu, but that's not going to happen unless i can solve the choppy video thing........ :( 

any help appreciated... thanks!

(edit)

this happens when i'm watching dvds in mplayer too. anyone has a clue?[/QUOTE]
In config, Video, make sure you have xv selected. That might help.

---

### Post by penvzila on 2005-12-10
I get about a 1/4 to 1/2 second audio delay in mplayer not matter what, so it looks like I'll be using totem.

---

### Post by Cl1mh4224rd on 2005-12-10
[QUOTE=agds]Sorry, I must have missed your posts.  I tried it just now.  The trailer itself plays fine, but Firefox initially flipped out and opened three, maybe four, new windows.  They were full screen versions of the video that begins with a voice over saying, "As a director&#8230;"  They closed almost immediately, maybe because I had already clicked on the trailer link.  It was strange.[/QUOTE]
Ah-ha! So I'm not going crazy. That's always good to know. :)

---

### Post by autonomy on 2005-12-11
I can't remove mplayer-386 without removing mozilla-mplayer, which mplayer-nogui doesn't replace, and I don't have any plugins. At least, Quicktime and Winders Media movies aren't working.

---

### Post by Hairy_Palms on 2005-12-11
autonamy if u just right click install mplayer-nogui it should ask you if you want to remove mplayer-386 but nothing else also did you follow step 3 on how to install the w32 codecs?

---

### Post by autonomy on 2005-12-11
I didn't see your script until now. What you said about mplayer-nogui was correct. I've just clicked on your third step in your post that started this thread if that's what you meant by "step 3 on how to install the w32 codecs".

---

### Post by autonomy on 2005-12-11
PS It says that I don't have permission to extract that folder to /usr/lib/win32. Please help.

---

### Post by Hairy_Palms on 2005-12-11
extract the codecs in your home folder 
then run sudo nautilus 
and then copy the extracted folder to /usr/lib/win32

---

### Post by Jingo on 2005-12-12
[QUOTE=ultranet]In config, Video, make sure you have xv selected. That might help.[/QUOTE]

Didn't help for me....

Still have choppy video and audio!

---

### Post by autonomy on 2005-12-12
I still need plugins.

---

### Post by Threepwood on 2005-12-13
I can not get mplayer to work within firefox.  The whole video downloads and then I only see a gray box.  Does anyone else have this problem or know of a fix for it?

---

### Post by bronwe on 2005-12-16
Lost Data,

I got mplayer to work and had difficulty with the repositories too.  One way to add repositories is with "Add Applications," under the Ubuntu logo at Left.   Let it load and then go into the "Tools" pull-down strip.  Click on Repositories.  Then click on "Add Repositories."  

It's that simple.  Add the multiverse repository.  You can ignore the error messages.  After adding the multiverse repository, use synaptic to download mplayer mplayer-plugin, and mplayer-fonts just like in the initial post.  Good luck

-Bronwe

---

### Post by macewan on 2005-12-22
tried installing mozplugger?

sudo apt-get install mozplugger

---

### Post by patrick295767 on 2006-01-06
mozplugger didnt replace totem
maybe apt-get remove totem 
could be done first... 
  
Is there a way to use anythg but totem ?

---

### Post by christooss on 2006-01-06
To remove totem from mozilla you have to remove plugin.conf in mozilla dir. So that plugins can be reconfigurated

---

### Post by agds on 2006-01-06
mozplugger won't know to remove the Totem plugin for Firefox.  You need to do that manually.
```
sudo rm *totem*
```
when executed in /usr/lib/mozilla-firefox/plugins should do the trick.  For my embedded media, I use mozilla-mplayer rather than mozplugger.

---

### Post by Kem Rixen on 2006-01-08
I'm sorry for the really basic question, but, how do you run scripts?

---

### Post by christooss on 2006-01-08
sh yourscript

or

chmod +x yourscript
./yourscript

---

### Post by newbie_buntu on 2006-06-21
this still applies in 6.06 (dapper drake); I realize the post is in the breezy badger category, but everything works, except the new link to the codecs is: [http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2).

Once they're un-zipped and un-tarred, to the desktop, here's the commands I used to get them into my /usr/local/lib/codec directory, since 6.06 doesn't use /usr/local/win32:

```
sudo cp /home/~user_name~/Desktop/essential-20060611/* /usr/local/lib/codecs/
```

(please remember to replace the ~user_name~ with your login, don't copy and paste! you learn code much better when you have to type it yourself!)

since  this was the first hit on google to address my needs directly, I thought I'd be nice enough to add my experience/two cents!

j

---

### Post by trubblemaker on 2006-11-14
good point about removing the plugings file, maybe the original post will get updated to help others?

---

