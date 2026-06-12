---
title: "LoL! Unity is gone, but GNOME Classic now works. Hello?!?!?"
date: 2011-08-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-08-10
Heh!  Gotta love these alphas.

I just did a massive update, and...

Unity has vanished, but...

GNOME Classic is now working fine (as I type).

Oh, well, guess I'll run GNOME Classic for a while...  :D

---

### Post by nomko on 2011-08-10
Be happy that Unity is gone! Now your desktop looks like a normal desktop and not like some overvalued netbook...

---

### Post by VinDSL on 2011-08-10
> **nomko said:**
> Be happy that Unity is gone!
Yes, I see it now.  I should be happy.  It's a godsend!

This is how the gray hairs envision Ubu 11.10, yes?  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-08-10 01:23:20(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-08-10 01:23:20.png")[/INDENT]


Just like 1995!  LoL!

---

### Post by el_koraco on 2011-08-10
Gnome 3 fallback mode. The worst thing to happen to Linux since 1995.

---

### Post by mc4man on 2011-08-10
There appears to be some possible issues with the new gnome-session & a unity login - Gs is ok
(2 Ubuntu choices in login, other poor & inconsistent behavior

Finally got sick of it and reverted for the moment

---

### Post by VinDSL on 2011-08-10
Volume control works in the indicator panel.

Hrm...

Wonder why can't they make it work in Unity?

---

### Post by mc4man on 2011-08-10
> **VinDSL said:**
> Volume control 
Wonder why can't they make it work in Unity?
Has always and still works fine. - the mouse-over - scroll on indicator was broken for some time, that was recently fixed and is also ok now.

---

### Post by redkiwi on 2011-08-10
Unity 2D is working ;)

---

### Post by lucazade on 2011-08-10
> **mc4man said:**
> Has always and still works fine. - the mouse-over - scroll on indicator was broken for some time, that was recently fixed and is also ok now.

I can confirm. Events on indicators have been enhanced and fixed in the latest days, now it accept mouse wheel and middle click (probably used for mute)

---

### Post by walt.smith1960 on 2011-08-10
Gnome Shell is working pretty well for me too. Just Unity (3D) seems to be broken for the moment.

---

### Post by redkiwi on 2011-08-10
I think a new version comes soon, because a lot of stuff gets merged...

[https://code.launchpad.net/~unity-team/unity/trunk](https://code.launchpad.net/~unity-team/unity/trunk)


Volume control...
Scrolling is working, but mouseklicks on the slider is still broken :sad:

---

### Post by VinDSL on 2011-08-10
> **redkiwi said:**
> Volume control...
Scrolling is working, but **[COLOR="Red"]mouseklicks on the slider[/COLOR]** is still broken :sad:
Yep, that's what I'm (still) experiencing.  And, when I click the slider, it freezes everything for 5-10 seconds - on this machine, and others.

I was testing the latest daily build (8-Aug) earlier tonight, and it was doing the same thing.

Anyway, I got tired of GNOME Classic, so called, and installed Ubu 2D.

At least, this is tolerable, even though Ubuntu-One is hammering the CPU.  :)

---

### Post by VinDSL on 2011-08-10
Interesting!  That was quick...

I've been checking Synaptic every 5 minutes, and...

A brace of compiz updates just popped up - and life is good again.  :D

---

### Post by mc4man on 2011-08-10
The problem was initiated by a simple typo in gnome.desktop - 
a h should of been a H

---

### Post by coffeecat on 2011-08-10
@VinDSL, thanks for this thread. I opened ccsm last night to disable snapping windows (I really, [SIZE="3"]really[/SIZE], [SIZE="4"]really[/SIZE], dislike snapping windows :() and I thought it was that which had broken compiz and Unity for me.

Still waiting for the updates that will mend it again. :|

---

### Post by jerrylamos on 2011-08-10
> **el_koraco said:**
> Gnome 3 fallback mode. The worst thing to happen to Linux since 1995.

I can use "Unity" slower, full of screen clutter, Compiz constant overhead even when I'm in full screen mode and nothing Compiz is doing is even visible.  Microsoft forces people to keep buying faster and faster and more expensive pc's just to keep up with all the Microsoft overhead.

For ordinary installs etc. I drop back to command line frequently since the "Unity picturegraphics" don't have the required function.  Not even close.

So "Unity" makes linux look vaguely like MacOS or a touch screen tablet - both of which are mighty short of function and full of screen waste.

Well, whatever sells.

I use Unity-2D because I test whatever Ubuntu throws over the wall.  Unity-3D is fuzzy with hard to read transparent overlays and slower.

Jerry

---

### Post by moore.bryan on 2011-08-10
For my two cents, I would *much* prefer GNOME Shell to be the default fall back to Unity3D than Unity2d!

Oh, and the latest compiz updates have brought-back Unity. Now to figure-out by ubuntuone and aptd take-up all my memory for the first two minutes of being logged-in!

---

### Post by sgage on 2011-08-10
Now Unity is not working for me. There is no launcher, only my desktop wallpaper and a top panel that contains only the Nautilus menus. I logged into Gnome Shell, did an update via Synaptic - noticed there was a new Unity and thought ah! it'll be fixed. Tried Unity again and still no go. ???

---

### Post by mc4man on 2011-08-10
> **sgage said:**
> Now Unity is not working for me. There is no launcher, only my desktop wallpaper and a top panel that contains only the Nautilus menus. I logged into Gnome Shell, did an update via Synaptic - noticed there was a new Unity and thought ah! it'll be fixed. Tried Unity again and still no go. ???

If you have the new compiz (1:0.9.5.0-0ubuntu3) and gnome-session (3.1.3-0ubuntu10) then you should be ok for unity, maybe try a couple of logins in a row.
You could also try opening ~/.compiz/session and deleting all the files inside, then try again

---

### Post by terry_gardener on 2011-08-10
unity was not working for me this morning either but the workaround i did was clicked file - new window, which open nautilus and navigated to the /usr/share/applications and then loaded terminal. 

i then did unity --reset and unity appeared and working and i have been using it all day. 

however you have to leave the terminal window open so i moved to workspace 4 out the way.

---

### Post by sgage on 2011-08-10
> **mc4man said:**
> If you have the new compiz (1:0.9.5.0-0ubuntu3) and gnome-session (3.1.3-0ubuntu10) then you should be ok for unity, maybe try a couple of logins in a row.
You could also try opening ~/.compiz/session and deleting all the files inside, then try again

I had those versions of the packages installed. But the clearing out of ~/.compiz/session did the trick... thanks!

---

### Post by chrisccoulson on 2011-08-10
> **moore.bryan said:**
> For my two cents, I would *much* prefer GNOME Shell to be the default fall back to Unity3D than Unity2d!


That misses the point of "fallback" somewhat. The fallback session exists for people who don't have the hardware to run Unity, so a "fallback" to a shell with very similar demands on the graphics hardware seems a little pointless...

---

### Post by coffeecat on 2011-08-10
Ah, that's better! The latest set of updates have restored Unity for me. No messing about with config files - no resets either - just an update. I was getting bored with gnome-shell. Am I the only one in this thread who prefers Unity over gnome-shell and classic gnome? :)

---

### Post by sgage on 2011-08-10
> **coffeecat said:**
> Ah, that's better! The latest set of updates have restored Unity for me. No messing about with config files - no resets either - just an update. I was getting bored with gnome-shell. Am I the only one in this thread who prefers Unity over gnome-shell and classic gnome? :)

I haven't really made up my mind. I'm trying them both pretty much every day. They each have their pros and cons, and I can't quite decide which I prefer...

---

### Post by moore.bryan on 2011-08-10
> **chrisccoulson said:**
> That misses the point of "fallback" somewhat. The fallback session exists for people who don't have the hardware to run Unity, so a "fallback" to a shell with very similar demands on the graphics hardware seems a little pointless...
Yeah, I know... I just can't stand the look of Unity2D, so thankfully Unity3D works just fine for me. :-)

---

### Post by moore.bryan on 2011-08-10
> **coffeecat said:**
> Ah, that's better! The latest set of updates have restored Unity for me. No messing about with config files - no resets either - just an update. I was getting bored with gnome-shell. Am I the only one in this thread who prefers Unity over gnome-shell and classic gnome? :)
I wouldn't have written this last year, but Unity has come so far in responsiveness I use it on my Ubuntu install full-time. I'm still a *huge* fan of GNOME Shell, though, and use that with my Fedora 15 install. I think Unity has a far way to go, but is a valiant effort. If I *absolutely* had to choose, though, it'd probably be GNOME Shell.

---

### Post by ventrical on 2011-08-10
I just did a fresh install of alpha 3 oneric and I have the default Unity desktop !?

---

### Post by VinDSL on 2011-08-11
> **ventrical said:**
> I just did a fresh install of alpha 3 oneric and I have the default Unity desktop !?
Not sure what you're asking - or if that was a question or a statement, but...

Yes, Unity is the default DE on Ubuntu's flagship product.

And, I'm overjoyed to have it back...  :)

---

### Post by ventrical on 2011-08-12
Actually I did a partial upgrade (and then found out this was not the way to go.) So I do not have the Unity 3D but rather a GNOME that looks like Unity ?

---

### Post by VinDSL on 2011-08-12
I see.  Thanks.

Yes, partial upgrades are a dicey proposition.

Personally, I only do a partial upgrade if I'm bored and looking for adventure - there isn't any suitable alternative - I'm installing fresh daily builds every 24 hours, anyway, and don't care if I puke my current install - et cetera.

In general, partial upgrades are to be avoided like the plague, as you probably discovered.  :)

One way I protect myself, when I'm not in a whimsical mood, is to check the updates/upgrades using (first) Synaptic, and (then) apt-get.  I look to see if anything is being held back, if I've got anything pinned that I don't want to replace.

After a while, you get a *feel* for packages (or combinations of packages) that have a history of causing much wailing and gnashing of teeth.

Sometimes I check for updates every 5 minutes - sometimes every other day.

Right now, today, 12-Aug-2011, I'm being very careful about what I'm doing.  I had 199 updates waiting for me, when I got home last night, and I considered every one of them, before applying the changes.

Caveat emptor, you know?  ;)

