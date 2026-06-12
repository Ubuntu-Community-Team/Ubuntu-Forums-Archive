---
title: "HOWTO: Install Xfce Themes"
date: 2006-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Aldoliel on 2006-08-01
This is a guide to installing Xfce Themes in Xubuntu 6.06.

Themes are *normally* distributed in .tar.gz, .tar.bz2 or .zip archives.

**Using The GUI**
[LIST=1]
[*]Download the theme 
[*]Extract the theme into a folder using Xarchiver (or whatever archiver you use) 
[*]Then copy that folder into *~/.themes* (create this directory if it doesn't exist) 
[/LIST]

**Using the Terminal**
[LIST=1]
[*]Download the theme 
[*]```
cd /.themes 
```
[*]```
tar xzvpf yourtheme.tar.gz
``` (or *unzip yourtheme.zip*) 
[/LIST]

**Alternative Terminal Method**
[LIST=1]
[*]Download the theme to your home directory
[*]```
tar xzvpf yourtheme.tar.gz
``` (or *unzip yourtheme.zip*)
[*]```
cp /yourtheme/ /.themes 
```
[/LIST]

You *should* now see the theme in User Interface Settings!

**Troubleshooting**
[LIST=1]
[*]Make sure that the theme is extracted into a directory, and that it's all there. 
[*]Maybe try moving it to /usr/share/themes/ using sudo. This is useful if you want other users and system utils (ones that ask for a password) to be able to use the theme too.
[/LIST]

Permission is hereby granted to copy, edit and distribute this howto without restriction. [http://aldoliel.infogami.com/Xfce_themes](http://aldoliel.infogami.com/Xfce_themes)

---

### Post by dolby on 2006-08-02
alternative way

Download the theme

```
 cd /usr/share/themes
sudo cp /pathtodownloadedtheme/yourtheme.tar.gz /usr/share/themes
sudo tar xzvf yourtheme.tar.gz
sudo rm -rf yourtheme.tar.gz 
```

You should now see the theme in User Interface Settings

---

### Post by Aldoliel on 2006-08-04
Thanks, that method *should* have the same result as the second troubleshooting method

---

### Post by Psquared on 2006-09-17
I've been looking for this thread. I've installed a couple of themes using this method but they don't show up. In fact, the themes that are installed in /usr/share/themes do not show up in "User Interface Settings."

I have the directory /.themes as well, but there is nothing there at all. Where is Xfce looking for themes?

---

### Post by Neo40 on 2006-09-17
And what is the way to install mouse themes? I'm interresting to install this one: [http://www.xfce-look.org/content/show.php?content=32627](http://www.xfce-look.org/content/show.php?content=32627)
but I can't figure out to install it correctly...Can you help me?
Thanks

---

### Post by Do0odz on 2007-07-06
I cant handle tar.gz themes !!! can anyone help me !! plz :( I really want to change my theme

---

### Post by mega386 on 2007-07-14
i have also tried both methods and its not showing up in the preferences.  HELP!!

---

### Post by dedhandi on 2007-08-15
Yeah I'm still having real difficulty. Trying to install a Murrine theme, have installed it into the /usr/share/themes directory but it hasn't shown in either User Interface Settings or Window Manager Settings. Can such a simple thing really be so difficult?

---

### Post by lexinc on 2007-11-29
[http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-6.06-trouble](http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-6.06-trouble)-installing-themes-449229/

check out this link everyone. All you have to do is go to windows manager settings instead. It's really great.

---

### Post by BLTicklemonster on 2007-12-25
WTF? Isn't there an easier way to do themes in xfce? LIke can't I just use a folder for them in my home directory like gnome or something?

---

### Post by Steveway on 2007-12-25
Why even a tutorial? It's so easy!
Just unpack them and throw them into ~/.themes/
Done!
Also, why did you use sudo dolby? That is not needed and is a potential risk. 
So keep in mind kids: Everytime you missuse sudo, god kills a kitten.

---

### Post by BLTicklemonster on 2007-12-25
Okay, I put them in 

/home/bill/.themes

and they aren't - well, tell me this, I've seen two different places where I could change what I'd call themes, where do you go to change themes? 

Applications>Settings>Settings Manager

Both User Interface and Window manager allow me different choices in how my themes look. I have no idea why, but there's two places to do this. Is there a third place?

---

### Post by juxtaposed on 2008-01-12
Don't know if this was mentioned, but I had to have it like this:

~/.themes/THEMENAME/xfwm4/

For an XFWM theme.

---

### Post by Labot2001 on 2008-03-04
Hey,

I'm a total n00b at Xfce, xubuntu, and Linux in general X_x

I tried dragging the extracted xfce theme folder to the destination usr/shared/themes but it wouldn't let me =/ Any troubleshooting tips? (other than those which you already mentioned; I don't understand what you mean by "Code" lol)

---

### Post by KuruOujou on 2008-04-05
As much as I hate druging up an old thread, I thought I should sortof help redeem myself for that stupid post I made a few years ago on the wireless, and give back to the community...not that I wouldn't do that anyway.


So yeah, to Labot2001: When you drag and drop with Thunar, it will say you don't have permissions if you are just opening a folder. You have a few options:
1) Try putting the theme in ~/.themes (where ~ is your home folder, like for me, it's /home/kuroshi, so the whole directory would be /home/kuroshi/.themes) - The dot is important, most programs look for dots at the beginning of files/folders for configuration files, and the terminal and thunar both see files/folders with dots in front of them as hidden.

2) Open a terminal and type "sudo thunar" without the quotes. This will open thunar as root (and give you a nifty little root warning), so you can drag and drop the file into /usr/share/themes, as long as you navigate there in the window you opened as root. (I say that incase you have one open that isn't root that you are copying from, and the other window open that is root that you are copying too.)

3) Finally, you can go into the terminal and type something like this (once again without the quotes) "sudo cp -R /directory/to/downloaded/theme /usr/share/themes". This will do basically the same as above, but without the pretty graphics.


As for the rest of you having problems, if it's a GTK theme, A) Be sure you have gtk2-engine-xfce installed (I think that's the name of it), and B) Check to see where you're looking. They don't show up in window manager. They show up in User Interface Preferences.

---

### Post by acy76 on 2008-07-30
For those who've come across this thread during a search, I've found the following difference when installing themes in Xubuntu 8.04.1:

The instructions above are correct, except that the place to choose a new theme is 'xfce settings manager -> window manager' (not user interface as suggested).

Hope this is of some help.

---

### Post by mister_p_1998 on 2009-02-25
I did by going into settings manager and then User Interface (After first having copied the themes to /usr/share/themes (Unpacked)

Steve

---

### Post by Rofko on 2009-03-11
I agree with mister_p_1998's solution as the easiest. Seems overcomplex though. There are too many steps compared to the drag and drop method in, say, Gnome.

---

