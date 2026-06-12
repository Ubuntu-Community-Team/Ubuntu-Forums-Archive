---
title: "Script: Easily change quality of MP3 files"
date: 2007-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by picpak on 2007-12-29
**[color=red]DISCLAIMER:[/color]** I don't want this topic turning into a discussion of how bad it is to turn a low quality mp3 into an even lower quality mp3. I don't want to "kill" their mp3s; I want to provide them with a solution to a very viable problem. Maybe they're running low on disk space, or need smaller files for their mp3 player.

[size=4]Intro:[/size]

I for one got very tired of having to always type *lame -b 128* etc, etc. into the terminal each time I wanted to change the quality of an mp3. Sure, there's [http://www.media-convert.com/](http://www.media-convert.com/) , but that lags our internet. So I whipped up this script.

[size=4]Installation for Nautilus[/size]

Installation for the default file manager in Ubuntu.

1) Download mp3Convert by downloading the attachment at the bottom of this post.

(Alternatively, you can get the code right here:

```
#!/bin/bash

quality=128
title=Converting
file=$@

if [ "$file" ]; then
cd `pwd`
lame -b $quality "$file" 2>&1 | awk -vRS='\r' '(NR>3){gsub(/[()%|]/," ");print $2; fflush();}' | zenity --progress --auto-close --auto-kill --title="$title" --text="$title $file at $quality kbps to $file.mp3"
fi
```

Copy and paste it into the *Text Editor* and save it as *~/mp3Convert.sh*.)

2) Open up a terminal (**Applications** > **Accessories** > **Terminal**) and put the script into *~/.gnome2/nautilus-scripts* (the folder Nautilus checks to find any scripts):

```
mv mp3Convert.sh ~/.gnome2/nautilus-scripts
```

3) Make the script executable so that Nautilus will detect it.

```
chmod 740 ~/.gnome2/nautilus-scripts/mp3Convert.sh
```

All done! Now you can right click an mp3 file and go to **Scripts** > **mp3Convert.sh**.

[size=4]Installation for Thunar[/size]

Installation for the default file manager in Xubuntu.

1) Download mp3Convert by downloading the attachment at the bottom of this post.

(Alternatively, you can get the code right here:

```
#!/bin/bash

quality=128
title=Converting
file=$@

if [ "$file" ]; then
cd `pwd`
lame -b $quality "$file" 2>&1 | awk -vRS='\r' '(NR>3){gsub(/[()%|]/," ");print $2; fflush();}' | zenity --progress --auto-close --auto-kill --title="$title" --text="$title $file at $quality kbps to $file.mp3"
fi
```

Copy and paste it into *Mousepad* and save it as *~/mp3Convert.sh*.)

2) Open up a terminal (**Xfce Menu** > **Accessories** > **Terminal**) and put the script into *~/.config/Thunar/actions* (not needed, but it's a nice clean place to put it):

```
mkdir -p ~/.config/Thunar/actions
mv mp3Convert.sh ~/.config/Thunar/actions
```

3) Make the script executable:

```
chmod 740 ~/.config/Thunar/actions/mp3Convert.sh
```

3) Now go to **Edit** > **Configure custom actions...**. Click the **Add** (plus) sign and put in the following:

a) Under the *Basic* tab:

**Name:** mp3Convert.sh
**Command:** ~/.config/Thunar/actions/mp3Convert.sh %f

b) Under the *Appearance Conditions* tab:

Put a checkmark next to **Audio files**. Click **Ok** and exit out of the actions manager.

Now you can right click an mp3 file and go to **mp3Convert.sh**.

[size=4]Configuration[/size]

By default it converts files to 128kbps, which I know isn't everyone's cup of tea. So you can edit *~/.gnome2/nautilus-actions/mp3Convert.sh* (or *~/.config/Thunar/actions/mp3Convert.sh*, depending on where you put it) by doing

```
gedit ~/.gnome2/nautilus-actions/mp3Convert.sh
```

(or, *mousepad ~/.config/Thunar/actions/mp3Convert.sh*)

and changing line 3 from

```
quality=128
```

to

```
quality=192
```

Or, whatever quality you prefer. Save and exit.

Enjoy!

---

### Post by Mary.Riley on 2008-02-03
Is there a way to do this for Konqueror as well?

---

### Post by _march_ on 2008-02-09
Thanks for your Skript :)
Just added it in our [Wiki]("http://wiki.ubuntuusers.de/Thunar/Benutzerdefinierte_Aktionen") :D

---

