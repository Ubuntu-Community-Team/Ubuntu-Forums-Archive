---
title: "problem with tar.gz file"
date: 2018-04-11
forum: New to Ubuntu
---

### Post by newblank25 on 2018-04-11
I'm using ubuntu 18.04 beta. I downloaded gnome-hearts_.03.org.tar.gz to download folder. i thought that just using extracting in download progam would open program. It seems I'm wrong. Can some please help with proper sequence to open this and run it?thx

---

### Post by SeijiSensei on 2018-04-11
To extract the archive

```
tar xzvf gnome-hearts_.03.org.tar.gz
```

The "x" switch invokes gzip. Beyond that you need to read the documentation to know what to do next.

---

### Post by newblank25 on 2018-04-11
tried that in terminal and got this.
tar xzvf gnome-hearts_.03.org.tar.gztar (child): gnome-hearts_.03.org.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
what happenned?

---

### Post by Dennis N on 2018-04-11
If it's in the Downloads folder, you have to cd in the terminal to that folder before running the command (or else include the path to the file with the file name).

---

### Post by logix2 on 2018-04-12
You probably downloaded the source, which needs to be compiled. That's pretty complicated, especially since it depends on each program and its dependencies. Until you're more accustomed to Linux/Ubuntu, I would suggest sticking to the applications available in the official repositories (installable through Ubuntu Software) or downloading deb files.

---

### Post by monkeybrain20122 on 2018-04-12
If you are new you shouldn't be using 18.04, which is a beta for testers to file bug reports,  you should get 16.04.4

The tar.gz file is just an archive exactly like a zip file, it is not an installer. You open the archive by right clicking it and extract here, the tar xzvf gibberish does exxactly the same thing with command lines, to extract the archive and that's all,--so you can skip it and just do the right click,-- it won't start any program or install any just like you won't if you unzip a zip file unless it is a virus.

The archive can contain anything: data, a compiled binary, or source code. If it is a compiled binary there is a file you can run by right clicking it or running in terminal (if you make it executable), if it is source codes then you'll have to compile it to get the binary, it is usually not simple for beginners.

gnome-hearts appears to be in the repository, just install it with the software centre.

---

### Post by PaulW2U on 2018-04-12
> **monkeybrain20122 said:**
> gnome-hearts appears to be in the repository, just install it with the software centre.
But it doesn't appear to be in 18.04 - [https://launchpad.net/ubuntu/+source/gnome-hearts](https://launchpad.net/ubuntu/+source/gnome-hearts) - which is probably why newblank25 downloaded the source from elsewhere. gnome-hearts also seems to be missing from both Debian testing and unstable.

---

### Post by newblank25 on 2018-04-12
I was using ubuntu 16.04 but wanted to try the beta version of ubuntu 18.04 . My gnome- hearts wasn't installed with upgrade. yes that is why I downloaded the source. I found a window version which wine can run. it is ok but i liked gnome version better. Will it be available when ubuntu 18.04 LTS? Thx for help

---

### Post by PaulW2U on 2018-04-12
> **newblank25 said:**
> Will it be available when ubuntu 18.04 LTS? Thx for help
No, the fact that gnome-hearts is also not in Debian unstable or testing (on which Ubuntu is based) means that for some reason it has been removed. If it ever gets added back into Debian then there's a chance it will be back in Ubuntu again. Was this an official GNOME game? If so then it may have been dropped by GNOME.

I'm glad that you found an alternative that works in Wine.

---

### Post by Yellow Pasque on 2018-04-14
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=887946](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=887946)

---

### Post by newblank25 on 2018-04-14
thx for info can admin close this discussion

---

### Post by Yellow Pasque on 2018-04-14
You can mark the thread SOLVED (thread tools menu above first post) if you are satisfied with the answer.
Actually, I think you may be able to get away with using the gnome-hearts .deb from Ubuntu 17.10. Debian intends to remove some of the needed dependencies, but they haven't done it yet (because their release cycles are a lot longer) and those packages probably got cloned into Ubuntu 18.04.

It's not ideal to mix packages from different releases, but looking at the dependencies for gnome-hearts, I'd guess it's a very low risk of causing dependency issues down the road. It's your system and your call though.

---

### Post by SeijiSensei on 2018-04-14
> It's not ideal to mix packages from different releases, but looking at the dependencies for gnome-hearts, I'd guess it's a very low risk of causing dependency issues down the road. It's your system and your call though.

 I had to do just that the other day for the pdftk package which doesn't exist yet for 18.04 either. Had to include a couple of other packages for dependencies, but it was pretty clear from the apt errors what those packages were.

---

### Post by iscollin on 2018-04-14
Yeah see if you can get it in .deb file  that would be much easier than compiling

---

