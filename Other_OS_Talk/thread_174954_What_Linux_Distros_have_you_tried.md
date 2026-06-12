---
title: "What Linux Distros have you tried?"
date: 2006-05-12
forum: Other OS Talk
---

### Post by RAV TUX on 2006-05-12
I posted this info in a different thread I realize it would be fun to start a seperate thread:

I have tried a number of different Linux Distros:

Both for PC and 64 bit

Distro:..................................PC....... ..................................64 bit
Scientific Linux.................(couldn't get it running)...................(loaded fine but NO mouse and sound)
SUSE..............................(haven't tried for PC).......................(Couldn't get it running either)
Yoper.............................(Simply Awesome!)..........................(haven't tried for 64bit yet)
Ubuntu............................(love it!).......................................(Couldn 't get it running either)
Kubuntu...........................(nice, but don't use).......................(Couldn't get it running either)
Musix...............................(Couldn't get it running either)..........(great first distro to get running on EM64T)
Morphix(Gnome)..................(haven't tried for PC).....................(Most Awesome for EM64T!)
gnoppix.............................(haven't tried for PC)......................(Couldn't get it running either)
Kinneret............................(haven't tried for PC)......................(Awesome BUT how to enable english, oy!)
mepis................................(haven't tried for PC)......................(Couldn't get it running either)
other OS's
PC-BSD.............................(awesome, first KDE exp.)................(haven't tried for 64bit yet)
Debian K11 Hurd..................(Couldn't get it running either).........(haven't tried for 64bit yet)
Windows XP Sp2.................(No windows here)..............................(currently using)

currently going to try:

Fedora Core 5
Dreamlinux Studio Edition
Dreamlinux Standard Edition

I think this is a complete list?

*Let me restate the obvious: "tried" (can mean two things as in "tried to install", or if there was success in installation "tried" as in "tried out after install"). Since I started the thread my dual-definitions of the term "tried" can go both ways.*

---

### Post by briancurtin on 2006-05-12
every single one ever made.

ever.

---

### Post by RavenOfOdin on 2006-05-12
Slackware -- installed, got it running, was annoyed at lack of GUI and uninstalled.
Mandrake -- installed, got it running.
RedHat 7.3 -- installed, running, but KDE wouldn't start correctly and left my monitor with a cross hatch of blue among other things. This was on an old 386.

anything else:

FreeBSD 4.6 -- tried it but I had problems with the boot procedure

---

### Post by Lovechild on 2006-05-12
Let's see:

Red Hat 5.x
Mandrake 7
Mandrake 8
Progeny
Debian GNU/Linux
LFS
Gentoo
Arch
SuSE
Fedora
Ubuntu
Foresight Linux

And I've tried the following non Linux OS':

FreeBSD
BeOS
Windows 95
Windows 98SE
MS DOS 6.x
DR-DOS

And now I'm back on Fedora since they are the only ones who concern themselves with my basic security and freedom. I probably forgot a few distros - if it's been released I've probably had it installed, I'm a distro junkie.

---

### Post by briancurtin on 2006-05-12
[QUOTE=Lovechild]And now I'm back on Fedora since they are the only ones who concern themselves with my basic security and freedom.[/QUOTE]
could you elaborate on this? i dont use ubuntu so im not saying "come on man ubuntu is so secure and protects your freedom" or anything, im not a fan, just wondering what other distros have brought you to the thinking that Fedora are the only ones who care about that.

---

### Post by aysiu on 2006-05-12
[QUOTE=briancurtin]could you elaborate on this? i dont use ubuntu so im not saying "come on man ubuntu is so secure and protects your freedom" or anything, im not a fan, just wondering what other distros have brought you to the thinking that Fedora are the only ones who care about that.[/QUOTE] Lovechild's probably referring to this: > Security

You can always expect interesting and exciting advancements in security from Fedora Core, and this release does not disappoint. Security Enhanced Linux (SELinux) is now using the reference policy, which makes it easier to create and maintain modular security policies. The introduction of a stack protector to GCC 4.1 makes it harder than ever for hackers to exploit buffer overflows, one of the most common security vulnerabilities.

[http://fedoraproject.org/wiki/Security/Features?highlight=%28fstack%29](http://fedoraproject.org/wiki/Security/Features?highlight=%28fstack%29)

Fedora has switched to using the reference policy for the SELinux security framework. This supports binary modules, allowing SELinux policies to move into individual packages. Developers can use this to ship site-specific policy customizations. Fedora Core also supports the Multi Category Security (MCS) SELinux policy by default, in addition to Type Enforcement (TE), Muti Level Security (MLS), and Role Base Access Control (RBAC) security policies. These gains in security continue to make Fedora Core one of the most secure general-use operating systems in the world. Find more facts at:

[http://fedoraproject.org/wiki/Security](http://fedoraproject.org/wiki/Security)

[http://serefpolicy.sourceforge.net/](http://serefpolicy.sourceforge.net/)

Linux Unified Key Support (LUKS) provides hard disk encryption support in Fedora Core 5. David Zeuthen of Red Hat, the HAL developer and maintainer, worked on the LUKS integration with HAL and GNOME, finishing just in time for the new Fedora Core release. Hard disk encryption provides one of the best physical security solutions -- protection of your data if your hard disk falls into the wrong hands.

[http://fedoraproject.org/wiki/Software/LUKS](http://fedoraproject.org/wiki/Software/LUKS)  from [the Fedora Wiki](http://fedoraproject.org/wiki/FC5ReleaseSummary).

---

### Post by Rhapsody on 2006-05-12
I've tried Ubuntu 5.10 (on Live CD) and I'm using Kubuntu 5.10 right now.

As for non-Linux, I've owned PC with the following installed:

Windows for Workgroups 3.11
Windows 95 (alternating and sometimes dual-booting with Windows for Workgroups 3.11 on a particularly unstable PC)
Windows 98
BeOS Personal Edition (briefly, dual-booted with Windows 98)
Windows XP Home (dual-booted with Windows 98 for a few years, then it was the sole OS, now dual-booting with Kubuntu 5.10)

I've also made some use of Windows 2000 on other PCs, but never on one I owned.

---

### Post by Lovechild on 2006-05-12
Fedora also deploys several glibc and gcc technologies to protect against stack smashing attacks, ProPolice, FORTIFY_SOURCE=2, Exec shield. There's also a default restrictive firewall deployed - don't tell me Ubuntu doesn't need that because they don't open ports by default - when Joe user installs a random package and it yanks in say.. sendmail for some reason - he could by default having an open service on the internet. Firewalls protect the user and it's just good sense to have it - belt and suspenders remember?

I've begged and pleaded Ubuntu to enable this by default since early in the Hoary cycle and every cycle I get told that security unfortunately needs to be defered to the next cycle - now we have Dapper which will be out and supported for 5 years, without technology that stops nearly half of all reported security flaws[1]. This is well tested security options that do not break the end user experiences unless the software is broken - please don't tell me that enabling a few compiler switches is to much work, I have compiled an entire system with these switches without alternations to the code. The system has been fixed by early adopters.. this is a major security improvement with minimal overhead and deployment cost but with huge wins in support. But Ubuntu sadly just doesn't care enough to do this, I can find no other explaination for this barage of rejection, maybe back in the Hoary cycle early adoption was an issue for Dapper shipping without it is nothing less than insane with the market we are trying to hit.

From a stack protection POV who has the best by default security? Windows XP SP2 or Ubuntu Dapper.. Yep Windows.. Ubuntu is worse than Windows because SP2 actually deployed some similar stack protection fir Windows users. 

You optout of security, not in - remember that, you chose when it's wise to be insecure - when security doesn't get in your way and these technologies (aside SELinux which can cause a few issues due to policy flaws) really only gets in your way when software is broken in it's behaviour

[1] source: Mark J. Cox, numbers from stems FC3/4, RHEL3/4.

---

### Post by RAV TUX on 2006-05-12
[QUOTE=Lovechild]
And now I'm back on Fedora since they are the only ones who concern themselves with my basic security and freedom. I probably forgot a few distros - if it's been released I've probably had it installed, I'm a distro junkie.[/QUOTE]

This will be the next distro I will try Fedora core 5 is the most recent right?

I actually burned CD's but they were not good copies for what ever reason. Will attempt to burn more or maybe a DVD if they have it.
:mrgreen:

---

### Post by Stormy Eyes on 2006-05-12
Red Hat, Mandrake, Slackware, Lesbian, Debian, Gentoo, Knoppix, Libranet, Ubuntu. I've also used FreeBSD.

---

### Post by RAV TUX on 2006-05-12
[QUOTE=Stormy Eyes] Lesbian[/QUOTE]

Lesbian? do  you have a link?
:shock:

EDIT: nevermind I found the link:

[http://lists.debian.org/debian-curiosa/2001/10/msg00025.html](http://lists.debian.org/debian-curiosa/2001/10/msg00025.html)

EDIT: Hey is this a real Linux OS or just a paraody?

[http://www.lesbian.mine.nu/](http://www.lesbian.mine.nu/)

---

### Post by Lovechild on 2006-05-12
[QUOTE=yozef]This will be the next distro I will try Fedora core 5 is the most recent right?

I actually burned CD's but they were not good copies for what ever reason. Will attempt to burn more or maybe a DVD if they have it.
:mrgreen:[/QUOTE]

You would want to grab the FC5 release although FC6 which is being worked on now is looking to include some fine tech as well as even better security. If you want to join the bughunting effort I'd recommend the Development branch which is kinda like Ubuntu' development branch (Dapper currently), scary at time, will eat babies on occasion but for the most part it's a solid experience as long as you know what you are doing and prepare for the worst.

There are DVD images available - one thing to remember is that burning depends heavily on media, slow burning tends to be best for bad hardware and media. That solved my issue with my old Lite-ON CDRW at least, my Plextor burns anything I throw at it without complaining (you do get what you pay for at times).

You can PM me for a guide to setting up proper multimedia support on FC5 if you want, I haven't had time to put it anywhere so that might force me to do it.

---

### Post by RAV TUX on 2006-05-12
[QUOTE=Lovechild]

You can PM me for a guide to setting up proper multimedia support on FC5 if you want, I haven't had time to put it anywhere so that might force me to do it.[/QUOTE]

Thanks I'll let you know if I need any backup.
:cool:

---

### Post by Orunitia on 2006-05-12
hrm... let's see.

Mandrake (I think 9.1 and 9.2 is what I used. Started using linux with mandrake 9.1.)
Suse
Slackware
Debian
Red Hat 9
Fedora core (Every version.)
And of course, Ubuntu. I've stuck with Debian and Ubuntu the longest. (Ubuntu beats Debian for the longest I've had it installed though. Just Debian without all the hassle. :P)

I *think* that's all of them. Keep in mind that I've tried several versions of all of those distros. >_< Even though it's not that many compared to some of the people that will post here, it still feels like a lot.
One of these days I'm gonna try gentoo. (I'm always saying that. I really don't feel like going through the damn install though.)

---

### Post by RAV TUX on 2006-05-12
OK add to my list

distro....................PC.............................64bit

Mepis.............(haven't tried on pc).........(can't get it running on 64bit)

I may have had high expectancies for Mepis with all the high plugs for it from the community here but rule number one for me is if it proves to be too difficult then I have to give it a thumbs down.

Mepis is NOT a good distro for newbies. 

It may be a good distro but I find it more difficult then ubuntu to install.
:(

EDIT:

downloading now A Fedora Core 5 DVD iso image for 64bit, will give follow up feed back.

---

### Post by RavenOfOdin on 2006-05-12
[QUOTE=Stormy Eyes]Lesbian[/QUOTE]

Uh? How does that work?
Are you giving them the old "I'm a lesbian trapped in a man's body" line? ;)

(EDIT: What. . .
 The. . .
 ****static** KWEEEEEEEEEEEEE**)

 Not a safe distro for work. :eek:

---

### Post by Iandefor on 2006-05-12
Xandros, Knoppix, MEPIS, Tomsrtbt, SUSE Linux, Ubuntu, and Fedora Core 5.

Of them all, I'm most impressed with Fedora.

---

### Post by RAV TUX on 2006-05-12
[QUOTE=yozef]I posted this info in a different thread I realize it would be fun to start a seperate thread:

I have tried a number of different Linux Distros:

Both for PC and 64 bit

Distro:..................................PC....... ..................................64 bit
Scientific Linux.................(couldn't get it running)...................(loaded fine but NO mouse and sound)
SUSE..............................(haven't tried for PC).......................(Couldn't get it running either)
Yoper.............................(Simply Awesome!)..........................(haven't tried for 64bit yet)
Ubuntu............................(love it!).......................................(Couldn 't get it running either)
Kubuntu...........................(nice, but don't use).......................(Couldn't get it running either)
Musix...............................(Couldn't get it running either)..........(great first distro to get running on EM64T)
Morphix(Gnome)..................(haven't tried for PC).....................(Most Awesome for EM64T!)
gnoppix.............................(haven't tried for PC)......................(Couldn't get it running either)
Kinneret............................(haven't tried for PC)......................(Awesome BUT how to enable english, oy!)
other OS's
PC-BSD.............................(awesome, first KDE exp.)................(haven't tried for 64bit yet)
Debian K11 Hurd..................(Couldn't get it running either).........(haven't tried for 64bit yet)
Windows XP Sp2.................(No windows here)..............................(currently using)

currently going to try:
Mepis...............................(after I burn CD I will try on PC)

I think this is a complete list?[/QUOTE]

As stated in prior posts Mepis didn't work and I am downloading Fedora Core 5,

Now the only distro I have been able to get to work on my Em64T computer is Morphix Gnome 0.5 pre4  so I went back to the Morphix site to see what kind of derivatives have been built on their OS.

I found a beautiful Morphix derivative:

Dreamlinux
[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

Check out Dreamlinux this is the most excited new Linux Distro to date!!!!

It comes in two forms now Standard Edition and Studio Edition 
I am downloading both ISO images.

The cool thing with Dreamlinux is you can actually build your own linux distro and they also plan on a 6 month release cycle like Ubuntu.

Again I was just talking to my wife of how I wanted to build my own Linux distro, I was dreaming then I found Dreamlinux!

"The exclusive MKDistro tool allows you to build your own Distro from the ground up easily, in a completely assited way."

I'll let everyone here know how Dreamlinux goes(I'll be up late tonight!)
:KS

---

### Post by RAV TUX on 2006-05-12
wow major trouble posting to this thread, my apologies.

---

### Post by RAV TUX on 2006-05-12
This happened to me twice today where I had trouble posting then it eventually came up in triplicate.


Anyway, yeah downloading the iso image of Dreamlinux, Standard and studio edition now.
[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

---

### Post by briancurtin on 2006-05-12
[QUOTE=yozef]OK add to my list

distro....................PC.............................64bit

Mepis.............(haven't tried on pc).........(can't get it running on 64bit)

I may have had high expectancies for Mepis with all the high plugs for it from the community here but rule number one for me is if it proves to be too difficult then I have to give it a thumbs down.

Mepis is NOT a good distro for newbies. 

It may be a good distro but I find it more difficult then ubuntu to install.
:([/QUOTE]i installed mepis without looking. what were you doing?

also, i dont know if you can consider that you "tried" the mepis distribution if you couldnt get it working

---

### Post by aysiu on 2006-05-12
yozef, you appear to be on a one-person crusade against Mepis.

I'm sorry, but Mepis isn't as difficult as you make it out to be. I'm not saying your experience isn't *valid*, only that it's *uncommon*.

From what I've seen (and I've seen *a lot* of posts here), most Ubuntu users have had an easy time of using Mepis but have ditched it for other reasons. I'm not just speaking for myself (there are plenty of times when I experience something weird and no one else is experiencing it--for example, [this weird Firefox bug](http://www.ubuntuforums.org/showthread.php?t=161154)).

You have to realize that your experience is your experience. You have to take a step back and try to contextualize your experience in the larger scheme of others' experiences. Is your experience an aberration or the norm?

Sometimes, like in this one, I think you have to concede your experience with Mepis is an aberration.

---

### Post by jason.b.c on 2006-05-12
[QUOTE=Stormy Eyes]Red Hat, Mandrake, Slackware, Lesbian, Debian, Gentoo, Knoppix, Libranet, Ubuntu. I've also used FreeBSD.[/QUOTE]


Uuhh.??,  "Lesbian"..??  woah.:)

---

### Post by RAV TUX on 2006-05-13
[QUOTE=yozef]
Anyway, yeah downloading the iso image of Dreamlinux, Standard and studio edition now.
[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)[/QUOTE]

OK exciting update: just burned to CD Dreamlinux Studio Edition will try now.

About the few Mepis enthusiast in the Ubuntu forum, lighten up I am not against Mepis or any other distros. I am just posting my personal experience as a newbie.

Mepis didn't work!; it's nothing to get hung about, Ubuntu is still my primary OS.  Scientific Linux, SUSE, gnoppix, didn't work either. I don't hear anybody crying over that, but then not a lot of people are here promoting them either.


I have moved beyond the Mepis scenario hours ago and have already downloaded 3 other distros.

1. Fedora Core 5
2. Dreamlinux Studio Edition
3. Dreamlinux Standard Edition

I'll post back my newbie reviews of the above three distros.
:mrgreen:

---

### Post by GreenfrogCT on 2006-05-13
A number of them . . . 

Red Hat, going back to 5.0 I think
Suse - several incarnaitons.  Wasn't impressed.
Mandrake - 7, 8, 9, 10 - tried the first Mandriva release.  Ecccch.  Erased it.  * (J'aime la France, mais ils sont grands au vin et au grandiose souper, pas si bon aux systèmes informatiques.)  *  Moved to Ubuntu.  It was a good move.
Ubuntu Breezy Badger, Now running Dapper Beta on one partition, Breezy on another, XP Pro on another.  (sorry - job requires I run XP.)  I have a file and application server on my network still running Mandrake 10.  I think that will become a Dapper server when the final release comes out.

Non GNU . . .

Well, I started out as a child . . .  bought a surplus DEC PDT-11/150 running RSX, RT11 and RSTS. (I think I still have that system in a closet down in my utility room somewhere.)  Played with Commodore VIC-20, 64, and 128.  Wrote games in 6502 assembler.  Worked with CPM and CDOS, then with MS-DOS at 3.x, and forward, followed by every incarnation of Windows from 3.1 forward, as well as OS/2 from the very early releases, seriously starting at 2.1 and 3.0 (AKA "Warp),  (which I did some voice application development work in, including an off-track-betting IVR program for horse racing.) and 4.0 which, unfortunately, was too little too late.

I've got to tell you, I'm pretty impressed with Dapper.  Yeah, there's a few bugs still (Beta = "Not out of the oven yet")  but this is one impressive OS distro . . . and I've seen my share over the years.

:mrgreen: Ribbitt

---

### Post by briancurtin on 2006-05-13
[QUOTE=yozef]About the few Mepis enthusiast in the Ubuntu forum, lighten up I am not against Mepis or any other distros. I am just posting my personal experience as a newbie.

Mepis didn't work!; it's nothing to get hung about, Ubuntu is still my primary OS.  Scientific Linux, SUSE, gnoppix, didn't work either. I don't hear anybody crying over that, but then not a lot of people are here promoting them either.[/QUOTE]
mepis enthusiast? i frankly dont like the distro, but it was cake to install. thats my piece on mepis. im just not sure why you are saying that you tried a distro, but you couldnt have really tried because it didnt work.

---

### Post by RAV TUX on 2006-05-13
[QUOTE=GreenfrogCT]
I've got to tell you, I'm pretty impressed with Dapper.  Yeah, there's a few bugs still (Beta = "Not out of the oven yet")  but this is one impressive OS distro . . . and I've seen my share over the years.

:mrgreen: Ribbitt[/QUOTE]

Yes I agree Ubuntu Dapper beta is pretty awesome and by far the best OS I have come across, I started with the hoary hedgehog and have been hooked ever sense.
:mrgreen:

I am still blown away by Yoper which I use as a dual boot with Ubuntu Dapper Beta.

[http://www.yoper.com/](http://www.yoper.com/)

Ubuntu/Yoper are here to stay on my computer!

*Let me restate the obvious: "tried" (can mean two things as in "tried to install", or if there was success in installation "tried" as in "tried out after install"). Since I started the thread my dual-definitions of the term "tried" can go both ways.*

---

### Post by Kobalt on 2006-05-13
Fedora 3, Suse 10.0, Ubuntu 5.04 - 5.10 - 6.06

---

### Post by tseliot on 2006-05-13
[QUOTE=Lovechild]You can PM me for a guide to setting up proper multimedia support on FC5 if you want, I haven't had time to put it anywhere so that might force me to do it.[/QUOTE]
Isn't this guide good enough? ;) 

[http://www.fedorafaq.org/]("http://www.fedorafaq.org/")

---

### Post by Kindred on 2006-05-13
Ubuntu, DSL, Slackware, Gentoo, Arch.

---

### Post by tseliot on 2006-05-13
[LIST]
[*]Linspire 5.0 
[*]Ubuntu (and Kubuntu) Hoary, Breezy, Dapper
[*]Knoppix 4.0
[*]MEPIS 3.3.1 , 3.4.3
[*]Fedora Core 3, 4, 5
[*]PCLinuxOS 9.2, 9.3
[*]Debian Sarge
[*]OpenSUSE 10
[*]Arch Linux Noodle
[*]Gentoo 2005.1, 2006
[*]Vector Linux 5.0.1
[*]Zenwalk
[*]FreeBSD 6.0
[*]PC-BSD 1.0
[*]DesktopBSD 1.0
[/LIST]

I'm currently using:
[LIST=1]
[*]On my Desktop: Fedora Core 5 and Ubuntu Dapper
[*]On my laptop: Arch Linux Noodle
[/LIST]

---

### Post by RAV TUX on 2006-05-13
[QUOTE=yozef]OK exciting update: just burned to CD Dreamlinux Studio Edition will try now.



I have...downloaded 3 other distros.

1. Fedora Core 5
2. Dreamlinux Studio Edition
3. Dreamlinux Standard Edition

I'll post back my newbie reviews of the above three distros.
:mrgreen:[/QUOTE]



Dreamlinux Studio Edition is by far the single most best linux distro out!  I am amazingly floored by every aspect of Dreamlinux Studio Edition. 

1. Beautiful and most awesome website of any Linux Distro.
2. ISO files simply and easy to find, download quick and easy.
3. Live and install CD all in one. Dreamlinux Studio Edition simply works on my old intel828ioe as well as on my new computer (intel EM64T dual-core).
4. beautiful Xfce settings
5. Fastest Distro yet.
6. can access iPod devices

Take a look and try it out. I will be running a Dual boot of Ubuntu and Dreamlinux Studio Edition  on both my computers.

Dreamlinux-home site(English)
[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

This wonderful Distro out of Brazil is a refined and elegant work of art.

Dreamlinux...because dreams can come true

:KS 

QUICK GUIDE

Dreamlinux is a "LiveCD" distribution inspired on the Debian, Knoppix and Morphix distributions, which can be used running through the CD, without causing any defect to the installed system and to the computer. But, if you want to, you can use the option Install Dreamlinux in the menu, or through DMCP - Control Panel, to install the system, which will work as any other Linux's distribution.

To start a session with Dreamlinux, put the CD in the drive and set, if necessary, the Bios of your computer to be possible make the boot through the CD. When you start the system a screen will appear with many options of boot which allow, in other alternatives, the correction of eventual errors in the hardware's detection and sets on the monitor resolution. But it's better if you don't use, in the beggining, none of the options in the boot screen, letting the system load normally. Just when an eventual error in your hardware's set or in the video plate resolution appears is when you must seek, on the boot's screen, an option that can adapt better in your hardware.

[[IMG]http://img163.imageshack.us/img163/8155/tela60sv.th.jpg[/IMG]](http://img163.imageshack.us/my.php?image=tela60sv.jpg)GTKPOD for your iPods

[[IMG]http://img160.imageshack.us/img160/6634/kino0sa.th.jpg[/IMG]](http://img160.imageshack.us/my.php?image=kino0sa.jpg)Kino - Video Editor

[[IMG]http://img87.imageshack.us/img87/2289/tela19bt.th.jpg[/IMG]](http://img87.imageshack.us/my.php?image=tela19bt.jpg)XFCE running Rox-Filer
+ XMMS audio player

[[IMG]http://img88.imageshack.us/img88/6978/wings1tr.th.jpg[/IMG]](http://img88.imageshack.us/my.php?image=wings1tr.jpg)Wings 3D

---

### Post by 3rdalbum on 2006-05-13
The first Linux I used was Ubuntu, and I'm still running it on my Mac and PC.

But I've tried:
dlx (tiny Linux that comes with Bochs)
Puppy
DSL
Dynebolic
Looking Glass 3D Live CD

---

### Post by Lovechild on 2006-05-13
> **tseliot]Isn't this guide good enough?  said:**
> http://www.fedorafaq.org/[/URL]

Not in my opinion, they tend to yank in every repo out there and that's a problem - I just add livna and the gstreamer repos that gives you the stuff you need for multimedia and closed vdeo drivers.

---

### Post by RAV TUX on 2006-05-14
Ok after more trials of Linux Distros I have decided there are only two I will use on a regular basis, installed on my harddrive in 2 different boxes.

1. Ubuntu
[http://www.ubuntu.com/](http://www.ubuntu.com/)

2. Yoper
[http://www.yoper.com/](http://www.yoper.com/)

while Dreamlinux Studio Edition is great especially if you want to build your own Linux Distro with their MKDistro tool, it is mostly usefull as a live CD.
[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

Same for Morphix 0.5-pre4 Gnome.
[http://www.morphix.org/index.php?option=com_content&task=view&id=39&Itemid=59](http://www.morphix.org/index.php?option=com_content&task=view&id=39&Itemid=59)
:mrgreen:

---

### Post by RAV TUX on 2006-05-16
I stopped dual booting lastnight and now exclusively use Ubuntu Dapper beta

---

### Post by christhemonkey on 2006-05-16
Ubuntu Dapper Drake.

---

### Post by Moebius on 2006-05-16
Let's see If memmory doesn't fail me

Red Hat, Mandrake, SuSE, Caixa Mágica, Fedora and Ubuntu.

Live CDs of fond memory (but not all of them)
Knoppy, Kororaa, DSL.

---

### Post by mjm115 on 2006-05-16
I started with Mandriva(when it was still Mandrake), switched to Suse, tried Xandros, switched back to Suse and then discovered Kubuntu.  I've been with Kubuntu ever since.

---

### Post by RAV TUX on 2007-09-22
> **RAV TUX said:**
> I posted this info in a different thread I realize it would be fun to start a seperate thread:

I have tried a number of different Linux Distros:

Both for PC and 64 bit

Distro:..................................PC....... ..................................64 bit
Scientific Linux.................(couldn't get it running)...................(loaded fine but NO mouse and sound)
SUSE..............................(haven't tried for PC).......................(Couldn't get it running either)
Yoper.............................(Simply Awesome!)..........................(haven't tried for 64bit yet)
Ubuntu............................(love it!).......................................(Couldn 't get it running either)
Kubuntu...........................(nice, but don't use).......................(Couldn't get it running either)
Musix...............................(Couldn't get it running either)..........(great first distro to get running on EM64T)
Morphix(Gnome)..................(haven't tried for PC).....................(Most Awesome for EM64T!)
gnoppix.............................(haven't tried for PC)......................(Couldn't get it running either)
Kinneret............................(haven't tried for PC)......................(Awesome BUT how to enable english, oy!)
mepis................................(haven't tried for PC)......................(Couldn't get it running either)
other OS's
PC-BSD.............................(awesome, first KDE exp.)................(haven't tried for 64bit yet)
Debian K11 Hurd..................(Couldn't get it running either).........(haven't tried for 64bit yet)
Windows XP Sp2.................(No windows here)..............................(currently using)

currently going to try:

Fedora Core 5
Dreamlinux Studio Edition
Dreamlinux Standard Edition

I think this is a complete list?

*Let me restate the obvious: "tried" (can mean two things as in "tried to install", or if there was success in installation "tried" as in "tried out after install"). Since I started the thread my dual-definitions of the term "tried" can go both ways.*Since this post I have a lot to add to this list.

---

### Post by ArtF10 on 2007-09-22
meh, I found Dream Linux rather ordinary on my machine.  Nothing quite as good as it was hyped up to be when I downloaded and installed this past August.  Nothing I couldn't do in Ubuntu, so just removed it.  I found that it did not (hardware detection related?) pickup the proper video card (NVIDIA) resolution and was pretty slow in booting up...definitely slower than Ubuntu.

**In order**, I;ve tried

Ubuntu
Zenwalk
Puppy Linux
Yoper
Xubuntu
Mepis
Dream Linux
Sam Linux
Mint Linux XFCE
Fluxbuntu

Presently, dual booting Ubuntu (for the effects) / Xubuntu(for the speed, although I've added bling bling here as well...still faster though).

**Wish List:**
e-Live Gem 1.0 ---> even before installing, I know I'm going to like this.
Arch Linux ---> again, for the speed.....maybe when I've got a week to waste next summer.

---

### Post by fistfullofroses on 2007-09-22
For Linux specifically:

BLAG, 
Fedora Core, 
RedHat (not enterprise but before Enterprise and Fedora split),
Slackware, 
Wolvix, 
Slax, 
Knoppix, 
Puppy, 
DSL, 
HAL 91, 
Zenwalk, 
Yellow Dog, 
Ubuntu, 
Kubunu, 
nUbuntu, 
Xubuntu, 
Edubuntu, 
College Linux, 
dynebolic, 
Pardus, 
TurboLinux, 
GoboLinux, 
Debian, 
Mandrake, 
Mandriva, 
Caldera, 
BackTrack, 
SuSE, 
Vector, 
gNewSense, 
Gentoo, 
Arch, 
Mepis,
Sabayon,
Lunar,
Bluewhite64,
Slamd64,
OpenSUSE,
Freespire,
LinuX-Gamers,
Fluxbuntu,
Ubuntu Studio,
Mint,
Absolute,

Non Linux

Nexenta,
Belenix,
FreeBSD,
NetBSD,
Syllable,
Menuet,
FreeDOS,
MS DOS 6.22
MS DOS 7.10
Haiku,
Minix3 (in qemu)
Visopsys,
SkyOS (an old beta)

:::EDIT:::
almost forgot -
Win 3.1,
Win95,
Win98,
Win Mangled Edition,
Win2k,
WinXP,
WinNT 4,
Win Vista (briefly on my friend's laptop)

:::Another Edit:::
Darwin,
MacOS 7-7.5.5,
MacOS 8,
MacOS 9,
MacOS X 10.4

---

### Post by Skorzen on 2007-09-23
I've tried this ones:

Ubuntu,
Kubuntu,
Xubuntu,
Kurumin,
Caixa Mágica,
and Fedora 7.

Ubuntu owned them all. :lolflag:

---

### Post by fistfullofroses on 2007-09-23
I highly recommend trying BLAG if you like Ubuntu a lot.

---

### Post by Bart_D on 2007-09-23
> **fistfullofroses said:**
> I highly recommend trying BLAG if you like Ubuntu a lot.

What;s the difference between BLAG and Ubuntu?

---

### Post by newlinux on 2007-09-23
Ubuntu
Kubuntu
Xubuntu
DreamLinux
Debian
Redhat

Ubuntu and Kubuntu are my favorites. Although I do like Dreamlinux.

---

### Post by Chilli Bob on 2007-09-24
Ubuntu - Cool
Kubuntu - meh - Amarok is nice, you can keep the rest.
Xubuntu - Nice, but I just added xfce to my Ubuntu and run that occasionally.
Knoppix - Nice, the best KDE distro I've tried.
Fedora - Installed, but wouldn't run.
Puppy - Love that little guy.
Zenwalk - Nice
Mandriva - meh - like Kubuntu but orange
Damn Small - a cool idea, but feels clunky.
Free BSD - Installed, but wouldn't run
Gentoo - A lot of work for minimal gain. Maybe cooler if I understood more of what I was doing instead of selecting defaults so often.
Berry - strange??

there were some more, but that's all I can think of at present.

---

### Post by acowboydave on 2007-09-24
Installed: Linux XP, Fedora 6, Linux Mint 3.1, Kubuntu, Xubuntu, Ubuntustudio, Vector Linux 5.8 Gold, Ubuntu Feisty, Ubuntu Ultimate Gamers

---

### Post by jamathis on 2007-09-25
I've tried several.

Ubuntu
Linux Mint (currently using)
Ubuntu Studio
Mandriva/Mandrake (also currently using)
Red Hat/CentOS/Whitebox/Fedora
SuSe
PCLinuxOS
Backtrack
Knoppix
PHLAK
dyne:bolic
Xandros
Slackware
Slax
Mepis
Sabayon
KateOS
Foresight
Ark
Damn Small
Puppy
Debian
Freespire
SymphonyOS
Fruglaware
Vector

I liked most of them that I have tried.  A few I've found lacking and just not for me (i.e. SuSe, Xandros, & Foresight).  Overall, I like Ubuntu and it's derivative Linux Mint the most.

---

### Post by Nevon on 2007-09-25
I've only ran these dists (except for ubuntu) on a virtual machine, so I'm not sure if that even qualifies as testing. But saying it does, I've tested the following:
- Ubuntu
- OpenSUSE
- Mandrake
- Fedora
- Dreamlinux
- Fluxbuntu
- Evine Gem

---

### Post by ahaslam on 2007-09-27
Yoper
OpenSuse
Ubuntu
Xubuntu
Debian
Zenwalk
Sabayon
Gentoo (stage 2)
Fedora Core
Mint
Mepis
Damn Small
Slackware
Knoppix
Puppy
Arch
DreamLinux
Vector
Slax
Elive
Forsight
Linux-gamers
Frugalware
KateOS
Gparted
PartedMagic
Ulteo
PCLOS
Mandriver

[B]
My favourites: Ubuntu, Zenwalk & Arch[/B]

;)

---

### Post by knowledge296 on 2007-09-27
hello im currently trying ubuntu 7 and am having problems with my video card i have hp pavilion with ATI Radeon XPRESS 200M 5955 (PCIE)
 can u help me get setup for 3d please!


in terminal
cat /etc/X11/xorg.conf | grep Driver   shows
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "fglrx"
 any help would be great

---

### Post by Docula79 on 2007-09-27
Hi. I have only been using linux around 3 months now. I use Ubuntu feisty. (My main distro. Love it). I have played about with SLAX but have settled on DSL (Damn small) for my portable pen drive linux distro. I especially like the stats that are displayed on the desktop on DSL. Been thinking about downloading suse but have been told its a bit advanced for me. Im still getting to grips with basic terminal commands. Very impressed with linux in general though. I wont go back to windows EVER. :-)

---

### Post by maybeway36 on 2007-09-27
Kubuntu - first one I tried (after Knoppix), still using it
Ubuntu (I prefer KDE over GNOME)
PCLinuxOS (actually dual-booting with Kubuntu to try it out - installed its GRUB to a floppy)
Fedora 7
Debian etch and sid

I prefer Kubuntu over Debian+KDE mostly because of the better default settings.

My favorite Linux app is x11vnc. Oddly, none of the above seem to be using the newest version. :confused:

P.S. I also have FreeDOS on my computer, mostly for ML Yaht and some other games.

---

### Post by markp1989 on 2007-09-27
In no order:

Fedora
Linux XP
DSL
Knoppix
Debian
Puppy linux
Slackware 
Ubuntu

I believe there are more

---

### Post by mediocrates on 2007-09-28
Red Hat 7.0, 7.1, 7.2, 7.3, 8, 9
Fedora 1, 2, 3, 4, 5, 6, 7
SuSE 8.0, 8.2, 9.0, 10
Frugalware 0.4
PCLinuxOS 2007
PCBSD 1.3
Slackware
Mandriva
Linux Mint 3.1

---

### Post by Cene on 2007-09-28
Let's see..

GNU/Linux:
Knoppix
SuSE
Debian
(K/X)Ubuntu
Slackware
Damn Small Linux
Gentoo (Currently using)

BSD:
OpenBSD
FreeBSD

Other:
Windows 3.1/3.11
Windows 95
Windows 98(SE)
Windows ME
Windows 2000
Windows XP
Windows 2k3 Server
OS/2 Warp
ReactOS
MacOS 9
MacOS X

I guess that's about it.
I've been using Gentoo now for about six months, and am totally in love with it. <3
Portage is just great. Ports was great for BSD too, but no DRI = no fun. :(

---

### Post by Calash on 2007-09-28
Fedora
Gentoo
Ubuntu
Puppy
DSL
ReactOS

---

### Post by Alucard-sama on 2007-09-28
In no particular order:

Ubuntu 6.06 - Installed fine, Desktop loaded, DHCP didn't work properly.
PCLinuxOS - Installed fine, Desktop loaded, DHCP worked with a little tweaking.
Fedora Core 5 - Couldn't install.
Linux Mint 3.0 - Worked Perfectly.
Gentoo - Worked Perfectly.
Kubuntu 7.04 - Worked Perfectly -Except that I had to Open Repositories In Firefox Before I Could Download From Them Using Synaptic/Apt-Get/Aptitude-.
Puppy Linux - Worked Perfectly (And Off A USB).
Ubuntu 7.04 - Worked Perfectly.
Ubuntu Ultimate Gamer's Edition 1.4 (Basically Ubuntu 7.04 With Some Tweaks and ALOT of Pre-installed Software) - Worked Perfectly.

---

### Post by thegnome87 on 2007-09-29
[COLOR="Orange"]**Mandriva**[/COLOR] (first distro) Move, Mandriva 2006, Mandriva 2007  (loved the distinctive icon look, and Control Center...can't afford the club :-()

[COLOR="Green"]**SUSE**[/COLOR] 10.0, 10.1 (loved the professional GNOME of 10.1, but left it after my computer couldn't handle YAST and update slowness...I'm sure it got better)

[COLOR="Sienna"]**Ubuntu**[/COLOR] Breezy, Dapper, and Feisty (impressed with every release and love the 1 Disc install)

[COLOR="RoyalBlue"]**Fedora**[/COLOR] 5, 6  (simple but complete GNOME environment like Ubuntu, plan to try the later editions...one of my favorite installs)

**PC**[COLOR="Blue"]**LinuxOS**[/COLOR] 0.93 (impressed by all included codecs and added Mandriva CC goodness)

[COLOR="Lime"]**Linspire**[/COLOR] 5.0, [COLOR="MediumTurquoise"]**Freespire**[/COLOR] 1.0 (the old CNR was good while it lasted and so were the legal codecs...just hated how slow development was)


Others briefly tried but not necessarily installed: Puppy, DSL, Sugar (Fedora for kids ;-)), Mint, Ulteo (whatever happened to that?), MEPIS, Knoppix. 


OtherOS

[COLOR="Red"]Freesbie[/COLOR] Live FreeBSD

[COLOR="DarkOrchid"]Solaris 10[/COLOR] (took forever to install...ahh! loved the Java Desktop aka refined GNOME)

---

### Post by RAV TUX on 2007-09-30
> **Docula79 said:**
> Hi. I have only been using linux around 3 months now. I use Ubuntu feisty. (My main distro. Love it). I have played about with SLAX but have settled on DSL (Damn small) for my portable pen drive linux distro. I especially like the stats that are displayed on the desktop on DSL. Been thinking about downloading suse but have been told its a bit advanced for me. Im still getting to grips with basic terminal commands. Very impressed with linux in general though. I wont go back to windows EVER. :-)Try Wolvix for your pen drive.

---

### Post by anemptygun on 2007-09-30
Mandriva is pretty nice. Also try out Arch linux. If you like desktop effects...

SABAYON

---

### Post by stuh84 on 2007-09-30
I've tried a fair few, more than I care to, and probably can remember, but only a few have really impressed me. In terms of the ones which didn't stick around too long, and aren't worth going into too much, I'll say

Dynebolic, Arch, Knoppix, DSL, Ubuntu Studio, Red Hat, Slackware, Xubuntu, Kubuntu, and many many others that I cant think of right now.

The notable ones for me are as follows

Ubuntu - Still my favourite non-Mac OS. Not everything works out of the box, not everything is configured, some things take more work than in other distros, but it is my comfort zone. I feel at home in Ubuntu, and know of a way of doing most things I need to in it. I'm not a fan of Kubuntu because me and KDE have never got on, and Xubuntu, the way it is configured anyway, is just Ubuntu made for slow PC's, and I dont have any particularly slow PC's.

Fedora - I kept trying it in virtual machines and the like, and never got on with it for some reason. However, I decided one day to install it fully on my laptop, and its now what I boot into a lot of the time. Its polished (better font rendering I find than Ubuntu), and it is really well specced, essential programs and a bit of faff, I like it a lot, 3rd favourite OS without question.

PCLinuxOS - Seems okay, but all of what it says it configure out of the box, I know how to configure myself in other distro's anyway, so it only saves me about 5 minutes on first install anyway. Nothing to get excited over. The KDE implementation is nice, but I still dont like KDE that much.

Mandrivia - Similar to PCLinuxOS minus the not having to configure much. It is nice though, for what it is, just not my bag.

SuSe - Were it not for YaST, I think this is the best KDE distro, very polished, looks great, feels held together better than nearly every distro I've tried (in terms of consistency), but I cannot stand YaST, way too bloated.

Sabayon - Would love to use it more, but it doesn't like my laptop :(, very pretty and full of fun though


Put it simply, I'm a Gnome kind of guy, and Ubuntu has what I like in it, as does Fedora. All other distro's I've tried just don't match up for one reason or another.

---

### Post by screaminj3sus on 2007-09-30
Fedora - First distro I tried (Core 4 I think?) We decided to try and install it on an old pc of a friends, that was an experiance. Almost nothing worked, yum hardly worked at all, i didn't know anything about linux and ended up putting XP back on it.

Ubuntu- Had pretty much forgotten about linux, but I kept seeing alot of stuff about the release of dapper. I researched it alot and figured out I could try and dual boot with it. I used it for a while but decided I just didn't like it as much as XP and uninstalled it.

OpenSuSE: I tried 10.1/2, i really liked the gui and it's overall polish, but updates were a NIGHTMARE they were so slow and didn't work, also it takes like 2 minutes to boot it which is ridiculous.

PClinuxOS- Really liekd this one. My first KDE distro, very fast and polished. But things like unfixable HORRIBLE font rendering, and issues with my ipod made me stop using it.

Overall I always come back to ubuntu, I sued feisty for a while but bugs like CD ripping preferences not working right, and compiz running horribly slow made me go back to vista, right now using gutsy on my other drive and it's the ebst I've tried so far.

---

### Post by xArv3nx on 2007-09-30
Just a list.

NOTE: I'm not counting version, so I'll just say Mandriva instead of Mandrake 10.2, then Mandriva 2007, etc.

PCLinuxOS
Ubuntu
OpenSUSE
Fedora
Sabayon
Mint
Debian
Mepis
Mandriva
Damn Small
Zenwalk
Gentoo
Knoppix
Kubuntu
Puppy
Arch
Vector
Freespire
DreamLinux
Sidux
Ubuntu Studio
Xubuntu
Elive
PC-BSD
Ubuntu CE
Foresight
Xandros
SAM
Nexenta
Pardus
Linspire
Novell SLE
Gparted
VLOS
Linux XP
Ulteo
Klikit Linux

^^All but two of these are just from me looking at the Distro Watch rankings and finding what I've tried. VLOS + Klikit Linux = not in top 100.

---

### Post by RAV TUX on 2007-09-30
> **xArv3nx said:**
> Just a list.

NOTE: I'm not counting version, so I'll just say Mandriva instead of Mandrake 10.2, then Mandriva 2007, etc.

PCLinuxOS
Ubuntu
OpenSUSE
Fedora
Sabayon
Mint
Debian
Mepis
Mandriva
Damn Small
Zenwalk
Gentoo
Knoppix
Kubuntu
Puppy
Arch
Vector
Freespire
DreamLinux
Sidux
Ubuntu Studio
Xubuntu
Elive
PC-BSD
Ubuntu CE
Foresight
Xandros
SAM
Nexenta
Pardus
Linspire
Novell SLE
Gparted
VLOS
Linux XP
Ulteo
Klikit Linux

^^All but two of these are just from me looking at the Distro Watch rankings and finding what I've tried. VLOS + Klikit Linux = not in top 100.

Thats it? ;)

I believe klikit is not listed on DW because they are on a waiting list and have not paid for an ad to be taken seriously and bumped up.

For Klikit and others you need to go to [Distropedia]("http://cafelinux.org/distropedia/").

---

### Post by odiseo77 on 2007-09-30
*buntu (mainly Ubuntu)
Debian
Elive
Dreamlinux
Fedora Core
Slackware
SuSE
Knoppix
Puppy
Mandriva (years ago when it was named Mandrake)
Gentoo
Slax
Gparted
DSL
PHLAK

Maybe I'm missing something

Other (not linux):
PC-BSD (didn't like it)
FreeBSD (like it, still learning it).

---

### Post by ddrplayer512 on 2007-10-01
Fedora 5
Ubuntu
openSUSE 10.2
Fedora 7
PCLinuxOS
Gentoo, only up to live cd install though because one mistake and I trashed my Windows partition.
Debian Etch
Kubuntu
Arch Linux
DSL
...and... that's about it.

My favorites are openSUSE 10.3 RC (Because of Buisness focuses) Fedora 7(Loved the general feel of the GNOME desktop and Ubuntu(loved the community).

---

### Post by Caffeine_Junky on 2007-10-02
Well, I had my first taste of linux when Ubuntu 5.04  was released.  I was new to computers at the time and I was using Win98SE. (I think)
So the linux (Ubuntu) system was hard to get a grip-on at the time.

:lolflag:( I remember now that I was trying to install .debs by "doubleclicking" them !! haha,.. I didnt find synaptic the first time around) :p

Ahhhh, memories!! 

Anyhoo, ..I returned to linux in July this year (07), ..and since then I have tried:  (tried means run the live cd and installed to HDD, in most cases )

Win98SE
Win Millennium
Win XP

FreeBSD 6.2 
Mandriva 2007
Kubuntu 7.04
openSUSE 10.2
Mint 3.0
Puppy
Fedora 7
Simply Mempis
Gentoo
Debian
Knoppix
Mint
Slax
Dyne
PClinuxOS
Vector
Ubuntu 7.04
Arch
Elive Gem
Wolvix
Sidux
PCBSD
Sabayon
gOS

---

### Post by j.miller565 on 2007-10-03
Well I've tried:

SuSe 10.2
Kubuntu 6.10, 7.04
Sabayon mini 3.3b
Sabayon 3.4f
Fedora Core 6
Fedora 7
Zenwalk
PCLinuxOS
Linux Mint 
Ubuntu 6.06, 6.10, 7.04
Elive Gem
Gentoo


I want to try Debian and Slackware soon lol

---

### Post by Armadillo Kilr on 2007-10-03
ive tried the following:

-ubuntu 7.04
-ubuntu ultimate edition 1.04
-ubuntustudio
-fedora core 6
-mandriva (one/spring) 2007

and im still experimenting so the list shall grow :guitar:

---

### Post by Circus-Killer on 2007-10-03
well, lets see. here is the ones i've tried.....with my personal opinion as a rating:

[LIST]
[*]Coral Linux (0/5)
[*]Red Hat (2/5)
[*]Mandrake (before it became Mandriva) (4/5)
[*]Gentoo (4/5)
[*]Fedora Core (3/5)
[*]Slackware (1/5)
[*]Ubuntu (5/5) (my current distro of choice)
[/LIST]

---

### Post by Mr. Dude on 2007-10-03
I currently use Ubuntu for the family desktop, Fedora for my desktop, Gentoo/Debian for my laptop, and Fedora for my brother's laptop.


I've messed around with Mint Linux and the early Red Hats, and some Corel Linux thing that I never bothered with.

I had a lot of trouble with Gentoo when I first started out, and Corel refused to get past the bootloader, but this was years ago on a rubbish PC.

---

### Post by GerryB on 2007-12-15
> **RAV TUX said:**
> Ok after more trials of Linux Distros I have decided there are only two I will use on a regular basis, installed on my harddrive in 2 different boxes.

1. Ubuntu
[http://www.ubuntu.com/](http://www.ubuntu.com/)

2. Yoper
[http://www.yoper.com/](http://www.yoper.com/)

while Dreamlinux Studio Edition is great especially if you want to build your own Linux Distro with their MKDistro tool, it is mostly usefull as a live CD.
[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

Same for Morphix 0.5-pre4 Gnome.
[http://www.morphix.org/index.php?option=com_content&task=view&id=39&Itemid=59](http://www.morphix.org/index.php?option=com_content&task=view&id=39&Itemid=59)
:mrgreen:

Every thing you said about Dreamlinux is true and some. I'm posting from it right now, installed, listening to a great radio station on Streamtuner. It's a great distro, super easy to work with. I was extremely surprised when I found it. Everything works right out of the box, even music videos on Yahoo no less, and especially ripping and recording radio streams. It's one of the best if you don't want to work too hard at getting things to work.

---

### Post by astromech on 2007-12-15
Mepis 3.4 ,6.5

Ubuntu
Kubuntu
6.06,7.04

Xubuntu 7.04 (currently my fave)

7.10- only live disc (intsall on next machine)

SuSe

Knoppix - instead of dual booting and for online purchases.

Vector

Zenwalk

Dreamlinux 

Fedora

Debian Etch KDE

Freespire

DSL

Puppy

PCLinuxOS - Somehow I like the .93 better than 2007 neither  worked right with my monitor and amarok kept cutting out.Too bad it's nice other than that.

I'm loving Xubuntu 7.04 Thank you to those who helped make it !

---

### Post by screaminj3sus on 2007-12-16
Fedora(6/7/8)
Suse(10.1/10.2/10.3)
Mepis
Foresight 
Mint(Celena/Darnya)
PCLOS(2007)
Mandriva(2008)
Xubuntu (7.10)
Ubuntu(6.06/6.10/7.04/7.10)
Kubuntu(6.10/7.10)

Sadly In have yet to be able to replace windows.

---

### Post by nerval on 2007-12-16
Chronologically...

- Slackware
- Suse
- Yoper
- Debian
- Gentoo
- Ubuntu
- Pardus
- Ubuntu...

Honest opinion about which is the best ? None.

The world unfortunately hasn't reached a point where to create a perfect os. Apple sux because you can't use shitloads of programs with it, windows sux because it freezes all time, linux sux because 1- apple reason, 2 - to accomplish all upgrades you have to actually format your system, 3 - most of good programs are uncontinued, 4 - i don't know if it is for web hits; but no distro is willing to actually publish a distro for eternal use, 5 - using linux reminds me actually I'm poor and can't purchase a new computer.

---

### Post by zesty on 2007-12-17
I'm currently on Ubuntu 7.10.  It was the easiest to setup for me.  I plan to dual boot another distro with KDE but haven't picked one yet.  In the past I've tried (in no particular order):

Puppy
DSL
Knoppix
Gentoo
Kubuntu
Xubuntu
Slackware
Fedora (never got it fully installed)
Xandros

I'm sure there's more I can't remember

---

### Post by chris4585 on 2007-12-18
i've tried:
Ubuntu 6.06
Ubuntu 6.10
Ubuntu 7.10 (my favorite)
Dreamlinux
Freespire
Sabayon 3.04
Opensuse 10.x (i forgot which one i think 10.3)
Fedora 6
gOS

Those are ones i've actually installed

but i've tested:

Symphony OS
Puppy
DSL
Slax
Mint
Mandriva
gentoo
vixta (fedora based)
PCLinuxOS (i was expecting more from this one but, during installation, there wasnt a back button.. of course when i needed it so i had to restart the installation over again.)
Linux xp
knoppix

---

### Post by new2*buntu on 2007-12-18
Puppy (5/5) I think that it is the best minimal distro.
Ubuntu (4.5/5) It was almost perfect but a few issues made me look for something else. Also, I did not like the brown theme (just my personal taste).
Xubuntu (4/5) Good, but not great.
Debian (3/5) My experience with the Debian netintall was not the great. Only kept it for one day.
Fedora 8 (unrated) I was never able to get it to boot.
Mint Main Edition (5/5) One of the most polished distros I have found, which worked out of the box on my system.
Mint XFCE (6/5) Same as the Main Edition, but with the speed of XFCE.

---

### Post by wolfen69 on 2007-12-18
> **GerryB said:**
> Every thing you said about Dreamlinux is true and some. I'm posting from it right now, installed, listening to a great radio station on Streamtuner. It's a great distro, super easy to work with. I was extremely surprised when I found it. Everything works right out of the box, even music videos on Yahoo no less, and especially ripping and recording radio streams. It's one of the best if you don't want to work too hard at getting things to work.

i agree, but let's not forget Mint or Sabayon when talking about an "all in one" distro. but anyone of them will get the job done in a pinch.

---

### Post by LinuxGuy1234 on 2007-12-20
Windows XP.................................[COLOR="Red"]Sucks, got viruses[/COLOR]
Ubuntu........................................[COLOR="Lime"]OK[/COLOR]
Debian.........................................[COLOR="Lime"]OK[/COLOR]

Next up:  Arch.

---

### Post by Rutabega on 2007-12-20
SUSE Personal 9.1
Ubuntu Edgy-Feisty-Gutsy 
Zenwalk
Fluxbuntu 
Antix 

I am currently using Antix.

---

### Post by yabbadabbadont on 2007-12-20
Too many to list, including some that haven't existed for years.  (I've been using Linux for about 12 years)

---

### Post by kelvin spratt on 2007-12-20
Virtually all of them lots don't work some reasonable Elive Gem the best for doing work on. Arch for its speed its the only KDE distro I like. My own Ubuntu based E17 non of the other E17 variants come close.

---

### Post by manmower on 2007-12-21
> **kelvin spratt said:**
> Arch for its speed its the only KDE distro I like.

Arch is not a "KDE distro".

---

### Post by LinuxGuy1234 on 2007-12-27
> **manmower said:**
> Arch is not a "KDE distro".

If you do as root (in Arch):
```
pacman -S kde
```
it will be.

---

### Post by maybeway36 on 2007-12-27
Used Kubuntu for a long time, then switched to Mint for a while, and now I'm on Debian Testing. I've tried zillions of others, but I admire Debian for its robust core.

---

### Post by molom on 2007-12-28
I've tried:
Ubuntu (Good, but no out of the box experience) 
Kubuntu (Didn't like it)
Xubuntu (Like it more than ubuntu, but the same out of the box problem)
Linux Mint (Love it, its the best)
elive (Didn't like it at all because it was completely broken, maybe next release it will be better)
gOS (Better than elive, but still some few issues)
geubuntu (Very nice, but didn't like the artwork much and there were minor bugs)
Suse (Hated it)
Mandriva (Hated it)
PCLOS 2007 (Best KDE distro so far, but I don't like KDE)
Knoppix (Its been a while, but it was nice)
Zenwalk (Had a bad wireless experience, but then again I wasn't experienced myself during that time)
Ubuntu Studio (It was nice)
Linspire (The worst)
Xandros (It was nice)
DreamLinux (I found the artwork ugly, hated the dock and found some bad bugs)

I like Linux Mint (gnome) the most and use it the whole time, but e17 is my favourite DE.

Cheers,
molom

---

### Post by Dr Small on 2007-12-28
Ubuntu ............... [COLOR="SeaGreen"]Works, and I use it[/COLOR]
Kubuntu ............. [COLOR="SeaGreen"]Works[/COLOR]
Edubuntu ............ [COLOR="Red"]Couldn't get it installed[/COLOR]
Xubuntu ............... [COLOR="SeaGreen"]Works[/COLOR]
Fluxbuntu .............. [COLOR="SeaGreen"]Works[/COLOR]
Fedora .................. [COLOR="Red"]Couldn't get it to work (on this machine)[/COLOR]
gOS ...................... [COLOR="SeaGreen"]Works[/COLOR]
PuppyLinux ............. [COLOR="SeaGreen"]Works[/COLOR]
FeatherLinux ............. [COLOR="SeaGreen"]Works[/COLOR]
LinuxMint .................... [COLOR="SeaGreen"]Works[/COLOR]
Gparted LiveCD ............. [COLOR="SeaGreen"]Works[/COLOR]
TrinityRescueKit ............. [COLOR="SeaGreen"]Works[/COLOR]
Ubuntu CLI CD ................ [COLOR="SeaGreen"]Works[/COLOR]

---

### Post by molom on 2008-01-06
If anybody is interested in E17 distros, Linux Mint E17 will be released this month.

Check this website for details, updates and so on ( [http://linuxminte17.wordpress.com/](http://linuxminte17.wordpress.com/) ). The website will soon have screenshots, video tutorials and more unofficial artwork.

Cheers,
molom

---

### Post by SomeGuyDude on 2008-01-06
My list is now up to...

Ubuntu - KDE/GNOME/E17
Kubuntu
Fedora Core 4
Fedora 8
Xandros
PCLinuxOS
Sabayon
Mandriva 2007
Opensuse 10.3
Linux Mint
DreamLinux

Plus a version of Red Hat I got with a book in like 1999, but I don't count that.

---

### Post by mike^_^ on 2008-01-07
gentoo
arch
ubuntu dapper-hardy
fedora 6-8
suse 9-10
opensuse 10.3
xubuntu feisty
DSL
puppy
some version of redhat that came with a book my dad got me
linux from scratch 
couple distro's based on the open solaris kernel, i cant remember which ones
debian

---

### Post by scizzo on 2008-01-07
Ubuntu Hardy Heron (Alpha X)
Debian (sid) 
Red Hat 
Sabayon 3.4e
BestLinux
Slackware
Gentoo
OpenSuse

---

### Post by jeffus_il on 2008-01-07
Suse
Dsl
Gentoo
Mandrake
RockLinux
Knoppix

---

### Post by Borbus on 2008-01-07
Red Hat, years ago, before Fedora and RHEL, can't remember which release it was, I didn't use Linux for ages after my RH box died.
Fedora, core 2 was the first one I used, this was my desktop distro for a while, this was before I got a good box and got into gaming... I started using Windows after this.
I got a dedicated server, I started using CentOS on it. Then I later moved to Debian.
Then I installed Arch Linux on my desktop, I used it for a while, with Gnome. Then I tried to install XGL, which was quite unstable back then and messed something up badly. I couldn't be bothered to try to fix it so I tried Ubuntu. It was pretty good. Then I went back to doze for a while, now I'm back on Ubuntu again. Still using Debian on servers all that time.

I also used SLED at some point, can't remember when, and I've also used other unix-like OSs like FreeBSD and SunOS.

---

### Post by Linuxratty on 2008-01-07
Would someone please tell me how to delete multiple posts?
I do not see a delete button.

---

### Post by Linuxratty on 2008-01-08
]Every thing I've had :
Windows 3.0,95,98,XP. OSX 
Linux:
Linspire,Freespire Mint (ran live cause Mint would not install.)
 Ubuntu,Kbuntu,(Both feisty)
 fedora8 ,GoOS(live),
Klikit,
Mepis7.
Of all of these,my favorites are,in fact,the last two.
 I'm running Mepis7 now and waiting for Klikit stable as I had a bit of trouble with the bets.

---

### Post by mips on 2008-01-08
Red Hat
K/Ubuntu
Debian
Mepis
Dreamlinux
DSL
Puppy
Sidux
OpenSuse
Cherry
Linux Mint
Gentoo
Sabayon
Knoppix
Pardus
Arch (current)


Not Linux but: OpenBSD, OliveBSD, FreeBSD, PC-BSD, DesktopBSD, NetBSD, Solaris

---

### Post by sujoy on 2008-01-08
Till now I have tried out:

Red Hat
Fedora Core 6
Open Suse 10.2
Ubuntu 7.04
Slackware 12
Dreamlinux
Linux Mint
Mandriva 2008 64bit
Gentoo (current)
Debian Etch
Ubuntu 7.10 (current)
Zenwalk


waiting to try out ....
Fluxbuntu
Arch Linux

---

### Post by Akkeasd on 2008-01-08
Ubuntu only.

But I want to try some other distro of Linux, what you suggest to try for "not-so-noobie" user?

---

### Post by handy on 2008-01-08
Red Hat
Mandrake
Suse
Caldera
Linspire
Debian
(K)(X)Ubuntu (current)
Sabayon (current)
Gentoo (kinda)
Arch (less kinda)
DreamLinux
PCLOS
Knopix
gNewSense
Some other old distro's that I can't remember...

Non-linux
Nexenta, Solaris, PC-BSD, Zeta, Mac OS 7(9) Panther & Leopard (current)
Amiga... :lolflag:  Where it all began for me very early in 1987.

We'll leave the windows closed eh?!

---

### Post by Nevon on 2008-01-08
Ubuntu
Arch Linux
Linux Mint
Debian
Fedora
OpenSuse
DreamLinux
Xbuntu
Mandriva
Sabayon

That's all, I think.

---

### Post by handy on 2008-01-08
> **Akkeasd said:**
> Ubuntu only.

But I want to try some other distro of Linux, what you suggest to try for "not-so-noobie" user?

Have a look at [***_distrowatch_***]("http://distrowatch.com/"), it gives you the top 100 non-MS OS's/distro's, you have to scroll down the page some & the list is on the right hand side.

Sabayon is good & easy, DreamLinux is nice too, so are lots of the others... ;-)

---

### Post by Elvish Legion on 2008-01-08
> **Akkeasd said:**
> Ubuntu only.

But I want to try some other distro of Linux, what you suggest to try for "not-so-noobie" user?

If the command line doesnt scare you Arch is a good one

---

### Post by Akkeasd on 2008-01-08
Thanks handy, that is grrreat site. :)

I don't know **yet** what distro is "the one" :D

But I'm gonna find it out soon. 8)

---

### Post by articpenguin on 2008-01-08
i have tried 

Fedora
opensuse
mandriva
sabayon
pclinuxos

i always seem to come back to kubuntu though XD

i am going to try freespire in virutalbox when my new ram comes.

---

### Post by qpieus on 2008-01-08
(k)(x)ubuntu 5.10, 6.06, 7.10
sam
pclinuxos 2007
pclinuxos 2008 minime
vector
dreamlinux
dsl
puppy
slax
sabayon
debian
zenwalk
arch
knoppix
sidux
nexenta
feather
deli
BeaFanatIX

---

### Post by Seguaro on 2008-01-08
_Linux_:
Slackware
Ubuntu
Kubuntu
Xubuntu
DSL
DSL-N
E-Live

_Non Linux:_
FreeBSD
SysV
CP/M (this was the first OS I ever used)
MS-DOS (forgot all the different versions)
PC-DOS 7 (This was IBM's version of DOS)
Windows 2.0
Windows 3.1
Window 95
Windows 98/SE
Windows ME
Windows XP
Windows Vista

---

### Post by allforcarrie on 2008-01-08
DSL
Fedora
Redhat
geento
mephis
slax
ubuntu :)
mint  :)

---

### Post by Bungo Pony on 2008-01-09
Ubuntu: First one I've tried, I'm using it, and I'm liking it. Feisty was my fav though. Actually, I'm using UbuntuStudio. Also tried Ubuntu with E17 installed, which I also like. If I wasn't so attached to Gnome, I'd go with E17.

Kubuntu: Found KDE to be glitchy and slow

Xubuntu: Didn't really do anything for me.

Fluxbuntu: Couldn't get it to work.

DSL: Absolutely love it! It really gives old PCs a new life!

PCLinuxOS: Runs really nice, KDE's done nice, but I don't really like KDE to begin with.

GeeXboX: Blech. Runs entirely in RAM, but I don't like the media player.

Puppy: Nice for those who like Windows-ish distros, but I didn't like how drives mounted, nor the lack of security.

TinyMe (PCFluxboxOS): Nice, easy install, looks good, runs well on older hardware. I'm actually becoming quite fond of it!

---

### Post by Pogeymanz on 2008-01-10
Windows3.1
Windows95
Windows98(SE)
WindowsXP
(Xu)(Ku)(U)buntu  ---I love Xubuntu the most; XFCE is so clean, but not bland.
openSUSE
Mandriva
DSL
Fluxbuntu

---

### Post by dolphin_oracle on 2008-01-11
Ubuntu 6.10 (still running)
Flubuntu
Xubuntu 6.10, 7.04, 7.10
Wolvix
Antix (mepis w/ fluxbox)-current favorite

---

### Post by Mithrilhall on 2008-01-11
Mandrake (before the renaming to Mandriva)
Fedora
OpenSuse
CentOS
Slackware
Gentoo
Yoper
Ubuntu
Kubuntu
Xubuntu
Debian
Sidux

I currently run Kubuntu @ home but I'll be switching over to Debian soon.

I just tried Sidux today and I'm liking it so far.

---

### Post by seanc7 on 2008-01-11
I started with Ubuntu.

Then I Kubuntu and Xubuntu.  Went back to Ubuntu.

Then I started distro hopping the last month

Sabayon
Gentoo
Mint
Fedora 7
Debian

Currently running PCLinuxOS.

I'm downloading Fedora 8 now.

I'll see how that goes for a couple of months. We use it at work for a few things, it looks good there.

When Hardy is released I'll do a reinstall to try it out.

---

### Post by kool_kat_os on 2008-01-11
Ubuntu 7.10
Ubuntu 7.04
Ubuntu 7.10 Server
Linux Mint....Errors...More Errors....And guess what?...Even more errors

---

### Post by labeeb97 on 2008-01-21
Itried ( in order) Knoppix,Linspire five-0, and Ubuntu

---

### Post by scorp123 on 2008-01-21
> **seanc7 said:**
> I'm downloading Fedora 8 now. Don't bother. Fedora 8 is buggy like hell. On some of my HP laptops I can't even boot it without some workaround. It won't boot in VMware without a workaround (the virtual SCSI adapter doesn't get recognised) and if you change the package selection during installation you risk a core dump, which means the installer will instantly crash and you can start from scratch again.

I was able to reproduce this series of odd behaviour on a couple of my test machines (where other distros work tip top) so I am pretty sure it's not me. :)

---

