---
title: "Torrent Swapper Install how-to."
date: 2006-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by turbojugend_gr on 2006-10-15
If you were always wishing for a proper torrent client for your ubuntu installation, finally there is one! Which one? -> **Torrent Swapper**, the social bittorent client. Here are some links for you to check it out. Hopefully it will enter the Repos.

[Home]("http://bit-torrent.sourceforge.net/")
[wikipedia topic]("http://en.wikipedia.org/wiki/Torrent_Swapper")
[and also check out a wikipedia comparison of almost all clients]("http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software")

OK if you think now it worths the trouble let's go on. I believe the documentation sucks, and since there is no deb out there, here is a walk through.


**1**. Download the tarball from the official site.

**2**. Extract it where it suits you. (I prefer a ~/Apps/Swapper location)

**3**. Open up Synaptic and install the following packages: 
-openssl
-swig
-python
-python 2.4
-python-wxversion
-python-wxgtk2.6
-libwxgtk2.6-0
-libwxbase2.6-0
-python-m2crypto

**4**. After you have successfully installed all the dependancies above, navigate into the folder you have previously created, containing the Torrent Swapper untared files. There find the file *abc.py* click properties and make it executable (as program).

**5**. In a terminal navigate to the above folder and type "*./abc.py*". ENJOY !

**6**. (OPTIONAL): If you wish to create a script to simply start Swapper with one command in a terminal type "*sudo gedit /usr/bin/torrentswapper*" there copy/paste the following:
```
#!/bin/bash

cd PATH_TO_THE FOLDER_CONTAINING_TORRENT_SWAPPER && ./abc.py

```Of course put the appropriate path there, save and exit *(don't forget to make /usr/bin/torrentswapper executable too)*. Now every terminal, or launcher given "torrentswapper" starts this amazing application.

I hope it helps somebody.

P.S.: Notice I am far from being called an expert, but I will try to help as much as possible with questions _regarding the installation_ progress.

---

### Post by turbojugend_gr on 2006-10-16
OK 12 people at least have seen this thread, I hope it worked for you , but plz post if it did, so I know if it is working, as I only done this in two edgy machines. Thank you in advance.

---

### Post by viciouslime on 2006-10-16
This is an excellent torrent client, thanks! I've been looking for a replacement for &#956;torrent for aaaaages now and I think this might just be it. Thanks again :D

---

### Post by ~LoKe on 2006-10-16
Works fine for me in Edgy. I'll try it out for a few days.

**EDIT:** The tray icon is much too large.

---

### Post by turbojugend_gr on 2006-10-16
> **~LoKe said:**
> Works fine for me in Edgy. I'll try it out for a few days.

**EDIT:** The tray icon is much too large.

yup, the tray icon is streched, I can't tell why... I just came to only use this when minimized... I hope someone finds a workaround for this, I can't... Glad it worked for you tough!

---

### Post by Jsmith on 2006-10-17
Since I booted M$ XP out the door, I've been looking for a Azureus replacement (being it's buggy to me in edgy)

Torrent Swapper isn't as customizable as Azureus, but it's clean and stable

---

### Post by bruenig on 2006-10-18
No RSS integration and broadcatching? That is all that is needed for utorrent to be trashed.

---

### Post by redman5087 on 2006-10-18
I get the following error on ubuntu dapper

Traceback (most recent call last):
  File "./abc.py", line 23, in ?
    from interconn import ServerListener, ClientPassParam
  File "/home/redman/swapper/interconn.py", line 5, in ?
    from Utility.helpers import getSocket
  File "/home/redman/swapper/Utility/helpers.py", line 15, in ?
    from BitTornado.download_bt1 import defaults as BTDefaults
  File "/home/redman/swapper/BitTornado/download_bt1.py", line 7, in ?
    from BT1.Choker import Choker
  File "/home/redman/swapper/BitTornado/BT1/Choker.py", line 7, in ?
    from Swapper.toofastbt.Logger import get_logger
  File "/home/redman/swapper/Swapper/__init__.py", line 22, in ?
    import Overlay.permid as permid
  File "/home/redman/swapper/Swapper/Overlay/permid.py", line 10, in ?
    from M2Crypto import Rand,EC,EVP
