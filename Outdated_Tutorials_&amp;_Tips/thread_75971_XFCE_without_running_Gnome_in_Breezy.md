---
title: "XFCE without running Gnome in Breezy"
date: 2005-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by SFN on 2005-10-14
I did this HOWTO for Hoary originally. People seemed to like it. Since that time, Breezy has been releasesd, a couple of minor proceduress have changed and I've learned some things so I figured I'd re-write it.

I've seen posts about getting down to XFCE4 after install but what I wanted was just XFCE4 from the start. Nothing else. I found a site in French that had the info I needed so I thought I'd redo it for you all here.

This is for an x86 install. If you are installing on a PPC system, this may not work for you. Actually, it may not work on an x86 system either. It all depends on your hardware. 
 
Boot with the CD inserted. At the initial prompt, type "server" and press enter. This will get you your bare (or bare-ish) install. Once the install is complete and you are logged in, change your sources.list to include the universe and multiverse repos. To do that, do

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

then

```
sudo nano /etc/apt/sources.list
```

Replace everything in the file with the following lines

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free license. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse


Do a "Ctrl-X" and press &#8220;Y&#8221; to save the edited file

Do

```
sudo apt-get update
```

then

```
sudo apt-get dist-upgrade
```

Once that is done, do

```
sudo apt-get install xubuntu-desktop gdm
```

Now reboot. When you see the Ubuntu login screen, login.

Once you are in, one thing you should do right off the bat is get ivman working. This will allow your USB drives and other hotplug items to automount.

Open the XFCE menu, by clicking the button on the far left of the iconbar. Click 'Run Program...' and type 'ivman &'. Then click the "Run" button. Now, open the XFCE menu again and choose "Quit". Make sure that the radio button next to "Quit current session" and the checkbox next to "Save session for future logins are both checked. Click the "OK" button.

Once you are logged out, you can log back in.

