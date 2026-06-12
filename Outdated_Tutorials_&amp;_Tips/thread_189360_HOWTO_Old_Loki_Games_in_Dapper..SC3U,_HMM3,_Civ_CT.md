---
title: "HOWTO: Old Loki Games in Dapper..SC3U, HMM3, Civ CTP..and more!"
date: 2006-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Footissimo on 2006-06-05
**_Preamble_**

Old [Loki](http://www.lokigames.com/) games, some of which are still sold by [Tuxgames](http://www.tuxgames.com) are becoming more and more difficult to just install.  Hopefully this HOWTO will help you install Heroes of Might and Magic 3, Heavy Gear 2, Heretic 2, Simcity 3000 Unlimited, Civilization: Call To Power etc (see below).  Some of the stuff may well apply to other Loki games...I just don't know.  I'm not a technical person - I just got the information from [this site](http://members.shaw.ca/dan.mckay/LokiInst.html), [Linux Questions](http://www.linuxquestions.org), Google searches and a bit of guesswork. These games installed on Ubuntu Dapper, 32bit with a Nvidia (5700VE) card..don't know about other set-ups, if you want me to try then send me a computer :P

For this HOWTO, I'll assume you are installing systemwide in /usr/local/games and that you'll fiddle with temporary patches and what not in the user home.

***IMPORTANT:**With all the loki installers, don't press 'play' when the installer has finished if you have installed as root (i.e. sudo) as that will play the game as root and the preferences directory (i.e. '.loki') will have root permissions.  Just press exit, then use the command or menu item instead.*
***[COLOR="Red"]EVEN MORE IMPORTANT:[/COLOR]** the 'sunsite' mirror used for the various patches and updates in these guides is now deaded, so you'll have to use ```
ftp://mirrors.dotsrc.org/lokigames
``` instead*

Games Covered:

Civilization: Call To Power
Heavy Gear 2
Heretic 2
Sim City 3000 Unlimited
Heroes of Might and Magic 3
Railroad Tycoon 2


**_Sim City 3000 Unlimited_**

Open a terminal window (Applications->Accessories->Terminal). Go to wherever the CD is mounted:
```
cd /media/cdrom0
```

Start the installer, for me, I checked all the options:
```
sudo sh setup.sh
```

Download the patch:
```
cd ~/
```
```
wget ftp://sunsite.dk/mirrors/lokigames/updates/sc3u/sc3u-2.0a-x86.run
```

Run the patch (plus --keep, not sure why, but it seems to solve a usagetrap error):
```
sudo sh sc3u-2.0a-x86.run --keep
```

Run the game, but assume an older kernel version:
```
LD_ASSUME_KERNEL=2.4.26 /usr/local/bin/sc3u
```

Fingers crossed, it should work!

Getting it to work as a menu item is another pain!  There should be a item under 'Games' in Alacarte, but it won't work, so we make a little script to run the program:
```
gedit
```

Add the following:
```
#!/bin/sh
cd /usr/local/games/SC3U
LD_ASSUME_KERNEL=2.4.26 /usr/local/bin/sc3u
```

Save as something obvious, like 'sc3ulaunch' or similar, then make it executable and move it to the right directory:
```
chmod +x sc3ulaunch
```
```
sudo mv sc3ulaunch /usr/local/bin
```

You can now change the menu entry in Alacarte to 'sc3ulaunch' and it should work!

Get rid of the faff:
```
cd ~/ (or wherever you downloaded the patches to)
```
```
rm sc3u-2.0a-x86.run
```
```
sudo rm -rf sc3u-2.0a-x86
```


**_Civilization: Call To Power_**

Civ is relatively painless, just need the correct patch.

Open a terminal window (Applications->Accessories->Terminal). Go to wherever the CD is mounted:
```
cd /media/cdrom0
```

Start the installer (create the symlink in /usr/local/bin, when it asks):
```
sudo sh install
```

The game will work, but with issues, soooo download the patch:
```
cd ~/
```
```
wget ftp://sunsite.dk/mirrors/lokigames/updates/civctp/civctp-1.2a-english-unified-x86.run
```

There are a variety of different patches, but it's the english-unified that seems to work.

Run the civctp patch:
```
sudo sh civctp-1.2a-x86.run
```

When done, remove the faff:
```
rm civctp-1.2a-english-unified-x86.run
```

There is an entry in Alacarte, but it didn't seem to show up (for me), so I toggled the visibility off and then on again and that seemed to sort it (weird!)


**_Heroes of Might and Magic 3_**

Open a terminal window (Applications->Accessories->Terminal). Go to wherever the CD is mounted:
```
cd /media/cdrom0
```

Start the installer (create the symlink in /usr/local/bin, when it asks):
```
sudo sh setup.sh
```

You can run the game, though (for me) without the patch it doesn't run fullscreen (amongst other issues), so download the patch:
```
cd ~/
```
```
wget ftp://sunsite.auc.dk/pub/os/linux/loki/updates/heroes3/heroes3-1.3.1a-unified-x86.run
```

The patch will segfault if you try to run it.  Run it with the 'keep' option (it will still segfault, but bear with me!):
```
sh heroes3-1.3.1a-unified-x86.run --keep
```

We need to patch the patch (*sigh*), go to the offending directory and remove the dodgy file:
```
cd heroes3-1.3.1a-unified-x86/bin/Linux/x86/
```
```
rm loki_patch
```

Download the new loki_patch and make it executable:
```
wget http://www.step-n-up.com/downloads/loki_patch
```
```
chmod +x loki_patch
```

Go back a few directories and run the update (now as root):
```
cd ../../../
```
```
sudo sh update.sh
```

Hopefully that should now work, I found no problems with the menu item - use that or type:
```
heroes3
```

To remove the faff:
```
cd ~/
```
```
sudo rm -rf heroes3-1.3.1a-unified-x86
```
```
rm heroes3-1.3.1a-unified-x86.run
```


**_Heretic 2_**

Open a terminal window (Applications->Accessories->Terminal). Go to wherever the CD is mounted:
```
cd /media/cdrom0
```

Start the installer (create the symlink in /usr/local/bin, when it asks):
```
sudo sh setup.sh
```

A load of errors will probably appear in the terminal window - can't find the bin/x86/heretic file, several directories etc etc.  These will be fixed after install...just let it carry on for now.

Lets move that file manually.  Remember to change 'cdrom0' to whatever your cdrom directory is called:
```
sudo cp /media/cdrom0/bin/x86/glibc-2.1/heretic2 /usr/local/games/heretic2/
```

Create a symbolic link from the heretic2 file to the /usr/local/bin directory, so running Heretic is easier:
```
sudo ln  -s  /usr/local/games/heretic2/heretic2 /usr/local/bin
```

To get the program to run, we also need the two patches:
```
cd ~/
```
```
wget ftp://sunsite.auc.dk/pub/os/linux/loki/updates/heretic2/heretic2-1.06b-unified-x86.run
```
```
wget ftp://sunsite.auc.dk/pub/os/linux/loki/updates/heretic2/heretic2-1.06c-unified-x86.run
```

Running the patches will cause a segfault, sooo time to patch the patches:
```
sh heretic2-1.06b-unified-x86.run --keep
```

This will still cause a segfault, but no worries, just change directories:
```
cd heretic2-1.06b-unified-x86/bin/Linux/x86/
```

Delete the borked loki_patch and download the newer one:
```
rm loki_patch
```
```
wget http://www.step-n-up.com/downloads/loki_patch
```

Change the permissions:
```
chmod +x loki_patch
```

Back up a few directories and run the update:
```
cd ../../../
```
```
sudo sh update.sh
```

You need to do exactly the same for the 1.06c patch, summarised:
```
cd ~/
```
```
sh heretic2-1.06c-unified-x86.run --keep
```
```
cd heretic2-1.06c-unified-x86/bin/Linux/x86/
```
```
rm loki_patch
```
```
wget http://www.step-n-up.com/downloads/loki_patch
```
```
chmod +x loki_patch
```
```
cd ../../../
```
```
sudo sh update.sh
```

You can now play the game by typing:
```
heretic2
```

To create a menu item, just load Alacarte and use the command 'heretic2'.  The icon is messed up - if you want a better one then:
```
wget http://aslan.homelinux.com/dana/icons/games/heretic2.png
```
```
sudo mv heretic2.png /usr/share/pixmaps/
```

There should now be a slightly better Heretic icon in your default icon directory :)

Lastly, clean up the faff:
```
cd ~/
```
```
sudo rm -rf heretic2-1.06b-unified-x86
```
```
sudo rm -rf heretic2-1.06b-unified-x86
```
```
rm heretic2-1.06b-unified-x86.run
```
```
rm heretic2-1.06c-unified-x86.run
```

Heavy Gear 2 HOWTO will be added onto this later :)

---

### Post by Footissimo on 2006-06-07
**_Heavy Gear II_**

This is a complete pain, but after a bit of googling and guesswork, it seems to work using OpenGL and systemwide.

Open a terminal window and install the freetype 2 - this seems to work for the old freetype package needed for the game:
```
sudo apt-get install freetype2
```

Go to whereever the cdrom is mounted (cdrom0 for me) and install:
```
cd /media/cdrom0
```
```
sudo sh setup.sh
```

I chose to just install the base, movies and the 'recommended' libararies to the default /usr/local/games/hg2 directory.  After installing you can try the game, but it'll probably through up some errors as seen on [this thread](http://ubuntuforums.org/showthread.php?t=180560).  Get the patch:
```
cd ~/
```
```
wget ftp://sunsite.auc.dk/pub/os/linux/loki/updates/hg2/hg2-1.0b-unified-x86.run
```

Run that patch with the keep option:
```
sudo sh hg2-1.0b-unified-x86.run --keep
```

Again, running the game will throw up similar errors.  We need to modify the  hg2 script.  Assume a default install:
```
 sudo gedit /usr/local/games/hg2/hg2
```

A text editor window should pop up.  Look out for this bit of the script:
```
fullpath="`ls -l "$fullpath" | awk '{print $11}'`"
```

Change that $11 to $10.  Save the modified script.

You should now be able to play the game:
```
hg2
```

Unfortunately, it doesn't seem to make an menu item.  It's fairly straightforward, just make a new entry in Alacarte Menu Editor and use the command 'hg2'.  If you need a better icon:
```
wget http://aslan.homelinux.com/dana/icons/games/hg2.png
```
```
sudo mv hg2.png /usr/share/pixmaps
```

This will put a slightly better HG2 icon in the default icon directory.

To remove the faff:
```
cd ~/
```
```
rm hg2-1.0b-unified-x86.run
```
```
sudo rm -rf hg2-1.0b-unified-x86
```

Hopefully that'll work :)


**_Railroad Tycoon 2_**

Much the same as Civ:CTP, this is an easy one to install, so I'll just summarise the instructions:

```
cd /media/cdrom0 (or whereever your CDRom is mounted)
sudo sh setup.sh
cd ~/
wget ftp://sunsite.auc.dk/pub/os/linux/loki/updates/rt2/rt2-1.54c-unified-x86.run (download patch)
sudo sh rt2-1.54c-unified-x86.run --keep

```

Type 'rt2' to run. A menu item appeared for me, but only after logging in and out of GNOME.  If one doesn't appear then just use Alacarte with the command 'rt2' - an icon will also be in /usr/local/games/RT2, though its not the best (working on that!)

To remove the faff:
```
cd ~/
rm rt2-1.54c-unified-x86.run
sudo rm -rf t2-1.54c-unified-x86
```

---

### Post by nukedog on 2006-06-08
Damn!
So close, got the same old error about not being able to access  /home/nukedog/.loki/
So I went to the terminal and used "sudo hg2"
to launch, and got all the way to launching a mission, wich never started, crashed and gave me:

hg2: FATAL: could not initialize OpenGL Library 'libGL.so.1'

It's no fun being a newb...

Video card is an Nvidia NV20 GEforce 3 if that matters.
](*,)

---

### Post by Footissimo on 2006-06-08
Hmm..sounds like your permissions on the .loki directory (its the hidden directory that saves preferences, save games etc as user) are wrong.  If you just delete the .loki directory then it will remake it when you try again:

If HG2 is the only loki game installed then you can safely do:

```
cd ~/
sudo rm -rf .loki
```

to delete the loki folder - it will be reinstalled when you start the game again (as user)

You should be able to run it as user now (i.e. just hg2)

The other problem - is direct rendering enabled?  If you're unsure then:

```
glxinfo | grep direct
```

If no then you need to get your graphics drivers sorted (there are tons of threads on that..and stuff in the wiki)

Also, did you make sure the box was pressed to install the GL Drivers (after which is said 'Strongly Recommended' or something like that when installing?

If the answer is yes to both of them, then I'd imagine that you haven't got a necessary library installed - look in Synaptic (System->Admin->Synaptic Package Manager) for possible culprits - there is a libgl1 package, though it would be difficult NOT to have that installed :)

Best I can do atm - not very technical myself!

---

### Post by nukedog on 2006-06-08
I got:

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

So you are right.
I'll work on my drivers when I get home from work.
Thank you for all your help.

---

### Post by Footissimo on 2006-06-08
Bear with it, it all becomes a lot easier :)

There's a good HOWTO, on Nvidia drivers in the Wiki [here](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29),  if you have one.

---

### Post by nukedog on 2006-06-08
](*,) 
God I'm dumb.
I got my computer so screwed up, It wouldn't even boot!
I'm back from re-installing, and I'm startin' again!
:mrgreen:

---

### Post by nukedog on 2006-06-09
I got it all back togeather, followed your instructions, and now have the drivers working, but get:

 error while loading shared libraries: libgthread-1.2.so.0: cannot open shared object file: No such file or directory

:-k

---

### Post by ildfroe on 2006-06-29
I can't get simcity to work:mad: 
I can see the intro movie, but after that I just get a black screen with the mouse pointer and some music.
Any help???

This is the output:
```
$LD_ASSUME_KERNEL=2.4.26 /usr/local/bin/sc3uCreating sc3u preferences directory: /home/claus/.loki/sc3u
fcntl: Operation not permitted
fcntl: Operation not permitted
MESSAGE:

BUG! (Segmentation Fault)  Going down hard...
SimCity 3000 Unlimited 2.0.955a
Built with glibc-2.1 on x86
Stack dump:
{
        0xffffe420
        0xb6eb5c52
        0xb79e5342
        0xb77587e0
        0x814a685
        0x8358123
        0x8358da0
        0x8359253
        0x8153291
        0xb7d5c31f
        0x8144ca1
}
Please send a full bug report,
along with the contents of autosave to: support@lokigames.com
Unable to execute loki_qagent - exiting

```

---

### Post by Footissimo on 2006-06-29
Could you tell me which version of Ubuntu and which video card..and if direct rendering is working:

```
glxinfo | grep direct
```

[This ](http://ubuntuforums.org/showthread.php?t=21087&page=2&highlight=sim+city+3000+unlimited) old thread suggests trying different kernel versions.  You could try running it with:

```
LD_ASSUME_KERNEL=2.2.5 /usr/local/bin/sc3u
LD_ASSUME_KERNEL=2.2.5 /usr/local/bin/sc3u
```

etc :)

---

### Post by ildfroe on 2006-06-29
I'm on a Dapper with ATI and direct rendering is working.
Tried assuming different kernels, but still just a black screen:( 
There was a guy in that other old thread with the same problem, but no solution.

---

### Post by Footissimo on 2006-06-29
I just thought I'd try out my installation myself and found that the-previously-working-perfectly-well installation is now doing the music to the video but not the video itself.  The game does play but I now have to press enter or click to get to the intro screen.  When I have some time, I'll do a fresh reinstall and see what problems are coming up.

The only other thing I can think of off the top of my head is to try and redo the loki-patch within the sc3u patch - see the Heretic instructions, though I think I remember trying this before and it coming up with some checksum errors

*sigh* :(

---

### Post by ildfroe on 2006-06-30
No, the loki-patch dosn't work now.
I guess I won't be playing this game again:(
Thanks for trying though;)

---

### Post by Footissimo on 2006-07-02
Sorry :(

Tried reinstalling it twice with my own instructions and it worked both times. Looked around the innernet and found a few people with similar problems to you (i.e. similar seg fault and stack dump) but with no answers and Loki doesn't exist to report the fault to :( Even tried removing the libraries mentioned in the dynamic executable README (openal, libsmpeg and opensdl), but I just can't replicate your seg fault.  I even tried playing with xorg resolutions and modules :( :( If you are having problems with other games (particularly the old loki games) then I'd post your xorg.conf to here and the vid forums...you could try reinstalling, if you haven't already (may just be a disk transfer error) - note I did check all options in the loki menu (for data packs and whatnot).

Otherwise

:(

---

### Post by ildfroe on 2006-07-02
Well, thanks for trying;)

I suppose it might be my laptop and the fglrx driver. Sometimes when a game (through cedega) changes resolution the screen will just get blank. However that can be fixed by ctrl-alt-f2 and the back with ctrl-alt-f7, but thats not the case with simcity:(

---

### Post by Rasymas on 2006-07-06
I used loki to install MAFIA on my machine. Installation was peace of cake, but I coulnd't start the game, even If I had the required video drivers. Now it only uses space, and I don't need that. So waht should I type in order to remove MAFIA from my machine? :roll:

---

### Post by Footissimo on 2006-07-06
Did you install it as root?  i.e. 'sudo'

---

### Post by SYSDmg on 2006-07-07
So i followed your little walkthrough and it works sorta...and when i say works i mean it actually will execute the game and then gives me a xlib error and then locks my x session. I think it has something to do with something I did to get xgl working properly...any thoughts?

---

### Post by Rasymas on 2006-07-09
> **Footissimo said:**
> Did you install it as root?  i.e. 'sudo'

I guess so.. Here's the command I used to install the game:

```
sudo sh mafia_1.2-english.run
```

so how to remove the game now? :k

---

### Post by Footissimo on 2006-07-09
> **SYSDmg said:**
> So i followed your little walkthrough and it works sorta...and when i say works i mean it actually will execute the game and then gives me a xlib error and then locks my x session. I think it has something to do with something I did to get xgl working properly...any thoughts?

Sorry for not replying sooner.  Never used XGL, but I remember there was a post about how to get OpenGL apps and XGL to work nice.  What happens if you disable XGL?

> **Rasymas said:**
> I guess so.. Here's the command I used to install the game:

```
sudo sh mafia_1.2-english.run
```

so how to remove the game now? :k

Well the game is probably in /usr/local/games/mafia or something like that.  Go to that directory (or whatever the directory has been named and look for an uninstall script).  If you're not sure, try this in terminal:

```
cd /usr/local/games
ls
```

A list of directories under /usr/local/games should appear, type:

```
cd mafia
ls
```

..assuming the mafia directory is called mafia ;)

Now look for a uninstall script....then run it as root:
```
sudo sh uninstall
```

If the file is named uninstall.sh or .run then just add that - 8/10 its just uninstall.

Hope that helps :)

---

### Post by Footissimo on 2006-07-09
Oh and Mafia works in wine, though the howto in the wine database suggests moving it from windows to wine, which may be pointless if you don't have windows

[Wine DB](http://appdb.winehq.org/appview.php?iAppId=1693)

---

### Post by SYSDmg on 2006-07-10
So i disabled xgl temperarily (yea i cant spell, whaddya gonna do about it?) and ran the kernal command and this is what i get:

sysdmg@lapdmg:~$ LD_ASSUME_KERNEL=2.4.26 /usr/local/bin/sc3u
fcntl: Operation not permitted
fcntl: Operation not permitted
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  20
  Current serial number in output stream:  21


Im sorta newb with gui's and anythign thats no command line oriented and all this x stuff is way over my head
I kinda think if i tried another kernel it might work, so i just tried 2.5 ( i dont know which kernles to use) and it gave me a black screen with some laggy sim city music... hopefully your wonderfull wisdom can help out

---

### Post by Footissimo on 2006-07-10
As I said in the HOWTO - I'm not a techie person myself ;) 

The kernels I've seen mentioned to try are 2.2.5 and 2.2.4 - try those, however, the fact that it came up with:

```
X Error of failed request: BadMatch (invalid parameter attributes)
```
Would suggest (according to [this](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)) that YUV acceleration needs to be disabled.  When you make the SC3U launcher (as stated in the HOWTO) you could just add:

```
#!/bin/sh
cd /usr/local/games/SC3U
SDL_VIDEO_YUV_HWACCEL=0
LD_ASSUME_KERNEL=2.4.26 /usr/local/bin/sc3u
```

See if that works for ya.

---

### Post by cucisan on 2006-07-10
hm great howto!

just wondering if there is a way to install homm3 from the windowscd version like there is for e.g. tribes2. 
the data seems to be split in many .cab files. maybe i just need the loki installer? (setup.sh, xml config file for the installer, ...?)

any help would be very much appreciated ;)

ps: it is known to run with wine.. but not the network part - which is the most important to me.. =:)

---

### Post by SYSDmg on 2006-07-11
nope, same error, and then when i try 2.2.5 it will get me into the game with laggy sound again and then i have to kill x to do anything

---

### Post by Footissimo on 2006-07-11
> **cucisan said:**
> hm great howto!

just wondering if there is a way to install homm3 from the windowscd version like there is for e.g. tribes2. 
the data seems to be split in many .cab files. maybe i just need the loki installer? (setup.sh, xml config file for the installer, ...?)

any help would be very much appreciated ;)

ps: it is known to run with wine.. but not the network part - which is the most important to me.. =:)

I was about to type 'Wine' but then saw your PS :( The wine db says that 'hotseat' MP is the problem...I presume this is what you're talking about? Making a loki installer is waaaay beyond me, and I doubt that it would help anyway as its just a way of automating the installation (with wine) AFAIK.  

You could try talking to the nice people [here](http://www.liflg.org/), but, like I said, if the issue is about specific components of directx that wine can't deal with, then, you're buggered, sorry :(

Otherwise, it's ebay time.  Would it be illegal to use BT if you have a copy from another platform?

> **SYSDmg said:**
> nope, same error, and then when i try 2.2.5 it will get me into the game with laggy sound again and then i have to kill x to do anything

Is the composite extension still loaded despite XGL being turned off (i.e. is it still present in your xorg.conf)..as this may be the cause of your troubles - if the composite extension is still in Xorg then try commenting it out, rebooting, then trying SC3U.

I'll try loading the composite extension on my computer and see if I can replicate your error

---

### Post by Román on 2006-07-11
I got Rune to run, but I don't have any graphics card so OpenGL gets so slow I couldn't really play it.

But I can tell you that yo have to set ```
LD_ASSUME_KERNEL=2.4.26
```** AND **```
RUNE_DATA_PATH={path_to_rune}/System/
```.

For a standard setup that is ```
RUNE_DATA_PATH=/usr/local/games/rune/System/
```

---

### Post by sarolite on 2006-07-13
I can install the game fine. However, when I try to install the patch as per the directions on the top post, I get:

> root@patti:/usr/share/games/CivCTP# sh civctp-1.2a-english-unified-x86.run
Verifying archive integrity...OK
Uncompressing Civilization: Call To Power 1.2a Update..............................................................................................................................................................
./update.sh: line 56: loki_patch: command not found
The program returned an error code (1)

When I try to run the game (both before and after the failed patch install), I get (*edit: I get this error when I either hit "Play Tutorial" or try to start a single player game after having selected all the game options. When it needs to load/create a map, in other words.*):
> 
Failed loading /usr/share/games/CivCTP/dll\\map\\geometric.dll: libc.so.6: ELF file class not __ELF_WORDSIZE-bitMap Generator Error: Could not load library /usr/share/games/CivCTP/dll\\map\\geometric.dll, using builtin map generator
Fatal signal: Floating Point Exception (SDL Parachute Deployed)

BUG! (Segmentation Fault)  Going down hard...
Killed

I'm sad. Any advice? I'm a noob, but if something goes over my head, I'll have my husband do it! :-#

---

### Post by Footissimo on 2006-07-13
I'm pretty sure thats what happens when the game isn't patched (vaguely remember it letting me in, but not to actually play).

Try the patch again, but with the keep option i.e.

Go home:```
 cd ~/
```
Redownload the patch: ```
wget ftp://sunsite.dk/mirrors/lokigames/updates/civctp/civctp-1.2a-english-unified-x86.run
```
Run the patch using as user:```
sh civctp-1.2a-english-unified-x86.run --keep
```

Don't apply it at this point (it won't anyway as the game is installed as root), we just want to expand out the patch.

Go into the patch directory:```
cd civctp-1.2a-english-unified-x86/bin/Linux/x86
```

Remove the possibly dodgy file:```
rm loki_patch
```

Download the new loki_patch and make it executable:
```
wget http://www.step-n-up.com/downloads/loki_patch
```
```
chmod +x loki_patch
```

Go back a few directories and run the update (now as root):
```
cd ../../../
```
```
sudo sh update.sh
```

Try it out:```
civctp
```

I'm just guessing from the errors that you listed that it's something to do with the dodgy loki-patch file (it's problematic on other Loki Entertainment games).  Sometimes just running the patch (unaltered i.e. "sudo sh civctp-1.2a-english-unified-x86.run --keep") with the --keep bit works..haven't got a clue why..if you do this before patching the loki-patch file, then note that the new civctp directory will be kept with root permissions)

Hope that helps

---

### Post by HAARP on 2006-07-26
I managed to get Heavy Gear 2 running on my own.
Had to copy the CD on my hard drive and rename the 2 .tar archives to tar.gz. Then I had to lowercase everything since copying off the disk made it case-sensitive.
Now I managed to install it. To avoid the error
```
Couldn't run Heavy Gear 2 (hg2stub). Is HEAVY_GEAR_2_HOME set?
```
I have to cd into the directory HG is installed into and launch it from there. Now it gets me into the menu and I can set it up.

However, when I try to play, I get this when moving:

[[IMG]http://img76.imageshack.us/img76/3163/hg2000fa5.th.jpg[/IMG]](http://img76.imageshack.us/my.php?image=hg2000fa5.jpg)

That's right, the textures are smeared all over the place when moving. Can't play that!
I encountered this before, when noclipping in games and you look at a place without any textures. I tried fiddling with the graphics settings with no success.
Any ideas? Is it possible to force the game into Software-rendering?

---

### Post by HAARP on 2006-07-28
- Resolved -
Apparently, you have to use the same resolution in X as in the game. It's a pity I can't set anything higher than 1024x768 in the game, so I have to set X to 1024 in order to play the game..

---

### Post by rpalyvoda on 2006-08-10
Hi,

I'm not able to install the patch for CivIII

> =============================================================
Would you like to apply this update? [Y/n]: y

Please enter the installation path: []: /usr/local/games

=============================================================
Performing update:
Creating uninstall script, this may take a while...
Computing MD5 sums for new uninstaller, this may take a while...
cp: cannot stat `/usr/local/games/civctp': No such file or directory
ERROR: Can't find /usr/local/games/civctp.dynamic
romko@romko:~/civctp-1.2a-english-unified-x86$


Does anyone has any idea as to where is my mistake?

Thanks,

---

### Post by christooss on 2006-09-14
I patched simcity. Then I start it and movie loads and than when I click enter there is only cursor. No text or other things.

When I run sc3bat it works like it should.

Any solutions?

---

### Post by christooss on 2006-09-14
I saw that ildfroe asked same question. But still no solution :(

---

### Post by dolny on 2007-03-14
Anybody knows how to get sound in Rune :( ?

```
Bound to ALAudio.so
open /dev/dsp: Device or resource busy
open /dev/dsp: Device or resource busy
Audio initialization failed.

```

OK, nevermind - had to change permissions for /dev/dsp and turn off Exaile ;) Yeah! time for some Rune multiplayer.

---

### Post by Volatile314 on 2007-08-27
Hm, it seems like the loki_patch link is down. Could you post it again, please?

---

### Post by Volatile314 on 2007-08-27
> **Volatile314 said:**
> Hm, it seems like the loki_patch link is down. Could you post it again, please?

...ehm, loki_patch to heroes of might and magic 3, that is...

---

### Post by _march_ on 2007-10-01
Hi :)
Some links concerning this Thread:
[loki_patch]("http://icculus.org/~msphil/loki/x86/")
[Patches 4 HOMM]("ftp://mirrors.dotsrc.org/lokigames/patches/heroes3/")
[SimCity 3000 unlimited - Patches]("ftp://mirrors.dotsrc.org/lokigames/patches/sc3u")
[CivCTP Patches]("ftp://mirrors.dotsrc.org/lokigames/patches/civctp")
[heretic2 - Patches]("ftp://mirrors.dotsrc.org/lokigames/patches/heretic2/")
[updates]("https://babelize.org/download/lokigames/updates/")
[addons, patches, demos and more]("http://www.holarse-linuxgaming.de/h2006/space/Holarse+FTP+Server") - just hit *>>Zum FTP-Server*

Some Howtos (German) can be found at: [ubuntuusers.de](http://wiki.ubuntuusers.de/Spiele) 

_march_ 8)

---

### Post by DoOrDoNot on 2008-08-09
Has anyone gotten Heavy Gear 2 to install and work in Hardy Heron?  I just got the Loki Linux CD from Amazon.  Have gone through the threads with bash to install and have tried to work the patch.  Can't get the patch to patch, however.  I think I will go crazy soon if I can't play this game.  Mechwarrior 2 in DosBox only goes so far.  Thanks very much for any advice.

---

### Post by theadmiral on 2008-12-16
I am trying to install the heroes 3 patch however i can only find patches with the error
"Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 814399959 1999548749"

Do you know a way around this?

---

### Post by Phantom Power on 2008-12-21
I had the same issue, and found the fix for it [here]("http://www.g-loaded.eu/2007/02/25/error-when-using-old-runbin-installers-under-linux/"). I've posted the relevant bit in case that page disappears.

> In order to resolve this issue and make the installer “assume” that you use an old GNU/Linux version, you should export the following environment variable before using the installer:

```
export _POSIX2_VERSION=199209
```

After you finish installing the software, delete that ENV variable:

```
unset _POSIX2_VERSION
```

It took me a significant amount of time to learn about this workaround and, basically, I discovered it while searching for the software that creates these self-installing archives.

Hope this tip helps someone out there.

---

### Post by theadmiral on 2009-01-02
Thanks that worked

for anyone else coming along this error you will still get an error but run the patch with ' -keep' parameter and it runs successfully.

---

### Post by _march_ on 2009-02-09
I got most of my Loki games working - you'll find articles at [http://wiki.ubuntuusers.de via googletranslate](http://translate.google.de/translate?hl=de&sl=de&tl=en&u=http://wiki.ubuntuusers.de/Spiele&prev=hp) or [http://wiki.ubuntuusers.de/Spiele](http://wiki.ubuntuusers.de/Spiele).

Did anyone got Heavy Gear II working? 
[LIST=1]
 [*] I started *sudo _POSIX2_VERSION=199209 ./setup.sh*
 [*] installed package **libttf2**
 [*] patched the game with **hg2-1.0a-x86.run** and **hg2-1.0b-x86.run**
 [*] tried to install the update *sudo _POSIX2_VERSION=199209 ./hg2-1.0b-cdrom-x86.run --keep* or without option *--keep* - but it didn't work :(
[/LIST]
```

sudo _POSIX2_VERSION=199209 /bin/bash ./hg2-1.0b-cdrom-x86.run --keep
Creating directory hg2-1.0b-cdrom-x86
Verifying archive integrity...OK
Uncompressing Heavy Gear II 1.0b Update..............................................
=============================================================
Welcome to the Heavy Gear II 1.0b Update
=============================================================

Would you like to read the README for this update?  [Y/n]: n

=============================================================
Would you like to apply this update? [Y/n]: 

=============================================================
Performing update:
Computing MD5 sums for new uninstaller, this may take a while...
ERROR: No matching delta for /usr/local/games/hg2/credit.txt
The program returned an error code (3)

```
This creates a folder containing e.g. **update.sh** - running this file 
```
sudo _POSIX2_VERSION=199209 /bin/bash ./update.sh 
=============================================================
Welcome to the Heavy Gear II 1.0b Update
=============================================================

Would you like to read the README for this update?  [Y/n]: n

=============================================================
Would you like to apply this update? [Y/n]: 

=============================================================
Performing update:
Computing MD5 sums for new uninstaller, this may take a while...
ERROR: No matching delta for /usr/local/games/hg2/credit.txt


```
Any solutions? I already tried things mentioned in this thread and on [members.shaw.ca](http://members.shaw.ca/dan.mckay/LokiInst.html).

_Usefull links:_
[LIST]
[*][members.shaw.ca](http://members.shaw.ca/dan.mckay/LokiInst.html)
[*][Updates, patches ...](http://lokifiles.tuxgames.com/)
[/LIST]

---

### Post by ernstblaauw on 2009-05-07
I updated my railroad tycoon to version 1.54c. However, I still do not get sound. In the terminal, I only get the message:

```
Warning: Unable to open audio: No available audio device
```

I tried to change permissions of /dev/dsp, but still no sound (and same message). I'm running Jaunty. Can anyone help fixing the sound?

---

### Post by Dry Heat on 2009-05-23
Railroad Tycoon 2 sound issues are also being discussed under this thread:

[http://ubuntuforums.org/showthread.php?p=7334016#post7334016](http://ubuntuforums.org/showthread.php?p=7334016#post7334016)

I have sound with RT2 under Ubuntu 9.04.  I am using the ALSA sound driver instead of the default PulseAudio.

Perhaps you can try that?

Dry Heat

---

