---
title: "multi user image boot hash value"
date: 2008-12-23
forum: Programming Talk
---

### Post by atisz on 2008-12-23
hi

i have a task to do, but since i am not that familiar with linux systems i am stuck a little bit. could anyone of us give me some advice regarding my problem which is the following

task:
to load user images
each image contains users data and settings
images are stored on a central server
to store the data effectively- hash value on each file
files that is being used by multiple users are stored only once
detect the match using the hash value of each file


advice i was given:

to create a skeleton of a filesystem with 0kb files and then load the contents of each file
to skip some folders: proc, media, sys, dev

- i think of doing this like each user image contains just the 0kb filesystem structure and than it loads the content of each file - this would let us to store the similar files only once

any advice or help regarding some scripts would be appreciated

thank s for reading

have a nice day
bye

---

