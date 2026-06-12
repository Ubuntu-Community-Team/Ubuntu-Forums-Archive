---
title: "There should be application rolling releases!"
date: 2009-04-24
forum: Recurring Discussions
---

### Post by CJ Master on 2009-04-24
Hello,

I was just thinking about how ridiculous it is to have to wait six months if a new program just came out, in order to use it. I am well aware of Backports, but those are slow just the same.

Now here's my proposition: Make applications only rolling release, not important system files. This way you keep the stability of regular releases, along with having the newer programs; the best of both worlds.

Edit: Um.... the poll looks skewed for some reason... Just say Yes, no, or I don't know in your posts please.

---

### Post by LowSky on 2009-04-24
or just use a linux distro with rolling releases

[http://www.archlinux.org/](http://www.archlinux.org/)

or use Debian test/unstable
[http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/)


not to mention some apps require new important security update or new kernel relleases, so the pick and choosing becomes harder to do, rolling distros like Arch are great but they too can sometimes have problems

---

### Post by CJ Master on 2009-04-24
> **LowSky said:**
> you ask you shall recieve

[http://www.archlinux.org/](http://www.archlinux.org/)

or use Debian test/unstable
[http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/)

I'm well aware of Sid and Arch. This is about Ubuntu though. There's no reason Ubuntu should have stale old programs.

---

### Post by FuturePilot on 2009-04-24
> **CJ Master said:**
> Hello,

I was just thinking about how ridiculous it is to have to wait six months if a new program just came out, in order to use it. I am well aware of Backports, but those are slow just the same.

Now here's my proposition: Make applications only rolling release, not important system files. This way you keep the stability of regular releases, along with having the newer programs; the best of both worlds.

I've thought the exact same thing. I think it would be an interesting idea. Keep the base system (kernel etc) frozen so as to have a stable base, but have the latest version of all the desktop applications available like OpenOffice, Pidgin, Banshee, etc etc.

---

### Post by SuperSonic4 on 2009-04-24
Yes I think there should be but you'll have to sacrifice some stability for it.

A rolling release distro would be better but on the other hand not having a rolling release means a longer lifespan for old version

---

### Post by snowpine on 2009-04-24
I voted no; I think you should either have a well-done stable release distro (like Ubuntu) or a well-done rolling release distro (like Arch), but not some half-baked in between not quite stable, not quite rolling distro. :)

Are you aware that if you'd like a newer version of a specific application, there are several different ways to get it? You can add a 3rd party repository, install it from a .deb, or build it from source. Just because you use 8.04 doesn't mean you can't install Openoffice 3, for example.

Anyways, your idea is not even possible with Ubuntu because of their development process. They take a snapshot of the Debian repository every six months and use that as the starting point for each Ubuntu release. If they implemented your idea, they would basically just be mirroring a portion of the Debian Sid repository. :)

---

### Post by CJ Master on 2009-04-24
> **SuperSonic4 said:**
> Yes I think there should be but you'll have to sacrifice some stability for it.

A rolling release distro would be better but on the other hand not having a rolling release means a longer lifespan for old version

There would be almost no stability sacraficed. Remember; we're talking about updating programs only, not important system files.

Future: Thank you, I agree!

---

### Post by Sand &amp; Mercury on 2009-04-24
Having apps updated on a rolling schedule would create problems as they could rely on libraries that are considered important system files that wouldn't get updated; after a while, everything would start messing up.

A lot of apps have their own PPA repositories, so you can just add those if you want the latest and greatest of something.

---

### Post by LowSky on 2009-04-24
all the newest apps are easy to get, either use a site like getdeb, or go to the softwares developers website and see if they have their own repo.

For every new install I add some extra repos


heres pidgin
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

here banshee
[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)

Openoffice 3.0 repo for Ubuntu 8.10 (not really needed at this point).
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

