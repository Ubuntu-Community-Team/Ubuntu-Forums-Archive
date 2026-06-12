---
title: "lame output file extension"
date: 2008-03-30
forum: Programming Talk
---

### Post by midlifecrisis on 2008-03-30
I'm trying to write a script that will resample mp3's. so far i have this:

#!/bin/bash
for f in *.mp3 ; do
  fileout="$f" | sed 's/.mp3//g'
  lame -b 96 "$f" "$fileout"	
done

but this outputs files with a name of <filename>.mp3.mp3

I'm trying to get the files named <filename>_ipod.mp3 but for the life of me I can't figure it out, I have googled for help but I'm coming up short.

Ideally, I'd like the ouput file in an ipod subfolder and the files with the original name.

This is to create mp3's for my shuffle so there is no problem with the id3tags being stripped out by lame.

Thanks for any help

---

### Post by ghostdog74 on 2008-03-30
indent your code. also put them in [ code ] tags

```

#!/bin/bash
for f in *.mp3 ; do
   fileout=$(echo "$f" | sed 's/.mp3$//g')
   lame -b 96 "$f" "$fileout"
done

```
alternatively, use bash's own string manipulation without sed
```

#!/bin/bash
for f in *.mp3 ; do
   fileout=${f%*.mp3}
   lame -b 96 "$f" "$fileout"
done

```

---

### Post by midlifecrisis on 2008-03-30
cheers, I did indent the code but it's been lost in the post.

Neither of these help as they both produce <filename>.mp3.mp3

I'm trying to remove the duplication of file extensions and include the "_ipod" or create the new file in a subfolder with the original filename.

---

### Post by midlifecrisis on 2008-03-30
I've got it sorted with this:

fn=${f%*.mp3}"_pod.mp3"
lame -b 96 "$f" "$fn"

cool, now onto working with files

Cheers

---

### Post by midlifecrisis on 2008-03-30
this is the final (for now) script

[FONT="Courier New"]
#!/bin/bash
TARGET_DIR=”ipod/”
mkdir -p $TARGET_DIR

for f in *.mp3 ; do
[INDENT]fn=${f%*.mp3}”_pod.mp3&#8243;[/INDENT]
[INDENT]lame -b 96 “$f” “$fn”[/INDENT]
[INDENT]mv “$fn” $TARGET_DIR/[/INDENT]
done
[/FONT]

this resamples mp3’s to 96kbps, for my ipod shuffle. It renames  files as filename_ipod.mp3, creates an ipod folder and moves the resampled file to it.

along this this [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

this seems like the best way to manage an ipod shuffle on ubuntu

Cheers

---

