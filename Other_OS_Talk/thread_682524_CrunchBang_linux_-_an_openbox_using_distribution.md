---
title: "CrunchBang linux - an openbox using distribution"
date: 2008-01-30
forum: Other OS Talk
---

### Post by meborc on 2008-01-30
[http://crunchbang.org/archives/2008/01/22/crunchbang-linux-7-dot-10-dot-01-release-notes/](http://crunchbang.org/archives/2008/01/22/crunchbang-linux-7-dot-10-dot-01-release-notes/)

have been looking for a openbox distro (just to have everything set up from the beginning) to try out new looks

has any one tried it? any experience? downloading now

---

### Post by trevorgasm on 2008-01-30
i just downloaded, and ran it via virtual box. seems nice, fast, easy to use. i only tinkered with it for a litle bit tho. deffinately something i will look at more after class today.

---

### Post by wolfen69 on 2008-01-31
i just checked it out in virtualbox. it seems it would be no good with less than 192MB ram. but i liked it alot. it comes with a good selection of apps. also has all codecs etc. very nice. i will keep it in mind for my next 256mb machine.

---

### Post by urukrama on 2008-01-31
Looks interesting, but I'll probably stick with a command-line install of Ubuntu and adding whatever I need/want. I probably won't recommend this to other users, though. I am a bit weary of one-man distros. 

I might give this a try, though, just for fun :-)

---

### Post by meborc on 2008-02-02
one man distro or not - it is just a mod of ubuntu server + packages available in the repors... minor tweaking the scripts etc... so there is no need for a bunch of developers or support... just a ubuntu mod

i had time today to finally format my old laptops hdd and i installed crunchbang on it... so far so good :) no problems yet

EDIT: ram usage 90 Megs - now that is ligh (web browser running 4 tabs... nothing more)

---

### Post by chris4585 on 2008-02-04
i am going to give this a try and test it a bit

---

### Post by hilltop_yodeler on 2008-02-07
I've been using it now for a couple of days and am very pleased with the performance and the simplicity.  Philip has done nice work in putting this together.

My one trouble so far is that (short of doing some xml coding) I'm not sure about how to update the openbox menus.  I know that if I install menu (sudo apt-get install menu) that I can use the update-menus feature (sudo update-menus), which will add any new applications that I have installed to the openbox menu.  I'm just not sure though if this will interfere with the way that the menus have been set up in CrunchBang. 

Has anyone tried installing menu in CrunchBang?

---

### Post by hilltop_yodeler on 2008-02-07
Incidentally, I asked this same question on the CrunchBang forum.  Read Phillip's reply here:
[http://crunchbang.org/forums/topic/best-way-to-update-menus?replies=2]("http://crunchbang.org/forums/topic/best-way-to-update-menus?replies=2")

---

### Post by securitybreach on 2008-06-05
I know this thread is a little old but I thought I would mention an easier way to edit menus in openbox. There is a program called obmenu which allows you to change the menu with a gui instead of editing xml files manually. Just install it with 
```
sudo apt-get install obmenu
``` Just make sure to reload openbox via the menu after making changes. Here is the project's website with screenshots:

 [http://obmenu.sourceforge.net/scrshot.html](http://obmenu.sourceforge.net/scrshot.html)

Thanks

---

### Post by MaxIBoy on 2008-06-05
So it's like Ubuntu, only it runs even faster?
I'm intrigued... I've got an extra 45-gig partition, might give it a whirl to see if I like it.

---

### Post by eriqjaffe on 2008-06-05
> **securitybreach said:**
> I know this thread is a little old but I thought I would mention an easier way to edit menus in openbox. There is a program called obmenu which allows you to change the menu with a gui instead of editing xml files manually. Just install it with 
```
sudo apt-get install obmenu
``` Just make sure to reload openbox via the menu after making changes. Here is the project's website with screenshots:

 [http://obmenu.sourceforge.net/scrshot.html](http://obmenu.sourceforge.net/scrshot.html)

ThanksIIRC, obmenu handles the "openbox --reconfigure" behind the scenes, I've *never* had to reload openbox to get changes I made in obmenu to show up.

---

