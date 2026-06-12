---
title: "Howto: Install Chandler (Feature-filled PIM)"
date: 2007-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Espreon on 2007-11-29
OK, if you don't know what Chandler it is a PIM (personal information manager) that is chock full of features.

 If you don't know what a PIM is click this Wikipedia link: [http://en.wikipedia.org/wiki/Personal_information_managerde](http://en.wikipedia.org/wiki/Personal_information_managerde) will 

This guide will work on an install of Ubuntu (7.10) and I think 6.06 - 7.04 as well. But I am not sure about K/Xubuntu...

OK now lets get on to the installation, this app takes about 100-200 MB of space:

Remember all the commands that have "yourhome" in it replace "yourhome" with the name of your home directory

1. First fire up the terminal

2. Enter this in the terminal

```

sudo wget http://downloads.osafoundation.org/chandler/releases/0.7.2/Chandler_linux_0.7.2.tar.gz -O /opt/chandler.tar.gz

```

3. Enter this in the terminal and browser to /opt and extract chandler.tar.gz

```

sudo nautilus

```

Then rename the folder that was extracted to: chandler

4. Now lets make a Menu entry:

```

alacarte

```

In the Office Catagory make a new menu item and for the name put in Chandler and for the command put in: /opt/chandler/chandler
For the icon browse to /opt/chandler/Chandler.egg-info/resources/icons
and pick an icon.

5. Launch and enjoy!

To uninstall:

1. Fire up the terminal and enter this command:

```

sudo rm -r /opt/chandler

```

2. Delete the menu entry

And your done...

---

### Post by maphew on 2008-08-12
Chandler Desktop is now at version 1.0, so don't use the wget link above.Canonical download page is [http://chandlerproject.org/download](http://chandlerproject.org/download). Revised steps 1,2,3:
```

cd /opt
sudo wget -c http://downloads.osafoundation.org/chandler/releases/latest/Chandler_linux_1.0.tar.gz
sudo tar zxvf Chandler_linux_1.0.tar.gz
sudo mv Chandler_linux_1.0/ chandler

#optionally, remove downloaded archive:
sudo rm Chandler_linux_1.0.tar.gz 

```

---

### Post by dimeotane on 2008-12-03
Currently Chandlerproject.org provides the deb for v1.02

[http://downloads.osafoundation.org/chandler/releases/latest/Chandler_linux_1.0.2-1_i386.deb](http://downloads.osafoundation.org/chandler/releases/latest/Chandler_linux_1.0.2-1_i386.deb)

however it has a dependency issue on my Hardy Heron, asking for "libicu36"
which can be downloaded from here:

[http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb)

it didn't add an icon to the ubuntu menu, so I'll look into that next.
i ran it with ALT-F2 chandler

---

### Post by hokage13 on 2009-03-11
I have just installed Chandler, and it seems like a useful program.  However, the fonts are really hard to see...its in light grey.  Is there a way to change the font color?

I am using Ubuntu 8.10 the dark theme and I tried changing back to the default theme but still the font color is hard to read :(

---

### Post by scathlock on 2010-08-13
How to run this s**t on Karmic?

---

