---
title: "HOWTO: Change GDM Login Screen"
date: 2005-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2005-01-06
Search for and download a GNOME GDM login screen.

Computer -> System Configuration -> Login Screen Setup -> Graphical Greeter -> Install New Theme -> xxxx.tar.gz -> Install -> Click on new theme -> Close

[http://www.customize.org/list/ggdm](http://www.customize.org/list/ggdm)
[http://art.gnome.org/themes/gdm_greeter/](http://art.gnome.org/themes/gdm_greeter/)
[http://www.gnome-look.org/index.php?xcontentmode=150](http://www.gnome-look.org/index.php?xcontentmode=150)

---

### Post by Uuranor on 2005-01-06
[http://www.gnome-look.org/index.php?xcontentmode=150](http://www.gnome-look.org/index.php?xcontentmode=150)

---

### Post by Yver on 2007-01-29
In Ubuntu 6.10 Edgy, GO to System>Administration>Login Window

---

### Post by ingo on 2007-02-17
anyway of doing this on the command line? I've got Kubuntu but for reason best known to me use gdm :)

---

### Post by mochiko on 2008-06-03
hello, i'm super-new to ubuntu, and i have the hardy heron edition thingy. 

i used to use gutsy gibbon, and i know how to get gdm themes from the internet and install them in the login window. 

i'm quite frustrated with this problem that i'm facing - although i click the +Add Item button and the login theme is shown in the list AND i select the theme that i want, it doesn't actually change. 

It kept showing this theme (like the ubuntu beige theme). i forgot the name because i removed the item, making it permanently lost. i thought this would solve the problem. but then when i logged out and came back, a window came up and said, "the ubuntu (whatever the name is) theme cannot be found" and it showed a completely different theme than i had selected still!

i really don't know what to do. i don't believe it's for a specific theme, but it doesn't switch to any theme. if anyone has any idea on how to deal with this, i would greatly appreciate the help.

---

### Post by d3v1150m471c on 2009-12-18
I was having the exact same problem. Easy solution, put this in your terminal :

gksudo -u gdm dbus-launch gnome-appearance-properties

That will bring you to your typical background selection but don't be alarmed, select the new login background and close it as normal and enjoy your new login screen background :). 

If you want to add a custom picture to this you may add them just as you would add your typical gnome backgrounds through the menu that opens with the above command. If it rejects it, make sure you format and size the picture like the others in the menu. You can do this with GIMP. Good luck!

---

### Post by biggles1000 on 2010-11-27
works well, but how do I stop the appearance window popping up every time (I used the gksudo -u gdm dbus-launch gnome-appearance-properties command) I switch my laptop on? (Ubuntu 10.10)

---

### Post by deviltalk on 2010-12-12
i tried that too and all i get is:

No protocol specified
Cannot open display: 

(gnome-appearance-properties:2060): Gtk-WARNING **: cannot open display: :0.0

---

### Post by MetalMusicAddict on 2010-12-25
> **deviltalk said:**
> i tried that too and all i get is:

No protocol specified
Cannot open display: 

(gnome-appearance-properties:2060): Gtk-WARNING **: cannot open display: :0.0

Yep. Doesn't seem to work anymore. :(

---

### Post by Amarokus on 2011-02-21
So far, the best solution that I came up with is to install old GDM from sources.
Here you can find the package: [https://launchpad.net/ubuntu/jaunty/+source/gdm](https://launchpad.net/ubuntu/jaunty/+source/gdm), i.e.[COLOR=Black] gdm_2.20.10.orig.tar.gz
To install on top of that new current GDM you should write: ./configure --prefix=/usr/
Worked perfectly for me.
[/COLOR]

---

### Post by Amarokus on 2011-02-21
I posted the procedure what I did on my [blog]("http://max.oleh.net/blog//index.php/techBlog/how-to-change-gdm-themes-in-ubuntu-maverick").

---

### Post by MarkoCro on 2011-03-04
I have found solution for changing GDM theme, fonts and wallpaper and many other Ubuntu related guides here:

[http://www.techytalk.info/ubuntu-debian-gdm-login-screen-theme-wallpaper/]("http://www.techytalk.info/ubuntu-debian-gdm-login-screen-theme-wallpaper/")

---

### Post by debd on 2011-03-04
drs305, i really dont have a word to thank you..I was damn fustrated wit al the methods posted in diff threads and then I came across ur's. the purge and reinstall method(for diff boot prtition)  just restored everything.

thanks a lot man.

---

### Post by shubhamearth on 2011-05-03
i am using Ubuntu 10.04 and in it i am not finding the option of changing the login screen......the system->administration->login screen does not have any option to change the login theme:confused:

---

