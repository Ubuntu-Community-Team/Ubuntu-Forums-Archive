---
title: "How to clean up your MP3 tags using Rhythmbox and EasyTag"
date: 2011-03-17
forum: Outdated Tutorials &amp; Tips
---

### Post by singmajesty on 2011-03-17
Hi everyone,

I had my share of grief today as I attempted to clean up the tags in my music collection, but now that I've gone through the paces myself I wanted to help share it.

First off, my favorite Linux application I've used for tagging is EasyTag, which is available from the software center. It is very handy to populate tags from filenames, or to correct file names from tags, or to easily apply similar tags to multiple tracks.

A couple tips if you use it yourself: when you select multiple tracks and wish to apply a changed parameter to all the tracks you have selected, make the change then click the small round circle next to that property. Otherwise it only applies to one track. Also, clicking the "Help" button for the "Fill Tags" or "Rename Files and Folders" scanners will give you the shortcuts for artist, title, track number and more. Very helpful. When you have a scanner set up correctly, be sure to click the green icon in the scanner window to apply those settings to your selection. Then use Ctrl+S to save your changes to the files. You can make it save files without asking by going to Preferences.

The next problem you'll face is Rhythmbox's logical, yet illogical ordering of tags when processing files. Rhythmbox appears to read tags in the order in which they appear in the file. Unfortunately, this means that it will read ID3v2, ID3v1, then APE, in that order. If you're like me, and want to use EasyTag to update your file, that means that ID3v2, the most important tag, gets the lowest priority.

If you would like to remove the APE tags from your files, so the ID3 tags can show in Rhythmbox, try this script:

```
#! /usr/bin/env python
# -*- coding: utf-8 -*-

# Copyright (C) 2011 - cenyongh <cenyongh@gmail.com>
#

import os

def cleanup(file_path):
    file = open(file_path,'rb')
    
    content = file.read() 
    i = content.find('APETAGEX')
    if i != -1:
        print 'cleanup %s' % file_path
        file = open(file_path,'wb')
        file.write(content[:i])
        file.close()

if __name__ == '__main__':
    BASE_DIR = '/storage/Media/Audio/Music'
    for dirpath, dirnames, filenames in os.walk(BASE_DIR):
        for filename in filenames:
            cleanup(os.path.join(dirpath,filename))
```

... save it to a file on your machine (like ~/remove_ape_tags.py) and run it from a terminal (python ~/remove_ape_tags.py)

Lastly, you may also consider removing the ID3v1 tags from your files, if they give you trouble. Somehow my ID3v2 tags got updated, but the ID3v1 tags were still old. I opened up EasyTag, unchecked the option in properties for ID3v1, then saved all the files. If it won't let you save, you can try doing something small to all the files, like adding a URL value, then removing it.

I hope this helps! It feels ridiculous to have had so much pain getting my tags to show up correctly, but alls well that ends well. Best of luck!

---

### Post by Thund3rstruck on 2011-03-18
You may want to check out [MP3Tag.de]("http://www.mp3tag.de/en/") in Wine. I've used it for years to clean-up tags based on directory (and like a million other filters). 

Custom solutions are always awesome though! Thanks for the share!

---

### Post by Arabica Bean on 2011-03-18
Have a look at Musicbrainz' Picard, and MP3Diags in the repos. Must have tools in my book.

---

