---
title: "mono 1.1.6 is in debian"
date: 2005-04-21
forum: Programming Talk
---

### Post by manstrike on 2005-04-21
I just finished downloading mono 1.1.6 from debian
monodevelop however seems very buggy half the time it will crash on any input and the other half it will not display the source view window
but the rest of it looks good I suspect I need a newer version of some dependence as monodoc goes fine as do the rest of the mono apps I got

---

### Post by jdodson on 2005-04-21
[QUOTE=manstrike]I just finished downloading mono 1.1.6 from debian
monodevelop however seems very buggy half the time it will crash on any input and the other half it will not display the source view window
but the rest of it looks good I suspect I need a newer version of some dependence as monodoc goes fine as do the rest of the mono apps I got[/QUOTE]

ya, mixing package repositores as in adding debians is not recommended.  

i would suggest following the mono wiki howto:

[http://www.ubuntulinux.org/wiki/BeagleInstallHowto](http://www.ubuntulinux.org/wiki/BeagleInstallHowto)

the beagle install requires mono, so its a win/win situation.

*EDIT* sorry that is an old link, use this: [http://www.ubuntulinux.org/wiki/HoaryBeagleInstallHowto](http://www.ubuntulinux.org/wiki/HoaryBeagleInstallHowto)

and beagle cant work with the normal package repositories anyway... *SLAPS HEAD*  
hmmmm, the wiki recommends mixing repos in this instance..... ok forget what i said, commence mixing in this instance for the latest versions:)  i helps to rtfm, even for mods.

---

### Post by manstrike on 2005-04-22
I wouldn't also normally mix but I have been developing with mono and hit a number of bugs in the 1.0.5  build so I'm nearing a point were I upgrade or dump ubuntu 

plus the Mono for Debian site [http://pkg-mono.alioth.debian.org/](http://pkg-mono.alioth.debian.org/)
has all the extra packages not yet uploaded into debian such as monodevelop 0.6

the APT source:
deb [http://debian.meebey.net/](http://debian.meebey.net/) ./

---

### Post by manstrike on 2005-05-17
got monodevelop running stable I had to also install icu and pkg-config from debian unstable plus delete the mondevelop config folder found in ~/.config/MonoDevelop

---

### Post by jerome bettis on 2005-05-17
can someone explain what this mono / beagle stuff is all about?  there seems to be a lot of interest in it and i have no idea what it is ... :confused:

---

### Post by manstrike on 2005-05-17
[QUOTE=jerome bettis]can someone explain what this mono / beagle stuff is all about?  there seems to be a lot of interest in it and i have no idea what it is ... :confused:[/QUOTE]
 it just lets you run .net apps under linux works a lot like java
and beagle is just a search tool that indexes your data so should give back better results
I just use it to program with

---

### Post by neighborlee on 2005-05-18
[QUOTE=manstrike]it just lets you run .net apps under linux works a lot like java
and beagle is just a search tool that indexes your data so should give back better results
I just use it to program with[/QUOTE]
-------
flames ready ( although this is not bait), I just want to say I dont trust this mono stuff ny further than I could throw bill gates and lately that aint far I dont think. Are we really poised to accept a standard that M$ created and aren't there issues with the api (gui stuff) between the various platforms ?..I think real intelligent debate should go on about this before ubuntu just ups and decides to adopt it ...I am pretty sure I heard that gnome has likely no intentions of supporting it ( while of course novell is :dah) so ubuntu based on gnome I find this slighty bothersome at least.

lets open talks ?

cu
neighborlee

---

### Post by LordHunter317 on 2005-05-18
[QUOTE=neighborlee]-------
flames ready ( although this is not bait),[/quote]No, it's just unformed, ignorant tripe.

>   Are we really poised to accept a standard that M$ createdSeeing as C# is an ECMA standard and they haven't bothered any of the multiple groups reimplementing .NET at all? 

That makes no sense.  Microsoft really can't do anything about people reimplementing their published API unless they do so in a way they have patented.  Which isn't likely to happen.


>  and aren't there issues with the api (gui stuff) between the various platforms ?Currently, yes.  This is largely due to the way Mono originally went about implementing portions of the .NET API.  Originally, they intended to use WINE to run System.Windows.Forms using apps.  It quickly became obvious that this is simply a nonfunctional solution and they are quickly working on providing a proper reimplementation of System.Windows.Forms.


> ...I am pretty sure I heard that gnome has likely no intentions of supporting itSeeing as Miguel de Izaca is behind Mono, you'd be totally wrong.

---

### Post by harryc on 2005-05-18
[QUOTE=manstrike]I just finished downloading mono 1.1.6 from debian
monodevelop however seems very buggy half the time it will crash on any input and the other half it will not display the source view window
but the rest of it looks good I suspect I need a newer version of some dependence as monodoc goes fine as do the rest of the mono apps I got[/QUOTE]Mono 1.1.7 is available in backports-staging. I'm not a developer, but it seems very stable for Beagle and Tomboy.

[http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/universe/binary-i386/](http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/universe/binary-i386/)

---

