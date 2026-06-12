---
title: "How do I create shortcut on desktop to NAS Share?"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by bill34 on 2014-03-21
Hi, New to forum and Ubuntu, but not new to PC's having started out using DOS a long time ago.

I have installed Ubuntu (the latetest stable version) on an old laptop for the sole purpose of allowing me to access files on my NAS drive. I can see the NAS drive and its shares using the home folder. I need to be able to drag and drop files from one share (or folder in a share) to another share or folder share. The way I have been doing this in WIndows XP is by mapping the NAS drive and creating desktop shortcuts of the folders I want to work with and then simply drag and drop files from one to the other. I am unable to find how to do this (or a similar) on Ubuntu. I get an error when I try to create a link to the NAS shares, telling me I can't create dynamic links to a NAS share. The NAS  (a Netgear ReadyNAS) uses Linux so I am not sure why this would be. Can anyone give me some pointers on how to do this, without having to learn backdoor access to Ubuntu? I would like to do this simply by using the GUI. I assume this is possible and it just me being stupid. TIA.

Bill.

---

### Post by pqwoerituytrueiwoq on 2014-03-21
1st set the share to automount on your system, i have used gigolo to set that
then just create shorcuts to the folders on the nas, or you can make regular folders and use [FONT=courier new]mount --bind[/FONT] to link them
you can make shortcuts like this
```
ln -s /path/to/nas/folderOrFile ~/Desktop/shortcutName
```

---

### Post by squakie on 2014-03-21
> **pqwoerituytrueiwoq said:**
> 1st set the share to automount on your system, i have used gigolo to set that
then just create shorcuts to the folders on the nas, or you can make regular folders and use [FONT=courier new]mount --bind[/FONT] to link them
you can make shortcuts like this
```
ln -s ~/Desktop/shortcutName /path/to/nas/folderOrFile
```

I've been trying the ln command myself on a local file and have found that the "to" file seems to be needed first, then the target.  So, if you are trying to link TO /path/to/nas/folderOrFile as you show, wouldn't it be:
```

ln -s /path/to/nas/folderOrFile ~/Desktop/shortcutName
```

I am FAR from knowing all of this - I was just testing as I have a need for the same thing, and found I had to flip the parameters as per the help for ln.

If I have that wrong, PLEASE post a correction and I'll remove my post as I don't want to cause any confusion!  ;)

Dave ;)

---

### Post by pqwoerituytrueiwoq on 2014-03-21
opps, you are right squaki, when [FONT=courier new]ln[/FONT] did not give me a error i assumed i had it right

---

### Post by bill34 on 2014-03-22
Thanks for the reply guys, I have installed Gigolo and will give it a try. I am still not sure where I type in the code, but will keep searching.

Bill.

---

### Post by Jacobonbuntu on 2014-03-22
Hi bill, take a look at [this link]("http://askubuntu.com/questions/429493/how-to-create-a-bookmark-that-opens-a-network-shared-folder/429496#429496"), I hope it helps. Commands, you type in the terminal. It might feel a bit "geeky" in the beginning to use the terminal, but it is not that difficult, and you will find out that the terminal usually gives you very specific and usefull feedback once you get used to it. However, most things in Ubuntu, you can do in GUI.

---

