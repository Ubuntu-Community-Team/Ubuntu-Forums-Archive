---
title: "Trying to make Ubuntu run like Arch"
date: 2006-06-29
forum: Other OS Talk
---

### Post by K.Mandla on 2006-06-29
After being shocked, stunned and overwhelmed by the precision and speed of Arch, I ran into a brick wall over a wireless card that should, by all rights, mesh perfectly with that OS ... but wouldn't.

I blame myself for that failure; it's obviously some tweak I haven't discovered or learned, mixed with a liberal measure of Linux newbieness on the whole. Suffice to say, the card worked perfect in Ubuntu but wouldn't in Arch. And I couldn't figure out why. #-o 

Faced with a dealbreaker like that (and for me it was a dealbreaker), I started thinking ... what's the difference between a base Arch install and a Ubuntu server installation? It's a bit heavier, of course, but would it really be that noticeable? And If Ubuntu will configure the wireless card without a hitch, why not start from scratch with a Dapper server and stack packages on top of that?

I had pecked around with minimal installations a few months ago, trying to make Ubuntu an option on some very old laptops. The [low memory installation methods in the wiki]("https://help.ubuntu.com/community/Installation/LowMemorySystems") give some lightweight GUI options that served as my starting point.

In short, after two or three tries at minimizing the bulk, I've started with this, on top of a Dapper server installation:

```
sudo apt-get install x-window-system-core xfce4 xfce4-terminal thunar prelink preload
```
That puts X into place and the core XFCE structure. I know IceWM, FluxBox and OpenBox are all faster, but I'm an XFCE fan and I get used to things in certain places. I also wanted to be able to compare it with Arch, and I had been using the xfce-svn repositories.

Prelink and preload I found on the [Xubuntu.info]("http://xubuntu.info") site, along with instructions on how to configure them. 

I don't use a login manager; I just log in at the terminal screen and start the gui with 

```
startxfce4
```
For a browser, I use Swiftfox. I find it starts and loads faster. [Disabling ipv6]("http://www.ubuntuforums.org/showthread.php?t=202838") helps too.

In all, the results were not that different. The test machine was an old Dell Latitude CPx J750GT -- 750Mhz/512Mb/20+20Gb/ATI Rage Mobility M1.

I can't say that Ubuntu matched my startup times with Arch, but Ubuntu lagged by no more than 7-8 seconds to boot, and 2-3 seconds to start the GUI. That's acceptable to me ... when I have the added bonus of a working wireless card. :wink: 

If anyone has suggestions on how to lighten the Ubuntu load, or to tweak the setup further, I'd be happy to hear them.

**Edited, Sept. 23: **Since I first posted this at the end of June, I've had the opportunity to collect and try a lot more tweaks that have "narrowed the gap" between Ubuntu's boot and run times, and Arch's lightning-fast delivery.

Before you get all excitable and start reformatting your drive, I should say that I still consider myself a newb, and it's possible that there are ideas here you might find worthless. Or for that matter, you might find they don't improve things at all for you. Your mileage ***will*** vary.

[LIST]
[*]**Binary video drivers**. This will depend on your hardware, of course. But it's probably safe to bet the nvidia drivers (or what have you) will outperform the nv drivers (or what have you).
[*]**Tweaking ext3 file systems to get the best speed for older machines.** Try the ideas [here]("http://www.ubuntuforums.org/showthread.php?t=226644") and [here]("http://ubuntuforums.org/showthread.php?t=107856"). 

[*]**Use a processor-specific kernel. **Try [this]("http://www.ubuntuforums.org/showthread.php?t=186792"), and if you like, other parts of ubuntu_demon's excellent guide.

[*]**Clear out unneeded services.** [This]("http://ubuntuforums.org/showthread.php?t=89491") is time-consuming, but worth it.

[*]**Install InitNG.** I'll be honest: I couldn't get [this]("https://help.ubuntu.com/community/InitNG") to install, but I've heard that it works wonders.

[*]**vm.swappiness.** [This]("http://www.ubuntuforums.org/showpost.php?p=1255511&postcount=43") is another tip from ubuntu_demon. As I understand it, if you run your machine with a relative overabundance of memory, that tweak is just a given. In the case of a stripped-down Xubuntu installation, I think it's safe to say if you have more than 96Mb, you're in good shape. (My system only needs 52Mb to boot as I described it above, and has yet to peak over 72Mb.)

[*]**Reprofile your bootup, then tweak readahead.** [This]("http://www.ubuntuforums.org/showthread.php?t=254263") will require you to install readahead first, since it's part of the default Ubuntu installations, but if you start with a server install, you didn't get it. Enter *sudo aptitude install readahead* in a terminal before you try the stuff jdong listed there.
[/LIST]
These are sort of optional. They might increase your boot speed or just make things easier, but that's up to you and your hardware.

[LIST]
[*]**axely says **[xfs is the way to go]("http://www.ubuntuforums.org/showthread.php?t=246969"). Although for me, [it slowed things down]("http://www.ubuntuforums.org/showpost.php?p=1475250&postcount=31"). Setting up xfs is quicker than ext3 + dir_index + journal_data_writeback + noatime, though. It's going to depend on your processor speed and your assessment of the results.

