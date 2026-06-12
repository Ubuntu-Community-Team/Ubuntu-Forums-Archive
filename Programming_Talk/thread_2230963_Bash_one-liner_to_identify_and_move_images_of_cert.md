---
title: "Bash one-liner to identify and move images of certain size"
date: 2014-06-22
forum: Programming Talk
---

### Post by pmorton on 2014-06-22
Can anyone help me with thi? I want to search the directory tree for all .jpg files, use Imagemagick's "identify" command to find all those whose size is 300x300 pixels, and move such files to a particular directory. I'm convinced a one-liner will do the job, but my bash skills are not up to it.

---

### Post by steeldriver on 2014-06-22
Something like

```

while read -r w h f; do 
  (($w==300)) && (($h==300)) && echo mv -t "path/to/dest/" "$f"
done < <(find path/to/src -iname '*.jpg' -exec identify -quiet -format "%w %h %d/%f" {} \;)

```

maybe

---

### Post by pmorton on 2014-06-22
I've now tried that but it's not doing the job.  The identify command outputs not just the file name but a long string of other information, so it's not suitable for feeding raw into the do loop.

---

### Post by steeldriver on 2014-06-22
Hmm... maybe you have a different version? the [FONT=courier new]**-format "string"**[/FONT] option isn't very well documented but you could try %M for the filepath instead of %d/%f

---

### Post by ofnuts on 2014-06-22
As true one-liner:
```

find -type f -iname '*.jpg' -exec identify -quiet -format "%d/%f"$'\t'"%wx%h" {} \; | grep "300x300$" | cut -f 1 | xargs -d '\n' mv -t $thedir

```

In slow motion:
[LIST]
[*]find all .the .jpg 
[*]use identify to output "directory/name[tab]widthxheight" for each file 
[*]filter this with grep to keep only the lines ending with requested widthxheight 
[*]cut the line (on the tab) to retain the first item: file path/name 
[*]use xargs to feed all these this to "mv -t" 
[/LIST]

Code above will work with spaces in file names...

---

### Post by pmorton on 2014-06-22
Ok, here's what did the trick, identifying all .pnf files size 300x300 pixels and moving them into another directory:

#!/bin/bash
while read -r file; do 
mv -t "./NewDirectory" "$file"
done < <(find ./ -iname '*.png' -exec identify -quiet -size 300x300 -format "%M" {} \;)

Thanks for your assistance with that!

(that daft smiley is a semi-colon plus a close bracket - perfect illustration of why these things should be banned).

---

### Post by ofnuts on 2014-06-22
If you put your code within ```
 brackets (see the "#" icon in the full editor), parenthesies are not interpreted as smileys:

[code]#!/bin/bash
while read -r file; do 
mv -t "./NewDirectory" "$file"
done < <(find ./ -iname '*.png' -exec identify -quiet -size 300x300 -format "%M" {} \;)
```

But I don't understand how your code works, my version of Identify (V6.7) doesn't use the -size parameter as a filter(*) and the ImageMagikc site (v6.8) doesn't document it as working that way either. So your code above should be returning all files, independently of size...

(*) "identify -size 400x400" and  "identify -size 300x300" both have a 0 return code on a 400x400 image.

---

### Post by pmorton on 2014-06-23
Ha - you are quite right, ofnuts. My code hasn't isolated files size 300x300 at all! Also, I had to sed the files to remove spaces before running my script. Now, I'm going to start again and try yours.

---

### Post by pmorton on 2014-06-23
Yes, that's it; working perfectly. Fantastic one-liner, and handles spaces in file names, as you say. Many thanks for your help.

---

