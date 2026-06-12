---
title: "[SOLVED] Which apps to use on an old system?"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by bhadotia on 2008-08-08
We just installed ubuntu 7.10 on a friend's old laptop (256mb RAM and intel celeron M processor). Obviously the system is very slow on GNOME. I tried installing XFCE (xubuntu-desktop package), but still the desktop speed is not up to the mark. I also tried installing fluxbox(which was smoking fast as its a window-manager and not a desktop-manager like GNOME or XFCE), but just could not figure my way out through its cofiguration and usage.  Tried some google search (at which  I  am not very good when it comes to computers etc.) but to no avail. So at last I have come here asking for some kind help.

I would be very grateful if some one could point me to some informative pages on what are the lightweight apps that can be used a substitutes for the standard ubuntu apps such as firefox, ryhtmbox, totem etc. 
Also , if some information on how get fluxbox (or any other window manager) working on ubutnu can be given , I would appreciate it very much. Fluxbuntu ,as I said, was very fast . I read about it in a linux magazine article . But ,in that article, the explanation on how to configure fluxbox was very brief - so that I was lost.

Many thanks in advance.

---

### Post by snowpine on 2008-08-08
> **bhadotia said:**
> We just installed ubuntu 7.10 on a friend's old laptop (256mb RAM and intel celeron M processor). Obviously the system is very slow on GNOME. I tried installing XFCE (xubuntu-desktop package), but still the desktop speed is not up to the mark. I also tried installing fluxbox(which was smoking fast as its a window-manager and not a desktop-manager like GNOME or XFCE), but just could not figure my way out through its cofiguration and usage.  Tried some google search (at which  I  am not very good when it comes to computers etc.) but to no avail. So at last I have come here asking for some kind help.

I would be very grateful if some one could point me to some informative pages on what are the lightweight apps that can be used a substitutes for the standard ubuntu apps such as firefox, ryhtmbox, totem etc. 
Also , if some information on how get fluxbox (or any other window manager) working on ubutnu can be given , I would appreciate it very much. Fluxbuntu ,as I said, was very fast . I read about it in a linux magazine article . But ,in that article, the explanation on how to configure fluxbox was very brief - so that I was lost.

Many thanks in advance.

Hi Bhadotia, I am a big fan of Fluxbox/Fluxbuntu. The difference between them is that Fluxbox (as you know) is a windows manager you can install on top of your existing Ubuntu install, whereas Fluxbuntu is a complete "distro" with a lightweight application suite and pre-configured Fluxbox (wallpaper, desktop icons, custom menus, auto-mounting of USB drives, etc.) but unfortunately you must install Fluxbuntu fresh. I highly recommend it if you want to experience what is possible using Fluxbox. You can read more of my thoughts on Fluxbuntu in this thread: [http://ubuntuforums.org/showthread.php?t=855596](http://ubuntuforums.org/showthread.php?t=855596)

Now, to answer your original question. Here are the lightweight applications that Fluxbuntu includes: rox file manager, kazehakase web browser, abiword word processor, gnumeric spreadsheet, claws email, xmms music player, leafpad text editor, etc. You can experiment with these applications from your existing Ubuntu installation, test them side by side with the default applications to see if you notice an improvement in speed. Good luck!

---

### Post by swisscow on 2008-08-08
Email, use Claws. Just swapped to it from thunderbird. Thunderbird opened in over 10 seconds, claws just 3 :-)

---

### Post by snowpine on 2008-08-08
ps Since Fluxbuntu does not have a Live CD and cannot be installed on the same partition as an existing Ubuntu system, if you want to check it out, my suggestion is to test it on a Virtual Machine on a faster computer, or on a separate partition. I like it, but it is not for everyone! :)

---

