---
title: "Advice about a few things"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by Azuma on 2012-11-18
Hi everyone, complete newb with Linux here :)
Just wanted some advice on certain things about Ubuntu, I will be moving over to arch after I finish learning more about Linux but until then I need to make the best of Ubuntu.
So basically I would like to know the following:

Any programmes I should install ( Already have wine )
Any commands I should know
Anything I should learn to improve my knowledge of Linux

If anyone would like to suggest things please go ahead, will learn anything and everything I possibly can :P
Thanks in advance.
Azuma

---

### Post by mlentink on 2012-11-18
Could you perhaps narrow things down a bit by explaining what you want to achieve, what you would like to do? System administration? Programming? 

As to commands, take a look at linuxcommand.org

---

### Post by Azuma on 2012-11-18
Not trying to achieve anything really, just moved from windows to Linux and I am trying to learn as much as possible about Linux, maybe then I may try to " achieve " something.
Who knows, I literally installed Linux because I like the feel of it, oh and without gates running Microsoft I don't exactly feel safe, who knows what they are doing with our information now. :P

---

### Post by MG&amp;TL on 2012-11-18
Applications: wait until you need to do something. Then look to see if you already have it. Then look in the software centre to see if you can get it easily. Then do a bit of googling to see if you can find instructions or download. Then ask here. :)

Commands: depends whether you like working with a textual prompt or not. Personally, it's a lot faster and more efficient for certain tasks, and I love my shell to bits. If you do decide you want to learn the linux shell (it's *very* extensive), there's a list of resources here to get you started (!) : [https://help.ubuntu.com/community/CommandLineResources]("https://help.ubuntu.com/community/CommandLineResources")

Things to know: pick something you're interested in about your system. Prepend "ubuntu" or "linux" to it if you think it's necessary. Then go for your search engine. There's a vast amount of material out there.

---

### Post by Azuma on 2012-11-18
There's loads of things I need to do, it's just a case of finding the apps I need.
Photoshop apparently won't work with my version of ubuntu without taking something from a windows registry.
So I am stuck with gimp for now, Utorrent will not install for some unknown reason, so I am trying to find a decent download manager ( like freedownloadmanager ) but for Linux and if it supports torrents and magnet links even better.
Need a decent theme for my system and music software and probably a lot more but its 1am here so I wont try to work it all out now.
Thanks for the CMD link is really helpful.

---

### Post by MG&amp;TL on 2012-11-18
> **Azuma said:**
> There's loads of things I need to do, it's just a case of finding the apps I need.
Photoshop apparently won't work with my version of ubuntu without taking something from a windows registry.
So I am stuck with gimp for now, Utorrent will not install for some unknown reason, so I am trying to find a decent download manager ( like freedownloadmanager ) but for Linux and if it supports torrents and magnet links even better.
Need a decent theme for my system and music software and probably a lot more but its 1am here so I wont try to work it all out now.
Thanks for the CMD link is really helpful.

Photoshop I can't help with, but don't be "stuck with" GIMP. It's an incredibly powerful tool, it just has a quirky way of doing things.

UTorrent is of dubious quality. Or at least it was the few times I ran it (on XP). There's a built-in (and very capable) torrent client called "Transmission" installed by default. For download managers, there's an *axel* frontend that's available in the software centre.

Linux is a little more configurable than other platforms. "System themes" don't really exist. Icon themes, desktop themes, application themes, even sound themes exist. But not as one package. Also, there is more than one interface available. Try out a few, see what your preferences are like. Examples include LXDE, Xfce, Unity (Ubuntu's default), Gnome-shell, and KDE. Plus a load of weird and/or wonderful ones, ranging from the likes of *ratpoison* to *enlightenment*.

---

### Post by andrew.46 on 2012-11-18
> **Azuma said:**
> 
Photoshop apparently won't work with my version of ubuntu without taking something from a windows registry.


Perhaps have a look at virtualisation, an application such as VirtualBox will allow you to run Windows in a virtual machine and then Photoshop can be easily installed. Worth having a good look at Gimp first though...

---

### Post by newb85 on 2012-11-18
Others have hinted at it, but I'll say it directly.  When you want to do something, your first approach should not be to grab a Windows program for it and try running it on Wine.  Unless you have a specific reason you're tied to a Windows application, you're better off trying native Linux apps.

[list]
[*]Start with applications in the main repositories.  Ways to install them include the Software Center, apt-get (from the terminal), and Synaptic (not installed by default).
[*]Look for applications that can be installed by adding a PPA.  PPAs can be added from the Software Sources dialog or using add-apt-repository (from the terminal).  Once the PPA has been added, the method for installing is the same as for packages in the main repositories.
[/list]

---

### Post by critin on 2012-11-18
> **Azuma said:**
> Hi everyone, complete newb with Linux here :)
Just wanted some advice on certain things about Ubuntu, I will be moving over to arch after I finish learning more about Linux but until then I need to make the best of Ubuntu.
So basically I would like to know the following:

Any programmes I should install ( Already have wine )
Any commands I should know
Anything I should learn to improve my knowledge of Linux

If anyone would like to suggest things please go ahead, will learn anything and everything I possibly can :P
Thanks in advance.
Azuma

If you truly want to learn about linux, don't hang on to a Windows crutch through wine.  There are linux programs to do anything wine can do.  If you absolutely have to use a win program, dual boot with windows and use it directly.

Learn by doing.  Work with it, do things, explore, experiment.  Read the forums for how to solve problems, even if you don't have any issues--you'll be surprised how you'll grow if you do that.

Good luck and have fun!

---

### Post by newb85 on 2012-11-18
> **critin said:**
> Learn by doing.  Work with it, do things, explore, experiment.  Read the forums for how to solve problems, even if you don't have any issues--you'll be surprised how you'll grow if you do that.

Put another way, play with Ubuntu until you break it, then figure out how to fix it.  Repeat as needed.

---

### Post by deadflowr on 2012-11-18
Since you're planning on installing it anyway, why not bypass Ubuntu and just install Arch.
You'll probably learn more faster that way then by using Ubuntu.

---

### Post by mlentink on 2012-11-19
and ah...

please read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Azuma on 2012-11-19
> **deadflowr said:**
> Since you're planning on installing it anyway, why not bypass Ubuntu and just install Arch.
You'll probably learn more faster that way then by using Ubuntu.
I already installed it, but after installing the base I got lost.
I needed a desktop environment asap so I quickly put Ubuntu on, I am using VirtualBox to test stuff and run Arch test installs already.
The only reason I want photoshop is because i'm used to it and Gimp just will not do what I need, it's not a bad programme but It wont do what I want.

---

### Post by slickymaster on 2012-11-19
> **newb85 said:**
> Put another way, play with Ubuntu until you break it, then figure out how to fix it.  Repeat as needed.

Yeap. Trial and error has always been, since the dawn of mankind, the best way to learn.

---

### Post by critin on 2012-11-19
> **newb85 said:**
> Put another way, play with Ubuntu until you break it, then figure out how to fix it.  Repeat as needed.

Absolutely.   Breaking stuff is a great opportunity to move ahead.

---

### Post by ForEveryman on 2012-11-20
> **newb85 said:**
> Put another way, play with Ubuntu until you break it, then figure out how to fix it.  Repeat as needed.

Well, that certainly reflects my experience since installing 12.04 on a brand new Ultrabook.  So far, I haven't managed to break anything that couldn't be fixed, and I've learned a lot along the way.  :P

---

