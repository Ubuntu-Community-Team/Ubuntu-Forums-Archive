---
title: "Installing and uninstalling"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by testosteroar on 2013-03-01
I have ubuntu 12.10 and I dont know how to find the stuff I download so I can uninstall them. Example: I tried installing skype for ubuntu which didnt work. Also if anyone knows hoe to get skype working for 12.10 I would love to know thank you.

---

### Post by Princess Bernice on 2013-03-01
Here are the steps for finding programs that you want to uninstall:

On the menu bar on the top, click on these: System > Administration > Synaptic Package Manager

Synaptic Package Manager will open up; look for the box that's labeled "Quick Search" & type the name of the program you want to uninstall.

Click the checkbox beside the name of the program you want to uninstall, and select "Mark for Complete Removal".

Instructions on how to install Skype can be found here: [http://www.noobslab.com/2012/11/install-latest-skype-41-in-ubuntu.html](http://www.noobslab.com/2012/11/install-latest-skype-41-in-ubuntu.html)

Hope that helps.

---

### Post by 3rdalbum on 2013-03-01
How did you install Skype and what is not working? Please be specific.

If you installed Skype using the Deb (Debian) package, or through a repository or PPA or Ubuntu Software Center, then you can use Software Center to remove it too.

---

### Post by audiomick on 2013-03-01
> **Princess Bernice said:**
> Here are the steps for finding programs that you want to uninstall:

On the menu bar on the top, click on these: System > Administration > Synaptic Package Manager

Synaptic Package Manager will open up; look for the box that's labeled "Quick Search" & type the name of the program you want to uninstall.

Click the checkbox beside the name of the program you want to uninstall, and select "Mark for Complete Removal".

Synaptic is not, as far as I know, installed by default on any version past about 10.10 or so. It can be installed via the Software center, but the instructions above apply in principle to the Software center as well, even if the steps are not precisely the same.

If you know the name of the package for sure and exactly, and it was installed via the package management somehow, i.e. from a .deb or a repository, you could also use the command

```
sudo apt-get purge <package_name>
```

However if you don't know the package name exactly, that will just give you errors.

---

### Post by oldos2er on 2013-03-01
> **Princess Bernice said:**
> Here are the steps for finding programs that you want to uninstall:

On the menu bar on the top, click on these: System > Administration > Synaptic Package Manager


Ubuntu hasn't used Gnome 2.x for well over two years; your advice is seriously out-of-date.

---

### Post by testosteroar on 2013-03-01
I looked up the downloads for skype on linux and there are no downloads for ubuntu 12.10 64 bit. there are ubuntu 12.04 32 bit and multiarch. I tried multiarch and everything downloaded fine but the program refused to open when I tried to open it. It just blinked a few times then did nothing. Thank y'all for the installing/unistalling help I got it figured out now.

---

### Post by androideka31 on 2013-03-01
I'd stay away from Skype until it's stable. It really messed me up and I was running Pangolin. I had to un install Ubuntu then reinstall.

---

### Post by DiabolicalClaptrap on 2013-03-01
> **testosteroar said:**
> I have ubuntu 12.10 and I dont know how to find the stuff I download so I can uninstall them. Example: I tried installing skype for ubuntu which didnt work. Also if anyone knows hoe to get skype working for 12.10 I would love to know thank you.

[Skype for Linux]("http://www.skype.com/en/download-skype/skype-for-linux/")

Try Ubuntu 12.04. This package will run through the Ubuntu Software Center.

There are a few ways to remove programs. One is synaptic, which you can get with: sudo apt-get install synaptic
Once in synaptic, you can search for your program, right click and select completely remove, and apply it. You'll be taken through a few dialogs which you can just click 'ok' on. Make sure nothing fishy is going on, like the removal of "unity".

The other way is more hands on but more convenient. Let's use skype as an example:

ctrl, alt + t on your keyboard to enter terminal. In here, type: sudo apt-get remove/purge

You can use either one of these. Purge will remove all package files (i.e. any installers), configuration files. Remove will simply uninstall, but keep packages and any config files.

Similarly, you can use: sudo apt-get install program here

---

### Post by Paqman on 2013-03-01
> **androideka31 said:**
> I'd stay away from Skype until it's stable. It really messed me up and I was running Pangolin. I had to un install Ubuntu then reinstall.

I'd call it stable. I've had it installed on several machines for a couple of years at least and it gives me no trouble at all.

---

### Post by samsom63 on 2013-03-01
> **Paqman said:**
> I'd call it stable. I've had it installed on several machines for a couple of years at least and it gives me no trouble at all.

Same for me, very stable on ubuntu 12.10 so far

---