[*]**Automatically login to XFCE without GDM (or KDM or XDM).** [It speeds things up]("http://www.ubuntuforums.org/showthread.php?t=152274") when compared to straight K/X/Ubuntu, but if you're comparing things to Arch linux, you'll need to even the playing field. ;)

[*]**Tune Ubuntu for broadband.** [This]("http://www.ubuntuforums.org/showthread.php?t=251509") won't interest you if you're not on high-speed internet. Otherwise, your Internet response times might improve.
[/LIST]
As a final note, if you're a fellow tweaker (and I mean that in the technophile sense of the word ... not some other senses ;) ), you might want to install [bootchart]("http://www.ubuntuforums.org/showthread.php?t=241604") early in the game. It will give you an idea of what effect your efforts are having, and provide a graphical history for your individual machine.

I almost forgot! These are some vanity packages that you might want for your new system. These don't speed things up (in some cases, they might actually slow things down ;) ), but they're nice to have and make your system a little more attractive. I'll list them as a code line so you can cut and paste if you like.

```
sudo aptitude install tango-icon-theme-extras xscreensaver-gl-extra xscreensaver-data-extra thunar xfce4-terminal mousepad xarchiver xfce4-goodies
```
As I mentioned a while back, you can get away without thunar, mousepad or a terminal program, but they make things sooo much easier!

My next project: An Ubuntu server with the Equinox DE as the GUI and XFE for an explorer program. Yowza!

Cheers! :KS

**Edited, Oct. 7, 2006: **Since Edgy hit beta, I've been trying to get a feel for what's changed and how that will affect these tweaks. A couple of them are considerable.

First, the new startup is far faster (from my perspective) than the startup in Dapper (which is funny, because Dapper seemed like such an improvement over Breezy). I find that there are fewer unnecessary services running than what I was seeing in Dapper (that's going to depend on your hardware, though), and it seems the start/stop procedures are more streamlined. 

Second, there seems to be a change afoot with the processor-specific kernel packages. If you look at [linux-686]("http://packages.ubuntu.com/edgy/base/linux-686") at packages.ubuntu.com, it now suggests the 686 kernel is the "generic" installed kernel, and the option to install [linux-386]("http://packages.ubuntu.com/edgy/base/linux-386") is available. So for Pentium II+ (?) users, there does not seem to be a need to install a different kernel. Now remember: I'm no expert, so I could be completely wrong with that, which is why I kind of tapdanced through that last sentence.

Next, I'm withdrawing my endorsement of [Swiftfox]("http://www.getswiftfox.com"), mostly on the advice of people like [Kilz]("http://www.ubuntuforums.org/member.php?u=78588") who make, in my opinion, a very strong case against using it. [Swiftfox isn't distributed freely]("http://www.getswiftfox.com/source.htm") and it's compiled by a third person to be installed without the option of looking at the source. While I certainly don't disrespect Jason Halme or suspect him of any wrongdoing, it's a point I often preach at Windows users -- the fact that they have no way of knowing *exactly* what they're installing -- and so I have to follow my own advice on that one.

Instead I've taken to [installing Iceweasel]("http://www.ubuntuforums.org/showthread.php?t=270631"), which is the [GNUzilla browser]("http://www.gnu.org/software/gnuzilla/") created from the Firefox source code, but without stepping on Mozilla's legal toes. Oddly enough, I find it just as perky as Swiftfox, and I have the added bonus of surfing with a clear conscience.

An additional tweak that has proven very helpful was [this one]("http://www.ubuntuforums.org/showpost.php?p=1520299&postcount=18") from jdong, who suggested running *sudo e2fsck -fD /dev/hdXY* **from a live CD desktop**. (That last part is important.) e2fsck will optimize the directories on that drive, and I've found the speed difference to be noticeable (as much as 4-5 seconds on a 1Ghz machine). Try it by booting to a live CD after you've installed your system, then issuing the command from a terminal. Remember that it's only an option if you're using ext3.

