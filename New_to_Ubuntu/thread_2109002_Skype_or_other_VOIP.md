---
title: "Skype or other VOIP"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by venkinag on 2013-01-26
I tried to install skype using the command

```
sudo apt-get install skype
```

I get the following error

[COLOR="Red"]The following packages have unmet dependencies.
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages.[/COLOR]

I have gone through various forums, followed the steps, but I ended up with the same message as above.

FYI, When I type ***uname -a*** in the terminal, I get this
[COLOR="Blue"]Linux ubuntu 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]

I need some help to install skype.

**OR**

Please can someone point me to an alternative to skype that can interop with multiple voip software including skype.

---

### Post by black veils on 2013-01-26
you just need to enable the canonical partner repositories (software channels).

in software sources there is a tab called other software, or something. find canonical partners and check the boxes.

then refresh/reload your repos, either by update manager 'check' button, or ```
sudo apt-get update 
``` in the terminal.

---

### Post by Impavidus on 2013-01-26
This has happened before: [http://ubuntuforums.org/showthread.php?t=2085901](http://ubuntuforums.org/showthread.php?t=2085901)

You could install only **skype-bin**, which should give you the program. Although I'm not sure it will properly install it (menu entry, panel icon), you will be able to start the program from the command line. Else you can install directly from the skype website (slightly harder) or wait for a few days. There must be an error in the dependencies. Skype may be dependent on a new version of skype-bin, which isn't in the repo's yet. It should be corrected in a few days.

---

### Post by gifford on 2013-01-26
I could not tell from your post what version of Ubuntu you are using, 12.10 or 12.04?

You can use synaptic package manager to fix your broken packages. If you do not already have it installed, do so and go to edit and then fix broken packages. I would then reboot.

You could then download the latest version for Ubuntu from the Skype site and then click the download and the software center will install.

---

### Post by shaunbrown1995 on 2013-01-27
If you're running 64bit Ubuntu, The following command worked for me.
sudo dpkg --add-architecture i386 && sudo apt-get update && sudo apt-get install ia32-libs

---

### Post by venkinag on 2013-01-27
Hi gifford, I am using Ubuntu 12.10.  I will try Synaptic package manager to see if it works.

---

### Post by venkinag on 2013-01-27
> **black veils said:**
> you just need to enable the canonical partner repositories (software channels).

in software sources there is a tab called other software, or something. find canonical partners and check the boxes.

then refresh/reload your repos, either by update manager 'check' button, or ```
sudo apt-get update 
``` in the terminal.

Hi, Canonical partners is already checked.  But I still faced the problem.  See attached screenshot.

---

### Post by black veils on 2013-01-27
hmm.. in the software sources, on updates tab, make sure that **recommended** is checked.

refresh/reload the repositories

then run this command in terminal ```
sudo apt-get remove skype skype-bin
```try again to install skype.

so far all i have seen from searching is someone had problems due to a repository malfunctioning, which corrected after a day or 2. the other is making sure any old skype is removed first, and of course the canonical partners selected.

Edit:
i know it is in the repositories, and this may make no difference, but its another method to try.. [http://www.tecmint.com/install-skype-4-1-in-ubuntu-xubuntu-linux-mint/](http://www.tecmint.com/install-skype-4-1-in-ubuntu-xubuntu-linux-mint/)
32-bit
```
sudo apt-get install libxss1
``````
cd /tmp
``````
wget http://www.skype.com/go/getskype-linux-ubuntu-32/skype-ubuntu-precise_4.1.0.20-1_i386.deb
``````
sudo dpkg -i skype-ubuntu*.deb
```64-bit
```
sudo apt-get install libxss1
``````
cd /tmp
``````
wget http://www.skype.com/go/getskype-linux-ubuntu-64/skype-ubuntu-precise_4.1.0.20-1_amd64.deb
``````
sudo dpkg -i skype-ubuntu*.deb
```

---

### Post by venkinag on 2013-01-29
Thank you everyone.  

I used the command ```
sudo apt-get install libxss1
```

It gave me bunch of *unmmet dependencies* errors.  At the end of the error message it suggested that I use 'apt-get -f install'.  I tried it as a sudo user.  It installed all dependencies and my skype started working!

I did not use synaptics package manager.

Special thanks to shaunbrown1995 and black veils.

---

### Post by black veils on 2013-02-13
[Deleted]

---

