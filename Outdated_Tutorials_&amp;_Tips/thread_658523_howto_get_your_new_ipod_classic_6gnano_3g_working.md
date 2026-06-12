---
title: "howto: get your new ipod classic 6g/nano 3g working"
date: 2008-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by twright on 2008-01-04
**[COLOR=Red]this tutorial is not needed for hardy, only gutsy[/COLOR]**

Apple have recently released a new look for their ipods, but with the new interface comes more firmware encryption to stop 3rd party media players (including Amarok, Rhythmbox and gtkpod) syncing music to the ipods.

Since there is no itunes for linux it was up to the guys at[ http://ipodminusitunes.blogspot.com]("http://ipodminusitunes.blogspot.com/") to crack it.

  This should work for any new nanos and ipod classics. Please be aware that this is rather experimental so please make sure that you have all of the music on you ipod backed up before attempting it. The programs instanlled by this tutorial are from the hardy repository so don't be supprised if they break stuff. 

If this causes all music to disappear off your ipod you don't need to access a windows machine to fix it, when you get it working you can sync new music on and it will appear.

This will only work with applications which use libgpod (rhythmbox, amarok and gtkpod). Finally as of rhythmbox version 0.11.5 podcasts are sorted as podcasts although only amarok and gtkpod seem to be able to transfer album art.

here's how to get it working (type this into terminal one line at a time, use the same terminal session for all):
 
```
sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.tmp
echo deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse >> /etc/apt/sources.list
apt-get update
aptitude install libgpod3 libgpod-common
```if you use rhythmbox:
```
aptitude install rhythmbox
```if you use amarok:
```
aptitude install amarok
```if you use gtkpod:
```
aptitude install gtkpod

```then:```
aptitude remove libgpod2
```this may prompt you to remove the ubuntu-desktop package, don't worry - it's only a meta-package

then check if it works. if it does run
```
rm /etc/apt/sources.list
mv /etc/apt/sources.list.tmp /etc/apt/sources.list
apt-get update
```Banshee not supported (it uses it's own library rather than libgpod)

***thanks to [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/) for the tutorial i origanally based this on***

---

### Post by TheOrangePeanut on 2008-01-07
This worked perfectly.  I'm using Linux Mint 4 and Amarok.  Thanks.

---

### Post by reclusivemonkey on 2008-01-07
I don't seem to be able to get Album Art working at all with gtkpod; has anyone had any luck with this? Its not so much that the iPod doesn't recognise album art, its gtkpod itself that flatly refuses to set any artwork.

---

### Post by Sukarn on 2008-01-07
> **reclusivemonkey said:**
> I don't seem to be able to get Album Art working at all with gtkpod; has anyone had any luck with this? Its not so much that the iPod doesn't recognise album art, its gtkpod itself that flatly refuses to set any artwork.

What exactly is the error you get? I've had album art working since I got my iPod Classic back in November.

---

### Post by reclusivemonkey on 2008-01-07
> **Sukarn said:**
> What exactly is the error you get? I've had album art working since I got my iPod Classic back in November.

[http://ubuntuforums.org/showpost.php?p=4051032&postcount=87](http://ubuntuforums.org/showpost.php?p=4051032&postcount=87)

I hear plenty of people have got it working but its eluding me =[

I followed the instructions at the beginning of that post to get it working, and the songs transfer great and I can see my ratings/plays etc. but the Album Art flat out refuses to work from gtkpod. I think I am going to upgrade to Hardy Heron soon and see if that works for me.

---

### Post by Sukarn on 2008-01-07
DO NOT DO THIS IF YOU ARE NOT GOOD AT FIXING A BROKEN SYSTEM.

OK, This may sound like a daunting or stupid idea to you, and many people here would suggest against it, but i would tell you to manually download and install (using dpkg) the following packages as well as each dependency error you get, from debian unstable (sid).

[libgpod3](http://packages.debian.org/sid/libgpod3)
[libgpod-common](http://packages.debian.org/sid/libgpod-common)

I am assuming that you followed a compiling guide and installed the libgpod package from source code and named it libgpod2.

That is how I have my iPod Classic running happily. The above packages for base functionality with gtkpod and other programs, + python-gpod and the required dependencies from debian unstable for gPodder (audio podcast program).

If you encounter any error you cannot solve, then ask away.

---

### Post by reclusivemonkey on 2008-01-07
> **Sukarn said:**
> DO NOT DO THIS IF YOU ARE NOT GOOD AT FIXING A BROKEN SYSTEM.

OK, This may sound like a daunting or stupid idea to you, and many people here would suggest against it, but i would tell you to manually download and install (using dpkg) the following packages as well as each dependency error you get, from debian unstable (sid).

[libgpod3](http://packages.debian.org/sid/libgpod3)
[libgpod-common](http://packages.debian.org/sid/libgpod-common)

I am assuming that you followed a compiling guide and installed the libgpod package from source code and named it libgpod2.

That is how I have my iPod Classic running happily. The above packages for base functionality with gtkpod and other programs, + python-gpod and the required dependencies from debian unstable for gPodder (audio podcast program).

If you encounter any error you cannot solve, then ask away.

Sounds like a plan to me =] Cheers, I will try that when I get home. My Gutsy has already had plenty thrown at it, a bit more won't hurt!

---

### Post by Sukarn on 2008-01-08
> **reclusivemonkey said:**
> Sounds like a plan to me =] Cheers, I will try that when I get home. My Gutsy has already had plenty thrown at it, a bit more won't hurt!

I'm waiting for a report on your progress.

---

### Post by reclusivemonkey on 2008-01-08
I installed Hardy Heron on my laptop and had some degree of success with gtkpod; I could add album artwork although I didn't save it to my iPod as I didn't want to mess things up just yet. I think I will hold on until Hardy Heron comes out and then try managing my iPod on that although gPixpod seems to throw a wobbly when it looks at the Photo Database.

---

### Post by Sukarn on 2008-01-08
> **reclusivemonkey said:**
> I installed Hardy Heron on my laptop and had some degree of success with gtkpod; I could add album artwork although I didn't save it to my iPod as I didn't want to mess things up just yet. I think I will hold on until Hardy Heron comes out and then try managing my iPod on that although gPixpod seems to throw a wobbly when it looks at the Photo Database.

I would not suggest using GPixPod or gtkpod with your photos just yet. Neither of them seems to work well right now (latest version) with iPod Classic.
After using GPixPod, the iPod doesn't display thumbnails in albums but displays the photos in the right panel and in full screen.
With gtkpod its the other way round. It doesn't display the photos in full screen or in the right panel, but only displays thumbnails.

Right now I visit a friend's place to sync my photos. I have it set up such that I made a Data directory on my iPod and a Photos directory inside the data directory. I put all my photo albums inside this Photos directory and then I have it set up on my friend's comp so that it automatically synchronizes my iPod with the Data\Photos directory present on the very same iPod.
Works like a charm.

---

### Post by reclusivemonkey on 2008-01-08
> **Sukarn said:**
> 

Right now I visit a friend's place to sync my photos. I have it set up such that I made a Data directory on my iPod and a Photos directory inside the data directory. I put all my photo albums inside this Photos directory and then I have it set up on my friend's comp so that it automatically synchronizes my iPod with the Data\Photos directory present on the very same iPod.
Works like a charm.  Use Windows and iTunes? That's what I am doing now, but its a pain. I am seriously considering buying a Mac this year just to end all these hassles!

---

### Post by twright on 2008-01-08
Apple only encrypt the firmware in order to make you buy a Mac (honestly they are worse than Microsoft) so please don't give in to their tyranny

you would probably be better off buying an iRiver or another more open device with ogg support and no firmware locking

alternative some people have been managing to run iTunes in wine (i tried and failed)

also make sure that you don't let iTunes update your iPod firmware, they are likely to change the encryption soon

i myself have been using Windows XP in Virtual Box up to now but i shall probably abandon that as iTunes doesn't recognize most of my album art anyway

---

### Post by SecondTwo on 2008-01-09
Hey - This worked perfectly for me, but only AFTER I plugged my shiny new iPod classic into a Windows box.  It didn't work straight out of the package.  Just a heads up for people experiencing the same problem.  Thanks!

---

### Post by reclusivemonkey on 2008-01-09
> **twright said:**
> Apple only encrypt the firmware in order to make you buy a Mac (honestly they are worse than Microsoft) so please don't give in to their tyranny


Erm, I think you'll find apple are a commercial entity; people choose to buy their products. Tyranny is a completely different concept.

> **twright said:**
> you would probably be better off buying an iRiver or another more open device with ogg support and no firmware locking

Well, firstly I got my iPod free. I got it from one of those free iPod websites; I can confirm it does work! I also looked around at a lot of different mp3 players and the iPod classic was by far the cheapest per Gb of storage. Ogg support is fine if you use ogg; I personally don't. The next best alternative was a Cowon but again it was a lot more than the iPod (if I had to pay for it).

> **twright said:**
> 
i myself have been using Windows XP in Virtual Box up to now but i shall probably abandon that as iTunes doesn't recognize most of my album art anyway

iTunes did ok with my album art. It found most stuff, and that which it didn't I added easily myself. Unfortunately when I sync my iPod, the album art doesn't all transfer. It gets most of it, but some of it isn't quite right

---

### Post by twright on 2008-01-09
> Well, firstly I got my iPod free. I got it from one of those free iPod websites; I can confirm it does work! I also looked around at a lot of different mp3 players and the iPod classic was by far the cheapest per Gb of storage. Ogg support is fine if you use ogg; I personally don't. The next best alternative was a Cowon but again it was a lot more than the iPod (if I had to pay for it).
i mean that switching mp3 players is a lot cheaper than switching to a mac

> Erm, I think you'll find apple are a commercial entity; people choose to buy their products. Tyranny is a completely different concept.
They attempt to lock you into using their products. The only difference between them and Microsoft is that Microsoft is more successful

---

### Post by reclusivemonkey on 2008-01-10
> **twright said:**
> i mean that switching mp3 players is a lot cheaper than switching to a mac


They attempt to lock you into using their products. The only difference between them and Microsoft is that Microsoft is more successful

I'm not simply considering buying a Mac just for a mp3 player. I need a new computer.

Again, I don't buy the lock in. If you know nothing about computers it might work, but I have freedom of choice. I don't have to buy a Mac to use an iPod; I don't have to buy my music from iTunes to use an iPod.

---

### Post by twright on 2008-01-10
> I'm not simply considering buying a Mac just for a mp3 player. I need a new computer.
fair point, Macs are good computers :)

> Again, I don't buy the lock in. If you know nothing about computers it might work, but I have freedom of choice. I don't have to buy a Mac to use an iPod; I don't have to buy my music from iTunes to use an iPod.why else has apple put multiple checksums on the database and encrypted the firmware, you don't just buy a Mac becuase it supports the ipod better, but you are much more likly to because of it

---

### Post by Robert Leithe on 2008-01-11
I take it it's a bad sign when you follow the instructions here, connect your iPod, start Amarok, lists the iPod's content, add to it, disconnect it and it says No Albums, No Artists, No Playlists etc etc.
However, it still says 73,0 GB Used and 1,2 GB Free

Any ideas?

Sincerely
Robert Leithe

---

### Post by twright on 2008-01-11
i haven't tested it with amarok (only rhythmbox) but it should work :confused:

if you have all your music still in itunes you could reset your ipod otherwise the music is still on there, just not registering (you can get it off with difficulty)

if you can reset without loosing anything can you try it in rhythmbox?

---

### Post by Robert Leithe on 2008-01-12
I ended up doing a complete reset (iPod attached to a Windows computer) and copying all the music over from scratch. I think I'll wait another while before I give Ubuntu this chance again :)

---

### Post by SentientFluid on 2008-01-12
> **twright said:**
> why else has apple put multiple checksums on the database and encrypted the firmware, you don't just buy a Mac becuase it supports the ipod better, but you are much more likly to because of it

Mac's don't support iPods any better or worse than Windows does.  I've been using my iPod(s) in Windows for long time and never had a problem with them. iTunes and a couple of games are the only reason I have Windows running. Once I find a good method of syncing my iPod in Ubuntu, I'll have much less reason to run Windows. :)

Anyway, my ex had a Mac and had more problems with her iPod (exact same model as my first one) on it than I ever had in Windows.

The checksum is to make it more difficult to use the iPod with software other than iTunes, not to try and force you to buy a Mac.  If you're using iTunes you're more likely to by from the iTunes Store than some other online store, after all.

---

### Post by twright on 2008-01-12
anyway, they are trying to make you buy one of their products (which one it is is irrelevant)

apple do some great stuff (webkit, their icons) but their hostility towards linux users is very annoying. if you look at the license section of your ipod you can that it uses free type, an open source project (that is why all the text looks so crisp). And safari's engine is based on khtml, apple should not take so much whilst giving so little back :mad: (it shouldn't take more than a tweaks to get itunes working on linux, they are both BSD based and most linux software has been ported effortlessly to OSX, in fact it would cost a lot less than apple spend on locking developers out)

---

### Post by SentientFluid on 2008-01-12
> **twright said:**
> anyway, they are trying to make you buy one of their products (which one it is is irrelevant)

Which is the goal of every company, and you actually don't have to buy iTunes. It's free.

> **twright said:**
> apple do some great stuff (webkit, their icons) but their hostility towards linux users is very annoying. if you look at the license section of your ipod you can that it uses free type, an open source project (that is why all the text looks so crisp). And safari's engine is based on khtml, apple should not take so much whilst giving so little back :mad: (it shouldn't take more than a tweaks to get itunes working on linux, they are both BSD based and most linux software has been ported effortlessly to OSX, in fact it would cost a lot less than apple spend on locking developers out)

You forgot that Mac OS X is Unix based, as well.  Anywho, I think we've hijacked the thread more than enough.

Is libgpod6 able to run in Feisty?  Because I keep getting dependency errors (the versions installed are less than the version needed) yet when I try to install/update those dependencies, there are no higher versions available. Do they come from a specific repository that I maybe don't have?

---

### Post by twright on 2008-01-12
if you temporally add the debian sid repository (google it) via software sources you should be able to get all the dependencies from there (don't update with sid enabled as it is unstable)

---

### Post by Sukarn on 2008-01-13
> **twright said:**
> if you temporally add the debian sid repository (google it) via software sources you should be able to get all the dependencies from there (don't update with sid enabled as it is unstable)

and as it is a different distribution.

Upgrading with sid repository enabled is asking for trouble big time.

---

### Post by Trampis on 2008-01-13
is there any way other than using windows to get my ipod to mount; all I have is ubuntu. My external HD works fine.

---

### Post by twright on 2008-01-13
borrow a friends PC?

else you could try using virtual box (you will have to install windows in there but it won't interfere with ubuntu)

---

### Post by xGutsAndGloryx on 2008-01-14
ubuntu will detect my ipod nano. it will bring up a icon on the desktop. i bring it up in gtkpod and try to add more songs/albums to it. it won't let me. it will pull the album i have on it already but i can't add to it. i eject the ipod and it won't let me listen to my old songs... i am trying to restore it... any other advice?

---

### Post by Sukarn on 2008-01-14
> **xGutsAndGloryx said:**
> ubuntu will detect my ipod nano. it will bring up a icon on the desktop. i bring it up in gtkpod and try to add more songs/albums to it. it won't let me. it will pull the album i have on it already but i can't add to it. i eject the ipod and it won't let me listen to my old songs... i am trying to restore it... any other advice?

Right click on the iPod's name in **gtkpod**, click **Edit iPod Properties**.

Click on the drop down box next to **Model**.

Select your iPod model. Just because you are following this thread, I assume you have a nano video, so go to **Nano Video (3rd Gen.)** and select the appropriate colour.

Try adding / removing songs now.

---

### Post by xGutsAndGloryx on 2008-01-14
i selected it already... i have limited edition red 8 gb ipod nano..  i selected the 8 gb black video ipod nano.... i selected 6 generation... is that correct?

---

### Post by twright on 2008-01-14
firstly does it it work in rhythmbox, that should detect it automatically?

---

### Post by xGutsAndGloryx on 2008-01-14
no... that was the software i was using... it would pull all mp3's from the ipod.. i tried updating it.. i ejected the ipod.. i checked it the files didn't update and all my orignal files are gone...

---

### Post by twright on 2008-01-14
could you try going through the tutorial again, it sounds like it didn't work (that was what was happening before the fix)

---

### Post by xGutsAndGloryx on 2008-01-14
i tried it and it doesn't recognize that part of the command
/usr/bin/ipod-read-sysinfo-extended

---

### Post by Sukarn on 2008-01-15
> **xGutsAndGloryx said:**
> i selected it already... i have limited edition red 8 gb ipod nano..  i selected the 8 gb black video ipod nano.... i selected 6 generation... is that correct?

No. That is incorrect.

Select **Nano Video (3rd Gen.) -> 8 GB Nano (Red) (xB257)**

---

### Post by Rocket2DMn on 2008-01-15
This did not work for me on my new iPod Classic 80GB.  First that ipod-read-sysinfo-extended command wasnt available.  When I did run amarok, I had the same problem I had before - I could read and play just fine, but the iPod itself no longer sees the music and neither does iTunes in windows (which I need to work).  iTunes gave me the error that it couldn't read the contents and I need to Restore to factory settings (again).  Thanks for trying OP, I guess we'll just have to wait for more officially unoffical support through amarok to not essentially brick the iPods until Restored.

---

### Post by Sukarn on 2008-01-16
EDIT: Post redundant and useless. Contents removed.

---

### Post by davidwrocklage on 2008-01-16
any idea if this should/could work with a 160g classic?

---

### Post by twright on 2008-01-16
this should but please try it rhythmbox first and if any step fails don't try without it (else it will make the ipod stop recognizing any songs without a reset)

---

### Post by Lithium17 on 2008-01-16
Tried this, got to stage 2. I tried to install the debs specified but the Package Installer returned this "dependency not satisfiable: libc6".

Any ideas as to how to fix?

It's kinda important for me since I don't have a Windows OS installed anymore.

Thanks

---

### Post by twright on 2008-01-16
hi

you may need to go into software sources (System->Administration->Software Sources) and tick all of the boxes except Source code

that should make it work :)

---

### Post by Lithium17 on 2008-01-16
I think I see my problem. The debs I was trying to install were the ones for Gutsy, but I'm using Feisty. I guess I have to look for the right ones.

---

### Post by twright on 2008-02-05
i am totally rewriting this howto as the meathod i origanally posted takes to long and doesn't always work

this should work for everyone having problems with the 1st one

original meathod (for referance)
> [SIZE=3]**Step 1:**[/SIZE]
Make sure you can mount your ipod in ubuntu, all you should need to do is plug it in and it should open in nautilus (if you have a laptop you may need to plug it into a USB port at the back not the side). If it doesn't mount, make sure that you first used it on a PC (not a MAC) and in itunes "disk usage" is enabled.
 
[SIZE=3]**Step 2:**[/SIZE]
Go to[ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/](ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/) and dowload + install libgpod2_0.5.3+actually0.6.0-0.1_i386.deb then libgpod-dev_0.5.3+actually0.6.0-0.1_i386.deb

If they won't install then you probably just need to enable the necessary repository to allow you to install the dependencies. To enable them go into software sources (System->Administration->Software Sources) and tick all of the boxes except Source code.
 
[SIZE=3]**Step 3:**[/SIZE]
Open a terminal (applications->accessories->terminal) and type in *df *(and press enter)*. *that should display something like this:     Code:
     tom@tom-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             74321152  68704644   2596292  97% /
varrun                  972212       160    972052   1% /var/run
varlock                 972212         0    972212   0% /var/lock
udev                    972212        84    972128   1% /dev
devshm                  972212       140    972072   1% /dev/shm
lrm                     972212     33652    938560   4% /lib/modules/2.6.22-14-generic/volatile
fusesmb               74321152  68704644   2596292  97% /home/tom/Network
/dev/hda               8339312   8339312         0 100% /media/cdrom0
[COLOR=red]/dev/sdb1              3793036   2876844    916192  76% /media/TOM'S IPOD[/COLOR]
tom@tom-laptop:~$ 
Note the line which refers to ipod (highlighted in red). This shows which device is you ipod and where it is mounted
 
[SIZE=3]**Step 4:**[/SIZE]
Now you just need to type one more command into terminal to get your ipod working

**[COLOR=Red]This stage is essential, if you don't do it and attempt to sync then all of your songs will vanish[/COLOR]**
 
For most ipods you just need to use this:
     Code:
     sudo /usr/bin/ipod-read-sysinfo-extended /dev/sdb1 /media/IPOD 
try typing this in to see if it works (it should prompt you for you password then return you to the prompt)
 
if that doesn't work you will need to customize it eg if rf returned: 
     Code:
      [COLOR=green]/dev/sdb1[/COLOR]              3793036   2876844    916192  76% [COLOR=blue]/media/TOM'S IPOD[/COLOR] 
you would need to use
     Code:
     sudo /usr/bin/ipod-read-sysinfo-extended [COLOR=green]/dev/sdb1[/COLOR] [COLOR=blue]/media/TOM\'S\ IPOD[/COLOR] 
(you need to put \ before any space or apostrophe)



Now Rhythmbox and amarok should be able to sync music to you ipod (i still haven't been able to get gtkpod working properly)

[B][SIZE=3] Known Issues:
[/SIZE][/B][LIST]
[*]This may not work with Amarok
[*]Album artwork is not transfered
[*]Podcasts are not sorted as podcasts
[*]/usr/bin/ipod-read-sysinfo-extended is not always found
[*]if you have firmware 1.1 this will not work[/LIST]***thanks to [http://lilserenity.wordpress.com/200...-ipod-nano-3g/]("http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/") for the tutorial i based this on***

---

### Post by paulkenny on 2008-02-07
Hi,
Thanks a million for the howto it worked fine for me and I can now transfer music to my 3g nano.
However as described in the howto the album art is not transferred. Does anyone know why this is the case? Is it a bug in libgpod3?
  Cheers,
    Paul

---

### Post by twright on 2008-02-07
rhythmbox's support for libgpod3 is still very new, album art should be coming soon

if you use gtkpod that does support album art but you will have to get it yourself manually (off google images)

---

### Post by ShanghaiTeej on 2008-02-13
This worked for me, except when I tried to remove libgpod2, a prompt asked me to remove ubuntu-desktop, so I just skipped this step and removed the Hardy repositories.  Everything works for now!  Thank you very much for taking the time to make that tutorial!

---

### Post by twright on 2008-02-14
it is safe to remove ubuntu-desktop (it is just a meta package)

you only need to remove libgpod2 as a precaution (so that no programs attempt to use it), if you install any programs which will sinc with your ipod from the hardy repos you should be OK

---

### Post by Ni85 on 2008-02-19
Hey
first of all thanks for the how-to: i can finally see my music again. i got a weird problem after the procedure, though.
something somehow changed the layout of all my internet pages, as if the font was different now.
is it a known issue? and is there a way to set it back? it's really annoying to read now..
hope somebody can help
thanks

---

### Post by Neon Lights on 2008-02-19
I love you.

---

### Post by twright on 2008-02-19
weird, i don't think the upgraded packages were anything to do with fonts

you could try adjusting firefox's font settings in preferences>content:
[IMG]http://i191.photobucket.com/albums/z76/tomdwright/screenshot2.png[/IMG]

---

### Post by Ni85 on 2008-02-20
hey
thanks for your help.
i think i'm going totally off topic (even if these things happened immediatly after i followed this howto), so tell me if you think i should just open a new thread.

i reset firefox and it partially works, besides some e-mails that are displayed in Nimbus Mono L, which is the most annoying font ever.
besides this, that i don't know how to fix (and i'd really like to), compiz is still not working (i have tried to reinstall it, but nothing changed and it still gives me a "desktop effects could not be enabled" response when i try to activate it - it was working fine until 2 days ago); while a new problem came up, and i've noticed just now...
i can't use open office's links from the applications menu, while it starts if i run it in terminal.
any idea about this??
i know it sounds totally weird, but i didn't do anything besides following this howto, and after it all these problems came up for the first time...
thanks again

ps also skype has some font problems: contact's names, buttons and chats are displayed in a weird font.

pps can't display youtube videos anymore... since i haven't installed all the updates in the hardy repo, and after i was done with the libraries i erased it from the software sources, should i try to put it back in and update everything and see what happens?

---

### Post by twright on 2008-02-20
the software installed by this tuutorial is mainly alpha (from the hardy repos) so that could cause some problems

try editing openoffices shortcut to what you enter in the terminal to open it

envy should get compiz working

---

### Post by vitaliyn on 2008-02-20
Great solution to a BIG problem I had.  I switched to Ubuntu but my new, shiny ipod classic wont work with amarok.  Thanks to everyone that was involved in this!

---

### Post by Ni85 on 2008-02-21
hey
nothing solved here: also in terminal the only way to launch open office is to type 
```
openoffice
```
and it opens a standard grey page that allows me to open any of OO's applications; but this is what happens with the other "normal" codes:
```
tado@tado-laptop:~$ openoffice -writer
Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'
tado@tado-laptop:~$ ooffice -writer
Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'

```

compiz won't work and i totally don't get what the problem is; in some situations fonts in firefox are still in Nimbus Mono L; skype fonts are different as well and i can't see videos on youtube while they were working perfectly until 3 days ago.

is there a way to uninstall the new libraries and have the old ones back, at least to see if this can solve all these weird problems?
or should i try instead to update all the software in the hardy repo, and see what happens?

or is there any other solution?

thanks

---

### Post by Muscar on 2008-02-28
Thanks!

---

### Post by twright on 2008-02-28
> **Ni85 said:**
> hey
nothing solved here: also in terminal the only way to launch open office is to type 
```
openoffice
```and it opens a standard grey page that allows me to open any of OO's applications; but this is what happens with the other "normal" codes:
```
tado@tado-laptop:~$ openoffice -writer
Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'
tado@tado-laptop:~$ ooffice -writer
Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'

```compiz won't work and i totally don't get what the problem is; in some situations fonts in firefox are still in Nimbus Mono L; skype fonts are different as well and i can't see videos on youtube while they were working perfectly until 3 days ago.

is there a way to uninstall the new libraries and have the old ones back, at least to see if this can solve all these weird problems?
or should i try instead to update all the software in the hardy repo, and see what happens?

or is there any other solution?

thanks
upgrading to hardy's repository would probably leave you with a very broken install

you can purge the programs and libraries use in synaptics the reinstall them, that will give you the gutsy versions

you can also delete all the hidden files in your home folder. that might fix the font issues (but lose program setting)

---

### Post by Ni85 on 2008-03-03
> **twright said:**
> upgrading to hardy's repository would probably leave you with a very broken install

you can purge the programs and libraries use in synaptics the reinstall them, that will give you the gutsy versions

you can also delete all the hidden files in your home folder. that might fix the font issues (but lose program setting)

i tried it again on a new and clean system; it worked again for my ipod, but still gives me problems. not as many as the first time though: now i have "only" the openoffice issue. same problem as before.
how do i downgrade again?

is 
```
aptitude install libgpod2
aptitude remove libgpod3 libgpod-common
```

enough?

thanks again for your help!

---

### Post by twright on 2008-03-04
i would try sudo aptitude purge ligpod3 libgpod-common then sudo aptitude install libgpod2

it might be easier to install openoffice from openoffice.org instead of the repos

are you running 64bit ubuntu?

there is a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/187407](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/187407)

---

### Post by Ni85 on 2008-03-04
> **twright said:**
> i would try sudo aptitude purge ligpod3 libgpod-common then sudo aptitude install libgpod2

it might be easier to install openoffice from openoffice.org instead of the repos

are you running 64bit ubuntu?

there is a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/187407](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/187407)

great! i upgraded ooffice with hardy's repos; purged libgpod3 and ligpod-common, reinstalled libgpod2; followed the howto again and now everything works fine! both my gutsy and my ipod!
i also had to reinstall firefox from synaptic cause after this second try i had a problem with the ssl protocol. but now everything's fine!
thanks a lot for help and patience!

---

### Post by mahershi on 2008-03-05
I am running Ubuntu 8.04 (pre-release). I installed libgpod3 and common. I also installed gtkpod, but, it doesn't pop up as the default program when I connect my ipod-classic. (Anyone know how to make gtkpod default program for the ipod?)

Other than that (gtkpod not being the default ipod manager) things worked (almost): WHen I connected the ipod, rhythmbox (rb) popped up. I could see my ipod in rb. I could browse to the music on my ipod, but, I couldn't play! When I tried to "eject" the ipod rhythmbox crashed. (I have reported a bug about that.)

---

### Post by twright on 2008-03-05
you don't need to do this for hardy as it is supported out of the box
 
you had set the default from preferences>removable disks and media (or something like that)

---

### Post by buried on 2008-03-10
Thanks a lot!

---

### Post by luisjorge on 2008-03-12
Hi everyone! Thanks twright! This is just what I was looking for! Got my 80G ipod today, and spent hours trying to get it to work under any program in linux, until I found this guide:) I'm using amarok to manage my ipod now.
The only problem is I can't get the album art to be transfered to the iPod. Does anyone know how to do this? I already tried the "update album art" option, but nothing happens.
Any ideas?

Thanks very much in advance!

Luis Jorge.

---

### Post by twright on 2008-03-12
you can use gtkpod for album art but you need to get it manually from google image or drag and drop to your desktop from rhythmbox and select (don't delete them until you have synced).

the reason it doesn't work in rhythmbox is simply because they haven't implemented it yet with the new libgpod, gtkpod got there first as it's developed with libgpod

---

### Post by luisjorge on 2008-03-15
Hi! I'm trying to use gtkpod to manage the music in my ipod classic, and see if I can get the artwork transfered properly, but the build from the how-to doesn't support aac files. For that I need to install gtkpod-aac, which removes gtkpod.
Is this ok? Or will my ipod stop working with gtkpod if I do this?

Thanks!

Luis Jorge.

---

### Post by luisjorge on 2008-03-18
Hi everyone! I just tried to transfer the album art with Amarok, and it works just fine! All you have to do is select the "update album artwork" option, and when you select "disconnect", wait until the "synchronizing" animation on the iPod stops. Amarok doesn't really give any graphical feedback that it's actually doing anything, but the iPod keeps receiving things, and the processor stays at 100%. When it's finished, everything stops and everything is set.

Now I have another problem. I installed gtkpod through this guide, (I installed the gtkpod-aac version, actually), and now I can't remove it. I just selected "completely remove" from synaptic, and gtkpod doesn't appear on my menus anymore, but it's still in synaptic, permanently "marked for remove", and whenever I click "apply", I get this:

```
E: gtkpod-aac: subprocess post-removal script returned error exit status 1
```

So now every time I install, remove or update anything, I get this error from gtkpod removal and an additional error when the system tries to configure amarok (which I also installed according to this guide).

Any ideas on how to clean this up?

Thanks in advance!

Luis Jorge.

---

### Post by twright on 2008-03-18
great,
i might even switch to amarok now :) (gtkpod is very useful but the interface needs some work and album art should be downloaded automatically)

you can try using sudo aptitude  remove --force gtkpod-acc

---

### Post by luisjorge on 2008-03-18
Hi! Thanks for the tip!

> you can try using sudo aptitude remove --force gtkpod-acc

However, it didn't completely work, I think. I got this:

```
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the gtkpod-aac package. This might mean you need to manually fix this package.
```

How do I do that, or what can I do?

Thanks!

---

### Post by twright on 2008-03-22
could you post the full output of sudo apt-get purge gtkpod-aac

it looks like a library somewhere is not linked correctly, you could post a bug against the hardy version of gtkpod-aac

---

### Post by twright on 2008-03-23
just checked and gtkpod is working fine for photo :)

rhythmbox is sorting podcasts properly at last > **Sukarn said:**
> I would not suggest using GPixPod or gtkpod with your photos just yet. Neither of them seems to work well right now (latest version) with iPod Classic.
After using GPixPod, the iPod doesn't display thumbnails in albums but displays the photos in the right panel and in full screen.
With gtkpod its the other way round. It doesn't display the photos in full screen or in the right panel, but only displays thumbnails.

Right now I visit a friend's place to sync my photos. I have it set up such that I made a Data directory on my iPod and a Photos directory inside the data directory. I put all my photo albums inside this Photos directory and then I have it set up on my friend's comp so that it automatically synchronizes my iPod with the Data\Photos directory present on the very same iPod.
Works like a charm.

---

### Post by bhavi on 2008-03-24
> **twright said:**
> Apple have recently released a new look for their ipods, but with the new interface comes more firmware encryption to stop 3rd party media players (including Amarok, Rhythmbox and gtkpod) syncing music to the ipods.

Since there is no itunes for linux it was up to the guys at[ http://ipodminusitunes.blogspot.com]("http://ipodminusitunes.blogspot.com/") to crack it.

  This should work for any new nanos and ipod classics. Please be aware that this is rather experimental so please make sure that you have all of the music on you ipod backed up before attempting it. The programs instanlled by this tutorial are from the hardy repository so don't be supprised if they break stuff. 

If this causes all music to disappear off your ipod you don't need to access a windows machine to fix it, when you get it working you can sync new music on and it will appear.

This will only work with applications which use libgpod (rhythmbox, amarok and gtkpod). Finally as of rhythmbox version 0.11.5 podcasts are sorted as podcasts although only amarok and gtkpod seem to be able to transfer album art.

here's how to get it working (type this into terminal one line at a time, use the same terminal session for all):
 
```
sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.tmp
echo deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse >> /etc/apt/sources.list
apt-get update
aptitude install libgpod3 libgpod-common
```if you use rhythmbox:
```
aptitude install rhythmbox
```if you use amarok:
```
aptitude install amarok
```if you use gtkpod:
```
aptitude install gtkpod

```then:```
aptitude remove libgpod2
```this may prompt you to remove the ubuntu-desktop package, don't worry - it's only a meta-package

then check if it works. if it does run
```
rm /etc/apt/sources.list
mv /etc/apt/sources.list.tmp /etc/apt/sources.list
apt-get update
```Banshee not supported (it uses it's own library rather than libgpod)

***thanks to [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/) for the tutorial i origanally based this on***

Works great I was banging my head at this.. Thanks.....

---

### Post by Sukarn on 2008-03-26
> **twright said:**
> just checked and gtkpod is working fine for photo :)


Might have been fixed in a more recent release then.

I'll check whether my photos are working fine or not in a while. Having my exams at the moment.

---

### Post by darth.k on 2008-03-26
I used the first guide and it worked, I can now transfer music to my ipod.  However amarok will no longer auto detect my ipod.  I have to manually add a new device each time giving a new name every time because if I name it for example ipod and then reconnect naming it ipod again its says cannot add devices with duplicate names.

very confused, any tips?

---

### Post by DragonJoker on 2008-03-30
hi!!
i'm italian so i'm not sure my english is very well, but i'll try to explain:
i used amarok 1.47 and all worked great (except when syncronyzing LOADS of music). then i saw amarok 1.48 was on the net and I upgraded...
now i can't set the right ipod model (classic 80gb) cause it ends at 6xth gen (80 gb video or smth)
so i cannot view music on my f***** ipod.
i think that's because of the setting of the ipod model because i re-installed libgpod 0.6.0 and have read ipodsysinfoextended...
i don't know how to do
please help...             thanks a lot      DR J

---

### Post by Sukarn on 2008-03-31
> **DragonJoker said:**
> hi!!
i'm italian so i'm not sure my english is very well, but i'll try to explain:
i used amarok 1.47 and all worked great (except when syncronyzing LOADS of music). then i saw amarok 1.48 was on the net and I upgraded...
now i can't set the right ipod model (classic 80gb) cause it ends at 6xth gen (80 gb video or smth)
so i cannot view music on my f***** ipod.
i think that's because of the setting of the ipod model because i re-installed libgpod 0.6.0 and have read ipodsysinfoextended...
i don't know how to do
please help...             thanks a lot      DR J

I cannot help with amarok, sorry, I do not use that.

Try installing gtkpod from the repository, and set up your ipod in gtkpod properly so that the model and everything is set correctly, then try removing or adding one file in your iPod with gtkpod, and save the changes.

---

### Post by twright on 2008-03-31
can you try redoing the tutorial after running "sudo aptitude purge amarok libgpod3 libgpod-common"
 
that should totally reinstall the latest version> **DragonJoker said:**
> hi!!
i'm italian so i'm not sure my english is very well, but i'll try to explain:
i used amarok 1.47 and all worked great (except when syncronyzing LOADS of music). then i saw amarok 1.48 was on the net and I upgraded...
now i can't set the right ipod model (classic 80gb) cause it ends at 6xth gen (80 gb video or smth)
so i cannot view music on my f***** ipod.
i think that's because of the setting of the ipod model because i re-installed libgpod 0.6.0 and have read ipodsysinfoextended...
i don't know how to do
please help... thanks a lot DR J

---

### Post by polytropos on 2008-06-13
This worked for me--it got my 8Gb nano working perfectly.  Many thanks.

---

### Post by Sukarn on 2008-06-14
If you're on hardy (Ubuntu 8.04) then you do not need this howto.

---

### Post by twright on 2008-06-14
> **Sukarn said:**
> If you're on hardy (Ubuntu 8.04) then you do not need this howto.
good point, i have added a note to the original post

---

### Post by lunanueva on 2008-08-19
so i followed the instructions that twright gave at the beginning of the thread, and all i got gtkpod working for my 3rg gen nano (except the artwork), but everything loaded properly and with no problem.  

but now, after listening to two tracks, the ipod screen is completely frozen and i can't even shut it off!!! 

i don't know what to do besides let the battery run out, then try something different later.  does anyone know what happened?  i hope i didn't kill my ipod.  thanks in advance for any responses.

---

### Post by punong_bisyonaryo on 2008-10-04
Hey everyone!

I just bought an Ipod Nano 3rd generation and plugged into Hardy. I'm not planning to download iTunes, so my goal is to avoid it like the plague. The tutorial on the first page does not work on a brand new Nano because it doesn't have some files yet, like the iTunesDB, and the SysInfo file is blank. However, gtkpod is able to create the necessary files and directories and after this I can now copy music to my iPod using either gtkpod or Rhythmbox.

But there is a problem: if I put in more than 1 song, the iPod freezes after a few seconds after ejecting. It's my first iPod, it's 4AM, and I am at wit's end.

---

### Post by mwalimu54 on 2008-11-27
Thanks, this worked well for me on Gutsy with my Nano 8GB.  I had to put new music on it before I could see any of the old though.

---