Finally, I've found it was *very* worthwhile to experiment with Openbox. For what I've seen, Openbox is every bit as flexible and beautiful as XFCE, and yet makes a vast improvement *again* over the speed of XFCE. For as fast as Xubuntu is when compared to Ubuntu, Openbox is every bit faster. I might be going out on a limb here, but if you **really** want to eke every last bit of speed out of your rig, you really have to try one of the *box sisters -- Openbox, Fluxbox or Blackbox (and IceWM, but that doesn't end with *box ;) ). 

Cheers!

**Edited: Dec. 20, 2006:** I should have mentioned this a while ago, but I consolidated most of these tips and tweaks into a howto for Edgy. Rather than pollute (?!) the forums with yet another post about speeding up Ubuntu, I put it [on my humble blog]("http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/"). I know, I know: It's tacky to link to my blog, but the fact of the matter is, it's not anything you haven't already read through -- it's just reorganized into a step-by-step guide. So don't feel obliged to visit. Cheers!

**Edited, Nov. 6, 2007:** Wow, it seems like forever since I first wrote this thread. Things have changed a lot since Dapper. I still keep up with the changes, but for all practical purposes the tweaks and ideas are in a guide on [my blog]("http://kmandla.wordpress.com"). There's still the version for [Edgy]("http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/"), as well as [Feisty]("http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/") and [Gutsy]("http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/") editions. Please feel free to check them out and make suggestions. I haven't visited this thread in a long time, but I haven't suddenly stopped trying to squeeze speed out of Ubuntu either. ;) Cheers!

---

### Post by woedend on 2006-07-01
I couldn't get it done simply.
I removed all services possible and ran just an equal ubuntu and arch install.  arch just annihilated ubuntu this time around (the drake is very slow compared to breezy for me...i dont know why).  
shame you couldn't get your wireless working ,arch really is a beautiful distro...maybe you should give it another go...its my choice right now.

---

### Post by K.Mandla on 2006-07-01
I might try it again. The silliness of it all is that I'm all of four inches from the PCMCIA port to the router, so the wireless is sheer vanity. And I have a nifty PCMCIA wired connector.

For the record, I removed a few other packages, just to see if I could trim the fat even more. I dropped the jfs and xfs utilities and vim (which I detest), along with some others. I doubt it made much of a difference, but you never know.

---

### Post by hizaguchi on 2006-07-01
I did a "server" install of Ubuntu and then used aptitude to add only the parts of "ubuntu-desktop" that I actually use.  I ended up with a Gnome desktop that runs on around 80 megs of RAM (seems to vary from 69-85, I have no idea why).  It is extremely snappy and starts up much faster than a normal Ubuntu.  It's not quite Arch, but I'm very happy with it since I get the benefits of this community and apt-get to make up for the small performance difference.

I still need to install the i686 kernel and make a few other tweaks too, so the performance gap may get even smaller.

---

### Post by woedend on 2006-07-01
the thing is, it's not the 686 which makes it so fast....tests have been done that show this.  (and slackware would make ubuntu look bad as well)...I'm not sure exactly what it is (packaging technique, patches, layout?). 
@hizaguchi - does that take a long time to piece together what you need?  I thought about it, but usually end up doing a full install and then removing the pieces I dont need...it seemed to go quicker...and ended up with 70-80 megs at boot like you :).

---

### Post by hizaguchi on 2006-07-01
[QUOTE=woedend]@hizaguchi - does that take a long time to piece together what you need?  I thought about it, but usually end up doing a full install and then removing the pieces I dont need...it seemed to go quicker...and ended up with 70-80 megs at boot like you :).[/QUOTE]
Didn't take me very long.  I just used aptitude and went through the list of dependencies for "ubuntu-desktop" and marked just the stuff I wanted, and then let it install.  Somehow though I ended up without APM support and had to go back and install apmd and libapm to be able to suspend to ram.  Thing is, my memory usage is creeping upward as I install new software (stuff that isn't running, like F-spot and Banshee).  I had it trimmed down to 69 megs, but now it's up around 85 just from installing stuff like that.  I'm not really clear on how that happens.  Wasn't a problem with Arch.

Anyhow, I'm curious too about what makes Arch so fast if it isn't the optimization.  Maybe the fact that it is usually running a more up-to-date kernel and xorg than Ubuntu?

---

### Post by K.Mandla on 2006-07-04
I asked the same question on the Arch forums, and in between the funny replies, it seems that some folks blame the initscripts, while others point to optimization -- and others to bloat -- as the reason Arch runs faster.

Either way, I'm still tweaking my Dapper setup to see if I can make it run a wee bit faster. Any suggestions? At this point I'm just searching packages.ubuntu.com to see what's in ubuntu-minimal, subtracting anything that looks trimmable, and seeing if I can still boot. :neutral: 

If there's a better way, I'd be willing to listen. Should I recompile the kernel and take out the unnecessary?

---

### Post by newman on 2006-07-08
I installed arch, but it did not have the madwifi drivers and so it didn't detect my atheros wifi card.  Also I coulndn't figure out how to install Xfce so I had no X.
I'm running xubuntu again with some extra stuff removed, and it's not bad, but I really wanted to try Arch because everyone raves about how fast it is...

---

### Post by egon spengler on 2006-07-09
I'm using Arch now and other than boot time I really don't think it's any faster than ubuntu.

---

### Post by hizaguchi on 2006-07-12
> **newman said:**
> I installed arch, but it did not have the madwifi drivers and so it didn't detect my atheros wifi card.  Also I coulndn't figure out how to install Xfce so I had no X.
I'm running xubuntu again with some extra stuff removed, and it's not bad, but I really wanted to try Arch because everyone raves about how fast it is...

You have to install xorg along with some kind of window manager.  Gnome is just "gnome" and KDE is just "kde", so I would have thought "pacman -Sy xfce" would have worked.  It might be "xfce4" or something like that though.  You could check the package list on the Arch website to see for sure.  Or you might even want to try the latest xfce build from Shadowhand's repo.  There's info on that in the wiki if you just search for "shadowhand".


