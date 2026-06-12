---
title: "Is Ubuntu lame for a home server?"
date: 2009-08-09
forum: Recurring Discussions
---

### Post by fela on 2009-08-09
Hi
Now I use Ubuntu desktop version on all the desktop computers I can, and have done for quite some years.

But recently (as in January kind of time) we built a home server for lots of things (my second computer build). Now it was obvious I was gonna put Linux on it (windows didn't even cross my mind :P), the question was what distro. Now in a perfect world I would have put Slackware or Gentoo on it - as the computer doesn't have the best of specifications (it was built on a budget for £120), and I would have definitely NOT put a GUI on it.

But in the real world, my Dad needed to use the server for stuff like downloading files, backing up files, etc. and he's a complete n00b at the command line (MacOS all his computer-using life). So guess what was put on there? Ubuntu, desktop version (and 32 bit to add insult to injury, didn't have a 64 bit cd handy).

He connects to it via VNC to administrate it and stuff (I always cringe when I see the VNC window with its seconds-long latencies), but obviously I administrate it over ssh (which has basically no latency over our 100MB ethernet network).

I just think it's lame having a GUI installed on a home server. I SOOOOO want to get rid of it! Plus, having a distro like slackware on it would propel my geek status by a factor of 65,536 :lolflag:

What do you think, is it lame having a GUI on a home server?

I DO NOT use it, remember! << the GUI, that is!

---

### Post by Barrucadu on 2009-08-09
The lameness is slightly mitigated because you use SSH, but is still present :P

---

### Post by MasterNetra on 2009-08-09
You do realize there is a server edition right? Also how would people know your using a GUI if you don't tell them? ;) Anywho, just my thoughts can't give any more then that sense I myself no where near knowledgeable enough to seriously play with servers yet.

---

### Post by fela on 2009-08-09
> **Barrucadu said:**
> The lameness is slightly mitigated because you use SSH, but is still present :P

I know :(

Maybe I'll just pretend it's not there. I'll create a user that I login with, and a group that the normal user is part of. I'll make ALL the gnome files + gdm and X11 only accessible to the, let's say 'gui' group, so when I ssh I have to login as a different user to even see the the gui files...


^^ I WAS joking by the way!

---

### Post by fela on 2009-08-09
> **MasterNetra said:**
> You do realize there is a server edition right? Also how would people know your using a GUI if you don't tell them? ;) Anywho, just my thoughts can't give any more then that sense I myself no where near knowledgeable enough to seriously play with servers yet.

I know about the server one. But I installed the desktop one so I didn't have to manually install the GUI (laziness rather than lack of knowledge).

PS. I LOVE playing with servers...

EDIT: plus I didn't have a server install cd handy, and all the server packages that come with the server edition are easily installable on the desktop version.

---

### Post by steveneddy on 2009-08-09
Ubuntu Server would be a great server for home or professional use.

I have used it in the past and are about to set up a new server when the next LTS comes out.

---

### Post by jaxxstorm on 2009-08-09
I personally think Ubuntu's server version is excellent. I also think there is nothing wrong with using a GUI *for a home server*

There is no chance in hell I'd ever use a GUI for a production server, having said that I wouldn't use Ubuntu for a production server just yet, its RedHat or nothing for me right now, the support is excellent.

---

### Post by RandomJoe on 2009-08-09
So, what's a server?  Nothing particularly special, after all...  Whether a spare leftover, or a high-end machine optimized for I/O, it's still a PC.  I run GUIs on most of mine because they spend much of their time doing nothing at all.  Why not let them pull double duty on occasion?  If I want / need I can go in and do things that require a GUI.  I don't do it often - it's much easier for (lazy) me to ssh in and do things that way! :)  But the option is there and I do use it occasionally.

Now, one option if you really can't spare the cycles is to boot to the console, and manually run X when you want GUI.  I do that by default on my Slack servers, haven't bothered with the Ubuntu ones.

Only machines I haven't put X on are firewall boxes.  Generally some older kit that would be painfully slow for that anyway.

A business-critical production machine that spends much of its time actually DOING something is a different beast.  But for home use?  Not a problem...

Oh, as for what would *require* a GUI?  My biggest reason:  At the console, I can have a single terminal at a time onscreen.  In X, I can have multiple xterms open simultaneously and SEE them all at the same time!  That can be invaluable for troubleshooting and configuration.

