---
title: "Automatic Beryl in Mepis, Kororaa, and Sabayon"
date: 2007-03-02
forum: Other OS Talk
---

### Post by summersab on 2007-03-02
- - I'm double posting to get this in the forum I intended to have it in. Please feel free to delete this instance. - -

Alright, I am on a mission. It is called "bring Linux to the masses." I have converted 3 people so far at my college and the 4th is on his way. I am in the process of writing a script that beefs up Ubuntu and installs things that the default setup leaves out. One thing that I have been trying to add is automatic Beryl configuration.

Kororaa has, by far, the best autodetection of video cards that I have ever seen. Sabayon Mini detects whether your current card will support AIGLX or XGL. They are both Gentoo based. Now we have Mepis. Just this week, Mepis 6.5 Beta 7 was released with automatic setup of video cards and Beryl. And it is UBUNTU BASED! Alright, I have torn into the masses of mkxf86config and just gotten lost because I'm still only an 8 month old convert. I've tried rolling my own. Even still, why can't we, the largest Linux community, plop together a script that will automatically select the correct video driver that enables DRI for a video card and then set up Beryl (to steal Mepis' slogan) in the "Ubuntu way"? The "Linux for HUMAN BEINGS" way? If you so much as tell me to run dpkg-reconfigure xserver-xorg, I'll scream. It sucks. I want DRI by default. I want to be able to select "Beryl" from synaptic and have it run on reboot with no messy config. (Honestly, it's no trouble for me to set up, but a newbie has no idea what $vi /etc/X11/xorg.conf means!) Let's write a script - modify some existing code from Kororaa, Sabayon, Knoppix, and Mepis - and get Beryl running with a simple double click. Would anyone like to help me? I'll lend my services, but I'll admit, I'm still pretty green.

Long live Tux.

I think I accidentally put this post in the wrong forum. I meant to put it in the General forum. Whoops!

- - I'm double posting to get this in the forum I intended to have it in. Please feel free to delete this instance. - -

---

### Post by summersab on 2007-03-02
Alright, I am on a mission. It is called "bring Linux to the masses." I have converted 3 people so far at my college and the 4th is on his way. I am in the process of writing a script that beefs up Ubuntu and installs things that the default setup leaves out. One thing that I have been trying to add is automatic Beryl configuration.

Kororaa has, by far, the best autodetection of video cards that I have ever seen. Sabayon Mini detects whether your current card will support AIGLX or XGL. They are both Gentoo based. Now we have Mepis. Just this week, Mepis 6.5 Beta 7 was released with automatic setup of video cards and Beryl. And it is UBUNTU BASED! Alright, I have torn into the masses of mkxf86config and just gotten lost because I'm still only an 8 month old convert. I've tried rolling my own. Even still, why can't we, the largest Linux community, plop together a script that will automatically select the correct video driver that enables DRI for a video card and then set up Beryl (to steal Mepis' slogan) in the "Ubuntu way"? The "Linux for HUMAN BEINGS" way? If you so much as tell me to run dpkg-reconfigure xserver-xorg, I'll scream. It sucks. I want DRI by default. I want to be able to select "Beryl" from synaptic and have it run on reboot with no messy config. (Honestly, it's no trouble for me to set up, but a newbie has no idea what $vi /etc/X11/xorg.conf means!) Let's write a script - modify some existing code from Kororaa, Sabayon, Knoppix, and Mepis - and get Beryl running with a simple double click. Would anyone like to help me? I'll lend my services, but I'll admit, I'm still pretty green.

Long live Tux.

---

