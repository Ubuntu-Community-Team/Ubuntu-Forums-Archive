---
title: "Subversion Integrity Checks"
date: 2007-03-20
forum: Programming Talk
---

### Post by blanky on 2007-03-20
Hey guys I'm working on a Subversion revision downloader for my game. Basically, I want it to check if there are updates and if there are download them. My server has a cron job that checks out the latest revision of my game's **media content** and packages it up using the zip program. At first I was thinking about also creating md5hash files and then having my script check the md5 of each local package and the md5 of each remote package, but as I soon learned, each time I zipped, whether or not I changed anything, the md5 hash was different.

So after some tinkering, I finally settled on the following idea. Before my server would zip the packages, it would run an md5 hash on every file in the folders I would zip with something like this (recursively):

```
find -type f | sed '/.*svn.*/d' | xargs md5sum > md5hash
```

The sed part is to avoid the subversion specific stuff.

Anyways, I then would md5sum the actual output file, so I'd:

```
md5sum md5hash > nameofzip.md5
```

To keep the file small, that is. I would then download the zip. I'd then run my script and have it read the nameofzip.md5 md5hash of the zip I'm checking and compare it to the one inside my zip archive.  If they were different, then I'd wget it.

I have the same problems though. Say I take a hash of all the files, I then zip it. Well, the next time I go to take a hash of all the files, it's different. And yes, I haven't modified the files in any way.

I've been at this for a long time, I'm really desperate and going crazy, do you guys know what I could be doing wrong? Sorry if I'm not being very clear, I'm really tired of repeating myself over and over again to no avail, so if something didn't seem clear please tell me and I'll clarify.

---

### Post by WW on 2007-03-21
Are you running the commands in the same directory where your files are stored, so the files md5hash and nameofzip.md5 are included in the list of files found by the **find** command?  If so, then you *are* changing something, since the md5hash and nameofzip.md5 files will change each time you run the commands.  If that is the problem, you could put md5hash and nameofzip.md5 somewhere else, perhaps /tmp.  Or just delete the files at the approprate time.

---

### Post by blanky on 2007-03-21
THAT'S EXACTLY WHAT I WAS THINKING HAHAHA. I just thought of that right now while working out, and I tried to do something else and I became more convinced that that was the problem. I'll check right now man!

**EDIT**: I'm not sure, because I supposedly deleted them after using them, so they shouldn't have still been there after I did the find command once more, or does this happen even when I do it the first time? Here's a snippet of the packaging script:

```

# maps.pk3
echo "Packaging maps.pk3..."
cd maps/
find -type f | sed '/.*svn.*/d' | xargs md5sum > md5hash
md5sum md5hash > maps.pk3.md5
rm md5hash
zip -r maps.pk3 . -x \*svn\* -x \*dolphinview\* -x \*nfs\* -x \*db\* -X
mv -f maps.pk3 ..
mv -f maps.pk3.md5 ..
cd ..

```

So basically I have a directory called maps/, and I go in and create md5hash, then I md5sum the md5hash file (*To make it a lot smaller, is this legit?*), then I delete the original md5hash, package the files in the maps/ directory ([i[including the maps.pk3.md5[/i]), then move the maps.pk3 and the maps.pk3.md5 files up one level ([i]Yes I know the latter is already within the zip/pk3, but I still also need to ahve a separate copy. Then I move back up on directory.

I really need to hit the bed I'm exhausted from having messed with this problem over and over again, but I'd ***immensely*** appreciate any feedback. Maybe with this information you can see if it really is the problem, I'd test it but I really need to go. Thanks WW! I'll test it tomorrow regardless!

**EDIT**:

> 
since the md5hash and nameofzip.md5 files will change each time you run the commands.


Why is that so? Even if I have the exact same things and I haven't modified anything whatsoever?

---

### Post by blanky on 2007-03-21
I fixed it by moving md5hash to /tmp for the time being, thanks! Still ironing out some bugs.

---