ImportError: cannot import name EC

---

### Post by dannyboy79 on 2006-10-18
bittornado is the bomb!

---

### Post by turbojugend_gr on 2006-10-19
> **redman5087 said:**
> I get the following error on ubuntu dapper

Traceback (most recent call last):
  File "./abc.py", line 23, in ?
    from interconn import ServerListener, ClientPassParam
  File "/home/redman/swapper/interconn.py", line 5, in ?
    from Utility.helpers import getSocket
  File "/home/redman/swapper/Utility/helpers.py", line 15, in ?
    from BitTornado.download_bt1 import defaults as BTDefaults
  File "/home/redman/swapper/BitTornado/download_bt1.py", line 7, in ?
    from BT1.Choker import Choker
  File "/home/redman/swapper/BitTornado/BT1/Choker.py", line 7, in ?
    from Swapper.toofastbt.Logger import get_logger
  File "/home/redman/swapper/Swapper/__init__.py", line 22, in ?
    import Overlay.permid as permid
  File "/home/redman/swapper/Swapper/Overlay/permid.py", line 10, in ?
    from M2Crypto import Rand,EC,EVP
ImportError: cannot import name EC

Are you sure you have installed all the dependencies?
IF you are sure you haven't missed any from the dependencies in my first post, try a dist upgrade. If both fail to solve this issue, plz copy-paste again the errors you get, starting from the line you issued the command not from the line the errors start. I hope we 'll get this solved.

---

### Post by turbojugend_gr on 2006-10-19
> **dannyboy79 said:**
> bittornado is the bomb!

Bittornado is nice , it is getting decent speeds, but it's gui lacks usability. But this one, Torrent Swapper, has a much more professional approach, has a very nice gui, is getting very nice speeds and on top of all those it's "social" features let you know from whether the torrent is appreciated/or dead, up to using someone else upload rate to increase your own! All this make it very attractive to me.

However, it's a matter of taste, you should use what suits you. ;)

---

### Post by turbojugend_gr on 2006-10-19
> **Jsmith said:**
> Since I booted M$ XP out the door, I've been looking for a Azureus replacement (being it's buggy to me in edgy)

Torrent Swapper isn't as customizable as Azureus, but it's clean and stable

Yup, it is stable and clean... but as if you llok at the links in my first post, or explore the app a bit... you will see it is much more than that! (btw it is using much less sources than azureus too..)

I am glad you enjoy it! :)

---

### Post by dannyboy79 on 2006-10-19
> **turbojugend_gr said:**
> Bittornado is nice , it is getting decent speeds, but it's gui lacks usability. But this one, Torrent Swapper, has a much more professional approach, has a very nice gui, is getting very nice speeds and on top of all those it's "social" features let you know from whether the torrent is appreciated/or dead, up to using someone else upload rate to increase your own! All this make it very attractive to me.

However, it's a matter of taste, you should use what suits you. ;)

What other features besides capping your upload limit and download limit, knowing who your connected to, being able to allow what files out of all the torrent files you want to download, as well as knowing if you're router is blocking incoming connections would you want. Could you explain, "up to using someone else upload rate to increase your own" to me? I find that bittornado doesn't tie up a lot of resources like I have noticed with other clients. Also, some sites you have to sign up for, don't allow just ANY client, the client has to be approved due to people cheating and such.

---

### Post by turbojugend_gr on 2006-10-19
> **dannyboy79 said:**
> What other features besides capping your upload limit and download limit, knowing who your connected to, being able to allow what files out of all the torrent files you want to download, as well as knowing if you're router is blocking incoming connections would you want. Could you explain, "up to using someone else upload rate to increase your own" to me? I find that bittornado doesn't tie up a lot of resources like I have noticed with other clients. Also, some sites you have to sign up for, don't allow just ANY client, the client has to be approved due to people cheating and such.

