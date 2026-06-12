---
title: "Avant Window Navigator &lt; ObjectDock"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-13
I got avant window navigator hoping it would be more like objectdock...with a lot of options...but I don't really know how it works.  Here's what I want:

Set on top edge or screen
Quick autohide
Shortcuts to selected applications

That's really all I need, but i haven't been able to do any of that.  I know you can make it autohide, but it is very slow, and it isn't my computer.  Also, all it does not is keep the windows....but like I said...I'd like to have shortcuts just like you can have with objectdock or the Mac dock. I'd appreciate any help.  Thank you.

---

### Post by Rukaru on 2008-05-13
And is there a way to run objectdock on ubuntu without using wine?

---

### Post by Inxsible on 2008-05-13
> **Rukaru said:**
> I got avant window navigator hoping it would be more like objectdock...with a lot of options...but I don't really know how it works.  Here's what I want:

Set on top edge or screen
Quick autohide
Shortcuts to selected applications

That's really all I need, but i haven't been able to do any of that.  I know you can make it autohide, but it is very slow, and it isn't my computer.  Also, all it does not is keep the windows....but like I said...I'd like to have shortcuts just like you can have with objectdock or the Mac dock. I'd appreciate any help.  Thank you.Avant gives you 2 of the 3. You can autohide it and it can have launchers for selected apps. However, you cannot set it anywhere but its default location of bottom center.

I have no clue how objectdock works. Never used it.

---

### Post by Inxsible on 2008-05-13
> **Rukaru said:**
> And is there a way to run objectdock on ubuntu without using wine?
I just googled on it and it seems to be Windows software. So No you cannot run ObjectDock without Wine, unless of course you are willing to pay for CrossOver and its still not a guarantee that ObjectDock will run on Crossover.

---

### Post by bred on 2008-05-13
[http://wiki.awn-project.org/index.php?title=FAQ]("http://wiki.awn-project.org/index.php?title=FAQ")

[COLOR="RoyalBlue"]hope it will help u[/COLOR]

---

### Post by Joeb454 on 2008-05-13
If I remember correctly, you can move Kiba-Dock around the screen, and I think it will autohide and allow shortcuts to selected apps. So the OP may want to look into that

---

### Post by Inxsible on 2008-05-13
> **Joeb454 said:**
> If I remember correctly, you can move Kiba-Dock around the screen, and I think it will autohide and allow shortcuts to selected apps. So the OP may want to look into thatI agree, but its a little heavy on the memory footprint.

There is also KoolDock which allows for all 3 i think.

---

### Post by Joeb454 on 2008-05-13
I never noticed a heavy memory footprint, usually after Ubuntu has loaded I have around 1600Mb RAM left to play with ;)

---

### Post by Inxsible on 2008-05-13
> **Joeb454 said:**
> I never noticed a heavy memory footprint, usually after Ubuntu has loaded I have around 1600Mb RAM left to play with ;)Yeah, these days the computers have 2GB+ total memory so its not like your world comes crashing down on you. But yeah, the Physics engine (i forget the name) takes up a lot of memory.

---

### Post by SunnyRabbiera on 2008-05-13
well currently AWN is targeted at OSX users but I think they may offer the option to change where it appears in later versions... its still in early development so you have to give it some leeway.

---

### Post by Lord Xeb on 2008-05-13
For shortcuts, just drag and drop what you want into AWN and it will appear there (kind  of like the panel).


For auto-hide, right-click on the AWN bar and select "preferences" (you must have AWN manager for this to work though), then select "auto-hide bar when not in use"

For setting it on the top of the screen, I have no idea... sorry

---

### Post by Lord Xeb on 2008-05-13
For shortcuts, just drag and drop what you want into AWN and it will appear there (kind  of like the panel).


For auto-hide, right-click on the AWN bar and select "preferences" (you must have AWN manager for this to work though), then select "auto-hide bar when not in use"

For setting it on the top of the screen, I have no idea... sorry

