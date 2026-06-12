---
title: "INX Is Not X"
date: 2008-07-15
forum: Other OS Talk
---

### Post by Tux Aubrey on 2008-07-15
I know that some people like to take minimalism to the extreme.  Here's an Ubuntu-based cli Live distro that is specifically designed to teach the power of the command line.  So far, I've used it in a VM and it is great fun and definitely worth the download!  Here's the developer's blurb (taken from Another Linux Forum)

> INX ( INX Is Not X) is now based on Ubuntu 8.04.1 , using the ubuntu-minimal and ubuntu-standard meta-packages as a base. 
It is a live CD designed to give people a fun way to learn about the command line. It is not just white text on a black console - it might surprise you. 

The structure is a series of menus from which you can choose what to try out. The most important part of the distro is probably the series of tutorials that walk you through some basic command line methods. You can listen to internet radio, either through a few "hard coded" options or entering search terms ( say, "goonshow" :-) ) 

There are two main browsers, an IRC client (irssi), three file managers (Midnight Commander, Vifm, Linm), a mail client (mutt) with two setup options (one uses Gmail, the other your ISP with the IMAPS secure protocol). The default editor is "Jed" but Vim is included, with run-time, and of course nano. Zile is included as a tiny emacs-like editor as well. As they say, "But wait! there's more!" ... I won't spoil the surprise  

