---
title: "[SOLVED] How to get code::Blocks installed."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by DOS4dinner on 2008-07-03
Okay, I downloaded the Ubuntu version of code::Blocks. How on earth do you install it? I tried entering sudo dpkg -i *.deb, and looked like it installed, but when I tried to run it it started and then crashed itself out. Synaptic said I had a bad file, which I removed (along with the other code::blocks files).

---

### Post by ChameleonDave on 2008-07-03
> **DOS4dinner said:**
> Okay, I downloaded the Ubuntu version of code::Blocks. How on earth do you install it? I tried entering sudo dpkg -i *.deb, and looked like it installed, but when I tried to run it it started and then crashed itself out. Synaptic said I had a bad file, which I removed (along with the other code::blocks files).

I've just downloaded it and installed it in order to see if I could help you, and it works fine for me.

Are you sure all the dependencies installed correctly?

Try running "*sudo apt-get install -f*".

---

### Post by DOS4dinner on 2008-07-03
> **ChameleonDave said:**
> I've just downloaded it and installed it in order to see if I could help you, and it works fine for me.

Are you sure all the dependencies installed correctly?

Try running "*sudo apt-get install -f*".

Complete n00b here, but how do you use that code to install the program?

also, is there a way to check if my dependencies are installed right?

---

### Post by ChameleonDave on 2008-07-04
> **DOS4dinner said:**
> Complete n00b here, but how do you use that code to install the program?

also, is there a way to check if my dependencies are installed right?

Open up a command-line terminal (e.g. GNOME Terminal, Konsole, XTerm...).

Type or paste in the command I gave before.  It checks the system for half-installed software and missing dependencies.

---

### Post by DOS4dinner on 2008-07-04
Done. It does not look like there were any errors or failures. Should I try reinstalling it? Oh, and how did you install it (assuming you are using ubuntu 8.04)?

---

### Post by ChameleonDave on 2008-07-04
> **DOS4dinner said:**
> Done. It does not look like there were any errors or failures. Should I try reinstalling it? Oh, and how did you install it (assuming you are using ubuntu 8.04)?

I used gdebi-kde.  If you use GNOME, there is gdebi-gtk.

I used it on the dependencies first (the tarball from the website provides seven DEBs) and then on the main package.  gdebi installed some extra dependencies for me.  I ran "sudo apt-get install -f" afterwards just in case.

---

### Post by Canis familiaris on 2008-07-04
Here is a good HOWTO for installing Code::blocks in hardy:

