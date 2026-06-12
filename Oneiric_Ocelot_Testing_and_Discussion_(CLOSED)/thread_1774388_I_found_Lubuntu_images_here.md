---
title: "I found Lubuntu images here"
date: 2011-06-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-06-03
Since this became the go-to thread for Lubuntu dev I felt the need to update image location :)

Look here:

[https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing)

Many thanks to phillw for getting this done.

Original post below the break ;)

********************************************

It took a bit of searching, but I found the Lubuntu alpha1 images here:

[http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/)

The torrent had no seeders though.

**Major edit**; I'd not yet been subscribed to the mailing list (I am now) but Julien Lavergne had posted a very brief release note:

> A quick mail to announcement the availability of Lubuntu Oneiric Alpha
1. This ISO is just a snapshot of current development, there is no big
noticeable changes.

Current changes and know issues :
- Build with "install recommends" by default
- No langpack included
- Include apt-xapian-index, which should be removed later
- gnome-power-manager may crash
- GTK3 applications are ugly 

This ISO is primary for developers which want to test the current result
of the ISO, and testing curent behavior with the GTK2/GTK3 mix, and the
switch to install recommends by default. You can also start testing
Oneiric in the VM by installing it with this ISO.

No need to heavily test the ISO, we are going to switch the build
system, and nothing really new is in (no updates of LXDE and related
packages).

Download : [http://people.ubuntu.com/~gilir/lubuntu-oneiric-alpha1.iso](http://people.ubuntu.com/~gilir/lubuntu-oneiric-alpha1.iso)
Torrent :
[http://people.ubuntu.com/~gilir/lubuntu-oneiric-alpha1.iso.torrent](http://people.ubuntu.com/~gilir/lubuntu-oneiric-alpha1.iso.torrent)
md5sum : [http://people.ubuntu.com/~gilir/md5sum.txt](http://people.ubuntu.com/~gilir/md5sum.txt)

---

### Post by dino99 on 2011-06-03
Thanks, bookmarked :)

as im tired about gnome3 new design, i've installed Lubuntu-desktop & made some tweaks. But i cant find, sadly,  a Lubuntu dedicated forum :(

---

### Post by kansasnoob on 2011-06-03
No Lubuntu forum yet, we just have to use these forums. You can set the "lubuntu" prefix on threads in the main support categories.

---

### Post by kansasnoob on 2011-06-03
The Lubuntu Alpha1 Live CD boots to a tty, so you have to type **startx** to get the DE.

**Edit**: Using 'startx' sort of breaks things. It's much better to use either:

sudo service lxdm start

Or:

sudo /etc/init.d/lxdm restart

Otherwise the only serious thing I noticed was the lack of restart or shutdown buttons.

**Edit #2**: using the commands above instead of using "startx" seem to solve that problem!

I'm installing now so I'll have to pick around for more bugs post-installation and puzzle a bit about what package(s) to file bugs against. I'm thinking just the meta-package "lubuntu-desktop" if I can't think of anything more appropriate.

Not sure what version of LXDE this is but it appears to be a pure LXDE default theme. Rather ugly IMHO but simple and intuitive to use.

**Edit #3**: using one of the correct commands above to start lxdm result in a fairly correct Lubuntu desktop, but it's Alpha1. The GTK+ 3 changes haven't even begun yet.

---

### Post by kansasnoob on 2011-06-03
One more bug so far, upon completing the installation I was asked whether to restart or keep using the Live DE as usual. I chose to restart and after cycling down the CD ejected as expected but the screen was just blank.

So I removed the CD, closed the tray and hit enter, but nothing happened. I tried some common key combos but finally had to use the reset button on my box to complete the restart.

I've now just updated the controlling grub so we'll see what she looks like in a few minutes ;)

Then on to bug filing.

---

### Post by kansasnoob on 2011-06-03
It booted just fine. Something I noticed from lxdm (the login screen) is that it boots the "default" DE, but the list of options includes "lubuntu" and selecting it presents the better looking Lubuntu DE. That is of course just my opinion.

It's so early in development that it's unrealistic to expect things to be anywhere near polished and I need to further explore the ins and outs of Lubuntu/LXDE.

I think I'll try Xchat/IRC again, in the past I've just not been able to keep up with it though.

I need to study the lxpanel a lot :)

---

### Post by kansasnoob on 2011-06-03
I posted a query at "lubuntu-desktop@lists.launchpad.net":

> First a brief intro. I'm Erick Brunzell at Launchpad, Lance at iso-testing (in which I've participated for over 3 years), and "kansasnoob" at Ubuntu forums.

I'm quite glad to see that Lubuntu will soon become an official member of the Ubuntu family. I particularly look forward to the day that Lubuntu's images are included in Ubuntu's iso-testing.

Anyway I obtained the Lubuntu Oneiric Alpha1 image here:

[http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/)

And naturally I encountered a few minor bugs. To expect any less this early in a dev cycle is insane, but I still felt they should be reported. The specific bugs are:

1) The Lubuntu Alpha1 Live CD boots to a tty, so you have to type startx to get the DE.

2) The default DE lacks restart or shutdown buttons.

3) Upon completing the installation I was asked whether to restart or keep using the Live DE as usual. I chose to restart and the CD ejected as expected but the screen was just blank. So I removed the CD, closed the tray and hit enter, but nothing happened. I tried some common key combos but finally had to use the reset button on my box to complete the restart.

Of course none of these are serious or unexpected this early in a dev cycle, but I wanted to get my feet wet checking out bug filing against Lubuntu anyway, and I'm a bit puzzled.

I'm used to iso-testing pure Ubuntu so all of the above bugs would be filed against 'casper' but I know these bugs were not present when I tested Ubuntu so I thought I should possibly file them against the meta-package 'lubuntu-desktop' but that's a no-go.

I'm just wondering if the meta-package 'lubuntu-desktop' should be added to launchpad as a bug filing option?

How stupid was that?

---

### Post by teh603 on 2011-06-03
I'm watching Lubuntu as well, but its hard to find the releases since the forum people don't sticky the download links in the forums anymore. =/

---

### Post by phillw on 2011-06-04
Hi guys, LTNS.

I consider my wrists slapped!

>  hiyas kansasnoob,

firstly, great to see you - I don't get onto the forum areas as much as I used to (or should do). The A1 is still built the 'old way' and is, afaik, just a toe stretching session for the new kernel to be included. There has been some work the apps done, along with deciding which applications we include by default. Pcman has a new pcmanfm out in the wild for us to break. Hooks for apport are on the TODO list and are being added, but the 1,000 dedicated developers we have ..... err, well, I may have over estimated by 998 are awaiting getting their teeth into the 'official' iso building system. This should be done for a2.

The general page for 11.10 is at [https://wiki.ubuntu.com/Lubuntu/Developers](https://wiki.ubuntu.com/Lubuntu/Developers) 

Progress on the apport hooks can be found at [https://wiki.ubuntu.com/Lubuntu/Developers/TODO](https://wiki.ubuntu.com/Lubuntu/Developers/TODO) 

If you, or any of the testers on the main area would like to keep abreast of what Lubuntu is up to, please doe feel free to add the mailing list to your cluttered boxes (We don't send that many out!) [https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)  has the one click link to get the lubuntu discussions.

Please give my regards to Ranch Hand, I must pop on and find out what better name he has for 11.10 - I will make a point of letting the testing area know when A2 comes out, but the a1 had little in the way of changes. 

Apart from anything else, it will be nice to 'touch base' with all you great people again.
For A2, I will try to get a set of notes together so you good people know where Lubuntu is headed for 11.10, as it is the precursor for 12.04 (LTS) we need to get as many bugs ironed out as possible during the 11.10 cycle (errr, you may recall Grub2 coming out in 9.10 :P ). 
Lubuntu is also now popping it's toe into the water for accessibility, but realistically this is a couple of cycles away - we simply do not have enough devs. Accessibility could do themselves a favour, but we do have a meeting coming up under Jono Bacon to allow us to ask questions. It is times like this I miss Ranch Hand's 'say it as it is' attitude, although JM one of our devs is no shrinking violet. I'm sure he and Ranch Hand would get on great :P

My kindest regards to you and the rest of the testers,

Phill.
P.S. - Now go and dig me up a spare developer or two :D
@ Julien and JM - if there is any thing factually incorrect, please correct me.

I will keep you all up to date - I promise!

Regards,

Phill.

---

### Post by kansasnoob on 2011-06-04
I'm glad to see you around. I did read the PM's from both you and Chris, I just haven't had time to respond properly :(

My greatest concern was just figuring out how to properly file and assign bugs to "lubuntu-desktop", but in retrospect the one's I mentioned are either casper or ubiquity bugs so I'd assume it'd be proper to file against those packages with an explanation (including comparison of behavior between Ubuntu and Lubuntu).

However, I do still wonder if the meta-package "lubuntu-desktop" shouldn't be somehow added to possible bug filing options :confused:

When Lubuntu is included in iso-testing I'll shift a large part of my focus onto it, but naturally I'll have a learning curve to tackle ;)

The new ubiquity is a challenge within itself but hopefully this month I should get a router up and running so I'll be able to test on at least two PC's at the same time (three after adding a KVM switch).

The third is a low spec PII 333MHZ CPU w/256MB of RAM so that could be quite helpful in regards to Lubuntu. It does run Lubuntu 11.04 just fine.

I'm having a bit of trouble learning how to tweak LXPanel, but it's just a matter of learning :D

At some point it would be cool to be able to add "drag-n-drop" to the panel, but that's another story for another day.

The thing is Unity, and particularly gnome3, have just presented too many obstacles and I've always admired the lightweight aspect of Lubuntu anyway. Why devote more system resources to a DE than needed?

Regardless I hope having an experienced iso-tester dedicated to the project may be helpful.

---

### Post by SevenMachines on 2011-06-04
I'd think lxde will probably get more attention now the gnome3 and unity moves are made, its always seemed like the more natural 'classic' desktop move for those who arent too fond of gnome3/unity (although xfce is still nice too :) ) gnome3's fallback isnt really the same.

---

### Post by kansasnoob on 2011-06-04
> **SevenMachines said:**
> I'd think lxde will probably get more attention now the gnome3 and unity moves are made, its always seemed like the more natural 'classic' desktop move for those who arent too fond of gnome3/unity (although xfce is still nice too :) ) gnome3's fallback isnt really the same.

I have always liked LXDE. But I found gnome2 to be sooooo easy to customize that I only fiddled around a little bit.

Now, I don't hate Unity, I just honestly feel like I'm not smart enough (or capable enough due to age and visual limitations) to use Unity and/or gnome3.

IMHO the most accurate comment I've read from the Gnome devs is this:

> Port to GSettings: since we wanted to be cool, there was no way we would still use the venerable gconf to store settings. Porting to GSettings was quite fun, especially as gnome-panel was probably one of the heaviest user of gconf (and it was certainly using it in interesting ways). We now use GSettings in interesting ways too since some API is still missing in GSettings. Oh, and we're also using dconf (which is what GSettings uses as a backend by default) directly, **[COLOR="Red"]which is completely insane and crazy. But we love insane and crazy![/COLOR]**

Source:

[http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead%2C-long-live-gnome-panel](http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead%2C-long-live-gnome-panel)!

I can certainly see why Ubuntu/Canonical decided to go with Unity. IMO Unity is only frustrating, gnome3 itself is absolutely horrible :mad:

Regardless, Lubuntu did finally get the blessing from SABDFL so they're now truly part of us. I can't find the link ATM but I did read that Lubuntu will also eventually offer Unity.

I somehow doubt though that LXDE themselves would embrace that, at least not any time soon.

For me it's time to tell Gnome I'm going away soon: "Sorry Gnome, I loved you for a long time but you just got too insane and crazy"!

---

### Post by kansasnoob on 2011-06-04
I did file a "test" bug report:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/792850](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/792850)

We do need to know how to file bugs against Lubuntu :D

I also posted a reply at the Lubuntu mailing list asking if we might benefit from a sub-forum here:

[http://ubuntuforums.org/forumdisplay.php?f=46](http://ubuntuforums.org/forumdisplay.php?f=46)

That might be helpful while Lubuntu transitions to full status and develops it's own forum, or it may be dumb idea - I do have dumb ideas from time to time :)

---

### Post by SevenMachines on 2011-06-04
Personally i was using gnome2 with a very minimal panel and gnome-do, which is pretty much where gnome3 and unity have headed so i'm ok with using them. Without encouraging any more threads with endless unity/gnome3 discussions :) i'm fairly ok with unity's simplicity, with a little hacking around. 
Back on topic though, i had looked at xfce and lxde occasionally at times and thought they were nice but were gnome2-ish enough not to really stand out. Now they do stand out, and, thanks to your thread, i had a new look a lxde and have to say i was impressed by the improvement since last time. It looks a lot more polished than i remember, that may be a mix of improvements in lxde and my poor memory obviously! Seems like a good choice for more focus and buffing for those who want a more recognisable desktop. Whatever peoples personal preference, i'm always impressed by having a choice at gdm (well, lightdm!) of a real range of quality options, a nice sign of a lot of people beavering away on the things they like, and well appreciated whether its something i would go for or not. Ah, the agony of choice :)

---

### Post by SevenMachines on 2011-06-04
Personally i think that the release+1 forum might benefit from a couple of sub-forums itself for this kind of thing. A lot can get lost when bugs/testing/cafe discussions are bundled together.

---

### Post by phillw on 2011-06-04
> 
Regardless, Lubuntu did finally get the blessing from SABDFL so they're now truly part of us. I can't find the link ATM but I did read that Lubuntu will also eventually offer Unity.


Hmm, do try to find the link, as the last I heard was that the only alteration to Lubuntu regarding Unity would be possibly be people unhappy with Unity and switching to LXDE.

But, our devs are peculiar creatures, if they believe that they can fit Unity into the spec of [ Minimal Spec](https://help.ubuntu.com/community/Lubuntu#System requirements) for Lubuntu I guess I'll have more wiki pages to write up and link up to!

Regards,

Phill.

---

### Post by teh603 on 2011-06-04
> **phillw said:**
> Hmm, do try to find the link, as the last I heard was that the only alteration to Lubuntu regarding Unity would be possibly be people unhappy with Unity and switching to LXDE.
I'll be honest, I see LXDE more as a way to keep stringing out older hardware than an alternative to Unity. For me, the "best" alternative is KDE, which I've found to be fairly easy to theme and has a lot of easily-installable theme packages.

That having been said, Xubuntu and Lubuntu have their place. There's so much older hardware like my eeePC 701 and Winbook M Series out there that still runs, and runs well, but might choke a bit on a full-size modern frontend.

Puppy is right out until they can find a way to make their disto actually install on a hard drive and work properly >.>

---

### Post by phillw on 2011-06-04
> **teh603 said:**
> ...the "best" alternative is KDE, ...

Oddly enough lubuntu and kubuntu people work together ;) As do we with Xubuntu and Ubuntu.

Whilst some may like to start a war with Ubuntu Vs Kubuntu Vs Xubuntu Vs Lubuntu Vs Edubuntu Vs MythUbuntu Vs etc.... In practice they are doomed to failure. All the devs and team members are committed to the Ubuntu ethos and happily chat to each other and swap ideas.

The thought of Bill Gates and Steve Jobs having such a chat does really prove the advantage of F/OSS :)

Regards,

Phill.

---

### Post by ronacc on 2011-06-04
> **teh603 said:**
> 
Puppy is right out until they can find a way to make their disto actually install on a hard drive and work properly >.>

off topic but what problem are you having with a HD install of puppy ?

---

### Post by DougieFresh4U on 2011-06-04
> **teh603 said:**
> 

Puppy is right out until they can find a way to make their disto actually install on a hard drive and work properly >.>

> **ronacc said:**
> off topic but what problem are you having with a HD install of puppy ?

Installed Puppy many times to HD

---

### Post by ronacc on 2011-06-04
I also have done many HD installs of puppy , I really like the way it handles random networks .

---

### Post by kansasnoob on 2011-06-05
> **phillw said:**
> Hmm, do try to find the link, as the last I heard was that the only alteration to Lubuntu regarding Unity would be possibly be people unhappy with Unity and switching to LXDE.

But, our devs are peculiar creatures, if they believe that they can fit Unity into the spec of [ Minimal Spec](https://help.ubuntu.com/community/Lubuntu#System requirements) for Lubuntu I guess I'll have more wiki pages to write up and link up to!

Regards,

Phill.

I think that may have been a bad dream derived from this:

> Support for global menu in lxpanel : TODO 

I'm not too crazy about the global menu.

Source (more than bite size):

[https://wiki.ubuntu.com/Lubuntu/Developers/TODO](https://wiki.ubuntu.com/Lubuntu/Developers/TODO)

---

### Post by kansasnoob on 2011-06-05
> **teh603 said:**
> I'll be honest, I see LXDE more as a way to keep stringing out older hardware than an alternative to Unity. For me, the "best" alternative is KDE, which I've found to be fairly easy to theme and has a lot of easily-installable theme packages.

That having been said, Xubuntu and Lubuntu have their place. There's so much older hardware like my eeePC 701 and Winbook M Series out there that still runs, and runs well, but might choke a bit on a full-size modern frontend.

Puppy is right out until they can find a way to make their disto actually install on a hard drive and work properly >.>

At one point I found Lubuntu's pcmanfm lacking considerably but I now find I can navigate my mess just as easily with it as I can with nautilus.

I do however prefer the added bloat of a few Gnome apps, like gedit, but a lot of that is just personal preference.

---

### Post by teh603 on 2011-06-05
> **ronacc said:**
> off topic but what problem are you having with a HD install of puppy ?The fact that you can't get .sfs files to integrate with the desktop if you install it on an HD? Which means installing from tarballs, which always gives me a big freaking headache.

> **phillw said:**
> Oddly enough lubuntu and kubuntu people work together ;) As do we with Xubuntu and Ubuntu.

Whilst some may like to start a war with Ubuntu Vs Kubuntu Vs Xubuntu Vs Lubuntu Vs Edubuntu Vs MythUbuntu Vs etc.... In practice they are doomed to failure. All the devs and team members are committed to the Ubuntu ethos and happily chat to each other and swap ideas.
I wasn't trying to start a war, just trying to state personal opinion.

---

### Post by kansasnoob on 2011-06-05
I'm finding most of my desired "tweaks" are actually quite easy. It definitely looks like Lubuntu will be my new home.

I'll still definitely keep playing in Ubuntu, if nothing else to monitor for difference in changes to underlying goodies like casper and ubiquity.

This is just much more comfortable. The learning curve from retro-gnome to LXDE is not nearly as steep as that of switching to Unity for me.

LXpanel is not quite as easy to modify as gnome-panel2 was, but it's just a matter of learning a few new tricks :)

---

### Post by ronacc on 2011-06-05
> **kansasnoob said:**
> I'm finding most of my desired "tweaks" are actually quite easy. It definitely looks like Lubuntu will be my new home.

I'll still definitely keep playing in Ubuntu, if nothing else to monitor for difference in changes to underlying goodies like casper and ubiquity.

This is just much more comfortable. The learning curve from retro-gnome to LXDE is not nearly as steep as that of switching to Unity for me.

LXpanel is not quite as easy to modify as gnome-panel2 was, but it's just a matter of learning a few new tricks :)

Thats pretty much the case with any DE you just have to learn new tricks . The question I ask myself is is it worth the bother . The Lubuntu oneric A1 looks interesting so I've prepped a partition for it on my test box , I'll install it later today . right now I have Oneric with gnome-shell on there and Debian squeeze and sid , Sabayon ,Suse and Puppy + several more open partitions available .

---

### Post by kansasnoob on 2011-06-05
> **ronacc said:**
> Thats pretty much the case with any DE you just have to learn new tricks . **The question I ask myself is is it worth the bother . **The Lubuntu oneric A1 looks interesting so I've prepped a partition for it on my test box , I'll install it later today . right now I have Oneric with gnome-shell on there and Debian squeeze and sid , Sabayon ,Suse and Puppy + several more open partitions available .

It's worth it to me :)

In deed, I also have Squeeze, Lucid, Maverick and Natty all running gnome2 very well so I have a long, long time to sort things out, but I love playing with the bleeding edge stuff and learning to tweak it to my liking.

But Unity and gnome3 are just beyond me. I know some love 'em, and others hate 'em, I'm in a different category: just not smart or capable enough to comprehend either. And that's OK :)

ATM Lubuntu is just a great fit for me. Hopefully I'll be able to help that project just like many help Ubuntu, Kubuntu, Xubuntu, etc.

I'll still have to delve into the "low-fat" Kubuntu when it rolls out :)

---

### Post by wnelson on 2011-06-05
Is there a file manager that does not use gvfs? I understand that pcmanfm might be using udisk instead?

Walt

---

### Post by kansasnoob on 2011-06-05
> **wnelson said:**
> Is there a file manager that does not use gvfs? I understand that pcmanfm might be using udisk instead?

Walt

I'm very new to Lubuntu so I can't be sure, but going to Synaptic and checking dependencies both 'gvfs-fuse' and 'gvfs-backends' are listed as "recommends", not depends.

A search for 'gvfs' in Synaptic shows it is installed however. Ultimately I don't know :confused:

I can say that things seem stable, but copying large files/folders is noticeably slower. I'm not sure I really care much about that because I perform most large transfers via terminal now.

---

### Post by phillw on 2011-06-05
gvfs was finally added by default into 11.04 (Prior it was a user driven addition) gvfs looks after (networked drives) and windows drives. It was causing a few support calls, so the team decided to add it by default. 

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ#Windows share does not show up in PCManFM](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ#Windows share does not show up in PCManFM)

Regards,

Phill.

---

### Post by ronacc on 2011-06-06
sorry for going off topic kansas  , I may be asking you for pointers when I get to playing with my lubuntu install .

---

### Post by kansasnoob on 2011-06-06
> **ronacc said:**
> sorry for going off topic kansas  , I may be asking you for pointers when I get to playing with my lubuntu install .

It's all cool with me, I just don't want this thread to die an untimely death :)

And it looks like the mods erased a page :confused:

I'm still in a major learning curve here myself. I was out to the doctors today and while I was gone I did a fresh install of Natty Lubuntu so I could make comparisons between what should be a working OS and a dev OS.

I'm now trying to do some mowing but by the end of this week I should know more, hopefully much more :D

---

### Post by cariboo on 2011-06-06
> And it looks like the mods erased a page 

Not erased, just moved to [here]("http://ubuntuforums.org/showthread.php?t=1776831").

---

### Post by phillw on 2011-06-06
Thanks mods. 

Would you guys prefer a new title / thread starting for Lubuntu Ocelot? It makes sense that we keep it to one thread, especially during the a1 / a2 / a3 series.

Regards,

Phill.

---

### Post by kansasnoob on 2011-06-06
> **phillw said:**
> Thanks mods. 

Would you guys prefer a new title / thread starting for Lubuntu Ocelot? It makes sense that we keep it to one thread, especially during the a1 / a2 / a3 series.

Regards,

Phill.

That would be cool to me. You'll notice in post #1 I had to make a major edit regarding the release announcement because I was not subscribed to the mailing list at that time.

Then I had to make two major edits in post #4 because I learned I didn't know what I was doing :oops:

I'm totally cool with a rewrite of this thread regarding Lubuntu. I was just sharing what I'd found, but I need to do a lot of studying to get up to speed. That's why I did a fresh install of Lubuntu Natty today.

I'll be busy most of this week but I should be totally on-board thereafter. I already have the lxpanel 90% figured out, and pcmanfm is just easy to navigate, not much learning needed.

I just need a bit of time to get up to speed with some other things ............... like the screensaver settings, which files/folders to backup to save settings, etc.

So far things have been well documented either at the Lubuntu wiki or at LXDE, and quite often just a Google search finds what I need to know :D

---

### Post by kansasnoob on 2011-06-06
I'm just dieing to know if Lubuntu will stay with lxdm or go with lightdm :confused:

The reason I'm dieing to know is I'm used to using gdm and xrandr to set a lower screen resolution. I can do it with an xorg.conf but I prefer using the display pre-session.

---

### Post by cariboo on 2011-06-06
My feeling is that this thread should be kept as it is, I just removed the off topic posts.

If you want to start a Lubuntu-Oneiric specific thread, by all means go ahead.

---

### Post by teh603 on 2011-06-06
So is Lubuntu i386 and AMD64, or just i386 at this point? I'm tempted to see just how fast I can goose my computers, but my big desktop PC has to have AMD64 because of all its memory.

---

### Post by ronacc on 2011-06-06
At the link in the first post there is only 1 .iso  . I was wondering about AMD64 myself since I am in the same situation as you on my test box . I installed from the only .iso and it came up I386 so when running that install some of my mem isn't recognised .Maybe someone knows if they are planning an AMD64 version sometime  .

edit : its very light on resources 274 mb mem in use with Opera and pcmanfm and the system profiler open so loosing a bit of mem shouldn't hurt too much . LOL

---

### Post by phillw on 2011-06-07
When alpha 2 comes out, it should have the 64 bit variant as Lubuntu should then be built using the standard iso building system that the rest of the family use.

Regards,

Phill.

---

### Post by kansasnoob on 2011-06-07
I had posted about 64-bit Lubuntu here:

