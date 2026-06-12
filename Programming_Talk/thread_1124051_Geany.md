---
title: "Geany"
date: 2009-04-12
forum: Programming Talk
---

### Post by swappo1 on 2009-04-12
Hello,

I just insalled geany yet I don't have it listed under my applications menu on the tool bar.  The only way I can open it is through the terminal.  How do I get it into my Applications?  Also, how do I set it to use a hot key to open it?  I have gedit set to <ctrl><alt>g but I can't rember how I did it.  One more thing, the geany website lists the current release as .16 yet I have .13 how do I get the current version?  Thanks.

---

### Post by slavik on 2009-04-13
Applications -> Programming -> Geany

getdeb.net should have the latest version. I remember compiling mine. Jaunty has latest if you are feeling brave.

---

### Post by mltucker on 2009-04-13
Edit: 

Yeah, it would be easier to just get the .deb from getdeb.net.

Hi,

Are you running GNOME?

As for the most recent version, it looks like the most recent in the repository is 0.14-1.  If you run your updater it should update to this.  You can always run synaptic to check this out and update it.

If you want to use the most recent version, 0.16, you will have to build it from source.  

1. Download geany-0.16.tar.gz from

[http://download.geany.org/]("http://download.geany.org/")

2. Decompress it with

```

>> tar xvfz geany-0.16.tar.gz

```

3. Make sure you have the necessary dependencies.  What you need will depend on if you have already built programs from source.  You should have the GTK dependencies since you already installed it once.  I would try:

```

>> sudo apt-get install build-essential make automake libtool glib intltool

```

EDIT: corrected build-essentials->build-essential

(that's what I needed)

4. Run the autoconfig script:

```

>> cd geany-0.16
>> sudo ./autogen.sh

```

5. and finally build it

```

>> sudo make
>> sudo make install

```

It should work now.

---

### Post by mltucker on 2009-04-13
There is a menu editor in gnome that will let you put it in your Applications menu.  The simplest way is to create a launcher that runs the terminal command

```

>> geany

```

---

### Post by swappo1 on 2009-04-13
I ran menu editor in gnome and the programing menu is in italics(all others that show up are non-italics).  I can't find anything that will activate this menu.  Geany is in the menu and it is checked, its just the programming menu doesn't show up.

I couldn't get this to work.  
> >> sudo apt-get install build-essentials make automake libtool glib intltool
I got  
> E: Couldn't find package build-essentials
Also, how can I get the darker theme?  I saw this post [http://ubuntuforums.org/showthread.php?t=1015319&highlight=geany+background](http://ubuntuforums.org/showthread.php?t=1015319&highlight=geany+background)
I put the files in this folder ~/.geany/filedefs/ yet when I restart geany, I get a white background still.  I can't use the white background, it really hurts my eyes.

---

### Post by mltucker on 2009-04-13
Sorry -- it's "build-essential".

---

### Post by mltucker on 2009-04-13
As for the color theme, 

1. Download the theme from this website:

[http://code.google.com/p/geany-dark-scheme/]("http://code.google.com/p/geany-dark-scheme/")

2. Put it into the ~.geany/filedefs/ directory,

3. Decompress it:

```

tar xvjf geany_dark_filedefs_20081209_215628.tar.bz2

```

That should work.

-Mark

---

### Post by swappo1 on 2009-04-13
That was a mispelling on my part.  Now I'm getting E: Couldn't find package glib.

---

### Post by mltucker on 2009-04-13
Did you try the .deb mentioned above?  This would be much easier.  There are files that are needed to build from source that aren't needed to install from the .deb.

---

### Post by mltucker on 2009-04-13
Yeah.  You won't have to worry about the dependencies if you get it from the .deb.  I just did it:

1. Download from 

[http://www.getdeb.net/app/Geany]("http://www.getdeb.net/app/Geany")

(you'll have to select which ubuntu version and whether you are on a x64 or x86 processor).  I chose x86 intrepid.

2. Install:

```

sudo dpkg -i geany_0.16-1~getdeb1_i386.deb

```

Run.  It will automatically move your configuration directory.

---

### Post by swappo1 on 2009-04-13
Okay, I got 0.14 which is the latest version for Hardy.

---

### Post by swappo1 on 2009-04-13
I got the dark themes to work now. All I had to do was copy the .c file and rename it .cpp.  Now I just need to figure out how to get the programming menu to work under Applications.

---

### Post by mltucker on 2009-04-13
Yeah, it's weird that that doesn't work.  Try removing Geany from the menu (move it somewhere else and then delete it from the Programming menu), then drag it back in.

-Mark

---

### Post by mltucker on 2009-04-13
The Gnome keyboard shortcut program isn't the best... try gconf-editor.  You can apt-get install this.  It has the ability to assign commands to keyboard shortcuts, so you could map Ctrl-Alt-g to run the command "geany".

-Mark

---

### Post by swappo1 on 2009-04-13
I used gconf editor to set the keys to open geany.  Still can't figure out why I can't get programming menu under Applications to come up.  I suppose if I really need to I can move geany to Accesories or Education.

---

### Post by slavik on 2009-04-13
in menu editor: click on applications, then on the right make sure programming is checked.

---

