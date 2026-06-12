---
title: "Using utorrent with wine"
date: 2006-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by hikitsu4 on 2006-06-07
[LEFT]This shows you how to install and use utorrent with wine in Ubuntu _Dapper_ 6.06 and 
Ubuntu _Edgy Eft_ 6.10 **Note:** At the bottom of the page. (only a section for _fresh_ install for now with Edgy Eft). [/LEFT]
                                                                   
If you want to know what native linux torrent programs is avalible just look at the bottom ;)


The How to: (Ubuntu Dapper 6.06)

First you need to add wine rep into sources.list

Step 1: 

sudo cp /etc/apt/sources.list /etc/apt/sources.backup1

Step 2:

Use one of the following editors.

Gnome editor:

sudo gedit /etc/apt/sources.list


KDE editor:

sudo kate /etc/apt/sources.list
or
sudo kwrite /etc/apt/sources.list


XFCE editor:

sudo mousepad /etc/apt/sources.list


Other graphical editors:

sudo leafpad /etc/apt/sources.list 

** Note: **To get this light editor that looks and feels like notepad do the following

sudo apt-get install leafpad


Command prompt editor:

sudo nano -w /etc/apt/sources.list 


Step 3:

add this at the bottom

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


Step 4:

sudo apt-get update
sudo apt-get install wine
sudo apt-get clean


Step 5:

winecfg


Step 6:

goto "drivers" then press autodetect.

**Note: **Step 7 and 8 isn't needed to start wine, but good to do anyway.


Step 7:

Then goto **"audio"** and remove "OSS driver" and press "ALSA driver" insteed and choose ider default sample 44100,48000 and default bits 16.


Step 8: 

Go go **"Application"** menu then change the "Windows version" from "Windows 2000 to Windows XP", you need to have XP setting on to be able to use "UPNP". But you can have it on anyway even without using that setting, but this how to does **not **cover "UPNP". 

After this wine is installed and configured!


Step 9:

Now you need to download utorrent to your Linux system, or use it with your dual boot windows.

First up dual boot:

make a shortcut at the desktop with favourite window manager.
wine /media/hda1/Program Files/insert your directory/utorrent.exe


Step 10:

Next up is:
If want to just download and use it with Linux without dual boot then the only difference is the folder of choice.

Start your browser and go to [http://www.utorrent.com/download.php](http://www.utorrent.com/download.php) then press "Get µTorrent 1.6 Standalone (170 KB)" then save it to your directory, for example in my case /home/yournickname/program/.

Make a shortcut at the desktop with your favourite window manager.
wine /home/yournickname/yourfolderofchoice/utorrent.exe

** OK** if you followed ider of these two and made it then great!


Step 11:

Then if you click on the shortcut you just made on the desktop then it will start utorrent. After that press not to make torrent files into default, after that the speedguide will start up and guide you, just choose your settings.

Becorse there are so many settings i made some screenshots of my settings, the difference is that you need to choose your settings in the "folders" section. 

** Note:** You can download the file at the bottom of this post.


Step 12:

Ok first up:

Press "Put new downloads in"
Then choose your folder, you cannot choose a NTFS partition becorse it cannot write to it, well anyways this is an example of mine.
h:\torrents

Next up:

Press "Move complete downlods to"
_ Example:_
h:\downloads

And the last:
Press "Store .torrent files in"
_ Example:_
h:\torrents

OK, when you made the settings **"speedguide"+"my screenshot settings"+"folders settings"** you are done! 
_ Remeber_ you got to _start_ the program _then add_ the torrents. 


Step 13:

[LEFT] If you are wondering why you should use utorrent and not the native linux torrent programs, read this:
[/LEFT]
                                         
It uses very little cpu and memory, and works very well with wine in Ubuntu Dapper 6.06 LTS and 6.06.1 LTS, and Ubuntu Edgy Eft 6.10, also it supports DHT, peer exchange, UPNP and RSS.

**Note:** I couldn't get UPNP to work with wine.


It supports also Protocol Encryption (compatible with Azureus 2.4.0.0 and BitComet 0.63) but i think the other person you are downloading from or are seeding to need to have it enabled also if you got it.

Step 14:

[CENTER] IMPORTANT INFO: 


                              If you use firestarter (or any other software/hardware firewall) you need to make port 32459 (or any other port you set) open for incoming connections or you will get super slow download. 

** Note:** utorrent only uses one port for all downloads.
[/CENTER]
                        

Step 15:

sudo firestarter


Step 16:

goto Policy


Step 17:

Right click on allow service then copy/paste 32459 (or any other port you set) into port, then see to that "anyone" is on then press ok. 


Step 18:

Press "Apply policy"


Step 19: 

If you want more information about using utorrent with wine, and possible fixes look at this link:
[http://www.securenet.net/members/jeanpelo/linux_guide.html](http://www.securenet.net/members/jeanpelo/linux_guide.html)


[CENTER] Possible problems with utorrent section:
[/CENTER]
                                                     
[CENTER] KDE Problems info: 

[/CENTER]
                                                     If you got any problems with utorrent freezing when you use more than one desktop or when you minimize utorrent, then you can try the possible fix pointed out by "Ivhassel", the fix is to minimize µTorrent to kicker, and then to maximize it again.

100% CPU use problem when using older wine: The fix is to update wine to a more current version. (current version is: 0.9.22).
[CENTER]** Note:** This version is from the resp on this post.
[/CENTER]
                          


[CENTER] This section shows you how to use the normal user with wine and not "root" (gksu).

      I made some mistakes when making the how to but this should fix the problem, **you only need to follow this section** if you followed the howto **before** i updated it, that means you don't need to do this now if you followed the howto for the _first_ time.
[/CENTER]
                                                    

Step 1:

cd /home/yournickname/


Step 2:


sudo rm -r .wine


Step 3:

winecfg

setup the settings again.


Step 4:

wine /home/yournickname/yourfolderofchoice/utorrent.exe

fix the settings again

DONE!

[CENTER] List of linux bittorent clients 
(_note_: the info about version _only_ apply's to Dapper and _not_ to Edgy Eft)

[/CENTER]
                                                                                                ktorrent: Plus: opensource, nice plugins and interface, resource friendly. minus: unstable downloads, DHT not supported to Azureus, utorrent or bitcomet. 

rtorrent: Plus: opensource, fast, resource friendly, command line, minus:  (avalible in resp, but not the latest version).
[http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

bittornado: Plus: opensource, peer exchange, easy to use, minus: not resouce friendly. (avalible in resp, but not the latest version).

azureus: Plus: opensource, DHT, peer exchange, fast, minus: too many options, not resouce friendly, confusing. 

[CENTER]Windows bittorent clients

[/CENTER]
                                                                      utorrent using wine version 0.9.22: Plus: fast, resource friendly, DHT ((only with bitcomet, Mainline, other utorrent clients)), peer exchange ((only with other utorrent clients)) minus: closed source.

[CENTER]** Note:** If you want more then please look at this page
 [http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software](http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software)



Section for installing utorrent with wine with Ubuntu _Edgy Eft_ 6.10

NOTE: This section is for _fresh_ install only for now _not_ upgrade


[CENTER][LEFT]Adding resp into Synaptic: 


1. Start Synaptic 

2. Goto the menu "Settings" then choose the _second_ choice.

3. In the section "Ubuntu Edgy" see to that the first _four_ choices are selected.

4. Then goto "Internet Updates" and see to that the first _four_ there also is selected, then close the window.

5. Press "reload".


Installing wine with Synaptic: 

6. Search for "wine" then do a right click on it and choose "mark for installation", then  choose apply from the toolbar.

7. Follow the  **"Step 5-18"** at the _Dapper_ Section.

8. DONE!
[/LEFT]
            [/CENTER]
            [/CENTER]

---

### Post by rodrigo666 on 2006-06-07
Very nice how-to.

I could follow it just right.

Thanks for sharing it.

---

### Post by gushy on 2006-06-08
very handy thanks, I had wondered why I couldn't get utorrent working (wouldn't connect to any trackers), but updating wine to the one in the repository you list fixed the issue.

:grin:

---

### Post by terryman on 2006-06-08
Great howto! Thanks a lot :)

btw the 100% cpu use with older wine was true. fixed when updated to last version ;)

---

### Post by kreso on 2006-06-08
I've got a question: If you use uTorrent on Linux, will it be as fast as it is on windows? I mean, which is better ,to use Azureus or uTorrent under wine?

---

### Post by kreso on 2006-06-08
I got a weird problem, uTorrent seems to flicker every second?? I changed the "Update interval" to 10 seconds and then it flickered every 10 seconds? is there a way to remove the effect?

---

### Post by Ivhassel on 2006-06-08
**1.**
> **kreso]I got a weird problem, uTorrent seems to flicker every second?? I changed the "Update interval" to 10 seconds and then it flickered every 10 seconds? is there a way to remove the effect?[/QUOTE]
Currently no, though this might be fixable in wine. [Source]("http://forum.utorrent.com/viewtopic.php?id=6353&p=4")

