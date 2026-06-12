---
title: "What should I try next?"
date: 2007-04-02
forum: Other OS Talk
---

### Post by letitsnow on 2007-04-02
Right now I have a triple boot with Kubuntu 6.10, xp, and opensuse 10.2. I'm not too fond of suse so i'm looking through my pile of distros and i can't decide what to try. My machine is a celeron 2.0ghz, 256mb ram, and integrated graphics. What should i try?
 here's what i have:
Zenwalk 4.2
Sabayon 2.2mini
Sabayon 2.3mini
GoblinX mini 1.4
Simply MEPIS 6.0(i don't really want another ubuntu based distro though)
PCLinuxOS mini me .93a
Knoppix 5.1
and Fiesty

I'm rather intrigued by sabayon and PCLOS, but if the live cd is an indication of system speed sabayon would crawl, and i havn't even burned PCLOS yet.
i'd be keeping xp and kubuntu.

---

### Post by arox on 2007-04-03
Zenwalk 4.4.1, Arch, Gentoo

---

### Post by igknighted on 2007-04-03
If you want PCLOS go with the new one (2007).  The KDE in the older version (0.93) was really buggy.  If you want a PCLOS based distro, try SAM Linux.  It is PCLOS with Xfce. It's really nice.  Sabayon is a good choice.  3.3 is a bit buggier than 3.2 was, but they are live CDs so try them and see how it goes.

Forget Mepis 6.0, it's basically Kubuntu Dapper.  I have never tried GoblinX, so I can't comment on it.  Zenwalk is OK, but really quirky.  It is slack based, so you need to either (a) learn to use lilo as your bootloader, or (b) learn to set up a grub entry manually.  If you choose B, be aware that you need to change the default file system from XFS to something else (ext3 usually).  Also, Zenwalk's repo system doesn't work as well as Suse or Ubuntu's.

Of the distro's you list, Zenwalk will likely be the fastest.  SAM would be a close second if you tried it out.  Feisty is OK, but crashes too much for me (I think my hardware conflicts somewhere, I haven't bothered to figure that part out yet... so you might be OK).  When it worked it was really nice.  It's pretty much edgy with some really nice GUI touches added to it, but also faster.

In short, you have lots of good choices.  Why limit yourself?  If you've got the disks, try them all and leave the one you like best on when you are done.

---

### Post by letitsnow on 2007-04-03
> In short, you have lots of good choices. Why limit yourself? If you've got the disks, try them all and leave the one you like best on when you are done.
You have a good point.:) 
Most of my problem is the lack of disk space, but i'll be ordering a new HD soon. Right now i have all my music on an NTFS partition and i don't really like that, but it has to be there because i don't have enough room to move it and resize.

i think i'll mess with the zenwalk live cd for a while today.

GoblinX is kinda like DSL but slack based, i'm probably not going to install that.

---

### Post by letitsnow on 2007-04-03
ok, zenwalk live is faster than my edgy install, which is faster than windows. i've never liked xfce much though.

---

### Post by igknighted on 2007-04-03
I have never much like Xfce either... but I do find SAM appealing.  If speed is what you really want, try Sidux.  It is based on Debian Sid (so packages are very bleeding edge), but most people just get a stable configuration and just update apps when they want a newer version.  When you feel like updateing everything a simple apt-get dist-upgrade will take care of it (and there is even a script to automate it.  It uses KDE and absolutely flies.  You can install any other DE on it (except Gnome... gnome doesn't make usable packages for Debian Sid... you COULD source compile it... but that would be absurd).

As far as really fast gnome distro's go, you might want to try Foresight (or Oz, Rav_Tux's brew of foresight).  I have used it and found it OK, but gnome doesn't really tickle my fancy and having the package tools in a web browser never really caught on for me.  It is a fast and stable system though.

I know it uses Xfce, but DreamLinux is a solid choice as well.  It's look adn feel is decidely OSX like, but I feel like its just a really solid distro (I like the concept of the dock, but beyond that the OSX look doesn't really do it for me).

