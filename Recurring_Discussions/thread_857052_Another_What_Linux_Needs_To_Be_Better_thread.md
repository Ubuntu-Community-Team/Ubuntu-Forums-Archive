---
title: "Another What Linux Needs To Be Better thread"
date: 2008-07-12
forum: Recurring Discussions
---

### Post by Yfrwlf on 2008-07-12
Always have to have more of these threads, especially after each Ubuntu release. ;)

While the brainstorm site is great, having a heap of ideas in the same thread can be fun too.

Everyone post your most frustrating problems with Linux, or general ways in which you can vision improvements! :)

**[COLOR="Blue"]1) Standardized packaging API that allows inter-distro program installation.[/COLOR]**

[INDENT]Tired of feeling trapped in one distro version at a time?  Want to install that new program that isn't in the repos, but you feel like throwing your keyboard through your monitor when you hit snags all over the place?  You're not alone!  If a Linux mechanism/API/compatibility layer/standardized packaging container/format was created at some point in order to allow program installation across all Linux distros, you and everyone else would have the freedom to use what you want, when you wanted.  Say goodbye to being locked into distro X for programs YZQ, use any one you like!  Share programs with your friends over the internet!  Save program packages in an archive for later use, never having to worry about compiling them or compatibility with them!  Yes, the future will be much brighter and more free as soon as this gets worked out.  They're working on it now, one of the latest ideas being the [Berlin Packaging API]("http://www.osnews.com/story/19901").  Also see the [LSB packaging workgroup]("http://www.linuxfoundation.org/en/Packaging").[/INDENT]

**[COLOR="Blue"]2) Standardized/modular driver installation.[/COLOR]**

[INDENT]Again, ever stuck with wanting that new piece of hardware to work with Linux, but you want to either stick with an older kernel or distro, or even your newer one doesn't include it or support it fully?  Share drivers online easily with a standardized/common driver installation package format and kernel driver API!  Never again have to teach your grandma to compile her printer drivers each time she upgrades, just find the standardized printer driver, click on it, and you're done!  Enjoy the *true* freedom of using Linux instead of feeling like your sister needs a computer science degree or mastery at programming in order to easily use her operating system![/INDENT]

**[COLOR="Blue"]3) Joystick, webcam, tablet, and other peripheral support.[/COLOR]**

[INDENT]KDE does a much better job with having utilities to configure and calibrate many more peripherals than Gnome does, so it'd be great if Gnome would add these abilities as well, or better yet use the ones that were "made for KDE", which brings me to my fourth and similarly-themed point...[/INDENT]

**[COLOR="Blue"]4) Make everything more cross-compatible and modular, in every way, so any of them can be used anywhere.[/COLOR]**

[INDENT]More APIs, more standard ways of doing things.  Modularity = freedom.  Modularity = smart programming.  The first thing you should do when programming, after you come up with a great idea, is figure out how it will fit in with the existing operating system.  Plan ahead, and make your program talk to popular standards, and it will get used a lot more.  Plugins are popular for a reason, and just think if the plugins themselves could be used with *other* programs as well.  (Insert witty remark about Firefox's popularity here.)  As for KDE and Gnome applications?  It has to stop.  A program should not be locked into the look and feel of one particular desktop environment.  Using a further standardized X GUI language would allow any program to be run inside any DE while retaining the look and feel of that DE.  [wxWidgets]("http://www.wxwidgets.org/") goes a long way towards accomplishing this, now all it needs is the ability to display KDE applications natively as well.  Then, it's a matter of writing the code for the GUI front-end once, and you're done, for all operating systems and desktop environments.  Just one more thing to make using KDE configuration utilities for Gnome easier, so that Gnome can easily utilize some of the good features of KDE if users want it to.  Having a Linux program which is exclusive to one DE only results in fragmentation and duplication of work.[/INDENT]

**[COLOR="Blue"]5) Further help users to get to all the things they need.[/COLOR]**

[INDENT]Good documentation, helpful messages/pop-ups and more feedback in general, a way to find out which devices are supported under Linux and/or a place to **buy** devices that are supported (think the Apple Store, but for Linux), and again, installation package standardization, so that **all** the Linux programs that can replace programs users knew and loved on Windows and Macs can be accessible to them without hoping the thing they need is in the repositories and often being between a rock and a hard place if it's not.[/INDENT]

I want Linux to become the defacto operating system, but these problems plague many users who try it and will keep many users at bay, and greatly slow the adoption rate of Linux.  Again, having a nice, pretty, bundled OS that has a repository with lots of programs in it is good, but not having to worry about what's in the repository, or better yet, being able to use any repository, and not having to compile and fill a repository for every flavor and version of Linux, will allow Linux to go much further beyond what it is now, much more rapidly.  Any, before it gets mentioned, I know that binaries thankfully are download and click to run which is great, but integration with the package manager to add easy remove and update abilities as well as having menu items is very important for users in their search for a user-friendly OS.

---

### Post by p_quarles on 2008-07-12
Moved to Recurring Discussions, as implicitly requested by OP. ;)

---

### Post by karellen on 2008-07-12
to the OP: don't you think you are asking a little too much? ;)

---

### Post by Barrucadu on 2008-07-12
Right, if you want a standardised packaging format, start working on one that is clearly superior to all other current formats, and is so superior that all distros would be a fool not to switch.

---

### Post by madjr on 2008-07-12
> **Barrucadu said:**
> Right, if you want a standardised packaging format, start working on one that is clearly superior to all other current formats, and is so superior that all distros would be a fool not to switch.

it's already here:

[http://0install.net/matrix.html](http://0install.net/matrix.html)

it just needs more volunteers to start **packaging**

great developer

it would be a standard if distros would help the guy and not focus on their **small deb vs rpm war** that's been going on for so long which has only fragmented linux.

deb vs rpm has been the stupidest thing ever:
[http://www.osnews.com/story/19901](http://www.osnews.com/story/19901)

---

### Post by Canis familiaris on 2008-07-12
I agree with only #3 and #5. Rest are very difficult to incorporate.

---

### Post by Yfrwlf on 2008-07-12
Time for another mega-response of blatheringness. :grin:

I was hoping for more ideas other than packaging discussion, but it **is** an important topic. ;)

> **Barrucadu said:**
> Right, if you want a standardised packaging format, start working on one that is clearly superior to all other current formats, and is so superior that all distros would be a fool not to switch.

That's the attitude that is the cause of the format war that Madhr has mentioned, but you may be partially correct in that if there was a format that was much easier than all others, then that potentially could help, but I think at this point more is needed.  Will explain below...

> **madjr said:**
> it's already here:

[http://0install.net/matrix.html](http://0install.net/matrix.html)

it just needs more volunteers to start **packaging**

great developer

it would be a standard if distros would help the guy and not focus on their **small deb vs rpm war** that's been going on for so long which has only fragmented linux.

deb vs rpm has been the stupidest thing ever:
[http://www.osnews.com/story/19901](http://www.osnews.com/story/19901)

More programs using these alternative formats would be nice, and I'm not sure why more don't use Autopackage or Zero Install or whatnot, but I think the key could be a combination of these three steps.

1.  The Berlin Packaging API: It seems to be possibly the lowest-level solution which will hopefully branch out to all distros easily and create a neutral/standard API.  I've said it elsewhere many times, but it never ceases to amaze me how everyone loves HTTP, HTML, FTP, XML, and other standards out there, but that many seem to demonize packaging standards.  Any way, I believe this is probably the best solution if it can allow compatibility with new formats without having to do heavy modification of the existing package managers, and that should be the goal.  The package managers need to modularize/define themselves more so that they only concentrate on what's given to them when it is given in some standardized way, and not care about the silly format of the package itself.

2.  Package managers need to be made to take advantage of the Berlin Packaging API ideally, or to adopt some other kind of system themselves which allows them to read any packaging format and easily add new ones.  If this is made difficult because the existing RPM and DEB formats each have missing information in them, then care in teaching them how to use those *formats* should be taken but dealt with, and emphasis on package formats which contain all of the information necessary to categorize and get any software installed should be made, including updating the RPM and DEB package formats so that they contain this information.

3.  The packages themselves.  Like mentioned above, if DEB and RPM packages need to contain more information so the manager can know how to categorize and install them properly and intelligently, then those formats need to be updated and the old ones depreciated.  Or, a new format is created which contains everything that is necessary.  What I was thinking of is that a container format for packages could make everything much less confusing for everyone.  The way I see it, formats should be an extremely trivial thing as long as they contain what's necessary.  Just like movie or sound file formats can be read by most any music or movie player, they should be readable by any package manager.  Like media formats having containers like AVI, MKV, and others, if Linux had a packaging container format like LNX or whatnot, then RPM, DEB, and other formats could be placed into this, and that would solve file naming confusion as well.  What's better, if existing RPM and DEB files are missing some information that is needed for any package manager to do a clean installation of them, this container format could contain that information to help them out whenever it contained these formats, so in essence it could act as a wrapper, or compatibility layer.

> **Anurag_panda said:**
> I agree with only #3 and #5. Rest are very difficult to incorporate.

But very important, and not impossible.  Nothing ever is, especially with computers.  I actually don't believe the problem is that difficult at all in essence, I think all the muck that has grown up and surrounded this issue has make it much worse.  But, I think all that's truly needed is a simple common method of communication i.e. standard that has to be composed.  All that has to be done is at some point, on some level, the bare essential things that are needed to install a package need to be defined.

You have a user-accessible library?  OK, I'm configured to put those here on this system.  You have a user-accessible binary?  OK, I've decided that on this particular system, I'm putting those here, but there's already a program there which is a different version, and since both versions are stated as being exactly required by two other different packages (meaning the program has a poor API as only the newer one should be needed), I deal with those conflicts by doing XYZ.  In fact, if the packaging systems were made completely modular and dynamic like they should be, you could tell the package manager or the Berlin Packaging API or whathaveyou to install everything to the same file directory structure like Windows has if you wanted to.  Along that same note, if the entire file system was virtual, then you could always go to the same location on any system by typing in something like "cd etc" for configuration or even "cd conf", and be taken to one location where all the configuration files are located, then that would also solve the silly annoying problems of directory structures being different on different distros too.

> **karellen said:**
> to the OP: don't you think you are asking a little too much? ;)

No, I think I'm asking for exactly what Linux needs to evolve and become much better than it is now.  There are many forces out there that want Linux to fragment, and we shouldn't let this happen and I believe solving this is critical.  Distros should not be so segregated from one another, that's silly and foolish.  Combining the time and power of Linux users together in more ways will amplify that power.  Plus, Linux should give you freedom, and users depending on their package managers and repositories along with those repository maintainers to package the programs that they want access to on that particular flavor of Linux is completely outrageous and a huge waste of time.  They have a lot of things they could be doing rather than recompiling programs all the time, that's not where effort in Linux should be focused.  Think about how incredibly wonderful it would be if you had access to **any and all Linux software from your repository**.  Liked that game that was in the last Ubuntu release?  No problem, it's still available!

Some Linux users complain about duplicated effort in other areas, which can be a problem as well if things aren't modularized enough in general, but packaging has to be the biggest waste of effort imaginable.  Computers should compute for you, not require you to be a rocket scientist.  No one should have to worry about Linux packaging other than using a nice tool to package a program once, and then forgetting about it until the next version of their program comes out, and hell, just automate the whole thing so you don't have to do anything at all.  As soon as Linux software packaging is push-button-simple, there'll be no stopping the penguins, and it's all doable. :)

P.S. Not to turn this into a conspiracy theory or darken things, but everyone should also realize that the companies behind distros **do** have an interest in keeping users on their distros.  This motive can be counter-productive for all Linux users if the tools they create aren't modular and portable, if they dig into only their system.  So far I haven't seen it happen too much except for the package manager and this format situation.  The package manager is "on the bottom" so to speak, it's one of the most fundamental pieces of software on your system in a way, so having this problem there where it demands that you need distro version X if you want to install package Y keeps their users in a prison.  If Linux users care about true freedom, modularity, and standards, so that all software is shareable and the choice in Linux distro flavors comes down to how the programs are configured when they are installed, they will support those distributions which support these principals.  A campaign to push for Linux freedom at this point may even be what's necessary to help get this across if certain big Linux companies are purposefully not giving interest into resolving this problem due to their own self interests.

---

### Post by Sealbhach on 2008-07-12
I find all the different file-types I download very confusing.

tar
tar.gz
bzr
bin

I just want them to behave like a deb file, just double click to run it.


.

---

### Post by Xzallion on 2008-07-12
> **Sealbhach said:**
> I find all the different file-types I download very confusing.

tar
tar.gz
bzr
bin

I just want them to behave like a deb file, just double click to run it.


.

tar and tar.gz are compression formats simliar to .zip and .rar. They are just compressed data and not a binary so click and run should just be to uncompress them and last I checked this was the case in Ubuntu.

.bzr is a package format similar to .deb, .rpm, etc and just needs the package manager installed for it to work.  I don't know if multiple package managers can run together without causing problems, and I imagine they would cause all sorts of problems for the each other.

.bin is just a disk image like .iso.  You just need an extractor, and I think the one in ubuntu supports this you just have to associate it.

---

### Post by Yfrwlf on 2008-07-12
> **Sealbhach said:**
> I find all the different file-types I download very confusing.

tar
tar.gz
bzr
bin

I just want them to behave like a deb file, just double click to run it.


.

Agreed, things are rocky out there for new Linux users still.  However, there will always be at least a few formats for movies, sound, compressed files, and software packages, but if there was more emphasis on using good container formats, that would go a long way to solving that problem.  Containers are good because they allow a diversity of different formats while still showing the simple parts to end-users unless they want to look inside the container.  More often than not though, they don't really care as long as it's a good format that works and allows them to get to the media they want.  Same goes with packaging and everything else.

A .LINUX or .LNX file which contained all the different preferred Linux software packaging types would be wonderful.  tar, tar.gz, bzr, bz2, bin, deb, rpm, source files, ebuilds, whatever! :)  Linux users just need package managers or subsystems or wrappers or APIs or whatever to give them the ability to read all of them and to allow new ones to be easily added on in the future.

---

### Post by Yfrwlf on 2008-07-12
> **Xzallion said:**
> tar and tar.gz are compression formats simliar to .zip and .rar. They are just compressed data and not a binary so click and run should just be to uncompress them and last I checked this was the case in Ubuntu.

True, they were concerned because offering plain compressed binary packages is one of the methods currently for getting Linux software.  Since these formats of course contain no data about where the files should be placed, it'd be difficult to have the package manager deal with them in the way they were supposed to be installed, but it still could deal with them.  The package manager could offer to deal with the file, and it could store them in a special place for simple uncompressed binaries, and could either ask the user for a name for the program or just use the name of the compressed file.  That way, the user could "uninstall" them from the manager interface.  I don't know, just an idea, but of course a much better solution is that a standard package format/container replaces this compressed program distribution system. :)

> **Xzallion said:**
> .bzr is a package format similar to .deb, .rpm, etc and just needs the package manager installed for it to work.  I don't know if multiple package managers can run together without causing problems, and I imagine they would cause all sorts of problems for the each other.

Unless the package manager was just a simple program which listened to a universal configuration file which told managers where the user wanted files placed, and if package managers dealt with dependency resolution issues in the same way because they and the package format had all the information necessary to cope with anything thrown at them (within a confined scope of some standard packaging API), then yes they could cope side by side I think. ;)

I'd love it if things become that modular, but I think just making each package manager able to read multiple package formats would hopefully be enough.

> **Xzallion said:**
> .bin is just a disk image like .iso.  You just need an extractor, and I think the one in ubuntu supports this you just have to associate it.

Actually I think .bin is used for binary files sometimes, but now I can't find any examples of it. >.<  Oh and don't forget .run files. :P  I don't know if a package manager could deal with all of these, well, I'm sure it could be done but perhaps it wouldn't be that appropriate.  At the very least, any files which are based on scripts will be replaced with proper package formats, like .run and such, since there's no need to make a jerry-rigged script to accomplish what a simple package format will do and make much easier.