The iso is about 186 MB, and I think worth the download... ( I'm somewhat biased of course, as the primary author). The Release Candidate 1 can be found at: [http://inx.maincontent.net/download.html](http://inx.maincontent.net/download.html) If you would like to help with testing the torrent we set up yesterday, please try.


The homepage is [http://inx.maincontent.net](http://inx.maincontent.net)  

> Some of the programs included in INX:

abcde                                          (CD ripper script)
calcurse                                       (calendar)
cmatrix                                        (screensaver)
console-freecell                             (little card game)
console-terminus
cplay                                           (music player)
dialog
dict                                             (dictionary lookup from command line)
elinks-lite                                      (tabbed CLI browser)
fbgrab                                          (take screenshots in a tty / vt )
fbi                                               (picture viewer - also fbgs which shows pdf files)
figlet                                            (fun ascii font mangler)
gpm                                             (use your mouse)
greed                                           (another little game)
htop                                            (improvement on the "top" monitor)
iftop                                            (monitor network activity)
iptraf                                           (network monitor with attitude.    .    .    )
irssi                                             (IRC client)
jed                                              (emacsish editor with mouseable menus and colours/syntax etc.    )
links2                                           (graphical or text mode browser - graphics on frame buffer)
linm                                             (yet another file manager)
mc                                              (Midnight Commander file manager)
moc                                             (Music On Console - very nice)
mpg321                                        (mp3 from the command line)
mplayer-nogui                                (music and video player)
mutt                                            (email client)
robotfindskitten                             (another harmless game.    .    .    )
sc                                               (spreadsheet)
screen                                         (powerful cli session manager - who needs a window manager?)
sl                                                (not telling you)
sshfs                                           (secure encrypted file access/sharing with ssh)
telnet                                          (yeah, well, it still has uses.    .    .    )
urlview                                         (see URLs from mutt with CTRL+B)
usbmount                                     (automatic usb mounting, with menu in INX)
vifm                                             (file manager for vi/vim fans)
vim                                             (the editor, plus runtime etc.    )
zile                                             (tiny basic emacs clone)

Menus:  GNU Screen , Secure Share (use sshfs to access network resources) Tutorial ( currently nine tutorials from the very simple to the *slightly* advanced), Net & Web, Fun ( some little games, and a CD player using mplayer (CDMP), Mail (use mutt with IMAPS either via your ISP or Google), .    .    .    

You can boot the live CD "toram" (choice is on the boot-up screen), which of course runs faster and frees your CD or DVD device for other uses.    

Quite a lot of other stuff.     Moc features prominently as the music player for example.    

You can also get a Virtual Box compressed image (expands to 8 Gig maximum, download size about 177 MB) Look in [http://www.inx.maincontent.net/devel](http://www.inx.maincontent.net/devel) , and get the RC1 version

Just bunzip2 the file, and point virtualbox at the decompressed hard drive image.     

The user name for the VBox image is "inx" and the password is "inx"

---

### Post by darrelljon on 2008-07-15
Cool, I've been looking for a non-graphical but text menu driven distro.

---

### Post by zmjjmz on 2008-07-15
Wow!
This looks great!

---

### Post by zmjjmz on 2008-07-15
Well, It'd be more helpful if this didn't need to run from LiveCD
:/
EDIT: I'll try the experimental script.

---

### Post by VitaLiNux on 2008-07-15
Good! I'd give it a try! After all, I'm a VM freaky!!  XD

---

### Post by DeadSuperHero on 2008-07-15
If only I had found this last month...

---

### Post by zmjjmz on 2008-07-15
> **Mr. Psychopath said:**
> If only I had found this last month...

You can still download some of the scripts, you may appreciate them.

---

### Post by Chilli Bob on 2008-07-16
> **Mr. Psychopath said:**
> If only I had found this last month...

I've been planning on trying Mr Pschopath's experiment myself on a spare PC, but this INX looks like an easier option.  I'll definitely give it a look.

---

### Post by inx-one on 2008-07-16
It *is* possible to install to a hard drive, but as you say it is experimental.

Note that currently you need a blank hard drive for this to work - that is, the installer knows nothing about partitioning.

The Virtual Box images are made with the 'inxtaller' script, so it works fine for that purpose - but it's easier to just grab the ready-made image from the /devel directory on the site, of course.

For those who feel adventurous - go ahead and try the install script, but *please* try it on a machine that "doesn't matter". It won't break anything, but it simply uses the whole hard drive currently. Multiple hard drives are another no-no at the moment.

You run the installer from the live CD - it basically blats the read-only file system onto your hard disc, and installs grub to the mbr.

You can grab a copy from Launchpad:

Brief information:
[https://code.launchpad.net/~inx-devel/inx/inxtaller]("https://code.launchpad.net/~inx-devel/inx/inxtaller")

The script:
[http://bazaar.launchpad.net/~inx-devel/inx/inxtaller/files](http://bazaar.launchpad.net/~inx-devel/inx/inxtaller/files)

Or (easier) grab it from the site while booted in INX ( it isn't linked there but it is in the root of the site):

wget [http://inx.maincontent.net/inxtaller](http://inx.maincontent.net/inxtaller)

Remember, if it breaks you get to keep both pieces ;)

---

### Post by chris4585 on 2008-07-16
this is pure awesomeness.. *gives a copy to his girlfriend* :D

---

### Post by Chilli Bob on 2008-07-16
D'OH!!  I think they've used up their bandwidth.  I can't get to the download page at all.

---

### Post by Chilli Bob on 2008-07-16
> **Chilli Bob said:**
> D'OH!!  I think they've used up their bandwidth.  I can't get to the download page at all.


err....ummmm... or _I_ could pay _MY_ ISP bill.  

It's downloading now. :oops:

---

### Post by zmjjmz on 2008-07-16
> **inx-one said:**
> It *is* possible to install to a hard drive, but as you say it is experimental.

Note that currently you need a blank hard drive for this to work - that is, the installer knows nothing about partitioning.

Does INX have cfdisk included?
Because then I could just wipe the current partition (which is an athfs partition) on the HDD.
Speaking of this, will a computer with 128MB RAM work nicely?
I know toram wouldn't work, but from the HDD in a normal way?

---

### Post by inx-one on 2008-07-16
> **zmjjmz said:**
> Does INX have cfdisk included?
Because then I could just wipe the current partition (which is an athfs partition) on the HDD.
Speaking of this, will a computer with 128MB RAM work nicely?
I know toram wouldn't work, but from the HDD in a normal way?

Yes, cfdisk is included. Note that just wiping one partition on your drive is not enough, *if you have others*, though. The inxtaller script (so far) just makes a swap and a / and uses *the whole drive*.

The live CD ISO will boot in Vbox with 96 MB RAM allocated to it - I don't have an actual machine with 128 MB or less, but it's worth a shot. If the CD boots, the inxtaller should work.

sudo ./inxtaller

should do. Please report success or failure with comments :) We hope to improve the "inxtaller" but tests in a virtual machine are not the same as "the real thing" !

---

### Post by Chilli Bob on 2008-07-16
OK, I've got it working, and if all goes well I will be posting this from elinks.  I gotta be honest and say that I'm not loving elinks at all. It's a pain to navigate around in.  On the other hand I can see myself using Jed. The internet radio is cool (was just listening to "Hammer to Fall" on Virgin radio.  The leggo man movie was cool.  The spreadsheet feels a bit clunky, even to someone who grew up using as-easy-as.  All in all I'm having a hoot with INX.  It's like the old pre-windows DOS days, but with the promise of screen (If I can work it).  I'd really love an RTF word processor though.  That would rock!

---

### Post by FrostFire on 2008-08-02
> **Chilli Bob said:**
> [snip]
I'd really love an RTF word processor though.  That would rock!

I've had a look at what's available for rtf editing and they all need X, however there is a package called udo that will allow you to write plain text files and compile them into rtf files. you could use that in jed. You can look at rtf using unrtf or wv

---

### Post by wolfen69 on 2008-08-02
looks nice. cant wait to try it. keep up the good work.

---

### Post by spencercarran on 2008-08-02
Would it be possible to put this on a 256MB flash?

---

### Post by wolfen69 on 2008-08-03
i'm typing this reply from the inx live cd. i have to say i'm impressed. this will definitely sharpen my command line skills. i was shocked to see it plays videos very well, and the graphical web browser is pretty good too.

what about wireless? how can i get that going?

great job with this distro. one of the most unique i've seen. the built in tutorial is a nice touch too. well, i've got to  go back to exploring what this has to offer. thanks for all the hard work.

---

### Post by inx-one on 2008-08-09
> **wolfen69 said:**
> what about wireless? how can i get that going? 

Well, my laptop is a ppc iBook G4 , and so far I haven't attempted a ppc INX :)

The CLI tools for wifi are there, but you will have to read up on configuring it, sorry - I have no suitable testing methods here.

'wpasupplicant' is in INX, as is 'wireless-tools'

Perhaps a future version will have a config menu for wireless...

INX is Ubuntu Hardy underneath, so the same instructions apply.

Hope this helps...
[http://help.ubuntu.com/community/WifiDocs/WifiHowTo]("http://help.ubuntu.com/community/WifiDocs/WifiHowTo")

---

### Post by zmjjmz on 2008-08-09
Maybe you could try and install ceni?

Also, I've been meaning to try out INX, but with my hurt shoulder I can't lift any eMachines to test it on x_x

---

### Post by inx-one on 2008-08-16
The Release Candidate 2 of INX is now on the server:

[http://inx.maincontent.net/download.html](http://inx.maincontent.net/download.html)

 New in RC-2:

* Not exactly new, but I have incorporated a wrapper script that runs
  xlinks2 / links2 -g  *from the menus* with directfb, which makes
  using it much more pleasant, without using suid root on the links2
  binary. Invoking it as xlinks2 from the command line of course
  bypasses the wrapper and still works fine with directfb.

Your mouse should work better with xlinks2 now, and it should be  quicker. :)

* Fixed the "wikig" command to use this wrapper, since it's a little
  script, and had the same access issue as the menus.

* Extra introductory docs, both "Starters" and "Advanced" - these are
  accessible from the new "first-screen" that pops up after the boot
  sequence. You can get an index, navigate forwards or back and so on.

* Credits also accessible from the "first-screen"

* GNU GPL Version 3  item on the "first-screen"

* "Welcome" splash screen - this and the "first-screen" are in yellow
   and "brown" (actually it's a non-bold yellow that looks brown - let
   me know what you think of this. It looks OK on my monitor... )

* Welcome splash should only appear on first booting, and after
   continuing from the opening screen to the main INX menu.

* "Tools" menu has two new keys to access the first screen - "a" to get
   the default screen, "b" to go to the "INX 101" screen. On exit from
   these you should return to the Tools menu.

* Added some basic "man" pages - see "apropos inx" and "man cdmp"

* Included "Inxtaller" and "Buildinx" - but without menu links, and
  referenced only from the "advanced" docs. (With warnings, for
  inxtaller) Man pages for each.

Enjoy :)

---

### Post by chris4585 on 2008-08-16
@_@ *downloads*

can't wait to try this! :shock:

---

### Post by zmjjmz on 2008-09-06
Bump, I want to see how far along this is.

---

### Post by chris4585 on 2008-09-06
Yeah it deserves a bump in my opinion

---

### Post by zmjjmz on 2008-09-07
Does RC2 include the installer?

---

### Post by inx-one on 2008-09-08
> **zmjjmz said:**
> Does RC2 include the installer?

Yes, it's there in /usr/local/sbin/inxtaller.

Please read the 'advanced" introductory docs from the first screen after boot-up, and look at "man inxtaller"

It has not changed, but there have been three successful installs to blank drives, including one I have done on a box that I wiped to experiment with.

Just don't try to make a dual boot, or anything that requires multiple partitions, unless you are confident about hacking the script!

Currently you need to delete all partitions on the drive with cfdisk or fdisk before you start. Yes, it's pretty basic so far, but functional for a simple install.

If anyone *does* improve the script, please let us know. INX has a small team of people so far, who are often busy with Real World issues and work :)

The best way to stay in touch with INX is to sign up for the mailing list at

[http://lists.inx.maincontent.net/listinfo.cgi/inx-inx.maincontent.net](http://lists.inx.maincontent.net/listinfo.cgi/inx-inx.maincontent.net)

You can read the posts at

[http://lists.inx.maincontent.net/pipermail/inx-inx.maincontent.net/](http://lists.inx.maincontent.net/pipermail/inx-inx.maincontent.net/)

There should be a new (interim) iso in the next week or so...

Stay tuned.

Also, one easy way to get a bootable USB stick of INX is to use the program "Unetbootin" from

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

The boot-up screen is not as nice as the INX one, but it does work, and you can boot "toram" if you wish - you can also save work on the stick, but it uses the FAT filesystem, so mc and co. might complain about not being able to change permissions. Still saves the file if you skip the warning :)

I've installed the inx-rc2 iso to a 256 MB USB stick successfully here, using Unetbootin. That would be the smallest possible size, since the squashfs image uses most of the space (around 186 MB) as you would expect. There's still around 50 MB spare - and since the USB mounts automatically at /media/usb0 for example, you can save stuff to that mount point. A bigger drive would obviously be an advantage though.

---

### Post by zmjjmz on 2008-09-08
Wonderful to hear that.
I'll get to installing it once my MacBook is fixed so I can burn CDs.

---

### Post by sertse on 2008-09-08
Hi, it's a great distro, but I already told you that :P Got it working on my usb, now it's much more convenient. 

INX also has a irc channel, #inx on freenode. Lurk there sometime.

Should also emphasise inx-one's comment, before anyone gets hurt: The installer atm doesn't recognise partitions, other OSes etc. So be careful if you're going to use it.

---

### Post by zmjjmz on 2008-09-08
I actually don't care much for dual boots, so none of my computers have to deal with it.

---

### Post by inx-one on 2008-09-13
There's a new iso for INX - it is an interim one that fixes a few issues.

[http://inx.maincontent.net/devel/devel-updates/](http://inx.maincontent.net/devel/devel-updates/)

Fixes:

* The nice people at shoutcast.com altered their website, with the result that the "Search for music on shoutcast" menu fails in INX. We've substituted the "classic.shoutcast.com" URL, which seems to have fixed that - at least for the moment!

* Some changes in the code to make temporary files more secure

* a few other minor bug fixes

The new iso in the above URL will probably be moved to the "official" download link soon, assuming that testing by users does not show any major issues.

Please do test it out!

---

### Post by zmjjmz on 2008-09-13
Cool; downloading it now.

---

### Post by Tux Aubrey on 2008-10-06
Just a note to advise all the console fans that INX version 1.0 is ready.

See the announcement and download links on launchpad at [https://launchpad.net/inx/+announcements](https://launchpad.net/inx/+announcements)

For the curious:
> 
 INX is a "Live CD" distribution of GNU/Linux, derived from
 Ubuntu 8.04.1 LTS, but using "ubuntu-minimal" and "ubuntu-standard"
 as a base. It is console only, without any graphical "X" programs.

 INX is intended as a "tutorial" and introduction to the Bash
 command line, but is a fully capable, portable GNU/Linux system in
 its own right. It has a collection of easy-to-use menus, colour
 themes, easy configuration tools, music (and video on the frame buffer),
 some games, and several surprises for those who are not aware of
 what can be done in a console/tty.

A great way to get to grips with using the command line - and it runs just fine in a virtual machine.

---

### Post by zmjjmz on 2008-10-06
I installed it on one of my old computers.
See blog for more info.

---

### Post by wolfen69 on 2008-10-07
[Here]("http://inx.maincontent.net/inx-1.0.iso.torrent") is the torrent file. will seed for as long as possible. keep up the good work.

---

### Post by fistfullofroses on 2008-10-07
I have been working on a similar distribution, though without the Debian/Ubuntu base. I will download your liveCD as soon as I am on a non-restricted network ;)

---

### Post by sertse on 2008-10-08
<3 INX.

and its really for than just a series of "how to use the command line" tutes. 

The included apps cover most of what one needs for general, if basic computer usage. A good "has all you need" OS solution if you're going console only if there was one. Hopefully the inxtaller will get better in the future!

---

### Post by kill4killin on 2008-10-08
/Subscribe

I saw that there was a post on digg today about this and started googling for some information that would show up about it here in my office (websense can be a pain in the butt soemtimes, it thinks the INX site is "sexually explicite content", but I digress) and I ended up here ironically enough.

I'm very interested in this project. I too was working for a while on doing something just like this, stripping down ubuntu to just a cli OS and trying to minimize the RAM usage and install footprint. I was able to get it to install on just slightly larger an install then than Ubuntu Server's 500MB and it was capable of running on just over 32MB of RAM in my virtual machine. I'll have to try to package the project and send it off to some of you guys to see if it can maybe help improve this project at all or maybe vis-versa.

I'll be getting on the freenode #INX irc as soon as I get back to my desk (around noon EST). I can't wait to talk to you guys, I look forward to testing this out as well and helping improve it anyway I can.

:guitar:

> **fistfullofroses said:**
> I have been working on a similar distribution, though without the Debian/Ubuntu base. I will download your liveCD as soon as I am on a non-restricted network ;)

P.S. FistFullofRoses: I'm in the Atlanta area as well, we should work on a project together sometime!

---

### Post by fistfullofroses on 2008-10-08
Sure thing. Hit me up via Email [email]fistfullofroses@gmail.com[/email]

---

### Post by Tux Aubrey on 2008-10-08
Coverage on Digg for INX ([http://digg.com/linux_unix/Look_Ma_No_X](http://digg.com/linux_unix/Look_Ma_No_X))

Looks like a lot of people are upset by the idea!  How sweet!

(I'm not an INX dev BTW, just an interested by-stander and a witness for the defence)

---

### Post by Jim! on 2008-10-09
> **Tux Aubrey said:**
> Coverage on Digg for INX ([http://digg.com/linux_unix/Look_Ma_No_X](http://digg.com/linux_unix/Look_Ma_No_X))

Looks like a lot of people are upset by the idea!  How sweet!

(I'm not an INX dev BTW, just an interested by-stander and a witness for the defence)

Yeah I saw the digg article today as well I think I'll give this one a try in the near future, after I try Arch Linux of course.

---

### Post by Tom Morris on 2008-10-11
This looks pretty awesome. Not something I really would use, but very cool nonetheless. Plus the Digg thread is a hilarious train wreck of stupid.

---

### Post by sertse on 2008-11-07
Topping this thread, with a few nice tricks to tell you all. =)

[SIZE="3"]**_Installing INX (and keep your partitions/other distros)_**[/SIZE]

For those who don't want to wipe out their whole hard disk to install INX, Ubiquity (Ubuntu's standard installer) works fine. Though this means switch to X to install (sacrilege!) it works, with all the same options (recognising partitions, other distros..) as you had when installing Ubuntu.

[SIZE="3"]**_Run INX alongside Ubuntu (i.e Ubuntu+INX)_**[/SIZE]

Going further, it's possible to install (fresh install, unfortunately there no easy way of putting INX in an existing Ubuntu) the complete Ubuntu desktop on top of INX; INX, in a way "is" Ubuntu CLI with INX being a CLI "desktop environment" to it. 

Just install the rest of Ubuntu "apt-get install ubuntu-desktop" and reboot...,Viola! you have the Ubuntu you all know and love, *and* INX. To assess INX, just go a console/tty (Alt+Ctrl+F[1-6]) and login. Alt+Ctrl+F7, switches you back to Ubuntu (and X) again. This allows you to run both Ubuntu and INX natively and simultaneously if you want. INX uses Ubuntu 8.04. 

It is theoretically *possible* after to upgrade from 8.04 to 8.10 just like any other Ubuntu system, but you do so at your own risk. My experience of it has either had some part of Ubuntu or INX not working after the upgrade, whereas 8.04 works perfectly fine.

[SIZE="3"]**_Issues and Troubleshooting_**[/SIZE]

**1. My resolution in INX is all messed up! Nothing fits to the screen!**

Edit your menu.lst (sudo jed boot/grub/menu.lst) and in "defoptions" add "vga=###". Reboot. See this post for what number to use for your resolution: [http://ubuntuforums.org/showpost.php?p=1528638&postcount=2](http://ubuntuforums.org/showpost.php?p=1528638&postcount=2)

**2. The mouse in xlinks2 is jerky and not smooth like the live cd!**

Edit rc.local (sudo jed etc/rc.local) and add this:

"chmod 666 /dev/tty0"

Reboot. 

**3. Network Issues**

If you were using INX to download Ubuntu, you might find Ubuntu's Network Manager isn't working. This is particularly the case with wireless where you probably used "Ceni" in INX to set it up. If it works you can allow just allow Ceni from INX to manage your connection, but if you need/want Network Manager, switch into INX, go to Ceni and tell Ceni to remove configuration. Go to Ubuntu and/or reboot. Network anager should work now.

Many thanks to the inx-one and other inx fans for the advice given in this thread. Credit goes to them.

---

