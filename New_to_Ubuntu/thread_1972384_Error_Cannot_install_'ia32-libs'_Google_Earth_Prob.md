---
title: "Error: Cannot install 'ia32-libs' Google Earth Prob"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-05-03
Had to uninstall GE last night and now would like to re-install. When I use Gdebi to open the .deb file for GE, I get the error in the title.

I guess I could try to install ia32-libs via the terminal, but I don't understand why it can't be installed as part of the GE process. I thought this is what GDebi did.

Thanks

---

### Post by Curtis6767 on 2012-05-03
I've been searching for a way to install this package but getting nowhere.

What I need to do in install this package in a way that goes out and finds and then installs all its dependencies. 

When I just do sudo apt-get install ia32-libs, I immediately get an error saying there are unmet dependencies and says that it depends on ia32-libs-multiarch.

If I try to install that multiarch pack, then I get another error saying it depends on another pack, etc. And this just keeps going and none of these libs packs are installed.

in my lib32 file I have a couple of packs that say they're broken. "libBrokenLocale-2.15.so"

Any ideas?

Edited: 

Now I've found a .deb file: ia32-libs_20090808ubuntu13_amd64.deb

I think this must be from 2009 and could be outdated. It is 57.5MB in size.

Any ideas on what might happen if I should download and install this deb file? I don't want to mess things up more than they already are.

Edit II:

I've gone into Ubuntu Packages at packages.ubuntu.com/precise/libs and the #'s on the files there matches the #'s on the deb file above. 

Still like to get some input before I install that deb file.

Thanks

---

### Post by Curtis6767 on 2012-05-04
I find it interesting that no one has any idea about how to fix this issue. 

The inability to install ia32-libs is causing continued problems including a wrecked Software Center and Package Manager. The package manager offered up a package that was needed in the early hours of this problem, but the package could not be installed and when I tried to install it, the package manager went postal, shut down numerous times, supposedly sent bug reports here and there. I've quited this beast by going in and checking and unchecking various software sources.

ia32-libs is available in the Software Center, but I can't install it. I have the 64bit  .deb file for Google Earth but can't install that because it gets stopped in the process with an error about not being able to install ia32-libs.

Which came first, the chicken or the egg? One big circle of errors. 

And GE is just the app I'm having trouble with now. If I were to try and  install other apps from the Software Center I think there's a good  chance I'll run into the same issue. For whatever reason, the inability  to install ia32-libs has blocked the pipeline.

In a community of 20mil users there has to be someone out there who knows a work-around for this issue.

Thanks

---

### Post by oldos2er on 2012-05-04
Which version of Ubuntu are you using?

Edit: Nevermind, I see you mentioned Precise in your first post. Make sure you have the universe repository enabled, run **sudo apt-get update**, then try installing GE with gdebi again.

---

### Post by Curtis6767 on 2012-05-04
> **oldos2er said:**
> Which version of Ubuntu are you using?

Edit: Nevermind, I see you mentioned Precise in your first post. Make sure you have the universe repository enabled, run **sudo apt-get update**, then try installing GE with gdebi again.

Thanks for your reply. I do have the universe repo enabled and I have tried sudo-apt-get-update numerous times without success.

I have done a search on ways to force an install and came across QApt, which is available in the Software Center. I've downloaded it.

I have the .deb file for ia32-libs and when I right-click it, I have the option to install via QApt. I'm reluctant to do this because if it fails my system will be borked and I'll be looking at a fresh install.

Here is the link with some info about QApt: [https://jontheechidna.wordpress.com/2010/07/05/introducing-qapt-and-the-muon-package-manager/](https://jontheechidna.wordpress.com/2010/07/05/introducing-qapt-and-the-muon-package-manager/)

Any opinion on QApt?

Thanks

---

### Post by oldos2er on 2012-05-04
Never heard of QApt. I don't see how a different package manager front-end will help, frankly.

Regarding > The package manager offered up a package that was needed in the early hours of this problem, but the package could not be installed and when I tried to install it, the package manager went postal which package could not be installed? Can you run the following commands in a terminal and post all their output here? ```
sudo apt-get update

sudo apt-get install -f
```

---

### Post by Curtis6767 on 2012-05-04
> **oldos2er said:**
> Never heard of QApt. I don't see how a different package manager front-end will help, frankly.

Regarding  which package could not be installed? Can you run the following commands in a terminal and post all their output here? ```
sudo apt-get update

sudo apt-get install -f
```

Thanks for your reply. Yes I've done all of the above until I'm blue in the face and no change.

When Ubuntu would not recognize my printer (it did the other day), I just gave up. I've done a fresh install, and I'm not too happy about it. 

Thanks

---

### Post by oldos2er on 2012-05-05
Sorry you had problems. Hopefully your fresh install will behave better.

---

### Post by baijea on 2012-09-18
Hi,

the solution to a similar problem I had is listed in [http://ubuntuforums.org/showpost.php?p=12246372&postcount=7](http://ubuntuforums.org/showpost.php?p=12246372&postcount=7).

Hope this helps!

---