anything else can be picked up in .deb form here
[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by amauk on 2009-04-24
> **CJ Master said:**
> There would be almost no stability sacraficed. Remember; we're talking about updating programs only, not important system files.
But there would be
Applications depend on "important system files"

A newer version of App-X will probably need newer versions of library-Y & Z, etc.

I'm afraid, If you want rolling releases, use a rolling release distro

---

### Post by lswest on 2009-04-24
> **CJ Master said:**
> There would be almost no stability sacraficed. Remember; we're talking about updating programs only, not important system files.

Future: Thank you, I agree!

Some new programs can require a new or updated version of another package.  Firefox, for example, requires xulrunner (in archlinux at least) and both packages need to be updated, and xulrunner is dependent on other packages, etc. Chances are one of the many dependencies will end up being a system package, which, using your idea, would be "frozen" and thus the update would fail.

Just my thoughts on the matter,
Lswest

---

### Post by days_of_ruin on 2009-04-24
> **amauk said:**
> But there would be
Applications depend on "important system files"

A newer version of App-X will probably need newer versions of library-Y & Z, etc.

I'm afraid, If you want rolling releases, use a rolling release distro

Exactly.

---

### Post by ddrichardson on 2009-04-24
> **CJ Master said:**
> There would be almost no stability sacraficed. Remember; we're talking about updating programs only, not important system files.

Future: Thank you, I agree!
I'm not sure I follow the meaning of "Applications" and "Important system files", for example where do new versions of KDE/Gnome/XFCE fit in that model?

As someone else said, the supporting libraries are almost certainly going to be updated too.

---

### Post by FuturePilot on 2009-04-24
> **LowSky said:**
> all the newest apps are easy to get, either use a site like getdeb, or go to the softwares developers website and see if they have their own repo.

For every new install I add some extra repos


heres pidgin
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

here banshee
[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)

Openoffice 3.0 repo for Ubuntu 8.10 (not really needed at this point).
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

anything else can be picked up in .deb form here
[http://www.getdeb.net/](http://www.getdeb.net/)

The thing is though, none of those are officially supported. When you step outside the Ubuntu repos, you're on your own. If you find a bug in any of those packages from a third party repo, you can't report it to Ubuntu. If there's a security vulnerability there's no guarantee that the maintainer of that repo will update it.

Suse works in a similar way as to what the OP described. It offers to let you add officially supported repos that will give you the latest version of XYZ application, but the base system is pretty much frozen.

> **ddrichardson said:**
> I'm not sure I follow the meaning of "Applications" and "Important system files", for example where do new versions of KDE/Gnome/XFCE fit in that model?

As someone else said, the supporting libraries are almost certainly going to be updated too.

IMO the DEs would be excluded from this. As for the libraries, not necessarily. You can compile an application against older libraries, you don't necessarily need to have the latest libraries.

---

### Post by FuturePilot on 2009-04-24
..

---

### Post by ddrichardson on 2009-04-24
> **FuturePilot said:**
> IMO the DEs would be excluded from this. As for the libraries, not necessarily. You can compile an application against older libraries, you don't necessarily need to have the latest libraries.
As you said - not necessarily - but that's a nightmare to package for.

Ultimately that's the argument I'd have against this - a lot of effort for an unsubstantial return and a huge divergence from the rest of the project.

sabdfl is _very_ keen on the six month release cycle in any event.

---

### Post by Tibuda on 2009-04-24
Ubuntu 0.00 Rolling Rabbit

---

### Post by snowpine on 2009-04-24
> **FuturePilot said:**
> The thing is though, none of those are officially supported. 


Then ask yourself, "WHY have they chosen not to officially support these?" and you will have the answer. :)

ps Assuming resources are finite, would you rather have the Ubuntu team working on the next release, or backporting the latest version of Pidgin to Hardy?

---

### Post by Skripka on 2009-04-24
> **FuturePilot said:**
> 
IMO the DEs would be excluded from this. As for the libraries, not necessarily. You can compile an application against older libraries, you don't necessarily need to have the latest libraries.

You can compile yes...that doesn't necessarily mean that it would work...or that you wouldn't risk doing harm to your system.

Let us say that Ubuntu has version X of the database that drives the Evolution mail client.  You know, that Evolution mail client you cannot remove, as it's database and libraries are integrated into Ubuntu/Gnome?

...let us also say that old version A of some arbitrary software depends on old database X.  Now, You want the new version of this software, version: A+1 requires the newest version of database X to run, the new database being version X+1.

Are you seeing why this could do havoc on your system?  Old Ubuntu with old DE and system, mixed with NEW not necessarily compatible database software which is depended on by the OS.  It is asking for disaster.

---

### Post by blueshiftoverwatch on 2009-04-24
I voted yes but after reading some of the responses I can see why a rolling release might not be best.

---

### Post by sertse on 2009-04-24
Actually, Ubuntu's PPA system is a nice way of addressing this. Users/Upstream devs with an particular interest in an app would form their own repos you can follow to the latest versions while keeping everything else the same. 

That's how it is now, and it works pretty well. Especially for end user apps, I know some PPAs would get even before Debian Sid

---

### Post by Namtabmai on 2009-04-24
No for me, well mostly no.

> **snowpine said:**
> Then ask yourself, "WHY have they chosen not to officially support these?" and you will have the answer. :)