Anyhow though, I've given up on speeding up Ubuntu beyond just using BUM and taking things out of my Gnome session startup list.  I regular install was using 120 megs when I first installed it and now it's using 85 megs without me doing anything other than normal upgrades.  It seems to vary like that alot, so I can't tell if things I try make it any better, so it is pointless to sit and remove things at this point.  I just went and bought 512 MB of ram and now it seems about as fast as Arch was with 128 MB.

---

### Post by K.Mandla on 2006-07-12
If you start with the base install, you can update with *pacman -Syu*, then add XFCE with *pacman -S xfce4 xorg*. You have to generate your own xorg.conf file, or use *hwd* to make one. (I have this all written down on my little scratch pad on my desk.)

If you open /etc/pacman.conf, you can add this line at the bottom ...

```
[xfce-svn]
Server = http://arch.os-zen.net/pkg/xfce-svn
```
then add the newest version of XFCE with *pacman -S xfce4-svn xfce4-svn-extra*. 

The best place to look for this stuff is in the [Arch wiki]("http://wiki.archlinux.org"). It's very useful. I don't spend much time on the [Arch forums]("http://bbs.archlinux.org") though. I like it better here. :D

---

### Post by brentoboy on 2006-07-13
There is another post in this forum that talks about compiling with 686 optimization, and some guy showed in his real world test about a 10% speed improvment by compiling to the 686 (dropping 386 compatibility altogether)

There were some signficant improvemnts by including some extended multi media assembly instructions that didnt exist on the 386, but those only apply if you are using code that would use them.

The problem is that the 10% speed increase is per package.  So, just by optimizing an application (say firefox) you still dont get a full 10% speed increase becuase it uses lib's that arent optimized, and it will spend some time in the kernel which also isnt yet optimized.

In short, you have to pull a gentoo and compile the whole dang thing for 686 in order to see the 10% (ish) speed increase that arch enjoys by being a 686+ distro.

Arch also removed excess stuff from the kernel, which ubuntu keeps in there becuase if it fixes one person's wireless card, it is worth it (which is why your wireless works.)

The other thing arch did is remove uneeded dependancies from packages like supporting QT or GTK if their desktop doesnt need it (technically you only need one or the other) and lots of other potential dependancies that arent always used.  In this way, the have minimized the size of each binary executable as much as possible without removing the important functionality most people want.

Arch would be great if they had the repo's that ubuntu has, and if things just worked like they do in ubuntu, but if they did that, well, you would have something closer to ubuntu than arch...  it cuts both ways.

