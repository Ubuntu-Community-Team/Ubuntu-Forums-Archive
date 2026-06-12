---
title: "APT vs Portage?"
date: 2007-07-30
forum: Other OS Talk
---

### Post by izanbardprince on 2007-07-30
I was browsing through a Sabayon forum and heard someone mention what a relief Portage was, after having used the "horrible apt-get system on Ubuntu".

It would seem to me that it's easier to install a deb package than to compile everything you want to run, and from everything I've read, Portage sounds like pulling teeth with pliers.

Comments?

---

### Post by ThinkBuntu on 2007-07-30
For basic tasks, both are fine. You get more flexibility with Portage because you can specify how the program is compiled. This lets you make not only tweaks for the compiling process, but also to leave out parts of the app that you have no use for. With Debian's Apt system, you pretty much take what they give you.

**APT:**
* Always works
* Quick
**Portage:**
* Slower
* Gives user greater control

But speed aside, if you're just adding, removing, and searching for packages, there's little difference between:

emerge audacious
and
apt-get install audacious

Both grab the dependencies and install the program.

---

### Post by mips on 2007-07-30
ThinkBuntu summed it up pretty well I would say. I don't see the one being easier than the other.

Portage gives you more control, people just have to keep in mind that it is used in a sourced based distro and that it takes longer to install things.

---

### Post by ThinkBuntu on 2007-07-30
Oh, and there's no graphical frontend really on par with Synaptic for use with Portage (which is pretty much fail-safe). At least if there is, I have yet to use it.

---

### Post by Bachstelze on 2007-07-30
> **ThinkBuntu said:**
> 
**APT:**
* Always works


I have to disagree here. Major problems with Apt - i.e. those who make it unusable - are rare but exist. I've never heard of anyone having issues that serious with Portage.

---

### Post by igknighted on 2007-07-30
> **HymnToLife said:**
> I have to disagree here. Major problems with Apt - i.e. those who make it unusable - are rare but exist. I've never heard of anyone having issues that serious with Portage.

I agree with you completely, but a little clarification:

With Portage, if you do not know how to use it, a great deal of apps will be masked and unable to install/update.  This often gives the impression that portage cannot install these, but it can... you just need to figure out how to un-mask the packages.

While apt rarely makes a user work to "unmask" a package, apt is definitely the more likely of the two to mess something up outside of the user's control.  So if you bork your system with portage, likely it was your fault.  With apt, it is less likely to screw something up yourself, but more likely to mess up on its own.

---

### Post by bread eyes on 2007-07-30
They both suck.

---

### Post by stmiller on 2007-07-31
> **ThinkBuntu said:**
> Oh, and there's no graphical frontend really on par with Synaptic for use with Portage (which is pretty much fail-safe). At least if there is, I have yet to use it.

[URL="http://kuroo.org/"]
Try Kuroo.[/URL]

---

### Post by ThinkBuntu on 2007-07-31
> **stmiller said:**
> [URL="http://kuroo.org/"]
Try Kuroo.[/URL]
Their were so many warnings about Kuroo around the Sabayon forums that I never touched the thing.

---

### Post by igknighted on 2007-07-31
> **ThinkBuntu said:**
> Their were so many warnings about Kuroo around the Sabayon forums that I never touched the thing.

Yeah, Kuroo isn't good.  There is a far less complex (see: not as many options) GUI tool somewhere IIRC that is a bit more stable... but even that isn't that great.

It doesn't make any sense to put a GUI on portage.  Portage needs to be nimble enough to add tons of options, so even if you did put a GUI on it you would have to manually add all the options.  All you would accomplish in the end is slowing down the install more (due to waiting for the GUI).

... Although ...

If you could make a GUI app that could intelligently propose solutions to masked packages and perhaps even implement them without the user ever seeing, that might be worthwhile... but thats way beyond a simple GUI package manager front-end.

---

### Post by ThinkBuntu on 2007-07-31
I'm actually enjoying using Netpkg at the moment. It's nothing particularly special, but it always works fine and is very quick for searching. I have yet to look into any features beyond your typical install, remove, upgrade, and search, but on a system designed to be light, I thankfully don't have to worry as much about stripping down packages.

---

### Post by hanzomon4 on 2007-08-01
Portage fails to work when compiling some packages, this makes me rate apt as better cause every package in the repos installs. Portage also can break things easily if you uninstall something. It's cryptic and therefore not as good as apt, from a certain point of view. 

I honestly don't think you should compare the two, source and pre-compiled packages just gives you different kinds of worms not really more or less.

---