First of all, you should give it a try yourself, there's no other way you can understand all it's capabilities. The thing is I have nothing to do with this project, so I have no intention of "advertising it". If you find you are ok with bittornado I have no problem with it, it is my previous client after all.

Despite the above, I will try to answer your questions this time. I would like to ba able to know if the torrent I am Downloading is appreciated by other users (TS does that BT not), what similar torrents other users like or suggest to me (again TS does while BT not). I would like to be able to boost my DL rate using someone else's upload rate( which TS all other clients I know of though don't, again). Since you don't seem to at least gave a try, it is reasonable enough you don't know that TS uses slightly less memory than bittornado-despite having by far a more feature-packed and graphics-packed gui, and using itself python too (in my system TS -25 to 28 mbs while BT 23 up to 34 mbs). Finally I would like a gui that shows all torrents active-or not in one window... as all advanced clients do.

In specific, the "using someone else's ul rate to boost your dl" given the fact I have nothing to do with the project-I can't explain at all how it is succeeded, I just know I am using my friends UL rate (using Torrent Details>>Download Boosting and adding my friends there). So simple. At least it suits me!

My goal, is not to spread the use of TS, by any means, I just wanted to help other users install what I think to be the nicest Linux Torrent Client (if not of any OS)-which was a pain in the *** to me, as it lacked in documentation. I am happy if I do that. If you don't wish to try this- I am with you, after all I used BitTornado the last year too, and I liked it. I don't see any point though for you to point out that BT is the best---given the fact it is clear you haven't at least used TS.

P.S.: That goes for everyone using this thread, I have nothing to do with the project, I am just a very happy user, who tried to help others enjoy what he is enjoying himself.-

P.S.2: @dannyboy79-> I don't see any reason to be caught in a lengthy debate, use whatever suits you, if you wish to discuss which client is best create a thread for it, I 'll be happy to contribute my opinion. This thread is created for TS how-to install, so such comments have nothing to do with the subject, thus I won't take them into account again, you can invite me or any other user to prove your views elsewhere.
Regards, Tubojugend.

---

### Post by Peter76 on 2006-10-19
This sounds a lot like the tribler program... Is this a fork of it?

Edit:

Just dled it and ran it; this is the same as tribler, only some other icons. Wonder what happened here

Edit again:

READ THE DISCLAIMER AT THE HOME PAGE

"In the past, we have conducted the largest crawl of the Bittorrent P2P system. We will also be crawling the network in order to detect any inefficiencies and shortcomings in our P2P software. However, this will also show us how the software is used, including the occurrence of illegal activities."

Tribler states the same at their website.

What IS happening here? Or am I just Paranoid?

---

### Post by turbojugend_gr on 2006-10-19
@Peter76: I am sorry, I have no information on this, maybe you are right. I can't still make out why is this so important? Plz help me with this :)

---

### Post by Peter76 on 2006-10-20
Hi Turbojugend, don't be sorry;-), your how-to is really good, it's the software that concerns me... I did some googling yesterday but not a lot came up. I just thought it strange that two programs use almost exactly the same codebase and nothing is mentioned.
Then I came across the disclaimer; here is the complete one for reference:

"Using our software increases your tracability. Every Tribler software installation has a unique identifier based on Elliptic Curve Cryptography, which helps the software to keep track of friend and foe. In the past, we have conducted the largest crawl of the Bittorrent P2P system. We will also be crawling the Tribler network in order to detect any inefficiencies and shortcomings in our P2P software. However, this will also show us how the software is used, including the occurence of illegal activities."

What I read here is that it is possible to exactly show what every client is doing, which is a feature that could be used by the law...
Anyway, as all of us probably never do anything illegal with torrent clients...., this doesn't offer any real privacy.

