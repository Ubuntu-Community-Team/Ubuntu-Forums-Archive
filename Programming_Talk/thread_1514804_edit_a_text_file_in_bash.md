---
title: "edit a text file in bash"
date: 2010-06-21
forum: Programming Talk
---

### Post by jakupl on 2010-06-21
Hi, I want to make a script that changes the ~/.gnome2/backgrounds.xml file.

I want to add one background so that for instance this:

```
<?xml version="1.0"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper deleted="false">
    <name>Fluffodome</name>
    <filename>/usr/share/backgrounds/Fluffodome.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#01011b1b3636</pcolor>
    <scolor>#01011b1b3636</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Curls by Candy</name>
    <filename>/usr/share/backgrounds/CurlsbyCandy.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#a0a09b9b9090</pcolor>
    <scolor>#a0a09b9b9090</scolor>
  </wallpaper>
</wallpapers>
```

becomes this:

```
<?xml version="1.0"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper deleted="false">
    <name>Fluffodome</name>
    <filename>/usr/share/backgrounds/Fluffodome.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#01011b1b3636</pcolor>
    <scolor>#01011b1b3636</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>Curls by Candy</name>
    <filename>/usr/share/backgrounds/CurlsbyCandy.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#a0a09b9b9090</pcolor>
    <scolor>#a0a09b9b9090</scolor>
  </wallpaper>
  <wallpaper deleted="false">
    <name>whatever</name>
    <filename>/blablabla/blabla</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#000000000000</pcolor>
    <scolor>#000000000000</scolor>
  </wallpaper>
</wallpapers>
```
so basically, I want to add some text above the ```
</wallpapers>
```

How would that be possible in a script, using cat for instance

---

### Post by Lampi on 2010-06-21
what about patch?

you run diff -Naur <newfile> <oldfile> <diffile>.patch

then you can use patch -i <diffile>.patch in the directory

kind of weird since patch is desgined for source code management, but it will work on any plain text as is your xml code

---

### Post by jakupl on 2010-06-21
> **Lampi said:**
> what about patch?

you run diff -Naur <newfile> <oldfile> <diffile>.patch

then you can use patch -i <diffile>.patch in the directory

kind of weird since patch is desgined for source code management, but it will work on any plain text as is your xml code

is patch installed as default on ubuntu? Since It will be used on many different installs.eird since patch is desgined for source code management, but it will work on any plain text as is your xml code

will this altso work on files that are different. I only want to add text above the ```
</wallpapers>
```
 without changing the rest of the xml file.
and the text above that will vary from computer to computer.

---

### Post by Penguin Guy on 2010-06-21
You can find a bunch of backgrounds and background-manipulating scripts [here]("http://dl.dropbox.com/u/1217030/Backgrounds.tgz"), they should give you an idea how to do this, although I can't guarantee they'll all work perfectly.

---

### Post by oldfred on 2010-06-21
Is not a tool available?

       Display the path to the current desktop wallpaper.

              gconftool-2 --get /desktop/gnome/background/picture_filename

man gconftool-2

Manually with gconf-editor and see script to automate & man gconftool-2
[http://www.packtpub.com/article/ubuntu-user-interface-tweaks](http://www.packtpub.com/article/ubuntu-user-interface-tweaks)

---

### Post by Lampi on 2010-06-21
> is patch installed as default on ubuntu?

I don't think so.

Now that you mention you plan to place this on various machines I highly doubt diff + patch is the right choice: patch only works if the original file you used the diff on is very close-to-identical compared to the file on the other machines you wish to alter: patch can only find blank line offset differences, nothing else -> it will complain if actual *content* is different from the original file.

---

### Post by jakupl on 2010-06-21
Well I figured it out. I just replace ```
~/.gconf/desktop/gnome/background/%gconf.xml
```
using:

This is the relevant piece of code. It's very un-economical and noob'ish, but it does the job.... well it should.

```
#!/bin/bash
if [ -d /home/$USERNAME/.gconf ]; then
    echo '''.gconf exists'''
else
    echo '''.gconf does not exist, creating directory'''
    mkdir /home/$USERNAME/.gconf
fi

if [ -d /home/$USERNAME/.gconf/desktop ]; then
    echo '''.gconf/desktop exists'''
else
    echo '''.gconf/desktop does not exist, creating directory'''
    mkdir /home/$USERNAME/.gconf/desktop
fi

if [ -d /home/$USERNAME/.gconf/desktop/gnome ]; then
    echo '''.gconf/desktop/gnome exists'''
else
    echo '''.gconf/desktop/gnome does not exist, creating directory'''
    mkdir /home/$USERNAME/.gconf/desktop/gnome
fi

if [ -d /home/$USERNAME/.gconf/desktop/gnome/background ]; then
    echo '''.gconf/desktop/gnome/background exists'''
else
    echo '''.gconf/desktop/gnome/background does not exist, creating directory'''
    mkdir /home/$USERNAME/.gconf/desktop/gnome/background
fi
rm ~/.gconf/desktop/gnome/background/%gconf.xml
cat << EOF >> ~/.gconf/desktop/gnome/background/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="primary_color" mtime="1277143967" type="string">
		<stringvalue>#000000000000</stringvalue>
	</entry>
	<entry name="secondary_color" mtime="1277143967" type="string">
		<stringvalue>#000000000000</stringvalue>
	</entry>
	<entry name="picture_filename" mtime="1277143967" type="string">
		<stringvalue>/home/$USERNAME/.gnome2/WHATEVER-WALLPAPER.jpg</stringvalue>
	</entry>
	<entry name="color_shading_type" mtime="1277143967" type="string">
		<stringvalue>solid</stringvalue>
	</entry>
	<entry name="picture_options" mtime="1277143967" type="string">
		<stringvalue>stretched</stringvalue>
	</entry>
</gconf>
EOF
```

---

### Post by hannaman on 2010-06-22
You can use sed to add text to a file.  For your usage, you can insert text before a line using something like:

```
sed -i '/\<\/wallpapers\>/i\
  <wallpaper deleted="false">
    <name>whatever</name>
    <filename>/blablabla/blabla</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#000000000000</pcolor>
    <scolor>#000000000000</scolor>
  </wallpaper>' ~/.gnome2/backgrounds.xml
```

This is untested of course, but it should be something along these lines.

The -i will edit the file in place, so be sure to make a backup before running this.

---

