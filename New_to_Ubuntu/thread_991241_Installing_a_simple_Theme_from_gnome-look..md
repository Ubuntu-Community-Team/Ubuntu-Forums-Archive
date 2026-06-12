---
title: "Installing a simple Theme from gnome-look."
date: 2008-11-23
forum: New to Ubuntu
---

### Post by fredscripts on 2008-11-23
Hi!

I'm trying to install this GTK theme:

[http://www.gnome-look.org/content/show.php/Overglossed?content=74813](http://www.gnome-look.org/content/show.php/Overglossed?content=74813)

All right, after following the instruccions that it says:


```
1.Download the file to your desktop
2.Right click the file and select extract here
3.open a terminal and run this command:
sudo cp -r $HOME/Desktop/Overglossed /usr/share/themes

4.Open the theme manager, you can now
see the Overglossed theme as a theme,
when you click on it , it suggests
taners amazing wallpaper he made for this theme!!
click apply to apply the wallpaper!
```

A message appears telling me that I need the black-white 2 style icons package to install it properly.

No problem then, I go to the link the author says:

[http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619](http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619)

I download the tar file. Extract it and move it into /usr/share/icons. I restart.

OK, why it isn't working now? (same message that I need the black-white style when trying to set that theme).




Another issue, I installed this usplash screen in order not to have the classical Ubuntu loading bar while loading the system at start up:

[http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)

Of course I chose the Stable download.

I tried to follow the installation howto:

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

but I found that there should be an easy way, so I installed the startupmanager (sudo apt-get install startupmanager), and then choose Appearance, manage usplash themes ... and chose the .so file that I found after extracting the usplash tarball.

OK, after rebooting, any kind of usplash appears, only the kernel with messages like ...

Setting hardware ..................... [ OK ]
Configuring hardware ..................[ OK  ]

So, what should I do to get a simple usplash working?

Thanks!!!!

---

### Post by fooman on 2008-11-23
download the tar.gz file to your desktop.

go to system > preferences > appearance > theme tab

drag and drop the tar.gz file into the appearance preferences box with the other pre-installed themes

you should see a message saying that the theme installed correctly...choose "overglossed" theme from the list.

---

### Post by fredscripts on 2008-11-23
Thanks fooman, but I already did that, please read the entire post to see my exact problem :) the problem is in installing the GNOME Icons black-and-white 2 Style. And the other problem is installing a usplash theme.


I cannot understand why there isn't executable files to install themes  / usplashes  / icons...I really hate to download a tarball and then cheking HOW-TO's to install them and most of them then fail at installing.

---

### Post by fooman on 2008-11-23
icon themes install the same way.

download the black_white_2_style file to your desktop.  right-click on it and choose "extract here"

open the newly created "black-white 2 style" folder.

in there will be a file called black-white_2-style.tar.gz

drag & drop that into the appearance preferences box.

---

### Post by fredscripts on 2008-11-23
Oh thanks man it worked, but now another message appears saying:

This theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed.

What should I do?

---

### Post by Tom--d on 2008-11-23
Just forget the message.

Just click on Customize.

---

### Post by fooman on 2008-11-23
you could ignore it if everything looks/works ok,  or you can install gtk2-engines-ubuntulooks from synaptic or in a terminal:

```
sudo apt-get install gtk2-engines-ubuntulooks
```

---

### Post by fredscripts on 2008-11-23
I'm attaching a screenshot to show the problem.

I sudo apt-get install ubuntulooks in order to get rid of that message.

Now another (yes, yet another...) message appears telling me that I have not installed the GTK+ theme engine!!!

which package is that?

Check how the panel of the bottom isn't properly loaded (it is cut and the left icons are bad structured within the panel).

---

### Post by fredscripts on 2008-11-23
> **fooman said:**
> you could ignore it if everything looks/works ok,  or you can install gtk2-engines-ubuntulooks from synaptic or in a terminal:

```
sudo apt-get install gtk2-engines-ubuntulooks
```

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Thanks for your help, but still cannot get that theme working as you can see in the previous screenshot :(

---

### Post by fredscripts on 2008-11-24
> **fredscripts said:**
> I'm attaching a screenshot to show the problem.

I sudo apt-get install ubuntulooks in order to get rid of that message.

Now another (yes, yet another...) message appears telling me that I have not installed the GTK+ theme engine!!!

which package is that?

Check how the panel of the bottom isn't properly loaded (it is cut and the left icons are bad structured within the panel).


Please help with it...bet I'm not the first person that try to install a simple theme :(

---

### Post by fredscripts on 2008-11-24
Anyone? at least with the usplash screen problem...:(

---

### Post by fredscripts on 2008-11-25
I'm sorry for bumping again but...one of the reasons I switched to Ubuntu is because of the freedom of customizing the environment. This is the first time I just want to change the theme and the usplash screen, I'm really dissapointed :(

---

### Post by MikeDK on 2008-11-27
one thing is, that when installing ubuntulooks engine it removes ubuntu-desktop,

isnt this surposed to be installed for the desktop to work as it should???

Kind Regards MikeDK

---

