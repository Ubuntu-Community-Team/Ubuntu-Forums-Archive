---
title: "What should I use for revision control of a customized Ubuntu install"
date: 2010-12-20
forum: Programming Talk
---

### Post by Jason O on 2010-12-20
Here is the scenario. 

I have an Ubuntu install on a VirtualBox instance. I need to be able to login, modify the system, then commit the entire install to some type of revision control system. At the same time, my associates need access to the same repo so they can make commits.

I use git for web development, but adding and entire install to a git repo is memory overflow city. From what I can tell, somewhere inside "/lib" directory, git got into some sort of loop and ran out of memory.

I don't remember exactly what happened when trying svn, but it didn't work right either.

So my question is, what should I be using for revision control of an entire installation?

Oh, and the way this will be used is the latest version in the repo will be tarred up and put on a usb partition along side a live environment. The live enviroment is used to format the disks, and untar the system. After/during the install, we manually change the host name and tweak a couple files. We have done this successfully with no problems. But not with revision control. Apparently, tar doesn't choke on the funky lib files.

---

### Post by worksofcraft on 2010-12-21
> **Jason O said:**
> Here is the scenario. 

I have an Ubuntu install on a VirtualBox instance. I need to be able to login, modify the system, then commit the entire install to some type of revision control system. At the same time, my associates need access to the same repo so they can make commits.

I use git for web development, but adding and entire install to a git repo is memory overflow city. From what I can tell, somewhere inside "/lib" directory, git got into some sort of loop and ran out of memory.

I don't remember exactly what happened when trying svn, but it didn't work right either.

So my question is, what should I be using for revision control of an entire installation?

Oh, and the way this will be used is the latest version in the repo will be tarred up and put on a usb partition along side a live environment. The live enviroment is used to format the disks, and untar the system. After/during the install, we manually change the host name and tweak a couple files. We have done this successfully with no problems. But not with revision control. Apparently, tar doesn't choke on the funky lib files.

My first impulse would be to bung the whole thing in a tar ball and splice a version .major.minor number onto it's name.

"Revision control" then consists of choosing the tar file that has the version number you want.

This is roughly what they do for shared libraries but using library format instead of archive. Personally I would stick the version number before the file name suffix instead of after it so that it remains a *.tar file instead of becoming a *.7 file if you know what I mean ;)

---

### Post by Jason O on 2010-12-21
> **worksofcraft said:**
> My first impulse would be to bung the whole thing in a tar ball and splice a version .major.minor number onto it's name.

"Revision control" then consists of choosing the tar file that has the version number you want.

This is roughly what they do for shared libraries but using library format instead of archive. Personally I would stick the version number before the file name suffix instead of after it so that it remains a *.tar file instead of becoming a *.7 file if you know what I mean ;)

I appreciate your response, but I still need the ability for multiple developers to commit to the project simultaneously. Surely, Ubuntu doesn't have just one developer making system changes at a time?

---

### Post by worksofcraft on 2010-12-21
> **Jason O said:**
> I appreciate your response, but I still need the ability for multiple developers to commit to the project simultaneously. Surely, Ubuntu doesn't have just one developer making system changes at a time?

Isn't what you are asking for a bit like a whole independent new distro tree of Linux? Ubuntu solves it by having identified releases like "Natty Narwhal" and "Hardy Heron"... I'm not sure how it works between releases but I don't think they support branching.

---

### Post by Jason O on 2010-12-21
> **worksofcraft said:**
> Isn't what you are asking for a bit like a whole independent new distro tree of Linux? Ubuntu solves it by having identified releases like "Natty Narwhal" and "Hardy Heron"... I'm not sure how it works between releases but I don't think they support branching.

What I am wanting to do is put an entire Ubuntu install under revision control so that multiple developers can modify the system, then commit those changes to a central repository.

The resulting repo will be tarred up for clone installs on multiple machines with identical hardware.

I know that Ubuntu uses bzr/Bazaar for managing the source of their various *packages*....but what do they use for the core system??? Or what do any of the many distro developers use for revision control of their systems?

---

### Post by eeperson on 2010-12-21
Ubuntu puts the source code for the individual packages under version control rather than the entire OS. Everything is a package, even the kernel and the tools to install packages.  If you need to make code change I recommend keeping the source, for just the packages you need to change, in version control.

For making config changes, what you should use depends on what you are trying to do.  If you are looking to manage the configuration of multiple installs I would recommend using something like [Puppet]("http://en.wikipedia.org/wiki/Puppet_%28software%29").  If you are trying to make a custom Ubuntu installer look [here]("https://help.ubuntu.com/community/InstallCDCustomization").  You can then version the config files for these tools.

---

### Post by worksofcraft on 2010-12-21
Virtual box has a handy "snapshot" facility that basically then  records changes to the disk image since last snapshot. That way you can always revert to an earlier "revision".

Also you can export "appliances" from virtual box and when you install them on another virtual machine you have a clone of your original.

