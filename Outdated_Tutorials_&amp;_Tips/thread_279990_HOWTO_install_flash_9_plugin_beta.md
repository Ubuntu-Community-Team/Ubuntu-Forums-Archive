---
title: "HOWTO install flash 9 plugin beta"
date: 2006-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by bruenig on 2006-10-18
EDIT: January 16, 2007
This thread is officially obsolete as flash 9 is finished and out of beta. But, since you came here looking for a way to install flash 9, I will just put the instructions for the final version.

Note, I have done this on edgy. If anyone wants to confirm that it works on any other versions, feel free.

Open the terminal, Applications>Accessories>Terminal, I will assume this stuff will all being happening in the home directory as that is where the terminal opens by default.

**First** remove the previously installed flash plugins (obviously if you don't have any installed, disregard).
There are a few ways to do it depending on the way you installed it. If you are not sure, you can do all of them without damaging anything but if you do all of them, make sure you do them in order. If you know how you installed the old one initially, choose the appropriate one.

1. Removing it via apt
```
sudo apt-get remove flashplugin-nonfree
```

2. Removing it manually if it is in the /usr/lib/firefox/plugins directory
```
sudo rm /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/flashplayer.xpt
```
If it tells you that a file doesn't exist, don't worry about it. Flash 7 had flashplayer.xpt but flash 9 beta 1 didn't, so depending on which version you had installed, you may get an error that flashplayer.xpt doesn't exist. Or if you don't have any of them installed, they both won't exist. Either way, just carry on.

3. Removing it manually if it is in the ~/.mozilla/plugins directory
```
rm ~/.mozilla/plugins/libflashplayer.so ~/.mozilla/plugins/flashplayer.xpt
```
Same thing applies as number 2 as far as errors are concerned, just disregard.

**Second** get the tar.gz file
```
wget  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

**Third** extract the tar.gz
```
tar xf install_flash_player_9_linux.tar.gz
```

**Fourth** change into the new directory
```
cd install_flash_player_9_linux/
```

**Finally** run the installer script and follow the prompts
```
sudo ./flashplayer-installer
```
When it asks for your mozilla, seamonkey, or firefox directory, tell it /usr/lib/firefox

That should be it. If you want to remove all the excess garbage that you downloaded, just change back into the home directory and remove it.
```
cd
rm -rf install_flash_player_9_linux*
```

---

### Post by bassMonkey on 2006-10-19
Cool! Flash 9 BETA is out for linux! Wonder why noone seems to notice...

---

### Post by coreyt on 2006-10-19
Many of you will be happy to know a beta of the Flash Player 9 came out yesterday!

1.  Download the correct binary for linux at Adobe labs

```
http://labs.adobe.com/downloads/flashplayer9.html
```

2. Unpack the files into a directory somewhere.

3. Copy libflashplayer.so into the following directory

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

4. Give the file correct permissions.

```
sudo chmod 644 /usr/lib/mozilla/plugins/libflashplayer.so
```

5. Link the file to Firefox's plugins directory.

```
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so libflashplayer.so
```

6.  Restart Firefox and enjoy! :mrgreen:

---

### Post by rudiz on 2006-10-19
If I romove the old FP will FP work in Opera?

Because FP9 does not show up in opera:plugins.

---

### Post by lox_federico on 2006-10-19
It works also on amd64 through nspluginwrapper!!! :mrgreen:

But it's still a beta, so expect some probs (I noticed some XML loading errors on few Flash 8 sites).

I hope there would be a REAL 64bit release when they'll reach the final version. :rolleyes:

---

### Post by Intangir on 2006-10-19
how do we make sure its using alsa?
i set FIREFOX_DSP stuff to be 'aoss' before to help with bad sync

---

### Post by Kalinda on 2006-10-19
I believe it continues to use FIREFOX_DSP, since mine is still set to Alsa.

It works pretty nicely, in that I can view Flash 9 sites now. And the sound isn't craptastic anymore, though I still can't play it at the same time as music, but that's not a big deal.

However, has anyone else noticed that the video is *really* sluggish? It's really noticeable when watching videos off YouTube or movie trailers... or maybe it's just me.. I know it's a beta, but still.. I'll have to check the bug reports.

---

### Post by coreyt on 2006-10-19
I'm not having any issues.  Try taking out the dsp setting in firefox and see if that helps.  I had flash installed, but had not done the dsp trick to get audio working.  Now sound works even if I'm playing sounds in SongBird..

---

### Post by skymt on 2006-10-19
I had some major problems with it. In Firefox, Youtube video has an almost unwatchable framerate. In Opera, Youtube videos freeze up around a minute in. So, I removed it in favor of version 7. I'll check up on it again when the next beta comes out.

---

### Post by homy06 on 2006-10-19
nevermind. 

it doesn't work with my a site my mother uses so I stll can't get her off windows. almost there. I shake my fist at flash.

---

### Post by Alpha_toxic on 2006-10-19
I just tried it here on my Opera and it looks fine for now. I assume there will be bugs thought, as it is beta. Anyway, I'm happy they kept their promisse, I'll give Adobe some of their lost points back ;)
[quote=skymt]I had some major problems with it. In Firefox, Youtube video has an almost unwatchable framerate. In Opera, Youtube videos freeze up around a minute in. So, I removed it in favor of version 7. I'll check up on it again when the next beta comes out.[/quote]
Youtube works for me in Opera in Edgy

---

### Post by Low J. on 2006-10-19
Works great for me...framerate and sync is great.  In order to get it to work though I had to create a symlink to libflashplayer.so in my directory /home/yourdirectory/.mozilla/plugins/

---

### Post by yemu on 2006-10-19
hi,
it's going to b very short howto:

1. download Flash9BETA from [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

2. close Firefox

3. unpack the file in the temporary directory

4. rename ~/.mozilla/plugins/libflashplayer.so to eg. libflashplayer.bak

5. copy the libflashplayer.so from downloaded archive to ~/.mozilla/plugins

6. Start Firefox and enjoy your brand new Flash9 :-)

This works in Edgy but should also work in Dapper

Best regards
Yemu

---

### Post by hikaricore on 2006-10-19
bump so people notice :P

---

### Post by evs on 2006-10-19
Sweet, I can finally watch YouTube videos!

---

### Post by hikaricore on 2006-10-19
> **evs said:**
> Sweet, I can finally watch YouTube videos!

that comment almost frightens me.

/me wonders how many more stupid flash ads will work now. (since the one yesterday with the lady talking about voip phone service nearly scared the living @%!$ out of me, first time flash sound ever worked when I didn't want it to.)

---

### Post by doobit on 2006-10-19
> **bassMonkey said:**
> Cool! Flash 9 BETA is out for linux! Wonder why noone seems to notice...

Maybe because they are more interested in the the RC release of Edgy?

---

### Post by wolf202 on 2006-10-19
works great in firefox how do I install for swiftfox?

Great guide though, submitted to [wikitut.org]("http://www.wikitut.org")

[http://www.wikitut.org/index.php?title=How_to_Install_the_Flash_9_Plugin_on_Linux](http://www.wikitut.org/index.php?title=How_to_Install_the_Flash_9_Plugin_on_Linux)

-wolf

---

### Post by BarFly on 2006-10-19
Thanks for the step by step detailed instructions which saved me lots of aggrevation.  I am very happy.  It is about time, Adobe.

---

### Post by Crashmaxx on 2006-10-19
Here is an alternate method I used, that worked great, even for swiftfox.

Assuming you have flash 7 installed and working, this is what you do:

1. Download the tar and extract it. You will now have a file libflashplayer.so and a readme file.

2. Open the folder you extracted libflashplayer.so to in nautalis.

3. Open a terminal and type:
```
locate libflashplayer.so
```
This will find all the paths for the plugin, even swiftfox.

4. Type "sudo cp ", then drag the file libflashplayer.so from the open nautalis folder to the terminal and drop. Now copy and paste the first path locate found. Make sure you have spaces between the paths, and hit enter and put in you password.

5. Repeat step 4 for all the paths locate found, except the path for your extracted libflashplayer.so, if that shows up.

6. Then delete the tar and all extracted files and restart anything using flash.

Now flash 9 should work for everything, enjoy!

Cliff Notes: Just copy the file you downloaded and extracted to the all the current flash 7 plugin locations.

---

### Post by TrendyDark on 2006-10-19
Thanks for the how to! I noticed this today by accident, and I'm one who's been worrying adobe would never give us something to gawk at in disbelief, after having used Flash 7 for how many years?

---

### Post by bsmith1051 on 2006-10-19
You can check your installed version of Flash here,
[http://www.adobe.com/products/flash/about/]("http://www.adobe.com/products/flash/about/")

---

### Post by Treviño on 2006-10-19
Isn't better to use **packages**?

[Here]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/66873/comments/5") you are...

- [flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb") (Firefox Plugin)
- [flashplayer-nonfree_9.0.21.55-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplayer-nonfree_9.0.21.55-3v1ubuntu0_i386.deb") (Standalone player)

They works both in dapper and in edgy!

Use my repo for being updated ;)

PS: The package tries to remove any previous installation (also those in the home dirs...)

---

### Post by jdunn on 2006-10-19
Works Great.  Audio/Video is finally in sync.  I downloaded it from the Macromedia web site.  What's odd is, both Flashplayer 7.0 and 9.0 show up in firefox about':'plugins.  When playing flash on You Tube, I checked that 9.0 is definitely running.  Also, I performed an entire search on my hard drive and didn't find a 7.0 of libflashplayer.so.

---

### Post by bruenig on 2006-10-19
> **Treviño said:**
> Isn't better to use **packages**?

[Here]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/66873/comments/5") you are...

- [flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb") (Firefox Plugin)
- [flashplayer-nonfree_9.0.21.55-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplayer-nonfree_9.0.21.55-3v1ubuntu0_i386.deb") (Standalone player)

They works both in dapper and in edgy!

Use my repo for being updated ;)

PS: The package tries to remove any previous installation (also those in the home dirs...)

Probably is better to go with the packages. I put this together before they had been created.

---

### Post by JunySan on 2006-10-19
Nice!!!!!!!!8)

---

### Post by Treviño on 2006-10-19
> **bruenig said:**
> Probably is better to go with the packages. I put this together before they had been created.
No problem... I just wanted not to post my repository in a new thread also if I uploaded them after few hours from the player release ;)

---

### Post by Athanasius on 2006-10-19
I did a (I think) simpler version.. especially for the non-terminal gui people.

First, go to 
[http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

Download the plugin and extract to desktop.  Then open the file and right-click copy gflashplayer.so

Next open your home directory, hit ctrl+h and put it in your plugins folder under Mozilla.

It works fine for me:)

---

### Post by Subnet on 2006-10-19
Has anyone had any luck on this for the 32 bit version of firefox running in Dapper 64?

---

### Post by yemu on 2006-10-20
bump

---

### Post by flu on 2006-10-20
Should I remove flashplugin-nonfree package before I install Flash 9?

---

### Post by Treviño on 2006-10-20
You simply could upgrade it...
That's the best choice: [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

---

### Post by Robor on 2006-10-20
> **Treviño said:**
> You simply could upgrade it...
That's the best choice: [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)
Worked for me!  :p

---

### Post by RafRaf on 2006-10-20
Im using the v9 and everything works great except sound is gone after resume from suspend. Anybody had similar problem?

---

### Post by goldup on 2006-10-20
Thnak you.

---

### Post by TrendyDark on 2006-10-20
Has anyone been having problems with Firefox crashing or sites that use flash ads lagging out? Since installing the new plugin I seem to be having performance issues with Firefox.

Anyone else have this problem?

---

### Post by WoodyMahan on 2006-10-20
Here is a link to an article that gives instructions on getting the new BETA version of FlashPlayer running with FF.

[http://www.linuxplanet.com/linuxplanet/reviews/6322/1/](http://www.linuxplanet.com/linuxplanet/reviews/6322/1/)

No more frustration over not being able to play newer Flash Videos.

ENJOY!!!

---

### Post by Sef on 2006-10-20
To those who don't know what a beta version is: Beta means that it is in testing mode, so you may have crashes and other problems with it that you should not have with a stable version.

---

### Post by aysiu on 2006-10-20
I've moved this to HowTos... since that's what it is.

---

### Post by Dual Cortex on 2006-10-20
edit: Got it working with opera. Flash 7 still *persevered* at first. Had to delete the old plugin. Directory for older plugin found at tools>preferences>advanced>PLug-in OPtions

---

### Post by Rob2687 on 2006-10-20
You can even just put it in ~/.mozilla/plugins

---

### Post by phormion on 2006-10-21
I'm not sure this is a Flash 9 issue, but on my computer I get a really weird output from about:plugins (with plugin.expose_full_path set to true in about:config) in Firefox 1.5.0.7 (on Dapper): 

> 
Shockwave Flash

    File name: /home/fane/packages/flash-player-plugin-9.0.21.55/libflashplayer.so
    Shockwave Flash 7.0 r68


at the beginning of the list, and then right at the end:

> 
Shockwave Flash

    File name: /home/fane/packages/flash-player-plugin-9.0.21.55/libflashplayer.so
    Shockwave Flash 9.0 d55


At least on youtube and other Flash sites it seems to use Flash 9 (if I right click on it I get "About Adobe Flash Flayer 9" as an option), but it's still strange. I think it's related to pluginreg.dat in my home dir, and to my careless removal of the link to the Flash 7 plugin while Firefox was running... Anyway, it should be fixed by re-generating or manually editing pluginreg.dat in the Firefox profile, I think.

LATER EDIT: nevermind, I fixed it by removing pluginreg.dat from ~/.mozilla/firefox - firefox regenerates it when you run it again.

---

### Post by wilberfan on 2006-10-21
> **Subnet said:**
> Has anyone had any luck on this for the 32 bit version of firefox running in Dapper 64?

Yeah.  What he said.   I'd like to get this going on my AMD64 box...  :-k

---

### Post by Jose Catre-Vandis on 2006-10-21
works a treat, and the best howto on the forum to boot :-)

---

### Post by phormion on 2006-10-24
Anybody here have trouble with Flash videos with the new v9 player? Especially Youtube, I get videos stopping at random, then if I move the cursor it will maybe play a bit more and stop again. Sometimes it hangs right away, sometimes it hangs after a few seconds, but it happens very often. 

There's quite a few people reporting this on the Adobe forums, check these two threads: 

[http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=616&threadid=1207078&enterthread=y](http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=616&threadid=1207078&enterthread=y)

[http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=616&threadid=1206328&enterthread=y](http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=616&threadid=1206328&enterthread=y)

I'm using Dapper, whatever alsa version came with it (1.0.12, I think), 2.6.15-27-k7 kernel, Firefox 1.5.0.7 & 2.0RC3.

---

### Post by mccord on 2006-10-25
> **phormion said:**
> Anybody here have trouble with Flash videos with the new v9 player? Especially Youtube, I get videos stopping at random, then if I move the cursor it will maybe play a bit more and stop again. Sometimes it hangs right away, sometimes it hangs after a few seconds, but it happens very often.
same here...
the plugin is very unstable under opera 9.02
sometimes it crashes/freezes opera and i have to kill the process :|
sites like [http://bitsandpieces1.blogspot.com/](http://bitsandpieces1.blogspot.com/) are a no-go (many youtube videos linked on the site)
i reverted back to flash 7 under opera, and using firefox with flash 9 for sites i need the plugin for

---

### Post by ske1fr on 2006-10-25
Thanks for this Coreyt.  Now Laura Pausini's mouth is moving in synch with her singing!

For any new users who are still getting lipsynch problems in Firefox:  you may already have a symbolic link to the old Flash 7 plugin in your Firefox plugins folder.  I found that removing this symbolic link and remaking it fixed the problem and showed Flash 9 in a Firefox "about:plugins" check.  It may be blatantly obvious to most seasoned Linux users, but it might not be to new users!  I count myself in this category.

In other words, at point 5 in the HOWTO, do this:

```
cd /usr/lib/firefox/plugins/
**sudo rm libflashplayer.so**
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so libflashplayer.so

```
This should mean that the new plugin is enabled.  By the way, I also renamed the old plugin before copying in the new one, so if it didn't work I can just replace the new with the old, and redo the symlink.

---

### Post by johnleonard on 2006-10-27
Here is another link with a method for installing Flash 9.0 beta
[http://everythingelse.wordpress.com/2006/10/23/howto-install-flash-9-beta-on-ubuntu-the-easy-way/](http://everythingelse.wordpress.com/2006/10/23/howto-install-flash-9-beta-on-ubuntu-the-easy-way/)

---

### Post by jayneella on 2006-11-06
Hi i have just followed these steps and im getting an error message saying i already have a management tool running but i dont? i have re booted but it still gives the error message!

---

### Post by jayneella on 2006-11-06
> **jayneella said:**
> Hi i have just followed these steps and im getting an error message saying i already have a management tool running but i dont? i have re booted but it still gives the error message!

Ok it seems to be installing now, but it is taking ages! is this normal???

---

### Post by MatteHead on 2006-11-06
Yepp, the packages works great for me, cheers!

---

### Post by firezip on 2006-11-06
Thanks for the .deb. I finally watch flash videos on spikedhumor now :)

---

### Post by TheFourElements on 2006-11-06
doesn't work on breezy. Any suggestions. When I run the code in the instructions i get this 

```
~/flash-player-plugin-9.0.21.55$ sudo mv libflashplayer.so /usr/lib/firefox/plugins/
mv: cannot move `libflashplayer.so' to `/usr/lib/firefox/plugins/libflashplayer.so': No such file or directory

```

---

### Post by molgar on 2006-11-07
> **TrendyDark said:**
> Has anyone been having problems with Firefox crashing or sites that use flash ads lagging out? Since installing the new plugin I seem to be having performance issues with Firefox.

Anyone else have this problem?

Yes, I had to go back to flash 7, I was getting a crash every 20 minutes or so. Painful.

---

### Post by bruenig on 2006-11-09
> **TheFourElements said:**
> doesn't work on breezy. Any suggestions. When I run the code in the instructions i get this 

```
~/flash-player-plugin-9.0.21.55$ sudo mv libflashplayer.so /usr/lib/firefox/plugins/
mv: cannot move `libflashplayer.so' to `/usr/lib/firefox/plugins/libflashplayer.so': No such file or directory

```

Did you try to .deb packages? Those are the easiest. You may also try instead of ```
sudo mv libflashplayer.so /usr/lib/firefox/plugins/
```
this
```
sudo mv libflashplayer.so /usr/lib/mozilla-firefox/plugins/
```
make sure you are in the appropriate directory of course, the directory where libflashplayer.so is. You appeared to be in the terminal output you pasted, but just a reminder.

---

### Post by blitzer on 2006-11-09
No flash here !

I go to places like Youtube, google video and it tells me I don't have java script enable or the flashplayer ? ](*,) 

Plugins are toast - I checked the about: plugins in the url and it shows up updated ?

Same problem in Windows XP.  [COLOR="Red"]What is really bothering me is when I use my Yahoo mail my inbox buttons such as: Delete, move and spam don't do anything ? ](*,)  [/COLOR]

Any help would be appreciated :) 

Anyone else having these problems ?  Maybe Firefox 2 ?  Maybe running beryl interfering ? This I will check !

---

### Post by SebMKd on 2006-11-10
Awesome! Finally the web is alive again.:cool: 

I used 'flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb' to update my firefox 2.0. Super easy. Just had to type the one line in the terminal as indicated in the first post.
Note: I previously had flash7 on FF2.0. And for those who want/need to know I had done before that the super easy upgrade from FF1.5 to FF2.0 with the script here: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by essexman on 2006-11-10
> **bruenig said:**
> You can now install via a deb package, thanks to trevino for this.

[flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb ]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb")(Firefox Plugin)
[flashplayer-nonfree_9.0.21.55-3v1ubuntu0_i386.deb ]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplayer-nonfree_9.0.21.55-3v1ubuntu0_i386.deb")(Standalone player)

For these, although I have not tested them, you would first download them. From there you can either double click which will launch some graphical deb installer (I think it is called gdebi) 

Thanks for this howto.

Gdebi works very well for me. Quick and simple (just like me).

When installing proprietary software, such as abobe Flashplayer, it is necessary to click on the Terminal arrow icon, open up the built-in terminal, and highlight the OK icons then press enter to accept.  These programs  require  active acceptance of the licence before they work.

---

### Post by phormion on 2006-11-10
Blitzer, what did you try to do to install the plugin? Does it show up under 'about:plugins'?

---

### Post by blitzer on 2006-11-10
This has to be an Edgy problem with Flash ?

Did the .deb's (can you install both (plugin - stand alone) or just one ? This was not stated.

I've never had this mush of a problem on installing applications even in Linux ](*,)  untill now :-?  

About : plugins in the 2.0 firefox browser shows them listed.

---

### Post by bruenig on 2006-11-12
> **blitzer said:**
> This has to be an Edgy problem with Flash ?

Did the .deb's (can you install both (plugin - stand alone) or just one ? This was not stated.

I've never had this mush of a problem on installing applications even in Linux ](*,)  untill now :-?  

About : plugins in the 2.0 firefox browser shows them listed.

You can install both, one is the plugin, I will give you a hint it is the one that says plugin. And the other is the stand alone player, meaning it stands alone from any other application, i.e. it is not integrated into a browser or some other app like the one called plugin.

---

### Post by blitzer on 2006-11-12
Hey thanks for the reply bruenig :D 

But FLASH is all FUBAR'D for my system !

I think it has to do with moving files and not having root privs. [COLOR="Red"]Just guessing.[/COLOR]

[COLOR="Blue"]Is anyone using Yahoo mail having any problems with it ?  I can't use any of my inbox buttons at all - this has never happened before been with yahoo along time ](*,)  Sent e-mail to yahoo support and no answer :-|  [/COLOR]

---

### Post by phoqueyoo on 2006-11-13
I can ONLY use OSS. I heard this was alsa only. Is there way to convert alsa to oss (i think aoss only works from oss to alsa) so I can use this with sound?

---

### Post by jonnybecker on 2006-11-15
Hi,

I've got a problem upgrading to flash 9 beta from trevino's repository.

I always get this screen (in gui and console) that you can find in the attachment. But I don't know what to do then. I scrolled all the way down, but I cannot confirm or whatever. There's no way to press the ok. The upgrade process is stuck then.

Anybody got a solution?

Cheers
Jonny

---

### Post by essexman on 2006-11-15
> **jonnybecker said:**
> Hi,

I've got a problem upgrading to flash 9 beta from trevino's repository.

I always get this screen (in gui and console) that you can find in the attachment. But I don't know what to do then. I scrolled all the way down, but I cannot confirm or whatever. There's no way to press the ok. The upgrade process is stuck then.

Anybody got a solution?

Cheers
Jonny

Click on the OK with your mouse, that should make  the OK highlight red; The press Enter.

But maybe don't do it yet.

After initial success Flash Beta 9 failed I couldn't get past 30 Seconds for videos such as youtube.  I desparatly want to get Golfspan.com working, but the vidios are Flash 8 and above only.  No warning with Flash 7, they just dont work.

I've tried all the fixes, including upgrading to ALSA 1.0.13 from source (after swearing that I wouldn't risk my system ever again after Dapper)  

Youtube works fine with 7 and aoss sound, but so many sites won't work with 7.  Beta 9 works well on sites with no sound; but if there is sound - everything freezes.](*,)

---

### Post by WhizCas on 2006-11-15
> **essexman said:**
> Click on the OK with your mouse, that should make  the OK highlight red; The press Enter.

But maybe don't do it yet.

After initial success Flash Beta 9 failed I couldn't get past 30 Seconds for videos such as youtube.  I desparatly want to get Golfspan.com working, but the vidios are Flash 8 and above only.  No warning with Flash 7, they just dont work.

I've tried all the fixes, including upgrading to ALSA 1.0.13 from source (after swearing that I wouldn't risk my system ever again after Dapper)  

Youtube works fine with 7 and aoss sound, but so many sites won't work with 7.  Beta 9 works well on sites with no sound; but if there is sound - everything freezes.](*,)

Got the same problem :(. Any fixes known?

---

### Post by blitzer on 2006-11-16
Ditto ](*,)

---

### Post by jrings on 2006-11-16
I think at first Youtube videos worked on Flash 9 but with old Firefox. Now they stopped with Firefox 2. Then again, they also don't work in Konqueror, so I might be wrong or it could be some other reason.
Anyway: :(

---

### Post by bryanb on 2006-11-16
Worked perfectly! Thanks for the info :)

---

### Post by jonnybecker on 2006-11-18
Hi,

still got the same problem:
[http://ubuntuforums.org/showthread.php?p=1762400&highlight=HOWTO+install+flash+9+plugin+beta+screen#post1762400](http://ubuntuforums.org/showthread.php?p=1762400&highlight=HOWTO+install+flash+9+plugin+beta+screen#post1762400)

> Click on the OK with your mouse, that should make the OK highlight red; The press Enter.
This didn't work unfortunately.

I have the same problem now with google earth from the PLF repository.

Anyone suggestions how to solve this 'behaviour'?

Cheers
Jonny

---

### Post by tseliot on 2006-11-18
> **jonnybecker said:**
> Hi,

still got the same problem:
[http://ubuntuforums.org/showthread.php?p=1762400&highlight=HOWTO+install+flash+9+plugin+beta+screen#post1762400](http://ubuntuforums.org/showthread.php?p=1762400&highlight=HOWTO+install+flash+9+plugin+beta+screen#post1762400)


This didn't work unfortunately.

I have the same problem now with google earth from the PLF repository.

Anyone suggestions how to solve this 'behaviour'?

Cheers
Jonny

press TAB until the word OK is highlighted. Then press ENTER

---

### Post by jonnybecker on 2006-11-18
Hi,

you are a lifesaver. This worked. Thanks!!! Hooray for tseliot.

Cheer
Jonny

---

### Post by dontunderstand on 2006-11-20
oh why bad things happen to me :( 

tried this .deb on my dapper. it didnt finish installing but had some errors, and now my synaptic and updater doesnt show any pakages anymore!!! when i start synaptic or update it says this:
> E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

i had flash7 installed and didnt uninstall it before.
so after .deb failed, i copied the libflashplayer.so from flash9 archive manually to usr/lib/firefox/plugins where no such named file was at this time, and it worked for a while, but afterwards (probably after restart) it was flash7 working again.


how do i fix my synaptic and everything :evil: ?

---

### Post by bruenig on 2006-11-20
> **dontunderstand said:**
> oh why bad things happen to me :( 

tried this .deb on my dapper. it didnt finish installing but had some errors, and now my synaptic and updater doesnt show any pakages anymore!!! when i start synaptic or update it says this:


i had flash7 installed and didnt uninstall it before.
so after .deb failed, i copied the libflashplayer.so from flash9 archive manually to usr/lib/firefox/plugins where no such named file was at this time, and it worked for a while, but afterwards (probably after restart) it was flash7 working again.


how do i fix my synaptic and everything :evil: ?
First do sudo apt-get remove flashplugin-nonfree. If that fixes it then fine. If it doesn't then redo the deb part of my initial howto:

1.Download that deb.

2.sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
Either way do sudo apt-get remove flashplugin-nonfree first.

---

### Post by dontunderstand on 2006-11-20
yeah, well the problem is i cant.
> ~$ sudo apt-get remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.


---

### Post by bruenig on 2006-11-20
> **dontunderstand said:**
> yeah, well the problem is i cant.
Move that deb on the original howto into /var/cache/apt/archives, then do sudo aptitude reinstall flashplugin-nonfree. Simple copy and paste commands:
```

cd /var/cache/apt/archives
sudo wget http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
sudo apt-get install flashplugin-nonfree
```
Also I would remove that manually installed flash plugin first just to be safe.

---

### Post by OMJD on 2006-11-20
Although this works for me, I find it very buggy and it won't play everything properly. In addition, it sometimes causes firefox to crash.

Is there a non beta for Flash 9?

---

### Post by gschoper on 2006-11-20
There's a new version of the flash 9 plugin available at [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

EDIT: This version seems to be a big improvement over the previous. No freezes on youtube/google video.

gschoper

---

### Post by Treviño on 2006-11-21
Packages: [http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/) ;)

---

### Post by dmizer on 2006-11-21
i get very choppy video from the most current release.  a slight improvement (7 always completely crashed firefox).  don't know about sound yet as i've had about the worst time in the world getting sound to work properly in any linux on any of my computers.

i found it amusing though that by visiting adobe's flash test site that it can't identify which version i'm using.

edit:
i need to check my desktop pager before i comment.  about an hour after i initially "installed" flash 9, i discovered that i still had an instance of firefox running in another desktop.  upon closing that and reinstalling flash 9, all is well.

edit II:
the adobe flash test site now correctly displays my flash version information.  amazing what restarting firefox can do.

---

### Post by st14n on 2006-11-21
Ah, finally the sound and picture is in sync. Upgraded from version 8 to 9 beta 2. But I also experience some choppy video, but it seems to be very seldom, so I don't find it annoying.

---

### Post by dontunderstand on 2006-11-21
maybe i need to reinstall the flash7 package but where do i get thatone?   

i deleted the manually installed file and then
> 
me@my-laptop:/var/cache/apt/archives$ sudo wget [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb)
--05:00:18--  [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb)
           => `flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb.3'
Lahendan 3v1n0.tuxfamily.org... 212.85.158.4
Loon ühendust serveriga 3v1n0.tuxfamily.org|212.85.158.4|:80... ühendus loodud.
HTTP päring saadetud, ootan vastust... 200 OK
Pikkus: 2 603 662 (2.5M) [application/x-debian-package]

100%[====================================>] 2 603 662  535.20K/s    ETA 00:00

05:00:23 (516.23 KB/s) - `flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb.3' salvestatud [2603662/2603662]

me@my-laptop:/var/cache/apt/archives$ sudo aptitude reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  flashplugin-nonfree
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the flashplugin-nonfree package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
me@my-laptop:/var/cache/apt/archives$


---

### Post by bruenig on 2006-11-21
> **dontunderstand said:**
> maybe i need to reinstall the flash7 package but where do i get thatone?   

i deleted the manually installed file and then

Yeah you probably should delete that file, enable the extra repositories and try to install the flash 7 flashplugin-nonfree and see if that works.

---

### Post by Sabrage on 2006-11-21
I'm trying to extract the the flash 9 beta 2 tarball in the /usr/lib/firefox/plugins/ folder, but I don't have permission to. How can I get permission to extract it?

Here's the link I'm using: [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)

---

### Post by Treviño on 2006-11-21
[dontunderstand]("http://ubuntuforums.org/member.php?u=140209") Try to download the latest version from [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) ;)
Sabrage, extract it with tar xf FP9_plugin_beta_112006.tar.gz, then sudo mv flash-dir/*.so /usr/lib/firefox/plugins (I don't remember exactly  the tar directory... Look for it :))

---

### Post by cnbiz850 on 2006-11-21
the new plugin seems to be conflict with Tab Mix Plus add-on. Whenever I click to close a tab, FF2 crashes.  Removing the flash plugin resolves it.

---

### Post by zgerrz on 2006-11-21
the beta 2 flash plugin from trevino's repo doesn't work at all for me. firefox thinks i have no flash installed at all.

the same happened to me for seveas's beta 2 flash.

beta 1 flash worked fine from trevino's repo.

---

### Post by pseudologically on 2006-11-21
> **Athanasius said:**
> I did a (I think) simpler version.. especially for the non-terminal gui people.

First, go to 
[http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

Download the plugin and extract to desktop.  Then open the file and right-click copy gflashplayer.so

Next open your home directory, hit ctrl+h and put it in your plugins folder under Mozilla.

It works fine for me:)
That's the way I did it!

I just did a new install and since I knew that I'd be using Flash 9 **beta** not 7 **final** I decided to never install 7 in the first place.

Works great this way, with no command lines; great for n00b5!

---

### Post by pseudologically on 2006-11-22
> **Sabrage said:**
> I'm trying to extract the the flash 9 beta 2 tarball in the /usr/lib/firefox/plugins/ folder, but I don't have permission to. How can I get permission to extract it?

Here's the link I'm using: [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)
Well, since this is a test version of Flash 9 for Linux, I'd suggest you don't even attempt to install Flash in that folder. Try using "~/.mozilla/plugins"

But if you insist on gaining Administrator privileges, typing "sudo " before before the "tar" command in the terminal will grant you those privileges. And, if you're not using a terminal . . . well . . . I don't know; quit now.

EDIT: I forgot to mention: you only need to right-click the archive and "Extract Here," then just copy the .so file; you don't need the README -- which you should always read when installing software and whatnot.

---

### Post by Sabrage on 2006-11-22
> **pseudologically said:**
> EDIT: I forgot to mention: you only need to right-click the archive and "Extract Here," then just copy the .so file; you don't need the README -- which you should always read when installing software and whatnot.

Thanks pseudologically, this worked great (sudo cp).

---

### Post by berserker on 2006-11-22
The latest beta still causes Firefox 2.0 to freeze on my system.  It must be one of the extensions that is causing a problem since most people seem to have had success with it.

---

### Post by hal10000 on 2006-11-26
I got flash 9 working fine, but only by installing it into my ~/.mozilla/plugins/ and still having flash 7 reside in /usr/lib/mozilla/plugins/. Without flash 7 on some sites I had no sound and on others the player would hang occasionally. A few days ago I installed the latest update (flash-player-plugin-9.0.21.78. Everything is fine and life is easy.

---

### Post by Magellan on 2006-11-26
I can't get Flash 7 or 9 running. 
I've tried Automatix, the installer from Adobe (for 7), instructions from this site (for 9) and instructions on the linked sites from this thread.

Nothing seems to work.

I'm running FF v1.5.0.0, Ubunti 6.06 (LTS).

Where in FF can I tell where the plugins should be?  I seems to have a number of choices: /usr/lib/mozilla/plugins; ~/.mozilla/pligins; /usr/lib/flashplugin-nonfree; /usr/lib/firefox/plugins; /usr/lib/mozilla-firefox/plugins; and maybe a few more that look like likely locations.

I can't find anywhere in FF where the plugins are listed.

------
Edit:
OK, I figured out that putting about: plugins into a browser pulls up the plug-in info.  Here's what I get:
    File name: /usr/lib/mozilla-firefox/plugins/libflashplayer.so
    Shockwave Flash 7.0 r68

According to this, it seems like I have flash 7 installed.  A number of sites I go to tell me I don't have the most recent version of Flash and direct me to the download site for Flash 7.  Maybe these sites require v9, but since I'm running Linux I get routed to the most recent stable version of Flash?

I'll try upgrading to 9 and checking this again.

Edit 2:
------
copying the libflashplayer.so to the folder specified in about: plugins fixed the problem. I am now able to view videos that I couldn't before.

Now to read the other threads on choppy video and sound...

---

### Post by Deathmoon on 2006-11-27
Awesome, the first post on this showed a great tutorial and it worked!  Before I did this, I could view videos on youtube, however I was not able to view videos on [www.liveleak.com;](www.liveleak.com;) this seemed to have fixed the problem!

---

### Post by lori.ann on 2006-11-27
If you're worried about flash ads, go into Firefox/Tools/Add-ons and add AdBlock Plus. It blocks everything out: banners, pop-ups, you name it.

---

### Post by rejekt on 2006-11-27
I issued the command...

```
sudo dpkg -i flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb
```

...after the wget statement and it opened up this license agreement thing inside  the terminal and I couldn't get rid of it. I tried hitting enter along with other options and nothing worked, except the 'escape' button. Well I finally just closed the terminal thinking it would go away and then tried to use the GUI interface to install the deb file. It gave me an error that only one updater can run at a single time. I've tried rebooting and shutting down, nothing seems to remove the process running trying to install it.

I tried to purge the install from the updater by using...

```
sudo dpkg --purge flashplugin-nonfree
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
```

...anyone have any suggestions to remove or fix this?

---

### Post by bruenig on 2006-11-27
> **rejekt said:**
> I issued the command...

```
sudo dpkg -i flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb
```

...after the wget statement and it opened up this license agreement thing inside  the terminal and I couldn't get rid of it. I tried hitting enter along with other options and nothing worked, except the 'escape' button. Well I finally just closed the terminal thinking it would go away and then tried to use the GUI interface to install the deb file. It gave me an error that only one updater can run at a single time. I've tried rebooting and shutting down, nothing seems to remove the process running trying to install it.

I tried to purge the install from the updater by using...

```
sudo dpkg --purge flashplugin-nonfree
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
```

...anyone have any suggestions to remove or fix this?

You have to use tab to get to the ok, and then hit enter.

---

### Post by rejekt on 2006-11-27
> **bruenig said:**
> You have to use tab to get to the ok, and then hit enter.

Thank you very much, that helped out and I completed the installation. :)

---

### Post by dmber on 2006-11-28
> **Athanasius said:**
> I did a (I think) simpler version.. especially for the non-terminal gui people.

First, go to 
[http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

Download the plugin and extract to desktop.  Then open the file and right-click copy gflashplayer.so

Next open your home directory, hit ctrl+h and put it in your plugins folder under Mozilla.

It works fine for me:)
this worked perfectly for me!  thank you so much!

---

### Post by blitzer on 2006-11-28
> **blitzer said:**
> Hey thanks for the reply bruenig :D 

But FLASH is all FUBAR'D for my system !

I think it has to do with moving files and not having root privs. [COLOR="Red"]Just guessing.[/COLOR]

[COLOR="Blue"]Is anyone using Yahoo mail having any problems with it ?  I can't use any of my inbox buttons at all - this has never happened before been with yahoo along time ](*,)  Sent e-mail to yahoo support and no answer :-|  [/COLOR]


Well I found my problem not having flash and Web mail not working - it was my router settings ](*,)   All this time and it was my router:redface: 

Thanks for the how-to all is good in flash world and web mail :-\"

---

### Post by berserker on 2006-11-28
> **blitzer said:**
> All this time and it was my router

What router setting did you change to fix your problem?

---

### Post by blitzer on 2006-11-28
> **berserker said:**
> What router setting did you change to fix your problem?


It was under my firewall settings tab:  Additional filters:  unticked -Filter Java Applets.

It just dawned on me my problems were web based and that led me to check my router.

---

### Post by merlyn on 2006-11-29
Hi all,

I downloaded the Flash 9 tarballs, uninstalled Flash 7, extracted Flash 9 and moved the Flash 9 lib across to my plugins directory.

Everything seemed to go as it should, but when I type about: plugins or visit Adobes 'about flash' site the reported version is still Flash 7.

Any tips, tricks or suggestions would be most welcome.

Cheers.

P.S the space between 'about:' and 'places' in the message above is deliberate, as a smiley kept on inserting into the message.

P.P.S never mind, it would seem that it took a while for the version change to 'register', everything is now cool. Thanks heaps for the HowTo.

---

### Post by mymate on 2006-11-29
great guide, thanks for this!

---

### Post by Literatka on 2006-12-04
I need version 8 of Macromedia but I don't know how to get it and I've finally got a verson in the package in this page but it's not working on this website : 
[http://www.dvbstyle.com/news/index.html](http://www.dvbstyle.com/news/index.html)

Any tips?

---

### Post by transantique on 2006-12-04
great topic guys[,](http://www.youtube.com/watch?v=WIF5dXqMtU4) than you very much[.](http://www.youtube.com/watch?v=WIF5dXqMtU4)[.](http://www.youtube.com/watch?v=WIF5dXqMtU4)

---

### Post by ReconUnit415 on 2006-12-09
Oh my god!

Thankyou for this tut!

Now I can view comcast.net right and I do not have to use that laggy IE 4 linux 6!

---

### Post by DrMilo on 2006-12-09
Thanks for the Deb, said it has dependency issues but don't we all.

---

### Post by JohnnyVW on 2006-12-09
> **berserker said:**
> The latest beta still causes Firefox 2.0 to freeze on my system.  It must be one of the extensions that is causing a problem since most people seem to have had success with it.

I'm having the same problem.  I uninstalled all of my extensions in FF 2.0, but it still freezes.  I noticed that if I minimize, then bring the window back up a few times, it'll eventually work...  kinda.

Is this a FF2/flash 9 thing?  Is there a video setting in FF2 that can be tweaked?  

So many sites have gone to flash 8/9 now.

---

### Post by berserker on 2006-12-09
> **JohnnyVW said:**
> Is this a FF2/flash 9 thing?

It's gotta be because flash 7 works just fine for me in Firefox/Swiftfox 2.

---

### Post by towanda on 2006-12-09
I am running Breezy and Firefox 2.0 on an older system that won't play nicely with Dapper.  I have meticulously followed all the installation methods in this topic and nothing has worked, although I have gotten to the point that Flash shows the first frame of whatever I'm trying to play and then freezes.  My Firefox talkback agent has been quite busy as well.  Here's what I have been using to test Flash:

[http://tinyurl.com/ydmqdd](http://tinyurl.com/ydmqdd)

Any help would be appreciated.

---

### Post by JohnnyVW on 2006-12-09
> **berserker said:**
> It's gotta be because flash 7 works just fine for me in Firefox/Swiftfox 2.

Yeah, Flash 7 works fine with my FF2/Edgy setup...

Has anyone had trouble with Flash 9 and FF 1.5?  I think I'm going to try it on the laptop.  For some reason, FF didn't get upgraded to 2.0 when I went from Dapper to Edgy.

---

### Post by towanda on 2006-12-10
Here are all the places where I have the .so file.  Where should it be so that Firefox doesn't crash all the time and so I can look at Flash pages?

towanda@my-machine:~$: locate libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla-firefox/plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/home/towanda/Desktop/flash-player-plugin-9.0.21.78/libflashplayer.so
/opt/firefox/plugins_2006-11-25T23:47:45-0600/libflashplayer.so

---

### Post by towanda on 2006-12-11
Here's the dmesg |tail from the last time Firefox crashed, which it has been doing since I've been trying to install Flash 9:

 dmesg | tail
[4303722.948000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4303722.948000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303724.406000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4303724.406000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303734.803000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4303734.803000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303736.182000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4303736.182000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303843.660000] Inbound IN=eth0 OUT= MAC=00:03:6d:1e:48:15:00:14:bf:31:e3:5f:08 :00 SRC=64.154.81.224 DST=192.168.1.101 LEN=41 TOS=0x00 PREC=0x00 TTL=235 ID=541 58 PROTO=TCP SPT=80 DPT=40647 WINDOW=32767 RES=0x00 ACK PSH URGP=0
[4303875.673000] Inbound IN=eth0 OUT= MAC=00:03:6d:1e:48:15:00:14:bf:31:e3:5f:08 :00 SRC=64.154.81.224 DST=192.168.1.101 LEN=41 TOS=0x00 PREC=0x00 TTL=235 ID=317 98 PROTO=TCP SPT=80 DPT=40647 WINDOW=32767 RES=0x00 ACK PSH URGP=0

---

### Post by marx2k on 2006-12-14
I'm trying to update to the latest v9 Beta 2 of FlashPlayer plugin for FF2

The only location I had libflashplayer.so was
/usr/lib/firefox/plugins/libflashplayer.so

so I manually removed that, then to test that FireFox didnt have it any more I went to Adobe's site to test and it told me to install the plugin.  So obviously flash player was gone.

I then downloaded the Version 9 Beta 2 from Adobe ([http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin](http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin)) and copied the .so file to 
/usr/lib/firefox/plugins/libflashplayer.so

I then went BACK to adobe and it says that I have version 7.0.68.0 installed.

I'm not sure what is going on here.  I also checked about:plugins and it tells me     
File name: libflashplayer.so    
Shockwave Flash 7.0 r68

I tried:
```

locate libflashplayer.so
/home/marx2k/Desktop/flash-player-plugin-9.0.21.78/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so

```

so Im not sure what else I can do?

---

### Post by marx2k on 2006-12-14
Alright, I restarted FireFox... then tried YouTube and it seems to be running with FlashPlayer 9

HOWEVER... when I go to about:plugins I see both

```

Shockwave Flash   File name: libflashplayer.so
Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```

at the the top and on the bottom I see

```

Shockwave Flash    File name: libflashplayer.so
Shockwave Flash 9.0 d78

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```

So.... I don't understand that. Can someone please explain?

---

### Post by bruenig on 2006-12-14
> **marx2k said:**
> Alright, I restarted FireFox... then tried YouTube and it seems to be running with FlashPlayer 9

HOWEVER... when I go to about:plugins I see both

```

Shockwave Flash   File name: libflashplayer.so
Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```

at the the top and on the bottom I see

```

Shockwave Flash    File name: libflashplayer.so
Shockwave Flash 9.0 d78

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```

So.... I don't understand that. Can someone please explain?

It sounds like there was some issue with the pluginreg.dat file. It is located at ~/.mozilla/firefox/pluginreg.dat. You can open that with a text editor and see all the stuff it has. Delete out the flash 7 part if you want. If everything works, don't see what the issue is but at least you know where it is coming from now.

---

### Post by marx2k on 2006-12-14
> **bruenig said:**
> It sounds like there was some issue with the pluginreg.dat file. It is located at ~/.mozilla/firefox/pluginreg.dat. You can open that with a text editor and see all the stuff it has. Delete out the flash 7 part if you want. If everything works, don't see what the issue is but at least you know where it is coming from now.

Strangely enough, that file only has the earlier version of Flash in it! It does inform that it is a generated file, so what script is it generated by? Anyone?

---

### Post by bruenig on 2006-12-14
How did you install flash 7 in the first place. If you installed via apt, you need to do sudo apt-get remove flashplugin-nonfree. I believe that this may be the issue because flashplugin-nonfree installs it to a different directory than /usr/lib/firefox/plugins and so firefox may be seeing both of the plugins.

---

### Post by marx2k on 2006-12-15
I believe it installed through the browser itself from the Adobe site.  However, about:plugins tells me that it is using File name: libflashplayer.so

So Im going to guess this is a mistake within the browser config files and I will disregard it since youtube shows Flash Player 9 in the right click/about 

Adobe also detects now that I have 9 installed whereas before it was saying 7.

---

### Post by rev_b on 2006-12-15
I noticed since I completely uninstalled flash from my system, and only extracted libflashplayer.so from flash 9 to ~/.mozilla/plugins , the firefox freezes (100% cpu utilization) stoped. Can anyone confirm this?

---

### Post by SNAKE2 on 2006-12-15
hey,
 I am new on this. I have downloaded  flash 7. it is now on my desktop, so how can I install it:confused:

---

### Post by bruenig on 2006-12-15
> **SNAKE2 said:**
> hey,
 I am new on this. I have downloaded  flash 7. it is now on my desktop, so how can I install it:confused:

Follow the howto on the first post of this thread. You don't want flash 7, 9 beta is much much better. To sum it up if you don't want to go to the front page, open a terminal, Applications>Accessories>Terminal and copy and paste the following.

```
wget http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb && sudo dpkg -i flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb
```

The whole thing, including the &&.

---

### Post by LaneLester on 2006-12-21
I installed the flash 9 beta, and then browsed to a site that uses Flash. My whole system went crazy, and after failing to get control back, I rebooted. Now all of my windows for every program have no borders and no title bar!

What do I need to do to heal my system?

**Later:** I accidently discovered that metacity had quit working. I ran it from a terminal, and everything is fixed.

Lane

---

### Post by bruenig on 2006-12-21
> **marx2k said:**
> I believe it installed through the browser itself from the Adobe site.  However, about:plugins tells me that it is using File name: libflashplayer.so

So Im going to guess this is a mistake within the browser config files and I will disregard it since youtube shows Flash Player 9 in the right click/about 

Adobe also detects now that I have 9 installed whereas before it was saying 7.

If you are using the ubuntu repos firefox, then the flash plugin is not installed through the browser. If you are using the firefox from firefox then the instructions would be completely different depending on where you installed it.

---

### Post by Lee Davies on 2006-12-29
Just to say thanks for the guide! Worked perfectly... even works for "Opera".

Just change "firefox" in;

> **bruenig said:**
> **Finally** move over the plugin to the plugins directory.
```
sudo mv libflashplayer.so /usr/lib/**firefox**/plugins/
```
to;

```
sudo mv libflashplayer.so /usr/lib/**opera**/plugins/
```

Thanks again!

---

### Post by tturrisi on 2006-12-29
Just out of curiosity, doesn't the ubunto repo have the latest flash plugin now?  I am running Etch & flash9.x was recently added to the deb repo.

---

### Post by bruenig on 2006-12-29
> **tturrisi said:**
> Just out of curiosity, doesn't the ubunto repo have the latest flash plugin now?  I am running Etch & flash9.x was recently added to the deb repo.
It looks like it is in the edgy-backports multiverse repository now. But that isn't a default repo, so I guess this probably still serves some purpose for some.

---

### Post by styven on 2006-12-30
Hi all,

Installed FP9 as per this thread, worked a treat. Thanks.

Only thing is upon rebooting my laptop this morning i ahve no sound at all, for anything, not even boot up beeps etc, no music will play etc.

I have booted a knoppix disc to check and it is not he hardware as i got sound.

So i need to uninstall FP9 to check this has not caused the problem, but don't know how?

Any help is appreciated.

Steve

---

### Post by bruenig on 2006-12-30
There is no reason that I can think of that could possibly cause the sound to go out because of installing flash. All this really does is add one file to a directory, nothing else.

---

### Post by Gremlinzzz on 2007-01-04
Download flashplayer 7to desktop -extract  to desktop                                                                                 ok =the commands to install are simple                                                                                                          cd Desktop
cd install_flash_player_7_linux
ls
./flashplayer-installer                                                                                                                                             ok now to make it flashplayer 9 Google flashplayer 9 updates download to desktop  extract    to desktop.go to home folder- click view- check show hidden folders open mozilla folder open plugin folder delete the plugins and replace with the flashplayer 9  plugins you downloaded.just copy and paste. done easy. the reason i do it this way is the edgy guide  way doesn't seem to be working.

---

### Post by bruenig on 2007-01-04
Why is flash player 7 necessary?

---

### Post by raul_ on 2007-01-04
[http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")

PS: i've answered this question at least 17 times in the forums ;) do a little searching...it doesn't hurt anybody, and it's faster than waiting for the replies

---

### Post by bruenig on 2007-01-04
> **raul_ said:**
> [http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")

PS: i've answered this question at least 17 times in the forums ;) do a little searching...it doesn't hurt anybody, and it's faster than waiting for the replies

This wasn't a question by the way. This was an attempt at a how to.

PS: Read the title and then the content before posting an answer and how about linking to a how to with deb packages when you do respond since those are better than manual installs. See my signature.

---

### Post by raul_ on 2007-01-05
Oh i'm sorry i was a little sleepy, i read that the installation wasn't working #-) may i suggest that you change the title of your thread to "HOW TO:" in capital letter, like the other how to's in the forum ;) and you should have posted it in the how-to's and faq's section. My bad, i apologise again :(

---

### Post by c-m on 2007-01-05
I have the following problem

pkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 flashplugin-nonfree depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
 flashplugin-nonfree depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 flashplugin-nonfree depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.
dpkg: error processing flashplugin-nonfree (--install):


can anyone help?

---

### Post by Gremlinzzz on 2007-01-07
Ok just paste the commands in terminal        [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by bruenig on 2007-01-07
Or for a deb that is tracked by apt, go to my signature.

---

### Post by jvc26 on 2007-01-07
Yup...
Il

---

### Post by bruenig on 2007-01-07
Someone had this problem earlier on IRC, his problem was that his system wasn't up to date. He pasted his sources.list and he had pretty much everything commented out and so his system was very far behind. Try
```
sudo apt-get update && sudo apt-get upgrade
```
and if that doesn't do anything, paste your /etc/apt/sources.list in here so I or someone else can see what you might be missing.

---

### Post by aysiu on 2007-01-07
Is there a question in this thread?

**Edit**: I've merged this with the other Flash 9 beta HowTo threads. We don't really need more than one of these.

---

### Post by saulgoode on 2007-01-07
> **bruenig said:**
> ... and how about linking to a how to with deb packages when you do respond since those are better than manual installs. See my signature.

Distributing Flash 9 as a DEB package -- indeed any distribution at all -- is forbidden by Section 3.b of [Adobe's End User License Agreement](http://labs.adobe.com/technologies/eula/flashplayer.html). You did read that before you downloaded the player, right? You therefore realize that you have now authorized Adobe to, at their discretion, enter your home or business and examine any technological gadgets that  they find (Section 2.b).

---

### Post by bruenig on 2007-01-07
> **saulgoode said:**
> Distributing Flash 9 as a DEB package -- indeed any distribution at all -- is forbidden by Section 3.b of [Adobe's End User License Agreement](http://labs.adobe.com/technologies/eula/flashplayer.html). You did read that before you downloaded the player, right? You therefore realize that you have now authorized Adobe to, at their discretion, enter your home or business and examine any technological gadgets that  they find (Section 2.b).

If this was the case, it would seem odd that ubuntu would have the package available in their repos. Has anyone told canonical about this, they usually are very cautious about stuff like this.

---

### Post by saulgoode on 2007-01-08
I wasn't aware that Flash 9 was in a repository. What I presented was an *End Users* License Agreement so perhaps Ubuntu has made special arrangements with Adobe that permits them to *distribute* it. I have been following the Adobe/Macromedia fiasco for well over a year now and I am not sure when the EULA appeared (I have no interest in installing Flash on my computer). Considering Adobe's lackadaisical attitude toward Linux, it is also quite possible that the EULA was not posted until after Ubuntu placed the program in their repository.

In any event, the apparent discrepancy warrants investigation. I am not that familiar with the Ubuntu process for handling such things (and this thread is probably not the appropriate place to discuss it). Perhaps one of the more veteran Ubuntu users might care to step in  and clarify this issue.

---

### Post by acorey on 2007-01-12
Hi, I just figured out how to install flash 9 myself. I didn't see this howto mainly because I didn't know that I needed flash 9.
 I was trying to watch Comedy Centrals John Stewart and kept getting a screen telling me I needed to update flash. It provided a link to the adobe site that would allow me to download flash 7 which is not the version needed to view the media on this site. Finally, I stumbled on references to flash 9 beta and installed it. It worked and I am now able to watch.
 Sorry if this sounds a little like a plug for CC or JS. I just wanted to make sure that some one could google straight to here if they are having the same problem.

---

### Post by fakie_flip on 2007-03-10
Why is gflashplayer not included with the Ubuntu package flashplugin-nonfree?

---

### Post by bruenig on 2007-03-10
gflashplayer is not in any of the repos is probably a good reason and it isn't necessary for flashplugin-nonfree to work so it isn't really a dependency. Forcing someone to download it would therefore be destructive to choice.

---

### Post by fakie_flip on 2007-03-12
How can I get gflashplayer?

---

### Post by bruenig on 2007-03-13
> **fakie_flip said:**
> How can I get gflashplayer?

what is gflashplayer? are you talking about gnash or something else?

---

### Post by fakie_flip on 2007-03-14
It is a standalone flash player. It does not require a browser to run in. If you download a flash movie to your computer, you can use gflashplayer to play it. Totem will play some flash movies but not very well. It can't take user input.

---

### Post by victorbrca on 2007-05-04
> **yemu said:**
> hi,
it's going to b very short howto:

1. download Flash9BETA from [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

2. close Firefox

3. unpack the file in the temporary directory

4. rename ~/.mozilla/plugins/libflashplayer.so to eg. libflashplayer.bak

5. copy the libflashplayer.so from downloaded archive to ~/.mozilla/plugins

6. Start Firefox and enjoy your brand new Flash9 :-)

This works in Edgy but should also work in Dapper

Best regards
Yemu



Just installed this way on my Edgy and it worked!!!!  Now I can use gadgets on my iGoogle to listen to RadioBlogClub!!!!


Vic.

---

### Post by alextaylor88 on 2007-06-20
Thanks for the info everyone. I'll try it. I may be back. Keep in mind I'm a Apple and Windows
person since the 80's.
Bye,
Alex

---

### Post by orionjoe on 2008-01-04
So I'm a brand-new Ubuntu user and I cannot get the flash plugin to work. I've uninstalled it and reinstalled it several times. When I go to a page that has flash ,something with embedded youtube for example, I get a notification from firefox saying I need to download the needed plugin. I choose the Adove Flash player 9 and next and I get an error saying it's already installed...but flash still doesn't work on any site.

Sorry if this is long-winded, I'm starting to get frustrated :P

Any help would be greatly appreciated, thanks!

---

