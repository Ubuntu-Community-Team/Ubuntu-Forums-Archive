---
title: "Tribler : the best bittorrent client for linux ?"
date: 2006-08-11
forum: Outdated Tutorials &amp; Tips
---

### Post by reda_ea on 2006-08-11
[SIZE=4]BIG IMPORTANT EDIT[/SIZE]
this is OOOOOOOLLLLLLDDD
Tribler now has changed a lot,
AND,
they have their own repos and make debs themeselves
so intead of losing your time here, read this :
> **synctext said:**
> Hello All,
A message from the Tribler developers. 
Tribler 3.6.0 is released now and tested to work on Ubuntu.
Download link : [Source code]("http://sourceforge.net/project/showfiles.php?group_id=159448&package_id=178952&release_id=495616")
Ubuntu repository; add to /etc/apt/sources.list the line :
deb [http://debian.tribler.org/debian](http://debian.tribler.org/debian) testing main  #or unstable
[digg.com news article link]("http://www.digg.com/offbeat_news/Tribler_3_6_0_4th_gen_file_sharing")
Please post a message here if you run into problems.
Have Fun,
Dr. Ir. J.A. Pouwelse
Assistant Professor, P2P specialist
Delft University of Technology
thet's it
[SIZE=4]END OF THE BIG IMPORTANT EDIT[/SIZE]

After looking for and trying all (native+gtk) bittorrent clients I could find (and get to compile), I found tribler ([http://www.tribler.org/](http://www.tribler.org/)) witch seems to do all I need from it, and , well, I like it better than the others.
It seems to do more than just bittorrent, something about social sharing I don't understand much (maybe when I'll try this more I'll understand).
from the website
> With Tribler, we are creating software for video file sharing that has a basic understanding of human friendships, of user tastes in content, and of Internet connectivity between users. Currently, Tribler is not production-level software yet, but we do have a fully functional proof-of-concept.
[...]
Features that we are adding include:
    * Amazon-like recommendations to get interesting files
    * Doubling the download speed by using the upload capacity of friends
    * Real-time P2P file sharing with P2P video streaming
    * Showing the locations of other downloaders of the same content with city-level accuracy on a world map
Anyway, take a look at the official page, they have a lot of information there.

And, of course, I made a package for it (that's why I started this thread) it can be downloaded here:
**EDIT**
The older version doesn't work anymore. ere's the lastest version, use this one instead. [http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb](http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb)
**/EDIT**

And if you want to use the web interface, you must configure it to use the loopback interface (it crashed on me when I made automatic) and access it using something like phpABC witch can be found here :
[http://www.swiftlytilting.com/phpabc/](http://www.swiftlytilting.com/phpabc/)
just put it in your webserver and go there and fill the informations you configured the server with.

well that's it ..

---

### Post by TecnoVM64 on 2006-08-12
Sorry but the .deb doesn't work and their repos don't seem to be working correctly, it looks really nice on the screenshots though :(
I'd like to try it :D

Edit: oh ok, it's just that lycos doesn't support direct linking, here's a mirror that supports direct linking ;). :
[http://b.tecnovm64.com/Packages/tribler_3.4.1-0ubuntu1_i386.deb](http://b.tecnovm64.com/Packages/tribler_3.4.1-0ubuntu1_i386.deb)

---

### Post by reda_ea on 2006-08-12
thanx for the mirror

I made a little mistake in the link adress I think that's what caused the error (but direct linking works for me ...)

anyway I corrected everything now :)

---

### Post by Tom Brokaw on 2006-08-12
How does it compare to utorrent?

---

### Post by reda_ea on 2006-08-12
don't know .. you try and tell me :D

---

### Post by MyBigToe on 2006-08-12
Works great for me so far!

---

### Post by justinlb on 2006-08-13
Thanks this is working well, I've been looking for an alternative for Azureus for a while. :D

---

### Post by kostkon on 2006-08-13
Yes I think it's much better from Azureus, if you want to use a lightweight bittorent app; and the idea of social sharing of files is good so you get two things in one with this great app! :)

---

### Post by MyBigToe on 2006-08-13
my only problem so far is that when i download a torrent off a site with a space in, I have to save to my hard drive then open it in tribler or it cant find it

---

### Post by ubuntian on 2006-08-13
hi reda_ea, could u please provide the step of installation so that newbie like me can understand it easily, thx!

---

### Post by Rule on 2006-08-13
is tribler OSS??

---

### Post by MyBigToe on 2006-08-13
> **ubuntian said:**
> hi reda_ea, could u please provide the step of installation so that newbie like me can understand it easily, thx!

As a newbie myself, all i did was download it, open it, and it installed

---

### Post by reda_ea on 2006-08-13
> **ubuntian said:**
> hi reda_ea, could u please provide the step of installation so that newbie like me can understand it easily, thx!

You mean just getting it to work ?? 
get the deb, double click, install, go to applications>internet, click tribler ... :-s 

Or maybe you meant compiling from source ?
Look at the instructions from their website (they have their own customized version of a python library witch requires pyhon headers and all to compile ..)

> **Rule said:**
> is tribler OSS??
Yeah, MIT license I think, anyway it's based on ABC witch is based on Bittornado witch is based on the officiel bittorrent client, so I think it HAS to be opensource

---

### Post by ubuntian on 2006-08-13
the link seem got problem, i can't completely download it....

---

### Post by wbc1228 on 2006-08-14
thanks reda_ea for introducing (and putting the package together) Tribler to the rest of us.  I think Tribler is the best linux torrent appliation I have used yet (azureus was slow and took up too much memory/cpu. qtorrent, bittornado, default bittorrent didn't display unicode correctly and didn't support multiple torrents at one time).  

The main features that I really liked about Tribler: 
- lots of options (I can change ports, limit download/upload speed, change default download location)
- support of unicode filenames
- nice gui

But is it better than uTorrent & BitComet for Windows?
close, but not quite there yet.
Things I like dislike about Tribler: 
- ahhhh... integrating "human friendship" into a torrent software?  not for me, at least not in a torrent software. there are instant messengers, forum, etc. for that.  
- Another feature that is bugging me is that this software "recommends torrent" to me.  Is it monitoring on me?  It just doesn't feel right somehow.  
- The "advanced options" are embedded too deeply and can only be access once the torrent is downloading.  For example, if a torrent file consists of multiple files and I want to exclude one of them from downloading (ie I don't want/already have that particular file), I won't be able to deselect that file until I have selected a download location (which will automatically download all the files).

---

### Post by reda_ea on 2006-08-14
> **wbc1228 said:**
> - ahhhh... integrating "human friendship" into a torrent software?  not for me, at least not in a torrent software. there are instant messengers, forum, etc. for that.  
- Another feature that is bugging me is that this software "recommends torrent" to me.  Is it monitoring on me?  It just doesn't feel right somehow.

from the FAQ in the official website

>  Privacy
From our license: [Tribler] will by default exchange your download history with others. This feature can be disabled by disabling the recommender in the Preference menu. See also the disclaimer at [the bottom of this page]

so all it does is send your history to others, they don't keep it on a server (wich would have been stange for a P2P app), and you can disable it.

Anyway these are just features you only use if you want, The recommendations don't work yet for me, I think I need more history and it needs more users contributing.

> **wbc1228 said:**
> - The "advanced options" are embedded too deeply and can only be access once the torrent is downloading.  For example, if a torrent file consists of multiple files and I want to exclude one of them from downloading (ie I don't want/already have that particular file), I won't be able to deselect that file until I have selected a download location (which will automatically download all the files).

I also hate not being allowed to chose wich files to download before the download begins, that's the main reason I didn't like other clients (and the reason I like bitcomet). I also don't like having to double click on a torrent to have it's details.

---

### Post by MyBigToe on 2006-08-14
any idea on how to make it open torrents with spaces by double clicking or choosing to open it in tribler on download complete without having to open them from the software

---

### Post by TSP on 2006-08-20
Thanks great client! 
Th only bad thing is that sometimes the torrents get's stoped :(

---

### Post by rigor on 2006-08-21
Hey friends, do you know this [http://www.torrentflux.com/]("http://www.torrentflux.com/") ???

Sounds good ?!?!? 8) 8)

---

### Post by TecnoVM64 on 2006-08-21
yeah, that one is awesome, but you need a web server first :)

---

### Post by wbc1228 on 2006-08-30
humm...
My tribler died on me.
Whenever i try to run it, a popup windows "Update to Tribler 3.5.0" opens and it seems to run fine for .0001 seconds.  
After that, the gui (the update notification and tribler itself) commits suicide.  The two windows are still there, but there are no pictures or text in them).
what is weird is that even if you try to kill it (using the command line), it refuses to die and go away.
I tried to reinstall it but that didn't solve the problem.
Anyone else having this issue or is it just me?

---

### Post by Logic* on 2006-08-30
Mine died on me too. I didn't get the popup window, but all the rest you said happened to me too

Except I could kill it.

Anyone prepared to make an updated 3.5.0 deb? I have so far failed miserably.

---

### Post by declaration on 2006-08-30
Mine has died too : (

---

### Post by TecnoVM64 on 2006-08-30
Whenever they make it, I'll host it again :)

---

### Post by rodrigo666 on 2006-09-01
I can't install because it needs some "swig" deppendece.

But I can't find that from my Synaptic.

---

### Post by f4nt0m3t on 2006-09-01
Me neither, anyone got any repository?

---

### Post by reda_ea on 2006-09-01
Hi, sorry didn't notice it was updated, I'll make a package tomorrow.

and for the dependencies it needs a special version of some library, and you must compile that library yourself (so you must have the python development headers and all .. )

---

### Post by reda_ea on 2006-09-01
Hi, sorry didn't notice it was updated, I'll make a package tomorrow.

**EDIT**
here is it: [http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb]("http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb")

---

### Post by wbc1228 on 2006-09-03
> **reda_ea said:**
> Hi, sorry didn't notice it was updated, I'll make a package tomorrow.

**EDIT**
here is it: [http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb]("http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb")

thanks for the update reda_ea!
It is working now.  Your help is highly appreicated.

Thanks again.

---

### Post by The Noble on 2006-09-03
Much appreciated! The update works very well, no problems at all that I can see. This will become my torrent player of choice, especially if we could add this to the repos or something... An auto updater would be nice.

---

### Post by st14n on 2006-09-03
I see Tribler has provided an "unstable" debian repository (see [http://tribler.org/index2.php?layer0=6]("http://tribler.org/index2.php?layer0=6")). I know too little about the package system, but would it mess up my Dapper installing Tribler from this?

Edit: Just curious, the package you provided works fine :)

---

### Post by wampirek on 2006-09-04
> **reda_ea said:**
> Hi, sorry didn't notice it was updated, I'll make a package tomorrow.

**EDIT**
here is it: [http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb]("http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb")

Hello, 

Thanks for the tribler package. 
I've installed previous version some time earlier, but it stopped working (the same problems that were mensioned here), so I decided to download the new one :) 
I installed all necessary programs (such as newest swig, wxPython and m2crypto) and then installed your package. And now, when I try to startr tribler it only shows error message: 

[[IMG]http://img308.imageshack.us/img308/4830/triblerfr8.th.png[/IMG]](http://img308.imageshack.us/my.php?image=triblerfr8.png)

I'm rather new with linux, but checked (in Synaptic) that I've got correct versions of programs: 
openssl - 0.9.8 
swig - 1.3.27 
wxPython - [http://www.wxpython.org/download.php](http://www.wxpython.org/download.php) - Starship repository for Ubuntu 6.06 
m2crypto downloaded version 0.16 and installed (but in Synaptic it is still visible as version 0.13 - I don't know why)

I don't know what else I can do to make Tribler work again ](*,)

---

### Post by TSP on 2006-09-05
Thanks again for the deb!

PS: Can you please post a basic guide to compile this client? thanks ina dvabce!}

Cheers!

---

### Post by bjorkiii on 2006-09-05
:) Was looking forward to trying it but i got the 64 version of ubuntu bugger bugger bugger :(

---

### Post by reda_ea on 2006-09-06
@st14n
I think that repo will make you install at least the m2crypto lib which you shouldn't ijnstall over the ubuntu one. and also be careful of upgrading your ubuntu packages to debian versions from that repo as it make break stuff (if I need a package from debian I download it manually and install it

@wampirek
you don't need to install anything, everything is availaible in the ubuntu repos, and will install from dependencies in the package, except the M2crypto which is compiled with tribler so you don't even need to have it installed.
so just remove the wxpython you got from the special repo (wxpython is availaible in default repos), and, did you install M2Crypto yourself ? of with gdebi/dpkg ? anyway you don't need it since it's included in my package.

@TSP
you need to download the special hacked M2Crypto they made (I think it's in their website) and use it with tribler, you don't need to do anything else, just install the other dependencies, and it will work.
As for compiling that special M2Crypto, you will need a lot of packages including python sources (headers) because you are compiling a python module...and you should be careful not to overwrite your current version in Ubuntu (synaptic wont tell you and that may create problems). Other than that it's very easy

Oh, and could someone provide a 64bit package ? I don(t have a machine where I can make it.

---

### Post by TSP on 2006-09-08
Thanks for the info :D

---

### Post by wampirek on 2006-09-08
> **reda_ea said:**
> @wampirek
you don't need to install anything, everything is availaible in the ubuntu repos, and will install from dependencies in the package, except the M2crypto which is compiled with tribler so you don't even need to have it installed.
so just remove the wxpython you got from the special repo (wxpython is availaible in default repos), and, did you install M2Crypto yourself ? of with gdebi/dpkg ? anyway you don't need it since it's included in my package.
So I just removed wxpython (using Synaptic), removed special repos from my sources.list, updated it and installed wxpython again (from Ubuntu repos).
After that I made: *sudo dpkg -i tribler3.5.deb* and then *tribler*
And that's what my Ubuntu returned: 

[I]Traceback (most recent call last):
  File "/usr/share/tribler/abc.py", line 14, in ?
    import wx
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
    from wx._core import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13405, in ?
    from _misc import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc.py", line 4, in ?
    import _misc_
ImportError: /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc_.so: symbol _ZTV11wxLogBuffer, version WXU_2.6 not defined in file libwx_baseu-2.6.so.0 with link time reference[/I]

so I think that version 2.6 of wxpython unicode is not installed :( How should I do it then? 

M2Crypto - dowloaded [http://wiki.osafoundation.org/pub/Projects/MeTooCrypto/m2crypto-0.16.tar.gz](http://wiki.osafoundation.org/pub/Projects/MeTooCrypto/m2crypto-0.16.tar.gz) and installed: 

[I]python2.4 setup.py build
python2.4 setup.py install[/I] 
Should I remove it? How? 

I know that these are probably basic questions, but as I said before, I'm new with linux...

---

### Post by TSP on 2006-09-08
reda here is another similar client based in abc (is more like utorrent)amd you can build it the same way you do with tribler, if you have time can you make a deb for us? Thanks in advance!

[http://bit-torrent.sourceforge.net/](http://bit-torrent.sourceforge.net/)

Im just build deb of libtorrent and btg (another bittorrent client) i have deb of rtorrent, ktorrent and a couple of other bittorrent client for ubuntu if anyone's want it, give me advice please :D

---

### Post by wampirek on 2006-09-09
> **TSP said:**
> reda here is another similar client based in abc (is more like utorrent)amd you can build it the same way you do with tribler, if you have time can you make a deb for us? Thanks in advance!

[http://bit-torrent.sourceforge.net/](http://bit-torrent.sourceforge.net/)

Thank you, thank you very much! Torrent swapper works fine :) Tribler still shows error message, but Swapper downloads and uploads very well :) 
I had to install wxPython from Starship repository again, but it was worth it :-D 
Startind it from command line is uncomfortable, but at least, it works 8)

---

### Post by jamesford on 2006-09-09
i guess an amd64 deb of one of these is too much to ask for?

---

### Post by TSP on 2006-09-09
> **wampirek said:**
> Thank you, thank you very much! Torrent swapper works fine :) Tribler still shows error message, but Swapper downloads and uploads very well :) 
I had to install wxPython from Starship repository again, but it was worth it :-D 
Startind it from command line is uncomfortable, but at least, it works 8)

Glad i can help you :D i try to use swapper but i can't i need m2crypto a special version, i can't find it.
I would be great if you can tell me how i can make this client to work

PS.you don't need to start the client froma  terminal, make a link o something liek that whith the same comand you use to start it ;)

---

### Post by alexandermimix on 2006-09-09
```
sudo dpkg --force-architecture -i tribler_3.5.0-0ubuntu3_i386.deb
``` ?

unfortunatly doesnt work (I installed the dependancies... anyone have a 64bit deb file?

---

### Post by wampirek on 2006-09-10
> **TSP said:**
> Glad i can help you :D i try to use swapper but i can't i need m2crypto a special version, i can't find it.
I would be great if you can tell me how i can make this client to work
M2Crypto - I dowloaded it from here: [http://wiki.osafoundation.org/pub/Projects/MeTooCrypto/m2crypto-0.16.tar.gz](http://wiki.osafoundation.org/pub/Projects/MeTooCrypto/m2crypto-0.16.tar.gz) 

unpacked, entered its directory and installed:
[I]python2.4 setup.py build
python2.4 setup.py install[/I]

I hope it helps you :) 

BTW - I don't know how to make a link to swapper. When I want to start it, first I must enter its directory and then write *python2.4 abc.py*. How should I create a link for this?

---

### Post by TSP on 2006-09-10
I have TW working :D

I made this to launch Swapper. first add this script in your home folder

```
#!/bin/sh
#

cd /where/you/whave/swapperfolder
exec python2.4 abc.py

```

Save it as **.swapper.sart** for example, give it exec permisions (nautilus, right click in this file)
and then just edit your menu and in comand point this file, give it a name and you have a laucher :D

---

### Post by wampirek on 2006-09-11
> **TSP said:**
> 
```
#!/bin/sh
#

cd /where/you/whave/swapperfolder
exec python2.4 abc.py

```

O! Thank you **very much**! It works fine :) 

Successful downloading then :)

---

### Post by Janoubie on 2006-11-04
frindes .. is there any steps for us ( new linux user ) like code copy and paste in terminal :)

---

### Post by Cheizzz on 2006-11-21
How come I have to be root to run Tribler? I'm not all comfortable with that.

---

### Post by Peturrr on 2006-12-11
I do want to warn people. This project is from my University (TU Delft) and in the news they were also saying that his next level client/protocol was designed to monitor people/ to make it easier to convict people for illegal filesharing. So, a little caution.

To back this up: A quote from one of the developers
"Tribler wil het maken van illegale kopieën ontmoedigen door het bijhouden van gegevens en de geschiedenis van gebruikers, aldus promovendus [Pawel Garbacki]("http://pds.twi.tudelft.nl/%7Epawel/") van Elektrotechniek, Wiskunde en Informatica tegenover Delta. "Bij Bittorent is iedereen anoniem, dat is een heel ander verhaal.""

Translated:
"Tribler wants to discourage the creation of illegal copies by storing data and history of the users, according to PHD Pawel Garbacki. At Bittorrent networks, everybody is anonymous, this is a completely different story."

---

### Post by Flash_Mordon on 2006-12-15
This might also be of interest to those using Torrent Swapper:

"Using our software increases your tracability. Every Torrent Swapper client installation has a unique identifier based on Elliptic Curve Cryptography, which helps the software to keep track of friend and foe. In the past, we have conducted the largest crawl of the Bittorrent P2P system. We will also be crawling the network in order to detect any inefficiencies and shortcomings in our P2P software. However, this will also show us how the software is used, including the occurrence of illegal activities."

Found here: [http://bit-torrent.sourceforge.net/disclaimer.php]("http://bit-torrent.sourceforge.net/disclaimer.php")

---

### Post by FaceorKneecaps on 2006-12-22
or an apt-get tutorial....

---

### Post by synctext on 2007-03-05
Hi All,

A message from the Tribler developers. . .

We are getting close to a big new release of 
Tribler. Our source code in the Dev Wiki:
[https://dev.tribler.org/browser/abc/branches/mainbranch]("https://dev.tribler.org/browser/abc/branches/mainbranch")
is getting cleaned of the last bugs.

We will soon create an Release Candidate 1 and
enter a week of testing. Is anyone interested in
doing some Beta testing and giving us detailed feedback ?

Greetings from Holland,
Johan.

Assistant Professor Dr. J.A. Pouwelse
Delft University of Technology

---

### Post by synctext on 2007-03-28
Hello All,

A message from the Tribler developers. 
Tribler 3.6.0 is released now and tested to
work on Ubuntu.

Download link : [Source code]("http://sourceforge.net/project/showfiles.php?group_id=159448&package_id=178952&release_id=495616")

Ubuntu repository; add to /etc/apt/sources.list the line :
deb [http://debian.tribler.org/debian](http://debian.tribler.org/debian) testing main  #or unstable

[digg.com news article link]("http://www.digg.com/offbeat_news/Tribler_3_6_0_4th_gen_file_sharing")

Please post a message here if you run into problems.

Have Fun,
Dr. Ir. J.A. Pouwelse
Assistant Professor, P2P specialist
Delft University of Technology

---

### Post by tripmix on 2007-04-03
I had hoped this could help me with my debian64 torrent problems but no such luck. The package above complains that python2.4-m2crypto-ec don't exit in my repositories and when using the source to run it it uses 100% cpu and 50% mem and thats way worse than what I'm stuck whit now, bittornado. utorrent is the one thing I miss about win. I sure hope there will be usefull bt app for linux64 out there soon, every thing Iv tried for the last 6 months uses way to much of my system resources or don't have the ability to select files.

---

### Post by rodrigo666 on 2007-04-03
Yeah, I also miss uTorrent so badly.

When some one is gonna do a uTorrent clone for Linux?

Every other goddamn bittorrent client sucks in Linux!!!:mad: 

Azureus - weights more than a blue whale and has more bugs than a dirty restaurant;

Ktorrent - it's okay, **if you use KDE**, wich is not the case of mostly Ubuntu users (I guess), for me it didn't worked well with Gnome since I could not managed to make my temp Directory in another partition not my "/home/";

Deluge - it's almost okay, but it does not have the option to select the files to download and don't get good speeds also;

rTorrent - c'mon, do you really find that non-gui interface user-friendly? Give me a break!;

Bittornado - Can this be called a client? Do you really think so?;

Frostwire - almost work well, but lacks the ability to choose files to download and does not have a good speed also;

Transmission - excellent speed of download, but lacks the ability to choose the files and other useful features.

I'm stuck with Transmission while I wait for some Linux uTorrent clone.

---

### Post by rodrigo666 on 2007-04-03
Oh, and by the way, I forgot to mention Tribler:

When I try to run it, this is what I got:
> 
rodrigo@ubuntu64:~$ tribler
ls: /usr/lib/python2.4/site-packages/wx-2.6*: Arquivo ou diretório inexistente
Hmmm... No wxPython unicode package found for python2.4, cannot run Tribler, sorry
exit: 13: Illegal number: -1

---

### Post by mykalreborn on 2007-04-04
> Deluge - it's almost okay, but it does not have the option to select the files to download and don't get good speeds also;
you can choose which files to download with deluge. maybe you have an older version of it.

---

### Post by rodrigo666 on 2007-04-04
> **mykalreborn said:**
> you can choose which files to download with deluge. maybe you have an older version of it.

Hmm, I will search for that new version as soon I get home (in work now), just hope they get a better download speed, since deluge was around 35 kb/s and transmission gets around 65 kb/s.

---

### Post by tripmix on 2007-04-04
I have very similar experiences whit debian testing amd64. 

Many of the apps I try have some bugs or something that messes up down/up speed.

For example ktorrent refuse to upload more than a few kbs, and whit azureus back when it 

worked made my up/down speed go to full speed for a minute before went down to 0 for 

about a minute and back up again.

So far bittornado is the only client that down/upload normally on my system, the downside is 

that it can only have one torrent per instance and the more you open the more resources it 

uses. Open 3 and leave them running for a day or so and all my mem and swap is gone. It 

also lack support for UPnP witch leave my system open unless i close the ports manually.

It sounds to me that ubuntu have more luck here, do anyone have any experience whit both 

and can tell me if this is true?

If I wanted to try ubuntu could I just change my sources.list to ubuntu sources and do a 

apt-get dist-upgrade?

PS: text was much easier to read with spaces between lines, good thinking :D

---

### Post by jdsampayo on 2007-04-06
> **rodrigo666 said:**
> Yeah, I also miss uTorrent so badly.
When some one is gonna do a uTorrent clone for Linux?

...

I'm stuck with Transmission while I wait for some Linux uTorrent clone.

Hello everyone! My first post! :D

If you miss much uTorrent like myself, well I'm actually running uTorrent in Ubuntu with wine and all works well, It takes a considerable time to startup, but then all it's ok. And I get the maximum speed available in my network connection. No much memory and CPU usage like Azureus. For me, it runs just like in Windows, you have all the features available.

---

### Post by synctext on 2007-04-06
> **tripmix said:**
> my debian64 torrent problems; complains that python2.4-m2crypto-ec don't exit.

Hi Tripmix,

We should be able to fix your problem(s)...
Can you de-install m2crypto libs on you box ?
There probably is an older "non-ec" installation mixing up things.
Then please install the new M2Crypto from our
server; such as this unstable/amd64 version :
[http://debian.tribler.org/debian/dists/unstable/main/binary-amd64/m2crypto-ec_0.15-3_i386.deb](http://debian.tribler.org/debian/dists/unstable/main/binary-amd64/m2crypto-ec_0.15-3_i386.deb)

If you run into WxWindows errors :
[http://debian.tribler.org/debian/dists/unstable/main/binary-amd64/wxpython2.6-gtk2-ansi_2.6.2.1-2_i386.deb](http://debian.tribler.org/debian/dists/unstable/main/binary-amd64/wxpython2.6-gtk2-ansi_2.6.2.1-2_i386.deb)

Hope that works for you . . .

Greetings,
Johan.

Dr. Ir. J.A. Pouwelse
Assistant Professor, P2P specialist
Delft University of Technology

---

### Post by brodiepearce on 2007-04-08
Does Tribler support importing partial downloads, or does it have a plugin that can do so?  If so I'm sold. ;)

---

### Post by Hangly on 2007-04-17
> **rodrigo666 said:**
> Oh, and by the way, I forgot to mention Tribler:

When I try to run it, this is what I got:

rodrigo@ubuntu64:~$ tribler
ls: /usr/lib/python2.4/site-packages/wx-2.6*: Arquivo ou diretório inexistente
Hmmm... No wxPython unicode package found for python2.4, cannot run Tribler, sorry
exit: 13: Illegal number: -1


This is what I'm getting too.  WTF does it mean?

edit:  I copied wx* from python2.5 to python2.4.  that seems to have worked.

---

### Post by giuliastro on 2007-05-22
One of the two repository doesn't work, the other one misses some dependencies and Tribler doesn't run on Feisty.

---

### Post by gijsbrecht on 2007-05-24
> **giuliastro said:**
> One of the two repository doesn't work, the other one misses some dependencies and Tribler doesn't run on Feisty.

You can get a feisty deb from getdeb.net:
[http://www.getdeb.net/app.php?name=Tribler](http://www.getdeb.net/app.php?name=Tribler)

---

### Post by kruppe on 2007-06-03
Thanks for the recommendation. I'll check out Tribler

---

### Post by luvcash75 on 2007-08-27
Well this is my first ever mention on a ubuntu forum and I am doing this to hopefully help some other newbies like me.
I got so wound up with windows problems over and over I finally took the plunge to Ubuntu 2 weeks ago.  I can only say how pleased, well overjoyed I am that I made the decision to.  It seemed a little daunting and complicated to start with but I soon got the hang of it and it kicks you know what over windows!
Back to what the forum is about.  I have spent so much time with torrents in the last couple of years and on windows there was no question for me that Utorrent was by far the best.  To find initially I couldn't use it on Ubuntu was a real dissapointment so I tried many clients including Ktorrent, Rtorrent, Deluge, Azureus, bittornado and qbittorrent.  I don't have the worlds best download speed the differences between them was often vast. 
I then found I could use Utorrent under Wine which as a Newbie was awkward at first but I figured it out.  It seemed good at first but the speeds were very up and down.  I went back to Deluge and found it was so slow but most stable.
I still wasn't happy so I did some further research and there seemed to be a lot of mention for Transmission although I couldn't find an easy download for it.  I did finally find one and what can I say.  Well finally I have found a torrent that gets me over 200kbs constant again and doesn't take all my resources to do so.  
My million percent recommendation to anyone new is transmission, it pickss up very quickly and holds a very solid and constant full throttle speed.  The link I found for download is on this page:

 [http://www.techystuff.info/?p=96](http://www.techystuff.info/?p=96)

I hope this will help someone who struggled as much as I did.

Thanks

Lee :)

---

### Post by DarkDancer on 2007-08-28
Can you use Tribler like a standard bittorent client? I.E. can I point FireFox at it and then click the torrent in FireFox? I tried, but I can't find the actual program itself (It must be there somewhere.)

Other than that I like it quite a bit. I did use Azureus, but the last updat I got made it slow my system down to a complete crawl, to the point where I had to kill the desktop to stop it running (this would happen within 2 minutes of starting Azureus).Tribler slows it down too, once it gets really going on a downwload, but not nearly as much....

---

### Post by Sushubh on 2007-09-01
i am using it and it is damn slow on my ubuntu. p4 1.8 and 1 gig RAM. :(

plus the UI messes up a lot of time requiring a kill switch.

[IMG]http://i9.tinypic.com/67f5p3s.png[/IMG]

---

### Post by reda_ea on 2007-09-16
> **luvcash75 said:**
> The link I found for download is on this page:

 [http://www.techystuff.info/?p=96](http://www.techystuff.info/?p=96)

I hope this will help someone who struggled as much as I did.


[www.getdeb.net](www.getdeb.net) has it too

---

### Post by ray1claw on 2007-10-23
hey fellas... i downloaded tribler 4.1.7 deb from tribler.org... and ive been runnin it over nyte... all the downloads seem to start well... they keep running at nice speeds and all... but when the next day i wake up and chek on it... i find it all screwed up... i realize that nuthin has downloaded... all the downloads r bak to 0% and they r starting all over again... this is bad... cuz i usually download loads of stuff which doesnt complete in a day with my shitty speeds... but if theres nuthing like continuing its own partial downloads then wats the use... i guess ill switch over to azureus or transmission now... 
i like the tribler concept and i wanna use it... so pls reply fast....

---

### Post by 1jackjack on 2008-03-17
Just to boost this thread up to date, the new deluge is the way forward. I would say it is by far the closest to a Linux port of uTorrent. It has all the features I used in uTorrent (except for labels, but they are planned for the next release), and it is lightweight, and maxes out my connection!

Just my 2 cents,
Jack

---

### Post by mefi on 2008-07-17
which one out of rTorrent, Transmission and Azureus is most alike uTorrent?

---

### Post by rodrigo666 on 2008-07-18
> **1jackjack said:**
> Just to boost this thread up to date, the new deluge is the way forward. I would say it is by far the closest to a Linux port of uTorrent. It has all the features I used in uTorrent (except for labels, but they are planned for the next release), and it is lightweight, and maxes out my connection!

Just my 2 cents,
Jack

Does it have "Force Re-Check"? Because that feature is really handy and I don't recall to have in the previous releases.

---

### Post by whitethorn on 2008-07-18
> **rodrigo666 said:**
> Does it have "Force Re-Check"? Because that feature is really handy and I don't recall to have in the previous releases.

I have the version 0.5.9.1 which I believe is the actual one, and it does have a Force ReCheck option.

---

### Post by L815 on 2008-07-19
I was always a Azureus fan because it's open source and has unlimited amount of options.

Until that is I can to Ubuntu and got to use Transmission.
The newest version 1.22.x is awesome. 

It's simple, accepted by all the trackers I've come by.
Has built in Blocklist options
Runs without much footprint
I like how the GUI is put together


So for me IN ORDER:
-Transmission
-Azureus (Now Vuze -_-)
-Deluge
-uTorrent (via Wine)

---

### Post by clio on 2008-07-23
Hello.
rtorrent with rssdler040 are fast as utorrent :)

---

### Post by jlfallaw on 2008-11-27
Sorry, but the whole 'social sharing' thing is too much. As someone who has had trouble with ISPs getting all up in my business about file sharing, I prefer as much anonymity as possible in a torrent client. I don't need to add friends or even see any information about who I'm sharing with.

---

### Post by add1kt on 2009-03-17
For what it is worth, here is a simple test I ran on my 3 favorites: vuze, deluge, tribler

Numbers rounded to nearest min/KB

Tribler: LinuxMint-- 20 min. @ 568KB/s avg. peaks around 700K
Vuze: LinxMint-- 18 min. @ 631KB/s avg. peaks around 900K
Deluge: LinuxMint-- 21 min. @ 541KB/s avg. peaks around 700K

Notes:  Vuze and Tribler screamed to respective avg. speeds, Deluge took the longest to get up to speed.
	Tribler is the least refined with the least amount of configurablility. A bit heavy on CPU usage
	Vuze use the most resources (CPU/RAM), most configurable.
	Deluge is the lightest and most resource friendly of the three, still a lot of configurability.

Trial two, smaller file fewer seeders.

Tribler: File 2-- 8 min. @ 156KB/s avg. peaked around 350K during the last minute.
Vuze: File 2-- 10 min. @ 125KB/s avg. peaked around 250K.
Deluge: File 2-- 11 min. @ 113KB/s avg. peaked around 250K during the last minute.

This seems to go with what I have experienced, generally vuze/azureus has been fast for me, i dont know much about deluge, and tribler which I am new to seems to do better when there are less seeders.  But this test is not all inclusive and far from perfect.  Just my brief experience.

---

### Post by shadowlands on 2009-04-21
i loaded this up and now i get an error message.  How do I remove it?

---

### Post by Arup on 2009-04-22
I vote for the latest Transmission, it works as good and fast as uTorrent which I use in Windows, the added feature of IP address and auto update of IP address is a boon, one which even uTorrent lacks and only Azureus accomplishes via safe peer plugin. Transmission is written in C and therefore is as light and stable as uTorrent and far less resource hungry than Java based Azureus or Python based Deluge.

---

### Post by rpgaction on 2009-05-23
I just tried installing the latest stable version of Tribler, but when I go to launch it, nothing happens at all. Like seriously, nothing at all. Anybody have any suggestions?

---

### Post by NFblaze on 2009-05-26
try starting it from the terminal. It might output an error that you can cross-reference on the forums.

---

### Post by synctext on 2009-06-16
Anybody got the latest V5.1 working on their Ubuntu box?
Works for me.. *changelog: content search takes less then 1.5 seconds*
Details : [http://p2p-blog.com/index.php?itemid=1082](http://p2p-blog.com/index.php?itemid=1082)
-j

---

### Post by add1kt on 2010-05-17
Deluge, by far my new favorite

---

### Post by Grenage on 2010-05-17
*Angry necromancer hits **YOU** for 9001 damage!*

---

