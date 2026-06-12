---
title: "HOWTO: Getting Breezy 'Human' Icons in Dapper"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Footissimo on 2006-06-03
Some may be a bit bothered by the fact that the old Breezy Human **icon** theme set is not available in Dapper by default.  There are 'LegacyHuman' themes available for the control and border themes, but not for the icons.

Fear not, getting those less orange Breezy human icons is fairly easy.

Open up a terminal window i.e. Applications->Accessories->Terminal

Make sure you're in the home directory:

```
cd ~/
```

Download the Breezy Artwork set:

```
wget http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/ubuntu-artwork_0.2.27.orig.tar.gz
```

Extract the archive:

```
tar -xzf ubuntu-artwork_0.2.27.orig.tar.gz
```

Go to the bit where the icon set is:

```
cd ~/ubuntu-artwork-0.2.27/art/icons/
```

Change the name of the icon set folder so it doesn't conflict with the Dapper Human set:

```
mv Human LegacyHuman
```

Use your favorite text editor to edit the index.theme file and rename it to 'LegacyHuman' or whatever you changed the folder to:

```
gedit ~/ubuntu-artwork-0.2.27/art/icons/LegacyHuman/index.theme
```

Your text editor should pop up now..and at the top it should look something like this:

```
[Icon Theme]
Name=Human
Comment=Ubuntu default theme
Inherits=gnome
```

Change the 'Name' bit to whatever name you used for the folder, LegacyHuman, in my example:

```
[Icon Theme]
Name=LegacyHuman
Comment=Ubuntu default theme
Inherits=gnome
```

Save the file and exit.

Now we just need to shove that icon set to where it should be:

```
cd ~/ubuntu-artwork-0.2.27/art/icons/
```

then:

```
sudo mv LegacyHuman/ /usr/share/icons/
```

Tada!  You should see LegacyHuman, or whatever you renamed it to, in the icon theme list.

To get rid of the mess in the home directory:

```
rm -rf ~/ubuntu-artwork-0.2.27/
```
```
 rm ~/ubuntu-artwork_0.2.27.orig.tar.gz
```

Thankyou to Rui Pais for showing me the way :)

---

### Post by PingunZ on 2006-07-25
Nice howto, but why would you do that :s ?

---

### Post by Footissimo on 2006-07-25
..because the new 'human' icons have more colour and therefore are less likely to match different themes :)

---

### Post by Clay85 on 2006-07-29
Is there nowhere to just download the .png/.xpm files?

Are we talking about the icons as in usr/share/pixmaps? (I am.)

Or, is there some other kind of icon I'm missing. Maybe I'm way off.

---

### Post by Footissimo on 2006-07-29
You can get them in the Breezy artwork set:

[http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/ubuntu-artwork_0.2.27.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/ubuntu-artwork_0.2.27.orig.tar.gz)

---

