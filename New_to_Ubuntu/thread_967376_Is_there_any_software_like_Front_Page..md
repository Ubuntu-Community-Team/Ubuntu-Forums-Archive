---
title: "Is there any software like Front Page."
date: 2008-11-02
forum: New to Ubuntu
---

### Post by theamber on 2008-11-02
Hi is there any software to make web pages and publish them like Front Page express for Linux?
Thanks.

---

### Post by ad_267 on 2008-11-02
Kompozer is probably what you're after if you want a WYSIWYG application.

It might be a good idea to have a look at using a content management system for publishing your website instead.

---

### Post by theamber on 2008-11-02
Thanks I downloaded komposer now I have the files but I do not see any executional files how do I install it from the desktop?

---

### Post by theamber on 2008-11-02
I extrated it and put kmposer on the application menu now where should I put the komposer folder or should i live it on the desktop. I mean is there a better directory where to put it.

---

### Post by ad_267 on 2008-11-02
Installing software in Ubuntu is different to Windows. Please read this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

You can go to Applications -> Add/Remove and search for Kompozer to install it.

---

### Post by FreewheelinFrank on 2008-11-02
System>Administration>Synaptic Package Manager

Search for Kompozer, right click and check 'Mark for installation', then click 'apply'.

---

### Post by ad_267 on 2008-11-02
Just to clarify, installing from Add/Remove and installing from Synaptic will have the exact same effect. They are just different methods of accomplishing the same thing.

---

### Post by FreewheelinFrank on 2008-11-02
> **ad_267 said:**
> Just to clarify, installing from Add/Remove and installing from Synaptic will have the exact same effect. They are just different methods of accomplishing the same thing.

Yes, that's right.

---

### Post by theamber on 2008-11-02
I just downloaded it from google and extracted then I run the komposer file and it works. I inserted it in the menu applications > internet manually but the Komposer folder is in the desktop where should I put it.

---

### Post by FreewheelinFrank on 2008-11-02
I think you'd be better off uninstalling it and reinstalling via Add/Remove or Synaptic.

---

### Post by theamber on 2008-11-02
> **FreewheelinFrank said:**
> I think you'd be better off uninstalling it and reinstalling via Add/Remove or Synaptic.

The problem is that it does not show in add remove nor in ultamix where is Synaptic?

---

### Post by ad_267 on 2008-11-02
Go to System - Administration - Software Sources and make sure that universe and multiverse are ticked, then try again.

Synaptic is in System - Administration - Synaptic Package Manager. I've got no idea what ultamix is.

---

### Post by theamber on 2008-11-02
> **ad_267 said:**
> Go to System - Administration - Software Sources and make sure that universe and multiverse are ticked, then try again.

Synaptic is in System - Administration - Synaptic Package Manager. I've got no idea what ultamix is.

Ultamix is another software installer universe and multiverse where checked.
In add remove programs it shows synaptic installed but I dont see it.
I am trying to find Komposer in the add remove menus but is not there.

---

### Post by Joeb454 on 2008-11-02
Ultamatix is not supported at all on these forums - it WILL break your system (eventually).

To install Kompozer please try clicking [this link]("apt://kompozer") or finding something from [this website]("http://appnr.com/")


Update: For more about Ultamatix - read this blog post: [http://mjg59.livejournal.com/99905.html](http://mjg59.livejournal.com/99905.html)

---

### Post by ad_267 on 2008-11-02
It's kompozer with a z.

---

### Post by theamber on 2008-11-03
> **Joeb454 said:**
> Ultamatix is not supported at all on these forums - it WILL break your system (eventually).

To install Kompozer please try clicking [this link]("apt://kompozer") or finding something from [this website]("http://appnr.com/")


Update: For more about Ultamatix - read this blog post: [http://mjg59.livejournal.com/99905.html](http://mjg59.livejournal.com/99905.html)
Thanks, now how do i remove ultamatix it does not appear in the add remove programs.

---

### Post by macogw on 2008-11-03
> **theamber said:**
> The problem is that it does not show in add remove nor in ultamix where is Synaptic?

Oh God.  Do NOT use Ultamatix.  It WILL break your system.

---

### Post by ad_267 on 2008-11-03
> **theamber said:**
> Thanks, now how do i remove ultamatix it does not appear in the add remove programs.

This should help: [http://ubuntuforums.org/showthread.php?p=5993059](http://ubuntuforums.org/showthread.php?p=5993059)

It should appear in Synaptic, and you can select to "Mark for complete removal"

Then you need to edit your /etc/apt/sources.list file to remove the lines added by ultamatix. You can edit this file by pressing Alt+F2 and running "gksu gedit /etc/apt/sources.list".

---

