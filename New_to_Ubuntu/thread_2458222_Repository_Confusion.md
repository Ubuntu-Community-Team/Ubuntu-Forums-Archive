---
title: "Repository Confusion"
date: 2021-02-19
forum: New to Ubuntu
---

### Post by the-yipper on 2021-02-19
I am very confused about what is happening when I get the "updates are available" message and I install them. I am running I believe the 20.04 (is it focal fossil?) and such a newbie that I can't even be sure of that.
As you can hopefully see from the attachment that hopefully attached; I have three Audacity icons in my "applications" application, and clicking on each one brings up slightly different versions of Audacity. {I am a musician, and Audacity is probably the primary reason I need a computer).
Two of the icons bring up an Audacity that has a truncated effects menu and the inability to "add/remove" effects.
I believe they all bring up the latest 2.4 Audacity...
Another thing is, if I shut down my system (or do a software update that requires rebooting) the "recoverable projects" are recovered with no wave forms in them. I think this is because the different instances, represented by the 3 icons save the data files in different directories; and the effects menu problem probably has to do with the audacity.cfg file, which may be overwritten by each of the three icons competing for the same file; not to make this an audacity question that should be in an audacity forum, but the three different icons might be a problem that someone can solve here in the new to ubuntu forum...
Also, I have a "ubuntu software" application, plus a "software updater" one, along with a "software and updates" one; and to make matters worse, a "snap store"
I have no idea where the software I get is coming from, if it is the latest, and am totally confused about the "other software" thing that appears in probably all the above applications (if that's what they are) some of them say "disabled upon upgrade to focal fossil" -and so does that mean to ignore them; i.e. not check the box because they are disabled, since I think I am running 20.04 which I think is focal? Or does that mean that if I want to still maintain legacy code that I might have that has been deprecated by focal fossil, I should check the box?
I understand that you might have to give me a 60 credit hour college level course on repositories etc. to answer this question; but in lieu of that, is there a good O' Reilly book or online resource that could explain the whole thing to me? Thank you in advance (even for reading this far)

---

### Post by yancek on 2021-02-19
>   I believe the 20.04 (is it focal fossil?) and such a newbie that I can't even be sure of that.

You can be sure of that by copying and pasting the following into a terminal and looking at the otuput:

```
 lsb_release -d
```

Different ways to accomplish the same thing.  If you go to the Activities tab in the upper left and type in Software & Updates it will show different repository options/sources from which you can download software.  The software in the Ubuntu repositories is not always the 'latest' as it isn't put there until it is tested so it should be stable.  The simplest and fastest way to download/install software is from a terminal with the apt command.  Doing this you would need to know the name of the software.   

If the Other Software you refer to is what you see in Software & Updates, the Canonical Partners should be self explanatory and software you get from third party sources will show below that.

I'm not sure why your system shows 3 icons for Audacity.  Have you checked to see what each of these links points to?  Have you checked the .cfg file you mentioned?  

The link below is the Ubuntu documentation on repositories so start there.

  [URL="https://help.ubuntu.com/community/Repositories"]https://help.ubuntu.com/community/Repositories

[/URL]

---

### Post by Dennis N on 2021-02-19
Yes, the source of packages can get confusing. If you use the default "Ubuntu Software" application of Ubuntu 20.04 and search for Audacity, we are offered two choices. See screenshot. The first is the default 2.3.3 package (a .deb package) and the second is a snap package of version 2.4.2. To see this information open each package's page, and look at the Details section, where the version and source are listed. See second screenshot. Note from the first screenshot, that I have both installed, accounting for two icons.

Unlikely for a new user, but there may also be a PPA version or a Flatpak version of Audacity which are another story - you need to take extra steps to get one of these.

---

### Post by grahammechanical on 2021-02-19
With Linux there is always more than one way to do something. In my opinion, this has become less complicated over the years with Ubuntu. We can use the command line or we can use a utility with a Graphical User Interface (GUI).

Software Updater is the GUI utility that will update/upgrade the operating system. Software & Updates is the GUI utility that gives us some control over where (repositories or sources) we get software from. And, hence from where the updates come from.

Ubuntu Software (Software) is the app store that we download & install applications from. We can also use it to remove (delete) applications. We can also do all this from the command line and it is also possible to install another GUI utility that will also do this. It is called Synaptic Package Manager. It has a long pedigree.

Ubuntu is built on a Linux distribution called Debian. In Debian all software whether it be libraries or applications is packaged in the Debian Package format (deb). A few years ago the developers of Ubuntu (commercial name = Canonical) came up with a way of packaging applications that they called Snap packaging. The Snap store was a GUI way to install/remove Snap apps. By now the Snap store & Ubuntu Software should have been blended together. In fact in my install of 20.04 the Snap store icon has been removed.

Development of Linux distributions does not stop and developers have their own ideas of where they want Linux distributions to progress to. I think that it is possible to use Ubuntu in the same way we use a television or radio - without knowing anything about how it actually does what it does. But when we become curious we find ourselves struggling to understand concepts and methods.

Regards

---

### Post by CatKiller on 2021-02-19
> **the-yipper said:**
> am totally confused about the "other software" thing that appears in probably all the above applications (if that's what they are) some of them say "disabled upon upgrade to focal fossil" -and so does that mean to ignore them; i.e. not check the box because they are disabled, since I think I am running 20.04 which I think is focal?

The packages for Ubuntu (aside from snaps, which are a parallel self-contained sandboxed thing) are distributed from Ubuntu's package repositories. Canonical takes a fairly conservative approach to their inclusion and testing, so not every piece of software will be there, and it's unlikely to be the latest version, although security updates and bugfixes get backported to the versions that are there. You can supplement the software that's available from the repositories by adding additional sources of packages called PPAs (Personal Package Archives) with more or newer packages.

Each PPA is arranged specifically for each Ubuntu release, since a given version of software is going to require particular versions of other packages. Because of that, when you upgrade from one release to another, all PPAs are disabled to prevent breakage. They aren't *deleted*, since that would suck from a usability perspective, they just aren't used any more; it's achieved by commenting out a particular line of the configuration file along with an explanation of what's happened and why. Those lines are also automatically changed to point to the equivalent PPA for the new release although no check is done for whether that PPA for the new release actually exists. 

If the PPA exists, and you still require the software provided by it even though you're on the newer Ubuntu release, you can re-enable it. If you no longer neediit because the software you were getting from it is now provided by your new Ubuntu release, you can remove it entirely. Those are decisions for the user to make, so the upgrader just takes the middle ground of not using the PPA by default.

---

### Post by rsteinmetz70112 on 2021-02-19
I'll chime in a little here. 
Unless you have a specific need for something special I would stay with the Ubuntu repositories and away from PPAs until you get comfortable with Linux. 
I would also stay with the LTS (long Term Support) versions as they are supported for longer otherwise you will find yourself upgrading fairly often.  20.04 is the latest LTS version, the next one will be 22.04, out around April of 2022 with upgrades availible 3-4 months later.

---

