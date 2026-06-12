---
title: "Fresh new user"
date: 2014-09-06
forum: New to Ubuntu
---

### Post by AspiringDesigner on 2014-09-06
First of I want to say I am liking ubuntu as far as the theme, wallpaper and the overall feel it has. 
I decided to make a new thread because as a fresh new ubuntu user with no linux expirience I wonder if it was possible to be helped in a small areas. 
I am using ubuntu I just freshly after days managed to figure out what i was doing wrong and could not install, but now it is up and running fully and well. 
My situation now is that little stuff such as skype I can't seem to be able to install, keeps auto opening the sotware center and it just does not want to install. It acts as if its downloading and everything is goinng well but then once it downloads it just says install as if it never installed and I look for it all over the place ad is no where. I also noticed another problem which is if I try downloading things I normally used to use in windows like bittorrent or just simply other stuff it does download in the ubuntu side but then it wont open, keeps giving me this window about how I need to find a program to be able to read such files (the installation files of any software) 
For what i gathered so far in ubuntu if it is not in the software center it cannot be downloaded and installed, makes me feel like a sort of Itunes thing where if its not from them just simple cant use it.

---

### Post by EuclideanCoffee on 2014-09-06
Welcome to Ubuntu! 

You can install software outside of the Software Center.

Here's a walk through for Skype.
[http://askubuntu.com/questions/488053/how-to-install-skype-4-3](http://askubuntu.com/questions/488053/how-to-install-skype-4-3)

You may also install it via Software Center. I'm unsure why you can't in particular.

---

### Post by Bucky Ball on 2014-09-06
Which Ubuntu release are you using?

---

### Post by grahammechanical on 2014-09-06
Ubuntu has installed by default a BitTorrent client called Transmission. Search for it the Dash. Are you sure that you are not trying to install MS Windows versions of software? Windows exe files will not run on Linux.

Software in the software centre is packaged for Ubuntu and has been code audited to make sure it does not do anything nasty to the operating system. The same cannot be said for software downloaded from web sites.

Skype is not in the software centre because it is proprietary and not open source software. It cannot be code audited or patched by Ubuntu maintainers. But so long as it is a Linux version that has been package in the debian (.deb) package format we can install it. 

If you wish to talk about Ubuntu in general terms, which is what you are doing, then we have a section called Ubuntu, Linux and OS chat. If you want help with problems, then you need to be specific as to what the problem is. Specific about the applications you are trying to install.

Regards.

---

### Post by deadflowr on 2014-09-06
Skype is available through the canonical partner repositories.
It's been up-dated.
Here a quick howto
[http://www.omgubuntu.co.uk/2014/08/install-skype-linux-4-3-ubuntu-software-center](http://www.omgubuntu.co.uk/2014/08/install-skype-linux-4-3-ubuntu-software-center)

---

### Post by EuclideanCoffee on 2014-09-07
> **deadflowr said:**
> Skype is available through the canonical partner repositories.
It's been up-dated.
Here a quick howto
[http://www.omgubuntu.co.uk/2014/08/install-skype-linux-4-3-ubuntu-software-center](http://www.omgubuntu.co.uk/2014/08/install-skype-linux-4-3-ubuntu-software-center)

FYI, this doesn't work for me. There is no Skype package available to me.

EDIT: I just realized that I had to enable the other sources in the directions. Works fine now.

---

### Post by deadflowr on 2014-09-07
> **ruze said:**
> FYI, this doesn't work for me. There is no Skype package available to me.

EDIT: I just realized that I had to enable the other sources in the directions. Works fine now.

You can also go here
[https://apps.ubuntu.com/cat/applications/skype/](https://apps.ubuntu.com/cat/applications/skype/)
And click on the orange button marked
"available on the software center"
it'll ask to launch application(the software center) and open up directly at the skype one

---

### Post by Impavidus on 2014-09-07
As said, skype is available from the canonical partner repositories. Enable those repositories and skype will be available from the software centre.

You'll find software for almost everything you need in the repositories. Often not the programs you were familiar with on Windows, but other, equivalent, programs, that may even be better. In case you really need it and know what you are doing, you can install software from other sources, so you're not tied to the software centre.

If you want software, I'd say this is the right order to try (in some cases you may want to swap rules 5 and 6):
1: Install via the software centre (or one of the alternative front ends).
2: Find an alternative that is available through the software centre.
3: Find a [PPA]("https://help.ubuntu.com/community/PPA") that will add the software to the software centre.
4: Download a .deb file, double click it and it should install.
5: Download a pre-compiled binary or script and install it manually. There are no simple rules for manual installation.
6: Download the source code, compile and install manually. There are no simple rules for manual installation.
7: Write the software yourself.

The windows way of downloading an installer is more or less equivalent to rule 4.

---

### Post by stalkingwolf on 2014-09-07
download and install skype from synaptic package manager.   you will need to change the repositories first.
open synaptic, then click settings > repositories > other software.  make sure canonical partners is checked. Click close.  click reload that will reload the repositories with updated packages.

type skype into the search bar.  it should be version 4.3.**** if not it wont work  . then just mark for installation and apply.  it will be in the internet tab.

---

### Post by deadflowr on 2014-09-07
> **stalkingwolf said:**
> download and install skype from synaptic package manager.   you will need to change the repositories first.
open synaptic, then click settings > repositories > other software.  make sure canonical partners is checked. Click close.  click reload that will reload the repositories with updated packages.

type skype into the search bar.  it should be version 4.3.**** if not it wont work  . then just mark for installation and apply.  it will be in the internet tab.

Installing synaptic would be a good starting point first.;)

---

### Post by olliemonster on 2014-09-09
First of all, Glad you like Ubuntu  Now for your question You can't install windows .exe files though Ubuntu because the code is incompatible (actually you could use a program like wine but that's would be for a different day)  You would need to find a .deb file instead and install that though the Ubuntu software center.

---

### Post by ThatBum on 2014-09-10
The Software Center isn't like the iTunes Store level of control at all. It's actually a GUI frontend for the system's package manager. What the package manager does is download and install/remove packages from repositories. Packages contain the program and instructions on how to install it, such as dependencies on other programs and post-install actions. Repositories are collections of packages on remote servers. The list of the repos' contents are cached on your machine in a database.

The main Ubuntu repositories are the most trusted and are enabled by default. A few additional ones can be enabled at Software & Updates in settings. The reason for this is that some software can't be included by default for legal reasons, for example proprietary software such as Skype.

You can also add PPAs (personal package archive), which include more or updated software as compared to the repos, and often contain a single program, maintained by smaller-time devs. Please be careful when adding PPAs, as the quality standard of the main repos doesn't necessarily apply.

Additionally, you can install software manually by running downloaded .deb files. This is not recommended, as the software will not update because it's not in the repo database (software like Dropbox and Google Chrome add their repos when installing, however). Finally, one could compile/build the program from scratch, but this is very complicated for the average user and should be a last resort if it's not available elsewhere.

Hope I was of help.

---