---

### Post by madjr on 2008-07-12
also wanted to add that even if ubuntu is the popular distro of the moment (just between **geeks**), things could change.

**pre-installed** base of other distros will overtake the linux market (not only ubuntu market):

Asus = xandros
HP = Suse
Lenovo = Suse
Dell = Ubuntu
Everex = [gOS]("http://www.thinkgos.com/")
Acer = Linpus linux (Taiwanese)
[Zonbu]("http://www.zonbu.com/home/") = Zombu OS
Intel (classmate-pc) = Mandriva
Sears = [Freespire]("http://www.freespire.org/")
etc = etc

you see everyone is using a **different** distro and brand

no one distro will ever dominate. If the **first experience is not good** they go back to **[COLOR="DarkRed"]Windows[/COLOR]** or **[COLOR="RoyalBlue"]Mac[/COLOR]**, plain and simple.

They wont go looking for other distros (wth is a distro?), only **geeks** do that.


Standards need to be in place if we are ever to really **compete with Mac and windows**.

---

### Post by cardinals_fan on 2008-07-12
> **madjr said:**
> also wanted to add that even if ubuntu is the popular distro of the moment (just between **geeks**), things could change.

**pre-installed** base of other distros will overtake the linux market (not only ubuntu market):

Asus = xandros
HP = Suse
Lenovo = Suse
Dell = Ubuntu
Everex = [gOS]("http://www.thinkgos.com/")
Acer = Linpus linux (Taiwanese)
[Zonbu]("http://www.zonbu.com/home/") = Zombu OS
Intel (classmate-pc) = Mandriva
Sears = [Freespire]("http://www.freespire.org/")
etc = etc

you see everyone is using a **different** distro and brand

no one distro will ever dominate. If the **first experience is not good** they go back to **[COLOR="DarkRed"]Windows[/COLOR]** or **[COLOR="RoyalBlue"]Mac[/COLOR]**, plain and simple.

They wont go looking for other distros (wth is a distro?), only **geeks** do that.


Standards need to be in place if we are ever to really **compete with Mac and windows**.
What's your point?  People get the distro that comes with their PC.  What's the problem?

The problem with standardized packages is that there is no one perfect format.

---

### Post by aysiu on 2008-07-12
> **madjr said:**
> 
no one distro will ever dominate. It's possible that no one distro will ever dominate, but I don't know what you're basing this absolute statement on.

As a matter of fact, it's also very possible that one distro *will* dominate (at least for home consumers and businesses, not self-professed geeks).

All it takes is for *one* Linux preinstalled option to really take off. If that happens, whatever that distro is will likely become the dominant distro. And by "take off," I mean in an iPod way, not an Eee way.

---

### Post by madjr on 2008-07-12
> **cardinals_fan said:**
> What's your point?  People get the distro that comes with their PC.  What's the problem?

The problem with standardized packages is that **there is no one perfect format.**

there is no perfect format not because is not possible, but simply because the devs are **not working together** like the OP mentioned

---

### Post by SunnyRabbiera on 2008-07-12
The package installer unification thing has been played around with for years, I am opposed to it...

---

### Post by madjr on 2008-07-12
> **SunnyRabbiera said:**
> The package installer unification thing has been played around with for years, I am opposed to it...

cons ?

---

### Post by Yfrwlf on 2008-07-12
> **cardinals_fan said:**
> What's your point?  People get the distro that comes with their PC.  What's the problem?

The problem with standardized packages is that there is no one perfect format.

See the original post for the list of problems.  These problems especially plague lesser-known distros.  The point is your distro flavor of choice should not lock you into your selection of programs.  The point is being able to install *any program easily* on Linux, regardless of where it's located, so that programs become *actually* sharable and distributable.

Again, if you still don't understand by now, all I can do is tell you that many users out there hate Linux because of it's limited ability to get stuff done and install software without being a master at programming due to fragmentation problems like the ones I've mentioned.  If you want more use cases, I'll give you them, but hopefully you understand now.  Regardless of what you believe, users are having big problems.  If you want to help, you'll have to acknowledge this fact.

> **aysiu said:**
> It's possible that no one distro will ever dominate, but I don't know what you're basing this absolute statement on.

As a matter of fact, it's also very possible that one distro *will* dominate (at least for home consumers and businesses, not self-professed geeks).

All it takes is for *one* Linux preinstalled option to really take off. If that happens, whatever that distro is will likely become the dominant distro. And by "take off," I mean in an iPod way, not an Eee way.

That's probably what Canonical, Novell, Red Hat, and others would love to see happen.  Linux users choosing their distros just because of their software selection.  That's not freedom.  Freedom is being able to find, install, and use a program regardless of where it's located.  Freedom is being able to use the distro you want with the software you want.  The only difference there should be between distros is the default software it comes with, and the default configuration and ease-of-use of their configuration files, those are really the only two I can think of.  Everything else should be completely modular, including the kernel, but for now at the very least just being able to install any software.  I want direct access to the software that is provided by third parties without having to worry about compiling or specific package support for the distro and distro version I happen to be running, and **so do those third-party vendors**.  If you want more programs for Linux, and want to share programs with users regardless of their distro flavor, then you want this to be easy to accomplish.  The LSB has gone a long way to help ensure software is portable with it's binary compatibility, and with the [Berlin Packaging API]("http://www.osnews.com/story/19901") hopefully it will be just one more small step that will make a huge difference.

I know, wanting there to be programs and games made by vendors for Linux that can be sold in stores and easily downloaded and installed from the net is crazy.

I'm such a loon. </sarcasm>

> **madjr said:**
> there is no perfect format not because is not possible, but simply because the devs are **not working together** like the OP mentioned

That's possible that there could be a combined format that "does it all", but that's a format war and it can easily be avoided.  Just like arguing if Blu-Ray or HD-DVD is better, or NFS or SMB, or DivX or Xvid, it may be a fairly lost cause.  All that needs to happen is compatibility for all or most all of the existing formats, and a way to add new ones easily.  If either RPM or DEB or any of the others do not contain enough information for correct program installation, they should be depreciated and revisions made and/or an entirely new format or container format.  I know that they are working on DEB2, and perhaps RPM is working on updating theirs as well, so during these corrections they need to include what is required to make them installable by any package manager.

Again though, this [Berlin API]("http://www.osnews.com/story/19901") could be the best solution, so I'll support whatever solution can actually get done to accomplish this.  If Ubuntu refuses to adopt it, I'll use some other distro which allows me to install whatever software I want. ;)

> **SunnyRabbiera said:**
> The package installer unification thing has been played around with for years, I am opposed to it...

All problems are solvable.  Standardization can be done in such a way that it doesn't take away any freedoms for developers or users, but instead gives them.  Standardization can be done in such a way that it is hidden from both developers and users, and gets out of there way.  If implemented properly, it can allow extensible freedom into the distant future and adapt and evolve, while still making all software usable without any cost to performance (though certainly programs could be updated to take advantage of new features/libraries or whatnot, but that happens any way).  That, right there, would be a great feature.  There's no reason for being opposed to a great feature.  Are you also opposed to the ODF, HTML, and other standards as well?  I'll bet you like the idea of being able to access documents and web pages regardless of what computer you're on, so don't be hatin' on the freedom and benefits that cross-distro package installation would give you.  See features for what they are, and if you don't like them then don't use them.  Go back to telnet and BBSes for your internet use, and if you want to compile every program before you use it that's fine, and if you only want access to what's in your distro's repositories, again, your choice.

There's a lot of us out here that want more choice and more freedom, and we'll support standards as long as those standards are good.

---

### Post by p_quarles on 2008-07-12
> **Yfrwlf said:**
> If you want more use cases, I'll give you them, but hopefully you understand now.  Regardless of what you believe, users are having big problems.  If you want to help, you'll have to acknowledge this fact.
Yes, please give specific examples. I simply can't think of any significant, stable application that isn't packaged in a way that makes it super-easy to install on both rpm- and dpkg-based distributions. In other words, there is already a great deal of centralization in terms of package management, and consolidating it further is *not going to help* with the relatively small number of fringe applications that don't get packaged in a way that is useful for the average non-geek user.

---

### Post by madjr on 2008-07-12
> **p_quarles said:**
> Yes, please give specific examples. I simply can't think of any significant, stable application that isn't packaged in a way that makes it super-easy to install on both rpm- and dpkg-based distributions. In other words, there is already a great deal of centralization in terms of package management, and consolidating it further is *not going to help* with the relatively small number of fringe applications that don't get packaged in a way that is useful for the average non-geek user.

if this was totally how it is then eeePC users would not have to dump xandros just to install an app and go back to windows.

binaries are only available to particular distros or distro versions.

it's a big mess.

---

### Post by popch on 2008-07-12
> **Yfrwlf said:**
> These problems especially plague lesser-known distros. .... .

Could there possibly a reason for the lesser-known distros being, well, less known?

> **Yfrwlf said:**
> Again, if you still don't understand by now,  ... Regardless of what you believe, users are having big problems. ...  .

I suggest you check your rhetorics. 

> **Yfrwlf said:**
> Freedom is being able to find, install, and use a program regardless of where it's located. Freedom is being able to use the distro you want with the software you want. .

Who keeps you from finding and using a distro and the programs of your choice? Do we have to remind you that freedom carries the burden of learning and doing your own research?

---

### Post by 23meg on 2008-07-12
The reason you can't simply pick any binary and run it on any distro release is not that there isn't a unified packaging standard / API, but lack or shortage of binary compatibility. Few people in the free software world argue for the benefits of constantly striving for binary compatibility, which have little significance when weighed against the disadvantages. 

In simpler terms, the problem, if you see it as such, lies for the most part at the content (application and library code itself), not the form (packaging). Misplacing it will lead you to all sorts of weird non-solutions such as "a GUI for alien", "a common packaging format", "double click to install RPMs", etc.

---

### Post by cardinals_fan on 2008-07-12
> **madjr said:**
> there is no perfect format not because is not possible, but simply because the devs are **not working together** like the OP mentioned
What, in your opinion, would this perfect format be?  What would it look like?  How would it be written?
> **Yfrwlf said:**
> See the original post for the list of problems.  These problems especially plague lesser-known distros.  The point is your distro flavor of choice should not lock you into your selection of programs.  The point is being able to install *any program easily* on Linux, regardless of where it's located, so that programs become *actually* sharable and distributable.

Again, if you still don't understand by now, all I can do is tell you that many users out there hate Linux because of it's limited ability to get stuff done and install software without being a master at programming due to fragmentation problems like the ones I've mentioned.  If you want more use cases, I'll give you them, but hopefully you understand now.  Regardless of what you believe, users are having big problems.  If you want to help, you'll have to acknowledge this fact.

I haven't experienced this.  Please do list some programs that people are having trouble installing.
> **madjr said:**
> if this was totally how it is then eeePC users would not have to dump xandros just to install an app and go back to windows.

binaries are only available to particular distros or distro versions.

it's a big mess.
*sighs*

People are dumping Xandros and returning to XP because they want to run **Windows** software, not software for other distros.

---

### Post by Sealbhach on 2008-07-12
> **Xzallion said:**
> tar and tar.gz are compression formats simliar to .zip and .rar. They are just compressed data and not a binary so click and run should just be to uncompress them and last I checked this was the case in Ubuntu.

.bzr is a package format similar to .deb, .rpm, etc and just needs the package manager installed for it to work.  I don't know if multiple package managers can run together without causing problems, and I imagine they would cause all sorts of problems for the each other.

.bin is just a disk image like .iso.  You just need an extractor, and I think the one in ubuntu supports this you just have to associate it.

Thanks for taking so much time to explain,it's very good of you.  But as a moderate user, I want just one format that will work with one click and doesn't give me a lot of backchat.

Like .exe in windows.

That's what people like me want from software - we don't want to know all the fiddly details.


.

---

### Post by madjr on 2008-07-12
> **cardinals_fan said:**
> 

*sighs*

People are dumping Xandros and returning to XP because they want to run **Windows** software, not software for other distros.

is that the case for everyone who dumps xandros?

some only want to update their software but binaries are not available in the xandros repos, or the web (even that of FOSS).

the easiest option is simply go back to windows and run your FOSS there.

another user lost.

here i quote an user:

[COLOR="DarkSlateGray"][I]
got this as a replacement for **old win98se**. It won&#8217;t automaticly **load any program even the ones made for linux.** I will have to return it for a refund.[/I][/COLOR]

---

### Post by cardinals_fan on 2008-07-12
> **madjr said:**
> is that the case for everyone who dumps xandros?

some only want to update their software but binaries are not available in the xandros repos, or the web (even that of FOSS).

the easiest option is simply go back to windows and run your FOSS there.

another user lost.

here i quote an user:

[COLOR="DarkSlateGray"][I]
got this as a replacement for **old win98se**. It won&#8217;t automaticly **load any program even the ones made for linux.** I will have to return it for a refund.[/I][/COLOR]
I was generalizing - always dangerous.  But the majority of Xandros users who switch to Windows do so for Windows software.

---

### Post by Yfrwlf on 2008-07-12
> **p_quarles said:**
> Yes, please give specific examples. I simply can't think of any significant, stable application that isn't packaged in a way that makes it super-easy to install on both rpm- and dpkg-based distributions. In other words, there is already a great deal of centralization in terms of package management, and consolidating it further is *not going to help* with the relatively small number of fringe applications that don't get packaged in a way that is useful for the average non-geek user.

Geez why is this so hard to grasp?  You want me to give you a list of programs which don't provide *DEB* files for the *specific version* of *Ubuntu* that you're using?  I don't think the forum moderators would appreciate me spamming a thread like that.  I really don't think it's necessary, because anyone sane should know that of course it's impossible to have a repository for every version of every distro for every program they could want, and the majority of programs on so-called "third-party" websites typically have one or more of the following: source files, straight compressed binaries, or RPMs.  Good luck finding many examples of *software packages* that you can click and install.  I hate repeating myself, but what is needed is for package managers to be intelligent enough to install Linux software, always, period.  It's not at all impossible.

> **popch said:**
> Could there possibly a reason for the lesser-known distros being, well, less known?

Who keeps you from finding and using a distro and the programs of your choice? Do we have to remind you that freedom carries the burden of learning and doing your own research?

I stated that you should not have to choose a distro based on the software it has in it's repositories.  We want more freedom than that.  We want a **better** solution.  If you don't care for it yourself and are happy with the way things are now, so be it, but me and many others do care, and you wanting us to shut up and be happy with what we have the repositories will never work on us, because we're not, and users switch back to Mac and Windows because of this problem, not to mention there are less Linux programs shared on the internet because of it, among other things.  Everyone would have much more choice if they could use the software they want from anywhere, how is that at all hard to understand?

Windows and Mac are nice because they offer a solid API to target, so you can send programs to others and they will be able to use them easily.  All Linux has to do is refine it's API in terms of packaging, since it already has the ABI mostly defined, and poof, you can install RPMs in Ubuntu and DEBs in Fedora and everyone will want that capability built into their distro and package managers so they can have access to programs regardless of their distro.  Linux only has a 2-10% market share, it doesn't deserve to be fragmented times the number of distros that exist, it needs to grow more, faster, and did I mention the huge power consumption wasted on recompilation of software for different distros has to be pretty staggering?  Save trees, buy electric cars, eat your veggies, and use Linux distros that give you the most freedom while supporting changes that will give you more. *pant*

> **23meg said:**
> The reason you can't simply pick any binary and run it on any distro release is not that there isn't a unified packaging standard / API, but lack or shortage of binary compatibility. Few people in the free software world argue for the benefits of constantly striving for binary compatibility, which have little significance when weighed against the disadvantages. 

In simpler terms, the problem, if you see it as such, lies for the most part at the content (application and library code itself), not the form (packaging). Misplacing it will lead you to all sorts of weird non-solutions such as "a GUI for alien", "a common packaging format", "double click to install RPMs", etc.

