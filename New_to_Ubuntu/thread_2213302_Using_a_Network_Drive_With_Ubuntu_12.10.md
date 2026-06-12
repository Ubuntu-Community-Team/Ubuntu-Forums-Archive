---
title: "Using a Network Drive With Ubuntu 12.10"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by Rik_Hess on 2014-03-25
I am very new to Ubuntu and I am having an occasional problem seeing my network drive.

I use a network drive to store all my data so it can be accessed from any computer on my home network.

When I run Home Folder, there is a section on the left list that allows me to Browse the network, and my drive is there.

But some apps, like Thunderbird, do not seem to see the network drive when I tried to set my email profile in the Profile Manager. Same thing with GnuCash in that its Browse for folder does not see the network drive. 

Is there a way to make the entire system see this drive? In Win XP I just map the drives folders to drive letters and then they work like standard folders and are there for any app to use them. I need to use my email and finance tools from any computer I'm working on.

Thank you.

---

### Post by 3rdalbum on 2014-03-26
I must admit I have not used network drives on anything after 12.04, but if 12.10 works the same you will find your network drive in the ".gvfs" folder inside your home directory.

.gvfs is a hidden folder and you can see hidden folders by pressing Control H. You can then create a bookmark to the .gvfs folder so it is easy to access from the Open/Save windows in programs.

If the drive is not in .gvfs, try in /media/

---

### Post by Rik_Hess on 2014-03-26
I tried the tip you shared, but while the network drive folders Bookmarks showed in the Home folder display, they were not available in the TBird Profile Manager.

Any other ideas?

Thanks.

---