so what is a guy supposed to do who wants to have his arch and his wireless too?  use lsmod from the command line.  it will list (ls) all the modules (mod) that are loaded into your kernel.  chances are that your wireless module is listed. (you might have to google the modules listed and discover which one is your wireless.

then, install arch.
use lsmod, and see if it is in there.

if it isnt, then google/use the arch wiki/forums and see how you install that particular kernel module in arch.  chances are the module is either avialable as part of the kernel or as a project on sourceforge.  once you find the code, you'll have to build the module and insert it into your kernel.  (no problem -- right?)

That's all there is to it.   Good luck.

have you tried DSL-N It is *REALLY* fast.

---

### Post by hizaguchi on 2006-07-16
I'm slowly starting to use up my shiny new ram.  All that time of having 128 megs had taught me to run efficiently, but now I'm doing alot of stuff at once and keeping Firefox tabs open and I've got evolution in the system tray... and all of this is really dragging Ubuntu down.  It's not the memory now, it's that Arch is actually faster for doing alot of stuff at once.  I have no idea why.

---

### Post by K.Mandla on 2006-07-29
I haven't made any real breakthroughs on this, but I have noticed a distinct difference in load times for different file systems.

I had been using reiserfs which was a bit taxing, since I use 1Ghz and slower machines almost exclusively. Changing to ext3 with dir_index was a very strong improvement.

I've also combed through the ubuntu-minimal and xubuntu-desktop, and *aptitude remove --purge*d out a lot of things I just don't use (like pcmciautils, on a desktop). I don't know if that makes a big improvement, but I figured if it wasn't being used, it could be stripped out.

I'm also keeping an eye on the [GenBunToo]("https://wiki.ubuntu.com/GenBunToo") pages, since that might be a nice middle ground for me. 

If you've got any ideas ... ;)

---

### Post by dolby on 2006-07-31
i ve been experimnting trying to speed up xubuntu too cause even though my pc is above the xubuntu criteria (athlon xp 1.7+ 256 ram geforce2 mx 400 graphics card) it behaves too slow. been lookin for a more optimised deb based xfce system to my hardware with no luck yet. 

arch is way too advanced for my current knowledge of the linux system
dreamlinux seems nice but geing a brasilian distro with not much english support on forum doesnt seem promising

---

### Post by bodhi.zazen on 2006-08-16
It is easier to make Arch run like Ubuntu. Just install Arch, enable the community repositories and then type;

pacman -Syu
pacman -S *

Seriously, I have tried this with Ubuntu myself. I like the large repository in Ubuntu.

The closest I have come is as follows (let me know if you need more specific instructions).

Start with Ubuntu Alternate install CD.

Do a server install (you will have a CLI only, no X and no synaptic yet).
Install X and synaptic (use aptitude or apt-get)
Install your window manager. Rather then using kubuntu-desktop install:
  kde-base rather then kubuntu-desktop
  Gnome-desktop rather then Ubuntu-desktop 
  XFCE4 rather then Xubuntu.

When choosing applications try to only install what you need/want and not excessive recommended packages.

The problem with Ubuntu is Bloat. Loose the fat.

You can run Ubuntu faster if you change to Fluxbox, Openbox, or IceWM.

The following will get you very familiar with the CLI. 

Warning: the CLI is addictive. I no longer boot into a GUI (XDM/KDM/GDM).
Log in at the CLI; type:
 
startx /usr/bin/startkde
startx /usr/bin/startxfce4
startx /usr/bin/gnome-session

Better startx /usr/bin/fluxbox

Define these in your ~.bashrc as :
alias startflux='startx /usr/bin/fluxbox", etc.

More fun with the CLI:

You can have more then 1 virtual terminal- use Ctrl-Alt-F1, Ctrl-Alt-F2, etc to switch between them.

Did you know you can also have several virtual X sessions as well???

At the CLI type 
startkde &

After KDE is up and running switch back to the CLI ( Crtl-alt-F1)
type startx /usr/bin/fluxbox -- :1 &

Viola, you now have both KDE and Fluxbox running.
To change to KDE -> ctrl-alt-F7
to change to Fluxbox -> ctrl-alt-F8
For CLI ctrl-alt-F1

My wife likes KDE, I use Fluxbox. Now we do not have to log in and out to share the computer.

Another option, which works better is to switch to Debian. Debian is very simmilar to Ubuntu.
Perform a Debian minimal (server) install from testing or etch.
then istall X and your window manager(s).

Try other distros- Zenwalk, BLAG, experiment.

Remember: Install as few packages as possible and you should achieve much better performance.

At the end of the day it was easier to run Arch (I am typing from Arch with Openbox at the moment).

---

### Post by brucevangeorge on 2006-09-10
You mentioned prelink and preload. What's the difference between them? DO they do the same thing? Wouldn't it be redundant to install both? Instead of one...

---

### Post by K.Mandla on 2006-09-10
> **brucevangeorge said:**
> You mentioned prelink and preload. What's the difference between them? DO they do the same thing? Wouldn't it be redundant to install both? Instead of one...
I don't know for sure. Every reference to prelink and preload always seems to mention them in tandem, and to be honest, I've never thought of testing one without the other. :-k 

Really, all I know about the two packages I learned [here]("http://packages.ubuntu.com/dapper/admin/prelink") and [here]("http://packages.ubuntu.com/dapper/misc/preload"). My limited knowledge of Linux suggests to me that one is a preloader, as the name suggests, while the other keeps a map of shared libraries, so things aren't loaded up twice. That's probably a very crude interpretation, and probably not very accurate.

I know they work, though. :mrgreen:

---

### Post by brucevangeorge on 2006-09-11
What about using initNG? There's some hype surrounding it.

I also found a speed increase over the xt3 filesystem by using jfs instead.

---

### Post by xXx 0wn3d xXx on 2006-09-11
Prelink - Makes a "library" or all the libraries. I keeps a list of them for quick acess.

Preload - Takes note of your most commonly applications and "preloads" them into your memory, making them start faster.

InitNG is a replacement for standard init. It is faster but splitting process into smaller ones (like upstart) but the project seems to have been abandoned, sadly. Upstart, another replacement for init will be in Edgy.

---

### Post by brucevangeorge on 2006-09-11
K.Mandla:

You say that you do not use a Login Manager. I did the steps you mentioned to get a super lite desktop. But, I find it annoying to have to login every single time. Is there a way to auto-logon or what login manager for xfce would you reccomend?

---

### Post by brucevangeorge on 2006-09-11
> **K.Mandla said:**
> 
```
startxfce4
```


This doesn't work. Says command start not found. Also doesn't work If I say sudo startxfce4.

How did you get the GUI running?

---

### Post by bodhi.zazen on 2006-09-11
> **brucevangeorge said:**
> This doesn't work. Says command start not found. Also doesn't work If I say sudo startxfce4.

How did you get the GUI running?

xfce4-session or startx. 8)

---

### Post by brucevangeorge on 2006-09-11
Thank you bodhi. That worked.

To the original poster: have you managed to get a decently working instalation? What does your desktop look like?

When I followed your steps, there were no icons on the desk, and all the windows and themes had a very harsh grey color. Nothing like the smooth lines of the original Xubuntu. It looked strange.

---

### Post by K.Mandla on 2006-09-11
That doesn't sound quite right. If you installed xfce4 with *sudo aptitude install xfce4* you should get something strikingly similar to the default Xubuntu desktop. If it's harsh grey with a kind of lattice background and a big X for a cursor, I believe that's the default X desktop. That's not what you want.

I have noticed that the *startxfce4 *command doesn't seem to take effect until reboot (I don't know why, though). So you could restart and try *startxfce4* after the login. That might do the trick.