Yes it's annoying, but it's bearable if you have 3D support on your graphics card enabled, along with a 2 secs update interval. imho  said:**
> I've got a question: If you use uTorrent on Linux, will it be as fast as it is on windows? I mean, which is better ,to use Azureus or uTorrent under wine?

Personally I'd prefer µTorrent over Azureus. Both feature filled, but µTorrent seems less of a burden on my system. µTorrent seems to stay under 10% CPU usage, which is fine with me. 

**3.**
**µTorrents beta**'s are also very stable & reliable imho, so that's what I'm running under wine atm.

**4.**
If anyone tries µTorrent under the **latest wine 0.9.15**, then please post your experiences. I don't feel like breaking anything atm. Still too much breakage to solve from last time ;)

---

### Post by Ivhassel on 2006-06-09
[QUOTE=Ivhassel]
**4.**
If anyone tries µTorrent under the **latest wine 0.9.15**, then please post your experiences. I don't feel like breaking anything atm. Still too much breakage to solve from last time ;)[/QUOTE]

It does work flawlessly ...

---

### Post by athlonkmf on 2006-06-09
I have  a problem when using it with kdea-desktop. When I change to another desktop and then change back to the utorrentdesktop, the screen is frozen (even though it's still working)

Also, how to include chinese character (fonts) in wine then?

---

### Post by Ivhassel on 2006-06-09
[QUOTE=athlonkmf]I have  a problem when using it with kdea-desktop. When I change to another desktop and then change back to the utorrentdesktop, the screen is frozen (even though it's still working)[/QUOTE]

I experience the same under KDE. When I minimize µTorrent, or use more than one desktop, then the µtorrent freezes. What I do to solve this, is minimize µTorrent to kicker, and then to maximize it again.

---

### Post by hikitsu4 on 2006-06-09
[QUOTE=Ivhassel]I experience the same under KDE. When I minimize µTorrent, or use more than one desktop, then the µtorrent freezes. What I do to solve this, is minimize µTorrent to kicker, and then to maximize it again.[/QUOTE]
I have never had this problem with Gnome or with XFCE i guess it is a KDE only problem, but one problem i noticed is that if try to download a torrent with lots of jpg files the window goes away, but is still running with the other torrents in the background. And then the only way to fix this is to kill -9 both "wineserver and utorrent.exe".

---

### Post by jdusablon on 2006-06-09
Huh? I'm not rying to troll, here, but why the heck would you use utorrent under wine when there are PLENTY of torrent clients under linux? Fact is, the basic bittorrent client under Ubuntu allowed me do download the dapper iso at >600KB/s! (read: Bytes, not bits)

I don't really understand why (besides doing it for its own sake). Why???

---

### Post by CronoDekar on 2006-06-09
[QUOTE=jdusablon]Huh? I'm not rying to troll, here, but why the heck would you use utorrent under wine when there are PLENTY of torrent clients under linux? Fact is, the basic bittorrent client under Ubuntu allowed me do download the dapper iso at >600KB/s! (read: Bytes, not bits)

I don't really understand why (besides doing it for its own sake). Why???[/QUOTE]

Basically, because uTorrent offers a lot more features than the basic torrent client, but still uses very little resources.  I'm not sure that if it has all the features of Azureus, but it has all of them I care about and uses MUCH less in resources.

If you don't have any need or desire for the extra features though, the standard bittorrent client should be fine.  Nothing wrong with that!

EDIT: Also because on the [uTorrent page](http://www.utorrent.com/) they have screenshots that are downloading Ubuntu 5.10.  That's gotta count for something! ;)

---

### Post by FredB on 2006-06-09
I prefer from far Azureus because it seems that utorrent is not really clean with its user...

[http://phoenixlabs.org/2006/03/07/the-%c2%b5torrent-fiasco/]("http://phoenixlabs.org/2006/03/07/the-%c2%b5torrent-fiasco/")

> This is because µTorrent&#8217;s developer recently licensed his backend technology to a company known for monitoring P2P networks.

Today we confirmed that it is for a new content distribution system - something explicitly stated in the contract, meaning they are not allowed to use it for monitoring P2P users or anything else.

So is helping out a company known for P2P monitoring morally wrong? Maybe. But everyone needs to eat. The licensing had no malicious intent toward P2P users, and it does not affect µTorrent in any way.

After that, you will be aware to use or not this torrent client.

---

### Post by sushi on a grill on 2006-06-10
it seems a bit slower compare to utorrent under windows in terms of connecting to other seeders


but its working now nontheless


i think i'll stick to utorrent instead of any other linux clients because its cleaner and works better, imho

---

### Post by Rizado on 2006-06-10
There are other choices than azureus on linux... My personal favorite is KTorrent. It's much like utorrent and doesn't take more than tops 2% CPU.

---

### Post by jdusablon on 2006-06-10
There are BOATLOADS of bittorrent clients. Even the builtin one is fine for me...super fast speeds and very low resource usage.
t
I'm having a hard time believing utorrent performs any better. I certainly couldn't get it going any faster than even the builtin one! In fact, on the dapper iso, I only got 300 to 400MB/s with utorrent.

Granted, the interface is clean, but, for its features, it doesn't get cleaner than this:

---

### Post by hikitsu4 on 2006-06-10
I think everyone should just use the torrent program that works best for them, and everyone should just leave it at that. You can just test what bt program works best for you, it's the same with all computer programs and OS's.

---

### Post by jdusablon on 2006-06-10
Agreed.:)

---

### Post by foofightrs777 on 2006-06-10
One reason could be encryption.  I know Bittorrnado does not support this feature.  Encryption can be VERY useful for those with ISP who filter torrent traffic.  And yes, Azereus supports encrytion as well but some people don't like java.  It's the choice of the lesser evil for each individual: java or a compatibility layer.

---

### Post by Jengu on 2006-06-10
[QUOTE=hikitsu4]
make a shortcut at the desktop with fab window manager, use this syntax
"gksu wine /media/hda1/Program Files/[insert your directory]/utorrent.exe"
[/QUOTE]

Why is the gksu there? That's a really bad idea -- you're running a closed source windows exe with root permissions. Potentially it could do anything to your system. If it's because your windows partition isn't writeable for users, you should fix that instead of running wine with root permissions. You're gambling that there isn't some bug in wine or utorrent that will delete your whole system.

---

### Post by hektisk on 2006-06-11
[QUOTE=Jengu]Why is the gksu there? That's a really bad idea -- you're running a closed source windows exe with root permissions. Potentially it could do anything to your system. If it's because your windows partition isn't writeable for users, you should fix that instead of running wine with root permissions. You're gambling that there isn't some bug in wine or utorrent that will delete your whole system.[/QUOTE]

I was wondering this as well.  I'm a newbie so I followed it step by step (and it's working great, thanks!) but I'm not sure why I'm running this as root.  So there's no reason to?

---

### Post by Wandering Wombat on 2006-06-11
[QUOTE=jdusablon]Huh? I'm not rying to troll, here, but why the heck would you use utorrent under wine when there are PLENTY of torrent clients under linux? Fact is, the basic bittorrent client under Ubuntu allowed me do download the dapper iso at >600KB/s! (read: Bytes, not bits)

I don't really understand why (besides doing it for its own sake). Why???[/QUOTE]

Some private trackers I use basically only allow Utorrent or Azureus, as much as I like Azureus, I find it too bloated, so its Utorrent for me ;) I like Rufus, but some private trackers don't like it. Is there a list somewhere of all Linux/Ubuntu clients I can check to see if they are banned?

**Banned Clients list** <<< one private tracker I use!
  ABC  	
  BitLord 	
  burst! 	
  eXeem 	
  Shareazza 	
  G3 	
  BitSpirit 	
  eDonkey2000 	
  Turbo Torrent 	
  BinTorrent 	
  Torrentstorm 	
  BitComet 	
  XBT Client 
  Qtorrent 	
  CTorrent and clones 	
  ed2k 	
  MLdonkey 	
  Opera 	
  Ziptorrent 	
  Acquisition 	
  Rufus 	
  Bittorrent++ 	
  Torrent Station 	
  KTorrent 	

Cheers ;o)

---

### Post by hikitsu4 on 2006-06-11
[QUOTE=Jengu]Why is the gksu there? That's a really bad idea -- you're running a closed source windows exe with root permissions. Potentially it could do anything to your system. If it's because your windows partition isn't writeable for users, you should fix that instead of running wine with root permissions. You're gambling that there isn't some bug in wine or utorrent that will delete your whole system.[/QUOTE]
.

---

### Post by hikitsu4 on 2006-06-11
OK i fixed the faq to not use "gksu", if you followed the faq and dont want to use "gksu", then do this.

Step 1:

cd /home/yournickname/

Step 2:

sudo rm -r .wine

Step 3:

winecfg

setup the settings again.

Step 4:

wine /home/yournickname/yourfolderofchoice/utorrent.exe

fix the settings again.

DONE!

---

