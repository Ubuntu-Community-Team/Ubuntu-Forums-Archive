---
title: "Howto: merge OpenMedSpel with your standard OpenOffice.org dictionary"
date: 2010-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by rimshot4 on 2010-05-13
There's a known bug wherein OpenMedSpel will not work properly in Ubuntu Karmic (and by extension, Linux Mint 8). (See [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/329968](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/329968)) If you can install the extension, and select the OpenMedSpel dictionary, the spellcheck underlines all of your non-medical words even though you have not deactivated your standard dictionaries. This is a workaround. I have posted it to Launchpad bug thread and will post it in Linux Mint forums as well.

This method has only been tested under Linux Mint 8 Helena, but should work with Ubuntu Karmic and other Ubuntu and Mint releases as well. I used it for US English, but there's no reason you can't use it in your standard dictionary language of choice. 

1. Download OpenMedSpel's txt and csv file in .zip format by visiting [http://www.e-medtools.com/openmedspel.html](http://www.e-medtools.com/openmedspel.html) and clicking on the link at the bottom of the page (or download directly from this link: [http://www.e-medtools.com/openmedspel100.zip](http://www.e-medtools.com/openmedspel100.zip))

2. Extract the files from the archive. Open en_US_OpenMedSpel.aff with gedit. Use Cntrl+A to highlight all of the text, and Cntrl+C to copy it to the clipboard.

3. Backup the original dictionary. You can do this by renaming /usr/share/dict/american-english to american-english.bac. You will need root privileges. Then open the file you just renamed, as root, and save it as american-english.

4. Paste the the contents you copied into the file. Now the file isn't alphabetized, but that shouldn't matter. Save the file and exit.

5. Test your new dictionary by opening OpenOffice writer and typing "Zophran." Then right-click on the word. It should offer you "Zofran." 

Bingo! If you need to undo the changes, simply delete american-english and rename american-english.bac to american-english. 

I'm a bit of a newbie myself so I'm not comfortable posting the terminal commands for making this happen. If anyone wants to modify my little tutorial, feel free!

---