---

### Post by VinDSL on 2011-08-13
w00t!

Just survived another omnibus update...  :D


[INDENT](Click to expand)

[[img]http://vindsl.com/images/Screenshot at 2011-08-13 01:05:03(650x520).png[/img]]("http://vindsl.com/images/Screenshot at 2011-08-13 01:05:03.png")[/INDENT]


Anxiously awaiting the beta...

---

### Post by ventrical on 2011-08-13
Right you are !

I did the synaptic routine,let that roll and it set to 'remove' three packages (that had to do with Unity 3.0 etc..)

OK.. so fine and dandy. Everything updated . Only thing was that during this process it removed the <APPLICATIONS> icon from the side-bar.  I know this is only aplha .. I expect this stuff.

  I tried an experiment and installed the fvwm-crystal desktop manager and so I can boot into that really good as a back-up.

I'm not worried about it because I have a commited hdd and laptop specifically for testing.

Thanks for your input.

---

### Post by ventrical on 2011-08-13
Hey Vin!! wheres your application Icon ???????????

---

### Post by mc4man on 2011-08-13
The applications icon is no more - in the big red button

---

### Post by VinDSL on 2011-08-13
Yep!  They're hiding it inside the Start Button now (second icon, bottom-center).

Don't know what it's supposed to be?!?!?


[INDENT](Click to expand)

[[img]http://vindsl.com/images/Screenshot at 2011-08-13 02:27:51(650x520).png[/img]]("http://vindsl.com/images/Screenshot at 2011-08-13 02:27:51.png")[/INDENT]

---

### Post by VinDSL on 2011-08-13
BTW, in anticipation of the question...

Yes, I run anti-virus software (avast!) in Linux.  LoL!  :D

---

### Post by ventrical on 2011-08-13
> **VinDSL said:**
> BTW, in anticipation of the question...

Yes, I run anti-virus software (avast!) in Linux.  LoL!  :D

Thanks for the Icon suggestion. I have to try that again because I couldn't get it going even after the large update in synpatic.

2. Avast !! ?

Teach me mojo master :)

---

### Post by ventrical on 2011-08-13
Thanks for the apps Icon tip.

Wow.. Unity 2d and Gnome3 working like a stable version !!

---

### Post by VinDSL on 2011-08-13
> **ventrical said:**
> Avast !! ?

Teach me mojo master :)
You can download the deb over here:  [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)

