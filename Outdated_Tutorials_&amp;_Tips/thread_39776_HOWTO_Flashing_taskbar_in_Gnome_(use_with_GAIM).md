---
title: "HOWTO: Flashing taskbar in Gnome (use with GAIM)"
date: 2005-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by zafar on 2005-06-06
A long wanted feature in gnome is flashing taskbars, to use with programs such as GAIM for new IM notification and others. The code has been submitted in a gnome bugzilla and was submitted into the gnome cvs so I patched the current version of libwnck to handle the flashing taskbar. Thanks goes to FLeiXiuS for the 64bit version of the patched libwnck.

**To get the patched version of libwnck:** 
```
**For x86:** wget http://z.narutochaos.com/ubuntu/libwnck16_2.10.0-0ubuntu1_i386.deb[B]
For x86-64 (AMD64):[/B] wget http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/libw/libwnck/libwnck16_2.10.0-2_amd64.deb

```This downloads the patched libwnck.
```
**For x86:** sudo dpkg -i libwnck16_2.10.0-0ubuntu1_i386.deb
**For x86-64(AMD64):** sudo dpkg -i libwnck16_2.10.0-2_amd64.deb
```This installs the patched version.
```
sudo echo libwnck16 hold | sudo dpkg --set-selections
```The command keeps apt-get from overwriting it.
```
killall gnome-panel
```This command closes the gnome panels and they automatically restart. 

After this, your taskbar should flash when the window manager is sent the urgent hint. 

**To get GAIM to use flashing taskbar notification:**

Start up GAIM and click Tools and then Preferences. Then click on the "Plugins" preference and check the checkbox beside the Message Notification plugin. After that there should be a Message Notification preference entry under the parent "Plugins". Click on that and it should give a list of options for the Message Notification plugin. Check the box for "set window manager "URGENT" hint and configure the rest of the options to your liking. Now, when you recieve a new message, your taskbar will flash to notify you.

---

### Post by Sionide on 2005-06-06
Great one.. I've always wished for this, resorting till now to all the other methods to alert you of new messages! Thanks.

---

### Post by pdk001 on 2005-06-06
> Click Tools and then Preferences. Then click on the "Plugins" preference and check the checkbox beside the Message Notification plugin. After that there should be a Message Notification preference entry under the parent "Plugins". Click on that and it should give a list of options for the Message Notification plugin. Check the box for "set window manager "URGENT" hint and configure the rest of the options to your liking. Now, when you recieve a new message, your taskbar will flash to notify you.
where is "Tools"?

---

### Post by zafar on 2005-06-06
[QUOTE=pdk001]where is "Tools"?[/QUOTE]
It is in the menubar in GAIM. You can also use CTRL + P to get to the preferences.

---

### Post by lizardking on 2005-06-06
Some screen? ;-)

---

### Post by pdk001 on 2005-06-06
[QUOTE=zafar]It is in the menubar in GAIM. You can also use CTRL + P to get to the preferences.[/QUOTE]
thanks for quick replay

---

### Post by Sionide on 2005-06-06
[img]http://www.sionide.net/gallery/albums/pics/Screenshot.sized.png[/img]

See Nicks IM window is slightly darker, it fades in and out as well instead of just flashing like MSN on windows does. Much cooler :D

---

### Post by dabear on 2005-06-06
This is great, but how do I change the color and the rapidity?

---

### Post by bored2k on 2005-06-06
Beautiful. I like the subtle blink. Very nice :D

---

### Post by Sionide on 2005-06-06
Would it work for highlight on xchat or any other progs?

---

### Post by pdk001 on 2005-06-06
im just successfully done and waiting to recieve a new one

---

### Post by bored2k on 2005-06-06
Everything should flash, a terminal, a window, everything ;).

---

### Post by Gtaylor on 2005-06-06
One of you KDE guys figure something out for us :)

---

### Post by zafar on 2005-06-06
[QUOTE=dabear]This is great, but how do I change the color and the rapidity?[/QUOTE]