ps Assuming resources are finite, would you rather have the Ubuntu team working on the next release, or backporting the latest version of Pidgin to Hardy?

Well if Ubuntu was a true rolling release that wouldn't be a problem. There would be no Hardy, Gutsy, Intrepid etc. It would all just be the lastest set of packages. So in theory all they would have to support is what every packages they choose to provide. If someone is having trouble with an older package the standard reply would be to upgrade to the latest then try again. 

For the general users, they don't care if they have version X of a package they just want their computer to work. So for this a time based release is perfect.
But I'm not the average user, far from it. I can easily adapt. Most of my system is stock but where I need the latest and greatest I know where to get them from ( ppa/deb/source ) and I don't expect any support if I do this. Personally I think this is the way it should be. It eases the strain on Ubuntu to provide core support while leaving me to get on with what I want to do.

That said I would like to see some sort of packaging system on top of apt that allows for a much easier upgrade of software. I love apt and wouldn't change it but I would like something like ebuilds as well. With ebuilds all I had to do was rename a ebuild to match the latest package version number and it would try and go off and build the latest release. Trying to package and updated version of an existing package in Ubuntu is no where near as simple.

---

### Post by jowilkin on 2009-04-24
Adding 3rd party PPAs gets to be a PITA..

I think 3rd party PPAs should be aggregated into a single repository.  Do not include this repository by default and warn the user very sternly that the packages will not be supported by Canonical if they try to add it.  Use pinning in aptitude so that the user needs to specifically say if they want to add a program from this repo instead of the official repos. 

But for god sakes stop making me hunt all over the place just to get new apps or upgraded versions of apps.

---

### Post by Namtabmai on 2009-04-24
> **jowilkin said:**
> I think 3rd party PPAs should be aggregated into a single repository.

Awesome and who decides if my PPA should be aggrogated into this central PPA? What happens if they decide not to include me? Who pays for this central PPA to be managed? Who performs security checks on this central PPA?

The whole point of PPA ( personal package archive ) is that they are just that. Personal. If Ubuntu wanted to manage a set of unsupported debs they would set something up, such as the existing universe repo,

---

### Post by jowilkin on 2009-04-24
> **Namtabmai said:**
> Awesome and who decides if my PPA should be aggrogated into this central PPA? What happens if they decide not to include me? Who pays for this central PPA to be managed? Who performs security checks on this central PPA?

The whole point of PPA ( personal package archive ) is that they are just that. Personal. If Ubuntu wanted to manage a set of unsupported debs they would set something up, such as the existing universe repo,

The easy solution is that everything gets included.  No one decides what gets included.  That's why it's called unsupported.

Who decides which PPAs can be included on launchpad right now??  If there is such a person than why can't they do the same for one repo instead a bunch of separate ones?

Honestly I don't understand the vitriol I've run into against this idea when I've brought it up previously.  It seems to work fine for Arch with their AUR.

---

### Post by Namtabmai on 2009-04-24
> **jowilkin said:**
> 
Who decides which PPAs can be included on launchpad right now??  If there is such a person than why can't they do the same for one repo instead a bunch of separate ones?.

Well firstly someone does have to approve users/projects for launchpad and secondly and more importantly the user themselves has to decide which ones they add.

Blindly making every PPAs available to any user that clicks a check box is a security nightmare that Ubuntu would never want to encourage.

---

### Post by Sef on 2009-04-24
Not the first time this has been discussed, so moved to reucurring discussions.

---

### Post by BslBryan on 2009-04-24
> **namtabmai said:**
> well firstly someone does have to approve users/projects for launchpad and secondly and more importantly the user themselves has to decide which ones they add.

Blindly making every ppas available to any user that clicks a check box is a security nightmare that ubuntu would never want to encourage.
+1

---

### Post by jowilkin on 2009-04-24
> **Namtabmai said:**
> Well firstly someone does have to approve users/projects for launchpad and secondly and more importantly the user themselves has to decide which ones they add.

Blindly making every PPAs available to any user that clicks a check box is a security nightmare that Ubuntu would never want to encourage.

So if someone is approving these PPAs then that would obviously be the person who decides what goes into the repo I suggest. People would still be required to explicitly say they want things out of this repo (obviously not with a simple check box but perhaps via pinning as I suggested), but it should be less difficult than scouring the web with google with no idea if a PPA does or does not exist for the package I want.

