---
title: "I don't want the whole ubuntu-desktop package"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by rwin on 2008-10-23
Hi,

I just did a fresh install of Hardy on my new laptop. I decided I wanted to remove some applications including evolution, gimp (wanted 2.6) and open office (also wanted the 3.0 version).

So I removed those by ```
sudo apt-get remove evolution*
``` and so on. The trouble I came into was, that I couldn't see any Gnome-Panel after reboot. So looked it up and re-installed it by using: ```
sudo apt-get install gnome-panel
```Okay, then I had several other desktop applications not working. I read in this forum, "... just make sure you got the ubuntu-desktop package installed."

So I did ```
sudo apt-get install ubuntu-desktop
``` BUT I now got exactly the packages back that I removed before (evolution, gimp, openoffice)... I'm quite new to Ubuntu and might be following the wrong approach here, do you have any advice?

Thanks in advance!

Rajko


Just to make clear, what my question is: I know those applications are part of the ubuntu-desktop package. I just wanted to remove these specific packages without doing harm to the system itself.

---

### Post by oldsoundguy on 2008-10-23
under applications is a program called add/remove.  You can un-install evolution, for instance, there without resorting to terminal and it should leave everything else intact.
(handy area .. also System,> Administration,> Synaptic Package Manager has a lot of things you can add/remove to customize your set up.)
I did not un-install Evolution.  I just removed the quick launch from the panel and dragged and dropped Firefox and Thunderbird and Pan to take it's place.

---

### Post by laurielegit on 2008-10-23
I tried this a while back and also didn't succeed. as I did it through the synaptic package manager it failed to remove them as they were depended on by some other programs. try just going into the actual folder were the program is stored and deleting (but be ready to bare the consequences)

If anyone does know how to remove evolution *please* pm me.

---

### Post by niyonk on 2008-10-23
Evolution is the first thing i remove after a fresh install. And it removes fine except the icon in  the menu

Try synaptic
or
sudo apt-get remove evolution evolution-common

Good Luck!

---

### Post by aeiah on 2008-10-23
ubuntu-desktop is a metapackage. a package of packages. removing parts of it will destroy this metapackage. whilst this isnt as bad as it sounds, it really just means that if any brand new programs get included in the metapackage in the future, when you do an upgrade it will fail to pick these up. you wont have a problem upgrading the individual bits you've kept though.

but yes, i suggest using add/remove instead. evolution is needed by a lot of things though. why do you want to delete these things? if its for space saving reasons then i guess you'll have to remove it, but you can remove things from your menu if you hardly ever use them by right clicking on your menu and selecting 'edit menus'

---

### Post by laurielegit on 2008-10-23
> **niyonk said:**
> Evolution is the first thing i remove after a fresh install. And it removes fine except the icon in  the menu

Try synaptic
or
sudo apt-get remove evolution evolution-common

Good Luck!

Thanks! That worked perfectly for me :)

---

### Post by niyonk on 2008-10-23
> **aeiah said:**
> but you can remove things from your menu if you hardly ever use them by right clicking on your menu and selecting 'edit menus'

Do you have any ideas as to why it does not remove the menu entry?
Although not a big deal, it's a pain. :(

---

### Post by rwin on 2008-10-23
Thanks for all of your input on this, especially aeiah. That's the kind of information I was looking for.

> ubuntu-desktop is a metapackage. a package of packages.

I guess it was more of a "clean-up"-idea. I can deal with just removing it from the menu, though. Instead I learned about another issue.

So thanks!

---

