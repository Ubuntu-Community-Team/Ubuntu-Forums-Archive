---
title: "Basic Bash Loop Fails Help."
date: 2008-03-19
forum: Programming Talk
---

### Post by Gen2ly on 2008-03-19
I admit this is my first loop.  From what I've read this is the right way to create a loop but the loop only runs once and quits.  I believe this has something to do with the variable-reference.

What I'm looking to do is create a script that I can type

```
command *.png
```

and all pngs will be run through the script.  Here's the script:

```
#!/bin/bash
# resize-image-new - makes new image and resizes.
# http://www.imagemagick.org/www/command-line-options.html

# Fixes / ToDo
# add ability to subtract enhance flag
# add looping: resize-new-image 400 *.png

SIZE=$1
NAME=$2
COLORS=2048
DEPTH=16
RESIZEDNAME="${NAME%.*}"-"$SIZE".png
#ENHANCE - options to enhance image -enhance smoothes rough images

if [[ -z $NAME ]]; then
    echo "resize-image <WIDTHxHEIGHT> <original-image>"
    exit;
fi

# Convert (SIZE is proportional least value is used and only x needs specifid.)
# Compress PNG

for i in "$NAME"; do
    convert -resize "$SIZE" -enhance "$NAME" "$RESIZEDNAME"
    mogrify -colors $COLORS -depth $DEPTH "$RESIZEDNAME"
    optipng -o5 "$RESIZEDNAME" 
done
```

The script works fine by typing:

```
command picture.png
```

However specifying *.png will only loop once.  What am I notunderstandigng here?

---

### Post by Quikee on 2008-03-19
If you have pictures 1.png, 2.png and 3.png, specifying "command *.png" will execute "command 1.png 2.png 3.png".

What you will need to do is loop through input arguments the following (or any other) way:

[PHP]for i in "$*"; do
   echo $i
done[/PHP]

---

### Post by Gen2ly on 2008-03-19
hmm, this is going to required a more involved process.  I actually have set another variable before the filename

```
resize-image-new size filename.png
```

so using "$*" isn't going to work as it will grab "size filename.png" hmm,  any idea?  My initial thought is to use "$*" and then bash filter out size.  Would that do it?

---

### Post by Quikee on 2008-03-19
> **Dirk.R.Gently said:**
> hmm, this is going to required a more involved process.  I actually have set another variable before the filename

```
resize-image-new size filename.png
```

so using "$*" isn't going to work as it will grab "size filename.png" hmm,  any idea?  My initial thought is to use "$*" and then bash filter out size.  Would that do it?

I am not a bash expert but I would do something like this then:

[PHP]count = 0
for i in "$*"; do
    if [ $count != 0 ]; then
      do except for first argument 
    fi
    let count = count + 1
done  [/PHP]

---

### Post by mssever on 2008-03-19
After getting the first value (size or whatever), use the shift command to knock it off the list of positional parameters. Then, ```
for i in "$@"; do
    #do something with "$i", making sure to always put it in double quotes
done
```Note "$@" instead of "$*". $* in quotes expands all positional parameters to a single string, while $@ in quotes keeps the parameters separate.

---

### Post by Gen2ly on 2008-03-21
hmm, I'm going to have to learn more about bash.  I'm reading what looks like to be a pretty [good guide]("http://wooledge.org:8000/BashGuide").  Thanks for pointing me in the right direction.  I'll see what I can figure out.

---

### Post by zippaplick on 2008-03-21
Look at the shift command for bash for a simple way to pick off the cmd line args.
This snippet will pick off the first arg then loop through the rest.


```

#!/bin/sh
echo "SIZE: $1"
echo "THE PNGs:"
shift
while [ $# -gt 0 ] ; do   
    # do something interesting with each png
    echo $1
    shift
done

```

---