Free license registration is here:  [http://www.avast.com/registration-free-antivirus.php](http://www.avast.com/registration-free-antivirus.php)

And, here's a mini avast! HOWTO for installing it:  [http://ubuntuforums.org/showpost.php?p=10426480&postcount=14](http://ubuntuforums.org/showpost.php?p=10426480&postcount=14)

Really, I run avast! to protect my friends and acquaintances.

Viruses don't seem to affect Linux et al. but I don't want to accidentally pass one off to a Win user either, you know?


Here's a POC screenie (avast! runs fine in UbuOO A3) ;)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-08-13 15:08:36(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-08-13 15:08:36.png")[/INDENT]

---

### Post by ventrical on 2011-08-13
Thanks .. I downloaded it , double clicked it and the Ubuntu Software Center pops up and says there is a prob with software Center and closes down.

  Do I have to do the other settings first?

---

### Post by VinDSL on 2011-08-13
> **ventrical said:**
> Thanks .. I downloaded it , double clicked it and the Ubuntu Software Center pops up and says there is a prob with software Center and closes down.
I don't use Ubu Software Center, just because of incidents like that. ;)

I use dpkg, when installing debs...


_EXAMPLE_

[LIST]
[*]Download the avast! deb and place it in a folder by itself.
```
/Downloads/Avast
```[/LIST][LIST]
[*]Open a terminal and navigate to the folder containing the deb.
```
$ cd Downloads/Avast
```[/LIST][LIST]
[*]Run dpkg with enhanced privileges.
```
$ sudo dpkg -i *.deb
```[/LIST]
I use this process with all deb installs - kernels updates, nvidia drivers, whatever - works every time.

---

### Post by ventrical on 2011-08-14
This is as far as I got with it. 

I am not sure if resetting the block will work ? or solve this problem.

---

### Post by ventrical on 2011-08-14
OK... Thanks Vin .. It kicked in real nice after Avast deleted a 'user-stop' file. I think it had to do with resetting the license settings.

 I set the other parameters as you suggested but I used the terminal because I can't find CLI.

  Thanks a million!!

---

### Post by VinDSL on 2011-08-14
I guess we were typing at the same time, but I'll post this for general consumption.
 

> **ventrical said:**
> This is as far as I got with it. 

I am not sure if resetting the block will work ? or solve this problem.

Avast! won't work with the default kernel.shmmax setting - guaranteed.  :)

I've never figured out why they set it so low, but... most distros do.

The fix is easy!  ;)