No matter where the problem lies, it needs to be solved.  At some point, on some level, a common language needs to be adopted to allow programs to run, for packages and everything else.  It's entirely possible to keep binary compatibility, and for a large part Linux does retain that compatibility.  When and where it doesn't though, that needs to be fixed of course, and it needs to be extended for newer, faster, better methods of running programs.

The fact that we can't install an RPM easily is a problem.  The fact that we can't use a package manager which is compatible with all the different kinds of formats so we can install whatever software I want to is a problem.  The fact that package file types are being used which don't allow their installation on any system, if that's the case, is a problem.  We want access, to all programs, easily, anytime, anyplace.  It's a great feature.

> **Sealbhach said:**
> Thanks for taking so much time to explain,it's very good of you.  But as a moderate user, I want just one format that will work with one click and doesn't give me a lot of backchat.

Like .exe in windows.

That's what people like me want from software - we don't want to know all the fiddly details.


.

Thanks.  See, proof, a Linux user is having trouble.  They're not the first.  If none of you want to offer solutions to this problem, then you're not helping anyone.

Whether this problem is solved by means of package managers being made compatible with the common or all of the Linux software package formats that are out there, or an API being adopted on some level allowing for this to happen, or the LSB being extended, or a new package format replacing the existing ones because the existing ones don't define enough information, or the existing formats being updated so that they do, myself and many others will stand in support of this system if it's an open, flexible, extensible standard that *allows cross-distro Linux program interoperability*.  I mean geezus, I moved to Linux so that I could jump onto open standards.  Java was great because it's cross-platform, and yet Linux is having a hard time even being cross-distro?

I will use whichever distro solves this problem and starts using it.  Hopefully ISVs will choose the best format whether it be a container or package or system, it will be an open format, and I will support that distro and use it so that I can have access to ALL Linux software.

---

### Post by p_quarles on 2008-07-12
> **Yfrwlf said:**
> Geez why is this so hard to grasp?
Don't accuse people of failing to "grasp" things when they are in fact disputing your points.

> You want me to give you a list of programs which don't provide *DEB* files for the *specific version* of *Ubuntu* that you're using?
No. An *example* is a single instance which stands for a group of similar things. That's what I asked for -- not a comprehensive and exhaustive list. 

The rest of your point is just moving the goal posts. Initially you were asking for a unified packaging system, but now you are pointing to a need for repackaged applications for each major release of each distribution. As 23meg said, this has nothing to do with packaging and everything to do with binary compatibility. Having Fedora and Sidux use the same packaging system would not have the slightest impact on this problem.

> I don't think the forum moderators would appreciate me spamming a thread like that.
I don't appreciate the attacking tone you are taking when someone questions your premises. You ought to be able to discuss the points without resorting to belittling those who disagree with you. 

> I really don't think it's necessary, because anyone sane should know that of course it's impossible to have a repository for every version of every distro for every program they could want, and the majority of programs on so-called "third-party" websites typically have one or more of the following: source files, straight compressed binaries, or RPMs.  Good luck finding many examples of *software packages* that you can click and install.  I hate repeating myself, but what is needed is for package managers to be intelligent enough to install Linux software, always, period.  It's not at all impossible.
Perhaps it's not impossible, but there are major barriers to such a thing, and it has nothing to do with package management software.

---

### Post by cardinals_fan on 2008-07-12
> **Yfrwlf said:**
> Geez why is this so hard to grasp?  You want me to give you a list of programs which don't provide *DEB* files for the *specific version* of *Ubuntu* that you're using?  I don't think the forum moderators would appreciate me spamming a thread like that.  I really don't think it's necessary, because anyone sane should know that of course it's impossible to have a repository for every version of every distro for every program they could want, and the majority of programs on so-called "third-party" websites typically have one or more of the following: source files, straight compressed binaries, or RPMs.  Good luck finding many examples of *software packages* that you can click and install.  I hate repeating myself, but what is needed is for package managers to be intelligent enough to install Linux software, always, period.  It's not at all impossible.

An exhaustive list isn't necessary.  I'd just appreciate hearing about a few programs that you feel are major issues, because I haven't seen any.

BTW, straight binaries are totally "click and install".

---

### Post by Yfrwlf on 2008-07-12
> **p_quarles said:**
> Don't accuse people of failing to "grasp" things when they are in fact disputing your points.

No. An *example* is a single instance which stands for a group of similar things. That's what I asked for -- not a comprehensive and exhaustive list.

I don't care where the problem is, that doesn't make it any less of a problem, whether it's in package formats or managers or compatibility in general.  If you have input on where the problem is, that's fine and I'm not belittling that, I'm belittling anyone who says there's no problem when there is, because by saying that they belittle users like me who have a big problem with it.  Of course, no one should be belittling anyone else, so I apologize. :)

You asking that question led me to believe that you have failed to grasp what I'm saying otherwise I don't see why you'd ask if you understood already that it was a problem, because then I wouldn't have to prove it to you, but I'll humor you any way.  Enemy Territory: Quake Wars.  They offer a binary script, so the package manager has no knowledge of it, it doesn't solve easy software removal with any package managers because it doesn't hook into any of them, nor does it offer updates.  It's very static, and while being portable it doesn't have anything to do with the problems I pointed out.  The reason it's not a DEB is because it would ostracize Red Hat-based distros and others.  The reason it's not a RPM is because it would ostracize Debian-based distros.  They release it like that because as of right now, there is no good standard Linux packaging format which is compatible with all distros.

> **p_quarles said:**
> The rest of your point is just moving the goal posts. Initially you were asking for a unified packaging system, but now you are pointing to a need for repackaged applications for each major release of each distribution. As 23meg said, this has nothing to do with packaging and everything to do with binary compatibility. Having Fedora and Sidux use the same packaging system would not have the slightest impact on this problem.

I was told that the Linux ABI was solid, and so far it seems to be.  I've downloaded several programs which were simple binaries, and the programs run well.  There definitely is a packaging problem too though regardless of ABI compatibility issues.

> **p_quarles said:**
> I don't appreciate the attacking tone you are taking when someone questions your premises. You ought to be able to discuss the points without resorting to belittling those who disagree with you.

Perhaps it's not impossible, but there are major barriers to such a thing, and it has nothing to do with package management software.

It is very real and needs to be solved.  Would you care to voice any potential solutions to this problem, or do you not really care to see it fixed?  If you're saying packaging wasn't an issue, why are developers working on it's solution with the Berlin/LSB Packaging API?  If compatibility is also an issue, I guess the LSB needs to get it's butt in gear, or something needs to happen someplace, doesn't it? :)

As Ian Murdock put it, today, [software installation sucks on Linux]("http://ianmurdock.com/2006/12/15/software-installation-on-linux-today-it-sucks-part-1/"), but [tomorrow hopefully it won't]("http://ianmurdock.com/2006/12/19/software-installation-on-linux-tomorrow-it-wont-with-some-cooperation-part-2/").

Read about the [Burgdorf Packaging API here]("http://www.linuxfoundation.org/en/Burgdorf_Packaging_API").

> **cardinals_fan said:**
> An exhaustive list isn't necessary.  I'd just appreciate hearing about a few programs that you feel are major issues, because I haven't seen any.

BTW, straight binaries are totally "click and install".

You sound like you may not have read my first post or you just didn't understand, I know it was long.  I've already spoken about binaries, yes I know you click on them to run them, I'm talking about software packages, not compressed archives.  I listed the limitations of these compared to a nice program package which installs and can be easily removed later and even updated if the package contains a URL for it, all from the native systems package manager.  Yes, I'm glad simple binaries exist, and that's the reason why the large companies which support Linux put them out there, but a packaging solution is needed to make software installation suck less.  There are so many reasons, licensing being another one of them.  We need standards to solve this problem, or for the solutions that do exist to be usable by the existing package managers, just, whatever it takes to get software installed cross-distro in Linux.

---

### Post by cardinals_fan on 2008-07-12
> **Yfrwlf said:**
> 
You sound like you may not have read my first post or you just didn't understand, I know it was long.  I've already spoken about binaries, yes I know you click on them to run them, I'm talking about software packages, not compressed archives.  I listed the limitations of these compared to a nice program package which installs and can be easily removed later and even updated if the package contains a URL for it, all from the native systems package manager.  Yes, I'm glad simple binaries exist, and that's the reason why the large companies which support Linux put them out there, but a packaging solution is needed to make software installation suck less.  There are so many reasons, licensing being another one of them.  We need standards to solve this problem, or for the solutions that do exist to be usable by the existing package managers, just, whatever it takes to get software installed cross-distro in Linux.
I did read the first post, but I wasn't clear with my response.  My point is simply that asking for a unified package standard is not going to make it happen.  Until I see clear, achievable goals in this regard, I put it in the "not going to happen and not worth worrying about" category.  I'm not convinced that the Berlin API represents a step in the right direction.  Anyway, I think that you underestimate the value of simple binaries.  I run my web browser (Opera) from a binary downloaded from their site, and here are a few advantages:

* Software versions.  I can run two different versions of Opera at once, through different binaries.
* Portability.  I can move this binary to any distro and have it run fine.
* Control.  I control every part of the app, because it's all stored in a folder in my home directory.

I'm certainly not saying that EVERY app should be distributed this way, but it's a very decent approach for smaller programs such as browsers or basic utilities.

---

### Post by p_quarles on 2008-07-12
> **Yfrwlf said:**
> I don't care where the problem is, that doesn't make it any less of a problem, whether it's in package formats or managers or compatibility in general.
The location of the problem matters a great deal for the kind of solution that would actually make a difference. 

> If you have input on where the problem is, that's fine and I'm not belittling that, I'm belittling anyone who says there's no problem when there is, because by saying that they belittle users like me who have a big problem with it.  Of course, no one should be belittling anyone else, so I apologize. :)
I would not deny that there are problems, but I tend to think that there are good reasons why obvious solutions (e.g., universal package managers) haven't already been implemented. One of the main reasons, in my view, is the fact that the benefits of such a solution may be insignificant compared to the problems it would create. It would require, in all likelihood, major overhauls to Red Hat, Debian, and their respective offshoots (and to a lesser extent, Gentoo and its derivatives). Many distributions, in all likelihood, would refuse to adopt it on the principal that it breaks backward compatibility or requires redundancy. This, in turn, makes it less likely that companies like id would ever have any interest in repackaging their software in accordance with this new, unused "standard." 

> You asking that question led me to believe that you have failed to grasp what I'm saying otherwise I don't see why you'd ask if you understood already that it was a problem, because then I wouldn't have to prove it to you, but I'll humor you any way.  Enemy Territory: Quake Wars.  They offer a binary script, so the package manager has no knowledge of it, it doesn't solve easy software removal with any package managers because it doesn't hook into any of them, nor does it offer updates.  It's very static, and while being portable it doesn't have anything to do with the problems I pointed out.  The reason it's not a DEB is because it would ostracize Red Hat-based distros and others.  The reason it's not a RPM is because it would ostracize Debian-based distros.  They release it like that because as of right now, there is no good standard Linux packaging format which is compatible with all distros.
That's an old example. Commercial binaries that have been released in the recent past (Opera, Skype and VirtualBox spring to mind) are routinely packaged for several major distros, including Ubuntu. 

Anyway, I asked for an example because I wanted to get a clearer picture of what you consider to be the problem, and I'm still seeing moving goal posts. Initially you said:
> **Yfrwlf said:**
> Again, if you still don't understand by now, all I can do is tell you that many users out there hate Linux because of it's limited ability to get stuff done and install software without being a master at programming due to fragmentation problems like the ones I've mentioned.  If you want more use cases, I'll give you them, but hopefully you understand now.  Regardless of what you believe, users are having big problems.  If you want to help, you'll have to acknowledge this fact.
ET doesn't require you to be a programmer to install it. The problem, as you say, is that it doesn't respect packaging standards. This particular instance has to do neither with binary incompatibility *nor* with the lack of a standard universal package manager: it has everything to do with the fact that the manufacturer (id) declined to respect package management standards to begin with. That, in turn, probably has more to do with when it was released than with anything else. 

I'm all for Linux getting better. What I have a problem with is the "solutions" that provide the illusion of user-friendliness but actually just reduce the flexibility of the platform.

---

### Post by 23meg on 2008-07-12
[QUOTE=Yfrwlf]I hate repeating myself, but what is needed is for package managers to be intelligent enough to install Linux software, always, period. It's not at all impossible.[/QUOTE]

No. What you fail to understand is that unless the software (libraries + applications) in question are capable of running together, what package manager you use is irrelevant. You can have the "unified" package manager of your dreams that's capable of operating with every package format known to man, yet unless the content of the packages in question, the actual software, can work together, it will be of no use.

[QUOTE=Yfrwlf]It's entirely possible to keep binary compatibility, and for a large part Linux does retain that compatibility.[/QUOTE]

Of course it is, in theory. It's just that 99% of the people who work on the actual code don't see any benefit in keeping it, and I don't see a reason to take your word over theirs. 

And no, Linux is famous for constantly breaking ABI with each release (except for the userspace interface, which has always been stable). Most userspace libraries aren't too different either. 

[QUOTE=Yfrwlf]The fact that we can't install an RPM easily is a problem. [/QUOTE]

No it's not, and as long as you keep repeating that it is like a broken record, you won't even come close to realizing the actual problems.

[QUOTE=Yfrwlf]The fact that we can't use a package manager which is compatible with all the different kinds of formats so we can install whatever software I want to is a problem.[/QUOTE]

That's like complaining that your local car vendor only ships the five cheapest models of cars and you're stuck with those when you can't even afford the cheapest one. Even if you came up with your ideal package manager tomorrow, you wouldn't be able to actually utilize it to "install whatever software you want" on any release of any distro. 

[QUOTE=Yfrwlf]I was told that the Linux ABI was solid, and so far it seems to be.[/QUOTE]

Depends on what you call "the Linux ABI". Do a search for stable_api_nonsense.txt (no kidding) and read it.

---

### Post by Yfrwlf on 2008-07-13
Stable platofrms exist.  Linux could be one too, if those involved had the right attitude and wanted it to.

And I thought the Windows upgrade treadmill was bad...

I hope Linux can be stabalized as a platform so that it can be targeted for software development without recompilation.  I will support whatever distributions or standards that emerge in favor of this.

---

### Post by madjr on 2008-07-13
> **Yfrwlf said:**
> Stable platofrms exist.  Linux could be one too, if those involved had the right attitude and wanted it to.

And I thought the Windows upgrade treadmill was bad...

I hope Linux can be stabalized as a platform so that it can be targeted for software development without recompilation.  I will support whatever distributions or standards that emerge in favor of this.

+1

This reminds me of the recent case of **ufw** (**un**complicated firewall...), the sponsors sweared by that it did not need a GUI. Well guess what, 2 weeks later (after lots of **rants**) a GUI was released because it was not so "**un**complicated" as they thought.

Linux might be **OPEN** Source, but most of it's developers have the most **CLOSED MIND SETS** ever.

we could get this solved if we locked those guys in a room a few hours, because clearly they have never sat down and discussed this in their lives. It's all about **[COLOR="Red"]Politics[/COLOR]**, they just need to solve their differences once and for all.

**in summary** the only responses i see here with all these **tech jargons**  is "**leave the problem as is**"

ps: someone will surely counter-reply this... saying once again to "leave it as is"

---

### Post by Yfrwlf on 2008-07-13
> **madjr said:**
> +1

This reminds me of the recent case of **ufw** (**un**complicated firewall...), the sponsors sweared by that it did not need a GUI. Well guess what, 2 weeks later (after lots of **rants**) a GUI was released because it was not so "**un**complicated" as they thought.

Linux might be **OPEN** Source, but most of it's developers have the most **CLOSED MIND SETS** ever.

we could get this solved if we locked those guys in a room a few hours, because clearly they have never sat down and discussed this in their lives. It's all about **[COLOR="Red"]Politics[/COLOR]**, they just need to solve their differences once and for all.

**in summary** the only responses i see here with all these **tech jargons**  is "**leave the problem as is**"

