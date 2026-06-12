---
title: "strange behaviour"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by broomsticks on 2008-05-09
I am posting this because I had a look in the threads and didn't find much.

Since I installed Ubuntu Linux in dual boot, it has been doing a very peculiar thing: randomly the desktop freezes, blocking every operation (and stopping music from, say, amarok) for something like 30-45 seconds. After this, the HD led lights up for a moment and the system starts working again.

I've seen this happening with 7.10 and now with 8.04... so I'm starting to think it could be my pc.

I have at the moment put ubuntu in a 10 GB partition, with a 2gb swap file partition.

I am working on an Asus Portable with a core duo 72300E, and 1 GB of RAM.

I really like working in Ubuntu (when I'm browsing happily) but these moments of downtime really make it quite unusable on the long run.

Anyone has a solution? 

Thanks in advance..

---

### Post by spiderbatdad on 2008-05-09
There could be several possible causes.

Firefox 3 beta 5 has a bug that causes an enormous file to be written into a hidden folder in your home directory: /.mozilla/firefox/something.default/urlclassifier3.sqlite.
The fix (as I understand) is too remove the file and restart Firefox.
Personally, I have switched to Seamonkey for browsing, and am very pleased with it.

Also the trackerd indexing program in Hardy tends to be resource intensive. I kill the process and remove it from start-up options.

---

### Post by broomsticks on 2008-05-09
couldn't be FF 3 because it happened to also in 7.10..

I'll try and see the other solution... wouldn't you be so gentle to tell me how I could do that?

---