You can run this (each & every time) prior to using avast!:
```

sudo sysctl -w kernel.shmmax=100000000

```
This will work for the remainder of your session.  When you reboot, it goes back to the default setting.


Or, you can fix it permanently by editing your ~/etc/sysctl.conf file:
```

$ sudo gedit ../../etc/sysctl.conf

```
At the bottom of this file, add a blank line, followed by a line containing...
```

kernel.shmmax=100000000

```
...save & reboot.


Here's how my ~/etc/sysctl.conf file currently looks:
```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
[B][COLOR="Red"]# Needed for Avast!
kernel.shmmax=100000000[/COLOR][/B]
#

```
Choose your poison!  :D

---

### Post by ventrical on 2011-08-14
You're absolutely right. I now have it set permanently. It works like a breeze in Oneric Ocelot. Only thing is that my config tells me that 'ipv4- we are not a router' etc.. I'll paste it. I'm not sure if I set this PC for DNS Secure settings using Comodo DNSes.

Thanks for all your help. That is a real bright work-a-round you have employed. I have some asking me about antivirus on the Ubuntu OS. I tried to set up AVG about a year ago. I got it working but not to my liking.

---

### Post by ventrical on 2011-08-14
Here is how I set up the new file.

I know that this is way off the topic of your original post.

Thanks so much.

----------------------------------------------

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See [http://lwn.net/Articles/277146/](http://lwn.net/Articles/277146/)
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
kernel.shmmax=100000000
#

---

### Post by VinDSL on 2011-08-14
> **ventrical said:**
> Thanks for all your help. That is a real bright work-a-round you have employed. I have some asking me about antivirus on the Ubuntu OS.
My pleasure!

Heh!  The most usual comment is, "You're the only person I know that runs AV software on Linux!"

Now, there's 2 of us...  :D

---

### Post by cariboo on 2011-08-15
I really don't see the point of running an AV client on Linux, they don't work that well on Windows, with some of the malware out in the wild. It also won't help against social engineering.

---

### Post by VinDSL on 2011-08-15
> **cariboo907 said:**
> I really don't see the point of running an AV client on Linux, they don't work that well on Windows, with some of the malware out in the wild. It also won't help against social engineering.
It's a scanner.  It doesn't run in realtime, so there's no performance hit, like with Windows AV software.

It comes in handy for checking your Thunderbird mail boxes, downloads folder, et cetera.

I use it to scan locally stored backups of my production server too, for malware.

And, the price is right...  ;)

---

