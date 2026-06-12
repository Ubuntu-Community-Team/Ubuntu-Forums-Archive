---
title: "Windows ASP/MSSQL programmer being out dated, needs to move to *NIX quick! Ubuntu?"
date: 2005-12-05
forum: Programming Talk
---

### Post by cloneofsnake on 2005-12-05
Hi there,

I work for a certain web company that is mainly a FreeBSD house, but I actually came from a small company that was bought and merged into the big family.  I am still working on those legacy apps that came with the small company, I mainly do MS SQL stuff w/ a little ASP.  Now, the mother company has some other group started "upgrading" our apps to their UNIX environment, running PHP, MySQL and Oracle... etc.  So, this means I'm outdated!  I need to "upgrade" myself quick!

I've installed and tried Mandrake (9.2?), Knoppix, and recently SUSE 10.  My computer at home now has SUSE 10 running perfectly, but I don't really like its directory structure (from what I've heard and seen, it's not standard Linux like the other distro.)

Now, I'm not sure if this can be achieved, but here's what I want:  I want to set up a Linux at home that is "most similar" to standard UNIX, I need to learn to install packages and programming tools ~ Apache, PHP, MySQL, Oracle... etc.  I just need to learn the basics to get around and install / uninstall stuff.  Then, I will spend most of my energy in programming.

Is Ubuntu a good "UNIX" environment in that sense?  (Is it pretty close to "standard"?  Will I be able to easily apply my knowledge from Ubuntu to a UNIX or FreeBSD environment?)  If not, any suggestions?

Thank you all!

---

### Post by knipknap on 2005-12-05
If you come from Windows desktop application programming and are looking for something similar to .NET, you probably want to use Mono.
That pretty much rules out Fedora, unless you want to install Mono manually.

Not sure about Mandrake, but I guess since they use KDE/Qt they are not too interested in Mono, which is primarily GNOME/Gtk-based.

Novell/SuSE should be fine, but if you already know Unix good enough to be disturbed by YaST's way of doing things, Debian is great.

And lastly, if you want Debian but want it convenient - that's Ubuntu's quest. Welcome home.

---

### Post by cactus on 2005-12-05
if you are searching for industry standard..there are a couple.
your best bet would be to ask what linux distributions are used in the new company..and "learn" those first.
if they use redhat-el, then use centos (free recompiled clone)..quite good.
if they use fedora..use fedora
if they use freebsd...use freebsd.

if they are just using LAMP architecture (linux apache mysql php), then just about any linux distro will do. Just make sure the php and mysql versions are what you are using at work..you should be golden.

good luck. :)

---

### Post by commodore on 2005-12-05
You shoulda start using UNIX earlier cause they rock and they're better than Windows ;)

---

### Post by cloneofsnake on 2005-12-05
[QUOTE=cactus]if they are just using LAMP architecture (linux apache mysql php), then just about any linux distro will do. Just make sure the php and mysql versions are what you are using at work..you should be golden.
[/QUOTE]

They use FreeBSD, but I was hoping that [COLOR="Red"]Linux is close enough to FreeBSD that[/COLOR] if I learn to do the basics (install / adminster) on a standard Linux box, [COLOR="Red"]I can apply my knowledge with relative ease to FreeBSD.[/COLOR]  Anyone knows FreeBSD enough to verify that this is true?  This is my box at home, so I would like to use it to do multimedia and bit torrent and stuff, and I think Linux is probably much better for those "leisure" tasks.

As for programming, I'll need to learn PHP / MySQL.  I've already done some PHP / MySQL at work (small projects, now abandoned).  Since I'm still on MS SQL full time at work, I want to start or join some projects outside of work.  (I think working is the best way to learn.)  Anyone out there learns the same way I do?  [COLOR="Red"]Can anyone suggests any projects (PHP / MySQL only)[/COLOR]?  Thanks!

---

### Post by cloneofsnake on 2005-12-05
[QUOTE=commodore]You shoulda start using UNIX earlier cause they rock and they're better than Windows ;)[/QUOTE]

Hey.. better late than never right?  That's what I'm trying to do now... besides, work really takes one's energy & time away... I have always been passionate about technology and games, but recently I have no energy / time to do much outside of work!  Don't get me wrong... I love what I do and all... but work is work... and it SUCKS!  (It sucks the life outta ya! :) )

---

### Post by Jonne on 2005-12-05
You can do php & mysql on every OS. You can even stay on Windows to write your scripts (although some stuff is different on Windows, things like permissions are weird, but these are things you rarely encounter. php scripts are generally portable).

If your job really is only writing php scripts (and the occasional shell script), you shouldn't worry about which OS to use. Use the one that suits you best. Ubuntu would be a good choice to do that, as installing & configuring apps is very easy (provided they're in the repo's ;) ).

Remember that you can run Apache, PHP and MySQL on anything.

---

### Post by jerome bettis on 2005-12-05
linux is not unix. i'd recommend you look at gentoo if you really want to learn how nix systems work. it provides the nice things about linux, but is advanced enough to force you to learn things. but it's still different from unix in a lot of ways, however very similar in nature.