Well, that's what I make from it... for me it is enough to stop using tribler/swapper, which I really liked.
Hope somebody can prove me wrong or reads this in a different way, and hope I explained my concerns a bit better to you.

---

### Post by Zorro on 2006-10-20
charles@charles-desktop:~/Desktop/torrent$ ./abc.py
Traceback (most recent call last):
  File "./abc.py", line 23, in ?
    from interconn import ServerListener, ClientPassParam
  File "/home/charles/Desktop/torrent/interconn.py", line 5, in ?
    from Utility.helpers import getSocket
  File "/home/charles/Desktop/torrent/Utility/helpers.py", line 15, in ?
    from BitTornado.download_bt1 import defaults as BTDefaults
  File "/home/charles/Desktop/torrent/BitTornado/download_bt1.py", line 7, in ?
    from BT1.Choker import Choker
  File "/home/charles/Desktop/torrent/BitTornado/BT1/Choker.py", line 7, in ?
    from Swapper.toofastbt.Logger import get_logger
  File "/home/charles/Desktop/torrent/Swapper/__init__.py", line 22, in ?
    import Overlay.permid as permid
  File "/home/charles/Desktop/torrent/Swapper/Overlay/permid.py", line 10, in ?
    from M2Crypto import Rand,EC,EVP
ImportError: cannot import name EC
charles@charles-desktop:~/Desktop/torrent$



Is what I get :/   I have all the dependencies from your 1st post... So not sure where to go now :(


Thanks for the effort in posting also...

---

### Post by bionnaki on 2006-10-20
does torrentswapper work with oink?

---

### Post by turbojugend_gr on 2006-10-21
@ Peter76: Well, you should know, that it it is the protocoll (bittorrent) itself that lacks anonymity, and it is stated too many times. Google it up and you will see it has nothing to do wit the clients. Another thing is that alll clients, if you check so, can show you peers/seeeds you are connencted to, along with their ip number, so it has nothing to do with the client, the only thing Swapper does more, is it allows you to chat and interact with other users.

Bottom line is, bittorrent p2p protocol is the one lacking anonymity, and everyone can watch at anytime what ip's are downloading what files. Again there's nothing in common to me between those two apps, but then again it is only trivial.

Hope I made things easier for you ;).

---

### Post by turbojugend_gr on 2006-10-21
@Zorro: Hmmm... well try giving this a try, because I am unsure about how the ~/Desktop folder is managed, as it is not a usual catalogue, try to untar the tgz in a folder similar to what I said in my post (in a usual folder in your home anyway), the most probable thing is you won't have this solved, but for now it tricks me that you use such a location (~/Desktop is accessed in many ways, and I am not sure it has the needed "rights", but instead of getting caught in changing the rights in such a folder just untar again in another and since you want it to be visible on your desktop use a symbolic link instead.)

---

### Post by DagMan on 2006-10-21
I cant meet these 2 dependencies in dapper.

-libwxbase2.6-0
-python-m2crypto

the second one is available as m2crypto and the description implies that it could be the package I need.

I can't get libwxbase2.6-0.  I downloaded what was available, a 2.4 version, but it didn't work.  The error at the command line was while trying to import a module called EC.

---

### Post by turbojugend_gr on 2006-10-22
@Dagman: Install the m2Crypto, is the one needed. As for the Libwxbase2.6-0, hmmm.... I believe that it is not needed, given the info I 've gathered about it (short story it is supposed to be used for non-gui apps, instead libwxgtk2.6 is fo the gui ones) and I believe you have the latter. So rty installing m2crypto, all other deps fullfilled and you should work.

P.S.: When I am 100% sure 'bout this, I will remove the dep from the how-to.

---

### Post by Peter76 on 2006-10-22
@turbojugend: Thanks for your explanation, didn't know this was a problem with the bittorrent protocol... And nice I can use swapper/tribler again;-)

---

### Post by turbojugend_gr on 2006-10-23
@Peter76: Glad to help!