(NOTE: It would appear that ivman is dying every so often at random. If you plug in a USB drive and it does not automount, just run "ivman" from the "Run Program" menu item like you did initially. Once I get this fixed, I'll update these instructions.)

If you find that your computer hangs on shut downs or reboots, you MAY be able to resolve this issue editing  grub&#8217;s menu.lst. In the terminal, do:

```
sudo nano /boot/grub/menu.lst
```

Find the section that starts with ## ## Start Default Options ##. In that section you will see a line that starts with # kopt=root=". Do not uncomment that line. Just add "nolapic" to the end of that line. Save the file by doing &#8220;Ctrl-X&#8221; and press &#8220;Y&#8221; to save the changes and do

```
sudo dpkg-reconfigure linux-image-*version*
```
(NOTE: Replace *version* with the actual version number of your kernel.)

Reboot or shut down and you MAY find that your problem is gone.

(NOTE: I am discovering that this also solves a problem I was having with usplash not working. I don't know why this would fix it and I can't guarantee that it would fix it for you.)

What you now have is a somewhat bare Ubuntu install with only XFCE4 as your desktop with a couple of goodies added just to make you experience easier. You can find other items you might want by searching through Synaptic. 

Enjoy!

---

### Post by poofyhairguy on 2005-10-14
I suggest a few more changes. Instead of apt-getting XFCE4, advise people to install the 

xubuntu-desktop


pacakge instead.

---

### Post by SFN on 2005-10-14
Yeah, I just found out about that after this afternoon after I wrote that.

To be honest, I'm kind of wondering if this is even relevant with Xubuntu being a planned project now.

Thoughts, anyone?

---

### Post by telmo on 2005-10-14
I want xubuntu! Enough said! :KS

---

### Post by poofyhairguy on 2005-10-14
[QUOTE=SFN]Yeah, I just found out about that after this afternoon after I wrote that.

To be honest, I'm kind of wondering if this is even relevant with Xubuntu being a planned project now.

Thoughts, anyone?[/QUOTE]


Until the ISOs are made this is needed.

---

### Post by SFN on 2005-10-15
Here's a question. I haven't tried the xubuntu-desktop method as I'm in the middle of something else. What is the display manager used? The package doesn't show one so if we install this way, do we just get the console login prompt?

---

### Post by mctavish on 2005-10-15
no display manager. xdm is a little broken according to the xubuntu mailing list.

Also, there are likely to be a few rough edges on xubuntu, it seems they didn't get as much done as they ideally wanted to before universe was frozen. Automounting is an example of that. It didn't make it.

Don't let that stop anyone from trying it though. If you want to see an xfce4 based desktop, the best thing to do is try it out, give feedback if things aren't quite working and generally get the momentum up on the whole thing.

I'd love to see it really smooth for Dapper.

---

### Post by SFN on 2005-10-15
Well, I'm trying the method shown above right now. Right off the bat it looks like a ton of fonts are being installed. Most of them, I'll never use. I guess that's part of making a nicely rounded distro for everyone, which is cool.

---

### Post by SFN on 2005-10-15
Automounting is now working. Instructions updated.

---

### Post by jogi on 2005-10-15
hi sfn

thx for your tutorial!
so far i have installed the default ubuntu 5.10 base system and changed to xfce
now i don't really want to use gnome anymore, is there a way to safely remove gnome or at least some parts? i think there might be dependency problems, but
do you have any suggestions?

---

### Post by SFN on 2005-10-15
Glad it worked for you.

You can definitely remove Gnome but which parts can be removed can get tricky. Somebody else would be better qualified to tell you how to do that.

Plus (and this is just my opinion) there always seem to be tasks that are a real pain without Gnome. You're working along just fine in XFCE (or Fluxbox or WindowMaker or whatever) and you try to do something and realize that the only way you know how to do it is through some Gnome (or KDE) interface. Sure, you can learn how to do it from the command line but three or four sessions of how to do some relatively insignificant task without a Gnome GUI can irritate some people rather harshly.

Personally, I would leave Gnome on. The only reason I make use of the info in this tutorial is I'm playing with making a bootable CD that's fairly small and is heavily customized. For my regular desktop at home, I haven Gnome and XFCE and Elgihtenment installed. Mainly though, I use Gnome.

Soprry, I can't give you a better answer.

---

### Post by Cynos on 2005-10-15
I just did apt-get remove gnome

---

### Post by SFN on 2005-10-15
That's interesting. As I said, I'm running Gnome. Looking in Synaptic, it would appear that the package titled "gnome" isn't even installed.

---

### Post by reet on 2005-10-15
Thanks for this tutorial in installing XFCE without gnome. This has allowed me to install only the essentials on my computer, and not have to sift through Synaptic for an hour after installation is complete to remove all the extra garbage that was installed that I don't need.

I noticed that in your tutorial you manually installed synaptic and firefox. I noticed that both these programs were already installed when I rebooted to a graphical interface.

---

### Post by SFN on 2005-10-15
[QUOTE=reet]I noticed that both these programs were already installed when I rebooted to a graphical interface.[/QUOTE]

You're right. Looking at the xubuntu-desktop package, it looks like it installs synaptic and firefox. I'll update the instructions.

Thanks for catching that.

---

### Post by jogi on 2005-10-16
> That's interesting. As I said, I'm running Gnome. Looking in Synaptic, it would appear that the package titled "gnome" isn't even installed.

yes strange, isn't it?

when i want to remove this package i get:

Package gnome is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

maybe i can uninstall gnome by removing separately every package it uses except the ones that are important, such as libs :)

---

### Post by angrykeyboarder on 2005-10-16
[quote=SFN]Yeah, I just found out about that after this afternoon after I wrote that.

To be honest, I'm kind of wondering if this is even relevant with Xubuntu being a planned project now.

Thoughts, anyone?[/quote]

For the time being I'd say it's relevant.  I don't think Xubuntu is that well known yet.

