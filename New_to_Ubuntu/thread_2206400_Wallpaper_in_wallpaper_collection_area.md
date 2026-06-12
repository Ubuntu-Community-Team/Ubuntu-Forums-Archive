---
title: "Wallpaper in wallpaper collection area"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by GUZZLR on 2014-02-18
Hello All...
If I find a wallpaper I wish to download from somewhere, how can I place it where the stock wallpaper are located in System Settings > Appearence 
Ubuntu 13.10
Thanks for the help

---

### Post by deadflowr on 2014-02-18
There is probably some easier to use app out there in the grand universe, but simply add an entry to the .xml file in the folder
```
/usr/share/gnome-background-properties
```

or, as I did, went even further and basically took one of those xml files copied into home then strip it of the old default entries and replace them with my own.
Then copied it back into the folder.

The file would be raring-wallpapers.xml.(for 13.04)
But that really doesn't matter, what matters is that the file is an xml file and that it is in that folder.
Mine is simply mypictures.xml.

All you have to change would be the entries for the name and the filename.
You might also want to remove the first entry which is the entry for the slideshow wallpaper.
(unless you want to see how that works and replace the slideshow with you own)

Again, though, there's probably a better, easier to use, app if one exists for that.

Oh yeah, 13.04?
That release is end of life, by the way.

Edit: of course you could simply place them in the Pictures folder and use that option.

---

### Post by GUZZLR on 2014-02-19
Sorry....I am on 13.10, not 13.04.  My mistake.  I will try this and report back. Thanks

---

### Post by GUZZLR on 2014-02-22
[QUOTE=deadflowr;12933257]There is probably some easier to use app out there in the grand universe, but simply add an entry to the .xml file in the folder
```
/usr/share/gnome-background-properties
```


I'm having trouble with this ): 
1.  I found the gnome-background-properties folder
2.  I have renamed a picture to have the .xml file extension. Example: Beauty_Beach.xml
3.  I don't know how to get the renamed picture into the background folder?  If I try the move command, it gives me a goofy "permission denied" error window, if I simply try to drag it into the folder, it will not allow that, if I copy the picture file, and try to paste, there is no paste option..

Thanks for the help

---

### Post by deadflowr on 2014-02-22
Do you mean the background folder in 
```
/usr/share/backgrounds
```
?
You'll need to be root to move or copy something into that.
```
sudo cp original/file/path /usr/share/backgrounds/
```
should put the file into that folder.
But the filename path can be anywhere you want in the .xml file.
It doesn't have to be in the backgrounds folder.

But like I stated earlier, there is probably an easier way, and less daunty, to do this.

---

### Post by GUZZLR on 2014-02-22
Sorry...
I'm just not following this code. When I copy and paste it into a terminal, it is not recognized.  I dont understand why I dont have admin. rights on my own computer?

---

### Post by deadflowr on 2014-02-22
> **GUZZLR said:**
> Sorry...
I'm just not following this code. When I copy and paste it into a terminal, it is not recognized.  I dont understand why I dont have admin. rights on my own computer?

I hope you didn't simply copy what I posted, that was an example.
Replace the first entry with your own entry.
(The original file path entry)

But to try an make some sense of this try this
First copy a picture file into the background folder
```
sudo cp /home/yourname/Pictures/pictureYouCopy.jpg /usr/share/backgrounds/
```
Then open the xml file, Easiest is to use gedit
```
gksu gedit /usr/share/gnome-background-properties/precise-wallpapers.xml
```
(change the precise wallpaper.xml to which ever version you have.
Then, what I do is, copy one of the entries
```
<wallpaper>
    <name>Murales</name>
    <filename>/usr/share/backgrounds/Murales_by_Jan_Bencini.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

```
Then I move down and paste it right below that entry.
Make sure there is no empty lines between the two entries
```
<wallpaper>
    <name>Murales</name>
    <filename>/usr/share/backgrounds/Murales_by_Jan_Bencini.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
  <wallpaper>
    <name>MyNEWNAME</name>
    <filename>MyNEWFILEPATH</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

```
The important part is that the top of the entry says <wallpaper> and the bottom says </wallpaper>

Then save it and see if it shows up in the wallpapers section of Appearance.
If done right, and you only click on the save button once it'll show duplicate entries for the original wallpapers plus the new entry you added.
(That's because the save makes a backup of the file as it existed before you saved it. But double clicking will overwrite that with what you just did. Make sense?

Edit: Somehow I feel like I'm making this seem more complex than it actually is.
It's not overly complex, but it might seem that way at first.

That's also part of the reason I would recommend seeing if some app is available to do this, or something like this.

---

