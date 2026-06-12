---
title: "Questions Regarding Desktop Environments, Window Managers, etc."
date: 2012-07-21
forum: New to Ubuntu
---

### Post by LLAAC on 2012-07-21
Hi,

I've been using Ubuntu for quite a while. Not an absolute beginner, but I know next to nothing about removing and replacing desktop environments or the difference between them and window managers. I know a desktop environment contains a window manager, but I don't know much else.

I'd also like some information on the related toolkits because I'm utterly confused.

My situation is this: I've got Gnome-Shell installed. I've tried various other desktop environments, some of which I've liked. I am absolutely sick of GNOME at the moment, although I've gotten so used to it that I'm stuck in that state of "comfortable but not satisfied". I know how to install other DEs and log in to their sessions - that's simple enough -  but I don't how to completely replace what I'm using.

I know one of the common beginner questions is "desktop environment versus window manager" and I kind of grasp the answer, though not completely. I also know that there are a ton of threads on that, so I don't need an absolute explanation here, although I think it'll be a part of the answers because they're all so inter-related. I think my issue is not with the difference between the two, but how to minimize use of a DE and use an alternative window manager without ruining my desktop.

Say I wanted to install a WM like Fluxbox (just an example), and I wanted to remove everything GNOME and Unity-related. What would I need to keep in order to have a working desktop?

This is where my toolkit question comes into use. If I were to use a window manager and remove GNOME or KDE, I'm guessing I'd need to keep GTK+ or Qt (or any other toolkit) in order to have a working desktop. (My understanding of this is also minimal, so I could be wrong about this as well.)

I don't know how to go about removing what I want to remove without breaking my desktop. I can, yeah, have several sessions. But I don't want my system bloated with DEs and their packaged software and different file mangers that I'm never going to use. 

I don't want or need most of the applications packaged with, say, GNOME or KDE. I can easily install the few I need from the Software Center or terminal. But I don't want to just remove all packages at once (purge), because I know that'd result in my losing all related software instead of just the extra bloat I don't want, not to mention serious problems regarding dependencies.

I can, yes, just install one of the Ubuntu variations, but I'm having serious problems booting anything from a live CD or USB (and I mean anything - Fedora, Ubuntu, several others). This is a separate problem, and I'm looking into a solution for that elsewhere. In any case, I feel it'd be a good learning experience to do this manually without having to resort to continuous fresh installs to change the things I want to change.

Maybe this is all better suited for the Desktop Environments section, so I wouldn't mind having this moved if needs be.

I know this post is kind of going about in several different directions, so I think I'll try to sum up my questions as:

1) How much (and what) do I need to remove in order to replace one DE with another?

2) If I wanted to use a window manager instead of a fullblown desktop environment, how do I go about removing the bloat associated with the DE without breaking my desktop?

Thanks.

---

### Post by sudodus on 2012-07-21
> **LLAAC said:**
> ...

I know this post is kind of going about in several different directions, so I think I'll try to sum up my questions as:

1) How much (and what) do I need to remove in order to replace one DE with another?

2) If I wanted to use a window manager instead of a fullblown desktop environment, how do I go about removing the bloat associated with the DE without breaking my desktop?

Thanks.

1. Look at this link

[[COLOR="Red"]_http://www.psychocats.net/ubuntu/_[/COLOR]]("http://www.psychocats.net/ubuntu/")

at [COLOR="Red"]**Playing Around**[/COLOR]

2. I'll leave this one to be answered by people with more experience about window managers.

---

### Post by LLAAC on 2012-07-21
> **sudodus said:**
> 1. Look at this link

[[COLOR="Red"]_http://www.psychocats.net/ubuntu/_[/COLOR]]("http://www.psychocats.net/ubuntu/")

at [COLOR="Red"]**Playing Around**[/COLOR]

2. I'll leave this one to be answered by people with more experience about window managers.
Thank you. 

That was very helpful, actually.

What about DEs not listed there, though? Lesser known ones which don't have an Ubuntu derivative.

I haven't found any which I like that aren't official derivatives (save for Enlightenment which Bodhi uses - and I know Bodhi is based on Ubuntu), but I'm just asking out of interest.

In any case, that was quite helpful. Thanks again. I'll also wait to see which answers come out for the second question.

---

### Post by ajgreeny on 2012-07-21
Bear in mind, that if you for example install fluxbox and then use psychocat's command to remove gnome, you will end up with a rather useless system as there will be nothing in the way of applications left to use.

That explains in a practical manner, the difference between a window manager like fluxbox, and a DE.  Fluxbox itself has no really usable applications as dependencies, but only the various libraries and services needed for a graphical system to run, ie, there is no text editor, no word processor., no web-browser etc etc, just the means to run all of them if you choose.  A DE such as gnome, has all of those applications as dependencies and they are a basic part of the whole "DE package" of gnome.

I hope that makes sense to you, and does not confuse you even more.

Try it out by installing openbox, a good example which I have used, but do not yet uninstall any part of gnome.  Now log out and then login again choosing openbox at the login screen.  You will now have available all the applications you are used to but gnome itself will not be running.

---

### Post by Peripheral Visionary on 2012-07-21
It doesn't include some of the newer DEs like Cinnamon and Unity, but [this]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893") little post is the best "layman's language," novice-friendly explanation of the difference between a window manager and a desktop environment I've ever read. It also has a good description of the four most popular Linux desktops, again written in novice-friendly "ordinary users' language."

---

### Post by kestrel1 on 2012-07-21
I have just switched to Cinnamon & have found that applications open in a slit second.
With Unity it could take a fair bit longer.
It can be a trial to install, unless you know what to do.
I will put a how to together.

Here you go:
How to install Cinnamon on Ubuntu 12.04

First you need the repository, so enter the following at a command prompt (Terminal window):

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
```

Then you need to update your sources:

 ```
sudo apt-get update
```

Once this has finished you can install Cinnamon:

```
sudo apt-get install cinnamon cinnamon-session cinnamon-settings
```

Once installed you just need to logoff & select Cinnamon from the list of DE's

---

### Post by malspa on 2012-07-21
What I like to do is add a WM and not worry about deleting any of the stuff from the default DE. Hard drive space is not an issue, and even if I have to run apps native to the default DE, they still run much snappier if I'm logged into the WM.

I noticed this a long time ago when I had Kubuntu 6.06 on an old notebook. KDE was very sluggish on that notebook, so I added Fluxbox and used that instead, and that took care of the problem.

So, I do this all time now; for example, I have Openbox added to Ubuntu 12.04, AwesomeWM added to Debian Squeeze (GNOME), E17 added to PCLOS (KDE), and so forth.

Not sure if that would work for you, but that's my approach.

---

### Post by LLAAC on 2012-07-22
Thanks a lot for the replies.

I certainly have the answers I needed.

I have actually had Cinnamon installed for a while, but I don't think I gave it as much attention as I probably should have. I do prefer it over Gnome Shell, so I might just stick with that. 

In the meantime, I'll also try a few window managers on top of GNOME like suggested.

Again, thanks very much for the replies. 

I'll mark this as solved.

---

