---
title: "Make Gnome apps look good in KDE and how to Autostart programs in KDE."
date: 2005-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by landotter on 2005-03-10
I've been playing with KDE this week and found my Gnome apps looked awful, so I need to fire up the gnome settings daemon automatically when I logged into KDE.

I also wanted to autostart gnome-volume-manager on KDE login so that it would manage my usb storage so:

To start gnome-volume-manager and gnome-settings-daemon in KDE is to symlink the executables from /usr/bin to ~.kde/Autostart.
 
 Do this by dragging and dropping within Konqueror and choosing "link".

To make Gnome apps blend with KDE apps visually I used Plastik for KDE and Clearlooks with Gnome, and themed KDE's palatte to match:

[img]http://photos7.flickr.com/6269099_6271717ca1_o.jpg[/img]


close enough for me. ;)

---

### Post by bored2k on 2005-03-10
[QUOTE=landotter]I've been playing with KDE this week and found my Gnome apps looked awful, so I need to fire up the gnome settings daemon automatically when I logged into KDE.

I also wanted to autostart gnome-volume-manager on KDE login so that it would manage my usb storage so:

To start gnome-volume-manager and gnome-settings-daemon in KDE is to symlink the executables from /usr/bin to ~.kde/Autostart.
 
 Do this by dragging and dropping within Konqueror and choosing "link".

To make Gnome apps blend with KDE apps visually I used Plastik for KDE and Clearlooks with Gnome, and themed KDE's palatte to match:

[img]http://photos7.flickr.com/6269099_6271717ca1_o.jpg[/img]


close enough for me. ;)[/QUOTE]
 Pretty close (y).

Oh the old kcontrol ... boy was it easy2use ... but no! *slaps himself* I don't like KDE :@

---

### Post by landotter on 2005-03-10
[QUOTE=bored2k]Pretty close (y).

Oh the old kcontrol ... boy was it easy2use ... but no! *slaps himself* I don't like KDE :@[/QUOTE]
 LOL, Gnome and KDE aren't oil and water! 

KDE's really got some underlying slap-your-forehead type issues pretty much sorted: nice file dialog, printing, modem configuration, font installation, and CD Burning.

Yeah, some of the UI's a bloody mess and that really bothers me, on the other hand the developers aren't so scared of violating a HIG code that they withhold tools.

I use both. 

Mmmmm. Knome. :P

---

### Post by bored2k on 2005-03-10
[QUOTE=landotter]Mmmmm. Knome. :P[/QUOTE]


Lol I wish there was such thing ... but NO *double slap*.

You know what would be Awsome? "G3B" ... Yesterday I broke my own rules and installed K3B... My hands got shaky when I had to press enter to "install kdelibs?" :( . Now I feel like my Ubuntu got a 30% speed downgrade to punish me ... pleaseee someone make a good GNOME only burning app quick before i lose it !

---

### Post by Quest-Master on 2005-03-10
[QUOTE=bored2k]Lol I wish there was such thing ... but NO *double slap*.

You know what would be Awsome? "G3B" ... Yesterday I broke my own rules and installed K3B... My hands got shaky when I had to press enter to "install kdelibs?" :( . Now I feel like my Ubuntu got a 30% speed downgrade to punish me ... pleaseee someone make a good GNOME only burning app quick before i lose it ![/QUOTE]
 Why not Gnomebaker?

---

### Post by bored2k on 2005-03-10
[QUOTE=Quest-Master]Why not Gnomebaker?[/QUOTE]
 I gave it a spin. It's cute. Other than that, I don't like it. It did not erase my DVD-RW's when everything else did [including k3b]. And it's not nearly as complete as K3B. I love the broad K3B configuration windows, all the info it gives to the user, the fact that it can encode videos directly using transcode, its plugin, I just "dig it".

I also tried Graveman but I would rather use GnomeBaker instead.

---

### Post by landotter on 2005-03-10
I use Nautilus for data CD--it's awesome for that, but hey--I've got 5 gigs of / room before I get to /home--installing some kde/qt libs to use one of the best open source programs such as k3b is worth it.

---

### Post by bored2k on 2005-03-10
[QUOTE=landotter]I use Nautilus for data CD--it's awesome for that, but hey--I've got 5 gigs of / room before I get to /home--installing some kde/qt libs to use one of the best open source programs such as k3b is worth it.[/QUOTE]
 If I *EVER* install and dual-boot Kubuntu I would whipe it clean , only leaving K3B . This is a lot better than switching to Nero for some sureshot burning ...

---

### Post by dr.drake on 2006-03-02
I was looking for a while for a simple explanation (a noob explanation) how to autostart applications in KDE, but only somewhere hidden in a thread with a different name I found it. since this thread has the right name, I'll copy-paste **jpmontalbo**'s post and edit it a bit:

This is how I make applications start automatically when you login. 

1. Go to your **home** folder 
2. Click on **View** at the top and then click on **Show Hidden Files** you will now see hidden directories
3. go to **.kde** folder. 
4. go to **autostart** folder 
5. click on the **K-menu** button, bottom left on the screen
6. drag application into the autostart folder
7. chose the **Link Here** option

done

---

### Post by biga805 on 2009-11-16
> **dr.drake said:**
> 

This is how I make applications start automatically when you login. 

1. Go to your **home** folder 
2. Click on **View** at the top and then click on **Show Hidden Files** you will now see hidden directories
3. go to **.kde** folder. 
4. go to **autostart** folder 
5. click on the **K-menu** button, bottom left on the screen
6. drag application into the autostart folder
7. chose the **Link Here** option

done

Excellent... This was exactly what I was looking for.. Thanks for digging, lol

---

