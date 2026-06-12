---
title: "Ubuntu GTK1.2 Remix"
date: 2008-09-29
forum: Other OS Talk
---

### Post by K.Mandla on 2008-09-29
Hi. I put together a Hardy live CD (using some of the links in the sticky at the top of this forum, by the way ;) ) that uses only GTK1.2 software, and I thought I'd mention it in case anyone is interested. It's nothing earth-shattering, but if you're working on an old machine that can boot from CD, it might be a curiosity. There are lots of better live CDs out there.

In short, you get IceWM-lite, Dillo, Sylpheed-GTK1, emelFM and gtkedit, with a process viewer and an image viewer. It's exceedingly sparse, but kind of quirky. It's also prewired with some speed tweaks, which is either good or bad.

More information:

[http://kmandla.wordpress.com/2008/09/30/ubuntu-gtk12-remix/](http://kmandla.wordpress.com/2008/09/30/ubuntu-gtk12-remix/)
[http://kmandla.wordpress.com/ubuntu-gtk12-remix/](http://kmandla.wordpress.com/ubuntu-gtk12-remix/)

Don't bother telling me if you don't like it or think it pointless; I made it for me, not you. 

On the other hand, if you have a suggestion (outside of changing the theme ... #-o ) I'm willing to listen. Don't expect much though; I'm not in the business of masterminding distros. 

Cheers!

---

### Post by zmjjmz on 2008-09-29
Most sub-300MHz computers don't have 128MB RAM, might want to reduce it to 32Mb or 16MB of RAM.

---

### Post by K.Mandla on 2008-09-30
Good point. I was eyeballing those numbers against that 450Mhz machine I used to experiment upon, and it had 256Mb. But you're right, that was probably an upgrade. Thanks!

---

### Post by chris4585 on 2008-09-30
*downloads* Can't wait to test this out, it looks very interesting

---

### Post by K.Mandla on 2008-09-30
Don't get too excited. It's not *that* great ... ;)

I've found a few rough edges that I need to fix this weekend, but other than that it seems to work fine for the few people that have given me feedback. If you do try it, at least tell me if it worked. :)

---

### Post by Sorivenul on 2008-09-30
Works fabulously!  Whatever "rough edges" might exists, I haven't really found any to complain about.  I was wondering when somebody would come along and do this.  I never had the time myself, and I'm glad this remix exists.  Thanks!

---

### Post by zmjjmz on 2008-09-30
Has anyone tested this out on a reaaaalllllllyyyyyyy old computer yet? Like a Pentium I?
If it works under 32MB RAM, please say so.

---

### Post by chris4585 on 2008-09-30
earlier when i tested it on virtualbox while installing ubiquity xorg freaked out, but i fixed it by switching ttys, then while trying to start ubiquity i got a error, i think it was related to python..  Other then that it looks great

good job K.Mandla

> **zmjjmz said:**
> Has anyone tested this out on a reaaaalllllllyyyyyyy old computer yet? Like a Pentium I?
If it works under 32MB RAM, please say so.

I'm not sure... but I have a friend who just got a old computer 128mbs of ram, it can only do dial up networking.. its that old, it might be a pentium I or II, I'll find out and give it a shot

---

### Post by zmjjmz on 2008-09-30
Ubiquity prolly won't run on something that old...
K.Mandla, do you have any plans on making it possible to install it via the alternate installer?

---

### Post by K.Mandla on 2008-10-01
> **chris4585 said:**
> earlier when i tested it on virtualbox while installing ubiquity xorg freaked out, but i fixed it by switching ttys, then while trying to start ubiquity i got a error, i think it was related to python..  Other then that it looks great
Okay, thanks for that. I hadn't fully installed from the CD yet, just started ubiquity to make sure it was working from the live environment. (I didn't want to overwrite the installation I used to make it, in case I wanted to change something. :roll: ) I'll push a little farther into that and make sure it *really* works.
> **chris4585 said:**
> good job K.Mandla
Thanks! I'm pleased you liked it. :)
> **chris4585 said:**
> I'm not sure... but I have a friend who just got a old computer 128mbs of ram, it can only do dial up networking.. its that old, it might be a pentium I or II, I'll find out and give it a shot
Just a note, I pulled most of the sub-packages that control things like ppp, wireless and so forth. If you wait a few days, I'll rework it so some of those fundamentals are still in place.

I know that sounds rather drastic, but since it was really only for my own use, I didn't have a need for modems, wireless, etc. Probably not a wise move in retrospect. :oops:
> **Sorivenul said:**
> Works fabulously!  Whatever "rough edges" might exists, I haven't really found any to complain about.  I was wondering when somebody would come along and do this.  I never had the time myself, and I'm glad this remix exists.  Thanks!
Wow, you're welcome! :biggrin:
> **zmjjmz said:**
> Has anyone tested this out on a reaaaalllllllyyyyyyy old computer yet? Like a Pentium I?
If it works under 32MB RAM, please say so.
I'd be curious too. If you've got a machine that will scrape the bottom, tell me if it performs like crap. Crap is not part of the plan, but it's always possible to end up there.
> **zmjjmz said:**
> K.Mandla, do you have any plans on making it possible to install it via the alternate installer?
I didn't, but if it turns out to be something of use, I'll make a point of learning how. 

Thanks again for all the positive feedback. Negative feedback ... well, I suppose you can tell me that too. :lol:

---

### Post by zmjjmz on 2008-10-01
Well I'd have to have an alternate installer of sorts to run it on that bottom scraper in the first place :P
Maybe you could modify the [inxtaller](https://code.launchpad.net/~inx-devel/inx/inxtaller) to your liking?

---

### Post by chris4585 on 2008-10-01
> **zmjjmz said:**
> Well I'd have to have an alternate installer of sorts to run it on that bottom scraper in the first place :P
Maybe you could modify the [inxtaller](https://code.launchpad.net/~inx-devel/inx/inxtaller) to your liking?

That would be interesting to see how that plays out

---

### Post by snowpine on 2008-10-01
This is brilliant! Great idea. :)

---

### Post by K.Mandla on 2008-10-01
Thanks! I hope you like it. :)

---

### Post by K.Mandla on 2008-10-01
Okay, wow. Yes, the ubiquity installer goes nuts after picking a partition. I'll have to see I can figure out why, although I doubt there's much I can do about that. I suppose I could rebuild the system with ubiquity installed, but that means there will be a shred of GTK2 stuff in there already. And I don't really know if that will solve the problem.

Maybe an alternate installer CD is a better way to do this after all. And zmjjmz is right, a very low-level machine would never get the live CD working anyway. Please stay tuned. ...

---

### Post by chris4585 on 2008-10-01
hrm the ubiquity installer didn't even start for me :confused:

---

### Post by K.Mandla on 2008-10-01
Did you start it with sudo? It sputters and dies without sudo. Of course, it will probably eventually sputter and die anyway, so sudo doesn't really make that much of a difference. :lol:

---

### Post by chris4585 on 2008-10-02
I don't think I did, when I find the time I'll test it again with sudo and report back

---

### Post by MaxIBoy on 2008-10-02
Quit tempting me, people! I'm running Debian minimal on that new/old computer/server and that's final!

---

### Post by K.Mandla on 2008-10-02
> **MaxIBoy said:**
> Quit tempting me, people! I'm running Debian minimal on that new/old computer/server and that's final!
Oh, come on, it's just a little live CD. You can give it a spin, right ... ? :twisted: :D

---

### Post by K.Mandla on 2008-10-04
Okay, I've tried three times now to get the Ubiquity installer working, and for whatever reason it just doesn't want to play along. So I'm planning on changing direction slightly, and repacking an alternate install CD image over this method. 

On the other hand, I updated the ISO last night and re-uploaded it, this time with Beaver, XPaint, XFig and Ghostview on board as well. I playtested it on my 550Mhz Celeron, and I was quite pleased with the way it performed. It's a shame it can't be installed from that image because it would have been interesting to see it without the CD lag.

If you'd like to take a crack at it, please download the fresh image and toss out the old one. I'm not tacking on version numbers since I don't expect there to be much need for updates; updating between releases would be the only requirement, and that should be handled through the standard methods. And since most of those programs are unlikely to be updated, the software you get when you start it up is probably the freshest it will ever be. :D

Thanks for the feedback and tips; it might take me a little while, but I'm set on recreating this in an installable form. Cheers!

---

### Post by Sorivenul on 2008-10-04
Thanks for the update!  I plan on grabbing the updated image soon.

---

### Post by K.Mandla on 2008-10-04
Cool. Note that I used an account on Filefront as a mirror; I don't know if it's faster, but at least you don't have to rename the ISO.

Sorry you can't install it. If you manage to get that working, let me know.

---

### Post by Sorivenul on 2008-10-04
> **K.Mandla said:**
> Sorry you can't install it. If you manage to get that working, let me know.

I'm sure there's some workaround that can be done that doesn't even involve an installer.  I think kagashe has one posted somewhere on here that may work until an install function gets worked out.  I'll try to find it.

EDIT:  [Found the post]("http://ubuntuforums.org/showpost.php?p=5711022&postcount=23").  I realize the specific one deals with DeLi, but it could easily become a workaround until the installation woes can be resolved.

---

### Post by K.Mandla on 2008-10-19
Finally, after weeks of smacking my head against three different LCDs, I have a script and an ISO that will install this thing, with a relatively narrow margin of error. I've built and rebuilt it on my end at least six or seven times on two different systems, and it seems to be working.

[http://kmandla.wordpress.com/ubuntu-gtk12-remix/](http://kmandla.wordpress.com/ubuntu-gtk12-remix/)

If anyone is interested, or if anyone would be so kind, please give it a whirl on an old machine and tell me how it goes. I've done rock-bottom installs on machines as slow as a 550Mhz Celeron, and it seems to handle well. I'd be curious to see how an even-slower machine takes it.

If you're worried about a machine that can't handle the graphical requirements in a live environment, you *should* (I have to say should, of course) be able to boot to a terminal prompt and run the install script from there. 

Thanks again to zmjjmz for pointing out the inxtaller script; that ended up working perfectly, with a day's worth of nudging. :)

Cheers all!

---

### Post by sertse on 2008-10-19
The inxtaller couldn't handle partitions and generally assumes it'll take the whole HD. I'm guess it's still the case here?

---

### Post by chris4585 on 2008-10-19
> **sertse said:**
> The inxtaller couldn't handle partitions and generally assumes it'll take the whole HD. I'm guess it's still the case here?

more than likely, sertse my variant of the inxtaller (installplus) is the same way.

found here [http://boxbuntu.com/downloads/Scripts/installplus]("http://boxbuntu.com/downloads/Scripts/installplus")

if anyone is interested

there's a few things you have to change though, contact me if you are

I took a while editing the script so I'm pretty proud of it

---

### Post by K.Mandla on 2008-10-20
> **sertse said:**
> The inxtaller couldn't handle partitions and generally assumes it'll take the whole HD. I'm guess it's still the case here?
Yup. You could probably hand-adjust it to work around other partitions and create some kind of dual boot, but that's not something I'm interested in doing. It's GPLv3; someone else can add that.

---