---

### Post by JillSwift on 2009-08-09
There's one ***real*** reason servers generally don't have GUIs on them: the GUI takes up resources the server could otherwise use to keep up with demand.

On a home server, demand is rarely an issue. Having one or not becomes entirely the caprice of the owner. "lame" doesn't enter into it, except in the case of the immature little whippets who think using Linux OSs is some form of competition.

---

### Post by fela on 2009-08-09
@randomjoe: this machine, even though it's a home server, is pretty much doing things all the time with all the people in my house using it one way or another. I'll list all the servers it's running (might be more, I forget :P):

Samba
FTP
SSH
Printing (CUPS)
VNC
DAAP (iTunes music sharing)
Apache web server (two drupal websites)
UPnP media server (for a REVO wireless media device)

And there might be more.

The specifications:
CPU: single core athlon LE-1600 with Cool'n'Quiet (clock speed throttling) enabled, 2.2GHz max speed (isn't overclocked for obvious reasons)
RAM: 2GB DDR2 800MHz (used to have 512MB, ran like crap then with little ram + single core CPU)
GPU: integrated (note single core CPU) nvidia 6150/nforce 430

There's a SATAII/IDE card thrown in for kicks aswell. Well, it's absolutely necessary of course for the ancient IDE disk in there.

The reason I hate using the GUI on it is mainly because of the slowness of VNC. If I found a much faster VNC equivalent with a latency that you wouldn't notice (something like Citrix...), then I'd much rather the GUI to be on it.

---

### Post by fela on 2009-08-09
> **JillSwift said:**
> "lame" doesn't enter into it, except in the case of the immature little whippets who think using OSs is some form of competition.

There, fixed the extra word you accidentally put in there :lolflag:

Well, the resources argument does count in my case, if you look at my post above ^^^^

---

### Post by Barrucadu on 2009-08-09
> **RandomJoe said:**
> Oh, as for what would *require* a GUI?  My biggest reason:  At the console, I can have a single terminal at a time onscreen.  In X, I can have multiple xterms open simultaneously and SEE them all at the same time!  That can be invaluable for troubleshooting and configuration.

Tried using screen? ;)

---

### Post by lykwydchykyn on 2009-08-09
> **fela said:**
> 
Well, the resources argument does count in my case, if you look at my post above ^^^^

I may just be getting old, but to me your hardware doesn't sound old or struggling for resources.  I run close to a dozen services on an old Pentium 2 at home.  

I personally don't see a problem having some GUI on a server if it helps you or others maintain the thing better.  That said, I wouldn't be using GNOME, Compiz, and all the odds and ends that come with the standard ubuntu-desktop package.  

As for production environments, if your server can't handle an idle instance of xorg and gdm, it probably shouldn't be a production server.

---

### Post by tom66 on 2009-08-09
We are running three servers which all have GUIs:
  - a mail server, which is quite busy at times, runs on Windows XP SP3.
  - a web server, which is quite busy, and quite old, runs on Red Hat 6 (I think, not sure about version).
  - a new web server, to replace the old one, which will go live in a few weeks, runs on Ubuntu 8.10. It has a dual-core Pentium chip and a good graphics card. It also runs Compiz, surprisingly this helps reduce load on the server because it means the CPU does less of the graphics stuff and more of the servery-stuff.

All of these servers are actually old (new, in some cases) desktops that nobody wants anymore!

---

### Post by fela on 2009-08-09
> **lykwydchykyn said:**
> I may just be getting old, but to me your hardware doesn't sound old or struggling for resources.  I run close to a dozen services on an old Pentium 2 at home.
Maybe it's because my desktop that I normally use has a dual core athlon at 3.1GHz (soon to be quad core PhenomII :P), with 4GB RAM and a 9800GT 512MB graphics card....

> 
As for production environments, if your server can't handle an idle instance of xorg and gdm, it probably shouldn't be a production server.
Umm, it can handle it. Just that using it with the GUI is pretty slow. I don't know why but I assume it's the specs. Even if I attach a screen to the server and use it locally, the GUI isn't terribly responsive. It could be because it's running software graphics. In fact, that must be why! Maybe I'll try and install a graphics driver for it (haven't even thought about that!).

