---
title: "Nikon needs Ubuntu flash upgrade"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by dave6 on 2015-06-12
Hi

I was told about Nikon Image Space aka nikonimagespace.com for the few extra things it can do for sharing photographs "one at a time or by album" and you can allow or disallow down loads etc including setting passwords for viewing different albums

I thought to myself this is great, and to get the extra 18GB free + password protection, just reg my nikon camera with the site, needed to do that via windows, library’s do come in handy:p

Done all that uploaded a few photos for testing via email, all works, until I go to log in with ubuntu I get 
[ATTACH=CONFIG]262546[/ATTACH]


Then by doing the down load, trying to install, I get

[ATTACH=CONFIG]262547[/ATTACH]

Got flash player off loaded from ubuntu and then started to re-install flash and got the following

[ATTACH=CONFIG]262557[/ATTACH]

Useless program, don't know which is the worst, Linux, Microsoft or other

Dave

---

### Post by cariboo on 2015-06-12
You could use:

```
sudo apt-get install --reinstall flashplugin-installer
```

to upgrade flash.

---

### Post by grahammechanical on 2015-06-12
Which is worse? The web site for using Adobe Flash player. Then Adobe for no longer developing a Linux version of Adobe Flash player. So, Windows and Mac machines get Adobe Flash Player 18 but Linux distributions get Adobe Flash Player 11.2. But there is goodnews. Patches to fix security flaws are still being back ported to Adobe Flash Player 11.2

[http://www.idigitaltimes.com/adobe-flash-player-update-download-install-critical-fix-prevent-viruses-malware-448852](http://www.idigitaltimes.com/adobe-flash-player-update-download-install-critical-fix-prevent-viruses-malware-448852)

It is a common practice to upgrade a package by first removing the existing package and then installing the upgrade package. I see nothing wrong with the second image. That is normal. But Software Centre not being able to access the archive is another matter entirely.

Regards.

---

### Post by kostkon on 2015-06-12
Chrome comes with the latest Flash, you could use that instead of Firefox.

---

### Post by monkeybrain20122 on 2015-06-13
Software centre is having a problem from the last screenshot, which is probably caused by server temporarily unavailable. But then your problem is not likely to be solved by installing or 'upgrading' flash from the software Centre or similar (sudo apt-get blah blah) because flash on linux is stuck at version 11.2 as graham explained.

You have two options. 1) Use Chrome, which bundles its own flash and it is up to date (version 18 now)
2) Use a wrapper to use Chrome's flash in firefox [http://www.webupd8.org/2015/04/fresh-player-plugin-024-released-with.html](http://www.webupd8.org/2015/04/fresh-player-plugin-024-released-with.html)
This normally works very well, but as of a few days ago there is a bug in version 0.3.0 and it is broken now, I would wait at least til next week if I go this route.

Edited: actually there is a third option, [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html) It is a wine based hack to use Windows' flash on Linux but it brings in more overhead and is not as smooth as the other two alternatives.

---

### Post by dave6 on 2015-06-13
I think I will go with Chrome, as I will only need it for the nikonimagespace thing, "that's one long word" 
I read in a mag recently, it is only in the computing world that you need to learn a degree worth of knowledge to use computer / tap / phone etc, then they bring out a new updated OS and you have to relearn it all again, the person that wrote the comment, compared it to a car

Dave

Oh dear, that did not work

[ATTACH=CONFIG]262567[/ATTACH]

Would it be some thing to do with this version of ubuntu ??

[ATTACH=CONFIG]262569[/ATTACH]

Dave

Got this when I used the above line from cariboo

```
daboss@daboss-desktop:~$ sudo apt-get install --reinstall flashplugin-installer
[sudo] password for daboss: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic libbabl-0.0-0
  libgegl-0.0-0 nvidia-settings-experimental-304
Use 'apt-get autoremove' to remove them.
Suggested packages:
  x-ttcidfont-conf ttf-mscorefonts-installer ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-installer
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 7,002 B of archives.
After this operation, 140 kB of additional disk space will be used.
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/multiverse flashplugin-installer amd64 11.2.202.451ubuntu0.12.04.1
  404  Not Found [IP: 91.189.91.23 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/multiverse flashplugin-installer amd64 11.2.202.451ubuntu0.12.04.1
  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.451ubuntu0.12.04.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.451ubuntu0.12.04.1_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
daboss@daboss-desktop:~$ 
```

Dave

---

### Post by R.E.A.D001 on 2015-06-13
Looks like your plugin inside of your browser may not be enabled, or may even need linked inside of Ubuntu.

---

### Post by dave6 on 2015-06-14
> **R.E.A.D001 said:**
> Looks like your plugin inside of your browser may not be enabled, or may even need linked inside of Ubuntu.

Which browser, both firefox and chrome are throwing up the same error or flash request ?

How do I, need linked inside of Ubuntu

I read the above thread "how do i install Flash? 		" wish I could do that 

Dave

No idea how I fixed it, but after a 290mb download update Chrome is now working with nikon image space

So, if I could I would mark this thread as solved

Dave

---

### Post by Vladlenin5000 on 2015-06-14
You can :p

In your first post > Thread tools.

---

### Post by kurt18947 on 2015-06-15
> **dave6 said:**
> No idea how I fixed it, but after a 290mb download update Chrome is now working with nikon image space

So, if I could I would mark this thread as solved

Dave

I'm glad you got it working. What may have happened is that your first effort appears to have installed Chrom**ium** which is Chrome without Google's proprietary bits, including pepperflash so Chromium was using Flash ver. 11.2.xxx. Perhaps Chromium would have worked if you had also installed pepperflash.  'Pepperflashplugin-nonfree' browser plugin is also found in the repositories. I keep a Chromium with pepperflash installation for such occasions. I find the need rare but it does arise as you found.  Chromium seems to be a resource hog compared to Firefox these days (that wasn't always the case). I'd guess that Nikon is not aware that flash 11.2.xxx is kept up-to-date re security patches for linux and won't permit older versions of flash to run, patched or not.

---

