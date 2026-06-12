---
title: "Linux Variable Passing"
date: 2011-04-06
forum: Programming Talk
---

### Post by hateborne on 2011-04-06
Sorry to bother everyone, but I've run into an interesting question.

How would one pass a filename?

Clarification: I am tinkering with minor Ubuntu odds 'n' ends and I found the built in md5 checksum package/addin/etc. It is pretty self explanatory, but I thought to add it to the right click menu when I select a file. So I can right click, pick "MD5" from menu, and then get a popup with the sum. The popup is handled by zenity, and the md5 sum is built in... I am still unclear how to pass the filename of what I am opening. 

Is there a default variable(s) for passed items? In perl, when passing arguements, the default variable is $_[0] $_[1] etc etc. Does such a variable exist for Linux Ubuntu (or I suppose technically Debian)?

I would generally just faceroll Google results for an hour or two, but I cannot find a way to clearly and concisely query the mess above.

Thank You in Advance,
-Hate

---

### Post by Vaphell on 2011-04-06
never used zenity but in general when you run
```
some_script some.file
```
you can access that parameter with $1, for example
echo "$1"
will print out the file name.

using nautilus-actions you can customize rightclick menu with your own entries
in parameters part you need to type %f or something (there is a menu with available symbols that will pass the desired value to the command)

---

### Post by kaibob on 2011-04-06
> **hateborne said:**
> Clarification: I am tinkering with minor Ubuntu odds 'n' ends and I found the built in md5 checksum package/addin/etc. It is pretty self explanatory, but I thought to add it to the right click menu when I select a file. So I can right click, pick "MD5" from menu, and then get a popup with the sum. The popup is handled by zenity, and the md5 sum is built in... I am still unclear how to pass the filename of what I am opening. 

You can use a nautilus script, which is placed in "~/.gnome2/nautilus-scripts" directory. The script is selected by way of the "Scripts" entry in the Nautilus right-click menu. 

```
#!/bin/bash

number=$(md5sum "$1")
number="${number%% *}"

zenity --title "$1" --info --text "$number"
```

In a Nautilus script, "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" returns the selected file name including its path, and "$1" returns the file name without its path.

To learn more about Nautilus scripts:

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by hateborne on 2011-04-07
Thank you both very much.

kaibob, thank you for not only answering but providing a link for additional research!

-Hate

---