EDIT: turns out it is using hardware acceleration after all. Maybe Ubuntu Jaunty has become the 'winblows vista of linux distros'.

---

### Post by lswb on 2009-08-09
Resources can be a factor but reliablility and security are also big reasons for not having X or a gui on a server. Think about it, when was the last time you saw a crash that wasn't related to X or graphics drivers?

---

### Post by fela on 2009-08-09
> **lswb said:**
> Resources can be a factor but reliablility and security are also big reasons for not having X or a gui on a server. Think about it, when was the last time you saw a crash that wasn't related to X or graphics drivers?

It was when my hdd had a head crash. That was the last hang anyway. The last crash was when I used a development kernel with 256MB RAM and a corrupt swap partition, so yeah...actually that was my only full on crash with Linux. It said 'panic - not syncing or something like that, and the caps + num lock lights flashed I think. It was ages ago so I might not remember right.

---

### Post by JillSwift on 2009-08-09
> **fela said:**
> There, fixed the extra word you accidentally put in thereHow rude. Really, *don't* put words in my mouth. I have my reasons for being specific. Even if you don't agree with them, please respect my right to express them.

> **fela said:**
> Well, the resources argument does count in my case, if you look at my post above ^^^^
I disagree that you'd need to trim off the GUI just because you aren't using the latest high capacity server. Honestly, all of that is I/O, which your processor and sub-systems will handle nicely.

Here's an alternative to VNC - you can run GUI apps via SSH with the -Y switch. I find that very convenient, and a whole lot faster than VNC or similar remote desktop could ever be. =^_^=

---

### Post by fela on 2009-08-09
> **JillSwift said:**
> How rude. Really, *don't* put words in my mouth. I have my reasons for being specific. Even if you don't agree with them, please respect my right to express them.


I disagree that you'd need to trim off the GUI just because you aren't using the latest high capacity server. Honestly, all of that is I/O, which your processor and sub-systems will handle nicely.

Here's an alternative to VNC - you can run GUI apps via SSH with the -Y switch. I find that very convenient, and a whole lot faster than VNC or similar remote desktop could ever be. =^_^=

Sorry about the words in your mouth thing, I was just saying that I'm not just talking about Linux here (well I am, but that doesn't come into it).

