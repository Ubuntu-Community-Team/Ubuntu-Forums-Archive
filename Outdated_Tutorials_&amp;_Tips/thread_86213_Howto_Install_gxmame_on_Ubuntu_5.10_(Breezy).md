---
title: "Howto: Install gxmame on Ubuntu 5.10 (Breezy)"
date: 2005-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2005-11-04
1. Get file:
```
wget -c http://mikesplanet.net/deb/gxmame_0.35beta2-1~breezy_i386.deb
```
2. Install xmame-x:
```
sudo apt-get install xmame-x
```
*Note: you can substitute xmame-sdl or xmame-svga for xmame-x. It matters what works best for you.*

3. Install File:
```
sudo dpkg -i gxmame_0.35beta2-1~breezy_i386.deb
```
4. Restart Gnome Panel:
```
killall gnome-panel
```

---

### Post by christooss on 2005-11-04
Where can I get mame games?

---

### Post by Technoviking on 2005-11-04
[QUOTE=christooss]Where can I get mame games?[/QUOTE]
That would be telling:). Seriously, you should be able to fine a few legal roms via Google.

Mike

---

### Post by logan5 on 2005-11-04
I would do a google search for "rom world"

---

### Post by Logic* on 2005-11-04
Thx Mike, worked great

---

### Post by christooss on 2005-11-04
Thanks I found faboulus page with lots of games.

Is downloading legal? Im just wondering is this piracy

BTW it works fine. Thanks :)

---

### Post by bored2k on 2005-11-04
It's legal as long as you own a legal copy of the game you are downloading. If not, you are advised (by the download sites) to remove the game after a month. And no, do not post links here.

---

### Post by bored2k on 2005-11-04
[CENTER][IMG]http://img91.imageshack.us/img91/1664/screenshotxmamex11version086oc.png[/IMG]
Street Fighter Alpha 3

[IMG]http://img91.imageshack.us/img91/7756/screenshotxmamex11version086oc1.png[/IMG]
King of Fighters '99

[IMG]http://img91.imageshack.us/img91/9095/screenshotxmamex11version086oc2.png[/IMG]
Hah! I can't believe I can still lay the smackdown X-D.


Sad it doesn't recognize my KOF2000/2003|Metal_Slug4/5, but it's still **great** :).[/CENTER]

---

### Post by christooss on 2005-11-04
1942 -Counter Attack
[img]http://www.shrani.si/pics/1942124817.jpeg[/img]

I have spend alot of coins on this game when I was little

---

### Post by bored2k on 2005-11-04
Heh :). 19XX is even better.

---

### Post by Technoviking on 2005-11-04
I have made Breezy debs for xmame/xmess 0.100, but have not tested them yet.

If you want to test them, you can down load them from my website:
```

wget -c http://mikesplanet.net/deb/xmame-common_0.100-1~breezy_all.deb
wget -c http://mikesplanet.net/deb/xmame-gl_0.100-1~breezy_all.deb
wget -c http://mikesplanet.net/deb/xmame-sdl_0.100-1~breezy_i386.deb
wget -c http://mikesplanet.net/deb/xmame-svga_0.100-1~breezy_i386.deb
wget -c http://mikesplanet.net/deb/xmame-tools_0.100-1~breezy_i386.deb
wget -c http://mikesplanet.net/deb/xmame-x_0.100-1~breezy_i386.deb
wget -c http://mikesplanet.net/deb/xmess-common_0.100-1~breezy_all.deb
wget -c http://mikesplanet.net/deb/xmess-x_0.100-1~breezy_i386.deb
```
*Please Note: xmame-gl_0.100-1~breezy_all.deb is just a pseudo file.*

---

### Post by bored2k on 2005-11-04
Any difference between the one on repos and those?

---

### Post by Technoviking on 2005-11-04
[QUOTE=bored2k]Any difference between the one on repos and those?[/QUOTE]
The repos is at version 0.86. 

Mike

---

### Post by bored2k on 2005-11-05
Your build did not support OSS, which is the sound system that worked here.
Did not detect the few Neo-Geo games I have here, which the other build did.
I had to go back-