the one downside of gentoo is that it compiles your programs instead of just installing a precompiled binary. so if you want to install crap like kde, open office etc (you really shouldn't) it can take a very long time.

if you do try it, don't expect it to be easy. expect lots of reading and a few problems which you will have to solve along the way. however in the end you'll be better off than if you just popped in the mandrake cd.

---

### Post by Burke on 2005-12-05
[QUOTE=cloneofsnake]They use FreeBSD, but I was hoping that [COLOR="Red"]Linux is close enough to FreeBSD that[/COLOR] if I learn to do the basics (install / adminster) on a standard Linux box, [COLOR="Red"]I can apply my knowledge with relative ease to FreeBSD.[/COLOR]  Anyone knows FreeBSD enough to verify that this is true?  This is my box at home, so I would like to use it to do multimedia and bit torrent and stuff, and I think Linux is probably much better for those "leisure" tasks.[/QUOTE]

FreeBSD is in some respects *very* similar to Linux, and knowledge tends to be mostly transferrable between the two, but I would recommend using FreeBSD if that's what they use at work.  As for the whole 'Linux is better for Desktop users' thing, I disagree. This was once true, but this concept has become outdated.  Once you have FreeBSD installed and have some of the basic concepts figured out, it is very much the same as Linux in terms of functionality. Whereas Ubuntu has Apt-get, FreeBSD has ports.  Both install software with one command (or two clicks, with the right frontend...)

Case in Point, either is fine, but I recommend FreeBSD for you. If you feel you would really rather use Linux, I think Ubuntu is a great choice, but Gentoo ([http://gentoo.org](http://gentoo.org)) tends to be more FreeBSD-ish. Your call. Good luck.

---

### Post by Burke on 2005-12-05
[QUOTE=jerome bettis]...i'd recommend you look at gentoo if you really want to learn how nix systems work.[/QUOTE]

I completely agree. I installed Gentoo, and it was an extremely educational experience. I highly recommend it.

---

### Post by nemik on 2005-12-05
i still have nightmares from my gentoo experience. i might trry it again one day but not soon.

if you're going to be coding php/m,ysql (my favourite combo) then ubuntu should be a good enough dev environment to mimic your BSD set-up at work. but if you're going to be doing actual BSD administration and advanced stuff in there( clustering up computers, hosting and such) then install BSD itself from scratch may be the way to go.

either way, welcome and all the best. php and mysql are really a wonderful combo IMO.

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=cloneofsnake]Hi there,

I work for a certain web company that is mainly a FreeBSD house, but I actually came from a small company that was bought and merged into the big family.  I am still working on those legacy apps that came with the small company, I mainly do MS SQL stuff w/ a little ASP.  Now, the mother company has some other group started "upgrading" our apps to their UNIX environment, running PHP, MySQL and Oracle... etc.  So, this means I'm outdated!  I need to "upgrade" myself quick!

I've installed and tried Mandrake (9.2?), Knoppix, and recently SUSE 10.  My computer at home now has SUSE 10 running perfectly, but I don't really like its directory structure (from what I've heard and seen, it's not standard Linux like the other distro.)

Now, I'm not sure if this can be achieved, but here's what I want:  I want to set up a Linux at home that is "most similar" to standard UNIX, I need to learn to install packages and programming tools ~ Apache, PHP, MySQL, Oracle... etc.  I just need to learn the basics to get around and install / uninstall stuff.  Then, I will spend most of my energy in programming.

Is Ubuntu a good "UNIX" environment in that sense?  (Is it pretty close to "standard"?  Will I be able to easily apply my knowledge from Ubuntu to a UNIX or FreeBSD environment?)  If not, any suggestions?

Thank you all![/QUOTE]

Ha!  I wish I had your problem!  I will probably be pounding out the VB code for a living till the day I die!

I think from the perspective of someone who is switching from Windows to a *NIX, the BSDs, Unices, and Linuxes all have a lot more in common with each other than with Windows.  There are differences in the details (where config files are located, what various command line options do, etc.), but I think the overall feel is pretty similar.  Many of the concepts are transferable, but you learn never to take certain things for granted.

---

### Post by fct on 2005-12-06
Since FreeBSD is what your company is using, it's freely available and there are tons of documentation available on internet, I suggest you go for FreeBSD.

Although both FreeBSD and Linux are mostly UNIX, FreeBSD has some differences when it comes to system configuration that are interesting to learn (specially things like the "wheel" group, the ports system and the hardware device naming schema).

But if you don't care about administration and just want the programming side, Apache+PHP+MySQL will work the same in both systems.

---

### Post by blanky on 2005-12-06
I agree with a few, if what you use at work is FreeBSD (but in use it, I mean you actually *use* it, not that your administrator uses it or whatever), then you'll be more used to FreeBSD, seeing as you're at work for a long time, you'd be more used to donig things the FreeBSD way. However, for the desktop stuff and multimedia, that'd be a different thing to learn. Learn to get your apps working and stuff. IF you want to have the same OS as your work just because, but you cant get anything to work on it, then I recommend any other OS, probably Ubuntu, where 'it just works', and you still have your LAMP environment (which, as others have said, is available almost anywhere).

---