[http://ubuntuforums.org/showpost.php?p=10809882&postcount=3](http://ubuntuforums.org/showpost.php?p=10809882&postcount=3)

Since I have no 64-bit hardware I can't say much more ;)

---

### Post by phillw on 2011-06-07
thanks,

a2 is quite busy for Lubuntu, as we have to decide the final contenders of what applications we will natively install on the general isos. I reminded our TL last night, that was a OMG moment! 

As previously stated, from alpha2, Lubuntu will (we pray) be using the standard ISO building system that ubuntu, kubuntu, xubuntu etc. use. As always, there is a 'but' as Debian are just changing over some stuff themselves. They hope that all will be in place for the a2.

Most of the time the Devs may as well speak and write in a language developed on the Klingon home world of Qo'noS, but I do get the general idea and can always go pin one of our Dev's down to translate some of the more technical details into human. 

Regards,

Phill.

---

### Post by xebian on 2011-06-07
I have been running 64-bit Lubuntu from the repo for the last 2 or 3 cycles now.  I mainly used CLI + lubuntu-core to get a minimal X session as a VBox host and then run my Kubuntu and Ubuntu guest.

BTW lubuntu-core installed in Kubuntu is a very good rescue tool when X fails to start which usually is desktop effects issue.  Boot to lubuntu and then run system-settings from there to turn off desktop effects.

---

### Post by ronacc on 2011-06-07
> **kansasnoob said:**
> I had posted about 64-bit Lubuntu here:

[http://ubuntuforums.org/showpost.php?p=10809882&postcount=3](http://ubuntuforums.org/showpost.php?p=10809882&postcount=3)

Since I have no 64-bit hardware I can't say much more ;)

Thanks for the link kansas . I've got the torrent comming down now , only getting about 50kb/s from it so it will take awhile .When it completes I'll leave the box running and seed .

---

### Post by kansasnoob on 2011-06-07
> **phillw said:**
> thanks,

a2 is quite busy for Lubuntu, as we have to decide the final contenders of what applications we will natively install on the general isos. I reminded our TL last night, that was a OMG moment! 

As previously stated, from alpha2, Lubuntu will (we pray) be using the standard ISO building system that ubuntu, kubuntu, xubuntu etc. use. As always, there is a 'but' as Debian are just changing over some stuff themselves. They hope that all will be in place for the a2.

Most of the time the Devs may as well speak and write in a language developed on the Klingon home world of Qo'noS, but I do get the general idea and can always go pin one of our Dev's down to translate some of the more technical details into human. 

Regards,

Phill.

Indeed, you probably saw my latest response on the mailing list:

[https://lists.launchpad.net/lubuntu-desktop/msg04144.html](https://lists.launchpad.net/lubuntu-desktop/msg04144.html)

Those thousand devs, minus 998, are going to have their hands full :D

---

### Post by phillw on 2011-06-07
> **ronacc said:**
> Thanks for the link kansas . I've got the torrent comming down now , only getting about 50kb/s from it so it will take awhile .When it completes I'll leave the box running and seed .

As a rule, I always host the Lubuntu isos on my server. On this occasion, with what out Head of Dev said about a1 I did not. 

From a2 onwards, there will be a fall back for if there is no torrent feeders via a direct download and the builds will have 32 & 64 by default.

Regards,

Phill.

---

### Post by ronacc on 2011-06-07
there was a link for direct d/l but I didn't try it , I like to use torrents to help take load off the servers and I try to seed atleast for awhile for the same reason . my test box often sits idle so it might as well do some good .

---

### Post by Catharsis on 2011-06-08
> **kansasnoob said:**
> I'm just dieing to know if Lubuntu will stay with lxdm or go with lightdm :confused:

I remember reading in a couple places that Lubuntu is supportive of switching to LightDM, so I wouldn't be surprised if it switches once the entire Ubuntu family switches.

As an aside, a Call for Testing for LightDM was posted to the ubuntu-desktop list a couple days ago.

---

### Post by xebian on 2011-06-08
> **Catharsis said:**
> I remember reading in a couple places that Lubuntu is supportive of switching to LightDM, so I wouldn't be surprised if it switches once the entire Ubuntu family switches.

As an aside, a Call for Testing for LightDM was posted to the ubuntu-desktop list a couple days ago.

This is just another logon screen-manager and it doesn't really matter which one you use to bring up your fav desktop session.
If I may, there should be just one Ubuntu(Universal?) DM across all the *buntu flavor with distinctive theme(s).

---

### Post by SevenMachines on 2011-06-08
> **xebian said:**
> If I may, there should be just one Ubuntu(Universal?) DM across all the *buntu flavor with distinctive theme(s).

I think this is very much part of what lightdm is aiming to be, one standard display manager for all (not just ubuntu obviously). With plenty of configurabilty to allow for all the different uses

---

### Post by teh603 on 2011-06-09
Just tried the 64-bit iso on my USB stick, and dayum. That thing runs like a scared goat. Once I get some more blank DVDs, I'm going to have to try it on my old Winbook and report back.

Edit: When can we expect to have the nVidia binary driver? Much as Nouveau and its 3D libraries are popular, I kinda need something that actually works.

---

### Post by kansasnoob on 2011-06-09
Regarding DM's, as far as I can see most display managers have a more eloquent way of handing boot off to X. Consider these examples:

```
/.
/etc
/etc/X11
/etc/X11/Xsession.d
/etc/X11/Xsession.d/60xdg_path-on-session
/etc/dbus-1
/etc/dbus-1/system.d
/etc/dbus-1/system.d/gdm.conf
/etc/gdm
/etc/gdm/Init
/etc/gdm/Init/Default
/etc/gdm/PostLogin
/etc/gdm/PostLogin/Default.sample
/etc/gdm/PostSession
/etc/gdm/PostSession/Default
/etc/gdm/PreSession
/etc/gdm/PreSession/Default
/etc/gdm/Xsession
/etc/gdm/gdm.schemas
/etc/init
/etc/init.d
/etc/init.d/gdm
/etc/init/gdm.conf
/etc/pam.d
/etc/pam.d/gdm
/etc/pam.d/gdm-autologin
/usr
/usr/bin
/usr/bin/gdm-screenshot
/usr/bin/gdmflexiserver
/usr/bin/gdmsetup
/usr/lib
/usr/lib/gdm
/usr/lib/gdm/gdm-crash-logger
/usr/lib/gdm/gdm-factory-slave
/usr/lib/gdm/gdm-host-chooser
/usr/lib/gdm/gdm-product-slave
/usr/lib/gdm/gdm-session-worker
/usr/lib/gdm/gdm-set-default-session
/usr/lib/gdm/gdm-simple-chooser
/usr/lib/gdm/gdm-simple-greeter
/usr/lib/gdm/gdm-simple-slave
/usr/lib/gdm/gdm-xdmcp-chooser-slave
/usr/sbin
/usr/sbin/gdm
/usr/sbin/gdm-binary
/usr/share
/usr/share/applications
/usr/share/applications/gdmsetup.desktop
/usr/share/doc
/usr/share/doc/gdm
/usr/share/doc/gdm/AUTHORS
/usr/share/doc/gdm/NEWS.gz
/usr/share/doc/gdm/README
/usr/share/doc/gdm/changelog.Debian.gz
/usr/share/doc/gdm/copyright
/usr/share/doc/gdm/examples
/usr/share/doc/gdm/examples/custom.conf
/usr/share/gconf
/usr/share/gconf/schemas
/usr/share/gconf/schemas/gdm-simple-greeter.schemas
/usr/share/gdm
/usr/share/gdm/autostart
/usr/share/gdm/autostart/LoginWindow
/usr/share/gdm/autostart/LoginWindow/at-spi-registryd-wrapper.desktop
/usr/share/gdm/autostart/LoginWindow/gdm-simple-greeter.desktop
/usr/share/gdm/autostart/LoginWindow/gnome-mag.desktop
/usr/share/gdm/autostart/LoginWindow/gnome-power-manager.desktop
/usr/share/gdm/autostart/LoginWindow/gnome-settings-daemon.desktop
/usr/share/gdm/autostart/LoginWindow/metacity.desktop
/usr/share/gdm/autostart/LoginWindow/onboard.desktop
/usr/share/gdm/autostart/LoginWindow/orca-screen-reader.desktop
/usr/share/gdm/gdb-cmd
/usr/share/gdm/gdm-greeter-login-window.ui
/usr/share/gdm/gdm.schemas
/usr/share/gdm/gdmsetup.ui
/usr/share/gdm/language-options
/usr/share/gdm/locale.alias
/usr/share/gnome
/usr/share/gnome/help
/usr/share/gnome/help/gdm
/usr/share/gnome/help/gdm/C
/usr/share/gnome/help/gdm/C/gdm.xml
/usr/share/gnome/help/gdm/C/legal.xml
/usr/share/gnome/help/gdm/de
/usr/share/gnome/help/gdm/de/gdm.xml
/usr/share/gnome/help/gdm/el
/usr/share/gnome/help/gdm/el/gdm.xml
/usr/share/gnome/help/gdm/en_GB
/usr/share/gnome/help/gdm/en_GB/gdm.xml
/usr/share/gnome/help/gdm/es
/usr/share/gnome/help/gdm/es/gdm.xml
/usr/share/gnome/help/gdm/fr
/usr/share/gnome/help/gdm/fr/gdm.xml
/usr/share/gnome/help/gdm/id
/usr/share/gnome/help/gdm/id/gdm.xml
/usr/share/gnome/help/gdm/it
/usr/share/gnome/help/gdm/it/gdm.xml
/usr/share/gnome/help/gdm/ko
/usr/share/gnome/help/gdm/ko/gdm.xml
/usr/share/gnome/help/gdm/oc
/usr/share/gnome/help/gdm/oc/gdm.xml
/usr/share/gnome/help/gdm/ru
/usr/share/gnome/help/gdm/ru/gdm.xml
/usr/share/gnome/help/gdm/sl
/usr/share/gnome/help/gdm/sl/gdm.xml
/usr/share/gnome/help/gdm/sv
/usr/share/gnome/help/gdm/sv/gdm.xml
/usr/share/gnome/help/gdm/uk
/usr/share/gnome/help/gdm/uk/gdm.xml
/usr/share/gnome/help/gdm/zh_CN
/usr/share/gnome/help/gdm/zh_CN/gdm.xml
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/gdm-xnest.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/gdm-setup.png
/usr/share/icons/hicolor/32x32/apps/gdm-xnest.png
/usr/share/omf
/usr/share/omf/gdm
/usr/share/omf/gdm/gdm-C.omf
/usr/share/omf/gdm/gdm-de.omf
/usr/share/omf/gdm/gdm-el.omf
/usr/share/omf/gdm/gdm-en_GB.omf
/usr/share/omf/gdm/gdm-es.omf
/usr/share/omf/gdm/gdm-fr.omf
/usr/share/omf/gdm/gdm-id.omf
/usr/share/omf/gdm/gdm-it.omf
/usr/share/omf/gdm/gdm-ko.omf
/usr/share/omf/gdm/gdm-oc.omf
/usr/share/omf/gdm/gdm-ru.omf
/usr/share/omf/gdm/gdm-sl.omf
/usr/share/omf/gdm/gdm-sv.omf
/usr/share/omf/gdm/gdm-uk.omf
/usr/share/omf/gdm/gdm-zh_CN.omf
/usr/share/pixmaps
/usr/share/pixmaps/faces
/usr/share/pixmaps/faces/astronaut.jpg
/usr/share/pixmaps/faces/baseball.png
/usr/share/pixmaps/faces/butterfly.png
/usr/share/pixmaps/faces/cat-eye.jpg
/usr/share/pixmaps/faces/chess.jpg
/usr/share/pixmaps/faces/coffee.jpg
/usr/share/pixmaps/faces/dice.jpg
/usr/share/pixmaps/faces/energy-arc.jpg
/usr/share/pixmaps/faces/fish.jpg
/usr/share/pixmaps/faces/flake.jpg
/usr/share/pixmaps/faces/flower.jpg
/usr/share/pixmaps/faces/grapes.jpg
/usr/share/pixmaps/faces/guitar.jpg
/usr/share/pixmaps/faces/launch.jpg
/usr/share/pixmaps/faces/leaf.jpg
/usr/share/pixmaps/faces/lightning.jpg
/usr/share/pixmaps/faces/penguin.jpg
/usr/share/pixmaps/faces/puppy.jpg
/usr/share/pixmaps/faces/sky.jpg
/usr/share/pixmaps/faces/soccerball.png
/usr/share/pixmaps/faces/sunflower.jpg
/usr/share/pixmaps/faces/sunset.jpg
/usr/share/pixmaps/faces/tennis-ball.png
/usr/share/pixmaps/faces/yellow-rose.jpg
/usr/share/pixmaps/gdm-foot-logo.png
/usr/share/pixmaps/gdm-setup.png
/usr/share/pixmaps/gdm-xnest.png
/usr/share/pixmaps/gdm.png
/usr/share/pixmaps/nobody.png
/usr/share/pixmaps/nohost.png
/usr/share/polkit-1
/usr/share/polkit-1/actions
/usr/share/polkit-1/actions/gdm.policy
/usr/share/xsessions
/usr/share/xsessions/xsession.desktop
/usr/share/xsessions/xterm.desktop
/var
/var/cache
/var/cache/gdm
/var/lib
/var/lib/gdm
/var/lib/gdm/.gconf.defaults
/var/lib/gdm/.gconf.defaults/%gconf-tree.xml
/var/lib/gdm/.gconf.mandatory
/var/lib/gdm/.gconf.mandatory/%gconf-tree.xml
/var/lib/gdm/.gconf.path
/var/lib/gdm/.local
/var/lib/gdm/.local/share
/var/lib/gdm/.local/share/applications
/var/lib/gdm/.local/share/applications/mime-dummy-handler.desktop
/var/lib/gdm/.local/share/applications/mimeapps.list
/var/log
/var/log/gdm

```

```
/.
/etc
/etc/dbus-1
/etc/dbus-1/system.d
/etc/dbus-1/system.d/org.lightdm.LightDisplayManager.conf
/etc/init
/etc/init.d
/etc/init.d/lightdm
/etc/init/lightdm.conf
/etc/lightdm.conf
/etc/pam.d
/etc/pam.d/lightdm
/usr
/usr/bin
/usr/bin/lightdm
/usr/share
/usr/share/doc
/usr/share/doc/lightdm
/usr/share/doc/lightdm/changelog.Debian.gz
/usr/share/doc/lightdm/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/lightdm.1.gz
/var
/var/cache
/var/cache/lightdm
/var/log
/var/log/lightdm
```

I know that's lightdm vs gdm, but lxdm is similar.

Lightdm just goes straight for X instead of looking for preset defaults ..................... I guess because X is always right :rolleyes:

I don't like it because there is no PreSession to X.

OTOH even LXDM can be somewhat buggy.

---

### Post by phillw on 2011-06-09
I'd suggest placing bets,

for those not on the mailing list (and why aren't you?!!)

As we progress to a2, which is really eating up time with the new things, there is a discussion going on between the devs as to 'try' LightDM out, with a fall back to LXDM.

As we are short of devs, I always vote for what the devs think is possible. It does appear that they think that LightDM is possible provided they maintain a 'fall back' position incase it all goes horribly wrong.

I've no idea if they are going to try and get LightDM in at a2 or a3, or gradually introduce it as Lubuntu heads towards its first LTS at 12.04 - As only the couple of devs can decide upon their own workload and how many 'man hours' they can spare it is their choice.

There are pros and cons each way, I'm just glad I'm not head of dev and the one to make the call.

Regards,

Phill.

---

### Post by teh603 on 2011-06-10
> **phillw said:**
> I'd suggest placing bets,

for those not on the mailing list (and why aren't you?!!)

As we progress to a2, which is really eating up time with the new things, there is a discussion going on between the devs as to 'try' LightDM out, with a fall back to LXDM.

As we are short of devs, I always vote for what the devs think is possible. It does appear that they think that LightDM is possible provided they maintain a 'fall back' position incase it all goes horribly wrong.

I've no idea if they are going to try and get LightDM in at a2 or a3, or gradually introduce it as Lubuntu heads towards its first LTS at 12.04 - As only the couple of devs can decide upon their own workload and how many 'man hours' they can spare it is their choice.

There are pros and cons each way, I'm just glad I'm not head of dev and the one to make the call.

Regards,

Phill.Well, first off... the last computer I was able to competently program was an Apple //c. So, are you *sure* you want me on your mailing list, asking all the stupid questions?

---

### Post by ojdon on 2011-06-10
Trying to download the torrent but there isn't a great deal of seeds. Anyone mind seeding to speed things up? Or is there a mirror for Lubuntu 11.10?

---

### Post by kansasnoob on 2011-06-11
> **phillw said:**
> I'd suggest placing bets,

for those not on the mailing list **[COLOR="Red"](and why aren't you?!!)[/COLOR]**

As we progress to a2, which is really eating up time with the new things, there is a discussion going on between the devs as to 'try' LightDM out, with a fall back to LXDM.

As we are short of devs, I always vote for what the devs think is possible. It does appear that they think that LightDM is possible provided they maintain a 'fall back' position incase it all goes horribly wrong.

I've no idea if they are going to try and get LightDM in at a2 or a3, or gradually introduce it as Lubuntu heads towards its first LTS at 12.04 - As only the couple of devs can decide upon their own workload and how many 'man hours' they can spare it is their choice.

There are pros and cons each way, I'm just glad I'm not head of dev and the one to make the call.

Regards,

Phill.

I am, since the time I first posted to the list.

Or at least I think I am.

I did see some discussion going on there regarding lxdm vs. lightdm, but remember I'm just now getting my feet wet in the Lubuntu poll, so I have the whole learning curve thing to deal with :)

I'm also time challenged ATM.

---

### Post by kansasnoob on 2011-06-12
The only thing about Lubuntu that has me puzzled is getting the hardware temp monitor to work in the panel. I've installed lm-sensors and run "sensors-detect" but I still get just an NA.

I'm also not wild about Xscreensaver, but it'll work ;)

---

### Post by ronacc on 2011-06-13
I don't even see a temp applet for the lubuntu panel , I installed psensor , not a very satisfactory display but at least you can see if the sensors are working . What I would like to find is where to set the login window to automatic .

---

### Post by kansasnoob on 2011-06-13
I think I have Xscreensaver about 90% figured out. These two web pages are very helpful:

[http://www.jwz.org/xscreensaver/faq.html](http://www.jwz.org/xscreensaver/faq.html)

[http://www.jwz.org/xscreensaver/man2.html](http://www.jwz.org/xscreensaver/man2.html)

In fact, I'm wondering if I couldn't use it with gnome3? I'll have to try sometime.

No luck on the computer temp applet, but I did find this:

[http://forum.lxde.org/viewtopic.php?f=21&t=1263&hilit=lxde+temperature+monitor&start=10](http://forum.lxde.org/viewtopic.php?f=21&t=1263&hilit=lxde+temperature+monitor&start=10)

I'm really amazed at how easy Lubuntu is to get used to ............ almost boring :lolflag:

Something I would like to learn is how to restore default desktop and/or panel settings. I'm sure it's easy but I'm still a bit confused about that.

---

### Post by Catharsis on 2011-06-13
> **ronacc said:**
> What I would like to find is where to set the login window to automatic .

Edit```
/etc/xdg/lubuntu/lxdm/lxdm.conf
```and add the line```
autologin=user
```where 'user' is your username.

For more info see the lxdm man page.

---

### Post by kansasnoob on 2011-06-13
> **ronacc said:**
> I don't even see a temp applet for the lubuntu panel , I installed psensor , not a very satisfactory display but at least you can see if the sensors are working . What I would like to find is where to set the login window to automatic .

I found a way to set the auto-login earlier today playing in Peppermint Two:

[http://ubuntuforums.org/showpost.php?p=10066458&postcount=6](http://ubuntuforums.org/showpost.php?p=10066458&postcount=6)

But after doing that I found that I had root access to all files & folders. For instance I use a custom xorg.conf, and I could just open a terminal and type "gedit /etc/X11/xorg.conf", then edit and save with no need for sudo :(

But I need to do some repeat testing. That may be just how pcmanfm works :confused:

I'm in Ubuntu Natty classic right now getting some work done but I've fiddled around with all of my LXDE installs so much I should probably start from scratch and then repeat some of my mods more cautiously :)

The next time I'm in Lubuntu I'll snap some screenshots regarding that temp monitor.

I can't say I'm all that impressed with either lightdm or lxdm ATM. I may decide to try gdm version 3 from the Debian package list sometime in the near future.

Sometimes a little "bloat" can be a good thing if it actually adds functionality, like gedit.

Totally OT, but I have a router, some cables, and a KVM switch coming from NewEgg sometime this week so I'll soon have three computers to play with at once. One is an old PII w/333mhz CPU & 256mb RAM so I can really check out how much bloat effects a slow machine :)

---

### Post by kansasnoob on 2011-06-13
> **Catharsis said:**
> Edit```
/etc/xdg/lubuntu/lxdm/lxdm.conf
```and add the line```
autologin=user
```where 'user' is your username.

For more info see the lxdm man page.

Thanks for the info. Us LXDE converts can use all the help we can get :)

One of the greatest obstacles has been web searches themselves. Quite often searching for info about "lubuntu" renders mostly results for "ubuntu", so I've found that searching for "lxde" or individual components like "lxpanel" or "lxdm" renders much better results.

---

### Post by ronacc on 2011-06-13
unfortunately that didn't do it . also tried /etc/lxdm/lxdm.conf no luck , that seems to be controled by upstart , investigating , thanks for the hint , it at least got me headed in a direction .

---

### Post by Catharsis on 2011-06-13
> **kansasnoob said:**
> Quite often searching for info about "lubuntu" renders mostly results for "ubuntu", so I've found that searching for "lxde" or individual components like "lxpanel" or "lxdm" renders much better results.

If you put "Lubuntu" in quotes it won't add suggestions. That's what I've been doing.

---

### Post by Catharsis on 2011-06-13
> **ronacc said:**
> unfortunately that didn't do it . also tried /etc/lxdm/lxdm.conf no luck , that seems to be controled by upstart , investigating , thanks for the hint , it at least got me headed in a direction .

From the man page, it sounds like you might have to run```
update-alternative --config lxdm.conf
```to get the symlink (default.conf) updated. You can check default.conf and see if it includes the autologin line. The system checks /etc/lxdm/default.conf for its configuration, which itself is just a symlink/copy of /etc/xdg/lubuntu/lxdm/lxdm.conf

---

### Post by kansasnoob on 2011-06-13
Regarding the temp monitor thing I dropped into my Lubuntu Natty install and took a couple of screenshots. I used a couple of different panel colors/themes and window sizes:

[ATTACH]195000[/ATTACH]

[ATTACH]195001[/ATTACH]

The little NA in the panel is what I get, and the app settings dialog looks like this:

[ATTACH]195002[/ATTACH]

My Oneiric Lubuntu install is almost identical, but I'm going to boot it now to investigate the display manager issue a bit more closely.

---

### Post by kansasnoob on 2011-06-13
> **Catharsis said:**
> If you put "Lubuntu" in quotes it won't add suggestions. That's what I've been doing.

You're right. I'm sort of in "D'oh" mode (picture Homer Simpson here) ATM after having to repeat "web search 101" all over again :lolflag:

Sometimes the simplest things really do have simple answers ;)

---

### Post by kansasnoob on 2011-06-13
Here's what "/etc/lxdm/default.conf" looks like before editing:

```
lance@lance-desktop:~$ cat /etc/lxdm/default.conf
[base]
# autologin=dgod
session=/usr/bin/startlubuntu
# numlock=0
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
# arg=/usr/bin/X -nr vt1

[display]
gtk_theme=Clearlooks
bottom_pane=1
lang=1
theme=Lubuntu

[input]

[userlist]
disable=0
white=
black=

```

Based on what I'd seen earlier in Peppermint Two I tried to edit my xorg.conf w/o root privileges and it failed as it should.

I checked in Synaptic and lxdm is still being used, no lightdm installed, so I'm going to try an edit and I'll be back with the results directly :)

---

### Post by ronacc on 2011-06-13
sudo update-alternative --config lxdm.conf returned "update-alternative  command not found " but hand editing default.conf did the trick .

@kansasnoob  I don't have the temperatue monitor applet showing as available in the oneric panel in lubuntu .

---

### Post by kansasnoob on 2011-06-13
Okay I modified this line in "/etc/lxdm/default.conf":

```
# autologin=dgod
```

To this:

```
autologin=lance
```

That is, I removed the comment and replaced "dgod" with my username, and autologin works as expected :)

I also checked to see if I could modify root files w/o being root and I still couldn't, so that thing in Peppermint Two is either due to a bug or some other mod I made :D

Looks good to me but I'd appreciate any feedback.

---

### Post by kansasnoob on 2011-06-13
> **ronacc said:**
> sudo update-alternative --config lxdm.conf returned "update-alternative  command not found " but hand editing default.conf did the trick .

@kansasnoob  **I don't have the temperatue monitor applet showing as available in the oneric panel in lubuntu .**

It's odd that I do I guess:

[ATTACH]195003[/ATTACH]

Notice the NA between my screensaver applet and the volume applet?

---

### Post by ronacc on 2011-06-13
yes that must be something else I also hand edited default.conf , I checked for root access without sudo and do not have it .

---

### Post by ronacc on 2011-06-13
gah , my stupidity I wasn't hitting the "add" button , it's there now [-o<

---

### Post by kansasnoob on 2011-06-13
Beyond getting that temp applet to work properly the only thing I notice is the double icon in the panel showing that my network is broken, although it's not, but compared to parent Ubuntu it's fairly bug free. That is, most things just work :D

What amazed me was how easy it actually is to modify the lxpanel. At first I missed the "drag-n-drop" capability of gnome2, but after a bit of playing I find lxpanel to be quite simple. You can use however many "App Launch Bars" you like (wherever you like) to place any menu items in the panel.

And flash based video like Hulu is much better on Lubuntu than what I was experiencing on gnome with this cheap Intel board :guitar:

IMHO, compared to all options currently available with gnome3, this is a winner :D

---

### Post by ronacc on 2011-06-13
yes lubuntu kind of grows on you , I've got the 2 x'd out net icons too but I ignore them since it's obiously working . If I can make any progress with the temp applet I'll  post it but from that link you posted it looks like we'll have to wait awhile .

---

### Post by kansasnoob on 2011-06-13
> **ronacc said:**
> yes that must be something else I also hand edited default.conf , I checked for root access without sudo and do not have it .

I'll check that Peppermint Two install again to make sure I wasn't just asleep at the wheel - certainly possible - and I'll test a new install if needed.

What's cool about Peppermint is the reliance on truly free cloud apps. I don't particularly care for it, but for those with very small hard drives it could be great.

They also develope Mint's LXDE version but I just can't stand Mint's tools.

---

### Post by teh603 on 2011-06-13
> **kansasnoob said:**
> I'll check that Peppermint Two install again to make sure I wasn't just asleep at the wheel - certainly possible - and I'll test a new install if needed.

What's cool about Peppermint is the reliance on truly free cloud apps. I don't particularly care for it, but for those with very small hard drives it could be great.

They also develope Mint's LXDE version but I just can't stand Mint's tools.Instead of using cloud apps, it might be safer for people's freedom of choice to use small local apps. M$ Word 5 was less than a megabyte in size, and did almost everything that the latest version does- I used it on a Mac SE (as in 68k CPU at 8 Mhz) and it ran blazing fast. There's no reason why a modern word processor needs to be as big as they're getting.

---

### Post by ronacc on 2011-06-13
you are right there , I'll bet upwards of 90% of users never use most of the "features" in the heavy weight packages , no matter which one . They should definitely be available for those who do but not default .Personally I find just about any text editor adequate for my correspondence needs ( I learned to write notes and letters on a manual Underwood typewriter a couple of decades before word processors ).

---

### Post by kansasnoob on 2011-06-13
> **teh603 said:**
> Instead of using cloud apps, it might be safer for people's freedom of choice to use small local apps. M$ Word 5 was less than a megabyte in size, and did almost everything that the latest version does- I used it on a Mac SE (as in 68k CPU at 8 Mhz) and it ran blazing fast. There's no reason why a modern word processor needs to be as big as they're getting.

I haven't really needed to worry about bloat much in quite a few years, but even before moving to Ubuntu I'd been using Abiword in Windows. I still use Abiword, it does everything I need a word processor to do.

I have considered using Google docs but I've just never gotten around to trying it out.

---

### Post by phillw on 2011-06-13
I do so love this time in a release's formation... People who are best of friends all falling out saying 'my app is better than your app'... I'm always glad when the decision has been made!

[Original List of applications](https://wiki.ubuntu.com/Lubuntu/Applications) is where we started, and the mailing list has been lively! As the dates are very close to closure [Lubuntu 11.10 Schedule](https://wiki.ubuntu.com/Lubuntu/Developers#Schedule) I look forward to what is eventually decided. As we all know, we cannot please all the people all the time. For every little extra bit asked for, something must go. The line in the sand that may not be crossed is > A Pentium II or Celeron system with 128 MiB of RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. Thankfully we do have 'grown up' discussions with a wonderful absence of 'spitting the dummy out'. 

As already mentioned, the alpha 1 was an alpha 1 in every meaning of the word. As odd as it may seem, the hard work for everyone from devs via testers and bug-triagers / fixers to documentation etc. really starts at alpha 2.

Sorry if this seems more like a blog, but I did promise to keep you all 'in the loop'.

Many thanks for your continued testing and reporting of issues.

Regards,

Phill.
P.S. I'm finally getting my head round these Virtual Machines;)
P.P.S. The Direct Link for Lubuntu 11.10 alpha 1 has expired, following on from comments about the lack of seeders I am getting it transferred to my server area - I will let you know when it is done.

****EDIT**** The link on [Lubuntu Testing](https://wiki.ubuntu.com/Lubuntu/Testing) has been updated to reflect the fact the iso now lives on my server.

---

### Post by ronacc on 2011-06-13
I seeded lubuntu A1 for a couple of days last week and had zero takers , I can start again if there is a need .

---

### Post by teh603 on 2011-06-13
> **ronacc said:**
> you are right there , I'll bet upwards of 90% of users never use most of the "features" in the heavy weight packages , no matter which one . They should definitely be available for those who do but not default .Personally I find just about any text editor adequate for my correspondence needs ( I learned to write notes and letters on a manual Underwood typewriter a couple of decades before word processors ).
I've got an old typewriter at home that I used to use. Not an Underwood, but its still really ancient.

> **phillw said:**
> Sorry if this seems more like a blog, but I did promise to keep you all 'in the loop'.
Eh, its ok. It keeps those of us not on the mailing list informed.

Edit: Is there any way to include Gedit or Kate, or a word processor that supports replacing tabs with spaces while typing? When I'm writing, I can't be hitting the spacebar eight times, and when I'm uploading the tab characters get stripped out and ignored because the internet can't be bothered to follow accepted English formatting. Abiword and Leafpad don't support it.

If its in the repositories that's fine too, as long as I can find it.

---

### Post by ronacc on 2011-06-13
you can install gedit in lubuntu , with a few extra libs it drags in it only adds about 10 mb .

---

### Post by phillw on 2011-06-13
> 
Edit: Is there any way to include Gedit or Kate, or a word processor that supports replacing tabs with spaces while typing?.....

One of the things that has come out on the mailing list is that everyone has their own 'favourite' apps (you should have heard the debate on dropping x-chat because pidgin as a generic can do IRC and other variants of IM).

The point is to keep within our stated rule of specification for a basic install. After that, what you do with it is entirely upto you! (I had a full LAMP server on mine), along with both Chromium and Ffox, Abiword & Gnumeric along  with OpenOffice. 

The debates about what we can actually fit in to that spec are very tight, there does, as always, seem to be a little bit of 'drag' towards "well, I've got a multi core with 4GB of RAM etc..." - Our answer to that is "go and install Ubuntu". 

An example... And, it is **really** only an example, as the decision has not yet been made.

The removal of x-chat as a default and use pidgin. The space saved would allow extra language packs to be included on the iso.

@ Kansass - you know what you need, go google it & install it. EVERYTHING on the entire ubuntu repsository and all those sourceforge debs will run on Lubuntu :) If there is anything specific that you cannot find on the ubuntu database, I will go looking further afield for you.

Regards,

Phill.

---

### Post by teh603 on 2011-06-13
> **phillw said:**
> The debates about what we can actually fit in to that spec are very tight, there does, as always, seem to be a little bit of 'drag' towards "well, I've got a multi core with 4GB of RAM etc..." - Our answer to that is "go and install Ubuntu". 
I'm aware of that, and I don't plan on running it on the big desktop. I want to be able to use my old Winbook (with about half a gig of ram) as an emergency computer, and replacing tabs with spaces while typing is my only mission-critical feature. Its also one that nobody seems to think about using very often, for some reason.

Now, that old Winbook can run i386 Kubuntu 10.10 somewhat slowly, but I'd rather have it running as fast as it was when it was new.

> **ronacc said:**
> you can install gedit in lubuntu , with a few extra libs it drags in it only adds about 10 mb .10 megs isn't small, but its not as big as a lot of the bloatware I've seen. Once I get a decent burn I'll have to try it out. I ran out of blank CDs trying to fix my mini-mac and my style is a bit cramped until I can get some more.

---

### Post by phillw on 2011-06-14
The link on [Lubuntu Testing](https://wiki.ubuntu.com/Lubuntu/Testing) has been updated to reflect the fact the iso now lives on my server.

Regards,

Phill.

---

### Post by ronacc on 2011-06-14
question I opened pcmanfm with sudo and then tried to open my  /home/(user) dir and it gave me a permission denied , is this normal for pcmanfm ? and can it be invoked with full root privileges ?

---

### Post by phillw on 2011-06-14
> **ronacc said:**
> question I opened pcmanfm with sudo and then tried to open my  /home/(user) dir and it gave me a permission denied , is this normal for pcmanfm ? and can it be invoked with full root privileges ?

Ahhggg!!! **Always** use gksudo for graphical programmes, else it will - as it has done, mess up all your permissions!

Try issuing ```
cd /home/(user)
sudo chown (user) -R *

```

Don't include the ()'s :P

That *should* reset your permissions.

Regards,

Phill.

---

### Post by ronacc on 2011-06-14
I think you misunderstood me . I didn't mean I couldn't open my /home as user I could . I meant that pcmanfm when invoked with sudo would not open my user /home dir 
and returned a permission denied . It would open roots /home dir and all system dirs ok . And yes its a bad habit I have sometimes using sudo when I should use gksu .
note it also returns permission denied when I invoke it with gksu or if I open it from the Icon as user and then select tools > open current folder as root .
I'll take a screenshot as soon as I find out how to in lubuntu .

---

### Post by phillw on 2011-06-14
> **ronacc said:**
> 
I'll take a screenshot as soon as I find out how to in lubuntu .

Hi, Alt + PrtSc will take a snapshot of your desktop, it will appear in your ~home directory as a scrot.png file.

You can either ask on the Mailing list, or raise a bug for it.

Regards,

Phill.

---

### Post by ronacc on 2011-06-14
heres the SS . I'll investigate a little more then probably file a bug , if I do I'll post the # here .

---

### Post by phillw on 2011-06-16
Please be aware of a little gremlin in the works. There is a quick and dirty hack if you're so affected. If you are please add yourself to the 'affects me' in order to keep appraised of progress.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/797094](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/797094)

Regards,

Phill.

---

### Post by ronacc on 2011-06-16
I'm not seeing quite the same thing as in the bug report but something is definitely screwy . on my sys the total cpu usage in htop does not agree with the sum of the individual usages , about 2x as high , also htop reported usage is vastly higher than what is reported by screenlets>system monitor which seems too low . htop shows totals of about 60% per core while screenlets shows about 3% per core .

---

### Post by seeker5528 on 2011-06-16
> **ronacc said:**
> question I opened pcmanfm with sudo and then tried to open my  /home/(user) dir and it gave me a permission denied , is this normal for pcmanfm ? and can it be invoked with full root privileges ?

That's a risk with any software that writes configuration or temporary data to $HOME.

If you use the '-H' argument that will set $HOME within the sudo session so those things will write to root's home during the session instead of your home.

```
sudo -H pcmanfm
```

If you use gksudo or kdesudo they handle that and have the additional benefit of doing some X permissions voodoo for the benefit of people who use a display manager that start X session with more restrictive options.

EDIT" Oops, Guess I should have read the entire thread first.....

> **ronacc said:**
> I meant that pcmanfm when invoked with sudo would not open my user /home dir 
and returned a permission denied .

I get a 'Permission Denied' dialog box popping up, but I don't see what that is about, I can still browse my home directory.

After getting the dialog box I do see this in the terminal window I started pcmanfm from....

```
** (pcmanfm:5816): DEBUG: FmJob error: Permission denied
```

If I browse to the home directory of my other user account that I'm not logged in to I don't get that message.

I'm using GDM for my display manger, may or may not make a difference.

If I open pcmanfm normally then go to tools and choose 'Open Current Folder as Root', I get the same thing too.

Later, Seeker

---

### Post by ronacc on 2011-06-16
yes I found that if you just dismiss the "permission denied" you can browse and manipulate the user /home/dir as you would expect . I also have no idea what the "permission denied" is about .

---

### Post by phillw on 2011-06-16
> **ronacc said:**
> yes I found that if you just dismiss the "permission denied" you can browse and manipulate the user /home/dir as you would expect . I also have no idea what the "permission denied" is about .

hiyas,

In the absence of a bug report, could you assemble what you have found and done and pop it on to the mailing list. One of the devs may be better able to assign a bug report to it.

[https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)

will give you ability to post to the mailing list, else just send directly to [email]lubuntu-desktop@lists.launchpad.net[/email] and I'll see it in the moderation queue and forward it.

Many thanks for taking the time to help narrow down a little gremlin :)

Regards,

Phill.

---

### Post by ronacc on 2011-06-16
message sent to [email]lubuntu-desktop@lists.launchpad.net[/email] , subject pcmanfm bug .

---

### Post by kansasnoob on 2011-06-19
I'm tossing a note here, largely as a reminder to myself, Jonathan Marsden contacted me via the mailing list about having updated his ppa to include some Oneiric packages:

[https://launchpad.net/~jmarsden/+archive/lubuntu?field.series_filter=oneiric](https://launchpad.net/~jmarsden/+archive/lubuntu?field.series_filter=oneiric)

Also Julien Lavergne has suggested creating a "lubuntu-dev/lubuntu-daily" ppa.

@ ronacc,

Not sure if this is helpful at all, but I always just use the gui in pcmanfm:

[ATTACH]195511[/ATTACH]

In gnome I'd always installed 'nautilus-gksu' and then been able to "open as admin", but I found pcmanfm to be able to handle gui "opening-as-root" w/o the need for adding anything from the repos.

My oldest son helped complete my LAN wiring yesterday so the next couple of days I'm going to be attempting to move my home office into the next room. Wish me luck :)

---

### Post by ronacc on 2011-06-19
I get the permission denied with the gui too . but it is nice not to have to install the open as root . be careful during the move , don't trip over the chaos . good luck !

---

### Post by kansasnoob on 2011-06-20
Wow, they got that done fast:

[https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily)

There appear to be packages there for both Oneiric and Natty.

---

### Post by ronacc on 2011-06-20
thanks for the heads up . my permission denied problem is partially fixed . I can now open as root from the gui without getting the warning . However I now cannot open pcmanfm as root from terminal at all ! I now get an undefined signal error . also I did not show the pcmanfm updates only the libfm ones that could be the problem .

---

### Post by phillw on 2011-06-20
> **kansasnoob said:**
> Wow, they got that done fast:

[https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily)

There appear to be packages there for both Oneiric and Natty.

We may have only a few devs, but once they choose a plan of action it happens real fast :D (I'm sure they do that so that us doc gang cannot keep upto date ;) )

hopefully with the VM installed, they can now direct me to things to test out for them. 1I've still got a few (read as lot) of cobwebs to brush away, but I do hope to me more help than hinderance!

Regards,

Phill.

---

### Post by ronacc on 2011-06-21
now I can't start pcmanfm at all , from the icon or menu it just fails to start from term I get this .
```
ron@ron-desktop2:~$ pcmanfm

(pcmanfm:9937): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.29.8/./gobject/gsignal.c:2278: signal `status' is invalid for instance `0x9764940'
pcmanfm: symbol lookup error: pcmanfm: undefined symbol: fm_path_entry_set_model
ron@ron-desktop2:~$ 

```

---

### Post by ronacc on 2011-06-22
found the problem , as I said above when I added the PPA the libfm packages showed up but not the pcmanfm ones so I had the older pcmanfm file which is appearently incompatible with the new libfm . I d/l'd the new pcmanfm and installed dpkg , did no need force , it seems ok now .

---

### Post by MilkeySUFC on 2011-06-23
Is Lubuntu now on the same release schedule as Ubuntu and other derivatives?

I.E. will the Lubuntu A2 be available June 30th?

Cheers,
Milkey

---

### Post by phillw on 2011-06-23
The Lubuntu devs endeavour to keep the same schedule, but can be a day (or two) late. We are still dependent on the core release of ubuntu to spin our iso's up. This should change, hopefully in time for the alpha 2.

[Oneric Roadmap](https://wiki.ubuntu.com/Lubuntu/Developers#Roadmap)

Regards,

Phill.

---

### Post by MilkeySUFC on 2011-06-23
> **phillw said:**
> The Lubuntu devs endeavour to keep the same schedule, but can be a day (or two) late. We are still dependent on the core release of ubuntu to spin our iso's up. This should change, hopefully in time for the alpha 2.

[Oneric Roadmap](https://wiki.ubuntu.com/Lubuntu/Developers#Roadmap)

Regards,

Phill.

Hi Phill,

That roadmap has A2 scheduled for 7th July. The updated Ubuntu schedule has A2 as 30th June.

Do you know if Lubuntu A2 going to be 7th July or 30th June?

Cheers,
Milkey

---

### Post by Catharsis on 2011-06-23
> **MilkeySUFC said:**
> Hi Phill,

That roadmap has A2 scheduled for 7th July. The updated Ubuntu schedule has A2 as 30th June.

Do you know if Lubuntu A2 going to be 7th July or 30th June?

Cheers,
Milkey

Ubuntu Alpha 2 was rescheduled back to July 7th.

[https://wiki.ubuntu.com/OneiricReleaseSchedule](https://wiki.ubuntu.com/OneiricReleaseSchedule)

---

### Post by phillw on 2011-06-23
Hiyas,

Guyz & Galz, I've not really had chance to nail one of the two iso builders for Lubuntu into a corner (They are experts at ninja hiding). I will ask the two guys if they have had news from Canonical as to if a2 will be built fully using the Canonical build system, and also a proposed date for the release.

Please do appreciate that it is a really small team, and not only are they getting lubuntu 11-10 ready for it's debut as 'fully adopted' but also developing it!

As soon as I have news, I will post here and ensure that the wiki area for Lubuntu 11-10 schedule is kept up to date (Our Head of dev looks after that).

As if that is not enough, they are also liasing with looking at making daily spins of the iso available. (Makes note to brush up on my rusty rsync skills).

Regards,

Phill.

---

### Post by kansasnoob on 2011-06-23
> **phillw said:**
> Hiyas,

Guyz & Galz, I've not really had chance to nail one of the two iso builders for Lubuntu into a corner (They are experts at ninja hiding). I will ask the two guys if they have had news from Canonical as to if a2 will be built fully using the Canonical build system, and also a proposed date for the release.

Please do appreciate that it is a really small team, and not only are they getting lubuntu 11-10 ready for it's debut as 'fully adopted' but also developing it!

As soon as I have news, I will post here and ensure that the wiki area for Lubuntu 11-10 schedule is kept up to date (Our Head of dev looks after that).

As if that is not enough, they are also liasing with looking at making daily spins of the iso available. **[COLOR="Red"](Makes note to brush up on my rusty rsync skills).[/COLOR]**

Regards,

Phill.

Zsync is much easier :D

I'm a bit tied up ATM but hopefully I'll be able to fully engage within the next week.

---

### Post by ronacc on 2011-06-23
when lubuntu A2 shows up I'll use my test box for seeding the torrent for a few days. and yes zsync is easier .

---

### Post by phillw on 2011-06-24
Our head of dev has confirmed that Lubuntu are committed to the release schedule at [ Oneric Roadmap](https://wiki.ubuntu.com/Lubuntu/Developers#Roadmap) 

Regards,

Phill.

---

### Post by MilkeySUFC on 2011-06-24
> **phillw said:**
> Our head of dev has confirmed that Lubuntu are committed to the release schedule at [ Oneric Roadmap](https://wiki.ubuntu.com/Lubuntu/Developers#Roadmap) 

Regards,

Phill.

I meant to thank you for your earlier confirmation about the updated release schedule. Not long after I asked the question, the schedule on the front page sticky was also updated.

Thanks again,
Milkey

---

### Post by kansasnoob on 2011-06-26
Just a quick FYI:

I've had one problem after another here, the most time consuming have been related to storm damage, so it may take longer than I expected to really get up to speed with this (ppa's and all).

Just wanted Phill and all to know that I hadn't given up :)

---

### Post by kansasnoob on 2011-07-02
Just finally getting around to trying this ppa:

[https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily?field.series_filter=oneiric](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily?field.series_filter=oneiric)

And I've not encountered a single problem :D

Although I don't use mplayer so I can't comment on that.

I hope Lubuntu is on the iso-testing list in a few days, but even if it isn't it's well worth the wait.

---

### Post by kansasnoob on 2011-07-09
Haven't found any alpha2 images yet, but I noticed that not even Kubuntu produced an alpha2 image, so maybe we'll have to wait.

---

### Post by ronacc on 2011-07-09
I've been looking for it too . I intend to seed the torrent for awhile when something shows up , let my test box do something usefull for awhile .

---

### Post by phillw on 2011-07-09
In amongst several things I do to annoy the devs, was to remind them that alpha 2 was due. Having unlocked the cage where they are held, they ate the two security guys I had employed. This makes things awkward, devs a few and far between so I cannot shoot them dead. I'm awaiting for a Vet to arrive with those darn tranquiliser darts ;)

**** Ahh, in return for more security guards to eat, they have promised to work on it over the weekend ***


But, seriously, 2 devs who can even get their head round iso building the way Canonical do it along with full time jobs... They are working on it. I've been sort of promised it will arrive over the weekend.

Regards,

Phill.

---

### Post by kansasnoob on 2011-07-09
> **phillw said:**
> In amongst several things I do to annoy the devs, was to remind them that alpha 2 was due. Having unlocked the cage where they are held, they ate the two security guys I had employed. This makes things awkward, devs a few and far between so I cannot shoot them dead. I'm awaiting for a Vet to arrive with those darn tranquiliser darts ;)

**** Ahh, in return for more security guards to eat, they have promised to work on it over the weekend ***


But, seriously, 2 devs who can even get their head round iso building the way Canonical do it along with full time jobs... They are working on it. I've been sort of promised it will arrive over the weekend.

Regards,

Phill.

I figured as much. I hope the security guards weren't close friends ;)

I wasn't really worried at all, although I must admit that I'm impatient about Lubuntu getting in on the official iso-testing .............. impatient but also realistic.

I was just reading some of the comments regarding Ubuntu Developer Week, particularly this list:

> >  1. What is Lubuntu? (two sentence definition)
>  2. Why do we need abother *ubuntu flavour? (reason for our existence)
>  3. Who is it useful to? (intended audience)
>  4. How to get started (where to download, where to get help)
>  5. What do do when you have issues with it (where/how to report bugs)
>  6. Minimal hardware needed:
>     6.1 for GUI install
>     6.2 for manual install on very low RAM machines
>  7. Current known issues (point to FAQ)
>  8. What changes will Lubuntu Oneiric bring?
>  9. How you can help (testing/developing/translating/etc.)

And I'm trying to find an eloquent way of addressing 2 and 3 :)

I want to say Lubuntu is not just for old hardware anymore, because I truly believe that. PCManFM is just simple and intuitive as is the rest of the UI.

My two biggest complaints are the inability to increase the font of the clock and I can't for the life of me get the hardware temp applet to work in the panel.

Beyond those two things I can't think of a thing to complain about. Well, getting added to iso-testing makes three I guess ;)

I've never participated in Ubuntu Developer Week, would it be improper to ask for help from the QA team with getting added to iso-testing :confused:

Both of the computers I have hooked up to my new network ATM have way more than enough resources to run Lubuntu, both can even run Ubuntu (one only in 2D), but they're 1.5 and 1.6 MHZ CPU's w/2GB RAM each, and I notice such an improvement in flash video playback it's almost uncanny. 

But I fear it could be a bad idea to bring up the fact that some Ubuntu users are not in love with Unity and they may find Lubuntu (or one of the other variants) more suitable to their needs and desires. And I wouldn't want to cause the demise of any more security guards :D

Thanks for all you do.

---

### Post by phillw on 2011-07-09
> My two biggest complaints are the inability to increase the font of the clock and I can't for the life of me get the hardware temp applet to work in the panel.




One of the guys did actually get that to work, the DM system does not exactly talk to that area. With the news that the devs are REALLY going for LightDM, even I am leaving them alone!


I have a cut off day of about Wednesday to get any slides done. But I am, really awaiting the 1st build of Lubuntu with the Canonical system. 

Send on more human food :popcorn:


Regards,

Phill

---

### Post by stormelf on 2011-07-17
Any sign of Lubuntu alpha 2?

Am I correct that a major difference between alpha 1 and alpha 2 is that from there on forward Lubuntu will be distributed through the official Canonical infrastructure just like Xubuntu? 

Does that mean that we should expect alpha 2 to be available on this URL whenever it is released?
[http://cdimage.ubuntu.com/lubuntu/releases/11.10/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/)

E.g. just like the Xubuntu versjon
[http://cdimage.ubuntu.com/xubuntu/releases/11.10/](http://cdimage.ubuntu.com/xubuntu/releases/11.10/)

---

### Post by jmthomas on 2011-07-17
I sure hope so.  I have Lubuntu installed on my netbook and it really rocks.

They can keep Unity.  Tried it (Natty) for a few days of regular work and just didn't like it.

---

### Post by phillw on 2011-07-17
There is, as you know a delay in the release of alpha 2. This is to do with the repos. The head of dev is working on it. As soon as we get it released, I will ensure you all know where it is available from. Regardless of where it is officially hosted, there will be a link at [GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu) so I can keep our docmentation area in synch with things :)

Regards,

Phill.

---

### Post by andrewabc on 2011-07-18
I really hope so. I'm going to run liveusb for someones laptop whose HDD is extremely slow.

Trying to download alpha1 (torrent only), but not working.

So for now have to test 11.04 on liveusb to see how good it would work on laptop (dual core amd 64bit, amd graphics, 80gb hdd, 1gb ram). win vista so slow they don't use it much.

---

### Post by phillw on 2011-07-19
> **andrewabc said:**
> 

Trying to download alpha1 (torrent only), but not working.



The download, or the usb stick? 

If the torrent is down, as lubuntu is still small there may not be any seeders for an alpha. Please just use my server area to grab it from as a direct download. It is the 'server' option on [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing)

Regards,

Phill.

---

### Post by andrewabc on 2011-07-19
> **phillw said:**
> The download, or the usb stick? 

If the torrent is down, as lubuntu is still small there may not be any seeders for an alpha. Please just use my server area to grab it from as a direct download. It is the 'server' option on [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing)

Regards,

Phill.

11.10 alpha one torrent
[http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/)
[http://people.ubuntu.com/~gilir/lubuntu-oneiric-alpha1.iso.torrent](http://people.ubuntu.com/~gilir/lubuntu-oneiric-alpha1.iso.torrent)

I think I did download direct download from someone when it was released, but couldn't get liveusb to work on my computers (I think deleted it). So I'll just wait for latest alpha uploaded. 11.04 working fine on liveusb so far.

Only problem with 11.04 liveusb is that it showed 300 updates available, and it looked like 200 of them were language packs. I was installing them all but eventually ran out of room on my 4gb usb stick. So now only updating chromium and flash (since main purpose is web browsing).

---

### Post by phillw on 2011-07-20
> **andrewabc said:**
> 11.10 alpha one torrent
[http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/)

That link only stays live for about a week. Gives me time to get it onto my server (and others who host).

> 
Only problem with 11.04 liveusb is that it showed 300 updates available, and it looked like 200 of them were language packs. I was installing them all but eventually ran out of room on my 4gb usb stick. So now only updating chromium and flash (since main purpose is web browsing).

I'll have a dig into this, I do recall it being mentioned but thought it had been resolved.

Regards,

Phill.

---

### Post by andrewabc on 2011-07-20
Fresh 11.04 lubuntu liveusb
Update manager:
484 updates 277mb
I'd say about 1/2 to 2/3rds of updates are language packs. For firefox, gnome, translations, and translations updates. Lots of languages I don't need (I only need English).

Hopefully doesn't happen in 11.10.

---

### Post by ronacc on 2011-07-20
they really need to do something about the language packs and localization in general , after the initial selection at install none of that crap should be even shown unless you specifically request it to be .

---

### Post by andrewabc on 2011-07-21
> **ronacc said:**
> they really need to do something about the language packs and localization in general , after the initial selection at install none of that crap should be even shown unless you specifically request it to be .

Just to be clear, I've never installed it. I just have it running as liveusb with a persistence file to store my data/config/updates.

It would be nice if it could ignore the translation updates. Maybe it does this because when usb boots it still asks for language? Or does it occur on fully installed lubuntu (to hard drive)?

---

### Post by phillw on 2011-07-21
Hi,

sorry for the delay. The nearest I can find is [https://bugs.launchpad.net/ubuntu/+source/icedtea-web/+bug/766559](https://bugs.launchpad.net/ubuntu/+source/icedtea-web/+bug/766559) which was causing various problems.

It is marked as fixed and released, I have raised it on the mailing list to check as I'm sure there is a fix for it.

Regards,

Phill.

---

### Post by kansasnoob on 2011-07-21
I've not had much time to play lately, but I did manage to get my old Micron PII-335mhz w/256MB RAM to run Lubuntu Oneiric Alpha1 :)

I first tried Natty Lubuntu and no matter what I did it just failed. I'm curious what will happen with the Beta.

For what it's worth I think we're OK if we have to wait until 12.04 to get 100% on-board with the Ubuntu dev cycle :)

---

### Post by phillw on 2011-07-22
> Hi,

Just to confirm that there will be no Alpha 2 of Lubuntu Oneiric. Works are in progress to make it usable. I hope to have an Alpha 3 to test.

For the build with Ubuntu ISO build system, we still blocked by
technical problems on Canonical side. I'll post when I have more news about it.

Regards,
Julien Lavergne

Phill.

---

### Post by andrewabc on 2011-07-22
Phill I see you wrote about language packs.
[https://lists.launchpad.net/lubuntu-desktop/msg04456.html](https://lists.launchpad.net/lubuntu-desktop/msg04456.html)

You should probably link to this thread (more specifically my post talking about lang packs).

I'm guessing the problem is that I'm running liveusb which comes with every language possible, and thus when I check for updates it wants to update every language. Hopefully in future a way to disable it. If I manually uncheck every langpack update will it remember it when I reboot? They suggest on mailing list to uninstall langpaks I don't need. Hopefully it would remember this (I tried deleting "install lubuntu" desktop icon, but I think it came back when rebooted.

---

### Post by kansasnoob on 2011-07-22
Update on my old Micron PII-335mhz CPU w/256MB RAM;

While ***painfully slow*** both Lubuntu 11.04 and 11.10 will run on it :D

Something that amazed me was that any version of Puppy I threw at it had trouble connecting to my wired connection through a Trendnet router :confused:

Lubuntu has no problem connecting, I thought that was cool.

But it's back in the closet for now, I'm finishing up the kitchen redo (bad drywall the first time) so I need the additional counter/table space ;)

I'm not at all concerned about the devs not putting out an Alpha 2. Even Ubuntu breakage is terrible ATM. I wonder how much of it has to do with gtk2 -> gtk3 :confused:

---

### Post by phillw on 2011-07-22
> **kansasnoob said:**
> Even Ubuntu breakage is terrible ATM. I wonder how much of it has to do with gtk2 -> gtk3 

For our graphics people (read person), it has been and remains 'interesting' for them. But Rafael is up to the task and with feedback is doing really well for such a stage in an alpha life (by the 'rules' we are part way between a2 and a3).

I'm adding the requested ppa to the a1 to better keep it up to date in the absence of the a2. For those not on the mailing list and still testing via a1, if you add
```

ppa:lubuntu-dev/staging

```> (please note that this PPA is for
testing only, use it only if you want to report bugs).

Regards,

Phill.

---

### Post by kansasnoob on 2011-07-23
> **phillw said:**
> For our graphics people (read person), it has been and remains 'interesting' for them. But Rafael is up to the task and with feedback is doing really well for such a stage in an alpha life (by the 'rules' we are part way between a2 and a3).

I'm adding the requested ppa to the a1 to better keep it up to date in the absence of the a2. For those not on the mailing list and still testing via a1, if you add
```

ppa:lubuntu-dev/staging

```

Regards,

Phill.

I've been using the daily ppa:

[https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily)

I wonder if I'd dare mix the two :confused:

---

### Post by kansasnoob on 2011-07-23
Second dumb question of the morning :redface:

I've recently been playing with adding "lubuntu-core" to a running Ubuntu as an alternative DE.

In Natty it's really spiffy with the Lubuntu Desktop PPA:

[https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

One thing I always notice though is "galculator" is installed as a dependency. Do you think I should report that as a bug, or maybe just mention it on the mailing list?

This is a typical apt-log from installing "lubuntu-core":

> Install: libobrender21:i386 (3.4.11.2-2, automatic), lxsession:i386 (0.4.5-1ubuntu1, automatic), libobparser21:i386 (3.4.11.2-2, automatic), openbox-themes:i386 (1.0.2, automatic), **galculator:i386 (1.3.4-1ubuntu3**, automatic), obconf:i386 (2.0.3-3ubuntu2, automatic), lubuntu-default-settings:i386 (0.19), lubuntu-icon-theme:i386 (0.15, automatic), lubuntu-artwork:i386 (0.15), plymouth-theme-lubuntu-text:i386 (0.15), pcmanfm:i386 (0.9.8+git-6240436419-0ubuntu1, automatic), lubuntu-core:i386 (0.25), libfm-gtk0:i386 (0.1.15+git-3625952cea-0ubuntu2, automatic), giblib1:i386 (1.2.4-6, automatic), openbox:i386 (3.4.11.2-2), elementary-icon-theme:i386 (2.7.1-0ubuntu3, automatic), lxmenu-data:i386 (0.1.1-1, automatic), libfm0:i386 (0.1.15+git-3625952cea-0ubuntu2, automatic), lxpanel:i386 (0.5.6-1ubuntu5), scrot:i386 (0.8-13, automatic), libimlib2:i386 (1.4.4-1, automatic), libmenu-cache1:i386 (0.3.2-2ubuntu2, automatic), plymouth-theme-lubuntu-logo:i386 (0.15)
End-Date: 2011-07-22  12:48:01

---

### Post by phillw on 2011-07-23
> **kansasnoob said:**
> Second dumb question of the morning :redface:

I've recently been playing with adding "lubuntu-core" to a running Ubuntu as an alternative DE.

In Natty it's really spiffy with the Lubuntu Desktop PPA:

[https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

One thing I always notice though is "galculator" is installed as a dependency. Do you think I should report that as a bug, or maybe just mention it on the mailing list?

This is a typical apt-log from installing "lubuntu-core":


I'd bug report it.

Regards,

Phill.

---

### Post by phillw on 2011-07-23
> **kansasnoob said:**
> I've been using the daily ppa:

[https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily)

I wonder if I'd dare mix the two :confused:

Sorry, I cannot help you there. I have not been using the daily ppa.

Reply to the email re: no alpha2 and ask which is the best set up, I'm sure Julien or Jonathan will be happy to answer.

Regards,

Phill.

---

### Post by phillw on 2011-07-24
> **kansasnoob said:**
> I've been using the daily ppa:

[https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily)

I wonder if I'd dare mix the two :confused:

As you will have read on the ML, probably not a good idea. I include the answer here for anyone else following the thread> lubuntu-dev/lubuntu-daily PPA is still a work in progress. It's probably not a good idea to mixed them.

Regards,

Phill.

---

### Post by kansasnoob on 2011-07-24
> **phillw said:**
> As you will have read on the ML, probably not a good idea. I include the answer here for anyone else following the thread

Regards,

Phill.

Yes, that's cool :)

Considering the size of the Lubuntu dev team I'm always amazed at how quickly they respond. That includes you my good friend. You're a vital link in the project :D

AFAIK you're responsible for a great deal (or perhaps all) of the Lubuntu documentation. I hope to someday be able to become a greater asset to Lubuntu, until then I'll continue to be a thorn in your side :lolflag:

I plan on doing some other test installs ASAP. I'll keep the one with the daily ppa, but install another to test only the staging ppa, and I'll DL an Ubuntu daily to test that "galculator" dependency issue.

Right now I'm fighting a wasp problem that's delaying my re-remodeling/fire restoration project :(

---

### Post by phillw on 2011-07-25
> **kansasnoob said:**
> 

......AFAIK you're responsible for a great deal (or perhaps all) of the Lubuntu documentation.......

The sub teams keep their own areas up to date, and with the IRC support guys now having created their own FAQ area, even as a small team we can react pretty quickly to an issue. Everyone is encouraged to contribute to the wiki areas, even if a write up only helps one other person it is still a person helped.

Good luck with the wasps!

Regards,

Phill.

---

### Post by phillw on 2011-07-26
For those not on the mailing list. Lubuntu 11.10 hit a massive milestone today. A successful build using the Canonical build system. With this milestone, the testing changes a little. 

> 
(23:21:53) gilir: phillw, don't use the lubuntu-daily, it's not ready yet
(23:22:3 gilir: phillw, use lubuntu-dev/staging only if you want to test and report bugs about the artwork from Raphael
If you would like to help out on testing, then the release is at [Lubuntu Current](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)
For now, it's too big for a CD, but will be fixed for the stable release. Please use those images indead of the daily PPA if you want to test the latest version of Lubuntu.

For those willing to test, please do ensure you are aware of [Developers](https://wiki.ubuntu.com/Lubuntu/Developers)
and ensure you are on the mailing list. Lubuntu is light, and very quick on its feet.... We will get some documentation up a.s.a.p. for it but it has already gotten out to such places as Webupd8 

Julien, our head of dev is having a richly deserved beer to celebrate. I ask that we toast also to the work that all those people put in, without such people there would be no F/OSS.


Regards,

Phill.

---

### Post by cariboo on 2011-07-26
This is the official notice:

> Hi Ubuntu developers,

New images have pop up on cdimage.ubuntu.com [1]. Finally, Lubuntu is
out of the Ubuntu factory  [2]

For people who don't know Lubuntu, this is a quick presentation. Lubuntu
is a distribution based on Ubuntu, and the LXDE desktop environnement.
The main goal is to provide a very lightweight distribution, but with
all the advantages of the Ubuntu world (repositories, support ...).
Currently we are using :
- Chromium for the browser
- Openbox for the windows manager
- Pcmanfm for the file manager
- Abiword + Gnumeric for office work
- Pidgin for IM
- Audacious for playing music
- Gnome-mplayer for videos
- Some GNOME components : evince, file-roller, gnome-keyring 
- Most of the LXDE components
You can find the complete list of applications by default on the wiki
[3].

After 2 years of work, and 3 "unofficial" releases (10.04, 10.10 and
11.04), we had recently an official go from the Technical Board and ISO
images are now made like other Ubuntu flavors. I hope the 11.10 will be
the 1st official release of Lubuntu as a member of the Ubuntu family 

We have 2 important particularities. Like Xubuntu, we use another
GTK-based desktop environnement than GNOME, and we try to avoid
unnecessary GNOME depends which could slow the system. We need some
GNOME parts because LXDE doesn't provide all necessary components. It's
the reason why we are very careful about dependencies of those
applications.

We are also very strict with ressources requirement. It's the reason why
we don't include all Ubuntu specific applications. For example, we don't
include Software-Center because it's still a bit heavy for some of our
targets.

I would like to thanks all people who make this happen, especially Mark,
Colin and Emmet, and all people involved in the development of Lubuntu
and LXDE.

If you want to talk to the Lubuntu community, you can use our mailing
list (lubuntu-desktop@lists.launchpad.net) or IRC : #lubuntu on
Freenode. You can also find information on our wiki [3].

Thanks for your attention 

Regards,
Julien Lavergne


[1] [http://cdimage.ubuntu.com/lubuntu/](http://cdimage.ubuntu.com/lubuntu/)
[2] It's still young images, which for now, are oversized, don't load
the desktop session, and have wrong splash images .. they should be
better in the futur 
[3] [https://wiki.ubuntu.com/Lubuntu/Applications](https://wiki.ubuntu.com/Lubuntu/Applications)
[4] [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by phillw on 2011-07-28
Hi,

I asked about when the alternate iso could be expected and after a few checks, it appears it should have been automatically spawned.

Julien has looked into it and has spotted something, so hopefully we will have it arrive on the next daily build.

> > I guess only 32 and 64 bits are available for daily build, and
> alternate
> and armel (?) are produced only for releases (Alpha, Beta etc ..)

Actually, it's maybe a bug in the seed. I'll add a fix, and we will see
tomorrow (I love daily builds :p) if it's working.

Regards,

Phill.

---

### Post by cariboo on 2011-07-28
I installed the daily live on an 8GiB SD card for use in my netbook last night, I've found lots of bugs :). I've only reported the one I felt was a showstopper last night, bcmwl won't install, and I expect to report several more later today.

The sort of strange thing was that I use a Retail Plus+ USB wireless device based on a ZyDAS ZD1218B that is detected automagically, to do the updates and install the driver for the internal wireless device, but I don't want to use it for day-to-day usage.

---

### Post by phillw on 2011-07-28
> **cariboo907 said:**
> ...... I've only reported the one I felt was a showstopper last night......


you are doing better than me, it failed to run on my VM, as the alpha1 does, I'm not too sure what the issue is. VM's can only provide so much help.

but, early days yet, I've had my computer more broken on previous testing than this ;)

Regards,

Phill.

---

### Post by kansasnoob on 2011-07-31
Just testing a new 10.04.3 Lubuntu iso and I needed a place to post a screenshot ;)

[ATTACH]198919[/ATTACH]

---

### Post by VMC on 2011-07-31
> **kansasnoob said:**
> Just testing a new 10.04.3 Lubuntu iso and I needed a place to post a screenshot ;)

[ATTACH]198919[/ATTACH]

That's a screenshot of the install portion. I was hoping to see the the installed desktop. Is it 64bit now?

---

### Post by kansasnoob on 2011-07-31
> **VMC said:**
> That's a screenshot of the install portion. I was hoping to see the the installed desktop. Is it 64bit now?

I received a message today about testing 10.04.3 images - nothing to do with 11.10 :(

You can look at my responses here:

[https://lists.launchpad.net/lubuntu-desktop/](https://lists.launchpad.net/lubuntu-desktop/)

Scroll down to the area shown here (I'm Lance):

[ATTACH]198922[/ATTACH]

My take on that is, based on Jonathan's first post there, we're still learning:

[https://lists.launchpad.net/lubuntu-desktop/msg04522.html](https://lists.launchpad.net/lubuntu-desktop/msg04522.html)

In my last post I reminded him that Oneiric Alpha3 is upon us:

[https://lists.launchpad.net/lubuntu-desktop/msg04533.html](https://lists.launchpad.net/lubuntu-desktop/msg04533.html)

ATM the Lubuntu daily is still at the 25th, and doesn't work well, although it will install:

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

We're still just in early days of becoming "official" so we're all experiencing a learning curve. But I'm positive we'll get there :D

---

### Post by phillw on 2011-07-31
Or lack of.... I've just asked Julien about this.

> (16:38:15) phillw: gilir: the daily builds are not appearing at [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/) Is there a gremlin at work?
(16:43:54) gilir: phillw, No, I don't know why it's not updated since 07/25 :/

I guess we wait :(

Regards,

Phill.

---

### Post by kansasnoob on 2011-08-01
@ Phill,

With Jonathan uploading images (and md5's) to your server is there a way to search it?

I just noticed a message from Jonathan verifying that my md5sum was correct and the file was on your server but I tried and couldn't figure out how to find it :confused:

It's not a big deal and there's no need to go out of your way to reply :D

I see the Ubuntu alpha3 iso-testing images are already being prepared so I may not be available for a couple of days. I expect a couple of rebuilds.

---

### Post by phillw on 2011-08-01
> **kansasnoob said:**
> @ Phill,

With Jonathan uploading images (and md5's) to your server is there a way to search it?

I just noticed a message from Jonathan verifying that my md5sum was correct and the file was on your server but I tried and couldn't figure out how to find it :confused:



As Jonathan is real busy atm (I really did not expect him to even attempt the respin for a 10.04.3 with all the things going on RL and with Lubuntu). I will look at putting a search onto it, but it is a temporary server area. It was supposed to be for a couple of months and is now well over a year. Life gets complicated.....

I'll have a 'play' and see if I can create a quick page that will list all the various iso's and md5's that live on there.

Regards,

Phill.

---

### Post by phillw on 2011-08-01
> (22:33:49) gilir: new ISO available, for adventurous testers :) [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)
(22:34:29) gilir: I already reported several issues, be sure to check the bug tracker before reporting bugs :)

hot off the press :)

regards,

Phill.

---

### Post by kansasnoob on 2011-08-03
We're gaining all the time :D

I've been trying to figure out exactly how to go about transitioning from Ubuntu iso-testing to Lubuntu iso-testing. I know that sounds simple, and I could simply change my subscriptions from no Ubuntu testing to only Lubuntu testing and I may do that at some point.

With the total rebuild of ubiquity (the live installer) beginning with Maverick installation testing certainly became more complex. I used to just begin by creating a casper-rw partition, checking disc integrity, then running a persistent session to check the live CD, and then performing three tests:

Entire disc install
Auto-resize install
Manual partitioning install

But the new ubiquity actually provides many more options:

Entire disc install
Manual partitioning install
BUT the "auto-resize" now breaks down into several categories:

Install alongside may provide an auto-resize or it may just use any existing free space ..........

Or, if only one previous Linux install exists, it may offer to replace it, or if it's an Ubuntu variant it may offer to upgrade it .............

Or, if Windows exists it may offer to resize, replace, or if 4 primary partitions exist it will offer a Wubi install.

And I also do an Ubuntu upgrade test. (ATM there is no Lubuntu upgrade test).

Also I need to follow up on two ubiquity specific bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

And:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/819538](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/819538)

I'm actually partly responsible for the latter issue :oops:

I've been trying to figure out exactly how to crowd all of my testing into an appropriate time frame, and I also have a new hardware wish-list :)

Now that Lubuntu is officially in iso-testing I think when Alpha 3 testing is done I'll change my Ubuntu subscription to only testing the live CD, performing a manual install, and doing the upgrade.

Then I should be able to do a full round of testing with the Lubuntu images, and I have a couple of old 3GB ATA drives I should be able to use for testing that one bug - I hope. (I do wonder what would happen though if I used a 4GB flash drive and formatted it to ext4?)

Then if I buy one more hard drive I should be able to pull most of this off without pulling all my hair out :lolflag:

---

### Post by cariboo on 2011-08-03
@kansasnoob

An install on a flash drive should work well, I have Lubuntu installed on an 8GiB SD card, and although it isn't as fast as a hard drive install, it works well enough for testing.

---

### Post by phillw on 2011-08-03
Hi, the dailies are back... Not the full suite as yet, but the three we had previously.

I'm currently using VM's for installing, as the milestone RC's come up for alpa3, betas, final. I'll use VM, then hard-drive install them. As always, thanks for the continued help with the testing :)

Regards,

Phill.

---

### Post by kansasnoob on 2011-08-03
> **cariboo907 said:**
> @kansasnoob

An install on a flash drive should work well, I have Lubuntu installed on an 8GiB SD card, and although it isn't as fast as a hard drive install, it works well enough for testing.

I think I'll try that, but clear back when flash drives were a new thing everyone said FAT was the only way to go.

Even now I use FAT32 for my flash data drives. But I see I can now get a 4GB flash drive for about $7.00 although I'm likely to spend a bit more and go for Crucial. I've just had excellent luck with Crucial.

---

### Post by phillw on 2011-08-03
> **kansasnoob said:**
> ..... I see I can now get a 4GB flash drive for about $7.00 although I'm likely to spend a bit more and go for Crucial. I've just had excellent luck with Crucial.....
Hiyas,

I always recommended people buy a flash drive that is MicroSoft 'Ready Boost' certified for Live-USB use. These were both faster chips and more redundancy in built as they were certified to be little plug in 'RAM-disks', albeit a hell of a lot slower than RAM. I've been very happy with mine, and others who have bought them have not reported any failures (unlike with various 'cheap and cheerful' ones). Just be expected to pay about 2 - 4 times the price, but they are put through a decent level of secondary QA. [http://en.wikipedia.org/wiki/ReadyBoost](http://en.wikipedia.org/wiki/ReadyBoost) is the general area on them, and they are win7 so must still be available. 

Oh, and there is a request in to 'politely' ask Ubiquity to not demand 4.6GB of disk space as the minimum for Lubuntu, whether we get it approved, who knows... I really do hope they grant it. I think the issue of wanting twice as much RAM as required has also been raised.

Regards,

Phill.

---

### Post by VMC on 2011-08-03
kansas,

I haven't used Lubuntu for quite a while now. Maybe its time to start. It uses LXDE interface correct? 
I've read of recent errors, more so than Ubuntu. To be expected. Once they get completely on board, things should be better.

I will stay with Lucid and KDE Oneiric, Kubuntu, for the time being.


 Here's an interesting article regarding [Gnome3 and Linus comments]("http://www.osnews.com/story/25022/Linus_Torvalds_Not_a_Fan_of_Gnome_3"). Linus himself uses **Xfce**, which I don't particularly like, or rather I don't like Xubuntu version.

---

### Post by kansasnoob on 2011-08-04
I had to do a bit of searching but here's where I began to mess up the minumum disc space requirement:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/745148](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/745148)

More here:

[http://ubuntuforums.org/showthread.php?t=1719301](http://ubuntuforums.org/showthread.php?t=1719301)

But regarding Lubuntu I can see that it does require less space, but also the "manual/something else" option should I believe allow one to bypass that "requirement" just like you can bypass the requirement to be on a wired network.

But I need to get a drive that's small enough to do some actual testing. For Lubuntu I think the actual installation requires only about 2.15 GB for / so I'd think a person could conceivably use even a 3 GB drive, create only a / partition w/no swap, and once the installation is complete create a swap file (or create no swap at all if the RAM is sufficient size).

It appears from the current round of iso-testing that even Ubuntu uses about 3 1/4 GB so even with Ubuntu one should be able to use a 4 GB drive if choosing a manual install with low or no swap.

Testing, testing, testing :D

I think I also notice a regression in ubiquity regarding the Wubi if 4 primaries exist option but I need to do some further testing to be sure.

A lot of what I can do is limited by financial constraints which I'm sure everyone here faces from time to time :(

---

### Post by kansasnoob on 2011-08-04
> **VMC said:**
> kansas,

I haven't used Lubuntu for quite a while now. Maybe its time to start. It uses LXDE interface correct? 
I've read of recent errors, more so than Ubuntu. To be expected. Once they get completely on board, things should be better.

I will stay with Lucid and KDE Oneiric, Kubuntu, for the time being.


 Here's an interesting article regarding [Gnome3 and Linus comments]("http://www.osnews.com/story/25022/Linus_Torvalds_Not_a_Fan_of_Gnome_3"). Linus himself uses **Xfce**, which I don't particularly like, or rather I don't like Xubuntu version.

I love Linus' comments beginning with:

> While you are at it, could you also fork gnome, and support a gnome-2 environment?

I want my sane interfaces back. I have yet to meet anybody who likes the unholy mess that is gnome-3.

[https://plus.google.com/106327083461132854143/posts/SbnL3KaVRtM](https://plus.google.com/106327083461132854143/posts/SbnL3KaVRtM)

I can certainly see why SABDFL decided to go with Unity. I find Unity much preferable to the standard gnome-shell UI.

But this is OT so let's concentrate on Lubuntu, which I still find to have a very "sane" UI :D

It'd be great to post this at the Cafe if no one has already. Thanks for the info.

---

### Post by lucazade on 2011-08-04
I prefer this quote by Linus (2008 )

> An o/s should never have been something that people (in general) really care about: it should be completely invisible and nobody should give a flying[expletive deleted] about it except the technical people

---

### Post by kansasnoob on 2011-08-04
> **lucazade said:**
> I prefer this quote by Linus (2008 )

Seems almost contradictory to what he's now saying, eh?

I'd ask respectfully that we not go any further off topic in this thread though. In retrospect I probably shouldn't have even posted what I said in post #163 :(

I did however want to recognize VMC's comments, just as I'm doing with you know. I truly do respect everyone's opinions and everyone here, including you, has helped me immensely a number of times :D 

These are times of great change and it's hard for all of us, no matter what our preferences happen to be, to avoid expressing our personal likes and dislikes of these changes.

---

### Post by lucazade on 2011-08-04
> **kansasnoob said:**
> Seems almost contradictory to what he's now saying, eh?

I'd ask respectfully that we not go any further off topic in this thread though. In retrospect I probably shouldn't have even posted what I said in post #163 :(

I did however want to recognize VMC's comments, just as I'm doing with you know. I truly do respect everyone's opinions and everyone here, including you, has helped me immensely a number of times :D 

These are times of great change and it's hard for all of us, no matter what our preferences happen to be, to avoid expressing our personal likes and dislikes of these changes.

bravo
+1

---

### Post by kansasnoob on 2011-08-04
> **phillw said:**
> Hiyas,

I always recommended people buy a flash drive that is MicroSoft 'Ready Boost' certified for Live-USB use. These were both faster chips and more redundancy in built as they were certified to be little plug in 'RAM-disks', albeit a hell of a lot slower than RAM. I've been very happy with mine, and others who have bought them have not reported any failures (unlike with various 'cheap and cheerful' ones). Just be expected to pay about 2 - 4 times the price, but they are put through a decent level of secondary QA. [http://en.wikipedia.org/wiki/ReadyBoost](http://en.wikipedia.org/wiki/ReadyBoost) is the general area on them, and they are win7 so must still be available. 

Oh, and there is a request in to 'politely' ask Ubiquity to not demand 4.6GB of disk space as the minimum for Lubuntu, whether we get it approved, who knows... I really do hope they grant it. I think the issue of wanting twice as much RAM as required has also been raised.

Regards,

Phill.

I think within the next week or so I'll try fiddling with one or both of these old 3GB ATA drives.

I think on my old VIA box with 2GB of RAM I should be able to install Lubuntu with no swap and then add either a swap file or create a swap partition on another drive that I reconnect later.

I can't really hook up that old PII 335mhz box with 256MB RAM ATM because I have no space :(

Trying to get my kitchen put back together has stuff strewn all over, it's like living in a shoe box almost :)

---

### Post by kansasnoob on 2011-08-04
Well I figured out my monthly budget and decided I could spend $100 US on puter toys which amounted to a new Hannspree 18.5 inch wide-screen monitor so I can hopefully move my KVM switch to sharing my old VIA box and the old PII on it, and then have my Intel box using the 22" monitor all alone.

That $100 also includes a WD refurb 80GB drive so I can more easily perform some of the ubiquity install options by just plugging or unplugging a drive, and also one of these 4GB flash drives:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820313060](http://www.newegg.com/Product/Product.aspx?Item=N82E16820313060)

I had been going to use that money for either a Roku box or a WD TV box but that only allows "watching" for the most part (although the newest wired Roku has angry birds) and I'd rather put my money and my effort into something that's totally interactive.

In my entire life I've never found anything more interactive than participating in the Ubuntu forums :D

Now I need to clean and paint like crazy so I can get this stuff all hooked up when the UPS truck shows up :guitar:

---

### Post by phillw on 2011-08-04
> **kansasnoob said:**
> ....I had to do a bit of searching but here's where I began to mess up the minumum disc space requirement:

....(
IMHO, the problem is Ubiquity.

I have a very happy install of lubuntu 10.04 on a 2GB stick with about 500MB free for data.

It really puzzles me why the 'powers above' decided that an install needed twice the requirements for both RAM and HD space. 

I'm sorry to say, but this alteration should NEVER have got through SRU, but we were not a part of the 'official' stuff back then. 

I could rant about things, but the most important thing is that Lubuntu stays true to itself?.... The answer is yes :)

Regards,

phillw

---

### Post by phillw on 2011-08-05
Hi, for those not on the mailing list :P

> 
Hi,

Lubuntu Alpha 3 is released, and for the first time, along with other Ubuntu images :
[http://cdimage.ubuntu.com/lubuntu/releases/oneiric/alpha-3/](http://cdimage.ubuntu.com/lubuntu/releases/oneiric/alpha-3/) 

You can have a look at the official announcement of Ubuntu Alpha 3 ;)

This is a quick overview of this milestone :
New features for Oneiric :
- ISOs build with official build system
- Many updates from LXDE (most components had a official releases)
- Build with recommends packages by default
- Use recommends instead of depends for most of components of
lubuntu-desktop
- Register correctly LXDE as a desktop environment by xdg tools
- Switch to xfce4-power-manager for power management
- Add a microblog client : pidgin-microblog

Known issues
- No alternate ISO available, I hope it will be fixed shortly after the alpha 3 release.
- Using LXDM instead of Lightdm until configuration files are handle
correctly
- Include apt-xapian-index, which should be removed later
- Jockey crashes on start : [http://pad.lv/819506](http://pad.lv/819506) 
- Missing icons in the menu : [http://pad.lv/819525](http://pad.lv/819525) 
- No indicators on lxpanel : [http://pad.lv/819528](http://pad.lv/819528) 
- Installer require 4.6 Gb of free space : [http://pad.lv/819538](http://pad.lv/819538) 
- Gwibber install by default : [http://pad.lv/819519](http://pad.lv/819519) 
- GTK3 applications doesn't have a theme : [http://pad.lv/819529](http://pad.lv/819529) 
- Generic icon for network-manager : [http://pad.lv/796147](http://pad.lv/796147) 
- Generic icon for jockey : [http://pad.lv/819542](http://pad.lv/819542) 

Please remember that it's still an Alpha, we have still some times to test and fix the remaining issues.

Regards,
Julien Lavergne

Do feel free to have a try of it!

Regards,

Phill.

---

### Post by ronacc on 2011-08-05
I'm seeding the 64 bit and will add the 32 bit as soon as it finishes d/l'ing .

---

### Post by kansasnoob on 2011-08-05
> **phillw said:**
> IMHO, the problem is Ubiquity.

I have a very happy install of lubuntu 10.04 on a 2GB stick with about 500MB free for data.

It really puzzles me why the 'powers above' decided that an install needed twice the requirements for both RAM and HD space. 

I'm sorry to say, but this alteration should NEVER have got through SRU, but we were not a part of the 'official' stuff back then. 

I could rant about things, but the most important thing is that Lubuntu stays true to itself?.... The answer is yes :)

Regards,

phillw

I think we're on different pages here :confused:

I think you're talking about space for a live USB and I need to test an actual hard drive installation via ubiquity, and recent testing shows / uses about 2.3GB + whatever swap would be created, generally 2X the amount of RAM.

So even that old PII 335mhz cpu w/256 MB RAM would use nearly a full 3GB with almost no room to store data or install additional apps, but it should be possible :)

From everything I've read using ext as a file system  on flash drives wears them out very quickly, so I got serious about digging up old hardware.

I seriously think I should be able to install Lubuntu using the live CD (right now DVD because it's oversize) to a 3.2GB hard drive. (I'd previously said I had 2 old 3GB drives but they're actually 3.2GB).

Right now I'm trying to get part of my kitchen put back together but hopefully when UPS shows up Monday or Tuesday I'll be able to begin some more testing :D

OT but I also need to test an old PCI Diamond Stealth GPU and I want to do it with that new 18.5" Monitor so if I fry it I have exchange capabilities :)

Does that make me bad?

---

### Post by ronacc on 2011-08-05
just for grins I'll see what a minimum install of a3-64bit takes , I need to do a 64 bit install anyway . and BTW you can do an install with no swap  and also use one swap for several installs .

---

### Post by andrewabc on 2011-08-05
Bad news.

Installed alpha 3 on liveusb. It starts fine and loads desktop.

Networking icon at bottom right is missing (gives the "no icon" icon). I select the icon and it says "Networking enabled" and "wireless enabled" (both have charkmarks. connection information is greyed out and edit connections is available). But there is no wireless connection listed. With 11.04 it automatically lists a connection available to connect to (and even does the popup at top right of screen to notify me that it is available). With this alpha there is no wireless to connect to. No idea how to connect to my wireless connection other than maybe going into wireless settings and having to manually enter in the SSID of my wireless router??

I went into "Additional Drivers" to see if maybe it was needing a wireless driver (Didn't before, but I know other laptops sometimes asks for it), but there were no drivers available.

This is on a nettop. Intel atom N270. eeebox b202

So any suggestions? Why wireless work with 11.04 before but now it doesn't?

The nettop doesn't really have access to ethernet cable to see if that even works. I'll probably try normal ubuntu alpha 3 to see if similar problem.

---

### Post by phillw on 2011-08-05
I have a 2GB stick, lubuntu leaves me about 700MB free. I really do scratch my head when people say 'it needs this' etc. 

I have a 'persistant' install on that little critter. and, yes, it is the speed-boost certified stick that I advise people to get.

Regards,

Phill.

---

### Post by kansasnoob on 2011-08-05
> **phillw said:**
> I have a 2GB stick, lubuntu leaves me about 700MB free. I really do scratch my head when people say 'it needs this' etc. 

I have a 'persistant' install on that little critter. and, yes, it is the speed-boost certified stick that I advise people to get.

Regards,

Phill.

But I'm not talking about persistent "live". I'm talking about actually installing Lubuntu using the live installer (aka: ubiquity) to a hard drive :)

---

### Post by kansasnoob on 2011-08-05
> **andrewabc said:**
> Bad news.

Installed alpha 3 on liveusb. It starts fine and loads desktop.

Networking icon at bottom right is missing (gives the "no icon" icon). I select the icon and it says "Networking enabled" and "wireless enabled" (both have charkmarks. connection information is greyed out and edit connections is available). But there is no wireless connection listed. With 11.04 it automatically lists a connection available to connect to (and even does the popup at top right of screen to notify me that it is available). With this alpha there is no wireless to connect to. No idea how to connect to my wireless connection other than maybe going into wireless settings and having to manually enter in the SSID of my wireless router??

I went into "Additional Drivers" to see if maybe it was needing a wireless driver (Didn't before, but I know other laptops sometimes asks for it), but there were no drivers available.

This is on a nettop. Intel atom N270. eeebox b202

So any suggestions? Why wireless work with 11.04 before but now it doesn't?

The nettop doesn't really have access to ethernet cable to see if that even works. I'll probably try normal ubuntu alpha 3 to see if similar problem.

I'm hardly a wireless pro, in fact I'd say I'm a wireless dummy :P

But with my sons netbook I've had to use wicd for quite some time, maybe since about Karmic.

Of course installing wicd requires either a wired connection or using a chroot like this:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

NOTE: Since Natty it's no longer necessary to go through this crap:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Upstart_jobs_cannot_be_run_in_a_chroot](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Upstart_jobs_cannot_be_run_in_a_chroot)

The same has been true even upstream in Debian ........... I don't know why :confused:

---

### Post by phillw on 2011-08-05
> **kansasnoob said:**
> But I'm not talking about persistent "live". I'm talking about actually installing Lubuntu using the live installer (aka: ubiquity) to a hard drive :)

And, for a small disk installation is there a difference?

computer boots up, you work, and it saves everything? I am obviously missing something in my logic. Is it the word **persistent** that troubles people? I always thought of a system that saved what you did was an advantage :confused:

Regards,

Phill.

---

### Post by ronacc on 2011-08-05
I think what kansas means is that a live cd ( or stick) install is not the same as a hd install . With the live cd there are no physical directories ( or not the same ones as on a hd install ) they are virtual directories living inside a compressed file system  .

---

### Post by kansasnoob on 2011-08-06
> **phillw said:**
> And, for a small disk installation is there a difference?

computer boots up, you work, and it saves everything? I am obviously missing something in my logic. Is it the word **persistent** that troubles people? I always thought of a system that saved what you did was an advantage :confused:

Regards,

Phill.

How are you installing to the flash drive?

By booting the Live CD and then clicking on install?

Or using the USB-creator (aka: Startup Disc Creator)?

Or something else?

---

### Post by phillw on 2011-08-06
I am naughty, putting a persistant install on to a hard drive has what problems? I really do fail to see the difference between a small hard drive and a USB stick. 

Whilst Ubiquity addresses the out standing issues of RAM and HD requirement, it is indeed a dirty little hack. But, it works :)

Regards,

Phill.

---

### Post by kansasnoob on 2011-08-06
> **phillw said:**
> I am naughty, putting a persistant install on to a hard drive has what problems? I really do fail to see the difference between a small hard drive and a USB stick. 

Whilst Ubiquity addresses the out standing issues of RAM and HD requirement, it is indeed a dirty little hack. But, it works :)

Regards,

Phill.

I've never tried it, but AFAIK live installs boot using syslinux and casper, whereas actual installs would commonly use grub. But you can boot live images with grub2. And what ronacc said :D

I'm just focusing on that one bug where ubiquity doesn't seem to allow installations if the disc space is not within a set limit. IMHO using the manual (aka: Something else) option should override any set parameters in ubiquity regardless ................... that's what I need to test for :)

A fully automated installation does some things that I don't fully understand. I have two sets of hardware that I commonly use now:

Box #1:
JetWay JATOM-GM1-230-LF Motherboard
Intel Atom 230 CPU @ 1.60GHz
System Memory 2GB DIMM
Intel 82945G/GZ Integrated Graphics
Intel N10/ICH 7 Family High Def Audio Controller

Box #2:
VIA PC2500 Mainboard
VIA Esther C7 CPU 1500MHz
System Memory 2GB DIMM
VT8233/A/8235/8237 AC97 Audio Controller
CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] Graphics

But oddly using the fully automated installer wants to create more swap space on the older VIA box than it does on the Intel box, about 50% more. Why?

It really makes no sense to me since both have 2GB of RAM :confused:

But IMHO the manual install via the Live CD/DVD/USB should always allow installation unless there truly is insufficient space ............. much in the same way that one can install with no internet connection at all.

I should be able to run a bunch of these tests quite soon. IMHO I should be able to install Lubuntu to one of these 3.2GB drives. If not I should be able to provide some feedback at that bug report.

---

### Post by ronacc on 2011-08-06
I have got something really bizzare going on here . I burned the 64bit iso to a dvd using xfburn , wouldn't boot , tried burning it with k3b from ubuntu , wouldn't boot .tried burning it on a different box , wouldn't boot  tried booting each of the " coasters " on the different box , they all booted . Tried a previously burned Ubuntu a3 that I had used to reinstall my ubuntu ( gnome-shell ) partition , it booted , tried burning the lubuntu 32bit .iso using xfburn it boots  . The bizzare thing is that the 64bit .iso's will boot on one box but not the other , tried puting it on a usb stick no luck there either .  I'm going to re d/l the 64bit .iso and see if anything changes .

---

### Post by kansasnoob on 2011-08-06
> **ronacc said:**
> I have got something really bizzare going on here . I burned the 64bit iso to a dvd using xfburn , wouldn't boot , tried burning it with k3b from ubuntu , wouldn't boot .tried burning it on a different box , wouldn't boot  tried booting each of the " coasters " on the different box , they all booted . Tried a previously burned Ubuntu a3 that I had used to reinstall my ubuntu ( gnome-shell ) partition , it booted , tried burning the lubuntu 32bit .iso using xfburn it boots  . The bizzare thing is that the 64bit .iso's will boot on one box but not the other , tried puting it on a usb stick no luck there either .  I'm going to re d/l the 64bit .iso and see if anything changes .

I have no 64 bit hardware but I noticed a butt-load of bugs with 64-bit Lubuntu:

[http://iso.qa.ubuntu.com/qatracker/test/6095](http://iso.qa.ubuntu.com/qatracker/test/6095)

---

### Post by ronacc on 2011-08-06
I am all ( well 99.9% ) 64 bit here . Back when AMD came out with the first athalon 64 I swore off 32 bit . The only concession I have made is an eeepc  that I got when they first came out , everything else is 64bit and as a mater of principle I refuse to run ( with a few specific exceptions ) a 32bit OS on 64bit hdw

---

### Post by garvinrick4 on 2011-08-07
Running 64 bit 11.04 lubuntu with 3.0.1 oneiric kernel from:
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Need "module-init-tools 3.13.1 have in .deb package launchpad.
Running fine, I use 3.0 and up because it uses intels iwlagn driver at N speeds
where 2.6. would only use G, had to config file out the N of your card with iwlagn driver.
Anyway runs fine:

---

### Post by kansasnoob on 2011-08-07
> **garvinrick4 said:**
> Running 64 bit 11.04 lubuntu with 3.0.1 oneiric kernel from:
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Need "module-init-tools 3.13.1 have in .deb package launchpad.
Running fine, I use 3.0 and up because it uses intels iwlagn driver at N speeds
where 2.6. would only use G, had to config file out the N of your card with iwlagn driver.
Anyway runs fine:

That's great info. Since I use only wired networking I wouldn't have known that.

---

### Post by phillw on 2011-08-08
Watching the capital of my country burn with riots does not really leave me in a good a frame of mind. I am old enough to recall that last time all this happened in the UK.

My thoughts on dealing with such rampant violence are not on the 'left' side. In the UK, our police force are one of the few not to be routinely armed & we do not have water cannon  / tear gas / rubber bullets for the main part of UK. I fear that this may change.

If I could please ask that you raise bug report things, that is the 'official' way of tracking bugs & something lubuntu, and all variants must use. >  the devs do not read the forums .

I'm really sorry for not being around as much as I usually am. We all love our own country's, and things happen...

Regards,

Phill.

---

### Post by slavinzing56 on 2011-08-08
I also have done many HD installs of puppy , I really like the way it handles random networks .

---

### Post by ronacc on 2011-08-08
> **slavinzing56 said:**
> I also have done many HD installs of puppy , I really like the way it handles random networks .

I find it quite disappointing that the " major distros "  can't seem to handle networking and initial display setup as well as Barry does with Puppy .

---

### Post by northwestuntu on 2011-08-08
i havent used lubuntu for about a year now.  im glad to hear a 64 bit version is out now.  always thought it was missing out on a lot of users who want a 64 version.  i look forward to testing this out on my new hardware i just bought.

---

### Post by kansasnoob on 2011-08-09
> **phillw said:**
> Watching the capital of my country burn with riots does not really leave me in a good a frame of mind. I am old enough to recall that last time all this happened in the UK.

My thoughts on dealing with such rampant violence are not on the 'left' side. In the UK, our police force are one of the few not to be routinely armed & we do not have water cannon  / tear gas / rubber bullets for the main part of UK. I fear that this may change.

If I could please ask that you raise bug report things, that is the 'official' way of tracking bugs & something lubuntu, and all variants must use. .

I'm really sorry for not being around as much as I usually am. We all love our own country's, and things happen...

Regards,

Phill.

No worries, just stay safe :D

I'll probably be tied up for the better part of a week here.

---

### Post by caieng on 2011-08-10
I submitted this message to an earlier thread, but, turns out, it was marked "solved", which is misleading, because this problem is most definitely, NOT SOLVED.

So, I resubmit it, on its own.

The previous thread sought input from the forum, on a comparison of XFCE versus LXDE.  I would like to try them both, but, the newest iteration of Lubuntu, i.e. released for download a couple weeks ago, exceeds the capacity of the blank Verbatim CDROM's.

This is rather peculiar, not only because it would seem obvious that the size has exceeded the 700 megabyte capacity of the blank disks, but also because EARLIER versions of LXDE, including alpha releases from a couple of months ago, were NOT excessively large.

From a marketing perspective, it does look clumsy to release a distro that won't fit on the intended media....One wonders whether the engineers may have miscalculated some other aspects of the distro??? In the best case, it looks sloppy. In the worst case, the excessive size conveys the impression, at least to me, that folks in Ubuntuland, simply added some stuff to the Gnome version, and sent it on its merry way, one supposes without much testing, and certainly, without much thought. 

But, apart from that, this is a thread which asks: XFCE, versus LXDE, which is "more Lightweight". (great question, by the way, at least in my opinion.) 

So, can anyone explain to me, WHY the LXDE (supposedly "light weight" version of Ubuntu, IS LARGER than the burly Gnome version of Ubuntu (which, however, is ALSO too big to fit on a 700 MByte blank CDROM, but, it is nevertheless, less obese, than LXDE.)

CAI ENG

---

### Post by Basher101 on 2011-08-10
I did not look at the lubuntu or xubunut isos, but my 11.04 natty iso niceley fits on blanks. You can still use a Live USB tho

---

### Post by kerry_s on 2011-08-10
It's always like that during development. 
When it is released it should be normal. 
The only version you should be using/trying is 11.04. [http://lubuntu.net/](http://lubuntu.net/)

Your not a tester, nor would you know what to do if something go's wrong, other wise you wouldn't be asking. 11.10 is developing, it's an unfinished product.

---

### Post by XubuRoxMySox on 2011-08-10
Most distros include alot of software, like LibreOffice, Firefox, all that stuff. And most distros are getting too full of the software for CDs now and going with DVDs instead.

But the *applications* included on a distro's LiveCD or LiveDVD have nothing to do with the resource demands of the *desktop environment*. LXDE (the desktop environment, not the distro Lubuntu) is "lighter" than Xfce. It had nothing to do with the size of the software files on the CD, but it's performance on your computer once installed.

Hoping that helps,
Robin

---

### Post by Megaptera on 2011-08-10
> **kerry_s said:**
> it's always like that during development. 
When it is released it should be normal. 
The only version you should be using/trying is 11.04. [http://lubuntu.net/](http://lubuntu.net/)

your not a tester, nor would you know what to do if something go's wrong, other wise you wouldn't be asking. 11.10 is developing, it's an unfinished product.


+ 1

---

### Post by Megaptera on 2011-08-10
> **dixiedancer said:**
>  ... But the *applications* included on a distro's livecd or livedvd have nothing to do with the resource demands of the *desktop environment*. Lxde (the desktop environment, not the distro lubuntu) is "lighter" than xfce. It had nothing to do with the size of the software files on the cd, but it's performance on your computer once installed.

Hoping that helps,
robin

+ 1 !

---

### Post by kerry_s on 2011-08-10
my theory is there's extra debugging tools, plus there still in the process of selecting applications, like i hear there switching to the xfce4-power-manager, which i think is good, with that they can get rid of xscreensaver & gnome-power-manager.

---

### Post by claracc on 2011-08-11
You can download the current stable relase for lubuntu 11.04 from here: [http://lubuntu.lafibre.info/11.04/](http://lubuntu.lafibre.info/11.04/), all of these iso downloads fit a cdrom capacity.

---

### Post by caieng on 2011-08-11
Thanks to several forum members, GOOD REPLIES.

I should have written more carefully.

Start again:   Lubuntu, 11.04, downloads and fits just fine, on a single CDROM, as advertised.

This thread was started, because I THEN downloaded the NEWER (or, perhaps, even, the newest) version, 11.10 alpha or beta, i.e. a model intended for TESTING.

I am running a test, comparing different versions of LXDE.  I thought it would be useful/interesting/worthwhile to compare 11.04 with 11.10, to learn what advantage, if any, arose upon exploiting the newer version, on the target hardware:   OLDER computers.

I am unable to accomplish that goal, because the newest version is LARGER than the capacity of the CDROM.

"Older" hardware, remember?  no dvd player.....

Two questions remain, despite the excellence of the previous responses....

a.  WHY is the LXDE version of Ubuntu, i.e. Lubuntu, LARGER, (even if only for TESTING purposes), than the plain vanilla Ubuntu itself.....
Am I the only person who finds strange the notion that a "lighter" desktop environment, would nevertheless contain MORE software to download and install????
At least to me, that is terribly counter-intuitive.  Why would a testing version have MORE on it, than the final version???  That's also not good programming practice, from a software engineering point of view.

In my opinion, the BEST written software is that which is MORE compact, smaller, and faster, than the behemoth KDE's and GNOME's of this world.  I would not have been able to predict, ahead of time, that an LXDE version, whether FINISHED, or IN TESTING, would be LARGER in size, than the ordinary parent source:  Ubuntu itself.

Again I ask, as before:  Did the developers of Lubuntu simply ADD more software to an existing compilation of Ubuntu, and shove it out the door, on its merry way, to be "tested", evidently NOT on older computers, which lack the ability to pretend that "cdroms or dvd's what's the difference, anyway"????

b. Since the older version DOES fit on a CDROM, am I able, with Synaptic, to upgrade to the newest "testing" version, **without downloading** the "testing version"?

CAI ENG

---

### Post by mcduck on 2011-08-11
> **caieng said:**
> Thanks to several forum members, GOOD REPLIES.

I should have written more carefully.

Start again:   Lubuntu, 11.04, downloads and fits just fine, on a single CDROM, as advertised.

This thread was started, because I THEN downloaded the NEWER (or, perhaps, even, the newest) version, 11.10 alpha or beta, i.e. a model intended for TESTING.

I am running a test, comparing different versions of LXDE.  I thought it would be useful/interesting/worthwhile to compare 11.04 with 11.10, to learn what advantage, if any, arose upon exploiting the newer version, on the target hardware:   OLDER computers.

I am unable to accomplish that goal, because the newest version is LARGER than the capacity of the CDROM.

"Older" hardware, remember?  no dvd player.....

Two questions remain, despite the excellence of the previous responses....

a.  WHY is the LXDE version of Ubuntu, i.e. Lubuntu, LARGER, (even if only for TESTING purposes), than the plain vanilla Ubuntu itself.....
Am I the only person who finds strange the notion that a "lighter" desktop environment, would nevertheless contain MORE software to download and install????
At least to me, that is terribly counter-intuitive.  Why would a testing version have MORE on it, than the final version???  That's also not good programming practice, from a software engineering point of view.

In my opinion, the BEST written software is that which is MORE compact, smaller, and faster, than the behemoth KDE's and GNOME's of this world.  I would not have been able to predict, ahead of time, that an LXDE version, whether FINISHED, or IN TESTING, would be LARGER in size, than the ordinary parent source:  Ubuntu itself.

Again I ask, as before:  Did the developers of Lubuntu simply ADD more software to an existing compilation of Ubuntu, and shove it out the door, on its merry way, to be "tested", evidently NOT on older computers, which lack the ability to pretend that "cdroms or dvd's what's the difference, anyway"????

b. Since the older version DOES fit on a CDROM, am I able, with Synaptic, to upgrade to the newest "testing" version, **without downloading** the "testing version"?

CAI ENG
Like others have said, lighter has nothing to do with the amount of software included, but on the amount of resources it uses. Less load on CPU and lower RAM requirements are what make an OS lighter. (larger amount of software doesn't increase the CPU or RAM requirements, only the amount of hard drive space used. And that depends on how much program the user installs anyway, so amount of disc space used is in no way a good measure for the lightness of an OS)

And the size of the disc image is pretty much among the least relevant things when it's still in development. It's not intended to be used by anybody other than developers and testers at this point (testing meaning bug testing, not testing to see if you like it or not, as it's not finished product yet).

Development versions are larger simply because the developers are still working on it, and at that point it only slows down the development if they bother thinking about if the image is exactly the same size as a CD, especially since the included packages and their versions are still changing, and in addition all the bug tracing code makes the packages larger than what they would be in a final release.

---

### Post by XubuRoxMySox on 2011-08-11
Yup. It still has to "just work out of the box," and it still should have the latest versions, if possible, of a browser, e-mail client, office apps, music player, video player, and other commonly used desktop apps. Most of the latest versions of these things come in larger *file sizes*, even if they are "lightweight" when installed on a computer.

I use a few "legacy" applications (Seamonkey in place of Firefox and Thunderbird, for example) just because they're easier on my hardware, instantly available in the repositories, and just suit my own tastes better. But most people - even those with older hardware and seeking a distro that will run well on it - prefer the latest versions of their own favorite applications. During the experimental / testing phase of the elease cycle, the developers are trying out different ones to see how they work and what their users want.

By the time they are finally released in their final form, I promise, both Lubu and Xubu will easily fit on a regular CD. Both teams are committed to iso files no bigger than 700 MB by release time. Until then, the trial versions may be bigger or smaller just depending on how the testing is going.

-Robin

---

### Post by TBABill on 2011-08-11
The devs will chop it down before release. Keep in mind all the software comes from Debian Sid originally so they have to make their changes, repackage, reconfigure and test, change or whatever until they feel they have a final product. Until then it's pretty normal to have more software than they intend to finish with because it's all probably, in theory, up for removal in the event something doesn't work right.

---

### Post by caieng on 2011-08-11
[QUOTE="mcduck"]Less load on CPU and lower RAM requirements are what make an OS lighter.[/QUOTE]
Hi McDuck,

I don't agree, at all.  When we write, or read, "lighter", with reference to LXDE, (or XFCE), we are NOT referring to CPU or RAM, or hard disk either.  We are referencing the quantity of running processes.

Now, are those processes using up cpu resources?  YES.  Memory?  yes.  But, can you envision a "light" os that has a huge burden on both memory and cpu--->  yes... M$ Windows....

The fastest implementations use memory, lots of it, in fact, loading the entire OS into memory, bypassing the hard drive, after boot up.

The question, **you have thus far not addressed**, is why plain vanilla Ubuntu should be SMALLER on the CDROM than Lubuntu.

That makes no sense to me, whether one is testing, or has included gobs of testing software, or not.

CAI ENG

---

### Post by caieng on 2011-08-11
@dixiedancer and TBABill:

Thank you both, for skillful rejoinders, well written, and much appreciated.

Here's the problem, simplified:

Box A contains 500 trinkets, Box B contains 400 trinkets.  Both boxes are marketing research, experimental allocations.  When the final version is offered at the county fair next month, there will be only 300 trinkets in each box.

Salesman BBB complains to the head office that he would prefer to market boxes containing only 300 trinkets, since that is what will be offered at the county fair.  He protests that it makes little sense, from a marketing research perspective, to test public reception to the boxes if the contents differ from that  intended for distribution at the County Fair. 

Would you fire him/her for insubordination?  I would paste a gold star on his forehead.

CAI ENG

---

### Post by mcduck on 2011-08-11
> **caieng said:**
> Hi McDuck,

I don't agree, at all.  When we write, or read, "lighter", with reference to LXDE, (or XFCE), we are NOT referring to CPU or RAM, or hard disk either.  We are referencing the quantity of running processes.

Now, are those processes using up cpu resources?  YES.  Memory?  yes.  But, can you envision a "light" os that has a huge burden on both memory and cpu--->  yes... M$ Windows....

The fastest implementations use memory, lots of it, in fact, loading the entire OS into memory, bypassing the hard drive, after boot up.

The question, **you have thus far not addressed**, is why plain vanilla Ubuntu should be SMALLER on the CDROM than Lubuntu.

That makes no sense to me, whether one is testing, or has included gobs of testing software, or not.

CAI ENG
The amount of running processes would be a false indicator of system lightness, and the amount of installed software definitely is false as well (since installed software doesn't equal running software).

You can have many running processes that use very little resources, and you can have a few that are extremely heavy. So simply counting the number of processes doesn't tell you anything.

And yes, I *have* addressed your question. It's still under development, so it's not yet at the stage when there's any reason to fit it into a CD image. And even then the image will be pretty much the exact same size as any other Ubuntu version, the size of a CD. Since, once again, the amount available or installed software doesn't have anything to do with how new or powerful computer you need to run the OS. That only affects the amount of hard drive space required.

(I assume when you say "we" in the post, you mean "I", as that's definitely the strangest definition of a lightweight operating system I've heard this far. :))

---

### Post by dFlyer on 2011-08-11
> **caieng said:**
> I submitted this message to an earlier thread, but, turns out, it was marked "solved", which is misleading, because this problem is most definitely, NOT SOLVED.

So, I resubmit it, on its own.

The previous thread sought input from the forum, on a comparison of XFCE versus LXDE.  I would like to try them both, but, the newest iteration of Lubuntu, i.e. released for download a couple weeks ago, exceeds the capacity of the blank Verbatim CDROM's.

This is rather peculiar, not only because it would seem obvious that the size has exceeded the 700 megabyte capacity of the blank disks, but also because EARLIER versions of LXDE, including alpha releases from a couple of months ago, were NOT excessively large.

From a marketing perspective, it does look clumsy to release a distro that won't fit on the intended media....One wonders whether the engineers may have miscalculated some other aspects of the distro??? In the best case, it looks sloppy. In the worst case, the excessive size conveys the impression, at least to me, that folks in Ubuntuland, simply added some stuff to the Gnome version, and sent it on its merry way, one supposes without much testing, and certainly, without much thought. 

But, apart from that, this is a thread which asks: XFCE, versus LXDE, which is "more Lightweight". (great question, by the way, at least in my opinion.) 

So, can anyone explain to me, WHY the LXDE (supposedly "light weight" version of Ubuntu, IS LARGER than the burly Gnome version of Ubuntu (which, however, is ALSO too big to fit on a 700 MByte blank CDROM, but, it is nevertheless, less obese, than LXDE.)

CAI ENG

If your referring to 11.10 you are correct. Read the Release Notes. They state that you will need to use a dvd to burn the cd live desktops.

---

### Post by mcduck on 2011-08-11
> **caieng said:**
> @dixiedancer and TBABill:

Thank you both, for skillful rejoinders, well written, and much appreciated.

Here's the problem, simplified:

Box A contains 500 trinkets, Box B contains 400 trinkets.  Both boxes are marketing research, experimental allocations.  When the final version is offered at the county fair next month, there will be only 300 trinkets in each box.

Salesman BBB complains to the head office that he would prefer to market boxes containing only 300 trinkets, since that is what will be offered at the county fair.  He protests that it makes little sense, from a marketing research perspective, to test public reception to the boxes if the contents differ from that  intended for distribution at the County Fair. 

Would you fire him/her for insubordination?  I would paste a gold star on his forehead.

CAI ENG
the example might be more appropriate if you also accounted for the fact that each trinket has a different weight and value. And one box was actually for sale, while the other is still for the internal use of the research/development department of the company. ;)

I also said that the testing version of Lubuntu is not for testing how people like it. It's for *bug testing*. You should probably start by reading Ubuntu's wiki page for testing before you even try a development release. [https://wiki.ubuntu.com/Testing]("https://wiki.ubuntu.com/Testing")

---

### Post by drs305 on 2011-08-11
This thread has been moved to the Ubuntu+1 forum since the majority of the discussions relate to the image size of a pre-release version of the OS.

---

### Post by caieng on 2011-08-11
[QUOTE="dFlyer"]If your referring to 11.10 you are correct. Read the Release Notes. They state that you will need to use a dvd to burn the cd live desktops.[/QUOTE]

Thanks for that Gary,  umm, no, mea culpa, I DID NOT READ the Release notes, but I did read the text on the download page, which specifically stated CDROM, not DVD.

However, that is really IRRELEVANT to the central issue.  WHY in the world would Ubuntu folks issue a "light" distro, INTENDED FOR OLDER HARDWARE, and then make it impossible to install that software, by demanding use of DVD?

Moreover, why are folks here, on this forum, defending the shoddy practice of sending out "testing" versions which are OBVIOUSLY different from (and quite possibly defective) the intended RELEASE version, n months from now...?  That is an UNACCEPTABLE engineering practice.  For sure, this thread would never have arisen, for **I would not have downloaded** the distro, if it had insisted upon a DVD.

One does NOT test a version which is KNOWN to contain redundant software, in the amount of hundreds of megabytes.......

A few kilobytes, for some special testing routines, ok, no problem.  But, 70 MEGABYTES?

That's absurd.

WHY, if all this extra testing software is so crucial to assess the performance of this TEST version of LUBUNTU, does the plain vanilla version of Ubuntu NOT CONTAIN this SAME "testing" software?  Ubuntu itself is a good 50 Megabytes smaller than Lubuntu.  Why?

[QUOTE="mcduck"]I also said that the testing version of Lubuntu is not for testing how people like it. It's for bug testing.[/QUOTE]

I know nothing, or perhaps, LESS than nothing, about Ubuntu and Ubuntu's method of testing software.  But, I have a few DECADES of experience testing software in the industrial and aerospace sectors (no, I am not the guy who incorrectly computed the trajectory of that Mars capsule that crashed), and I am very confident, that you will NOT find a reference in the literature to support your idea that one should issue a pre-release version of software on a medium different from that intended for the final distribution.

"It's for bug testing."  Did you think about the implications of your sentence?

How do you want folks to test for bugs, if they cannot even make the cdrom?  Absurd.

Let's start over, shall we?

1.  LUBUNTU is a version of Ubuntu, destined for computers of LOW, or LIMITED resources, or those of ANTIQUE vintage, or at least, those with slow cpu's and modest sums of memory.

Now, if that premise is erroneous, and you, the developers of Lubuntu, intend instead, that I should test this distro on my 4 GHz Intel Core i7 with 16 GB DDR3, ok, that's also possible, but, that's NOT what most folks imagine, as the advantage offered by LXDE.

2.  Testing, whether for "bugs", or identifying user preferences, demands, if properly executed, a method of conveying the item to be examined to those folks engaged in the task of analyzing any potential defects.

3.  Whether or not it is correct, peoples' perceptions about a company, or a Linux distribution, are influenced by what many perhaps, might term as insignificant details.  I for one, judge the quality of a Linux distro by three factors, and I have never encountered anyone else who identifies the same factors as significant in judging the quality of the distro:

a.  out of the box, **effortless** installation:
(I am on record, as attesting to the fact, that in my opinion, the Ubuntu installer is the best, hands down, in the business)

b.  out of the box, effortless installation of VLC (if not already installed by default).  If VLC is present, but does not function properly by translating streaming audio, as it should, the distro is worthless, in my view (LINT).  Sorry, I am so used to speaking and writing LINT, I should write more respectfully, MINT.

c.  easy installation of Opera, my preferred browser.

Thus far, I have found very few Linux distros which fulfil those criteria.  I was hoping that Lubuntu would join that elite group.  Thus far, it is impossible to assess, using the 11.10 alpha/beta version.

Streaming audio reception (internet radio station receiver) is one application, where a 4GHz cpu will not outshine my simple 1GHz PIII with half a Gig of RAM.  

I can connect both computers to two different inputs on the Yamaha receiver, and fail then, on switching between the two inputs, to distinguish which computer is the faster/slicker/better....Remember the violinist or pianist performing behind a curtain, at competitions, so that the judges are focused on the sound, and not the visual appearance.

CAI ENG

---

### Post by ronacc on 2011-08-11
@ kansasnoob  I finaly got things straightened out and got a 64 bit install going . just for info the size on disk of a fresh 64 bit install is 3.45 gb ( no swap) .

---

### Post by cariboo on 2011-08-11
You are trying to run a testing version, all of the isos are ususally to big to fit on a cd until around the beta release when all the debugging files are removed. Instead of getting upset about it, if you'd read the release notes, you would have been warned about the problem. 

This is normal, it has nothing to do with whether it is a lighter distribution designed for older systems, or a full version designed for up to date systems. Check back after the beta is released, and you should get what you want.

If you to want to run a testing version, that may well be broken at various times, I'd suggest you read the stickies at the top of the page, and [this]("http://www.chiark.greenend.org.uk/~sgtatham/bugs.html") page, on how to report bugs.

---

### Post by kerry_s on 2011-08-11
i under stand what he's saying, but to me the problem is on his end.

wants to test but:
no dvd, not ubuntu's fault, a personal hardware limitation. work around or fix.

> 
1. LUBUNTU is a version of Ubuntu, destined for computers of LOW, or LIMITED resources, or those of ANTIQUE vintage, or at least, those with slow cpu's and modest sums of memory.


on a finished version that might be true, but it's not a finished version.

as far as testing go's, i assume that if you wanted to really test, you would find away.
can you use a usb device?

my computer doesn't even have cd, so i always use the start up disk creator to burn to usb flash drive and use that, i have several in different sizes.

---

### Post by caieng on 2011-08-11
[QUOTE="cariboo907"]You are trying to run a testing version, all of the isos are ususally to big to fit on a cd until around the beta release when all the debugging files are removed. Instead of getting upset about it, if you'd read the release notes, you would have been warned about the problem. 

This is normal, it has nothing to do with whether it is a lighter distribution designed for older systems, or a full version designed for up to date systems. Check back after the beta is released, and you should get what you want.[/QUOTE]

Thanks to all, for the encouragement.  Very good.

OK, I will wait....

I wish someone would explain why "debugging files" are so much larger (50 MB) on Lubuntu than ordinary Ubuntu....Is it perhaps, not clear, that the impression conveyed, by this anomaly, is that the Lubuntu variant is just the same old Ubuntu, upon which an extra 50 MB of LXDE has been tacked on.  The fact that the gnome testing version is SMALLER than the LXDE testing version, by some 50 MB, suggests, absent clarification, that Lubuntu is just a sorry step child....

I welcome clarification of this issue.

CAI ENG

---

### Post by caieng on 2011-08-11
[QUOTE="kerry_s"]my computer doesn't even have cd, so i always use the start up disk creator to burn to usb flash drive and use that, i have several in different sizes.[/QUOTE]

Thank you Kerry, for confirming that at least SOME of the audience for Lubuntu, contrary to my assertion, is using MODERN computers, and NOT the old, obsolete junk like I use.....

Good luck booting from "usb flash drive" on my older computers.  Technology didn't exist in those days....

[QUOTE="[Wikipedia](http://en.wikipedia.org/wiki/Live_USB)"]Some computers, particularly older ones, may not have a BIOS that supports USB booting.[/QUOTE]

Of course, if the developers are all using Core I5's to develop Lubuntu, then, "eh, what's all the fuss about"???

CAI ENG

---

### Post by cariboo on 2011-08-11
Threads merged by request.

---

### Post by zealibib slaughter on 2011-08-11
You can boot from usb even on old hardware.  Here is a link: [http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/](http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/)
 
One of the reasons for difference in size between ubuntu and lubuntu betas could be that lubuntu uses a complete different DE and set of apps that may be more buggy than ubuntu at this point in the dev.

---

### Post by 23dornot23d on 2011-08-11
> 
Now, if that premise is erroneous, and you, the developers of Lubuntu,  intend instead, that I should test this distro on my 4 GHz Intel Core i7  with 16 GB DDR3, ok, that's also possible, but, that's NOT what most  folks imagine, as the advantage offered by LXDE.
:D You are hitting the nail right on the head there ...... 

Your options as far as I can see ..... and I can see you really want to get involved as I first did
a lot of us on here are not developers - but we have a desire to try to help .....

The thing is ...... you as you state ..... have two machines .... and you can test it on the machine it does not need testing on ........ right ..... the 7 core proves nothing ........

Now to the point ......

You want to test it on the machine that is the older one with only a CD drive in it -  so what possibility do you have of doing this ....... :confused:

Me if it was me ..... in this situation .... 

I would not let it stop me .....

I would go out and buy a USB Dvd drive just to become part of this wonderful development cycle .........

and if you do not have USB ports ....

I would in that situation go out and buy a USB card presuming its a desktop computer.
If it is a desktop computer ..... you could maybe get a DVD drive for it ......

But you say ....... why should I have to do any of the above ......

Well from what I can gather reading this thread ..... then they leave you very few options ...... as they obviously do not think its worth putting it onto a CD ...... :confused:

[B]I like solving problems ..... but what a dilema .... you ask for a CD .... they say no its DVD only .....

Your only options .... USB or DVD ...... new attachments for your computer are the only way I can see for you to get into this development cycle ..... and then you can start breaking things in this world of development ....... 

Unless its a laptop with no USB's ..... then its a [PCMIA card with USB Adaptop on it ]("http://discountcablesusa.com/usb-video.html").....
and a USB DVD drive .....  :confused:  .... starts costing you money already just to get involved.

Oh for a CD .....  ( not sure that they can do that ..... !!!! ) ..... 

[/B]> 
"debugging files" are so much larger (50 MB) on Lubuntu than ordinary Ubuntu
I also guess this is impossible to download after a install from a CD too ...... 
------------------------------------------------------------------------------------------------------------------------

If you do have USB's though on the older machine ... and a USB stick ...... that is another possibility ,,,,,


cheaper too .....

---

### Post by ronacc on 2011-08-11
not everyone is running lubuntu because they have old hardware although I do like the fact that it runs quite happily on my amd64x2 6000+ with 4 gig of ram and 1.5 TB disk space AND also my first edition EEEPC 701 with an 800mhz celeron throtled to 600mhz and 512mb ram and a 4gb ssd .MY main reason for now using lubuntu is that I despise unity .

---

### Post by Catharsis on 2011-08-11
I can sympathize with your complaints. You'd just like to test the OS on a system that it's designed for.

How old is your system though? Is it even within the System Requirements? I think Lubuntu was designed for my 1.4 GHz 512MB RAM Dell Latitude, but not my 333MHz 192MB RAM Dell Inspiron. I use Tiny Core Linux on the Inspiron because it's more appropriate. And my Latitude can boot a LiveUSB (which would fit the oversized ISO), but my Inspiron cannot. Funny how that works out, eh? Maybe you just have one of the few computers who are unlucky enough to fit the System Requirements but are not be able to boot from USB or DVD.

If I were you I would install Lubuntu Natty and then upgrade to Oneiric using "update-manager -d". (Is that the right way to upgrade to a pre-release?)


In response to Lubuntu being larger than Ubuntu, I think that might be because Ubuntu has already started to work towards slimming the ISO down. Why hasn't Lubuntu done as much work in this regard? It's probably because Lubuntu has, what, 3 developers? For the entire distro? You have to realize that they're humans, not machines. Volunteer humans, even. :)

---

### Post by kansasnoob on 2011-08-11
> **drs305 said:**
> This thread has been moved to the Ubuntu+1 forum since the majority of the discussions relate to the image size of a pre-release version of the OS.

I truly wish this hadn't been merged :D

Merging basically turns this one thread into a separate Lubuntu dev forum which is difficult.

It becomes like your old grub2 thread:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Things get run together and become difficult to focus on ;)

---

### Post by Catharsis on 2011-08-11
> **kansasnoob said:**
> i truly wish this hadn't been merged :d

merging basically turns this one thread into a separate lubuntu dev forum which is difficult.

It becomes like your old grub2 thread:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

things get run together and become difficult to focus on ;)

+1

---

### Post by kansasnoob on 2011-08-11
Getting back to the original rant about Lubuntu Alpha 3 not fitting on a CD the answer has already been put out there .............. development versions should not be compared to a finished product!

Lubuntu was only accepted as an official offspring of Ubuntu a few months ago. The Oneiric Alpha 1 was not built as an official Ubuntu child, and there was no Alpha 2.

The first official daily build only appeared about a week before Alpha 3 and a lot of development has gone into merging Lubuntu as a full fledged member of the Ubuntu family.

No one should doubt the devotion of the original Lubuntu devs at "getting things right", nor should anyone doubt that Canonical will fail to fully integrate Lubuntu into the family ..... it's happening, SABDFL always goes through with his promises :D

Some patience is required. There is a reason for having a development cycle. Those of us with a tiny bit of FOSS knowledge understand that the word development means we're still working on it! Would you prefer that all development go on behind closed doors?

And IMHO anyone that fails to read the release notes for any distro is only looking for trouble.

BTW Lubuntu will remain "light" but there will still be even lighter distros out there.

---

### Post by kansasnoob on 2011-08-11
> **Catharsis said:**
> I can sympathize with your complaints. You'd just like to test the OS on a system that it's designed for.

How old is your system though? Is it even within the System Requirements? I think Lubuntu was designed for my 1.4 GHz 512MB RAM Dell Latitude, but not my 333MHz 192MB RAM Dell Inspiron. I use Tiny Core Linux on the Inspiron because it's more appropriate. And my Latitude can boot a LiveUSB (which would fit the oversized ISO), but my Inspiron cannot. Funny how that works out, eh? Maybe you just have one of the few computers who are unlucky enough to fit the System Requirements but are not be able to boot from USB or DVD.

If I were you I would install Lubuntu Natty and then upgrade to Oneiric using "update-manager -d". (Is that the right way to upgrade to a pre-release?)


In response to Lubuntu being larger than Ubuntu, I think that might be because Ubuntu has already started to work towards slimming the ISO down. Why hasn't Lubuntu done as much work in this regard? It's probably because Lubuntu has, what, 3 developers? For the entire distro? **[COLOR="Red"]You have to realize that they're humans, not machines. Volunteer humans, even.[/COLOR]** :)

+1!

And the first official iso was spun about a week to 10 days before Alpha 3 :D

I have enough faith in the Lubuntu and Canonical devs to believe the final will be good .............. and 12.04 will be excellent :guitar:

---

### Post by kansasnoob on 2011-08-11
> **caieng said:**
> Thanks for that Gary,  umm, no, mea culpa, I DID NOT READ the Release notes, but I did read the text on the download page, which specifically stated CDROM, not DVD.

However, that is really IRRELEVANT to the central issue.  WHY in the world would Ubuntu folks issue a "light" distro, INTENDED FOR OLDER HARDWARE, and then make it impossible to install that software, by demanding use of DVD?

Moreover, why are folks here, on this forum, defending the shoddy practice of sending out "testing" versions which are OBVIOUSLY different from (and quite possibly defective) the intended RELEASE version, n months from now...?  That is an UNACCEPTABLE engineering practice.  For sure, this thread would never have arisen, for **I would not have downloaded** the distro, if it had insisted upon a DVD.

One does NOT test a version which is KNOWN to contain redundant software, in the amount of hundreds of megabytes.......

A few kilobytes, for some special testing routines, ok, no problem.  But, 70 MEGABYTES?

That's absurd.

WHY, if all this extra testing software is so crucial to assess the performance of this TEST version of LUBUNTU, does the plain vanilla version of Ubuntu NOT CONTAIN this SAME "testing" software?  Ubuntu itself is a good 50 Megabytes smaller than Lubuntu.  Why?



I know nothing, or perhaps, LESS than nothing, about Ubuntu and Ubuntu's method of testing software.  But, I have a few DECADES of experience testing software in the industrial and aerospace sectors (no, I am not the guy who incorrectly computed the trajectory of that Mars capsule that crashed), and I am very confident, that you will NOT find a reference in the literature to support your idea that one should issue a pre-release version of software on a medium different from that intended for the final distribution.

"It's for bug testing."  Did you think about the implications of your sentence?

How do you want folks to test for bugs, if they cannot even make the cdrom?  Absurd.

Let's start over, shall we?

1.  LUBUNTU is a version of Ubuntu, destined for computers of LOW, or LIMITED resources, or those of ANTIQUE vintage, or at least, those with slow cpu's and modest sums of memory.

Now, if that premise is erroneous, and you, the developers of Lubuntu, intend instead, that I should test this distro on my 4 GHz Intel Core i7 with 16 GB DDR3, ok, that's also possible, but, that's NOT what most folks imagine, as the advantage offered by LXDE.

2.  Testing, whether for "bugs", or identifying user preferences, demands, if properly executed, a method of conveying the item to be examined to those folks engaged in the task of analyzing any potential defects.

3.  Whether or not it is correct, peoples' perceptions about a company, or a Linux distribution, are influenced by what many perhaps, might term as insignificant details.  I for one, judge the quality of a Linux distro by three factors, and I have never encountered anyone else who identifies the same factors as significant in judging the quality of the distro:

a.  out of the box, **effortless** installation:
(I am on record, as attesting to the fact, that in my opinion, the Ubuntu installer is the best, hands down, in the business)

b.  out of the box, effortless installation of VLC (if not already installed by default).  If VLC is present, but does not function properly by translating streaming audio, as it should, the distro is worthless, in my view (LINT).  Sorry, I am so used to speaking and writing LINT, I should write more respectfully, MINT.

c.  easy installation of Opera, my preferred browser.

Thus far, I have found very few Linux distros which fulfil those criteria.  I was hoping that Lubuntu would join that elite group.  Thus far, it is impossible to assess, using the 11.10 alpha/beta version.

Streaming audio reception (internet radio station receiver) is one application, where a 4GHz cpu will not outshine my simple 1GHz PIII with half a Gig of RAM.  

I can connect both computers to two different inputs on the Yamaha receiver, and fail then, on switching between the two inputs, to distinguish which computer is the faster/slicker/better....Remember the violinist or pianist performing behind a curtain, at competitions, so that the judges are focused on the sound, and not the visual appearance.

CAI ENG

If you'd like I'll answer each of your questions. Just let me know :D

---

### Post by cariboo on 2011-08-11
@kansasnoob

I merged the threads at the request of phillw.

---

### Post by kansasnoob on 2011-08-11
> **cariboo907 said:**
> @kansasnoob

I merged the threads at the request of phillw.

Oops. My bad :redface:

My biggest problem ATM is time. Simply more to do than there are hours in the day ;)

But this actually breaks down into areas beyond Lubuntu. Like Ubuntu development itself, how long a cycle should be, who should be involved, etc, etc.

IMHO we've got it about right and I've even played my part in trying to be sure important stuff gets included in the release notes :D

---

### Post by wojox on 2011-08-12
@kansanoob

Why don't you folks gussy up [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

I've started using Lubuntu 11.04 and think it's a great spin. Would be more the happy to help out. :D

---

### Post by arpanaut on 2011-08-12
> **cariboo907 said:**
> @kansasnoob

I merged the threads at the request of phillw.


Given the spirit of this thread thus far: wouldn't it have been better to have just moved the "obese" thread to Ubuntu +1 rather than pollute this thread with something that is just a development issue, rather than a lubuntu issue per se.  Just saying...  With your position in the forum cannot you use some editorial discretion?

I am not in any way trying to be disrespectful, I admire the work you do here... I just agree with kansasnoob it is not OT in this thread.  Oversize images are commonplace in development.

Just my humble opinion.

---

### Post by caieng on 2011-08-12
[QUOTE="CAIENG"]WHY, if all this extra testing software is so crucial to assess the performance of this TEST version of LUBUNTU, does the plain vanilla version of Ubuntu NOT CONTAIN this SAME "testing" software? Ubuntu itself is a good 50 Megabytes smaller than Lubuntu. Why?[/QUOTE]

[QUOTE="kansasnoob"]If you'd like I'll answer each of your questions. Just let me know[/QUOTE]

Thank you kansasnoob.  Yes, I am looking forward to learning the definitive answer to this question.  Sorry, then, to inquire, but as I am totally ignorant of all matters Ubuntu, are you one of the folks who is, or was, involved in release of this software?  Alternatively, you may simply be a very well informed, or very intelligent, or a very experienced Linux user, **but not** someone intimately aware of the decision making process, regarding release of this particular testing software (Lubuntu 11.10 alphaxxx) to the public for evaluation....

[QUOTE="kansasnoob"][QUOTE="cariboo907"]  
@kansasnoob

I merged the threads at the request of phillw.[/QUOTE]
Oops. My bad[/QUOTE]

I have absolutely no idea at all, what this shuffling and moving is all about.  why has kansasnoob committed an error?  phillw?

Very mysterious.

If I had been involved with the decision making process, regarding release of this software, I would have issued the following ultimatum, to whoever is running the ship:

1.  Keep the maximum size to fit on a cdrom, **if it is** the intention of Ubuntu to release the FINAL version on cdrom. (i.e. the TESTING version, and the FINAL version, MUST be on the same medium.)  This is part and parcel of the ABC's of software engineering.  (Brooks, McConnell, DeMarco, Fowler)

2.  Include no extra programs beyond those required to confirm that LXDE itself is working properly with this Linux kernel and the Debian sources.  If synaptic is working properly, then, anyone seeking to install "open office", (or whatever other, gargantuan program,) on their computer, can download that particular application.  The size of the final TESTING version should be well under 700 megabytes, because MANY other Linux versions, based on LXDE, including Lubuntu from last year, easily fit on a cdrom.

I would have resigned, rather than accept issuance of software INTENTIONALLY defective, i.e. unable to fit on the target medium.  Whoever runs this Ubuntu ship, needs to realize the impression conveyed, upon issuance of a testing version of the STANDARD version of Ubuntu, based on the bloated Gnome desktop environment, which is decisively, obviously, SMALLER than the LXDE testing version.  Even if kansasnoob finds some magical words to explain this disparity, the ordinary guy off the street, like me, uninformed, unaware of what is going on, cannot but help, feeling, that the engineering aspect of Lubuntu, is in disarray.  Neither the Gnome version, nor the LXDE version, in my opinion, should have been released, in excess of the capacity of the cdrom, as both were.

Not everyone in the world has access to high speed internet, and DVD drives. 

CAI ENG

---

### Post by kansasnoob on 2011-08-12
> **wojox said:**
> @kansanoob

Why don't you folks gussy up [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

I've started using Lubuntu 11.04 and think it's a great spin. Would be more the happy to help out. :D

Indeed, a lot of info on that page is pretty badly out of date IMHO. Phillw could tell you much more than I could about what work needs to be done with the wiki.

I generally begin my searches at one of these two links:

[http://lubuntu.net/](http://lubuntu.net/)

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

We could certainly use all the help we can get, so thanks in advance :)

ATM I'm quite busy with unrelated activities but I've been doing Ubuntu iso-testing for quite some time but I'm gradually shifting my focus to Lubuntu.

My primary focus is on ubiquity (the live-installer) and casper, and currently I'm most concerned about these two bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/819538](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/819538)

I should be able to get around to doing some testing regarding the latter of the two very soon, and regarding the other one I need to check and see what recent changes, if any, have been made to ubiquity since the 4th.

---

### Post by cariboo on 2011-08-12
If you want to learn more about the development of Lubuntu, have a look at the developer [wiki page]("https://wiki.ubuntu.com/Lubuntu/Developers").

I would also suggest you tone down your posting style a bit, as it comes across as very demanding. Keep in mind that we are all volunteers here, we do this for fun.

---

### Post by phillw on 2011-08-12
> **cariboo907 said:**
> If you want to learn more about the development of Lubuntu, have a look at the developer [wiki page]("https://wiki.ubuntu.com/Lubuntu/Developers").

I would also suggest you tone down your posting style a bit, as it comes across as very demanding. Keep in mind that we are all volunteers here, we do this for fun.

thanks boss, I do really struggle to realise why people complain about a test alpha. When we get 11.10 released, we WILL get a 10.04.3 released. For our devs to run on two completely incompatible systems for iso building is a part of us being accepted. 

Have none you learned the word >  PATIENCE  If not,  then go use some different system. 

Regards,

Phill.
:lolflag:

---

### Post by kansasnoob on 2011-08-12
> **caieng said:**
> Thank you kansasnoob.  Yes, I am looking forward to learning the definitive answer to this question.  Sorry, then, to inquire, but as I am totally ignorant of all matters Ubuntu, are you one of the folks who is, or was, involved in release of this software?  Alternatively, you may simply be a very well informed, or very intelligent, or a very experienced Linux user, **but not** someone intimately aware of the decision making process, regarding release of this particular testing software (Lubuntu 11.10 alphaxxx) to the public for evaluation....



I have absolutely no idea at all, what this shuffling and moving is all about.  why has kansasnoob committed an error?  phillw?

Very mysterious.

If I had been involved with the decision making process, regarding release of this software, I would have issued the following ultimatum, to whoever is running the ship:

1.  Keep the maximum size to fit on a cdrom, **if it is** the intention of Ubuntu to release the FINAL version on cdrom. (i.e. the TESTING version, and the FINAL version, MUST be on the same medium.)  This is part and parcel of the ABC's of software engineering.  (Brooks, McConnell, DeMarco, Fowler)

2.  Include no extra programs beyond those required to confirm that LXDE itself is working properly with this Linux kernel and the Debian sources.  If synaptic is working properly, then, anyone seeking to install "open office", (or whatever other, gargantuan program,) on their computer, can download that particular application.  The size of the final TESTING version should be well under 700 megabytes, because MANY other Linux versions, based on LXDE, including Lubuntu from last year, easily fit on a cdrom.

I would have resigned, rather than accept issuance of software INTENTIONALLY defective, i.e. unable to fit on the target medium.  Whoever runs this Ubuntu ship, needs to realize the impression conveyed, upon issuance of a testing version of the STANDARD version of Ubuntu, based on the bloated Gnome desktop environment, which is decisively, obviously, SMALLER than the LXDE testing version.  Even if kansasnoob finds some magical words to explain this disparity, the ordinary guy off the street, like me, uninformed, unaware of what is going on, cannot but help, feeling, that the engineering aspect of Lubuntu, is in disarray.  Neither the Gnome version, nor the LXDE version, in my opinion, should have been released, in excess of the capacity of the cdrom, as both were.

Not everyone in the world has access to high speed internet, and DVD drives. 

CAI ENG

Well, it's quite typical for development releases to have bugs. An oversize image is a bug and it's mentioned as such in the release notes and also on the daily image download page:

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Generally very little effort is made during the alpha stage to ensure that images will fit on a CD, this is true of all flavors of Ubuntu. Generally beta releases are more likely to fit on a CD, but the daily builds still may not.

But alpha, beta, and release candidate images are intended for testing and reporting bugs, and IMHO it's unfair to compare them to a final release. The Ubuntu philosophy on testing (in my words, not Canonical's) is that the more people who test and report bugs the better, therefore development images are made available to anyone and everyone.

I happen to like that. When I first started iso-testing I'd probably only filed half a dozen bug reports in my life so I had to learn a lot, and I still have a lot to learn. I'd get bored if there were no challenge involved whatsoever :)

Some other distros do keep testing very much "in house". PCLinuxOS is probably one of the best examples of that, or even Linux Mint generally releases only one or two "release candidates" shortly before the final release.

All Ubuntu testing releases (as well as the finals) include release notes which are intended to be read:

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha3](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha3)

Specifically:

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha3#Download_the_Alpha_3](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha3#Download_the_Alpha_3)

> This release is for developers only. Most of these images are oversize; you can use either a DVD or USB for installation instead of a CD. 

Some of us like the way Canonical/Ubuntu does things, sometimes we disagree with the designers and/or developers so we use the proper channels to try and change things. In my own case I've won a few fights and lost a few others, and that's OK.

I certainly hope that Ubuntu keeps development releases easily available to all who are interested (Fedora does this as well) rather than closing the dev process to only a chosen few :)

In the grand scheme of things I'm both a nobody and a somebody, that's sort of how Ubuntu works. We all try to help each other, but we're all just human beings so we sometimes say or do things wrong. I apologized with an "oops" when I found out that phillw had requested the merging of these threads because I respect him and the work he's done towards improving Lubuntu.

I hope this answers most of your questions :)

---

### Post by cariboo on 2011-08-12
I agree with kansasnoob, the way Canonical/Ubuntu does development, and allows anyone to run testing releases and report bugs is one of the things that brought me to Ubuntu. I participated in a closed testing session for Xandros, and look where it is now, I feel that if the process had been more open, we would have squashed a lot more bugs that showed up in the final release.

---

### Post by phillw on 2011-08-12
> I apologized with an "oops" when I found out that phillw had requested the merging of these threads because I respect him and the work he's done towards improving Lubuntu.

I hope this answers most of your questions :) 

There is no apology nor 'oops' needed, as you said, our fantastic forum admins did their best to get everything lubuntu & oneric into one area. This will have and still will take time. For that 'bosses', thank you.

Herding cats is not too easy, any one who disagrees is welcome to join!

Regards,
Phill.

---

### Post by kansasnoob on 2011-08-12
> **cariboo907 said:**
> I agree with kansasnoob, the way Canonical/Ubuntu does development, and allows anyone to run testing releases and report bugs is one of the things that brought me to Ubuntu. I participated in a closed testing session for Xandros, and look where it is now, I feel that if the process had been more open, we would have squashed a lot more bugs that showed up in the final release.

I can also remember when Xandros PROMISED to keep a free edition of Linspire/Freespire available. Does anyone use Xandros?

---

### Post by ronacc on 2011-08-12
xandros came pre installed on my eeepc 701 , it didn't last very long . I replaced it with puppy and now lubuntu .

---

### Post by cariboo on 2011-08-12
I'd have to check my email archive, but if I remember correctly the Xandros Beta was in 2000-2001.

Now lets get back on topic. :)

---

### Post by phillw on 2011-08-13
yeah, as we approach the cut off, and we are a democracy. for those not on the Mailing List,> Hello people,

I believe I've never introduced myself to this mailing list so I'll do it quick.
My name is Alexander Andjelkovic [1] and I'm very interested in
artwork and design.
My current task is to manage a poll which will help us select
community wallpapers for Lubuntu.

The poll is made out of contributions submitted to our Flickr group [2] and the top six most popular wallpapers will be added to the Lubuntu artwork package.

We have a problem with the current tool for polling however, users can only vote on one alternative. Keep this in mind when you vote, as you might want to vote on a less popular wallpaper to make it more popular. I know it's pretty dull, but we'll solve it for the next time we do a poll like this.

The poll is located here:
[http://vote.statsr.net/vote/140/lubuntu-11-10-community-wallpapers/](http://vote.statsr.net/vote/140/lubuntu-11-10-community-wallpapers/) 

The poll is public and you do not need to register anywhere to be able to vote. It will be up and running for approximatly two weeks.

Hopefully the mailing list will be enough to get peoples voices heard, but maybe someone with rights could add the poll in the IRC topic?

Regards,
Alexander Andjelkovic.

[1]: [https://wiki.ubuntu.com/frankbooth](https://wiki.ubuntu.com/frankbooth) 
[2]: [http://www.flickr.com/groups/uawt-8/](http://www.flickr.com/groups/uawt-8/)  and, yes we do pay attention as to what you good people wish for Lubuntu.

Regards,

Phill.

---

### Post by kansasnoob on 2011-08-14
Just received this on the mailing list and it's quite important so thought I'd share it with all:

**About GTK2 -> GTK3 Migration, a critical issue**

> I'm not sure what Lubuntu devs will do on this issue, but from the LXDE side, there is no plan for the migration at this moment. For now, migration to gtk3 brings much more problems and bugs with no visible benefit. XFCE also keeps using gtk2 in the near future.
**[COLOR="Red"]The Chromium browser, is going to use gtk2 for quite a long time[/COLOR]**, too. They needs to support some older commercial systems on which gtk3 is not available. For current applications used in LXDE, migration to gtk3 brings no benefit but the work needs to be done is very huge.

The problems we will have after the migration:
1. PCManFM: desptop icons will be broken and this part needs some sort of rewrite for gtk3. In addition, some theming stuff uses gtk2 only features.
2. LibFM: this part still uses much GTK2 APIs. Though I already started the preperation for migration, this won't happen recently. As gtk3 now changed its user input handling and the change is not backward compatible, I'm not sure what bugs this will bring.
3. The XSettings daemon inside LXSession doesn't seem to be working for both gtk2 and gtk3 at the same time.
4. LXAppearance cannot configure gtk2/gtk3 at the same time. Technically it's not possible to make it work for both of them at the same time.
5. LXPanel is completely broken under gtk3. The work needs to fix the panel and port it to gtk3 is even more than developing a new panel. Hence, I plan to develop a new one based on gtk3 from scratch later. I will use libwnck at that time to avoid some low level X11 hacks. Some new widgets provided in gtk3 are useful for the new desktop panel. This could decrease much maintaince load and many unresolved bugs. I'll also do some UI redesign then. For now, migration to gtk3 for this one is 100% impossible and nobody is going to do it.
6. Migration of other components are possible, but since the major components still need more love, spending the time for migration to gtk3 for the least important components is pointless.
7. GTK+ 2 and gtk+ 3 modules are incompatible. So I'm not sure what will hapen to IM module (input method) after the migration. We will need two different IM modules. One for gtk2, and the other one is for gtk 3. Otherwise we cannot type non-English characters.
8. GTK2 and 3 programs can coexist, but this requires two librraries to be installed on the disk and loaded at runtime. Having a desktop environment composed by mixed gtk2/3 programs is a very bad idea since the resource usage is doubled for no additional benefit. This is not acceptable for LXDE. As most non-Gnome GTK+ based applications are not yet ported to gtk3, unless we're going to depend on gnome components, migration to gtk3 now brings harms only.

To sum up, **[COLOR="Red"]we're not going to do gtk3 migration in LXDE now[/COLOR]**. The reasonable timing for the migration is when XFCE and other non-Gnome programs, especially Chromium, which has many users, start the migration.

**[COLOR="Red"]Xubuntu will not use gtk3 this time[/COLOR]**, and it's really time for Lubuntu and others to think about the issue.



That comes from the lead developer of pcmanfm so I think this info is reliable. I wonder what the full implications will be switching DE's like installing 'lubuntu-desktop' on top of 'ubuntu-desktop', etc :confused:

---

### Post by ronacc on 2011-08-14
If I may be allowed a bit of heresy it might be a good idea to have a non ubuntu based fall-back install .

---

### Post by kansasnoob on 2011-08-14
> **ronacc said:**
> If I may be allowed a bit of heresy it might be a good idea to have a non ubuntu based fall-back install .

IMHO it's times like these that show the true brilliance of Ubuntu's release cycle. I have both Lucid and Natty running quite well (although I've had a few crashes with Firefox 5) and that allows plenty of transition time :)

---

### Post by kansasnoob on 2011-08-14
I had to take a break from the physical work .......... really had to because my cardiac dysrhythmia kicked up :)

So I took a look at the disc space requirement bug and made a comment:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

Does that make sense?

---

### Post by teh603 on 2011-08-14
Makes sense, but I don't think the developers will go for either one. The fact that it *has* to have an internet connection now makes me think there's some essential package being held back in the repositories and not being put on the install CD. Which makes it vulnerable to packet scrambling by ISPs and such.

---

### Post by kansasnoob on 2011-08-14
> **teh603 said:**
> Makes sense, but I don't think the developers will go for either one. The fact that it *has* to have an internet connection now makes me think there's some essential package being held back in the repositories and not being put on the install CD. Which makes it vulnerable to packet scrambling by ISPs and such.

Well your comment tends to tell me that I didn't communicate well enough that the "internet connection" requirement does NOT stop installation.

OTOH the disc space requirement can NOT be overridden :D

---

### Post by kansasnoob on 2011-08-14
Reading that over again I just don't see how I can better clarify that :confused:

I wish someone could comment there regarding whether the lack of a wired power source stops installation or not :D

Something I hadn't thought to mention there is how most installation options are displayed following that screen. It varies greatly depending on how many drives/partitions/OS's you have ;)

Maybe the following screen should just say something like, "the installer shows you lack sufficient space, continue only if you wish to override the default specs, this may result in a failed installation".

---

### Post by kansasnoob on 2011-08-14
Actually this bug is still included in the release notes:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

Specifically:

> Ubiquity desktop installer proceeds to use free space without warning, if sufficient free space exists, and "install alongside" is selected, then clicking on the forward button just begins the installation without warning.

I think they even used my poor punctuation :oops:

So maybe if they plan on making some changes regarding that they could also tweak things to display the type of warning I'm suggesting instead of preventing installation altogether.

I dunno :confused:

---

### Post by ronacc on 2011-08-14
over the years ubiquity has caused me more grief than any other part of Ubuntu although the pathological hatred some of the devs have for Nvidia is a close second .

---

### Post by Catharsis on 2011-08-14
> **kansasnoob said:**
> I had to take a break from the physical work .......... really had to because my cardiac dysrhythmia kicked up :)

So I took a look at the disc space requirement bug and made a comment:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

Does that make sense?

I just see a lot of broken installs because of this. You really want to make the OS idiot-proof, so it's almost impossible for someone to accidentally do something they shouldn't, even because they just didn't understand what they were doing.

I can just see someone who isn't tech-savvy (read: most people) trying to install without enough free space, wanting to continue, thinking "Hey, the button's there, let's try it anyway" or "Well I can still continue, so it must still be OK to continue installing." And then it fails and they start cursing Ubuntu and get unbelievably frustrated because the installer "told them they could install it" when it allowed them to continue. And now they say that Ubuntu is buggy and full of errors because you can't even install it without running into problems.

---

### Post by cariboo on 2011-08-15
> **kansasnoob said:**
> Reading that over again I just don't see how I can better clarify that :confused:

I wish someone could comment there regarding whether the lack of a wired power source stops installation or not :D

Something I hadn't thought to mention there is how most installation options are displayed following that screen. It varies greatly depending on how many drives/partitions/OS's you have ;)

Maybe the following screen should just say something like, "the installer shows you lack sufficient space, continue only if you wish to override the default specs, this may result in a failed installation".

I always do installations on my netbook without a network connection, the last one was Lubuntu alpha 1. The original install wouldn't install the bcmwl module my internal wireless device needs, but after the install was finished I plugged in a usb wireless device that let me do the updates to alpha 3, which also allowed mer to install the driver for my internal wireless device and solved several other problems. 

Not having a network connection doesn't stop the installation process in any way. You will have to set the time zone manually, but that's the only problem I've run into.

---

### Post by kansasnoob on 2011-08-15
> **cariboo907 said:**
> I always do installations on my netbook without a network connection, the last one was Lubuntu alpha 1. The original install wouldn't install the bcmwl module my internal wireless device needs, but after the install was finished I plugged in a usb wireless device that let me do the updates to alpha 3, which also allowed mer to install the driver for my internal wireless device and solved several other problems. 

Not having a network connection doesn't stop the installation process in any way. You will have to set the time zone manually, but that's the only problem I've run into.

Could I possibly talk you into trying an installation just on battery power? I'll bet it'll let you proceed just like not having an internet connection.

---

### Post by teh603 on 2011-08-15
> **cariboo907 said:**
> I always do installations on my netbook without a network connection, the last one was Lubuntu alpha 1. The original install wouldn't install the bcmwl module my internal wireless device needs, but after the install was finished I plugged in a usb wireless device that let me do the updates to alpha 3, which also allowed mer to install the driver for my internal wireless device and solved several other problems. 

Not having a network connection doesn't stop the installation process in any way. You will have to set the time zone manually, but that's the only problem I've run into.You can sometiems get bcmwl to install automatically? I've never been able to, even with a wired connection. Hell, on 10.04 I had to purge the bcmwl modaliases package and reinstall both it and bcmwl before it'd install.

---

### Post by kansasnoob on 2011-08-15
> **Catharsis said:**
> I just see a lot of broken installs because of this. You really want to make the OS idiot-proof, so it's almost impossible for someone to accidentally do something they shouldn't, even because they just didn't understand what they were doing.

I can just see someone who isn't tech-savvy (read: most people) trying to install without enough free space, wanting to continue, thinking "Hey, the button's there, let's try it anyway" or "Well I can still continue, so it must still be OK to continue installing." And then it fails and they start cursing Ubuntu and get unbelievably frustrated because the installer "told them they could install it" when it allowed them to continue. And now they say that Ubuntu is buggy and full of errors because you can't even install it without running into problems.

I do understand that, in fact that's why I was involved in breaking things originally:

[http://ubuntuforums.org/showpost.php?p=11117831&postcount=162](http://ubuntuforums.org/showpost.php?p=11117831&postcount=162)

I believe currently a fresh install of Ubuntu comes in around 3.2GB for / + whatever for swap. Lubuntu is about 2.3GB + swap. Of course some additional space is needed for updates, additional apps, general usage, etc.

And an automated install will typically create a swap anywhere from 1X to 2X the amount of RAM. So my thought was to allow proceeding, but only with sufficient warning, and possibly providing only the manual install method (now called "something else").

Or if more control is needed then someone should use the alternate CD, and I think Lubuntu will have an alternate soon.

I tested with an old 3.2GB drive with the thought of creating only a / partition and then creating a swap file post-install since I have 2GB of RAM on this machine anyway, but it won't even allow an installation if less than 4.6GB is available.

Really though, having to use the alternate should not be a huge problem, it's just a tweaked version of the Debian installer.

---

### Post by cariboo on 2011-08-15
> **kansasnoob said:**
> Could I possibly talk you into trying an installation just on battery power? I'll bet it'll let you proceed just like not having an internet connection.

I've done that too, along with no network connection. :)

---

### Post by cariboo on 2011-08-15
> **teh603 said:**
> You can sometiems get bcmwl to install automatically? I've never been able to, even with a wired connection. Hell, on 10.04 I had to purge the bcmwl modaliases package and reinstall both it and bcmwl before it'd install.


No I've installed the driver manually from the CD/iso, or use a usb device that is automatically detected and enabled when it is plugged in. I have also used a network cable after the install is finished.

---

### Post by kansasnoob on 2011-08-15
> **cariboo907 said:**
> I've done that too, along with no network connection. :)

Thanks, that verifies what I suspected. Of the three "must haves" only the disc space limitation seems to stop one from proceeding beyond that page of the installer.

A few problems kind of present themselves with the automated installer determining the disc space anyway. Mostly the way in which swap is calculated.

I mean both of my machines have 2GB of RAM and during testing the installer will create anywhere from just over 2GB of swap to as much as 4GB of swap so I suppose if I created a free space of just over the supposedly required 4.6GB it could still possibly create too much swap causing the installation to fail :confused:

I'll try that and see.

---

### Post by ronacc on 2011-08-15
ubiquity will do the installation with no swap if you tell it to and/or it will use any swap already on the system , it doesn't even have to be on the same drive .

---

### Post by kansasnoob on 2011-08-15
> **ronacc said:**
> ubiquity will do the installation with no swap if you tell it to and/or it will use any swap already on the system , it doesn't even have to be on the same drive .

Yes, if you choose the manual install (now called, something else) method. In fact if you have more than one swap partition (I usually have one on each drive so I can remove any given drive w/o harm to what OS's I have on another drive) you actually have to tell the installer not to use certain swap partitions.

But if you use the fully automated defaults the installer will always create a new swap, in fact there's a bug report about even the new "upgrade via live CD" install creating an additional new swap partition :(

---

### Post by ronacc on 2011-08-15
I long ago gave up on anything but manual (something else ) , It bit me in the butt one too may times , and I don't ever let ubiquity format anything even with manual I always partition and format with a standalone gparted disk .My test box has 6 drives who knows how many partitions and right now but variable  2 debian installs sid and squeeze , 1 ubuntu ( gnome-shell ) , 2 lubuntu 32 & 64 bit , opensuse , puppy and sabayon  so you can see why I refuse to trust it to ubiquity any more that the bare minimum .

---

### Post by kansasnoob on 2011-08-15
I did the test I was speaking of and it failed as expected ;)

Since the whole premise of this bug is DE agnostic I used an Ubuntu alpha3 image instead of Lubuntu because I've had trouble installing a screenshot tool in Lubuntu, I suspect because of the transition to gtk3 - or something about dependencies.

Then I created about 4.6GB of free space where you now see sdb8 and sdb9 here:

[ATTACH]200094[/ATTACH]

Now, this also plays into the "using free space w/o warning" bug because as soon as I clicked on continue the installation began and auto-created that new 1.93GB swap leaving only 2.65GB for / which is not enough for Ubuntu ATM :(

So both bugs effect each other to a degree. I just need time to think about how I want to report this and what to suggest as potential remedies.

I'm thinking ATM that the free-space bug needs to really be fixed, preferably by visibly offering to use free-space, and if the default disc space requirement is not met the only installation option following should be manual partitioning.

But I've got a splitting headache (new meds) so it's nap time :D

---

### Post by kansasnoob on 2011-08-15
> **ronacc said:**
> I long ago gave up on anything but manual (something else ) , It bit me in the butt one too may times , and I don't ever let ubiquity format anything even with manual I always partition and format with a standalone gparted disk .My test box has 6 drives who knows how many partitions and right now but variable  2 debian installs sid and squeeze , 1 ubuntu ( gnome-shell ) , 2 lubuntu 32 & 64 bit , opensuse , puppy and sabayon  so you can see why I refuse to trust it to ubiquity any more that the bare minimum .

In deed, that's why I hate that the installer will now just begin the automated installation if it finds enough unallocated space on any system drive. That can include flash drives, media cards, etc :(

I'd seen somewhere that they may begin trying to default to creating a separate /home which would be cool, but I've not seen any recent dev notes so I'm clueless as to what's going on behind the scenes.

But no installation should begin w/o offering the manual partitioning option.

---

### Post by kansasnoob on 2011-08-15
Well, laying down makes my headache worse so I did this:

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/766265/comments/23](https://bugs.launchpad.net/ubuntu-release-notes/+bug/766265/comments/23)

More to follow. I thought of another test case to run.

---

### Post by kansasnoob on 2011-08-15
I found that "adding an unneeded swap partition" bug report so I'm sticking it here for my own use:

[https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507](https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507)

This does effect the Lubuntu specific bug that was merged as an Ubuntu duplicate.

---

### Post by phillw on 2011-08-15
One of iso spinners, who "mended" the disk space bug with a community edition has had a gentle poke on the ribs to see if can do the same for the RAM one. However, as
1) He is real busy in Real Life stuff,
2) We would, as an official release, much rather have this addressed at source instead of having a un-official release kicking around.

Our head of dev, does have an open bug report open over the disk space issue. But, we are going to join the official build system and as previously noted an 'alternate' iso spin is in discussion. I'm hopeful we may have some more input as to how that is done. As there are some skilled people, if all else fails I'm sure a community release would be forthcoming. Not perfect by any stretch of the woods, but there is also a strong belief within Lubuntu that we **must** support the 'older' kit. I have possibly hinted that a community 10.04.3 is possible, there is a draft out but the creator of that is one person & real busy right now. 

I know my oft asked plea for patience may be annoying to some, but I do once again ask that people realise that lubuntu is a really small team. The **must** have, i.e. full Canonical build has to take priority for this release sequence. As I recall one person saying in 9.10 when Grub2 was released.... the x.10 before an LTS is actually a stable beta - just do not tell any one 
:popcorn:

Sorry for the essay. As always when I do an 'AFAIK' note to you good people, I will ask our Head of Dev to have a read and correct any errors.

Once again, thank you all for the interest you have in Lubuntu.

Regards,

Phill.

---

### Post by Catharsis on 2011-08-15
> **kansasnoob said:**
> I do understand that, in fact that's why I was involved in breaking things originally:

[http://ubuntuforums.org/showpost.php?p=11117831&postcount=162](http://ubuntuforums.org/showpost.php?p=11117831&postcount=162)

I believe currently a fresh install of Ubuntu comes in around 3.2GB for / + whatever for swap. Lubuntu is about 2.3GB + swap. Of course some additional space is needed for updates, additional apps, general usage, etc.

And an automated install will typically create a swap anywhere from 1X to 2X the amount of RAM. So my thought was to allow proceeding, but only with sufficient warning, and possibly providing only the manual install method (now called "something else").

Or if more control is needed then someone should use the alternate CD, and I think Lubuntu will have an alternate soon.

I tested with an old 3.2GB drive with the thought of creating only a / partition and then creating a swap file post-install since I have 2GB of RAM on this machine anyway, but it won't even allow an installation if less than 4.6GB is available.

Really though, having to use the alternate should not be a huge problem, it's just a tweaked version of the Debian installer.

Ok, I can see that. I must have missed that bit about the manual install only in the comment. Go for it, sounds like a good idea.

---

### Post by kansasnoob on 2011-08-15
> **phillw said:**
> One of iso spinners, who "mended" the disk space bug with a community edition has had a gentle poke on the ribs to see if can do the same for the RAM one. However, as
1) He is real busy in Real Life stuff,
2) We would, as an official release, much rather have this addressed at source instead of having a un-official release kicking around.

**[COLOR="Red"]Our head of dev, does have an open bug report open over the disk space issue.[/COLOR]** But, we are going to join the official build system and as previously noted an 'alternate' iso spin is in discussion. I'm hopeful we may have some more input as to how that is done. As there are some skilled people, if all else fails I'm sure a community release would be forthcoming. Not perfect by any stretch of the woods, but there is also a strong belief within Lubuntu that we **must** support the 'older' kit. I have possibly hinted that a community 10.04.3 is possible, there is a draft out but the creator of that is one person & real busy right now. 

I know my oft asked plea for patience may be annoying to some, but I do once again ask that people realise that lubuntu is a really small team. The **must** have, i.e. full Canonical build has to take priority for this release sequence. As I recall one person saying in 9.10 when Grub2 was released.... the x.10 before an LTS is actually a stable beta - just do not tell any one 
:popcorn:

Sorry for the essay. As always when I do an 'AFAIK' note to you good people, I will ask our Head of Dev to have a read and correct any errors.

Once again, thank you all for the interest you have in Lubuntu.

Regards,

Phill.

The disc space issue was duped with:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

I don't totally agree with that because Lubuntu generally requires less space than Ubuntu but a lot of it has to do with how swap space is determined by the automated process.

I really am trying hard to get my ducks in a row to deal with this come Beta 1 testing. I do hope we'll have an official alternate CD by then.

Please don't think I'm complaining. Now that Lubuntu is part of the family the Ubuntu devs can and will help.

The best way i've found of getting them to help is by reporting valid bugs during iso-testing. I hope to be one of Lubuntu's "aces-in-the hole" coming out of the chute :)

---

### Post by phillw on 2011-08-15
> **kansasnoob said:**
> The disc space issue was duped with:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

I don't totally agree with that because Lubuntu generally requires less space than Ubuntu but a lot of it has to do with how swap space is determined by the automated process.



Politics I'm not keen on, but the raison d'etre for Lubuntu is a small machine. I am sure it will be resolved. The good people responsible for full ubiquity releases are, I know, liasing with the head of Dev from lubuntu. The rest of us will stay out of it as far is possible. They will not appreciate a flame war, just getting lubuntu to standard (as usual over sized build) is amassive milestone. It would be foolish for anyone, having made people aware of the problem to start having fall outs.

I look forward to the beta builds, do not forget alpha3 was the **first** Lubuntu ever to be built with the Canonical build system. Whilst I am sure we would like faster progress.... be patient. the very 1st trial of lubuntu came out in 9.10, things have come on a lot in very quick time!

If we get a 'on size' iso out with all the up to date things out by beta2, or even if we have to wait for RC - I, for one, will be a very happy bunny. 6 months to fine tune our LTS. That, would be fabulous :D

Regards,

Phill.

---

### Post by kansasnoob on 2011-08-17
Thought I'd give a shout-out to others that may be running mixed DE's ATM. The current updates look like a no-no:

```
[B][COLOR="Red"]libfm-gtk0 will be removed
lubuntu-core will be removed
lubuntu-default-settings will be removed
lubuntu-desktop will be removed
lxde-core will be removed
pcmanfm will be removed[/COLOR][/B]
apport (version 1.21.3-0ubuntu1) will be upgraded to version 1.21.3-0ubuntu3
apport-gtk (version 1.21.3-0ubuntu1) will be upgraded to version 1.21.3-0ubuntu3
apt (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
apt-transport-https (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
apt-utils (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
aptdaemon (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
aptdaemon-data (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
dconf-gsettings-backend (version 0.7.5-3) will be upgraded to version 0.9.0-0ubuntu1
gir1.2-gnomebluetooth-1.0 (version 3.1.3-0ubuntu2) will be upgraded to version 3.1.4-0ubuntu1
gnome-accessibility-themes (version 2.32.1-0ubuntu1) will be upgraded to version 3.1.5-0ubuntu2
gnome-bluetooth (version 3.1.3-0ubuntu2) will be upgraded to version 3.1.4-0ubuntu1
gnome-games-common (version 1:3.1.4-0ubuntu2) will be upgraded to version 1:3.1.5-0ubuntu1
gnome-keyring (version 3.1.1-0ubuntu4) will be upgraded to version 3.1.4-0ubuntu1
gnome-mahjongg (version 1:3.1.4-0ubuntu2) will be upgraded to version 1:3.1.5-0ubuntu1
gnome-media (version 2.91.2-2ubuntu1) will be upgraded to version 2.91.2-2ubuntu2
gnome-sudoku (version 1:3.1.4-0ubuntu2) will be upgraded to version 1:3.1.5-0ubuntu1
gnomine (version 1:3.1.4-0ubuntu2) will be upgraded to version 1:3.1.5-0ubuntu1
gparted (version 0.8.1-1ubuntu2) will be upgraded to version 0.8.1-1ubuntu3
language-selector-common (version 0.45) will be upgraded to version 0.46
language-selector-gnome (version 0.45) will be upgraded to version 0.46
libapt-inst1.3 (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
libapt-pkg4.11 (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
libdconf-dbus-1-0 (version 0.7.5-3) will be upgraded to version 0.9.0-0ubuntu1
libdconf0 (version 0.7.5-3) will be upgraded to version 0.9.0-0ubuntu1
libgcr-3-1 (version 3.1.1-0ubuntu4) will be upgraded to version 3.1.4-0ubuntu1
libgnome-bluetooth8 (version 3.1.3-0ubuntu2) will be upgraded to version 3.1.4-0ubuntu1
libpam-gnome-keyring (version 3.1.1-0ubuntu4) will be upgraded to version 3.1.4-0ubuntu1
mlocate (version 0.23.1-1ubuntu1) will be upgraded to version 0.23.1-1ubuntu2
python-apport (version 1.21.3-0ubuntu1) will be upgraded to version 1.21.3-0ubuntu3
python-aptdaemon (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
python-aptdaemon-gtk (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
python-aptdaemon.gtk3widgets (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
python-aptdaemon.gtkwidgets (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
python-problem-report (version 1.21.3-0ubuntu1) will be upgraded to version 1.21.3-0ubuntu3
software-center (version 4.1.14) will be upgraded to version 4.1.15
synaptic (version 0.75.2ubuntu3) will be upgraded to version 0.75.2ubuntu4
gir1.2-gmenu-3.0 (version 3.1.5-0ubuntu1) will be installed
gstreamer0.10-gconf (version 0.10.30-1ubuntu3) will be installed
libgck-1-0 (version 3.1.4-0ubuntu1) will be installed
libgnome-menu-3-0 (version 3.1.5-0ubuntu1) will be installed
libp11-kit0 (version 0.3-0ubuntu1) will be installed

```

That may resolve itself, I dunno :)

**************Update to the above*********************

I booted into a pure Lubuntu Oneiric install and the only thing messed up as far as updates with it is that a pcmanfm update is held back, so I'm guessing it's just a matter of waiting for some dependencies to resolve.

---

### Post by Catharsis on 2011-08-17
> **kansasnoob said:**
> Thought I'd give a shout-out to others that may be running mixed DE's ATM. The current updates look like a no-no:

```
[B][COLOR="Red"]libfm-gtk0 will be removed
lubuntu-core will be removed
lubuntu-default-settings will be removed
lubuntu-desktop will be removed
lxde-core will be removed
pcmanfm will be removed[/COLOR][/B]
apport (version 1.21.3-0ubuntu1) will be upgraded to version 1.21.3-0ubuntu3
apport-gtk (version 1.21.3-0ubuntu1) will be upgraded to version 1.21.3-0ubuntu3
apt (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
apt-transport-https (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
apt-utils (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
aptdaemon (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
aptdaemon-data (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
dconf-gsettings-backend (version 0.7.5-3) will be upgraded to version 0.9.0-0ubuntu1
gir1.2-gnomebluetooth-1.0 (version 3.1.3-0ubuntu2) will be upgraded to version 3.1.4-0ubuntu1
gnome-accessibility-themes (version 2.32.1-0ubuntu1) will be upgraded to version 3.1.5-0ubuntu2
gnome-bluetooth (version 3.1.3-0ubuntu2) will be upgraded to version 3.1.4-0ubuntu1
gnome-games-common (version 1:3.1.4-0ubuntu2) will be upgraded to version 1:3.1.5-0ubuntu1
gnome-keyring (version 3.1.1-0ubuntu4) will be upgraded to version 3.1.4-0ubuntu1
gnome-mahjongg (version 1:3.1.4-0ubuntu2) will be upgraded to version 1:3.1.5-0ubuntu1
gnome-media (version 2.91.2-2ubuntu1) will be upgraded to version 2.91.2-2ubuntu2
gnome-sudoku (version 1:3.1.4-0ubuntu2) will be upgraded to version 1:3.1.5-0ubuntu1
gnomine (version 1:3.1.4-0ubuntu2) will be upgraded to version 1:3.1.5-0ubuntu1
gparted (version 0.8.1-1ubuntu2) will be upgraded to version 0.8.1-1ubuntu3
language-selector-common (version 0.45) will be upgraded to version 0.46
language-selector-gnome (version 0.45) will be upgraded to version 0.46
libapt-inst1.3 (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
libapt-pkg4.11 (version 0.8.16~exp5ubuntu5) will be upgraded to version 0.8.16~exp5ubuntu6
libdconf-dbus-1-0 (version 0.7.5-3) will be upgraded to version 0.9.0-0ubuntu1
libdconf0 (version 0.7.5-3) will be upgraded to version 0.9.0-0ubuntu1
libgcr-3-1 (version 3.1.1-0ubuntu4) will be upgraded to version 3.1.4-0ubuntu1
libgnome-bluetooth8 (version 3.1.3-0ubuntu2) will be upgraded to version 3.1.4-0ubuntu1
libpam-gnome-keyring (version 3.1.1-0ubuntu4) will be upgraded to version 3.1.4-0ubuntu1
mlocate (version 0.23.1-1ubuntu1) will be upgraded to version 0.23.1-1ubuntu2
python-apport (version 1.21.3-0ubuntu1) will be upgraded to version 1.21.3-0ubuntu3
python-aptdaemon (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
python-aptdaemon-gtk (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
python-aptdaemon.gtk3widgets (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
python-aptdaemon.gtkwidgets (version 0.43+bzr669-0ubuntu1) will be upgraded to version 0.43+bzr670-0ubuntu1
python-problem-report (version 1.21.3-0ubuntu1) will be upgraded to version 1.21.3-0ubuntu3
software-center (version 4.1.14) will be upgraded to version 4.1.15
synaptic (version 0.75.2ubuntu3) will be upgraded to version 0.75.2ubuntu4
gir1.2-gmenu-3.0 (version 3.1.5-0ubuntu1) will be installed
gstreamer0.10-gconf (version 0.10.30-1ubuntu3) will be installed
libgck-1-0 (version 3.1.4-0ubuntu1) will be installed
libgnome-menu-3-0 (version 3.1.5-0ubuntu1) will be installed
libp11-kit0 (version 0.3-0ubuntu1) will be installed

```

That may resolve itself, I dunno :)

**************Update to the above*********************

I booted into a pure Lubuntu Oneiric install and the only thing messed up as far as updates with it is that a pcmanfm update is held back, so I'm guessing it's just a matter of waiting for some dependencies to resolve.


For some reason the PCManFM upgrade doesn't like dist-upgrade
```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  pcmanfm
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded
```
```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libfm-gtk0 lubuntu-core lubuntu-default-settings lxde-core pcmanfm
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 2,019 kB disk space will be freed.
```
```
$ sudo apt-get install pcmanfm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libfm-data libfm-gtk-data libfm-gtk1 libfm1
The following packages will be REMOVED:
  libfm-gtk0 libfm0
The following NEW packages will be installed:
  libfm-data libfm-gtk-data libfm-gtk1 libfm1
The following packages will be upgraded:
  pcmanfm
1 upgraded, 4 newly installed, 2 to remove and 0 not upgraded.
Need to get 560 kB of archives.
After this operation, 295 kB of additional disk space will be used.
```

Installing it manually with "apt-get install pcmanfm" works fine, installs and runs nicely here.

I've opened a bug report for it [here](launchpad.net/bugs/828287); if you're also affected please add yourself to the report and confirm it.

---

### Post by kansasnoob on 2011-08-17
> **Catharsis said:**
> For some reason the PCManFM upgrade doesn't like dist-upgrade
```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  pcmanfm
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded
```
```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libfm-gtk0 lubuntu-core lubuntu-default-settings lxde-core pcmanfm
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 2,019 kB disk space will be freed.
```
```
$ sudo apt-get install pcmanfm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libfm-data libfm-gtk-data libfm-gtk1 libfm1
The following packages will be REMOVED:
  libfm-gtk0 libfm0
The following NEW packages will be installed:
  libfm-data libfm-gtk-data libfm-gtk1 libfm1
The following packages will be upgraded:
  pcmanfm
1 upgraded, 4 newly installed, 2 to remove and 0 not upgraded.
Need to get 560 kB of archives.
After this operation, 295 kB of additional disk space will be used.
```

Installing it manually with "apt-get install pcmanfm" works fine, installs and runs nicely here.

I've opened a bug report for it [here](launchpad.net/bugs/828287); if you're also affected please add yourself to the report and confirm it.

I'm super cooked ATM but I'll take a closer look tomorrow :D

Thanks for sharing the info.

Totally OT but I gained a lot today towards getting my kitchen put back together, which means I'll someday be able to get back to doing what I prefer doing ............ playing here ;)

---

### Post by kansasnoob on 2011-08-17
Before laying down I decided to just try this:

```
lance@lance-desktop:~$ sudo **[COLOR="Red"]apt-get install --reinstall pcmanfm[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmtp8 xsltproc libegl1-mesa libntfs10 libegl1-mesa-drivers libevent-1.4-2
  libunity4 linux-headers-3.0-3 linux-headers-3.0.0-6-generic
  libdbusmenu-glib3 libindicate-gtk2 libgcr-3-0 libxcb-xfixes0 python-gconf
  libdbusmenu-gtk3-3 linux-headers-3.0-3-generic libgbm1 libgck0 python-webkit
  libdbusmenu-gtk3 gnome-doc-utils xdiagnose gir1.2-appindicator-0.1 tcl
  linux-headers-3.0.0-6 libnl1 liborbit2 libopenvg1-mesa intel-gpu-tools
  libntfs-3g80
Use 'apt-get autoremove' to remove them.
[B][COLOR="Red"]The following extra packages will be installed:
  libfm-data libfm-gtk-data libfm-gtk1 libfm1
The following packages will be REMOVED:
  libfm-gtk0 libfm0
The following NEW packages will be installed:
  libfm-data libfm-gtk-data libfm-gtk1 libfm1
The following packages will be upgraded:
  pcmanfm[/COLOR][/B]
1 upgraded, 4 newly installed, 2 to remove and 0 not upgraded.
Need to get 560 kB of archives.
After this operation, 139 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe pcmanfm i386 0.9.9-0ubuntu1 [207 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libfm-data all 0.1.16-0ubuntu1 [139 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libfm1 i386 0.1.16-0ubuntu1 [76.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libfm-gtk-data i386 0.1.16-0ubuntu1 [16.9 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libfm-gtk1 i386 0.1.16-0ubuntu1 [121 kB]
Fetched 560 kB in 3s (177 kB/s)     
(Reading database ... 180738 files and directories currently installed.)
Preparing to replace pcmanfm 0.9.8+git-6240436419-1~bzr459+p18~oneiric1 (using .../pcmanfm_0.9.9-0ubuntu1_i386.deb) ...
Unpacking replacement pcmanfm ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for menu ...
(Reading database ... 180739 files and directories currently installed.)
Removing libfm-gtk0 ...
Removing libfm0 ...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for shared-mime-info ...
Selecting previously deselected package libfm-data.
(Reading database ... 180658 files and directories currently installed.)
Unpacking libfm-data (from .../libfm-data_0.1.16-0ubuntu1_all.deb) ...
Selecting previously deselected package libfm1.
Unpacking libfm1 (from .../libfm1_0.1.16-0ubuntu1_i386.deb) ...
Selecting previously deselected package libfm-gtk-data.
Unpacking libfm-gtk-data (from .../libfm-gtk-data_0.1.16-0ubuntu1_i386.deb) ...
Selecting previously deselected package libfm-gtk1.
Unpacking libfm-gtk1 (from .../libfm-gtk1_0.1.16-0ubuntu1_i386.deb) ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Setting up libfm-data (0.1.16-0ubuntu1) ...
Setting up libfm1 (0.1.16-0ubuntu1) ...
Setting up libfm-gtk-data (0.1.16-0ubuntu1) ...
Setting up libfm-gtk1 (0.1.16-0ubuntu1) ...
Setting up pcmanfm (0.9.9-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...

```

---

### Post by ronacc on 2011-08-17
after installing the upgrades with synaptic you can also use synaptic to reinstall pcmanfm .

---

### Post by Sworddragon on 2011-08-18
pcmanfm was very buggy before the update but now it's more worse. For example pcmanfm crashes if you are in a directory and delete this directory in another tab. Or mounted directories are showing me outdated entries and on pressing F5 pcmanfm crashes too (only the first time but a reopening will show the corect entries then). Holding F5 for a few seconds in a directory will cause a duplication of all directories (logging out will fix this). Sometimes on a new login then the desktop isn't visible too. But a left mouseclick will fix this. I have opened yesterday 7 new tickets on sourceforge. But I have even opened much more tickets before (there are still much other crashes. File operations on big directories (a few 10.000 files) are very slow too).

Can somebody else confirm some of these problems?

---

### Post by kansasnoob on 2011-08-18
> **Sworddragon said:**
> pcmanfm was very buggy before the update but now it's more worse. For example pcmanfm crashes if you are in a directory and delete this directory in another tab. Or mounted directories are showing me outdated entries and on pressing F5 pcmanfm crashes too (only the first time but a reopening will show the corect entries then). Holding F5 for a few seconds in a directory will cause a duplication of all directories (logging out will fix this). Sometimes on a new login then the desktop isn't visible too. But a left mouseclick will fix this. I have opened yesterday 7 new tickets on sourceforge. But I have even opened much more tickets before (there are still much other crashes. File operations on big directories (a few 10.000 files) are very slow too).

Can somebody else confirm some of these problems?

I'll try to reproduce some of these problems, probably this evening, but could you post any bug report numbers?

Or any specific details? We need to let Pcman know so we can try to get them addressed. I'm quite new to LXDE and Lubuntu so I'm still dealing with a learning curve.

---

### Post by Sworddragon on 2011-08-18
[http://sourceforge.net/tracker/?func=detail&aid=3393358&group_id=156956&atid=801864](http://sourceforge.net/tracker/?func=detail&aid=3393358&group_id=156956&atid=801864)
[http://sourceforge.net/tracker/?func=detail&aid=3393447&group_id=156956&atid=801864](http://sourceforge.net/tracker/?func=detail&aid=3393447&group_id=156956&atid=801864)
[http://sourceforge.net/tracker/?func=detail&aid=3393472&group_id=156956&atid=801864](http://sourceforge.net/tracker/?func=detail&aid=3393472&group_id=156956&atid=801864)
[http://sourceforge.net/tracker/?func=detail&aid=3393477&group_id=156956&atid=801864](http://sourceforge.net/tracker/?func=detail&aid=3393477&group_id=156956&atid=801864)

Just a small taste of the bugs :)

But at least a few of my reported bugs are already fixed. And some other of them are accepted. I will stay on pcmanfm and wait for the future updates.

---

### Post by kansasnoob on 2011-08-18
Most of what you're talking about there is far beyond my tech level :(

Unless phillw has another idea by tomorrow I'll try commenting about this at the mailing list.

BTW I do have a sourceforge account but I've only dealt with grub2 there :(

---

### Post by Catharsis on 2011-08-19
> **Sworddragon said:**
> pcmanfm was very buggy before the update but now it's more worse. For example pcmanfm crashes if you are in a directory and delete this directory in another tab. Or mounted directories are showing me outdated entries and on pressing F5 pcmanfm crashes too (only the first time but a reopening will show the corect entries then). Holding F5 for a few seconds in a directory will cause a duplication of all directories (logging out will fix this). Sometimes on a new login then the desktop isn't visible too. But a left mouseclick will fix this. I have opened yesterday 7 new tickets on sourceforge. But I have even opened much more tickets before (there are still much other crashes. File operations on big directories (a few 10.000 files) are very slow too).

Can somebody else confirm some of these problems?

Yeah, I confirmed all of them earlier I think. Are you supposed to mark sourceforge bugs as confirmed? How do you triage these things? I actually ran into another bug resulting in a crash while I was confirming some of yours :) I just ran out of time to deal with it, haha.

---

### Post by phillw on 2011-08-19
A 64-bit alternate has crept into the daily build system... [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)  As it is my birthday and I am going on a a fantastic trip on a steam train I trust you all to give it a try :)

Regards,

Phill.

---

### Post by Sworddragon on 2011-08-20
> **Catharsis said:**
> Yeah, I confirmed all of them earlier I think. Are you supposed to mark sourceforge bugs as confirmed? How do you triage these things? I actually ran into another bug resulting in a crash while I was confirming some of yours :) I just ran out of time to deal with it, haha.

I can set all attributes of my own tickets but there is no confirmation flag. There are even some gtk related problems like changes in / are not updated automatic and the size output is broken (some of my folders are reported with ~147,7 TB and such things). But I have not much hope that gtk related problems are fixed in the near future (maybe in 1 year or more).

---

### Post by nymark1 on 2011-08-20
Hi
I am trying to download daily builds of Lubuntu 11.10. But I keep getting this error message:

**" Forbidden**

    You don't have permission to access /lubuntu/daily-live/current/ on this server.
     Apache/2.2.14 (Ubuntu) Server at cdimage.ubuntu.com Port 80 "

Can anyone tell me what this means. ? And how do I solve this problem?

---

### Post by kansasnoob on 2011-08-20
> **phillw said:**
> A 64-bit alternate has crept into the daily build system... [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)  As it is my birthday and I am going on a a fantastic trip on a steam train I trust you all to give it a try :)

Regards,

Phill.

I think someone needs to correct something about the link because "lubuntu" daily build is no longer search-able and the link you provided is for Ubuntu alternate :confused:

---

### Post by ronacc on 2011-08-20
look here [http://cdimage.ubuntu.com/lubuntu/daily-live/](http://cdimage.ubuntu.com/lubuntu/daily-live/)  unfortunately there don't seem to actually be any images available there :confused: and at  [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/) only the alternate is available .

---

### Post by kerry_s on 2011-08-20
looks like all the iso's been pulled. see pic
bet there just in the process of building

you can still get alpha3 here:
[http://cdimage.ubuntu.com/lubuntu/releases/11.10/alpha-3/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/alpha-3/)

---

### Post by kansasnoob on 2011-08-20
> **ronacc said:**
> look here [http://cdimage.ubuntu.com/lubuntu/daily-live/](http://cdimage.ubuntu.com/lubuntu/daily-live/)  unfortunately there don't seem to actually be any images available there :confused: and at  [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/) only the alternate is available .

Probably just a temp breakage thing :D

I'm so tired ATM I'd break something if I tried something new :lolflag:

---

### Post by ranch hand on 2011-08-20
> **phillw said:**
> A 64-bit alternate has crept into the daily build system... [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)  As it is my birthday and I am going on a a fantastic trip on a steam train I trust you all to give it a try :)

Regards,

Phill.
Happy Birthday.

Steam Trains are really neat.  My dad and I used to go on them every chance we had.  Just before I started school we saw the last working freight (steam) train come and get a load of grain from the elevator in Laingsburg Michigan (3 miles from the farm where I grew up).  I may have been 6 at the time but it made me a fan for life.

---

### Post by nymark1 on 2011-08-21
> **kerry_s said:**
> looks like all the iso's been pulled. see pic
bet there just in the process of building

you can still get alpha3 here:
[http://cdimage.ubuntu.com/lubuntu/releases/11.10/alpha-3/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/alpha-3/)
Thanks :-) 
I'll mark the thread as solved.

---

### Post by kansasnoob on 2011-08-21
It's not really helpful ATM because daily builds of Lubuntu seem borked, as you noted, but we've been discussing Lubuntu dev here:

[http://ubuntuforums.org/showthread.php?t=1774388](http://ubuntuforums.org/showthread.php?t=1774388)

You'll likely want to skip to the last 2 or 3 pages of that thread for current info. Welcome aboard :)

---

### Post by kansasnoob on 2011-08-21
It appears I'm not alone:

[http://ubuntuforums.org/showthread.php?t=1829555](http://ubuntuforums.org/showthread.php?t=1829555)

I already PM'ed nymark1 with a welcome to this thread :)

---

### Post by cariboo on 2011-08-21
MOved to Oneiric testing and discussion, before someone complains. :)

---

### Post by kansasnoob on 2011-08-21
> **cariboo907 said:**
> MOved to Oneiric testing and discussion, before someone complains. :)

As always, thanks for all you do :)

---

### Post by phillw on 2011-08-22
They are on the hunt, to my minimal knowledge, and to their great knowledge they appear to be honing in on the problem and it does not seem, to me, to be a massive problem :)

Seems something that is needed for the automatic daily build was not where it was expected by the program that does the daily builds, and / or  something else needs the latest version.

Regards,

Phill.

---

### Post by ronacc on 2011-08-22
when changing to a new build system some teething problems are to be expected .

---

### Post by ranch hand on 2011-08-22
> **ronacc said:**
> when changing to a new build system some teething problems are to be expected .
They surely are.

---

### Post by cariboo on 2011-08-22
Merged two threads by request.

---

### Post by phillw on 2011-08-25
The Daily Live builds succeeded.

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

The i386 even fits on a cd :P

You *should* be able to install from the live cd, so for those impatient to do a bit of testing, go and hug one!

Regards,

Phill.

---

### Post by phillw on 2011-08-26
With the successful build of the alternate images, I've updated [Testing](https://wiki.ubuntu.com/Lubuntu/Testing) and will strive to keep it up to date whilst we await the 'standard' iso builds to come back on :)

Regards,

Phill.

---

### Post by ronacc on 2011-08-26
how do I create a desktop launcher in Lubuntu ?
rt click on dt only offers to create a folder or file .

---

### Post by phillw on 2011-08-27
> **ronacc said:**
> how do I create a desktop launcher in Lubuntu ?
rt click on dt only offers to create a folder or file .

From one of those clever people via Mailing List...
> 

You could use lxshortcut.

In terminal, you go to your desktop folder. Run this command: lxshortcut -o application_name.desktop (Of course you will want to change "application_name" to something else).

A dialog will appear and you can choose the name or the icon, set the path to the file...

I hope we will have a right click function on desktop like in Xubuntu soon.

Regards,
TR&#7846;N Duy Hùng

I'll add it to the FAQ, Leszek also wrote a little patch that adds 'shortcut' to the right-click on the dt. The devs are figuring out where best to integrate it. If you email me, I'll forward the email on.

Regards,

Phill.

---

### Post by ronacc on 2011-08-27
thanks to both of you .

---

### Post by VinDSL on 2011-08-28
> **kansasnoob said:**
> No Lubuntu forum yet, we just have to use these forums. You can set the "lubuntu" prefix on threads in the main support categories.
Is this still THE place?!?!?  No Lubuntu Forum, yet?

I'll tell ya what...

I've been playing with Lubuntu, in my spare time, for a week or so - running off a lousy USB stick, and I'm thoroughly impressed!

First thing I do is install Adobe Flash.  Then, I spend 5 minutes installing upper n' lower panels, adding n' removing items, moving them where I want 'em, change the theme in Chromium, and I'm good to go!

This is like discovering Linux all over again!  LoL!  :D

Here's a quick screenie...


[INDENT][IMG]http://vindsl.com/images/2011-08-28-045508_1280x1024_scrot.png[/IMG][/INDENT]


Not too shabby for 5 minutes work, and a $6 WalMart USB card.

Heh!  Lubuntu is going to be a major contender - I can see that already.

Can't believe they don't have their own forum yet... or do they?  ;)

---

### Post by phillw on 2011-08-28
> **VinDSL said:**
> Is this still THE place?!?!?  No Lubuntu Forum, yet? ....
Can't believe they don't have their own forum yet... or do they?  ;)

All the *buntu family live on here, as previously noted simply use the lubuntu tag :)

Whilst not a forum, there is [http://lubuntu.net/](http://lubuntu.net/) which is a Drupal based site and work is ongoing to link it more closely to the wiki areas and work out what information should be where in order that there is no duplication and both are bang up to date. As you may not know from the wiki area, there is also #lubuntu-offtopic on freenode where we hang out in a more relaxed mode than on the official IRC support channel at #lubuntu.

Glad to hear you're enjoying lubuntu :P

Regards,

Phill.

---

### Post by VinDSL on 2011-08-29
> **phillw said:**
> Glad to hear you're enjoying lubuntu :P
Capital Razz smiley, eh?  LoL!  :D

Would you know if all Lubuntu .iso's are hybrid CD/USB images now?

I'd like to try different versions, but don't feel like fooling around with USB boot creators.

---

### Post by phillw on 2011-08-29
> **VinDSL said:**
> Capital Razz smiley, eh?  LoL!  :D

Would you know if all Lubuntu .iso's are hybrid CD/USB images now?

I'd like to try different versions, but don't feel like fooling around with USB boot creators.

AFAIK, you need to use the usb creator, as it generates the casper stuff you need for persistence.

Regards,

Phill.

---

### Post by phillw on 2011-08-29
A glitch has been found in the daily builds for Lubuntu, it is using an outdated Ubiquity version. The Beta looks like being delayed for about 24 - 48 hours. As we all know, we'd rather hold back for a little while and release a decent mile-stone release on the release cycle than something bad. This I learned during ubuntu testing. 

Sadly, there are now warnings on both LiveCD and Alternate. As some of these issues affect all of the family, please be patient with those sorting them out.

I repeat, the one area I can keep up to date by touching base with people is [Testing](https://wiki.ubuntu.com/Lubuntu/Testing). The qa guys & gals along with those involved in iso generation and the people dealing with 'critical' do out standing work. On this forum area,we know that... Just make sure others do!
:guitar:

Regards,

Phill.

---

### Post by VinDSL on 2011-08-29
> **phillw said:**
> AFAIK, you need to use the usb creator, as it generates the casper stuff you need for persistence.
Okay, thanks!

I guess I've been lucky.  I've been zsync'ing the Lubu .iso's and doing a diskdump (dd) to a 4GB USB stick.  Simple pimple!

I've only had one failure, but it might have been a bad download.  All the rest have worked fine.

Matter of fact, I'm running he latest daily build right now, off a thumbdrive.

Whatever works, eh what?  ;)

---

### Post by kansasnoob on 2011-08-30
> **phillw said:**
> A glitch has been found in the daily builds for Lubuntu, it is using an outdated Ubiquity version. The Beta looks like being delayed for about 24 - 48 hours. As we all know, we'd rather hold back for a little while and release a decent mile-stone release on the release cycle than something bad. This I learned during ubuntu testing. 

Sadly, there are now warnings on both LiveCD and Alternate. As some of these issues affect all of the family, please be patient with those sorting them out.

I repeat, the one area I can keep up to date by touching base with people is [Testing](https://wiki.ubuntu.com/Lubuntu/Testing). The qa guys & gals along with those involved in iso generation and the people dealing with 'critical' do out standing work. On this forum area,we know that... Just make sure others do!
:guitar:

Regards,

Phill.

The first "official" iso-testing images are just now being completed, in fact the Ubuntu live iso's are complete, but the Lubuntu images are still rebuilding.

I think what happened was that a few people got impatient and starting reporting to the iso-tracker prematurely. This led me to believe that I was not receiving proper notifications, but that was not the case.

I think we'll very likely be just fine, and on time, since Beta 1 is not scheduled for release until Sept 1st. That gives us well over 48 hours to squash any show-stopper bugs :)

I'll be spread pretty thin because I need to test both Ubuntu and Lubuntu images this time around in order to follow up on bugs in Ubuntu that I feel a responsibility to follow up on.

---

### Post by kansasnoob on 2011-08-30
Official desktop images here for i386:

[http://iso.qa.ubuntu.com/qatracker/info/6370](http://iso.qa.ubuntu.com/qatracker/info/6370)

Here for amd64:

[http://iso.qa.ubuntu.com/qatracker/info/6369](http://iso.qa.ubuntu.com/qatracker/info/6369)

NOTE: Those are only "testing" images, NOT the Beta 1 images!

The link for the alternate images is still borked but I'm just beginning a test with the 20110830 anyway ;)

---

### Post by VinDSL on 2011-08-30
> **kansasnoob said:**
> Official desktop images here for i386:

[http://iso.qa.ubuntu.com/qatracker/info/6370](http://iso.qa.ubuntu.com/qatracker/info/6370)
Thanks!

Downloading...  ;)

Nice touch - putting the zsync link on there!

---

### Post by VinDSL on 2011-08-30
USB image built and works fine!

Here's the command I'm using, if anyone is interested:
```

$ sudo dd if=oneiric-desktop-i386.iso of=/dev/sdb oflag=direct bs=1M

```

No pesky error dialog when the desktop loads, on this version.  Yeah!

Running perfect, actually...  :)

Good job!

---

### Post by kansasnoob on 2011-08-30
Sharing a quick laugh while burning the i386 live:

I completed an alternate install and reported the failure:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/835961/comments/6](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/835961/comments/6)

When I went back to it to reboot from cli I first typed:

eboot

Next I typed:

rebooty

Maybe it's time for a break :lolflag:

---

### Post by kansasnoob on 2011-08-31
I think the live images look pretty good, not perfect, but hopefully iso-testing brought focus to these bugs:

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/837470](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/837470)

[https://bugs.launchpad.net/ubuntu/+source/libappindicator/+bug/820080](https://bugs.launchpad.net/ubuntu/+source/libappindicator/+bug/820080)

[https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/838106](https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/838106)

I can't reproduce the first bug, but I really don't use pcmanfm in that manner :)

The second one effects other DE's as well so I'm sure it'll get some work prior to Beta 2.

The third is just a reminder for the release team to add a release note.

*********************************************

Now, the alternate image is being difficult, but Colin Watson is working on it from the development end and he's started asking me for info on the testing end ........... so I have high hopes :D

**********************************************

There will of course be no official upgrade path for Lubuntu Natty -> Lubuntu Oneiric because Lubuntu Natty was not "official".

**********************************************

Also no official Lubuntu Wubi testing so I'm a bit unsure about that, but I cross-tested with Ubuntu and found a minor glitch:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/838040](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/838040)

************************************************

Ultimately, for being the new kid on the block, I think we look pretty good :guitar:

---

### Post by phillw on 2011-08-31
> **kansasnoob said:**
> I think the live images look pretty good, not perfect, but hopefully iso-testing brought focus to these bugs:
**********************************************

There will of course be no official upgrade path for Lubuntu Natty -> Lubuntu Oneiric because Lubuntu Natty was not "official".

**********************************************


It did work from 10.10 to 11.04, using the update system - If it does not work thjis time, it may need a home grown one. Else we could do something that many have been screaming for for years and actually tell people to make a seperate /home partition :)

> 

Also no official Lubuntu Wubi testing so I'm a bit unsure about that, but I cross-tested with Ubuntu and found a minor glitch:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/838040](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/838040)

************************************************


In Lubuntu's most basic spec of computer... you would struggle to run Windows, never mind a 'Virtual Machine'. From my asking, until Lubuntu is 100% adopted the Wubi people seem dis-interested. I'm not going to rake through old emails, but they were the only people to turn me down when I asked for help as we where heading for 'official'.

> 
Ultimately, for being the new kid on the block, I think we look pretty good :guitar:

Heck, we're over 3 years old... in some countries they get married at that age :P 

thanks for the help, and also do as the Boss said & put yourself onto the who we are section. Once that is done, I'll nag the team to get the ability to alter the clock font and size sorted out. But it will be 12.04 testing for that; however I will ensure it is done.

Regards,

Phill.

---

### Post by kansasnoob on 2011-09-01
> put yourself onto the who we are section

I think I missed that :(

I'll pester you in a couple of days about how and where to do that.

Good to know about the Wubi thing. If it's going to stay that way then ubiquity should be tweaked for Lubuntu so it doesn't offer the option to install inside windows.

I'm going to repeat a Wubi test from ubiquity with Ubuntu yet tonight, but beginning with 12.04 I'll end all of my subscriptions to Ubuntu iso-testing and do only Lubuntu.

I actually enjoy iso-testing but right now I'm subscribed to too many tests. I did already reduce the Ubuntu side testing.

I played a bit this AM with adding lubuntu-core or lubuntu-desktop to Ubuntu and I really think it's just best to recommend fresh installs of Lubuntu. Too much clutter otherwise ;)

---

### Post by VinDSL on 2011-09-01
> **phillw said:**
> I'll nag the team to get the ability to alter the clock font and size sorted out. But it will be 12.04 testing for that; however I will ensure it is done.[...]
I was going to mention that, but I didn't want to appear trivial.

Sure, the clock font and size are... um... wanting, but...

The 24-hour time is what bothers me most.  Am I missing a button somewhere?

IMO, it's the only glaring flaw in Lubu...

---

### Post by kansasnoob on 2011-09-01
> **VinDSL said:**
> I was going to mention that, but I didn't want to appear trivial.

Sure, the clock font and size are... um... wanting, but...

The 24-hour time is what bothers me most.  Am I missing a button somewhere?

IMO, it's the only glaring flaw in Lubu...

I love trivial :lolflag:

Seriously, it's a long, long story, but since the design team got their hands on ubiquity (the live-installer) I've been a horrible nit-picker :D

I'm sure the clock can either be fixed or replaced. I'd also like to see the computer temp monitor fixed, or be able to use a load/usage monitor in lxpanel.

I know we need to keep things light, but it should be possible to add as much as a user wants.

I haven't tried conky at all but I wonder if it's possible to have something like that downsized to panel size, place it in the lower right hand corner, keep it "always on top", and then shrink the panel?

Sounds stupid I know. It'd probably be easier to just fix the lxpanel stuff. When I have time I need to play with the Xfce panel more.

I loved gnome-panel version 2.

---

### Post by phillw on 2011-09-01
I did a help file for formatting the clock a while ago, have a read of it (apart from the different formats, the only other thing I can suggest to make it clearer for you is to select 'bold' until the devs have a chance to play with the settings).

[https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock](https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock)

Regards,

Phill.

---

### Post by andrewabc on 2011-09-01
[http://cdimage.ubuntu.com/lubuntu/releases/oneiric/beta-1/](http://cdimage.ubuntu.com/lubuntu/releases/oneiric/beta-1/)

This beta1 release(desktop .iso is august 30, but torrents and alternate sept 1)?
See no announcement yet on lubuntu mailing list, and not sure if lubuntu does announcements like normal ubuntu (aka dont' bother downloading until official in case it gets rebuilt).

EDIT:
Downloaded the .iso, will test later.

---

### Post by VinDSL on 2011-09-01
> **phillw said:**
> I did a help file for formatting the clock a while ago, have a read of it[...]
Doh!  Just like Conky...  :D

```

%l:%M%p

```

That's what I was looking for.  Thanks!

---

### Post by andrewabc on 2011-09-01
Sad to report still no wireless on my nettop (liveusb of beta1). Wireless worked fine on 11.04.

Missing network icon on bottom right corner. Right click on "missing icon" icon says wireless and wired are enabled. No idea what to do. Under 11.04 it would say wireless network available and I'd just click on bottom right icon and select wireless connection (my router) and it would work fine.

---

### Post by phillw on 2011-09-02
The delay on the beta's was caused by two seperate bugs that left both normal and alternate builds unusuable. Both these critical bugs have been fixed and beta iso's successfully generated.

As for the announcement, it was ready but on hold pending us checking the new iso's worked!

> 

Hi,

Following the announce for Ubuntu, Lubuntu Beta 1 is also available for
testing. You can find it on
[http://cdimage.ubuntu.com/lubuntu/releases/oneiric/beta-1/](http://cdimage.ubuntu.com/lubuntu/releases/oneiric/beta-1/) 

A quick summary of important changes since Alpha 3 :
 * Alternate ISO are now available.
 * Keeping LXDM for login manager.
 * New theme made by Raphael.

Know issues :
 * Include apt-xapian-index : [http://pad.lv/798437](http://pad.lv/798437) 
 * Installer require 4.6 Gb of free space : [http://pad.lv/819538](http://pad.lv/819538) 
 * Fallback icons of libindicator not working : [http://pad.lv/819617](http://pad.lv/819617) 
 * Crash on startup for notification-daemon : [http://pad.lv/838383](http://pad.lv/838383) 
 * Ubiquity broken icon switcher : [http://pad.lv/830898](http://pad.lv/830898) 
 * Update desktop on persistent mode : [http://pad.lv/837470](http://pad.lv/837470) 

Happy testing :)

Regards,
Julien Lavergne


For the most up to date stuff whilst testing the beta iso's head over to [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) It's nice to see us there with the rest of the family at last :)

Regards,

Phill.

---

### Post by kansasnoob on 2011-09-02
> **andrewabc said:**
> Sad to report still no wireless on my nettop (liveusb of beta1). Wireless worked fine on 11.04.

Missing network icon on bottom right corner. Right click on "missing icon" icon says wireless and wired are enabled. No idea what to do. Under 11.04 it would say wireless network available and I'd just click on bottom right icon and select wireless connection (my router) and it would work fine.

You might want to see if it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/819617](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/819617)

I have the broken icon but my wired network still works.

---

### Post by kansasnoob on 2011-09-02
> **phillw said:**
> The delay on the beta's was caused by two seperate bugs that left both normal and alternate builds unusuable. Both these critical bugs have been fixed and beta iso's successfully generated.

As for the announcement, it was ready but on hold pending us checking the new iso's worked!



For the most up to date stuff whilst testing the beta iso's head over to [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) It's nice to see us there with the rest of the family at last :)

Regards,

Phill.

I think that bug about disc space required is fixed. The live CD now asks for 3.9 GB :)

I'm trying to sort out a couple of other issues, basically how to respond to various bug reports that I know are valid even though I'm told they're not.

And what still seems to be a partly broken software sources list when installing from the alternate CD.

Not much time between now and Beta 2 so I must remain busy :D

A lot of this means installing both Ubuntu and Lubuntu repeated times with the same version of either the debian-installer or ubiquity, so it gets really time consuming and quite often confusing.

---

### Post by phillw on 2011-09-02
> **kansasnoob said:**
> .....
A lot of this means installing both Ubuntu and Lubuntu repeated times with the same version of either the debian-installer or ubiquity, so it gets really time consuming and quite often confusing.....

Thanks for all you do, I'm about to mention on the ML as to why I have been a little pre-occupied. Once I have every thing in place, I can concentrate back on Lubuntu. As ever, as I was awaiting a set of iso's to be re-spun and launched, a new comer to Lubuntu jumped on them and got them through the QA tests.... It is times like this I think back to how fortunate we have been and are. By the time I had dinner and downloaded one - he had validated both alt installs. 
:popcorn:

Regards, 

Phill.

P.S. parents are away for w/end - I'm on dog-sitting duty. 2 X Border Collies = lots of walks!

---

### Post by phillw on 2011-09-02
Shhs, don't tell anyone :P

It has really just arrived in my in tray...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/819617](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/819617)

Please update to it and check it works for you. (Me? I just love ** fix released **).

But, seriously, if this does / does not fix it, please let us know via bug reporting.

Regards,

Phill.

---

### Post by andrewabc on 2011-09-03
> **phillw said:**
> Shhs, don't tell anyone :P

It has really just arrived in my in tray...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/819617](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/819617)

Please update to it and check it works for you. (Me? I just love ** fix released **).

But, seriously, if this does / does not fix it, please let us know via bug reporting.

Regards,

Phill.

Thanks! I guess I'll run liveusb on main computer that has access to ethernet internet. Update. Then run liveusb on my wireless nettop to see if works. Won't be for 10 hours though as I'm gone to work.

---

### Post by kansasnoob on 2011-09-03
I never had trouble connecting to my wired network so I can't comment on that, but at least we have an icon now:

[ATTACH]201371[/ATTACH]

Forgive the ugly background, I've been playing with colors and themes trying to come up with whatever works best for my blind old self :)

---

### Post by andrewabc on 2011-09-03
> **kansasnoob said:**
> I never had trouble connecting to my wired network so I can't comment on that, but at least we have an icon now:

[ATTACH]201371[/ATTACH]

Forgive the ugly background, I've been playing with colors and themes trying to come up with whatever works best for my blind old self :)

I see the up/down network icon, but what is the missing icon next to it in your image?

EDIT:
Updated lubuntu with the fix for networking. Networking now works perfectly! It shows my wireless connections and I can connect to them. Icon is there as well. Thanks!

Problem I notice now: No sliders work. Volume slider stays at very bottom. Doesn't move up when I click and drag. Same thing for keyboard/mouse options. I even try using keyboard arrows to move slider up/down etc but it does not move.
Any idea on what is wrong there?

---

### Post by kansasnoob on 2011-09-03
> I see the up/down network icon, but what is the missing icon next to it in your image?

Power management, I've thought about trying to remove it, probably could using the system settings but i haven't bothered yet. That doesn't even show up on my Intel box, only on my old VIA box.

> Problem I notice now: No sliders work. Volume slider stays at very bottom. Doesn't move up when I click and drag. Same thing for keyboard/mouse options. I even try using keyboard arrows to move slider up/down etc but it does not move.
Any idea on what is wrong there? 

No such problem here, at least not yet.

---

### Post by cariboo on 2011-09-03
> **andrewabc said:**
> I see the up/down network icon, but what is the missing icon next to it in your image?

EDIT:
Updated lubuntu with the fix for networking. Networking now works perfectly! It shows my wireless connections and I can connect to them. Icon is there as well. Thanks!

Problem I notice now: No sliders work. Volume slider stays at very bottom. Doesn't move up when I click and drag. Same thing for keyboard/mouse options. I even try using keyboard arrows to move slider up/down etc but it does not move.
Any idea on what is wrong there?

Did you try the mouse wheel to change the volume? It's a problem with Ubuntu too.

---

### Post by andrewabc on 2011-09-04
> **cariboo907 said:**
> Did you try the mouse wheel to change the volume? It's a problem with Ubuntu too.

Just tried that. Nothing.
The slider box (area that contains slider) gets highlighted when selected. But doesn't move.

Oddly even though volume is set to very bottom (I assume would be near mute?), I am still able to hear sounds (youtube).

I don't know if mouse/keyboard sliders are far left as possible by default. If not then I'm guessing that every slider box is set to 0 even though may not technically be at that point.

---

### Post by ronacc on 2011-09-04
I'm not seeing the volume problem on my lubuntu-64 bit install , could it ve related to your hardware ?

---

### Post by kansasnoob on 2011-09-04
Dumb question :confused:

If I choose to never show Xfce Power Manager icon how can I access it later on?

Here's a screenshot of what I see if I right-click on the still broken icon in the panel, and select preferences:

[ATTACH]201465[/ATTACH]

As I've said previously it doesn't even show up on my Intel desktop PC, only on my old VIA desktop PC.

And I prefer just using Xscreensaver to adjust my prefs :)

---

### Post by kansasnoob on 2011-09-04
> **ronacc said:**
> I'm not seeing the volume problem on my lubuntu-64 bit install , could it ve related to your hardware ?

I'm also not seeing that, and keyboard/mouse settings appear to work OK.

---

### Post by kansasnoob on 2011-09-04
Just thought to add:

I'm quite a noob to LXDE and Lubuntu, makes my ubu-name more relevant again :D

So apologies in advance for lacking answers, I'm struggling a bit myself ............ but I'm convinced, after fiddling with all other recent "buntu" flavors, that this is what's best for me ATM :)

And I still have parallel installs of both Ubuntu 10.04.3 and 11.04 to sustain me when I'm tired and want nothing to do with development!

---

### Post by jerrylamos on 2011-09-04
> **ronacc said:**
> I'm not seeing the volume problem on my lubuntu-64 bit install , could it ve related to your hardware ?

Volume really problematic on my notebook, my netbook, and especially my fast tower.  It's a pain.

Of course Narwhal runs fine....

Jerry

---

### Post by phillw on 2011-09-04
Hi good people,

I ask, once again, that you raise bug reports for issues. As stated, the devs do not hang around here. Filing a bug report allows everyone to see its progress. Whilst I can nudge our devs, I cannot give them the detailed information that they need for them to chase down a bug such as the inner workings of the system you are using.

We do really appreciate all the extra bodies helping, but they do really need details of a problem as opposed to "It does not work". This applies across the entire *buntu family. To this end, the work that has been done for bug reporting is wonderful. Please do use it.

Regards,

Phill.

---

### Post by jerrylamos on 2011-09-04
> **VinDSL said:**
> Capital Razz smiley, eh?  LoL!  :D

Would you know if all Lubuntu .iso's are hybrid CD/USB images now?

I'd like to try different versions, but don't feel like fooling around with USB boot creators.
Technique I use is easier for me than startup disk creator and faster for me than dd which is very particular about USB stick format:

My solution is to format a USB stick to ext3.  Can add a 2nd partition labelled casper-rw for persistent mode if you like.

I use zsync to update the .iso's

I usually do sudo chmod 666 *.iso since the image downloads with just root permissions.

Simply copy the Oneiric.iso onto the USB.

I always have other Ubuntu partitions running so I do:

df to make sure what /dev/sdx the USB is, in this example sdc1

sudo gedit /etc/grub.d/40_custom then add this to the file:

menuentry "Ocelot sdc1 USB" {
set isofile="/oneiric-desktop-i386.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

sudo update-grub

If necessary do
sudo grub-install /dev/sda

then reboot and choose the new Grub2 entry.

Try running the Live, if you wish, do an install.

Since putting the .iao onto the USB is a simple copy, updating to the next day's .iso is just a copy to the USB no messy isohybrid or startup disk creator.

I also copy the .iso to a file on an existing partition and folder, say on sda1 and have a 40_custom entry for that. 

Fun.  Jerry

---

### Post by VinDSL on 2011-09-04
> **jerrylamos said:**
> Technique I use is [...]

Fun.  Jerry
Thanks!

I'll have to try that method...  ;)

---

### Post by ronacc on 2011-09-04
> **jerrylamos said:**
> Volume really problematic on my notebook, my netbook, and especially my fast tower.  It's a pain.

Of course Narwhal runs fine....

Jerry

since some of us are having the problem and others not it may be hardware related , both my 32 bit and 64 bit installs are plain vanilla no special settings for sound and work as they should , that box is already shutdown  for the night I'll post my hardware tomorrow  .

---

### Post by VinDSL on 2011-09-05
> **jerrylamos said:**
> Fun.  Jerry
Whoa!  This is nice!

Never ran a USB stick with persistence enabled.

It's a little slower when loading, but saves time not having to install the flash plugin, reconfig the desktop, et cetera.

Thanks!

---

### Post by VinDSL on 2011-09-05
> **andrewabc said:**
> Problem I notice now: No sliders work. Volume slider stays at very bottom. Doesn't move up when I click and drag.[...]
I started having this "volume slider" problem on the USB install I just made (latest daily build).

I solved it by:
[LIST]
[*]Installing PulseAudio
[*]Rebooting
[*]Removing the original volume control from the LXPanel
[*]Adding a new volume control to the LXPanel
[/LIST]
So far, so good.

Hopefully, it will survive a restart...  ;)

---

### Post by VinDSL on 2011-09-05
w00t!  Got Conky working with full transparency...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-5-sep-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-sep-2011.png")[/INDENT]


Look at the CPU & RAM usage...  :D

I'm starting to l-o-v-e this distro!

---

### Post by kansasnoob on 2011-09-05
That looks really cool, would you please share how exactly you set Conky up in that manner?

I've certainly found that even running full screen videos in Lubuntu uses less resources that Ubuntu itself.

> **VinDSL said:**
> w00t!  Got Conky working with full transparency...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-5-sep-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-sep-2011.png")[/INDENT]


Look at the CPU & RAM usage...  :D

I'm starting to l-o-v-e this distro!

---

### Post by Dark_Ronius on 2011-09-05
I've found, no matter how many times I try, the Lubuntu iso doesn't seem to burn properly. Tried many different cds, dvds, burning with windows and burning with Mac OS X but I keep getting the error that the cd is unreadable, and it doesn't seem to boot when I try to install from cd. Is anyone else having this problem?

For the time being I have had to install the Ubuntu beta then install the lubuntu-desktop package. I'm feeling, even though my specs are quite up to Gnome-shell and Unity, there are too many errors and bugs in the both of them, especially in this beta. So far I've had no problems with LXDE, and it's great for running Minecraft at proper speed ;)

---

### Post by ronacc on 2011-09-05
I have not had any problems with the iso's either 32 or 64 bit , Have you tried burning it from an ubuntu install using k3b , I find that works much better that brasero or cd/dvd creator . alternately try burning it to a usb stick with unetbootin  .

---

### Post by teh603 on 2011-09-06
> **Dark_Ronius said:**
> I've found, no matter how many times I try, the Lubuntu iso doesn't seem to burn properly. Tried many different cds, dvds, burning with windows and burning with Mac OS X but I keep getting the error that the cd is unreadable, and it doesn't seem to boot when I try to install from cd. Is anyone else having this problem?
Could be drive failure on the Mac. I've noticed that Apple's drives last only two years or less.

Its why I built the custom PC I'm using now; Apple's hardware is too much of a pain in the butt to replace.

---

### Post by WasMeHere on 2011-09-07
> **jerrylamos said:**
> Technique I use is easier for me than startup disk creator and faster for me than dd which is very particular about USB stick format:

My solution is to format a USB stick to ext3.  Can add a 2nd partition labelled casper-rw for persistent mode if you like.
...
sudo gedit /etc/grub.d/40_custom then add this to the file:

menuentry "Ocelot sdc1 USB" {
set isofile="/oneiric-desktop-i386.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

sudo update-grub

If necessary do
sudo grub-install /dev/sda

then reboot and choose the new Grub2 entry.

Try running the Live, if you wish, do an install.
...
I also copy the .iso to a file on an existing partition and folder, say on sda1 and have a 40_custom entry for that. 

Fun.  Jerry
Thanks for a convenient way to run live iso-files, Jerry!

I keep iso-files of several interesting distros on a partition. You inspired me to make them easily bootable by hardlinking them to a file name, 'candidate.iso' that is called by grub. It is very easy to remove 'candidate.iso' and hardlink another iso-file to it.
```
rm candidate.iso
ln another-distro.iso candidate.iso
```
So I did
```
sudo gedit /etc/grub.d/40_custom
```
and added this to the file:
```
menuentry "Boot UBUNTU 10+ BASED SYSTEM from /media/multimed-2/CD/candidate.iso" {
set isofile="/CD/candidate.iso"
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
```
sudo update-grub
``` is needed only once. When booting, grub finds the distro, that is linked to 'candidate.iso'. (There are distro images, that cannot be booted this way, for example Ubuntu-8.04.)

Have fun/Olle

*Edit: You must change the reference to the partition and directory, so that it fits your configuration (edit the bold red text):*```
menuentry "Boot UBUNTU 10+ BASED SYSTEM from /**[COLOR="Red"]media/sda2/CD[/COLOR]**/candidate.iso" {
set isofile="/**[COLOR="Red"]CD[/COLOR]**/candidate.iso"
loopback loop (**[COLOR="Red"]hd0,2[/COLOR]**)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```

---

### Post by andrewabc on 2011-09-07
I finally got lubuntu running on new desktop. Could not get liveusb to run (when it went from BIOS->boot OS it could not boot device). So I had to burn beta1 to livecd.

It booted fine. The volume slider works. But the mouse/keyboard sliders still do not work.

So this is weird.

Glad to see both VGA+HDMI monitor/tv working at same time. Although just copying each other. I'm guessing there is a way to have one monitor as desktop1 and the other as desktop2?

---

### Post by phillw on 2011-09-07
> **andrewabc said:**
> 
 But the mouse/keyboard sliders still do not work.



Is this the known bug [https://bugs.launchpad.net/ubuntu/+source/lxinput/+bug/725194](https://bugs.launchpad.net/ubuntu/+source/lxinput/+bug/725194)

As you will see, it has many duplicates. As always, trying to herd bugs into one fix is difficult when there are multiple repeats. Can you please try the fix. If it does not work, then report it back it as still an issue.

If so, I will look back and ask if our Head of Dev would consider your problem a new problem. but with many people reporting a similar bug, and him susbscribing to it, along with people not really taking the time to check similar bugs the time taken to round up bugs is removing the time they have to actually fix it.

I'm sorry if that seems harsh, but duplicated bugs just eat up the precious time the devs have.

Regards,

Phill.

---

### Post by VinDSL on 2011-09-08
> **kansasnoob said:**
> That looks really cool, would you please share how exactly you set Conky up in that manner?
I'll publish the Conky (transparency) mods, when its implementation in Lubuntu becomes stable.

I'm still trying to nail-it-down.

As it stands, Conky acts differently inside Lubuntu, depending on the machine you're running it on, e.g. config needs to be tweaked from machine-to-machine.

Basically, I've had the best luck using "desktop" as the own_window_type, and using "Feh" to draw the wall.  Otherwise, it's a conventional .conkyrc setup.

The problem is, Lubuntu is a moving target at the moment, and I don't want to publish something that's going to break in 12 hours, you know?

Once things pan out, I'll do a data dump...

---

### Post by kansasnoob on 2011-09-08
> **VinDSL said:**
> I'll publish the Conky (transparency) mods, when its implementation in Lubuntu becomes stable.

I'm still trying to nail-it-down.

As it stands, Conky acts differently inside Lubuntu, depending on the machine you're running it on, e.g. config needs to be tweaked from machine-to-machine.

Basically, I've had the best luck using "desktop" as the own_window_type, and using "Feh" to draw the wall.  Otherwise, it's a conventional .conkyrc setup.

The problem is, Lubuntu is a moving target at the moment, and I don't want to publish something that's going to break in 12 hours, you know?

Once things pan out, I'll do a data dump...

Thanks :D

No rush, I'm headed out this AM to buy some materials to finish putting my kitchen back together. Living w/o a kitchen is getting very old.

---

### Post by ronacc on 2011-09-08
heck all you really need is a microwave and a MrCoffee .

---

### Post by phillw on 2011-09-09
> **VinDSL said:**
> I'll publish the Conky (transparency) mods, when its implementation in Lubuntu becomes stable.

I'm still trying to nail-it-down.

As it stands, Conky acts differently inside Lubuntu, depending on the machine you're running it on, e.g. config needs to be tweaked from machine-to-machine.

Basically, I've had the best luck using "desktop" as the own_window_type, and using "Feh" to draw the wall.  Otherwise, it's a conventional .conkyrc setup.

The problem is, Lubuntu is a moving target at the moment, and I don't want to publish something that's going to break in 12 hours, you know?

Once things pan out, I'll do a data dump...

A try with the Beta 1 does not changed every 24 hours - those are the Dailies They only all break when Beta 2 comes out:P

Thanks for keeping on top of it, it looks pretty damn cool to me!

Regards,

Phill.

---

### Post by ronacc on 2011-09-10
is there an editor for the menu ?

---

### Post by kansasnoob on 2011-09-19
> **ronacc said:**
> heck all you really need is a microwave and a MrCoffee .

That's about all I've been using, along with a toaster ;)

I think it's been nearly five years since I almost burned my house down, after which I sort of turned the place into a studio apartment where the living room became a kitchen of sorts, and the bedroom became the "grand room" where all else occurred :D

But the whole house is tiny, about 26 feet X 32 feet overall, so it's been cramped. But I now seem to be really gaining.

But, back on topic, I've set aside the next few days for Beta 2 iso-testing which should begin either late today or sometime tomorrow.

My greatest concern ATM is the alternate installer as I've found it quite buggy, but I feel confident in our devs' abilities.

I really haven't noticed any show-stopping bugs in my installed Lubuntu-oneiric.

---

### Post by kansasnoob on 2011-09-19
I guess my iso-testing "sniffer" still works OK :D

I'd no more than posted here when I got a notice of Ubuntu live image testing, not Lubuntu yet, but it won't be far behind.

But already I need to do a repeat :(

I wasn't pay enough attention and I'm confused about what's "mounted" pre-install ................... must-pay-attention. Or is that:

Must. Pay. Attention.

I hate when I make stupid mistakes. OTOH the upside is that I've been just using Ubuntu/Lubuntu for weeks w/o any issues that required any real attention :D

But going weeks w/o problems also made me rusty, so now I'm a rusty clunker ;)

---

### Post by phillw on 2011-09-19
Lubuntu beta 2 tests have arrived on the tracker site. Unfortunately they are empty! Lance has fired in an email to flag the issue.

Regards,

Phill.

---

### Post by ronacc on 2011-09-19
is the beta-2 different from todays daily and if so please post a link .

---

### Post by phillw on 2011-09-19
> **ronacc said:**
> is the beta-2 different from todays daily and if so please post a link .

The qa tests for the milestone releases are discussed at [Testing the Milestones](https://wiki.ubuntu.com/Lubuntu/Testing#QA_testing_of_Milestone_releases). I've had a really good try at getting [ Lubuntu Testing](https://wiki.ubuntu.com/Lubuntu/Testing) into some decent semblance of order providing information that I think is pertinent to testers. Please do let me know if there is anything extra you would like on there.

Regards,

Phill.

---

### Post by kansasnoob on 2011-09-20
Already the alternate has rebuilt twice, currently up to 20110920.1, and the live image is rebuilding as I type this ;)

I just popped in here to find the proper bug report for the broken power manager icon. The network manager icon is fixed, and oddly on my Intel box the power manager icon doesn't show up at all by default, but it does on my VIA box, but I just change the settings so it doesn't it.

But, even though I don't use it - and therefore don't see it - some users will use it and want it fixed :)

---

### Post by kansasnoob on 2011-09-21
Wow, Julien got right on that software sources bug in the alternate and it's fixed in 20110920.2-i386 :)

But I see both the Ubuntu and Lubuntu live images are rebuilding again as I type this.

I have a Dr's appointment in a few hours and it looks like I'll have plenty more testing to do when I return :)

---

### Post by phillw on 2011-09-21
Got about 4 hours to d/load here :( Darn slow out here in the countryside :\

Yeah, he's quick fixing things!

Regards,

Phill.

---

### Post by ronacc on 2011-09-21
is there going to be a formal beta2 of lubuntu ?

---

### Post by phillw on 2011-09-21
> **ronacc said:**
> is there going to be a formal beta2 of lubuntu ?

Hi,

[https://wiki.ubuntu.com/Lubuntu/Developers#Roadmap](https://wiki.ubuntu.com/Lubuntu/Developers#Roadmap)

Has the roadmap. hopefully the Beta2 will move from QA-testing to milestone release tomorrow :)

Regards,

Phill.

---

### Post by ronacc on 2011-09-22
the beta2 is up , dl-ing the 64bit alternate now .

---

### Post by phillw on 2011-09-22
> **ronacc said:**
> the beta2 is up , dl-ing the 64bit alternate now .

Crikey,

you guys are mad keen... Yes, the beta 2 has left the QA section and onto [http://cdimage.ubuntu.com/lubuntu/releases/oneiric/beta-2/](http://cdimage.ubuntu.com/lubuntu/releases/oneiric/beta-2/)  however, before you all go posting duplicates of bugs, would you please allow Julien to make the official announcement with the release notes?

Julien has been mad busy as it went through the QA stage, please give him a little time to sleep and get the official announcement out with the all important notes.

Once he officially announces it and the notes, I will update the [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing)  area. For those who really like the 'cutting edge', why not get involved at the QA stage? Details are on the [https://wiki.ubuntu.com/Lubuntu/Testing#QA_testing_of_Milestone_releases](https://wiki.ubuntu.com/Lubuntu/Testing#QA_testing_of_Milestone_releases)  area.

Regards,

Phill.

---

### Post by ronacc on 2011-09-22
did the alternate install , a few glitches but got it installed anyway . installer found my wireless card ( rtl8185 ) and configured it , found my router but could not configure dhcp ( manual configure after booting into the install ok ) . selecting guided in the partitioner did not produce a useable configuration or rather produced no configuration , would not allow me to go back and select manual , kept looping in guided , aborted install and selected manual next time ( had previously partitioned and formated disk with gparted ) that worked but it only asked if I wanted to install grub and did not give a choice of where ( 3 disks in that box ) , the install was to sdb but grub went to sda . late tonight so I'll do tests of the install tomorrow .

---

### Post by andrewabc on 2011-09-23
Good news.

On livecd on my fast/new computer, volume and mouse/keyboard(options) sliders work. 

One odd thing I noticed is that while it was booting up lubuntu desktop the screensaver started. I have no idea why, in settings it says 10 minutes (default), and I don't think it was booting that long. Maybe 5 min. This did not happen while booting liveusb on nettop (which loads faster than livecd).

On my nettop with liveusb the keyboard/mouse sliders work. But the volume slider does not work. This makes me think it is hardware related, and as someone suggested earlier they uninstalled/installed some software/drivers which fixed it which I might try sometime. Or file a bug. I'll see later.

---

### Post by phillw on 2011-09-23
Ermm, it seems to have died on the 20th Sept. Which is a pain. I've manually added the release notes to the testing area at [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing) Hopefully this will be resolved soon.

Regards,

Phill.

---

### Post by phillw on 2011-09-23
> **ronacc said:**
> did the alternate install , a few glitches but got it installed anyway . installer found my wireless card ( rtl8185 ) and configured it , found my router but could not configure dhcp ( manual configure after booting into the install ok ) . selecting guided in the partitioner did not produce a useable configuration or rather produced no configuration , would not allow me to go back and select manual , kept looping in guided , aborted install and selected manual next time ( had previously partitioned and formated disk with gparted ) that worked but it only asked if I wanted to install grub and did not give a choice of where ( 3 disks in that box ) , the install was to sdb but grub went to sda . late tonight so I'll do tests of the install tomorrow .

From my point, there are two bugs... 
1) the loop when trying to get to manual partitioning
2) the inability to tell grub where to install.

I should have some time free over the w/end to have a play with the 1st one, I'd have to have a think about just how I set up my two 500GB internal hard drives on my laptop to play with the second one. 

Do let me know any updates & I will try to re-create them to be able to confirm on a bug report.

As ever, thanks for the continued testing :)

Regards,

Phill.

---

### Post by ronacc on 2011-09-23
I did a reinstall from the alternate tonight went exactly the same , I did find a way to get out of the partitioner loop , selecting go back just sends you into the loop , so does selecting undo changes ( even though no changes have been made yet) but if you select one of the partitions it dumps you into manual and you can proceed . I didn't believe  they could do it but they have managed to make the partitioner even more bizarre and confusing than before .again the installer couldn't configure dhcp but the installed system did with no problem . I think I'll try the live cd tomorrow .

---

### Post by ronacc on 2011-09-24
well I tried the desktop 64bit live cd , it booted to a cmd prompt , checked md5 and burned another copy , same result , typing startx <return> loaded the lxde desktop , set res and activated wifi from there and then selected install , the install went faster and smoother , the partitioner gui is different on the live cd than on the alternate , better , still not good but atleast better than the abortion on the alternate . it asked where to install grub  and found my other installs . when it said it was finished and asked to restart it did not eject the cd , manualy ejected the cd , the restart went to a cmd prompt ( login ) logged in but startx failed with a message that it couldn't find the nvidia module ( which I had not yet installed ) or the nv driver .going to try again and not change the res in the installer .

edit : did a 3rd install from the 64bit desktop same result , booted into another install on the same box and examined the lubuntu install , looked at /etc/x11  found no xorg.conf so why is it looking for the nvidia proprietary driver ? also looked at my /home/<me> it was empty except for 8 hidden items no ~/documents no ~/downloads no nothing . that box is out in my workshop and its shutdown for the night tomorrow I'll take a look at /root and see if I find anything there .

---

### Post by Thomas1477 on 2011-09-24
I have burned Lubuntu 11.10 Beta 2 three (3) times. Have installed 3 times, but can not get it to boot. Stops after start bluetooth. Any one have any ideas?

---

### Post by ronacc on 2011-09-24
mine is stopping at the same place , see my post just above yours .

---

### Post by Thomas1477 on 2011-09-24
I used the 32bit live desktop. The date of the iso was Sept. 21. I have not found a Beta 2 that is dated Sept. 22 or later.
At this time I am using Xubuntu Beta 2. It is working great, but I would like to give Lubuntu a try.

---

### Post by ronacc on 2011-09-25
just use the alternate install cd . That results in a working desktop . if you are wifi only you will have to set that up after booting into the install the installer seems to have a problem configuring dhcp but the installed sys has no problem , and select manual in the partitioning section to setup the partitions the way you want .

---

### Post by kansasnoob on 2011-09-25
@ ronacc,

Instead of "startx" try "sudo service lxdm start". That should give you the actual Lubuntu DE instead of standard LXDM.

I did run into that problem and tried to get it mentioned in the release notes:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837)

Not really sure about the installation and/or post-installation problems :confused:

I wonder if repeating the installation from the actual Lubuntu DE would matter?

I didn't notice any real irregularities in the alternate as far as partitioning is concerned.

---

### Post by kansasnoob on 2011-09-25
> **Thomas1477 said:**
> I used the 32bit live desktop. The date of the iso was Sept. 21. I have not found a Beta 2 that is dated Sept. 22 or later.
At this time I am using Xubuntu Beta 2. It is working great, but I would like to give Lubuntu a try.

From my md5sum file the Beta 2 is the same as the 20110921.1 daily, which has a ".1" because it was a rebuild on 0921:
> 16ad74b4c11a76aff14fe05678140399  oneiric-desktop-i386.iso
&#65279;16ad74b4c11a76aff14fe05678140399 (&#65279;lubuntu/daily-live/20110921.1/oneiric-desktop-i386.iso)
&#65279;16ad74b4c11a76aff14fe05678140399 *lubuntu-11.10-beta2-desktop-i386.iso


The Lubuntu Beta 2 images are here:

[http://cdimage.ubuntu.com/lubuntu/releases/11.10/beta-2/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/beta-2/)

---

### Post by ronacc on 2011-09-25
> **kansasnoob said:**
> @ ronacc,

Instead of "startx" try "sudo service lxdm start". That should give you the actual Lubuntu DE instead of standard LXDM.

I did run into that problem and tried to get it mentioned in the release notes:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837)

Not really sure about the installation and/or post-installation problems :confused:

I wonder if repeating the installation from the actual Lubuntu DE would matter?

I didn't notice any real irregularities in the alternate as far as partitioning is concerned.

I'll try from the lubuntu de using your suggestion and report back .
on the alternate partitioner select "guided" and then from the next screen try to "go back" and select something else .

---

### Post by phillw on 2011-09-25
Not sure if this is the issue with your installs, but it has just been reported and will get fixed.

[https://bugs.launchpad.net/bugs/858279](https://bugs.launchpad.net/bugs/858279)

Regards,

Phill.

---

### Post by ronacc on 2011-09-25
Kansas I tried your suggestion to put the installer into lubunu de , it worked and the install seemed to go ok but the result was the same , booting into the install stalls at bluetooth and you cannot get to a gui , ctrl>alt>F1  and running sudo service lxdm start says that lxdm is already running and gives a process # but X won't start , the problem seems to be with the video driver  I've got an Nvidia 5200fx in that box and it seems to be trying to start a driver that is not yet installed I may try d/l'ing the driver from nvidia copying it to my /home/<me> and hand installing it from term . and BTW this time the partitioner did not offer to let me choose my SDB for the install from guided and that drive was completely empty and freshly formated to ext4 , the only choices guided offerd me were SDA also empty and formated to ext3 and SDC with 2 oter installs ( not buntu's ) .also it shows the drives in reverse order to gparted  the drive gparted sees as SDA the installer sees as SDC .

@ phillw  thanks I'll try copying the headers over from an install on another box .

---

### Post by kansasnoob on 2011-09-25
> **phillw said:**
> Not sure if this is the issue with your installs, but it has just been reported and will get fixed.

[https://bugs.launchpad.net/bugs/858279](https://bugs.launchpad.net/bugs/858279)

Regards,

Phill.

Hmmm, I see that was an i386 install and I wonder why I haven't encountered that problem :confused:

I'm busy ATM but I'll soon do some more testing.

---

### Post by ronacc on 2011-09-25
another update on my battle with the 64bit beta2  There are more problems with the desktop beta 2 than the missing header files in /usr/src/ . I copied the header files from another box that also has lubutu installed from an earlier daily and updated daily . also copied my /home/<me> from that box because the /home/<me> that the desktop beta 2 created was essentially empty . first I replaced the header files and tried a reboot , same result stalls after starting bluetooth , then replaced the /home/<me> with the good one again same result . Then I hand installed the nvidia driver for my card and at last was able to boot to a working ( sort of) but crippled desktop , menu was unpopulated only logout and run ( run didn't do anything ) but I was able to start pcmanfm from the panel and get a terminal from there and update from there , rebooted after update no help ,got to a desktop but still crippled, started synaptic from term and reinstalled lubuntu desktop , lubuntu core and lubuntu defaults rebooted to a still crippled desktop . any ideas what to try next gratefully accepted .

---

### Post by Thomas1477 on 2011-09-25
@romacc Will try your post #378.

@kansasnoob I am downloading per your post #380. I think that is the same place that I did my download on Sept. 22.

To the both of you--- I think we may have a problem with Nvidia drivers per other post that I have read, but I may be wrong. Also thanks to the both of you for your help.):P

---

### Post by ronacc on 2011-09-25
I don't think the problem lies with the nvidia drivers themselves , I hand installed the driver from source no problem , I think the problem lies in the installer not installing everything it should , basically the beta 2 desktop cd is a complete washout .

---

### Post by phillw on 2011-09-26
Hiyas, there are so many issues that you are uncovering I've done this:

> Hi Julien,

It really does seem that the desktop ISO is crippled in several ways. The forum testers are having all sorts of grief with it & trying various work-arounds. Could you please have a look at the thread [http://ubuntuforums.org/showthread.php?t=1774388](http://ubuntuforums.org/showthread.php?t=1774388) from about page 37 which is when they switched to beta 2. There are so many little gremlins that reading it would make more sense then my trying to list them. I *know* that devs don't read forum posts, but if you would make an exception for these guys in this case.

Regards,

Phill.

He's a good guy & I'm sure he will pop by and have a read.

Regards,

Phill.

---

### Post by ronacc on 2011-09-26
Thanks Phil . I don't think the problem lies with Lubuntu itself , I have 2 installs on one box ( 1 32bit  1 64bit ) that were installed around A2 and have been updated continuously since and they show none of the problems that the beta 2 does so that makes me think that something in the build process went badly wrong .and since the alternate install disk results in a functional desktop the problem lies somewhere in the difference between it and the desktop cd . although it is interesting to note that the "live" part of the desktop cd works beautifully .

---

### Post by Thomas1477 on 2011-09-26
I downloaded both the i386 live iso and the i386 alt iso this morning. After burning both of them, I put the disk in my test pc and when I hit F1 the i386 live CD is a beta 1 dated 21 Sep. 2011. It is not a Beta 2.
The Alt CD is a beta 2 dated 22 Sep 2011.
It would seem to me that a i386 live CD beta 2 iso has not been upload to the Beta 2 download site.:confused:

---

### Post by amjjawad on 2011-09-26
Can I share my Test Notes here?
I'm testing Lubuntu 11.10 Beta2.

Thanks!

---

### Post by ronacc on 2011-09-26
go ahead thats what this thread is for .

---

### Post by amjjawad on 2011-09-26
---------------------------------------------------------------------------------------------------------------------------------------
Test No.1
---------------------------------------------------------------------------------------------------------------------------------------
PC: P4 3.0GHz - 2GB RAM - 40GB IDE HDD - Intel Graphics Card (driver=i915) 
Media: Lubuntu 11.10 Beta 2 LiveCD - 32 bit
---------------------------------------------------------------------------------------------------------------------------------------

Notes:
1- Try Lubuntu without installation does not work and drop you to CLI. Typing "starx"  command will take you to LXDE Desktop with LXDE wallpaper instead of Lubuntu Desktop. There is an icon on the LXDE Desktop to Install Lubuntu.

Reboot done ...

2- Install Lubuntu Option > Quit > Quit > Lubuntu Desktop. Please note that I used to do the same with Lubuntu 11.04.

3- I chose "Something Else" and created a new Partition (sda9) with 3.91GB from un-allocated disk space. Please note that I'm Multi-Booting several Distros on this test PC. GRUB was installed into sda9 not MBR (sda). Installation was smooth and errors-free.
> After Installation < 

4- Choose a Picture during the installation process simple does nothing. Even when I took a picture, it didn't show it on the preview small box. 
[http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8210](http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8210)

Apparently, it's a new feature but I'm not sure how does it work?

5- "Removable Medium is inserted" pop-up window during installation. Not sure if that's a bug or something?!
[http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8211](http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8211)

6- Continue Testing OR Reboot > Reboot > Please remove installation media and press Enter - Not Responding when Press Enter > Force Reboot - Ctrl+Alt+Del > "Press Enter to reboot msg" > Reboot Done.

Not sure if that's an error or something but I recall I got the same with other LiveCD and other Distros, mainly Ubuntu-Based.

Installation done ... rebooted.

7- Wallpapers are really nice and getting better. Good job :)

8- Sometimes, the menu doesn't disappear even after making a selection: [http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8205](http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8205)
Clicking on the desktop does nothing. I had to go to menu and click there twice and then it disappeared.

9- Looks like "Enable Networking" and "Enable Wireless" does nothing: [http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8204](http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8204)
It's not 'ticked' or 'selected'. Looks like a bug?

10- Customize Look and Feel > Window Border > No Preview
[http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8207](http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8207)

11- Some apps are not installed. I suggest to include these apps. IMHO, I see it's good to have these:
a- numlockx
b- dnsmasq ([http://forum.lxde.org/viewtopic.php?f=6&t=31326](http://forum.lxde.org/viewtopic.php?f=6&t=31326))
c- GParted
d- Flash Player

12- LSC installed:

sudo add-apt-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install lubuntu-software-center

I'm finding it a bit hard to deal with. For example, you need to Double Click on a Category and it takes sometime until the contents show up. Search Box is disabled until you choose a Category and that means if you don't know in which Category the application or program you want is included then you need to select "All". I was looking for Firefox to install but couldn't easily find it because I got many selections. Not to mention I got some Crash Error and it was asking to report this problem.

13- Crash Report sometimes with Chromium and PCManFM.

14- I see too many themes, widget, etc are installed by default. I suggest (IMHO) to remove the extra themes and give users the choice to install these after installing Lubuntu 11.10 in case they want to. Perhaps PPA for all these extra themes? won't that reduce some size? perhaps I'm wrong and it's just a suggestion.

---------------------------------------------------------------------------------------------------------------------------------------

Ok, that's all for now. 
I'm also done with two other tests on the other PC, one from LiveCD and the other from LiveUSB. Got some stuff to share with you but guess that will be later because I must go now.

Thank you for your time :)

---

### Post by phillw on 2011-09-26
As him reading through the posts, he asks..> I only saw the problems about the drivers not installed using jockey, but this one should be fixed. Can, at least, he can list properly the issues he have in an ordered list ?

Regards,
Julien Lavergne

Once done, i'll ask Julien to pop on again. Please try and provide as much information as possible, as we would for an apport bug report. The devs really are crippled when there is not enough detail for them to work with.

Thanks for your continued testing :)

Regards,

Phill.

---

### Post by ronacc on 2011-09-26
I'll do 2 installs tomorrow one from 64 bit alternate and one from 64 bit desktop and write down things as I go along .

---

### Post by Thomas1477 on 2011-09-26
Up and running after installing with the x86 alternate cd. At this time all seems to be ok. I have updated and installed the nvidia current driver. I have Lubuntu installed with Xubuntu. I had forgotten how much I disliked text base installers.:)

---

### Post by andrewabc on 2011-09-27
> **amjjawad said:**
> 
11- Some apps are not installed. I suggest to include these apps. IMHO, I see it's good to have these:
a- numlockx
b- dnsmasq ([http://forum.lxde.org/viewtopic.php?f=6&t=31326](http://forum.lxde.org/viewtopic.php?f=6&t=31326))
c- GParted
d- Flash Player


is numlockx still needed? I remember always installing it, but I thought with recent versions wasn't needed?

gparted, I don't think needed to be installed by default. Maybe installed when running from liveusb/livecd like normal ubuntu (but once OS installed to HDD no longer installed)?

I highly doubt they'd include flash by default, especially if they don't with any other ubuntu version. As long as easy to find/install (software center or synaptic).

---

### Post by amjjawad on 2011-09-27
> **andrewabc said:**
> is numlockx still needed? I remember always installing it, but I thought with recent versions wasn't needed?

Why not? if you have a PC and you want to use your Num-Pad, specially if your password has some numbers? I see no harm with it.


> gparted, I don't think needed to be installed by default. Maybe installed when running from liveusb/livecd like normal ubuntu (but once OS installed to HDD no longer installed)?

Perhaps it's just me who is in love with GParted :P
Just kidding. I actually do lots of tests and I do need GParted to be included with each and every install no matter what distro I use.
If someone with solo installation (one distro) then YES, it's not required but if at least you are dual-booting, I guess it comes handy.

> 
I highly doubt they'd include flash by default, especially if they don't with any other ubuntu version. As long as easy to find/install (software center or synaptic).

As per Julien:

> Proprietary software, we can't include it by default.


---

### Post by amjjawad on 2011-09-27
I forgot to add that "LockScreen" is very useful too. Those who are switching form Ubuntu to Lubuntu (the number is increasing) will find it very useful. It's already included in LXDE Desktop by default so why not with Lubuntu?

[http://forum.lxde.org/viewtopic.php?f=8&t=31300](http://forum.lxde.org/viewtopic.php?f=8&t=31300)

---

### Post by phillw on 2011-09-27
Hi,

well obviously it will not be in 11.10, but from zero to a well functioning and low resource app, Stephen has done an outstanding job. It is still a W-I-P, and he is still tweaking it in response to 'paper-cut' bugs. some achievement :p We've tested it in 11.04 and 11.10 

We are however happy enough to allow people at it, the nice thing is that we're at the picking over style etc. The app works, it is nice to see an app built with 'make it work' as the 1st priority, followed by make it look pretty :P

[Lubuntu Software Center](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_install_Lubuntu_Software_Center) Has the details, I'm sure they are the same for 11.04, but being the devout coward I am on double checking things I will ask before I edit my entry. (I'm sure the boss said that the ppa would 'auto-learn' between 11.04 and 11.10).

Stephen has been very canny in writing it, as we found out when we saw the xubuntu logo in it as a screen-shot. It will work with any debian system with about the only tweak being the little 'all' badge.

:popcorn:

Regards,

Phill.

---

### Post by ranch hand on 2011-09-27
> **amjjawad said:**
> 
Perhaps it's just me who is in love with GParted :P
Just kidding. I actually do lots of tests and I do need GParted to be included with each and every install no matter what distro I use.
If someone with solo installation (one distro) then YES, it's not required but if at least you are dual-booting, I guess it comes handy.

Gparted is installed on everything I install.  Would not be without it.

Now for the But. think about the first time Linux user, dual booted with some inferior OS as their primary OS.

I do not like the removal of a number of things Ubuntu has removed from the default install.  I do think that if you have trouble finding and installing Gparted you better not have it on your OS.

Now don't point out that sfdisk comes installed.  It will do a lot more damage a lot faster than gparted will.  It is harder to find.  If you find it and don't read the man page and help that is your mistake.

---

### Post by phillw on 2011-09-27
> **ranch hand said:**
> Gparted is installed on everything I install.  Would not be without it.

Now for the But. think about the first time Linux user, dual booted with some inferior OS as their primary OS.

I do not like the removal of a number of things Ubuntu has removed from the default install.  I do think that if you have trouble finding and installing Gparted you better not have it on your OS.

Now don't point out that sfdisk comes installed.  It will do a lot more damage a lot faster than gparted will.  It is harder to find.  If you find it and don't read the man page and help that is your mistake.

Hello my old friend!

now, not 'old', but 'old'... you know what I mean ;)

As always we are stuck between a pig and a poke. How do you 'guide' a windows person on their 1st install of a linux system? There is an old saying "a little knowledge is dangerous", I'm for keeping guided for n00bs.

[rant] I just REALLY WISH they'd remove the blooming 'encrypt my /home' option.... A n00b forgets the password & everything is lost... Why the heck that is not only available with the likes of LVM etc on the alternate is totally beyond me.[/rant]

Good to see you still about :)

Regards,

Phill.

---

### Post by cariboo on 2011-09-27
> **phillw said:**
> Hello my old friend!

now, not 'old', but 'old'... you know what I mean ;)

As always we are stuck between a pig and a poke. How do you 'guide' a windows person on their 1st install of a linux system? There is an old saying "a little knowledge is dangerous", I'm for keeping guided for n00bs.

[rant] I just REALLY WISH they'd remove the blooming 'encrypt my /home' option.... A n00b forgets the password & everything is lost... Why the heck that is not only available with the likes of LVM etc on the alternate is totally beyond me.[/rant]

Good to see you still about :)

Regards,

Phill.

There is a way to recover data from an ecrypted home directory, have a look [here]("http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html").

The big problem is a matter of education, most Windows users are used to clicking everything in sight, without reading what the dialogue boxes say, and there isn't a lot we can do to change it. Unfortunately Canonical is catering to this type of user, by simplifying the installation process.

What I find really funny, are those users that select to encrypt their home directories, and also select auto-login, there by negating  the purpose of an encrypted home directory.

---

### Post by phillw on 2011-09-27
> **cariboo907 said:**
> There is a way to recover data from an ecrypted home directory, have a look [here]("http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html").

LMFAO! but thanks for the link. And there's me with the 128bit pass-phrase written down from my testing of a beta2 install with an encrypted /home area!

Regards,

Phill.

---

### Post by amjjawad on 2011-09-28
> **ranch hand said:**
> Now for the But. think about the first time Linux user, dual booted with some inferior OS as their primary OS.


IMHO, GParted "was" installed by default with 9.10 under "System" Menu then "Administration" Sub-Menu.
That should be fair enough to anyone to understand this is "watch-out area" and he/she must be careful. When he/she will open the program, he'll find the password pop-up window which will yet again indicates that you must be careful when dealing with that.
If someone for some weird reason decided to ignore all that, it's his/her problem :)

That's my humble personal opinion.


> I do not like the removal of a number of things Ubuntu has removed from the default install.  

Like GParted got removed after installation starting from Ubuntu 10.04 if I'm not wrong.

> I do think that if you have trouble finding and installing Gparted you better not have it on your OS.

I agree. If someone so new to all this and he/she can't even find GParted and doesn't know how to install it, better live without it. But again, a new thread here or any where else will give the answer :) that if he/she didn't bother to search on Google.

---

### Post by andrewabc on 2011-09-28
> **amjjawad said:**
> Why not? if you have a PC and you want to use your Num-Pad, specially if your password has some numbers? I see no harm with it.


I meant that it auto started numlock when OS booted on its own, and thus it wasn't needed anymore. But maybe that is not the case for most people or I'm remembering it wrong.

> Perhaps it's just me who is in love with GParted
I love it too and always install it. Doesn't mean a good default installed program for everyone (normally you would do partitions and stuff when installing then forget about that stuff) :)

---

### Post by ronacc on 2011-09-28
the numlock on at boot is sometines default and sometimes not , If you notice that it is off on first boot just install numlockx , they can't seem to make up their minds .

---

### Post by amjjawad on 2011-09-28
> **andrewabc said:**
> I meant that it auto started numlock when OS booted on its own, and thus it wasn't needed anymore. But maybe that is not the case for most people or I'm remembering it wrong.

If I remember correctly, starting from Ubuntu 10.04, Num-Lock is no longer active on its own unless the user install it. I have no idea what's the point behind that? For a year now, I have to install it right after I'm done with installation.


> I love it too and always install it. Doesn't mean a good default installed program for everyone (normally you would do partitions and stuff when installing then forget about that stuff) :)


I always create my partitions (using GParted) before I install any OS unless there is a reason that could prevent me from that; for example: when I installed Lubuntu 11.10 beta 2, I did the partitioning during the installation to test whether it works well or not.

Most likely the one who decided not to include GParted as the default program does not use it or install it after he/she installs Ubuntu. Perhaps I'm wrong.

---

### Post by amjjawad on 2011-09-28
> **ronacc said:**
> the numlock on at boot is sometines default and sometimes not , If you notice that it is off on first boot just install numlockx , they can't seem to make up their minds .

Yes, for a year now, one has to install it so it could be "ON" the next time he/she reboots. However, while the user on the login screen, Num-Lock is OFF.

Some BIOS has that option where you can turn it ON every time you boot but I noticed that doesn't work anymore with Linux. IDK why?!

---

### Post by kansasnoob on 2011-09-29
Has anyone else found lxpanel to be borked following recent updates?

My DE is currently almost useless, and Alt + F2 doesn't work either.

About the only thing I can do is go to a tty and launch whatever app I need to use.

Not so good for a Beta 2 :(

---

### Post by phillw on 2011-09-29
> **kansasnoob said:**
> Has anyone else found lxpanel to be borked following recent updates?

My DE is currently almost useless, and Alt + F2 doesn't work either.

About the only thing I can do is go to a tty and launch whatever app I need to use.

Not so good for a Beta 2 :(

Hello my good friend, good to see the grim reaper has not got you yet :P

would you please bug report it? My Asking our Head of Dev over here to read the reports only tells him the symptons. Getting it bug-reported at least gives them a chance... We all know about 'regressions' where they fix one thing and break about 200 others!

Thanks. Now if only we could get the standard iso to blooming work :P such are the joys of a new build system 
:lolflag:


Regards,

Phill.

---

### Post by kansasnoob on 2011-09-29
> **phillw said:**
> Hello my good friend, good to see the grim reaper has not got you yet :P

would you please bug report it? My Asking our Head of Dev over here to read the reports only tells him the symptons. Getting it bug-reported at least gives them a chance... We all know about 'regressions' where they fix one thing and break about 200 others!

Thanks. Now if only we could get the standard iso to blooming work :P such are the joys of a new build system 
:lolflag:


Regards,

Phill.

Only the remodeling "reaper" ;)

I noticed in my in-box I need to follow up on this bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/854837)

And I'll certainly do that. But I generally do not report each and every little bug during a dev cycle unless it persists for at least 24 hours.

Quite often it's due to the way updates are handled during a dev cycle and it quite often resolves itself quickly :)

I also find it useful to ask here at the forums if someone else has encountered the same problem. In this case I did notice some jockey updates and that would be my best guess, but I'll wait a bit to see if future updates resolve the matter.

---

### Post by amjjawad on 2011-09-29
> **kansasnoob said:**
> Has anyone else found lxpanel to be borked following recent updates?

My DE is currently almost useless, and Alt + F2 doesn't work either.

About the only thing I can do is go to a tty and launch whatever app I need to use.

Not so good for a Beta 2 :(

What updates?
I'm testing Lubuntu 11.10 Beta 2 on two machines. How can I produce that issue?

I'm having another issues like LSC continuously crashing, File Manger is crashing and "Enable Networking" and "Enable Wireless" has display bug, etc.

---

### Post by kansasnoob on 2011-09-29
> **amjjawad said:**
> What updates?
I'm testing Lubuntu 11.10 Beta 2 on two machines. How can I produce that issue?

I'm having another issues like LSC continuously crashing, File Manger is crashing and "Enable Networking" and "Enable Wireless" has display bug, etc.

Puter had been sleeping since yesterday and I applied these:

> Start-Date: 2011-09-29  12:44:27
Commandline: aptdaemon role='role-commit-packages' sender=':1.34'
Upgrade: gir1.2-appindicator3-0.1:i386 (0.3.91-0ubuntu1, 0.4.1-0ubuntu1), libgtk2.0-common:i386 (2.24.6-0ubuntu3, 2.24.6-0ubuntu4), libpeas-common:i386 (1.2.0-0ubuntu1, 1.2.0-0ubuntu2), libcanberra-gtk-module:i386 (0.28-0ubuntu8, 0.28-0ubuntu9), libgail18:i386 (2.24.6-0ubuntu3, 2.24.6-0ubuntu4), libunity6:i386 (4.0.6-0ubuntu1, 4.0.6-0ubuntu2), gir1.2-gtk-2.0:i386 (2.24.6-0ubuntu3, 2.24.6-0ubuntu4), libcanberra-gtk3-0:i386 (0.28-0ubuntu8, 0.28-0ubuntu9), gir1.2-unity-4.0:i386 (4.0.6-0ubuntu1, 4.0.6-0ubuntu2), libnm-gtk0:i386 (0.9.1.90-0ubuntu2, 0.9.1.90-0ubuntu3), gtk2-engines-pixbuf:i386 (2.24.6-0ubuntu3, 2.24.6-0ubuntu4), nautilus-data:i386 (3.2.0-0ubuntu2, 3.2.0-0ubuntu4), network-manager-gnome:i386 (0.9.1.90-0ubuntu2, 0.9.1.90-0ubuntu3), libcanberra-gtk3-module:i386 (0.28-0ubuntu8, 0.28-0ubuntu9), libpeas-1.0-0:i386 (1.2.0-0ubuntu1, 1.2.0-0ubuntu2), firefox:i386 (7.0+build2+nobinonly-0ubuntu4, 7.0.1+build1+nobinonly-0ubuntu1), grub-gfxpayload-lists:i386 (0.4, 0.5), libgtk2.0-bin:i386 (2.24.6-0ubuntu3, 2.24.6-0ubuntu4), libcanberra-gtk0:i386 (0.28-0ubuntu8, 0.28-0ubuntu9), libappindicator1:i386 (0.3.91-0ubuntu1, 0.4.1-0ubuntu1), libcanberra0:i386 (0.28-0ubuntu8, 0.28-0ubuntu9), firefox-locale-en:i386 (7.0+build2+nobinonly-0ubuntu4, 7.0.1+build1+nobinonly-0ubuntu1), libappindicator3-1:i386 (0.3.91-0ubuntu1, 0.4.1-0ubuntu1), libnm-gtk-common:i386 (0.9.1.90-0ubuntu2, 0.9.1.90-0ubuntu3), libnautilus-extension1:i386 (3.2.0-0ubuntu2, 3.2.0-0ubuntu4), libgtk2.0-0:i386 (2.24.6-0ubuntu3, 2.24.6-0ubuntu4), gir1.2-peas-1.0:i386 (1.2.0-0ubuntu1, 1.2.0-0ubuntu2)
End-Date: 2011-09-29  12:45:17

When the panel disappeared I used the terminal and applied these:

> Start-Date: 2011-09-29  15:28:32
Commandline: apt-get dist-upgrade
Upgrade: icedtea6-plugin:i386 (6b21.1.2-0ubuntu1, 6b21.1.3-1ubuntu1), libnm-gtk0:i386 (0.9.1.90-0ubuntu3, 0.9.1.90-0ubuntu4), icedtea-plugin:i386 (1.1.2-0ubuntu1, 1.1.3-1ubuntu1), icedtea-6-jre-cacao:i386 (6b23~pre10-0ubuntu3, 6b23~pre10-0ubuntu4), network-manager-gnome:i386 (0.9.1.90-0ubuntu3, 0.9.1.90-0ubuntu4), jockey-common:i386 (0.9.4-0ubuntu8, 0.9.4-0ubuntu9), libkpathsea5:i386 (2009-11, 2009-11ubuntu1), openjdk-6-jre-headless:i386 (6b23~pre10-0ubuntu3, 6b23~pre10-0ubuntu4), alsa-utils:i386 (1.0.24.2-0ubuntu7, 1.0.24.2-0ubuntu8), openjdk-6-jre:i386 (6b23~pre10-0ubuntu3, 6b23~pre10-0ubuntu4), icedtea-netx:i386 (1.1.2-0ubuntu1, 1.1.3-1ubuntu1), icedtea-6-jre-jamvm:i386 (6b23~pre10-0ubuntu3, 6b23~pre10-0ubuntu4), openjdk-6-jre-lib:i386 (6b23~pre10-0ubuntu3, 6b23~pre10-0ubuntu4), libasound2:i386 (1.0.24.1-0ubuntu8, 1.0.24.1-0ubuntu9), jockey-gtk:i386 (0.9.4-0ubuntu8, 0.9.4-0ubuntu9), libnm-gtk-common:i386 (0.9.1.90-0ubuntu3, 0.9.1.90-0ubuntu4)
End-Date: 2011-09-29  15:29:12

I haven't had time to check further since then :)

I don't bother with LSC, IMHO it's just another UI to what I prefer to do in Synaptic, but that's just my choice.

I occasionally get a pcmanfm crash report but pcmanfm still works OK so I think that's OK because I suspect it's a race issue with apport.

No problems here with networking and I have no wireless to try, just a borked power management icon that I don't care much about.

But now I have no panel :)

---

### Post by ronacc on 2011-09-29
after todays updates my 32bit install is a bit flaky , lxterminal starts but quits immediately ditto the shutdown button pcmanfm ok , my 64bit install does not seem to have the problems , theese are upgrades of previous installs , I had to give up on testing the beta2 , the box I was using for that had a hardware problem .

---

### Post by kansasnoob on 2011-09-30
This AM I booted into the DE again, still no panel, so I went to tty and ran another round of updates, still no lxpanel.

So I went to tty and tried "sudo service lxdm restart" just as a wild-hair approach and after logging back into the default DE all is back to normal :)

No real idea what went wrong exactly.

---

### Post by ronacc on 2011-09-30
thanks for the tip ,todays updates + restarting lxdm fixed my 32bit install .

---

### Post by cmike on 2011-09-30
Hey - from some time after few updates/upgrades on my 64-bit Lubuntu 11.10 Beta 2 I have high CPU load - a process 'Xorg' takes at least 20-50% of my CPU. I have no idea, what causes it. I've upgraded X server too edgers version (1.11), but nothing changed.

---

### Post by pkg9991 on 2011-09-30
how's ubuntu 11.10 and lubuntu 11.10 different? can somebody in brief please explain

---

### Post by amjjawad on 2011-09-30
I did fresh installation for Lubuntu 11.10 on P4 with less than 512MB RAM and 20GB IDE HDD. The purpose was to test it with Dual-Booting. I installed Lubuntu 11.10 then Lubuntu 11.04.
Dual-Booting is fine but I'm having weird stuff when running in the Recovery Mode.

I did:

```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

Nothing yet ...

---

### Post by amjjawad on 2011-09-30
> **pkg9991 said:**
> how's ubuntu 11.10 and lubuntu 11.10 different? can somebody in brief please explain

On my signature, check "Lubuntu" and "LXDE" links and you'll understand ;)

---

### Post by amjjawad on 2011-09-30
This might be off topic but I was wondering if someone of you guys having a problem with LXPanel on **Lubuntu 11.04**? Two users reported a frozen LXPanel on LXDE Forum and I was wondering if someone else is having the same issue?

[http://forum.lxde.org/viewtopic.php?f=8&t=31360](http://forum.lxde.org/viewtopic.php?f=8&t=31360)

---

### Post by kansasnoob on 2011-10-01
> **amjjawad said:**
> This might be off topic but I was wondering if someone of you guys having a problem with LXPanel on **Lubuntu 11.04**? Two users reported a frozen LXPanel on LXDE Forum and I was wondering if someone else is having the same issue?

[http://forum.lxde.org/viewtopic.php?f=8&t=31360](http://forum.lxde.org/viewtopic.php?f=8&t=31360)

Look at post #416. I got it back that way :)

---

### Post by amjjawad on 2011-10-01
> **kansasnoob said:**
> Look at post #416. I got it back that way :)

Hi and thanks for your reply :)
So, same goes to Lubuntu 11.04? the users who reported that are using 11.04.
[http://ubuntuforums.org/showpost.php?p=11298590&postcount=416](http://ubuntuforums.org/showpost.php?p=11298590&postcount=416)

I'll inform them anyway and let's see what will happen :)

---

### Post by cmike on 2011-10-03
> **cmike said:**
> Hey - from some time after few updates/upgrades on my 64-bit Lubuntu 11.10 Beta 2 I have high CPU load - a process 'Xorg' takes at least 20-50% of my CPU. I have no idea, what causes it. I've upgraded X server too edgers version (1.11), but nothing changed.

Hey, it's me again.
I review my problem again, and I think that lxpanel causes high cpu load. On attached screenshot top show this high load.

---

### Post by ronacc on 2011-10-03
> **cmike said:**
> Hey, it's me again.
I review my problem again, and I think that lxpanel causes high cpu load. On attached screenshot top show this high load.

I'm not seeing that on either my 32 or 64 bit installs , checked each both before and after this AM's updates .

---

### Post by amjjawad on 2011-10-03
> **kansasnoob said:**
> I haven't had time to check further since then :) 
Yet again, I had to wipe my HDD (20GB IDE Samsung) and this time, I had to use "dd" command to write zero to its sectors ... I suspect it's dying so just trying to play with it before it dies.

I installed Lubutnu 11.10 again and installed all the updates. Will try to produce some errors.

> I don't bother with LSC, IMHO it's just another UI to what I prefer to do in Synaptic, but that's just my choice.

You are not alone :) I don't like Software Center, I like to use the Terminal (so I can learn more about commands) and Synaptic. So I agree. However, I was just trying to help my team to report some bugs. As far as I know, LSC won't be included by default in the next release :)

> I occasionally get a pcmanfm crash report but pcmanfm still works OK so I think that's OK because I suspect it's a race issue with apport.
It works with me but the crash reports show up when I open it. Couldn't even send any report.

>  No problems here with networking and I have no wireless to try
It's a display bug as per Julien.
If you Right Click on the Networking Icon, you see "Enable Networking" and "Enable Wireless" are both un-ticked/un-checked. If you tick these two options, nothing happens. If you un-tick, both options will be disabled and you go offline. Restarting the machine will go back to square Zero where both options are un-checked.

I might attach or include some screenshots :)

---