Hope this helps... theres a right distro for everyone, the problem is searching through the thousands that exist to find it :)

---

### Post by letitsnow on 2007-04-03
KDE is my favorite DE so anyhting that uses it and is fast is good. i'll take a look at sidux.

I only have one cd-r left so i'm being cautios about how i use it. how many times can you erase and re-burn a cd-rw?

Thanks for taking the time to write all this!

---

### Post by celsofaf on 2007-04-05
> **letitsnow said:**
> KDE is my favorite DE so anyhting that uses it and is fast is good. i'll take a look at sidux.

I use Sidux and also run Arch Linux with KDE. I found Arch to be faster than Sidux, and Sidux is also faster than Kubuntu in my view. You'll like Arch.

---

### Post by letitsnow on 2007-04-06
i just installed PCLOS tr3 and i have to say i like it! it's much faster than kubuntu and the control panel is also nice. i didn't really like the installer, but it got the job done.

one thing i didn't like about sidux is that even discussing codecs on their forums is taboo, that one thing led me to try pclos first.

feisty live didn't recognize either of my swap partitions and wouldn't let me change my resolution from 640x480.

---

### Post by Rodneyck on 2007-04-06
Everything is faster than Kubuntu.

Sidux is great. Run the du-fixes script to install most proprietary stuff. It is an amazing script that basically does everything for you...even cleans up unwanted files and packages.

If you want the codecs installed... use the debian ones (not the ones for ubuntu);