If Canonical is so reluctant to do this, perhaps the community should take care of it themselves by setting up and managing such a repo.  This is the spirit of Linux after all.

Or I guess the not insignificant subset of the Ubuntu community that favors something like rolling releases should move to a distro with a community willing to accommodate them (which has been happening already, see [http://ubuntuforums.org/showthread.php?t=1125754](http://ubuntuforums.org/showthread.php?t=1125754)).  Not saying this in a mean spirited way, but it seems to be a feature that many people want that has been continuously shot down by the Ubuntu community.

Ubuntu seems to have a hand-holding philosophy from what I can tell.  For instance not letting people discuss how to enable the root account is kind of ridiculous.  Ubuntu tries to keep themselves newbie friendly, but are likely to lose advanced users.

I hope no one takes this as an insult to Ubuntu, I am only trying to state the facts as I see them.

---

### Post by Mehall on 2009-04-24
There is a difference between "Advanced users" and "newest programs", and that's something people always forget in these discussions.

Ubuntu has plenty of advanced users, and on release day, it's reasonably up-to-date, considering it's based on Debian.

if you want Arch, go ahead and use Arch. Rolling Release doesn't work half-and-half, you would need to make the whole distro rolling release, which SABDFL doesn;t want.

---

### Post by ddrichardson on 2009-04-25
> **jowilkin said:**
> Honestly I don't understand the vitriol I've run into against this idea when I've brought it up previously.  It seems to work fine for Arch with their AUR.
I wouldn't go that far, Arch's rolling releases frequently make AUR packages need removing. For example AUR has versions of libxft and lib-cairo compiled for LCD filters which make fonts very crisp on LCD displays. Cairo is updated by pacman and the custom libraries ar gone until someone redoes the AUR package and I manually reinstall it.

I've nothing against this because I get the Arch Way and know what I'm doing but Ubuntu has a very large number of new users who are attracted to its simplicity and ease of use, who might not have a big technical bent - can  you imagine the support headaches this would cause?

---

### Post by CJ Master on 2009-04-27
I have read several posts here about how applications could not be updated safely while important files are frozen. However, new plan, what if applications are updated, but not system files by themselves? This doesn't mean that they are frozen, but they won't be updated like the other packages.

Now, there's a glaring con with my idea above. Stability. My thoughts are, before sending the patches down to the normal desktop users, they would send them down to the people with the testing versions instead. (Think Debain Sid.) Once we're sure its 99.9% safe, then send the patches down to normal users. Bang: A solid, but up to date distrobution.

---

### Post by will1911a1 on 2009-04-28
May as well make the whole thing a rolling release.

I voted "No".

---

### Post by Mehall on 2009-04-28
> **will1911a1 said:**
> May as well make the whole thing a rolling release.

I voted "No".

I think it tells something that a guy with the Arch logo for an avi is saying no.

I also voted no, btw.

---

### Post by growled on 2009-04-28
Personally, I don't want Ubuntu to become a rolling release. However, I wouldn't be opposed to cutting releases to once a year, and in between times to add updates to the repositories. I think versions should get software and system updates for the life of the product, and not just security updates.

---

### Post by CJ Master on 2009-04-28
> **will1911a1 said:**
> May as well make the whole thing a rolling release.

I voted "No".

As I have said many times, making the whole distro rolling would cause stability issues.

---

### Post by sertse on 2009-04-28
> **CJ Master said:**
> As I have said many times, making the whole distro rolling would cause stability issues.

Yes, but overstated. Users really just need to read and "care" about thier system before each upgrade. I agree it is too much to expect from Ubuntu's targets though.

Ubuntu is about freezing sid and stablising it. Try sidux, =) a end user distro that focuses on keeping sid rolling.

---

### Post by CJ Master on 2009-04-28
> **sertse said:**
> Yes, but overstated. Users really just need to read and "care" about thier system before each upgrade. I agree it is too much to expect from Ubuntu's targets though.

Ubuntu is about freezing sid and stablising it. Try sidux, =) a end user distro that focuses on keeping sid rolling.

While thats fine for people a bit more experianced, beginers expect to get their updates without any hitches. 

I've tried Sidux. Broke my computer the first time I updated it. Not going back. :P

---

### Post by Mehall on 2009-04-29
see? There's a reason why Ubuntu don't update everything and anything.

Canonical have chosen their method. You don't like it? Choose a different one.

---