Actually, with a lot of tweaks, I'm getting really good performance out of a 1Ghz machine. I rebuilt the 750mhz laptop I mentioned oh-so-long-ago and it's very spunky now as a music machine.

Edit: My best results thus far are described [here]("http://kmandla.wordpress.com/2006/08/30/speed-week-the-finale/"). I know, it's not much of a blog. :rolleyes:

---

### Post by K.Mandla on 2006-09-11
> **brucevangeorge said:**
> What about using initNG? There's some hype surrounding it.

I also found a speed increase over the xt3 filesystem by using jfs instead.
I poked around with InitNG for a little while but I couldn't get it to install. Isn't the new system init pegged for Edgy? Is that similar to InitNG? 

EDIT: Just reread and saw xXx 0wn3d xXx's post. Sorry. :frown: 

I've tried reiserfs, ext3 and xfs, and my best results were still with ext3 with the dir_index, journal-data-writeback and noatime tweaks. I'm 99 percent sure that's because I work with machines that are so slow, though. Faster processors can handle the file system demands better than mine can, so ext3 is best for me. :wink:

---

### Post by brucevangeorge on 2006-09-11
Have you run Open Office on your system? With XFCE?

You know how it keeps its owm theme? It uses a very dark dirt grey for its interface? (except for the colored frame from XFCE surrounding it). Well, that's what mine looked like.

I'll post a pic if you need an example.

It looked like the X desktop with XFCE borders. If that makes any sense.

Also, there were not any icons. Do I need those installed separatelly?

---

### Post by brucevangeorge on 2006-09-12
> **K.Mandla said:**
> I poked around with InitNG for a little while but I couldn't get it to install. Isn't the new system init pegged for Edgy? Is that similar to InitNG? 

EDIT: Just reread and saw xXx 0wn3d xXx's post. Sorry. :frown: 

I've tried reiserfs, ext3 and xfs, and my best results were still with ext3 with the dir_index, journal-data-writeback and noatime tweaks. I'm 99 percent sure that's because I work with machines that are so slow, though. Faster processors can handle the file system demands better than mine can, so ext3 is best for me. :wink:

From what I read, XFS and Reiser both use more CPU than ext3. I use JFS becuase it has better performance than ext3, uses a little more CPU, but it also gives me more diskspace when formatting.

---

### Post by K.Mandla on 2006-09-12
> **brucevangeorge said:**
> From what I read, XFS and Reiser both use more CPU than ext3. I use JFS becuase it has better performance than ext3, uses a little more CPU, but it also gives me more diskspace when formatting.
Good call. The best file system is always going to be the one that works best for the user and the machine. That's one of the things I like about linux -- I'm not tied to a particular option because Microsoft says so.

> **brucevangeorge said:**
> Have you run Open Office on your system? With XFCE?
Actually, Abiword and Gnumeric (*sudo aptitude install abiword gnumeric*) do just about everything office-wise I need. If I need to make a pdf I print to a postscript file and convert with ps2pdf14. It's a little backward, but I don't have many office requirements.

OpenOffice might bog things down again, but it's worth a try.

> **brucevangeorge said:**
> You know how it keeps its owm theme? It uses a very dark dirt grey for its interface? (except for the colored frame from XFCE surrounding it). Well, that's what mine looked like.

I'll post a pic if you need an example. ... It looked like the X desktop with XFCE borders. If that makes any sense.
A snapshot might be a good idea, just so we can be sure we're all on the same page. 

Also remember to check to see if XFCE is "managing" the desktop. Under Applications > Settings > Desktop Settings, make sure the box that says "Allow XFCE to manage the desktop" is checked. That's the only other thing offhand I can think of that might keep you from getting the proper background.

> **brucevangeorge said:**
> Also, there were not any icons. Do I need those installed separatelly?
You should get the default "Rodent" set installed, but you might also have to enable them under the User Interface Settings. If they're not there, try *sudo aptitude install tango-icon-theme-extras*, which will install the Tango suite, which is much more attractive in my opinion. :biggrin:

---

### Post by brucevangeorge on 2006-09-12
Yup. Did the Tango Suite. Also installed the GTK clearlooks theme. Now my windows look nice and smooth like gnome.

How much memory does your system use by default? When you just booted?

---

### Post by K.Mandla on 2006-09-12
At boot, my little 750Mhz only needs 52Mb to reach the desktop. After starting XMMS and Realplayer 10 and running for three or four hours, I'm  only up to 72Mb. 

It's very speedy to boot, too ... if you can find the post on automatically logging in without GDM, that makes the whole login+startxfce4 process quicker too.

---

### Post by brucevangeorge on 2006-09-12
That's not bad. My startup with all the icon & window themes is 59.5mb (according to conky). When I use swiftfox, ut jumps to ~78mb.

---

### Post by K.Mandla on 2006-09-15
I'm editing my original post with a few tweaks I've discovered since the end of June. Thus far, they still don't push Ubuntu to the speed of Arch, but the gap (in my perspective) is narrowing. 

If I get the time and inclination, I'll rearrange this as a collective howto for older machines. I'm still tweaking and finding new ways of doing things. It's a learning process. ... ;)