ps: someone will surely counter-reply this... saying once again to "leave it as is"

Right, that seems to be the way it is because the only responses I've gotten here so far is "it can't work" and "leave it as it is".  The fact the LSB exists proves that many others are interested in having a standardized Linux platform, so the only problem then is it simply needs to be extended a little bit.  For some reason, whether political/business or whatnot, packaging was left out of the LSB, but now there's this push to bring it back in which I hope is successful.

Compatibility should be a feature of any OS, and so we need distros which tout this as a great feature of using their distro.  The Linux Foundation provides LSB  compatibility checking tools for this and a [list of distros which are LSB compliant]("https://www.linuxfoundation.org/lsb-cert/productdir.php?by_prod").  The latest version of Ubuntu in the list is still 6.06 Dapper, but maybe they will try to add 8.04 as well soon I hope.

So, to sum up, distros need to be binary compliant as well as incorporate some sort of packaging standard as well, and all of this needs to be strongly supported and touted as a feature.  I know both of us greatly appreciate such a feature, and I know a lot of other Linux users out there would also love not to have their archives of programs broken with distribution upgrades, and ISVs would love to have a stable platform to target.

I believe any theoretical bloat or performance loss due to the result of keeping a stable ABI can be negated by making everything more modular instead of integrated.  While integration may offer slight speed increases, I believe modularity and APIs, if done right and made extensible, will negate most all the theoretical performance loss.  This will free up software to much more easily co-exist with different versions, so that different modules, even the kernel, can be swapped out for substitutes, enabling users with much more freedom.  For example, I love the fact that I can run any number of different window managers and desktop environments, and that I can even mix the two, inside X.org.  Modular programming is not only smart, it decreases duplicated effort, allows flexibility, and gives everyone more freedom in general.  All that it takes is a little planning to ensure that the interfaces are standardized, so that the program can co-exist with other programs.  I don't want to use an operating system that is "baked" into one massive cookie, and be stuck waiting for the next big distro release, an all-or-nothing approach.  Instead, I want to pick out the cookies I like, and replace the ones I don't like from other sources (internet, archives, repositories, whatever), until I get the selection of software that I want.

Some Linux users understand this and for some like me it's why they use Linux, while others just think it's the ultimate evil for some strange reason.  A sad example of this rigidity recently, I went to the [Click 'n Run]("http://www.cnr.com/") website only to try about ten different programs which weren't in my Ubuntu 8.04 repository, and none of them would install, not one.  Click 'n Run says it's objective is to make installing software easier.  Well, it doesn't really, it's simply a front-end for software repositories for a few of the bigger distributions.  I've been watching it over the years, and it was touted as being a solution to the package management mess, but it's not in any way whatsoever.  Packages for the specific distributions are still required, and there are many, many packages missing even for the few "major" distributions that are listed.  It doesn't really provide anything better than the Add/Remove front-end provides.

Any way, I don't know if this anti-standardization of binary and packaging APIs logic (greatly contrary to all the other areas which are very very pro-standardization) is being injected by the bigger distros because they want Linux users to switch just because of their provided software or not, but it's really unfortunate.

I will take a look at [Zero Install]("http://0install.net/") and see about helping them with their project.  Apparently, a lot more work needs to be done to help Linux become a targetable platform, and I refuse to let these giant distros shine the light off what's really important: software, and our ability to access it and use it.  I'm not going to use proprietary distros and let these companies segregate this small market even further just because they want a bigger piece of the pie.  <rant> I'm so sick of everything now days being proprietary and locked down, hell I can't even get my car's computer reset because it's too stupid to know that I replaced a sensor without paying the dealership $100, just because they locked down their software to interface with the computer unless you pay them $10,000 per year for a license which most auto shops can't afford and shouldn't have to afford.  It's all rotten and I'm sick of it. </rant> :)

Any way, Linux standardization FTW!!! ^^

---

### Post by saulgoode on 2008-07-13
> **Yfrwlf said:**
> I will take a look at [Zero Install]("http://0install.net/") and see about helping them with their project.

My recommendation would be that you take a look at a project like GIMP (or FFMPEG, or AbiWord, or any *application*) and see about helping with that project. Then you might learn why so few Free Software developers are interested in locking themselves into standardized ABIs. There is no way you are going to get a project like GIMP to restrict itself to the functionality of GTK 2.6 because there are features that have been added in 2.8, 2.10, and 2.12 which the developers *want* to use (in many cases, they lobbied for and provided patches for those added features). 

You rant against being locked in, yet the solution you propose is to lock in the developers creating the software. You're too focused on the distro/user relationship and exhibit little understanding of the nature of the upstream source of the software.

---

### Post by cardinals_fan on 2008-07-13
> **Yfrwlf said:**
> 
I will take a look at [Zero Install]("http://0install.net/") and see about helping them with their project.  Apparently, a lot more work needs to be done to help Linux become a targetable platform, and I refuse to let these giant distros shine the light off what's really important: software, and our ability to access it and use it.  I'm not going to use proprietary distros and let these companies segregate this small market even further just because they want a bigger piece of the pie.  <rant> I'm so sick of everything now days being proprietary and locked down, hell I can't even get my car's computer reset because it's too stupid to know that I replaced a sensor without paying the dealership $100, just because they locked down their software to interface with the computer unless you pay them $10,000 per year for a license which most auto shops can't afford and shouldn't have to afford.  It's all rotten and I'm sick of it. </rant> :)

Any way, Linux standardization FTW!!! ^^
So it's not OK to lock in users, but it's fine to lock in developers?

EDIT: Weird!  Saulgoode posted the same thing above...

---

### Post by karellen on 2008-07-13
Zero install seems a good idea to me (there was once something similar called  Auto Package if I remember well), it looks similar to the ".exe"-s in Windows, a feature I find very useful

---

### Post by madjr on 2008-07-13
> **karellen said:**
> Zero install seems a good idea to me (there was once something similar called  Auto Package if I remember well), it looks similar to the ".exe"-s in Windows, a feature I find very useful

zeroinstall has a lot more features and better than most things we use now. see a **comparison**:

[http://0install.net/matrix.html](http://0install.net/matrix.html)

they only need volunteers testers and packagers, i will try to give a hand

after they get a few good packages tested and listed, they will lift off

---

### Post by Yfrwlf on 2008-07-13
> **saulgoode said:**
> My recommendation would be that you take a look at a project like GIMP (or FFMPEG, or AbiWord, or any *application*) and see about helping with that project. Then you might learn why so few Free Software developers are interested in locking themselves into standardized ABIs. There is no way you are going to get a project like GIMP to restrict itself to the functionality of GTK 2.6 because there are features that have been added in 2.8, 2.10, and 2.12 which the developers *want* to use (in many cases, they lobbied for and provided patches for those added features). 

You rant against being locked in, yet the solution you propose is to lock in the developers creating the software. You're too focused on the distro/user relationship and exhibit little understanding of the nature of the upstream source of the software.

> **cardinals_fan said:**
> So it's not OK to lock in users, but it's fine to lock in developers?

EDIT: Weird!  Saulgoode posted the same thing above...

No.  If GIMP requires a newer version of a library, then it's dependency can be something like requires >= GTK 2.12.  The LSB is a bunch of base libraries, several libraries that are very common to find being used by many Linux programs, but if newer versions or different libraries are needed, those should be available to be automatically downloaded and installed, and done in such a way that allows the newer and the older library to co-exist easily (that is, if the program would like to present the newer library for shared use with other programs).  0Install accomplishes this nicely.

The >= means extensibility.  For example, OpenGL 2.0 allows programs which use 1.0 to be run as well, because those abilities are still there, but version 2.0 allows programs to have the option of using new features.  A standard is much better though if it's not wrapped up inside the software, making it more modular.  If you could use the OpenGL 2.0 API itself, the communication standard instead of the entire software stack, with, say, DirectX OpenGL Version, then that gives users more flexibility and modularity (not that I'd do that haha, just an example).

Sorry, users AND developers. :)

Another example which I've already stated above, MKV.  It's a video container format, but inside it you can place many different kinds of video files, audio files, subtitles, etc.  It gives developers the ability to do what they want while simplifying the "front-end" for users.

Wrappers, compatibility layers, whatever you want to call them, standardization, when done right, is everyone's friend.  Developers don't have to use any standards, they can redesign the whole computer if they want to, but unless they have great reasons for doing so and the option to simply extend the power of the existing systems wasn't satisfactory, their work may go unnoticed, and while some developers don't give a crap about others using their software, others would like that very much to happen.  The latter developers are thus interested in making sure users and other developers have *access* to their software.  Standards *provide access* and are good when they are *extensible when the need arises*.

I'm not in favor of taking away anyone's freedom, and believe standards can always be found to give everyone more freedom.  Like I said, standards on SOME level are the only way to provide access.  You couldn't use *anyone's* program if there wasn't a standardized way on some level to get from point A to point B.  The only difference is in this case, the Ubuntu OS you're using, the developers in the software repositories largely control what access you have to the software you want to use.  That's not a system I like, I want software to be cross-distro, I want more accessibility than that for everone, this silly fragmentation is horrible for Linux which is struggling enough as it is, so I intend to see that system **improved**.

> **karellen said:**
> Zero install seems a good idea to me (there was once something similar called  Auto Package if I remember well), it looks similar to the ".exe"-s in Windows, a feature I find very useful

Yep.  There is always some way to deal with compatibility issues, and the key is making the extensible API.  Many other OSes have done it, and if Linux wanted to too, it could certainly pull it off in the best, most open, most extensible way that would give developers and users all the flexibility they needed and much, much more freedom by having this awesome feature.  All problems have a solution. ;)

Again, Linux compatibility FTW! ^^

---

### Post by Yfrwlf on 2008-07-13
> **madjr said:**
> zeroinstall has a lot more features and better than most things we use now. see a **comparison**:

[http://0install.net/matrix.html](http://0install.net/matrix.html)

they only need volunteers testers and packagers, i will try to give a hand

after they get a few good packages tested and listed, they will lift off

Awesome, am looking into it too. ^^

---

### Post by madjr on 2008-07-13
> **Yfrwlf said:**
> Awesome, am looking into it too. ^^

i like how he states in the comparison
[I]
**Thousands of packages available**:[/I]
    *The system is widely adopted*


only needs more packages for wide adoption

---

### Post by Foster Grant on 2008-07-15
Mac OS X probably has the best installer format: archives expand and install themselves into a RAM disk, which has the application preloaded. Drag the application (which is actually a special directory with binaries, some dependencies and drivers) into the Mac OS X "Applications" folder. No restart is needed; simply dismount the RAM disk (which flushes the contents from memory).

---

### Post by aysiu on 2008-07-15
> **Foster Grant said:**
> Mac OS X probably has the best installer format: archives expand and install themselves into a RAM disk, which has the application preloaded. Drag the application (which is actually a special directory with binaries, some dependencies and drivers) into the Mac OS X "Applications" folder. No restart is needed; simply dismount the RAM disk (which flushes the contents from memory).
Why is that the best?

That makes no sense to me.

In fact the first time I tried to install an application on a Mac, I was completely lost. I double-clicked the .dmg file and saw a white disk on the desktop. I opened it and saw an icon and double-clicked it. The application launched. When I tried to remove the white disk, the application closed.

Not intuitive at all.

I actually had to do online research to find out that you drag the icon to the Applications folder and *then* delete the white disk.

---

### Post by Foster Grant on 2008-07-15
> **aysiu said:**
> Why is that the best?

That makes no sense to me.

In fact the first time I tried to install an application on a Mac, I was completely lost. I double-clicked the .dmg file and saw a white disk on the desktop. I opened it and saw an icon and double-clicked it. The application launched. When I tried to remove the white disk, the application closed.

Not intuitive at all.

I actually had to do online research to find out that you drag the icon to the Applications folder and *then* delete the white disk.

Um .... read the friendly manual? :lol: That's what I did when I had to switch from Mac OS 9 to Mac OS X at a former job a couple of years ago.

The OS X method is the easiest to teach. It also makes removing applications a relatively painless drag-and-drop maneuver.

[SIZE="1"]And before somebody asks me if I read a manual before trying Ubuntu (yeah, I hear you mooks back there in the peanut gallery :D ) I bought and read Neal Krawetz's book *Hacking Ubuntu* before installing from the 7.10 LiveCD.[/SIZE]

---

### Post by madjr on 2008-07-15
> **Foster Grant said:**
> Mac OS X probably has the best installer format: archives expand and install themselves into a RAM disk, which has the application preloaded. Drag the application (which is actually a special directory with binaries, some dependencies and drivers) into the Mac OS X "Applications" folder. No restart is needed; simply dismount the RAM disk (which flushes the contents from memory).

this could be a good read:

[The Utopia of Program Management]("http://www.osnews.com/story/19711/The_Utopia_of_Program_Management")

combines the benefits of windows, mac and linux

well in conclusion some people say in the comments the closest thing is **[0install]("http://0install.net/matrix.html")**

here's a recent interview of features and where is heading:

[http://www.netbsd.org/gallery/pkgsrc-interviews.html#zero-install](http://www.netbsd.org/gallery/pkgsrc-interviews.html#zero-install)

---

### Post by aysiu on 2008-07-15
> **Foster Grant said:**
> Um .... read the friendly manual? :lol: That's what I did when I had to switch from Mac OS 9 to Mac OS X at a former job a couple of years ago.

The OS X method is the easiest to teach. It also makes removing applications a relatively painless drag-and-drop maneuver.

[SIZE="1"]And before somebody asks me if I read a manual before trying Ubuntu (yeah, I hear you mooks back there in the peanut gallery :D ) I bought and read Neal Krawetz's book *Hacking Ubuntu* before installing from the 7.10 LiveCD.[/SIZE]
That's silly. Something isn't "the best" if you have to read the manual. And drag and drop for uninstalling programs isn't any easier (especially ergonomically speaking) than unchecking boxes to uninstall them.

---

### Post by Foster Grant on 2008-07-15
> **aysiu said:**
> That's silly. Something isn't "the best" if you have to read the manual. And drag and drop for uninstalling programs isn't any easier (especially ergonomically speaking) than unchecking boxes to uninstall them.

You can also hit the delete key; accomplishes the same thing (moves it to the Trash).

And you should always read the manual at first except for the most basic items. Even a toaster oven is complicated if you've never used it before.

@madjr: Zero Install looks interesting but it doesn't look ready for prime time.

---

### Post by aysiu on 2008-07-15
You must mean Cmd-Delete. I've never been able to get the Delete key alone to actually move any files to the trash in OS X. Yet another unintuitive thing I had to look up to find out.

---

### Post by Foster Grant on 2008-07-15
> **aysiu said:**
> You must mean Cmd-Delete. I've never been able to get the Delete key alone to actually move any files to the trash in OS X. Yet another unintuitive thing I had to look up to find out.

Yeah, you're right. There was a piece of freeware from Apple (though not supported) for System 6/7/8/9's Finder that allowed you to hack the keyboard commands for nearly everything; altering that keyboard command was fairly common.

(I had [one of these](http://lowendmac.com/compact/macintosh-plus.html). At the time, it was awesome. :) Then they came out with [this](http://lowendmac.com/compact/macintosh-se30.html). My Mac was still awesome, but I was aware that there was something more awesome out there that I just couldn't afford. :( )

Of course, when Mac OS X came out Apple did away with the old Put Away command (Cmd-y), which was downright egregious. It both ejected media (the equivalent of dragging the disk to the trash) *and* put items in the Trash back where they came from if you changed your mind.

---

### Post by steveneddy on 2008-07-15
I hate to say it, but it really sounds like you are looking for **ONE** distro, and one only.

Sounds like Windows to me.

[COLOR="Blue"]**"One ring to rule them all..."**[/COLOR]

Personally, I like to compile apps on my machine, they just seem to run better that way. I think I'm a future Gentoo user.

Once one figures out how to use the various packaging schemes used in the various forms of Linux, it really is easy to install whatever one wants.

You are making good arguments, but I wonder if this is really necessary for any Linux to become a total Windows or Mac replacement. 

I also wonder if this is exactly the way that many mainstream Linux distributions are going?

I prefer the old ways myself.

---

### Post by madjr on 2008-07-15
> **Foster Grant said:**
> 

@madjr: Zero Install looks interesting but it doesn't look ready for prime time.

it's ready, the problem is it has not been adopted because distros are just focusing on their own systems. Either rpm, deb or something else.

distros don't care to collaborate with each other (even the same rpms don't work for fedora and suse or some debs for debian and ubuntu).

anyway, you are free to help package or contribute for zero install. It has more advantages than any other system today, just lack of testers and packages (but that may change).

---

### Post by Yfrwlf on 2008-07-16
> **Foster Grant said:**
> Mac OS X probably has the best installer format: archives expand and install themselves into a RAM disk, which has the application preloaded. Drag the application (which is actually a special directory with binaries, some dependencies and drivers) into the Mac OS X "Applications" folder. No restart is needed; simply dismount the RAM disk (which flushes the contents from memory).

Having to restart after installing a program?  Oh yeah, the painful ol' Windows days. ;)  But on a serious note, what you're describing is a little bit similar perhaps as what [Klik]("http://klik.atekon.de/") does, it runs programs from a mounted image basically.  Has benefits as well as issues, but it's a pretty decent system.  I think in comparison to  Zero Install though, Zero is better, as it leaves your system packages "untouched" while still not having the performance hit issue that Klik does, though I think any performance hit may be fairly minimal.  Of course, if you were to start running more intensive programs with Klik, it may then be an issue, so my guess is Zero or the Burgdorf API will be of more interest to everyone.

> **steveneddy said:**
> I hate to say it, but it really sounds like you are looking for **ONE** distro, and one only.

Sounds like Windows to me.

[COLOR="Blue"]**"One ring to rule them all..."**[/COLOR]

Personally, I like to compile apps on my machine, they just seem to run better that way. I think I'm a future Gentoo user.

Once one figures out how to use the various packaging schemes used in the various forms of Linux, it really is easy to install whatever one wants.

You are making good arguments, but I wonder if this is really necessary for any Linux to become a total Windows or Mac replacement. 

I also wonder if this is exactly the way that many mainstream Linux distributions are going?

I prefer the old ways myself.

I know you didn't say that it was evil per say, but let me rant for a sec and say I'm quite tired of Linux users saying that being able to install an app on any distro is evil, just like HTML or OpenGL is evil because it's a common standard.  No, I don't think having access to software is evil, but if you like compiling software, that's fine, and you will be able to continue doing so and using Linux as a development platform while at the same time have the mechanisms in place for being able to install things like both RPMs **and** DEBs on your computer.  Anyone who says that such a thing is evil is full of it, and if they want to use a distro that doesn't have this horribly evil API or evil minimal LSB base package installed on it, and wants to avoid Zero Install like the plague, be my guest.  I don't understand why exactly you'd be so upset that you now have the ability to install RPM packages easily on Ubuntu for example, though.  You only want to install DEB files because they are holy magical happy unicorn giggle files, while the big evil mean RPMs will destroy the world?  That's extremely anal if you ask me, there's nothing to be afraid of.  But, whoever thinks that, fine, they can think that while the rest of us use the software/APIs that give us wide-open access to content and software, just like those evil HTML or ODF files do.

It's easy to install whatever one wants?  Well, there's a lot of us who beg to differ, and that's why we're trying to help make it easier.  Once one spends a lot of frustrating hours trying to figure out how to compile something, or use Alien to translate an RPM into a DEB, etc etc, then yes I guess you could say it becomes "easier" at least, but "easy" is relative.  Most users don't want to do all that, I don't care to do all that either, I'd rather use programs that just work unless I'm interested in playing around with the source for some reason.  I think if program installation were to stay difficult on Linux, I don't think it will never beat Mac or Windows on the desktop because most normal computer users are technically incompetent and more accurately simply **don't want to do all that**, and suggesting that they all learn to compile and whatnot is crazy, it's not going to happen, and again before anyone says it yes, I know repositories are nice, but having this fragmentation there means that third-party apps is an impossibility unless all distros adopt at least one system that can be used by software developers so they can have access to all those distros at once.  Right now, that system is Zero Install, the new Burgdorf API, Klik, Autopackage, and others (but again, Zero and the API seem to be the best right now).  It will happen, it has to happen, but they can sure use your help and support. (see below for links, if you've missed them)

> **madjr said:**
> it's ready, the problem is it has not been adopted because distros are just focusing on their own systems. Either rpm, deb or something else.

distros don't care to collaborate with each other (even the same rpms don't work for fedora and suse or some debs for debian and ubuntu).

anyway, you are free to help package or contribute for zero install. It has more advantages than any other system today, just lack of testers and packages (but that may change).

Open source software is about sharing and accessibility.  Focusing on your own platform and users instead of helping everyone to be able to get access to any software isn't helpful for everyone.  Linux should not be "proprietary", it should be open and accessible.  Software does no good if your normal every day users can't access it, so having this rift of RPMs vs. DEBs and Fedora vs. Ubuntu and such isn't helping anyone but the companies behind the biggest repositories.  "Ha, I've got more software than you, come over and use MY OS!"  No.  Give all Linux users equal access, regardless of their distro, and allow websites and developers to release one package that works on any Linux OS (and even better, any OS at all, but that's another subject).  Once I can install either RPM or DEB formats (as well as others) on any distro I pick, I will be much happier, no longer will I be totally stuck waiting for the next distro to come out or have to compile new packages and libraries which break 50 different things on my machine.  I will have **full and easy access** to Linux apps.  Who wouldn't want that?

And, right now with Zero Install and other projects, everyone will eventually be able to have that (and already do, but they need more packaging work done).  So, go to [Zero Install site]("http://0install.net/index.html") and the [Burgdorf site]("http://www.linuxfoundation.org/en/Burgdorf_Packaging_API") and read about two projects working on making the future of Linux better for *everyone*, not just Ubuntu users. :)

