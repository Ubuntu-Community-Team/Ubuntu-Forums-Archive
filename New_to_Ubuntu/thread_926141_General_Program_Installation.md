---
title: "General Program Installation"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Infantry001 on 2008-09-21
Well, I just successfully set up a dual-boot system (yay!) with XP and Ubuntu. Now, I was wondering, generally, how do you install programs onto Ubuntu?

And specifically, I want to install [Geany]("http://www.geany.org") :p

---

### Post by Mornedhel on 2008-09-21
In a terminal :

sudo apt-get install geany

Friendlier :

System > Administration > Synaptic Package Manager, mark Geany, apply.

Read up on packages and repositories. There's probably something in the stickies.

---

### Post by lisati on 2008-09-21
The easiest way while you're finding your way around is through the "Applications"->"Add/Remove Software" menu. 
Another place to look is "Synaptic" (On my system it's on the "System"->"Administration"->"Synaptic Package Manager" menu)
For software you download, it's probably easiest if you use ".deb" packages.

EDIT: I almost forgot: from the terminal, there's the "apt-get install" and "aptitude install" methods

---

### Post by Mornedhel on 2008-09-21
This thread :

[http://ubuntuforums.org/showthread.php?t=781352](http://ubuntuforums.org/showthread.php?t=781352)

is linked to in the "New to Ubuntu ?" sticky. It's rather lengthy but seems to cover most of the deal.

---

### Post by Infantry001 on 2008-09-21
Oh, so most programs are downloadable via the Synaptic Package Manager? Cool. I always thought I had to download the source, compile it, and go through a whole mess of things :/ haha

Thanks very much!

---

### Post by Mornedhel on 2008-09-21
> **Infantry001 said:**
> I always thought I had to download the source, compile it, and go through a whole mess of things :/ haha

You know, I *really* wish this myth would go away. It hasn't been true for years now. I don't blame you or anything, but this is really persistent...

Not to say you will never have to download the source and compile it.

General installation actually goes like this :

1. Check in Synaptic / other package manager if package is already in the repositories. If so, install. End. Else :
2. Check if official website for software offers a direct download of a .deb package, or alternatively, a URL and key to a custom repository. If so, install. End. Else :
3. Check if getdeb.net has a package for your version of Ubuntu. If so, install. End. Else :
4. Get source. Read README and/or INSTALL file. Follow instructions, configure-make-sudo make install or whatever the readme suggests. Constatation A : you don't have all the required libraries. Attempt to install libraries, starting again at 1., until A. is not true anymore. Redo 4.

---