---

### Post by proxess on 2006-09-15
right now im running my old portable machine with ubuntu and its extremely fast

i installed ubuntu 5.10 server, dist-upgraded it to dapper, installed xorg, xdm, blackbox, synaptic, firefox, vlc, xmms, gaim, xterm and a few other things from automatix, and its super fly

edit:
its an intel celeron with mmx 466mhz 128k L2 cache
64mb sd ram
s3virge 4mb graphics
6.4gb disk

---

### Post by Neobuntu on 2006-10-04
Is there a speed reason for starting with 5.10 or is that just what you did?

Thank you.

BTW Speed is a worthy goal and time is something you will never get back (yet still, I tinker).

I have a real challenge. How about an old Thinkpad 560 (no E,X,Z or nothin') notebook with 24MB RAM, 2.1G HD and weird sudo 256K (8bit) 800x600 Trident9660/Cyber xx85 DSTN screen? How do I get a fast ubuntu on that? Deli Linux (with X and fluxbox) almost worked, but for the crappy Video. I'd say deli Linux (Beta) is the lowest one can go and still have decent (opinion) X apps. (Yes I know about DSL.)

...and another thing(laptop). I will not even tell you (well, I guess I am) about my 200MB HD (not GB), **[COLOR="Red"]8MB[/COLOR]** [COLOR="Red"]RAM[/COLOR] (not 80MB), TFT 800x600, Satelite notebook! He he. It's a miracle of science that it runs 95(now)! Full Deli (makes me hungry) at 400**M**B wouldn't even fit here. Shouldn't it be able to run Linux (X at least like 95) too? Too bad 95 is SO old(and unsecure).

Just so you know what a old computer **really** is. :)

Seriouly I guess I have to bite the bullet and go for a (remove HD and copy software to it) full fledged (what does fledged mean?); custom install of either Slackware or Debian; on the Thinkpad. I (think) Slack might be trimmer but I sure would prefer the Debian way. 

What do you know about these?

---

### Post by K.Mandla on 2006-10-04
> **Neobuntu said:**
> I have a real challenge. How about an old Thinkpad 560 (no E,X,Z or nothin') notebook with 24MB RAM, 2.1G HD and weird sudo 256K (8bit) 800x600 Trident9660/Cyber xx85 DSTN screen? How do I get a fast ubuntu on that? Deli Linux (with X and fluxbox) almost worked, but for the crappy Video. I'd say deli Linux (Beta) is the lowest one can go and still have decent (opinion) X apps. (Yes I know about DSL.)

I will not even tell you (well, I guess I am) about my 200MB HD (not GB), **8MB** RAM (not 80MB), TFT 800x600, Satelite notebook! He he. It's a miracle of science that it runs 95(now)! Full Deli (makes me hungery) at 400**M**B wouldn't even fit here. Shouldn't it be able to run Linux (X at least like 95) too? Too bad 95 is SO old(and unsecure).

Just so you know what a old computer really is. :)

Seriouly I guess I have to bite the bullet and go for a (remove HD and copy software to it) full fledged (what does fledged mean?); custom install of either Slackware or Debian. I (think) Slack might be trimmer but I sure would prefer the Debian way. 

What do you know about these?
You're right: With machines that old, you almost have to go with another distro.

For what I've seen, the biggest problems for Ubuntu are memory and hard drive space. [I tried to install Ubuntu on 32Mb of memory]("http://www.ubuntuforums.org/showthread.php?t=259901"), and the installer freaks out. You end up leaving out important stuff -- like network cards -- because it needs all the space it can get just to *run itself*. 

Then you're left with a crippled text-based system that takes *minutes *to boot anyway, and it becomes a slow, mind-numbing experience. I did it once or twice, got frustrated, then put more memory in.

Additionally, it takes 300Mb to put a server into place, and I've not been able to trim a functional GUI to below 700Mb total, with the server install. It might be possible, but you'd have to pick-and-choose things from x-window-system-core, and that could take *forever*.

Which isn't to say it isn't possible. It just means it's tricky, time-consuming, and in the end, might not be worth the effort involved.

Except you would win the admiration and respect of everyone on the forums. :mrgreen:

---

### Post by Neobuntu on 2006-10-04
Being right is so, well, cozy. LOL

No really, I don't have a problem with a distro like Ubuntu moving toward newer, faster hardware that most everyone has.

Yet, I'd hate to toss a working computer and these experiments intrigue me. So it's nice to have options.

So I'm back tring, to out-do 95 but with newer, safer software. It's not easy. Hardware limits are hardware limits. Still, they can perform many tasks and also the tasks that they did back in their day. What to do? It's definately a hobby and wastes time. Maybe I'll make a large screen MP3 player out of it.

---

### Post by K.Mandla on 2006-10-04
There are lots of minidistros out there, entire linux-based systems on a floppy. ...