In this way I have a base development appliance where I got rid of everything that I didn't need for software development. From that I derived an appliance that has all the dev tools and libraries installed. I use imports of that as the basis for building and testing software on an otherwise virgin system.

---

### Post by Jason O on 2010-12-21
> **eeperson said:**
> Ubuntu puts the source code for the individual packages under version control rather than the entire OS. Everything is a package, even the kernel and the tools to install packages.  If you need to make code change I recommend keeping the source, for just the packages you need to change, in version control.

For making config changes, what you should use depends on what you are trying to do.  If you are looking to manage the configuration of multiple installs I would recommend using something like [Puppet]("http://en.wikipedia.org/wiki/Puppet_%28software%29").  If you are trying to make a custom Ubuntu installer look [here]("https://help.ubuntu.com/community/InstallCDCustomization").  You can then version the config files for these tools.

Ok, so if in Ubuntu development everything is a package, at what stage does someone press the "assemble" button? There has to be a point at which the packages converge to form the installer/live CD/iso/etc. If there is a "package" that ends up being the master container for the installer/iso/live system, what is it?

Puppet in not what I need here. I need installable systems ready to go. But, Puppet does look cool for a different project, I'll definitely look into that.

Thanks for your time and feedback eeperson.

> **worksofcraft said:**
> Virtual box has a handy "snapshot" facility that basically then  records changes to the disk image since last snapshot. That way you can always revert to an earlier "revision".

Also you can export "appliances" from virtual box and when you install them on another virtual machine you have a clone of your original.

In this way I have a base development appliance where I got rid of everything that I didn't need for software development. From that I derived an appliance that has all the dev tools and libraries installed. I use imports of that as the basis for building and testing software on an otherwise virgin system.

Yeah, I have been using VirtualBox for quite a while (big fan). I could use VB for poor mans version control if it were only me working on the project. But in this case, it's VERY important that multiple developers can work on the project at the same time. There would be no way of merging changes made by two different developers.

Thanks again worksofcraft.

------

A few years ago, I made a heavily customized Mepis linux live cd. I used the method they had described in their wiki for customization. It envolved chrooting into the live environment and doing the "development" while inside.

I'm fine with wiki'ish CD customizing methods, but that does not leave me with something that can be merged.

I guess we will just have to build a base installer, and control everything else through packages. Then we'll have to refresh the build with a typical customization process, sucking in our updated packages.

It still seems a bit hackish. I imagine there is some kind of master build script that can assemble the installer/live CD from the appropriate packages. Does anyone know if there is such a script?

---

### Post by eeperson on 2010-12-22
> **Jason O said:**
> Ok, so if in Ubuntu development everything is a package, at what stage does someone press the "assemble" button? There has to be a point at which the packages converge to form the installer/live CD/iso/etc. If there is a "package" that ends up being the master container for the installer/iso/live system, what is it?

> **Jason O said:**
> I imagine there is some kind of master build script that can assemble the installer/live CD from the appropriate packages. Does anyone know if there is such a script?

You're right that there is an 'installer' that exists outside of the packages.  Did you see the second link in my last post?  It gives directions for doing this very thing.  The page I linked gives directions for doing this for the 'Alternate Install' but it also has links to directions for doing the same to live CDs.

---

### Post by ssam on 2010-12-22
if git can't manage then i doubt any of the others will.

maybe one of the non distributed RCSs (SVN, CVS) might work better, as they do not try to keep the entire history around.

alternatively could you just use revision control on some directories?

or look at tools like [http://fai-project.org/](http://fai-project.org/)

---

### Post by Jason O on 2010-12-22
> **eeperson said:**
> You're right that there is an 'installer' that exists outside of the packages.  Did you see the second link in my last post?  It gives directions for doing this very thing.  The page I linked gives directions for doing this for the 'Alternate Install' but it also has links to directions for doing the same to live CDs.

Yes, I saw the link and I'm familiar with this process. But thanks for the info. I just don't see how this will support a group development environment. This is the biggest challenge, and a vital component of this project.

> **ssam said:**
> if git can't manage then i doubt any of the others will.

maybe one of the non distributed RCSs (SVN, CVS) might work better, as they do not try to keep the entire history around.

alternatively could you just use revision control on some directories?

or look at tools like [http://fai-project.org/](http://fai-project.org/)

FAI looks pretty interesting, thanks for the tip.

-----------

**Conclusion:** I have a few options and I see the limitations. I think the best option for us would be to get a solid base installer CD built (by one freakin' guy) and then do all other development in packages...and then run some kind of 'build' script to mount the base CD and update it (remove stuff, add stuff, change stuff).

Thanks for the help!

---

### Post by eeperson on 2010-12-22
> **Jason O said:**
> Yes, I saw the link and I'm familiar with this process. But thanks for the info. I just don't see how this will support a group development environment. This is the biggest challenge, and a vital component of this project.

The alternate install lets you script the installation with 'preseed' config files.  The config files will allow you to create repeatable builds.  You can put the config files under version control which will allow you to collaborate on them.

---