### Post by mips on 2007-03-02
I hope you are wearing your asbestos suite. See this thread [http://www.ubuntuforums.org/showthread.php?t=323456](http://www.ubuntuforums.org/showthread.php?t=323456)

---

### Post by igknighted on 2007-03-02
I completely understand the debate and sympathize with both sides.  However, Ubuntu is supposed to be "linux for human beings", meaning (in my eyes) anyone can use it.  Us Ubuntites who have been at it a while can troubleshoot the hit/miss FOSS drivers that are out there, but many n00bs cannot.  Instead of making things difficult, there should be an option at boot of the liveCD that asks if you want to use proprietary drivers and explains the choice a little (pros and cons).  Many people cannot boot ATI cards on ubuntu without the fglrx drivers, and even some nvidia cards.  With my Sabayon liveCD, theres a noprop boot option that uses only opensource stuff, or it can use proprietary stuff.  Maybe Ubuntu would go the opposite, start with default and only enable proprietary if there are issues, idk, bu the point is many people still need them, and I say linux users w/ proprietary vid drivers until we can knock some sense into nvidia and ati/amd is better than windows users who simply say "I tried linux, it was awful, didn't boot at all" because of something like that.

An option for beryl/compiz would be nice, but that's fluff.  Ubuntu has a lot of other, more vital stuff to work on.  Fluff is nice (and we are slipping behind almost every other distro in this category) but lets not get focused on beryl like its something that is make or break, because its just an extra that everyone like to oogle about.

---

### Post by fuscia on 2007-03-02
> **summersab said:**
> Alright, I am on a mission. It is called "bring Linux to the masses." I have converted 3 people so far at my college and the 4th is on his way. I am in the process of writing a script that beefs up Ubuntu and installs things that the default setup leaves out. One thing that I have been trying to add is automatic Beryl configuration.

[ah]automatix[/choo!!1]

---

### Post by kazuya on 2007-03-02
I love your enthusiasm, summerslam. I am currently getting mepis beta 7 as we speak. I love Beryl. This is why I gave Sabayon a shot even though it was gentoo-based. 
Pclinuxos2007test also has beryl almost ready to go for user.

Is kororaa good again. It was the best when it started.

---

### Post by Rodneyck on 2007-03-02
> **kazuya said:**
> 

Is kororaa good again. It was the best when it started.

I really liked kororaa, but the last version I tried or could use was the mainstream version with a release date of 2005. The livecd (2006) gave me problems. Their release cycle is like every six months or more. I think there is like one developer on the project, which is a shame. It was a nice system, except for the fact everything was extremely outdated.

I figured if I was going to update everything, I might as well ship over to Gentoo for a fresh install instead.

---

### Post by frodon on 2007-03-02
Isn't it enough easy to install beryl yet ? :
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Beryl is not for beginners because it introduces some bugs/limitations so any non-beginner won't have any problem to install it.

All is fine for me.

---

### Post by summersab on 2007-03-02
Yes, for people who have done it a lot, installing Beryl is pretty simple - manually. For newbies, it takes time to learn. However, I think you are dead wrong in saying that Beryl is not for newbies - if it were, then how come there are at least 3 distributions that automatically integrate it? It should be that simple - it already is! Why can't Ubuntu make it automatic, then? Does ANYONE want to help port mkxf86config to Ubuntu or something??? It is worth the effort!

---

### Post by frodon on 2007-03-02
> **summersab said:**
> Yes, for people who have done it a lot, installing Beryl is pretty simple - manually. For newbies, it takes time to learn. However, I think you are dead wrong in saying that Beryl is not for newbies - if it were, then how come there are at least 3 distributions that automatically integrate it? It should be that simple - it already is! Why can't Ubuntu make it automatic, then? Does ANYONE want to help port mkxf86config to Ubuntu or something??? It is worth the effort!No they offer to test it, it is not their standard. It makes an enormous difference.

I remind you that many games don't work with beryl and that there's some CPU usage problems in some cases.

---

### Post by Nythain on 2007-03-02
Sabayons usage of beryl pissed me off... beryl/compiz should most definately NOT be for the complete newb... partial newb sure... in fact once i got my system going and learned a wee little bit, discovering beryl has been a huge factor in my learning since then... mainly, cuase it was not so "newb" easy to get rolling... i had video card issues, bug issues, svn vs. ubuntu repo issues... compiling addon plugins, whatever...

Then there's the resource consumption... i have a pretty decent (ok, a so-so) machine, capable of doing most everythign i want it to do, and i find myself leaving beryl off most of the time unless im trying to "impress" windows friends, due to the slowness of everyday app usage.

lets not even  get into game performance if i can get most games to run at all while running beryl.

i say, use beryl to win over the windows masses ( quickly becoming moot with the release of vista, suddenly all my transparent glowing wobbling windows just arent as awe inspiring anymore, neither are my desklets for that matter) then once your friends install linux, encourage them to learn about thier system and how it works and how to set it up and configure it... they're definately gonna need those skills later down the road

personally im against almost any script that automates the installation and configuration of software on my system... we have ubuntu users of months to years now that dont know how to edit sources.list because they've relied to heavily on easy ubuntu and automatix to set thier system up. kind of kills the whole linux experience... if you want automation and no controll, you should stick with windows

---

### Post by jhenager on 2007-03-02
This would indeed qualify as a mission, but I don't see it as impossible. One thing to keep in mind would be that halfway through the process outlined by PriceChild, a restart is necessary, so that would right there exceed my very basic scripting skills. I do think adding the repos could be all done up front, and then maybe have the last action of that script create another script that would go in the Startup Programs that finished the processes could get people going by only doubleclicking one icon. (And the last action of the second script would be to remove itself from the Startup Programs, of course.)
As you can see, I'm no programmer, and I don't even play one on TV.  

[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+edgy+nvidia](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+edgy+nvidia)

Edit: One other consideration is that the directions are different for ATI and nVidia cards. This would either require two different scripts, or some conditional branching either based on hardware detection (the most cool of the two options) or having the user press 1 for ATI, 2 for nVidia.

I do agree that if you want total automation and don't want to have to think, Windows fits the bill, but I don't agree that Beryl is any less spectacular because of the release of Vista. The few little crumbs of 'eye candy' offered in Vista absolutely pale in comparison, IMHO.

---

### Post by RAV TUX on 2007-03-03
> **igknighted said:**
> I completely understand the debate and sympathize with both sides.  However, Ubuntu is supposed to be "linux for human beings", meaning (in my eyes) anyone can use it.  Us Ubuntites who have been at it a while can troubleshoot the hit/miss FOSS drivers that are out there, but many n00bs cannot.  Instead of making things difficult, there should be an option at boot of the liveCD that asks if you want to use proprietary drivers and explains the choice a little (pros and cons).  Many people cannot boot ATI cards on ubuntu without the fglrx drivers, and even some nvidia cards.  With my Sabayon liveCD, theres a noprop boot option that uses only opensource stuff, or it can use proprietary stuff.  Maybe Ubuntu would go the opposite, start with default and only enable proprietary if there are issues, idk, bu the point is many people still need them, and I say linux users w/ proprietary vid drivers until we can knock some sense into nvidia and ati/amd is better than windows users who simply say "I tried linux, it was awful, didn't boot at all" because of something like that.

An option for beryl/compiz would be nice, but that's fluff.  Ubuntu has a lot of other, more vital stuff to work on.  Fluff is nice (and we are slipping behind almost every other distro in this category) but lets not get focused on beryl like its something that is make or break, because its just an extra that everyone like to oogle about.OK the problem with the "any one can use it concept", is I can not use it on my new computer with advanced hardware, I can use it fine on my older crappy computer. So are we only Human if we own old crappy hardware? or are people who own advanced systems destined to be alienated?

On my newest computer Ubuntu simply does not work.

Perhaps this is one of the many reasons I use Sabayon Linux on my primary computer.

A short list of Debian OS's that don't work for me:

Debian 
Ubuntu

A short list of Debian OS's that simply work without fail:

KNOPPIX
NepaLinux

A short list of Debian OS's that work for me but are so damned flawed and buggy it is not worth the effort:

Mepis
Kanotix (now defunct)





> **summersab said:**
> - - I'm double posting to get this in the forum I intended to have it in. Please feel free to delete this instance. - -

Alright, I am on a mission. It is called "bring Linux to the masses." I have converted 3 people so far at my college and the 4th is on his way. I am in the process of writing a script that beefs up Ubuntu and installs things that the default setup leaves out. One thing that I have been trying to add is automatic Beryl configuration.

Kororaa has, by far, the best autodetection of video cards that I have ever seen. Sabayon Mini detects whether your current card will support AIGLX or XGL. They are both Gentoo based. Now we have Mepis. Just this week, Mepis 6.5 Beta 7 was released with automatic setup of video cards and Beryl. And it is UBUNTU BASED! Alright, I have torn into the masses of mkxf86config and just gotten lost because I'm still only an 8 month old convert. I've tried rolling my own. Even still, why can't we, the largest Linux community, plop together a script that will automatically select the correct video driver that enables DRI for a video card and then set up Beryl (to steal Mepis' slogan) in the "Ubuntu way"? The "Linux for HUMAN BEINGS" way? If you so much as tell me to run dpkg-reconfigure xserver-xorg, I'll scream. It sucks. I want DRI by default. I want to be able to select "Beryl" from synaptic and have it run on reboot with no messy config. (Honestly, it's no trouble for me to set up, but a newbie has no idea what $vi /etc/X11/xorg.conf means!) Let's write a script - modify some existing code from Kororaa, Sabayon, Knoppix, and Mepis - and get Beryl running with a simple double click. Would anyone like to help me? I'll lend my services, but I'll admit, I'm still pretty green.