For now, I think that is all hardcoded in, so you would have to get the sources and recompile to change it.

---

### Post by mike998 on 2005-06-06
This is just what I needed.  Thanks for the How-To!

---

### Post by lizardking on 2005-06-06
[SIZE=5][FONT=Comic Sans MS]wonderful[/FONT][/SIZE]
 \\:D/

---

### Post by moment on 2005-06-06
man you saved my relationship :D my girlfriend is always complaining about me not paying enough attention to her :D:D

seriously thanks alot. it's very nice.

---

### Post by simianMiscreant on 2005-06-06
you ROCK OUT

---

### Post by Sionide on 2005-06-06
[QUOTE=moment]man you saved my relationship :D my girlfriend is always complaining about me not paying enough attention to her :D:D

seriously thanks alot. it's very nice.[/QUOTE]
 Same! ...I still don't pay enough attention though because I'm reading these forums too much ;)

---

### Post by pdk001 on 2005-06-06
i've just recieved a message, show me what it does
this is awesome

---

### Post by MemoryDump on 2005-06-06
works great.. thxs for the hack :p

---

### Post by Seth on 2005-06-06
[QUOTE=Gtaylor]One of you KDE guys figure something out for us :)[/QUOTE]
 I think this patch is in latest Breezy Gnomestuffs.

As for KDE, it's been able to flash taskbar items for a long time.

---

### Post by Michael on 2005-06-06
This trick is pretty nice but I'm not sure I want to keep it, how do I uninstall it?

---

### Post by XDevHald on 2005-06-06
OoOoOoO! I like this little trick, thanks!

---

### Post by zafar on 2005-06-06
[QUOTE=Michael]This trick is pretty nice but I'm not sure I want to keep it, how do I uninstall it?[/QUOTE]

To remove it just install the original libwnck which you can find [here](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/libw/libwnck/libwnck16_2.10.0-0ubuntu1_i386.deb). Then repeat the gnome panel kill step and the taskbar won't flash.

Also, thanks everyone for the kind words, I've been wanting/trying to get this to work forever and finally got it working. Glad i could help you all out.

---

### Post by lonewolf72 on 2005-06-09
Thanks for this.  It helps a lot, especially now that I run Linux at work and my boss is using Yahoo to contact me...

---

### Post by i3dmaster on 2005-06-09
[QUOTE=lonewolf72]Thanks for this.  It helps a lot, especially now that I run Linux at work and my boss is using Yahoo to contact me...[/QUOTE]
 Awesome! good stuff

---

### Post by Ride Jib on 2005-06-10
Has anyone else not been able to install new software using synaptic after following this howto?

Edit: Sorry, this seems to be an archive problem tonight. 

Nice feature. I love it. Colors are great too, but options are always nice.

---

### Post by DShafik on 2005-06-11
Thank you **so** much! This has been the most annoying thing about switching to Linux from WInXP! 

Now to get my Nautilus integrated SVN wrapper working...

- Davey

---

### Post by Deka on 2005-06-11
Sweet How To! Thanks, I've been missing this ever since my switch from windows.

---

### Post by Orunitia on 2005-06-12
Very nice. The one thing KDE was better at than gnome for me.

---

### Post by Sionide on 2005-06-12
There are other ways you can get Gaim to alert you of messages but this is by far the best way. :)

---

### Post by FLeiXiuS on 2005-06-14
For those of you who are 64bit Hoary All-Stars, :-D, libwnck16-i386 is solemly for the i386 arch.


For AMD 64 users, this link should be more the sufficient.  You'll have to of course change the filename in each step which zafar had showed.

[http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/libw/libwnck/libwnck16_2.10.0-2_amd64.deb](http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/libw/libwnck/libwnck16_2.10.0-2_amd64.deb)

Great tip!

---

### Post by zafar on 2005-06-15
Thanks FLeiXiuS. I'll add that to the first post.

