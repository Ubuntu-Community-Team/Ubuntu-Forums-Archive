---
title: "Rhythmbox multiple radio links at once and/or backup"
date: 2009-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by froller on 2009-05-29
Through a few distro upgrades and several rebuilds (as a result of pushing Ubuntu limits :D) I wanted an easier way to recover my radio links within Rhythmbox.  The only solution found was to add them one at a time, tedious, and there was no solution for exporting or backing up the radio links short of hunting down the xml file that held them.  I had hoped that since Rhythmbox accepts http links from the command line I would be able to feed it links from a file in a terminal (which it failed).  What was discovered is this file could be added to the radio list from within the GUI of Rhythmbox.  

Here is a little howto for creating the link file and adding it to Rhythmbox.  This file is handy for backing up as well and thus recovering radio links.  Perhaps there is better way, and if there is please post.

First collect your stations.

open **Firefox**
goto **sky.fm** for example (just my favorite site for online radio.) 
click **View->Page Source**
press **ctrl+a** to select all the code.
open your favorite text editor
paste in a text file and save
from command line run the following:

```
grep -o 'http:[^"]*' source.file |grep /mp3/ |grep -v low >> destination.file
```

Each pipe to grep refines the list, so adjust accordingly.  see:
```
man grep
```
for more information on grep.

When done you should have a file content that looks similar to this:

```
http://www.sky.fm/mp3/smoothjazz.pls
http://www.sky.fm/mp3/uptemposmoothjazz.pls
http://www.sky.fm/mp3/tophits.pls
http://www.sky.fm/mp3/the80s.pls
http://www.sky.fm/mp3/hit70s.pls
http://www.sky.fm/mp3/oldies.pls
http://www.sky.fm/mp3/classical.pls
```

Of course you can manually create your file in a text editor so long as the end results are a single column of routable links.

Then from your desktop:

open **Applications->Sound and Video->Rhythmbox Music Player**
click on **Radio** in the left pane.
click on **Music->Import File...** from the main menu.
navigate to your **"destination.file"**
click **open**

You should see all the links that Rhythmbox will accept in your radio list.  Genre is "unknown" until you listen to the station for the first time.  Hope this helps someone.  Again, if there is an easier way please post.

---

