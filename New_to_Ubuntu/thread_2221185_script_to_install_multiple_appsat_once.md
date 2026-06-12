---
title: "script to install multiple appsat once?"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by HL84 on 2014-05-01
Hi,

is it possible to create a script or something like that which does a series of terminal-commands at once?
For example, if I want to  install these apps

sudo apt-get install vlc browser-plugin-vlc
sudo apt-get install flashplugin-installer
sudo apt-get install inkscape
sudo apt-get install gimp
sudo apt-get install libreoffice libreoffice-l10n-de
...

How can I do this all at once or create something like a script that does this, so that I don't have to do that manually?

Thanks

---

### Post by xeonix on 2014-05-01
Simple. Bash scripting.

ex:
```

#!/bin/bash
sudo apt-get install -y vlc flashplugin-installer gimp someother_programs

```

change mode or make it executable by "chmod +x scriptname.sh"
run the script with "sudo sh scriptname.sh".

---

### Post by deadflowr on 2014-05-01
A script would work, but why not just string them all together
```
sudo apt-get install app1 app2 app3 app4 app4 and so forth
```

You don't have to run apt-get install for every package.
As long as you have a space between the package names, it will install those.

If fact, just make a quick text file and then copy/paste it into the terminal.

---

### Post by HL84 on 2014-05-01
> **xeonix said:**
> Simple. Bash scripting.

ex:
```

#!/bin/bash
sudo apt-get install -y vlc flashplugin-installer gimp someother_programs

```

change mode or make it executable by "chmod +x scriptname.sh"
run the script with "sudo sh scriptname.sh".

Sounds great. I guess I'll do it that way. This suffix "-y" is this to confirm the installations for every package which normally would ask for a yes/no, right? Or does this have a different meaning? (sorry for this maybe too obvious question - I'm really a beginner as you can see ;) )

Oh, and another question: I also have a few "http://www.xxxxxxx.com/yyyy/zzzz.deb"-files I need to install and also 1 *.sh-file. Is this also possible in a simple way?

---

### Post by vasa1 on 2014-05-01
> **HL84 said:**
> Sounds great. I guess I'll do it that way. This suffix "-y" is this to confirm the installations for every package which normally would ask for a yes/no, right? Or does this have a different meaning? (sorry for this maybe too obvious question - I'm really a beginner as you can see ;) )
From **man apt-get**:
```
       -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all
           prompts and run non-interactively. If an undesirable
           situation, such as changing a held package, trying to install
           a unauthenticated package or removing an essential package
           occurs then apt-get will abort. Configuration Item:
           APT::Get::Assume-Yes.

```
But, as far as possible, I avoid using "-y": I stay at the keyboard and respond to system prompts.

---

### Post by vasa1 on 2014-05-01
> **HL84 said:**
> ... I'm really a beginner as you can see ;) )

Oh, and another question: I also have a few "http://www.xxxxxxx.com/yyyy/zzzz.deb"-files I need to install and also 1 *.sh-file. Is this also possible in a simple way?

Are you sure you're really a beginner? Installing stuff from outside the software center?

---

### Post by HL84 on 2014-05-01
Beginner to Linux for sure. Back in the day we were doing things with MsDos, so doing a little bit of terminal-commands is at least something I'm capable of. And installing things that way is easier than using the software center for me. ;)

---

### Post by ian-weisser on 2014-05-01
> **HL84 said:**
>  I also have a few "http://www.xxxxxxx.com/yyyy/zzzz.deb"-files I need to install and also 1 *.sh-file. Is this also possible in a simple way?

First you download it.
Then you install it.
The proper place to keep deb packages is /var/cache/apt/archives/zzzz.deb
```
sudo wget --directory-prefix=/var/cache/apt/archives/ http://www.xxxxxxx.com/yyyy/zzzz.deb    # download to /var/cache/apt/archives/zzzz.deb
sudo dpkg --install /var/cache/apt/archives/zzzz.deb                                          # install
```

**Beware**: deb packages from the wild are not supported software, are not tested with Ubuntu, might break your Ubuntu system, might introduce malware, and/or might break you Ubuntu system's ability to install regular updates...including security updates. ALWAYS try the Ubuntu Repositories first.

---

### Post by HL84 on 2014-05-01
Actually I'm just planning to install Chrome, BlueJ and Dropbox as deb-files. Too bad they cannot be installed otherwise on lubuntu afaik. (the sh-file is yEd)

---

### Post by ian-weisser on 2014-05-01
It's great that you install only packages you trust.
I do too.

Nevertheless, they are not supported software, and Ubuntu does not test them nor provide security updates for them. Their developer is responsible for those.
It's a different ecosystem than Windows, and it works a different way. We would be remiss to a new user if we didn't tell you.

---

### Post by Vaphell on 2014-05-01
look for PPAs (3rd party repos) first. Once you add them to your approved repos, the installation procedure is the same. Chrome and Dropbox seem to have them, not sure about BlueJ

[http://www.ubuntuupdates.org/ppa/google_chrome](http://www.ubuntuupdates.org/ppa/google_chrome)
[http://www.ubuntuupdates.org/ppa/dropbox](http://www.ubuntuupdates.org/ppa/dropbox)

always check for software in this order: official repos > PPAs > .deb files > source, weird installers

---

