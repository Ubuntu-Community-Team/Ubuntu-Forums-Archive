---
title: "HOW-TO: Enable and Disable the Recently Used Menu in Gnome"
date: 2005-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by audax321 on 2005-11-16
To disable the recent documents menu in Gnome:

- Open '/home/username/.recently-used' in gedit:
[INDENT]gedit /home/username/.recently-used[/INDENT]

- Empty the contents of the file, save, and exit.

- Make the file read-only:
[INDENT]chmod 400 /home/username/.recently-used[/INDENT]


To re-enable the recent documents menu in Gnome:

- Make the file readable and writeable by the owner:
[INDENT]chmod 600 /home/username/.recently-used[/INDENT]


**AN EASIER ALTERNATIVE TO THE ABOVE!!!**
Use the script below by adding it to the nautilus script menu:

- Open a blank text document and copy/paste the following:
```

#!/bin/sh

# Enable/Disable Recent Documents Menu in Gnome

if [ ! -f "$HOME/.recently-used" ]; then
	echo "" > "$HOME/.recently-used"
	chmod 600 "$HOME/.recently-used"
fi

if [ -w "$HOME/.recently-used" ]; then
	echo "" > "$HOME/.recently-used"
	chmod 400 "$HOME/.recently-used"
	if [ "$?" = "0" ]; then
		zenity --title="Disabled" --info --text="The 'Recent Documents' menu item has been disabled."
	else
		zenity --title="Error" --error --text="There was an error disabling the 'Recent Documents' menu."
	fi
elif [ -f "$HOME/.recently-used" ]; then
	chmod 600 "$HOME/.recently-used"
	if [ "$?" = "0" ]; then
		zenity --title="Enabled" --info --text="The 'Recent Documents' menu item has been enabled."
	else
		zenity --title="Error" --error --text="There was an error enabling the 'Recent Documents' menu."
	fi
else
	zenity --title="Error" --error --text="It appears the file '$HOME/.recently-used' does not exist and could not be created."
fi

```

- Save the file and exit.

- Set the proper permissions:
[INDENT]chmod 755 /path/to/saved/file[/INDENT]

- Copy the file to the nautilus script directory located at:
[INDENT]/home/username/.gnome2/nautilus-scripts[/INDENT]

:)

---

### Post by stfu on 2006-11-06
How about in Edgy?

/home/user/.recently-used.xbel pops up and resurrects no matter what you do.

---

### Post by phoqueyoo on 2006-11-06
Yeah, this doesn't work in edgy. I REALLY want to get rid of this so if anyone has found a way, post it.

---

### Post by stfu on 2006-11-08
anyone? :)

---

### Post by caribo&#361; on 2006-11-16
```
$ rm .recently-used.xbel
$ mkdir .recently-used.xbel
```

this works, but you'll get gtk-warnings in console..

---

### Post by dolphinsonar on 2007-01-15
> **caribo&#361 said:**
> ```
$ rm .recently-used.xbel
$ mkdir .recently-used.xbel
```this works, but you'll get gtk-warnings in console..

Thanks for that, I haven't seen this solution anywhere else.  This is a good way to disable the recent documents menu in edgy.

---

### Post by microsafe17 on 2007-01-23
> **caribo&#361 said:**
> ```
$ rm .recently-used.xbel
$ mkdir .recently-used.xbel
```

this works, but you'll get gtk-warnings in console..

It definitely does work, thanks for the great idea.

---

### Post by dolphinsonar on 2007-06-05
> **dolphinsonar said:**
> Thanks for that, I haven't seen this solution anywhere else.  This is a good way to disable the recent documents menu in edgy.


Yeah, still works in Feisty.  Just did a clean install, and my Recently Used Documents menu is clean as well.  That function is weird.  Good riddance.

---

### Post by toastysquirrel on 2008-02-10
> **microsafe17 said:**
> It definitely does work, thanks for the great idea.
Question 1) Does this work in Gutsy?
Question 2) Do you still need to edit the *.recently-used* file?

:)

---

### Post by Oleq on 2008-02-11
It works very well, thanks! ;)

---

### Post by kryth on 2008-02-26
Doesn't seem to work in Gusty.

---

### Post by jochem_ on 2008-04-01
> **kryth said:**
> Doesn't seem to work in Gusty.

What I did was make the file immutable

```
sudo chattr +i recently-used.xbel
```

I am using Debian, but I guess this will work for you too.

---

### Post by achelis on 2008-04-01
Last method works in Gutsy.. Thanks for that :)

Is there no way to completely remove it from the "Places"-menu? This seems more like a hack that breaks the functionality rather than disabling it..

---

### Post by almalaci on 2008-04-19
Mind the missing '.' at the beginning of the filename.
It seems to work for me too on Gutsy.
And how do you change the command to re-enable it?

---

### Post by PsyWolf on 2008-04-28
> **jochem_ said:**
> What I did was make the file immutable

```
sudo chattr +i .recently-used.xbel
```