I saw you modified you post after seeing the reply.  Frankly either way I don't think "x-winow-system-core" is necessary.  XFCE4 or xubuntu-desktop is going to require it anyway, so it will be installed.

APT at it's best. ;-)

I'm a lazy typist, what can I say?

---

### Post by SFN on 2005-10-16
> **angrykeyboarder]I saw you modified you post after seeing the reply.  Frankly either way I don't think "x-winow-system-core" is necessary.  XFCE4 or xubuntu-desktop is going to require it anyway, so it will be installed.

APT at it's best.  said:**
> 


So it is. I've updated the instructions. That sure makes for a clean and quick install. One could say it's almost..."breezy"!

[QUOTE=angrykeyboarder]I'm a lazy typist, what can I say?

Tell me about it. The whole reason x-window-system-core and synaptic and firefox were still in there is because I copied and pasted my original HOWTO.

I need to attend an "Attention to Detail" seminar.

---

### Post by SFN on 2005-10-17
Here's something I could use some help with.

In the instructions, you will see this:

> (NOTE: It would appear that ivman is dying every so often at random. If you plug in a USB drive and it does not automount, just run "ivman" from the "Run Program" menu item like you did initially. Once I get this fixed, I'll update these instructions.)

It turns out that ivman is just not starting back up after reboot. I've tried creating a startup script and placing it in /etc/init.d but that doesn't work. Not even when running that script by hand using "sudo /etc/init.d/ivman". I did find some instructions on the ivman page that say to edit IvmConfigBase.xml so that the value of "fork" is set to "true" if you are starting ivman at boot. Unfortunately, that setting makes no difference one way or the other.

Ideally, I'd like to start ivman at boot but just starting it upon login would be fine too. Anybody have any ideas?

I should add, if I replace "ivman &" with "gnome-volume-manager &" in the original instructions, gnome-volume-manager starts up upon reboot without issue. Perhaps that's the way to go here, for the time being.

---

### Post by darius_underhill on 2005-10-17
I have a question, I saw in one the the screenshots of Zenwalk [Screenshot]("http://www.zenwalk.org/images/desktop.jpg")

And it seems that the taskbar is on the right part of the screen.  I can seem to do that in XFCE in ubuntu.  Can anyone help???  Thanks

---

### Post by SFN on 2005-10-18
[QUOTE=darius_underhill]I have a question, I saw in one the the screenshots of Zenwalk [Screenshot]("http://www.zenwalk.org/images/desktop.jpg")

And it seems that the taskbar is on the right part of the screen.  I can seem to do that in XFCE in ubuntu.  Can anyone help???  Thanks[/QUOTE]

Well, that's interesting. That's not the task bar. That's what Xfce calls the iconbox. It's an alternative to the taskbar. All that should show is apps that are currently active. However, that screen shot shows many more apps than the ones that appear to be currently active.

I suppose those could be apps that are minimized but running 12 apps, then minimizing 10 of them and showing the iconbox is rather misleading.

At any rate, if you would like to run the iconbox instead of (or even in addition to) the taskbar, just click the Xfce Menu button and choose "Run Program...". In teh box that opens up, type "xfce4-iconbox".

If you want the iconbox to run on startup, make sure it's running then click the Xfce Menu button and choose "Quit". Make sure that the radio button next to "Quit current session" and the checkbox next to "Save session for future logins" are both checked, then click the OK button. Once you log back in, the iconbox should be running.

---

### Post by Kelvin on 2005-10-20
Hi,

Thanks for the How-To. xfce4 on top of a minimal install is just what I'm looking for.

I've got trouble though, and am hoping someone can give me a few hints. I've gone clear through the install. Now, boot up happens and I'm left with a blank screen with an underscore cursor in the upper left corner. Nothing happens from there.

Reboot using Linux single and tried startxfce4, same result. :( 

I'm trying to use this install on a 366MHz clamshell iBook, 256 Ram.

Any ideas? I'd be grateful.

---

### Post by poofyhairguy on 2005-10-20
[QUOTE=Kelvin]Hi,

Thanks for the How-To. xfce4 on top of a minimal install is just what I'm looking for.

I've got trouble though, and am hoping someone can give me a few hints. I've gone clear through the install. Now, boot up happens and I'm left with a blank screen with an underscore cursor in the upper left corner. Nothing happens from there.

Reboot using Linux single and tried startxfce4, same result. :( 

I'm trying to use this install on a 366MHz clamshell iBook, 256 Ram.

Any ideas? I'd be grateful.[/QUOTE]


XFCE works on my clamshell iBook, but I have the whole ubuntu-desktop installed.

---

### Post by jogi on 2005-10-20
hi sfn and co

do you have by chance problems when you move or resize windows in xfce?
my cpu utilization goes through the roof and i have already tried a lot
unfortunately this really sucks :)
i know that this has been already discussed a lot, but i want to know if you guys have the same problem like me having used this kind of installation

---

### Post by Kelvin on 2005-10-20
> 
XFCE works on my clamshell iBook, but I have the whole ubuntu-desktop installed.

Thanks Poofyhairguy! Did you leave the Gnome desktop on or strip it out? I can run the whole Enlightened Gnome pairing well, but was looking for something lighter.

I've since tried building my own, and have always come up to this same blockage, whether using GDM, WDM, or XDM.

What other setups have worked for you on your clamshell? 

Thanks again!

---

### Post by SFN on 2005-10-20
[QUOTE=jogi]hi sfn and co

do you have by chance problems when you move or resize windows in xfce?
my cpu utilization goes through the roof and i have already tried a lot
unfortunately this really sucks :)
i know that this has been already discussed a lot, but i want to know if you guys have the same problem like me having used this kind of installation[/QUOTE]

I don't have this problem at all.

This is just a stab in the dark but have you added anything on top of this install? A processor-specific kernel, perhaps?

Basically, I'm just trying to see if there is anything other than the basic install detailed here.

---

### Post by jogi on 2005-10-22
hi sfn

i downloaded the ubuntu 5.10 breezy badger install cd, put it in the cd rom drive and installed it right away
after the quick and flawless installation i followed your instructions in your tutorial
so far so good
then i changed from gnome to xfce, but in gnome and xfce i got the same problems. the cpu is really busy redrawing windows when you move them (cpu utilization 70% or more)
i didn't install something kernel specific on my own, but i did look for some misconfigurations in the kernel config, but so far i haven't found anything
yes, and i tried installing ubuntu 5.10 on another computer and even one at school (64 bit machine with 2 gb ram and a good graphic card), but i got the same result
the graphic user interface was slow and the cpu has to do the work the graphic card should do

today it was too much, out of the blue i installed debian and xfce, and guess what?
everything seems to work in order, the gui nice and fine working properly

i really like ubuntu, but such things really make me change the distribution

hm

---

### Post by SFN on 2005-10-23
[QUOTE=jogi]i tried installing ubuntu 5.10 on another computer and even one at school (64 bit machine with 2 gb ram and a good graphic card), but i got the same result the graphic user interface was slow and the cpu has to do the work the graphic card should do

today it was too much, out of the blue i installed debian and xfce, and guess what? everything seems to work in order, the gui nice and fine working properly
[/QUOTE]

Wow. Well, on one hand, I wish I could tell you why that happened. On the other hand, great news that its working for you.

Hope you're enjoying it.

---

### Post by gidycz on 2005-10-24
First: XFCE is exactly what I was looking for and it brought my old powermac back to life.

BUT, it seems that Red and Blue are switched in XFCE.  There was no problem in the Mac OS before I installed Linux, so I don't think it's a hardware problem.  Anyone have any ideas?

---

### Post by SFN on 2005-10-25
[QUOTE=gidycz]First: XFCE is exactly what I was looking for and it brought my old powermac back to life.

BUT, it seems that Red and Blue are switched in XFCE.  There was no problem in the Mac OS before I installed Linux, so I don't think it's a hardware problem.  Anyone have any ideas?[/QUOTE]

I've done this on a number of different machines but haven't seen this result yet. It does seem odd that it wasn't a problem with the MAC OS. Are that and XFCE the only operating systems you've tried on this particular computer?

One other suggestion. It seems like the wrong way to solve this but have you tried adjusting the gamma correction?

Click the Settings on the toolbar. Click Display. You will see sliders there for gamma correction.

Hope this helps.

---

### Post by DariusTriplet on 2005-10-25
I installed xubuntu-desktop today, and love it, except for a minor issue:  The panel at the bottom has disappeared.  I don't quite recall what I was doing - IIRC, nothing extraordinary, and hadn't edited anything at all - yet I've lost the panel.

Does anyone know how to get it back, and any ideas as to what happened to it?

---

### Post by SFN on 2005-10-26
[QUOTE=DariusTriplet]I installed xubuntu-desktop today, and love it, except for a minor issue:  The panel at the bottom has disappeared.  I don't quite recall what I was doing - IIRC, nothing extraordinary, and hadn't edited anything at all - yet I've lost the panel.

Does anyone know how to get it back, and any ideas as to what happened to it?[/QUOTE]

Ihad the exact same thing happen ont he first day I installed it. I wasn't doing anything either. It just vanished. I tried off and on all day to get it back, including a dpkg-reconfigure of xubuntu-desktop. Nothing.

Finally, out of frustration, I reinstalled everything. It's been fine ever since.

Terrible answer, I know but it's the only one I have.

---

### Post by celluloid on 2005-10-27
did you try 'xfce4-panel&' in the run program box? this has happened to me before and I did that then rebooted/logged in/out with save session ticked and it was back.

---

### Post by SFN on 2005-10-27
I did that and no dice but we could be talking about two separate issues so it's certainly worth a try.

---

### Post by Kyral on 2005-10-27
The panel thing is tricky. If you save your session while the panel is gone you are gonna have to make a new session to restore it. I generally first get my session running the way I want (Stuff starting up, etc), save it, then uncheck the "Save Session at Logout" box :D

And I only switched last night. XFCE + Compositing is ***nice***. And runs with the same amount of resources as GNOME + Metacity w/o compositing

---

### Post by kairu0 on 2005-10-27
I add a taskbar to the bottom panel, kill the top panel, then save my session.

This reduces resources and saves screen real estate.

---

### Post by ubnoobie on 2005-10-30
cool! i didn't even notice xubuntu  :)   i have been looking for a xfce4-based distribution all weekend for a friends old 333 mhz system.. ubuntu's default install is painful on it (160mb ram, old 4 gig hd)..

i have an ugly love-hate relationship with xfce4.. LOVE it's speed, love it's layout (which i mimic the best i can with gnome), and absolutely HATE xffm.. 

what i'd really like to see though, is nautilus integrated into xfce4.. not rox. which isn't much better than xffm. and yes, it can be done. see [www.cobind.com](www.cobind.com) (no activity with the distro since summer 04). cobind's entire package set was ideal for "marginal" systems that aren't quite up to taking on a gnome or kde based system.  if you like xfce4, you need to at least toss cobind on a spare/test machine for a bit to see what it was.

if xfce4 hadn't been dropped from fedora 4 (what _were_ they thinking), my old k6/2 would probably still have cobind on it (was based on fc1). i did have a sarge-based xfce4 system on it for a bit, but i could never get it "just right".. so i went to an even lighter weight micro distribution in popcorn slax. but i really miss apt on that system (slax is slackware based).

---

### Post by gidycz on 2005-11-06
[QUOTE=SFN]Are that and XFCE the only operating systems you've tried on this particular computer?

One other suggestion. It seems like the wrong way to solve this but have you tried adjusting the gamma correction?

Click the Settings on the toolbar. Click Display. You will see sliders there for gamma correction.

Hope this helps.[/QUOTE]

I was originally running gnome, too.  That had no problem with the colors, either. (but was so slow I couldn't run it)

  I'm sure it's not a gamma issue, or a monitor settings issue.  Red and blue are actually reversed.  Any ideas?

---

### Post by SFN on 2005-11-08
[QUOTE=gidycz]Red and blue are actually reversed.  Any ideas?[/QUOTE]

Wow. Not a clue, here. That's just plain odd.

Sorry I can't be of more help.

---

### Post by conor on 2005-11-12
I have been trying all day to install xubuntu but I am too much of a newbie to get it right.  Here are a few methods I tried:

1) Install xubuntu-desktop on top of my Kubunu install then removed kde files.  (At restart this brought me to a login command line and said that there were no other display managers installed)

2) Tried to install xubunutu-desktop on a server install (Couldn't load ndisdriver [modprobe] after installing the .inf for some reason, thus couldn't install anything from an online repository.)  

