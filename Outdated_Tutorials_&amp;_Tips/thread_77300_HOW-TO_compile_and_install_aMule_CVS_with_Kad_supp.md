---
title: "HOW-TO: compile and install aMule CVS with Kad support"
date: 2005-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by fede on 2005-10-16
[SIZE="4"]**_aMule CVS with Kad compile HowTo_**[/SIZE]

Below I try to describe how to compile the development version (CVS, I think it stands for Current Version Snapshot) of aMule in Ubuntu 5.10 Breezy Badger.

These CVS releases can be enabled for Kad support, which allows for a MUCH IMPROVED search functions, as far as I know (and as little as I do, too) Kad provides much better search results than other file sharing networks.

The latest stable release (available in universe repos) does not include Kad support, which is scheduled for the next release (to come at an uncertain date in the future). So for now, if you want amule with kad, the CVS are all you can use.

Also, the amule wiki is currently down due to a spam attack, so I hope this is useful in the meantime.

*WARNING1: I'm a newbie to linux, so I cannot really explain anything. I'm just posting what worked for me (under a default Breezy Install) in case it might be useful. This has probably been the first time I successfully compiled something – so I really don't grasp why or how this works. I hope more knowledgeable people can add to this if necessary.*

*WARNING2: CVS are development versions and I believe that as such they might be unstable or non working. I suppose they might be unpredictable, unstable and maybe damage your system, etc – I really don't know the least thing about this, be warned. I just wanted Kad to work, and saw that there's a lot of reports of these CVS working fine, so I did this to be able to get Kad until the next amule version is released.*

----------------------------------------------------------------------------------------
**Steps:**

1. To compile amule you need to have these packages installed:
	g++ 
	libcurl3-dev 
	gettext 
	make 
	libwxgtk2.6-0 
	libwxgtk2.6-dev 
	libwxbase2.4-1 
	libwxbase2.4-dev 
	libgtk2.0-dev

(use synaptic or if you prefer, 

```
sudo apt-get install g++ libcurl3-dev gettext make 
sudo apt-get install libwxgtk2.6-0 libwxgtk2.6-dev 
sudo apt-get install libwxbase2.4-1 libwxbase2.4-dev libgtk2.0-dev

```
)

2.Download amule CVS from:

 ```
http://www.hirnriss.net/?area=cvs
```

to a directory in your home folder.  (I used 20051016) 

3. Open a terminal window and go to wherever you put the CVS package. Steps 4-7 should be done there.

4. Uncompress the CVS package:

```
tar xjfv aMule-CVS-20051016.tar.bz2
```

	This creates an amule-cvs directory.

5. Go into that directory, and prepare the script for compilation:

```
cd amule-cvs
./configure --enable-kad-compile
```

6. Compile:

```
make
```

7. Install:

```
sudo make install
```

8. For kad to work, you have to open 3 ports in your system. I believe this are blocked by default, so I installed firestarter using synaptic and allowed the following ports:

4662 (edonkey TCP)
4665 (edonkey UDP, which is TCP + 3 ie 4662+3= 4665) 
4672 (Kad?)

(to allow a port, select the bottom section under the Policy tab, for Inbound traffic policy, and add a rule specifying this port number)

9. run 

```
amule
```

	from a terminal or from the gnome menu, if it doesn't yet appear there, use
	
```
killall gnome-panel 
```

	to refresh the gnome menu.
	
Note that sometimes Kad initially appears as firewalled and changes to ok after some time (10-30 seconds?). Also, in preferences -> connection, I set up my connection speeds, which where by default really low, but I don't know if this is necessary or not.	
-----------------------------

Good Luck! :smile:

---

### Post by ow50 on 2005-10-16
I build aMule CVS debian packages for i386 Breezy from time to time. You can find them at
[http://koti.mbnet.fi/~ots/ubuntu/breezy/](http://koti.mbnet.fi/~ots/ubuntu/breezy/)

Note the different packaging. Most people will want the following
[LIST]
[*]amule
[*]amule-common
[*]amule-ed2k
[/LIST]

The debian source is at
[http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/)

---

### Post by fede on 2005-10-16
Great, that's much better than doing what I had to!

---

### Post by btdown on 2005-10-17
ow50, thanks for the aMule work! 
One question..I already have aMule installed from the standard breezy rep (universe?) and how would I upgrade to one of your cvs versions? simply download and use dpkg to upgrade, or would i need to remove the original and install your never version?
 
Thanks!
BT

---

### Post by ow50 on 2005-10-17
[QUOTE=btdown]One question..I already have aMule installed from the standard breezy rep (universe?) and how would I upgrade to one of your cvs versions? simply download and use dpkg to upgrade, or would i need to remove the original and install your never version?[/QUOTE]
Just download and install with "sudo dpkg -i amule*.deb". Breezy has packages "amule" and "amule-utils". If you have them both installed, just make sure you upgrade both.

---

### Post by btdown on 2005-10-17
thanks for the info!!

---

### Post by Josef K. on 2005-10-18
[QUOTE=ow50]I build aMule CVS debian packages for i386 Breezy from time to time.[/QUOTE]

how about add a package.gz (or whatever synaptic\adept needs) and make an unofficial repository? ;)

