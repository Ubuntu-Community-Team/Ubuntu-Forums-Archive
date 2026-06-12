---
title: "storing my data in python"
date: 2009-07-31
forum: Programming Talk
---

### Post by ryanhaigh on 2009-07-31
I have a little python script that is generating thumbnails and colour information for about 2000 photos (in time this may grow). Generation of the photos creates a PIL image.

I am trying to figure out the best means of storing the data. At the moment the script stores the path,imgdata (the PIL image in a StreamIO) and the colour infomation in a class. I then create an instance of this class for each image, appending to a dict (path is key) and when finished pickle the whole thing to a file on the disk. The problem with this approach is that I use a whole lot of memory which is really uneccessary as the imgdata doesn't need to be kept while doing most of the processing.

Today I separated the storage but it was obviously still keeping everything in memory till i pickled it. I started looking for a new approach. I tried shove which provides a dict interface to a number of backends and actually looked quite promising but the more I looked the more I thought about using a database as...well a database rather than the key:value store.

So I have started looking into python + db and WOW there are just too many options. One of the things I liked about shove was the ability to change backends really easily, and it seems that sqlalchemy is used for many of these backends, so I have started looking into sqlalchemy as an option (using sqlite for now and moving to mysql/PostgreSQL in the future).

I am basically looking for opinions on the best way to go with this and would appreciate input and constructive criticism.

---

