---
title: "Thumbnails &amp; Bluefish"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by toothwright on 2012-07-25
I have been using bluefish in 12.04 for simple HTML for a few weeks and found it ideal for my purpose.
 
I have had no difficulty inserting thumbnails before but now some images refuse to play ball.

If I use dialogs to insert a thumbnail (using a 2mb jpg) the code is inserted correctly but the thumbnail image is not formed in the directory and therefore there is no display when the HTML is run.

I thought it might be related to file size but if I scale the original image (to say 500kb) and try to use the dialog to insert a thumbnail from the smaller target it still doesn't work.

My work-around is to make a thumbnail of the 2mb image in GIMP and save it in the image directory and the HTML then works properly.

Am I making some crass operating error in bluefish that can easily be corrected by a more experienced poster?

---

### Post by ads52 on 2012-08-12
You might be interested to see the changelog for the latest version of Bluefish, I have highlighted the relevant section:

```

The file changelog can be obtained from subversion using the `svn2cl' utility. 
The release changelogs are also available from our homepage: 
http://bluefish.openoffice.nl

[COLOR=Red]*** 2.2.3 ***[/COLOR]

Bluefish 2.2.3 has mostly many minor bugfixes and many minor enhancements. There
are only few major changes: a corrupted state in the syntax scanner that could
lead to a segfault was fixed, code folding had major fixes and improvements,
search had major fixes, and a lorem ipsum generator was added. The GUI was
restructured in some areas, and some shortcut key combinations were added. Some
visibility features were added such as a bigger cursor and cursor highlighting,
and some options were improved such as zoom and the custom colors. External
commands had some changes such as better cursor positioning after a filter has
been used, user supplied arguments for external commands, and an option to
restore the default settings. On the multiplatform front: the broken shortcut
key S was fixed on OSX, and file recovery was fixed on Windows. On the web front
some dialogs were added for HTML5,[COLOR=Red]** the thumbnail generator was fixed,**[/COLOR] and insert
color, path and relative path have been added. Many language files were
improved, and more user configurable options have been added to most language
files. You can now select a block of text by dragging the mouse in the margin,
and move the selected block with <ctrl><up> and <ctrl><down>.   

```so perhaps an upgrade might fix the problem? There is an Ubuntu Community Document that would be helpful to you perhaps:

[https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu](https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu)

All the best with this :).

---

