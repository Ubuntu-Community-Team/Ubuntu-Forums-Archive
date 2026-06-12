---
title: "Swiftfox, a faster Firefox"
date: 2006-03-11
forum: Outdated Tutorials &amp; Tips
---

### Post by pgmario on 2006-03-11
How would you like a faster Firefox?
I just stumbled upon [http://getswiftfox.com/](http://getswiftfox.com/) , offering "an optimized build of Mozilla Firefox for **AMD and Intel processors** including Athlon XP, Pentium4, Athlon 64, Celeron, Duron and Sempron." 

There are builds of the most recent official release (2.0 at the moment) and even newer branch and trunk builds:[LIST]
[*]Swiftfox 2.0 = Same version as the Firefox shipped with Ubuntu 6.10 "Edgy Eft" (but faster, of course). I recommend you download this version if you want a browser for everyday use.
[*]Swiftfox 2.0.0.1pre (Gecko 1.8 branch) = This is where all security patches go. It will be Swiftfox 2.0.x.
[*]Trunk = Will be Firefox/Swiftfox 3 (Your extensions won't work with this.)[/LIST]The latter three builds are updated almost daily. 
I have only tried the 2.0 build so far, and it does not only feel faster, the test at [http://scragz.com/tech/mozilla/test-rendering-time](http://scragz.com/tech/mozilla/test-rendering-time) proved that feeling to be correct.
Rory made an extensive speed test of all versions and compared them to Firefox and Epiphany. You can find his post [here]("http://ubuntuforums.org/showthread.php?p=861088#post861088").

[U][B]Overview
[/B][/U][B]
1. Installation
2. Enable all plugins
3. [/B][B]Starter on your desktop or taskbar
[/B]**4. Localization**
**5. If your extensions don't work** 
**6. Speed up things even more**


[B]1. Installation:
[/B]**EDIT: **There is a **repository** online now, so that you can always get the latest version of swiftfox automatically. Just add the following line to /etc/apt/sources.list and do a ```
sudo apt-get update && sudo apt-get install swiftfox
```---OTHER/OLDER WAYS TO INSTALL SWIFTFOX---
You can download **Ubuntu-debs** from [http://getswiftfox.com/ubuntu.htm](http://getswiftfox.com/ubuntu.htm). Just download the appropriate file for your processor, go to the directory where you downloaded it to and type ```
sudo dpkg -i swiftfox*ubuntu*.deb
```Installation without a .deb:[LIST=1]
[*]Go to [http://getswiftfox.com/](http://getswiftfox.com/) and download a build of your choice (e.g. Swiftfox 1.5.0.7)
[*]Extract the downloaded tar.bz2-file into your home directory, giving you a "swiftfox" directory.
[*]If you have any Firefox windows open, close them.
[*]Go to the "swiftfox" directory in your home folder (with Nautilus or in a terminal or whatever you like) and start the file called "firefox" (surprise). Enjoy surfing faster![/LIST]To uninstall, just delete the "swiftfox" folder.

-------------------------------------------

Swiftfox automatically used my old preferences, bookmarks, etc.

**2. Enable all plugins**
To enable all plugins (flash, etc.) from your original Firefox installation do (make sure to enter that trailing dot):
```
cd /path/to/your/homefolder/swiftfox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* . 
```As long as you have one Swiftfox window open, all calls from other applications (e.g. your e-mail client) to open a new Firefox window/tab will open it in Swiftfox.

**3. Starter on your desktop or taskbar**
If you have a starter on your desktop or taskbar for Firefox and want to make it start Swiftfox:[LIST=1]
[*]right-click on the starter icon
[*]choose "properties"
[*]change the command to ```
/path/to/your/homefolder/swiftfox/swiftfox
```[/LIST]**4. Localization**
For information on how to localizeSwiftfox, e.g. to change the menus to be in German, Swedish, or any other language, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=212310").
[B]
5. If your extensions don't work[/B] 
If you use one of the branch or trunk builds instead of that of the recent release (2.0), *some of your extensions might not work*. 
To re-enable them after you have switched back to 2.0 go to Tools>Extensions, right-click on the disabled extensions and select "enable".
You could also create **a new profile for testing purposes**: In a terminal, change to the Swiftfox folder and launch the profile manager with the following command (make sure to enter that dot in front of the slash): ```
 ./firefox -ProfileManager
```**6. Speed up things even more**
If you want to speed up things even more, you could install the [Fasterfox]("http://fasterfox.mozdev.org/") extension. This works in both Swiftfox and the regular Firefox. I don't use prefetching, but the network tweaks it applies are excellent.

---

### Post by GoA on 2006-03-12
How much faster it was? I'm currently downloading it to test it out, first run on normal firefox: 5.5 second: 6.4 third: 6.7.

EDIT: Swiftfox

First: 2.5
Second 3.24
Third 3.39.

That's about two times faster. Holy*.

And in normal usage it's also a lot faster than Dappers default firefox. Thanks for the tip. :)

---

### Post by pgmario on 2006-03-12
I added information on how to enable plugins from an older Firefox installation.

---

### Post by NoWhereMan on 2006-03-12
cool man, if only it weren't locked, that would be cool in dapper... maybe as an option?

---

### Post by Lord Illidan on 2006-03-12
Nice.. Is there one optimized for Intel now?

---

### Post by pgmario on 2006-03-12
[quote=NoWhereMan]cool man, if only it weren't locked, that would be cool in dapper... maybe as an option?[/quote] What do you mean by "locked"? That no new packages are accepted into Dapper? That's not too much of a problem, you can also install it under Dapper following the exact same instructions above.
[quote=Lord Illidan]Nice.. Is there one optimized for Intel now?[/quote] Not from Swiftfox. But I would suggest taking a look at [http://forums.mozillazine.org/]("http://forums.mozillazine.org/"). There are more optimized builds under "Third Party/Unofficial builds".

---

### Post by NoWhereMan on 2006-03-12
[QUOTE=pgmario]What do you mean by "locked"? That no new packages are accepted into Dapper? That's not too much of a problem, you can also install it under Dapper following the exact same instructions above.[/QUOTE]
Sure, and so I did, I meant it would have been nice if it could come bundled with dapper :)

---

### Post by pgmario on 2006-03-12
[quote=NoWhereMan]Sure, and so I did, I meant it would have been nice if it could come bundled with dapper :)[/quote] That would be cool, but I have my doubts this is ever going to happen, since it's unofficial and the official Firefox is already included. I would like to be proven wrong, though. :-)

---

### Post by NoWhereMan on 2006-03-12
[QUOTE=pgmario]That would be cool, but I have my doubts this is ever going to happen, since it's unofficial and the official Firefox is already included. I would like to be proven wrong, though. :-)[/QUOTE]

universe repo? :)

---

### Post by mjwood0 on 2006-03-12
This really is great!  My rendering times at the site provided went from around 6 seconds to under 3 seconds.  Really does seem faster too.

Plus, all the plugins seem to work just fine.  Truely a great improvement!

Thanks!

---

### Post by mstlyevil on 2006-03-12
Excellent. I can attest that this works great in Dapper.

---

### Post by MighMoS on 2006-03-12
/me has a flashback to his gentoo days.

This definately looks cool, I may deb it up for conveniance in a few days (and with Intel opts as well, *I guess*).

---

### Post by geearf on 2006-03-12
Hello,
I'm trying the 1.8 build right now it really seems faster.
But maybe because of 1.8 I'll have to try the 1.5 later.

---

### Post by geearf on 2006-03-12
Now it also makes me wanting to try a nice port of mmoy's patches to linux, even if his work is oriented to P4 processor.

---

### Post by MetalMusicAddict on 2006-03-12
[QUOTE=GoA]How much faster it was? I'm currently downloading it to test it out, first run on normal firefox: 5.5 second: 6.4 third: 6.7.

EDIT: Swiftfox

First: 2.5
Second 3.24
Third 3.39.

That's about two times faster. Holy*.

And in normal usage it's also a lot faster than Dappers default firefox. Thanks for the tip. :)[/QUOTE]
Where I can I test render times like this?

---

### Post by mstlyevil on 2006-03-12
[QUOTE=MetalMusicAddict]Where I can I test render times like this?[/QUOTE]

Install the fasterfox extention into firefox and it will also be installed in swiftfox at the same time. The extention will display the render times at the bottom toolbar on the right.

---

### Post by pgmario on 2006-03-12
[quote=MetalMusicAddict]Where I can I test render times like this?[/quote] [http://scragz.com/tech/mozilla/test-rendering-time]("http://scragz.com/tech/mozilla/test-rendering-time"), as mentioned in my first post.

---

### Post by dralaroc on 2006-03-12
Yup, a little quicker on my celeron.  No install issues using Dapper.

---

### Post by treys on 2006-03-13
[QUOTE=dralaroc]Yup, a little quicker on my celeron.  No install issues using Dapper.[/QUOTE]
Celeron is a Intel cpu, this build is optimized for Athlon cpus...

One question, how will the update in ff work? Will there be no problem updating?

---

### Post by GoA on 2006-03-13
You have to be more careful when reading this forum, the testsite was mentioned in the first post. ;)

---

### Post by monkeyface on 2006-03-13
Sounds good, but does it change the name from Firefox to Swiftfox? if so, that doesn't sound very good.. :-#

---

### Post by monkeyface on 2006-03-13
[QUOTE=GoA]How much faster it was? I'm currently downloading it to test it out, first run on normal firefox: 5.5 second: 6.4 third: 6.7.

EDIT: Swiftfox

First: 2.5
Second 3.24
Third 3.39.

That's about two times faster. Holy*.

And in normal usage it's also a lot faster than Dappers default firefox. Thanks for the tip. :)[/QUOTE]
Maybe it is time to switch to Gentoo? Didn't knew you actually can feel a difference.. :-k

---

### Post by John.Michael.Kane on 2006-03-13
Can't one just copy the about:conf settings for swiftfox, and apply them to ubuntu's firefox, and have the same effects.

---

### Post by monkeyface on 2006-03-13
[QUOTE=SD-Plissken]Can't one just copy the about:conf settings for swiftfox, and apply them to ubuntu's firefox, and have the same effects.[/QUOTE]
No, the binaries is compiled with MMX, SSE etc. and are optimized for athlon-xp.

---

### Post by pgmario on 2006-03-13
> **treys]One question, how will the update in ff work? Will there be no problem updating?[/quote] I don't know. It says "Automatically check for updates for Swiftfox" in the preferences, but I don't know if this really works. You could either mail the developer and ask him or just wait until 1.5.0.2 of FF2 comes out.

[quote=monkeyface]Sounds good, but does it change the name from Firefox to Swiftfox? if so, that doesn't sound very good.. :-#[/quote] It does change the name, but it still credits the Firefox developers.

[quote=monkeyface] Maybe it is time to switch to Gentoo? Didn't knew you actually can feel a difference.. :-k[/quote] If you think it's worth compiling EVERYTHING yourself, go ahead. But I don't want to start any flaming here, everyone can of course do what suits him best  said:**
> Can't one just copy the about:conf settings for swiftfox, and apply them to ubuntu's firefox, and have the same effects. The effects don't have anything to do with about:conf, but can only be applied with optimization flags when compiling the application from source. Of course you can then tweak network settings under about:conf in both FF and Swiftfox or use the [Fasterfox]("http://fasterfox.mozdev.org/") extension to speed things up even more (I'll add this extension to the how-to).

---

### Post by dralaroc on 2006-03-13
[QUOTE=treys]Celeron is a Intel cpu, this build is optimized for Athlon cpus...

One question, how will the update in ff work? Will there be no problem updating?[/QUOTE]


Yeah I know.  I installed Dapper this past weekend.  I was using Breezy, and I am just having loads of fun installing stuff to see how it works, what effects that it has on my system etc.  I am new to this linux stuff 2.5 weeks now and I have already installed then reinstalled the Os about 5 times.  I guess you can say I break it to fix it.  Sorry to get off topic. Dapper runs like a champ by the way!!

---

### Post by i3dmaster on 2006-03-13
[QUOTE=geearf]Hello,
I'm trying the 1.8 build right now it really seems faster.
But maybe because of 1.8 I'll have to try the 1.5 later.[/QUOTE]
Are you talking about Mozilla 1.8 or firefox 1.8..? I've never heard firefox is going to ver 1.6 above even dev release...

---

### Post by i3dmaster on 2006-03-13
[QUOTE=pgmario][http://scragz.com/tech/mozilla/test-rendering-time]("http://scragz.com/tech/mozilla/test-rendering-time"), as mentioned in my first post.[/QUOTE]
I used Opera9 TP2 to test the same thing and it seems much faster than firefox.

---

### Post by pgmario on 2006-03-13
[quote=i3dmaster]Are you talking about Mozilla 1.8 or firefox 1.8..? I've never heard firefox is going to ver 1.6 above even dev release...[/quote]
In contrast to the 1.5 number, 1.8 does not refer to the Firefox version, but to that of the rendering engine Gecko. Gecko 1.8 is the foundation for Firefox 1.5, as you can see in this [roadmap](http://cbeard.typepad.com/.shared/image.html?/photos/uncategorized/releaseroadmapdraftv1_2.png).

---

### Post by pgmario on 2006-03-13
[quote=i3dmaster]I used Opera9 TP2 to test the same thing and it seems much faster than firefox.[/quote]
I don't have Opera installed at the moment, so I can't comment on its speed. The reason I don't have it installed is that I really like Firefox's extension system. I think the last version of Opera I ran was 8.x and I didn't like its interface (many, many options, yet not some of those which some Firefox extensions give you).
But if you prefer it, ok. It's adhering to the standards, so I won't try to convince you to use Firefox. ;)

---

### Post by IGNIZ on 2006-03-13
mplayer plugin doesn't work for me, the others just works fine, any idea? i installed firefox and plugins with automatix

---

### Post by pgmario on 2006-03-13
[quote=IGNIZ]mplayer plugin doesn't work for me, the others just works fine, any idea? i installed firefox and plugins with automatix[/quote] Did you follow the instructions in the first post on how to enable the plugins? If you didn't...do :D If you did, try ```
cd /path/to/your/homefolder/swiftfox/plugins[FONT=monospace] 
[/FONT]sudo rm libtotem_mozilla.*
``` And restart Firefox.

---

### Post by FlashBuster on 2006-03-13
[QUOTE=GoA]How much faster it was? I'm currently downloading it to test it out, first run on normal firefox: 5.5 second: 6.4 third: 6.7.

EDIT: Swiftfox

First: 2.5
Second 3.24
Third 3.39.

That's about two times faster. Holy*.

And in normal usage it's also a lot faster than Dappers default firefox. Thanks for the tip. :)[/QUOTE]

Epiphany (with 10 Tabs open,most extensions enabled, didn't even close it and do a clean start!) gave me:
1st: 2,15 s
2nd: 2,17 s
3rd: 2,10 s

Firefox(clean startup):
1st: 4,10 s
2nd: 415 s
3rd: 4,04 s

I think I'll go with Epiphany \\:D/

---

### Post by pgmario on 2006-03-13
[quote=FlashBuster]Epiphany (with 10 Tabs open,most extensions enabled, didn't even close it and do a clean start!) gave me:
1st: 2,15 s
2nd: 2,17 s
3rd: 2,10 s

Firefox(clean startup):
1st: 4,10 s
2nd: 415 s
3rd: 4,04 s

I think I'll go with Epiphany \\:D/[/quote]
Did you test Firefox or Swiftfox?

---

### Post by benplaut on 2006-03-13
i'm gonna compile it myself some day... we'll see how it is, then :D

---

### Post by GoA on 2006-03-14
[QUOTE=monkeyface]Maybe it is time to switch to Gentoo? Didn't knew you actually can feel a difference.. :-k[/QUOTE]

In theory yes but Ubuntu is so good that I'm just going to tweak this system. And with 10/10 mb internet connection the difference is a little bigger because now the pages just about flashes to your browser. So there definetly is a difference. And also Dappers firefox has been said quite widely that it is slow.

---

### Post by FlashBuster on 2006-03-14
[QUOTE=pgmario]Did you test Firefox or Swiftfox?[/QUOTE]
I tested Firefox, since the mainreason for swiftfox seems to be the "optimization" and epiphany seems to work faster.
Another reason is that I'm running a Pentium M, so i won't install an AMD-optimized build (although it should work as well).

---

### Post by dcstar on 2006-03-14
Looked ok until I tried to install the mozdev dictionaries so my Spellbound extension would work again - then it refused to start again with a segmentation fault!

Oh well, it was an interesting exercise for about 40 minutes........

EDIT: Hmm, reinstalled and went in as root user to install the dictionaries again, worked ok as root user, but when I ran Swiftfox as my normal user is crashed again - the first time!

Subsequent uses run ok!!

---

### Post by TrendyDark on 2006-03-14
Downloaded the file, checked it out, just like my Firefox browser (themes and all), so I don't get the point. Meh, seemed a little faster.

---

### Post by pgmario on 2006-03-14
[quote=TrendyDark]Downloaded the file, checked it out, just like my Firefox browser (themes and all), so I don't get the point. Meh, seemed a little faster.[/quote]
Well, yes. That's what it is. It **is **your Firefox browser, just a little bit faster (if you're using an AMD processor). That's why the description says it's an optimized build of the Mozilla Firefox browser.

---

### Post by pgmario on 2006-03-14
[quote=dcstar]Looked ok until I tried to install the mozdev dictionaries so my Spellbound extension would work again - then it refused to start again with a segmentation fault!

Oh well, it was an interesting exercise for about 40 minutes........

EDIT: Hmm, reinstalled and went in as root user to install the dictionaries again, worked ok as root user, but when I ran Swiftfox as my normal user is crashed again - the first time!

Subsequent uses run ok!![/quote]
I haven't had any problems here so far. Let us know if it keeps working.

---

### Post by dermotti on 2006-03-14
Hmm interesting. 

My firefox renders the page in 9.6547 seconds

I just installed Epiphany, and it renders the page in like 2.656 seconds.


Epiphany faster than firefox?

---

### Post by pgmario on 2006-03-14
[quote=dermotti]Epiphany faster than firefox?[/quote]
Not here...
Swiftfox (with 18 extensions): 3,19
Epiphany: 4,41

---

### Post by dermotti on 2006-03-14
How do you tell how many "extensions" are active? maybe my firefox is loading extensions and my Epiphany isnt....

---

### Post by pgmario on 2006-03-14
[quote=dermotti]How do you tell how many "extensions" are active? maybe my firefox is loading extensions and my Epiphany isnt....[/quote] I'm talking about the extensions you can install in Firefox under Tools > Extensions. E.g. BugMeNot or AdBlock. Have a look at [https://addons.mozilla.org/extensions/?application=firefox]("https://addons.mozilla.org/extensions/?application=firefox"). You cannot install extensions in Epiphany.

---

### Post by Xanf on 2006-03-14
I've found that it's actually enough to disable PANGO for normal Ubuntu Firefox - and the difference with Swiftfox becomes almost non-existent.
The main problem of FF in UBUNTU is PANGO...:(

---

### Post by IGNIZ on 2006-03-14
[QUOTE=pgmario]Did you follow the instructions in the first post on how to enable the plugins? If you didn't...do :D If you did, try ```
cd /path/to/your/homefolder/swiftfox/plugins[FONT=monospace] 
[/FONT]sudo rm libtotem_mozilla.*
``` And restart Firefox.[/QUOTE]
i did, but i haven't swiftfox/firefox/plugins so i did on swiftfox/plugins and the only one not working is the mplayer plugin

i did what u said but there is no libtotem_mozilla in my plugins folder so i can't remove it...

this is the ls of my swiftfox/plugins

flashplayer.xpt    libjavaplugin_oji.so  libunixprintplugin.so
libflashplayer.so  libnullplugin.so      nppdf.so

---

### Post by Zeroangel on 2006-03-14
[QUOTE=Xanf]I've found that it's actually enough to disable PANGO for normal Ubuntu Firefox - and the difference with Swiftfox becomes almost non-existent.
The main problem of FF in UBUNTU is PANGO...:([/QUOTE]
Is there an option to do this somewhere? Or do you have to compile FF without Pango?

---

### Post by dermotti on 2006-03-14
[QUOTE=pgmario]I'm talking about the extensions you can install in Firefox under Tools > Extensions. E.g. BugMeNot or AdBlock. Have a look at [https://addons.mozilla.org/extensions/?application=firefox]("https://addons.mozilla.org/extensions/?application=firefox"). You cannot install extensions in Epiphany.[/QUOTE]


Tools --> Extensions  in epiphany shows extensions

---

### Post by pgmario on 2006-03-14
[quote=IGNIZ]i did, but i haven't swiftfox/firefox/plugins so i did on swiftfox/plugins and the only one not working is the mplayer plugin

i did what u said but there is no libtotem_mozilla in my plugins folder so i can't remove it...

this is the ls of my swiftfox/plugins

flashplayer.xpt    libjavaplugin_oji.so  libunixprintplugin.so
libflashplayer.so  libnullplugin.so      nppdf.so[/quote] Try
```
sudo apt-get install mozilla-mplayer
cd /path/to/your/homefolder/swiftfox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* . 
``` You will get some errors that most of the files already exist. But you should then find some links similar to "mplayer-plugin..." in that directory.

And you're right, there is no directory called /homefolder/swiftfox/firefox, I corrected that.

[quote=dermotti]
Tools --> Extensions  in epiphany shows extensions[/quote] Ooops, sorry. That's cool... :cool:
Are there more extensions available than the ones installed with apt-get?

---

### Post by Zeroangel on 2006-03-14
I've just replaced my Firefox 1.5.1 installation (/opt/firefox/) for the Swiftfox branch release. After backing up the old 1.5 install, replacing the content of /opt/firefox with the swiftfox install and copying plugins from the 1.5 install over to swiftfox, I have found that it works flawlessly!

---

### Post by i3dmaster on 2006-03-14
[QUOTE=pgmario]I don't have Opera installed at the moment, so I can't comment on its speed. The reason I don't have it installed is that I really like Firefox's extension system. I think the last version of Opera I ran was 8.x and I didn't like its interface (many, many options, yet not some of those which some Firefox extensions give you).
But if you prefer it, ok. It's adhering to the standards, so I won't try to convince you to use Firefox. ;)[/QUOTE]
In fact I use both. That's why I feel opera is a little faster.. but you'r right, the FF extension is a cool feature that I like too...

---

### Post by Xanf on 2006-03-14
[QUOTE=Zeroangel]Is there an option to do this somewhere? Or do you have to compile FF without Pango?[/QUOTE]

Yep.  See this thread:

[http://www.ubuntuforums.org/showthread.php?t=134627](http://www.ubuntuforums.org/showthread.php?t=134627)

---

### Post by Zeroangel on 2006-03-14
Man, Ubuntu should make a seperate binary called mozilla-firefox-ndn for those who need to view indic pages.

EDIT: Nevermind. Just swiped this post from the link.
[QUOTE=diebels]You don't need to recompile it.

Just run with:
MOZ_DISABLE_PANGO=1 firefox

If you want to make it permanent(until next update), then:
```
sudo mv /usr/bin/firefox /usr/bin/firefox.orig
```
```
sudo gedit /usr/bin/firefox
```
insert this:
```
#!/bin/sh
MOZ_DISABLE_PANGO=1 firefox.orig $@
```
```
sudo chmod +x /usr/bin/firefox
```[/QUOTE]
Guess it doesn't need to be recompiled.

---

### Post by Xanf on 2006-03-14
I actually solved this issue in rather harsh way - by simply disabling PANGO globally - by MOZ_DISABLE_PANGO=1  setting in environment. :cool:

---

### Post by Zeroangel on 2006-03-14
I think I discovered a bug in SwiftFox.

I am running into problems installing extensions. Every time I try to install an extension, SF/FF will not start. 

I've discovered that when the extension is installed the files are written to the extensions/{extensionid} folder but some of them are marked as read only and the access permissions are otherwise borked. Setting the access permissions to a normal (rwxr-xr-x) will fix the problem and allow that extension to be installed, but it must be done for each extension that you are installing.

Does anyone else get this bug in Swiftfox?

---

### Post by zachtib on 2006-03-15
I saw this and got really excited to the point that I started to download it before remembering I have a pentium m cpu...

---

### Post by saads on 2006-03-15
Many of my extensions don't work.  It says they are not compatible with Swiftfox 1.6a1.  Like All-in-one Gestures, Tab Clicking Options, and User Agent Switcher.

---

### Post by mstlyevil on 2006-03-15
[QUOTE=saads]Many of my extensions don't work.  It says they are not compatible with Swiftfox 1.6a1.  Like All-in-one Gestures, Tab Clicking Options, and User Agent Switcher.[/QUOTE]

Replace it with this version of Swiftfox (Swiftfox 1.5.0.1) and they should work. It uses the same engine version as Firefox 1.5.

---

### Post by saads on 2006-03-15
ya, i actually used the 1.8 version - works fine.  I was using the Ahtlon64 trunk version before.

---

### Post by pgmario on 2006-03-15
[quote=Zeroangel]I think I discovered a bug in SwiftFox.

I am running into problems installing extensions. Every time I try to install an extension, SF/FF will not start. 

I've discovered that when the extension is installed the files are written to the extensions/{extensionid} folder but some of them are marked as read only and the access permissions are otherwise borked. Setting the access permissions to a normal (rwxr-xr-x) will fix the problem and allow that extension to be installed, but it must be done for each extension that you are installing.

Does anyone else get this bug in Swiftfox?[/quote] I have no problems installing extensions. Where is your Swiftfox installed? I have its folder in my home directory and everything works fine.
EDIT: I just saw your post where you said you installed it in /opt. Try to install it in /home/yourusername/

---

### Post by _simon_ on 2006-03-15
I can't see the difference between the different versions.

Which should I be using? I have an Athlon XP.

---

### Post by pgmario on 2006-03-15
[quote=_simon_]I can't see the difference between the different versions.

Which should I be using? I have an Athlon XP.[/quote]
You could use every build **except** the "Trunk for AMD64". The stable version is 1.5.0.1, and all of your extensions should work with it. So I suggest you try that build.

---

### Post by ts2000 on 2006-03-15
Swiftfox won't run.  Here's the output.  Any ideas.  Permission seem to be okay.


dave@ubuntu:~/swiftfox$ ./firefox
./run-mozilla.sh: line 131:  6405 Illegal instruction     "$prog" ${1+"$@"}

---

### Post by ts2000 on 2006-03-15
Fixed error:

"dave@ubuntu:~/swiftfox$ firefox
./run-mozilla.sh: line 131:  6405 Illegal instruction     "$prog" ${1+"$@"}  "

I deleted firefox from synaptic package manager.

Now runs fine.

Dave.

---

### Post by dcstar on 2006-03-24
[QUOTE=Zeroangel]I think I discovered a bug in SwiftFox.

I am running into problems installing extensions. Every time I try to install an extension, SF/FF will not start. 

I've discovered that when the extension is installed the files are written to the extensions/{extensionid} folder but some of them are marked as read only and the access permissions are otherwise borked. Setting the access permissions to a normal (rwxr-xr-x) will fix the problem and allow that extension to be installed, but it must be done for each extension that you are installing.

Does anyone else get this bug in Swiftfox?[/QUOTE]
I had extension related problems, but they seemed to fix themselves after a few attempts to start up Swiftfox.

I didn't check any file permissions, so it could have been that on my system too.

---

### Post by cerebrix on 2006-03-24
```
@ubuntu:~/swiftfox/plugins$ sudo ln -s /usr/lib/mozilla-firefox/plugins/* 
ln: target `/usr/lib/mozilla-firefox/plugins/nppdf.so' is not a directory
```

any ideas?

---

### Post by geearf on 2006-03-24
yes you're not saying where you want your simlink.

You can a "." for example.

---

### Post by pgmario on 2006-03-24
Yes, you forgot that trailing ".", which means "current directory".
Make sure to copy the entire line from my first post.

---

### Post by zero0w on 2006-03-24
Really nice build, it's compiled with gcc4, so it will solve the [SCIM issue](https://wiki.ubuntu.com/SCIM) as well.

I feel a little faster with everything down to the interface responsiveness. Beautiful job.

---

### Post by bradlis7 on 2006-03-24
Is there any way to make middle mouse click close a window on swiftfox? I can't stand what it does now. I don't even understand what it's supposed to do.

EDIT: Oops, it's at [http://www.mozilla.org/support/firefox/mouse](http://www.mozilla.org/support/firefox/mouse) right under the table.

---

### Post by frodon on 2006-03-25
[QUOTE=ts2000]Fixed error:

"dave@ubuntu:~/swiftfox$ firefox
./run-mozilla.sh: line 131:  6405 Illegal instruction     "$prog" ${1+"$@"}  "

I deleted firefox from synaptic package manager.

Now runs fine.

Dave.[/QUOTE]Is there another way to get rid of this error ?, firefox has some dependencies and there's some package i don't want to remove.

---

### Post by The Pinny Parlour on 2006-03-25
Firstly, thank you.   Just installed Swiftfox as I was getting tired of how slow breezy's default FF was loading (slowly).  The Swiftfox install procedure mention on post 1 works a treat.  All my bookmarks, ext, etc are working fine.  

Best of all, it's HEAPS quicker.

Thank you for bringing this build to my attention.

---

### Post by pgmario on 2006-03-25
[quote=frodon]Is there another way to get rid of this error ?, firefox has some dependencies and there's some package i don't want to remove.[/quote] I don't get this error, so I can't help you with it. But I wouldn't remove the Ubuntu Firefox either because of all the dependencies. Which version of Swiftfox did you install? As I said, 1.5.0.1 works fine here. Trunk builds may or may not work.
[quote=The Pinny Parlour]Firstly, thank you.   Just installed Swiftfox as I was getting tired of how slow breezy's default FF was loading (slowly).  The Swiftfox install procedure mention on post 1 works a treat.  All my bookmarks, ext, etc are working fine.  

Best of all, it's HEAPS quicker.

Thank you for bringing this build to my attention.[/quote]
You're welcome :-)

---

### Post by Rory on 2006-03-25
Benchmark results on Ubuntu Breezy 32 bit w/ k7 kernel installed and ati drivers installed.
Athlon XP 3000+ 64 / 512mb RAM / ATI 9200SE / K8V SE Deluxe


MULTIPLE SPEED TEST: (for lack of a better title)
[http://www.24fun.com/downloadcenter/benchjs/benchjs.html](http://www.24fun.com/downloadcenter/benchjs/benchjs.html)  (Final Results)
Epiphany:               12.5 seconds
Firefox:                  19 seconds w/extensions
Swiftfox 1.5.0.1:     10 seconds  w/out extensions 17 sec. w/ ~25 extensions
Swiftfox 1.8.0:        18 seconds w/ extensions
**Swiftfox 1.8:           7  seconds** w/out extensions!!! (Every time!))
Swiftfox AMD64       12 seconds (I have a AMD64 CPU)

RENDERING TEST:
[http://scragz.com/tech/mozilla/test-rendering-time](http://scragz.com/tech/mozilla/test-rendering-time) (average of a few reloads)
Epiphany:                3.25 !!! (surprising given it wins handily in the above tests)
Konqueror:              3.25  
Firefox:                  1.94
Swiftfox 1.5.0.1:     1.62 w/out extensions; 1.72 sec. w/ ~25 extensions
Swiftfox 1.8.0:        1.73
**Swiftfox 1.8:           1.72**
Swiftfox AMD64        2.0  (I have a AMD64 CPU)


Firefox=1.5.0.1 Mozilla tarball that was installed using Ubuntuforums instructions.

Swiftfox 1.8.0=Firefox 1.5.0.2 branch
Swiftfox 1.8=Firefox 2 branch (no extensions.  plugins installed.)

All pipelining tweaks in about:config done for firefox and swiftfox.
all plugins and extensions enabled and identical for firefox and swiftfox.

RESULTS:
-Swiftfox wins on the multiple speed test.

-All Firefox/Swiftfox versions perform equally on the rendering test.

-Swiftfox 1.8 (Firefox 2) clobbers all contenders by a very wide margin on the multiple speed test.  

-All other Swiftfox versions perform on par with one another and consistently beat Firefox by a noticeable margin.

-the difference between testing with extensions and without is significant!  It's the difference between 10 seconds and 7 seconds on Swiftfox 1.5.0.1!!!  This is mostly because of Test 2 where 8 red graphics boxes pop up and then are closed.  With extensions, the amount of time it takes to complete increases dramatically.

CONCLUSION:
Swiftfox beats Firefox
Swiftfox 1.8 (Firefox 2) beats all other Swiftfox versions, which perform equally.
Epiphany all over the place; I'll leave epiphany tests to the epiphany fanboys.

WINNER:
Swiftfox 1.8 (Firefox 2)

---

### Post by Rory on 2006-03-25
Well, now I need some help.  All my extensions kept working as  I moved from my opt/firefox/ version to Swiftfox 1.5.0.1, 1.5.0.2 but when I started Swiftfox 2 (1.8 branch), it disabled all my extensions.  That's fine as they don't yet work under that branch.  

But, now when I got back to any other version, all my extensions are there but disabled.  

Can anyone help???

Thx,
Rory

---

### Post by pgmario on 2006-03-25
Tools>Extensions
Right-Click on the disabled extensions and select "enable".

I created a new profile when I tested the trunk build. To do that, start Firefox or Swiftfox with the "-ProfileManager" option.

---

### Post by Rory on 2006-03-25
Many thanks!!!  Yes, it was as simple as just right-clicking on each extension (and theme, by the way), selecting Enable and restarting browser.  Plus, once enabled, it reverted to all your default themes, homepage, etc.  

Thanks very much!!  

Would be great of the initial poster of this thread could update his first post with this warning/tip.

Thanks again!
R.

---

### Post by pgmario on 2006-03-25
You're welcome. Well, I am the initial poster and there has been a warning since day 1 of this thread (after the word "attention" in bold letters ;) ). But I will add the tip on how to re-enable the extensions.

---

### Post by pgmario on 2006-03-25
And, by the way, thanks a lot for this comprehensive speed test! I had tested the trunk build but will now give the 1.8. build a try, too.
One suggestion though: I think the speed improvements are indeed influenced by the number of extensions, so to be even more precise 1.5.0.1 would have to be retested with all extensions disabled.

---

### Post by YorYor on 2006-03-25
Excellent stuff! My laptop's a miserly AMD 1.2GHz, but now it finally feels as good as it did on Windows (in terms of speed of course)! Thanks pgmario!

Now I will be tesing it to see if it hangs/crashes like the old Firefox does...

---

### Post by bradlis7 on 2006-03-25
[QUOTE=Rory]RENDERING TEST:
[http://scragz.com/tech/mozilla/test-rendering-time](http://scragz.com/tech/mozilla/test-rendering-time) (average of a few reloads)
Epiphany:             3.25 !!! (surprising given it wins handily in the above tests)
Firefox:               1.94
Swiftfox 1.5.0.1:  1.62 (updated)
Swiftfox 1.8.0:     1.73
Swiftfox 1.8:        1.72[/QUOTE]

Wow, I just loaded this page up on windows, and it was 6 seconds. Maybe my internet is slower, or I have a different configuration.

---

### Post by pgmario on 2006-03-26
[quote=bradlis7]Wow, I just loaded this page up on windows, and it was 6 seconds. Maybe my internet is slower, or I have a different configuration.[/quote]It's different for everyone. Depends on your computer, bandwidth, number of extensions, how long the browser has been running, etc.

---

### Post by Rory on 2006-03-26
[QUOTE=pgmario]I think the speed improvements are indeed influenced by the number of extensions, so to be even more precise 1.5.0.1 would have to be retested with all extensions disabled.[/QUOTE]

I agree.  I believe my updated scores reflected that, by accident.  Swiftfox 1.5.0.1 shaved about 2 seconds on the Multiple Speed Test and dropped from 1.72 to 1.62 on the Rendering test when I had the extensions disabled.  It's not popped back up to the original numbers with my extensions enabled.  I can't be positive that's what it is, but I think you teased it out.  I probably have about 25 extensions installed.  

It's the Swiftfox (Firefox 2 beta) Multiple Speed Test that impressed me.  I should have also done some tests against Konqueror, as I've always found it to be a very snappy browser compared with Firefox or any others.  But, when I tried I was having pop-up blocker problems.  

At the end of the day, this brings home to me the value of a light, fast browser as the tests clearly demonstrate that a fast computer on paper is not as great of value of the browser you're using holds your hardware back.  

R.

---

### Post by pgmario on 2006-03-26
Nice work with the updated values. I linked to your post from the first page.

---

### Post by Rory on 2006-03-26
I've updated the test explanation a bit.  I also added Konqueror for the rendering test.  I'd like to do Konqueror for the Multiple Speed test but I can't figure out how to disable the pop-up blocker in Konqeuror.  Doh!  If anyone knows, let me know. :)

Thx,
R.

---

### Post by SkimWear on 2006-03-27
WOW! its a HUGE difference from regular firefox. I was thinking it wasn't going to do anything. I loaded it on and I've nearly tripled my speeds. I know hit 3.0-4.5 secs loading the test page where I used to hit 9.0secs++ loading that page.

This topic deserves a Sticky.

---

### Post by MihaiM on 2006-03-28
./run-mozilla.sh: line 131:  8858 Illegal instruction     "$prog" ${1+"$@"}

Uninstalled firefox from Synaptic but it didn't help. Just lost my icons.

---

### Post by pgmario on 2006-03-28
[quote=MihaiM]./run-mozilla.sh: line 131:  8858 Illegal instruction     "$prog" ${1+"$@"}

Uninstalled firefox from Synaptic but it didn't help. Just lost my icons.[/quote]
As we mentioned before: DO NOT REMOVE THE UBUNTU VERSION OF FIREFOX!
Many things in the system depend on the firefox package!
Did your error occur after you tried to run "run-mozilla.sh" or "firefox"? You are not supposed to run "run-mozilla.sh".

---

### Post by MihaiM on 2006-03-28
Did ./firefox in the swiftfox folder

---

### Post by pgmario on 2006-03-29
[quote=MihaiM]Did ./firefox in the swiftfox folder[/quote]Sorry I don't know what's wrong. If you tried to start one of the newer branch or trunk builds, I would suggest trying the 1.5.0.1 build. Other than that, I can't help you, sorry.

---

### Post by Stirling on 2006-03-30
[QUOTE=MihaiM]./run-mozilla.sh: line 131:  8858 Illegal instruction     "$prog" ${1+"$@"}

Uninstalled firefox from Synaptic but it didn't help. Just lost my icons.[/QUOTE]
What processor do you have?

---

### Post by dcstar on 2006-03-30
[QUOTE=Rory]Benchmark results on Ubuntu Breezy 32 bit w/ k7 kernel installed and ati drivers installed.
Athlon XP 3000+ 64 / 512mb RAM / ATI 9200SE / K8V SE Deluxe


MULTIPLE SPEED TEST: (for lack of a better title)
[http://www.24fun.com/downloadcenter/benchjs/benchjs.html](http://www.24fun.com/downloadcenter/benchjs/benchjs.html)  (Final Results)
Epiphany:               12.5 seconds
Firefox:                  19 seconds (updated)
Swiftfox 1.5.0.1:     16 seconds  w/out extensions 18 sec. w/ ~25 extensions
Swiftfox 1.8.0:        18 seconds
Swiftfox 1.8:           7  seconds!!! (Every time!))
.......[/QUOTE]
Just out of interest, my XP-2500+ / 768mb / Via Unichrome (with direct rendering working) / Breezy K7 does ~10.25 seconds on multiple runs with Swiftfox 1.5.0.1

I would have thought your setup would beat this?

---

### Post by pgmario on 2006-03-30
[quote=dcstar]Just out of interest, my XP-2500+ / 768mb / Via Unichrome (with direct rendering working) / Breezy K7 does ~10.25 seconds on multiple runs with Swiftfox 1.5.0.1

I would have thought your setup would beat this?[/quote]Maybe it's because he has an AMD64, and only the trunk build is *really* optimized for 64?

---

### Post by VCSkier on 2006-03-30
does anyone know of or use an optimized version of firefox for intel processors (a pentium m, specifically).  i looked around on the mozilla unofficial build forum, but didn't see any that looked good.  anyone have any recommendations?

---

### Post by pgmario on 2006-03-30
[quote=VCSkier]does anyone know of or use an optimized version of firefox for intel processors (a pentium m, specifically).  i looked around on the mozilla unofficial build forum, but didn't see any that looked good.  anyone have any recommendations?[/quote]This site is not up-to-date, but you might find something there: [http://pryan.org/mozilla/firefox/]("http://pryan.org/mozilla/firefox/")
Since I don't have a pentium processor, I can't give you any advice on how good these builds are.

---

### Post by MihaiM on 2006-03-30
Athlon 1000MHz @ 1200

---

### Post by Stirling on 2006-03-30
[QUOTE=MihaiM]Athlon 1000MHz @ 1200[/QUOTE]
Does that processor have SSE support?

---

### Post by Rory on 2006-04-01
[QUOTE=pgmario]Maybe it's because he has an AMD64, and only the trunk build is *really* optimized for 64?[/QUOTE]

Yes, I would have thought my set-up would have cranked it a bit faster, too.  Not sure why.  So many variables.  

But, I assumed that the AMD64 version would only work on a 64bit OS.  I have a 64 CPU but run 32bit OS.  

Anyone know?

Q.

---

### Post by Rory on 2006-04-01
Okay, I just tried the AMD64 trunk version and added it to my results post.  It's a little worse on the Rendering at 2 seconds but much better on the multiple page test at 12 seconds.  Hmm...

---

### Post by Rory on 2006-04-01
I just figured it out with a bit more testing and did a significant update to the test results post.  

Basically, Swiftfox 1.5.0.1 does around 1.6-1.7 on the Rendering test.  But, on the Multiple Speed Test without extensions I got 10 seconds consistently, like the other poster.  But, when I enabled all 25 extensions, it brought it up to 17 seconds!!!  A signficant increase.

But, I noticed that most of the time increase is a result of Test 2 where 8 red boxes pop up and then close.  If I brought that number in to line on the with and without extensions tests, I'd end up with similar results.  

The good news is that the later builds of Swiftbox really improve on this one test.  So, there's hope yet.  

Rory

---

### Post by Stirling on 2006-04-02
There are now some Intel builds available and also one for the AMD K6-2 if anyone has a really old AMD box.

---

### Post by pgmario on 2006-04-02
[quote=Stirling]There are now some Intel builds available and also one for the AMD K6-2 if anyone has a really old AMD box.[/quote]Good to know, I added it to the first post.

---

### Post by VCSkier on 2006-04-04
[QUOTE=Stirling]There are now some Intel builds available and also one for the AMD K6-2 if anyone has a really old AMD box.[/QUOTE]
excellent.  it certainly is faster in the quick tests i ran.  when i get out of class, i'll post my actual test times.  thanks!

---

### Post by zero0w on 2006-04-15
Swiftfox 1.5.0.2 has come out right after Firefox 1.5.0.2. :)

The XForms extension has upgraded from 0.3 to 0.4, and of course all the bug fixes accompanied with Firefox 1.5.0.2.

In addition, Swiftfox 1.5.0.2 has also changed the name of the execute script/binary due to problems [reported in another thread](http://ubuntuforums.org/showthread.php?t=153969):

firefox -> swiftfox
firefox-bin -> swiftfox-bin

With this in mind you can feel free to upgrade now.

---

### Post by Stefan_hb on 2006-04-15
Thank you very much for this HOWTO, it really seems to have speed up my browser.
How can I make "swiftfox" the default browser for gnome, so it will open links from Thunderbird, etc.?

---

### Post by SomeoneWhoIsntMe on 2006-04-15
No 64-bit :(

---

### Post by babelfishi on 2006-04-15
Hmm. I'm having some troubles...
What I did:
- Download, Extract, Put in home folder
- Created a link of swiftfox 
```
sudo ln -s ~/swiftfox/swiftfox /usr/local/bin/swiftfox
```

When Swiftfox starts, it prompted as default browser. I clicked yes, and errors came up in the command prompt:
```

(Gecko:10460): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

```

And it seems that it does not change Swiftfox as default browser. 

If I run swiftfox from root:
```

---@ubuntu:~/swiftfox$ sudo swiftfox

(Gecko:10656): libgnomevfs-WARNING **: Could not create per-user Gnome application-registry directory: /root/.gnome/application-info

(Gecko:10656): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

```

Anyone help here?

---

### Post by dcstar on 2006-04-15
[QUOTE=Stefan_hb]Thank you very much for this HOWTO, it really seems to have speed up my browser.
How can I make "swiftfox" the default browser for gnome, so it will open links from Thunderbird, etc.?[/QUOTE]
One simple way is to replace the original /usr/bin/firefox shortcut that points to your "old" Firefox with a shortcut that points to the new Swiftfox equivalent (where-ever you installed it).

You can go through and edit all the various individual setting that use this shortcut, but it may be simpler to just change one place.

---

### Post by dcstar on 2006-04-15
[QUOTE=babelfishi]Hmm. I'm having some troubles...
What I did:
- Download, Extract, Put in home folder
- Created a link of swiftfox 
```
sudo ln -s ~/swiftfox/swiftfox /usr/local/bin/swiftfox
```
........
Anyone help here?[/QUOTE]
Better to copy (or move) as root the package to that directory, as I'd say having the correct permissions (not user ones) is important for a global app to run correctly.

I'm not sure links to a user's directory space will be good enough.

---

### Post by dcstar on 2006-04-15
Swiftfox 1.5.0.2 is now available, but you have to download it and extract the files over you existing 1.5.0.1 Swiftfox install (with Swiftfox closed!).

I did that and it started up ok 100% with the new version.

---

### Post by Stirling on 2006-04-16
[QUOTE=babelfishi]Hmm. I'm having some troubles...
What I did:
- Download, Extract, Put in home folder
- Created a link of swiftfox 
```
sudo ln -s ~/swiftfox/swiftfox /usr/local/bin/swiftfox
```

When Swiftfox starts, it prompted as default browser. I clicked yes, and errors came up in the command prompt:
```

(Gecko:10460): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

```

And it seems that it does not change Swiftfox as default browser. 

If I run swiftfox from root:
```

---@ubuntu:~/swiftfox$ sudo swiftfox

(Gecko:10656): libgnomevfs-WARNING **: Could not create per-user Gnome application-registry directory: /root/.gnome/application-info

(Gecko:10656): libgnomevfs-WARNING **: Deprecated function.  User modifications to the MIME database are no longer supported.

```

Anyone help here?[/QUOTE]
This appears to affect the official Firefox build also.  See [Bug 294375](https://bugzilla.mozilla.org/show_bug.cgi?id=294375) which depends on the resolution of [Bug 273524](https://bugzilla.mozilla.org/show_bug.cgi?id=273524).

---

### Post by Ensnared on 2006-04-16
I just tried this out as I'm using the official Firefox build normally. The rendering on the test-page from the first post was 4.19 seconds with Swiftfox, 4.52 seconds with regular Firefox. That's on an Intel P4 portable computer.

Several of my extensions did not work (like NoScript, which I rely heavily on), so I'll stick with the regular build instead - I can pretty much afford those extra 0.33 seconds of rendering time ;) I'll try the Athlon build when I get back to my main workstation though, maybe that's a better improvement. But if extensions aren't 100% compatible (and there really is no reason why they shouldn't be), then it's too much hassle for my preference.

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=Ensnared]I just tried this out as I'm using the official Firefox build normally. The rendering on the test-page from the first post was 4.19 seconds with Swiftfox, 4.52 seconds with regular Firefox. That's on an Intel P4 portable computer.

Several of my extensions did not work (like NoScript, which I rely heavily on), so I'll stick with the regular build instead - I can pretty much afford those extra 0.33 seconds of rendering time ;) I'll try the Athlon build when I get back to my main workstation though, maybe that's a better improvement. But if extensions aren't 100% compatible (and there really is no reason why they shouldn't be), then it's too much hassle for my preference.[/QUOTE]
Try using the build for Intel Pentium computers ;) Also use the 1.5.0.2 build. Not the trunk builds.

---

### Post by Ensnared on 2006-04-16
[QUOTE=MasterChief1234]Try using the build for Intel Pentium computers ;) Also use the 1.5.0.2 build. Not the trunk builds.[/QUOTE]Yes, I pretty much figured that out before I tried anything :p Wouldn't do much good to install an AMD-optimised build on an Intel system, obviously ;) But yes, those were the ones I tried, and the difference really was quite insignificant in my case.

---

### Post by Rob2687 on 2006-04-17
~2 seconds faster on my P4 :D

Now when are they gonna have an Intel SSE only version...my P3 could really use an optimized build like this...

---

### Post by Stirling on 2006-04-17
[QUOTE=Rob2687]~2 seconds faster on my P4 :D

Now when are they gonna have an Intel SSE only version...my P3 could really use an optimized build like this...[/QUOTE]
There is now a build available for Pentium 3.

---

### Post by bigbirdsam_malaysia on 2006-04-18
[QUOTE=Stirling]This appears to affect the official Firefox build also.  See [Bug 294375](https://bugzilla.mozilla.org/show_bug.cgi?id=294375) which depends on the resolution of [Bug 273524](https://bugzilla.mozilla.org/show_bug.cgi?id=273524).[/QUOTE]

Hi ! I had the "Default Browser" problem too, what I did:

1. Make a link in swiftfox directory to "firefox".
---> ln -s /opt/swiftfox/swiftfox /opt/swiftfox/firefox
(where /opt/swiftfox is my install directory)

I found that when we select "Set default..." in version 1.5.0.2, the program will set the default browser to "/opt/swiftfox/firefox %s" and which firefox does not exist! So, just make a link.

Hope this will help.

---

### Post by Ensnared on 2006-04-18
Tried this on my Athlon XP workstation now, and it does feel a bit faster, but the numbers aren't as good as I'd hoped.

I did some quick and dirty testing loading the test-site ([http://scragz.com/tech/mozilla/test-rendering-time](http://scragz.com/tech/mozilla/test-rendering-time)) with both Firefox and Swiftfox, and with two different kernels. This is on an AMD Athlon XP 2600+ with 1GB RAM, and the testing was done by simply reloading the page 5 times.
```
Firefox + stock Dapper 2.6.15-20-k7 kernel:
16.92
12.48
16.21
 8.65
 8.04
Average: 12.46 seconds
```
```
Swiftfox + stock Dapper 2.6.15-20-k7 kernel:
13.5
 5.78
 5.02
 4.78
11.64
Average: 8.14 seconds
```
```
Firefox + optimised Athlon 2.6.16-ck6 kernel:
19.33
 7.71
 8.89
 8.42
16.16
Average: 12.10 seconds
```
```
Swiftfox +  optimised Athlon 2.6.16-ck6 kernel:
 6.67
16.46
 5.66
 5.06
12.71
Average: 9.31 seconds
```

Obviously one would have to do a lot more than 5 tests to get a more accurate number since the variations on each sample are so huge, but atleast these are some cold numbers on the subject. So it does seem it is indeed faster, but it's strange that running an optimised kernel doesn't have a bigger impact on it.

As for my extentions, it seems like NoScript has some issues with the 1.5.0.2 version of both Firefox and Swiftfox, so that turned out to not be compatibility issue after all ;)

---

### Post by Stirling on 2006-04-18
[QUOTE=bigbirdsam_malaysia]Hi ! I had the "Default Browser" problem too, what I did:

1. Make a link in swiftfox directory to "firefox".
---> ln -s /opt/swiftfox/swiftfox /opt/swiftfox/firefox
(where /opt/swiftfox is my install directory)

I found that when we select "Set default..." in version 1.5.0.2, the program will set the default browser to "/opt/swiftfox/firefox %s" and which firefox does not exist! So, just make a link.

Hope this will help.[/QUOTE]
Seems like you would run into [this bug](http://ubuntuforums.org/showthread.php?t=153969) only in reverse this time.  I assume you didn't though?

---

### Post by Aramis on 2006-04-25
[QUOTE=pgmario]
If you have a **starter on your desktop or taskbar** for Firefox and want to make it start Swiftfox:[LIST=1]
[*]right-click on the starter icon
[*]choose "properties"
[*]change the command to ```
/path/to/your/homefolder/swiftfox/firefox
```[/LIST]**Attention:** If you use one of the branch or trunk builds instead of that of the recent release (1.5.0.1), *some of your extensions might not work*. 
To re-enable them after you have switched back to 1.5.0.1 go to Tools>Extensions, right-click on the disabled extensions and select "enable".
[/QUOTE]

Hi y'all,

Swiftfox is extremely fast on my machine. I also went throught a couple of tweak tutorials, performance are really on the UP. Thanks to all for that ! :KS 

However, the above indications for the launcher do not work. I got permission denied "*can't launch the ICON*" . I am not sure this is the proper translation since the error message is actually in french... I am not trying to start an ICON, am I ?
Furthermore, all extensions work except for those installed directly with Swiftfox. So, can I assume that every time I want a new extension I have to use Firefox and then copy the plugin folder as described in the 1st message of this topic. I have to admit it is a bit of a drag [-( 

I did read the few posts that mention this problem but I am a total n00b in Linux and I have no clue as of what to do to solve it. I mean "change the rights to the folder" is a concept I can understand, however make it happen is another ball game all together (Especially assessing if it is done properly :mrgreen: ).

Cheers,

Ar@mi$

---

### Post by tht00 on 2006-04-26
Sweet.

I'm not finding the overall page loading all that much faster, but the program itself isn't hanging as much (opening tabs, etc).  There is actually very little delay now, where before it was sluggish.

:D

---

### Post by K2712 on 2006-04-26
Hey, I just wanted to say thanks for pointing Swiftfox out.  I installed it and immediately noticed a HUGE difference in speed.  Thanks again.

---

### Post by jms830 on 2006-04-26
for those of you confused about the launcher not working, it should be noted that instead of
/path/to/your/homefolder/swiftfox/**firefox**

the new swiftfox (1.5.0.2) would be
/path/to/your/homefolder/swiftfox/**swiftfox**

so this below is slightly outdated :) 

> 
If you have a starter on your desktop or taskbar for Firefox and want to make it start Swiftfox:

   1. right-click on the starter icon
   2. choose "properties"
   3. change the command to
      Code:

      /path/to/your/homefolder/swiftfox/firefox


---

### Post by VCSkier on 2006-05-01
i said i would post my times a few weeks ago, and never got around to it, but here they are.  i ran each test twice.

[scragz.com]("http://scragz.com/tech/mozilla/test-rendering-time") test:
firefox: 3.52, 4.37
swiftfox: 3.24, 3.05

[BenchJS]("http://www.24fun.com/downloadcenter/benchjs/benchjs.html") test:
firefox: 25.91, 27.47
swiftfox: 22.05, 21.51

very decent speedup for me.  :)

---

### Post by Aramis on 2006-05-06
**@jms830**

thanks for that it works now ! I think the author of this thread should update his opening message accordingly. SwitfFox rocks anyway :mrgreen:

A.

---

### Post by pgmario on 2006-05-06
[quote=Aramis]I think the author of this thread should update his opening message accordingly.[/quote]Done. Sorry for the delay, it still worked for me with the original command.

---

### Post by Aramis on 2006-05-06
[QUOTE=pgmario]Done. Sorry for the delay, it still worked for me with the original command.[/QUOTE]

Hi **Mario**,

I meant no offence by suggesting an update was necessary :wink:. Your comment makes me wonder which version you *still* use. I am running SwiftFox 1.5.0.2. And, Thanks to **jms830** I understand what I was supposed to do in the first place (e.g call the correct _*.sh_ file) - Now, if it still worked for you I suppose you were not running 1.5.0.2 (and above) since the file _firefox.sh_ is not present in the SwiftFox folder.

Gosh it is hard to be a newbie! but I reckon it must be hard for HOWTO authors to keep up (meaning the level of details and information) with the likes me :mrgreen:

Good night !

Ar@mi$

---

### Post by Stirling on 2006-05-06
As of version 1.5.0.3 there are symlinks in the swiftfox folder for firefox and firefox-bin that point to swiftfox and swiftfox-bin, so anyone's links that point to swiftfox/firefox will still work.

---

### Post by pgmario on 2006-05-06
[quote=Aramis]Hi **Mario**,

I meant no offence by suggesting an update was necessary :wink:. Your comment makes me wonder which version you *still* use. I am running SwiftFox 1.5.0.2. And, Thanks to **jms830** I understand what I was supposed to do in the first place (e.g call the correct _*.sh_ file) - Now, if it still worked for you I suppose you were not running 1.5.0.2 (and above) since the file _firefox.sh_ is not present in the SwiftFox folder.

Gosh it is hard to be a newbie! but I reckon it must be hard for HOWTO authors to keep up (meaning the level of details and information) with the likes me :mrgreen:

Good night !

Ar@mi$[/quote]No problem, I don't think it was offending. You're absolutely right to say that the first post needed an update.
I think it still worked for me because I just copied the new files into the old swiftfox folder. So, the firefox file was still present and it even loaded the correct version of Swiftfox (1.5.0.3), and that's why I didn't realize there was a problem in my how-to.

---

### Post by pgmario on 2006-05-06
[quote=Stirling]As of version 1.5.0.3 there are symlinks in the swiftfox folder for firefox and firefox-bin so anyone's links that point to swiftfox/firefox will still work.[/quote]Ok, then that's why it worked for me, I upgraded directly from 1.5.0.1 to 1.5.0.3.

---

### Post by routerstu on 2006-05-07
swiftfox is amazing!

thank you

---

### Post by mips on 2006-05-08
I'm running Kubuntu Dapper which does not come with a firefox install by default & I never installed firefod. I downloaded switfox and extracted it to my home directory, created menu & panel icons. All this works great.

The things that don't work are  Flash & Real which I installed according to the restricted formats wiki.

**How do I get Flash & Realplayer to work ???**

---

### Post by aeroshadow on 2006-05-08
How do Swiftfox's speeds compare to Opera's?

---

### Post by Aramis on 2006-05-09
Hello there,

[QUOTE=aeroshadow]How do Swiftfox's speeds compare to Opera's?[/QUOTE]

I guess the best thing to do is to see for yourself. Unless I am mistaking, some posters talked about a small utility/website :confused: that computes the time it took for a browser to do the job. My guess is that you can repeat the operation for your system/browser and tell us about it :mrgreen:

HTH

Ar@mi$

---

### Post by dcstar on 2006-05-12
[QUOTE=mips]I'm running Kubuntu Dapper which does not come with a firefox install by default & I never installed firefod. I downloaded switfox and extracted it to my home directory, created menu & panel icons. All this works great.

The things that don't work are  Flash & Real which I installed according to the restricted formats wiki.

**How do I get Flash & Realplayer to work ???**[/QUOTE]
Your Swiftfox "Plugins" directory should have links (or the actual files) to the following files in it:

libflashplayer.so
nphelix.so
nphelix.xpt
libflash-mozplugin.so

If you don't, find them on your system and copy/link them to that directory.

---

### Post by mips on 2006-05-12
[QUOTE=dcstar]Your Swiftfox "Plugins" directory should have links (or the actual files) to the following files in it:

libflashplayer.so
nphelix.so
nphelix.xpt
libflash-mozplugin.so

If you don't, find them on your system and copy/link them to that directory.[/QUOTE]

thx, i'll have a look.

---

### Post by yoshiznit123 on 2006-05-12
Hey, great howto :-) One thing though, I don't think it's necessary to use 'sudo' when you link all the plugins into the folder (since it's in your home folder)... other than that, swiftfox is wicked
 :cool: 

Samuel

---

### Post by gulp35 on 2006-05-14
is the swiftfox site not working for anyone else?

---

### Post by Stirling on 2006-05-15
[QUOTE=gulp35]is the swiftfox site not working for anyone else?[/QUOTE]
works for me

---

### Post by zhoux on 2006-05-16
does any one have a similar problem? 
I installed Java Runtime Environment via the respos, and it worked fine with firefox. 
However when i switched to swiftfox, java cannot be detected.

Help

---

### Post by Triton on 2006-05-16
This is what I do:  

I have the firefox installed from the repos and configured with all the plugins
Download swiftfox and copy the files to the firefox dirs in usr/lib/firefox and overwrite the dist firefox files.

It's kinda the junky way to do it but it works for me

---

### Post by mips on 2006-05-17
[QUOTE=dcstar]Your Swiftfox "Plugins" directory should have links (or the actual files) to the following files in it:

libflashplayer.so
nphelix.so
nphelix.xpt
libflash-mozplugin.so

If you don't, find them on your system and copy/link them to that directory.[/QUOTE]

Ok copied all those to my swiftfox plugins folder.

Flash works.

Real still does not work. Does not open anything in the browser. Can download clips and play them with realplayer but have NO sound.

I also need to figure out how to make Swiftfox my default browser so stuff does not open with konqueror when I click a link or something.

---

### Post by zhoux on 2006-05-17
[QUOTE=mips]Ok copied all those to my swiftfox plugins folder.

Flash works.

Real still does not work. Does not open anything in the browser. Can download clips and play them with realplayer but have NO sound.

I also need to figure out how to make Swiftfox my default browser so stuff does not open with konqueror when I click a link or something.[/QUOTE]

Dunno if it would work for Kubuntu, but in Swiftfox, go to Edit => Preferences => General Tab => Click Check Now underneath the default browser, if it asks you if you want to select it as the default, click yes.
That should work...but not so sure

---

### Post by mips on 2006-05-18
[QUOTE=zhoux]Dunno if it would work for Kubuntu, but in Swiftfox, go to Edit => Preferences => General Tab => Click Check Now underneath the default browser, if it asks you if you want to select it as the default, click yes.
That should work...but not so sure[/QUOTE]

That is set. For example, if I click a link in Konversation it opens up Konquerer.

---

### Post by Ensnared on 2006-05-18
[QUOTE=mips]That is set. For example, if I click a link in Konversation it opens up Konquerer.[/QUOTE]
This is because many KDE apps have a tendency of executing "x-www-browser" rather than the actual configured browser.

The x-www-browser is just a pointer to the actual browser, and to change it you do this:```
sudo update-alternatives --config x-www-browser
```...and enter the number for the actual browser you want to use.

---

### Post by Swiss on 2006-05-20
Wow! Firefox: 9s Swiftfox: 3s! Thanks!

---

### Post by Blur-king on 2006-05-21
Hi guys, applied the howtos to speed up Firefox on Swiftfox and I think it makes it even faster, maybe someone can test it....

---

### Post by Lopsicle on 2006-05-21
Wow I just changed my default browser to SwiftFox. thank you pgmario its much faster. :)

---

### Post by Lopsicle on 2006-05-21
ps....didnt put down the speeds because my putter has abit of a complex ;)

---

### Post by Phil_McCrackin on 2006-05-21
Definitely faster! Works great! Thanks!

---

### Post by D!mon on 2006-05-23
WOW! Now my firefox (swiftfox of coz :) ) works as fast as under windows and even faster!!! I was using konqueror before because firefox was too slow, now I can get it back :) Thanks in adavnce:)

---

### Post by padre999 on 2006-06-05
It is definately faster... but all in English...

I have the de-locales installed in mozilla/firefox. But swiftfox doesn't use them. They are also not listed in the extensions.

Is there a (not so difficult) possibility to get locales installed on swiftfox?

---

### Post by JSchwage on 2006-06-06
It's amazing how much quicker and snappier Swiftfox is compared to plain ol' Firefox. This is now my browser of choice for Linux.

I've always been a big user of the Firefox extensions. So having a speed increase and the ability to still use my extensions is a big plus for me. :D

---

### Post by razialx on 2006-06-06
Swiftfox seems to be very fast... however it changed what default fonts are used. I opened Firefox up, but it is now using SwiftFox's settings. What can I do to turn the fonts (size, font etc) back to what they were when I first installed Dapper? Thanks.

---

### Post by th3gh05t on 2006-06-09
Hi, 

I cannot get Swiftfox to play video clips. I have copied over the flashplayer files, but everytime I go to a website, it always says that I need to install additional plug-ins.

Can someone help me out?

Thanks, th3gh05t

---

### Post by CronoDekar on 2006-06-09
Just did the rendering tests in both Opera 9 and Swiftfox to compare, and for Opera I got 3.37.  And in Swiftfox? ... also 3.37.  Nice :)

---

### Post by geearf on 2006-06-12
Any of you has the same problem :

When I open some pages in some tabs, firefox freezes for a little while.
I've tried swiftfox's bon echo, then with no extension, without any Chrome*.css, and without pref.js, it's a bit better but still there...

Any hope on this ?

thanks :)

---

### Post by mehaga on 2006-06-15
I got swiftfox, tested it using a link fond in this thread and it' wasn't any faster than firefox. They're about the same. One time firefox is faster, next time it's swiftfox... Epiphany had similar results. I tested several days ago and forgot the exact results, but if I remember well, opera was about 10-15% faster than any of them.
Now, I just heard of and tried new firefox-based browser called flock. I don't know how fast it is, but it's good. :)

Peace :)

---

### Post by FredB on 2006-06-15
Flock is a "web-2.0" based browser, using del.ic.ious, flickr and other web based services.

---

### Post by moore.bryan on 2006-06-15
a little off topic, but swiftfox continually just closes on me.  i uninstalled *all* extensions/plugins/goodies and it still just randomly closes.  any ideas?

---

### Post by FredB on 2006-06-15
I compared both Firefox 1.5.0.4 (ubuntu version) and Swiftfox 1.5.0.4.

I used [http://scragz.com/tech/mozilla/test-rendering-time.php]("http://scragz.com/tech/mozilla/test-rendering-time.php") in order to have a test. (click on both images to have them in full size)

Firefox 1.5.0.4 : 3.32
[URL=http://www.flickr.com/photo_zoom.gne?id=167693396&size=o"]
[IMG]http://static.flickr.com/56/167693396_d4c6cc9ed8_s.jpg[/IMG][/URL]

Swiftfox 1.5.0.4 : 2.44

[[IMG]http://static.flickr.com/66/167693397_be75bbd458_s.jpg[/IMG]]("http://www.flickr.com/photo_zoom.gne?id=167693397&size=o")

So Swiftfox is around 36% quicker.

The only difference is optimization : -O2 for firefox, -O3 for Swiftfox.

My computer is an intel P4  - 2.6 ghz / 1 gb / Ubuntu Dapper Drake.

I don't think that CPU based code will change something more than 0,2%.

---

### Post by kamil212 on 2006-06-15
nice post, I got to try it out when I get home,
Thanks

---

### Post by FredB on 2006-06-15
[QUOTE=kamil212]nice post, I got to try it out when I get home,
Thanks[/QUOTE]

You're welcome.

I will try with my homemade builds and see if I can get more speed using -O3 instead -Os in my optimization line ;)

---

### Post by th3gh05t on 2006-06-15
[QUOTE=th3gh05t]Hi, 

I cannot get Swiftfox to play video clips. I have copied over the flashplayer files, but everytime I go to a website, it always says that I need to install additional plug-ins.

Can someone help me out?

Thanks, th3gh05t[/QUOTE]


Anyone have this problem too? 

(It happens w/ Firefox as well.)

---

### Post by mehaga on 2006-06-16
[QUOTE=FredB]I compared both Firefox 1.5.0.4 (ubuntu version) and Swiftfox 1.5.0.4.
[http://scragz.com/tech/mozilla/test-rendering-time.php]("http://scragz.com/tech/mozilla/test-rendering-time.php") 

Firefox 1.5.0.4 : 3.32


Swiftfox 1.5.0.4 : 2.44



My computer is an intel P4  - 2.6 ghz / 1 gb / Ubuntu Dapper Drake.

[/QUOTE]

Wow! I get between 7 and 10-11 seconds on Athlon 64 3000 /1 GB with 32bit dapper :sad:

---

### Post by Stirling on 2006-06-16
[QUOTE=vekaz]Wow! I get between 7 and 10-11 seconds on Athlon 64 3000 /1 GB with 32bit dapper :sad:[/QUOTE]
Adblock can significantly slow down some of the benchmark tests.  Especially the benchjs test.  You might try disabling any extensions and then run the benchmark again.

---

### Post by mehaga on 2006-06-16
[QUOTE=Stirling]Adblock can significantly slow down some of the benchmark tests.  Especially the benchjs test.  You might try disabling any extensions and then run the benchmark again.[/QUOTE]

I disabled the few extensions I had installed, stopped popup blocker and stopped anti-phishing. Results are the same. Could someone with similar HW post their results, please?

---

### Post by xeero on 2006-06-16
[QUOTE=moore.bryan]a little off topic, but swiftfox continually just closes on me.  i uninstalled *all* extensions/plugins/goodies and it still just randomly closes.  any ideas?[/QUOTE]

I noticed that Swiftfox vanished on me a couple times the other evening.  haven't used it long enough to compare with Firefox to see if both of them have this problem or just swiftfox...

---

### Post by lotheac on 2006-06-17
[QUOTE=vekaz]Wow! I get between 7 and 10-11 seconds on Athlon 64 3000 /1 GB with 32bit dapper :sad:[/QUOTE]

I got something like that too on Athlon 64 3500+, but the bottleneck was my net connection. The page is like 800kB large so it takes about 8 secs to load for me - got better results by saving it and opening locally (although it probably isn't meant to be done like that seeing it's a php, but well...)

---

### Post by jeffreyvergara.NET on 2006-06-17
I installed swiftfox using automatix and it worked fine... then I tried to install swiftfox plugins but it just hangs, i got this error when i tried "apt-get update"

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
jeffrey@ubuntu:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

it just hang here...

---

### Post by mehaga on 2006-06-17
[QUOTE=lotheac]I got something like that too on Athlon 64 3500+, but the bottleneck was my net connection. The page is like 800kB large so it takes about 8 secs to load for me - got better results by saving it and opening locally (although it probably isn't meant to be done like that seeing it's a php, but well...)[/QUOTE]

Ah, thank you for  your reply, I feel little better now :)

Yes, I got something like 2 sec once with Opera loading the page from cache, I guess...

Anyway, I would lie if I said Swiftfox is any faster then Firefox on my machine. I've been using Flock for the past few days and I think that si going to be my browser until something even better comes out. 

Peace :)

---

### Post by Moldy Jello on 2006-06-18
hey thanks a lot, there are so many things that i am slowly finding out about Linux, Ubuntu in general, and now i can brag about a special firefox for me, its like 3 times faster, i love it

---

### Post by dilidon on 2006-06-19
[QUOTE=th3gh05t]Anyone have this problem too? 
(It happens w/ Firefox as well.)[/QUOTE]
You had a problem of plugins not showing up. I had that problem in the beginning too. I figured it out on my machine. I had the Automatix install the newer Firefox or whatever it installs while I already had the Ubuntu default one in place. So, without really knowing it, I had two Firefoxes in my machine, as they got installed into different locations. And that seemed to cause this. So probably all the plugins were there for the one I never used. Maybe you have a similar situation? So I completely removed anything but the default Ubuntu firefox and all the plugins started working. Before, I could see none of them in the about:plugins screen (maybe just 2 basic ones), although I had installed each and every one of them. After reverting back, all was fine. They all appeared without me doing any extra tweaking.
*After* that I found out about swiftF and installed it (hence, no need for another version of the firefox anyways, I guess) and anything I can do in my swiftfox I can do in my firefox and vice-versa. Swiftfox is quite nice.

---

### Post by Cris987 on 2006-07-04
I can't get my launcher to work. 

Okay, first when I run the "firefox" script inside the "swiftfox" folder using terminal, everything works fine. But when I change the command of my launcher to /home/gilbert/Desktop/Installers:Drivers/swiftfox/swiftfox , the launcher launches a "starting mozilla firefox" window and loads for about 10 seonds before disappearing. Anyone knows what is wrong XD?

---

### Post by pgmario on 2006-07-11
> **Cris987 said:**
> I can't get my launcher to work. 

Okay, first when I run the "firefox" script inside the "swiftfox" folder using terminal, everything works fine. But when I change the command of my launcher to /home/gilbert/Desktop/Installers:Drivers/swiftfox/swiftfox , the launcher launches a "starting mozilla firefox" window and loads for about 10 seonds before disappearing. Anyone knows what is wrong XD?
Can't help you there, sorry. Did you find a solution?

---

### Post by pgmario on 2006-07-11
If anyone wants to localize their Swiftfox, have a look at [this thread](http://ubuntuforums.org/showthread.php?t=212310).

---

### Post by bruenig on 2006-07-11
I use a keyboard shortcut do start my default browser. When I had firefox as default and used the keyboard shortcut, It would load to my homepage. When I use swiftfox, it shows my home directory. Anyone know how to change this and make it load my homepage?

---

### Post by bruenig on 2006-07-11
I figured out a way to get around that. If anyone is interested this site [http://doc.gwos.org/index.php/GnomeKeyboardShortcut](http://doc.gwos.org/index.php/GnomeKeyboardShortcut) tells you how to set shortcuts with your own commands. Set the shortcut with that and it loads the homepage.

---

### Post by Metacarpal on 2006-07-21
> **Cris987 said:**
> I can't get my launcher to work. 

Okay, first when I run the "firefox" script inside the "swiftfox" folder using terminal, everything works fine. But when I change the command of my launcher to /home/gilbert/Desktop/Installers:Drivers/swiftfox/swiftfox , the launcher launches a "starting mozilla firefox" window and loads for about 10 seonds before disappearing. Anyone knows what is wrong XD?

When I installed Swiftfox, my panel launcher for Firefox began loading Swiftfox instead automatically.  The taskbar shows "Starting Mozilla Firefox", but then it's Swiftfox that opens.  Looking at my launcher properties, it shows the command as being firefox %u

Maybe if you point your launcher back to firefox, it'll pull Swiftfox like it does for me.

---

### Post by 0123456789 on 2006-07-27
> **Metacarpal said:**
> When I installed Swiftfox, my panel launcher for Firefox began loading Swiftfox instead automatically.  The taskbar shows "Starting Mozilla Firefox", but then it's Swiftfox that opens.  Looking at my launcher properties, it shows the command as being firefox %u

Maybe if you point your launcher back to firefox, it'll pull Swiftfox like it does for me.

That is because when you launch firefox, it launches /usr/bin/firefox. But  /usr/bin/firefox is symbolic link to /usr/lib/firefox/firefox.  When you install Swiftfox it will change /usr/bin/firefox to point to Swiftfox instead.  If you want firefox to actually point to firefox, change /usr/bin/firefox to point back to /usr/lib/firefox/firefox.

---

### Post by dfego on 2006-07-27
It sped up my Firefox a little bit, but it wasn't worth the downgrade in browsing experience.  All the fonts in the browser were rendered horribly (even basic ones).  I assume this has to do with tweaking to anti-aliasing or something, but either way, I'm back on Firefox.

---

### Post by Stirling on 2006-07-27
> **dfego said:**
> It sped up my Firefox a little bit, but it wasn't worth the downgrade in browsing experience.  All the fonts in the browser were rendered horribly (even basic ones).  I assume this has to do with tweaking to anti-aliasing or something, but either way, I'm back on Firefox.
That is strange.  I notice no font rendering issues at all with Swiftfox.

---

### Post by jsmanness on 2006-07-28
Great thread!  I was wondering how I could add Swiftfox to my panel (by replacing Firefox as the web browser) as well as put it in my applications. 

Thanks,

Jon

Sorry, found what I needed on earlier theads...

---

### Post by Xecuter on 2006-07-30
Swiftfox, Firefox and Epiphany all uses 12 seconds in rendering that page.

There's got to be something wrong!

---

### Post by dfego on 2006-07-30
> **Xecuter said:**
> Swiftfox, Firefox and Epiphany all uses 12 seconds in rendering that page.

There's got to be something wrong!

Well it would depend on what kind of computer you're running, I suppose.  Is it relatively new, or is it on the older side?

---

### Post by Xecuter on 2006-07-31
> **dfego said:**
> Well it would depend on what kind of computer you're running, I suppose.  Is it relatively new, or is it on the older side?

Heh, well you be the judge: 
AMD Athlon-XP 2000+ @ 1,66 GHz
1024MB Kingston RAM

But the problem is that Swiftfox weren't any faster that Firefox.

---

### Post by jackpipe on 2006-08-02
Phew 19 pages.  Surely there's a way on ubuntu forums to display an entire thread in a single page with minimized headers or something?

Anyway, one question I haven't seen answered - Is this thing safe?

I mean I use my browser to get at my online bank accounts, etc etc, and I really don't want some nefarious piece of software slowly uploading all my passwords to somewhere in indonesia.

The getswiftfox.com domain seems to be hiding behind an anonymous domain name service, which doesn't do much to ease my worries.

Anyone know more about the author(s) ?

---

### Post by Stirling on 2006-08-02
> **jackpipe said:**
> Phew 19 pages.  Surely there's a way on ubuntu forums to display an entire thread in a single page with minimized headers or something?

Anyway, one question I haven't seen answered - Is this thing safe?

I mean I use my browser to get at my online bank accounts, etc etc, and I really don't want some nefarious piece of software slowly uploading all my passwords to somewhere in indonesia.

The getswiftfox.com domain seems to be hiding behind an anonymous domain name service, which doesn't do much to ease my worries.

Anyone know more about the author(s) ?
I can say with complete certainty that Swiftfox doesn't steal passwords or do any other type of nefarious activities.  So basically you are as safe using it as you are using the official Firefox. :)

---

### Post by Stirling on 2006-08-03
[Swiftfox 1.5.0.6]("http://getswiftfox.com/") is now available.

---

### Post by Stirling on 2006-08-07
Swiftfox is now available as deb files for Ubuntu.  

[http://getswiftfox.com/ubuntu.htm](http://getswiftfox.com/ubuntu.htm)

---

### Post by Darrious on 2006-08-07
When I try to install the .deb package the output is this. ```
root@linux:/home/linux/Desktop# dpkg -i  swiftfox_1.5.0.6-1ubuntu_pentium4.deb
dpkg: error processing swiftfox_1.5.0.6-1ubuntu_pentium4.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 swiftfox_1.5.0.6-1ubuntu_pentium4.deb
root@linux:/home/linux/Desktop#

```

---

### Post by Stirling on 2006-08-07
I just uploaded all the debs again.  Please download the build once more and let me know if that works correctly.

---

### Post by Darrious on 2006-08-07
Now it builded correctly. I don't see any changes with the browser. I turned it off then back on, but still nothing

---

### Post by Stirling on 2006-08-07
> **Darrious said:**
> Now it builded correctly. I don't see any changes with the browser. I turned it off then back on, but still nothing
I don't want to seem dense but what does this mean?  :?:

---

### Post by Oppi on 2006-08-08
[FONT="Tahoma"][SIZE="2"]Hi,

just wanted to install swiftfox: 
downlaoded the .deb package (swiftfox_ 1.5.0.6-1ubuntu_pentium4.deb) 

then installed it with the gdebi  - all went fine. no errors

but there is no change, no swiftfox folder in my home directory or elsewhere.

tried to install in terminal (sudo dpkg -i swiftfox...) - all went fine  - but still no swiftfox folder or files anywhere.

where do i have to look? what do i have to do ? 

greets, Oppi    


Edit: Got it going somehow now with another tutorial ([http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox) ). Only thing that does not work for now, that german language is not supported by the newest version. Maybe soon.
[/SIZE][/FONT]

---

### Post by Darrious on 2006-08-08
> **Stirling said:**
> I don't want to seem dense but what does this mean?  :?:

I see no changes to the speed of the browser, and there is nothing that seems any different. I think that the look is supposed to be the same, but there is no difference in the speed of it. Is there something I'm doing wrong?

---

### Post by Kilz on 2006-08-08
Swiftfox is a project that perverts FOSS. It takes the sources from Firefox, compiles them. Uses the MPL to change the binaries to a non foss license and restrict others from redistributing it. But dosnt comply with section 3 of the MPL that requires the source be made avaiable by the same means as the binaries. Its like the TIVO of browsers.

---

### Post by Chareos on 2006-08-19
still, I didn't understand if it updates automatically (like firefox) or not...

---

### Post by MintabiePete on 2006-09-01
1

---

### Post by stampit on 2006-09-01
this is awesome. thanks.

---

### Post by pgmario on 2006-09-20
> **Chareos said:**
> still, I didn't understand if it updates automatically (like firefox) or not...
It doesn't update automatically here.

---

### Post by Wangsta on 2006-10-07
sorry for being a total n00b, but i have an old laptop without any of the instructions/manuals.
i have no idea what processor my is, but i do know my laptop is a Toshiba satellite with a MK6015MAP hard drive. how would i find out what processor it uses??

---

### Post by handy on 2006-10-07
Search [here]("http://www.isd.toshiba.com.au/71/live.dll/topic/content/driver_search.jsp?BV_SessionID=@@@@0729812599.1160273069@@@@&BV_EngineID=ccceaddimlhkfddcefecekfdffhdfgi.0&MODE=NPRO&CATOID=-15058") & you should find what you need, if not email Toshiba.

---

### Post by K.Mandla on 2006-10-07
> **Wangsta said:**
> how would i find out what processor it uses??
Short of searching Google for the model number, you could try ...

```
cat /proc/cpuinfo | grep model
```
That should spit out a line that identifies the processor for you.

---

### Post by Wangsta on 2006-10-08
wow, what an easy way to get it.
thats awesome, thanks!

---

### Post by sktfeelsdapper on 2006-10-12
So does this only work if you have the other firefox open?

---

### Post by TheRingmaster on 2006-10-15
> **GoA said:**
> How much faster it was? I'm currently downloading it to test it out, first run on normal firefox: 5.5 second: 6.4 third: 6.7.

EDIT: Swiftfox

First: 2.5
Second 3.24
Third 3.39.

That's about two times faster. Holy*.

And in normal usage it's also a lot faster than Dappers default firefox. Thanks for the tip. :)
yah but compare that with opera

---

### Post by dbenhur on 2006-10-24
OK, so how long do we need to wait for 2.0 versions of swiftfox?

---

### Post by ciscosurfer on 2006-10-24
You can grab it now > [http://getswiftfox.com](http://getswiftfox.com) > Swiftfox 2.0pre or later

---

### Post by Stirling on 2006-10-25
> **dbenhur said:**
> OK, so how long do we need to wait for 2.0 versions of swiftfox?
Swiftfox 2.0 builds are now available.

---

### Post by peterj on 2006-11-09
They've added an installer now as well, ran like a peach for me in edgy.

[http://www.getswiftfox.com/installer.htm](http://www.getswiftfox.com/installer.htm)

Great stuff thanks!

---

### Post by ashrack on 2006-11-12
Too all who would like SWIFTFOX 1.5.0.8 to be released please read this:
[http://ubuntuforums.org/showthread.php?t=298253](http://ubuntuforums.org/showthread.php?t=298253)

---

### Post by ashrack on 2006-11-12
Too all who would like SWIFTFOX 1.5.0.8 to be released please read this:
[http://ubuntuforums.org/showthread.php?t=298253](http://ubuntuforums.org/showthread.php?t=298253)

---

### Post by dotsi on 2006-11-12
Swiftfox can now be installed directly from a repository: [http://blogs.getswiftfox.com/?p=27](http://blogs.getswiftfox.com/?p=27)

---

### Post by TheRingmaster on 2006-11-12
> **dotsi said:**
> Swiftfox can now be installed directly from a repository: [http://blogs.getswiftfox.com/?p=27](http://blogs.getswiftfox.com/?p=27)
thanks for showing us that!

---

### Post by dcstar on 2006-11-23
For those that just want to add it in:

deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

---

### Post by pgmario on 2006-11-24
I added the repository information to the first post and restructured it a little, adding an overview, etc.

---

### Post by punkybouy on 2006-12-16
Swiftfox is great.  Both Firefox and Mozilla are so slow on my installation of Edgy they are almost unusable and made me think there was a problem on my network.  Both looked they could not resolve DNS names.  Swiftfox wa well, swift and proved there was nothing wrong with my network.

---

### Post by manutdfan2850 on 2006-12-29
nevermind got it..

---

### Post by Ederico on 2007-01-01
Great stuff, I installed it and it delivers what it promotes itself as! Well done to anyone involved. :)

---

### Post by manutdfan2850 on 2007-01-03
how do you uninstall swiftfox? I checked under Add/remove and synaptic and its not there....

---

### Post by teejay17 on 2007-01-03
> **manutdfan2850 said:**
> how do you uninstall swiftfox? I checked under Add/remove and synaptic and its not there....
How did you install it? Was it through Automatix?

---

### Post by gerowen on 2007-01-06
Question, I have an Intel Celeron processor, but I'm not sure which of the packages I should install.  It has a couple of Celerons listed with different packages I should install for each one.  Could you help me out?  It's a 2.2 Ghz Intel Celeron 32 bit processor.  Here's a screenie of my processor info screen.

[http://i2.photobucket.com/albums/y45/dudeman41465/Computer%20Screenshots/processor.jpg](http://i2.photobucket.com/albums/y45/dudeman41465/Computer%20Screenshots/processor.jpg)

---

### Post by Stirling on 2007-01-06
> **marcusdean.adams said:**
> Question, I have an Intel Celeron processor, but I'm not sure which of the packages I should install.  It has a couple of Celerons listed with different packages I should install for each one.  Could you help me out?  It's a 2.2 Ghz Intel Celeron 32 bit processor.  Here's a screenie of my processor info screen.

[http://i2.photobucket.com/albums/y45/dudeman41465/Computer%20Screenshots/processor.jpg](http://i2.photobucket.com/albums/y45/dudeman41465/Computer%20Screenshots/processor.jpg)

Any modern Celeron such as yours should use the build for "Celeron (Willamette, Northwood, Celeron D)"

---

### Post by gerowen on 2007-01-06
Yeah I found out using x86info that mine was a Northwood, and equivalent to a P4, so I used the swiftfox-pentium4 package and it's working fine.

---

### Post by Blario on 2007-01-09
Any ideas as to what version to use for an Athlon 64-bit processor that's using a generic 32-bit kernel?  Would getting the 64bit version of swiftfox be beneficial if my kernel is only 32?

---

### Post by esaym on 2007-01-09
> **dotsi said:**
> Swiftfox can now be installed directly from a repository: [http://blogs.getswiftfox.com/?p=27](http://blogs.getswiftfox.com/?p=27)


Will adding that offer automatic updates?

---

### Post by TheRingmaster on 2007-01-09
> **esaym said:**
> Will adding that offer automatic updates?

yes, when a newer version of swiftfox enters the repository, then you will be asked to update the one you have via the update manager.

---

### Post by esaym on 2007-01-09
> **TheRingmaster said:**
> yes, when a newer version of swiftfox enters the repository, then you will be asked to update the one you have via the update manager.

Thats what I thought.  Great to hear!:mrgreen:

---

### Post by Athanasius on 2007-01-12
Automatix

---

### Post by esaym on 2007-03-23
> **dotsi said:**
> Swiftfox can now be installed directly from a repository: [http://blogs.getswiftfox.com/?p=27](http://blogs.getswiftfox.com/?p=27)


She works great!!

[IMG]http://www.lindsay.ath.cx/pics/aptswiftfox.png[/IMG]

---

### Post by HasratUSA on 2007-03-25
> **Zeroangel said:**
> Is there an option to do this somewhere? Or do you have to compile FF without Pango?

Forgive me for my utter ignorance but what the hell is a Pango? Some kinda alien?

---

### Post by TheRingmaster on 2007-03-25
> **HasratUSA said:**
> Forgive me for my utter ignorance but what the hell is a Pango? Some kinda alien?
It is what renders the text in ubuntu's firefox.

---

### Post by esaym on 2007-03-25
> **TheRingmaster said:**
> It is what renders the text in ubuntu's firefox.


And if your distro is slackware 10.2 don't even bother trying to compile and install it.  It's got millions of dependencies and fixing those deps breaks millions of others.  It's what lead me to ubuntu because I couldn't run FF2.0 back when it was still a beta :KS

---

### Post by liamwithers on 2007-04-05
Hi, I have followed the instructions of installing Swiftfox and it seems to have worked. I then right clicked my FF icon and changed the command to the swiftfox one. It still says Firefox at the end of the page titles though. "Ubuntu Forums - Reply to Topic - Firefox" being the current page title. Is swiftfox installed?

---

### Post by Stirling on 2007-04-06
> **liamwithers said:**
> Hi, I have followed the instructions of installing Swiftfox and it seems to have worked. I then right clicked my FF icon and changed the command to the swiftfox one. It still says Firefox at the end of the page titles though. "Ubuntu Forums - Reply to Topic - Firefox" being the current page title. Is swiftfox installed?
Make sure all existing Firefox windows are closed before launching Swiftfox.

---

### Post by Wiebelhaus on 2007-04-06
I installed via the automatix2 system , i have not noticed any faster performance but it does have all the codecs and plugins needed natively which is nice.

---

### Post by pkarlos_76 on 2007-04-10
This version is in violation of the mozilla licences, please don't trust a build that you are not allowed to see the code for. Also beware that because you can't see the code, you can't hvae a reasonable gurantee that it is spyware/trojan free. This author appears to be engaging in deceptive practices and maliciously promoting this product as a Firefox based product using a name that is quite similar to a intellectually protected name. AOL forced GAIM to change it's name to Pidgin for example. I suspect the Mozilla lawyers may persure cease and desist orders on this individual if he does not comply with the Mozilla licences.

---

### Post by K.Mandla on 2007-04-12
> **pkarlos_76 said:**
> This version is in violation of the mozilla licences, please don't trust a build that you are not allowed to see the code for. Also beware that because you can't see the code, you can't hvae a reasonable gurantee that it is spyware/trojan free. This author appears to be engaging in deceptive practices and maliciously promoting this product as a Firefox based product using a name that is quite similar to a intellectually protected name. AOL forced GAIM to change it's name to Pidgin for example. I suspect the Mozilla lawyers may persure cease and desist orders on this individual if he does not comply with the Mozilla licences.
I think it would be better to discuss this issue [here]("http://http://forums.getswiftfox.com/viewtopic.php?t=202"), rather than on this forum. Licensing issues are for Mozilla and Jason Halme to settle. Rather than suggest the author is implanting spyware or trojans into his software, you could inspect the [source code]("http://www.getswiftfox.com/source.htm") for his patches, and compile your own. Otherwise, it may be worthwhile to review his [redistribution license]("http://www.getswiftfox.com/LICENSE") for the binaries.

---

### Post by Karlgw on 2007-04-16
You should probably look at this link [http://www.getswiftfox.org/](http://www.getswiftfox.org/) as it appears that the author of Swiftfox is not playing fair with the appropriate licenses.

---

### Post by Stirling on 2007-04-17
> **Karlgw said:**
> You should probably look at this link [http://www.getswiftfox.org/](http://www.getswiftfox.org/) as it appears that the author of Swiftfox is not playing fair with the appropriate licenses.
If you have questions about the license issue still please read the comments on the following bug:
[https://bugzilla.mozilla.org/show_bug.cgi?id=367321]("https://bugzilla.mozilla.org/show_bug.cgi?id=367321")

---

### Post by Stirling on 2007-06-02
[Swiftfox 2.0.0.4 is available]("http://getswiftfox.com")

---

### Post by rickycodie on 2007-06-02
i read that firefox is not to be anymore.
i am sad.

---

### Post by TheRingmaster on 2007-06-02
> **rickycodie said:**
> i read that firefox is not to be anymore.
i am sad.
you mean swiftfox, right?

---

### Post by Stirling on 2007-06-03
Swiftfox is alive and well.

---

### Post by ukripper on 2007-06-05
Great Howto, swiftfox is actually 3 times faster on my system than firefox even with widgets enabled. thanks.

---

### Post by zek725 on 2007-06-05
I don't like [ugly Microsoft-like fonts]("http://forums.getswiftfox.com/viewtopic.php?p=561&highlight=font#561"). How do I set it to use Ubuntu's fonts like the default in Firefox?

---

### Post by zek725 on 2007-06-05
I've installed swiftfox-2.0.0.4-pentium3 from a shell script downloaded from [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm) 

How do you uninstall Swiftfox?

repost: [http://forums.getswiftfox.com/viewtopic.php?t=225](http://forums.getswiftfox.com/viewtopic.php?t=225)

---

### Post by ukripper on 2007-06-06
> **zek725 said:**
> I've installed swiftfox-2.0.0.4-pentium3 from a shell script downloaded from [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm) 

How do you uninstall Swiftfox?

repost: [http://forums.getswiftfox.com/viewtopic.php?t=225](http://forums.getswiftfox.com/viewtopic.php?t=225)

```
sudo apt-get remove swiftfox
```

OR

look at [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm) there is uninstaller for you.

***[COLOR="Red"]"There is also an uninstaller available for those that use the installer. "[/COLOR]***

---

### Post by zek725 on 2007-06-06
> **ukripper said:**
> ```
sudo apt-get remove swiftfox
```

OR

look at [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm) there is uninstaller for you.

***[COLOR="Red"]"There is also an uninstaller available for those that use the installer. "[/COLOR]***
thanks! The uninstaller worked!

---

### Post by maestrobwh1 on 2007-06-12
I agree it really kicks but... using the athalon xp version with faterfox.

Issue:  is anyone else not seeing the bar progress on the download manager?  The numbers show up: downloaded and total and the speed per second.  The bar just sits at zero.

---

### Post by ukripper on 2007-06-13
Swiftfox is also included in Automatix2 which installs and link your plugins to firefox on your machine automatically during installation.

---

### Post by maestrobwh1 on 2007-06-13
I actually used Automatix2 first, but that install is not "upgradeable" using apt/synaptic/adept so I added the repository.  At any rate, I left both on my system (the automatix one is in my opt directory).  Smartly, when both installed, they symlinked to my current firefox plugins in my /usr/lib/firefox/plugins (the apt installed swiftfox in the /usr/lib/  has the same setup.  I compared them in krusader just to make sure I wasn't missing anything.  The download manager opens but the blue bar never moves.  Packages download, and the associated numeric information changes as any download progresses.  It is more of an annoyance than an issue... although the bar at the bottom of the browser does the same thing.  Shows no movement as a page loads.

I am using the amd athalon xp build.

In firefox itself, the download manager works fine.

---

### Post by ukripper on 2007-06-14
> **maestrobwh1 said:**
> I actually used Automatix2 first, but that install is not "upgradeable" using apt/synaptic/adept so I added the repository.  At any rate, I left both on my system (the automatix one is in my opt directory).  Smartly, when both installed, they symlinked to my current firefox plugins in my /usr/lib/firefox/plugins (the apt installed swiftfox in the /usr/lib/  has the same setup.  I compared them in krusader just to make sure I wasn't missing anything.  The download manager opens but the blue bar never moves.  Packages download, and the associated numeric information changes as any download progresses.  It is more of an annoyance than an issue... although the bar at the bottom of the browser does the same thing.  Shows no movement as a page loads.

I am using the amd athalon xp build.

In firefox itself, the download manager works fine.

Strange problem, you can replicate that problem by removing swiftfox and follow this guide for reinstalltion. I think it will fix that problem.

---

### Post by maestrobwh1 on 2007-06-14
Actually, I tried this.  And I still get this very minor "bug"  I wonder if it is particular to the build I have, or perhaps it might just be a peculiarity of my setup.  I might try to remove firefox and swiftfox, then reinstall them.  Again, there is nothing wrong with my Firefox browser, except that it is obviously slower than swiftfox.

---

### Post by ukripper on 2007-06-14
> **maestrobwh1 said:**
> Actually, I tried this.  And I still get this very minor "bug"  I wonder if it is particular to the build I have, or perhaps it might just be a peculiarity of my setup.  I might try to remove firefox and swiftfox, then reinstall them.  Again, there is nothing wrong with my Firefox browser, except that it is obviously slower than swiftfox.

Are you using Feisty or Edgy? 

I tried this guide on Edgy worked perfectly. Feisty I am not very sure of, just used Automatix2.

---

### Post by Stirling on 2007-06-14
> **maestrobwh1 said:**
> Actually, I tried this.  And I still get this very minor "bug"  I wonder if it is particular to the build I have, or perhaps it might just be a peculiarity of my setup.  I might try to remove firefox and swiftfox, then reinstall them.  Again, there is nothing wrong with my Firefox browser, except that it is obviously slower than swiftfox.
Are you using the default window manager theme or something else?

---

### Post by maestrobwh1 on 2007-06-14
I do use beryl sometimes, but it happens even when beryl is not loaded (I don't have it autostart, as half the time I had to click the icon anyway)  In other words, this happens in pure **kubuntu feisty**, with the **kubuntu2 default theme that is standard**.  Keep in mind that all things are normal with firefox.  It isn't an issue where I am willing to cause other issues by trying to solve it.  If it is simply to go to adept or synaptic and purge the install and its settings, then reinstall it, I will do that.  I have uninstalled it but I didn't "purge" the install.  

BTW, as I mentioned, both the prior version 2.0.0.3  installed with automatix2 and the repository enabled adept install of 2.0.0.4 do this on the 32 bit athalon xp build. 

I don't think I purged both at the same time and then reinstalled just the one so perhaps the second install from adept is linking to an issue in the 2.0.0.3 version that is in my opt directory.  I'll fiddle with it over the weekend and either way I will post back.

How would I completely remove the automatix2 installed version, as it wasn't an apt driven install from what I can tell? I generally know more than a novice with Linux, but am not sure how to go about it other than to just to delete it's directory in krusader root mode, then it's links in my K menu.  Would there be a hidden directory in my home folder as well.  I am not at my home computer or I would answer that myself.  Talking out loud:-)

Edit - yup, same issue, even after the original installs were "purged."  I even tried the different builds for athalon.  Same issue.

---

### Post by zivagolee on 2007-08-04
Is there a way to make Swiftfox honor custom mime types set in gnome?

Example:

I set KTorrent has my default .torrent handler in gnome, however, Swiftfox only sees gnome-btdownload as the the .torrent handler (that is the system-wide default).

In Firefox, it works just fine but Swiftfox seems to either ignore or not see it.

Thanks!

---

### Post by mitsakos on 2008-02-12
which swiftfox version should i download for an intel quad core cpu

---

### Post by khughitt on 2008-05-20
*Bump*

Anyone? I'm guessing Nocona:

> 
Nocona
This build is recommended for the Intel 64bit chips including the Core 2 Duo.


...but I just wanted to make sure so I don't end up with something slower than the base version.

p.s. don't know if it's been mentioned, but also check out [Swiftweasel]("http://swiftweasel.tuxfamily.org/") if you haven't yet.
Thanks,

---

### Post by PhatKat on 2008-05-21
Err newbie witb buntu but does this work with FF3beta5 on Hardy?

---

### Post by khughitt on 2008-05-22
> **PhatKat said:**
> Err newbie witb buntu but does this work with FF3beta5 on Hardy?

Installing Swiftfox/Swiftweasel won't replace the current version of firefox you have, so you can use both. There are 3.0 versions of each as well, although they may not be as recent as the firefox version you have.

Check out:
[URL="http://getswiftfox.com/deb.htm"]
http://getswiftfox.com/deb.htm[/URL] and
[http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=231607]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=231607")

---

### Post by ChameleonDave on 2008-05-26
Thanks for the tip.

I've installed Swiftfox, and it neatly takes over where Firefox left off, even remembering my cookies.

The only difference that I can see is that Swiftfox takes 5 seconds to start up, instead of 8s.  By way of comparison, Opera takes 6s, Konqueror (KDE 3 or 4) takes 3s, and Epiphany takes 2s.

I went with the "i686" version first, and then tried the "pentium4".  Performance seems the same.

---

### Post by khughitt on 2008-05-27
> **ChameleonDave said:**
> Thanks for the tip.

I've installed Swiftfox, and it neatly takes over where Firefox left off, even remembering my cookies.

The only difference that I can see is that Swiftfox takes 5 seconds to start up, instead of 8s.  By way of comparison, Opera takes 6s, Konqueror (KDE 3 or 4) takes 3s, and Epiphany takes 2s.

I went with the "i686" version first, and then tried the "pentium4".  Performance seems the same.

I noticed a huge difference initially, but have found that with more and more extensions, it becomes slow no matter what. Probably the best thing to do is just to try and minimize the number of extensions (especially the bulky ones) you have installed and enabled.

---

### Post by cityismine on 2010-06-07
> **zivagolee said:**
> Is there a way to make Swiftfox honor custom mime types set in gnome?

Example:

I set KTorrent has my default .torrent handler in gnome, however, Swiftfox only sees gnome-btdownload as the the .torrent handler (that is the system-wide default).

In Firefox, it works just fine but Swiftfox seems to either ignore or not see it.

Thanks!

I'm having the same problem, it will not open movies in smplayer and torrents won't open in deluge. Everything works fine in firefox and chrome. Swiftfox for some reason doesn't honor the default helper applications.

---

### Post by hansum_rahul on 2010-06-12
It is much faster!

I was wondering what about IceWeasel? Is it in the repos?

---