### Post by ventrical on 2011-08-15
I have a USB to IDE/SATA Bridge cable device which allows me to hook up  any MS Windows based IDE or SATA HDD to my Ubuntu PC and scan the /media  of that drive.  AVG works probably the best but it does not have a GUI.

I did a test scan of an old hdd with Win XP on it and it detected a keylogger!! which other AV programs missed. Malware is more easily and readily detected when a Windows drive is not  the active OS.

  So , as a consultant (and for those who I have a hard time trying to teach the Ubuntus) it is good to have onhand because I can scan their hdds if they have a major crash from some wicked malware.

Also @ VinDsl pointed out, that it is good to scan e-mails with.

Other than this, I agree with Caribou. Even now, writing this message using Oneiric, Ubuntu is just so awesome ..

---

### Post by ventrical on 2011-08-15
> **cariboo907 said:**
> I really don't see the point of running an AV client on Linux, they don't work that well on Windows, with some of the malware out in the wild. It also won't help against social engineering.

Agreed about the social networking.  Iv'e seen malware  do things .... that make me have nightmares. Especially those directed at the social networks. It is yet another reason why I am converting to the Linuxes, because I was getting tired of being a crapware remover for faceB00k.

---

### Post by ventrical on 2011-08-15
@VinDsl

  Just wondering  what the code would be to uninstall avast antivirus.

---

### Post by VinDSL on 2011-08-15
> **ventrical said:**
> @VinDsl

  Just wondering  what the code would be to uninstall avast antivirus.
The easiest way to uninstall avast! would be to simply use Synaptic (GUI).

From a terminal (CLI) the command is:
```
$ sudo apt-get remove avast4workstation
```

---

### Post by ventrical on 2011-08-15
Again, my thanks.

---

### Post by VinDSL on 2011-08-16
> **ventrical said:**
> Again, my thanks.
You're welcome.

And, once again, I'm the only man that runs AV software in Linux.  LoL!

---

### Post by ventrical on 2011-08-16
Me two ! :)

---

### Post by ventrical on 2011-08-16
> **VinDSL said:**
> Interesting!  That was quick...

I've been checking Synaptic every 5 minutes, and...

A brace of compiz updates just popped up - and life is good again.  :D

Do you have the compiz settings manager installed?  I can see compiz in the system monitor but not in the menu. I am just wondering if I have to download it. I did that with Natty and it completely borked up the system.

  I have Ubu 2D, 3D and GNOME 3 working good but I would like to experiment with the likes of wobbly windows .. etc.. The 2D is awesome .. I like the way how the icon menus have this smooth scrolling but in GNOME shell and 3D the scrolling is more or less choppy.

---

### Post by VinDSL on 2011-08-16
Yes, I installed CCSM.  It isn't installed by default, for good reason(s).

It allows you to do stuff like (for instance) having 9 workspaces, but...


[INDENT][IMG]http://vindsl.com/images/Screenshot at 2011-08-16 01:24:40(650x520).png[/IMG][/INDENT]


Be forewarned:  Compiz (in Unity) is brittle.  It isn't like the good  ol' days.  Click the wrong box, and it will blow up in your face!  ;)

---

### Post by ventrical on 2011-08-16
Thats exactly my point Vin.!  I recall there were a few tips&tricks with Natty. I'm not sure if there is a tutorial on Compiz-With-Unity.

  In fact I think one of the major probs with Natty was that it was not compatible with Compiz. I have a feeling that this issue is going to be resolved with Oneiric or that Compiz may develop a global hook for Unity rather than the current custom hook, becauee, yeah .. you're right ..one wrong click.. and .... pppppphhht! :)

---

### Post by ventrical on 2011-08-16
They fixed that Unity 2D bug!!!! where you had to enter a letter in the search menu bar on the dash to get the icons to come up !!

Mabey it's a global fix. Will check and see.

---

### Post by ventrical on 2011-08-16
Nope.. not global fix yet.

---

### Post by ventrical on 2011-08-22
@vindsl

The Avast works exceptionally well !! I installed it on a  persistive pen_drive with Ubuntu and have been experimenting with the Eicar.tst file.

Just awesome.

Thanks again.

More and more Ubuntu just seems to have all the tools under the hood that we never got to use with commercial OS distros.

kudos to Avast.

---

### Post by VinDSL on 2011-08-23
Glad you like avast!

It's the best Linux AV software, IMO - Ubu installation foibles aside.

---

