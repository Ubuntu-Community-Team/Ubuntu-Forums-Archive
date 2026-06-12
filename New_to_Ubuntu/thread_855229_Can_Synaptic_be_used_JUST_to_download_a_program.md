---
title: "Can Synaptic be used JUST to download a program?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-07-10
Hi,
 I'm getting into program install issues on another laptop which can't as yet get online, so I'd love a way to transfer FULL programs via a flash drive. 

(See Thread 'Without ethernet or wireless in Ubuntu Studio' - I'm trying to install Network Manager)

It'd be great if I could use Synaptic JUST to download a program to my desktop, hopefully with all the dependencies included.

Can one do this with Synaptic? Many Thanks for assisting, Sorry if this is a dumb question,
Frank B.

---

### Post by roquefilipe on 2008-07-10
[http://beans.seartipy.com/2006/11/03...et-connection/](http://beans.seartipy.com/2006/11/03...et-connection/)

---

### Post by fatality_uk on 2008-07-10
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Go here and find the application you want. On the page it will also list the dependancies so you can check if you have those installed.

If the dependancies are satisfied, you can then just downlaod the *.deb from the packages page.

---

### Post by Canis familiaris on 2008-07-10
Yes you can. When you click Apply select checkbox "Download Package only" and it will not be installed.

These packages are downloaded to: /var/cache/apt/archives

Burn those packages to the CD

Then copy it back to the offline computer.

And install all those packages by:

```
sudo dpkg -i --force-depends *.deb
```

Then to recheck:
```
sudo apt-get install -f
```

---

### Post by comandrei on 2008-07-10
Or you can do this:
```

sudo apt-get clean //clears the apt-cache
sudo apt-get install you_app //(installing you app with all the needed dependencies)

```
on the computer with an internet connection.
After that you can copy on a USB flash drive or a cd the contents of /var/cache/apt/archives . You'll have there all the debs you need to run your program. Of course when you get to your computer you copy them in the same place and 
```

sudo apt-get install your_app

```.
APT checks if the packages already is downloaded (confrunts the version with it's internal database) and then installs it.

You shold also check [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for additionals dependencies.

---

### Post by Brightbelt on 2008-07-10
Many Thanks to everyone for all your help. I made a decision to go back to regular Ubuntu (Not Studio) because everything pretty much works there.

I do plan to experiment more with digital audio recording in Linux but I can install what I need in regular Ubuntu. My wireless works there right out of the box.

I see how much wisdom there is now in the 2 applications rule: "If 2 or more applications/systems don't work, you may need to try a different distro."

I did burn a CD of archived Deb downloads (including Network Manager) and installed them, but I ended up with broken packages among other things...

That may have been due to other things I had already tried to install or bits of network manager already floating around in my system.

It began to feel so complicated to solve all that mess that I threw my hands up in surrender.

Again, Many Thanks, Frank B.

---

