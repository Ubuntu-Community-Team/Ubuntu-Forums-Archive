---
title: "shell script and need width and height of an image"
date: 2005-07-15
forum: Programming Talk
---

### Post by audax321 on 2005-07-15
Hello,

  I'm writing a shell script and need to get the width and height of an image. I have imagemagick installed and tried to do:

image_properties=$(identify image.jpg)

but, the output that gets put in the variable is formatted as follows:

image.jpg JPEG 318x209 DirectClass 18kb 0.000u 0:01


It has the size in it, but I have no idea how to get it from there. Any help is appreciated.

Thanks  :)

---

### Post by audax321 on 2005-07-15
Okay, I found that I could do it like this:

echo $image_characteristics | { read first second third fourth fifth sixth seventh; echo "$third"; }

but the problem now is that if the filename has spaces, the image size isn't always the third item.

---

### Post by tomchuk on 2005-07-15
Something like this should work most of the time, it's a bit ugly but seems to work alright:

```

#!/bin/bash


function die() {
    echo -e "${1}"
    exit 1
}

# check that user entered proper number of args
if [[ "${#}" -ne "1" ]]
then
    die "Usage: $0 <image>"
fi

IMAGE="${1}"

# check that file exists
if [[ ! -f "${IMAGE}" ]]
then
     die "File not found: ${IMAGE}"
fi

# grab the identify string, make sure it succeeded
IMG_CHARS=$(identify "${IMAGE}" 2> /dev/null) || die "${IMAGE} is not a proper image"

# grab width and height
IMG_CHARS=$(echo "${IMG_CHARS}" | sed -n 's/\(^.*\)\ \([0-9]*\)x\([0-9]*\)\ \(.*$\)/\2 \3/p')

WIDTH=$(echo "${IMG_CHARS}" | awk '{print $1}')
HEIGHT=$(echo "${IMG_CHARS}" | awk '{print $2}')


echo -e "W: ${WIDTH}   H: ${HEIGHT}"

```

---

### Post by audax321 on 2005-07-15
Thank you that worked very well. Although if its not too complicated, could you explain what the expression with the sed command means and how it is formatted. The sed manual page doesn't say much about how to write that.

Thanks  :)

---

### Post by tomchuk on 2005-07-16
sure...

The command was: sed -n 's/\(^.*\)\ \([0-9]*\)x\([0-9]*\)\ \(.*$\)/\2 \3/p')

**sed** the program
**-n** run quiet, don't print anything
**'...'** sed command is surrounded in single quotes

**s/.../.../** sed syntax for search/replace, it means replace the first ... with the second ...
**\(...\)** escaped parenthesis contain individual bits of regex patterns
**\(^.*\)** match the start of the line (^) then anything (.*)
**\ ** match a space ("\ ")
**\([0-9]*\)** match any number (*) of digits ([0-9])
**x** match an 'x'
**\([0-9]*\)** again, match any number of digits
**\ ** again, match a space ("\ ")
**\(.*$\)** match anything (.*), up to the end of the line ($)
**/** this is the end of the "search" expression and the beginning of the replace expression
**\2 \3** replace everything with \2 \3 which match what corresponds to the second and third regexes contained in paranthesis: the width and the height.
**/** the end of the s/.../.../ statement
**p** print what you end up with

sed and regex is a mess to look at and try to understand, but once you get the hang of it, it's not too bad. Let me know if you need any more clarification.

---

### Post by audax321 on 2005-07-16
Thanks, I think I get it. Had to stare at it for awhile, but it makes sense.   :)

---

### Post by LordHunter317 on 2005-07-16
That messy sed script could be replaced with something cleaner:```
IMG_CHARS=`identify "$1" | cut -f 3 -d' '`
WIDTH=`echo $IMG_CHARS | cut -d'x' -f 1`
HEIGHT=`echo $IMG_CHARS | cut -d'x' -f 2`
```

---

### Post by tomchuk on 2005-07-17
Much cleaner, except:
```

$ ls
image 1.jpg  image1.jpg
$ identify "image1.jpg" | cut -f 3 -d' '
133x182
$ identify "image 1.jpg" | cut -f 3 -d' '
JPEG

```

---

### Post by poptones on 2005-07-17
That may be cleaner, but your explanation up there of regular expressions was awesome. If you can find the time, you should write a tutorial. I have **never** found a good tutorial online dealing with regular expressions (and I don't feel qualified to write one myself).

---

### Post by smoon on 2005-07-17
[QUOTE=poptones]That may be cleaner, but your explanation up there of regular expressions was awesome. If you can find the time, you should write a tutorial. I have **never** found a good tutorial online dealing with regular expressions (and I don't feel qualified to write one myself).[/QUOTE]

I always found this very useful [http://www.regular-expressions.info/](http://www.regular-expressions.info/).

---

### Post by poptones on 2005-07-18
Awesome link, thanks smoon.

---

