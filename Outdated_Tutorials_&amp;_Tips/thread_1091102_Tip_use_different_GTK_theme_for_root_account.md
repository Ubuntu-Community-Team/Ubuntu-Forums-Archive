---
title: "Tip: use different GTK theme for root account"
date: 2009-03-09
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2009-03-09
In recent versions of Gnome, I have noticed that some graphical apps launched as root will inherit the regular user's theme. Personally, I use a separate GTK theme with the root account because I like to be reminded visually to be careful. If you would like to do this two, here's how.

Above all, you need administrative privileges. If you don't, then don't need to worry about root's theme. 

First we need to create a couple files. Open a terminal and enter this command:
```

sudo nano /root/.gtkrc-2.0
[code] 

Or if you want to do this graphically:
[code]
gksudo gedit /root/.gtkrc-2.0
```

This should bring up an empty file. Add this line and save the file:
```

include "/root/.gtkrc.mine"

```

Now we are going to edit the file we referenced in the first file:
```

sudo nano /root/.gtkrc.mine
  #  or
gksudo gedit /root/.gtkrc.mine

```

I prefer to use the Redmond theme for the root account. It's classic, simple, and probably way different from any theme I might be using for my regular apps. So, I added this line to root's .gtkrc.mine file:
```

include "/usr/share/themes/Redmond/gtk-2.0/gtkrc"

```

I also set root's icon theme to GNOME (because I hardly ever use those icons) by adding this line to the file:
```

gtk-icon-theme-name = "gnome"

```

I even set the font by adding this section:
```

style "schrift"
{
font_name = "Sans 9"
}
widget_class "*" style "schrift"

gtk-font-name = "Sans 9"

```

You can set this stuff to whatever you want, or leave some things out. urukrama has some helpful info about editing .gtkrc.mine files on his blog: [http://urukrama.wordpress.com/openbox-guide/#Gtkthemes](http://urukrama.wordpress.com/openbox-guide/#Gtkthemes)

If you have any problems following this let me know.

---

