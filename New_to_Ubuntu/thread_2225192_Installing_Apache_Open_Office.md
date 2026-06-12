---
title: "Installing Apache Open Office"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by steve119 on 2014-05-20
Well, as usual, I am led down the primrose path of ignorance and wasted time. I have an install of AOO inside an incomplete install of AOO because I didn't know how to do it correctly in the first place. So how do I fix it? Should I start over by  removing all of the folders related to all parts of the install and redoing everything from the beginning, adjusting the commands to relevant locations as appropriate? Here is what I have now:

/home/alexis/Downloads/en-US/DEBS/en-US/DEBS/desktop-integration

Notice the dual entry of /en-US/DEBS/ ? Surely this must be a mistake on my part for reinstalling it once I was already in the installed folder without knowing it. At this point I am stuck without any idea what to do correctly unless someone responds. My intention is to just delete everything from beneath the Downloads/ folder that refers to the first /en-US/DEBS/.. and just start over but I don't know the consequences to the efficient operation of Lubuntu by doing this. I managed to install GIMP 2.8 without much trouble at all, and it works fine, but this has proved more difficult to accomplish. I hope someone can tell me the best way for a newb to backup and regroup and do this right the second (third?) time.

---

### Post by Lars Noodén on 2014-05-20
Have you seen the instructions for after you download and unpack the tarball? 
[https://www.openoffice.org/download/common/instructions.html#linux-deb](https://www.openoffice.org/download/common/instructions.html#linux-deb)

```

cd /home/alexis/Downloads/en-US/DEBS/
sudo dpkg -i ./*.deb

```

There should be a bunch of package files (.deb) in that directory.  After you've installed them, you can delete /home/alexis/Downloads/en-US/ and its contents if you don't want to keep them around.

Just out of curiosity, why are you trying to install Apache OpenOffice?  LibreOffice is available already in the package repository and can be installed using Synaptic.  

LXMenu -> System Tools -> Synaptic Package Manager
 
It's always easier to install stuff from the repository and as a bonus updates and patches are a snap and come with automatic notification.

---

### Post by steve119 on 2014-05-20
Thanks for replying LN, I appreciate it. I did read them, but it did not install the way that it was referred to in those instructions. My install started in the Downloads folder because thats where it went. I assume I was supposed to move it somewhere else but didn't know it. Instructions are often lacking in detail necessary for a newb so they assume you either have already done, or know something should be done. One or more of the listed folders in the tree above do in fact have LOTS of other "folders or files" in them but I don't know what to do about the multi-layered condition of the orignal folder as shown above. As for the AOO vs. Libre, isn't that like asking me why I'm not using Mint or Red Hat instead of Lubuntu 14? I don't know at this point what versions of anything might be supported by the SPM in Lubuntu 14 so I just picked one and tried to find/follow instructions on installing and using it. That's why I come back here for info since sometimes the instructions were written for ubuntu 12. Do I know what or if there's a difference between ubuntu 12 and Lubuntu 14? No, actually. If Libre Office is pretty much the same and installs easily from the SPM, then I'm all for it. So then I just need to delete the above mentioned AOO folder tree, right?

---

### Post by deadflowr on 2014-05-20
You can simply delete the en-US folder.
You already have the tar/zip file for AOO, so re-extracting it again won't take much time, since you won't have to download it again. If you want to re-extract/install it at some later point in time.

That said, if you haven't actually installed AOO(which I'm 99.9999% positive you didn't), then simply search for 
libreoffice in the software center. Or look under Office or Documents.
It'll auto install, and a plus as mentioned, keep updating when updates come through.

---

### Post by Lars Noodén on 2014-05-21
The reason for suggesting LO over AOO is that LO is in the repository and installs with one or two clicks.  You'll find it with The Software Center or with Synaptic.  Thus both installation and maintenance is more or less automatic.  AOO packages, in contrast, have to be installed manually and updated manually.  Same with the cleanup.  Everything found its right place when you ran dpkg, so any residue from AOO remaining inside the ~/Downloads/ folder can be removed after the installation.  The package manager is a really big advantage and it is hard to overstate how good it is, IMHO, and how much work can be saved by using it.  

But aside from the package management (which for me is a *huge* benefit) there is currently still little difference between AOO and LO, they still share much of the same code base.  If AOO had been in the repository and LO outside it, my recommendation would have been the opposite.  

If you need a newer version of anything than is in the main repository, there is usually a development PPA where you can get it.  Even then that is working within the package manger framework.

---

