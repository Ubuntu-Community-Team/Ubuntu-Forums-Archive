---
title: "HOWTO: GNOME - Install .DEBs with right click !"
date: 2005-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by shakin on 2005-05-11
Edit: It's now confirmed working. I fixed a filename issue (nautilus returns the filename with file:// on the front, so I stripped it off) and made it execute in a new terminal window so I could use sudo because dpkg doesn't work with gksudo. Serves me right for posting an untested script :)

Second edit: Thanks to Gandalf for pointing out the chmod error. It is fixed.

Ever wanted to install debs without opening a terminal? How about doing it by right-clicking on the file [just like those fancy KDE people](http://ubuntuforums.org/showthread.php?t=33440)?

Try this:

```
$ gedit ~/.gnome2/nautilus-scripts/Install\ Deb
```

Now add the following code and save the file.

```

#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-terminal -x sudo dpkg -i ${uri:7}
done

```

Make the script executable:
```

$ chmod +x  ~/.gnome2/nautilus-scripts/Install\ Deb

```

This script will be in your right-click menu under Scripts. It will show up for all files, but obviously will only install Debs and dpkg will give an error for other file types. It should work if you select multiple debs.

(Uninstaller removed because it won't work until the script can hook into the apt database to search for the real package name that was installed)

---

### Post by mattgirv on 2005-05-11
> **shakin]Ever wanted to install debs without opening a terminal? How about by right-clicking on the file [just like those fancy KDE people](http://ubuntuforums.org/showthread.php?t=33440)?

Try this:

```
$ gedit ~/.gnome2/nautilus-scripts/Install\ Deb
```

Now add the following code and save the file.

```

#!/bin/bash

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS said:**
> I am not currently running Gnome. Somebody let me know if it works or not and I'll fix it if it doesn't.[/CENTER]
 Hmm, well it doesn't seem to appear, in my right click menu. I don't have any "scripts" bit there either.

---

### Post by shakin on 2005-05-11
[QUOTE=mattgirv]Hmm, well it doesn't seem to appear, in my right click menu. I don't have any "scripts" bit there either.[/QUOTE]

No? Not when you right-click on a file? Can you cd to  ~/.gnome2/nautilus-scripts? Everything in that directory should be listed under Scripts when you right click on a file or folder.

I checked my original source for nautilus scripting ([http://www.ubuntuforums.org/showthread.php?t=26668](http://www.ubuntuforums.org/showthread.php?t=26668)) and there are no additional steps needed to make it work.

---

### Post by ildfroe on 2005-05-11
You need to make the script executeable before it shows up in the menu.
Right-click your script-file and change the properties.

edit: And it doesn't work :(

---

### Post by shakin on 2005-05-11
[QUOTE=ildfroe]You need to make the script executeable before it shows up in the menu. Right-click your script-file and change the properties.[/QUOTE]

Thank you. I have added that step to the how-to. I had originally copied another script and didn't need to do this step.

[QUOTE=ildfroe]edit: And it doesn't work :([/QUOTE]

I fixed the two problems that were preventing it from working. I started Gnome and actually tested it this time and it does work. I removed the uninstall script because it would never have worked.

---

### Post by ildfroe on 2005-05-11
Yep. It works fine now ;-)

---

### Post by Xian on 2005-05-11
This is very nice! Makes using Ubuntu even easier. :)

---

### Post by Gandalf on 2005-05-11
great HOWTO thx man
BTW replace
```

chmod +x Install\ Deb

```

with
```

chmod +x  ~/.gnome2/nautilus-scripts/Install\ Deb

```

because following your first command we aren't in ~/.gnome2/nautilus-scripts/ and will confuse some about it,
anyway great work, keep it up ubuntu addicted guys :D

---

### Post by benplaut on 2005-05-11
[QUOTE=Gandalf]great HOWTO thx man
BTW replace
```

chmod +x Install\ Deb

```

with
```

chmod +x  ~/.gnome2/nautilus-scripts/Install\ Deb

```

because following your first command we aren't in ~/.gnome2/nautilus-scripts/ and will confuse some about it,
anyway great work, keep it up ubuntu addicted guys :D[/QUOTE]

why didn't i just read the thread instead of spending precious time finding the file in Nautilus to make it executible  ](*,) 


 :razz:

---

### Post by Sniffer on 2005-05-12
Thks for this one.

Will save me a lot of time.

---

### Post by rwabel on 2005-05-15
thanks for that one, it's a nice way to install deb's like that

---

### Post by bobgreen5s on 2005-05-16
works great

btw, are there any tutorials on nautilus scripting?

---

### Post by Darrena on 2005-05-21
Great script, is there any way to make it pause at the end to see the output?

Thanks!

---

### Post by Sam on 2005-05-21
[QUOTE=Darrena]Great script, is there any way to make it pause at the end to see the output?

Thanks![/QUOTE]
Just add "read" on a single line at the end and it'll wait until you press Enter.

---

### Post by David Kaisemann on 2005-05-21
It's helpful! I'm  make this right now. Thank!

---

### Post by peanut butter on 2005-06-04
i did this but it wont install gnome baker

---

### Post by empathy on 2005-06-05
Fantastic time saver!

I am a ubuntu/linux n00b and have been researching how to install downloaded debs ... this is by far the most intuitive solution for me. Thank You. :grin:

---

### Post by Sionide on 2005-06-05
What a brilliant idea, something as simple as this shouldn't be too hard to have on the default installation right?

---

### Post by Jesus Franco on 2005-06-06
Awesome! Thanks for this how-to. I used kde and did use that script. It was nice. Its good to see it in Gnome aswell.  :grin:

---

