---
title: "Photo project with imagemagick and bash"
date: 2008-06-25
forum: Programming Talk
---

### Post by rockin_goliath on 2008-06-25
In order to save space on my hard drive, I am in the process of scaling down my collection of 5384 photos to a smaller resolution. I have them all in F-Spot, so they are all three directories deep in my photos folder. I have been able to convert most of them with this command:
```
find . -name "*.jpg" -exec sh -c 'convert -resize 1600x1200 ${1} ${1%\.jpg}.jpg' - {} \;
```
I didn't write this command myself, so I don't really know how it works, especially the file name arguments. Basically, it looks in a directory and all its subdirectories for files with the extension .jpg and scales them down to 1600x1200. The problem with this command is that it doesn't like spaces in the file names, and won't convert them. Renaming the files in any way or changing their directory positions is not an option, because it will screw up the F-Spot database. 

Therefore, it looks like I have two options:

Option #1 (and most preferable): Modify the above command slightly to play nice with files that have spaces in the name.

Option #2: Create a convert command or a bash script that will use the contents of a text file (containing a list of all the file paths) as the input and the output, ie the input file names will be the same as the output file names. Using the "Search" tool in Gnome, I can search for all the files named *.jpg and save the results to a text file, but surprise, the list is generated with spaces in the names. Perhaps there is way to wrap every line in this text file with quotes, maybe with the fmt command? 
For reference, the syntax for the convert command in imagemagick is:
```
convert [input file] [options] [output file]
```
My ideal command would look like this:
```
convert file-paths.txt -resize 1600x1200\> file-paths.txt
```

Would anyone be able to help me with this? Any help you can give me would be greatly appreciated. I am not a programmer, and have only done a little with bash to install media codecs and stuff, so it's exciting to learn how to do more with it. Thank you!

---

### Post by ghostdog74 on 2008-06-25
```

find /fullpath -name "*.jpg" -printf "%f:%p\n" | while IFS=":" read FNAME FPATH
do
 convert -resize 1600x1200 "$FNAME" "$FNAME" #not tested
done

```

---

### Post by timcredible on 2008-06-25
digikam can resize as many photos as you want in a batch process.  install digikam and kipi-plugins via synaptic if you want a nice gui to do this with

---

### Post by rockin_goliath on 2008-06-25
I tried ghostdog74's script, renaming "/fullpath" to "/home/myself/Photos" and the terminal output is "Unable to open (filename): No such file or directory". It does this for every single file, just trolling through them all with that output. I tried moving one of the "$FNAME" items to just after the convert command, but it had no effect.

---

### Post by Xaero252 on 2008-06-25
```
find . -name "*.jpg" -exec sh -c 'convert -resize 1600x1200 "${1}" "${1%\.jpg}".jpg' - {} \;
```
that should work havn't tested it but it should
working on my end, however it doesn't forcefully resize, you might want to look at command line options of resize, this resizes it where it will fit within 1600x1200 without distorting it, ex
1680x1050 images get resized to 1600x1000
2560x1600 images get resized to 1600x1000 as well
etc.. etc..

---

### Post by geirha on 2008-06-25
```
find /path/to/images -name "*.jpg" -exec convert -resize 1600x1200 {} {} \;
```

---

### Post by rockin_goliath on 2008-06-26
Thank you guys for all your help! I was able to get ghostdog74's script to work by replacing the $FNAME in the imagemagick command with $FPATH. The only problem is that it forcefully resized all of my images, ie images at a smaller resolution were scaled up, which I didn't intend. Fortunately I made an archive first. I will test out more of all of your kind suggestions. Thank you so much again!

---

### Post by geirha on 2008-06-26
Ok, this one will use identify to check the size, and only convert if width is greater than 1600 and height is greater than 1200. Should also handle special characters in filenames, like spaces and newlines.
[php]
find /path/to/images -type f -name "*.png" -print0 | while read -d $'\0' file; do 
  if [ `identify -format '%[fx:w > 1600 && h > 1200]' "$file"` == 1 ]; then
    convert -resize 1600x1200 "$file" "$file";
  fi;
done
[/php]

---

