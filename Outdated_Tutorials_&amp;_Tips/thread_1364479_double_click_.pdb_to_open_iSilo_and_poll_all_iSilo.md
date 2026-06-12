---
title: "double click .pdb to open iSilo and poll all iSilo files under wine"
date: 2009-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by prconnor@gmail.com on 2009-12-25
Hello,

This week I purchased iSilo for windows and have been running it under wine on my netbook (acer aspire 150) running ubuntu linux.  I fumbled around and made some customizations that I think have made the experience better for me.  I will use 'Single Quotes' to indicate menu choices and proper names such as file names.

1. Make iSilo open under wine when I double-click a .pdb icon.

1.1 Write a launch program (called mine 'iSilo' ... I know, very creative)

1.1.1 Decide where you want you file (I put mine in ~/bin/).  Open a text editor: ex: enter the following in a terminal
```
gedit ~/bin/iSilo
```

1.1.2 Paste the following as text in the file:
```
#!/bin/bash
launch="/home/USER_NAME/.wine/drive_c/Program Files/iSilo/iSilo/iSilo.exe"
if [ $# -eq 1 ]; then
	rename=$(echo $1 | sed -e 's/^/z:/' -e 's/\\//g')
	"$launch" "$rename"
elif [ $# -eq 0 ]; then
	"$launch"
fi
```
You will of course change USER_NAME with your actual user name.  Save and close the file.

1.1.3 Make the file executable.  In a terminal: ```
chmod +x ~/bin/iSilo
```

1.2 Add the launch program as the default program in your file manager.  The rest of this step applies to gnome desktop manager as that is what I use.  I'm sure that you can figure it out on KDE or what ever else you are using

1.2.1 Open nautilus ```
'Places'->'Home Folder'
```

1.2.2 Browse to a .pdb file on your harddrive

1.2.3 Right click on the .pdb file->'Properties'->'Open With'->'Add'->'Use Custom Command'->'~/bin/iSilo'->'Add'

1.2.4 Click the bubble next to iSilo to make it the default application.

1.3 Double click on the icon to verify it launches in iSilo under wine.

1.4 I also did this for MobiPocket (which doesn't work well under wine), eReader, and Adobe Desktop Editions (to double click on the install hyperlink of books).  But since most of my ebooks are iSilo, I selected this as the default for .pdb.  I set FBReader as the default for .prc which does a better job than MobiPocket for unencrypted MobiPocket files.





2. Poll all of my .pdb files so that 'Open Categorized' will find them.

I have been using iSilo on a palm pilot for about 7 years and have accumulated just shy of 1000 ebooks.  So of course opening all of them one at a time just didn't make sense.  This little script added all of my files to the database without my participation, but it is slow, took about 30 min I think.

2.1 

2.1 Write a launch program (called mine 'pollPDB')

2.1.1 Open a text editor ```
gedit pollPDB
```

2.1.2 Paste the following into the file:
```
#!/bin/bash
#
# Run this script to cause iSilo, used under wine to probe the listed directory for all files with the pdb extension.
#
#---------------User Input Area------------------------
iSiloApp="$HOME/.wine/drive_c/Program Files/iSilo/iSilo/iSilo.exe"
pdbDirectory="$HOME/Ebooks/iSilo/"
pauseLength="3"
#---------------End User Input Area--------------------
#
#
#
ls "$pdbDirectory"*.pdb > pdbList
while read pdbFile; do
	rename=$(echo "$pdbFile" | sed -e 's/^/z:/' -e 's/\\//g')
	"$iSiloApp" "$rename"&
	sleep $pauseLength
	killall iSilo.exe
done < pdbList
```
Edit 'pdbDirectory' to match where you would like to search.  If you have organized all of your .pdb files into subdirectories you can change ```
ls "$pdbDirectory"*.pdb > pdbList
``` to ```
ls "$pdbDirectory"*/*.pdb > pdbList
```, or run this code for each sub directory where you have files.

I have found that with a sleep interval lower than 3 iSilo sometimes does not stay open long enough to categorized all documents.  Maybe different on your system.

save and close the file.

2.1.3 Make the file executable. [PHP]chmod +x probePDB[/PHP]

2.2 Run the executable.  In a terminal type ```
./probePDB
```

2.3 Watch iSilo appear and disappear repeatedly for each file that is found.  

2.4 Open iSilo and test 'Open Categorized'.

Hope it worked for you.

---