I am using Debian, but I guess this will work for you too.

Yea this worked for me in Hardy.  There should be an option to turn this off more easily though.

---

### Post by johnnylavah on 2008-10-17
> **jochem_ said:**
> What I did was make the file immutable

```
sudo chattr +i recently-used.xbel
```

I am using Debian, but I guess this will work for you too.

this worked well on hardy, thank you!  do you know how to reverse the effect so recent documents is re-enabled?

---

### Post by tmetzcc325 on 2008-10-22
I haven't tried this, but I think you would just need to run the same command, but with a -i instead of +i.  Could be wrong, though.

---

### Post by anonymous_user on 2008-11-13
> **jochem_ said:**
> What I did was make the file immutable

```
sudo chattr +i recently-used.xbel
```

I am using Debian, but I guess this will work for you too.
Thank you =D>

---

### Post by croddy on 2008-11-18
Glad I found this thread. Great tip. I created it as a directory and it finally stopped working.

Even when I chmod'ed it 000, some surreptitious background process cheerfully removed it and recreated it for me. Creating the directory seems to break whatever brain-damaged, overly-aggressive nonsense is forcibly inserting .recently-used.xbel into our rectums.

It's a shame, too, because I'd use it... if I could stick it in ~/Private, but apparently it's not allowed to be a symlink.

---

### Post by fifth_rune on 2009-02-15
If I use the method where I remove the file and create a directory in its place, is there any way to undo that?  I keep trying to get rid of the new directory but it won't let me (operation not permitted, even when I am root).  Any help?

---

### Post by fermulator on 2009-05-22
Creating the bogus .recently-used.xbel directory worked for me in Jaunty.

---

### Post by P3P on 2009-09-22
From [https://bugzilla.gnome.org/show_bug.cgi?id=305325#c13](https://bugzilla.gnome.org/show_bug.cgi?id=305325#c13)



This is already implemented in gtk.

Add "gtk-recent-files-max-age=0" to your ~/.gtkrc-2.0.

'Something to click' is just missing ;-)

See:
[http://library.gnome.org/devel/gtk/2.15/GtkSettings.html#GtkSettings--gtk-recent-files-max-age](http://library.gnome.org/devel/gtk/2.15/GtkSettings.html#GtkSettings--gtk-recent-files-max-age)

---

### Post by alex_o on 2009-10-25
sudo chattr +i recently-used.xbel

that worked a treat...

to undo:
sudo chattr -i .recently-used.xbel

just install ubuntu-tweak and go to DESKTOP>GNOME and under history uncheck Enable system-wide "Recent Documents" list

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by Rumored on 2010-05-07
Since deleting the whole thing wastes a lot of space in the gnome-shell, I wrote a tiny python mess to remove specific entries matching any python regex patterns:
[http://pastebin.com/dakpXq0z]("http://pastebin.com/KVzaT2L7")

save as ~./cleanme.py , make it executable, run as
"~./cleanme.py SomeStuffYouDontWant SomeMoreStuffToDelete morePr0n ..."

careful, doesn't backup anything, no warranty that it works, might shoot you in the face... 
it should print out the elements it's deleting though, so you can always pipe it into a backup file...

Protip: add it to your crontab as an hourly job, easiest with "Scheduled Tasks" UI in Gnome (sudo aptitude install gnome-schedule)

---

### Post by jmagsho on 2010-05-20
Thanks, I had forgotten this, and the terminal commands worked like a charm in Lynx.

---

### Post by dcstar on 2010-05-25
No having .recently-used.xbel working breaks the Library (the list of VMs) of VMware Player 3.1.0.

[https://bugs.launchpad.net/ubuntu-tweak/+bug/585268](https://bugs.launchpad.net/ubuntu-tweak/+bug/585268)

---

### Post by Ubunthree on 2010-08-07
I have this little script which deletes a bunch of history-type things when I run it:

#!/bin/bash

rm -r /home/username/.macromedia
rm /home/username/.config/google-chrome/Default/History
rm -r /home/username/.cache/google-chrome
rm -r /home/username/.thumbnails

Does anything bad happen if I add this line:

rm /home/username/.recently-used*

And is there a way to get a script to run automatically at logoff/shutdown, the way you can at startup?

Thanks!

---

### Post by solitaire on 2010-10-25
Easier option is to point the cache & thumbnails folders to the /tmp/* folder so it's wiped at every reboot
I've got a simple script to recreate the folders at every boot.

---

### Post by jocheem67 on 2010-11-11
> #!/bin/bash
#
# /etc/rc.local.shutdown: Local shutdown script.
#
rm -f /home/#/.recently-used.xbel
rm -f /home/#/.recently-used.xbel.*
rm -rf /home/#/.macromedia/Flash_Player/#SharedObjects/*
rm -rf /home/#/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/*
rm -r /home/#/.thumbnails/*

Works with Arch, I guess that Ubuntu has a similar routine?

---