otherwise how can I make a cron job that check every week that site, download a new version if there and install it?! I'm afraid my script knowledge is still near zero :(

---

### Post by ow50 on 2005-10-18
[QUOTE=Josef K.]how about add a package.gz (or whatever synaptic\adept needs) and make an unofficial repository? ;)[/QUOTE]
I'm still thinkin' about that. It depends on whether I'll be providing only aMule or do I want to host other packages as well. If I choose to host only aMule, I just might even do a cron running script to build and upload aMule daily to a proper repository. And maybe even GPG-sign the packages.

---

### Post by btdown on 2005-10-18
Thanks! Im having problems with KAD, though. My router firewall (and ports 4662-4772) are open, but it still claims that its firewalled. I dont have a sw firewall installed on ubuntu, so Im wondering if there's anything else I need to change/edit in order to open them up. Any ideas?
BT

---

### Post by bored2k on 2005-10-18
[QUOTE=ow50]I build aMule CVS debian packages for i386 Breezy from time to time. You can find them at
[http://koti.mbnet.fi/~ots/ubuntu/breezy/](http://koti.mbnet.fi/~ots/ubuntu/breezy/)

Note the different packaging. Most people will want the following
[LIST]
[*]amule
[*]amule-common
[*]amule-ed2k
[/LIST]

The debian source is at
[http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/)

And my modified source is at
[http://koti.mbnet.fi/~ots/ubuntu/source/](http://koti.mbnet.fi/~ots/ubuntu/source/)

I only change the wx dependency's version number, so the source is not much different from that at vollstreckernet.[/QUOTE]
I love you..

---

### Post by ow50 on 2005-10-18
[quote=btdown]Thanks! Im having problems with KAD, though. My router firewall (and ports 4662-4772) are open, but it still claims that its firewalled. I dont have a sw firewall installed on ubuntu, so Im wondering if there's anything else I need to change/edit in order to open them up. Any ideas?
BT[/quote]
[quote=fede]Note that sometimes Kad initially appears as firewalled and changes to ok after some time (10-30 seconds?).[/quote]
Based on my experiences, it can take even hours for Kad to switch from "firewalled" to "ok". If you have the correct ports open, just wait.

I should have that repository up and running in a few days.

---

### Post by btdown on 2005-10-18
You were right! Somewhere between 10-15 mins it did switch to "ok" (non-firewalled). Pure genious!

---

### Post by ow50 on 2005-10-19
It's a repository now. Check the page for instructions.
[http://koti.mbnet.fi/~ots/ubuntu/breezy/](http://koti.mbnet.fi/~ots/ubuntu/breezy/)

Let me know if it works and I'll post it on the aMule forums as well.

Keep in mind that I might add other packages besides aMule to the repository later, so you might not want to add it permanently to your sources.list or if you do, keep an eye on what you update.

---

### Post by btdown on 2005-10-19
Thanks ow50!

---

### Post by n0n0m4n on 2005-10-19
Can anyone tell a complete newbie how to use the information ow50 provided? I can't make heads or tails of it.

I need something step-by-step like fede's instructions, lol.

Been trying for 3 days to get amule to work.

Thanks.

---

### Post by patrickslee on 2005-10-19
Everything but, CVS actually stands for Concurrent Versions System.

---

### Post by Josef K. on 2005-10-20
[QUOTE=ow50]It's a repository now. [/QUOTE]

GREAT! thank you very much \\:D/

>  Check the page for instructions.


BTW what does it mean "The packages are signed with Osmo Salomaa's GPG key. If you trust the packages, use the following commands to have apt trust them as well" and how it works? should I add the gpg lines in sources.list? what happen if I simply add the deb lines?

>  Keep in mind that I might add other packages besides aMule to the repository later, so you might not want to add it permanently to your sources.list or if you do, keep an eye on what you update.
what kind of package will you add?

---

### Post by ow50 on 2005-10-20
[QUOTE=Josef K.]BTW what does it mean "The packages are signed with Osmo Salomaa's GPG key. If you trust the packages, use the following commands to have apt trust them as well" and how it works? should I add the gpg lines in sources.list? what happen if I simply add the deb lines?[/QUOTE]
Apt/synaptic/update-notifier will warn about installing stuff from untrusted sources. If you get tired of these warnings and have found my packages to be reliable, you can get rid of those warnings.

I changed the wording to "run the following commands". Do not add them to sources.list. Instead, open a terminal, copy-paste and run the two commands. The commands will add my GPG key to the apt keyring. Similar to what package "ubuntu-keyring" does for packages that come from Ubuntu. You can view the apt keyring, e.g. with Synaptic: Settings -> Repositories -> Authentication.

You can search the web for info on how GPG itself works.

[QUOTE=Josef K.]what kind of package will you add?[/QUOTE]
Most likely it would be something that's not in Ubuntu's repositories, but there's a small chance I might add a newer version of something that's in Ubuntu. I won't host Marillat illegal codec stuff, since someone else will do that (looks like PLF from now on). Miscellaneous stuff.

---

### Post by ow50 on 2005-10-20
[QUOTE=n0n0m4n]Can anyone tell a complete newbie how to use the information ow50 provided? I can't make heads or tails of it.

I need something step-by-step like fede's instructions, lol.[/QUOTE]
Step-by-step:

1. Run command
```
sudo gedit /etc/apt/sources.list
```
Add the following lines to the end of the file
```
deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/
```
Save and quit gedit.

2. Open Synaptic. Click the refresh button. Search for "amule". Currently you should see "2.0.3+CVS20051019-1~0ots1" as the latest version. Mark packages "amule", "amule-common" and "amule-ed2k" (and others if you know you want them) for install or upgrade. Click the apply button.

3. If you don't want my repository as permanent, in Synaptic, goto Settings -> Repositories and uncheck the repositories (one binary, one source) with the address written above.

---

### Post by Yemoke on 2005-10-20
nice work ow50! with kad it can find alot more :)

---

### Post by n0n0m4n on 2005-10-20
Thanks heaps ow50!

---

### Post by Patrick on 2005-10-22
I did it the way as the TS described it...

Whats the big diffrence between those two ways??

I think with the repo thing you can upgrade more easy??

---

### Post by Thiago on 2005-10-22
Thanks for the repo ow5. Kad rules :D

---

### Post by bored2k on 2005-10-31
What is the port for KAD ?! I keep getting firewalled. I have 4662, 4672 and 4665 opened!

---

### Post by ow50 on 2005-10-31
[QUOTE=bored2k]What is the port for KAD ?! I keep getting firewalled. I have 4662, 4672 and 4665 opened![/QUOTE]
From aMule forums:
> Kademlia uses the same ports as ed2k: one TCP port of your choosing, one UDP at TCP+3, and another UDP port of your choosing.

Sometimes it may just take a while for Kad to switch from "firewalled" to "ok".

---

### Post by bored2k on 2005-10-31
Yeah I just noticed. As usual, aMule's taking a gazillion to connect to a file which pretty much drives me mad &#172;_&#172;.

---

### Post by Josef K. on 2005-12-15
anybody knows what --enable-optimize is for?
and why if I use checkinstall instead of make install I got this error

> 
*** Warning: The package name "amule-cvs" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

*** Warning: The package version "cvs" does not
*** Warning: contain any digits. dpkg might not like that.


and

> 
dpkg-deb - errore: (upstream) version (`cvs') non contiene cifre 
dpkg-deb: 1 errori nel file di controllo

:confused:

---

### Post by bulio on 2005-12-16
Awesome, thanks for the repository! Using Kad now and it rocks :)

---

### Post by sudokubuntu on 2005-12-17
Thanks! This is great.

---

### Post by ow50 on 2006-02-12
Just to let people know, I won't be building aMule CVS packages while the devs consider it such unstable that it needs to be run with "--I-am-scared-of-no-dangerous-code" option. I have rebuilt the 20060109 package with the [toolbar skin patch](http://forum.amule.org/thread.php?threadid=9073&sid=.).

Edit:
The toolbar skin patch link to aMule forums is dead, as they seem to have hosting problems.

With the patch you can specify the toolbar icons, e.g.
```
[Toolbar Bitmaps]
Connect_icon=/usr/share/icons/hicolor/24x24/stock/net/stock_disconnect.png
Disconnect_icon=/usr/share/icons/hicolor/24x24/stock/net/stock_connect.png
Connecting_icon=/usr/share/icons/hicolor/24x24/stock/net/stock_disconnect.png
Network_icon=/usr/share/icons/gnome/24x24/filesystems/gnome-fs-network.png
Transfer_icon=/usr/share/icons/gnome/24x24/stock/media/stock_repeat.png
Search_icon=/usr/share/icons/hicolor/24x24/stock/generic/stock_search.png
Share_icon=/usr/share/icons/hicolor/24x24/stock/net/stock_shared-by-me.png
Messages_icon=/usr/share/icons/hicolor/24x24/stock/image/stock_draw-callouts.png
Stat_icon=/usr/share/icons/hicolor/24x24/stock/chart/stock_insert-chart.png
Pref_icon=/usr/share/icons/hicolor/24x24/apps/gnome-control-center.png
Import_icon=/usr/share/icons/hicolor/24x24/stock/io/stock_insert-file.png
Help_icon=/usr/share/icons/hicolor/24x24/stock/generic/stock_about.png
```

Save that to a file, and then load the file in aMule preferences dialog under GUI-tweaks -> Skin file.

---

### Post by Josef K. on 2006-02-13
since I can't use anymore your builds (I've switched to amd64) I wonder where is this patch and how did you patch the source

---

### Post by ow50 on 2006-02-13
[QUOTE=Josef K.]I wonder where is this patch and how did you patch the source[/QUOTE]
The aMule forums seem to work again.  The patch is in [this](http://forum.amule.org/thread.php?threadid=9073&sid=.) thread.

To patch the source:
```
$ ls
amule-cvs  toolb.diff
$ cd amule-cvs/
$ cat ../toolb.diff | patch -p0
patching file src/amuleDlg.cpp
Hunk #3 succeeded at 667 (offset -20 lines).
Hunk #4 succeeded at 685 (offset -20 lines).
Hunk #5 succeeded at 1362 (offset -35 lines).
Hunk #6 succeeded at 1375 (offset -35 lines).
Hunk #7 succeeded at 1575 (offset -35 lines).
patching file src/amuleDlg.h
Hunk #1 succeeded at 162 (offset -12 lines).
Hunk #2 succeeded at 222 (offset -12 lines).
patching file src/PrefsUnifiedDlg.cpp
```
amule-cvs is the source directory and toolb.diff is the patch file.

Edit:
aMule forums are offline again. I'll attach the patch file here.

---

### Post by Mellon on 2006-02-17
Muchas Gracias, now Kad is working \\:D/

---

### Post by DanielJapan55 on 2006-04-01
Hey there,

I am totally new to Linux, my total computer knowledge consists of Microsoft word and internet explorer, until one week ago, so please talk to me like someone who doesn't know anything.  I read ow50's page for amule and I dont get any of it (now yoga, that's another thing, I studied in India..)

So far I have installed amule CVS Snapshot, then I click "connect" in the upper left and get "not connected (kad: off)" in the lower right corner.

Please tell me what I should do next.

thanks for your help and good karma merits will come your way....:) 

daniel

---

### Post by ow50 on 2006-04-01
[QUOTE=DanielJapan55]So far I have installed amule CVS Snapshot, then I click "connect" in the upper left and get "not connected (kad: off)" in the lower right corner.[/QUOTE]
**Toolbar: Settings -> Connections -> Networks**
Check both ED2K and Kademlia (or whatever you wish to use.)

**Toolbar: Networks -> Servers**
If your server list is empty, enter
```
http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met
```
and hit update (the blue arrow on the left.)

**Toolbar: Connect**
You should connect to a server almost instantly. If not, check the "aMule log" under Networks. Kademlia will connect slower. "Kad: off" should first change to "Kad: firewalled" and finally to "Kad: ok". If this is your first time connecting to Kad, it might take a while.

If you have some router or firewall that's causing problems, you might need to configure that. I don't know how.

---

### Post by ow50 on 2006-04-01
Status update: aMule CVS still appears too unstable.
```
This binary requires you to use the flag --only-chuck-norris-would-stop-me and only if you're very sure of it.
```

There's 2.1.1 packages posted on aMule forums, if someone is interested. I don't know of their quality. Feature-wise there should be no relevant difference to the old CVS packages I'm hosting.
[http://forum.amule.org/thread.php?threadid=9470&sid=](http://forum.amule.org/thread.php?threadid=9470&sid=)

---

### Post by DanielJapan55 on 2006-04-08
I did connect to a server imstantly but that is it.  I still get the message "Kad: off".  How long do you have to wait for the first time connecting?  I've had it running for 4 hours and it hasn't connected....anything else I should check?

Remember I am a super newbie to linux and ubuntu.

---

### Post by ow50 on 2006-04-08
[QUOTE=DanielJapan55]I did connect to a server imstantly but that is it.  I still get the message "Kad: off".  How long do you have to wait for the first time connecting?  I've had it running for 4 hours and it hasn't connected....anything else I should check?[/QUOTE]
**Toolbar: Networks -> Kad**
Try clicking the blue arrow to update the list of nodes and then try clicking the "Bootstrap from known clients". If you're not already downloading something, start downloading some file with lots of sources. If those sources are using Kad, it should ease connecting.

If you're using some router or firewall, make sure you have proper ports open. The ports are listed at some earlier post in this thread.

---