### Post by hikitsu4 on 2006-07-03
updated the howto to reflect on utorrent 1.6 stable, also added a list of some avalible to torrents.

---

### Post by xixer on 2006-07-03
hey, i just want to say great job with the how to.

this community is awesome

---

### Post by hikitsu4 on 2006-07-04
[quote=xixer]hey, i just want to say great job with the how to.

this community is awesome[/quote] Thanks i really try to make it as easy as possible.
I updated the howto now with the new screenshots for utorrent 1.6.

---

### Post by orb9220 on 2006-07-05
Just installed wine yesterday for dvd shrink.  

And then down and installed utorrent 1.6 still using 100% Cpu on my 6.06 Dapper.

Wine version 0.9.9 settings defualt for winXP

Any Ideas?

---

### Post by orb9220 on 2006-07-05
[QUOTE=orb9220]Just installed wine yesterday for dvd shrink.  

And then down and installed utorrent 1.6 still using 100% Cpu on my 6.06 Dapper.

Wine version 0.9.9 settings defualt for winXP

Any Ideas?[/QUOTE]

Never Mind the default synaptic doesn't give the latest had to deb from wine main.

Now working like a champ.

---

### Post by AirLange on 2006-07-10
.

---

### Post by mmcclure79 on 2006-07-15
uTorrent allows you to choose individual files from withing large torrents, are there any native cliets that do the same?

---

### Post by Kevf on 2006-07-15
I followed the tut right to the last step, but I don't understand how to create a shortcut (newbie, sorry ](*,) ).

Now I've closed utorrent and I completely lost the program! Only option I know is to 'which µTorrent.exe', but no results.

Could someone help me out?

---

### Post by hikitsu4 on 2006-07-15
> **mmcclure79 said:**
> uTorrent allows you to choose individual files from withing large torrents, are there any native cliets that do the same?

Check this website: [http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software](http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software) 
then at "Supports Selective Downloading" you can see witch torrent program supports it.

---

### Post by hikitsu4 on 2006-07-15
fixed up the howto to make it easier to read.

---

### Post by Underscore on 2006-07-15
> **mmcclure79 said:**
> uTorrent allows you to choose individual files from withing large torrents, are there any native cliets that do the same?

you could try azureus. download it via automatix or from the [official site]("http://azureus.sourceforge.net/")

---

### Post by jISh on 2006-07-16
Good guide, thanks. Got this proggy up and running in no time.

---

### Post by Dafoe on 2006-07-17
Hi guys n girls, 

I'm having trouble running utorrent 1.6 stable under my Ubuntu Dapper 6.06 and wine 0.9.9. 

First of all I cannot connect to any tracker (does Ubuntu block any ports by default ?)

Secondly the wine-preloader is hawking all the cpu.

I'm running utorrent with wine using non-root user #wine /usr/local/utorrent/utorrent.exe

any hints ?

regards,
arib

---

### Post by hikitsu4 on 2006-07-18
> **Dafoe said:**
> Hi guys n girls, 

I'm having trouble running utorrent 1.6 stable under my Ubuntu Dapper 6.06 and wine 0.9.9. 

First of all I cannot connect to any tracker (does Ubuntu block any ports by default ?)

Secondly the wine-preloader is hawking all the cpu.

I'm running utorrent with wine using non-root user #wine /usr/local/utorrent/utorrent.exe

any hints ?

regards,
arib
As it said in the howto the 100% cpu problem is solved if you use the latest wine, the other problem i dont know of but try the latest and see what happends. Most problem will be solved if you followed the howto but if you use an old version (0.9.9) you most have installed everything yourself.
I can only help if you followed the howto i dont know that much about linux.

---

### Post by Rothguard on 2006-07-18
nice guide but some heading and hyperlink to relevent start point would be a real winner LOL i spent a while getting errors because i was using the top method as root and not the normal user mode ](*,) ]

---

### Post by hikitsu4 on 2006-07-18
> **Rothguard said:**
> nice guide but some heading and hyperlink to relevent start point would be a real winner LOL i spent a while getting errors because i was using the top method as root and not the normal user mode ](*,) ]
I dont exactly know what you mean but, i made some changes with the numbering of the sections, english isnt my first lang so the problems i find with the howto i fix over time.

---

### Post by Dafoe on 2006-07-18
> **hikitsu4 said:**
> As it said in the howto the 100% cpu problem is solved if you use the latest wine, the other problem i dont know of but try the latest and see what happends. Most problem will be solved if you followed the howto but if you use an old version (0.9.9) you most have installed everything yourself.
I can only help if you followed the howto i dont know that much about linux.

Ok thx a bunch!I went back to the guide and found out that I accidently skipped step 3, adding the wine repository, when I updated wine to 0.9.17 everything is running smoothly.

thx again

---

### Post by bodhi.zazen on 2006-07-18
Nice guide. I have been using utorrent on my own and just ran across this guide.

I have tried several torrents and find utorrent is often the fastest assuming simmilar network/firewall configurations.

utorrent is also very light, although I agree Ktorrent is also nice.

---

### Post by ChakRa on 2006-07-21
Thanks a lot got the guide. Somehow i feel that utorrent actually runs better on linux lol. But the guide was very descritive and very easy to follow. Thanks again.

---

### Post by JerMe on 2006-07-21
Nice.  Wine 0.9.17 + uTorrent 1.6 works just fine (so far).

---

### Post by boast on 2006-07-26
I can't get utorrent to connect. Ive fowarded my ports on my router, and got it setup on utorrent. The other post wasn't answered if ubuntu blocks some ports or something? I don't have firestarter.

---

### Post by JerMe on 2006-07-26
> **boast said:**
> I can't get utorrent to connect. Ive fowarded my ports on my router, and got it setup on utorrent. The other post wasn't answered if ubuntu blocks some ports or something? I don't have firestarter.

Which version of Wine are you running?

---

### Post by boast on 2006-07-26
Wine 0.9.9

---

### Post by JerMe on 2006-07-26
> **boast said:**
> Wine 0.9.9

You need Wine 0.9.17.  Follow the directions on the first post of this thread to get the newer version of Wine.  Then you'll be able to connect to other peers.

---

### Post by boast on 2006-07-26
> **JerMe said:**
> You need Wine 0.9.17.  Follow the directions on the first post of this thread to get the newer version of Wine.  Then you'll be able to connect to other peers.
No wonder. I though the wine in the first thread was an older version. =\

Thanks.

---

### Post by hollaburoo on 2006-07-26
Has anyone managed to find a way to make firefox open utorrent when it downloads torrents?  I tried to make a shell script to call utorrent with the torrent as a parameter, but got weird filename errors.

---

### Post by FooAtari on 2006-08-05
Hi,

I created a desktop shortcut, but when I try and run it, nothing happens.

I created it by right click on Desktop and then Create Launcher and copied in the command from the HowTo.

What have I done wrong?

---

### Post by telperion on 2006-08-05
> **Ivhassel said:**
> **1.**


If anyone tries µTorrent under the **latest wine 0.9.15**, then please post your experiences. I don't feel like breaking anything atm. Still too much breakage to solve from last time ;)

wine 0.9.17 compiled by myself
utorrent 1.6 build 474 
work fine, very low cpu usage

---

### Post by CronoDekar on 2006-08-05
> **FooAtari said:**
> Hi,

I created a desktop shortcut, but when I try and run it, nothing happens.

I created it by right click on Desktop and then Create Launcher and copied in the command from the HowTo.

What have I done wrong?

Are there any spaces in the path?  If so, you'll have to put quotes around it.  Mine looks like this: (note though in my example I use the virtual path Wine uses, which is also possible)

wine "H:\programs\utorrent\utorrent.exe"

If that doesn't help, try copying the command and go to Appllications > Accessories > Terminal, paste and enter it there, and see what it gives you.

---

### Post by FooAtari on 2006-08-06
That seems to have fixed it, thanks.  I forgot about that.

---

### Post by hasbeen on 2006-08-11
works flawlessly. Thanks for the guide. I've been trying to seed files that are on my windows partition, and it works perfectly with utorrent. It didn't work with the other linux clients like ktorrent and even azureus.

---

### Post by bruenig on 2006-08-13
jdusablon, the only other bittorrent client with rss besides utorrent is azureus and that is only through plugin which is a bit tricky to install because of permissions issues and I can't handle running java all of the time which azureus requires. Just not enough resources to go around.

Also, does anyone know why you don't associate it with .torrent files or how to get them to open from firefox?

---

### Post by 505 on 2006-08-13
Just made a simple shell script to start utorrent. This script accepts a command argument for the torrent, so you could start utorrent directly from Firefox.

It a simple script, not much checking is done, so if some one want to improve it...

This script presumes you have a Z:\ drive in Wine. In the default Wine setup (mine at least) the root partion is references in Wine as Z:\

