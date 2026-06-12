---
title: "grdc should replace Vinagre as the default"
date: 2009-07-07
forum: Recurring Discussions
---

### Post by pt123 on 2009-07-07
remote connection application
[http://grdc.sourceforge.net/screenshots.html](http://grdc.sourceforge.net/screenshots.html)

Vinagre is a hopeless, they haven't fixed a major bug which makes it impossible to use.
[https://bugs.launchpad.net/bugs/203782](https://bugs.launchpad.net/bugs/203782)

While GRDC is packed with so many features that it doesn't look embarrassing with Windows VNC clients. It is actively developed too. 

I am not sure how Vinagre made default in the first place.

---

### Post by Joe_Bishop on 2009-07-07
agree, vinagre is too slow, although has slightly better ui

---

### Post by binbash on 2009-07-07
I totally agree with that.Grdc is 10x better than crap Vinagre.

---

### Post by Yes_It's_Me on 2009-07-07
Unlike vinagre, grdc does actually work. But neither like the server to have compiz very much :( Is there any way to get around that?

BTW: I just tried vnc'ing to a host which was vnc'ing back to that same client.

... It didn't work out too well...lol

---

### Post by pferraro on 2009-07-07
The Vinagre developer has been promising RDP support for several releases now, but has yet to deliver it.  It would be great to be able to dump tsclient for good.  A new grdc release was uploaded today - I'll give it a whirl.

---

### Post by xens on 2009-07-07
+1 grdc is great!

a nice feature is SSH tunnelling of VNC connexions

---

### Post by psyke83 on 2009-07-07
I've tested grdc and come to the conclusion that it's vastly superior to tsclient and vinagre in their current incarnations. I've posted a proposal for grdc to be set as the default remote desktop client.

Folks, if you want to see this happen, make your voice heard on the [ ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-July/009024.html").

---

### Post by afv on 2009-07-07
Just installed grdc but&#8230;

> 
grdc: error while loading shared libraries: libvncclient.so.0: cannot open shared object file: No such file or directory


Had to force libvncserver0 version from

> 
Package: libvncserver0
New: yes
State: installed
Automatically installed: yes
Version: **0.9.8.dfsg.3-0ubuntu1~ppa2**
Priority: optional
Section: libs
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 328k
Suggests: libvncserver0-dbg (= 0.9.8.dfsg.3-0ubuntu1~ppa2)
Description: API to write one's own vnc server
 LibVNCServer makes writing a VNC server (or more correctly, a program exporting a framebuffer via the Remote Frame Buffer protocol) easy.  It hides the programmer from the
 tedious task of managing clients and compression schemata.


to

> 
Package: libvncserver0
New: yes
State: installed
Automatically installed: yes
Version: **0.9.3.dfsg.1-1ubuntu2**
Priority: optional
Section: libs
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 397k
Depends: libc6 (>= 2.4), libjpeg62, zlib1g (>= 1:1.1.4)
Suggests: libvncserver0-dbg (= 0.9.3.dfsg.1-1ubuntu2)
Description: API to write one's own vnc server
 LibVNCServer makes writing a VNC server (or more correctly, a program exporting a framebuffer via the Remote Frame Buffer protocol) easy.  It hides the programmer from the
 tedious task of managing clients and compression schemata.


Working now.

---

### Post by graaant on 2009-07-07
I thought gnome-rdp was the best available at the moment, but grdc seems great!
Would love to see this included by default.

---

### Post by psyke83 on 2009-07-07
> Had to force libvncserver0 version from [snip]

That was due to a conflict in a newer version of libvncserver0 you installed from a random PPA. Hardly grdc's fault.

---

### Post by afv on 2009-07-07
> **psyke83 said:**
> > Had to force libvncserver0 version from [snip]

That was due to a conflict in a newer version of libvncserver0 you installed from a random PPA. Hardly grdc's fault.

Yes, I realized that. :)

[img]http://img31.imageshack.us/img31/9662/screenshot4z.png[/img]


By the way, and sorry for the off-topic, is there a way to see from what PPA the packages are?

---

### Post by psyke83 on 2009-07-07
> **afv said:**
> Yes, I realized that. :)

[img]http://img31.imageshack.us/img31/9662/screenshot4z.png[/img]


By the way, and sorry for the off-topic, is there a way to see from what PPA the packages are?

You can check the origin of packages in Synaptic (Origin button on the main interface); I don't know of the command-line equivalent off-hand, sorry.

---

### Post by Johan! on 2009-07-07
In the terminal, you can use "apt-cache policy <package>"

---

### Post by pt123 on 2009-07-07
This is becoming silly as this distribution has gone insane over boot times when you are more like to save the user's time by choosing the best applications. 
Like gdrc over Vinarge.

---

### Post by psyke83 on 2009-07-07
> **Johan! said:**
> In the terminal, you can use "apt-cache policy <package>"

Not the same as seeing the origin of all packages, though.

---

### Post by ktp on 2009-07-07
> **psyke83 said:**
> I've tested grdc and come to the conclusion that it's vastly superior to tsclient and vinagre in their current incarnations. I've filed a proposal for grdc to be set as the default remote desktop client.

Folks, if you want to see this happen, make your voice heard on [bug #396831]("https://bugs.launchpad.net/bugs/396831").

+1

grdc is really fast compared to vinagre.

---

### Post by psyke83 on 2009-07-07
> **pt123 said:**
> This is becoming silly as this distribution has gone insane over boot times when you are more like to save the user's time by choosing the best applications. 
Like gdrc over Vinarge.

Making semi-inflammatory remarks won't sway people's opinions; reasoned arguments will.

Besides, what's wrong with having optimized boot times? ;) We don't all leave our computers turned on 24/7 (and many people use laptops). A cold boot is even faster than resuming from hibernation on my laptop, and at least in my case, hibernating isn't as useful on a dual-booting laptop.

---

### Post by ktp on 2009-07-07
I think there is finally a great single application to replacement vinagre and tsclient.  GDRC is working great (loving the speed) and lets me chose keyboard grabbing.  I can finally get back to having full-screen RDP on one face of the cube.

I have not tested the vnc server part, but if it works as good as client part, this should be default.

---

### Post by 23meg on 2009-07-08
[QUOTE=pt123]I am not sure how Vinagre made default in the first place.[/QUOTE]

[QUOTE=pt123]This is becoming silly as this distribution has gone insane over boot times when you are more like to save the user's time by choosing the best applications. [/QUOTE]

These two statements are conflicting: if you're not sure what the considerations were that led to Vinagre being the default, how can you claim that the situation is "silly"? 

Vinagre came to be the default during the Hardy cycle, around February 2008, replacing xvncviewer4, precisely because it *was* the best application for the task at the time. It appears that GRDC *didn't even exist* then, and in any case, it has only had VNC support since this January, almost a year after that date. 

It may or may not be suitable to replace Vinagre with GRDC at the moment, and I'm not arguing either way, since I have yet to even test the latter and look into its technicalities at any reasonable depth. But be advised that firing away inflammatory comments without demonstrating any awareness of the background of the issues you're commenting on makes it appear as if your main motivation is to make insidious remarks whenever you encounter something you don't like, rather than help improve things.

---

### Post by pt123 on 2009-07-08
> **psyke83 said:**
> Making semi-inflammatory remarks won't sway people's opinions; reasoned arguments will.

Besides, what's wrong with having optimized boot times? ;) We don't all leave our computers turned on 24/7 (and many people use laptops). A cold boot is even faster than resuming from hibernation on my laptop, and at least in my case, hibernating isn't as useful on a dual-booting laptop.

Labelling remarks "inflammatory" won't sway people's opinions; reasoned arguments will.

Most people wouldn't be booting up more than 3 times in a day. Importance should be given to what people are booting into not how long booting takes.

---

### Post by pt123 on 2009-07-08
> **23meg said:**
> These two statements are conflicting: if you're not sure what the considerations were that led to Vinagre being the default, how can you claim that the situation is "silly"? 

Vinagre came to be the default during the Hardy cycle, around February 2008, replacing xvncviewer4, precisely because it *was* the best application for the task at the time. It appears that GRDC *didn't even exist* then, and in any case, it has only had VNC support since this January, almost a year after that date. 

It is not better than xvncviewer4, people still prefer to use it that over this Vinagre. xvncviewer4 is so much faster than Vinagre. Terminal Server Client which used xvncviewer4 was so much better than Vinagre. 
That is why it was **SILLY** Vinagre was made default over xvncviewer4 & Terminal Server Client combination which was in Gutsy.

---

### Post by zekopeko on 2009-07-08
> **psyke83 said:**
> Making semi-inflammatory remarks won't sway people's opinions; reasoned arguments will.


No it won't. Did you miss the entire mono "debate"?

---

### Post by zekopeko on 2009-07-08
> **pt123 said:**
> It is not better than xvncviewer4, people still prefer to use it that over this Vinagre. xvncviewer4 is so much faster than Vinagre. Terminal Server Client which used xvncviewer4 was so much better than Vinagre. 
That is why it was **SILLY** Vinagre was made default over xvncviewer4 & Terminal Server Client combination which was in Gutsy.

when you switch an application you account for regressions. and vinagre is an official part of Gnome. therefore more appealing.
not to mention TSC was/is a usability nightmare (for me).

---

### Post by pt123 on 2009-07-08
> **zekopeko said:**
> No it won't. Did you miss the entire mono "debate"?
maybe you should go and work on why Mono applications are so slow, than following other users on this board.

---

### Post by pt123 on 2009-07-08
> **zekopeko said:**
> when you switch an application you account for regressions. and vinagre is an official part of Gnome. therefore more appealing.
not to mention TSC was/is a usability nightmare (for me).
With that logic we will end up with Epiphany as the default browser. Vinagre is a slow unusable application probably adheres to Gnome's backward HIG.

---

### Post by xebian on 2009-07-08
> **psyke83 said:**
> You can check the origin of packages in Synaptic (Origin button on the main interface); I don't know of the command-line equivalent off-hand, sorry.

Use apt-cache show <package>  or aptitude show <package>

---

### Post by zekopeko on 2009-07-08
> **pt123 said:**
> maybe you should go and work on why Mono applications are so slow, than following other users on this board.

get a faster pc then a 600mhz pentium iii. and who am i following?

---

### Post by pt123 on 2009-07-08
> **zekopeko said:**
> get a faster pc then a 600mhz pentium iii. and how am i following?
maybe you are confused with the AMD model numbers but here have a read
[http://news.softpedia.com/news/AMD-Unveils-Energy-Efficient-Athlon-X2-4850e-Dual-Core-CPU-80170.shtml](http://news.softpedia.com/news/AMD-Unveils-Energy-Efficient-Athlon-X2-4850e-Dual-Core-CPU-80170.shtml)

Wake me up when MS decides to code their Windows Media Player in .Net. 
Somewhere along the line the Mono enthusiasts didn't get the memo from MS that .Net was targeted for Business applications.

---

### Post by zekopeko on 2009-07-08
> **pt123 said:**
> With that logic we will end up with Epiphany as the default browser. Vinagre is a slow unusable application probably adheres to Gnome's backward HIG.

sorry, i should have written **acceptable** regressions.
you certainly won't replace firefox for epiphany. too **many** regressions.

---

### Post by zekopeko on 2009-07-08
> **pt123 said:**
> maybe you are confused with the AMD model numbers but here have a read
[http://news.softpedia.com/news/AMD-Unveils-Energy-Efficient-Athlon-X2-4850e-Dual-Core-CPU-80170.shtml](http://news.softpedia.com/news/AMD-Unveils-Energy-Efficient-Athlon-X2-4850e-Dual-Core-CPU-80170.shtml)

Wake me up when MS decides to code their Windows Media Player in .Net. 

something is very wrong with your computer then. i'm using mono apps on an Asus 1000Hg (1.6Ghz Atom) without slowdowns.

> 
Somewhere along the line the Mono enthusiasts didn't get the memo from MS that .Net was targeted for Business applications.

you did? can i see it?

---

### Post by 23meg on 2009-07-08
> **pt123 said:**
> It is not better than xvncviewer4, people still prefer to use it that over this Vinagre. xvncviewer4 is so much faster than Vinagre. Terminal Server Client which used xvncviewer4 was so much better than Vinagre. 
That is why it was **SILLY** Vinagre was made default over xvncviewer4 & Terminal Server Client combination which was in Gutsy.

xvncviewer didn't let you choose bit depths or adjust any other settings either. And until you provide some technical backing as to why it may be so, "xvncviewer4 is so much faster than Vinagre" amounts to nothing other than anecdotal evidence (even though it might be true). If I said "Vinagre is just as fast as xvncviewer4", it would be just as valid, and by your standards, since and because you won't agree with it, I could call your position **SILLY**. Not very constructive discussion, is it?

You're not going to go very far in changing things with an attitude like this. Discussions like this don't tend to produce any outcome other than making people who fuel them unpopular to the extent that they will be ignored by the exact set of people who are in a position to make what they want happen. 

> **zekopeko said:**
> No it won't. Did you miss the entire mono "debate"?

Please avoid derailing discussions, especially with the magical M-word.

---

### Post by zekopeko on 2009-07-08
> **23meg said:**
> Please avoid derailing discussions, especially with the magical M-word.

Mono-nucleosis? :)

anyway just installed grdc 0.6 and i have to say that it's looking real slick. it allows me to mount my home on a RDP server and various other things.
so at least from a feature perspective it's more feature rich then Vinagre.

On the other hand why not help vinagre? All of this thing could have been implemented in vinagre. It just needs developers.

---

### Post by psyke83 on 2009-07-08
> **zekopeko said:**
> Mono-nucleosis? :)

anyway just installed grdc 0.6 and i have to say that it's looking real slick. it allows me to mount my home on a RDP server and various other things.
so at least from a feature perspective it's more feature rich then Vinagre.

On the other hand why not help vinagre? All of this thing could have been implemented in vinagre. It just needs developers.

If you look at the functionality of vinagre 0.5.1 (in Hardy), and compare it to the latest version in Jaunty, very little has changed. It doesn't support changing bit depths, RDP support has not been added, it has very few connection options and performance is very poor even on a high-bandwidth connection. See the bug mentioned by the original poster and do some testing yourself, and you'll see the performance problem yourself.

Extrapolate from the progress vinagre has made from Hardy to Jaunty, and you'll see that it's quite unlikely to reach feature parity with grdc in time for Karmic's release.

I think that if the author of vinagre is an Ubuntu user, seeing their application demoted from the default application list for Karmic will drive them towards making these essential improvements. In the meantime, end users will have access to a superior remote desktop application (IMHO).

---

### Post by psyke83 on 2009-07-08
> **23meg said:**
> xvncviewer didn't let you choose bit depths or adjust any other settings either. And until you provide some technical backing as to why it may be so, "xvncviewer4 is so much faster than Vinagre" amounts to nothing other than anecdotal evidence (even though it might be true). If I said "Vinagre is just as fast as xvncviewer4", it would be just as valid, and by your standards, since and because you won't agree with it, I could call your position **SILLY**. Not very constructive discussion, is it?

While I agree on virtually every point you made, let me clarify something. The xvncviewer application does (and did) allow you to change basic connection settings such as the encoding and bit rate. Furthermore, when xvncviewer (now renamed to xvnc4viewer) is installed, the tsclient frontend enables VNC support via this executable, so most users would have interacted with xvncviewer via the tsclient interface.

The major issue with xvncviewer is that its has a very basic X11 GUI, and even when you use the tsclient frontend, integration is poor (there is no pulldown toolbar to minimize/maximize or switch from fullscreen, for example).

Vinagre is superior in terms of its interface; where it is lacking is in features and performance.

---

### Post by BwackNinja on 2009-07-09
@pt123

I think you are misinterpreting what 23meg is saying. Talking about the options in xvnc4viewer he may be wrong, however you don't seem to see the significant difference between anecdotal evidence and statistical evidence. It "feels" faster is not a measure of whether or not something works faster; comparing 1 second to 2 seconds to connect for example, is.

And 23meg also wants to **help.** It isn't a popularity contest, but how you present yourself affects how you are received and being received positively can help a change like this occur.

Now I'm off to try grdc for myself :D

---

### Post by zekopeko on 2009-07-09
what grdc needs is a good tango-ish icon.

---

### Post by psyke83 on 2009-07-09
> **BwackNinja said:**
> @pt123

I think you are misinterpreting what 23meg is saying. Talking about the options in xvnc4viewer he may be wrong, however you don't seem to see the significant difference between anecdotal evidence and statistical evidence. It "feels" faster is not a measure of whether or not something works faster; comparing 1 second to 2 seconds to connect for example, is.

And 23meg also wants to **help.** It isn't a popularity contest, but how you present yourself affects how you are received and being received positively can help a change like this occur.

Now I'm off to try grdc for myself :D

I would actually like to know how to demonstrably measure the performance of vinagre vs another application. Even in the bug report, nobody has provided evidence to prove that vinagre is slow, but from real-world use, I completely agree with their conclusions.

Is there a way to measure the video bandwidth efficiency of the VNC implementation? Until I know how to measure it, all I can say is something like "scrolling a page in Firefox over VNC takes about 2 seconds for the screen to update, versus 0.1 seconds for grdc", or something equally vague.

It may have something to do with the encoding algorithm used, but if vinagre is using an older or less efficient algorithm, it shouldn't be using 2x or 3x the amount of CPU compared to other VNC clients.

---

### Post by psyke83 on 2009-07-09
> **zekopeko said:**
> what grdc needs i a good tango-ish icon.

I see very few other "polish" issues (aside perhaps from changing the menu item name) - the interface is already well-designed, and I've encountered no bugs or issues in my testing.

---

### Post by zekopeko on 2009-07-09
> **psyke83 said:**
> I see very few other "polish" issues (aside perhaps from changing the menu item name) - the interface is already well-designed, and I've encountered no bugs or issues in my testing.

the icon is ugly but that could be snatched from vinagre.
and somebody with intimate knowledge of dependencies should look at space issues (if any).
and if all of the depends are in main.

---

### Post by zekopeko on 2009-07-09
BTW can grdc auto resize RDP session to the client's screen resolution?
i always found that one annoying.

---

### Post by ktp on 2009-07-09
> **zekopeko said:**
> BTW can grdc auto resize RDP session to the client's screen resolution?
i always found that one annoying.

grdc defaults to client resolution for RDP.

[http://grdc.sourceforge.net/screenshot2.png](http://grdc.sourceforge.net/screenshot2.png)

It also has nice toolbar with resize and full-screen options once connected.

[http://grdc.sourceforge.net/screenshot5.png](http://grdc.sourceforge.net/screenshot5.png)

I am really loving grdc more and more I use it.

---

### Post by zekopeko on 2009-07-09
> **ktp said:**
> grdc defaults to client resolution for RDP.

[http://grdc.sourceforge.net/screenshot2.png](http://grdc.sourceforge.net/screenshot2.png)

It also has nice toolbar with resize and full-screen options once connected.

[http://grdc.sourceforge.net/screenshot5.png](http://grdc.sourceforge.net/screenshot5.png)

I am really loving grdc more and more I use it.

niceness!!! this is new (used 0.4/5). what i would like is somebody from user experience team check usability and give suggestions.

---

### Post by ktp on 2009-07-10
Anyone seen focus issues with GRDC and full-screen.  I have compiz enabled and have RDP open in full-screen mode on one face of the cube.  If I switch to RDP workspace using the shortcut keys (Ctlr + Shift + Left/Right Arrow), I don't have any issues.  But if I use the Workspace Switcher applet to switch, using the mouse, it seems like there are some issue with keys and activating windows in RDP.  Everything works OK if I min/max RDP session window or switch workspace using shortcut keys.

**This might not be GRDC issue** since I am seeing similar focus problems returning from locked screensaver; typing in firefox address bar, the suggestion list is not shown and have to min/max or switch back to firefox to fix it. Somehow compiz is in play since if I have compiz disabled I don't have these issues.

Edit:
Maybe this is GRDC issue.  It seems like Ctrl is locked and pressed when switching using the Workspace Switcher applet.  If I press Ctrl, then everything is working again.

---

### Post by bapoumba on 2009-07-11
i have moved the thread to the recurring discussions. @ all : Please feel free to open another thread to share experiences and tips on grdc in the support area of the forums, thanks.

---

### Post by FaberfoX on 2009-11-10
This thread's been sleeping for a while and I think it's time to wake it.
My main machine is a decent core2, and I've just started using an old thinkpad T40, a 1.5ghz pentium M.
On my main machine I've been using vinagre, foolishly thinking vnc was this slow even when on the local network, but it was somewhat tolerable.
In this old machine, vinagre is almost unusable, hitting the cpu really hard and keeping running at full speed, while lagging even when moving the pointer. Switching panels hits 100% cpu for about 2 seconds before the screen refreshes.
grdc works like a charm, barely using any cpu, so, what would be the formal procedure to get it into gnome and ubuntu?

---

### Post by pt123 on 2009-11-10
Gnome is corrupt, and you have to wonder about Ubuntu too.

---

### Post by gnomeuser on 2009-11-11
abolutely not grdc is a horrid mess just looking at the amount of configuration users have to do before it can become useful. Here is how it should work:

Select destination in the form of a person on your buddy list or contact registry. Then the telepathy tube over which the connection is negotiated already knows the capacity of the connection and should thus throttle the settings accordingly.

And up pops the remote desktop ready for use in the optimal focused on what the user is actually trying to do.

I believe vinagre is closer and more likely to bring this situation about than grdc ever will be.

---

### Post by 1jackjack on 2009-12-06
+1 for grdc. I've been putting up with an annoying bug in vinagre for over a year: after opening a connection, and minimising the window, then coming back to it, you lose the local mouse, and it's a real pain relying on the remote one; constantly overshooting buttons etc.

Also it may just be my delight in discovering this alternative, but grdc seems snappier all round!

---

### Post by tinahouse on 2009-12-24
GNOME likes to make things as simple as possible, especially recently it seems to remove features more often than adding them. Just some example: network-manager 0.7 removed a key type option which ends up killing my wifi for more than a year, and they only blame the kernel drivers; vino removed the advanced tab, which ends up having to use gconf-editor to edit some useful advanced options.

Well, I am not saying GNOME was wrong; it simply assumes that their users know nothing about computer, not even some basic common sense, so they don't like advanced options. So they are just trying their best to make things simple. While this is really good for programs like a music player, but would you expect a remote desktop program would just work as simple as clicking a "play" button in a music player? Most remote desktop users are very technical system administrators and they do need very advanced options.

So my point is, Vinagre and Remmina (oh by the way grdc now call remmina:) ) are just working towards different (and even opposite) direction and targeting towards different users. Don't expect Vinagre will add many advanced options because it's not the strategy of GNOME; and also don't expect Remmina will enter GNOME because GNOME hates technical things.

But Remmina won't enter GNOME doesn't mean it won't enter Ubuntu. Just take a look at the gnome-desktop-environment package in Lucid, you will see grdc it's there as an optional dependency and should hopefully be soon upgrade to Remmina; which seems to be good move for me.

---

### Post by megamaced on 2010-01-15
Just adding my name to the list of people who'd prefer to see Remmina installed instead of Vinagre and TSclient... Why have 2 remote desktop applications when you can consolidate into 1 - and a much better app at that...

---

### Post by juancarlospaco on 2010-01-15
*Maybe common people doesnt know but...*
RDP is not secure, as FTP is not secure.

I use SSH or FreeNX, 
i think Remote Desktop on Ubuntu should migrate to FreeNX, its GPLed technology,
far away better than VNC, and its secure because its an SSH tunnel.

---

### Post by Neural oD on 2010-03-17
I second Remmina - tsclient has some bugs that still are not fixed - the correct sorting of "Quick Connect" connections are not alpha numerical!!! This bug has been hanging around a looong time! +1 for Remmina!!

&btw RDP might not be "that" secure as say ssh - but some of us need to tunnel into M$ machines!

just my 2c worth

---

### Post by luka83 on 2010-07-04
I second that. We should drop vinagre and replace it with remmina. With ubuntu 10.10 on the way this is a perfect opportunity to get rid of the whole vinagre mess.

The reason that I believe that vinagre should be dropped is:
[LIST]
[*]it uses libgtk-vnc-1.0.0. to connect to other vnc servers. And for me it is only able to connect to other linux machins. (I've really invested way too much time into this installing various versions with the same non working resault) It failed to connect to realvnc server, tightvnc server, and from my reasearch on how to make it work, it seems that it is a big problem to connect to mac as well. Not to mention that vinagre lacks RDP support.
[*]vinagre bugs do not get fixed. It seems that it mostly gets a version bumped, but no features get included or bugs get fixed. And it has some major bugs, like just enter the wrong location and you'll get segmentation fault. Or try to connect to mac/tightvnc/realvnc.
[*]Vinagre has only two nice features - that is tabs and nearby list. But without bugfixing thay are useless. We could help out developers to fix vinagre, or we could just use remmina, since it already works and covers remote connectivity protocols a lot better.
[*]Vinagre is just wrong for default remote connectivity client, because it mostly doesn't work - either it doesn't support remote protocol or it just fails when it shouldn't. And that's a turn off for new users as well as for old once, since user gets a non working installed app that has to be removed/replaced by something that works. - Sure we can use tsclient or remmina or just use cli vncviewer, but how is a new user supposed to deal with that? I don't see why anyone should waste their time with something like vinagre which just doesn't work, while we could have a nice program like remmina by default, which has a nice clean gnomish interface, reach remote protocol support. Simple access to saved clients, lots of feature, simple reverse connections, ... 
[/LIST]

Does anyone know where precisely to make a proposal of a default package for ubuntu 10.10. as I would really like to see vinagre gone and replaced with something that works.

---

### Post by cristianfere on 2010-07-11
> **juancarlospaco said:**
> *Maybe common people doesnt know but...*
RDP is not secure, as FTP is not secure.

I use SSH or FreeNX, 
i think Remote Desktop on Ubuntu should migrate to FreeNX, its GPLed technology,
far away better than VNC, and its secure because its an SSH tunnel.

The new version of remmina 0.8 has native NX support (client).

Remmina is awesome, a don't understand why Vinagre is still default in ubuntu...

Remmina PPA: [https://launchpad.net/~llyzs/+archive/ppa](https://launchpad.net/~llyzs/+archive/ppa)

---

### Post by pt123 on 2010-11-08
yes!!! success

[http://www.omgubuntu.co.uk/2010/11/remmina-to-be-ubuntus-new-remote-desktop-app/](http://www.omgubuntu.co.uk/2010/11/remmina-to-be-ubuntus-new-remote-desktop-app/)

---