Long live Tux.

I think I accidentally put this post in the wrong forum. I meant to put it in the General forum. Whoops!

- - I'm double posting to get this in the forum I intended to have it in. Please feel free to delete this instance. - -

Before Mephis, Uberyl which is Stable Ubuntu based distro did this first:

Ubuntu+Beryl+Automatix=UBERYL

**[[B]UBERYL** , a distro based on ubuntu]("http://pollolinux.blogia.com/")[/B]
[SIZE=-1] - [ [Translate this page]("http://translate.google.com/translate?hl=en&sl=es&u=http://pollolinux.blogia.com/&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3DUBeryl%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DHyZ") ]

I have tested this distro out on multiple computers and found it more reliable then plain Vanilla Ubuntu...

(also in the future please do not double post, I haven't seen your other post yet but if you could provide a link I will merge them.)

EDIT: Threads merged appropriately, again please don't double post in the future.


[/SIZE]

---

### Post by RAV TUX on 2007-03-03
> **frodon said:**
> No they offer to test it, it is not their standard. It makes an enormous difference.

I remind you that many games don't work with beryl and that there's some CPU usage problems in some cases.

All games work for me using Beryl in Sabayon Linux.

I haven't tested Beryl games compatibility in UBeryl.

---

### Post by RAV TUX on 2007-03-03
> **frodon said:**
> 
Beryl is not for beginners because it introduces some bugs/limitations so any non-beginner won't have any problem to install it.

All is fine for me.This is why it has been suggested to test Beryl out on a live CD/DVD first only:

I stand by this recommendation, There are currently 3 live distro that I would refer users to:

Knoppix-historically the most reliable of live distros
Uberyl-test Beryl out on a live CD based on Ubuntu
Sabayon Linux-What I have used on my primary computer for over 4 months, so a strong recommendation is inevitable.

---

### Post by igknighted on 2007-03-03
> **Nythain said:**
> Sabayons usage of beryl pissed me off... beryl/compiz should most definately NOT be for the complete newb... partial newb sure... in fact once i got my system going and learned a wee little bit, discovering beryl has been a huge factor in my learning since then... mainly, cuase it was not so "newb" easy to get rolling... i had video card issues, bug issues, svn vs. ubuntu repo issues... compiling addon plugins, whatever...

Then there's the resource consumption... i have a pretty decent (ok, a so-so) machine, capable of doing most everythign i want it to do, and i find myself leaving beryl off most of the time unless im trying to "impress" windows friends, due to the slowness of everyday app usage.

lets not even  get into game performance if i can get most games to run at all while running beryl.

i say, use beryl to win over the windows masses ( quickly becoming moot with the release of vista, suddenly all my transparent glowing wobbling windows just arent as awe inspiring anymore, neither are my desklets for that matter) then once your friends install linux, encourage them to learn about thier system and how it works and how to set it up and configure it... they're definately gonna need those skills later down the road

personally im against almost any script that automates the installation and configuration of software on my system... we have ubuntu users of months to years now that dont know how to edit sources.list because they've relied to heavily on easy ubuntu and automatix to set thier system up. kind of kills the whole linux experience... if you want automation and no controll, you should stick with windows

I would hardly call sabayon for a complete newb.  It's not /hard/, but their stated goal is to be as cutting edge as possible (like Fedora, also not a newb distro), plus it is based on Gentoo.  If you don't do your homework and wnat something that just works, gentoo is not for you.  The gui frontend for portae (kuroo) is buggy as hell (no real sabayon users use it), and how many newbs want to use emerge from the command line to compile everything?  Like you said, semi n00bs maybe, or those who really want to learn.  I am OK with that.

---

### Post by RAV TUX on 2007-03-03
> **igknighted said:**
> I would hardly call sabayon for a complete newb.  It's not /hard/, but their stated goal is to be as cutting edge as possible (like Fedora, also not a newb distro), plus it is based on Gentoo.  If you don't do your homework and wnat something that just works, gentoo is not for you.  The gui frontend for portae (kuroo) is buggy as hell (no real sabayon users use it), and how many newbs want to use emerge from the command line to compile everything?  Like you said, semi n00bs maybe, or those who really want to learn.  I am OK with that.

You are correct about kuroo, I have never used it and probably never will. I have embraced Emerge and find it the best way to install or update anything.

While anyone who actively uses Emerge or even apt-get can tell you of its benefits;...a GUI may be needed for beginners...

Perhaps Uberyl(Ubuntu with Beryl preinstalled) would the best for people to test Beryl out in a live CD environment?

---