Howto:
1. Open a terminal
2. Type
```

cd /bin
sudo gedit utorrent

```
Enter you password
3. Paste the following code in gedit
```

#!/bin/sh

cd ~/.wine/drive_c/Program\ Files/utorrent
if [ "$1" != "" ]; then
	var="`echo $1 | sed 's/\//\\\/g'`"
	var="Z:${var}"
	wine utorrent.exe "$var"
else
	wine utorrent.exe
fi

```
3a. Optionally, edit the path to utorrent.exe
4. Save and close gedit
5. In the terminal type
```

sudo chmod a+x utorrent

```
And your done.

To test, just type 'utorrent' in the terminal, and utorrent should start.

---

### Post by bodhi.zazen on 2006-08-16
505:

Tlthough that works, try this:

edit your ~/.bashrc (vi, nano, gedit, use any editor you like)

add this line:

alias utorrent='wine /home/user_name/.wine/name_of_c_drive/Program\ Files/utorrent.exe &'

(change user_name and name_of_c_drive to the appropriate values)

Now all you need to do is type utorrent in a terminal.
Actually you can use tab completion and type uto <TAB> -> becomes utorrent -> press enter.

The cool thing is this: The file utorrent.exe is always the most up to date. by this I mean at times updates to utorrent become aailable. utorrent will offer to dwonlad and update when you boot. After the update utorrrent.exe itself is updated (works even for Beta versions ot utorrent).

Enjoy!

---

### Post by Philaretus on 2006-08-17
Where is that .bashrc file?

---

### Post by bodhi.zazen on 2006-08-17
Sorry, the .bashrc file is in your home directory:

This is a configuration file for your bash shell (terminal). You can do much with this file. An alias is an user defined command.

You may want to back up the file first: 
cp ~/.bashrc ~/.bashrc.bak 

Try

nano ~/.bashrc

or editor /home/user_name/.bashrc

where editor = vi, nano, gedit, etc

You can colorize your prompt. In my box, for example, root has a red prompt. Non-root users are green.

Other alias to consider may be:
alias cp='cp -i'
alias rm='rm -i'
alias la='ls -a'

The potential options is long and beyond this post.

---

### Post by remoir on 2006-08-27
has anyone try installing utorrent with wine 0.9.20 ? 

i got the errors below when executing wine utorrent.exe

------------------------------------
err:imagelist:ImageList_LoadImageW Error loading image!
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
err:imagelist:ImageList_LoadImageW Error loading image!
err:imagelist:ImageList_LoadImageW Error loading image!
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 16 lpiArray 0x33edd8
fixme:keyboard:UnregisterHotKey (0x20026,1): stub
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1

---------------------------------------------

---

### Post by mcpish on 2006-08-27
Is there anyway to make all applications opened with Wine share the same GTK+ look and feel of applications running in XFCE or Gnome?  I don't like how the Windows apps fonts and colors are slightly different.

---

### Post by feap on 2006-10-03
I followed the steps closely but I get a problem in step 11: every time I double-click on utorrent.exe I get "couldn't display "/home/[user]/utorrent.exe"". What could be the problem? Yes, I'm a beginner with ubuntu.

---

### Post by bodhi.zazen on 2006-10-03
> **feap said:**
> I followed the steps closely but I get a problem in step 11: every time I double-click on utorrent.exe I get "couldn't display "/home/[user]/utorrent.exe"". What could be the problem? Yes, I'm a beginner with ubuntu.

Most likely the path is incorrect.

Look up for some examples. It should look something like:

wine '/home/user_name/.wine/c/Program\ Files/utorrent.exe &'

where c= name of fake c drive. Use single '.

. files are hidden

Try ls -a to show them and ls ~/.wine to see you fake c drive.

---

### Post by feap on 2006-10-04
> **bodhi.zazen said:**
> Most likely the path is incorrect.

Look up for some examples. It should look something like:

wine '/home/user_name/.wine/c/Program\ Files/utorrent.exe &'

where c= name of fake c drive. Use single '.

. files are hidden

Try ls -a to show them and ls ~/.wine to see you fake c drive.

Thanks, works wonderfully now that I understood that I need to put the path as you described to mimic WIN paths!

---

### Post by airtonix on 2006-10-05
yeap, use rTorrent instead.....

it uses nCurses interface and so when you need to logout you can have rTorrent running in one of  your alternative terminals (ie: ctrl+alt+f1)

It does alot of things and its doesnt require java or wine....and it lets you load a whole directory of torrent files...with resuming of course.

I dont use any other client coz, rTorrent : 

[LIST]
[*]runs in a terminal, os its resource friendly
[*]doesn't require kde, gnome or xcfe...so again resource friendly
[*]lets me pick a particular file in a torrent if there is a bunch of files.
[*]lets me shape the in and out speeds with keys like (increase speed by 1kb with "a" and increase speed by 10kb with "s", decrease speed by 1kb with "z", decrease speed by 10kb with "x")
[*]shows me extended statistics on other clients in the torrent swarm
[*]doesnt use java[/LIST]The only thing that i think is lacking is the fact that it doesnt run in daemon mode, so you cant use zenity to create querie dialouges.....

---

### Post by Giggity on 2006-10-12
This has been working great for me for some time now.  It's gone flawlessly through several updates of Wine (0.9.17 through 0.9.22).

Now, how's about this for a challenge?  I'm looking to *skin* uTorrent, specifically the tray icon, since the native icon doesn't seem to have a transparent background, so it looks awkward if I use a transparent taskbar.  Skinning the tray icon requires me to place a tray.ico in "%AppData%\uTorrent", which in Windows for me was "c:\Documents and Settings\rob\Application Data\uTorrent".  I tried doing the same thing in Ubuntu, only with "/home/rob/.wine/drive_c/Documents and Settings/rob/Application Data/uTorrent", and it doesn't work.

Does wine support this kind of use?  That is, does there exist an %AppData% location under Wine that can be used for this purpose?  Or am I just asking too much?

I enclosed a small screenshot to help explain why I'm trying to find a better tray icon...

---

### Post by Druid Healer on 2006-10-19
It supports it, and the skinning of the icon works for me. Unfortunately wine has NOT implemented transparency for systray icons. So even if you skin it, you'll still get an ugly icon.

---

### Post by deadlydeathcone on 2006-10-19
[These]("http://www.darkt.net/tango/?page=apps&app=utorrent") are my favorite, and stupidly simple to install. Like Druid said the tray icons don't render correctly, but they still look much better than the default (just don't use the rest of the theme, as it looks horrible).

---

### Post by Giggity on 2006-10-24
> **Druid Healer said:**
> It supports it, and the skinning of the icon works for me. Unfortunately wine has NOT implemented transparency for systray icons. So even if you skin it, you'll still get an ugly icon.Good to know... thanks!

---

### Post by sheriffdaone on 2006-11-02
Well i have wine 0.9.24 and it doesn't work well i mean uTorrent gives an error like "Unable to map UPnP port". So why is that? i made everything right like it said on the first page. I always changed the port but nothing happened.

---

### Post by bodhi.zazen on 2006-11-02
> **sheriffdaone said:**
> Well i have wine 0.9.24 and it doesn't work well i mean uTorrent gives an error like "Unable to map UPnP port". So why is that? i made everything right like it said on the first page. I always changed the port but nothing happened.

Downgrade wine to 0.9.19.

