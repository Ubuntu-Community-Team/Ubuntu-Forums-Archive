---
title: "Can't install or uninstall package."
date: 2012-05-02
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-05-02
I tried to down load LMMS through a repository but that failed because of a conflict with a package called libjack( see snapshot). I had to abort that download.

I then went ahead and downloaded through the software center. This seemed to work but now I have the red circle with white line through it. 

The error reads: "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: Error: Broken Count > 0. This usually means that your installed packages have unmet dependencies."

I've also tried apt-get -f install as well as other remove-type commands but each time I try anything I'm met with that libjack error.

I also have libjack in the update manager. I've removed the check mark beside its description because when I did try to install it, it just wouldn't install.

Right now I'm on an endless loop of trying to uninstall libjack and/or LMMS.

Any ideas?

---

### Post by Immolatus on 2012-05-02
You might actually be having a problem with dpkg. Aptitude implements dpkg but dpkg puts together an installation. Here is a ref for you:

 [http://www.cyberciti.biz/ref/apt-dpkg-ref.html](http://www.cyberciti.biz/ref/apt-dpkg-ref.html)

---

### Post by Curtis6767 on 2012-05-02
Thanks, I'm running through some of those codes but I keep getting errors. First, I can't install libjack, which is what I think is causing problems, nor can I uninstall it because it's not installed. 

It has messed up the software center and package manager. I can locate the file, actually there are three, which may be the reason for this conflict,  in usr/var/cache/apt/archives.

These are all .deb packages.

I don't know where these files came from but I'm assuming they're associated with LMMS and the failed repos download of that. Because this has screwed up the Software Center I cannot remove LMMS through there. I've tried to remove LMMS via the terminal, but that fails and I get the libjack error.

Edit:

I'm not sure what I did that solved this problem because I did so many things more than once and at different time. The package manager was broken, the software center was broken, and I could not remove LMMS. Finally, on a prompt from the package manager warning me of a Partial Upgrade and then failure, the pop up said try sudo apt-get install -f, which I had already done numerous times, but for some reason this time it worked.

Thanks.

---

### Post by Immolatus on 2012-05-02
Hm.....nargles? Glad it worked out. Sounds like it was a combo of things.:guitar:

---

