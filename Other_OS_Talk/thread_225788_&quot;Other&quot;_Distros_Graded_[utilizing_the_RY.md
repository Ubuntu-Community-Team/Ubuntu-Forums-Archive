---
title: "&quot;Other&quot; Distros Graded [utilizing the RYDES standards]"
date: 2006-07-30
forum: Other OS Talk
---

### Post by richbarna on 2006-07-30
This thread uses R.Y.D.E.S (Rich Yozef Distro Evaluation System) to grade distros. The guide can be copied and pasted, and changed to suit your own grades of 1-5.

* Could you please **title** your post **"Distro Test - Distro"** then it will be easy to do a forum search if the list is popular and gets a bit long, Thanks.* 
(This can be done after your review by clicking edit and changing the title)

Instead of having a load of chit-chat posts could you please PM richbarna or yozef with any suggestions, Thanks Again.

[See my "howto" on adding other installed distros to the GRUB menu.lst]("http://www.ubuntuforums.org/showthread.php?p=1319395#post1319395")

>  
[COLOR=Blue]|It-0|        [/COLOR]Install
[COLOR=Blue] |Lt-0|[/COLOR] Live Test 
[COLOR=Blue] |H-0|     [/COLOR]Hardware support 
[COLOR=Blue] |C-0|[/COLOR]     Codecs 
[COLOR=Blue] |U-0|[/COLOR]     USB 
[COLOR=Blue] |G-0|[/COLOR]    Graphics 
[COLOR=Blue] |S-0|     [/COLOR]Speed 
[COLOR=Blue] |F-0| [/COLOR]Forum Support 

[COLOR=Blue] 0.[/COLOR] Didn't Work
[COLOR=Blue] 1.[/COLOR] Unsatisfactory
[COLOR=Blue] 2.[/COLOR] Satisfactory
[COLOR=Blue] 3.[/COLOR] Good
[COLOR=Blue] 4.[/COLOR] Very Good
[COLOR=Blue] 5.[/COLOR] Excellent 

PS: Don't forget the [Distro URL]("http://www.youhadtoclickit.com")

---

### Post by richbarna on 2006-07-30
[COLOR=Blue]|It-n/a|[/COLOR]        Install Test 0-5
[COLOR=Blue] |Lt-3|[/COLOR] Live Test "
[COLOR=Blue] |H-5|[/COLOR]     Hardware support "
[COLOR=Blue] |C-0|[/COLOR]     Codecs "
[COLOR=Blue] |U-5|[/COLOR]     USB "
[COLOR=Blue] |G-5|    [/COLOR]Graphics "
[COLOR=Blue] |S-3|[/COLOR]     Speed "
[COLOR=Blue] |F-?|[/COLOR] Forum Support "

Tested on a box with 256Mb RAM, Nvidia Gforce 5200, 1.7Ghz proc. ZyXel router.

I found the live cd slow, it took 5 minutes to get to the desktop and general usage was slow as well. (although live cd's are normally slower than in installed distro). 

All my hardware was supported, so no problems there.

Standard KDE desktop, I did notice that Google-Earth is preinstalled and works well. There is also GsetCpmpiz although I didn't play around with compiz.

I tried the install and IMHO is scary. I am used to being able to choose my /root partition then /home folder + Swap, I didn't get this. I just got a Gparted style view of my partitions but no "install to hdc?" or "select your swap partition", I could get the properties for a partition and put / as mount point, but that was it. I also know nothing about portage, so I decided for the sake of my harddrive to leave it alone and maybe experiment later on another PC. 
[See Setup and install Guide]("http://www.lxnaydesign.net/forum/viewtopic.php?t=800")

Ubuntu install it isn't !!

[http://www.lxnaydesign.net/](http://www.lxnaydesign.net/)

---

### Post by Lord Illidan on 2006-07-30
|It-4|        Install Test 

Excellent interface used for installation. Easy to use. The only drawbacks are the partitioner section, which can be misleading to new users, and the selection of packages, which often gave me dependency errors.

|Lt-1| Live Test 

Very slow, didn't work for me. Could be I need more RAM. SUSE is a big distro, after all.

|H-5|     Hardware support

Every piece of hardware was detected, no problems.

|C-2|     Codecs

Mp3 codecs were provided in the form of helix, yet Suse makes it difficult to install new codecs, since the multimedia players are crippled. Ubuntu outperforms Suse in this regard.

|U-5|     USB

Works.

|G-4|    Graphics

Nvidia drivers not included in Yast, had to download the official from Nvidia's site. Still, they worked without problems, and the distro correctly identified my monitor and resolution. Also, nv worked.

|S-4|     Speed

Could do with some work. But not bad..

|F-3| Forum Support

Not as good as this forum. Far less users, and more RTFMing.

0. Didn't Work
1. Unsatisfactory
2. Satisfactory
3. Good
4. Very Good
5. Excellent

---

### Post by xXx 0wn3d xXx on 2006-07-30
|It-4| Install Test 0-5

The Archlinux install cd has no gui-based interface. It's all text. Even though it has no pretty colors, I found it easy to use and install. 

|Lt-N/A| Live Test

There is a new live cd project called Larch (Live Arch) but I have not had the chance to test/use it.

|H-5| Hardware support 

All of my hardware was detected except my Broadcom wifi card which will never be detected by any distro but it's hardware detection is very good.

|C-2| Codecs 

Codecs are not included by default but can be easily be installed.

|U-5| USB

ALl of my USB devices were detected. Including my ipod, psp, and a few others.

|G-4| Graphics 

Since I have an ATi graphics card, it didn't work by default. I was using the vesa drivers but the ati drivers were easily installed. 

|S-5| Speed

Arch is amazingly fast. In terms of speed, it is faster then my Gentoo install without all the compiling times ! Boot time for me is under 25-30 seconds. 

|F-4| Forum Support

The forums can be found at bbs.archlinux.org and they are very helpful. While they do not have as many users or posts as the Ubuntu forums, the people on the forum are very helpful.

0. Didn't Work
1. Unsatisfactory
2. Satisfactory
3. Good
4. Very Good
5. Excellent

My overall rating is 4.7/5 Archlinux is fast, stable, and easy-to-use. It is now my prefered linux distribution and the only on my hard-disk. Arch has a great future and I think that it will become very popular.

---

### Post by richbarna on 2006-07-30
[COLOR=Blue]|It-5|[/COLOR]        Install Test 0-5

This has to be the easist, risk free install of any linux distro. To install you "dock" a folder called "dyne". You do this by clicking on the Hard Drive icon, which gives you root access to ALL partitions.

Then you click on the CD drive, and copy and paste the dyne folder to a partition of your choice. It's 600 Mb so it takes a few minutes, but that's all.

To save all your configuration files, Dyne:Bolic uses "nesting", this is basically the same as having a /Home folder. Just like the install, you click on "nest" and it asks which partition you want to use for the nested the nested folder. That's it, all installed. If you want to boot from GRUB instead of the CD, just add Dyne to the Menu.lst.

[COLOR=Blue]  |Lt-5|[/COLOR] Live Test 

Just using the "Live" version is awesome, it's fast and everything works "out of the box".

[COLOR=Blue]  |H-4|[/COLOR]     Hardware support 

I gave it a 4 because I have an nVidia card and I haven't yet found out if it's possible to get the newest nVidia drivers. My screen is offset by about 2 mm to the left. Although that is probably solveable.

[COLOR=Blue]  |C-5|[/COLOR]     Codecs 

Dyne:Bolic plays everything !! I tried wma, mp3, avi, mpg.

[COLOR=Blue]  |U-3|[/COLOR]     USB 

Multi-card reader, 3 pen drives (all worked)
Blue Tooth dongle (not recognised)
Web cam (will try later)

[COLOR=Blue]  |G-4|    [/COLOR]Graphics

4 because of the previous nVidia driver problem, otherwise crisp and bright, excellent video playback.

[COLOR=Blue]  |S-5|[/COLOR]     Speed 

No KDE or Gnome = Rapid (using xfce & fluxbox)

[COLOR=Blue]  |F-?|[/COLOR] Forum Support 

No forum that I know of, although there is a #dyne channel on IRC and a mailing list.

I am extremely impressed with this version of Dyne, having used the previous version.

It comes with Amarok 1.4 and K3B as standard. Both work "out of the box". It has some very good music editing software, and is also able to broadcast radio and podcasts.

This distro now has a permanent place on one of my partitions.

[http://www.dynebolic.org/index.php?show=available](http://www.dynebolic.org/index.php?show=available)

---

### Post by richbarna on 2006-07-30
[COLOR=Blue]|It-n/a|[/COLOR] Install 

I wouldn't install this distro.

[COLOR=Blue] |Lt-3|[/COLOR] Live Test 

As a live cd, it's ok if you need something quick to get on the internet.

[COLOR=Blue] |H-2|[/COLOR] Hardware support 

It found everything, but when I was testing cd's and dvd's I had to manually unmount and eject the cd's from a right click on the disk icon.
All other hardware worked as it should. Apart from when a cd refused to unmount and the system froze.


[COLOR=Blue] |C-4|[/COLOR] Codecs

Plays mp3 and avi video, I couldn't test any other formats as some were on cd's that wouldn't read and others were on another partition that I wasn't given access to.

[COLOR=Blue] |U-1|[/COLOR] USB

Nothing worked. I did an "lsusb" from the konsole and it showed that they existed but nothing automounted.I tried my blue tooth dongle (This works in Kubuntu by the way) my pen drives and a multi-card reader.

[COLOR=Blue] |G-5| [/COLOR]Graphics

Nvidia detected ok, crisp clean and bright graphics, the avi video played smoothly.

[COLOR=Blue] |S-4|[/COLOR] Speed

It booted and loaded quickly, but is pretty normal as live cd's go.

[COLOR=Blue] |F-?|[/COLOR] Forum Support

I didn't check.

So, this is a live cd with KDE. You can also choose fluxbox. That's about it, and I'm not very impressed, I can choose 100's of KDE distros that recognise a router and basic hardware. This is nothing special in my opinion.

No Firefox, No Amarok, and Kplayer is just ugly. I could have taken a screenshot, but it's just the same ol' kde, not worth the effort.

[http://www.slax.org/download.php](http://www.slax.org/download.php)

---

### Post by RAV TUX on 2006-07-30
[COLOR=Blue]|It-N/A|        [/COLOR]Install Test 

N/A

[COLOR=Blue] |Lt-5|[/COLOR] Live Test 

Fast boot to live CD, easy to navigate, screen recognition/English Language automatic

[COLOR=Blue] |H-5|     [/COLOR]Hardware support

All hardware detected: Creative Labs Sound Blaster Audigy Sound Card
Razer Diamondback mouse, Radeon X 856XT Platinum PCIE, etc

[COLOR=Blue] |C-4|     [/COLOR]Codecs

some codecs need to be loaded for DVD movies, CD plays in Kaffaine and recognizes Album , artist and songs. Mp3's load and play flawlessly in XMMS within seconds. tested from my blog site here:
[http://jozefmazeltov.multiply.com/music](http://jozefmazeltov.multiply.com/music)

[COLOR=Blue] |U-5|     [/COLOR]USB

Works.

[COLOR=Blue] |G-5|[/COLOR]    Graphics

Radeon X 856 XT Platinum works flawlessly

[COLOR=Blue] |S-5|     [/COLOR]Speed

Fast but remember I have an Intel EM64T 64bit Dual Core processor
[COLOR=Blue]
|F-4|[/COLOR] Forum Support

English forums are helpfull and adequate

> 
                              |It-0|        Install Test 0-5
|Lt-0| Live Test "
|H-0|     Hardware support "
|C-0|     Codecs "
|U-0|     USB "
|G-0|    Graphics "
|S-0|     Speed "
|F-0| Forum Support "

0. Didn't Work
1. Unsatisfactory
2. Satisfactory
3. Good
4. Very Good
5. Excellent                                                                                  
                                             

Question: Would I consider Knoppix 5.0 as a Distro I would like to install and use? Yes.

---

### Post by rattlerviper on 2006-07-31
|It-3|   Install Test
Installation was easy, BUT if you want to repartition the drive so you don't lose your other operating systen better figure out another way, as it is not included in the installer.

 |Lt-na|  Live test
This is not a live cd

 |H-5| Hardware support
Excellent, recognizedeverything including wireless card, sound card, and even set up my monitor correcrtly(a 21 inch crt).  This is the first install that EVERYTHING worked "out of the box".

|C-2| Codecs 
Load them up and use them, codecs for DVD playback are not included.

 |U-5| USB
Works well on my computer, used my USB mouse and have tested my thumbdrive and digital camera. Everything just worked.

|G-5| Graphics
Graphics worked great!  Even set up the resolution perfecrlty for my 21 inch crt.


 |S-4| Speed
Unuasually SLOW install, but worked VERY fast after the install.  This is on a 1.1 ghz celeron with 512 mb pc133.  I am very impressed at how fast everything works!

|F-4| Forum Support
Great forum support!  Not quite the level of support as the forums here, but darn close!

URL is [http://www.pcbsd.org/](http://www.pcbsd.org/)

Is this worthy of a permanant place on my harddrive?  I think it very well may be, and I am considering leaving it as a permanant addition!  I REALLY like PCBSD!

I am editing this to add info that I found in the forums over at pcbsd.  I'm not sure how I had wifi support "out of the box"!  After reading the forums over there I should have had to set it up myself using ndiswrapper.   If I understand correctly what is being said over there they have no wifi support out of the box!  YMMV, but I DID have working wifi without doing anything!

---

### Post by rattlerviper on 2006-07-31
|It-na| Install Test
I will NOT install this on my hard drive under ANY circumstance!  If this was the last Linux distro left I would switch back to Windows!

|Lt-1| Live test
Does look good, does not function well on MY computer.

|H-1| Hardware support
Was unable to use my USB mouse, had to dig through the garage for my old mouse that came with my computer.  It was unable to set a proper resolution for my monitor.  A 21 in crt, and if I tried to set resolution above 400x600 screen would blank out and I was running blind!!!  600x400???  Absurd!

|C-2| Codecs
Well it LOOKS as if it can play a cd.

|U-0| USB
USB support is nonexistant.  It did not recognize my mouse, thumb drive, digital camera, or web cam!  In fact I would bet that nothing USB will work!

|G-1| Graphics
600x400 resolution is simply not acceptable.  

|S-5| Speed
The only area were Puppy Linux excells, it is blazingly fast!  I would bet it would be even faster installed to harddrive.  Then again for a less than 70mb operating system it should be fast.

|F-4| Forum Support
There does seem to be good community support for this distro.  It looks like everything that is wrong on my system could be fixed with ALOT of work and all the info available at the forums.  I just don't feel like I should have to fix EVERYTHING!

[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

---

### Post by richbarna on 2006-07-31
[COLOR=Blue]|It-5|        [/COLOR]Install

Install was very easy, just tell it which partition,(if you are using Ubuntu GRUB, just install puppy GRUB on it's own partition, then edit your Ubuntu menu.lst to boot Puppy)

[COLOR=Blue] |Lt-5|[/COLOR] Live Test 

Very quick startup. And as a live cd it runs fast.

[COLOR=Blue] |H-4|     [/COLOR]Hardware support

I gave it a 4 because I had to  adjust my monitor  (2  mm offset thing) however it does have Xvidtune which allows you to tweak the screen position.

[COLOR=Blue] |C-3|[/COLOR]     Codecs 

Played mp3, avi. I did find extra codecs for Quicktime and Real in PupGet apt manager, it also has the lbdvdread package. Does not play wma, wmv.

[COLOR=Blue] |U-0|[/COLOR]     USB 

Nothing, I couldn't get it to recognise anything, lsusb does not work from the terminal.

[COLOR=Blue] |G-4|[/COLOR]    Graphics 

Graphics got a four only because of the offset monitor problem (easily solved though). Everything is fast, video played flawlessly even from the live cd.

[COLOR=Blue] |S-5|     [/COLOR]Speed 

Rapid, on a 1.7 Ghz AMD proc, 256 Mb RAM, but as RattleViper said, it's only 70 Mb, it should be quick.

[COLOR=Blue] |F-?| [/COLOR]Forum Support

As usual, I didn't check forum support (Lazy), I will check out the forums later and edit my posts.

All in all, I liked it, the thing that got me is the Seamonkey Browser. I need to find what fonts it is using as websites look gorgeous (better than Firefox default). I couldn't get any plugins to work for lack of an install script.

The jwm (Joes Window Manager) is clean, basic and fast, I like it.
This Distro is a newbie paradise, it has "wizards" for everything. When I first logged on, no internet. I just hit the "Connect" wizard and chose DHCP and it connected.

The reason I am going to keep Puppy on my hdd is that I have seen it with the enlightenment wm and it looks awesome. I feel that with all the software that is available, including "Pup-Get" (I love that :)) and DotPup packages, it has a lot of potential.

[http://www.puppylinux.org/user/downloads.php](http://www.puppylinux.org/user/downloads.php)

---

### Post by rattlerviper on 2006-07-31
ARRRRRRRRRRRRGGGGGGGGHHHHHHHHHH!

|It-0| Install Test
What can I say, it eat my grub!  When I restarted my pc after install I was greated with "No Operating System found. Aborting." I was able to throw my dapper cd in boot up live and see that all my partitions,(ubuntu, PCBSD, and yopper plus my swap)were all there, but I couldn't get to them.  I know I am  supposed to be able to fix the grub from the live cd, but I really don't know hoh, so I just reinstalled dapper!  I won't be trying this one again :confused: 

|Lt-na| Live test
Not a live cd


|H-na| Hardware support
Have no way of knowing, see above.

|C-na| Codecs
Have no way of knowing, see above.

|U-na| USB
Have no way of knowing, see above.

|G-na| Graphics


|S-na| Speed
Have no way of knowing, see above.

|F-3| Forum Support
Looked around the forums and found them to be adequate.

[http://www.yoper.com](http://www.yoper.com)
If you choose to install this one best of luck to you, but for me I shall stay away to avoid the possible trauma of losing my ability to use my computer again!

---

### Post by basketcase on 2006-07-31
[COLOR=Blue]|It-n/a|        [/COLOR]Install
[COLOR=Blue] |Lt-3|[/COLOR] Live Test 
[COLOR=Blue] |H-2|     [/COLOR]Hardware support 
[COLOR=Blue] |C-0|[/COLOR]     Codecs 
[COLOR=Blue] |U-2|[/COLOR]     USB 
[COLOR=Blue] |G-2|[/COLOR]    Graphics 
[COLOR=Blue] |S-2|     [/COLOR]Speed 
[COLOR=Blue] |F-n/a| [/COLOR]Forum Support 

[COLOR=Blue][/COLOR]For something more indepth see [http://basketcase.wordpress.com/2006/07/31/gobolinux-012/](http://basketcase.wordpress.com/2006/07/31/gobolinux-012/)

---

### Post by Lord Illidan on 2006-08-01
[COLOR=Blue]|It-3|        [/COLOR]Install

Installation was purely text based, no gui in sight. Also, one has to configure his own partitions manually with cfdisk, not very reassuring for some newbies. That aside, installation was fast, v. fast. It doesn't install lots of crap on your system, too.. In fact, Open Office doesn't even get installed, you get Abiword and Gnumeric instead, not bad choices. They keep the overall size down.

[COLOR=Blue] |Lt-NA|[/COLOR] Live Test 

[COLOR=Blue] |H-5|     [/COLOR]Hardware support 

Everything was detected, from my Genius Soundmaker Live 4.1 soundcard, to my Nvidida graphics card. My mouse also worked (it had a tendency not to work with previous versions). Installing Nvidia drivers (it defaulted to using 2D nv drivers) was a piece of cake. Install kernel sources with netpkg, then download the nvidia drivers from nvidia.com

[COLOR=Blue] |C-4|[/COLOR]     Codecs 

MP3 works. WMV works. Ogg works. Avi works. Wma works. Mpg works. Cool, everything works. Just had to install libdvdcss from netpkg. Note that it plays everything with gxine, there is no real mp3 player as we know it included.
[COLOR=Blue]
|U-5|[/COLOR]     USB 

Everything works.
[COLOR=Blue]
|G-5|[/COLOR]    Graphics 

Video card detected as nvidia, and nv drivers used. It was then a piece of cake to install official nvidia drivers.

[COLOR=Blue] |S-5     [/COLOR]Speed

Beats Ubuntu and Xubuntu hands down... Blazing fast. It uses XFCE as a window manager, so that could be the main cause, but also, it has very little baggage. Thunar pops up instantly.

[COLOR=Blue]|F-4| [/COLOR]Forum Support 

Haven't checked it out fully yet, but they seem a helpful, friendly bunch.

---

### Post by rattlerviper on 2006-08-01
|It-3| Install
Nice easy to follow graphical installer...but it takes 5 cds 6 if you want the "extra"

|Lt-NA| Live Test 
I downloaded the cds not the live dvd

|H-5| Hardware support 
Everything was detected and worked except my printer.  They have finally got wifi support down in 10.1

|C-4| Codecs
Everything you need to play music is here, but you have to install codecs for DVD playback.

|U-5| USB
Excellent, mouse, thumb drive, digital camera all work.

|G-5| Graphics 
I have NEVER had a major problem with graphics with Suse, and this one is no different.

|S-2|
Ok, Suse is a MAJOR distro, so I didn't expect blazing speeds but it was very slow.  I would go as far as saying this is bloated.  Yast, which is the package manager for Suse is amazingly slow.  It made me contemplate watching a movie while it did what it does!  That bieng said maybe if you have a faster computer with more memory it will hadle it better.  I have a coppermine celeron at 1.1ghz with 512 mb sdram.

|F-3| Forum Support 
I've dealt with them before over there, and while there are some friendly helpful people, I would say that the general atmosphere is not inviting.  I would go so far as to say there is a elitist attitude running around over there.

[http://en.opensuse.org/Welcome_to_openSUSE.org](http://en.opensuse.org/Welcome_to_openSUSE.org)
Will I keep Suse around on my hard drive? No, for a long time they were my distro of choice, and I have fond memories as they were my first distro back at 6.0.  I just can't justify this distro to myself any more when others do it faster, prettier, easier. :-(  I really wanter to like this distro.

---

### Post by rattlerviper on 2006-08-01
|It-2| Install
Well it did install, but it wasn't easy or quick.  Everything was done from command line Beginning in DOS:( .  It required 6 floppies for the software I wanted installed. You could have anywhere from 1-13 floppies depending on what you want.  1 nets you a command line. 2 floppies and you can have a GUI.  A total of 4 floppies and you can have Gui and a really old version of netscape. You can see how it works, choose your software and make the floppies;) 

|Lt-NA| Live Test 

|H-2| Hardware support 
Had to use a PS2 mouse a s the the one on the keyboard did not work.  I would also warn that the laptop seemed to get REALLY hot really quick.  I wasn't really worried about killing this laptop, but you might be worried about killing yours.  I must add the "laptop" quickly became a "desktop" as it got hot enough that I was worried about cooking myself more than the CPU #-o 


|U-0| USB
USB support? None!

|G-3| Graphics 
Functional on the old laptop.  I would guarentee problems if you tried to install on a system with Nvidia or ATI.

|S-3| Speed
Fast! Wow is it fast! If you think about it it is already done and waiting on you!  Then again 1.44Mb x 6 floppies= <9Mb of software installed! I think this might be running ontop of DOS? It states on the website that you must have windows or Dos installed to perform the install.  It uses Linux kernal 2.0.x according to the documentation on the website.

|F-0| Forum Support 
Good luck, as your on your own with this one.  No forum support.  Nill amount of info could be found through Google.

[http://mulinux.dotsrc.org/](http://mulinux.dotsrc.org/)
Overall I would recomend everyone stay away from this distro unless you have a computer with a 286 class proccesor, as this may be one of the few distros that will run on it. Other than thaqt I would keep looking.

As a after thought I saw that I neglected to put a rating on codecs...it would be 0 as there are NONE.

---

### Post by rattlerviper on 2006-08-01
|It-NA| Install
The main point of this distro is running it on a live cd, you can even add software that you would like to have onto your cd.  No way would I install it when the whole idea behind this distro is Live cd or using a thumb drive.

|Lt-5| Live Test 
Fast and efficient pretty well sum it up here.  If you want software to run while using the live cd choose carefully or make a muli session cd.  A bit of familiarity is to be noticed here.  For example Ubuntu has apt-get.  Slax has Slapt-get, why the name change I'm not sure, but if you are familiar with apt commands add a sl to the beggining and it will work. 


|H-3| Hardware support 
Did not find my DVD drive.  Everything else was found and functional.


|C-na| Codecs
I was in a hurry to be done with Slax Kill Bill!

|U-3| USB
Mouse and thumb drive work, my camera does not.  Not a big deal if I was installing Slax as I could fix it, but on something to be used as a live cd where ever I go:mad:


|G-5| Graphics 
Wow it just worked!  It seems like more and more distros are just working!  This is a really good sign for Linux!

|S-5| Speed
Fast.


|F-2| Forum Support
Congrulations, it has one.  On the other hand the forums over there are the road less traveled!  Not many posts or active users when compared to most other distros.  

[http://www.slax.org/](http://www.slax.org/)

---

### Post by drosophyllum on 2006-08-01
1 gentoo- a: for graphical b: old fashion way :-D 

|It-3| Install:a: its an improvement, but it failed three times for me before I finally got it to work. Its also still to hard for a noob.

|It-1| Install:b: I have to say that it wasn't as hard as I imagined but it wasn't a walk in the park, considering an error could waist two days of compileing... but it worked.... I missed my computer the two days through. :-D 


|Lt-4| Live Test a:
not bad...

|H-1| Hardware support A: It simply did not want to recognize my sound card.....](*,) 

|H-4| Hardware support b: heh, It was all right but most of it was done manually through the install... so it depended more on the users knowladge.

|C-5| Codecs a+b: portage or internet, they allways warked!

|U-0| USB a: nothing worked.... well thats not true, my mouse did but nothing else did.. :roll: 

|U-5| USB b: all worked  

|G-5| Graphics a: Worked well!

|G-1| Graphicsb b: oh shoot me

|S-3| Speed a: ubuntu like-ish

|S-5| Speed b: HOLY !@#$ =D> wow, this by far the fastest distro I have ever used!!!!!

 
|F-2| Forum Support a+b: very RFTM-ish but ive seen worse.

Kororaa

one horifying mesage, 

"EMERGE ERROR 

FAILURE 

INSTALL FAILED

ejecting cd-rom"

VLOS 

|It-5| Install: it cant get easier, anaconda is soooo noob friendly, but it fialed to addd users, a minor fixable problem.

|Lt-N| Live Test: none

|H-5| Hardware support: fabulous!

|C-5| Codecs very easy to install through portage (break my gentoos rep.)

|U-5| USB: everything worked, including my joystick!!!

|G-5| Graphics: very good

|S-4| Speed: faster than ubuntu!

|F-1| Forum Support: horrible forum, use gentoo's instead :-\" 









overall:

**nooblyness**:
a: 3
b:-281727893072812678349278903524789651279642378946712946723917389217489321794612379463712946738912467129461237946789123647892738921
korora: 2
vlos: 5

**speed**:
a: 3
b: a trillion
kororaa: N/A
VLOS: 4
**package**:
A: 5
B: 5
Kororaa: N/A
VLOS: 4 (yukiyu is a horrible portage front-end, get porthole)
**myrating**:
A: 3
B:4
Kororaa: 0
VLOS: 4

VLOS is a pain to dual boot!



[SIZE=3]**_PORTAGE IS AMAZING!!!!!!!!!_**[/SIZE]

edit:
oops: forgot the urls
[http://kororaa.org/](http://kororaa.org/)
[http://vidalinux.com/](http://vidalinux.com/)
[http://www.gentoo.org/](http://www.gentoo.org/)

---

### Post by rattlerviper on 2006-08-03
|It-na|
Chose not to install this one as there was nothing that screamed at me that I REALLY wanted to try it. 

|Lt-5| Live Test
Rock Solid!  Everything there that I expected to be...but it was rather "normal".  I really expected more from the beta since it is billing realease in 2007.  I expected cutting edge, but was rewarded with stability and everything that we are already use to.

|H-5| Hardware support
Well everything but my printer worked(it's a lexmark z816)but it's not going to work out of the box on any distro.

|C-3| Codecs
Average again, it has what you EXPECT a distro to have, Oog and such but it is lacking mp3 and DVD codecs.


|U-5| USB
Everything I threw at it worked


|G-5| Graphics
Everything worked(then again I have a intel 810 graphics chip).


|S-3| Speed
Average, won't win the race but won't come in last either.

|F-3| Forum Support
Not as good as here, but you could do worse!

[http://www.mandriva.com/en/community/](http://www.mandriva.com/en/community/)
This is the second distro I ever used(mandrake linux back then) around 6 years ago.  It is still solid, but there are much more intresting distros out there.

---

### Post by rattlerviper on 2006-08-03
|It-2|
Well the installer is nonGUI(which is fine) but it is confusing! It flips you back to the same page several times without letting you know what is going on.

|Lt-na| Live Test
Not a live cd, and if it was you would not want to run it as such:-\"  More on that later though!

|H-5| Hardware support
Everything worked! Everything includes that Lexmark z816 I posted in my previous review! holy cow batman that even beat Ubuntu!

|C-5| Codecs
They are ALL here! DVD, MP3, Oog.  You name it it is in here!


|G-5| Graphics
Everything worked great!

|S-2| Speed
SLOW!  This is the slowest distro I have EVER seen!  There is so much eyecandy here it really drags the sytem WAY down.  KDE with every option turned on plus some stuff I never even knew you could do!


|F-0| Forum Support
There is no forum that I could find!

[http://alinux.org/]("http://alinux.org/")

Allright folks I've gotta leave some more input here.  Don't download directly from ALInux if you want to try this, if you do you will end up with a .iso whose md5 does not match.  I wasted so many CDRs trying to burn the download from ALinux it makes me sick.  It is also WAY to slow!  Don't try bittorrent either 100% leachers no seeders. I had to pay .49 cents to download this...if you want to know where pm me and I'll let you know, but I'm sure if you want it you know where to go.  Make sure you use a 800MB cdr and not a 700MB CDR it is too big.  

If you REALLY want this on a pressed disk don't pay the 89.95 from the website it's just a ISO download!  If you really want to give money to ALinux for a download they are selling them on ebay for 8.95!  I think there are supposed 2 be 2 editions from what I can tell.  One "free" one without codecs, and one with the legal codecs that you get charged for.  That being said I got one with codecs for .49 cents.:-\" 

This is a Debian based distro and has apt-get and synaptic, so that is a very happy situation.  If someone has a ultrafast supercomputer they might love this distro!

By the way in my book .49 cents is WAY WAY too much for this distro!

---

### Post by richbarna on 2006-08-03
[COLOR=Blue]|It-4|        [/COLOR]Install
It's not a Gui install, and I already have my ext3 partitions prepared for testing distros so the install for me was easy, took about 15 minutes all in all.

[COLOR=Blue] |Lt-n/a|[/COLOR] Live Test 

[COLOR=Blue] |H-4|     [/COLOR]Hardware support 
Everything worked, I have kept the nv driver for nVidia but I will update that later. I had to use "alsaconf" to enable the sound on my Asus motherboard and had to fiddle around a bit.


[COLOR=Blue] |C-5|[/COLOR]     Codecs 
This little baby plays "everything" but I had to install dvdread. This was easy using "Netpkg" basic synaptic equivalent.

[COLOR=Blue] |U-4|[/COLOR]     USB 
Multi-card reader, pen drive, Sony digital camera all worked. Blue-tooth dongle didn't.

[COLOR=Blue] |G-5|[/COLOR]    Graphics 
Excellent, good video playback, fast. nVidia Gforce fx 5200

[COLOR=Blue] |S-5|     [/COLOR]Speed 
It is insanely fast !! It has xfce desktop, (which looks surprisingly good when it's tweaked a bit).

[COLOR=Blue] |F-4| [/COLOR]Forum Support 
I didn't ask any questions, just searched for some info. But the info given by the users was good. It's not as big as ubuntuforums but I think that they have some quality members there.

Zenwalk is staying on my computer. The only think that is missing is Amarok. I can get k3b from the Netpkg repo. I had to mount my "Shared Data" partition and add it to fstab manually, for me not a problem but for a newbie maybe. If this distro had Puppy or Dyne:Bolic's Automatic mount and root access to ALL partitions, it would be the perfect distro.

I am very very impressed :)
The devs at Zenwalk got this one right =D>
[http://www.zenwalk.org/](http://www.zenwalk.org/)

---

### Post by MethodOne on 2006-08-04
Kanotix 2006 Easter Edition

|It-4| Install
It's a GUI installer. It was easy, except you have to manually partition your drives.

|Lt-5| Live Test
Includes the standard KDE apps, streamtuner, XMMS, KOffice, VLC, preinstalled klik, and IceWM.  The only bad thing is that IceWM is in German.

|H-5| Hardware support
Everything worked, even my Winmodems.  Includes a script to install the proprietary NVIDIA drivers.  The TV tuner on my laptop didn't work.


|C-3| Codecs
No codecs except for MP3 and the ones built-in to VLC.

|U-5| USB
All my flash drives worked.  Haven't tested my other hardware.

|G-5| Graphics
Initially started with nv drivers.  After running the script for the proprietary NVIDIA drivers, everything worked as it should

|S-5| Speed
It's about the same speed as KNOPPIX, which is better than most live distros I used.

|F-2| Forum Support
The forums are mostly in German.  The English section isn't much help because fewer people post there.

I think it's a good distro, but it's based on Debian Sid.  Make sure you read the home page frequently or you might experience system breakage if you install a buggy package.

You can get it at [http://www.kanotix.com](http://www.kanotix.com)

---

### Post by rattlerviper on 2006-08-05
|It-4| Install
Easy, definantly no problems involved here.

|Lt-5| Live Test
Wow!  Best looking distro hands down in my opinion!  It also comes with everything that MOST people want.

|H-4| Hardware support
Apperently does not have madwifi out of the box.  Besaides a non functional wifi card it sure made me smile!  

|C-5| Codecs
As far as I can tell it contains every codec you need preinstalled.  Mp3..got it DVD...got it...Oog...got it:D 

|U-5| USB
Thumdrives work, Digital camera works.

|S-5| Speed
XFCE desktop, and it is FAST.

|F-3| Forum Support
Forums are in Portugues, with a small english section(verysmall).  But on the positive side, it apears that most of the answers to the questions in the english section come from one of the developers so they should at least be accurate.

[http://www.dreamlinux.com.br/]("http://www.dreamlinux.com.br/")
DreamLinux 2.0 is a great distro, though i would prefer to see my wifi card working out of the box it is obviously something that I could fix.

---

### Post by richbarna on 2006-08-06
|It-5| Install
This install was an absolute dream. Even a newbie would smile while installing this distro. Straight forward GUI installer.

|Lt-5| Live Test 
Everything worked and it is fast and smooth.

|H-5| Hardware support 
Everything works, sound monitor, mouse, keyboard...WOW!!

|C-5| Codecs 
It doesn't have them out of the box, but synaptic package manager is LOADED to the brim, wm32, everything: search, click, download, installed that's it.
 
|U-5| USB 
Everything works, Dongle, card reader, pen drive.

|G-5| Graphics
Amazing. This repo using Synaptic has nVidia drivers ATI drivers. Click and install, not a command line in sight !!!!! 

|S-5| Speed 
This OS whizzes !!! I mean it is RAPID, we are talking that it smokes ZenWalk or any xfce distro, and its KDE!!


|F-?| Forum Support 
Who needs a forum !? A monkey could install this !

Ok That's it, 4 partitions. Xp (for the wife), Ubuntu (always Ubuntu), PClinuxOS, and the fourth for testing.

From the repos I got nVidia drivers, all codecs, Google Earth, K3B, Amarok, Dvd Shrink, and God knows what else is in there !! This is a mean distro, you have got to try it.

Not only all this but it looks gorgeous, transparent Konsole, tool bar. Website fonts look amazing, bright colours, tools coming out of your ears, it's just click and do heaven.

This is the only distro i will give a 10 out of 10. Newbies will think this is Xp with Security and no crashes.

---

### Post by compwiz18 on 2006-08-09
I installed Puppy a while ago, so sorry if some of the stuff is not very precise.  I am giving this a better review then the last reviewer, simply cause it worked on my computer :D 

|It-3| Install
Tricky, but requires very little space... ~200MB is what I gave it.

|Lt-3| Live Test
VERY fast once loaded, takes ~2 minutes to load. Once installed to the hard drive, it takes ~20 seconds.  Works on the 3+ computers I have tried it on.

|H-4| Hardware support
Everything worked, but I did have to use ndiswrapper to make my wifi card go (suprise! ;) )

|C-5| Codecs
Can play Pirates of the Carribean (or any other normal DVD) without any additional stuff.

|U-NA| USB
N/A...I only use it if I need a quick boot to get something off the internet, usually in airports or hotels.

|G-4| Graphics
X works great, however the resolution is a little skewed (I have a widescreen laptop, but it didn't list widescreen resolutions on the resolution list), but it looks fine.

|S-5| Speed
INCREDIBLY fast, off the CD or the hard drive.

|F-NA| Forum Support
Didn't need any support, so wasn't tested.

0. Didn't Work
1. Unsatisfactory
2. Satisfactory
3. Good
4. Very Good
5. Excellent

---

### Post by RAV TUX on 2006-08-10
> **yozef said:**
> [COLOR=Blue]|It-N/A|        [/COLOR]Install Test 

N/A

[COLOR=Blue] |Lt-5|[/COLOR] Live Test 

Fast boot to live CD, easy to navigate, screen recognition/English Language automatic

[COLOR=Blue] |H-5|     [/COLOR]Hardware support

All hardware detected: Creative Labs Sound Blaster Audigy Sound Card
Razer Diamondback mouse, Radeon X 856XT Platinum PCIE, etc

[COLOR=Blue] |C-4|     [/COLOR]Codecs

some codecs need to be loaded for DVD movies, CD plays in Kaffaine and recognizes Album , artist and songs. Mp3's load and play flawlessly in XMMS within seconds. tested from my blog site here:
[http://jozefmazeltov.multiply.com/music](http://jozefmazeltov.multiply.com/music)

[COLOR=Blue] |U-5|     [/COLOR]USB

Works.

[COLOR=Blue] |G-5|[/COLOR]    Graphics

Radeon X 856 XT Platinum works flawlessly

[COLOR=Blue] |S-5|     [/COLOR]Speed

Fast but remember I have an Intel EM64T 64bit Dual Core processor
[COLOR=Blue]
|F-4|[/COLOR] Forum Support

English forums are helpfull and adequate

                                                                                  
                                             

Question: Would I consider Knoppix 5.0 as a Distro I would like to install and use? Yes.

[SIZE=3]**[COLOR=Blue]|It-5|        [/COLOR]Install Test **[/SIZE]

Knoppix has by far the best install I have seen from any distro, quick, intelligent and pain free....

simply open 'Root Shell'

type in the following command prompt:

>                               INGNORE_CHECK=1 sudo knoppix-installer 
The installer starts and will walk you through the install options and partitioner:

3 options to install:

1. debian
2. beginner
3. knoppix

[SIZE=3]**ALL the rest are the same as above....**[/SIZE]

---

### Post by hizaguchi on 2006-08-20
[COLOR=Blue]|It-4|[/COLOR]        Install Test

Install is ncurses based, but very simple and extremely fast.  It is reccomended to install only the base system initially and then add more packages later, so that's what I did.  Took about 15 minutes.  Then I added xorg and gnome with pacman, which was also very quick.

[COLOR=Blue] |Lt-N/A|[/COLOR] Live Test 

Not a live CD

[COLOR=Blue] |H-2|[/COLOR]     Hardware support 

Despite a lack of the kind of automatic hardware detection available in most distros, drivers for all of my hardware were available in the main repositories, including recent madwifi and fglrx.

edit: I have deducted points after realizing there is no vbetool or powersave in the repos, and they cannot be obtained through the AUR because vbetool fails to compile.  This is a pretty big deal for laptops.

[COLOR=Blue] |C-4|[/COLOR]     Codecs 

None installed by default, but most are easily added through the standard repositories.  There are no 32-bit packages, however, so Flash is probably out and you'll have to rely on the mpeg libs to play wmv, which I hear works now.

[COLOR=Blue] |U-2|[/COLOR]     USB 

USB support is enabled in the base install, but automounting has to be configured manually.  Instructions are in the wiki.
[COLOR=Blue] |G-3|    [/COLOR]Graphics 
Very recent versions of proprietary drivers are available in the repositories, and there are package builds for XGL and Compiz.  The desktop environments, however, are hardly customized at all, so they can be pretty ugly when first installed.

[COLOR=Blue] |S-5|[/COLOR]     Speed 

This is the fastest distro I've ever seen.  Take regular Arch and make it completely 64-bit.  It boots faster than Windows XP on my machine, and runs Gnome faster than Ubuntu runs Fluxbox.

[COLOR=Blue] |F-5|[/COLOR] Forum Support 

Forums are full of knowledgable and understanding people who are always willing to help out with problems.

Tested on a laptop with a Turion 64 X2 1.6GHz and 1 Gig RAM.  Installation is very easy, but configuration is a pain.  The result, though, is an extremely fast system with a package manager nearly as good as apt and a build system nearly as good as ports.  It's essentially the regular Arch distro, but for 64-bit machines.  [http://www.arch64.org](http://www.arch64.org)

---

### Post by Monsuco on 2006-09-19
|It-5| Install: Very very simple. I would say it's installer is on par with Ubuntu.
|Lt-3| Live Test: Did well though rather slow. You had to go through a setup menu.
|H-4| Hardware support: One neat feature is that ATI and NVidia is automatically supported. It also has propriatary WiFi and Modem drivers. Reasonable support for "winmodems".
|C-5| Codecs: With exception to CSS encrypted DVDs, most stuff such as WMA, MP3, WMV, Quicktime, Real, MPEG, and of course xiph are supported. There is a legitamate program that can be purchased for CSS dvd support (and of course libdvdcss2 would work).
|U-4| USB: It worked, with exception to specialized devices.
|G-4| Graphics: ATI and NVidia work out of the box, but some monitors don't.
|S-1| Speed: Slow, this is it's weak spot. You can speed it up by shutting down all the stuff it runs at boot and changing it so it wont do that.
|F-3| Forum Support: A new comunity. Most of the Linspire comunity can help you too.

Freespire comes with out of the box support for propriatary software. It's aim is ease of use. It did quite well in my test and it was refreshing to have MP3, WMA/WMV, Real, Quicktime, Flash, Java, Adobe Reader, ATI, and NVidia work without hassles. I do think they need CSS support, but that cost money I suppost (I think Linspire traded the name Lindows in exchange for WMA/WMV support as well as cash). Linspire still loves root a little too much, but they are improving. Freespire doesn't use the "w00t w00t we're all r00t" philosophy as much as it's comercial big sister, but it still allows for passwordless sudo. Freespire used to encourage CNR a little too much, but you can install synaptic and use apt-get. Recently it was announced that CNR will be made free (Linspire plans on using OEM fees and Click N Buy for income, but it doesnt sound as profitable). CNR does tend to let packages get old. I hated the theame used by Freespire and all the apps look theamed. Gaim, Thunderbird, Firefox, KDE, and others are all rather theamed. Easy to use, but I think I will stick with Ubuntu for now.

0. Didn't Work
1. Unsatisfactory
2. Satisfactory
3. Good
4. Very Good
5. Excellent

---

### Post by Minyaliel on 2006-09-21
[COLOR=Blue]|It-4|        [/COLOR]Install

Well, the install was easy, really, pretty much like with the Ubuntu live cd. Only con is that it is slooowww.

[COLOR=Blue] |Lt-5|[/COLOR] Live Test 

Good, fast and loads well, if not blazingly fast, then it at least doesn't keep you waiting for long.

[COLOR=Blue] |H-3|     [/COLOR]Hardware support 

Wouldn't recognize my WLAN card, everything else worked adequately.

[COLOR=Blue] |C-N/A|[/COLOR]     Codecs 

Didn't test it, but I'm not too sure anything's included. I wasn't able to check because their website is down.

[COLOR=Blue] |U-3|[/COLOR]     USB 

It would not recognize my mp3 player, but Ubuntu doesn't, either, since it's pretty new.

[COLOR=Blue] |G-4|[/COLOR]    Graphics 

It looks good, really does. What is annoying, though, is if you want to view a picture you've stored on your computer - you'll manually have to open up the program you wish to view the image in and drag the image icon to the program because there is no such thing as a right- click menu in Symphony. This, I think, you'll only have to do once, though, because after I'd done that it did indeed continue opening pictures in the same app. 

[COLOR=Blue] |S-5|     [/COLOR]Speed 

SymphonyOS is _fast_. On my laptop, the installed OS was just as fast as Puppy Linux is when running from a Live CD. 

[COLOR=Blue] |F-0| [/COLOR]Forum Support

Since the website seems to be down (permanently??), I cannot say how good their forums might have been. There seems to be no support anywhere, and, since their website is down, no wiki's or anything.

I have to say, at first, I absolutely loved this distro. That is, until I noticed the bugs. For a beta, it is full of errors; the menu links wouldn't work, there's no way you're ever going to figure out how to even change your desktop background picture, all in all, it's very frustrating and confusing. What I still love about this distro is the desktop environment, Mezzo. It is very simple to use, very intuitive, and it's pretty. I've already installed it and use it with Ubuntu, and have made my Kubuntu desktop look like a Mezzo desktop (without the bugs mentioned, for which I blame Mezzo). It is a very interesting distro, because it shows that things doesn't have to look just like in all the other distros out there. There's no menu bar, no right- click options or anything. Sure, you'll have to get used to it, but if the OS had worked with less errors and a better way of getting to your installed apps, I'd have thrown my Ubuntu cd in the trash a long time ago.

Conclusion: Good ideas, bad coding. 

[www.symphonyos.com](www.symphonyos.com)

---

### Post by richbarna on 2006-09-22
[COLOR=Blue]|It-5|        [/COLOR]Install
I already had a partition prepaired and it installed easily. As it was the base system and the rest came via download, total install time 1 hour.

 [COLOR=Blue] |Lt-N/A|[/COLOR] Live Test
 
 [COLOR=Blue] |H-3|     [/COLOR]Hardware support 
I have an nVidia graphics card, standard 17" Targa monitor, and inbuilt sound card on the ASUS mother board. The nVidia driver from the nVidia website was quick and easy. I had to tweak the xfree86 settings to get a screen resolution above 800x600 and the installed kernel is old and had no sound, so I updated the kernel and everything is running sweet.

 [COLOR=Blue] |C-4|[/COLOR]     Codecs 
Plays just about everything on first look, but will have to manually install certain unmentionable codecs ;)

 [COLOR=Blue] |U-5|[/COLOR]     USB 
Everything plugs in and works, bluetooth dongle, usb pendrive, Sony camera. Webcam will be tested at a later date

 [COLOR=Blue] |G-5|[/COLOR]    Graphics
Clear, fast, video playback is smooth.
 
 [COLOR=Blue] |S-5|     [/COLOR]Speed 
Both Gnome and KDE are very impressive, I have seen no slowdown on any application, boots fast too.

 [COLOR=Blue] |F-5| [/COLOR]Forum Support 
I read the forums to find out a few things, but as an Ubuntu user, their wasn't much that I hadn't already seen here. The forums seem friendly and give good advice to new users.

[http://www.debian.org/CD/](http://www.debian.org/CD/)

---

### Post by richbarna on 2006-09-24
[COLOR=Blue]|It-5|        [/COLOR]Install
This install was sweet and easy, even a newbie could do it.

[COLOR=Blue] |Lt-N/A|[/COLOR] Live Test 

[COLOR=Blue] |H-5|     [/COLOR]Hardware support 
Recognised everything, just did the usual nVidia driver install from the nVidia website, took 5 minutes once kernel headers had been installed vis synaptic.

[COLOR=Blue] |C-4|[/COLOR]     Codecs 
Plays everything apart from certain unmentionable codecs ;) 

[COLOR=Blue] |U-4|[/COLOR]     USB 
Everything recognised, although it had a problem with one of my pen drives.

[COLOR=Blue] |G-5|[/COLOR]    Graphics 
Fast and sweet. That's nVidia for you :)

[COLOR=Blue] |S-5|     [/COLOR]Speed 
Even though it's Gnome, this thing is lightning fast for me, I have elected Debian as my main distro now as everything works out of the box and runs fast and stable.

[COLOR=Blue] |F-5| [/COLOR]Forum Support
Very good forum with good information, although if you are an Ubuntu user, there isn't much that you would have to ask about Debian that you probably already know about Ubuntu.

My main distro now, absolutely outstanding. Download it with any Torrent software (I just got the first iso and then added all the software from synaptic):-
[http://cdimage.debian.org/cdimage/weekly-builds/i386/bt-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/bt-cd/)

---

### Post by TecnoVM64 on 2006-09-29
[COLOR=Blue]|It-3|        [/COLOR]Install
Not exactly easy for a newbie, but reading the dialogs is more than enough to understand

[COLOR=Blue] |Lt-N/A|[/COLOR] Live Test 

[COLOR=Blue] |H-5|     [/COLOR]Hardware support 
Perfect, everything worked in the first boot, just had to go through a wizard that actually sets up everything for you :), of course, nvidia drivers need to be installed manually.

[COLOR=Blue] |C-5|[/COLOR]     Codecs 
Everything except libcss2, nice.

[COLOR=Blue] |U-5|[/COLOR]     USB 
Mounted everything I tried perfectly, no problems there.

[COLOR=Blue] |G-5|[/COLOR]    Graphics 
Beautiful default setup, tango icons everywhere (yay!), and it still flies!, XFCE 4.3.99.1, also available KDE 3.5.4 and GNOME 2.16

[COLOR=Blue] |S-5|     [/COLOR]Speed 
What can I say, ZenWalk is really FAST, uses a beautiful Xfce setup by default, but still, any app loads in less than a second, I love this speed.

[COLOR=Blue] |F-5| [/COLOR]Forum Support
Nice small community, it's growing too, their forums are pretty useful and they have very nice projects (like Tuxgames and ZenCommunity) to make the size of the repos grow.

It's now what I use as my main OS, perfect, if you can't find something in the repos, you can get a Slack package and it works!, nice ideas, nice distro, nice speed, amazing!, I recommend it! :-D 

**Website**
[http://www.zenwalk.org]("http://www.zenwalk.org")

**Take a look to their projects!**
[http://users.zenwalk.org]("http://users.zenwalk.org") - ZenCommunity
[http://www.tuxgames.net]("http://www.tuxgames.net") - Tuxgames

---

### Post by basketcase on 2006-10-15
> **TecnoVM64 said:**
> [COLOR=Blue]|It-3|        [/COLOR]Install
Not exactly easy for a newbie, but reading the dialogs is more than enough to understand

[COLOR=Blue] |Lt-N/A|[/COLOR] Live Test 

[COLOR=Blue] |H-5|     [/COLOR]Hardware support 
Perfect, everything worked in the first boot, just had to go through a wizard that actually sets up everything for you :), of course, nvidia drivers need to be installed manually.

[COLOR=Blue] |C-5|[/COLOR]     Codecs 
Everything except libcss2, nice.

[COLOR=Blue] |U-5|[/COLOR]     USB 
Mounted everything I tried perfectly, no problems there.

[COLOR=Blue] |G-5|[/COLOR]    Graphics 
Beautiful default setup, tango icons everywhere (yay!), and it still flies!, XFCE 4.3.99.1, also available KDE 3.5.4 and GNOME 2.16

[COLOR=Blue] |S-5|     [/COLOR]Speed 
What can I say, ZenWalk is really FAST, uses a beautiful Xfce setup by default, but still, any app loads in less than a second, I love this speed.

[COLOR=Blue] |F-5| [/COLOR]Forum Support
Nice small community, it's growing too, their forums are pretty useful and they have very nice projects (like Tuxgames and ZenCommunity) to make the size of the repos grow.

It's now what I use as my main OS, perfect, if you can't find something in the repos, you can get a Slack package and it works!, nice ideas, nice distro, nice speed, amazing!, I recommend it! :-D 

**Website**
[http://www.zenwalk.org](http://www.zenwalk.org)

**Take a look to their projects!**
[http://users.zenwalk.org](http://users.zenwalk.org) - ZenCommunity
[http://www.tuxgames.net](http://www.tuxgames.net) - Tuxgames

I'll add to this as I just installed it on my box here.  

Installation was text based, something I hadn't seen in a while.  Even after Installation was completed, it still had text-based configuration.  Not a bad thing as everything ended up working, but I'm lazy...Hold my hand!  

Hardware -- Seemed to find everything on this Shuttle XPC system.  Very happy with hardware detection.  

Codecs -- Really didn't pay attention.  Sorry.  

USB -- Saw no problems either. 

Graphics -- Very clean, better than Ubuntu, reminds me of Vector Linux.  

Speed -- Would have to be a tie between this and Knoppix 5.0, and then I think this *might* edge out Knoppix, but I'd have to have the pair side-by-side.  

Forum Support -- Didn't have to use it, I did search their wiki a few times with little success, but google showed me what I needed.  

Really it is probably in my top 5.

---

### Post by Minyaliel on 2006-10-17
My latest crush... 

Installation: 2, I had to try four times before I could get the partitioning right. But it was worth it, now that I look back on it.

Live CD: 5, absolutely amazing; blazingly fast (fast like in DSL and Puppy Linux!), does what it's told.

Hardware: 4... It's (supposedly) one of the weaker points of this distro. It did not detect my WLAN card, but I haven't experienced any trouble apart from this.

Codecs: 5, it has everything out of the box. I haven't tried playing a DVD yet, but I don't see why that shouldn't be included aswell.

USB: 3... there's this issue with my digital cam... It did detect my mp3 player, though.

Graphics: 5. Wow, is this distro beautiful. I haven't seen anything quite like it. E17 sure looks wonderful. And the best thing is that it doesn't interfere with speed or look like it's bloated (eyecandy wise). And all those small, cute animations... and... and... *drool*

Speed: 5. Elive is designed for speed and stability, quoting their websites, and I totally agree. This distro is _fast_ and hasn't crashed _once_. Working with it is a pleasure.

Forum support: N/A I haven't had to ask for help yet, so I don't know. 

Additional notes: 
- Menu seems rather hard to configure. Not all programs show up, which is rather annoying. There should be a way to fix this, but I just can't be arsed.
- It's based on Debian, so it's easily managed by Synaptic or apt
- Configuring the theme is a little more difficult than in KDE and Gnome (but with all those pretty themes available, why would you want to?)

It's official: I'm switching distros...

---

### Post by ThinkBuntu on 2007-06-07
**Zenwalk 4.6**

Install (2): Installation offers few options, and is more restrictive than past Zenwalk installers. Post-installation configuration works, but many parts are unintuitive.

Live Test (0): There's none available, although I'm sure that ZenLive will be up-to-date with 4.6 any week now.

Hardware support (2): Wireless doesn't work from an install, which is semi-expected. But much worse is that ethernet didn't work, and I couldn't get it going using various terminal and graphical methods. The rest of my hardware is very vanilla, and works with every distro.

Codecs (5): All are there!

USB (5): Works superbly.

Graphics (3): I think the previous release looked a little better, but that's just taste. I give this a three because it's very average, and Xfce does nothing to help out. The new compositor feature to allow transparency and shadowing didn't work, with no explanation given.

Speed (4): Speed has always been one of Zenwalk's strong points, but this one isn't blazing fast. Just fast.

Forum Support (3): Forum support is good because the members try hard to resolve every problem, but not so good because you wait a long time for answers. I'll give it an average rating.

---

### Post by igknighted on 2007-06-07
Install (5): The Suse installer, while not blazing fast, allows for the best system customization of any installer I have ever used.  Everything here went perfectly smooth, no issues (10.1 had some update bugs with the installer/post install setup... none here).

Live Test (2): I didn't use it.  No sense in downloading a whole separate DVD to test a distro when I have HD space for that.

Hardware support (5): I wish I could give it a 6, really.  I've been a long time Fedora user, but Fedora 7 just couldn't give me what I needed from my dual monitor setup without a fight, and with Suse 10.2 it was set up perfectly without touching the CLI at all, very impressive.  Handling of drivers like the Nvidia driver also impressed me.

Codecs (3): All are available fairly easily, dvd playback was a little confusing because you have to remove the xine package included and install an xine package by a different name, but overall everything was rather simple.

USB (5): No issues at all.

Graphics (5): Again, Suse is tremendous.  Fedora is prettier overall, but Suse 10.2 just looks professional.  Only complain is the random pixel that sticks off the end of the mouse pointer, and if that is the biggest complain then they are doing something right.

Speed (3): Nothing earth-shattering.  I don't feel like it is slow, but I also don't feel like it is particularly fast.

Forum Support (3): Forum support is decent.  There are some people on suseforums.net who are very good, but the overall userbase there is small.  Novell and opensuse.org both have extensive documentation on their websites that helps.

Overall, Suse 10.2 is a trememdous distro.  Uncheck the ZMD Linux Management packages during the install and you will have smooth sailing throughout.

---

### Post by ThinkBuntu on 2007-06-07
> **igknighted said:**
> Install (5): The Suse installer, while not blazing fast, allows for the best system customization of any installer I have ever used.  Everything here went perfectly smooth, no issues (10.1 had some update bugs with the installer/post install setup... none here).

Live Test (2): I didn't use it.  No sense in downloading a whole separate DVD to test a distro when I have HD space for that.

Hardware support (5): I wish I could give it a 6, really.  I've been a long time Fedora user, but Fedora 7 just couldn't give me what I needed from my dual monitor setup without a fight, and with Suse 10.2 it was set up perfectly without touching the CLI at all, very impressive.  Handling of drivers like the Nvidia driver also impressed me.

Codecs (3): All are available fairly easily, dvd playback was a little confusing because you have to remove the xine package included and install an xine package by a different name, but overall everything was rather simple.

USB (5): No issues at all.

Graphics (5): Again, Suse is tremendous.  Fedora is prettier overall, but Suse 10.2 just looks professional.  Only complain is the random pixel that sticks off the end of the mouse pointer, and if that is the biggest complain then they are doing something right.

Speed (3): Nothing earth-shattering.  I don't feel like it is slow, but I also don't feel like it is particularly fast.

Forum Support (3): Forum support is decent.  There are some people on suseforums.net who are very good, but the overall userbase there is small.  Novell and opensuse.org both have extensive documentation on their websites that helps.

Overall, Suse 10.2 is a trememdous distro.  Uncheck the ZMD Linux Management packages during the install and you will have smooth sailing throughout.
The crazy thing is that those match up identically with there I would place my ratings for openSuSE. Except I'd give graphics a 6 too.

---

### Post by Nikron on 2007-06-07
Install (5): 3 minute install process, another 2 hours after that to actually get everything set up
Live Test (N/A): None
Hardware support (5): Recognized everything, except my intel N card, which I need to use ndiswrapper for it 
Codecs (4): Worked fine after downloading and installing.
USB (5): Worked out of the box
Graphics (5): It works after you install the nvidia drivers..
Speed (5): Extremely fast even using heavy window managers 
Forum Support (3): They're helpful, but not much activity.

Archlinux is basically the only distro I use now.  Mainly because it is customizable, and extremely slim, since you only install what you want. (The system and all its applications take up about 2 gigs on my computer.)

---

### Post by James85 on 2007-11-28
I found some more of these distro-tests on another forum just in case anybody is interested. There is quite a good Ubuntu Gutsy review:
[http://forum.linux-hardcore.com/index.php?board=23.0](http://forum.linux-hardcore.com/index.php?board=23.0)

---

### Post by igknighted on 2007-11-29
OpenSuse 10.3

Install (4.5): The installer, while it works perfectly and gives awesome customization options, is slow.  It took me two hours to install.  BUT, the job of an installer is to do it right (fast is a bonus), and the suse installer does more right than most others (ubiquity and anaconda included).

Live Test (N/A): I didn't try it.  I gave it a 2 before because the live disks were DVDs and non-installable.  I gave N/A here because the live disks seem to be more usable (cd size), and I did not check to see if they were installable.  So without any real knowledge of them I cannot rate them.

Hardware support (3.5): Hardware recognition is top-notch as always.  I was a bit disappointed that the nvidia drivers from the community repo did not work on any of three computer I tried them on.  Also the sound card on my laptop which works OOTB on Fedora 8 and with the backported modules on Gutsy does not work at all, even after installing the new alsa version.  The nvidia thing is really big... would have gone 3 if everything else wasn't so good.

Codecs (3): All are available fairly easily, dvd playback was a little confusing because you have to remove the xine package included and install an xine package by a different name, but overall everything was rather simple. (NOTE: Nothing has changed codec wise, so this is word for word what I wrote about suse 10.2)

USB (5): No issues at all. (Nothing has changed)

Graphics (5): I dig the green.  I think the KDE version looks much nicer than the gnome version (the panel in the gnome version is so plain...).  Overall it just looks professional, props to novell.

Speed (3): Yast speed is greatly improved, especially when it comes to reading repo cache.  I still use zypper most of the time, but for those times when the GUI is useful, I don't dread it anymore.  

Forum Support (3): Forum support is decent. There are some people on suseforums.net who are very good, but the overall userbase there is small. Novell and opensuse.org both have extensive documentation on their websites that helps. (same as 10.2)

Overall, Suse 10.3 is a step up.  I have added this next category because I find it relevant to any distro (and not really covered above)... perhaps we should replace USB with this?  What distro has issues with USB these days anyways?

Package Management (4): I know, I know... yast is awful.  And zypper is a pain too compared to yum and apt.  But there is enough ingenuity here to boost the score from the 2 I would otherwise give it.  First, the build service.  Anyone can load code to the site and have novell build packages for you into your own repo, where others can benefit.  Plus you can search these user repos and install via the awesome "one click install".  I'm running AWN and Fusion-Icon with this and its so much easier to get up and running than any other distro (what good is c-f without the fusion-icon applet to manage it?).  So while the structure sucks overall, the extras are really clever.

---

### Post by tdrusk on 2007-11-30
|It-0| Install
Install was every bit as smooth as Ubuntu's.
|Lt-0| Live Test
It took me a few tries to get the live cd to boot to the gnome desktop. You may have to use safe graphics mode. 
|H-0| Hardware support
Detected everything but my wireless card, which no distro has ever detected.
|C-0| Codecs
Come preinstalled with basically everything you need. 
|U-0| USB
Works great.
|G-0| Graphics
Detected my screen just as well as Gutsy did
|S-0| Speed
Pretty fast for the amount of stuff it has. Faster than Ubuntu Gutsy.
|F-0| Forum Support
You can use their forum, which is just okay, but you can also use Ubuntuforums since they are both based on Gutsy.


5. Excellent 

Everything works well. I don't have lockups like I did in Ubuntu. I still have the flash freezing firefox problem but that exists in every linux distro I have ever tried.Overall, the best distro I have ever used.

---

### Post by crimesaucer on 2007-12-01
**Archlinux 2007.08-2** on a *HP Pavilion dv4230us* (notebook)

My Computer Specs: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00495183&lc=en&cc=us&dlc=en&product=1136372&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00495183&lc=en&cc=us&dlc=en&product=1136372&os=228&lang=en)


**[COLOR="RoyalBlue"]|It - 0 then 5|[/COLOR]** The install was a bit difficult at first. They had problems with 2007.8-0 and 2007.8-1 booting up on some machines (like my laptop). They also upgraded the whole Pacman package manager at that time so installing 8-2 with the new pacman and the "boot-up bug" fixed was the way to go for a nice and easy install. (so fast once you know what you are doing).

The install is all in text (ncurses, then nano or vi for config files), I found this site had the easiest directions to follow: [http://www.raiden.net/?cat=&aid=276](http://www.raiden.net/?cat=&aid=276)

I installed using the testing repositories, so all of my packages are bleeding edge. I've had no problems with any of the testing packages or the new xorg-server and xf86-intel-video driver.


**[COLOR="RoyalBlue"]|Lt - n/a|[/COLOR]** No Live Test


**[COLOR="RoyalBlue"]|H - 2 to 4 (I have Intel)|[/COLOR]** For my detected Hardware, I had to add the Synaptics Touchpad driver, and configure it properly, I also had to add my "modes" section into my xorg.conf, as well as few other configurations. My BCMXX43 was detected, but I chose to use ndiswrapper because it worked better.


**[COLOR="RoyalBlue"]|C - 5|[/COLOR]** Codecs were as simple as: 

```
pacman -S codecs gstreamer0.10-bad gstreamer0.10-ugly gstreamer0.10-ffmpeg gstreamer0.10-mad gstreamer0.10-mpeg2dec

```

... and:

```
pacman -S flashplugin acroread j2re

```


**[COLOR="RoyalBlue"]|U - 5|[/COLOR]** USB works for my camera.


**[COLOR="RoyalBlue"]|G - 5|[/COLOR]** My embedded Intel Graphics card runs Compiz Fusion using AIGLX. I had to configure my xorg.conf for AIGLX, but that is easy.


**[COLOR="RoyalBlue"]|S - 5++|[/COLOR]** Speed... well, my Archlinux is SUPERFAST!!! (faster than xubuntu). 

I use xfce4, and the only thing slowing it down is the Compiz Fusion... which still is very fast. It's extremely fast when just using xfce4 and no composting. Metacity is also fast. But Compiz Fusion with limited plug-ins on xfce4 is what I use... (fast and pretty) 


**[COLOR="RoyalBlue"]|F - 5|[/COLOR]** Forum Support  is good. It has less people,  but the topics seem more technical. I've learned a lot about Linux since using Archlinux, and usually don't even have to ask any questions about anything because the topics are already started with an easy to find thread that's usually already solved. 


Overall I'm very happy with Archlinux and will be using it for a while. I give it a [COLOR="RoyalBlue"]**5+**[/COLOR]

In fact, it just gets better with the AUR and ABS, as well as all of the bleeding edge software.

---

### Post by Ptero-4 on 2008-02-22
My Current primary OS: ZenWalk.
It-5| Install
Pretty easy installer (text-based though).
|Lt-4| Live Test
Separate LiveCD edition.
|H-5| Hardware support
Fairly good hardware support, as good as ubuntu.
|C-5| Codecs
OOTB (AFAIK).
|U-5| USB
Autodetected all my USB stuf.
|G-4| Graphics
Compiz-fusion is easy to get (not in the repos though).
|S-5| Speed
Speedy.
|F-5| Forum Support
Second best to this one.


And my "other" OS: OpenBSD.
It-3| Install
Moderatelly difficult text-based installer.
|Lt-0| Live Test
No LiveCD
|H-2| Hardware support
Doesn't get my Wifi, printer nor trackpad (sees it as a generic mouse).
|C-0| Codecs
Haven't tried it.
|U-3| USB
Detects my sticks.
|G-3| Graphics
Have no plans in installing X, so I can't know if 3D accel works, but it does at least work good enough for my games and DOS emulator.
|S-5| Speed
Pretty fast.
|F-4| Forum Support
No forum of it's own, it relays on bsdforums.org (which is fairly good, although not nearly as good as this or the zenwalk ones).

---

