---
title: "Does Ubuntu mini work right out of the box?"
date: 2014-01-11
forum: New to Ubuntu
---

### Post by Punchy71 on 2014-01-11
Greetings,
   I am a considering switching to Ubuntu from Linux Mint. I was browsing elsewhere on the forums and noticed someone made a post about an Ubuntu "Mini" or "lightweight" version of Ubuntu and it piqued my interest. I have tried Ubuntu in the past and liked it, but found it a little heavier than I usually like in an Operating System. It just seems like too much plus the kitchen sink thrown in for good measure. I'm one who definitely thinks Ubuntu needs to have some fat trimmed, stream-lined and simplified...

 I think the post mentioned that it was a "you-build-it-yourself" spin of Ubuntu, which, to me, usually means you have to muck around to get it to work in the first place. Then you have to manually configure everything to get it running right rather than a "everything-works-right-out-of-the-box" like regular Ubuntu is. 

My question is, does anybody have experience with this "mini" version and if so, how close is it to an "everything-works-right-out-of-the-box" distro?

Thanks

---

### Post by deadflowr on 2014-01-11
Basically a mini install is a way to customize your system, beyond the core.
It's dependent on a working network connection, so if you can do a mini install, you know right off the bat that networking works.
What it does is installs the base system of Ubuntu, then you choose what to install on top.
The package installation is pretty straight forward, you can install the various desktop meta-packages and other basic packages, or manually select the various packages you want.
The trick though is remembering to select the packages with the spacebar. It is easy to not select anything by accident and reboot later into a console(terminal-like session), because no xorg packages were installed.
Chances are, if you want  light system, then you'd manually select the packages you want.
I would suspect most who install this way, would go near barebones, with only a window manager, a file manager, a terminal, a text editor, and a browser. Optionally, a package manager, like synaptic, for further system building later on.
You could go even lighter.
But if you install the packages needed correctly, rebooting into a working system will be of no trouble.

---

### Post by buzzingrobot on 2014-01-12
The mini.iso is an alternative installation method, not a so-called lightweight version of Ubuntu. 

The size of the mini.iso image is about 30 megs, which is approx. 1/30th the size of the standard installation image. It contains only enough to boot itself and establish a network connection.  The other components -- both those needed by the installer and those the user chooses to install -- are downloaded. 

During a mini.iso install, the user is asked to choose from a range of options to decide what will be installed.  These range from a full installation of a Ubuntu/Kubuntu/Lubuntu desktop to little more than a barebones command line system.

In fact, if the user chooses none of those options, the system will reboot to a command line, leaving it to the user to install any other components.

So, yes, unless you select one of the full desktop options during the installation, you will need to "muck about" with things to create a usable desktop system.

I've used this approach a number of times, building, for example, a Mate or a Cinnamon desktop. Post-install tweaking is necessary to polish things, and, often, to ensure things like sound, wifi and suspend work correctly.

This is a bit of a contrarian opinion, but I find so-called lightweight installations to generally not deliver all that much improvement, unless someone is working with severe hardware limitations.  The best way is to find out for yourself.

---

### Post by sudodus on 2014-01-12
I agree with the prevous replies, and want to add, that I think the leanest 'complete desktop package' of the mini iso is ***Lubuntu Core***. If you want something leaner, you need to pick the packages yourself and tweak it to work properly.

---

