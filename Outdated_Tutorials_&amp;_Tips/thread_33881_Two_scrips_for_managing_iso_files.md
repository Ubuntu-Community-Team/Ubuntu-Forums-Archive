---
title: "Two scrips for managing iso files"
date: 2005-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by sonny on 2005-05-12
Well I was looking for some scripts to mount and unmount iso images but I found none, well actually there's a thread [here](http://www.ubuntuforums.org/showthread.php?t=30635&highlight=scripts+iso)  about doing so, but the script is missing some basic parts that I just added, this thread was my inspiration on doing the scripts below, if someone has done it allready , well one more wouldn't hurt anyone. One thing to notice, this scripst are for nautilus, KDE users don't need this, there's plenty of konqueror's plugins that manage iso files.

Ok this code is now fixed with all the observations made from everyone, and correcting some mistakes I've made.

> Script for Mounting an Iso
First we make the folder where the files are going to be mounted, open a terminal and type:
~$ sudo mkdir /media/iso (I prefer this becuse then I just go to the system and the iso folder will be next to the cdrom and/or floppy like an other dev)

In a terminal do:
~$ gedit ~/.gnome2/nautilus-scripts/Mount\ Iso
When gedit shows up write this code:

#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-terminal -x sudo mount -o loop -t iso9660 "$1" /media/iso
done

Finally you have to make the file executable, to do so type in a terminal:
~$ chmod +x ~/.gnome2/nautilus-scripts/Mount\ Iso
 

Now you can right click on an iso file and mount it, by selecting the menu scripts and then Mount Iso from the menu that appears when you right click something, then a terminal will popup asking you for your password, type your sudo password and that's all. The next script is for unmounting the iso image, and we do like this:

> Script for unmounting the iso
open a terminal and type:
~$ gedit ~/.gnome2/nautilus-scripts/Unmount\ Iso

When the text editor showup put this code:
#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gnome-terminal -x sudo umount "$1"
done

Make executable by typing in the terminal:
~$ chmod +x ~/.gnome2/nautilus-scripts/Unmount\ Iso



Now you can mount and unmount iso files with just two clicks... hope this works for you, and make the life of some a little better. These are simple scripts, I guess that if you want to mount *.nrg or *.cue or something else the script will be the same just changing the filetype would be enough for the script to work. I will find out the filetypes for some other images and update the scripts within this weekend (if I'm free of homework).

I've tried the Heliode's code, but somehow it sometimes doesn't work in my machine, although you can use it instead of the code above, I just do it like this because of the failures of my machine, I don't know what I've done to it  ](*,) , anyway, hope this code works for everyone.

---

### Post by sonny on 2005-05-12
By the way I put the thread in here because I didn't know were to put it, and this is a very crowded forum, so I hope more people would see this in this place...  :-P

---

### Post by Sam on 2005-05-12
The good place should be [Hoary 5.04 Customization Tips & Tricks](http://ubuntuforums.org/forumdisplay.php?f=58).

---

### Post by TravisNewman on 2005-05-12
Moving to tips and tricks :)

---

### Post by Heliode on 2005-05-12
Excelent. This was one of the things what I was missing. A couple of things though; In the section about the 'Mount' script you provide the code for making the UNmount script executable. That, and it might be a good idea to change;

.gnome2/nautilus-scripts/Unmount\ Iso

to

~/.gnome2/nautilus-scripts/Unmount\ Iso

That way it will always work, regardless of whatever directory you might be in.
Nothing mayor, just a couple of things that might confuse new users.

Edit:
Something else though: you use 'sudo' in your scripts, and unless you are a member of the 'sudo' group (which is neither default nor a very wise thing), it'll need a password, but the user isn't prompted for one, so it doesn't work.

---

### Post by Heliode on 2005-05-12
Ok I figured out how to make it work in a nice, clean way. This will pop up a message box asking the user for the password:

Mounting:
```

#!/bin/bash
gnome-sudo "mount -o loop -t iso9660 "$1" /media/iso" &

```

Unmounting:
```

#!/bin/bash
gnome-sudo "umount "$1"" &

```

---

### Post by sonny on 2005-05-18
Ok I got the code to mount and *.img file, sorry for not posting it sooner, I got way too much things to do at work, and at school... but you just have to do:
> 
In a terminal type:
gedit ~/.gnome2/nautilus-scripts/Mount\ Img

when gedit shows up you put this code in:
#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-terminal -x sudo mount -o loop,ro -t iso9660 "$1" /media/img &
done

Save and close, then in the teminal type:
chmod +x ~/.gnome2/nautilus-scripts/Mount\ Img
 
That is all, if you want to unmount it, you can use the same code for the iso file explained before. Ok.. I'll find out more codes for mounting cd images and will update this thread as soon as I get more... if some of you know the code for some others, what are you waiting for posting it??? It's a community, help us if you can.

---

### Post by M7S on 2005-05-19
Thanks for the tips.

Imho, the nautilus-script folder quickly gets to filled if you have a lot of scripts there that is used just for one file type.

This is what I did instead:

> In a terminal type:
gedit ~/.myscripts/Mount\ Img

when gedit shows up you put this code in:
#!/bin/bash
gnome-sudo "mount -o loop -t iso9660 "$1" /media/iso" &

Save and close, then in the teminal type:
chmod +x ~/.myscripts/Mount\ Img

Rightclick on a iso-file and choose "Open with other program"*. Click on "Use a custom command"*, write "_path-to-your-home-folder-here_/.myscripts/Mount\ Img" and press OK.

*) Translated from sweedish.

To mount a iso just right click on it and choose 'Open with "Mount Iso"' to mount.


When it comes to unmounting isos I prefer to use a nautilus-script like this one:
> #!/bin/bash
gnome-sudo "umount /media/iso" &

That way I can unmount the iso without clicking on a the right iso-file.

Regards,
M7S

---

### Post by Sam on 2005-05-19
[QUOTE=M7S]Imho, the nautilus-script folder quickly gets to filled if you have a lot of scripts there that is used just for one file type.[/QUOTE]
You can create subfolders in the nautilus scripts folder to store your scripts !

---

### Post by M7S on 2005-05-19
[QUOTE=Sam]You can create subfolders in the nautilus scripts folder to store your scripts ![/QUOTE]
 Thanks, that's good to know.

---

### Post by cnekmp on 2008-06-17
For the version Ubuntu 8.04 the best way that i`ve found for correct umount of iso folder is:
```

Run in Terminal:
~$ gedit ~/.gnome2/nautilus-scripts/Unmount\ Iso

In text editor write down this code:
#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gnome-terminal -x sudo umount **-l /media/iso**
done

Save text file and run in Terminal:
~$ chmod +x ~/.gnome2/nautilus-scripts/Unmount\ Iso

```

NOTE:

**In my case the mount folder is in /media/iso , so you should change it to your mount folder name. And don't forget to write down "-l" option.**

That's all :)

---

