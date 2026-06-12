---
title: "Puppy Linux and its applications"
date: 2007-12-09
forum: Other OS Talk
---

### Post by willie_wang on 2007-12-09
Hi everyone! Anyone used puppy linux yet?

All I hear are good things about it. I love ubuntu, but I'm going linux crazy and want to try more distros.

one question. is it easy to install more apps on puppy? like can i compile my own applications and then run it on puppy? like bluefish and inkscape and such like? what are your experiences? what are the downsides to puppy? anything you can give me really!

thanks in advance people!

Willie

---

### Post by darrelljon on 2007-12-09
The biggest drawback with Puppy is it is a single user distro.

---

### Post by wjp.reg on 2007-12-09
> **willie_wang said:**
> Hi everyone! Anyone used puppy linux yet?

All I hear are good things about it. I love ubuntu, but I'm going linux crazy and want to try more distros.

one question. is it easy to install more apps on puppy? like can i compile my own applications and then run it on puppy? like bluefish and inkscape and such like? what are your experiences? what are the downsides to puppy? anything you can give me really!

thanks in advance people!

Willie

Why not check the [puppy user forum]("http://murga-linux.com/puppy/")

---

### Post by mb125 on 2007-12-09
I run puppy on a USB drive when im at work and want to get around the proxy server that blocks everything. It only takes up about 93mb and does not lag like a live CD

---

### Post by dizee on 2007-12-09
> **willie_wang said:**
> Hi everyone! Anyone used puppy linux yet?

All I hear are good things about it. I love ubuntu, but I'm going linux crazy and want to try more distros.

one question. is it easy to install more apps on puppy? like can i compile my own applications and then run it on puppy? like bluefish and inkscape and such like? what are your experiences? what are the downsides to puppy? anything you can give me really!

thanks in advance people!

Willie

There are a few different ways to install applications in puppy. The official packages are .pet files which can be installed from a package manager. There are also other community maintained packages called .pup files which you can download and install. The package selection isn't massive but almost all of the usual suspects are there, such as Opera, Openoffice, Inkscape etc.

Also since 3.0 was released Puppy is compatible with Slackware packages. There is support for .debs too but it isn't perfect.

You can compile from source too although the tools for it aren't installed by default, it's easy to get them though.

As for experiences, Puppy is blazing fast. Even on a pentium II it flies along, but without sacrificing functionality. It has an app for everything and if you use IceWM it looks great too.

The only (arguable) downside is that it's not really designed to be fully installed to a hard drive, as you run as root. Which in theory is  not a great idea.

---

### Post by willie_wang on 2007-12-09
darrelljon: Surely it wouldn't matter so much if you were the only user the machine??

Compiling from source is something I would definitely need to do as some of the hardware drivers I need (acer_acpi) need to compiled from source... however, i'm a bit disturbed at the fact that it's not designed to be fully installed on the hard disk, as this is the purpose i wanted for puppy.

Has anyone fully installed this to their hard disk? I've read up on how to do it, but as I'm a noob, I just want some feedback as to whether this is such an easy process and how well it runs from the hard disk??

Cheers for your responses guys...

ps. The puppy forums don't seem nearly as active as these forums :-\

---

### Post by init1 on 2007-12-09
> **willie_wang said:**
> Hi everyone! Anyone used puppy linux yet?

All I hear are good things about it. I love ubuntu, but I'm going linux crazy and want to try more distros.

one question. is it easy to install more apps on puppy? like can i compile my own applications and then run it on puppy? like bluefish and inkscape and such like? what are your experiences? what are the downsides to puppy? anything you can give me really!

thanks in advance people!

Willie
Puppy has it's own package management, and is now binary compatible with Slackware. Bluefish and inkscape are already installed, so you won't have to worry about those.

---

### Post by willie_wang on 2007-12-09
> **init1 said:**
> Puppy has it's own package management, and is now binary compatible with Slackware. Bluefish and inkscape are already installed, so you won't have to worry about those.

yup the package management looks pretty good. :) just another question. i know how to compile programs in ubuntu... is it a similar process in Puppy?

eg. sudo make && sudo make install?

---

### Post by init1 on 2007-12-09
> **willie_wang said:**
> yup the package management looks pretty good. :) just another question. i know how to compile programs in ubuntu... is it a similar process in Puppy?

eg. sudo make && sudo make install?
In Puppy, you are always root so you never need sudo. I'm not sure if the newest version has gcc installed by default, but in the older versions I had to do it manually. I do not, however, remember how I did it.

---

### Post by RAV TUX on 2007-12-09
> **willie_wang said:**
> Hi everyone! Anyone used puppy linux yet?

All I hear are good things about it. I love ubuntu, but I'm going linux crazy and want to try more distros.

one question. is it easy to install more apps on puppy? like can i compile my own applications and then run it on puppy? like bluefish and inkscape and such like? what are your experiences? what are the downsides to puppy? anything you can give me really!

thanks in advance people!

WilliePuppy is a very, very nice distro.

Easy to use, and fun I am surprised it is not the most used Distro of the moment.

---

### Post by willie_wang on 2007-12-09
> **init1 said:**
> In Puppy, you are always root so you never need sudo. I'm not sure if the newest version has gcc installed by default, but in the older versions I had to do it manually. I do not, however, remember how I did it.


this may sound really stupid, but bear in mind, all this jargon is a bit confusing... ok. i understand that you are always root. i'm okay with that (kind of).

but i've read this [http://www.puppylinux.com/download/release-3.00.htm](http://www.puppylinux.com/download/release-3.00.htm) and can't tell whether the gcc compiler is actually included (perhaps someone with a higher IQ than i could help? i can see gcc in the top line of the release notes, but don't know what this means? :()

and it says that puppy linux can run slackware packages... now on this page [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/) there is a slackware build package for the acer_acpi... could i use the files in [the link]("http://slackbuild.strangeworlds.co.uk/k/acer_acpi/") in puppy to install the acer_acpi??

thanks for all your responses & init1 :)

btw ravtux, haha, nice avatar :lolflag:

---

### Post by dizee on 2007-12-09
The compiler is not included by default, you download a file and put it in /mnt/home to compile from source. Have a read of [http://puppylinux.org/wikka/Compiling](http://puppylinux.org/wikka/Compiling)

Slackware packages need to be  .tar.gz files to work I think.

---

### Post by toomuchcomputertime on 2008-07-22
I am a puppy user. I used to use 'buntu, but have now switched to puppy because its ease of use, portability (I am now running off of my flash drive), and speed. The newest release Dingo is even better than the previous releases.

---

