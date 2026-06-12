---
title: "synaptic vs deb"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Palu on 2008-05-01
[LIST=1]
[*]If I install a deb file and later realize it was in synaptic, can I somehow associate the installation so I get automatic updates and better inventory of my installed software?
[*]Also, I have (so far) installed nothing from outside synaptic because I really love Ubuntu managing updates for me and it feels fun being a purist for now. However, if I DO install a deb file, are there additional concerns besides it being a purely manual process?
[*]If I installed a second package manager would it somehow see what the other one was doing? Can other package managers access the same package library in the first place? Is there any advantage to having more than one package manager? (This question is academic in intents and probably won't be attempted.)
[/LIST]

---

### Post by dje on 2008-05-01
1. If you install a deb that is in the repos already gdebi (the graphical package installer) should tell you that a later, older or similar version package is available in a repository
2. Not that i can think of, maybe someone else has some reasons
3. I don't know, sorry

hope that helps,
dje

---

### Post by OffAxis on 2008-05-01
3. The package managers for debian systems (that function on .deb packages) are structured similarly, as in they reference the same source file, /etc/apt/sources.list, and are built on the dpkg functions.
So the different gui managers (synaptic vs. adept for instance) are just different front ends.
Any advantage? Not really. Just different layouts.

---

### Post by SunnyRabbiera on 2008-05-01
well if you find yourself using random .debs on the internet its up to you to keep them updated, thats why itss usually best to stick to the repositories.
But sometimes installing extra .debs off the net can come in handy if you know what you are doing.

---

### Post by neurostu on 2008-05-01
3. Yes.

For instance 3 package managers ship with ubuntu:
Syanptic
aptitude 
apt-get

they all work together.

---

### Post by unutbu on 2008-05-01
A word of caution regarding the mixing of package managers. The author of aptitude, Daniel Burrows, says aptitude will not remove packages installed by apt-get. (See [http://linux.derkeiler.com/Mailing-Lists/Debian/2007-11/msg00090.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2007-11/msg00090.html) and
[http://ubuntuforums.org/showthread.php?t=727077](http://ubuntuforums.org/showthread.php?t=727077)).

Therefore, it is best to use apt-get alone, or aptitude alone, but not both together.

I believe that it is okay to use apt-get and Synaptic interchangably since Synaptic is merely a gui for apt-get commands.

---

### Post by forrestcupp on 2008-05-01
2. One big thing about installing debs is that you don't necessarily know if it is trustworthy like you do with the repositories.  Also, some debs that are created for Debian are not compatible with Ubuntu, so you have to be careful.  Aside from that, debs are not automatically updated if they are not in the repos, so if possible, you are better off if you can find a 3rd party repo for the app instead of just downloading a single deb.

3. Synaptic, Adept, and apt-get are *not* 3 different package managers.  Synaptic and Adept are GUI frontends for one and the same package manager, which is APT.  If you are talking about using 2 actually different package managers, like apt & rpm, then you are asking for trouble because they won't keep track of the same dependencies.

---

### Post by Oldsoldier2003 on 2008-05-01
the whole thing about packages not being updated if they aren't in the repos is kind of pointless anyhow. The repos are locked before the release of that distribution so you are stuck with the older version of the software for the lifecycle of that ubuntu unless you compile or install binaries from another source.

The one thing that does happen though is programs in the main repos get security updates for the lifetime of the distribution. Either way its really up to the user to maintain his/her software load if they want to "keep up with the Joneses"

---

### Post by nowshining on 2008-05-01
debs can be auto-updated if the site features a url for downloading updates of which you'll have to manually add it to the sources.lst file or basically in the GUI software sources if you have that installed - default on ubuntu. :)

Yeah tho those without any url like updating Glib, pango, and adding GTK to the system will have to always be updated manually.

edit: by the way [http://ftp.acc.umu.se/pub/GNOME/sources/](http://ftp.acc.umu.se/pub/GNOME/sources/) is the url for glib, pango and gtk and many others sources of which you'll need to compile and install it.

Then just about every other package you try to compile you'll need to update the Makefile and change all /usr/lib to /usr/local/lib save and then make clean and sudo make install.

oh but don't forget to run sudo ldconfig first, yes that's a lowercase L to update the libraries and their locations.

---

### Post by forrestcupp on 2008-05-02
> **Oldsoldier2003 said:**
> the whole thing about packages not being updated if they aren't in the repos is kind of pointless anyhow. The repos are locked before the release of that distribution so you are stuck with the older version of the software for the lifecycle of that ubuntu unless you compile or install binaries from another source.
That's only for the main repos, and like you said, they *do* still give security updates, so it *is* relevant.  

But what you said doesn't apply to Backports and Proposed updates, nor does it apply to 3rd party repos.  I can install a deb of Cinelerra and it will never be updated.  But if I use the Cinelerra CV repository, it will be updated regularly.

---