P.S: I can't seem to find anything in common for those 2 apps, can you gimme a link that shows evidence of this?

---

### Post by Peter76 on 2006-10-23
I can't give you a link, because I can't find anything on the subject, weird... If you compare the two source packages, you'll see almost everything is the same except the name... In the swapper package there's even a bit of tribler artwork left: swapper.xpm.
Even a lot of texts on the website are exactly the same.

---

### Post by DagMan on 2006-10-23
I found that the dependancy problems were either a problem with my sources.list or that Edgy has the needed packages and Dapper does not.

Have it installed but haven't used it yet, but thanks!

---

### Post by markster23 on 2006-10-23
can somebody post a screenshot ??

---

### Post by Somniis on 2006-10-23
Thanks for the excellent guide!  It runs great.

The only problem is that it won't download anything at all.  I'm behind a router and have forwarded the port, but it will not transfer any data.  Any suggestions? :???: 

To markster: Here's a screen of it.
[http://i48.photobucket.com/albums/f216/Somniis/Swapper.png](http://i48.photobucket.com/albums/f216/Somniis/Swapper.png)

(photobucket resized it)

---

### Post by turbojugend_gr on 2006-10-23
@peter76: Hmm, it seems they have changed the name and made a new start for some reason (did tribler have also "social" feautres?), but since it is a new app, you are among the first to dicover taht, so the lack of referances is logical. IF tribler had not social features then it seeems they changed the name and started over so on a new basis. You are pretty sharp with details m8, nice ;).

---

### Post by turbojugend_gr on 2006-10-23
@DagMan: nice, since you got it solved. Enjoy urself with that amazing client, use it social feautures too...

---

### Post by turbojugend_gr on 2006-10-23
@Somniis: Thank you m8, glad to help!

IF you have a port forwarded properly (let's say port 12345), you should place this in the preferences of TS. Assuimng that you have tried that allready, another suggestion would be to try a very "healthy" torrent, which should give you great speeds. If both are not the case, you might got (in a strange way) libtorrent uninstalled (unusual case)... keep posting.

---

### Post by Somniis on 2006-10-23
> **turbojugend_gr said:**
> 
IF you have a port forwarded properly (let's say port 12345), you should place this in the preferences of TS. Assuimng that you have tried that allready, another suggestion would be to try a very "healthy" torrent, which should give you great speeds. If both are not the case, you might got (in a strange way) libtorrent uninstalled (unusual case)... keep posting.

I have placed this in the pref. and am pretty sure I set up the forward correctly (have done it many times in Windows via my router).

I went to thepiratebay.org and downloaded the torrent with the most seeds (and leechers) I could find, just to test it out.  It's running now, but at < 1kb/s.  I've tried Azeureus (sp) as well as the client that comes with Ubuntu, but all have really crappy speeds.  Perhaps I do have libtorrent uninstalled, lol, I have no idea why it is not getting full speeds. ](*,)

Would UPnP have anything to do with this?  I don't have it enabled in my router.

Edit: I checked Synaptic and I do not have the libtorrent7 packages installed.  I'll download them and see if it helps anything. :)

Edit again: Doesn't help.  I'm all out of ideas now. :mad:

---

### Post by turbojugend_gr on 2006-10-23
Since I ain't able to think of sth else, and for you to get better help, I suggest that you should start a thread about this issue, I will closely watch it. Sorry but it is for your good, I wish I knew more, but I don't ;).

---

### Post by Somniis on 2006-10-24
> **turbojugend_gr said:**
> Since I ain't able to think of sth else, and for you to get better help, I suggest that you should start a thread about this issue, I will closely watch it. Sorry but it is for your good, I wish I knew more, but I don't ;).

It's probably just my network.  Torrent clients ran fine when I had Windows installed, but for some reason they just won't work with Ubuntu.  (I've even tried to use uTorrent via wine, and I still had the same issue)

Thanks for your help, regardless. :)  I'll try a few more things, and if it still isn't resolved, ask for more help on here.