---

### Post by thomerz on 2005-06-25
I have one little problem with this patch.

when i get a message in gaim, the taskbar flashes, but it doesn't stop if i open gaim and read the message. it goes on until i write back something. any fix for this?

---

### Post by Pinguvin on 2005-06-25
[QUOTE=thomerz]I have one little problem with this patch.

when i get a message in gaim, the taskbar flashes, but it doesn't stop if i open gaim and read the message. it goes on until i write back something. any fix for this?[/QUOTE]

go to plug-ins > message notification in gaim's preferences and take a look there  ;-)

---

### Post by jaac on 2005-06-25
Great Post :D

---

### Post by RuKK on 2005-06-28
Nice trick guys, and it'll be good to see it integrated into ubuntu (hopefully!), but you do know you can just install Guifications plugin for Gaim? You dont have to recompile or anything either. Works like a charm and I like it better than a flashing window.

---

### Post by mikedfrwal on 2005-06-28
its so kool looking thank you

---

### Post by Nasso on 2005-07-11
sweeeet! big thanks! :D

bye bye to that annoying friccin sound :)

---

### Post by mike998 on 2005-07-11
[QUOTE=RuKK]Nice trick guys, and it'll be good to see it integrated into ubuntu (hopefully!), but you do know you can just install Guifications plugin for Gaim? You dont have to recompile or anything either. Works like a charm and I like it better than a flashing window.[/QUOTE]

I actually use both - If I am away from my laptop and I miss the guification (max notification time 60 seconds) The taskbar is still flashing when I come back (hours later?)

---

### Post by Luggy on 2005-07-19
[QUOTE=zafar]
```
[B]
For x86-64 (AMD64):[/B] wget http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/libw/libwnck/libwnck16_2.10.0-2_amd64.deb

```This downloads the patched libwnck.
[/QUOTE]

I'm presently getting a 404 when trying to connect to that URL.
Any chance it moved or someone could host the file again?

---

