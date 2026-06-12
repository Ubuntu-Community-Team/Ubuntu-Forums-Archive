---
title: "[SOLVED] HOWTO: Solve flash problem on firefox"
date: 2005-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-11-13
Alright, lots of us have experienced firefox crashes on flash sites and got really frustrated. Now herez the fix for it:
This also works with Firefox 1.5!!!
```
sudo apt-get install flashplayer-mozilla arts
```
```
sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc

```and **change**
[PHP]FIREFOX_DSP="auto"[/PHP]
to
[PHP]FIREFOX_DSP="arts"[/PHP]
**OR**
[PHP]FIREFOX_DSP="none"[/PHP]
Even if u find an empty file or dont find any **FIREFOX_DSP="auto" **just type 
[PHP]FIREFOX_DSP="arts"[/PHP]
**OR**
[PHP]FIREFOX_DSP="none"[/PHP]
and save and exit.
now close all firefox windows and restart firefox and check any flash site. This shd work!

---

### Post by darrenrxm on 2005-11-13
Thankyou this was bothering me. So much that I was using opera instead of firefox. This is much better solution then the one I was using.

---

### Post by arnieboy on 2005-11-13
[QUOTE=darrenrxm]Thankyou this was bothering me. So much that I was using opera instead of firefox. This is much better solution then the one I was using.[/QUOTE]
nice to know that it worked for u too. :)

---

### Post by pxgray on 2005-11-14
This method did not work for me.  I still experience a crash *every* time firefox tries to load a Flash animation.

pxgray

---

### Post by arnieboy on 2005-11-14
[QUOTE=pxgray]This method did not work for me.  I still experience a crash *every* time firefox tries to load a Flash animation.

pxgray[/QUOTE]
did u try with both "arts" and "none"?

---

### Post by pxgray on 2005-11-14
[QUOTE=arnieboy]did u try with both "arts" and "none"?[/QUOTE]

Yes, I did both.  I just upgraded to 1.5rc2 via the instructions on the Wiki and the crashing problem still persists.  I am using Sun's j2re1.5 package to provide java, I'm not sure if that's important or not, but I seem to remember that the flash plugin depends on having java installed.

pxgray

---

### Post by shof2k on 2005-11-14
arnieboy,
Awesome....short, simple, and working 1st time.  Just the way i like my how-to's.

Thanks for this, flash has been buggin me for some time :)

---

### Post by Kebabji on 2005-11-14
I'm afraid this fix doesn't work for me either, i tried both none and arts - thanks though!

---

### Post by phanboy_iv on 2005-11-16
That fixed it! Thanks arnieboy! Now I gotta go catch up on Homestar Runner.

---

### Post by arnieboy on 2005-11-16
[QUOTE=Kebabji]I'm afraid this fix doesn't work for me either, i tried both none and arts - thanks though![/QUOTE]
u might want to install the arts package and give it another try.

---

### Post by arnieboy on 2005-11-16
[QUOTE=pxgray]Yes, I did both.  I just upgraded to 1.5rc2 via the instructions on the Wiki and the crashing problem still persists.  I am using Sun's j2re1.5 package to provide java, I'm not sure if that's important or not, but I seem to remember that the flash plugin depends on having java installed.

pxgray[/QUOTE]
u might want to install the arts package and give this another try.

---

### Post by crane on 2005-11-17
jason@ubuntu64:~$ sudo apt-get install flashplayer-mozilla arts
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
jason@ubuntu64:~$ sudo apt-get install flashplayer-mozilla arts
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
jason@ubuntu64:~$

---

### Post by arnieboy on 2005-11-17
[QUOTE=crane]jason@ubuntu64:~$ sudo apt-get install flashplayer-mozilla arts
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
jason@ubuntu64:~$ sudo apt-get install flashplayer-mozilla arts
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
jason@ubuntu64:~$[/QUOTE]
my immediate guess is that u have an AMD64 system and flashplayer-mozilla doesnt have an AMD64 port. doesnt matter. u need the following files in */usr/lib/mozilla/plugins*:
[HTML]libflashplayer.so
libflashplayer.xpt[/HTML]
do a 
```
slocate flashplayer
```
to find out where they are

---

