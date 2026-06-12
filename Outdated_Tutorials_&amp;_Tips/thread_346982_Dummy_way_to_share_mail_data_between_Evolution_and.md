---
title: "Dummy way to share mail data between Evolution and Thunderbird"
date: 2007-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by edmondt on 2007-01-26
Here is a trick on how to share mail data between Thunderbird and Evolution.

I have been using Thunderbird from PortableApps using wine and I wanted to try out Evolution, because it is better intergrated and I can sync my Pocket PC better with Evolution.

If you do not have any data on Evolution, you can do the following:

Open up your thunderbird profile folder with Nautilus, mine is on:

/home/edmondt/PortableApps/ThunderbirdPortable/Data/profile/Mail/Local Folders

Open up another Nautilus, navigate to your evolution folder, mine is on:

/home/edmondt/.evolution/mail/local

Now hold SHIFT and CTRL and click on the Inbox file from the thunderbird folder, drag it and drop it to the Evolution folder. This will create a symbolic link, rename this link to Thunderbird Inbox.

Next we can do the same thing,  hold SHIFT and CTRL and click on the Inbox file from the Evolution folder and drag and drop it to the Thunderbird folder, rename this link to Evolution Inbox.

Now you can access both inbox from either program, you may do the same with Sent Items, Drafts etc.


If you need to better import / export feature to thunderbird, download and install this addon:

[https://nic-nac-project.de/~kaosmos/mboximport-0.5.8.xpi](https://nic-nac-project.de/~kaosmos/mboximport-0.5.8.xpi)

I hope it helps, and maybe you can even use a single INBOX folder for both programs, I haven't tried that yet.

---

