---
title: "Music Organization"
date: 2009-05-11
forum: Programming Talk
---

### Post by prem1er on 2009-05-11
I'm beginning to learn python and for my first project I wanted to write a script to organize my music collection. As of now, all the music I download and rip is stored on one partition in a big unorganized mess (used for sharing).  Any time I add something new to this directory I copy the files to another partition in an organized structure (/music/Artist/Album(organized by year)).  For my script I was planning on reading through my unorganized directory and looking for new files.  I would then move into any new files and read the ID3 information from the first mp3.  I would parse out the useful data and then copy the file to the correct location on the other partition.  My questions are these.  

1. Mutagen seems like the most well documented tool for reading id3 tags in python. It just seems like I won't need most of its features, as I don't need to read formats besides MP3 and also don't have to write any ID3 tags.  Is there anything else out there that someone could suggest for this task?

2. Does my logic seem appropriate in getting the correct information from the mp3's?

Thanks

---

### Post by johnl on 2009-05-11
I have not used mutagen so I can't recommend one over the other :) but when I was doing something similar I used [this module](http://id3-py.sourceforge.net/)  which is available in the repos as 'python-id3'.  It was pretty simple to use.

Cheers.

---

### Post by prem1er on 2009-05-11
Thank you will look into it.

---

