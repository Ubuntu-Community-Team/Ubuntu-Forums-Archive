---
title: "Add new Items to Nautilus right-click menu and Run a Application."
date: 2009-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by valex on 2009-06-19
As you already know Nautilus is the main file manager in Gnome. Do you know that nautilus is highly customizable File manager? well. now I am going to discuss a good customizable property in nautilus. I already said about it in topic which is add new menu items to nautilus right click menu.

First of all, you want to [download]("http://www.grumz.net/index.php?q=taxonomy/term/6/9") a small software call "[Nautilus Action]("http://www.grumz.net/index.php?q=node/8")". ubuntu users can download via the software repositories using follow command.

[CENTER][COLOR="Red"]*sudo apt-get install nautilus-actions*[/COLOR][/CENTER]


others can download source package or rpm packages as your wish.

If you finished download and install then you can find it on [COLOR="Red"]**System->Preferences->Nautilus Action Configuration**[/COLOR].

Now you can see it's main window like this.

<table style="width:auto;"><tr><td><a href="http://picasaweb.google.com/lh/photo/muvDUVrkU-CnKUSnmPW0SA?authkey=Gv1sRgCM7q1J6Y1uL8HQ&feat=embedwebsite"><img src="http://lh5.ggpht.com/_2nF7-fq2uKw/SjuctMRR-BI/AAAAAAAAAHM/VEiEooI590M/s144/Screenshotedited2.jpg" /></a></td></tr><tr><td style="font-family:arial,sans-serif; font-size:11px; text-align:right">From <a href="http://picasaweb.google.com/janith3000/NautilusAction?authkey=Gv1sRgCM7q1J6Y1uL8HQ&feat=embedwebsite">Nautilus Action</a></td></tr></table>


To add new menu item for Nautilus right-click menu click "Add" button. when you get "Add New Item" window as follows add these details call,

Label: menu item name which will be appear in Nautilus right-click menu.
Tooltip: tooltip of the menu item.
icon: which is own by menu item. in this I selected "gtk-help" icon. but you can select your own icon. but remember Large icons will be freeze Nautilus.


<table style="width:auto;"><tr><td><a href="http://picasaweb.google.com/lh/photo/aXInsQVHf3TsONbIV8vR5A?authkey=Gv1sRgCM7q1J6Y1uL8HQ&feat=embedwebsite"><img src="http://lh6.ggpht.com/_2nF7-fq2uKw/SjucwtyQKbI/AAAAAAAAAHQ/wMM_Xfw2GzE/s144/Screenshot-1edited2.jpg" /></a></td></tr><tr><td style="font-family:arial,sans-serif; font-size:11px; text-align:right">From <a href="http://picasaweb.google.com/janith3000/NautilusAction?authkey=Gv1sRgCM7q1J6Y1uL8HQ&feat=embedwebsite">Nautilus Action</a></td></tr></table>


hmm... now we want to set path of our destination. I use a Gloobus(if you don't know about gloobus read [this]("http://linuxhug.blogspot.com/2009/06/gloobus-future-of-file-managers.html")) as a example. Add new profile or edit default profile call "Main". set it's name Glooobus or your favourite. but I still set it as Main. now click Edit.

fill folow details.
path: /usr/bin/gloobus this is a location of gloobus main binary files/core.
Parameters: %d

<table style="width:auto;"><tr><td><a href="http://picasaweb.google.com/lh/photo/xtkFXxnY5zzN7THBUuw7QQ?authkey=Gv1sRgCM7q1J6Y1uL8HQ&feat=embedwebsite"><img src="http://lh5.ggpht.com/_2nF7-fq2uKw/Sjuc2BHJA_I/AAAAAAAAAHU/U558PA294NI/s144/Screenshot-2edited2.jpg" /></a></td></tr><tr><td style="font-family:arial,sans-serif; font-size:11px; text-align:right">From <a href="http://picasaweb.google.com/janith3000/NautilusAction?authkey=Gv1sRgCM7q1J6Y1uL8HQ&feat=embedwebsite">Nautilus Action</a></td></tr></table>


now your configuration is completed. see right click on a item in nautilus. did you get like this?

<table style="width:auto;"><tr><td><a href="http://picasaweb.google.com/lh/photo/5QkjUxahbyJN722G1l9Gdw?authkey=Gv1sRgCM7q1J6Y1uL8HQ&feat=embedwebsite"><img src="http://lh3.ggpht.com/_2nF7-fq2uKw/Sjuc_jk1TyI/AAAAAAAAAHY/DChH-oSsoGc/s144/a8edited2.jpg" /></a></td></tr><tr><td style="font-family:arial,sans-serif; font-size:11px; text-align:right">From <a href="http://picasaweb.google.com/janith3000/NautilusAction?authkey=Gv1sRgCM7q1J6Y1uL8HQ&feat=embedwebsite">Nautilus Action</a></td></tr></table>


This tutorial has posted in my [blog]("http://linuxhug.blogspot.com/").

---

