---
title: "Install Skype on 12.10"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by prakashru on 2012-10-17
hi friends,

After struggling of hard efforts, I am failed to install the skype in ubuntu 12.10 and 64 bit machine.
Every time, it is showing the error

The following packages have unmet dependencies:

skype: Depends: skype-bin but it is not going to be installed

Please help me to install the skype.

Thanks in advance to all
Regards,
Prakash

---

### Post by oldos2er on 2012-10-17
Post moved to its own thread.

---

### Post by newb85 on 2012-10-17
Two things:

First, make sure the Canonical Partners repository is enabled.

Then, try running
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```
before installing.

---

### Post by squakie on 2012-10-18
Also - did you install via the package manager, or did you download Skype from somewhere else? If you just go to the software center, you'll see Skype is available there - that's how I installed it, and I haven't any of the problems with dependencies you mention.
 
A little background: most software has libraries, etc., it "depends" on to be able to install and run. The package manager, especially using one of the front-ends like Synaptic, try to resolve and install those dependencies at the time you try to install the package. If you pick up, as an example, a .deb of Skype from another source, it may not contain the dependencies and it won't automatically find them and install them. This results in errors like you are getting.
 
Via the terminal window, you can also ask the package manager to "grab" the dependencies for you:
 
sudo apt-get build-dep <package name>
 
You may need to try that with the package name for Skype.
 
If Skype did install but you can't run it, doing as newb85 mentioned may pick those up as well.
 
If at all possible, use apt or synaptic package manager or the software center (the icon looks sort of like a birthday present bag) to install - you will normally not encounter problems like this.

---

### Post by NikTh on 2012-10-18
As [newb85]("http://ubuntuforums.org/member.php?u=833049") said , be sure that Canonical Partners repository is enabled. 

Open a terminal (Ctrl+Alt+T) and do 

```
gksudo software-properties-gtk
```Mark the box 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225694&d=1350544653[/IMG]

and then do 

```
sudo apt-get update 
sudo apt-get install --reinstall skype
```Thanks

---

### Post by iamahsan on 2012-10-18
I had the same problem, Then i followed the [this link]("http://wiki.debian.org/skype").
```
# dpkg --add-architecture i386
# apt-get update
# wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)
# dpkg -i skype-install.deb
# apt-get install -f
```

Hope this works.

---

### Post by Linuxisfast on 2012-10-19
I have the same issue here on my Quantal x64, looks like its a packaging error. I have reported this on launchpad as well. [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/1068422](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/1068422)

It installs fine on the x32 12.10

Hope they fix this soon, Skype works fine on 12.04

---

### Post by Linuxisfast on 2012-10-20
Change your mirrors, seems like the mirrors in India haven't been synced properly. Skype installs fine with main mirror.

---

### Post by helmut_hed on 2013-02-22
Fails for me, Quantal x64, same failure mode (complaints about i386 qt package dependencies).  I am not in India so that particular mirror issue doesn't apply.... maybe some other does.

---