### Post by fistfullofroses on 2007-08-01
I prefer compiling from source, but hey whatever. If I had to choose a package management system it would likely be netpkg or slapt-get.

---

### Post by hanzomon4 on 2007-08-02
> **fistfullofroses said:**
> I prefer compiling from source, but hey whatever. If I had to choose a package management system it would likely be netpkg or slapt-get.

Nothing beats portage if you want to compile from source, although I think ports is simpler.

---

### Post by mike102282 on 2007-08-02
> **bread eyes said:**
> They both suck.

What do you prefer?

---

### Post by 67GTA on 2007-08-02
I'm conflicted. I learned to use Linux with Debian/Ubuntu, so Synaptic/Apt seems normal, and everything else seems ridiculously hard or complex. I really liked the Sabayon 3.3 mini edition, but did not understand the Portage /Emerge way of doing things. I Just ordered the 3.4 DVD and hope to be able to learn how to use Portage/Emerge.

---

### Post by bread eyes on 2007-08-02
> **mike102282 said:**
> What do you prefer?

Do you mean between (APT or Portage) or of any package manager?

---

### Post by ThinkBuntu on 2007-08-02
> **bread eyes said:**
> Do you mean between (APT or Portage) or of any package manager?
Maybe answer both?

---

### Post by fistfullofroses on 2007-08-02
I do not mean automated source install. I mean:

#tar -xvzf blah.tar.gz
#cd blah
#./configure
#make
#make check
#make install

---

### Post by Erunno on 2007-08-03
By the way, there's an alternative to Portage called Paludis which was developed by an ex-Gentoo developer (ex as in: They kicked him out) which is supposedly faster than Gentoo and has some features which Portage doesn't have. When I was still using Gentoo is was still in its infancy so I never gave it a try.

[Paludis / Portage differences]("http://paludis.pioto.org/portagedifferences.html")

---

### Post by bread eyes on 2007-08-03
> **ThinkBuntu said:**
> Maybe answer both?

I guess I'll do that. Between APT and Portage, APT because the way Portage is programed is a joke. Between all of them, Compile.

---

### Post by Frak on 2007-08-05
**Apt**
*Quick
*Space Efficient
Yet
*Give's nearly no control over the package
*Can Break the entire system if not careful

**Portage**
*Give's control
*The Program is usually faster in the longrun
Yet
*If removing packages, it doesn't run a Dependency check on whether other programs are using it.
*Programs can take up large amounts of space (OO.o=3GB), unless using ebuilds
*Installing or updating a package can cause in a ripple effect, causing many programs to stop responding.

IMHO, I prefer Apt.

---

### Post by SunnyRabbiera on 2007-08-05
I personally prefer apt, its brainless easy to use.

---

### Post by pain of salvation on 2007-08-05
Arch's pacman is the best.

---

### Post by termite on 2007-08-07
I like Portage!  After 18 months of Ubuntu (which I enjoyed), I switched to Gentoo and must say I far prefer its package-management (which isn't really package management, more like a way to maintain a source tree).  Ebuilds are easier to read and create than debs.

Yes, compiling stuff takes forever, but there is a speed advantage (not huge, but noticeable) and customizing is so much easier.

I installed Ubuntu on my mother's computer and she loves it.  It's Gentoo all the way for me, though :)

---

### Post by miggols99 on 2007-08-08
> Arch's pacman is the best.
I also prefer Arch's pacman.

**Pacman**
[LIST]
[*]Fast
[*]Removes dependencies (if you do pacman -Rs <pkg name> or if you do pacman -Rd <pkg name> it doesn't remove dependencies)
[*]No control over packages (you can use ABS to build your whole system like Gentoo if you want)
[*]Space efficient
[/LIST]

---

### Post by fwojciec on 2007-08-08
pacman + abs/aur/makepkg is truly ingenious.  it's like apt-get and portage smoothly merged into a single system that can handle both precompiled packages and managed compilation from source.  packaging system is the main reason i use arch linux at the moment and have no thoughts of even trying other distros anymore.

---

### Post by Scheater5 on 2007-08-10
My 2 cents is that it's the individual.  I personally use nothing but aptitude.  I have no use for the massive options and the configurable nature of compiling everything by hand nor with the aid of portage, and good 'ole apt-get works ok but I like the way aptitude handles dependencies better.  A buddy of mine, who runs the LUG at Clemson University, swears by apt-get.  Compiling takes too long for my purposes on a workstation, but when I was turning a dinosaur pc into a server, I at first looked at Gentoo and Sabayon because of portage, but eventually it got a stripped-down Xubuntu and therefore apt (or rather, aptitude).

---