3) Now I am going to try to install xubuntu-desktop over a full Ubuntu install.  I am not going to remove any gnome files until I know what went wrong the first time. 

Any idea what I could have done wrong?

---

### Post by SFN on 2005-11-12
[QUOTE=conor]I have been trying all day to install xubuntu but I am too much of a newbie to get it right.  Here are a few methods I tried:

1) Install xubuntu-desktop on top of my Kubunu install then removed kde files.  (At restart this brought me to a login command line and said that there were no other display managers installed)

2) Tried to install xubunutu-desktop on a server install (Couldn't load ndisdriver [modprobe] after installing the .inf for some reason, thus couldn't install anything from an online repository.)  

3) Now I am going to try to install xubuntu-desktop over a full Ubuntu install.  I am not going to remove any gnome files until I know what went wrong the first time. 

Any idea what I could have done wrong?[/QUOTE]

Never done Kubuntu at all so I couldn't help you there.

I've only seen the problem with the ndisdriver once before. That was caused by a bad ISO. If xubuntu on top of a gnome install also doesn't work, I'd take a look at the burnt ISO.

---

### Post by marksi on 2005-11-12
[QUOTE=conor]I have been trying all day to install xubuntu but I am too much of a newbie to get it right.  Here are a few methods I tried:

1) Install xubuntu-desktop on top of my Kubunu install then removed kde files.  (At restart this brought me to a login command line and said that there were no other display managers installed)