[http://www.debianadmin.com/install-libdvdcss-and-w32-video-codecs-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-libdvdcss-and-w32-video-codecs-in-debian-and-ubuntu.html)

---

### Post by igknighted on 2007-04-06
> **letitsnow said:**
> i just installed PCLOS tr3 and i have to say i like it! it's much faster than kubuntu and the control panel is also nice. i didn't really like the installer, but it got the job done.

one thing i didn't like about sidux is that even discussing codecs on their forums is taboo, that one thing led me to try pclos first.

feisty live didn't recognize either of my swap partitions and wouldn't let me change my resolution from 640x480.

I think discussing codecs in the terms of how Ubuntu handles them is taboo.  With pretty much any distro's forums you go to, try to avoid comparing that distro to Ubuntu... it strikes a lot of nerves.

---

### Post by kerry_s on 2007-04-07
If you really want to get your feet wet, you should try doing a custom install using ubuntu server install. I have found nothing better than building the OS to my needs, from the command line up.

net installer-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

type server, to do the server install
skip the selection screen,tab and enter
after reboot
login
sudo su
apt-get install xorg gdm what_ever_else_you_want_to_use
(Example: apt-get xorg gdm icewm icemc pcmanfm leafpad synaptic)
type> reboot
select your choice from the session menu and login.

Have fun.

---

### Post by RAV TUX on 2007-04-07
> **letitsnow said:**
> Right now I have a triple boot with Kubuntu 6.10, xp, and opensuse 10.2. I'm not too fond of suse so i'm looking through my pile of distros and i can't decide what to try. My machine is a celeron 2.0ghz, 256mb ram, and integrated graphics. What should i try?
 here's what i have:
Zenwalk 4.2
Sabayon 2.2mini
Sabayon 2.3mini
GoblinX mini 1.4
Simply MEPIS 6.0(i don't really want another ubuntu based distro though)
PCLinuxOS mini me .93a
Knoppix 5.1
and Fiesty

I'm rather intrigued by sabayon and PCLOS, but if the live cd is an indication of system speed sabayon would crawl, and i havn't even burned PCLOS yet.
i'd be keeping xp and kubuntu.

Try [COLOR=Purple]**Oz **[/COLOR]Linux.

[img]http://skins.hotbar.com/skins/mailskins/em/google_emoticons/emoti_129.gif[/img]

---

### Post by igknighted on 2007-04-07
> **RAV TUX said:**
> Try [COLOR=Purple]**Oz **[/COLOR]Linux.

[img]http://skins.hotbar.com/skins/mailskins/em/google_emoticons/emoti_129.gif[/img]

[cough]shamelessselfpromotion[/cough] :guitar:

I do plan on giving Oz a try... and I am especially excited about Cvill64 signing on... he was the guy who got me through the initial bumps with Sabayon... hes a great asset.  You should submit Oz to distrowatch to hopefully get on the radar more.

@ the OP: sorry to totally hijack this thread...  As I mentioned above, try them all.  Codecs for sidux (as rodneyck mentioned) are available via the h2 script.  That I believe is stickied in their forum.  It does really everything, its great.

---

### Post by RAV TUX on 2007-04-07
> **igknighted said:**
> [cough]shamelessselfpromotion[/cough] :guitar:

I do plan on giving Oz a try... and I am especially excited about Cvill64 signing on... he was the guy who got me through the initial bumps with Sabayon... hes a great asset.  You should submit Oz to distrowatch to hopefully get on the radar more.

@ the OP: sorry to totally hijack this thread...  As I mentioned above, try them all.  Codecs for sidux (as rodneyck mentioned) are available via the h2 script.  That I believe is stickied in their forum.  It does really everything, its great.

igknighted, Cvill64 is a trusted and good friend and a valuable asset overall to [COLOR=Purple][B][SIZE=5]Oz[/SIZE]

[COLOR=Black]@the OP if I haven't mentioned it before try:

Wolvix 

Developed by another good friend and member of The CafeLinux Forum....also one of the best Linux distros out.

[IMG]http://skins.hotbar.com/skins/mailskins/em/google_emoticons/emoti_205.gif[/IMG]
[/COLOR][/B][/COLOR]

---

### Post by letitsnow on 2007-04-07
Thanks for all the input!

i got some cd-rw's, so i'm good to go, now all i need is some HD space.

I haven't heard anything bad about OZ yet, so i'll keep an eye on it. any plans for a KDE OZ?

if i'm bored enough tonight i might try a server ubuntu 7.04 install to replace my odd acting kubuntu 6.1 install

---

### Post by Nda on 2007-04-07
I would also strongly suggest trying SAM 2007.  I've tried a few live CDs lately (including Zenwalk, Wolvix, and others) because I want to escape from the religious zealots increasingly influencing Ubuntu and these forums, and SAM is the only one that has impressed me sufficiently to install it.

It's good to look at, quick, and very well equipped: up-to-date software, codecs, flash, Java, etc. are all in there.  The only software I needed to install was Thunderbird to replace Sylpheed-Claws.  Installation from the live CD was quick and easy, GRUB and Synaptic are familiar to Ubuntu users, the SAM and PCLOS forums are good-natured and helpful (and religion free!).

If you are interested in 3D desktops you will find both Compiz and Beryl installed.  My IBM T30 laptop only has a Radeon M7500 integrated graphics chip and I was surprised to find that Beryl not only runs on it, but runs very smoothly indeed, and - so far - flawlessly.  I've never even tried installing Beryl before but at the moment I'm having a great time playing with its many options.

If you prefer KDE to Xfce you will find SAM's repositories have what you want as it's parent PCLOS is KDE-based.

I haven't wanted or needed to use Dapper since I installed SAM a week ago and I'm looking forward to learning more about GNU/Linux variants by comparing .rpm with .deb package systems, and some different commands and procedures.  Give it a try and see for yourself.

Nda

---

### Post by letitsnow on 2007-04-07
What's the difference between SAM and PCLOS? they are both KDE, aren't they?

i noticed the preinstalled compiz and beryl, but i can't run them, i'm not sure if it's my i810 integrated graphics or my 256 ram, but it just slows way down when it's on. did the same in ubuntu. 

> because I want to escape from the religious zealots increasingly influencing Ubuntu and these forums
i have an opinion about that, but it's a different discussion.:)

---

### Post by RAV TUX on 2007-04-07
> **letitsnow said:**
> Thanks for all the input!

i got some cd-rw's, so i'm good to go, now all i need is some HD space.

I haven't heard anything bad about OZ yet, so i'll keep an eye on it. any plans for a KDE OZ?



Oz comes with both KDE and Gnome by default, you can either install either one or both

---

### Post by RAV TUX on 2007-04-07
> **Nda said:**
> I would also strongly suggest trying SAM 2007.  I've tried a few live CDs lately (including Zenwalk, Wolvix, and others) because I want to escape from the religious zealots increasingly influencing Ubuntu and these forums, and SAM is the only one that has impressed me sufficiently to install it.

It's good to look at, quick, and very well equipped: up-to-date software, codecs, flash, Java, etc. are all in there.  The only software I needed to install was Thunderbird to replace Sylpheed-Claws.  Installation from the live CD was quick and easy, GRUB and Synaptic are familiar to Ubuntu users, the SAM and PCLOS forums are good-natured and helpful (and religion free!).

If you are interested in 3D desktops you will find both Compiz and Beryl installed.  My IBM T30 laptop only has a Radeon M7500 integrated graphics chip and I was surprised to find that Beryl not only runs on it, but runs very smoothly indeed, and - so far - flawlessly.  I've never even tried installing Beryl before but at the moment I'm having a great time playing with its many options.

If you prefer KDE to Xfce you will find SAM's repositories have what you want as it's parent PCLOS is KDE-based.

I haven't wanted or needed to use Dapper since I installed SAM a week ago and I'm looking forward to learning more about GNU/Linux variants by comparing .rpm with .deb package systems, and some different commands and procedures.  Give it a try and see for yourself.

Nda

I could never get PCLinuxOS or SAM to run on my computer

---

### Post by igknighted on 2007-04-07
> **letitsnow said:**
> What's the difference between SAM and PCLOS? they are both KDE, aren't they?

i noticed the preinstalled compiz and beryl, but i can't run them, i'm not sure if it's my i810 integrated graphics or my 256 ram, but it just slows way down when it's on. did the same in ubuntu. 


i have an opinion about that, but it's a different discussion.:)

Nope, SAM is an Xfce distro... the new one with nice compositing :).  I was really impressed, I have a really old laptop that runs Xubuntu that I gave to my g/f cause I hated Xfce in Xubuntu and never could get it to play nice... but between DreamLinux 2.2GL and SAM my opinion of Xfce's capabilities is starting to change.  The only real gripe I have about SAM is that some of that some of the PCLOS tools they use aren't adapted to Xfce at all... for instance if you try to use the Drake control centre to enable auto login, there will be no effect, because it tries to use kdm, while SAM uses gdm.  Overall though it is really well put together.

PS, is wbar in the Ubuntu repo's?  It is by far the smoothest dock I fave seen yet.

---

### Post by darksong on 2007-04-07
PClinuxOS - download the 2007 t3 if you want to try this out - its stable even though its a test, great features and a fairly desent community. Flash and some codexs ect some out of the box. Uses something similar to mandrakes control center (which is very good) and apt-get 4 rpm and snaptic (which is also good) for package management  and it looks great. You will need to do a bit of work getting the 3D drivers working, but this is very simple and requires no useage of command line.

Sabayon - If you want to try a gentoo bases disto, try this - it looks great but 3.3 is buggy at times in my experience, i had alot of problems with slowdown and beryl working initaily. 3D drivers, dvd, mp3, flash and java come out of the box though. Very nice and helpful community. Did i say it looks great - it is probably the best looking distro avalible atm. It has a wide range of software avalible to it, alot of 3D games such as quake 3, doom3 and unreal are avalible for download. This comes in 2 flavors - Mini is your minimalistic system, you will need to add all your apps ect to it. Mini comes with a cut down kde front end and for me the hardware detection in Mini was lacking. The DVD comes packed with applications. 

These are the 2 distros apart from ubuntu that i would recomend atm.

---

### Post by Nils Olav on 2007-04-07
This thread needs more gobolinux.

---