---

### Post by Technoviking on 2005-11-05
[QUOTE=bored2k]Your build did not support OSS, which is the sound system that worked here.
Did not detect the few Neo-Geo games I have here, which the other build did.
I had to go back-[/QUOTE]
I will work on that.

Mike

---

### Post by bored2k on 2005-11-05
Something weird just happened (on old xmame): apparently, neogeo games are a HUGE load on the system (maybe because it needs to load the neogeo.zip first? it escapes me). Anyways, any neogeo game turtles down my box and my hdd led strts flashing like there's no tomorrow. before loading the game i mistakenly set the video to XV Fullscreen and when i tried to load KOF 2000 (which now appears on list), after a long waiting time, it loaded, but soonly after, froze my X.

Bottom line: don't touch neogeo games people.

---

### Post by jmeadows111 on 2005-11-05
Here is my question -- I have installed gxmame, and am trying to get this game to run -- a screen pop-up, and runs through a loop well enough, but how do I actually get the game to start???

I am feeling distinctly stupid!:confused: 

[QUOTE=christooss]1942 -Counter Attack
[img]http://www.shrani.si/pics/1942124817.jpeg[/img]

I have spend alot of coins on this game when I was little[/QUOTE]

---

### Post by christooss on 2005-11-05
You have to copy zip file in /usr/share/games/xmame/roms and than click refresh and go to avalible map and than select a game and than play game

---

