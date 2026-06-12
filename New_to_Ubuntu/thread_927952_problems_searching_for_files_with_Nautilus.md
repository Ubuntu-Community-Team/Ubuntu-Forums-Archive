---
title: "problems searching for files with Nautilus"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-09-23
I have used the nautilus file browser to search for specific files that are in my NTFS (Windows) partition, and I have no problems finding the files that I want. For example, if I search for .exe files in the NTFS partition, I get a list of all the .exe files.

When I do the same thing, but I search in the ext3 (Ubuntu) partition it does not work. For example, if I search for all the .svg files in the ext3 partition, the search process starts, but after about 10 seconds, the screen goes blank, and nautilus restarts in the /home/jim directory. (I started the search for .svg files in the / (root file system), but I get no results at all.)

It appears the there may be something wrong with my ext3 partition, since the exact same search procedure works fine when I search the NTFS partition.

Does anyone have any ideas how to fix this problem?

JBA2337

---

### Post by AmitT on 2008-09-23
you can try to search with the tracker search tool.
it works well for me.

---

### Post by terry_gardener on 2008-09-23
try using the terminal 

command 

locate filename 
locate *.png (to find all files with extension)

---

### Post by nowshining on 2008-09-23
try putting a * in front of the item u want to find and at the end example *puppy*

---

### Post by JBA2337 on 2008-09-23
> **nowshining said:**
> try putting a * in front of the item u want to find and at the end example *puppy*
I tried that, putting * in front and behind my search term, and it did not work. Did not find anything.

Earlier this week I was using nautilus to search for certain types of files. What I was searching for was image files, such as files ending in .png, .svg, .gif, or .jpg.

For several days, when I searched for .svg or .png or .jpg, Nautilus would find anywhere from 300 to 1,900 files.

Something has changed, because now if I search for any of these terms, nautilus starts looking, and then all of a sudden, the screen goes blank, and I am returned to /home/jim, with none of the files being found. 

As I said, nautilus search was working fine earlier this week, and now I can't search for anything. I must use nautilus to do these searches, because I need to copy some of these files. The other search tools that are part of Ubuntu do not allow me to copy any of the files that they find.

Any other ideas?

JBA2337

---

### Post by nowshining on 2008-09-23
> **JBA2337 said:**
> I tried that, putting * in front and behind my search term, and it did not work. Did not find anything.

Earlier this week I was using nautilus to search for certain types of files. What I was searching for was image files, such as files ending in .png, .svg, .gif, or .jpg.

For several days, when I searched for .svg or .png or .jpg, Nautilus would find anywhere from 300 to 1,900 files.

Something has changed, because now if I search for any of these terms, nautilus starts looking, and then all of a sudden, the screen goes blank, and I am returned to /home/jim, with none of the files being found. 

As I said, nautilus search was working fine earlier this week, and now I can't search for anything. I must use nautilus to do these searches, because I need to copy some of these files. The other search tools that are part of Ubuntu do not allow me to copy any of the files that they find.

Any other ideas?

JBA2337

i've always had problems searching with nautilus myself - when i used gnome it took up a lot of cpu and slowed things down to a crawl on my P4, luckily konqueror only does that if also check in subfolders is checked but it only slows the cpu down at a lower amount than nautilus did..

---

### Post by JBA2337 on 2008-09-23
Earlier this week I was using nautilus to search for certain types of files. What I was searching for was image files, such as files ending in .png, .svg, .gif, or .jpg.

For several days this wwek, when I searched for the terms .svg or .png or .jpg, nautilus would typically find anywhere from 300 to 1,900 files.

Something has changed, because now if I search for any of these terms, nautilus starts looking, and then all of a sudden, the screen goes blank, and I am returned to /home/jim, with none of the files being found. 

If I search on my NTFS (Windows) partition, nautilus search works fine, as it should. But if I search on my ext3 (Linux) partition, nautilus does not work.

As I said, nautilus search was working fine earlier this week, and now I can't search for anything. I cannot use another search tool either. I must use nautilus to do these searches, because I need to copy some of these files. The other search tools that are part of Ubuntu do not allow me to copy the files that they find.

Using synaptic package manager, I reinstalled nautilus, and this did no good.

Does anyone have any idea how to fix this problem?



JBA2337

---

### Post by Rocket2DMn on 2008-09-23
Threads merged - please do not create duplicate threads, it is not fair to those trying to help you, and doesn't get you more or better help.  Thank you.

---