[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

I doubt very much you'll find one as full-featured as Ubuntu :rolleyes: but you never know. Even a distro on five or six floppies could make those ancient machines usable again. 

Good luck! Let us know what happens!

---

### Post by Neobuntu on 2006-10-05
Yeah, I must go out on a limb and say Linux does not shine as bright on really old hardware (so as not to miss lead). 

But what is really old and what are we doing with the old thing?

Good results can come from the time invested but they can never exceed their hardware. Yet, they can pretend to, as a client; given the minimum specs for that. :) See Edubuntu.

---

### Post by K.Mandla on 2006-10-07
Just a quick update ... I added jdong's e2fsck tweak, a note about Swiftfox and a few points on the processor-specific kernels. Nothing major, but worth mentioning. ;)

---

### Post by zek725 on 2006-10-15
Isn't xubuntu-desktop easier? What are the differences?:-k 

sudo aptitude install xubuntu-desktop

---

### Post by K.Mandla on 2006-10-15
> **zek725 said:**
> Isn't xubuntu-desktop easier? What are the differences?:-k 
Easier, yes ... but it also tends to install a lot of things that can slow me down. For example, without GDM as the desktop manager, the boot process is considerably faster. Granted, you have to log in at the terminal screen and start XFCE manually, but there are ways around that, and the speed difference is considerable.

It's an issue of drive space, too. Too many programs I don't need will take up space on the drive, forcing the head to skip over them when I want to do something else. It's not so much that fragmentation is a problem ... it's the fact that some space is taken up by programs that are "closer to the center," and access times fall, and response times fall, and things ... start ... to ... seem ... slower. ... ;)

In reality, for the average user, there's not much use in tweaking ad nauseum. There are people who do nothing but tinker and tweak, looking for the perfect combination for their machine. I'm one of those people. There's no harm in it. It's a hobby, I guess. :rolleyes:

---

### Post by zek725 on 2006-10-16
> **K.Mandla said:**
> Easier, yes ... but it also tends to install a lot of things that can slow me down. For example, without GDM as the desktop manager, the boot process is considerably faster. Granted, you have to log in at the terminal screen and start XFCE manually, but there are ways around that, and the speed difference is considerable.

It's an issue of drive space, too. Too many programs I don't need will take up space on the drive, forcing the head to skip over them when I want to do something else. It's not so much that fragmentation is a problem ... it's the fact that some space is taken up by programs that are "closer to the center," and access times fall, and response times fall, and things ... start ... to ... seem ... slower. ... ;)

In reality, for the average user, there's not much use in tweaking ad nauseum. There are people who do nothing but tinker and tweak, looking for the perfect combination for their machine. I'm one of those people. There's no harm in it. It's a hobby, I guess. :rolleyes:


8) Cool! I'll try it. :D

---

### Post by jhenager on 2006-10-16
> **Neobuntu said:**
> Yeah, I must go out on a limb and say Linux does not shine as bright on really old hardware (so as not to miss lead). 

But what is really old and what are we doing with the old thing?

Good results can come from the time invested but they can never exceed their hardware. Yet, they can pretend to, as a client; given the minimum specs for that. :) See Edubuntu.
On a whim I tried loading the Live CD on an original Pentium system. I think it is a 166MHz processor with 128MB of RAM and two 1.5GB SCSI hard disks.
After about 28 hours, it came up to an error message that the trash applet couldn't be loaded. I tried to tell it to ignore the error, but it seemed to just sit there, and I tired of the attempt and powered it off. There are limits to everything, I guess. It was trying, tho....:)

---

### Post by K.Mandla on 2006-10-16
That live CD definitely has a baseline for technology. It's not impossible to get Ubuntu running on [a machine with those specs]("http://www.ubuntuforums.org/showthread.php?t=259901"), though ...

---

### Post by bionnaki on 2006-12-18
thank you for this thread. I am going to install linux on my brother's old compaq machine that runs windows 98 on it. I am unsure of the exact specs (I remember it being a top-of-the-line computer around 1998 or so) but I am sure I can get the machine running well.

---

### Post by RajivNair on 2006-12-20
What i like the most about ARCH apart from the speed, is the concept of rolling release.Ubuntu has to manage at one time packages from 3 different versions comprising of 17000 packages(avg.) while in Arch the repository is divided on the terms of the s/w as extra,current,unstable,community and testing.So once you install it and keep your system updated you really dont have to d/w another ISO and also that Arch offers the latest packages(i'm already running kernel 2.6.19) ,even though it did had little issues with my intel chipset all i had to do was to append a simple command in grub menu.I really wish to see the concept of one single central repository in Ubuntu with latest packages ,and a snapshot can be brought out every 6 months.

---

### Post by MetalMusicAddict on 2006-12-20
> **RajivNair said:**
> I really wish to see the concept of one single central repository in Ubuntu with latest packages ,and a snapshot can be brought out every 6 months.

I really like that idea. :)

You can kinda do that now but its a little more manual. Editing your sources.list and all.

---

### Post by forger on 2008-07-02
You could just install ubuntu-minimal ubuntu-standard and remove all the packages installed along with ubuntu-desktop by purging it.
On the other hand, maybe you would like to use debian, which allows more customizing between packages

Also, let's not forget the wealth of modules and applications ubuntu provides for an all-around use :)

---

