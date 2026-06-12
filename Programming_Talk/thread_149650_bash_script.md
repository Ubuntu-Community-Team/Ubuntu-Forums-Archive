---
title: "bash script"
date: 2006-03-24
forum: Programming Talk
---

### Post by vladuz976 on 2006-03-24
hi i am trying to write a shell script to resize my pictures and create thumbnails so i can rsync my picture directory up to the server.

when i use ```
find . -name "*.jpg" -print
```
in the command line it nicely prints all the files that i want to edit.
like this 
```

./germany2005-2006/cimg0426.jpg
./germany2005-2006/cimg0428.jpg
./germany2005-2006/cimg0429.jpg
./germany2005-2006/cimg0430.jpg
./germany2005-2006/cimg0431.jpg
./germany2005-2006/cimg0432.jpg
./germany2005-2006/cimg0433.jpg
./germany2005-2006/cimg0440.jpg
./germany2005-2006/cimg0441.jpg
./germany2005-2006/cimg0445.jpg
./germany2005-2006/cimg0448.jpg
./germany2005-2006/cimg0449.jpg
./germany2005-2006/cimg0451.jpg
./germany2005-2006/cimg0452.jpg
./germany2005-2006/cimg0454.jpg
./germany2005-2006/cimg0455.jpg
./germany2005-2006/cimg0456.jpg

```
some how this doesn't work when i use it in the script, no thumbnails are created. the binary work when i use it outside of the script. 

anybody any clues?
```
#!/bin/bash
#shell script for resize
for i in `find . -name "*.jpg" -print`;
do imlib2_convert "$i" -scale 80x60 "thumb-${i}"

done

```

---

### Post by rupert on 2006-03-24
i used the following script to resize and convert some pictures for a webpage,
just play arround with it and strip the things out you dont need.
It uses imagemagiks convert

```

#!/bin/bash
#

# wechsel in die Ordner
WD=$(pwd)
find -type d | while read dir; do
cd "$dir"
#  ls *.png

# resize
Oname="${PWD##*/}"


i=1;
for file in *.png;
do
   filename="$Oname""_shot""$(printf "%03d" $i)"".png"
   mkdir thumbnails
   mkdir shots
   mv "$file" tmp_"$file"
   /usr/bin/convert -size 240x160 tmp_"$file" -resize 240x160! -type Palette -colors 128 +profile "*"  "thumbnails/$filename"
   /usr/bin/convert -resize 480x320! -type Palette -colors 128 tmp_"$file" "shots/$filename"
   rm tmp_"$filename"
   #mv tmp_"$file" shots/"$filename"
   #mv "$file" "$filename"
   ((i++))
done

cd "$WD"
done
exit 0

```

---

### Post by vladuz976 on 2006-03-24
where did you find that script? or did you write it yourself?

---

### Post by rupert on 2006-03-24
some parts are from other scripts i found googeling and some parts I wrote myself using the convert man page,
you can remove the mkdir and pathes before the $filename to create the thumbs in the current directory

---

