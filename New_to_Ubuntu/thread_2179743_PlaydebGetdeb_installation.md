---
title: "Playdeb/Getdeb installation"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by Itiwid on 2013-10-09
Hi All,

Having just made the switch to Linux I have been keen to scratch the Xcom itch and have a go at UFO:AI. The problem I am having is that the only mode of accessing the game (on the website) is through Playdeb.

I have attempted to install both playdeb and getdeb from their respective websites. However, the playdeb installation ends with:

dpkg: error processing /tmp/filewdVveT.deb (--install):
 cannot access archive: Permission denied
Errors were encountered while processing:
 /tmp/filewdVveT.deb

and the getdeb with:

dpkg: error processing /tmp/fileyEVt3y.deb (--install):
 cannot access archive: Permission denied
Errors were encountered while processing:
 /tmp/fileyEVt3y.deb

I do not understand the alternative installation method suggested on the site as I cannot find "system-administration-sofware sources" 

Apologies if this query is better posted in leisure and gaming.

I'm running Lubuntu 12.04 32bit btw.

Thanks for any assistance.

---

### Post by newb85 on 2013-10-09
System>Administration>Software Sources is the way to get to the Software Sources dialog in a desktop environment with the standard Free Desktop menu structure, and LXDE is not one of those.  Try looking for Software Sources in the menus of the Lubuntu Software Center.

---

### Post by newb85 on 2013-10-09
On second thought, the easiest way to add the Playdeb software source is by running the following commands in a terminal:

```
sudo add-apt-repository "deb http://archive.getdeb.net/ubuntu precise-getdeb games"
sudo apt-get update
```

After that, you should be able to add ufoai from the Software Center.

Be advised, it is unwise to add sources you don't trust to your system, regardless of how you add them.

---

### Post by Itiwid on 2013-10-10
Thanks for the help. Ok...

I have run the suggestedscripts in terminal and  the computer certainly did something. Beyond the action in terminal however nothing obvious seems to have changed so i am unsure if it has been successful. The available games in software center remain unchanged ( although I did locate software sources - thanks :) ) Getdeb shows in software sources with an automatic key - do i need to do something with the GPG key? (hunted around for a keyhash on the website, couldn't find one)

I ran the script suggested on the website:

[COLOR=#CFA53E][FONT=monospace]**wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -**[/FONT][/COLOR]

when i ran update again it ended with:

E: GPG error: [http://archive.playdeb.net](http://archive.playdeb.net) precise-playdeb Release: The following signatures were invalid: NODATA 1 NODATA 2


I am still unable to access anything from the playdeb website - clicking on the link opens a window asking if i wish to proceed, on clicking yes all that happens is an additional chromium window pops up.

Any more help would be great, thanks

---

### Post by Itiwid on 2013-10-10
Hi all. Thanks for the help. :)

I discovered a discussion about lubuntu software centre not being compatible with playdeb and have reverted to installing through synaptic package manager without problems. 

Great first experience of community sup.port though. thanks.

G

---

### Post by newb85 on 2013-10-10
Copied and pasted the wget... line directly from your post, and it worked perfectly for me.  But then, I'm no Raring, not Precise.

Have you tried directly downloading the key?  Simply entering [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) in your browser address bar (or clicking that link) should start the download.  It will put a file getdeb-archive.key in your Downloads folder.  Then you can open it and see whether the key really has no data.

---