---

### Post by 16777216 on 2008-05-13
Cairo dock is what you want.

If you want to use a repository.
First get the key.

```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
```Then in the main menu System > Administration > Software Sources.
Go to the Third-Party Software tab and add

```
deb http://repository.cairo-dock.org/ubuntu gutsy cairo-dock
```( I know it says Gutsy but it works on Hardy without problem. )

Reload the repo info and install from Synaptic or in a terminal type 
```
sudo apt-get update 
sudo apt-get install cairo-dock cairo-dock-plug-ins
```you will now find it in Applications > System Tools > Cairo-Dock.

If you don't want or trust a third party repo then a deb can be found here.

[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

---

### Post by Rukaru on 2008-05-13
> **16777216 said:**
> Cairo dock is what you want.

If you want to use a repository.
First get the key.

```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
```Then in the main menu System > Administration > Software Sources.
Go to the Third-Party Software tab and add

```
deb http://repository.cairo-dock.org/ubuntu gutsy cairo-dock
```( I know it says Gutsy but it works on Hardy without problem. )

Reload the repo info and install from Synaptic or in a terminal type 
```
sudo apt-get update 
sudo apt-get install cairo-dock cairo-dock-plug-ins
```you will now find it in Applications > System Tools > Cairo-Dock.

If you don't want or trust a third party repo then a deb can be found here.

[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

Okay..this is the part where I politely ask you to repeat that in English.  I am brand new to ubuntu.  Can you tell me what to do and how to do it step by step?  

I don't know what a deb is.  I mean...I assume it stands for debian, but I don't know what that is either...I've just seen it before.  I don't want to trust a third party repository.  Is getting this a secure risk of any sort?  I am dual booting XP.

---

### Post by Inxsible on 2008-05-13
> **Rukaru said:**
> Okay..this is the part where I politely ask you to repeat that in English.  I am brand new to ubuntu.  Can you tell me what to do and how to do it step by step?  

I don't know what a deb is.  I mean...I assume it stands for debian, but I don't know what that is either...I've just seen it before.  I don't want to trust a third party repository.  Is getting this a secure risk of any sort?  I am dual booting XP.Cairo dock is yet another option for using a dock. AWN, Cairo dock, KoolDock are simply docks that you can use anyone of.

What he has given you is the steps to install it on your machine, should you so want it.

.deb is a file extension. Such files can be installed on Debian based OS by simply double clicking on them.

When it comes to trusting a third party repo or using a deb --- They both amount to the same thing as in you are using a deb file generated by somebody else...so you are using someone else's code in any case.

Of course that is a risk since you don't know what that code has. But having said that, Linux supports a lot of Open Source and therefore  you will find many developers with neat and great pieces of software that they have written and made available to the public for free.

---

### Post by Rukaru on 2008-05-13
> **Inxsible said:**
> Cairo dock is yet another option for using a dock. AWN, Cairo dock, KoolDock are simply docks that you can use anyone of.

What he has given you is the steps to install it on your machine, should you so want it.

.deb is a file extension. Such files can be installed on Debian based OS by simply double clicking on them.

When it comes to trusting a third party repo or using a deb --- They both amount to the same thing as in you are using a deb file generated by somebody else...so you are using someone else's code in any case.

Of course that is a risk since you don't know what that code has. But having said that, Linux supports a lot of Open Source and therefore  you will find many developers with neat and great pieces of software that they have written and made available to the public for free.

Ok thanks.  Yeah...I am a huge security freak, so I don't think i want to take the risk unless someone can provide me with some information about this particular application that could convince me of it's safety.  

Now, I know Ubuntu is considered far safer than windows since there are far fewer viruses for it.  Of course, Ubuntu doesn't really have any good virus or spyware scanners, and that makes me nervous.  Having XP on the same computer makes me more nervous.  i don't like that you can access the C drive from XP while in Ubuntu. You need a password, but it still concerns me.

---