---

### Post by turbojugend_gr on 2006-10-24
@Somniis: Oh I forgot! Have you set up a static ip ofr your ubuntu? If not 99% that's the case. To set up a static ip, open networking (system>admin>networking) and there select static ip and provide the appropriate info info. If you wish me to be more specific with sth,ask fo it...

---

### Post by DagMan on 2006-10-24
Sorry to get ahead of you guys but if that isn't the problem or doesn't solve it, perhaps you have a firewall installed such as firestarter that Automatix will put there as part of the security suite, and need to set a rule for the port there too.

Also, I don't know if it was just a matter of a very slow starting torrent or not, but I added my external ip address as well when I wasn't getting anything at first.  This may or may not have been needed.  Usually it is not.  I mention it because I was previously using Azureas and did the same thing with it.

---

### Post by turbojugend_gr on 2006-10-24
@DagMan: it could be what you say, but the thing is that Somniis said he had used windoz before, and haven't mention Firestarter. SO i don't think he would use a firewall and not mention it...anyway most windoz users can't understand they need to set up static ip to get a port forwarded, so I guess that's it, I 'm feeling he will get this solved hopefully. :)

---

### Post by turbojugend_gr on 2006-10-26
> **Somniis said:**
> It's probably just my network.  Torrent clients ran fine when I had Windows installed, but for some reason they just won't work with Ubuntu.  (I've even tried to use uTorrent via wine, and I still had the same issue)

Thanks for your help, regardless. :)  I'll try a few more things, and if it still isn't resolved, ask for more help on here.

OK ,I am 100% you should get a static ip, if you have one ignore this (just make sure that the ports are forwarded for the ip you are using - if you have 10.0.0.18 and the ports are forwarded for 10.0.0.12 for example you have to change one of the two to match the other). If you have this solved let me know.

Anyone else got success with this TS how-to? Join the conversation m8s!

---

### Post by Wiorka on 2006-10-30
Thanks, your how-to worked perfectly for me :) It seems to be a very nice app, I'm trying it out now.

<edit>
As to stretched tray icon...
There are two icons in Swapper folder, swapper.ico and torrenticon.ico. I don't know which one is used in the tray, so I resized both in Gimp to 20x20 pixels, so that it fits nicely in my panel. Not very elegant, but works ;)

---

### Post by RaZoR1394 on 2006-10-31
Thanks for the howto but this app doesn't work properly for me. It seeds very bad, the downloading/seeding algorithm is behaving weird, it fails to launch when you edit the outside and local ip, you can't change priority (doesn't work) and if you look at the Sourceforge page it seems It's violating another projects license (seems to be a ripoff). I'm off with uTorrent now until a decent client comes.

---

### Post by turbojugend_gr on 2006-10-31
@ wiorka : Nice it worked for you, as for the icnos, I tried it in gimp but the image quality was poor. Nice workaround though.

---

### Post by turbojugend_gr on 2006-10-31
M8 you must be unlucky, as me and a couple of friends have never noticed anyone from your issues. As for the license issues I wonder if there is a link you can provie to me, so I can get more info? If it is the tribbler app, there must be a connection within the two apps, can't make out what though... I 'll be checking it.

---

### Post by turbojugend_gr on 2006-11-05
Come on everybody, give it a try, and join the talk, let us know if it worked for you! Or if it didn't...

8)

---

### Post by Mooseus on 2006-11-13
You are a legend my friend! I just made the swap to Linux from Windows XP and have been trying to find a good torrent program that works. I used to use bitlord, but unfortunately it didn't work. Anyway, I had a look at the wiki comparisons of torrent clients and I thought I'd want to give torrent swapper a go. As you said the documentation is pretty crumby and then I found you're how-to. I followed it step by step and it installed fine. I gave it a shot and it works a treat! Thanks again man!

---

### Post by turbojugend_gr on 2006-11-13
I am very glad it worked for you too. You are welcome m8... ;)