### Post by pxgray on 2005-11-17
Alright, I finally just now figured out why my Flash was crashing out Firefox every time, with a little help from a thread over at the Gentoo forums.  Turns out that X.org with composite rendering enabled and Flash don't get along, and since I had long since abandoned xcompmgr because of instability but hadn't adjusted my xorg.conf file it was still affecting Flash.  The fix for me was to remove the lines

```

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

and 

```

Option          "RenderAccel"           "true"
Option          "AllowGLXWithComposite" "true"

```

from my /etc/X11/xorg.conf file.  Flash works great now!  Hope this helps anyone else who is having crashing problems with Flash.

---

### Post by eXidos on 2005-11-17
Awsome worked great for me on the 'none' setting........never got this workin in 5.04 now everythings comin up millhouse!

---

### Post by punkr0x on 2005-12-18
Hey, it works!  Thank you arnieboy, after spending all night messing around with aoss and getting nowhere, arts did it for me!  Simple!

---

### Post by eriqk on 2005-12-18
Works delisciously. Now I get to watch the antics of Space Captainface.
Thanks!
I'm still mainly testing stuff, I hadn't noticed Firefox would freeze, but it did when I clicked the "sb emails" link. No idea why. but it's solved, which is very nice.

Groet, Erik

---

### Post by FiggyG on 2005-12-19
Went with Arts, amazing, the first to give me useful flash sound :D

---

### Post by Brando569 on 2005-12-19
i dont have that file :confused:

---

### Post by arnieboy on 2005-12-19
[QUOTE=Brando569]i dont have that file :confused:[/QUOTE]
even if the file is empty (or doesnt exist), just copy and paste according to the instructions. it will create the file and save the config.

---

### Post by varunus on 2005-12-19
Hey, for ppl using composite, you can still use composite with flash.  Check our poofyhairguy's composite manager howto (first post).

He added a section that I found on the gentoo forums on how to get it to work.

---

### Post by Jengu on 2005-12-19
```

xxxxxx@ubuntu:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla

```

I'm running a 32-bit system. Not sure what's wrong. My /etc/apt/sources.list:

```

#deb file:///cdrom/ breezy main restricted

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
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
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

## penguin liberation front
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

# OpenOffice.org 2 final packages (packages)
deb http://people.ubuntu.com/~doko/OOo2/ ./

# Latest kubuntu packages
deb http://kubuntu.org/packages/kde35 breezy main

```

---

### Post by NeoChaosX on 2005-12-19
Add multiverse to the end of these lines:

```
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
```

Then apt-get update, then try again.

---

### Post by cutOff on 2005-12-20
[QUOTE=NeoChaosX]Add multiverse to the end of these lines:

```
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
```

Then apt-get update, then try again.[/QUOTE]
Mmm I think that's universe, not multiverse.

Cheers

---

### Post by Al_maverick on 2005-12-20
[QUOTE=arnieboy]my immediate guess is that u have an AMD64 system and flashplayer-mozilla doesnt have an AMD64 port. doesnt matter. u need the following files in */usr/lib/mozilla/plugins*:
[HTML]libflashplayer.so
libflashplayer.xpt[/HTML]
do a 
```
slocate flashplayer
```
to find out where they are[/QUOTE]

I couldn't find those files on my system. where can I get them from?
I'm using swfdec, but it's old and won't run most flash sites.

Oh, I'm running Kubuntu 64.

---

### Post by NeoChaosX on 2005-12-21
[QUOTE=cutOff]Mmm I think that's universe, not multiverse.

Cheers[/QUOTE]
Please note I said "add multiverse **to the end of those lines**", "those lines" being the two I quoted. :p

---

### Post by Grimlock on 2005-12-22
I am still getting no sound in flash?? I have tried the changing to arts and none trick but it still doesn't want to give me sound??

---

### Post by Brando569 on 2005-12-23
[QUOTE=Grimlock]I am still getting no sound in flash?? I have tried the changing to arts and none trick but it still doesn't want to give me sound??[/QUOTE]

same here, my flash runs better in firefox 1.5 but i dont have any sound

---

### Post by faizan on 2006-01-06
hats off arnieboy! my case was weird. i could watch google videos and see flash ads but then my flash would not work with flickr and other stuff.. i was using another installation deb since this one was crashing.. now its perfect.. peace

edit: i should add.. when i was using arts, i had a horribe time lag between sound and video.. just changed the setting to none and its working perfectly..

---

### Post by punkr0x on 2006-01-09
Weird.. I'm using arts and it works for me.  But recently, I have to turn off system sounds (disable "sound server startup") to hear the flash sounds.  I didn't always have to do this.  Anyone have any ideas?

---

### Post by Pausanias on 2006-01-28
Thanks very much. Setting it to "arts" fixed my problem.

---

### Post by lucidite on 2006-02-20
Hi,

Tried both solutions, none of them work -- still crashes if I open a website with Flash.
Verified, I have "arts" package.
As well, I saw in this thread something about my xorg.conf file, opened it up, didn't seem to have that section.

Anything to help me out?

---

### Post by Iandefor on 2006-02-20
works beautifully. Thanks again, arnieboy!

---

### Post by cor2y on 2006-03-02
Thanks for the guide arnie finally got it to work.
Just had to replace none with arts.

---

### Post by davtaine on 2006-03-03
working...so, thank you sooo much.

---

### Post by Al_maverick on 2006-03-06
[QUOTE=arnieboy]my immediate guess is that u have an AMD64 system and flashplayer-mozilla doesnt have an AMD64 port. doesnt matter. u need the following files in */usr/lib/mozilla/plugins*:
[HTML]libflashplayer.so
libflashplayer.xpt[/HTML]
do a 
```
slocate flashplayer
```
to find out where they are[/QUOTE]


Where can I get these files? I have an AMD64, but I couldnt find these files anywhere in my system using slocate

Tnx!

---

### Post by desiboston on 2006-03-07
[QUOTE=pxgray]Alright, I finally just now figured out why my Flash was crashing out Firefox every time, with a little help from a thread over at the Gentoo forums.  Turns out that X.org with composite rendering enabled and Flash don't get along, and since I had long since abandoned xcompmgr because of instability but hadn't adjusted my xorg.conf file it was still affecting Flash.  The fix for me was to remove the lines

```

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

