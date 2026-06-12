---
title: "[SOLVED] - [Ubuntu 11.04] Nautilus Mount .iso script not working - gksudo issue"
date: 2015-12-08
forum: Programming Talk
---

### Post by gundeck2 on 2015-12-08
Man this is killing me...

I found a bunch of scripts about that are supposed to allow me to mount a .iso by right clicking the file and selecting the appropriate scripts.
It seems that gksudo does not work quite right. I can throw in a few gksudo in and about the script but I can never get to work.

```
<script>
#!/bin/bash
# mount
gksudo -k /bin/echo "got r00t?"
BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`
sudo mkdir "/media/$BASENAME"
zenity --info --title "ISO Mounter" --text "$BASENAME $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

if sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME"
then
if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted. Open Volume?"
then
nautilus /media/"$BASENAME" --no-desktop
fi
exit 0
else
sudo rmdir "/media/$BASENAME"
zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"
exit 1
fi
<script end>
```

I've gone through various renditions and they all end up the same...
The script executes.
I get asked for the root password
The Zenity window pops-up letting me know the "mkdir" should have already occurred, but the folder does not exist and the image is not mounted
I have also cut it down so it was only 6 lines.
```
<script>
#!/bin/bash
# mount
gksudo -k /bin/echo "got r00t?"
BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`
sudo mkdir "/media/ISO"
zenity --info --title "ISO Mounter" --text "$BASENAME $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/ISO"
<Script end>
```

Any ideas?
Also, I do not want to install additional apps if Nautilus can work.

---

### Post by deadflowr on 2015-12-08
Ubuntu 11.04?

---

### Post by Bucky Ball on 2015-12-08
> **deadflowr said:**
> Ubuntu 11.04?

+1.

As this is in Programming Talk don't know that it will make a lot of difference to support about programming, but you should seriously think about an upgrade to a supported release. 11.04 hasn't had a security update, or any update, in around two years. :|

---

### Post by spjackson on 2015-12-08
I'm far from being an expert in this area, but here goes.

I think what you are expecting by using gksudo echo and then sudo for the mkdir and mount commands is that credentials will get cached by gksudo so you will not get a terminal prompt for the remaining sudo commands. However, this doesn't work.

One option is to wrap the whole script in gksudo - e.g. "gksudo /path/to/my/script". The other option is to change the default behaviour of sudo/gksudo. Credential caching by default is by terminal (tty) but when the script is invoked from Nautilus, there is no terminal, so credential caching doesn't work. You can change this using the visudo command and adding the line
```

Defaults    !tty_tickets

```
Then your script should do what you intend. However, **do not change the default unless you understand what you are doing**. Read "man 5 sudoers" carefully because **getting it wrong can wreck sudo**.

There may be other solutions that I am not aware of.

---

### Post by gundeck2 on 2015-12-08
> **Bucky Ball said:**
> +1.

As this is in Programming Talk don't know that it will make a lot of difference to support about programming, but you should seriously think about an upgrade to a supported release. 11.04 hasn't had a security update, or any update, in around two years. :|

I agree with you there.
It certainly would be nice if the OS was updated, but that is beyond my control.
I have to work with what is installed in the field, which is Ubuntu 11.04.

---

### Post by gundeck2 on 2015-12-08
> **spjackson said:**
> I'm far from being an expert in this area, but here goes.

I think what you are expecting by using gksudo echo and then sudo for the mkdir and mount commands is that credentials will get cached by gksudo so you will not get a terminal prompt for the remaining sudo commands. However, this doesn't work.

One option is to wrap the whole script in gksudo - e.g. "gksudo /path/to/my/script". The other option is to change the default behaviour of sudo/gksudo. Credential caching by default is by terminal (tty) but when the script is invoked from Nautilus, there is no terminal, so credential caching doesn't work. You can change this using the visudo command and adding the line
```

Defaults    !tty_tickets

```
Then your script should do what you intend. However, **do not change the default unless you understand what you are doing**. Read "man 5 sudoers" carefully because **getting it wrong can wreck sudo**.

There may be other solutions that I am not aware of.

Thank you SpJackson
I will give that a go.
Thank you for the constructive response.

GunDeck

*Edit*
Worked like a Charm.
I did as you suggested script.sh in one file and the nautilus script call the script.sh.

```

#  Nautilus Script
#!/bin/bash
# mount
gksudo -k /home/USER/.gnome2/naulitus-scripts/script.sh

```

```

 #   script.sh

#!/bin/bash
# mount
BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`
sudo mkdir "/media/$BASENAME"
zenity --info --title "ISO Mounter" --text "$BASENAME $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"

if sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME"
then
if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted. Open Volume?"
then
nautilus /media/"$BASENAME" --no-desktop
fi
exit 0
else
sudo rmdir "/media/$BASENAME"
zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"
exit 1
fi


```

Also a thanks to deadflower for editing the OP and having a cool avatar. 
I power-watch 7 Deadly Sins - Season 1 not to long ago

---