See here: [Downgrade wine](http://doc.gwos.org/index.php/HowToWine#Downgrade_wine)

---

### Post by sheriffdaone on 2006-11-02
ok i did downgrade to 0.9.19 but still gives the same error also at the bottom it says "No incoming connections"?

---

### Post by angrykeyboarder on 2006-11-03
There are [numerous]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=622") very good Open Source Bittorrent Clients for X Window, Mac and Microsoft Windows.

Why use a proprietary one (especially a Windows-based one in Wine)?

---

### Post by bodhi.zazen on 2006-11-03
> **angrykeyboarder said:**
> There are [numerous]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=622") very good Open Source Bittorrent Clients for X Window, Mac and Microsoft Windows.

Why use a proprietary one (especially a Windows-based one in Wine)?

utorrent is not proprietary (to Microsoft). And it is very fast, efficient, full yet somehow featured.

Give it a try....

[utorrent](http://www.utorrent.com/)

Edit: Errr...  I just went to the utorrent forums and those folks are Linux Hostile.

Perhaps I shall have to update my thinking on utorrent and change to an alternate torrent client.

Edit2: I have had some contact with the utorrent moderators on the utorrent forums and it seems they are more frustrated with requests for a port to Linux then anything else. Other then that they seem generally helpful.

The utorrent code is not opensource and there are no current plans to develop such a port.

For now, continue to use wine.

If you are having problems with utorrent, perhaps you may find a solution on the utorrent forums.

[utorrent forums](http://forum.utorrent.com/index.php)

---

### Post by bodhi.zazen on 2006-11-03
The folks at utorrent gave me this link on utorrent.

[utorrent on Ubuntu](http://www.securenet.net/members/jeanpelo/linux_guide.html)

It is a very nice guide on utorrent on Linux. Covers themes and skins as well.

---

### Post by Zed on 2006-11-03
It's mentioned in the first post, and once again further up in this thread, but I'll put in another plug for rtorrent. It's fast, lightweight, Linux-native and installs with just 'sudo apt-get install rtorrent'. It's a text application -- it runs within a terminal window. If you insist on a GUI, it's not for you, but I'm a big fan of it.

(I don't mean to derail -- if you like utorrent under wine, that's great, but since some people were talking about seeking alternatives, I thought I'd mention one that scratches some of the same itches as utorrent.)

---

### Post by mahy on 2006-11-04
> **bodhi.zazen said:**
> utorrent is not proprietary (to Microsoft). And it is very fast, efficient, full yet somehow featured.


Well, it isn't owned by m$, but it IS proprietary. The mere fact that it costs no money to use doesn't make it Free. Check out [http://www.gnu.org](http://www.gnu.org) to learn about these subtle diffrences.

Personally, i wouldn't touch utorrent with a barge pole. Not because it's proprietary (Opera is as well and i use it), but i think it can't be trusted. Too much controversy around it. Look at wikipedia's articles about utorrent to see for yourself.

---

### Post by bodhi.zazen on 2006-11-06
> **mahy said:**
> Well, it isn't owned by m$, but it IS proprietary. The mere fact that it costs no money to use doesn't make it Free. Check out [http://www.gnu.org](http://www.gnu.org) to learn about these subtle diffrences.

Personally, i wouldn't touch utorrent with a barge pole. Not because it's proprietary (Opera is as well and i use it), but i think it can't be trusted. Too much controversy around it. Look at wikipedia's articles about utorrent to see for yourself.

Thanks mahy. I have tested rtorrent and it works OK.

No fancy GUI, which is fine just leting others know.

I had troubble with a few torrents. Others work OK.

---

### Post by rykel on 2006-11-27
Hi,

I am running utorrent under WINE successfully.

However, I deleted the desktop icon accidentally, and now, have no idea how to bring it back.

Could you please show me how to create that utorrent icon again?

Lastly, all non-English characters (eg. Chinese, Japanese, Thai) in utorrent become gibberish.

This might be a WINE setup issue. Do you know how to resolve the character problem?

Thank you!

---

### Post by bionnaki on 2006-12-01
how do you get rid of the flicker?

---

### Post by bodhi.zazen on 2006-12-01
Minimize the application :p

---

### Post by bionnaki on 2006-12-01
gee, thanks.

---

### Post by SubTerRaiN on 2006-12-04
how can i set utorrent thru wine to be default application for .torrent files in ubuntu 6.10 ?

thanks.

---

### Post by Flying_OE on 2006-12-13
I created a simple script uTorrent.sh:

=====snip=====
#!/bin/sh
LANG=en_US.utf-8
LC_MESSAGES=en_US.utf-8
TORRENT_FILE=`winepath "$1"`
wine "C:/Program Files/utorrent/utorrent.exe" "$TORRENT_FILE" &
=====snip=====

After this, I can simply associate .torrent files with this script. Furthermore, I also set the .torrent association from within Firefox so that it will let uTorrent open the files once they are downloaded.

As for language issues, it can be solved by the this script too. For example, since I want to emulate a Chinese environment (but I still want to keep all the dialogs, etc. in English), I can change "LANG=en_US" line to "LANG=zh_CN.utf-8" and Chinese characters are displayed properly automatically--provided you have already configured Chinese display in your Ubuntu.

---

### Post by flapane on 2006-12-16
It seems I am not reachable from trackers, why?
Here's my script attached, the port is the 32459

---

### Post by Lowfront on 2006-12-29
ok go to step 11.  But when I click on the shortcut I get an error 


Cannot open /home/lowfront/Desktop/link to utorrent.exe: No application suitable for automatic installation is available for handling this kind of file.

---

### Post by brainiac on 2007-01-08
my utorrent window has dissapeared... the app starts in systray but whatever i do, the main window wont show up again. 
any tips?

---

### Post by jaxson on 2007-01-15
When I minimize uTorrent in edgy it won't show it maximized when I click it. Only was I can get it back is to dbl click on the desktop shortcut again.

uTorrent 1.6
wine-0.9.29
edgy
gnome 2.16.1

---

### Post by jaxson on 2007-01-15
Reading the link below helped some, although in dapper the minimizing worked fine.

[http://www.securenet.net/members/jeanpelo/linux_guide.html](http://www.securenet.net/members/jeanpelo/linux_guide.html)

*shrug* Guess I'll wait and see if a future ver of wine fixes it.

ps. for Brainiac: untick all the system tray options to fix.

---

### Post by The303 on 2007-01-29
Hi, this is my first post on these forums.

I have followed the instructions step by step and have had absolutely no problems, everything was fine until I tried to add a torrent and begin downloading.

Every torrent I have attempted to start has immediately come back with the message "Error:Access denied" within utorrent.

Can anybody help please ?

---

### Post by The303 on 2007-01-29
Just realised that following the guide exactly to the word has grabbed me wine 0.9.30

Has anybody else got it working with this version ?

If not, then what is the easiest way to downgrade or get utorrent working.

I am using Kubuntu dapper btw

---

### Post by juyanith on 2007-01-29
Yeah, I've been running it with wine 0.9.30 and it works fine. Just make sure you uncheck "minimize to system tray" in utorrent prefs, otherwise it will not refresh properly when you switch workspaces unless you click the utorrent tray icon.

---

### Post by The303 on 2007-01-29
> **juyanith said:**
> Yeah, I've been running it with wine 0.9.30 and it works fine. Just make sure you uncheck "minimize to system tray" in utorrent prefs, otherwise it will not refresh properly when you switch workspaces unless you click the utorrent tray icon.

Thanks for that :) 

The only problem I have now is that the torrents start downloading (at a very good speed as well) but after about 10 seconds, as soon as the file starts to seed back, the torrent stops and goes to "Error:Access denied" :mad: I can still see how many seeds and peers there are.

This is so frustrating.  I only started using linux for the first time yesterday, but already I am so impressed that everything I need works better than windows and has been pretty much a doddle to get working.  Apart from this.  I have already tried azureus, but I can't stand it and it brought my system to its knees once I had more than 5 torrents running together.  I have to have one of these two browsers because of a private tracker I am a member of.

Any help would be much appreciated so that I can finally throw out my (evaluation :wink:) copy of windows for good.

---

### Post by nero2150 on 2007-01-29
I use utorrent for quite some now, eventually there are the little glitches here and there.
I have try to enable the sheduler to shutdown after completion of downloads but it just kill
utorrent. :(  
Is it possible to get this feature working for instance using a script to 
shutdown after utorrent closes or something. :-k  
If someone could help I m no good at scripting or even suggest an alternative :confused:

---

### Post by glabouni on 2007-01-29
> **brainiac said:**
> my utorrent window has dissapeared... the app starts in systray but whatever i do, the main window wont show up again. 
any tips?

+1

---

### Post by The303 on 2007-01-30
> **The303 said:**
> Thanks for that :) 

The only problem I have now is that the torrents start downloading (at a very good speed as well) but after about 10 seconds, as soon as the file starts to seed back, the torrent stops and goes to "Error:Access denied" :mad: I can still see how many seeds and peers there are.

This is so frustrating.  I only started using linux for the first time yesterday, but already I am so impressed that everything I need works better than windows and has been pretty much a doddle to get working.  Apart from this.  I have already tried azureus, but I can't stand it and it brought my system to its knees once I had more than 5 torrents running together.  I have to have one of these two browsers because of a private tracker I am a member of.

Any help would be much appreciated so that I can finally throw out my (evaluation :wink:) copy of windows for good.

Yay I sorted it :guitar: 

forgot to disable upnp doh!!

bye bye windows forever :D

---

### Post by c0rrupt on 2007-02-03
Nevermind...  Upgrading to 0.9.30 fixed it.
---------------------
uTorrent seems to work fine for about 30 seconds, then I get an error saying Request not supported and my torrents stop downloading.  I disabled uPnP, and also tried setting the windows version to XP but it didn't fix it.  Anyone know what is going on here?

Edgy Eft
Wine 0.9.29

---

### Post by danomatika on 2007-02-11
> **glabouni said:**
> +1

+1

grrr, it works fine sometimes then all of a sudden the utorrent window will not open ... although it is running.  No window, no sys tray, nothing.  I can see both it and wineserver in htop and I can even hear my hardrive ticking torrent packets.

In Wine 0.9.30, the utorrent gui does a slow death in this order:
1 - The utorrent  window and systray work great.
2 - After a few days, the systray icon does not appear for utorrent.
3 - After a few more days. the utorrent window does not appear, but utorrent is working fine in the background.

EDIT: I downgraded Wine to 0.9.22 and utorrent works great so far.  Yes, I tried reinstalling Wine 0.9.30 completely, writing new settings etc and the utorrent gui still dies for me :P

I filed a bug report to wine bugzilla.  If anyone else has this problem, please confirm it for me.  [BUG 7403]("http://bugs.winehq.org/show_bug.cgi?id=7403")

---

### Post by Ban-Man on 2007-02-12
Here's a quick work around for adding torrents to utorrent....

1. Open preferences->Other

2. Check "Auto-Load Torrents" (put where you'll save your torrents to)

3. Download a torrent to the folder you chose while utorrent is running and it should add it and start downloading :)

sorry if someone posted this already

---

### Post by nijisan on 2007-03-08
For those that are intereseted... I've got uTorrent working with Ubuntu, Wine and upnp.

Turns out that all I had to do was uncheck the "Add utorrent to Windows Firewall exceptions" option in the Preferences -> Connection dialog. See the screenshot

[ATTACH]26907[/ATTACH]

Now to have it integrate better with my Gnome theme.... :confused:

---

### Post by Amorphous_Snake on 2007-03-20
The flickering has stopped!!!

I upgraded to the latest Wine version, 0.9.33 and the flickering that showed up every second simply stopped. That's great.

Actually I don't know if the flickering stopped with 0.9.32 or with .33 as I didn't notice till today and I updated Wine yesterday, but anyhow update Wine and the flickering will go!

---

### Post by penno on 2007-04-10
Worked fine for me, thanks! (c: Yeah, important not to install wine (0.9.9) from the ubuntu repository. It doesn't work too well! haha (cpu max out, and didn't actually download anything.) But after installing the latest (0.9.34) from the wine repository - all was well. (c:

---

### Post by Ragdriet on 2007-04-13
It works fine, thanks for sharing ;)

---

### Post by Defree on 2007-04-21
Hiya guys. My first post as Ubuntu-forums member. Not my first problem though, but first that I cant seem to be able to find a solution to.

Downloading a torrent with multiple files in it. After around 5minutes, it displays a message saying "Error: invalid parameter". The download stops and then I can just start it over by pushing 'start'. Then, after another 5 or so minutes it stops again with the same error-msg. Sure isn't fun trying to download a say 5GB batch, when you have to restart it all the time.
I've also observed that the error often comes when utorrent finishes downloading  a piece of a file. And also it seems impossible to download a last piece of a file, to complete one file in the torrent.
It worked a little better when I decided to download just one file at a time, skipping the other files. Errors didn't come as often, but still left me unable to download the last piece.
Also, some torrents with more than one files work well. Actually this problem just appeared, after having used utorrent for a while with Ubuntu already.

Well it is a pain. So any help is welcomed! Nice tutorial btw. Used it to re-install wine.
Thanks!

---

### Post by leto440 on 2007-04-29
Similar thing here.  "Error: invalid parameter" message shows up in a lot less than 5 minutes, and whipes out the file I'm trying to download.

I just got uTorrent to work under Kubuntu Edgy and this is rather anoying.

---

### Post by zackr on 2007-06-10
Just tried the latest beta version of uTorrent 1.7.1 with the latest Wine (0.9.38)

None of the peers or seeds were connecting. So in the end I was forced to go back to uTorrent 1.6.1, though I had problems with file permissions so had to move all my old downloads to a new folder... grrrr

---

### Post by Amorphous_Snake on 2007-06-10
> **zackr said:**
> Just tried the latest beta version of uTorrent 1.7.1 with the latest Wine (0.9.38)

None of the peers or seeds were connecting. So in the end I was forced to go back to uTorrent 1.6.1, though I had problems with file permissions so had to move all my old downloads to a new folder... grrrr

Same problem here. uTorrent 1.7 runs fine and is stable and even UPnP works, but it can't connect to any peers or seeds. Moreover, I stopped using uTorrent (1.6.1) in Ubuntu because every now and then it would simply crash for no reason. I might be adding some torrents or removing some and then the program crashes. I am back to the bloat of Azureus.

---

### Post by kelvin spratt on 2007-06-10
perhaps i'm missing something here but what is the point of installing Utorrent in the first place as there are many excellent applications that run native in Linux.Ktorrent maxs out for me so did the frog till Java had a problem but i think that's been sorted if you download from Their site.Uttorent was a good client till it sold out to 
Bram Cohen and the MPAA, so what spyware and tracking devices have been added to the latest version. If you most use it i would recomend 1.5 or lower and remember utorrent is closed source, I'm not trying to stir up trouble but sleeping with the enemy is a dangerous game to play, we all know how far the MPAA and RIAA to get convictions

---

### Post by bodhi.zazen on 2007-06-10
> **kelvin spratt said:**
> perhaps i'm missing something here but what is the point of installing Utorrent in the first place as there are many excellent applications that run native in Linux.Ktorrent maxs out for me so did the frog till Java had a problem but i think that's been sorted if you download from Their site.Uttorent was a good client till it sold out to 
Bram Cohen and the MPAA, so what spyware and tracking devices have been added to the latest version. If you most use it i would recomend 1.5 or lower and remember utorrent is closed source, I'm not trying to stir up trouble but sleeping with the enemy is a dangerous game to play, we all know how far the MPAA and RIAA to get convictions

utorrent is a fast and light weight client.

However I now share your concerns regarding utorrent.

If you are looking for a light weight client, try rtorrent :

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by pt123 on 2007-06-10
> **kelvin spratt said:**
> perhaps i'm missing something here but what is the point of installing Utorrent in the first place as there are many excellent applications that run native in Linux.Ktorrent maxs out for me so did the frog till Java had a problem but i think that's been sorted if you download from Their site.Uttorent was a good client till it sold out to 
Bram Cohen and the MPAA, so what spyware and tracking devices have been added to the latest version. If you most use it i would recomend 1.5 or lower and remember utorrent is closed source, I'm not trying to stir up trouble but sleeping with the enemy is a dangerous game to play, we all know how far the MPAA and RIAA to get convictions


Maybe if developers spent some time to develop a quality non java based torrent client, than every second developer trying to develop another music player for Linux. 

rTorrent based clients are banned on most private trackers.

---

### Post by Amorphous_Snake on 2007-06-10
> **pt123 said:**
> Maybe if developers spent some time to develop a quality non java based torrent client, than every second developer trying to develop another music player for Linux. 

rTorrent based clients are banned on most private trackers.

I agree. That's the main reason I am using Azureus or uTorrent. Private trackers just hate KTorrent and Deluge. If they work with these two programs, why do I have to suffer under the bloat of Azureus or using Wine?

---

### Post by forfree on 2007-06-30
Is there a way that I can get utorrent to be synchronized between windows and ubuntu?  I'd like to be able to be downloading the same torrents regardless of which OS I'm in.

---

### Post by HolyMurderer on 2007-07-01
Use the same folders in both OS's. If you're using a NTFS folder to save the downloads, use ntfs-3g on Linux. If you're using a ext3 folder, use Ext2 IFS For Windows, which recognizes ext2 an ext3 in Windows.

---

### Post by forfree on 2007-07-01
I know that the Windows installation uses:

C:\Documents and Settings\USERNAME\Application Data\uTorrent

But how do I make it find that when I run the program in  Ubuntu?  Oh, and the windows drive is FAT32, so I don't have drive format to worry about.

---

### Post by endrre on 2007-07-02
A bit off-topic, why are rTorrent based clients banned from private trackers?

---

### Post by rumour on 2007-07-10
first thanks for the how to but i am having a problem downloading any thing using utorrent, and when i open to speed guide and click on if the port is forwarded properly then this gives a error! (i have not changed any parameter) and one more question can i use FAT32 partition as destination to store the files and .torrent files.

---

### Post by chilli on 2007-07-20
> **forfree said:**
> Is there a way that I can get utorrent to be synchronized between windows and ubuntu?  I'd like to be able to be downloading the same torrents regardless of which OS I'm in.
I use uTorrent under windows and KTorrent under linux and I have no problem in syncronize them. Just make sure they share the same directory and activate the 'Import' plugin in KTorrent.

---

### Post by liquid circuit on 2007-07-22
FYI:  When I opened uTorrent the other day (through Wine 0.9.41), I was prompted to download the latest version and upgrade... I decided to give it a shot and see how Wine handles it.  Well, it upgraded to 1.7.1 build 3360 successfully but there was a cosmetic problem... any unused part of the uTorrent window was being displayed in black.  This didn't affect the functionality/interface in any other way; purely cosmetic.

If you have run into the same issue, I have found a fix courtesy of [this blog]("http://lj4newbies.blogspot.com/2007/07/wine0940-and-utorrent17-on-win2000-mode.html").  And boy is it simple:

open a terminal and run```
winecfg
```
On the *Applications* tab in the window that opens, select "utorrent.exe" from the list of applications.  If *utorrent.exe* is not there, either add it by clicking the *Add* button (ideal if you use Wine for a lot of applications), or just select the *Default Settings*.

Then, in the *Windows* dropdown list choose **Windows XP** (mine was set to Windows 2000), hit *OK*, then restart uTorrent, and its all good.

---

### Post by kornface13 on 2007-08-20
I'm a huge utorrent fan, so when I made the ubuntu switch two days ago, utorrent is a must!!!

Anyone have any idea how to make utorrent the default torrent app?  I've tried everything I can think of.  Please help!!  Thanks in advance.

-tim

---

### Post by tuplich on 2007-09-22
Thanks for this guide! I coulndt connect to the trackers before. Now it works fine. :KS

---

### Post by Muzicman16 on 2007-10-08
Hey so i dl utorrent and at first no one could connect to me and i had the error of "Not connectable a firewall/router is limiting your network traffic. You need to open a port so others can connect to you."

after much trial and error i got firestarter to not block utorrent, and now i can actually upload to people. . .but i still have the same error.

also my ports are not forwarding anyone know of a guide or can anyone explain to me how to forward ports on utorrent.

---

### Post by bodhi.zazen on 2007-10-08
> **Muzicman16 said:**
> Hey so i dl utorrent and at first no one could connect to me and i had the error of "Not connectable a firewall/router is limiting your network traffic. You need to open a port so others can connect to you."

after much trial and error i got firestarter to not block utorrent, and now i can actually upload to people. . .but i still have the same error.

also my ports are not forwarding anyone know of a guide or can anyone explain to me how to forward ports on utorrent.

If you use a router, you forward the ports via the router. See the documentation that came with your router.

---

### Post by markofealing on 2007-10-11
> **Muzicman16 said:**
> Hey so i dl utorrent and at first no one could connect to me and i had the error of "Not connectable a firewall/router is limiting your network traffic. You need to open a port so others can connect to you."

after much trial and error i got firestarter to not block utorrent, and now i can actually upload to people. . .but i still have the same error.

also my ports are not forwarding anyone know of a guide or can anyone explain to me how to forward ports on utorrent.

Use this excellent website:

[http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by D-EJ915 on 2007-10-11
> **kornface13 said:**
> I'm a huge utorrent fan, so when I made the ubuntu switch two days ago, utorrent is a must!!!

Anyone have any idea how to make utorrent the default torrent app?  I've tried everything I can think of.  Please help!!  Thanks in advance.

-tim
what I did was set up Opera to automatically download .torrent files to a folder and then set up µTorrent to automatically load torrents from that folder, easy as pie although not really "ideal."

---

### Post by |Eric| on 2007-10-14
ok one question one suggestion 
a- can you continue your downloads in both system in a dual boot install or it will start all over ?
b- you might want to edit your mime types so that .torrents open automaticaly 

firefox: edit --> preferences-->content-->manage [filetype section]

---

### Post by ACorky on 2007-10-28
Hi all,
running uTorrent under wine 0. 9.47 and everything runs great unless you need to access a tracker on https.

when trying tracker stats displays HTTP Reply 0

anyone else experience this?

---

### Post by Lorenz on 2007-10-30
I'm having a weird problem with utorrent, perhaps you can help me.
It used to work nearly perfect with wine, download speeds were by far higher than with Ktorrent, deluge or Azureus.

But now, I can't use utorrent anymore. Everytime I start it, the symbol appears in the task bar, but I cannot open it. I can't do anything with it anymore. Reinstalling didn't help... any suggestions?

---

### Post by ninjamonkey26 on 2007-10-30
> **Lorenz said:**
> I'm having a weird problem with utorrent, perhaps you can help me...

But now, I can't use utorrent anymore. Everytime I start it, the symbol appears in the task bar, but I cannot open it. I can't do anything with it anymore. Reinstalling didn't help... any suggestions?

Same thing has just started happening with my utorrent client
wine-0.9.47
utorrent 1.7.5

plus the flicker effect is going on.

---

### Post by MattiMg on 2007-11-02
This should work

Close uTorrent

Go to /home/username/.wine/drive_c/windows/profiles/username/Application Data/uTorrent/

Delete Settings.dat, you might also want to delete Settings.dat.old.  uTorrent might use it as a backup.

Open uTorrent.

---

### Post by SegaBoy0 on 2007-11-03
> **MattiMg said:**
> This should work

Close uTorrent

Go to /home/username/.wine/drive_c/windows/profiles/username/Application Data/uTorrent/

Delete Settings.dat, you might also want to delete Settings.dat.old.  uTorrent might use it as a backup.

Open uTorrent.

Just wantd to say thanks MattiMg!  This worked perfectly for me.

---

### Post by Fraterius on 2007-11-15
> **ACorky said:**
> Hi all,
running uTorrent under wine 0. 9.47 and everything runs great unless you need to access a tracker on https.

when trying tracker stats displays HTTP Reply 0

anyone else experience this?

Hello I've got the same problem, any ideas?? Maybe some library is missing??

---

### Post by qntal on 2008-01-04
> **MattiMg said:**
> This should work

Close uTorrent

Go to /home/username/.wine/drive_c/windows/profiles/username/Application Data/uTorrent/

Delete Settings.dat, you might also want to delete Settings.dat.old.  uTorrent might use it as a backup.

Open uTorrent.

thanks man, i love you. i've been looking for this solution for ages. :lolflag:

also you must uncheck "Close to tray" and "Minimize to tray"

---

### Post by djbon2112 on 2008-01-07
Please forgive me if this has been answered before, but I'm having an issue.

uTorrent 1.7.5, Wine 0.9.52. If I try to use an https tracker, I get "Error 12150". Anyone know of a fix?

---

### Post by laser01 on 2008-02-03
For those users who are experiencing problems with uTorrent redrawing the window after minimising the application or changing desktop, I think the problem is related to the default uTorrent behaviour to minimise to the tray rather than the taskbar.

I found that disabling this behaviour solved the problem for me.

In the "Options > Preferences > General" dialog, there is a section called "System Tray"...

Make sure the following checkboxes are NOT ticked:
- Close to tray
- Always show tray icon
- Show baloon notifications in tray
- Minimize to tray
- Single click on tray icon to open

With regard to the comments in this thread questioning the need to run uTorrent under Wine, I agree that there are some excellent Linux native BT clients (KTorrent is an great application, for example), however, some private trackers restrict the users choice of client. As a community, we need to raise the profile of native Linux BT clients to make administrators of BT trackers more aware of Linux BT clients.

---

### Post by L34NN3 on 2008-02-19
I am having a problem with port forwarding too. I have already used the link provided earlier. My download speed maxes out at about 30kb/s which is dreadful! All my ports are forwarded correctly. I do not have any firewalls. I am using Gutsy and wine .54.

It isn't not downloading torrents, its just downloading them really slowly...

---

### Post by L34NN3 on 2008-02-21
Any clues for getting downloads above 30kb/s?

---

### Post by djbon2112 on 2008-02-22
It's one of two things: either you're getting throttled (by your ISP) or the torrent you're downloading sucks. Try some other torrents, or enable encryption.

---

### Post by bernd_b on 2008-06-05
> **Fraterius said:**
>  Originally Posted by ACorky  View Post
Hi all,
running uTorrent under wine 0. 9.47 and everything runs great unless you need to access a tracker on https.

when trying tracker stats displays HTTP Reply 0

anyone else experience this?


Hello I've got the same problem, any ideas?? Maybe some library is missing??


Is this problem fixed and did I miss the answer or does no one have a clue?

---

### Post by toadtwo on 2008-06-10
> **bernd_b said:**
> Is this problem fixed and did I miss the answer or does no one have a clue?

I'd also like to know, this is quite an annoying thing.

---

### Post by JamesHolden on 2008-06-30
i'm also getting HTTP Reply 0 when tryin' to connect to ssl trackers, any resolution available?

---

### Post by ratthing on 2008-07-20
There was a bug ([178191]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/178191")) filed earlier for amd64 gutsy indicating that wine wasn't built with the SSL option.  The bug was closed indicating that the package was fixed in hardy.

I'm on hardy i386, and on first perusal, ldd suggests wine here doesn't have SSL enabled, either, since I see no reference to OpenSSL libraries when I run ldd against it.

I'm compiling by hand to check.  I'll report back when it'd done, though it will be a while since my uTorrent file server is a lowly Athlon 900. :?

=RT=

---

### Post by ratthing on 2008-07-22
I resolved the "HTTP Reply 0" issue for the private tracker I was trying to connect to.  Thanks to JamesHolden for nudging me in the right direction to find a solution.

The "HTTP Reply 0" error results from the server certificate authority chain not being recognized as valid by OpenSSL. This may be due to the cert being self-signed, a server name/URL mis-match, or any number of other issues. 

Certs are expensive and some server owners can't afford a commercially signed cert. This doesn't invalidate the cert, it just means that it's not accepted by OpenSSL for the purposes of authentication, because the identity of the certificate holder is not verified. Cryptographically such a cert is still secure, you just might want to think twice before handing over credit card info or similar to a server with such a certificate. 

Anyway, on to the fix. 

First you need to get a copy of the SSL cert for the tracker you're having the problem with. You can do this by using the 'openssl' command at the CLI on your box.  Fetching the cert *should* be straightforward unless they are doing weird things with hostnames and ports.  Assuming they are also using SSL to serve their web pages, too, then the following should work.  "server_name" refers to the tracker you need the cert from: 

```
openssl s_client -connect server_name:443 > server_name.crt
```

Type 'quit' followed by <enter> to exit the openssl program. 

The new file 'server_name.crt' will have more than just the SSL cert in it, since the whole web page is downloaded. The part you want looks like this: 

-----BEGIN CERTIFICATE----- 
bunch of cryto code... 
-----END CERTIFICATE----- 

Go to where your distro stores cert files.  On Hardy they are in "/etc/ssl" and presumably are there on earlier versions, since that is the default location in Debian.

Back up your existing ca-certificates.crt file: 

```
sudo cp ca-certificates.crt orig.ca-certificates.crt
```

Now, edit ca-certificates.crt (using sudo) with your favorite text editor and add the cert you downloaded to the bottom of the file. Paste in the **whole** certificate, which includes the "BEGIN" and "END" lines.  Save the file and exit your editor.

Next restart wine and utorrent. You should now see "working" rather than "HTTP Reply 0" for the trackers you were trying to connect to with SSL. 

**Edit**: Apparently I got ahead of myself.  While adding the invalid cert does fix rtorrent if you used a patched rtorrent, it does not fix uTorrent.  I haven't checked Transmission or other bittorrent clients.  I'm still poking around, but don't have any further suggestions at this point for wine/uTorrent.

=RT=

---

### Post by musikgoat on 2009-01-30
> **djbon2112 said:**
> Please forgive me if this has been answered before, but I'm having an issue.

uTorrent 1.7.5, Wine 0.9.52. If I try to use an https tracker, I get "Error 12150". Anyone know of a fix?

I just wanted to state,  for anyone else that tracks along this error,  I was having the problem with 1.0.1 of wine,  and updated to 1.1.14 (was development but just went stable) and the issue is fixed.

---

### Post by swiper on 2009-02-04
uTorrent is working well for me under wine in Ubuntu 8.10.
My only problem is when I select auto shutdown when downloads complete all that happens is uTorrent is closed and the computer stays on.

I wrote a simple script to check if uTorrent has closed and if so then shutdown the computer.  Hopefully this will help someone.
Remember to execute the script using sudo so shutdown can be used.
I saved my script as ushutdown and placed it in my home directory and
made it executable with chmod +x ushutdown.

Also I am open to any suggections/criticisms.

```

#!/bin/bash
##########################################################################
#
# There is an option in uTorrent to autoshutdown when downloads complete.
# However, uTorrent only closes when run using wine in Ubuntu 8.10 when 
# downloads complete. This script checks to see if uTorrent has closed and
# if so then the script shuts down the computer.  Make sure to run this script
# using sudo so the shutdown works (ex: sudo ./ushutdown)
#
# YY/MM/DD
# 09/02/03 - CDS
#
##########################################################################
searchterm="Torrent"
seconds_between_checks=60
counter=0
utorrentpid=$(ps -A | grep $searchterm | cut -b 1-5)
if [ "$utorrentpid" = "" ]; then
	echo I dont think uTorrent is open
	echo Open uTorrent first and then start this script
	echo to shutdown the computer once downloads complete
	exit
fi
while true; do
   checkpid=$(ps -A | grep $searchterm | cut -b 1-5)
   if [ $utorrentpid -eq $checkpid ];then
	clear
        echo It has been $counter minutes since script started
        let counter=counter+1
	sudo echo $counter >> a.txt
	sleep $seconds_between_checks
   else
	echo uTorrent has been closed
	sudo shutdown -h now
	exit
   fi
done

```

---

### Post by Neural oD on 2009-02-04
just for a bit of info - if you are wanting a lightweight torrent client - that is native to linux - look at rtorrent- command line based - but very capable. I would recomend that you compile from source - as the ones in the repository tend to be a bit dated! It's really great because you can control your downloads remotely off slow connections - using rtorrent, screen, and ssh

---

### Post by blakew on 2009-03-04
I'm having great trouble getting utorrent 1.8.2 working with wine 1.1.16, under xubuntu 8.10. It's getting "peer error: error 10051". had the same error with wine 1.0.1.

---

### Post by CurtisM on 2009-05-25
Hello, I recently switched to ubuntu, and I was running utorrent in wine, and I didn't set my directories properly, so I downloaded two torrents to:

C:\windows\profiles\****\My Documents\Downloads\Torrent names

It can't open the containing file in WINE, and I can't search for it in the window that pops up, a tiny Wine window pops up saying Not Yet implemented

Now, would I have to redownload these torrents to a proper directory, or is there some way of getting it to work?

---

### Post by standalone3 on 2009-06-14
hi i am a newbe at this , all i want is to get my speeds to download faster i use to get 300kb/s to 400 kb/s now i get 1.2kb/s or 4.kb/s so i was looking for help but i dont have a clue what wine is for except for drinking now i have read lots of comments and some comments say u,torrent works with wine and some say it does not, now if ifollowed the instructions i would call my self a genus as i am far from it i will have to call it a day,  i can say all my settings seam to be ok and my port is saying ok mu uploads are on green and my downloads are blue but i ownly download one at a time,  but my speed is not and i am downloading from a private tracker, i have tryied tutorials and tips for months to the best of my knowledge somt times my speed goes up to 14.6kb/s like i tryied one here and it put myport to yellow tryangle so i put it back it was upnp i unticked it, any way i can get my head around any thing on hereas i am a bit thick to say the least but i will come back when my head is a bit clearer lol.:( oh i for got to say i am useing 1.6.1 u,torrent

---

### Post by bodhi.zazen on 2009-06-14
Why not use a linux native torrent client ? Transmission is one of several options.

---

### Post by iBurger on 2009-06-18
good point. I'm really fed up with uTorrent too. 
However, I can label torrents with it. *which is AWESOME.. :(

---

### Post by karlmp on 2009-08-15
rtorrent is the best

[http://www.ubuntugeek.com/list-of-bittorrent-clients-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-bittorrent-clients-available-in-ubuntu.html)

there's also wtorrent

---

### Post by iBurger on 2009-08-21
This is very decent guide;

[http://filesharefreak.com/tutorials/linux-setup-xorg-vncserver-wine-utorrent/](http://filesharefreak.com/tutorials/linux-setup-xorg-vncserver-wine-utorrent/)

---

### Post by shuddupnspend on 2009-08-25
This is addressed to fellow nubes.

I was looking for this kind of info a while ago.  I dunno if this helps anyone, but I have uTorrent running in Vista x64 and it is sharring a download directory (on my sata ntfs volume) with kTorrent which is running in jaunty9.04.

They play nicely with the same toys, one after the other depending whith OS I use.

Maybe I'm just redicovering the wheel here but It was news to me.
Now I can be downloading the same stuff no matter what size  & no matter which OS I boot to.
No special install procedure except setting the location for downloads & remembering to Log into the user acc (for the folder I'm using from my windows user account) befor I launch kTorrent in Ubuntu.

Please, if this is stating the obvious just roll ur eyes and move on

But nubes, if I have 50% of the DL file complete and move to the other OS where I havent ever opened the .torrent file yet, I can just locate that torrent file, double click and which ever program I am using, loads the torrent, sees the data (that has already been DL'd by the other program), checks it, and just picks the ball up an continues to run from where the othe program left off.

 I'm so impressed that I wish I could buy the company!

ps
Nice HowTo!

---

### Post by Zewbie on 2009-08-26
I use deluge, very much like utorrent no need to run utorrent under WINE

---

### Post by ashwinhgtx on 2009-11-18
My torrent speeds are lower when using Deluge, Transmission, qBittorrent or utorrent on Karmic. Only rtorrent matches the speeds I get using utorrent in XP. 
I haven't capped any upload/download speeds.

Can anyone help me figure this out?

---

### Post by Zewbie on 2009-11-18
are you using wifi if so that may be your problem. When I was duel booting with XP and Ubuntu. XP seemed to always connect at higher speeds. I did some forums reading to find out the Ubuntu wifi drivers were crap for some cards.  I installed ndiswrapper (lets you use windows driver in Ubuntu) and all was well.

Hoped this helps

---

### Post by ashwinhgtx on 2009-11-19
> **Zewbie said:**
> are you using wifi if so that may be your problem. When I was duel booting with XP and Ubuntu. XP seemed to always connect at higher speeds. I did some forums reading to find out the Ubuntu wifi drivers were crap for some cards.  I installed ndiswrapper (lets you use windows driver in Ubuntu) and all was well.

Hoped this helps

No I'm using an ADSL line. I connect to my modem via an ethernet port.

---

### Post by Sciamano on 2009-12-20
I'm having a weird problem with uTorrent, lately.
It used to work perfectly with wine, with download speeds by far higher than with any other torrent program. But lately new added torrents just sit there, and don't start.
If I close uTorrent and open it again, they start immediately... what could it be??
Of course the "don't start the download automatically" preference voice is UNCHECKED.

---

### Post by cubsacub on 2009-12-20
Over a year ago, I switched to Ubuntu after an unrecoverable Vista kernel crash after an AUTHORIZED update. Needless to say, that was the last straw.

---

### Post by a.toraby on 2010-08-30
How can I associate .torrent files to utorrent?

---