### Post by tiachopvutru on 2008-08-08
Look at the links of number 13 and 14 on here: [http://ubuntuapplications.blogspot.com/2007/08/top-26-ubuntu-application-sources.html]("http://ubuntuapplications.blogspot.com/2007/08/top-26-ubuntu-application-sources.html")

I found it googling "Ubuntu application low" (it's the first result) so I can't really guarantee that the suggestions are good, but it might warrants a look.

---

### Post by linkmaster03 on 2008-08-08
IceWM is another very light WM. You can also try BlackBox, which is what Flux is based off of.

'xfe' is a very light file browser, and aterm is much easier on resources than xterm or gnome-terminal. Epiphany is worth giving a try for a web browser.

---

### Post by snowpine on 2008-08-08
By the way, there are some real Fluxbox experts here on the forums (I'm not quite there yet!) and here is a good thread to educate yourself: [http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

---

### Post by mikjp on 2008-08-08
Openbox is another lightweight window manager and [IceWM](http://www.icewm.org/) is another one. Check Gentoo wiki about [configuring](http://gentoo-wiki.com/HOWTO_Openbox) Openbox.

For lightweight word processing, use Abiword (or Lyx). Opera might be lighter than Firefox. I have listed even lighter browsers in my blog posting [here](http://lightlinux.blogspot.com/2008/08/lightest-www-browsers-for-linux.html). 

Remember not to use Gnome apps with a lightweight window manager, they will spoil the lightness by loading all kinds of libraries. In addition, you should consider disabling unneeded services that get started while the system boots. Do you need e.g. Bluetooth? Or seven virtual terminals? The unnecessary services take up memory and CPU time. Disable them and you get a faster system. More info [here](http://www.ubuntugeek.com/sysvconfig-utility-for-configuring-init-script-links.html).

If you are ready to try another distro, give [Zenwalk](http://www.zenwalk.org) a try. Or some other distro mentioned [here](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html).

Greetings,

mikko

---

### Post by mali2297 on 2008-08-08
Some additional light-weight alternatives:

xpdf (to view pdfs)
feh (to view images)
mtpaint (to draw images)

---

### Post by bhadotia on 2008-08-08
> **snowpine said:**
> By the way, there are some real Fluxbox experts here on the forums (I'm not quite there yet!) and here is a good thread to educate yourself: [http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

> mikjp 	 		**Re: Which apps to use on an old system?**
 		Openbox is another lightweight window manager and [IceWM]("http://www.icewm.org/") is another one. Check Gentoo wiki about [configuring]("http://gentoo-wiki.com/HOWTO_Openbox") Openbox.

For lightweight word processing, use Abiword (or Lyx). Opera might be lighter than Firefox. I have listed even lighter browsers in my blog posting [here]("http://lightlinux.blogspot.com/2008/08/lightest-www-browsers-for-linux.html"). 

Remember not to use Gnome apps with a lightweight window manager, they will spoil the lightness by loading all kinds of libraries. In addition, you should consider disabling unneeded services that get started while the system boots. Do you need e.g. Bluetooth? Or seven virtual terminals? The unnecessary services take up memory and CPU time. Disable them and you get a faster system. More info [here]("http://www.ubuntugeek.com/sysvconfig-utility-for-configuring-init-script-links.html").

If you are ready to try another distro, give [Zenwalk]("http://www.zenwalk.org/") a try. Or some other distro mentioned [here]("http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html").

Greetings,

mikko 	


Thanks for the useful links guys:)
After posting this thread I did (and am still doing) some rigorous work on fluxbox and its starting to pay off!

Thanks for all the help:)

---

### Post by rossjman1 on 2008-08-08
XFCE should still run at a decent speed. Have you tried disabling services like Bluetooth, Tracker, and Printing if you don't use them? To disable them go to System > Administration > Services.

---

### Post by bhadotia on 2008-08-08
> **rossjman1 said:**
> XFCE should still run at a decent speed. Have you tried disabling services like Bluetooth, Tracker, and Printing if you don't use them? To disable them go to System > Administration > Services.

Yes , XFCE is certainly faster than GNOME but I said the speed is not up to the mark i.e., upto my expectation. Still, I think my friend I now much happy with fluxbox:)

---