### Post by kemmer on 2005-11-17
I am having problems help!!!!!
bob@ubuntu:~$ wget -c [http://mikesplanet.net/deb/gxmame_0.35beta2-1~breezy_i386.deb](http://mikesplanet.net/deb/gxmame_0.35beta2-1~breezy_i386.deb)
--15:45:34--  [http://mikesplanet.net/deb/gxmame_0.35beta2-1~breezy_i386.deb](http://mikesplanet.net/deb/gxmame_0.35beta2-1~breezy_i386.deb)
           => `gxmame_0.35beta2-1~breezy_i386.deb'
Resolving mikesplanet.net... 62.214.98.58
Connecting to mikesplanet.net|62.214.98.58|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

bob@ubuntu:~$ sudo apt-get install xmame-x
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmame-x
bob@ubuntu:~$
I had it installed once but it would not find roms i down loaded so i uninstalled it and i cant get it to work i am a noob and dont know what i am doing help!:confused:

---

### Post by lizardking on 2005-11-18
When I start gxmame it says that I have not executable found!
I tried to set them in /usr/games/xmame but it says:"not valid executable!"
If I do this in terminal I get:
lizardking@lizard:~$ xmame.x11
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  22 (XDGAOpenFramebuffer)
  Serial number of failed request:  12
  Current serial number in output stream:  12

help

---

### Post by christooss on 2005-11-18
Do you have a directory caled /usr/share/gxmame?

---

### Post by DaMasta on 2005-12-05
Anyone get a controller working? I got the buttons on my Logitech Dual Action working but not the sticks. I ran jscalibrator so I know they are recognized. Also, is there key maps for the games or is kind of learn as you go?

---

### Post by thenoobest1 on 2005-12-05
[QUOTE=christooss]1942 -Counter Attack
[img]http://www.shrani.si/pics/1942124817.jpeg[/img]

I have spend alot of coins on this game when I was little[/QUOTE]

one of the best games ever... other than Mario Kart

---

### Post by BLTicklemonster on 2005-12-06
Cool!!! This is awesome!!!! I've been looking for something to make my screen go black and make me panic, and the other night, I thought I had found it, but I'd just accidently kicked the monitor plug loose, but this program totally kicks!!! 


(actually, what I meant to say is, I installed it, now what? I mean, I can type gxmame in terminal, and I get a black screen. It stays black for a loooong time. Is there something else I need to do?)

---

### Post by BLTicklemonster on 2005-12-11
Crap, I killed another thread.

Okay, if anyone wants to draw this noob a picture, here's the deal:

I have it where it comes up alright. It shows tons of games, none of which I have. I downloaded marvel something vs streetfighters, extracted the contents into /usr/share/games/xmame/roms only after

```
cd /usr/share/games/xmame/roms/

sudo chown myname /usr/share/games/xmame/roms/
```

for pwnership.

But it still doesn't do anything.

Someone said copy the zip there, hit refresh, etc. I suppose he didn't mean extract, but to physically copy?

Still wanting to play, just not getting it.


*edit:

like the man said, copy to and refresh. Okay. Now. Insert coins? I'm going to have to go back to the website and find out what button does what now. Ooookay. Looks cool, though.

Thanks.

---

### Post by Wallakoala on 2005-12-11
i have a question...
Is there anyway to rename what it says on the gnome menu...because the name is really long and it bothers me for some reason
nevermind...i figured it out

---

### Post by Wallakoala on 2005-12-11
alright...i got a game running...but what are the dang controls? I randomly pressed buttons to get pass "Insert Coin", but once i get into the game I cant figure out how to fire! btw im playing 1941 counter attack if anyone can help me.

---

### Post by drift.addict on 2005-12-12
I get some sort of error about wine, my wine install corrupted, can anyone help me? email me please, at [email]drift.addict@gmail.com[/email]
thanks alot
-Adam

---

### Post by BLTicklemonster on 2005-12-15
[QUOTE=Wallakoala]alright...i got a game running...but what are the dang controls? I randomly pressed buttons to get pass "Insert Coin", but once i get into the game I cant figure out how to fire! btw im playing 1941 counter attack if anyone can help me.[/QUOTE]
what he said!!!!

---

### Post by Mosey on 2005-12-16
How come when I attempt to run most of the games I've downloaded it gives me an error saying it can't find certain files...

Are the games incomplete?

What gives?

---

### Post by BLTicklemonster on 2005-12-16
I think if you are going to start a how to thread you need to hang around and give help when requested.

Everyone pm this guy: [http://ubuntuforums.org/member.php?u=5551](http://ubuntuforums.org/member.php?u=5551) and ask him your questions.


Of course, I may be totally wrong, but it's worth a shot.

---

### Post by Wallakoala on 2005-12-16
Alright I figured out the controls. Press tab on the keyboard while in the game in order to show a menu, and then press "Controls, This Game" There will be a list of the controls for that game. 

I hope this helps.

---

### Post by Technoviking on 2005-12-16
[QUOTE=BLTicklemonster]I think if you are going to start a how to thread you need to hang around and give help when requested.

Everyone pm this guy: [http://ubuntuforums.org/member.php?u=5551](http://ubuntuforums.org/member.php?u=5551) and ask him your questions.


Of course, I may be totally wrong, but it's worth a shot.[/QUOTE]
Just because I built a working package does not mean I can solve every problem with it.

I get plenty of PM and e-mails asking for help, which I try to answer if I have the time (I have a job and a family). Please do ask to PM me asking for help, that are what the forums are for.

Mike

---

### Post by viscount on 2005-12-17
yep this worked for me, got a few games to run.

My wife is gonna love this, shes really into the old-school arcade 
type things, im more a WoW type of guy, but now that my account
has expired maybe I'll take up something new.

If someone has time, i would really apprecaite a key-listing for 
the controller commands for xmame, the game loads but
i can barely figure out the controls and just do a lot of mashing
until i find something that sort of works.

lil help?

---

### Post by BLTicklemonster on 2005-12-17
Okay Mike, my bad. Sorry, and thanks for this, it's cool as heck. My wife was seen playing on my machine just yesterday! (she's the one who says, I'm not getting on that linux thing)

---

### Post by leongor on 2005-12-17
After installation by post #1 I have black screen only and can do nothing, only restart my KDE. :confused:

---

### Post by Mosey on 2005-12-17
When I start the program i get an error that says  'No Executables found'?

What do I do?

---

### Post by Mosey on 2005-12-17
b-b-b-b-b-b-b-bump!

---

### Post by Mosey on 2005-12-17
Hmm...this thread apparently already has both feet in the grave.

So for the past couple hours i've been scanning forums and googling the hell out of this program and it seems that xmame is just damn near obsolete when it comes to playing most of the Mame roms hiding out there on the internet.

Okay.

So I decided to try advancemame...and advancemenu because I enjoy working with a GUI far far more than code.

I succesfully installed both.

On my first run I got this error:

[I]admin@ubuntu:~/Desktop/advancemenu-2.4.12$ advmenu
AdvanceMENU - Copyright (C) 1999-2004 by Andrea Mazzoleni
Emulator 'advmame' without rom files, ignoring it.
No working emulator found. Adjust the `emulator' options in your configuration
file. These options are documented in the `advmenu.txt' file.[/I]

Apparently it ignores any emulators without Rom files in them. Okay...i'll bite...I found and installed a Rom and ran it again:

[I]admin@ubuntu:~/Desktop/advancemenu-2.4.12$ advmenu
AdvanceMENU - Copyright (C) 1999-2004 by Andrea Mazzoleni
Unable to initialize the video driver. The errors are:
fb: Unsupported in X.[/I]

No dice.

It says in the documentation that it is in fact compatable with X. So what gives?

---

### Post by wargames on 2005-12-17
[QUOTE=leongor]After installation by post #1 I have black screen only and can do nothing, only restart my KDE. :confused:[/QUOTE]

Me too. I only get a black blank screen and then I have to restart gnome. Something is wrong here. :(

---

### Post by BLTicklemonster on 2005-12-17
???

```
trell@ubuntu:~$ wget -c http://mikesplanet.net/deb/gxmame_0.35beta2-1~breezy_i386.deb
--23:39:43--  http://mikesplanet.net/deb/gxmame_0.35beta2-1~breezy_i386.deb
           => `gxmame_0.35beta2-1~breezy_i386.deb'
Resolving mikesplanet.net... 62.214.98.58
Connecting to mikesplanet.net|62.214.98.58|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 258,572 (253K) [text/plain]

100%[====================================>] 258,572      250.73K/s

23:39:50 (250.21 KB/s) - `gxmame_0.35beta2-1~breezy_i386.deb' saved [258572/258572]

trell@ubuntu:~$ sudo apt-get install xmame-x
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmame-x
trell@ubuntu:~$
```

---

### Post by BLTicklemonster on 2005-12-18
This is a bit distressing. His link doesn't say he has xmame-x any more is what I think. I worked around as much as I could and got xmame and xmame common debs, and sudo apt-get -f install and it installed them, and for all intents and purposes, it looks like everything is there, but still, I get no executable found.

Can anyone help with this?

---

### Post by Mosey on 2005-12-19
For whatever reason...the package is no longer isntalling the executable file. Just some docs etc...

---

### Post by Wallakoala on 2005-12-21
One of my favorite games....

[[IMG]http://img287.imageshack.us/img287/1664/screenshotxmamex11version086oc.png[/IMG]](http://imageshack.us)    [[IMG]http://img410.imageshack.us/img410/1664/screenshotxmamex11version086oc.png[/IMG]](http://imageshack.us)

[[IMG]http://img287.imageshack.us/img287/7756/screenshotxmamex11version086oc1.png[/IMG]](http://imageshack.us)

Its pretty cool that I can actually beat the game because of unlimited credits

---

### Post by tawie on 2005-12-22
[QUOTE=Wallakoala]One of my favorite games....

[[IMG]http://img287.imageshack.us/img287/1664/screenshotxmamex11version086oc.png[/IMG]](http://imageshack.us)    [[IMG]http://img410.imageshack.us/img410/1664/screenshotxmamex11version086oc.png[/IMG]](http://imageshack.us)

[[IMG]http://img287.imageshack.us/img287/7756/screenshotxmamex11version086oc1.png[/IMG]](http://imageshack.us)

Its pretty cool that I can actually beat the game because of unlimited credits[/QUOTE]

hi, what 's name of this game? it's wonderful,  thanks a lot.

---

### Post by Wallakoala on 2005-12-22
[QUOTE=tawie]hi, what 's name of this game? it's wonderful,  thanks a lot.[/QUOTE]

That game is metal slug 2

---

### Post by bored2k on 2005-12-22
The Metal SLug series is amazing. It's also about 200 times better than Shock Troopers, the other Spek-SNK platform game. 

Playing Metal SLug online (thanks to Kaillera) with a buddy is just mind-blowing. 

[http://en.wikipedia.org/wiki/Metal_Slug](http://en.wikipedia.org/wiki/Metal_Slug)

---

### Post by Wallakoala on 2005-12-22
[QUOTE=bored2k]The Metal SLug series is amazing. It's also about 200 times better than Shock Troopers, the other Spek-SNK platform game. 

Playing Metal SLug online (thanks to Kaillera) with a buddy is just mind-blowing. 

[http://en.wikipedia.org/wiki/Metal_Slug](http://en.wikipedia.org/wiki/Metal_Slug)[/QUOTE]

Im just wondering...how do you play it online? As I already said, Metal Slug is seriously like my favorite game and I am extremely happy to be able to play it on gxmame. Btw...what are your specs because you said that neo-geo games crashed your comp. I ran metal slug full screen very smoothly. But I have pentium 4 3.4 and a gig of ram.

---

### Post by GameGod on 2005-12-23
I am the only one that GXMame is ridiculously unstable for?

---

### Post by bored2k on 2005-12-23
> **Wallakoala]Im just wondering...how do you play it online? As I already said, Metal Slug is seriously like my favorite game and I am extremely happy to be able to play it on gxmame. Btw...what are your specs because you said that neo-geo games crashed your comp. I ran metal slug full screen very smoothly. But I have pentium 4 3.4 and a gig of ram.[/QUOTE]You just need to run (via wine, cedega or crossover office said:**
> [http://www.kaillera.com/](http://www.kaillera.com/)[/CENTER]
 	 
[QUOTE]Kaillera enables emulators to play on the Internet.

It consists of a client and a server. The client is usually embedded into your favorite emulator and the server is a stand-alone application that needs to be run on a machine directly wired to the Internet. 		

**Kaillera features:**
[LIST]
[*]- Small, fast and efficient C++ code.
[*]- UDP use for better latency.
[*]- Intelligent networking cache code.
[*]- Multi-platform support.
[*]- Low to no lag for players with good ping.
[*]- Works through firewalls.
[*]- LANs/WANs support.
[/LIST]


**Note:** After playing old games online like those fantastic 4 player arcade games (Simpsons, etc) and those things you just said "I wish I could play this online" (does Street Fighter II ring a bell?), alongside with games that are just fantabulous anyways (Metal Slug, King of Fighters (4Players!), Capcom ones (!)), you might lose your social life for quite a while... trust me.

---

### Post by Wallakoala on 2005-12-23
> **bored2k]You just need to run (via wine, cedega or crossover office said:**
> [http://www.kaillera.com/](http://www.kaillera.com/)[/CENTER]
 	 


**Note:** After playing old games online like those fantastic 4 player arcade games (Simpsons, etc) and those things you just said "I wish I could play this online" (does Street Fighter II ring a bell?), alongside with games that are just fantabulous anyways (Metal Slug, King of Fighters (4Players!), Capcom ones (!)), you might lose your social life for quite a while... trust me.

omfg thanks so much! I'm gonna try this right now. I love that simpsons arcade game btw...

---

### Post by Wallakoala on 2005-12-23
[QUOTE=Wallakoala]omfg thanks so much! I'm gonna try this right now. I love that simpsons arcade game btw...[/QUOTE]

I have one problem with kaillera now....
I got the emulator working fine with wine, the and I can play all of my roms with it, but when I go online and try to join a game it tells me that I don't have the rom, but I can still play it with single player. I want to be able to play it online, so if you can help bored2k that would be fabulous.

---

### Post by anil_robo on 2005-12-26
I have roughly 4GB of ROMs lying around for quite some time. I haven't tested all of them, but tested the majority of neo-geo ones and they worked fine with NeoRageX. But when I load the same roms in xmame, it doesn't recognize any of the files! It gives errors! Why?

Is there any way I can rename the contents of zip file to make them compatible? I have the game, why can't I run it?

---

### Post by BLTicklemonster on 2005-12-26
[QUOTE=Mike Basinger]1. Get file:
```
wget -c http://ftp.us.debian.org/debian/pool/non-free/x/xmame/xmame-x_0.100-1_i386.deb
```
2. Install xmame-x:
```
sudo apt-get install xmame-x
```
*Note: you can substitute xmame-sdl or xmame-svga for xmame-x. It matters what works best for you.*

3. Install File:
```
sudo dpkg -i gxmame_0.35beta2-1~breezy_i386.deb
```
4. Restart Gnome Panel:
```
killall gnome-panel
```[/QUOTE]

This just worked for me.

---

### Post by andlinux21 on 2006-02-08
Where do i place the roms from my CD to the hard drive so that xmame can see and run them. I made a folder /home/MAME/roms and dropped them all there but gxmame or xmame couldnt see them when i tried to launch from xterm window:confused:

---

### Post by Master Shake on 2006-02-17
SOrry to bump this up, but using xmame and gxmame, I can't get any sound from the games.  I know the roms are good, as they work on my win partition.  The audio device is a Soundblaster Live!

Anyy ideas on what to check?

EDIT:  Never mind.  Didn't have an audio device selected...

---

### Post by johansonm on 2006-02-23
[QUOTE=andlinux21]Where do i place the roms from my CD to the hard drive so that xmame can see and run them. I made a folder /home/MAME/roms and dropped them all there but gxmame or xmame couldnt see them when i tried to launch from xterm window:confused:[/QUOTE]


/usr/share/games/xmame/roms

---

### Post by SVFUSiON on 2006-02-24
if i run from terminal i get a black screen, if i run the gui i get the x-mame file can not be found. Any ideas?

---

### Post by mushroom on 2006-02-24
I've installed both of these, but neither executables are found.

---

### Post by SVFUSiON on 2006-02-24
::BuMP::

---

### Post by johansonm on 2006-02-24
[QUOTE=mushroom]I've installed both of these, but neither executables are found.[/QUOTE]

My Gxmame exicutable is located:

```
-rwxr-xr-x  1 root root 308368 2005-11-04 13:00 /usr/games/gxmame
```

and my xmame is located:

```
lrwxrwxrwx  1 root root 23 2006-02-18 09:02 /usr/games/xmame -> /etc/alternatives/xmame
```


Maybe its just a perms issue?

---

### Post by Micro Rotors on 2006-02-25
[QUOTE=SVFUSiON]if i run from terminal i get a black screen, if i run the gui i get the x-mame file can not be found. Any ideas?[/QUOTE]

My screen goes black in the terminal and GUI. I can not get out of it unless I hit CTL+ALT+Backspace and login again.

---

### Post by SVFUSiON on 2006-02-25
that worked. but now when I try to play a rom it tells me all the files are not there, that are where it says in the gxmame config. Any ideas?

---

### Post by johansonm on 2006-02-25
[QUOTE=SVFUSiON]that worked. but now when I try to play a rom it tells me all the files are not there, that are where it says in the gxmame config. Any ideas?[/QUOTE]

Did you do a refresh? It won't find them normally until you force it to.

---

### Post by andlinux21 on 2006-02-26
followed the howto but i get no xmame executable found anyone else have that problem???

---

### Post by nicky75 on 2006-03-01
[QUOTE=andlinux21]followed the howto but i get no xmame executable found anyone else have that problem???[/QUOTE]

I have too :cry:

---

### Post by parktownprawn on 2006-03-01
[QUOTE=Micro Rotors]My screen goes black in the terminal and GUI. I can not get out of it unless I hit CTL+ALT+Backspace and login again.[/QUOTE]

I had the same problem - i think it has something to do with xmame-x and my graphics card. Seems to work fine with xmame-sdl. Try

```

sudo apt-get install xmame-sdl
sudo apt-get remove xmame-x
```

---

### Post by SVFUSiON on 2006-03-05
that did nothing for me. I am running the latest ATI drivers with an ATI Xpress 200m.

---

### Post by bob-o on 2006-03-05
Having the same issue. None of the above steps worked for me either. :(

---

### Post by mpeters13 on 2006-03-16
Windows: 1
Linux: 0

---

### Post by nicky75 on 2006-03-16
I think that problem is 3D accelleration, I had a ATI graphic card (ATI AIW 8500DV) and Gxmame didn't found xmame executable (and I had some problems with 3D acceleration). Now I have bought a NVIDIA card and works fine \\:D/

---

### Post by ubuntublue on 2006-03-17
oh to get metal slug 2 to work download neogeo rom ....

---

### Post by zi99y on 2006-03-25
If anyones interested I found the problem with the black screen on Mame - at least, this worked on my machine using KXMame. I believe the problem has to do with the DGA video mode when running an ATI graphics card with the fglrx drivers, which is buggy and/or broken.

I have been tweaking around with my xorg.conf file and made the following changes:

Under Section "Module"
```
	SubSection "extmod"
		Option "omit xfree86-dga" #Don't initialize the DGA extension
	EndSubSection

```
And commented out the extmod module with a #, like so
```
#	Load	"extmod"
```

Restarted X with a ctrl+alt+backspace and voila! I no longer get the black screen when launching kxmame/gxmame. It took quite a lot of investigation, I hope someone finds this useful.

---

### Post by SiMoNsAyS on 2006-03-30
tried it and yes, it solves the black screen problem but... i also get no 3d and i revert back to mesagl drivers :(

---

### Post by zi99y on 2006-03-30
Sorry to hear that :( but I can be sure and tell you that the DGA module isn't essential for opengl, because my setup still works. 

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5642 (8.22.5)

```

I tweaked around for hours to find this, I can't tell you much more detail I'm afraid.

---

### Post by SiMoNsAyS on 2006-03-30
ok finally got it working... tip: remove kernel restricted modules before trying it :D

@zi99y, didn't say thanks for the info ;)

---

### Post by tore- on 2006-04-12
Is there any chance to get this up to .105 or .104? Im currently building my own arcade-cab and have troubles with compiling my own xmame.

---

### Post by WARMACHINE on 2006-06-19
```

info: trying to parse: /etc/xmame/xmamerc
error: /etc/xmame/xmamerc(71): unknown option joyusb-calibrate, ignoring line
info: trying to parse: /home/max/.xmame/xmamerc
info: trying to parse: /etc/xmame/xmame-x11rc
info: trying to parse: /home/max/.xmame/xmame-x11rc
info: trying to parse: /etc/xmame/rc/pacmanrc
info: trying to parse: /home/max/.xmame/rc/pacmanrc
I386 joystick interface initialization...
OSD: Warning: No joysticks found disabling joystick support
loading rom 0: pacman.6e
loading rom 1: pacman.6f
loading rom 2: pacman.6h
loading rom 3: pacman.6j
loading rom 4: pacman.5e
loading rom 5: pacman.5f
loading rom 6: 82s123.7f
loading rom 7: 82s126.4a
loading rom 8: 82s126.1m
loading rom 9: 82s126.3m
done
pacman.6e    NOT FOUND
pacman.6f    NOT FOUND
pacman.6h    NOT FOUND
pacman.6j    NOT FOUND
pacman.5e    NOT FOUND
pacman.5f    NOT FOUND
82s123.7f    NOT FOUND
82s126.4a    NOT FOUND
82s126.1m    NOT FOUND
82s126.3m    NOT FOUND
ERROR: required files are missing, the game cannot be run.


```

eh?

i did as told to do and i installed all the other stuff in synaptic..and i get this message

---

### Post by andlinux21 on 2006-07-11
is there any update for this i can download the beta

---

### Post by r3dux on 2006-08-18
zi99y, Thanks for the info! That was some fine detective work! =D

Modifying the xorg.conf worked perfectly for me (no back to mesa issues); the only reason I hadn't seen the black screen problem before was because I was running kxmame under compiz whenever I'd tried it, which worked fine right off the bat..

Again, many thanks,
r3dux

P.S This was on Ubuntu 6.06, not 5.10

---