---

### Post by Barrucadu on 2008-07-16
> **Yfrwlf said:**
> I think if program installation were to stay difficult on Linux, I don't think it will never beat Mac or Windows on the desktop because most normal computer users are technically incompetent and more accurately simply **don't want to do all that**

Ah, the mythical average stupid user rears their head. If someone doesn't want to learn to do something the Linux way, Linux is obviously not for them and should stick with Windows (or Mac).

---

### Post by karellen on 2008-07-16
> **Barrucadu said:**
> Ah, the mythical average stupid user rears their head. If someone doesn't want to learn to do something the Linux way, Linux is obviously not for them and should stick with Windows (or Mac).

I doubt there is something like a "linux way"; things have evolved very much in the Linux world over the years and tasks that once required to be a cli geek now are simply a matter of point and click. I believe it's one of the reasons why Linux market share is increasing steadily. keeping things difficult purposely it's not the best way to attract new users. and we do want (more) users, don't we?

---

### Post by Foster Grant on 2008-07-16
> **Barrucadu said:**
> Ah, the mythical average stupid user rears their head. If someone doesn't want to learn to do something the Linux way, Linux is obviously not for them and should stick with Windows (or Mac).

So what *is* the Linux way? GNOME, EDE. CDE, KDE or Xfce? CLI, Enlightment, wmii or Motif? Fluxbox, dwm, Windowmaker or IceWM? Or since we're talking about the Linux way of software installation ... is that RPM, Debian's dpkg, YAST,  or from source? Or maybe you prefer [COLOR="SeaGreen"]emerge system[/COLOR], YUM, Smart Package Manager, BSD ports, OpenPackage or PC-BSD's .PBI system?

:lolflag: Consider your leg officially pulled, sir. :)

I'm not sure there *is* a Linux way, other than finding the way that works best for you.

---

### Post by Yfrwlf on 2008-07-16
> **Barrucadu said:**
> Ah, the mythical average stupid user rears their head. If someone doesn't want to learn to do something the Linux way, Linux is obviously not for them and should stick with Windows (or Mac).

You sound like you're almost to the point of trolling because of the "who cares about anyone else, they can go jump off a cliff" statement which is basically what you said, but let me respond and entertain you any way.

Yes, Linux should never change, you should have to do things like you did them in 1980 for ever and ever, and if anyone comes out with any software that improves anything, they should obviously be burned at the stake.

It's like being in the old geezers room at a republican convention.  If you don't think having easy access to software is a feature, then don't use it.  You'll always have that option, no matter what other Linux users decide to do.

And...mythical?  Have you been living under a rock?  With the EEE PC among other things, Linux is being made for users who don't know, and don't want to know, really anything more than how to click on the big icons to load their favorite programs.  Having easy "third-party" program access just means they could go to any website outside of their repos and click on a software package and have it easily installed for them, without the fiddling.

Yes, the world is coming to an end, I know, it's terrible.  Non-geeks using Linux, cats and dogs sleeping together, MASS HYSTERIA.  We should obviously all hack into and delete all the repositories so that these n00bs will leave so we can get back to the traditional Linux way of compilation frustration. :)

Seriously though, if you have a technical point, I'm more than happy to hear it, but the emotionalism surrounding your statement is just really amazing to me.  Open source software is just that, open, so if a group of users and developers want to work on program X, so be it.  If you don't want to help out or contribute ideas, so be it.  Not interested?  That's fine, don't help, but there are others who are.  We're going to help make it more accessible to users and developers who want easy access to software, so your statement really doesn't phase us.

---

### Post by Bosconian on 2008-07-16
To Be Better:

1. Get Apple to release a Linux version of iTunes.

2. A much better flash player - no skipped frames. no screen tearing. Both of which still happen in version 10.

3. A more professional look after install. Please get rid of that peachy colour as default as well. It looks damn awful in my opinion.


That's all for me really which isn't bad at all. I doubt we will ever see the first one though and in my opinion an OS without proper iPod support will always struggle.

---

### Post by Canis familiaris on 2008-07-16
I think there must be a front end for users and developers which could automatically pick up DEB or RPMs or any package for that manager to install into the pacakge manager of that distribution.

---

### Post by Canis familiaris on 2008-07-16
> **Bosconian said:**
> To Be Better:
... in my opinion an OS without proper iPod support will always struggle.
Apple do not give proper support to iPod on Linux. How could you find fault with the OS?
My Advice: Do not buy an iPod if you use Linux. If you already have one try some way to get it working or request Apple for a solution or do not use Linux at all.

---

### Post by Barrucadu on 2008-07-16
> **Foster Grant said:**
> I'm not sure there *is* a Linux way, other than finding the way that works best for you.

That's exactly the way :D

---

### Post by Yfrwlf on 2008-07-16
> **Bosconian said:**
> To Be Better:

1. Get Apple to release a Linux version of iTunes.

2. A much better flash player - no skipped frames. no screen tearing. Both of which still happen in version 10.

3. A more professional look after install. Please get rid of that peachy colour as default as well. It looks damn awful in my opinion.


That's all for me really which isn't bad at all. I doubt we will ever see the first one though and in my opinion an OS without proper iPod support will always struggle.

You win the prize.  Seriously, you're the first one to comment with new ways in which you believe Linux could be better.  Here I thought we were stuck on software portability (though it IS important). :)

1) Searching for and helping anyone who's working on it may help for now, if you're interested in seeing that.  Otherwise, as the above poster suggested, your only options, until it happens, is to use something else.  There are programs that do the same exact thing as itunes, so you could always rip the music from itunes, and then use those programs instead, like Amarok.  Or, you can buy the programs and hardware which are supported by Linux, or even better, which support Linux.

2) Pretty much done, they're still working on it, go [get it]("http://labs.adobe.com/downloads/flashplayer10.html") and report any bugs to them, and also consider helping out [Gnash]("http://www.gnashdev.org/") in the same way, too, as it's open source.

3)  Haha, you're not the first to suggest it.  Until they decide to change it, of course you can simply change the colors and backgrounds like I always do any way, and there are several other distros out there that have different default themes like [Linux Mint]("http://www.linuxmint.com/"), or you could release your own Ubuntu with your tweaks of course, but yeah, trust me, you're not the first to comment. ;)

> **Anurag_panda said:**
> I think there must be a front end for users and developers which could automatically pick up DEB or RPMs or any package for that manager to install into the pacakge manager of that distribution.

Exactly.  Developers, packagers, and end users could all now have a choice in which format to use, because the distro they're using would no longer be the deciding factor anymore.  The formats could directly compete.  To make it easier on end users, they could compete inside a container format too, so that users weren't a little confused with all the different file types.  Not that they don't already deal with multiple types in many other areas, but, you know, would make it a little easier to have .Linux files instead. :)

Making things modular allows competition to occur.  For example, if the Linux kernel was modular and used APIs and such, if everything was done right, I could swap out my Linux kernel and put in the Herd kernel if it was compatible with all the API calls that were the bare essentials to have.  Modularity = more freedom to choose. :)

Like you said, as soon as package managers can cope with multiple types, like a movie player, audio player, compression program, etc can, then developers will also be **even more free** to use **new** formats, too.  They won't be locked into DEB version 1 just because it's what lots of distros use which can't use anything else, they will have access to DEB version 2, and ebuilds, and whole completely new formats, so the formats will finally be able to compete, the easy to use and powerful ones will outshine the lesser ones.  Natural competition at work via public popularity and preferences instead of "the old way" being forced on everyone far into the future.

---

### Post by Yfrwlf on 2008-07-16
> **Barrucadu said:**
> That's exactly the way :D

And that's fine, but you don't need to rain on the parade of those wanting to add features and software to Linux. :)

You saying everyone should do things the way they want, but then saying they shouldn't use Linux if they want easy program installation, is a contradiction.  For now though, your advice is sadly accurate, maybe they should use other OSes until this problem gets resolve.  I, however, am instead going to help with adding this feature.  Then, your "Linux way" will include this ability.  Win win.

Not to mention you'll be winning in the following ways with easy software installation:

1) More software for Linux that works on any Linuxes means all users can get and share software, not to mention help out by reporting bugs and such, increasing Linux's adoption rate.

2) Developers can develop software for any distro and have their software actually easily get out to the masses, so that it can all be used, making more Linux software for everyone.

3) Freedom for everyone, period.

4) A bunch of 1 and 2 going back and forth, spiraling upwards, allowing more Linux users and developers to exist, making Linux take over the desktop markets.

5) Year of the Linux desktop! ;)

---

### Post by Canis familiaris on 2008-07-16
Great ideas Wfrwlf!

---

### Post by Foster Grant on 2008-07-16
> **Bosconian said:**
> To Be Better:

1. Get Apple to release a Linux version of iTunes.

Pigs will fly first.

> **Bosconian said:**
> 3. A more professional look after install. Please get rid of that peachy colour as default as well. It looks damn awful in my opinion.

Which distro? :D If you don't like the look of one, use another.

> **Bosconian said:**
>  in my opinion an OS without proper iPod support will always struggle.

Mine works fine. :)

---

### Post by Yfrwlf on 2008-07-16
> **Foster Grant said:**
> Which distro? :D If you don't like the look of one, use another.

When true software portability exists in Linux, this will much easier.  Ubuntu won't be the biggest star just because of it's selection of software, and you will then be more free to choose any distro, because the only distinguishing differences will be the particular initial software bundle it comes with, and the default settings.  You'll have access to all the nice programs that Ubuntu has.  Until then, they're sort of out of luck for the above reasons and somewhat restricted to Ubuntu.  Fedora and Suse have pretty big repos too but...*shrug*

Wait for Zero Install to grow it's packages, and ultimately Burgdorf to fix the problem, **then** you'll be set. :)

> **Foster Grant said:**
> Mine works fine. :)

They did have a point though, itunes would make Linux more popular, which is why you probably will never see Microsoft or Apple allowing it to happen (MS has Apple stock).  There are plenty of programs and digital music players out there that offer the same functionality though.  I highly recommend them instead. :)  ([Amarok]("http://amarok.kde.org/")!)

---