[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

---

### Post by Canis familiaris on 2008-07-04
Wrong Post

---

### Post by ChameleonDave on 2008-07-04
> **Anurag_panda said:**
> Wrong Post

What?

Anyway, DOS4dinner, remove the programs and try again (either with the same DEBs, or by using a repository, as Panda suggested).

```

sudo apt-get purge codeblocks_8.02-0ubuntu1.deb.tar.gz  codeblocks_8.02-0ubuntu1_i386.deb  codeblocks-contrib_8.02-0ubuntu1_i386.deb
codeblocks-dbg_8.02-0ubuntu1_i386.deb  codeblocks-dev_8.02-0ubuntu1_i386.deb
libcodeblocks0_8.02-0ubuntu1_i386.deb  libwxsmithlib0_8.02-0ubuntu1_i386.deb  libwxsmithlib0-dev_8.02-0ubuntu1_i386.deb

```

---

### Post by DOS4dinner on 2008-07-04
> **ChameleonDave said:**
> I used gdebi-kde.  If you use GNOME, there is gdebi-gtk.

I used it on the dependencies first (the tarball from the website provides seven DEBs) and then on the main package.  gdebi installed some extra dependencies for me.  I ran "sudo apt-get install -f" afterwards just in case.

Where might I find this gdebi-gtk? (I assume Ubuntu 8 uses GNOME)

---

### Post by DOS4dinner on 2008-07-04
> **ChameleonDave said:**
> What?

Anyway, DOS4dinner, remove the program and try again.

```

sudo apt-get purge codeblocks_8.02-0ubuntu1.deb.tar.gz  codeblocks_8.02-0ubuntu1_i386.deb  codeblocks-contrib_8.02-0ubuntu1_i386.deb
codeblocks-dbg_8.02-0ubuntu1_i386.deb  codeblocks-dev_8.02-0ubuntu1_i386.deb
libcodeblocks0_8.02-0ubuntu1_i386.deb  libwxsmithlib0_8.02-0ubuntu1_i386.deb  libwxsmithlib0-dev_8.02-0ubuntu1_i386.deb

```

Do I just throw that code into the terminal to install code::blocks? Sorry for my n00bness.Also, is that just one massive line or several lines?

---

### Post by ChameleonDave on 2008-07-04
> **DOS4dinner said:**
> Where might I find this gdebi-gtk? (I assume Ubuntu 8 uses GNOME)

I believe it is in the standard repositories (I've added so many extra ones that I am no longer sure what software comes from where!).

Therefore, you can either look for it in Synaptic, or enter the following at the command line:

```
sudo apt-get install gdebi
```

---

### Post by ChameleonDave on 2008-07-04
> **DOS4dinner said:**
> Do I just throw that code into the terminal to install code::blocks? Sorry for my n00bness.Also, is that just one massive line or several lines?

That is one massive line to totally remove ("purge") all the packages you tried to install before.

To reinstall it all, you might want to try Panda's link.  It seems to work well.

---

### Post by DOS4dinner on 2008-07-04
Okay. All the code::Blocks stuff is purged. Now, how do I use gdebi-gtk?

---

### Post by ChameleonDave on 2008-07-04
> **DOS4dinner said:**
> Okay. All the code::Blocks stuff is purged. Now, how do I use gdebi-gtk?

There are various ways you can install a package that you have downloaded.

```
sudo dpkg -i **PACKAGENAME.deb**
```

That's the most basic way.

```
sudo gdebi **PACKAGENAME.deb**
```

That will give a bit more info and handle dependencies nicely.

```
gdebi-gtk **PACKAGENAME.deb**
```

That will open up a graphical interface to install the package and handle dependencies.  It will ask for your password when it gets to the stage where it needs it.

You can also go to the directory containing the DEB package (using Nautilus, Dolphin, or whatever your system uses for browsing files) and simply click on it to run gdebi-gtk.  No command-line required.

---

### Post by DOS4dinner on 2008-07-04
> **ChameleonDave said:**
> There are various ways you can install a package that you have downloaded.

```
sudo dpkg -i **PACKAGENAME.deb**
```

That's the most basic way.

```
sudo gdebi **PACKAGENAME.deb**
```

That will give a bit more info and handle dependencies nicely.

```
gdebi-gtk **PACKAGENAME.deb**
```

That will open up a graphical interface to install the package and handle dependencies.  It will ask for your password when it gets to the stage where it needs it.

What order should I install the 7 .debs in?

---

### Post by Canis familiaris on 2008-07-04
If all those 7 debs are the only debs in that folder and in the same folder, you could install them all by:

```
sudo dpkg -i *.deb
```

PS. Why dont you install code::blocks thorugh the repos. Codeblocks is still is in deveopment phase and would be needed to be updated regularly. And repos would make that job much easier.

---

### Post by DOS4dinner on 2008-07-04
> **Anurag_panda said:**
> If all those 7 debs are the only debs in that folder and in the same folder, you could install them all by:

```
sudo dpkg -i *.deb
```

PS. Why dont you install code::blocks thorugh the repos. Codeblocks is still is in deveopment phase and would be needed to be updated regularly. And repos would make that job much easier.

I already tried that code. It did not work for some reason. Some of the parts installed but one of them did not. Also, I assume the repository is the synaptic list of programs, right? Well, I could not find code::Blocks on there. Otherwise, I just would have done that in the first place.

---

### Post by Canis familiaris on 2008-07-04
> **DOS4dinner said:**
> I already tried that code. It did not work for some reason. Some of the parts installed but one of them did not. Also, I assume the repository is the synaptic list of programs, right? Well, I could not find code::Blocks on there. Otherwise, I just would have done that in the first place.
This means that these DEBS will not work anyway. And that old problem will spurt again. Correct me if I am wrong.

Did you try the link which I gave before. I give it again because it worked very well for me.

[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

---

### Post by DOS4dinner on 2008-07-04
SOLVED! I thank both of you for helping out. It turns out I just needed to install them in a specific order. First, you install the lib. After that is done, you can install the main code::blocks one and it runs perfectly. Thanks!

---

### Post by ChameleonDave on 2008-07-04
> **DOS4dinner said:**
> I already tried that code. It did not work for some reason. Some of the parts installed but one of them did not. Also, I assume the repository is the synaptic list of programs, right? Well, I could not find code::Blocks on there. Otherwise, I just would have done that in the first place.
Firstly, the package name for code::Blocks is "codeblocks". (Package names are simply, with fancy branding removed.)

Once you install the program, you will indeed see "codeblocks" in Synaptic.

"Repository" doesn't exactly mean the Synaptic list, but kind of.  The repositories are websites which maintain archives of the latest versions of all the software you might need.  You access these repositories with a package manager, such as Synaptic, Aptitude, KPackage, or simply apt-get on the command line.

The list of repos (that's slang for software repositories) is located at "/etc/apt/source.list".  You can add extra repos to that file.  I've added tons of them.

What you see in Synaptic is all the packages which are available in the repos and/or installed on your system.

> **DOS4dinner said:**
> SOLVED! I thank both of you for helping out. It turns out I just needed to install them in a specific order. First, you install the lib. After that is done, you can install the main code::blocks one and it runs perfectly. Thanks!

Another way to do it is to install them in any order you like, but to force the system to ignore any dependency problems.

```
sudo dpkg -i --force-depends *.deb
```

That way, if package A.deb requires B.deb, it doesn't matter if you install A.deb before B.deb.

After forcing things in this manner, you should always run the following command to make sure than nothing is broken:

```
sudo apt-get install -f
```

---