2) Tried to install xubunutu-desktop on a server install (Couldn't load ndisdriver [modprobe] after installing the .inf for some reason, thus couldn't install anything from an online repository.)  

3) Now I am going to try to install xubuntu-desktop over a full Ubuntu install.  I am not going to remove any gnome files until I know what went wrong the first time. 

Any idea what I could have done wrong?[/QUOTE]

You don't need a display manager to run xubuntu. Just login on the command line and startx

---

### Post by conor on 2005-11-13
So the install ove ubuntu worked.  And I have realized alot of my flaws.  The problem with the modprobe: I had two instances of bcmwl5.inf but one I had accidently renamed bcmwl5.sys (using cp I changed the destination but I forgot to change the source.)  And I am assuming that when I removed the kubuntu files nothing was wrong and I just didn't know how to launch xfce at the command line.  It is just "```
sudo startx
```" then?

---

### Post by Biased turkey on 2005-11-13
[QUOTE=conor]So the install ove ubuntu worked.  And I have realized alot of my flaws.  The problem with the modprobe: I had two instances of bcmwl5.inf but one I had accidently renamed bcmwl5.sys (using cp I changed the destination but I forgot to change the source.)  And I am assuming that when I removed the kubuntu files nothing was wrong and I just didn't know how to launch xfce at the command line.  It is just "```
sudo startx
```" then?[/QUOTE]

the command to start xfce is: startxfce4

---

### Post by conor on 2005-11-13
[QUOTE=Biased turkey]the command to start xfce is: startxfce4[/QUOTE]

Hmm, this works for me, mostly.  When I try to load xfce4 without using sudo then it tells me I do not have permission.  When I load it using sudo then it logs me in a root and it is a pain to run sensitive programs (like gtk-gnutella) which do not like being run as a super user.  How can I get past the permission setting, or how do I change them?

---

### Post by MJRehrig on 2005-11-27
I installed xubuntu-desktop on top of a server install and when I so startx or startxfce4, the screen just goes blank.  I have tryed reconfiguring the display (dont remember what the command was).  Do I need to install anything else?  On the debian install that I previously had on this computer, I had xconf installed and that usually did the trick as to configuring the X server, but I can't find xconf anywhere anymore.  Do you know where to get it?

Thanks for any help!

---

### Post by videodrome on 2005-11-30
My older ATI card (no drivers needed other than those that come with X11. Rage Mobility P/M) just worked out of the box in the standard Gnome Breezy install. 

With a server+xubuntu install, nothing I do will make the card work. Black screen despite every xorg.conf change I've made. Only thing'll work is VESA. Yuck.

What is not installed in the xubuntu server install that IS install with the full ubuntu install pertaining to an old ati video card ?

Loomis

---

### Post by SFN on 2005-11-30
[QUOTE=videodrome]What is not installed in the xubuntu server install that IS install with the full ubuntu install pertaining to an old ati video card ?[/QUOTE]

That's a good question. I just checked the differences between xubuntu-desktop and ubuntu-desktop. Although there are differences to be sure, there doesn't seem to be anything that's glaringly obvious in the way of video drivers. There are no ATI packages in ubuntu-deskop.

Perhaps someone who knows more about Xubuntu and specifically it's interaction with ATI can address that.

Having said that, I was just speaking with a co-worker who was having trouble with his ATI Rage Express X200. Sounds like the same trouble only he was having it with Ubunutu instead of Xubuntu. He ended up using the VESA driver, then going in and editing his xorg.conf by hand using refresh and sync rates he got from his monitor manufacturer. Once that was done, he was able to boot into Ubuntu using the ATI driver but at 640x480. After that, he was able to run ATI's script - which was failing earlier because it was unable to detect the monitor. Once that script ran, everything worked.

I'm not remotely suggesting that as a solution. Nobody should have to do that. I'm more wondering why it wasn't working for him in Ubuntu followed closely by why yours IS working in Ubuntu and leading to why yours ISN'T working in Xubuntu. Could just be the difference in cards - your older, his newer - but I'd put money down that his solution would work for you. Again, not suggesting you do that but it would sure be interesting to see if that worked.

---

### Post by SFN on 2005-11-30
[QUOTE=MJRehrig]I have tryed reconfiguring the display (dont remember what the command was)[/QUOTE].
```
sudo dpkg-reconfigure xserver-xorg
```
[QUOTE=MJRehrig]On the debian install that I previously had on this computer, I had xconf installed and that usually did the trick as to configuring the X server, but I can't find xconf anywhere anymore.  Do you know where to get it?[/QUOTE]
Is that a package named xconf? I was just searching through Debian packages and I don't see xconf anywhere.

If you mean the config file, it's at /etc/x11/xorg.conf.

---

### Post by videodrome on 2005-12-01
I figured it out after messing with it for a week and pulling some of my hair out!

Hopefully this will work in all the older ATI cards.

This will be a quick reply until I type out a longer FYI howto thread sometime in the near future.

Working on my ATI Rage Mobilty 8mb P/M card in a Dell Inspiron 5000 laptop (Pentium 3 500) 

Ubuntu server install (no Gnome) + Xubuntu.

No modelines or modes are needed!

1400x1050 @ 24bit

_______________________________

1) Add VGA=795 to the end of the kernel line in Grub

2) xorg.conf:

Device 
Id - ati rage mobility p/m
driver - ati
busid - pci:1:0:0
videoram - 8192

Monitor
id - ITSX93
option - DPMS
horizsync - 30-100
vertrefresh - 50-100

screen
id - default
device - ati rage mobility p/m
monitor - ITSX93
depth - 24
subsection display
depth 24
modes 1400x1050

__________________________________

After some tweaks with BUM, it boots in less than a minute and a half, with only 128mb of ram currently installed. Runs super fast and looks great! 

Thanks!
Loomis

---

### Post by Onos on 2006-01-08
I hope that I am not derailing the topic too much:

I recently installed Ubuntu + Xfce4 and did some small bit of hacking about with Firefox 1.5 to get it to work.

Turns out that I needed to remove FireFox 1.07 in its entirety to make this happen - this in turn, forced a removal of xubuntu-desktop.

I cringed at this a bit, but the Synaptic package manger said this:

**Xubuntu desktop system**
______________________________________________________________________
This package depends on all of the packages in the Xubuntu desktop system

It is safe to remove this package if some of the desktop system packages are
not desired.
______________________________________________________________________

So, I went ahead and had it removed along with FireFox 1.07...

When I logged back in, my desktop settings were not coming up, specifically, my desktop background picture, and the context-sensitive menu when I right-click on the desktop was no more.

This is a minor annoyance compared to the hair-pulling of getting FireFox 1.5 to work nicely, but even after re-installing the xubuntu-desktop package, I still am unable to set my desktop background, and have no context menu when right clicking the desktop area.

Has anyone else come accross this yet? If so, is there any hack or other fix to get it to work right again?

Something tells me that I need to go hack some config file or change a symbolic link somewhere, but I haven't a clue as to how to do that. :confused:

---

### Post by Onos on 2006-01-08
A wee bit more digging around turns up this helpful link:

[http://ubuntuforums.org/showpost.php?p=556666&postcount=62](http://ubuntuforums.org/showpost.php?p=556666&postcount=62)

Here, Sapo suggest to another member having a similar problem to

**...press Alt + F2 and type:[FONT="Courier New"] xfdesktop[/FONT]**

Thanks!

---

### Post by rpm1200 on 2006-04-28
[QUOTE=videodrome]I figured it out after messing with it for a week and pulling some of my hair out!

Hopefully this will work in all the older ATI cards.

This will be a quick reply until I type out a longer FYI howto thread sometime in the near future.

Working on my ATI Rage Mobilty 8mb P/M card in a Dell Inspiron 5000 laptop (Pentium 3 500) 

Ubuntu server install (no Gnome) + Xubuntu.

[snip][/QUOTE]
I am experiencing a similar problem on my iMac rev B - I followed the steps in the [wiki]("https://wiki.ubuntu.com/InstallingXubuntu") to install Xubuntu/Breezy... I completed the server install then had a failure during the xubuntu-desktop install (the screensaver did not install), so I ran sudo apt-get -f install and that seemed to complete the xubuntu-desktop install.  Now when I run startxfce4 an error message flashes up really quickly then the screen clears and I get a blank screen with blinking cursor forever.  I could not read the whole error message but I noticed something about a log file - any idea what directory the log file is saved to?  
Since the iMac uses an ATI Rage Pro chipset I'll definitely try videodrome's steps....

---

### Post by rpm1200 on 2006-04-28
Got it now... 
Had to run sudo dpkg-reconfigure xserver-xorg.  After setting up the ATI card there, I got it to the point where it would not bomb out anymore when running startxfce4, but the monitor would go into standby mode and never come out.  After a quick google search I found out that you have to set the monitor to 60 horizontal (fixed) or it will never work.  In dpkg-reconfigure xserver-xorg I autodetected the monitor, which correctly identified the supported resolutions of 640x480, 800x600 and 1024x768.  Then I chose advanced mode, set the horizontal frequency to 60 and the vertical frequency to 75-117.  Voila, now it works and I am posting this from Firefox running in Xubuntu!

---