---

### Post by Mooseus on 2006-11-16
Now that I've tried to do the optional section so that I can just type "torrentswapper" in the terminal and it works, I get this message:

bash: /usr/bin/torrentswapper: Permission denied

I followed the instructions and typing:

#!/bin/bash

cd home/mooseus/programs/swapper && ./abc.py

after doing the gedit instruction. Any reason why this is happening?

---

### Post by turbojugend_gr on 2006-11-16
You have to make the script-file executable. in a terminal type "sudo nautilus", navigate to **/usr/bin** right click **torrentswapper** and select properties, there under permissions tab make it executable. Close nautilus.

You can now type torrentswapper or create a launcher that does the trick for you, or even better add torrent swapper to your applications/internet menu using right click on the menu, then edit menu. If you need any help ask for it, I 'll be glad to answer back.

Let me know how you did m8, Cheers, TJ.

---

### Post by Mooseus on 2006-11-16
Thanks it works fine, I just added it to my Internet menu.

---

### Post by Pinoy915 on 2006-11-16
I'm behind a router. A Linksys type for that matter. What do I put in the application name so I can forward the ports? For example, the regular bittorrent is Torrent1, bittornado is Tornado1, Azureus is Azur1, etc.

---

### Post by turbojugend_gr on 2006-11-16
Oh m8, I can't be sure for that, but I got a few hints. Torrent Swapper uses bittornado's core for sharing and ABC's code parts too, so try Tornado1 and whatever is for ABC client and see if either can do the trick.

Don't forget to post back here your solution, so others in your position can benefit from it.

I hope I was helpful, TJ.

---

### Post by Pinoy915 on 2006-11-17
Using Tornado1 as the application name and forwarding 6881-6889 seems to be fine.

---

### Post by turbojugend_gr on 2006-11-17
Nice, I am glad I helped. Thank you for posting back too, others will find that handy.

Cheers, TJ

---

### Post by Rule on 2006-11-21
I can't get torrent swapper to run ever since my edgy reinstall. I keep getting this following output, I do have all the needed programs installed...atleast im sure I do.

```
Traceback (most recent call last):
  File "./abc.py", line 23, in ?
    from interconn import ServerListener, ClientPassParam
  File "/home/pezplaya/programs/swapper/interconn.py", line 5, in ?
    from Utility.helpers import getSocket
  File "/home/pezplaya/programs/swapper/Utility/helpers.py", line 15, in ?
    from BitTornado.download_bt1 import defaults as BTDefaults
  File "/home/pezplaya/programs/swapper/BitTornado/download_bt1.py", line 7, in ?
    from BT1.Choker import Choker
  File "/home/pezplaya/programs/swapper/BitTornado/BT1/Choker.py", line 7, in ?
    from Swapper.toofastbt.Logger import get_logger
  File "/home/pezplaya/programs/swapper/Swapper/__init__.py", line 22, in ?
    import Overlay.permid as permid
  File "/home/pezplaya/programs/swapper/Swapper/Overlay/permid.py", line 10, in ?
    from M2Crypto import Rand,EC,EVP
ImportError: cannot import name EC

```

Rule

---

### Post by turbojugend_gr on 2006-11-21
Rule, it seems you don't... plz revisit the first post and install ALL dependancies there, and make sure you install the m2crypto library, as in dapper I think it was under a slightly different name. Also the libsxbase library was somehow tricky in dapper too, so make sure about that alos. Note I just pointed two tricky ones, you need to make sure you install ALL deps.

Cheers, TJ.

---

### Post by dakini on 2006-12-23
If you happen to have Wine installed, Torrent Swapper will run quite fine with it.

---

### Post by Pinoy915 on 2007-06-05
I had it working for a while and now it stopped working. I get a fatal error message.

Here's what pops up: > An error occured during Swapper startup:

<class 'bsddb.db.DBPageNotFoundError'>:(-30987, 'DB_PAGE_NOTFOUND: Requested page not found')

Here's what the terminal puts out:

> carlo@carlo-desktop:~/swapper$ ./abc.py 
Setting up languages
filename: english.lang
Client Starting Up.
Build: Build 1628
/home/carlo/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/carlo/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/carlo/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Preparing GUI.
Got listen port 6881
BuddyCast starts up
Traceback (most recent call last):
  File "/home/carlo/swapper/BitTornado/RawServer.py", line 151, in listen_forever
    func()
  File "/home/carlo/swapper/Swapper/BuddyCast/TorrentCollecting.py", line 125, in collect
    job = self.job_queue.getJob()
  File "/home/carlo/swapper/Swapper/BuddyCast/TorrentCollecting.py", line 69, in getJob
    task = self.fetcher.getTask(self.num_owners)
  File "/home/carlo/swapper/Swapper/BuddyCast/TorrentCollecting.py", line 34, in getTask
    self._reload()
  File "/home/carlo/swapper/Swapper/BuddyCast/TorrentCollecting.py", line 20, in _reload
    empty_torrents = self.torrent_db.getNoMetaTorrents()    #TODO: performance improve - check if db has changed
  File "/home/carlo/swapper/Swapper/CacheDB/CacheDBHandler.py", line 418, in getNoMetaTorrents
    all_keys = self.torrent_db._keys()
  File "/home/carlo/swapper/Swapper/CacheDB/cachedb.py", line 282, in _keys
    return dbutils.DeadlockWrap(self._data.keys, max_retries=MAX_RETRIES)
  File "bsddb/dbutils.py", line 62, in DeadlockWrap
  File "bsddb/dbshelve.py", line 123, in keys
DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')
Traceback (most recent call last):
  File "/home/carlo/swapper/BitTornado/RawServer.py", line 151, in listen_forever
    func()
  File "/home/carlo/swapper/Swapper/BuddyCast/TorrentCollecting.py", line 125, in collect
    job = self.job_queue.getJob()
  File "/home/carlo/swapper/Swapper/BuddyCast/TorrentCollecting.py", line 69, in getJob
    task = self.fetcher.getTask(self.num_owners)
  File "/home/carlo/swapper/Swapper/BuddyCast/TorrentCollecting.py", line 34, in getTask
    self._reload()
  File "/home/carlo/swapper/Swapper/BuddyCast/TorrentCollecting.py", line 20, in _reload
    empty_torrents = self.torrent_db.getNoMetaTorrents()    #TODO: performance improve - check if db has changed
  File "/home/carlo/swapper/Swapper/CacheDB/CacheDBHandler.py", line 418, in getNoMetaTorrents
    all_keys = self.torrent_db._keys()
  File "/home/carlo/swapper/Swapper/CacheDB/cachedb.py", line 282, in _keys
    return dbutils.DeadlockWrap(self._data.keys, max_retries=MAX_RETRIES)
  File "bsddb/dbutils.py", line 62, in DeadlockWrap
  File "bsddb/dbshelve.py", line 123, in keys
DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')
OnInit returned false, exiting...
Exception in thread Thread-11 (most likely raised during interpreter shutdown):
Traceback (most recent call last):
  File "threading.py", line 460, in __bootstrap
  File "threading.py", line 623, in run
  File "threading.py", line 364, in wait
  File "threading.py", line 229, in wait
<type 'exceptions.TypeError'>: 'NoneType' object is not callable
Unhandled exception in thread started by 
Error in sys.excepthook:

Original exception was:
carlo@carlo-desktop:~/swapper$ 

Anyone have any ideas on why it suddenly stopped working? By the way, I'm using Fiesty.

---

### Post by frost_uw on 2008-01-02
About tray icon: to fix this issue, you'll need to resize 'swapper.ico'. It has resolution 48x48, just resize it down to 16x16 (you may use GIMP) or download attachment and unpack it to swapper directory!

---

