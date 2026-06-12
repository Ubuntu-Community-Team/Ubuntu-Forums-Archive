---
title: "Repository question????"
date: 2006-04-04
forum: Repositories &amp; Backports
---

### Post by MJSOnline on 2006-04-04
Ok. I want to install things like xdvdshrink and other packages that are not in the repository.

What packages or source applications do I need to download and how do I put them in my sources list so that Synaptic Package Manager can see them. I can then select them and let Synaptic Package Manager install / configure them...

So I have a folder called Packages and one called sources. Both have for example xdvdshrink in them. One a deb and one a source file.

I then want to put the folder address into my sources list so, /media/SD/Packages - and - /media/SD/Sources.

Does that make sense? M

---

### Post by engla on 2006-04-04
Your questions make sense halfway. Putting things in synaptic won't automatically be a good thing, but it could of course be. Normally, to install a single package, you use

dpgk -i package.deb

in the terminal, or [if you installed gdebi] open the file with gdebi. The former won't resolve dependencies, but you can do that with 

apt-get -f install

if all dependencies are in the available repositories.

Anyway, if you want a "local repository", it's perfectly possible. [Here is a link]("http://wclp.sourceforge.net/documentation/adminguide.wclin/node8.html")

---

### Post by MJSOnline on 2006-04-05
A local repository sounds the way to go.  How do i input that into my current sources list?  Do I just download the deb packages tho?  Or does it install via the source package too?  So I have dvd123.tar.bz2 would this work too?  Thanks for the link. Matthew

---