Oh by the way, it's not the -Y switch it's the -X switch (or can you use -Y aswell?) - that wouldn't really be what I'm looking for because my dad (who's the only one who uses the GUI) uses windows and mac osx and not Linux. Ie. he doesn't use X11, which you need for X forwarding (what you were talking about I assume?).

Luckily I've found a much faster VNC equivalent called FreeNX, it's actually very fast, near local speeds (and I haven't even tweaked the settings :P).

---

### Post by JillSwift on 2009-08-09
> **fela said:**
> Sorry about the words in your mouth thing, I was just saying that I'm not just talking about Linux here (well I am, but that doesn't come into it).S'ok.

> **fela said:**
> Oh by the way, it's not the -Y switch it's the -X switch (or can you use -Y aswell?) - that wouldn't really be what I'm looking for because my dad (who's the only one who uses the GUI) uses windows and mac osx and not Linux. Ie. he doesn't use X11, which you need for X forwarding (what you were talking about I assume?).-X is X11 forwarding, -Y is "trusted" X11 forwarding. from man ssh: "Trusted X11 forwardings are not subjected to the X11 SECURITY extension controls." (I'm just used to using -Y on my home 'net.)

> **fela said:**
> Luckily I've found a much faster VNC equivalent called FreeNX, it's actually very fast, near local speeds (and I haven't even tweaked the settings :P).
Wow. I must give that a try!

---

### Post by dmizer on 2009-08-09
Using GUI or not in a server has nothing to do with resources wasted or not.

The main reason for shunning a GUI on a server is that a server is exposed to external attack. You want to reduce a server's profile as much as possible in order to reduce your risk of attack. A GUI on a server can bring in hundreds of nifty little daemons and resources, all ripe for exploit, particularly VNC.

So, the less you have running on your server, the less you are likely to get hacked. And yes, it CAN happen to anyone: [http://ubuntuforums.org/showthread.php?t=688979](http://ubuntuforums.org/showthread.php?t=688979)

Besides, with all the web administration tools out there, there's very little reason for you to use a GUI.

---

### Post by fela on 2009-08-09
> **dmizer said:**
> Besides, with all the web administration tools out there, there's very little reason for you to use a GUI.

Try telling my dad that!

---

### Post by crush304 on 2009-08-09
you might try 
no machine [http://www.nomachine.com]("http://www.nomachine.com") instead of vnc

---

### Post by chessnerd on 2009-08-09
It just depends on your preference. If you have a need for speed and can use the CLI well then don't bother with a GUI. If you like being able to visually see your files when you uses the server then, by all means, put a GUI on it. However, I don't know if you really need GNOME for this. Maybe you should put IceWM or JWM on there to lighten the load a bit.

---

### Post by dmizer on 2009-08-09
> **fela said:**
> Try telling my dad that!

Show, don't tell.

---

### Post by lykwydchykyn on 2009-08-09
> **dmizer said:**
> Using GUI or not in a server has nothing to do with resources wasted or not.

The main reason for shunning a GUI on a server is that a server is exposed to external attack. You want to reduce a server's profile as much as possible in order to reduce your risk of attack. Installing a GUI on a server brings in hundreds (if not thousands) of nifty little daemons and resourses, all ripe for exploit, particularly VNC.


I really think you're exaggerating here.  If by GUI someone means GNOME or KDE with all the bells and whistles, than maybe there's a problem.  Xorg with LXDE or icewm doesn't run even half a dozen daemons, much less hundreds.  And come on, thousands?  Please show me a process list with THOUSANDS of daemons.

I'll agree that VNC and XDMCP are readily exploitable if used over the internet.  But, to my knowledge, installing a simple GUI and xorg activates neither service and opens no ports in a default Ubuntu configuration.  Correct me if I'm wrong.

---

### Post by lisati on 2009-08-09
If this was a multi-choice poll, I would have chosen both "that's fine, mate" and "I don't care" - use what works!

---

### Post by Sublime Porte on 2009-08-09
I have X (ie. a GUI) installed on my server, but using VNC seems a little wasteful, especially when X has it's own network protocols built in. If I want to use any GUI application on the server, I just use it on my desktop, laptop or where ever I happen to be, using my local X display to open the app.

---

### Post by dmizer on 2009-08-09
> **lykwydchykyn said:**
> I really think you're exaggerating here.

Busted :popcorn:

Even if the GUI only adds a few extra daemons, you're still better off without. Also, the OP did indicate that they were using VNC, hence my comment on VNC.

However, [as was indicated before](http://ubuntuforums.org/showpost.php?p=7759622&postcount=7) ... if the server is not exposed to the internet, then feel free to add a GUI if it makes you feel comfortable. But that could make more work for you later if you decide to make the server live.

---

### Post by schauerlich on 2009-08-10
> **fela said:**
> Now in a perfect world I would have put Slackware or Gentoo on it - as the computer doesn't have the best of specifications (it was built on a budget for £120), and I would have definitely NOT put a GUI on it.

Why not?
> But in the real world, my Dad needed to use the server for stuff like downloading files, backing up files, etc. and he's a complete n00b at the command line (MacOS all his computer-using life). 
Right, using Mac OS X == command line n00b. I'll close my 3 terminals straight away. I wouldn't want to go against the stereotype.

> 
He connects to it via VNC to administrate it and stuff (I always cringe when I see the VNC window with its seconds-long latencies),
You obviously don't have a good VNC client.

> 
 but obviously I administrate it over ssh (which has basically no latency over our 100MB ethernet network).

Here's a cookie.

> I just think it's lame having a GUI installed on a home server.
Why? The GUI is a tool. Like many people have said, have it start up without X (if you're /really/ that worried about performance) and teach your dad how to type "startx".

> 
 Plus, having a distro like slackware on it would propel my geek status by a factor of 65,536
That's cute, you used a power of 2 that most people don't have memorized off the bat. LOL GEEK CRED!

> What do you think, is it lame having a GUI on a home server?
No.
> 
I DO NOT use it, remember! << the GUI, that is!
Really? I don't think you made that clear enough.

---

### Post by Sublime Porte on 2009-08-10
> Right, using Mac OS X == command line n00b. I'll close my 3 terminals straight away. I wouldn't want to go against the stereotype

Well I don't think he was implying that being an OSX user makes you a cli-phobic noob, just that his father has lived all his life in the comfort of the OSX GUI.

---

### Post by fela on 2009-08-10
> **crush304 said:**
> you might try 
no machine [http://www.nomachine.com]("http://www.nomachine.com") instead of vnc

I just tried that yesterday, it's wicked I know!

> **chessnerd said:**
> It just depends on your preference. If you have a need for speed and can use the CLI well then don't bother with a GUI. If you like being able to visually see your files when you uses the server then, by all means, put a GUI on it. However, I don't know if you really need GNOME for this. Maybe you should put IceWM or JWM on there to lighten the load a bit.

When I get the time, when I get the time....e17 or fluxbox sounds promising (haven't used IceWM or JWM, but I've used the other two).

> **dmizer said:**
> Show, don't tell.

Actually, I have. It's just that there's inevitably things you can't do over a web interface, such as setup SAMBA shares (yes, I use NFS but he uses samba).

> **Sublime Porte said:**
> Well I don't think he was implying that being an OSX user makes you a cli-phobic noob, just that his father has lived all his life in the comfort of the OSX GUI.

^^ What he said :)


Actually my next plan of action is to setup a easy-to-use but low on the resources window manager. GNOME, I've realized, is just too memory+cpu hogging.

---

### Post by Sublime Porte on 2009-08-10
> Actually, I have. It's just that there's inevitably things you can't do over a web interface, such as setup SAMBA shares (yes, I use NFS but he uses samba).

[Webmin](http://www.webmin.com) allows you to create/administer samba shares, and pretty much everything else your father would probably ever wanna do.

---

### Post by dmizer on 2009-08-10
> **fela said:**
> Actually, I have. It's just that there's inevitably things you can't do over a web interface, such as setup SAMBA shares (yes, I use NFS but he uses samba).

Even if there isn't a web interface (unlikely), most things (samba included) need to be set up via CLI anyway, at least if you want to do it properly.

> **Sublime Porte said:**
> [Webmin](http://www.webmin.com) allows you to create/administer samba shares, and pretty much everything else your father would probably ever wanna do.
Webmin isn't supported in Ubuntu. Does anyone know if [Ebox](http://ebox-platform.com/) allows you to configure samba shares?

---

### Post by Dragonbite on 2009-08-10
When I was starting to work with a server, the gui really helped me (although I was short on monitors).

Right now I am running a headless Ubuntu Server but am also thinking about setting up and fooling around with a CentOS server with GUI (now I have extra monitors :lolflag: ).

Either works fine. I have also found a couple GUI tools for configuring Apache and such that I haven't found the equivalent in Ubuntu or openSUSE (although they have Yast which is available over SSH / CLI and GUI and centralizes all of the configurations in one place)

Ultimately, use whatever works.

---

### Post by jaxxstorm on 2009-08-10
> **dmizer said:**
> Even if there isn't a web interface (unlikely), most things (samba included) need to be set up via CLI anyway, at least if you want to do it properly.


Webmin isn't supported in Ubuntu. Does anyone know if [Ebox](http://ebox-platform.com/) allows you to configure samba shares?

I've personally used Webmin in Ubuntu server, so what makes you say that it isn't supported?

---

### Post by Sublime Porte on 2009-08-10
> Webmin isn't supported in Ubuntu

Meaning nobody's going to hold your hand if something goes wrong? Or meaning it won't work with a reasonable feature-set? They seem to have an ubuntu aimed deb package on their downloads page...

---

### Post by dmizer on 2009-08-10
> **jaxxstorm said:**
> I've personally used Webmin in Ubuntu server, so what makes you say that it isn't supported?

[https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)
and
[https://answers.edge.launchpad.net/ubuntu/+question/2873](https://answers.edge.launchpad.net/ubuntu/+question/2873)

---

### Post by lykwydchykyn on 2009-08-10
I believe ebox has a samba module, but, meh; I'll take webmin over ebox any day, "supported" or not.

Here's to 4 years of webmin use on Ubuntu, SLES, and Debian without a hitch! \\:D/

---

### Post by 3rdalbum on 2009-08-10
I run a GUI on my home server, even though it's all fully set up.

Reason: So I can download files using that server, rather than keep my desktop rig burning power all night. Some files can only be easily downloaded in a web browser (like Rapidshare and some other download sites). And I also 'download' Flash video this way too - keep Firefox running on the server on a Megavideo page (setting it up with VNC), and when I get up in the morning I just use SSH to copy the video file from /tmp to wherever I want it, and then I "killall firefox".

---

### Post by The Real Dave on 2009-08-10
Na, I reckon its lame to use FreeNAS for a home server, its kinda like, making cookies from scratch, or using Shake and Bake :lolflag:

That said though, my servers run FreeNAS. Its actually a CLI but gives a GUI over a web interface. Based on FreeBSD so stable, and you can add packages from FreeBSD to it. Does all my CIFS, Samba, media, SSH, torrents, its great. Doesn't take much to run either, a less than 100Mb ISO, and can run perfectly well with 128Mb RAM. I originally used it on my 451Mhz, 128Mb RAM server (now a backup server, still on FreeNAS), before I upgraded it to 1.7Ghz, 384Mb PIV, which was previously running Ubuntu, slowly. 

My server actually boots from the FreeNAS disk, saving the config file on a flash drive, leaving the drives spin down when not being used, lowering heat and wear. The whole OS runs in RAM :D :D 

Definately useful if you want a server, without all the effort of setting up from CLI, adding packages and that, but still want the power. And runs well on old hardware :D 
[URL="www.freenas.org"]
FreeNAS[/URL]

---

### Post by Dragonbite on 2009-08-10
> **3rdalbum said:**
> I run a GUI on my home server, even though it's all fully set up.

Reason: So I can download files using that server, rather than keep my desktop rig burning power all night. Some files can only be easily downloaded in a web browser (like Rapidshare and some other download sites). And I also 'download' Flash video this way too - keep Firefox running on the server on a Megavideo page (setting it up with VNC), and when I get up in the morning I just use SSH to copy the video file from /tmp to wherever I want it, and then I "killall firefox".

I do my large downloads using my server without a GUI[LIST=1]
[*]Navigate to the webpage on my local machine (in my case, my laptop usually)
[*]open a terminal and SSH into my server
[*]navigate to the destination file I want to put the file
[*]Copy the Link Location from the website link into the clipboard
[*]type ```
wget 
``` 
[*]right-click and paste the URL the browser was going to download from 
[*]Hit Enter. 
[/LIST]

Once this is done, the server is going to continue downloading from that location even after I close the terminal and shut down my laptop.

Haven't tried downloading Flash video, though. Most of the time I am downloading Linux ISOs and such so it is pretty straight forward.

---

### Post by tsali on 2009-08-10
I have a Via C3 based home server. I found Ubuntu Server to be too resource intensive...slow as molasses.

I use Debian. It supports auto backup, daap server, web server, ftp server, samba.

I can admin via Webmin OR use an NX server/client to get a gnome desktop.

typically 148mb RAM in use without NX session, 380mb with NX session.

The gui was an afterthought. It ran for a long time without one. Since X wasn't running, it only used 70-80mb.

The Via C3 is slow, but since it is a server that runs many services background 24/7, time is on its side.

---

### Post by tsali on 2009-08-10
> **Dragonbite said:**
> I do my large downloads using my server without a GUI[LIST=1]
[*]Navigate to the webpage on my local machine (in my case, my laptop usually)
[*]open a terminal and SSH into my server
[*]navigate to the destination file I want to put the file
[*]Copy the Link Location from the website link into the clipboard
[*]type ```
wget 
``` 
[*]right-click and paste the URL the browser was going to download from 
[*]Hit Enter. 
[/LIST]

Once this is done, the server is going to continue downloading from that location even after I close the terminal and shut down my laptop.

Haven't tried downloading Flash video, though. Most of the time I am downloading Linux ISOs and such so it is pretty straight forward.

I would recommend that you install rtorrent and screen for your large downloads. Setup rtorrent to watch your download folder.

Start a session, start screen, start rtorrent. Then disconnet the screen session and logout.

Setup your client computers or terminals to download torrent files to your server's torrent folder and rtorrent will handle it from there.

You can setup rtorrent's upload/download throttle to prevent it from monopolizing your bandwidth.

---

### Post by fela on 2009-08-10
> **The Real Dave said:**
> Na, I reckon its lame to use FreeNAS for a home server, its kinda like, making cookies from scratch, or using Shake and Bake :lolflag:

That said though, my servers run FreeNAS. Its actually a CLI but gives a GUI over a web interface. Based on FreeBSD so stable, and you can add packages from FreeBSD to it. Does all my CIFS, Samba, media, SSH, torrents, its great. Doesn't take much to run either, a less than 100Mb ISO, and can run perfectly well with 128Mb RAM. I originally used it on my 451Mhz, 128Mb RAM server (now a backup server, still on FreeNAS), before I upgraded it to 1.7Ghz, 384Mb PIV, which was previously running Ubuntu, slowly. 

My server actually boots from the FreeNAS disk, saving the config file on a flash drive, leaving the drives spin down when not being used, lowering heat and wear. The whole OS runs in RAM :D :D 

Definately useful if you want a server, without all the effort of setting up from CLI, adding packages and that, but still want the power. And runs well on old hardware :D 
[URL="www.freenas.org"]
FreeNAS[/URL]

It's beginning to sound like my server is more like a gaming rig, with 2GB of RAM and an Athlon 64!!

At least I don't run KDE4 on it though. Now that WOULD be lame + stupid! I refuse to even run KDE4 on my desktop rig, it runs slower than windows vista.

---

### Post by Dragonbite on 2009-08-11
> **tsali said:**
> I would recommend that you install rtorrent and screen for your large downloads. Setup rtorrent to watch your download folder.

Start a session, start screen, start rtorrent. Then disconnet the screen session and logout.

Setup your client computers or terminals to download torrent files to your server's torrent folder and rtorrent will handle it from there.

You can setup rtorrent's upload/download throttle to prevent it from monopolizing your bandwidth.

I know nothing about torrents; using, storing, securing, etc.  Do I have to seed in order to download?

---

### Post by slakkie on 2009-08-11
> **fela said:**
> 
What do you think, is it lame having a GUI on a home server?


Yes. But since your dad needs it, it is kinda nice, sweet and thoughtful. So you are not lame (but your dad is.. LOL ;))

---

### Post by fela on 2009-08-11
> **slakkie said:**
> Yes. But since your dad needs it, it is kinda nice, sweet and thoughtful. So you are not lame (but your dad is.. LOL ;))

:lolflag: I always use the command line on it anyway, so I knew that I'm not lame :P

Once I get the time I'm gonna setup JWM on it as it's much faster than the current GNOME. Gnome is good for a dual core 4GB desktop machine like mine, but NOT for a server.

---

### Post by issih on 2009-08-11
Using a command line is not cool and a using a gui is not lame...

they are both excellent user interfaces that excel at different tasks.

Frankly I think guis are better for administration of most things, provided it is a well designed gui, but a cli interface will always be best for organising, and sorting large amounts of data, and for setting up processing workflows.

its a pointless question imo...

Oh and for the record you can ssh -X from a mac (all macs running leopard have an X server installed, and you could install the X server from the install dvds on versions previous to that), it works perfectly.

Personally though, I find vnc over a home network is perfectly usable unless you are doing something silly.

My opinion may be coloured however by the fact that I have to use it for work over the internet...now that can get painful, even using low profile settings.

---

### Post by fela on 2009-08-11
> **issih said:**
> Using a command line is not cool and a using a gui is not lame...

they are both excellent user interfaces that excel at different tasks.

Exactly. My statement is that the CLI excels at server (and desktop) tasks, and GUI's excel mainly at desktop tasks.

> Frankly I think guis are better for administration of most things, provided it is a well designed gui, but a cli interface will always be best for organising, and sorting large amounts of data, and for setting up processing workflows.

Frankly I think clis are better for administration of most things, provided it isn't DOS, but a gui interface will always be best for users unaccustomed to the cli.

> its a pointless question imo...

Oh.

> Oh and for the record you can ssh -X from a mac (all macs running leopard have an X server installed, and you could install the X server from the install dvds on versions previous to that), it works perfectly.

I knew that. My Dad uses Windows too though.

> Personally though, I find vnc over a home network is perfectly usable unless you are doing something silly.

I must be doing something silly then! Surely if TightVNC gives bad latencies (in my eyes) over a 100MB/s ethernet network, VNC has met a dead end with todays GUIs.

> My opinion may be coloured however by the fact that I have to use it for work over the internet...now that can get painful, even using low profile settings.

****OUCH!****

Seriously though, the ouch isn't just at the latencies. VNC over the internet is opening up such sweet opportunities to get hacked. I really wouldn't do that if I were you.

---

### Post by issih on 2009-08-11
VNC secured through an ssh tunnel is perfectly safe...or at least as safe as anything can be. having port 5900 open would be a terible idea, rest assured we don't do that, we do have the standard port 22 open for ssh, but have a denyhosts style program running and have an automated password cracker ferreting out weak user passwords, so things are relatively well set up.

Tight VNC is not very good in my experience, not sure why. I got to the point where I was happy with using it and stopped playing about.

I wonder if you are getting latency associated with the encoding, which given you have plenty of bandwidth across a local home network means you might do better to try reducing the colour depth and using other encoding options.

Have a fiddle with it, it really shouldn't be that painful on a lan.

---

### Post by fela on 2009-08-11
> **issih said:**
> VNC secured through an ssh tunnel is perfectly safe...or at least as safe as anything can be. having port 5900 open would be a terible idea, rest assured we don't do that, we do have the standard port 22 open for ssh, but have a denyhosts style program running and have an automated password cracker ferreting out weak user passwords, so things are relatively well set up.

Tight VNC is not very good in my experience, not sure why. I got to the point where I was happy with using it and stopped playing about.

I wonder if you are getting latency associated with the encoding, which given you have plenty of bandwidth across a local home network means you might do better to try reducing the colour depth and using other encoding options.

Have a fiddle with it, it really shouldn't be that painful on a lan.

Well, having any port open to the internet is a potential security risk, as no security solutions are perfect. But I guess you could say that just being connected is a security risk in the first place!

Anyway, believe me I've fiddled around with tightvnc (and other servers/clients) loads, and it's always high latency (well, quite high latency. I'm talking about moving/resizing windows etc, in fact I might make it so that resizing and moving windows is a wireframe only on the server, don't know why I didn't think of that). It's responsive in the sense that when you open a menu for instance, it opens immediately.

Also, I think that the connection is being limited to 10MB/s for some reason. I know that they both have 10/100 NICs (integrated, very similar motherboards), so I don't know (and care that much tbh) what the issue is there. Atm I only stream small audio files across it (it's easier playing the same music from the same computer on all the computers in the house), we're gonna get a firewire/usb/esata drive for backing up files.

---

### Post by issih on 2009-08-12
Ah well...as ever, use what works :)

---

### Post by tsali on 2009-08-13
> **Dragonbite said:**
> I know nothing about torrents; using, storing, securing, etc.  Do I have to seed in order to download?

No, you don't. But why wouldn't you?

---

### Post by Sublime Porte on 2009-08-13
> I would recommend that you install rtorrent and screen for your large downloads. Setup rtorrent to watch your download folder.
Start a session, start screen, start rtorrent. Then disconnet the screen session and logout.

Install deluge. It runs as a background daemon (at startup if you like) so it can always be running in the background, without you having to login or keep it running in screen. Then you can either connect to it remotely with the GTK-network client from your desktop, or ssh in and control it via CLI. There's also other options for controlling it, those are the two most common and practical though.

---

### Post by tsali on 2009-08-14
> **issih said:**
> VNC secured through an ssh tunnel is perfectly safe...or at least as safe as anything can be. having port 5900 open would be a terible idea, rest assured we don't do that, we do have the standard port 22 open for ssh, but have a denyhosts style program running and have an automated password cracker ferreting out weak user passwords, so things are relatively well set up.

Tight VNC is not very good in my experience, not sure why. I got to the point where I was happy with using it and stopped playing about.

I wonder if you are getting latency associated with the encoding, which given you have plenty of bandwidth across a local home network means you might do better to try reducing the colour depth and using other encoding options.

Have a fiddle with it, it really shouldn't be that painful on a lan.

NX (nomachine) works very well right out of the box. I didn't have to do any  fiddling at all.

---