and:confused: 


```

Option          "RenderAccel"           "true"
Option          "AllowGLXWithComposite" "true"

```

from my /etc/X11/xorg.conf file.  Flash works great now!  Hope this helps anyone else who is having crashing problems with Flash.[/QUOTE]



I AM STILL HAVING THE SAME problem. My xorg does not have that section. Does this work for centrinos? Plz help

---

### Post by cor2y on 2006-04-07
Ok can anyone help me.
A few weeks ago I followed this How To and everything was working, now I try it today and its back to flash crashing firefox.
 tried switching from "arts" to "none" to see if that would help, no go I already have the latest arts plugin installed from the first run through with this.

I launched firefox from the terminal and this is the error that springs up:
"/opt/firefox/run-mozilla.sh: line 131: 13288 Segmentation fault      "$prog" ${1+"$@"}" 
Even did a safe mode launch from the terminal same error.
The Only thing I've installed between then and now is the updates that came from Ubuntu via Synaptic no new programs etc.

Don't know what that error means either.

---

### Post by louis_nichols on 2006-04-08
I followed the howto once and it was working. Then, at one point, it stopped (perhaps after upgrading to ff 1.5, but I'm not sure).

What I do now is start firefox with *aoss firefox* (I updated all my shortcuts for this) and I have sound for flash. Perhaps it will work for some of you guys too.

PS: for transparency issues, try using the "knome" way. just search for poofyhairguy's howto. It works great for me, although I must admit I've had 2 or 3 crashes in 2 months (one of them really scrued up my account settings) but I think it's worth it.

---

### Post by BoboChimp on 2006-04-10
I posted the exact same problem here:
[http://www.ubuntuforums.org/showthread.php?t=156771](http://www.ubuntuforums.org/showthread.php?t=156771)

this thread solved it.  actually, the new problem turned out to be that flash animatinos weren't working at all and this thread solved that too.

thanks a lot.

---

### Post by eeried on 2006-05-03
Hello,

Many thanks to arnieboy for this howto. No crashes for some time. I set the DSP thing to "none". (setting it to arts didn't help). I use the compiled version of GPLFlash (see Ubuntu Wiki): which doesn't seem to work as a flash plugin. At least having no crash is a blessing, and I'm not a fan of flash -- pity some webmasters use it for no good reason.

Is arts needed if the "none" setting works?

---

### Post by arnieboy on 2006-05-03
[QUOTE=eeried]Is arts needed if the "none" setting works?[/QUOTE]
no.

---

### Post by Streetcrawler on 2006-06-01
Hello. I still do not get sound in Flash. I have tried every solution in this thread and every other thread I could find and I still get nothing. The videos play fine on Youtube and Google Video, but no sound. Sound works flawlessly while playing videos and audio files that aren't Flash based. I've reinstalled Flash numerous times, both through Synaptic and manaully installing. I even tried reinstalling Firefox. NOTHING works. This is maddening. What is even more ridiculous is that I can run my Windows install of Firefox with WINE and Flash works great! ](*,) AHHHHH! Ubuntu has been great otherwise.

---

### Post by barney_1 on 2006-06-02
Can anyone get this link to load in Firefox:
[http://interact10ways.com/usa/information_interactive.htm]("http://interact10ways.com/usa/information_interactive.htm")

I tried this fix but I just get the "click here to load plugin" window and no luck with that of course.  Works fine in windows but I'm trying not to do that anymore.

---

### Post by DarkStarDeity on 2006-06-02
[QUOTE=Streetcrawler]Hello. I still do not get sound in Flash. I have tried every solution in this thread and every other thread I could find and I still get nothing. The videos play fine on Youtube and Google Video, but no sound. Sound works flawlessly while playing videos and audio files that aren't Flash based. I've reinstalled Flash numerous times, both through Synaptic and manaully installing. I even tried reinstalling Firefox. NOTHING works. This is maddening. What is even more ridiculous is that I can run my Windows install of Firefox with WINE and Flash works great! ](*,) AHHHHH! Ubuntu has been great otherwise.[/QUOTE]

I had this problem first, and tried the solution in [this thread]("http://ubuntuforums.org/showthread.php?t=187207") of installing alsa-oss, which worked, but then I had the problem described in this thread of some (not all) flash sites (games usually) freezing Firefox. The fixes described here (modified slightly, see my post below) worked to fix both problems for me. But if you're still getting no sound, the alsa-oss fix might work for you.

---

### Post by DarkStarDeity on 2006-06-02
Just some modifications for Dapper - 
flashplayer-mozilla is no longer recognised, it's now flashplugin-nonfree (in fact, wasn't it that in Breezy as well?)
and the Firefox rc file is now in /etc/firefox/firefoxrc
with those modifications to the initial instructions, flash now seems to be working fine for me.

---

### Post by brin on 2006-06-04
On Dapper, I have found that by simply installing the esound-client package solved the sound problem. Run "sudo apt-get install esound-client" and reboot the system.

---

### Post by Streetcrawler on 2006-06-04
Just upgraded to Dapper, thinking it would magically solve my problem. Nothing has changed, I still do not get sound with Flash. I tried all the settings in this thread again and nothing worked. I installed "esound-clients" with an "s" because there was nothing called "esound-client." That didn't help. killall esd does nothing. aoss firefox does nothing. Changing the settings in mozilla-firefoxrc does nothing. Nothing has worked. I think I am the only person on the planet with this problem now. ](*,)

---

### Post by eeried on 2006-06-05
> Can anyone get this link to load in Firefox:
[http://interact10ways.com/usa/inform...nteractive.htm](http://interact10ways.com/usa/inform...nteractive.htm)

Yes I can (on Breezy), but I've been using some javascript code provided by a clever Ubuntu user on this forum (sorry can't find the link or the user's name again):

Create a new bookmark, preferrably visible on our Bookmark toolbar, call it whatever you like (I called mine "flah hell", and paste this long line of code into the "Location" field:
```
javascript:s='';b=0;while(document.embeds[b]){s+='<a href=%22'+document.embeds[b].src+'%22>'+document.embeds[b].src+'</a><br>';b++;};if(s){document.write(s);document.close();}else{alert('Sorry, no embeds found.');}
```

When you get to a page in which some flash is embedded or on a web site entirely made in flash and isn't displayed in FF, click on your flash hell bookmark: this will display a blank page with a link: click on the link and the page displays (or in your case, a download box appears -- your file being a DRC file). I din't download the file.

Hope this helps!

---

### Post by eeried on 2006-06-05
Flash plugin:

What I do is download flashplayer from the macromedia web site and install the TARGZ binary file.

Then uncompress it, and paste the two vital *so and *xpt files (to be found in  a dir called "mozilla") into the firefox plugin dir. I don't go through the flash installation procedure.

I find this better than rely on usually oldish version of Ubuntu-packaged flash.

I do have sound in Flash (tried with arte radio.com which is an all flash web site). Works with the javasscript in my previous message

Cheers,

---

### Post by brin on 2006-06-05
Streetcrawler,

Reboot the system to start afresh and lets go through a checklist.
- check that you have sound in your system with other apps such xmms music player.
- check if you have software sound mixing (esd) enabled in System/Preferences/Sound
- If esd is enabled in the previous check, then check that you have esound-clients installed. Ensure that you have the file /usr/bin/esddsp which comes from that package.
- Check that in /etc/mozilla/mozillarc MOZILLA_DSP is set to "auto" 
because when set to auto the browser will use esddsp if desktop manager is gnome and arts if on kde.

---

### Post by DarkStarDeity on 2006-06-08
[QUOTE=DarkStarDeity]Just some modifications for Dapper - 
flashplayer-mozilla is no longer recognised, it's now flashplugin-nonfree (in fact, wasn't it that in Breezy as well?)
and the Firefox rc file is now in /etc/firefox/firefoxrc
with those modifications to the initial instructions, flash now seems to be working fine for me.[/QUOTE]


Well, it looks like I spoke too soon - like a couple of people on this thread, this *was* working for me, then suddenly stopped. In the intervening period I had installed a couple of things to try out, including juk and amarok, as well as applying system updates. It seems that at least one of these things has borked this up. The other people on the thread also had installed updates - surely they are not the culprit. I can get sound back if I use aoss, but then Firefox crashes again. 

I'm reticent to try the esd-client suggestion because of this warning in the firefoxrc file:
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).

Does anybody have any ideas?

Edit: OK, following the link and looking at the bug report, it looks as though this might well be an intractable problem with the flash plugin.

Edit 2: So taking a hint from the malone bug report, I disabled system sounds (requires a reboot to kill any currently-running esd process - I tried killing it in the system monitor but sound was still missing) and now I have sound without firefox hanging. So it seems we can *either* have system sounds *or* a fully-working flash plugin in a stable firefox. The system sounds are pretty and all, but I prefer content over pretties, so I'll see how long this solves my problems for.

Just to re-iterate - for those still having the problem ***try turning off the systems sounds (and reboot)***

---

### Post by keithjr on 2006-06-15
A lot of the current unsolved flash problems seem to be stemming from the fact that flash has no means of configuring which device it uses as its primary audio output.  If one has two audio devices, like a crappy on-board sound and a nice PCI sound card, it will default to the onboard one.  There seems to be no way to change this.

---

### Post by jetpeach on 2006-06-15
is this really the case?  i just updated and flash stopped working, but it used to not work and i fixed it before.  but now i don't know how (and it seems nobody else does).

---

### Post by cleako on 2006-06-15
they have a different plugin called flashplugin-nonfree

---

### Post by cleako on 2006-06-15
dubble post

---

### Post by danielph on 2006-08-05
This worked for me:



sudo aptitude install alsa-oss
sudo gedit /etc/firefox/firefoxrc
 	FIREFOX_DSP=”aoss”

---

### Post by cantormath on 2006-08-05
What kinda of crash are you refering too? I have not had a problem.
The only problem that I had was yesterday, where I lost sound to flash movies.

What seemed to fix it doing the several updates from yesterday, uninstalling automatix completely, reinstalling automatix, and reinstalling the flash plugins.

now its back to normal as far as I can tell.

---

### Post by kvalis on 2006-08-05
I have downloaded flashplayer plug-in from Adobe, installed it to /etc/lib/firefox but I am still being asked to get the plug-in when I restart Firefox and go to [www.cartoonnetwork.com](www.cartoonnetwork.com).

Tried your suggestion, this is the result

> tore@ubuntu:~$ sudo apt-get install flashplayer-mozilla arts
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
tore@ubuntu:~$

Any suggestions??

kvalis

---

### Post by cantormath on 2006-08-06
> **kvalis said:**
> I have downloaded flashplayer plug-in from Adobe, installed it to /etc/lib/firefox but I am still being asked to get the plug-in when I restart Firefox and go to [www.cartoonnetwork.com](www.cartoonnetwork.com).

Tried your suggestion, this is the result



Any suggestions??

kvalis

Did you try automatix?

---

### Post by amwil1024 on 2006-09-10
Can anyone translate this to step x step for an idiot! :( 



> **arnieboy said:**
> Alright, lots of us have experienced firefox crashes on flash sites and got really frustrated. Now herez the fix for it:
This also works with Firefox 1.5!!!
```
sudo apt-get install flashplayer-mozilla arts
```
```
sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc

```and **change**
[PHP]FIREFOX_DSP="auto"[/PHP]
to
[PHP]FIREFOX_DSP="arts"[/PHP]
**OR**
[PHP]FIREFOX_DSP="none"[/PHP]
Even if u find an empty file or dont find any **FIREFOX_DSP="auto" **just type 
[PHP]FIREFOX_DSP="arts"[/PHP]
**OR**
[PHP]FIREFOX_DSP="none"[/PHP]
and save and exit.
now close all firefox windows and restart firefox and check any flash site. This shd work!

---

### Post by jetpeach on 2006-09-10
For all those who find this thread, I really don't recommend setting things up this way, flash will fight for your soundcard rights with that method such that nothing else can use it, even after firefox closes i found.
What I recommend, and it's started quite clearly, is to follow the ubuntuguide.org page  that described exactly howto setup flash.
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
the benefits of their setup is it allows multiple sounds.  i used to have a crash on firefox (total freeze, had to terminate) after accessing flash sites when i tried "aoss" in the firefoxrc file, but since i ran update-flashplugin as described i no longer do!

 amwil1024, hopefully the ubuntuguide page is clear enough, it tries to be very exact and clear.  if it isn't clear enough still, let us know and we can clarify even more.

also, for those curious flash 9 will be here soon for linux! check out the [adobe developers blog on progress]("http://blogs.adobe.com/penguin.swf/") on it.  hopefully a beta within a couple months...  this should solve the problems we have with performance, lag (i still notice about 1 second lag on sound/video) and of course all sites requiring newer than flash7.

---

### Post by thinker on 2006-09-10
jetpeach...

I tried the original ideas by arnie, to no avail, then found this at the end of the thread.  I did it (used synaptic via the ubuntuguide) and everything seemed to go just fine; downloaded from the macromedia site, and everything installed well enough... upon closing out of firefox and reopening, same problem.  The browser still shuts off immediately into loading a page with a flash script... 

As for arnie's original post; I have similar problems with not being able to get the arts package... I believe that would make me a 64-er?

Anyways, still no avail in loading pages... any new ideas?

---

### Post by jetpeach on 2006-09-12
oh drat, flash just crashed my firefox again.  it worked better for me it seemed this time (didn't crash every time, and not when i first tested it), but i still can't have flash crashing my browser frequently... so i'll change my firefoxrc to say "none" instead of aoss...  for me this allows sound to work, but it fights with kde and any other program for control of the soundcard, so i have to make sure kde has released the soundcard and reopen firefox usually.  blah. flash9 can't come soon enough for us linux folk...hopefully within a month or so we'll see a beta

also, everyone should note, i believe arnieboys guide at the beginning of this is also now wrong for the firefoxrc file that needs to be editing. he states to edit /etc/mozilla-firefox/mozilla-firefoxrc, but i'm not sure this is the right file, because i have /etc/firefox/firefoxrc and i think mozilla-firefox was the older package name, and now it's just firefox.  that could be some peoples problem.
but in either case, i don't recommend using arts.  none works better for me.  keep in mind, "none" doesn't mean your saying not to use sound, it just means your none going to use a sounds wrapper, so flash will play it's sound directly to the hardware (so it has the problems i mentioned above, but i still found this the most stable/best method).

---

### Post by F-beginner on 2007-12-31
thx arnieboy it worked fine also for me
my Flash is running
although my firefox in etc has a diff path, but I changed firefoxrc
and it worked with 'none':lolflag:

---

### Post by ronb94 on 2007-12-31
i am getting this:
```
Package flashplayer-mozilla is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplayer-mozilla has no installation candidate
ron@ron:~$ 
```
after running this:
```
sudo apt-get install flashplayer-mozilla arts
```

---

### Post by smartboyathome on 2007-12-31
This tutorial is very old. I don't think it applies much anymore.

---

