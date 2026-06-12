---
title: "[SOLVED] shell script that searches /home for a file"
date: 2007-11-07
forum: Programming Talk
---

### Post by mdpalow on 2007-11-07
Hello,

Can someone pls help me with a problem?

I'd like to find the code needed to search an ENTIRE /home directory for a file.

I'm not sure what I have is written correctly, but it does work; it just won't do everything I want.

Here's what I have:

find /home/$USER/some_file.txt -print | while read obj

I'm only showing one line of this code just to keep this msg short.

However, it only searches the $USER directory and not all the other folders within. I want to make it search all the directories within the $USER.

Can someone write an example of how it should be?

Thank you in advance..

---

### Post by enatiello on 2007-11-07
I tried find on my machine it appears to recurse during the search without any command line switches.  So, you could try something like this:

find /home/* -name "*somefile*"

if you have a list of users dirs you want to search, instead of all of them, you could try:

for i in `john ringo paul george`; do echo $i; find /home/$i -name "*somefile*"; done

---

### Post by mdpalow on 2007-11-07
enatiello,

thank you for this. Perfect answer and it worked.

Geez! I thought it was something completely different.

take care...

---

