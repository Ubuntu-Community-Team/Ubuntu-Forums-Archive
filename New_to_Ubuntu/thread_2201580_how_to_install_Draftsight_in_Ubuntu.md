---
title: "how to install Draftsight in Ubuntu"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by Ralph_Lam on 2014-01-25
Wierd...  I was able to download the Ubuntu version of Draftsight ( [http://www.3ds.com/products-services/draftsight/overview/](http://www.3ds.com/products-services/draftsight/overview/) ) and install it while using the Linux distro SolydK.  It opened right up and I was able to follow my nose and install it with no problem.

Now that I am using Ubuntu, I don't seem to be able to install it.....

Any ideas on how to install draftsight onto Ubuntu?

Thanks

---

### Post by squakie on 2014-01-25
Not being a person who uses CAD, I had never heard of this.  None the less I went to their site and download the first download marked Ubuntu .deb beta.  I then went to my downloads folder and clicked it to let the software center try to install it.  That ran for a short period - no error messages were shown, but it never did install it.  So, I went to the command line and used dpkg to try to install it and that failed.  I may doing something wrong when I use dpkg, but it dumped a LOT of messages about a LOT of packages not found - I assume dependencies for the package.

So, I stopped there since all I was trying to do was to see if it would install, and if so, to tell you how I did it.

So.....if you haven't already, install synaptic package manager:

sudo apt-get install synaptic

when that finishes, then:

sudo synaptic (or you can go through the menus to find it)

After it starts up, put "cad" (without the quotes) in the search string - it should show you several entries for cad.  I saw something on there for librecad or some such name, and also something called "freecad" but it is noted as in alpha.  There are probably others in that list.

Since I don't use or know anything about it, I'll leave it to someone who does know and is familiar with the CAD packages in the repositories to help you further.

---

### Post by MartyBuntu on 2014-01-25
I've only had luck installing the 32 bit version myself. It works.

---

### Post by philinux on 2014-01-25
[http://ubuntuforums.org/showthread.php?t=2179897](http://ubuntuforums.org/showthread.php?t=2179897)

See post #4.

---

### Post by Frogs Hair on 2014-01-25
I had a successful installation with 12.10 but haven' t used the program since .

---

### Post by Ralph_Lam on 2014-01-25
Well, this must be why people have more than one distro on there hard drive.  I fooled around with linux back in 2006 and bailed because of the seemingly vast differences between distros.

It HAS come a LONG way since then an I am actually thinking that one linux distro or another is in position to finally put the world on notice that they have options.

Having said that, I think that in this case it is particularly strange because Draftsight actually named it "Ubuntu Version", but it won't install on Ubuntu, and it installs perfectly and works perfectly on SolydK....  odd

---

### Post by philinux on 2014-01-25
> **Ralph_Lam said:**
> Well, this must be why people have more than one distro on there hard drive.  I fooled around with linux back in 2006 and bailed because of the seemingly vast differences between distros.

It HAS come a LONG way since then an I am actually thinking that one linux distro or another is in position to finally put the world on notice that they have options.

Having said that, I think that in this case it is particularly strange because Draftsight actually named it "Ubuntu Version", but it won't install on Ubuntu, and it installs perfectly and works perfectly on SolydK....  odd

The linux and mac versions are both Beta. That may explain it.

---

### Post by Ralph_Lam on 2014-01-25
I can just boot in SolydK and run it, so It is not the end of the world.  I was hoping that I could find one distro that would become my one-and-only and be the go-to OS for most if not all of my needs.  so far, SolydK has...

1.) been able to install and run Audacity, while running recognizes my microphone, other intput devcies with no extra steps form me me
2.) find my wireless(network) printer and print a test page
3.) mount my windows drive

BUT , does not allow the curser to keep deleting, back spacing, arrow move while keeping the button depressed.  You have to keep pushing the button to get it to keep deleting etc.

UBUNTU - noticably faster interface.

1.) installed and runs Audacity just like SolydK
2.) Finds network pritner, but can not print a test page, or any other page
3.)can not install Draftsight

It is always one thing or another with these distros.  So far, I am working between SolydK and Ubuntu, and I am kind-of wishing Ubuntu would do it all since it is blazing fast and very intuitive.

---

### Post by philinux on 2014-01-25
Did you see the link i gave in post #4

---

### Post by Gemnoc on 2014-02-02
You cannot fault Ubuntu for a large corporation (Dassault Systèmes)'s _cluelessness_ in providing a properly working debian package. Many volunteers learn to package open source software in their spare time, and they seem to do the job better than Dassault, which no doubt pays people to do it... :rolleyes: Obviously, since DraftSight is prioprietary and its sources are not available, the community cannot take matters into their hands.

They've been providing their software since 2010, and after almost 4 years it's still in Beta, and they have yet to propose a 64-bit package! Seriously? Open source projects have been doing it for freaking years.

I find this incredibly pathetic on their part.

You might find this blog post useful if your Ubuntu is 64-bit, it seems the last version brought changes in file locations: [http://linuxaideddesign.blogspot.ca/2014/01/draftsight-v1r5-is-out-with-lot-of.html](http://linuxaideddesign.blogspot.ca/2014/01/draftsight-v1r5-is-out-with-lot-of.html)

As for myself, since the last time I had to jump through hoops to get it working on Ubuntu 64-bit (which resulted in the package not being seen by the package manager), I decided to simply boycott the software. If I need to do some 2D CAD work, I make do with LibreCAD.

---

