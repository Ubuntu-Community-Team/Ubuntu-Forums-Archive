---
title: "Installing an app from Terminal"
date: 2017-10-09
forum: New to Ubuntu
---

### Post by ra.abbasi on 2017-10-09
Hello,

I'm new on Ubuntu 16.04 x64 and need to know the way using Terminal we are able to install an application rather than just simply installing it through Ubuntu Software. Now what commands to issue on Terminal to install, say, the VLC Media Player program please?

By the way,
I like to do most of my works by Terminal on Ubuntu.

---

### Post by yetimon_64 on 2017-10-09
For your example of VLC the command would simply be ...
```
sudo apt install vlc
```

The apt command will work out any necessary dependencies and install them automatically making the process very simple.

To see if an application is available (using your example of vlc) the command to use is ...
```
apt-cache policy vlc
```

And
```
apt-cache search vlc
``` to see related packages or packages that mention vlc in their name/description.

The apt-cache command (with the policy or search options) does not need sudo as it is not installing anything but just providing information, whereas sudo is needed for the apt command to actually install the program.

Regards, yeti.

---

### Post by linuxissuperawesome on 2017-10-09
Find Your Package [here]("https://packages.ubuntu.com/").
And Do The Following.
```
sudo apt-get install "package name"
```
eg.
If You Want To Install VLC, The Code Would Be ```
sudo apt-get install vlc
```.
Try To Run ```
sudo apt-get update
``` Once In A While. Good Luck!:grin::grin:

---

### Post by vasa1 on 2017-10-09
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto) is a nice resource.

---

### Post by deadflowr on 2017-10-09
Open a terminal and run
```
man apt-get
man apt
man dpkg
```
should give you most of the relevant options.
(click Q to close/exit the man pages)

extra command to find packages would be
```
apt search any-word-will-do
```
it'll try to list all packages even remotely related to whatever you type, with a basic description.

---

### Post by ra.abbasi on 2017-10-10
Thank you very much yeti. Done!

> [COLOR=#000000]Find Your Package [/COLOR][here]("https://packages.ubuntu.com/")[COLOR=#000000].[/COLOR]
I searched[ here ]("https://packages.ubuntu.com/xenial/video/")for the package just for testing. Which one should I've installed? 

Thanks to Vasa1 and all.
I will read the resource carefully but is there any list of primary commands of Ubuntu with examples for beginners, please?

---

### Post by ian-weisser on 2017-10-10
The commands I consider 'primary' are probably different from the list you consider so.
For basic commands to install and uninstall software from the Ubuntu repositories (the best choice for new users), re-read post #5 of this thread.

---

### Post by again? on 2017-10-10
> **ra.abbasi said:**
> Thank you very much yeti. Done!


I searched[ here ]("https://packages.ubuntu.com/xenial/video/")for the package just for testing. Which one should I've installed? 

Thanks to Vasa1 and all.
I will read the resource carefully but is there any list of primary commands of Ubuntu with examples for beginners, please?
You wouldn't browse [https://packages.ubuntu.com](https://packages.ubuntu.com) to install random applications... it's more of a reference site.

What I suggest if you want to practice using terminal to install applications, is to use synaptic to get the actual package name.
Install synaptic.
```
sudo apt install synaptic
```

You could browse the software centre for applications then search in synaptic to get the actual package name.
Clicking on properties in synaptic when a package is highlighted brings up an info window where you can highlight and copy the actual package name
to use via terminal install.
eg.
Gnome Mplayer as shown in the software centre.
[ATTACH=CONFIG]277075[/ATTACH]

Resultant search in synaptic.
[ATTACH=CONFIG]277074[/ATTACH]
So to install Gnome Mplayer via terminal I would use
```
sudo apt install gnome-mplayer
```
> glen@GU17:~$ sudo apt install gnome-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libgda-5.0-4 libgda-5.0-common libgmlib1 libgmtk1 libgmtk1-data mplayer2
Suggested packages:
  gecko-mediaplayer libgda-5.0-bin libgda-5.0-mysql libgda-5.0-postgres libgmlib1-dbg libgmtk1-dbg
The following NEW packages will be installed:
  gnome-mplayer libgda-5.0-4 libgda-5.0-common libgmlib1 libgmtk1 libgmtk1-data mplayer2
0 to upgrade, 7 to newly install, 0 to remove and 12 not to upgrade.
Need to get 1,723 kB of archives.
After this operation, 11.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Notice the last line asking to continue. Because the Y is capitalized in " [Y/n]" you can just press Enter to answer yes.


**P.S.** When using the terminal read what it is telling you before proceeding.
Don't continue if unsure what's happening.

You can find a good command line tutorial [**HERE**]("https://ryanstutorials.net/linuxtutorial/").

---