### Post by bored2k on 2005-07-19
[QUOTE=Luggy]I'm presently getting a 404 when trying to connect to that URL.
Any chance it moved or someone could host the file again?[/QUOTE]
 [http://www.ubuntu-de.org/wiki/windowmanager:gnome:blinkende_fensterleisteneintraege](http://www.ubuntu-de.org/wiki/windowmanager:gnome:blinkende_fensterleisteneintraege)

It's down :/

---

### Post by jcooper on 2005-08-03
I think this latest patch is rolled into the new Gnome release :D

(it's in Breezy now)

---

### Post by shanghaipi on 2005-08-04
are all these patches going to mess up breezy when it we try to install it over Hoary?  Because I think I'm becoming a patch whore and I'm just worried that I'll forget what patches I've applied...I hope I don't have to revert all of them to install Breezy correctly.

---

### Post by Trojan1313 on 2005-08-07
[QUOTE=zafar]A long wanted feature in gnome is flashing taskbars, to use with programs such as GAIM for new IM notification and others. The code has been submitted in a gnome bugzilla and was submitted into the gnome cvs [/QUOTE]
What's gnome cvs? Does this mean that these blinking things will be included in gnome from now on, or that it's already in?

Can we expect this out-of-the-box with breezy? Or any other new distro-releases for that matter?

---

### Post by Skel on 2005-08-10
link is down :(

---

### Post by NeTo on 2005-08-11
[QUOTE=Skel]link is down :([/QUOTE]
 If someone has webspace to spare, I have built the package with the required patches (i386 only). 

If anyone wants to build the package, the libwnck sources are needed, along with the patches at [http://bugzilla.gnome.org/show_bug.cgi?id=120439](http://bugzilla.gnome.org/show_bug.cgi?id=120439)

There are two patches to apply: [id=46302](http://bugzilla.gnome.org/attachment.cgi?id=46302&action=view) and [id=47053](http://bugzilla.gnome.org/attachment.cgi?id=47053&action=view), in that order. What the patches do is explained in the bugzilla page.

You can additionaly edit the debian changelog, so the version number is higher than the one in the Ubuntu repositories. I used 2.10.0-1~neto1 (the ~ should ensure that the package is upgraded if 2.10.1 or higher appears in the repositories in the future).

Three packages are built from libwnck. Of those, libwnck16 is the one to install.

Finally, if you want to tweak the glow (fade?) effect, you can modify the wnck_task_button_glow function in tasklist.c (after patching). The sine function at line 475 is the one to look at. You can easily modify the amplitude and/or the duration of the effect.

---

### Post by Spudgun on 2005-08-12
Can someone host the i386 file for me? Damn address is not resolving :/

---

### Post by traherom on 2005-08-12
[QUOTE=NeTo]If someone has webspace to spare, I have built the package with the required patches (i386 only). [/quote]Someone volunteer!

Actually, if there are noone soon, I'll host. Just hope my ISP doesn't finally catch on to my server. [img]http://ubuntuforums.org/images/smilies/eusa_whistle.gif[/img] PM me if you can't find someone else.

---

### Post by cutOff on 2005-08-12
[http://www.ubuntu.lt/render/Articles;aid,24](http://www.ubuntu.lt/render/Articles;aid,24) 

Hope this helps.

---

### Post by Spudgun on 2005-08-12
Thanks :D And thanks for the offer, traherom!

---

### Post by shanghaipi on 2005-08-12
So will this patch screw up Breezy when its October?

---

### Post by dryandplain on 2005-08-13
I'll gladly host this if someone will email me the file.

dryandplain atsymbol netscape period net

---

### Post by dryandplain on 2005-08-14
> Hi! I'm writing in response to the HOWTO: Flashing taskbar in Gnome thread at the Ubuntu forums.

I have attached the deb file I built for the i386 platform, along with the patched sources.
The deb has a different version to the ones posted before in thread. I bumped up the version number so the hold option doesn't need to be used at all. Only dpkg -i needs to be used for the package, and it won't be replaced by the one in the hoary repos (it will be replaced by the breezy one when it comes out).

Thank you for your time and have a nice day!
This link should be remain valid for quite some time:
[http://consolevision.com/members/upload/libwnck16_2.10.0-1_neto1_i386.deb](http://consolevision.com/members/upload/libwnck16_2.10.0-1_neto1_i386.deb)

I had to rename the ~ to an underscore in the filename, as my host wouldn't support it.

---

### Post by traherom on 2005-08-14
[QUOTE=dryandplain]This link should be remain valid for quite some time:
[http://consolevision.com/members/upload/libwnck16_2.10.0-1_neto1_i386.deb](http://consolevision.com/members/upload/libwnck16_2.10.0-1_neto1_i386.deb)

I had to rename the ~ to an underscore in the filename, as my host wouldn't support it.[/QUOTE]Thanks!

---

### Post by jamesrw on 2005-08-22
what about a link for the amd64? that is still down. I have webspace, let me know. 

Also, has anyone answered wether patches will screw up breezy!?!?

---

### Post by jaac on 2005-08-22
[QUOTE=jamesrw]Also, has anyone answered wether patches will screw up breezy!?!?[/QUOTE]

I hope so  :-|

---

### Post by NeTo on 2005-08-22
[QUOTE=jamesrw]what about a link for the amd64? that is still down. I have webspace, let me know. 

Also, has anyone answered wether patches will screw up breezy!?!?[/QUOTE]

I can send you the patched sources if you want to build them on amd64. The process should be as simple as untaring the sources and run *dpkg-buildpackage -b -uc*.
 
The package shouldn't screw up breezy, as I set the version number higher than the one in hoary, but lower than the one in breezy (I simply added a ~ to the version number). That means it'll be replaced whenever you upgrade.

---

### Post by gammyhand on 2005-08-22
[QUOTE=NeTo]I can send you the patched sources if you want to build them on amd64. The process should be as simple as untaring the sources and run *dpkg-buildpackage -b -uc*.
 
The package shouldn't screw up breezy, as I set the version number higher than the one in hoary, but lower than the one in breezy (I simply added a ~ to the version number). That means it'll be replaced whenever you upgrade.[/QUOTE]
 A masterpiece! Thank VERY much. I hated not knowing if I had an IM.

---

### Post by jamesrw on 2005-08-22
[QUOTE=NeTo]I can send you the patched sources if you want to build them on amd64. The process should be as simple as untaring the sources and run *dpkg-buildpackage -b -uc*.
 
The package shouldn't screw up breezy, as I set the version number higher than the one in hoary, but lower than the one in breezy (I simply added a ~ to the version number). That means it'll be replaced whenever you upgrade.[/QUOTE]
 send away, emails in the sig,

---

### Post by jamesrw on 2005-08-23
thanx for sending the files, but I had some trouble..

```
james@tux64:~/Desktop/libwnck_2.10.0-1~neto1.tar.gz_FILES/libwnck-2.10.0$ sudo dpkg-buildpackage -b -uc
dpkg-buildpackage: source package is libwnck
dpkg-buildpackage: source version is 2.10.0-1~neto1
dpkg-buildpackage: source maintainer is Ernesto Villarroel <villapancho@email.com>
dpkg-buildpackage: host architecture is amd64
dpkg-checkbuilddeps: Unmet build dependencies: libgtk2.0-dev (>= 2.5.4) libstartup-notification0-dev (>= 0.7-1) cdbs gnome-pkg-tools libxt-dev | xlibs-dev (<< 4.3.0)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
```


I went ahead and used the -d flag...


```
james@tux64:~/Desktop/libwnck_2.10.0-1~neto1.tar.gz_FILES/libwnck-2.10.0$ sudo dpkg-buildpackage -b -uc -d
dpkg-buildpackage: source package is libwnck
dpkg-buildpackage: source version is 2.10.0-1~neto1
dpkg-buildpackage: source maintainer is Ernesto Villarroel <villapancho@email.com>
dpkg-buildpackage: host architecture is amd64
 debian/rules clean
debian/rules:3: /usr/share/cdbs/1/class/autotools.mk: No such file or directory
debian/rules:4: /usr/share/cdbs/1/rules/debhelper.mk: No such file or directory
debian/rules:5: /usr/share/cdbs/1/rules/simple-patchsys.mk: No such file or directory
debian/rules:6: /usr/share/cdbs/1/class/gnome.mk: No such file or directory
debian/rules:7: /usr/share/gnome-pkg-tools/1/rules/uploaders.mk: No such file or directory
make: *** No rule to make target `/usr/share/gnome-pkg-tools/1/rules/uploaders.mk'.  Stop.
```

I leave something out??

---

### Post by NeTo on 2005-08-23
AFAIK, you should use -d flag if you want to force the package to build against an older version of the required libraries.

Your case is different though, as you don't have any version installed of those libraries.

To install them you just need to run:```
sudo apt-get install build-essential
sudo apt-get build-dep libwnck
```Omit the build-essential line if you already have that package installed.

After the packages are downloaded and installed you can run dpkg-buildpackage. Sorry I forgot to tell you about that  :(

---

### Post by gorkhal on 2005-08-24
this is so much cooler than windows...an excellent howto zafar...

i stopped talking to ppl on gaim now...just stare at the blinky taskbar...stare...stare...cant stop staring...stare...  :)

---

### Post by npu on 2005-08-24
great stuff! finally.

thanks!

hope x-chat will implement urgent soon.

---

### Post by jamesrw on 2005-08-24
[QUOTE=npu]great stuff! finally.

thanks!

hope x-chat will implement urgent soon.[/QUOTE]

oh but there is, it was a little buggy for me but worked:
[http://blight.altervista.org/index.php?act=Systray](http://blight.altervista.org/index.php?act=Systray)

---

### Post by arunsub on 2005-08-26
I have AMD64, but I'm using 32-bit Ubuntu. If i want to do this, should I use x86 or x86-64?

---

### Post by majikstreet on 2005-08-26
You rule.

Thank you so much.

I must read these forums like mad again.

I hate it when people im me and I  don't know!!! Now I will.

Thanks.

majikstreet

---

### Post by dabear on 2005-08-26
[QUOTE=arunsub]I have AMD64, but I'm using 32-bit Ubuntu. If i want to do this, should I use x86 or x86-64?[/QUOTE]
You should use x86

---

### Post by Trojan1313 on 2005-08-27
[QUOTE=arunsub]I have AMD64, but I'm using 32-bit Ubuntu. If i want to do this, should I use x86 or x86-64?[/QUOTE]
...why? :) Recently upgraded PC?

---

### Post by EnderTheThird on 2005-09-01
Anyone know if there's a way to do this while running the i686 kernel?

---

### Post by LaSSarD on 2005-09-15
Hey guys, I was using hoary and this patch was awesome, working perfect... I recently upgraded to Breezy using apt-get dist-upgrade and now the list of windows do not appear anymore... :(
I search for a breezy version of libwnck16 in packages.ubuntu.com, but it doesn't seem to exist =/
Any ideas?
Thanks :)

---

### Post by pgmario on 2005-09-17
[QUOTE=LaSSarD]Hey guys, I was using hoary and this patch was awesome, working perfect... I recently upgraded to Breezy using apt-get dist-upgrade and now the list of windows do not appear anymore... :(
I search for a breezy version of libwnck16 in packages.ubuntu.com, but it doesn't seem to exist =/
Any ideas?
Thanks :)[/QUOTE]

If you did this after installing the patch in Hoary:
```
sudo echo libwnck16 hold | sudo dpkg --set-selections
``` the package has not been updated.

Try
```
sudo echo libwnck16 install | sudo dpkg --set-selections
sudo apt-get update
sudo apt-get upgrade libwnck16
killall gnome-panel
```

---

### Post by LaSSarD on 2005-09-17
Thank you very much, **pgmario**! It might work, but I solved it by doing the following:
```
sudo apt-get install --reinstall libwnck-common
wget http://ftp.cs.umn.edu/pub/ubuntu/pool/main/libw/libwnck/libwnck16_2.10.0-0ubuntu1_i386.deb
sudo dpkg -i libwnck16_2.10.0-0ubuntu1_i386.deb
```

**EnderTheThird**, I'm using kernel 686 and I've got no problems with it (except when I've upgraded to breezy, but this is no kernel related) ;)

---

### Post by majikstreet on 2005-09-17
By the way, I believe that in breezy, it does this automatically... It's much nicer here in breezy :)

---

### Post by LaSSarD on 2005-09-17
[QUOTE=majikstreet]By the way, I believe that in breezy, it does this automatically... It's much nicer here in breezy :)[/QUOTE]
 Yes, on Breezy it works exactly the same way that the modified version on Hoary does ^^

---

### Post by pgmario on 2005-09-17
[QUOTE=majikstreet]By the way, I believe that in breezy, it does this automatically... It's much nicer here in breezy :)[/QUOTE]
Yes, I think it's in Gnome 2.12 by default.

---

### Post by psylvester on 2005-09-29
Start up GAIM and click Tools and then Preferences. Then click on the "Plugins" preference and check the checkbox beside the Message Notification plugin. After that there should be a Message Notification preference entry under the parent "Plugins". Click on that and it should give a list of options for the Message Notification plugin. Check the box for "set window manager "URGENT" hint and configure the rest of the options to your liking. Now, when you recieve a new message, your taskbar will flash to notify you.

its Doesnt Work for me. Can u help me????:rolleyes:

---

### Post by Superdarion on 2007-01-21
Anyone knows how to set the notifications to urgent on aMSN?

---