### Post by KaiJordanDay on 2008-07-16
I agree with webcam ect, I have to uses windows to use my graphics tablet (eww)

---

### Post by Yfrwlf on 2008-07-16
> **KaiJordanDay said:**
> I agree with webcam ect, I have to uses windows to use my graphics tablet (eww)

Which tablet do you have?  From my experience many tablets partially work in Linux, you can move the mouse pointer around, but the part that I think really makes them different from one another (and thus often currently incompatible) is the pen, and the buttons on it.  Also, I didn't have two different pressure sensitivities either. (In other words, it was only good for moving the mouse around, and double and single clicking, making it impossible to draw with.)

---

### Post by Yes on 2008-07-16
> **Yfrwlf said:**
> When true software portability exists in Linux, this will be possible.  Ubuntu won't be the biggest star just because of it's selection of software, and you will then be free to choose any distro, because the only distinguishing differences will be the particular initial software bundle it comes with, and the default settings.  You'll have access to all the nice programs that Ubuntu has.  Until then, they're sort of out of luck for the above reasons and somewhat restricted to Ubuntu.

Other distros have repos too, and they probably have all the same programs the Ubuntu repos do.

---

### Post by Yfrwlf on 2008-07-16
> **Yes said:**
> Other distros have repos too, and they probably have all the same programs the Ubuntu repos do.

No, Yes. ;)

There are 1895328 different distros, so it's utterly impossible.  The "smaller" distros suffer because they don't have many packagers, while the "bigger" distros get chosen often because their repos are big.  Allowing any package to be installed on any distro will level that playing field and put an end to this problem, along with many other problems.

---

### Post by Yes on 2008-07-16
> **Yfrwlf said:**
> No, Yes. ;)

There are 1895328 different distros, so it's utterly impossible.  The "smaller" distros suffer because they don't have many packagers, while the "bigger" distros get chosen often because their repos are big.  Allowing any package to be installed on any distro will level that playing field and put an end to this problem, along with many other problems.

I use Arch Linux, and I bet I could install anything you can from Ubuntu with pacman and yaourt (the apt-get equivalents of Arch).

---

### Post by Yfrwlf on 2008-07-16
> **Yes said:**
> I use Arch Linux, and I bet I could install anything you can from Ubuntu with pacman and yaourt (the apt-get equivalents of Arch).

Regardless, there are always going to be some programs that haven't been compiled yet for your distro and version, and I'm sure Pacman would love not having to recompile every package for every distro and version.  You won't need your select specific repos after Linux software is cross-distro.  Instead, you'll be able to add the Sourceforge Linux repo, or the Google Linux repo, or what have you.

It's a pain and a pressure that doesn't need to exist.  You'll be happier once you can install any Linux software packages.  I know I and many others will be. :)

---

### Post by aysiu on 2008-07-16
> **Yfrwlf said:**
> No, Yes. ;)

There are 1895328 different distros, so it's utterly impossible.  The "smaller" distros suffer because they don't have many packagers, while the "bigger" distros get chosen often because their repos are big.  Allowing any package to be installed on any distro will level that playing field and put an end to this problem, along with many other problems.
Does that smiley face mean you're exaggerating? If not, I'd like to know where you're getting that number from.

Most smaller distros use existing package management. For example, Damn Small Linux used to be based on Debian and use Debian repositories (it may still be based on Debian - I just haven't kept up with it). Sabayon is based on Gentoo and uses *emerge* to compile software, just as Gentoo does. Linux Mint is based on Ubuntu and uses Ubuntu repositories. PCLinuxOS is based on Mandriva and probably uses Mandriva's repositories.

As far as I can tell, the main packaging formats are .rpm, .deb, and .tar.gz (precompiled binaries or source code).

---

### Post by Canis familiaris on 2008-07-16
> **aysiu said:**
> 
As far as I can tell, the main packaging formats are .rpm, .deb, and .tar.gz (precompiled binaries or source code).
Actually the problem grows because DEBs and RPMs or various distros are incompatible.
For eg. SuSE RPM is incompatible with Red Hat RPM which is different from Mandriva's and so on.
Ubuntu and Debian are compatible but not completely either.
This incompatbility among RPMs and DEBs creates far too much confusion IMO and as a result there are great number of permutations in number of package managers.

---

### Post by Tomatz on 2008-07-16
> **Yfrwlf said:**
> Always have to have more of these threads, especially after each Ubuntu release. ;)

While the brainstorm site is great, having a heap of ideas in the same thread can be fun too.

Everyone post your most frustrating problems with Linux, or general ways in which you can vision improvements! :)

**[COLOR="Blue"]1) Standardized packaging API that allows inter-distro program installation.[/COLOR]**

[INDENT]Tired of feeling trapped in one distro version at a time?  Want to install that new program that isn't in the repos, but you feel like throwing your keyboard through your monitor when you hit snags all over the place?  You're not alone!  If a Linux mechanism/API/compatibility layer/standardized packaging container/format was created at some point in order to allow program installation across all Linux distros, you and everyone else would have the freedom to use what you want, when you wanted.  Say goodbye to being locked into distro X for programs YZQ, use any one you like!  Share programs with your friends over the internet!  Save program packages in an archive for later use, never having to worry about compiling them or compatibility with them!  Yes, the future will be much brighter and more free as soon as this gets worked out.  They're working on it now, one of the latest ideas being the [Berlin Packaging API]("http://www.osnews.com/story/19901").  Also see the [LSB packaging workgroup]("http://www.linuxfoundation.org/en/Packaging").[/INDENT]

**[COLOR="Blue"]2) Standardized/modular driver installation.[/COLOR]**

[INDENT]Again, ever stuck with wanting that new piece of hardware to work with Linux, but you want to either stick with an older kernel or distro, or even your newer one doesn't include it or support it fully?  Share drivers online easily with a standardized/common driver installation package format and kernel driver API!  Never again have to teach your grandma to compile her printer drivers each time she upgrades, just find the standardized printer driver, click on it, and you're done!  Enjoy the *true* freedom of using Linux instead of feeling like your sister needs a computer science degree or mastery at programming in order to easily use her operating system![/INDENT]

**[COLOR="Blue"]3) Joystick, webcam, tablet, and other peripheral support.[/COLOR]**

[INDENT]KDE does a much better job with having utilities to configure and calibrate many more peripherals than Gnome does, so it'd be great if Gnome would add these abilities as well, or better yet use the ones that were "made for KDE", which brings me to my fourth and similarly-themed point...[/INDENT]

**[COLOR="Blue"]4) Make everything more cross-compatible and modular, in every way, so any of them can be used anywhere.[/COLOR]**

[INDENT]More APIs, more standard ways of doing things.  Modularity = freedom.  Modularity = smart programming.  The first thing you should do when programming, after you come up with a great idea, is figure out how it will fit in with the existing operating system.  Plan ahead, and make your program talk to popular standards, and it will get used a lot more.  Plugins are popular for a reason, and just think if the plugins themselves could be used with *other* programs as well.  (Insert witty remark about Firefox's popularity here.)  As for KDE and Gnome applications?  It has to stop.  A program should not be locked into the look and feel of one particular desktop environment.  Using a further standardized X GUI language would allow any program to be run inside any DE while retaining the look and feel of that DE.  [wxWidgets]("http://www.wxwidgets.org/") goes a long way towards accomplishing this, now all it needs is the ability to display KDE applications natively as well.  Then, it's a matter of writing the code for the GUI front-end once, and you're done, for all operating systems and desktop environments.  Just one more thing to make using KDE configuration utilities for Gnome easier, so that Gnome can easily utilize some of the good features of KDE if users want it to.  Having a Linux program which is exclusive to one DE only results in fragmentation and duplication of work.[/INDENT]

**[COLOR="Blue"]5) Further help users to get to all the things they need.[/COLOR]**

[INDENT]Good documentation, helpful messages/pop-ups and more feedback in general, a way to find out which devices are supported under Linux and/or a place to **buy** devices that are supported (think the Apple Store, but for Linux), and again, installation package standardization, so that **all** the Linux programs that can replace programs users knew and loved on Windows and Macs can be accessible to them without hoping the thing they need is in the repositories and often being between a rock and a hard place if it's not.[/INDENT]

I want Linux to become the defacto operating system, but these problems plague many users who try it and will keep many users at bay, and greatly slow the adoption rate of Linux.  Again, having a nice, pretty, bundled OS that has a repository with lots of programs in it is good, but not having to worry about what's in the repository, or better yet, being able to use any repository, and not having to compile and fill a repository for every flavor and version of Linux, will allow Linux to go much further beyond what it is now, much more rapidly.  Any, before it gets mentioned, I know that binaries thankfully are download and click to run which is great, but integration with the package manager to add easy remove and update abilities as well as having menu items is very important for users in their search for a user-friendly OS.

So linux should be windows?

---

### Post by Tomatz on 2008-07-16
> **Yfrwlf said:**
> No, Yes. ;)

There are 1895328 different distros, so it's utterly impossible.  The "smaller" distros suffer because they don't have many packagers, while the "bigger" distros get chosen often because their repos are big.  Allowing any package to be installed on any distro will level that playing field and put an end to this problem, along with many other problems.

Thats 10 distros per user...

:lolflag:

---

### Post by Foster Grant on 2008-07-16
> **Yfrwlf said:**
> 
They did have a point though, itunes would make Linux more popular, which is why you probably will never see Microsoft or Apple allowing it to happen (MS has Apple stock).

