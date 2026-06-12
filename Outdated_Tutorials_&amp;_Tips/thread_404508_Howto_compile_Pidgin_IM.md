---
title: "Howto compile Pidgin IM"
date: 2007-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by TravisNewman on 2007-04-08
As you may know, Gaim has been renamed to Pidgin IM. Beta7 source is now available in testing. The only difference I see is the interface:
[http://bomahy.nl/hylke/blog/?p=25](http://bomahy.nl/hylke/blog/?p=25)
I don't guarantee that this won't break your system, so please be sure you make any necessary backups.

to install any dependencies you need to compile Pidgin, run the following:

```
sudo apt-get build-dep gaim
```

autogen also needs some files:
```
sudo apt-get install libglib2.0-dev
```

Go to the pidgin dev site to get the code:
[http://developer.pidgin.im/](http://developer.pidgin.im/)
extract the source, cd into the folder, and execute
```
sh autogen.sh
```
I got some warnings at this step but nothing that prevented me from continuing.

after that is finished, run
```
make && sudo make install
```
When it's ready to install it will ask for your password to copy the files over.

---

### Post by Dual Cortex on 2007-04-08
Thanks, got it compiled. Took quite a bit to do so...
Not much different, as you said.

Any idea if removing Gaim will kill any dependencies?

---

### Post by TravisNewman on 2007-04-08
I don't know... but since gaim and its libraries have changed names, I don't think there would be a problem with leaving the old gaim around.

---

### Post by ubuntu27 on 2007-04-08
Can't find the source. Can someone give me a direct link?

---

### Post by TravisNewman on 2007-04-08
> **ubuntu27 said:**
> Can't find the source. Can someone give me a direct link?
One direct link coming up!
[http://www.bomahy.nl/hylke/pidgin-mtn-snapshot20070408.tar.gz](http://www.bomahy.nl/hylke/pidgin-mtn-snapshot20070408.tar.gz)

It's the one on the page that says it's the "Developer Snapshot"

---

### Post by vicox on 2007-04-08
The site is down (probably because it got digg'ed).
Can you upload the snapshot please ...

---

### Post by TravisNewman on 2007-04-08
Well, I didn't save it, so I'm making a new one :)
I edited out some group names and screen names to protect privacy

---

### Post by vicox on 2007-04-08
Thanks, but ... i meant the source code :D

---

### Post by dyous87 on 2007-04-08
yes i want to compile pidgin im as well but i cannot get my hands on the source code. :(

---

### Post by smbm on 2007-04-08
Anyone got a deb handy?

I'm temporarily on dialup so downloading all the development stuff will take a while.

Thanks

---

### Post by dyous87 on 2007-04-08
I would gladly make a .deb for you if i had the source code, the server has been down for some time now though. :(

---

### Post by smbm on 2007-04-08
Thankyou.

If I'm ever in New York or your ever in the South West UK I'll buy you a pint.

---

### Post by Dual Cortex on 2007-04-08
Eh, I deleted the tar but still have the extracted sources. Wonder if I can still make the deb even though I already 'make install'ed it.

---

### Post by smbm on 2007-04-08
You should be able to checkinstall it I guess.

Did you have to build libpurple too?

---

### Post by Jarn on 2007-04-08
You can. All you need to make a deb is the sources. You can just type checkinstall and it will make a deb for you.

---

### Post by Dual Cortex on 2007-04-08
By the end:
> Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: y



> dpkg-deb: parse error, in file `/var/tmp/piKAepLfWBnjYcoOHjacZ/package/DEBIAN/co
ntrol' near line 4 package `pidgin':
 newline in field name `Applications/Internet'


---

### Post by smbm on 2007-04-08
Bummer

---

### Post by Dual Cortex on 2007-04-08
hmmm the "Group" section when building the deb for some reason showed something like:

"Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet"


In fact, this is what it says:

> This package will be built according to these values: 

0 -  Maintainer: [ root@mintDellDesktop ]
1 -  Summary: [ A GTK+ based multiprotocol instant messaging client
Development headers, documentation, and libraries for Pidgin
Bonjour plugin for Pidgin
Lotus Sametime plugin for Pidgin using the Meanwhile library
Mono .NET plugin support for Pidgin
SILC (Secure Internet Live Conferencing) plugin for Pidgin
Tcl scripting support for Pidgin
A text-based user interface for Pidgin ]
2 -  Name:    [ pidgin ]
3 -  Version: [ %pidginver ]
4 -  Release: [ 0%{?beta ]
5 -  License: [ GPL ]
6 -  Group:   [ Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ pidgin ]
9 -  Alternate source location: [  ]
10 - Requires: [ perl
pkgconfig, pidgin = %{epoch}
pidgin = %{epoch}
pidgin = %{epoch}
pidgin = %{epoch}
pidgin = %{epoch}
pidgin = %{epoch}
pidgin = %{epoch} ]



Fixing that reports another error:

> dpkg-deb: parse error, in file `/var/tmp/YQPTPHBVajkLrGagfGJbR/package/DEBIAN/co
ntrol' near line 9 package `pidgin':
 field name `pkgconfig,' must be followed by colon


---

### Post by dyous87 on 2007-04-08
still down :( gah...they should just put it on sf!

---

### Post by smbm on 2007-04-08
I think there are some people towards the end of this thread who have it:

[http://ubuntuforums.org/showthread.php?t=403857]("http://ubuntuforums.org/showthread.php?t=403857")

It's just a question of getting one of them to host it.

---

### Post by Dual Cortex on 2007-04-08
distclean'ed it

edit: use taylor's

---

### Post by LookTJ on 2007-04-08
[http://unpluggedpodcast.dreamhosters.com/files/pidgin-20070408.tar.gz](http://unpluggedpodcast.dreamhosters.com/files/pidgin-20070408.tar.gz)

---

### Post by kernelsandirs on 2007-04-08
Thanks Taylor, Building it now...
only needed libtool and intltool w/deps

Built great!!!
I still get this strange error I got on b6 as well about "unable to add"
"could not add the buddy 1..." something about most common reason maximum number of allowed buddies in list

---

### Post by gschoper on 2007-04-08
Great how-to! It compiled, installed and runs fine. 

It appears as though it's using ~/.gaim to store it's preferences and may step on your old gaim config, so it may be a good idea to back-up that dir before running in case you want to revert back to gaim without any issues:

```
cd ; tar cvjf gaim_backup.tar.bz2 .gaim
```

gschoper

---

### Post by vicox on 2007-04-08
I built a deb package with checkinstall:

[http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb](http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb)

You have to remove the package gaim first (sudo apt-get remove gaim) because I don't know how to define conflicts with checkinstall.
It was built on edgy, but seems to work on feisty too.

---

### Post by TravisNewman on 2007-04-09
I'm not even sure it conflicts. I have them both installed and can run them both.

---

### Post by vicox on 2007-04-09
There are some files, which are used by both. For example usr/share/dbus-1/services/gaim.service .

So when the pidgin-package tries to write its files, dpkg bars it from doing that because some of these files already exist and are being used by the gaim-package.

I think when you "make install", it simply overwrites the files and gaim doesn't break because they are probably the same.

---

### Post by mrgnash on 2007-04-09
Thanks :) I like the new interface.

---

### Post by DC@DR on 2007-04-09
Could someone shine a light on new features the final Pidgin 2.0 will have, so I can see if it's worth updating or not, thanks :-)

---

### Post by gbesso on 2007-04-09
Here's an amd64 package in case anyone's interested.
[http://gbesso.gold-host.co.il/repository/binary/p/pidgin_2.0.0beta7-1_amd64.deb]("http://gbesso.gold-host.co.il/repository/binary/p/pidgin_2.0.0beta7-1_amd64.deb")
EDIT: fixed url, it was broken for a while.

---

### Post by zarathustra on 2007-04-09
So what happens with the old subversion repository on Sourceforge?

---

### Post by gschoper on 2007-04-09
> **panickedthumb said:**
> I'm not even sure it conflicts. I have them both installed and can run them both.

I ran Gaim 2 beta 3.1(??) after running Pidgin and lost  my Yahoo account info. Just a suggestion to backup. Better safe than sorry.

gschoper

---

### Post by tehkain on 2007-04-10
I get this:
trying to overwrite '/usr/share/dbus-1/services/gaim.service (then a broken pipe error)
So is there anyway to remove gaim without ubuntu-desktop? I just dont want 5 million packages listed as uneeded.(nvm screw meta packages)

---

### Post by WishMaster on 2007-04-10
> **vicox said:**
> I built a deb package with checkinstall:

[http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb](http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb)

You have to remove the package gaim first (sudo apt-get remove gaim) 

Works fine here !!

New icon-theme is boring though... Hopefully this 'pidgin'-thing will finally implement some Google Summer of Code and/or MSN-updates (sending custom emoticons, webcam, personal messages,...)

---

### Post by scooper86 on 2007-04-10
i have just compiled pigdin but i am using avant for my dock and i was using the gaim plugin to show my status in the dock but it has stopped working i wonder if anyone else is using it and can help me out, thanks.

---

### Post by maddbaron on 2007-04-11
i downloaded the deb and i am being told i have a broken pipe and it cant overwrite d-bus, apparently my gaim d-bus is bad anyone know how i can fix this please?

---

### Post by maddbaron on 2007-04-11
> **tehkain said:**
> I get this:
trying to overwrite '/usr/share/dbus-1/services/gaim.service (then a broken pipe error)
So is there anyway to remove gaim without ubuntu-desktop? I just dont want 5 million packages listed as uneeded.(nvm screw meta packages)

u got same problem i got

---

### Post by gbesso on 2007-04-12
[QUOTE=maddbaron]
[QUOTE=tehkain]
I get this:
trying to overwrite '/usr/share/dbus-1/services/gaim.service (then a broken pipe error)
So is there anyway to remove gaim without ubuntu-desktop? I just dont want 5 million packages listed as uneeded.(nvm screw meta packages)
[/QUOTE]
u got same problem i got
[/QUOTE]
you can either remove gaim, since pidgin replaces it: 
sudo apt-get remove gaim

or if you want to keep gaim in order to keep the ubuntu-desktop meta-package, you can install pidgin with the --force-overwrite option:
sudo dpkg -i --force-overwrite <deb file>

---

### Post by simplyw00x on 2007-04-12
Real men compile it from scratch from the monotone repo, having had to manually install monotone-0.34 from a debian package.

[http://developer.pidgin.im/wiki/UsingPidginMonotone](http://developer.pidgin.im/wiki/UsingPidginMonotone)

---

### Post by vicox on 2007-04-12
Real men compile monotone from scratch!

---

### Post by russellc on 2007-04-14
I don't get this Monotone crap. First off, why do we have to download a 184 MB file first? Secondly, I can't even mtn pull properly for some reason. Gives the following message.

```

mtn: doing anonymous pull; use -kKEYNAME if you need authentication
mtn: connecting to localhost
mtn: network error: failed to connect: Connection refused

```

Obviously connecting to localhost won't do anything for it. I don't understand what could be the problem. I followed the instructions exactly. SVN was working perfectly fine in the first place. If it isn't broken, don't fix it.

---

### Post by brohan on 2007-04-15
Follow [http://developer.pidgin.im/wiki/UsingPidginMonotone](http://developer.pidgin.im/wiki/UsingPidginMonotone) closer.

My issue is when I've got everything and I run configure I get
```
checking for GLIB... no
configure: error:

You must have the GLib 2.0 development headers installed to build Gaim.

```

I do have libglib2.0-dev installed, and compiled glib 2.12.11 and yet it still isn't working. Any ideas?

---

### Post by digital0129 on 2007-04-15
I am having trouble compiling so I was wondering if anyone had debs for dapper?

---

### Post by simplyw00x on 2007-04-16
> **vicox said:**
> Real men compile monotone from scratch!
Touché

> I am having trouble compiling so I was wondering if anyone had debs for dapper?
No .deb, but I'm using paco to produce a binary package. Upload soon.

---

### Post by simplyw00x on 2007-04-16
Ok, one freshly-baked pidgin dev version package. I'd recommend paco to manage it, but you can just untar it in /. YMMV.

(x86) [http://download.yousendit.com/9BD79F7A59BB46C6](http://download.yousendit.com/9BD79F7A59BB46C6)

---

### Post by Brucevdk on 2007-04-19
Excuse me if anything I say here is incorrect, I've only been using monotone for 10 minutes.

> **russellc said:**
> I don't get this Monotone crap. First off, why do we have to download a 184 MB file first?

Apparently,  using monotone means every individual developer has the entire development history stored locally. When you commit, you don't commit to a centralized server (as you do with SVN) but to your local database. This means any calculation is done on your computer so I guess it reduces the strain on the server for huge projects. You have to retrieve the complete history because of how version control inherently works:

> When a file is under version control, we also say that it is registered in the version control system. Each registered file has a corresponding master file which represents the file's present state plus its change history—enough to reconstruct the current version or any earlier version. Usually the master file also records a log entry for each version, describing in words what was changed in that version. (quoted from [Concepts of Version Control]("http://www.gnu.org/software/emacs/manual/html_node/VC-Concepts.html"))

With monotone developers could even act as servers themselves  ([see the monotone FAQ]("http://www.venge.net/mtn-wiki/FAQ")), exchanging data underling and then eventually deciding  to push their changes to the pidgin.im database. Or something like that...

> **russellc said:**
> 
Secondly, I can't even mtn pull properly for some reason. Gives the following message.

```

mtn: doing anonymous pull; use -kKEYNAME if you need authentication
mtn: connecting to localhost
mtn: network error: failed to connect: Connection refused

```

Obviously connecting to localhost won't do anything for it. I don't understand what could be the problem. I followed the instructions exactly. SVN was working perfectly fine in the first place. If it isn't broken, don't fix it.

In [UsingPidginMonotone]("http://developer.pidgin.im/wiki/UsingPidginMonotone") it is stated that you can just do a *mtn pull* from your working directory. However, this only seems to work if you've set pidgin.im im.pidgin.* to your default directory/branch (instead of localhost). You can do this like:

```

$ mtn pull --set-default pidgin.im im.pidgin.*
mtn: setting default server to pidgin.im
mtn: setting default branch include pattern to 'im.pidgin.*'
mtn: setting default branch exclude pattern to ''
[...]
```

I still have to read the documentation thoroughly to understand what the wildcard exactly achieves but now you can just execute an *mtn pull && mtn update* from your working directory.

---

### Post by PaulFXH on 2007-04-24
My experience with Instant Messaging is minimal.
However, I was persuaded by a young friend to set up an MSN account (she uses Windows).
So, I thought Pidgin would allow me to communicate with her from my (new) MSN account without having to switch out of Ubuntu.
I also saw this as an opportunity to impress her with the versatility of Ubuntu/Linux towards which previous attempts have not gone down too well (although the Beryl cube at least drew a few gasps of awe and wonder).
I got Pidgin installed without any problems and it works fine. But, it apparently doesn't allow voice communication through MSN.
Unfortunately, this has resulted in a very black mark against Linux in the eyes of my friend.

So, is that it...it just can't be done or has Pidgin got a trick up its sleeve?

---

### Post by simplyw00x on 2007-04-24
> So, is that it...it just can't be done or has Pidgin got a trick up its sleeve?
It has been promised many times but never delivered. I believe aMSN offers a more complete MSN-replacement, and might accomplish this.

On the other hand... MSN voice chat is *terrible*.

---

### Post by Kaobear on 2007-04-24
Well, I am running make install as we speak and everything seems to be going as planned for the most part.  I needed an additional dependency of libtool before I got going, but that was as easy as running apt-get install libtool.

Thanks for an early look at what looks under the hood to be a promising client.

---

### Post by PaulFXH on 2007-04-24
Thanks to simplyw00x for the reply.
Actually, aMSN 0.96 does not have voice chat.
However, I then came across [this thread]("http://http://ubuntuforums.org/showthread.php?p=2524202#post2524202") which supplies links for installing aMSN 0.97 which has voice support. Whether this means the full voice chat available in MSN or just voice clip stuff I don't know as yet as I'm having a little difficulty installing it.
Strangely, the aMSN homepage doesn't mention aMSN 0.97.

---

### Post by gamma on 2007-04-24
> **simplyw00x said:**
> Ok, one freshly-baked pidgin dev version package. I'd recommend paco to manage it, but you can just untar it in /. YMMV.

(x86) [http://download.yousendit.com/9BD79F7A59BB46C6](http://download.yousendit.com/9BD79F7A59BB46C6)

Can you please repost your deb? Thanks! :D

---

### Post by andrek on 2007-04-24
Download Pidgin from this link, 2.0.0-beta7 compiled for feisty fawn as .deb
[http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0beta7-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0beta7-1_i386.deb)

---

### Post by Gilson on 2007-04-25
Well, i compile from source, and all it's great, no errors, thanks for this :).

---

### Post by gamma on 2007-04-28
Can someone post an updated deb, andrek's version is slightly dated and there's a bug with the idle time, there's no option to base it off X (mouse movement). I don't want a bijillion source deps just to build this. D:

---

### Post by TravisNewman on 2007-04-30
Looks like they've released the official beta 7. I'll be compiling this tonight and updating my original post if there's anything different that needs to be done

---

### Post by jdhore on 2007-04-30
> **panickedthumb said:**
> Looks like they've released the official beta 7. I'll be compiling this tonight and updating my original post if there's anything different that needs to be done

i compiled it myself less than a hour ago and they updated some of the artwork, but installation is EXACTLY the same (though you can now use a tar.bz2 or a .rpm if you're in the mood to use alien), remember to make uninstall the old one :)

---

### Post by rezpekt on 2007-04-30
Compiling it at the moment. Hopefully without problems... It's my second time to compile anything  ever... :P

Yeah, it's working.

---

### Post by thebert on 2007-05-01
Has anyone been able to compile a deb of beta7? I was able to compile a deb but was unable to install it. Can the new beta be installed side by side with feisty's gaim beta6? The link to the deb above gave me dependency problems with the currently installed gaim.

---

### Post by killaray on 2007-05-01
ok so is there a way to remove gaim without it completely uninstalling ubuntu,,,, i do a sudo apt-get remove gaim and it says its removing ubuntu-desktop along with it... last time i let the go on for long it started removing system files and such and i had to reinstall ubuntu... any way to get gaim off alone?? also everytime i try to checkinstall something it fails while installin the deb... its a different story everytime and sometimes it doesnt even make the deb.. does anyone know wut that could be about?

---

### Post by foundation on 2007-05-01
I used synaptic and removed gaim-data and it gave me a warning too (Also one about nautlius-sendto) but I went ahead with it and nothing bad happened and I than installed Pidgin and it's all okay. D:

But I don't want to be responsible for your install exploding so I guess wait for someone else.

---

### Post by Kujen on 2007-05-01
> **killaray said:**
> ok so is there a way to remove gaim without it completely uninstalling ubuntu,,,, i do a sudo apt-get remove gaim and it says its removing ubuntu-desktop along with it... last time i let the go on for long it started removing system files and such and i had to reinstall ubuntu... any way to get gaim off alone?? also everytime i try to checkinstall something it fails while installin the deb... its a different story everytime and sometimes it doesnt even make the deb.. does anyone know wut that could be about?

Removing "ubuntu-desktop" does not uninstall ubuntu, or remove system files. Go ahead and remove gaim.

---

### Post by TravisNewman on 2007-05-01
I compiled the newest beta, without first uninstalling the old one, and it worked fine. I still haven't uninstalled gaim either, I just don't use it anymore.

---

### Post by thebert on 2007-05-01
panickedthumb,

Did you create a deb when you compiled?

---

### Post by esun819 on 2007-05-01
> **panickedthumb said:**
> I compiled the newest beta, without first uninstalling the old one, and it worked fine. I still haven't uninstalled gaim either, I just don't use it anymore.

same here =). i opened gaim by accident just now lol and that still works too.

just a tip for when you're compiling: you might want to run ./configure with **--enable-nm=yes**, to avoid having pidgin trying to login to all the servers before you're even connected to the net.

---

### Post by thebert on 2007-05-01
I get this error trying to install it after running checkinstall.


dpkg: error processing /home/rrichar1/Desktop/pidgin-2.0.0beta7/pidgin_2.0.0beta7-1_i386.deb (--install):
 trying to overwrite `/usr/lib/gcc/i486-linux-gnu/4.1.2/crtendS.o', which is also in package gcc-4.1

---

### Post by spanella47 on 2007-05-01
i'm getting this error when compiling it:

dpkg: pidgin: warning - conffile `etc/gconf' is not a plain file or symlink (= `
/etc/gconf')
dpkg: pidgin: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain f
ile or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing /home/spanella47/Desktop/pidgin-2.0.0beta7/pidgin_2.0.0be
ta7-1_i386.deb (--install):
 trying to overwrite `/usr/bin/nm', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)

any ideas?

---

### Post by durand on 2007-05-01
yup, same error here.

```

(Reading database ... 239734 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.0.0beta7-1_i386.deb) ...
dpkg: error processing pidgin_2.0.0beta7-1_i386.deb (--install):
 trying to overwrite `/usr/bin/ld', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 pidgin_2.0.0beta7-1_i386.deb

```

---

### Post by syko21 on 2007-05-01
getting the same problems when installing the deb.

---

### Post by durand on 2007-05-01
gah, i just did a make install. Works alongside gaim. Thanks for the howto ;)

OH and Pidgin looks really neat. They've added loads of small features and revamped the look and icons. I only really use msn but they've added more support for custom animations and all display pics seem to work now.

---

### Post by FrancoNero on 2007-05-01
excuse my unmanlyness i.e. my resistance to compile anything (i'm an end user!!) but why is pidgin beta 7 not available through synaptic or update manager, i mean, it's the update to beta6 after all, after 6 comes 7....

---

### Post by Protoss on 2007-05-01
Well, it takes a little while for the packages to be compiled by the maintainers (they're volunteers AFAIK), and there may be breakages that might need to be resolved. So it may take a week or so.

---

### Post by 4l1da on 2007-05-02
> **andrek said:**
> Download Pidgin from this link, 2.0.0-beta7 compiled for feisty fawn as .deb
[http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0beta7-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0beta7-1_i386.deb)

Works very well!!!

---

### Post by SuperAndy on 2007-05-02
> **brohan said:**
> Follow [http://developer.pidgin.im/wiki/UsingPidginMonotone](http://developer.pidgin.im/wiki/UsingPidginMonotone) closer.

My issue is when I've got everything and I run configure I get
```
checking for GLIB... no
configure: error:

You must have the GLib 2.0 development headers installed to build Gaim.

```

I do have libglib2.0-dev installed, and compiled glib 2.12.11 and yet it still isn't working. Any ideas?

I get this same problem. I want to be able to compile from  source code, as it seems like a pretty key skill for a linux user.

but, its not lookingn promising.

---

### Post by jdhore on 2007-05-02
> **FrancoNero said:**
> excuse my unmanlyness i.e. my resistance to compile anything (i'm an end user!!) but why is pidgin beta 7 not available through synaptic or update manager, i mean, it's the update to beta6 after all, after 6 comes 7....

it may be the update to beta 6, but it hasn't been out very long so it's probably still considered to be "unstable" and since this is the first release under the name Pidgin, the Ubuntu team would have to go in and make a lot of changes to meta-packages (gnome, ubuntu-desktop, etc) in order for them to point to Pidgin AND Gaim (for people who don't want to upgrade)...it seems like it would be a huge pain and i believe one of the Ubuntu devs said they're not going over to Pidgin until Gutsy Gibbon (7.10) because it's too much hassle to change it in Feisty

---

### Post by durand on 2007-05-02
And another reason, pidgin will be fully released soon so there's not much point in packaging the beta.

---

### Post by FrancoNero on 2007-05-02
> **jdhore said:**
> ..it seems like it would be a huge pain and i believe one of the Ubuntu devs said they're not going over to Pidgin until Gutsy Gibbon (7.10) because it's too much hassle to change it in Feisty

why is it a hassle? (just asking)

---

### Post by jcpeart on 2007-05-04
I have just installed pidgin 2.0 on an Ubuntu 6.10 system and attempted to log on to my MSN Messenger account but when i try to connect i am getting the error message that "SSL support is needed for MSN. Please install a supported SSL library." I am now at a loss of what to do. Any suggestions. 

Jim

---

### Post by chownsb on 2007-05-04
I am trying to install Pidgin 2.0 final release on Fiesty Fawn.  I did configure, make, make install and everything worked fine but when I try to run Pidgin I get this error:
```
pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory
```
I've done a bunch of searching but haven't found any solutions to it yet.  I also tried installing a DEB that was posted but it complains that Gaim is conflicting.  Any ideas how to get either the source or the DEB to work?  Thanks.

---

### Post by jcpeart on 2007-05-04
I found the answer.  Install the SSL dev libraries and recompile.  Works like a champ.:)

---

### Post by thebert on 2007-05-04
Now that the pidgin final is released will it get to the feisty repos? or do we have to wait until 7.10?

---

### Post by lefen on 2007-05-04
> **jcpeart said:**
> I have just installed pidgin 2.0 on an Ubuntu 6.10 system and attempted to log on to my MSN Messenger account but when i try to connect i am getting the error message that "SSL support is needed for MSN. Please install a supported SSL library." I am now at a loss of what to do. Any suggestions. 

Jim


I'm having the same problem in Dapper, but Installing the SSL dev libraries and recompiling isn't working for me. Can anyone think why?

Cheers

---

### Post by venky on 2007-05-04
> **spanella47 said:**
> i'm getting this error when compiling it:

dpkg: pidgin: warning - conffile `etc/gconf' is not a plain file or symlink (= `
/etc/gconf')
dpkg: pidgin: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain f
ile or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing /home/spanella47/Desktop/pidgin-2.0.0beta7/pidgin_2.0.0be
ta7-1_i386.deb (--install):
 trying to overwrite `/usr/bin/nm', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)

any ideas?
Downgrade to checkinstall 1.6.0 and this problem should be fixed

---

### Post by Fylk on 2007-05-05
Can some one help explain to me what I do once I have downloaded the source. 

Also, any ideas if the universe is going to include this any time soon?

Finally, I may need help with getting GUIfactions up again.

---

### Post by kaede on 2007-05-05
is file transfer working out right now? coz im currently still on 2 beta 7. and quite satisfied with the GUI
just want to add some links

[http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb)

---

### Post by syko21 on 2007-05-05
Extract it to your desktop and open up a console
```

sudo apt-get install build-essential linux-headers-`uname -r`
cd Desktop
./configure
make
sudo make install

```
if ./configure gives you any dependency errors search for the packages in synaptic and install the ***-dev versions of them.

---

### Post by ticopelp on 2007-05-05
I so should have read this, like, twenty minutes ago. Oops!

---

### Post by Fylk on 2007-05-05
> **syko21 said:**
> Extract it to your desktop and open up a console
```

sudo apt-get install build-essential linux-headers-`uname -r`
cd Desktop
./configure
make
sudo make install

```
if ./configure gives you any dependency errors search for the packages in synaptic and install the ***-dev versions of them.

Was that for me?

---

### Post by zanglang on 2007-05-05
> **venky said:**
> Downgrade to checkinstall 1.6.0 and this problem should be fixed

Hmm... how do you downgrade checkinstall in Feisty? Tried specifying the version in aptitude, but didn't seem to work. :/
> $ sudo aptitude install checkinstall=1.6.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Unable to find a version "1.6.0" for the package "checkinstall"

---

### Post by Fylk on 2007-05-05
> **kaede said:**
> is file transfer working out right now? coz im currently still on 2 beta 7. and quite satisfied with the GUI
just want to add some links

[http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb)

I keep getting errors saying that its conflicting with my gaim-data. Don't tell me i have to remove all my gaim settings. 

Also, is the icon working in this build?

---

### Post by DetRedWing on 2007-05-05
I was having same SSL library problem. Trying almost anything. Then I somehow installed libgnutls-dev package and now msn is working

---

### Post by zerwas on 2007-05-05
> **Fylk said:**
> I keep getting errors saying that its conflicting with my gaim-data. Don't tell me i have to remove all my gaim settings. 

It's no problem to remove the packages gaim and gaim-data. Settings are saved in ~/.gaim. With Pidgin this gets ~/.purple

---

### Post by Dangling on 2007-05-05
> **zanglang said:**
> Hmm... how do you downgrade checkinstall in Feisty? Tried specifying the version in aptitude, but didn't seem to work. :/

It seems that Feisty repositories don't have the previous versions of checkinstall:
[https://launchpad.net/ubuntu/feisty/+source/checkinstall](https://launchpad.net/ubuntu/feisty/+source/checkinstall)

The 1.6.0 version is called 1.6.0-2ubuntu1 but I can only find it in Edgy. I'm not sure if its ok to install a package meant for Edgy in Feisty.

---

### Post by durand on 2007-05-05
> **chownsb said:**
> I am trying to install Pidgin 2.0 final release on Fiesty Fawn.  I did configure, make, make install and everything worked fine but when I try to run Pidgin I get this error:
```
pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory
```
I've done a bunch of searching but haven't found any solutions to it yet.  I also tried installing a DEB that was posted but it complains that Gaim is conflicting.  Any ideas how to get either the source or the DEB to work?  Thanks.

I got the same problem here, installed with the rpm converted to deb by alien. The other thing is that I did a make install from pidgin source at beta7 and when I installed using the converted deb, it still goes to /usr/local/bin/pidgin rather than /usr/bin/pidgin. When i do run /usr/bin/pidgin, i get the error mentioned above.

---

### Post by durand on 2007-05-05
Found the solution:
[http://www.nabble.com/add-to-wiki-t3678952.html](http://www.nabble.com/add-to-wiki-t3678952.html)

[QUOTE=James Lockie]
Can someone who knows the wiki add a section on problems? 

He is my problem and solution getting beta7 to work on Linux-x86_64: 

/tmp/pidgin-2.0.0beta7 $ pidgin 
pidgin: error while loading shared libraries: libpurple.so.0: cannot 
open shared object file: No such file or directory 

# find / -name libpurple.so* -print 
/tmp/pidgin-2.0.0beta7/libpurple/.libs/libpurple.so.0.0.0 
/tmp/pidgin-2.0.0beta7/libpurple/.libs/libpurple.so.0 
/tmp/pidgin-2.0.0beta7/libpurple/.libs/libpurple.so 
/usr/local/lib64/libpurple.so.0.0.0 
/usr/local/lib64/libpurple.so.0 
/usr/local/lib64/libpurple.so 

I had to add "/usr/local/lib64" to my /etc/env.d/00basic LDPATH= (AKA 
/etc/ld.so.conf for non-Gentoo). 

It's weird that g*m worked.
[/QUOTE]

---

### Post by dotsi on 2007-05-06
> **jcpeart said:**
> I have just installed pidgin 2.0 on an Ubuntu 6.10 system and attempted to log on to my MSN Messenger account but when i try to connect i am getting the error message that "SSL support is needed for MSN. Please install a supported SSL library." I am now at a loss of what to do. Any suggestions. 

Jim

I get that too when trying to use MSN account in Pidgin installed from [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin). Any suggestions?

---

### Post by allanlewis on 2007-05-07
> **PaulFXH said:**
> My experience with Instant Messaging is minimal.
However, I was persuaded by a young friend to set up an MSN account (she uses Windows).
So, I thought Pidgin would allow me to communicate with her from my (new) MSN account without having to switch out of Ubuntu.
I also saw this as an opportunity to impress her with the versatility of Ubuntu/Linux towards which previous attempts have not gone down too well (although the Beryl cube at least drew a few gasps of awe and wonder).
I got Pidgin installed without any problems and it works fine. But, it apparently doesn't allow voice communication through MSN.
Unfortunately, this has resulted in a very black mark against Linux in the eyes of my friend.

So, is that it...it just can't be done or has Pidgin got a trick up its sleeve?

If you want to use voice, then just install Skype. [www.skype.com](www.skype.com) has a Ubuntu repository.

---

### Post by Lorenz on 2007-05-07
I just compiled it under Edgy - had the problem with hotmail and SSL as well, but as mentioned earlier the problem is solved by downoading the ssl devs and re-compiling pidgin. Now it works very smoothly and looks cool!

About msn with voice - that never worked very well anyway (under windows).
It is really recommended to use Skype, even if the Linux version is hopelessly outdated. There is hope, however - a new version with video support will be released sooner or later :)

---

### Post by Elrohir on 2007-05-08
> **Lorenz said:**
> I just compiled it under Edgy - had the problem with hotmail and SSL as well, but as mentioned earlier the problem is solved by downoading the ssl devs and re-compiling pidgin. Now it works very smoothly and looks cool!

About msn with voice - that never worked very well anyway (under windows).
It is really recommended to use Skype, even if the Linux version is hopelessly outdated. There is hope, however - a new version with video support will be released sooner or later :)
I actually used Mozilla's SSL Libraries... can't remember if it was libnspr-dev or libnss-dev... can someone confirm?

---

### Post by webbie180 on 2007-05-08
Where can I find a deb for dapper?  Or how to make one?

---

### Post by lukanium on 2007-05-08
Hix, i encounterd this error when compiling Pidgin 2.0 
```

.....
Making all in po
make[2]: Entering directory `/home/lukas/source/pidgin-2.0.0/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/lukas/source/pidgin-2.0.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lukas/source/pidgin-2.0.0'
make: *** [all] Error 2

```
:confused:
[quote=Lorenz]
I actually used Mozilla's SSL Libraries... can't remember if it was libnspr-dev or libnss-dev... can someone confirm?
[/quote]
that's libnss-dev man !

---

### Post by fakie_flip on 2007-05-08
What is the problem? I enabled all the source repos in my sources.list by uncommenting them and now this error.

E: Unable to find a source package for gaim

```
winston@ubuntu:~$ sudo apt-get update && sudo apt-get build-dep gaim
Ign http://getswiftfox.com unstable Release.gpg                                
Ign http://download.skype.com stable Release.gpg                               
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://getswiftfox.com unstable/non-free Translation-en_US      
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B] 
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://getswiftfox.com unstable Release                                    
Ign http://download.skype.com stable Release                                   
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release                         
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US 
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Ign http://getswiftfox.com unstable/non-free Packages                          
Ign http://download.skype.com stable/non-free Packages                         
Hit http://security.ubuntu.com feisty-security/main Packages         
Hit http://getswiftfox.com unstable/non-free Packages                
Get:4 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release                      
Hit http://download.skype.com stable/non-free Packages                         
Hit http://security.ubuntu.com feisty-security/restricted Packages   
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-backports Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 4B in 3s (1B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for gaim
winston@ubuntu:~$ 
```

---

### Post by Angafirith on 2007-05-08
> **fakie_flip said:**
> What is the problem? I enabled all the source repos in my sources.list by uncommenting them and now this error.

E: Unable to find a source package for gaim


You don't have any source repositories in your sources.list. Try adding this, then run apt-get update again:

```
deb-src http://us.archive.ubuntu.com feisty main
```

---

### Post by fakie_flip on 2007-05-08
Wow, did it tell you to install this many packages? 93 packages to build pidgin?

winston@ubuntu:~$ sudo apt-get build-dep gaim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  autoconf automake1.7 autotools-dev cdbs debhelper gettext html2text intltool
  intltool-debian libaspell-dev libatk1.0-dev libaudiofile-dev
  libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev
  libcairo2-dev libcamel1.2-dev libdbus-1-dev libdbus-glib-1-dev
  libebook1.2-dev libedata-book1.2-dev libedataserver1.2-dev libesd0-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgadu-dev libgconf2-dev
  libgcrypt11-dev libglib2.0-dev libgnome2-dev libgnomevfs2-dev libgnutls-dev
  libgpg-error-dev libgstreamer0.10-dev libgtk2.0-dev libgtkspell-dev
  libhesiod0 libice-dev libidl-dev liblaunchpad-integration-dev libltdl3-dev
  liblzo-dev libmeanwhile-dev libncursesw5-dev libnm-glib-dev libnspr-dev
  libnss-dev libopencdk8-dev liborbit2-dev libpango1.0-dev libperl-dev
  libpng12-dev libpopt-dev libsasl2-dev libselinux1-dev libsepol1-dev
  libsm-dev libstartup-notification0-dev libtasn1-3-dev libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev libxss-dev
  libxt-dev libzephyr-dev libzephyr3 m4 po-debconf tcl8.4-dev tk8.4-dev x-dev
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-scrnsaver-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 93 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.3MB of archives.
After unpacking 100MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by fakie_flip on 2007-05-08
I've got build-essential and checkinstall, but how do i revert to the older version of checkinstall?

---

### Post by fakie_flip on 2007-05-09
Could someone help with this please?

```
winston@ubuntu:~/pidgin-2.0.0$ sudo apt-get install ncursesw-dev
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
winston@ubuntu:~/pidgin-2.0.0$ man dpkg
Reformatting dpkg(1), please wait...
winston@ubuntu:~/pidgin-2.0.0$ sudo dpkg --configure -a
dpkg: error processing x11proto-core-dev (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 x11proto-core-dev
winston@ubuntu:~/pidgin-2.0.0$ sudo apt-get --purge remove x11proto-core-dev && sudo apt-get install x11proto-core-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  x11proto-core-dev*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 479kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing x11proto-core-dev (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 x11proto-core-dev
Saving new apt-history status...
E: Sub-process /usr/bin/dpkg returned an error code (1)
winston@ubuntu:~/pidgin-2.0.0$
```

---

### Post by fakie_flip on 2007-05-09
I can't believe this. I pushed control c a bunch of times to stop it, and then it spit out even more errors. I am starting to get very frustrated with Ubuntu.

```
winston@ubuntu:~/pidgin-2.0.0$ sudo apt-get --purge remove libncursesw5 && sudo apt-get install libncursesw5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  normalize-audio libopenexr2c2a imlib11 libarts1c2a libartsc0 libmtp5
  libdc1394-13 docbook-to-man libavahi-compat-howl0 libxvidcore4 mplayer-skins
  libsilc-1.0-2 libflac++5c2 libfame-0.9 vcdimager libwxgtk2.6-0 fftw3
  libsp1c2 kdelibs-data libpvm3 libmp4v2-0 mplayer libpostproc0d mysql-common
  sp democracyplayer-data mencoder libavformat0d dvdauthor libmysqlclient15off
  ruby1.8 libcairomm-1.0-1 libglibmm-2.4-1c2a blt ruby libgmp3c2 libggi2
  libavahi-qt3-1 libgii1 libwxbase2.6-0 tcltls libxml1 libgtkmm-2.4-1c2a
  ffmpeg libmjpegtools0c2a python-glade-1.2 transcode libtunepimp5 libifp4
  libdbus-qt-1-1c2 libgii1-target-x libgdk-pixbuf2 docker libgsm1 libiso9660-4
  libdvdread3 sox python-gtk-1.2 tcl8.4 imlib-base tk8.4 libavcodec0d
  libmeanwhile1 mjpegtools libpq5 imagemagick libruby1.8 libquicktime0
  libglade0 libvcdinfo0 libmpcdec3 liblame0 libnjb5 libofa0 docbook libmpeg2-4
  libfaac0 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte* alsa-utils* amarok* amarok-xine* amsn* apport* apport-gtk*
  apt-history* aptitude* aspell* aspell-en* bittornado* bittornado-gui*
  bittorrent* bug-buddy* camorama* capplets-data* command-not-found* compiz*
  compiz-gnome* compiz-gtk* compiz-plugins* contact-lookup-applet*
  democracyplayer* deskbar-applet* desktop-effects* devede* ekiga* eog*
  epiphany-browser* evince* evolution* evolution-data-server*
  evolution-exchange* evolution-plugins* evolution-webcal* f-spot*
  file-roller* firefox-gnome-support* gaim* gaim-data* gcalctool*
  gconf-editor* gconf2* gdebi* gdebi-core* gdm* gedit* gimp-python* gksu*
  gnome-about* gnome-app-install* gnome-applets* gnome-applets-data*
  gnome-btdownload* gnome-control-center* gnome-cups-manager* gnome-doc-utils*
  gnome-games* gnome-games-data* gnome-keyring-manager* gnome-media*
  gnome-media-common* gnome-menus* gnome-mount* gnome-netstatus-applet*
  gnome-nettool* gnome-orca* gnome-panel* gnome-panel-data* gnome-pilot*
  gnome-pilot-conduits* gnome-power-manager* gnome-screensaver* gnome-session*
  gnome-spell* gnome-system-monitor* gnome-system-tools* gnome-terminal*
  gnome-terminal-data* gnome-user-guide* gnome-utils* gnome-volume-manager*
  gparted* gstreamer0.10-gnomevfs* gstreamer0.10-plugins-good* gthumb*
  gtkhtml3.14* gucharmap* hal-device-manager* hplip* hwdb-client-common*
  hwdb-client-gnome* k3b* kdebase-bin* kdebase-kio-plugins* kdelibs4c2a*
  kdesktop* kolf* ktorrent* language-selector* language-selector-common*
  language-support-en* launchpad-integration* libbonoboui2-0*
  libboost-python1.33.1* libcamel1.2-10* libebook1.2-9* libecal1.2-7*
  libedata-book1.2-2* libedata-cal1.2-6* libedataserverui1.2-8* libeel2-2*
  libexchange-storage1.2-3* libgail-gnome-module* libgdl-1-0* libgdl-1-common*
  libgksu2-0* libgnome-desktop-2* libgnome-media0* libgnome-menu2*
  libgnome-window-settings1* libgnome2-0* libgnome2-common* libgnome2-perl*
  libgnome2-vfs-perl* libgnome2.0-cil* libgnomecupsui1.0-1c2a*
  libgnomekbd-common* libgnomekbd1* libgnomekbdui1* libgnomeui-0*
  libgnomeui-common* libgnomevfs2-0* libgnomevfs2-bin* libgnomevfs2-common*
  libgnomevfs2-extra* libgtkhtml3.14-19* libgucharmap6* libk3b2* libkdegames1*
  libkonq4* liblaunchpad-integration0* liblpint-bonobo0* libmetacity0*
  libnautilus-extension1* libncursesw5* libpanel-applet2-0* libslab0*
  libtotem-plparser1* lsb-release* metacity* metacity-common* nano* nautilus*
  nautilus-cd-burner* nautilus-data* nautilus-sendto* network-manager-gnome*
  notification-daemon* onboard* openoffice.org* openoffice.org-gnome*
  openoffice.org-gtk* openoffice.org-help-en-us* openoffice.org-writer*
  pidgin* pidgin-guifications* python* python-apport* python-apt*
  python-at-spi* python-bittorrent* python-cairo* python-central* python-dbus*
  python-gconf* python-gdbm* python-glade2* python-gmenu* python-gnome2*
  python-gnome2-desktop* python-gnome2-extras* python-gnomecanvas*
  python-gnupginterface* python-gobject* python-gst0.10* python-gtk2*
  python-gtkhtml2* python-imaging* python-launchpad-bugs*
  python-launchpad-integration* python-libxml2* python-notify* python-numeric*
  python-orca-brlapi* python-problem-report* python-qt3* python-sip4*
  python-software-properties* python-support* python-tk* python-uno*
  python-virtkey* python-vte* python-wxgtk2.6* python-wxversion* python-xdg*
  python-xml* python2.5* restricted-manager* rhythmbox* screen* serpentine*
  software-properties-gtk* sound-juicer* synaptic* tasksel* tasksel-data*
  thunderbird-locale-en-gb* tomboy* totem* totem-mozilla* totem-xine* tovid*
  tsclient* txt2tags* ubuntu-desktop* ubuntu-docs* ubuntu-minimal*
  ubuntu-standard* unattended-upgrades* update-manager* update-manager-core*
  update-notifier* vino* xchat-gnome* xchat-gnome-common* yelp*
0 upgraded, 0 newly installed, 239 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/86.3kB of archives.
After unpacking 761MB disk space will be freed.
Do you want to continue [Y/n]? 
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 113557 files and directories currently installed.)
Preparing to replace x11proto-core-dev 7.0.10-1 (using .../x11proto-core-dev_7.0.10-1_all.deb) ...
Unpacking replacement x11proto-core-dev ...
(Reading database ... 113556 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing alacarte ...
dpkg: error processing alacarte (--purge):
 subprocess post-removal script killed by signal (Interrupt)
Removing ubuntu-minimal ...
Removing gdm ...
dpkg: error processing gdm (--purge):
 subprocess pre-removal script killed by signal (Interrupt)
dpkg: error while cleaning up:
 subprocess post-installation script killed by signal (Interrupt)
Removing alsa-utils ...
Purging configuration files for alsa-utils ...
Removing amsn ...

winston@ubuntu:~/pidgin-2.0.0$ 
winston@ubuntu:~/pidgin-2.0.0$ 
winston@ubuntu:~/pidgin-2.0.0$ Traceback (most recent call last):
  File "/usr/bin/apt-history", line 178, in <module>
    main()
  File "/usr/bin/apt-history", line 161, in main
    if not os.path.exists(prefix):
  File "/usr/lib/python2.5/posixpath.py", line 171, in exists
    st = os.stat(path)
KeyboardInterrupt

winston@ubuntu:~/pidgin-2.0.0$ 

```

---

### Post by Angafirith on 2007-05-09
When at all possible, I recommend using prevu to build packages. I think it's in the repositories now, so the following steps should set it up for you:

```
sudo apt-get install prevu
sudo prevu-init
```

Prevu init will occasionally fail. If that happens, just try running it again. It works by creating a chroot environment (essentially, a condensed linux installation) and compressing it. When you run "prevu" in a source directory, it will unpack that chroot, install packages to it, build your package, and then throw away any changes it made to that chroot. At the end, if will put all packages it makes into "/var/cache/prevu/{distro}-debs" where distro is your current ubuntu version. If you're running feisty, it will be feisty-debs.

Provided that you rarely ever use Ctrl + C to interrupt a prevu build, it shouldn't take up a lot of space on your drive. If you do interrupt a build, just clear out the contents of the "/var/cache/prevu/build" directory to get the space back.

[Pidgin is now in Debian Unstable]('http://packages.debian.org/unstable/source/pidgin'), which means you can just grab their source and build it without making too many changes. I know of only one change off the top of my head: in debian/rules, there's a line like this: "cp build/doc/html/*.{html png gif}". When you try to build it in ubuntu, it fails on this line. I changed it to "cp build/doc/html/*", which is not an optimal solution, but it works.

Heh, I thought I was going to make a short reply here.

---

### Post by thebert on 2007-05-09
fakie flip,  try installing ubuntu-desktop to reinstall everything.


I'm not exactly sure what you are trying to accomplish. Why were you trying to build gaim from source? If you want to install the latest version of pidgin you can download a .deb from [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

There will be a dependency error when you try to install the pidgin deb, (a confict with gaim-data) you can remove gaim gaim-data and ubuntu-desktop to install it. After pidgin is installed from the deb if you reinstall ubuntu-desktop again you will have gaim and pidgin installed.

---

### Post by bbrewerg on 2007-05-09
is there not a way to change the font sizes in the buddy list?  i've tried the GTK+ plugin that is in there by default as well as installing extended-prefs (which doesn't seem to work).  

the only way i can seem to get the font size to change is by changing the system wide applicaiton font under front preferences (for gnome, not just pidgin).  anyone have any better ideas?

---

### Post by teknosexual on 2007-05-09
> **Lorenz said:**
> I just compiled it under Edgy - had the problem with hotmail and SSL as well, but as mentioned earlier the problem is solved by downoading the ssl devs and re-compiling pidgin. Now it works very smoothly and looks cool!

Which devs did you install?

I installed the libssl-dev .9.8.b-2ubuntu2 in Synaptic, recompiled, but still have the SSL/MSN issue.

Edit: Nevermind, I found it! It's GnuTLS. 

Both MSN and Google Talk via Jabber work now. :)

---

### Post by bmadaras on 2007-05-09
> **lukanium said:**
> Hix, i encounterd this error when compiling Pidgin 2.0 
```

.....
Making all in po
make[2]: Entering directory `/home/lukas/source/pidgin-2.0.0/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/lukas/source/pidgin-2.0.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lukas/source/pidgin-2.0.0'
make: *** [all] Error 2

```
:confused:

that's libnss-dev man !

Did anyone figure out why this was happening?  I tried changing the link from /bin/sh to /bin/bash instead of /bin/dash like it is by default and it still does not give me the -o option?

---

### Post by foureight84 on 2007-05-09
i was trying to use checkinstall and i get this error

```

(Reading database ... 121066 files and directories currently installed.)
Unpacking pidgin (from .../pidgin_2.0.0-1_i386.deb) ...
dpkg: pidgin: warning - conffile `etc/gconf' is not a plain file or symlink (= `
/etc/gconf')
dpkg: pidgin: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain f
ile or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing /home/wasabi/Desktop/pidgin-2.0.0/pidgin_2.0.0-1_i386.deb
 (--install):
 trying to overwrite `/usr/bin/ld', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/wasabi/Desktop/pidgin-2.0.0/pidgin_2.0.0-1_i386.deb


```

---

### Post by fakie_flip on 2007-05-10
> **thebert said:**
> fakie flip,  try installing ubuntu-desktop to reinstall everything.


I'm not exactly sure what you are trying to accomplish. Why were you trying to build gaim from source? If you want to install the latest version of pidgin you can download a .deb from [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

There will be a dependency error when you try to install the pidgin deb, (a confict with gaim-data) you can remove gaim gaim-data and ubuntu-desktop to install it. After pidgin is installed from the deb if you reinstall ubuntu-desktop again you will have gaim and pidgin installed.

Getdeb.net? I'm not installing any flippin deb from there. The person who made those debs doesn't know what he's doing. I'll use debs from official ubuntu repositories, but for this one I'll compile my own.

I'm not building gaim from source. That command was to help me get dev packages needed to build Feisty. Even the guide on the first post of this forum says to do that.

---

### Post by milad on 2007-05-10
*//Sorry for my poor English*

I have installed Pidgin using the Deb package available in GetDeb.net and it works properly but I'm looking for development files that are not included in main Pidgin package. Does anybody know where I can get them?

Basically I'm trying to install a plugin for Pidgin called [Music Tracker]("http://code.google.com/p/musictracker/") which displays information about the track you are listening in your status message but it needs those development files for compiling.

Any solution for this?

---

### Post by milad on 2007-05-10
The problem is solved. I just had to install libgtk2dev

---

### Post by foundation on 2007-05-10
I'm loving Pidgin so far but some questions:

- In the contacts menu is there a way I can sort contacts per 'account' - like I have 3 accounts (2 MSN and 1 AIM) and it mixes the groups together and I really need them separate
- Where to download more plugins ?
- Where to download more themes or how to customise the appearance ?

Thanks. :)

---

### Post by th3gh05t on 2007-05-10
Does anyone have a Pidgin 2.0.0 deb for Dapper?

---

### Post by webbie180 on 2007-05-12
> **th3gh05t said:**
> Does anyone have a Pidgin 2.0.0 deb for Dapper?

Ya, any kind soul out there willing to help?  Me looking for it too....thanks.

---

### Post by bmadaras on 2007-05-12
> **bmadaras said:**
> .....
Making all in po
make[2]: Entering directory `/home/lukas/source/pidgin-2.0.0/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/lukas/source/pidgin-2.0.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lukas/source/pidgin-2.0.0'
make: *** [all] Error 2

I was just guessing on stuff to fix this and seem to have found it, needed the gettext and the html2text packages and it works

---

### Post by Fylk on 2007-05-12
Are you going to update this howto for the final release of Pidgin?

---

### Post by Elrohir on 2007-05-13
Due to doing a fresh install of Feisty on one of my computers, I compiled Pidgin from very scratch... Here are the packages needed:[LIST]
[*]libglib2.0-dev
[*]libgtk2.0-dev
[*]libxml2-dev
[*]libnss-dev
[*]gettext
[*]html2text[/LIST]Optional, for documentation, you may install[LIST]
[*]doxygen
[*]graphviz[/LIST]with all the dependencies met, extract the source code, configure, make, make install:
```
$ ./configure
$ make
$ sudo make install
```Cheers!

---

### Post by bryan1 on 2007-05-13
After doing 

```
make
```

I get this

```

make[3]: Leaving directory `/home/bryan/Desktop/pidgin/pidgin'
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/pidgin'
Making all in m4macros
make[2]: Entering directory `/home/bryan/Desktop/pidgin/m4macros'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/m4macros'
Making all in po
make[2]: Entering directory `/home/bryan/Desktop/pidgin/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/Desktop/pidgin'
make: *** [all] Error 2

```

Any idea?

---

### Post by Elrohir on 2007-05-13
> **bryan1 said:**
> After doing 

```
make
```I get this

```

make[3]: Leaving directory `/home/bryan/Desktop/pidgin/pidgin'
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/pidgin'
Making all in m4macros
make[2]: Entering directory `/home/bryan/Desktop/pidgin/m4macros'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/m4macros'
Making all in po
make[2]: Entering directory `/home/bryan/Desktop/pidgin/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: -o: not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/Desktop/pidgin'
make: *** [all] Error 2

```Any idea?
do you have the gettext and html2text packages installed? if they are, run ```
$ ./configure && make
```

---

### Post by bryan1 on 2007-05-13
Thanks for the help! doing "make" seems to be working right now

then I tried

```

make install
```

and got this

```

bryan@laptop:~/Desktop/pidgin$ make install
Making install in libpurple
make[1]: Entering directory `/home/bryan/Desktop/pidgin/libpurple'
make  install-recursive
make[2]: Entering directory `/home/bryan/Desktop/pidgin/libpurple'
Making install in gconf
make[3]: Entering directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[4]: Entering directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[4]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults /usr/bin/gconftool-2 --makefile-install-rule purple.schemas 2>&1 | \
                grep -v "^WARNING: failed to install schema" | grep -v "^Attached schema" 1>&2
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
None of the resolved addresses are writable; saving configuration settings will not be possible
test -z "/usr/local/etc/gconf/schemas" || mkdir -p -- "/usr/local/etc/gconf/schemas"
mkdir: cannot create directory `/usr/local/etc/gconf': Permission denied
make[4]: *** [install-schemaDATA] Error 1
make[4]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple'
make: *** [install-recursive] Error 1
bryan@laptop:~/Desktop/pidgin$ 

```

:( what is it this time haha

---

### Post by berserker on 2007-05-13
> **bryan1 said:**
> Thanks for the help! doing "make" seems to be working right now

then I tried

```

make install
```

and got this

```

bryan@laptop:~/Desktop/pidgin$ make install
Making install in libpurple
make[1]: Entering directory `/home/bryan/Desktop/pidgin/libpurple'
make  install-recursive
make[2]: Entering directory `/home/bryan/Desktop/pidgin/libpurple'
Making install in gconf
make[3]: Entering directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[4]: Entering directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[4]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults /usr/bin/gconftool-2 --makefile-install-rule purple.schemas 2>&1 | \
                grep -v "^WARNING: failed to install schema" | grep -v "^Attached schema" 1>&2
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
None of the resolved addresses are writable; saving configuration settings will not be possible
test -z "/usr/local/etc/gconf/schemas" || mkdir -p -- "/usr/local/etc/gconf/schemas"
mkdir: cannot create directory `/usr/local/etc/gconf': Permission denied
make[4]: *** [install-schemaDATA] Error 1
make[4]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple'
make: *** [install-recursive] Error 1
bryan@laptop:~/Desktop/pidgin$ 

```

:( what is it this time haha

Try ```
sudo make install
```

---

### Post by Elrohir on 2007-05-13
> **bryan1 said:**
> Thanks for the help! doing "make" seems to be working right now

then I tried

```

make install
```and got this

```

bryan@laptop:~/Desktop/pidgin$ make install
Making install in libpurple
make[1]: Entering directory `/home/bryan/Desktop/pidgin/libpurple'
make  install-recursive
make[2]: Entering directory `/home/bryan/Desktop/pidgin/libpurple'
Making install in gconf
make[3]: Entering directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[4]: Entering directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[4]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults /usr/bin/gconftool-2 --makefile-install-rule purple.schemas 2>&1 | \
                grep -v "^WARNING: failed to install schema" | grep -v "^Attached schema" 1>&2
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
None of the resolved addresses are writable; saving configuration settings will not be possible
test -z "/usr/local/etc/gconf/schemas" || mkdir -p -- "/usr/local/etc/gconf/schemas"
mkdir: cannot create directory `/usr/local/etc/gconf': Permission denied
make[4]: *** [install-schemaDATA] Error 1
make[4]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple/gconf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/bryan/Desktop/pidgin/libpurple'
make: *** [install-recursive] Error 1
bryan@laptop:~/Desktop/pidgin$ 

```:( what is it this time haha
For installing Pidgin (make install) you need root permission, thus you install with this command```
sudo make install
```

---

### Post by bryan1 on 2007-05-13
It worked, thanks! :)

---

### Post by bryan1 on 2007-05-13
Sorry for double post but where are those pidgin icons in? It didn't make desktop launcher so I had to make it myself and can't find pidgin icons

---

### Post by berserker on 2007-05-14
> **bryan1 said:**
> Sorry for double post but where are those pidgin icons in? It didn't make desktop launcher so I had to make it myself and can't find pidgin icons

```
locate pidgin.png
```

Mine are here:

/usr/share/icons/hicolor/48x48/apps/pidgin.png
/usr/share/icons/hicolor/32x32/apps/pidgin.png
/usr/share/icons/hicolor/24x24/apps/pidgin.png
/usr/share/icons/hicolor/16x16/apps/pidgin.png

---

### Post by cor2y on 2007-05-14
I compiled Pidgin with no problems and it basicly works , however  i am unable to get the links posted in IM chat to open with firefox by clicking on them like it worked in gaim or any of the new email notifications except msn to work when you select Open Mail.

Anyone know what the problem could be ?

---

### Post by z0mbi3 on 2007-05-20
> sudo apt-get build-dep gaim

Is it possible to reverse the above command? I installed build-dep gaim but obviously it isn't necessary and want rid of it.

---

### Post by boogachamp on 2007-05-20
Thank YOU!!!!!

---

### Post by NotoriousTF on 2007-05-22
Whoops! Realised queries didn't belong in this part of the forum, so I moved my post here: [http://ubuntuforums.org/showthread.php?t=441363&page=4](http://ubuntuforums.org/showthread.php?t=441363&page=4)

---

### Post by faxmaster on 2007-05-25
> **Elrohir said:**
> Due to doing a fresh install of Feisty on one of my computers, I compiled Pidgin from very scratch... Here are the packages needed:[LIST]
[*]libglib2.0-dev
[*]libgtk2.0-dev
[*]libxml2-dev
[*]libnss-dev
[*]gettext
[*]html2text[/LIST]Optional, for documentation, you may install[LIST]
[*]doxygen
[*]graphviz[/LIST]with all the dependencies met, extract the source code, configure, make, make install:
```
$ ./configure
$ make
$ sudo make install
```Cheers!
Thank you!  I finally managed to get it installed.

---

### Post by Quite Interesting on 2007-05-26
I'm trying to build my own deb for the 2.0.1 release but unfortunately every time I run the ```
dpkg-buildpackage -rfakeroot
``` command it runs fine for a bit but then eventually errors out giving the following error message.
```
*** Warning: Linking the shared library perl.la against the
*** static library /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a is not portable!
.libs/perl.o: In function `unload_perl_plugin':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl.c:494: undefined reference to `purple_debug'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl.c:513: undefined reference to `purple_debug'
.libs/perl.o: In function `load_perl_plugin':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl.c:420: undefined reference to `purple_debug'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl.c:449: undefined reference to `purple_debug'
.libs/perl.o: In function `purple_init_plugin':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl.c:649: undefined reference to `purple_plugin_register'
.libs/perl.o: In function `probe_perl_plugin':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl.c:400: undefined reference to `purple_plugin_register'
.libs/perl-common.o: In function `purple_perl_data_from_sv':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:383: undefined reference to `purple_value_get_type'
.libs/perl-common.o: In function `execute_perl':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:205: undefined reference to `purple_debug'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:214: undefined reference to `purple_debug'
.libs/perl-common.o: In function `purple_perl_sv_from_subtype':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:407: undefined reference to `purple_value_get_subtype'
.libs/perl-common.o: In function `purple_perl_sv_from_vargs':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:464: undefined reference to `purple_value_is_outgoing'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:465: undefined reference to `purple_value_get_type'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:541: undefined reference to `purple_value_get_type'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:608: undefined reference to `purple_value_get_specific_type'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-common.c:532: undefined reference to `purple_value_get_specific_type'
.libs/perl-handlers.o: In function `purple_perl_cmd_unregister':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:640: undefined reference to `purple_cmd_unregister'
.libs/perl-handlers.o: In function `purple_perl_cmd_register':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:575: undefined reference to `purple_cmd_register'
.libs/perl-handlers.o: In function `purple_perl_signal_connect':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:453: undefined reference to `purple_signal_connect_priority_vargs'
.libs/perl-handlers.o: In function `perl_signal_cb':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:259: undefined reference to `purple_signal_get_values'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:293: undefined reference to `purple_debug_error'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:300: undefined reference to `purple_value_is_outgoing'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:301: undefined reference to `purple_value_get_type'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:364: undefined reference to `purple_debug_misc'
.libs/perl-handlers.o: In function `purple_perl_plugin_actions':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:96: undefined reference to `purple_plugin_action_new'
.libs/perl-handlers.o: In function `purple_perl_plugin_action_cb':
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:42: undefined reference to `purple_plugin_get_name'
/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl/perl-handlers.c:34: undefined reference to `purple_plugin_get_name'
collect2: ld returned 1 exit status
make[6]: *** [perl.la] Error 1
make[6]: Leaving directory `/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins/perl'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/james/sources/pidgin/pidgin-2.0.1/libpurple/plugins'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/james/sources/pidgin/pidgin-2.0.1/libpurple'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/james/sources/pidgin/pidgin-2.0.1/libpurple'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/james/sources/pidgin/pidgin-2.0.1'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/james/sources/pidgin/pidgin-2.0.1'
make: *** [build-stamp] Error 2
```A bit of digging around suggests that problems like this usually come from not having libperl-dev install but I have had this installed and I have even reinstalled it for good measure. If anyone could tell me what the problem is it would be brilliant.

---

### Post by picpak on 2007-05-26
A direct download link to Pidgin's RPM is well hidden, but here it is:

[pidgin-2.0.1-0.fc6.i386.rpm](http://heanet.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.0.1-0.fc6.i386.rpm) (Right click > Save as if you don't want a bunch of ASCII gibberish)

I've made a DEB package from their RPM:

[libpurple0_2.0.1-1.SoS.2007.1_i386.deb](http://www.sendspace.com/file/fn8vob)
[pidgin_2.0.1-1.SoS.2007.1_i386.deb](http://www.sendspace.com/file/s7uos0)

Enjoy!

---

### Post by fct on 2007-05-26
> **picpak said:**
> A direct download link to Pidgin's RPM is well hidden, but here it is:

[pidgin-2.0.1-0.fc6.i386.rpm](http://heanet.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.0.1-0.fc6.i386.rpm) (Right click > Save as if you don't want a bunch of ASCII gibberish)

I've made a DEB package from their RPM:

[pidgin_2.0.1-1_i386.deb](http://www.sendspace.com/file/6j1cku)

Enjoy!

It killed my pidgin installation:

pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

---

### Post by picpak on 2007-05-26
Thanks for telling me that, after uploading it occurred to me that I hadn't actually tested it.

Link removed until someone releases a better DEB or I fix it, whichever comes first. Please, just downgrade to the getdeb version for now.

---

### Post by picpak on 2007-05-27
Alright, here are some real, working Pidgin 2.0.1 DEBs:

[b][libpurple0_2.0.1-1.SoS.2007.1_i386.deb](http://www.sendspace.com/file/fn8vob)
[pidgin_2.0.1-1.SoS.2007.1_i386.deb](http://www.sendspace.com/file/s7uos0)[/b]

First, remove your previous installation of Pidgin:

```
sudo apt-get remove pidgin
```

Then install it like so:

```
sudo dpkg -i libpurple0_2.0.1-1.SoS.2007.1_i386.deb pidgin_2.0.1-1.SoS.2007.1_i386.deb
```

Enjoy!

---

### Post by FrancoNero on 2007-05-28
popping "the question" again: why is this not available through software update?

---

### Post by Quite Interesting on 2007-05-28
FrancoNero: Perhaps this link will explain why people are reluctant to provide updates such as this [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

I really appreciate the work you put into creating those packages picpak and I'll probably end up using them. However I would really like my own attempt at creating a package to work if only as a way of learning. So hopefully someone could be able to tell me where I'm going wrong. I've even tried building the package with pbuilder and encountered exactly the same problem.

---

### Post by ShirishAg75 on 2007-05-30
> **picpak said:**
> Alright, here are some real, working Pidgin 2.0.1 DEBs:

[B][libpurple0_2.0.1-1.SoS.2007.1_i386.deb]("http://www.sendspace.com/file/fn8vob")
[pidgin_2.0.1-1.SoS.2007.1_i386.deb]("http://www.sendspace.com/file/s7uos0")[/B]

First, remove your previous installation of Pidgin:

```
sudo apt-get remove pidgin
```Then install it like so:

```
sudo dpkg -i libpurple0_2.0.1-1.SoS.2007.1_i386.deb pidgin_2.0.1-1.SoS.2007.1_i386.deb
```Enjoy!

Perhaps you or somebody else could upload to another mirror rapidshare.com or some other mirror as I'm unable to download from sendspace. :/

---

### Post by z0mbi3 on 2007-05-31
sorry to be a pain but could someone tell me how to make pidgin load at startup? It doesn't seem to be doing it by default.

---

### Post by Shinoda on 2007-05-31
> **ShirishAg75 said:**
> Perhaps you or somebody else could upload to another mirror rapidshare.com or some other mirror as I'm unable to download from sendspace. :/[http://rapidshare.com/files/34473160/libpurple0_2.0.1-1.SoS.2007.1_i386.deb](http://rapidshare.com/files/34473160/libpurple0_2.0.1-1.SoS.2007.1_i386.deb)
[http://rapidshare.com/files/34473161/pidgin_2.0.1-1.SoS.2007.1_i386.deb](http://rapidshare.com/files/34473161/pidgin_2.0.1-1.SoS.2007.1_i386.deb)
> **z0mbi3 said:**
> sorry to be a pain but could someone tell me how to make pidgin load at startup?System > Preferences > Sessions > Startup Programs > New > Name: [FONT=Courier New]Pidgin[/FONT] (e.g.), Command: [FONT=Courier New]pidgin[/FONT].

---

### Post by maddbaron on 2007-06-01
someone help please!
> Reading package lists... Done
Building dependency tree
Reading state information... Done
pidgin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libpurple0: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
              Depends: libdbus-1-3 (>= 0.94) but 0.93-0ubuntu3.1 is to be installed
              Depends: libdbus-glib-1-2 (>= 0.73) but 0.71-1ubuntu1 is to be installed
              Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
              Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
  pidgin: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is to be installed
          Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
          Depends: libcairo2 (>= 1.4.2) but 1.2.4-1ubuntu2 is to be installed
          Depends: libdbus-1-3 (>= 0.94) but 0.93-0ubuntu3.1 is to be installed
          Depends: libdbus-glib-1-2 (>= 0.73) but 0.71-1ubuntu1 is to be installed
          Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is to be installed
          Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
          Depends: libgstreamer0.10-0 (>= 0.10.12) but 0.10.10-1ubuntu2 is to be installed
          Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is to be installed
          Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is to be installed
          Depends: libsqlite3-0 (>= 3.3.13) but 3.3.5-0.2 is to be installed
          Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


tried reinstalling via adept and it won't do it. I tried reinstalling the beta and nothing. 
Someone help please!

---

### Post by Shinoda on 2007-06-02
Did you try picpak's debs?

---

### Post by Artemis3 on 2007-06-04
You don't need to compile this anymore, its in the repositories in feisty and gaim is now a transitional dummy  package to pidgin.

---

### Post by tino27 on 2007-06-06
Which repository? Cause I sure don't see it.

---

### Post by durand on 2007-06-06
The main one, im guessing? Try reinstalling gaim, does that work?

---

### Post by syko21 on 2007-06-06
its not in the repositories as far as I can see. I reinstalled gaim and it downloaded the beta6 package

---

### Post by durand on 2007-06-06
Yeah, your right, who did say it was?

Anyway, cant you compile it yourself and then do a make install?

---

### Post by tino27 on 2007-06-07
> **durand said:**
> Yeah, your right, who did say it was?

Anyway, cant you compile it yourself and then do a make install?

Yes, one can compile it, which is what this thread is about. But Artemis3 said that wasn't necessary because it's "in the repositories in feisty."

---

### Post by durand on 2007-06-08
> **tino27 said:**
> Yes, one can compile it, which is what this thread is about. But Artemis3 said that wasn't necessary because it's "in the repositories in feisty."

Yeah, your right...:(

---

### Post by zekopeko on 2007-06-08
look here for pidigin:

[www.getdeb.net](www.getdeb.net)

---

### Post by Caro_CR on 2007-06-09
> **milad said:**
> The problem is solved. I just had to install libgtk2dev

I don't know where to find that package. 

Would you help me?

---

### Post by Caro_CR on 2007-06-09
Did you mean libgtk2.0-dev?

---

### Post by screaminj3sus on 2007-06-20
> **Artemis3 said:**
> You don't need to compile this anymore, its in the repositories in feisty and gaim is now a transitional dummy  package to pidgin.

Are you sure you aren't using a third party repo?

---

### Post by Artemis3 on 2007-06-29
> **screaminj3sus said:**
> Are you sure you aren't using a third party repo?

My mistake indeed. They even removed the gaim to pidgin dummy package.
It is in the [debuntu repository](http://repository.debuntu.org/), i suppose ubuntu will not touch pidgin until gutsy.

---

### Post by mrazster on 2007-07-10
I just compiled and installed it on a clean xubuntu installation.

1. I followed the 2 first step in this howto

2. Downloaded and unpacked the latest sourcecode...

3.Then in terminal I did:
```
cd /home/username/pidgin-2.0.2
```

4.```
./configure
```

5.```
make
```

6.```
sudo make install
```

It all went perfectly well without any errors....

---

### Post by barney_1 on 2007-07-22
Trying to get this to work.  Everything seemed to install quite well on my Kubuntu 7.04 but when I go to add an icq buddy I get:

```
Unable to Add
Could not add the buddy ###ICQNUMBERHERE### for an unknown reason, 
The most common reason for this is that you have the 
maximum number of allowed buddies in your buddy list.
```

Any ideas?  Thanks

---

### Post by fakie_flip on 2007-08-01
Has anyone been able to get off the record plugin compiled for pidgin? I tried many times, and it seems impossible.

---

### Post by syko21 on 2007-08-01
it worked fine for me. I downloaded the source and 
```
sudo apt-get build-dep gaim-otr
./configure
make
sudo make install
```
and then restart pidgin, it worked fine.

PS> I built this package a while ago so there might be a few problems during ./configure that are dependency related but its easy enough to figure out.

---

### Post by tact on 2007-08-21
If after compiling from source you get the error "cannot load libpurple.so.0" or similar...  it could be because it was installed to /usr/local/lib instead of /usr/lib.

I had this tonight after compiling the latest version 2.1.1 from source.

make a symbolic link fixes it.

```
ln -s /usr/local/lib/libpurple.so.0 /usr/lib/
```

---

### Post by OttifantSir on 2007-08-29
I wanted to do this, but stopped after the first step, downloading the dependencies. It's a program that in itself is less than 10 MB (if memory serves correctly from the Windows version), yet the dependencies of the build-packages come in at near 40 MB in addition?

Well, will compile this if I get an answer to this: Are these packages needed afterwards, and if not, how to remove them?

---

### Post by Nekiruhs on 2007-08-29
> **OttifantSir said:**
> I wanted to do this, but stopped after the first step, downloading the dependencies. It's a program that in itself is less than 10 MB (if memory serves correctly from the Windows version), yet the dependencies of the build-packages come in at near 40 MB in addition?

Well, will compile this if I get an answer to this: Are these packages needed afterwards, and if not, how to remove them?
Any reason you want to compile it? Its packaged in a deb on [Getdeb.net ]("http://www.getdeb.net/release.php?id=1307")already.

---

### Post by faxmaster on 2007-08-29
> **OttifantSir said:**
> Well, will compile this if I get an answer to this: Are these packages needed afterwards, and if not, how to remove them?
You'll need them if you plan on upgrading/compiling future versions.

---

### Post by syko21 on 2007-08-29
you can copy the output of sudo apt-get build-dep gaim and install them with sudo apt-get install ***pasted packages***. Then just remove them using console history after you've compiled pidgin.

---

### Post by blunden on 2007-09-13
How do I get it added to the "Program"-menu? Now I have to run it with "pidgin" in the terminal. Also, do I still need the directory I extracted the source and compiled the app in?

I followed this tutorial.

[http://leetturtle.com/compile-pidgin-2-1-1-source-ubuntu](http://leetturtle.com/compile-pidgin-2-1-1-source-ubuntu)

---

### Post by chessnut on 2007-09-14
For those who are facing problems with checkinstall trying to overwrite files in /usr/bin (eg./usr/bin/ld), here's a quick fix for it:

1) Run checkinstall with the --inspect option (ie. checkinstall --inspect -D)

2) Upon successful compilation, checkinstall will prompt if you would like to review the files to be included in the pacakage. Choose "Yes"

3) Vi will be started and you will see a list of files which will be included in the package. Remove all the lines that do not contain the word "Purple" or "Pidgin"

**To delete lines in Vi, press the "d" key twice. To delete multiple lines (eg. 5 lines), type "5dd". **

4) Once that is done, all the necessary pidgin files will be included only and the creation and installation of the .deb file should be 100% successful.

Hope this helps.

---

### Post by joedoe123 on 2011-03-23
Wow.  Thanks alot.  That really does help.  Great post.

---

