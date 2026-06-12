---
title: "Virtual box sharing"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by ozbolt on 2008-09-29
I have up-to date ubuntu with virtualbox running WinXP (for some testing and programs), but i just don't know how to get to work shared folders so pleese 1 how to or tutorial please!
TNX.

---

### Post by starcannon on 2008-09-29
Create a folder at ~/ that you'd like to share.
Open up the settings for the XP install and point the shares to the folder
[IMG]http://img87.imageshack.us/img87/6069/vbfoldersharingsd7.png[/IMG]
in XP add it to network places, just follow along the Windows wizard.

[IMG]http://img441.imageshack.us/img441/5596/windowsnetorkplacesbp0.png[/IMG]

Now you can drag and drop things between Ubuntu and VB XP using this shared folder.

---

### Post by ozbolt on 2008-09-30
Thenx. Well, I see you are ReactOS and I have question about what are programs that works in there, I mean really works.
What I would need is DivX converter and some other video convertion tools? What about old (upon 2000) games? And what about MS office? Just asking...

---

### Post by ozbolt on 2008-09-30
Sorry for again posting but it doesnt run.
[[img]http://shrani.si/t/2f/oQ/4pog1OqI/doesntwork.jpg[/img]](http://shrani.si/?2f/oQ/4pog1OqI/doesntwork.png)
What to do?

---

### Post by Therion on 2008-09-30
Setting up a shared folder via "New Network Place" is one way to go about this, but typically the connection/transfer is slooooooooow.

The better route is setting up a "New Network Drive".  See [this tutorial](http://n00buntu.blogspot.com/2007/11/step-2-configuring-your-windows-vm.html) for instructions.  You'll need to scroll down a bit to the appropriate section.  The BEST way to do this is to set up a share when you're doing your virtual machine install though.

---

### Post by MrWES on 2008-09-30
Doesn't he need Guest Additions installed too?

---

### Post by Therion on 2008-09-30
> **MrWES said:**
> Doesn't he need Guest Additions installed too?
If he doesn't already then yeah, most likely. That's covered on the previous page of the tutorial.

---

### Post by starcannon on 2008-09-30
> **ozbolt said:**
> Thenx. Well, I see you are ReactOS and I have question about what are programs that works in there, I mean really works.
What I would need is DivX converter and some other video convertion tools? What about old (upon 2000) games? And what about MS office? Just asking...

Can't say for sure, I loaded it up in Virtual Box just to see it run. I have not yet really "tested" it, but it is definitely still alpha ware; the first thing I tried to do was to install the Virtual Box Guest Additions, upon which ReactOS crashed. So I'm guessing that for now you would not want to use it as a production OS; though if they continue with the project I think it may someday get there.

---

### Post by mateuszbaranski on 2008-10-04
> **ozbolt said:**
> I have up-to date ubuntu with virtualbox running WinXP (for some testing and programs), but i just don't know how to get to work shared folders so pleese 1 how to or tutorial please!
TNX.

I also spent 2 days on this topic. The FIRST thing that you should do in Windows xp machine is to INSTALL guest additions.
You could easily do it by runing the machine and than choosing "Install Guest Additions" from Device menu (not in Windows - it is in menu of the machine window!). This mounts the Guest Additions CD into your CDROM in Windows. Double click on CDROM and it starts installing them. Windows restart is needed. Then you could follow instructions in there:
[https://help.ubuntu.com/community/VirtualBox#Sharing Folders Between Host and Guest]("https://help.ubuntu.com/community/VirtualBox#Sharing Folders Between Host and Guest")

It simply doesn't work without this step. It is not written explicitly in above manual so I spent lot of time searching thru Internet.

---