As noted in the book *Apple Confidential 2.0*, Microsoft purchased 150,000 shares of non-voting Apple stock in 1997 for $150 million ($1,000 per share) to settle Apple's patent-infringement lawsuit regarding Quicktime for Windows code reused in Microsoft's Video for Windows. (Apple had $9 billion lying around, so it didn't really need the money). As a condition of the deal, Microsoft agreed to continue development and support of the Mac version of Office for another 5 years. The stock Microsoft purchased could not be converted into voting stock or sold for at least three years. Microsoft later converted that stock into 18.2 million shares of common stock for an effective purchase price of $8.25 per share. That sounds like a lot, but consider that currently over 33 million shares of AAPL are traded every day.

There's no question that stock has since been sold on the open market --- in 2001 according to Inside Microsoft, or in 2003 according to blogger [Justin Hartman](http://justinhartman.com/2007/11/23/microsofts-equity-in-apple/). There's a dip in AAPL stock value and spike in shares traded in April 2003, which would seem to support the idea that 18.2 million shares were dumped at that time. Within six months of that sale, [AAPL stock value jumped 79 percent](http://www.macminute.com/2003/09/02/aapl) thanks to the introduction of iPods, iTunes 4 and the iTunes Music Store, Safari 1.0 and Mac OS X Panther.

Hartman also says Microsoft currently owns about 0.0046% of Apple's outstanding shares through a Private Capital Management fund. It's not like that's enough of a lever to tell Steve Jobs what to do.

(Since mid-2001, the value of AAPL shares have increased nearly 1100 percent. MSFT left something along the lines of $1.7 billion on the table when it sold the stock.)

And Songbird is mo'betta than Amarok.

---

### Post by Canis familiaris on 2008-07-16
> **Tomatz said:**
> Thats 10 distros per user...

:lolflag:
Please tell me that there are not just 189,532 linux users. That would be far too less IMO. :(

---

### Post by aysiu on 2008-07-16
> **Anurag_panda said:**
> Actually the problem grows because DEBs and RPMs or various distros are incompatible.
For eg. SuSE RPM is incompatible with Red Hat RPM which is different from Mandriva's and so on.
Ubuntu and Debian are compatible but not completely either.
This incompatbility among RPMs and DEBs creates far too much confusion IMO and as a result there are great number of permutations in number of package managers.
I realize that, but Yfrwlf said smaller distros can't package all the software themselves.

My point was that they don't need to, since they're usually based off larger distros and use the larger distro's repositories anywhere.

---

### Post by Canis familiaris on 2008-07-16
> **aysiu said:**
> I realize that, but Yfrwlf said smaller distros can't package all the software themselves.

My point was that they don't need to, since they're usually based off larger distros and use the larger distro's repositories anywhere.

So smaller distros can use larger distros repos? Aren't there any restrictions? I mean if they can then Why does Mint uses seperate distros(OR am I mistaken to think that)?

---

### Post by aysiu on 2008-07-16
> **Anurag_panda said:**
> So smaller distros can use larger distros repos? Aren't there any restrictions? I mean if they can then Why does Mint uses seperate distros(OR am I mistaken to think that)?
Mint uses Ubuntu repositories.

It also adds its own very small repository for Mint-specific packages.

This is what the Mint /etc/apt/sources.list looks like: ```
## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Daryna (Linux Mint 4.0) +++
deb http://www.linuxmint.com/repository daryna main upstream import
## deb http://www.linuxmint.com/repository daryna community
## deb http://www.linuxmint.com/repository daryna backport

## +++ Romeo (Linux Mint Unstable) +++
## deb http://www.linuxmint.com/repository romeo daryna

## +++ Source Repositories +++
## deb-src http://www.linuxmint.com/repository daryna main upstream import
## deb-src http://www.linuxmint.com/repository daryna community
## deb-src http://www.linuxmint.com/repository daryna backport
## deb-src http://www.linuxmint.com/repository romeo daryna

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Gutsy (Ubuntu 7.10) +++
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

## +++ Backports & Proposed (Ubuntu Unstable) +++
#deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu gutsy-proposed main restricted universe multiverse

## +++ Source Repositories +++
#deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical +++
deb http://archive.canonical.com/ubuntu gutsy partner

## +++ Medibuntu +++
deb http://packages.medibuntu.org/ gutsy free non-free 
``` If you look in [http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/), you'll see there aren't that many packages that Mint itself maintains. Most packages are from Ubuntu.

---

### Post by Canis familiaris on 2008-07-16
> **aysiu said:**
> Mint uses Ubuntu repositories.

It also adds its own very small repository for Mint-specific packages.

I guess I was mistaken! :)

---

### Post by Tomatz on 2008-07-16
> **Anurag_panda said:**
> Please tell me that there are not just 189,532 linux users. That would be far too less IMO. :(

LOL

Obviously but i cant see how there is 1895328 distros out there...

---

### Post by Canis familiaris on 2008-07-16
> **Tomatz said:**
> LOL

Obviously but i cant see how there is 1895328 distros out there...

Yes of course.:)

But I hope there are that many Linux Users at least.

Maybe it was a figure of speech.

---

### Post by Canis familiaris on 2008-07-16
> **aysiu said:**
> you'll see there aren't that many packages that Mint itself maintains. Most packages are from Ubuntu.
I suppose that is the biggest strength of open-source, reusability of code and resources.

---

### Post by Tomatz on 2008-07-16
Isn't the point of an API to enable you to code software without having access to the source code?

Why would Linux need an API?

---

### Post by aysiu on 2008-07-16
There are only 349 distros on DistroWatch that I could find.

These are the hits-per-day on DW for all 349 distros: ```
**Rank 	Distro 	Hits-per-day**
1 	Ubuntu 	2312
2 	PCLinuxOS 	1941
3 	openSUSE 	1637
4 	Fedora 	1329
5 	Mint 	1271
6 	Sabayon 	927
7 	Mandriva 	884
8 	Debian 	881
9 	Damn Small 	673
10 	MEPIS 	599
11 	CentOS 	524
12 	Dreamlinux 	514
13 	Slackware 	495
14 	FreeBSD 	489
15 	Puppy 	475
16 	Kubuntu 	469
17 	Gentoo 	460
18 	Zenwalk 	426
19 	Arch 	421
20 	KNOPPIX 	399
21 	sidux 	334
22 	Vector 	318
23 	Slax 	297
24 	PC-BSD 	293
25 	Ubuntu Studio 	291
26 	Xubuntu 	275
27 	Freespire 	253
28 	Foresight 	242
29 	Red Hat 	232
30 	Elive 	231
31 	DesktopBSD 	222
32 	TinyMe 	204
33 	Xandros 	189
34 	Frugalware 	179
35 	Fluxbuntu 	175
36 	Absolute 	174
37 	GoblinX 	171
38 	OpenGEU 	170
39 	gOS 	167
40 	SystemRescue 	166
41 	BackTrack 	162
42 	linuX-gamers 	148
43 	SAM 	137
44 	Mythbuntu 	136
45 	Parted Magic 	135
46 	OpenSolaris 	133
47 	Musix 	130
48 	KANOTIX 	126
49 	OpenBSD 	125
50 	Yellow Dog 	124
51 	FreeNAS 	123
52 	64 Studio 	123
53 	Pardus 	120
54 	Ubuntu CE 	118
55 	Solaris 	114
56 	Scientific 	113
57 	Nexenta 	111
58 	Linux XP 	107
59 	DragonFly 	105
60 	Symphony OS 	100
61 	Novell SLE 	100
62 	Shift 	99
63 	Parsix 	99
64 	Linspire 	98
65 	Wolvix 	89
66 	NetBSD 	89
67 	Myah OS 	89
68 	StartCom 	88
69 	Pioneer 	87
70 	Granular 	87
71 	Ark 	87
72 	KateOS 	82
73 	X/OS 	79
74 	DeLi 	78
75 	Turbolinux 	77
76 	LFS 	77
77 	NimbleX 	76
78 	gNewSense 	76
79 	Yoper 	74
80 	GParted 	71
81 	DARKSTAR 	71
82 	ClarkConnect 	71
83 	m0n0wall 	70
84 	GeeXboX 	70
85 	Bluewhite64 	70
86 	Berry 	70
87 	Lunar 	68
88 	IPCop 	68
89 	Ultimate 	67
90 	SME Server 	67
91 	SaxenOS 	65
92 	dyne:bolic 	65
93 	AUSTRUMI 	65
94 	SmoothWall 	63
95 	Gentoox 	62
96 	RIPLinuX 	61
97 	Kiwi 	61
98 	GoboLinux 	61
99 	Ulteo 	59
100 	LiveCD Router 	58
101 	Devil 	58
102 	Vine 	57
103 	BLAG 	56
104 	PUD 	54
105 	Big Linux 	54
106 	KnoppMyth 	53
107 	UbuntuME 	52
108 	CRUX 	51
109 	Linpus 	50
110 	Famelix 	50
111 	eAR OS 	50
112 	Clonezilla 	50
113 	ALT 	49
114 	Trinity 	48
115 	Pentoo 	47
116 	EnGarde 	46
117 	rPath 	45
118 	JackLab 	44
119 	ArtistX 	43
120 	Greenie 	42
121 	BeleniX 	42
122 	Astaro 	42
123 	Endian 	41
124 	Draco 	39
125 	LinuxConsole 	37
126 	FreeSBIE 	37
127 	Vyatta 	36
128 	paldo 	35
129 	SchilliX 	34
130 	Finnix 	34
131 	2X 	34
132 	Kurumin 	33
133 	Helix 	33
134 	Ultima 	32
135 	Slamd64 	32
136 	pfSense 	32
137 	ADIOS 	32
138 	TrueBSD 	31
139 	Vixta.org 	30
140 	Momonga 	29
141 	CDlinux 	29
142 	Slackintosh 	28
143 	easys 	27
144 	Ututo 	26
145 	Resulinux 	26
146 	Sorcerer 	25
147 	AliXe 	25
148 	T2 	24
149 	PelicanHPC 	24
150 	PAIPIX 	24
151 	nUbuntu 	24
152 	Litrix 	24
153 	Gibraltar 	24
154 	ASPLinux 	24
155 	Source Mage 	23
156 	RoFreeSBIE 	23
157 	MoLinux 	23
158 	grml 	23
159 	trixbox 	22
160 	SliTaz 	22
161 	Skolelinux 	22
162 	Red Flag 	22
163 	MirOS 	22
164 	Karamad 	22
165 	Epidemic 	22
166 	UHU-Linux 	21
167 	Morphix 	21
168 	MidnightBSD 	21
169 	Oracle 	20
170 	GentooTH 	20
171 	Caixa Mágica 	20
172 	redWall 	19
173 	Poseidon 	19
174 	Grafpup 	19
175 	Coyote 	19
176 	Core 	19
177 	Archie 	19
178 	Alinex 	19
179 	Voltalinux 	18
180 	VMKnoppix 	18
181 	Freedows 	18
182 	B2D 	18
183 	Webconverger 	17
184 	Securepoint 	17
185 	Nonux 	17
186 	Knopperdisk 	17
187 	Censornet 	17
188 	ROCK 	16
189 	MythDora 	16
190 	Guadalinex 	16
191 	blackPanther 	16
192 	Asianux 	16
193 	White Box 	15
194 	Rocks Cluster 	15
195 	NST 	15
196 	Mutagenix 	15
197 	Frenzy 	15
198 	Euronode 	15
199 	BOSS 	15
200 	ZoneCD 	14
201 	LinuxTLE 	14
202 	INSERT 	14
203 	GNUstep 	14
204 	TEENpup 	13
205 	TA-Linux 	13
206 	STD 	13
207 	PLD 	13
208 	Ophcrack 	13
209 	NetSecL 	13
210 	Linux-EduCD 	13
211 	K-DEMar 	13
212 	CCux 	13
213 	ArcheOS 	13
214 	Xfld 	12
215 	Untangle 	12
216 	Topologilinux 	12
217 	SLAMPP 	12
218 	Protech 	12
219 	PapugLinux 	12
220 	OliveBSD 	12
221 	LG3D 	12
222 	Kaella 	12
223 	Comfusion 	12
224 	Aurora 	12
225 	Trisquel 	11
226 	RAYS 	11
227 	STUX 	11
228 	Olive 	11
229 	elpicx 	11
230 	College 	11
231 	BinToo 	11
232 	Tilix 	10
233 	Thinstation 	10
234 	SuperGamer 	10
235 	StressLinux 	10
236 	SoL 	10
237 	RUNT 	10
238 	Openwall 	10
239 	Magic 	10
240 	Deep-Water 	10
241 	clusterKNOPPIX 	10
242 	BeaFanatIX 	10
243 	tinysofa 	9
244 	ROSLIMS 	9
245 	QiLinux 	9
246 	MilaX 	9
247 	Media Lab 	9
248 	Linux+ Live 	9
249 	Kwort 	9
250 	Komodo 	9
251 	K12LTSP 	9
252 	eLearnix 	9
253 	Ufficio Zero 	8
254 	Pie Box 	8
255 	Penguin Sleuth 	8
256 	Openfiler 	8
257 	myLinux 	8
258 	Miracle 	8
259 	LliureX 	8
260 	gnuLinEx 	8
261 	Karoshi 	8
262 	Evinux 	8
263 	Clusterix 	8
264 	Càtix 	8
265 	cAos 	8
266 	AsianLinux 	8
267 	Tuquito 	7
268 	OpenNA 	7
269 	OpenLab 	7
270 	OLPC 	7
271 	MAX 	7
272 	LinnexOS 	7
273 	L.A.S. 	7
274 	How-Tux 	7
275 	Freeduc 	7
276 	eduKnoppix 	7
277 	DNALinux 	7
278 	DiscoverStation 	7
279 	BU Linux 	7
280 	BioBrew 	7
281 	Bayanihan 	7
282 	AbulÉdu 	7
283 	X-Evian 	6
284 	WIENUX 	6
285 	Plamo 	6
286 	Pingwinek 	6
287 	Nature's 	6
288 	Mayix 	6
289 	KnoSciences 	6
290 	Knoppel 	6
291 	Kalango 	6
292 	Honeywall 	6
293 	Hiweed 	6
294 	Hacao 	6
295 	Fermi 	6
296 	ERPOSS 	6
297 	ELX 	6
298 	Ekaaty 	6
299 	DANIX 	6
300 	ASLinux 	6
301 	AnNyung 	6
302 	Xteam 	5
303 	VNLinux 	5
304 	TupiServer 	5
305 	SuliX 	5
306 	Rails Live 	5
307 	Pingo 	5
308 	Co-Create 	5
309 	O-Net 	5
310 	Omoikane 	5
311 	NeoShine 	5
312 	Murix 	5
313 	Loco 	5
314 	LiVux 	5
315 	Insigne 	5
316 	Haansoft 	5
317 	GNIX 	5
318 	GEOLivre 	5
319 	Gelecek 	5
320 	FTOSX 	5
321 	EzPlanet One 	5
322 	Dzongkha 	5
323 	Condorux 	5
324 	Ankur Bangla 	5
325 	Wazobia 	4
326 	TumiX 	4
327 	pQui 	4
328 	Pilot 	4
329 	OpenLX 	4
330 	Nitix 	4
331 	NepaLinux 	4
332 	Myrinix 	4
333 	Julex 	4
334 	JoLinux 	4
335 	IndLinux 	4
336 	Impi 	4
337 	IDMS 	4
338 	Everest 	4
339 	Ehad 	4
340 	EduLinux 	4
341 	Dizinha 	4
342 	Burapha 	4
343 	Truva 	3
344 	Thisk 	3
345 	Swecha 	3
346 	NuxOne 	3
347 	Niigata 	3
348 	Muriqui 	3
349 	TFM 	1
``` Nowhere near 1895328 or whatever made-up number was thrown around before. And who uses Muriqui, TFM, or Swecha?

---

### Post by phrostbyte on 2008-07-16
> **aysiu said:**
> There are only 349 distros on DistroWatch that I could find.

These are the hits-per-day on DW for all 349 distros: ```
**Rank 	Distro 	Hits-per-day**
1 	Ubuntu 	2312
2 	PCLinuxOS 	1941
3 	openSUSE 	1637
4 	Fedora 	1329
5 	Mint 	1271
6 	Sabayon 	927
7 	Mandriva 	884
8 	Debian 	881
9 	Damn Small 	673
10 	MEPIS 	599
11 	CentOS 	524
12 	Dreamlinux 	514
13 	Slackware 	495
14 	FreeBSD 	489
15 	Puppy 	475
16 	Kubuntu 	469
17 	Gentoo 	460
18 	Zenwalk 	426
19 	Arch 	421
20 	KNOPPIX 	399
21 	sidux 	334
22 	Vector 	318
23 	Slax 	297
24 	PC-BSD 	293
25 	Ubuntu Studio 	291
26 	Xubuntu 	275
27 	Freespire 	253
28 	Foresight 	242
29 	Red Hat 	232
30 	Elive 	231
31 	DesktopBSD 	222
32 	TinyMe 	204
33 	Xandros 	189
34 	Frugalware 	179
35 	Fluxbuntu 	175
36 	Absolute 	174
37 	GoblinX 	171
38 	OpenGEU 	170
39 	gOS 	167
40 	SystemRescue 	166
41 	BackTrack 	162
42 	linuX-gamers 	148
43 	SAM 	137
44 	Mythbuntu 	136
45 	Parted Magic 	135
46 	OpenSolaris 	133
47 	Musix 	130
48 	KANOTIX 	126
49 	OpenBSD 	125
50 	Yellow Dog 	124
51 	FreeNAS 	123
52 	64 Studio 	123
53 	Pardus 	120
54 	Ubuntu CE 	118
55 	Solaris 	114
56 	Scientific 	113
57 	Nexenta 	111
58 	Linux XP 	107
59 	DragonFly 	105
60 	Symphony OS 	100
61 	Novell SLE 	100
62 	Shift 	99
63 	Parsix 	99
64 	Linspire 	98
65 	Wolvix 	89
66 	NetBSD 	89
67 	Myah OS 	89
68 	StartCom 	88
69 	Pioneer 	87
70 	Granular 	87
71 	Ark 	87
72 	KateOS 	82
73 	X/OS 	79
74 	DeLi 	78
75 	Turbolinux 	77
76 	LFS 	77
77 	NimbleX 	76
78 	gNewSense 	76
79 	Yoper 	74
80 	GParted 	71
81 	DARKSTAR 	71
82 	ClarkConnect 	71
83 	m0n0wall 	70
84 	GeeXboX 	70
85 	Bluewhite64 	70
86 	Berry 	70
87 	Lunar 	68
88 	IPCop 	68
89 	Ultimate 	67
90 	SME Server 	67
91 	SaxenOS 	65
92 	dyne:bolic 	65
93 	AUSTRUMI 	65
94 	SmoothWall 	63
95 	Gentoox 	62
96 	RIPLinuX 	61
97 	Kiwi 	61
98 	GoboLinux 	61
99 	Ulteo 	59
100 	LiveCD Router 	58
101 	Devil 	58
102 	Vine 	57
103 	BLAG 	56
104 	PUD 	54
105 	Big Linux 	54
106 	KnoppMyth 	53
107 	UbuntuME 	52
108 	CRUX 	51
109 	Linpus 	50
110 	Famelix 	50
111 	eAR OS 	50
112 	Clonezilla 	50
113 	ALT 	49
114 	Trinity 	48
115 	Pentoo 	47
116 	EnGarde 	46
117 	rPath 	45
118 	JackLab 	44
119 	ArtistX 	43
120 	Greenie 	42
121 	BeleniX 	42
122 	Astaro 	42
123 	Endian 	41
124 	Draco 	39
125 	LinuxConsole 	37
126 	FreeSBIE 	37
127 	Vyatta 	36
128 	paldo 	35
129 	SchilliX 	34
130 	Finnix 	34
131 	2X 	34
132 	Kurumin 	33
133 	Helix 	33
134 	Ultima 	32
135 	Slamd64 	32
136 	pfSense 	32
137 	ADIOS 	32
138 	TrueBSD 	31
139 	Vixta.org 	30
140 	Momonga 	29
141 	CDlinux 	29
142 	Slackintosh 	28
143 	easys 	27
144 	Ututo 	26
145 	Resulinux 	26
146 	Sorcerer 	25
147 	AliXe 	25
148 	T2 	24
149 	PelicanHPC 	24
150 	PAIPIX 	24
151 	nUbuntu 	24
152 	Litrix 	24
153 	Gibraltar 	24
154 	ASPLinux 	24
155 	Source Mage 	23
156 	RoFreeSBIE 	23
157 	MoLinux 	23
158 	grml 	23
159 	trixbox 	22
160 	SliTaz 	22
161 	Skolelinux 	22
162 	Red Flag 	22
163 	MirOS 	22
164 	Karamad 	22
165 	Epidemic 	22
166 	UHU-Linux 	21
167 	Morphix 	21
168 	MidnightBSD 	21
169 	Oracle 	20
170 	GentooTH 	20
171 	Caixa Mágica 	20
172 	redWall 	19
173 	Poseidon 	19
174 	Grafpup 	19
175 	Coyote 	19
176 	Core 	19
177 	Archie 	19
178 	Alinex 	19
179 	Voltalinux 	18
180 	VMKnoppix 	18
181 	Freedows 	18
182 	B2D 	18
183 	Webconverger 	17
184 	Securepoint 	17
185 	Nonux 	17
186 	Knopperdisk 	17
187 	Censornet 	17
188 	ROCK 	16
189 	MythDora 	16
190 	Guadalinex 	16
191 	blackPanther 	16
192 	Asianux 	16
193 	White Box 	15
194 	Rocks Cluster 	15
195 	NST 	15
196 	Mutagenix 	15
197 	Frenzy 	15
198 	Euronode 	15
199 	BOSS 	15
200 	ZoneCD 	14
201 	LinuxTLE 	14
202 	INSERT 	14
203 	GNUstep 	14
204 	TEENpup 	13
205 	TA-Linux 	13
206 	STD 	13
207 	PLD 	13
208 	Ophcrack 	13
209 	NetSecL 	13
210 	Linux-EduCD 	13
211 	K-DEMar 	13
212 	CCux 	13
213 	ArcheOS 	13
214 	Xfld 	12
215 	Untangle 	12
216 	Topologilinux 	12
217 	SLAMPP 	12
218 	Protech 	12
219 	PapugLinux 	12
220 	OliveBSD 	12
221 	LG3D 	12
222 	Kaella 	12
223 	Comfusion 	12
224 	Aurora 	12
225 	Trisquel 	11
226 	RAYS 	11
227 	STUX 	11
228 	Olive 	11
229 	elpicx 	11
230 	College 	11
231 	BinToo 	11
232 	Tilix 	10
233 	Thinstation 	10
234 	SuperGamer 	10
235 	StressLinux 	10
236 	SoL 	10
237 	RUNT 	10
238 	Openwall 	10
239 	Magic 	10
240 	Deep-Water 	10
241 	clusterKNOPPIX 	10
242 	BeaFanatIX 	10
243 	tinysofa 	9
244 	ROSLIMS 	9
245 	QiLinux 	9
246 	MilaX 	9
247 	Media Lab 	9
248 	Linux+ Live 	9
249 	Kwort 	9
250 	Komodo 	9
251 	K12LTSP 	9
252 	eLearnix 	9
253 	Ufficio Zero 	8
254 	Pie Box 	8
255 	Penguin Sleuth 	8
256 	Openfiler 	8
257 	myLinux 	8
258 	Miracle 	8
259 	LliureX 	8
260 	gnuLinEx 	8
261 	Karoshi 	8
262 	Evinux 	8
263 	Clusterix 	8
264 	Càtix 	8
265 	cAos 	8
266 	AsianLinux 	8
267 	Tuquito 	7
268 	OpenNA 	7
269 	OpenLab 	7
270 	OLPC 	7
271 	MAX 	7
272 	LinnexOS 	7
273 	L.A.S. 	7
274 	How-Tux 	7
275 	Freeduc 	7
276 	eduKnoppix 	7
277 	DNALinux 	7
278 	DiscoverStation 	7
279 	BU Linux 	7
280 	BioBrew 	7
281 	Bayanihan 	7
282 	AbulÉdu 	7
283 	X-Evian 	6
284 	WIENUX 	6
285 	Plamo 	6
286 	Pingwinek 	6
287 	Nature's 	6
288 	Mayix 	6
289 	KnoSciences 	6
290 	Knoppel 	6
291 	Kalango 	6
292 	Honeywall 	6
293 	Hiweed 	6
294 	Hacao 	6
295 	Fermi 	6
296 	ERPOSS 	6
297 	ELX 	6
298 	Ekaaty 	6
299 	DANIX 	6
300 	ASLinux 	6
301 	AnNyung 	6
302 	Xteam 	5
303 	VNLinux 	5
304 	TupiServer 	5
305 	SuliX 	5
306 	Rails Live 	5
307 	Pingo 	5
308 	Co-Create 	5
309 	O-Net 	5
310 	Omoikane 	5
311 	NeoShine 	5
312 	Murix 	5
313 	Loco 	5
314 	LiVux 	5
315 	Insigne 	5
316 	Haansoft 	5
317 	GNIX 	5
318 	GEOLivre 	5
319 	Gelecek 	5
320 	FTOSX 	5
321 	EzPlanet One 	5
322 	Dzongkha 	5
323 	Condorux 	5
324 	Ankur Bangla 	5
325 	Wazobia 	4
326 	TumiX 	4
327 	pQui 	4
328 	Pilot 	4
329 	OpenLX 	4
330 	Nitix 	4
331 	NepaLinux 	4
332 	Myrinix 	4
333 	Julex 	4
334 	JoLinux 	4
335 	IndLinux 	4
336 	Impi 	4
337 	IDMS 	4
338 	Everest 	4
339 	Ehad 	4
340 	EduLinux 	4
341 	Dizinha 	4
342 	Burapha 	4
343 	Truva 	3
344 	Thisk 	3
345 	Swecha 	3
346 	NuxOne 	3
347 	Niigata 	3
348 	Muriqui 	3
349 	TFM 	1
``` Nowhere near 1895328 or whatever made-up number was thrown around before. And who uses Muriqui, TFM, or Swecha?

A lot of those are forks of other distros too. Really if you can put distros into families there are very few (mainstream) ones:

1) Linux Standard based
-- This is Fedora, OpenSuSE, RHEL, Mandriva, etc.
2) Debian based
-- Ubuntu, Debian, Knoppix, MINT, MEPIS, DSL, etc.
3) Slackware based
-- Slackware, SLAX, Backtrack, Puppy Linux, etc.

