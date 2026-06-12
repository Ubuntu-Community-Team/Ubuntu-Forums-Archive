---
title: "how do i use zenity to make nautilus scripts?"
date: 2009-12-16
forum: Programming Talk
---

### Post by lance bermudez on 2009-12-16
#!/usr/bin/bash

echo '7zip file name'
read name
7z a -mm=deflate64 archive.zip $name
exit 0

how do i get the zenity gui interface for nautilus scripts? this works for me in command line. how do i get this to work with out having to have the bash file in the same dir as the file i want ziped?

---

### Post by Can+~ on 2009-12-16
Nautilus has a folder where it can read scripts:

```
~/.gnome2/nautilus-scripts/ 
```

And it passes certain arguments (environment, actually), like:

```
$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
$NAUTILUS_SCRIPT_SELECTED_URIS
$NAUTILUS_SCRIPT_CURRENT_URI
$NAUTILUS_SCRIPT_WINDOW_GEOMETRY
```

---

### Post by kaibob on 2009-12-16
> **lance bermudez said:**
> how do i get the zenity gui interface for nautilus scripts? this works for me in command line. how do i get this to work with out having to have the bash file in the same dir as the file i want ziped?

It's not clear to me how you want to use the zenity dialog in the nautilus script. Perhaps you could explain a bit more. 

For reference, the following site has a good basic explanation of how a nautilus script works:

[http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

And, the following site explains and has examples of zenity dialogs:

[http://library.gnome.org/users/zenity/2.24/zenity.html](http://library.gnome.org/users/zenity/2.24/zenity.html)

---

### Post by lance bermudez on 2009-12-17
I have my script in the nautilus scripts part of gome however when i click on it the script does nothing. I have to use it from the command line. by using zenity i mean a box will pop up to take the name of the file or dir i want ziped (the read name from above) and insert the name into the $name (the 7z a -mm=deflate64 archive.zip $name from above) I was told by youtube that this could be done but the guy in the video did not explain it on my very low level to get what he was taling about.

---

### Post by kaibob on 2009-12-17
When using a Nautilus script, the name of the file or files to be processed is obtained by way of the Nautilus file manager. Thus, for example, you would open Nautilus, right click on the file or files to be archived, scroll down to "scripts", and then select the name of the script. 

The following is the Nautilus-script equivalent of the shell script included in your original post. $@ is the file name or names passed from Nautilus to the script. I used the zip utility, because its the one I'm familiar with, and because it's already installed on my computer and allowed me to test the script. 

```
#!/bin/bash

zip -r archive.zip "$@"
```

As previously mentioned, this script has to be placed in the nautilus script directory. Also, this nautilus script should work to archive a directory, although you have to select the directory to be archived in the right pane of Nautilus.

---

### Post by lance bermudez on 2009-12-18
how would i have zenity give me a progress bar so i know when it is done?

---

### Post by lance bermudez on 2009-12-19
I have 

#!/bin/bash

7z a -mm=deflate64 archive.zip "$@" | zenity --progress --text="zipping" --pulsate --auto-kill

and it works if you dont mind the progress bar not moving. I have enven tried the --percentage=INT with INT= and number and the bar still does not move. I&#7743; also zipping big files becuse the bar just set their for a little while with out moving but when it is done it is all full.

---

