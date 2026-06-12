---
title: "how long is the support fo edubuntu 8.04"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by iamclueless on 2008-05-25
hi

i know the 6.06 releases has long term  support for edubuntu. however the documentation seems to suggest that this release does not have long term support.  please clarify. thanks

---

### Post by Inxsible on 2008-05-25
Can you point us to the said document ?

---

### Post by sam_delta on 2008-05-25
i had the idea that every supported derivative (kubuntu, ubuntu, xubuntu and edubuntu) are LTS when a LTS is released
ill do some research on that tho

sam

---

### Post by Inxsible on 2008-05-25
> **sam_delta said:**
> i had the idea that every supported derivative (kubuntu, ubuntu, xubuntu and edubuntu) are LTS when a LTS is released
ill do some research on that tho

sam
Xubuntu, btw, is not an officially supported OS.

[http://canonical.com/projects](http://canonical.com/projects)

[http://www.ubuntu.com/products/whatisubuntu/derivatives](http://www.ubuntu.com/products/whatisubuntu/derivatives)

---

### Post by sam_delta on 2008-05-25
well, found the info
info from 
[http://www.edubuntu.org/news/8.04-release](http://www.edubuntu.org/news/8.04-release)

> The base Ubuntu 8.04 is a Long Term Support release and will be supported for 36 months on both desktops and servers through our managed software repositories. The desktop package manager notifier checks automatically for security and maintenance updates / patches and prompts from the tool bar for simple selection and installation.

The Edubuntu 8.04 add-on desktop and application bundle will be supported for 18 months on both desktops and servers through our managed software repositories.

sam

---

### Post by sam_delta on 2008-05-25
> **Inxsible said:**
> Xubuntu, btw, is not an officially supported OS.

[http://canonical.com/projects](http://canonical.com/projects)

[http://www.ubuntu.com/products/whatisubuntu/derivatives](http://www.ubuntu.com/products/whatisubuntu/derivatives)

didnt knew that, thx for pointing that out.

sam

---

### Post by Inxsible on 2008-05-25
> **sam_delta said:**
> didnt knew that, thx for pointing that out.

sam
yup. It was strange to me when I found out too :(

I would think xfce and Xubuntu are pretty much standard like Gnome and KDE are. But who knew !!!!

---

### Post by sam_delta on 2008-05-25
yeah, i had been actually using xubuntu on an old machine for almost a year without knowing it wasnt supported,:p o well, its still good for old hardware

sam

---

### Post by Inxsible on 2008-05-25
> **sam_delta said:**
> yits still good for old hardware

samDamn right it is !! I installed it on an old laptop i found lying around. Although, I did find IceWM and Fluxbox to be faster on the machine. I still like Xubuntu because I can run the in-built compositor to run AWN- which I simply cannot do without ;)

Compiz just cannot run on that rig....so I can't run AWN under Fluxbox and xcompmgr was giving me errors with AWN

---

### Post by sam_delta on 2008-05-25
yeah, true, plus i find xubuntu way more stable than fluxbuntu, even tho fuxbuntu is faster

sam

---

### Post by iamclueless on 2008-05-25
whoa thanks for the xubuntu info.

so let me get this right... ubuntu has a whole is supported... but xubuntu is not... how does that work?? i would have thought that under the hood theyre the same... and receive the same updates.  i always assumed that it ku, xu, and ubuntu were basically just different WM for the same thing

so out of curiousity where would a command line barebones install stand???
thanks

---

### Post by phoenix_abhi on 2008-05-25
Why the Edubuntu have only 18 months support ?

---

### Post by Inxsible on 2008-05-25
> **iamclueless said:**
> whoa thanks for the xubuntu info.

so let me get this right... ubuntu has a whole is supported... but xubuntu is not... how does that work?? i would have thought that under the hood theyre the same... and receive the same updates.[COLOR=Red]  i always assumed that it ku, xu, and ubuntu were basically just different WM for the same thing[/COLOR]

so out of curiousity where would a command line barebones install stand???
thanksYou are right about that part except that Gnome/KDE/Xfce are not just WM, they are DM as in desktop managers. More info [here]("http://xwinman.org/") Its not "officially supported" by Canonical. But then again, how often do you ask Canonical for support? I am sure you most likely ask all your support question on this forum and we support Xubuntu ;-)

---

### Post by iamclueless on 2008-05-26
> **Inxsible said:**
> You are right about that part except that Gnome/KDE/Xfce are not just WM, they are DM as in desktop managers. More info [here]("http://xwinman.org/") Its not "officially supported" by Canonical. But then again, how often do you ask Canonical for support? I am sure you most likely ask all your support question on this forum and we support Xubuntu ;-)

right... so what would the actual difference be from a DE or WM that is supported vs one that is not.

im assuming that the difference would be maintenance of the xubuntu xfce runs out at 18 months while the gnome and kde ones would be maintained for 3 years

to extend the question a bit.  what is the problem if any with running an unsupported ubuntu.  for example, my old pc is running feisty... i think support will be pulled in October.  is there a problem if i was to continue running this for another year.  aside from not getting packages backported *i could compile i guess* what else could be a problem

thanks

---

### Post by sayakb on 2008-05-26
A desktop environment has a Window manager, a dedicated file manager, some dedicated apps and applets.
You might say that Window manager + things that make the WM usable = DE

---

### Post by iamclueless on 2008-05-26
not what i meant...

as in what is the difference between a WM or DE that is supported for 3 years(ubuntu and kubuntu) vs using one that is supported for 18 months (Xubuntu) or one not supported at all 

so lets say you run xubuntu or a vanilla instal plus a WM of your choice for 18 months... what are you actually losing once the canonical support runs out

or ultimately what are you losing from say sticking with a Gutsy install for the next 3 years instead of switching to Hardy.  the only thing im aware of would be the inability to get new packages.... but then cant you start using debian packages?

someone want to clarify

---

### Post by Inxsible on 2008-05-26
The only thing you are losing is the ability to get new software - which after 18 months, stopped getting developed for that release. just like you mentioned.

I mean, if any software comes out 20 months after the release of Gutsy - chances are they probably will not have packages for Gutsy as they most likely will be developed on Hardy, Intrepid or whatever the J version is(3 releases in 18 months). These software may also depend/require newer versions of existing libraries, which a Gutsy install may not have and may also not be able to get because of some other dependency issue.

Eventually you may also not be able to upgrade any software.

---

### Post by Duck2006 on 2008-05-26
cant you start using debian packages?

You can, but not all will work.

---

### Post by Inxsible on 2008-05-26
One scenario listed below may actually screw up your install.

Lets say program A depends  on libraries X and Y. Program B depends on X - version 2.05. Now assume that library Y had issues and has been completely replaced by Z in the newer OS releases.

Trouble starts when X updates to the newer version and Y cannot be because no new versions are available, making program A unusable. Because X got updated to a newer version, B may stop working. If more and more of this happens - most your programs will be rendered unusable leaving you a borked system.


In short, you don't have to upgrade to the new version as soon as it releases. You can always do it just before the next version releases. That way you are just 1 behind the latest and always "supported". And because you upgrade 5-6 months after the release - you can be pretty sure that you have a stable OS since most people have reported the bugs and they may have been fixed.

---

