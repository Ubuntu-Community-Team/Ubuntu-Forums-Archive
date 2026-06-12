---
title: "[SOLVED] acessing ubuntu filesystem from within vitrualbox and vise -versa"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-21
so i have virtualbox installed and all setup with windows xp pro

how can i acess my Ubuntu filesystem from within the guest OS (windows xp)?

and how can i access files from the guest OS in Ubuntu?

---

### Post by boblemur on 2008-09-21
im not sure, this is kind of the point of a virtual machine however what you can do, is share the folder u want accessible, and then map it inside windows. make sure u keep urself secure though because it is shared within the network. keep a password on it.

share the folder in ubuntu 

then go into windows and "map network drive" its under tools i believe from memory

hope this helps

---

### Post by MasterNetra on 2008-09-21
Well you can't access Ubuntu from within a Virtual Machine but with Virtual Box i think it can allow you to setup a shared folder that both can access but i wouldn't know how to go about it.

---

### Post by jimmy the saint on 2008-09-21
you need to install the VirtuabBox guest additions.  This does a lot of things, including allowing you to map a network folder from within the XP guest to a folder in your linux filesystem.  Do a google search for virtualbox shared folder.

---

### Post by tjwoosta on 2008-09-21
ok i have the guest additions already installed


i went into the virtual XP and shared the floders i wanted to share


i can access the shared files with another windows machine but not with ubuntu

in ubunutu i can go to "Places-Network" then i can see "Windows Network" but if i click on it, it comes up empty

also i cannot acess shared files from my other windows computer on ubuntu either

so basically what do i have to do to make Ubuntu see the shared files on the windows network?

---

### Post by jimmy the saint on 2008-09-21
you are going about this backwards.  You don't want to share the xp guest file.  You want to go into the XP guest, and from there, map a network drive.  This means that you are telling the XP guest to look on a network for a folder that it will treat as network storage.  

Visualize the guest and host as different machines.  The file that you want to share will be on the Ubuntu machine.  You want to be able to also access it from the windows machine.  You will create it on the Ubuntu machine just like any other file.  You have to tell the windows machine (the guest) to access it over the (imaginary) network.  So, from within the Windows machine (guest) you must tell it to map that file to a network drive.

You will be sharing a file that exists on the Ubuntu box, not the guest machine.  When it is set up, it will simply appear to be a network drive on the windows (guest) machine.

I wish I could find the tutorial that I used, but I just cant find it.

---

### Post by Therion on 2008-09-21
Well you were given the opportunity to set up shared folders during the install, but you can still map a new folder as a network drive.  

So, to attach the Ubuntu shared folder to your Windows guest, open Windows Explorer and look for it under “My Networking Places/Entire Network/VirtualBox Shared Folders.

By right-clicking on a shared folder and selecting “Map network drive” from the menu that pops up, you can assign a drive letter to that shared folder.

*Voila*!

---

### Post by drs305 on 2008-09-21
I just did this yesterday. Installed Guest Additions in VB. Then in Devices, Shared Folders I pointed it to my ubuntu folders. In Ubuntu, went to the folder I wanted to share and right clicked and ticked the share options. The next time I opened XP in VirtualBox, I went to Explorer, opened My Network, and it showed the folder I had marked to share in Ubuntu. When I clicked on it, it asked me my Ubuntu username and password, after which I had full access.

---

### Post by jimmy the saint on 2008-09-21
The problem with that method is that, for many, there is a huge lag.  It is a well documented bug that, last I checked, has not been addressed.  By mapping the file as a network drive, rather than a network place, the performance hit is solved

---

### Post by tjwoosta on 2008-09-21
man im so confused...



ok this is what i jsut did right now


in the virtualbox settings i went to shared folders and chose a folder to share
(/home/tj/desktop/shared-virtual)

then i started the virtual windows XP and went to Network Places

i clicked add new network place

then i clicked browse, and i found one that said "virtualbox shared folders", and inside this was the file i chose to share earlier


so now i can acess the shared folder from both ubuntu and the virtual xp

the problem is that it is incredibly laggy



> The problem with that method is that, for many, there is a huge lag. It is a well documented bug that, last I checked, has not been addressed. By mapping the file as a network drive, rather than a network place, the performance hit is solved

how do i do that?

---

### Post by Therion on 2008-09-21
Doing it from within VB is pretty simple too...
Open VB, but not the VM, and double-click on Shared Folders.
Click on the icon for "Add New Shared Folder".
Click on the dropdown arrow in the folderpath and choose "Other" to navigate to the folder you want to share/map as the network drive (i.e. Home).

*Voila*!

---

### Post by tjwoosta on 2008-09-21
yes that exactly what i did, but it is very laggy when i access this from within the virtual XP 

then "jimmy the saint" said there was another way to do it thats not laggy but i have no idea what he was talking about

---

### Post by Therion on 2008-09-21
Well you can do the same thing from within the Virtual Machine as follows, though I don't know that it will solve the lag problem you're reporting.  
For me, the shared Home folder is drive z: and there's no lag in opening or moving files.  

Anyway here's what you do...


EDIT: Nevermind... That won't work.  I'm not sure how he's telling you to do it from within the VM itself.  

<scratching head>

Okay, if I read post numbers 8 and 9 correctly, Jimmy seems to be saying that by using the method suggested in post 8 many users experience a lag.  Have you TRIED setting up the shared folder by going into VB first and setting it up as a network drive?  That appears to be the way that Jimmy is saying is the superior method and it works like a charm for me as well.

The method in post 8 is the one that seems odd to me.  It's sets up the shared folder as a network place, not as network drive.  Having the folder show up as a network drive is infinitely better than a new Network Place.

---

### Post by tjwoosta on 2008-09-21
yes!

actually it did work

its a good thing i read what you wrote before you erased it
(i had no idea how to map a network drive)

if you map it as a network drive instead of a network place there is no lag at all


all is setup perfectly now

thank you guys

---

### Post by tjwoosta on 2008-09-21
```
Ok this is what to do


in virtualbox settings go to shared folders and choose a folder to share


then start the virtual XP

right click "My Network Places" and choose map network drive

browse to "virtualbox shared folders" and then choose the folder that you shared earlier

(there is absolutly no lag at all)
```

```

This is what not to do!

before what i did was actually go into "My Network Places" and click "add new network place" then choose the folder you shared earlier

(that made it so when i tried to open the network place it was incredibly laggy)
```

---

### Post by Therion on 2008-09-21
Yes, that's the proper way to do things in my opinion.

Glad you got it worked out.

---