---

### Post by phrostbyte on 2008-07-16
> **Tomatz said:**
> Isn't the point of an API to enable you to code software without having access to the source code?

Why would Linux need an API?

It has an API. Just not for drivers. Linux is monolithic, it prefers drivers to be part of the kernel.

---

### Post by cardinals_fan on 2008-07-16
> **Yfrwlf said:**
> 
1) More software for Linux that works on any Linuxes means all users can get and share software, not to mention help out by reporting bugs and such, increasing Linux's adoption rate.

2) Developers can develop software for any distro and have their software actually easily get out to the masses, so that it can all be used, making more Linux software for everyone.

3) Freedom for everyone, period.

4) A bunch of 1 and 2 going back and forth, spiraling upwards, allowing more Linux users and developers to exist, making Linux take over the desktop markets.

5) Year of the Linux desktop! ;)
If Zero-Install can ever get going strong, fine.  It looks perfectly decent.  But, at the moment, I'm very happy with what we've got.  I don't care about the Linux adoption rate.

Back to the original purpose of this thread: "What does Linux need to be better?"  First, I think the real question is "What does **Ubuntu** need to be better?".  The Linux kernel is going strong and I don't have any issues with it.  I think that Ubuntu just needs **stability**.  Bug fixing and code auditing are the most important things right now.

---

### Post by madjr on 2008-07-16
> **cardinals_fan said:**
> If Zero-Install can ever get going strong, fine.  It looks perfectly decent.  But, at the moment, I'm very happy with what we've got.  I don't care about the Linux adoption rate.

Back to the original purpose of this thread: "What does Linux need to be better?"  First, I think the real question is "What does **Ubuntu** need to be better?".  The Linux kernel is going strong and I don't have any issues with it.  I think that Ubuntu just needs **stability**.  Bug fixing and code auditing are the most important things right now.

totally agree, stability and bug fixing is the best we could in the short term

---

### Post by Yfrwlf on 2008-07-17
The benefit is if, say, I'm on a DEB distro, and there's a program I want, but they only offer RPMs or source files which can be a nightmare and I don't want to fuss with that, I can then be able to, you know, install the RPM, and be able to use the program.

With the Burgdorf API, it won't just end there either, it won't just be being able for all users to install RPMs and DEBs on their distros, but it's being made extensible so that new formats can continue to be added.  Even if you're on a distro that has a big repository, you still don't have access to everything, there's still software that is RPM-only for example to those running Ubuntu and other DEB-based package managers, and you still haven't solved the problem of software projects/companies/developers being able to target you because that would be neglecting all the other distros and everyone would like a cross-distro solution(s).  If you're happy with the software you have now though, great.

Access to software.  That's good.  It's not rocket science.  And with that, I'm done with that subject unless someone has something new to add about it.

And no, my concern is for all of Linux, not just the Ubuntu package, which of course mostly contains upstream projects, the actual "Ubuntu part" of Ubuntu is pretty small, but of the software it does add it adds some nice usability features.  So, I find the attitude of only caring about "Ubuntu" and not "the other Linux stuff" very contradictory since Ubuntu is Linux.  So when anyone says stuff like "Ubuntu needs bug fixing" what they really mean is X needs bug fixing, and Gnome needs bug fixing, etc etc.  Just want to make sure everyone is clear on that. ;)

---

### Post by Canis familiaris on 2008-07-17
Ubuntu tries to benefit Upstream as much as possible:
Here is Mark Shuttleworth's thoughts on bug management:
[http://www.markshuttleworth.com/archives/145](http://www.markshuttleworth.com/archives/145)

---

### Post by Yfrwlf on 2008-07-17
> **Anurag_panda said:**
> Ubuntu tries to benefit Upstream as much as possible:
Here is Mark Shuttleworth's thoughts on bug management:
[http://www.markshuttleworth.com/archives/145](http://www.markshuttleworth.com/archives/145)

Yep and Launchpad and other projects do benefit upstream.  The Ubuntu selection of packages also gets a lot of users so they report a lot of bugs which also helps. :)

---

### Post by schmidtbag on 2008-09-27
To me, what Linux really needs is having the average user less reliant on the Terminal.  Linux without the terminal is a TERRIBLE idea, I'm just saying make it less mandatory.  For example, make a program for installing decompiled programs instead of the whole "./configure, make, make install" process.  It took me a long time to figure out when and how I'm supposed to do that, and even still I can get errors from it and have no idea how to fix them once in a while.

I find terminal based programs fine, I find terminal an excellent idea for root tasks, but its stupid how you have to rely on it for local tasks when there is no alternative.  Luckily, thats not an everyday thing, but for me its an every week thing.

I know many of you will disagree with this, but keep in mind that Terminal is a real turnoff to newbies.

---

### Post by jrusso2 on 2008-09-27
> **Yfrwlf said:**
> The benefit is if, say, I'm on a DEB distro, and there's a program I want, but they only offer RPMs or source files which can be a nightmare and I don't want to fuss with that, I can then be able to, you know, install the RPM, and be able to use the program.

With the Burgdorf API, it won't just end there either, it won't just be being able for all users to install RPMs and DEBs on their distros, but it's being made extensible so that new formats can continue to be added.  Even if you're on a distro that has a big repository, you still don't have access to everything, there's still software that is RPM-only for example to those running Ubuntu and other DEB-based package managers, and you still haven't solved the problem of software projects/companies/developers being able to target you because that would be neglecting all the other distros and everyone would like a cross-distro solution(s).  If you're happy with the software you have now though, great.

Access to software.  That's good.  It's not rocket science.  And with that, I'm done with that subject unless someone has something new to add about it.

And no, my concern is for all of Linux, not just the Ubuntu package, which of course mostly contains upstream projects, the actual "Ubuntu part" of Ubuntu is pretty small, but of the software it does add it adds some nice usability features.  So, I find the attitude of only caring about "Ubuntu" and not "the other Linux stuff" very contradictory since Ubuntu is Linux.  So when anyone says stuff like "Ubuntu needs bug fixing" what they really mean is X needs bug fixing, and Gnome needs bug fixing, etc etc.  Just want to make sure everyone is clear on that. ;)

Here is a few packages I had to go outside of .deb and the repository to run on Gutsy.

1. Real Player 11
2. IBM Lotus Symphony
3  Firefox 3 final.
4  zimbra client
5.  Antivir
6. PINE/PICO had to compile .deb would not work.
7.  Updated Picassa, and Google Earth
8.  Lightzone
9.  DVD2HDD
10. Softmaker Word Processor and Spread Sheet

---

### Post by cardinals_fan on 2008-09-27
> **schmidtbag said:**
> To me, what Linux really needs is having the average user less reliant on the Terminal.  Linux without the terminal is a TERRIBLE idea, I'm just saying make it less mandatory.  For example, make a program for installing decompiled programs instead of the whole "./configure, make, make install" process.  It took me a long time to figure out when and how I'm supposed to do that, and even still I can get errors from it and have no idea how to fix them once in a while.

I find terminal based programs fine, I find terminal an excellent idea for root tasks, but its stupid how you have to rely on it for local tasks when there is no alternative.  Luckily, thats not an everyday thing, but for me its an every week thing.

I know many of you will disagree with this, but keep in mind that Terminal is a real turnoff to newbies.
I can't think of any time I need to use the terminal on Xubuntu.  I certainly choose to, but it's not a requirement.

---

### Post by Yfrwlf on 2008-09-27
> **schmidtbag said:**
> To me, what Linux really needs is having the average user less reliant on the Terminal.  Linux without the terminal is a TERRIBLE idea, I'm just saying make it less mandatory.  For example, make a program for installing decompiled programs instead of the whole "./configure, make, make install" process.  It took me a long time to figure out when and how I'm supposed to do that, and even still I can get errors from it and have no idea how to fix them once in a while.

I find terminal based programs fine, I find terminal an excellent idea for root tasks, but its stupid how you have to rely on it for local tasks when there is no alternative.  Luckily, thats not an everyday thing, but for me its an every week thing.

I know many of you will disagree with this, but keep in mind that Terminal is a real turnoff to newbies.

Sure it is, the terminal requires existing knowledge mores-so than a GUI which displays a program's capabilities (to varying degrees of user-friendliness) to the user, and also all GUI programs should ideally have both command-line and GUI methods for interaction just because that is ideal for everyone.  Any way, a GUI is an environment that allows you to learn where-as the command line usually doesn't give you any help when you first start off.  I had to be taught about man pages, I had to be taught --help, and lots of the way things work I had to look up and read about.  With most GUI programs, that isn't required and the program's use is fairly straight forward.

Anyone who doesn't agree with that has been working at a command line for far too long and doesn't remember when they first struggled to learn how to use it. ;)

Any way, the point I really wanted to bring up is this: Do you know how there are different text output channels when a program is run?  They are called [standard streams]("http://en.wikipedia.org/wiki/Standard_streams").  Through channel 1, normal text gets spit out, but if there was an error, channel 2 spits out stuff.  This is useful for determining if there were any errors or not, etc etc.

Any way, what Linux needs right now to make the desktop more friendly is it needs to do one of two things, either funnel all/most of/whatever the standard errors out to the GUI, or they need to make a third channel explicitly for GUI output.  There are several instances where if a program doesn't work, nothing happens, and that's not good for a user's desktop, and the first response I give them is always "drop to a terminal and run it there to find out what happened".  That's not good as it requires terminal knowledge, when all they really needed to see is "can't find java" so they'd know oh, I don't have java installed, simple enough to fix.  There are several brainstorm entries about this. [[1]("http://brainstorm.ubuntu.com/idea/13387/"),[2]("http://brainstorm.ubuntu.com/idea/10529/"),[3]("http://brainstorm.ubuntu.com/idea/11995/"),[4]("http://brainstorm.ubuntu.com/idea/3729/"),[5]("http://brainstorm.ubuntu.com/idea/11595/")]

> **jrusso2 said:**
> Here is a few packages I had to go outside of .deb and the repository to run on Gutsy.

1. Real Player 11
2. IBM Lotus Symphony
3  Firefox 3 final.
4  zimbra client
5.  Antivir
6. PINE/PICO had to compile .deb would not work.
7.  Updated Picassa, and Google Earth
8.  Lightzone
9.  DVD2HDD
10. Softmaker Word Processor and Spread Sheet

Thank you, and there are of course a LOT more programs, because it's impossible for developers to package all their programs you could ever possibly want for you for your distro, and it's impossible for them to package every version as well nor should they have to, it's a royal pain.  Standardizing on at least one format (making all managers compatible with at least one format) to start out with is needed, and plugins for your managers to add more format compatibility when new formats become popular would be awesome as well.

> **cardinals_fan said:**
> I can't think of any time I need to use the terminal on Xubuntu.  I certainly choose to, but it's not a requirement.

That's fine and all, there are several improvements that could be made so that users never have to, because many **do** run into situations where they need to do so.  You're right though in that it's use is fortunately not required as much as it once was for most things.  You can unpack programs via the GUI, you can **run** programs even via the GUI, and even those improvements weren't until fairly recently, so all that needs to happen there is that needs to continue.  Make Linux **the** user-friendly OS in comparison to Mac and Windows.  It already is in some ways, so I want to see that continue of course, but not even being able to install a program that **can** run on Linux if it wasn't for the packaging mess standing in their way?  That's just so '90s and there's no reason for that.

---

### Post by yanom on 2009-01-29
> **Yfrwlf said:**
> Time for another mega-response of blatheringness. :grin:


More programs using these alternative formats would be nice, and I'm not sure why more don't use Autopackage or Zero Install or whatnot, but I think the key could be a combination of these three steps.



ZeroInstall = genius
Autopackage = designed by monkeys.

---

### Post by yanom on 2009-01-29
There is a program called GNU source installer.

---

### Post by cardinals_fan on 2009-01-29
I remember this thread...

---

