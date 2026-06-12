---
title: "Pattern matching of variable in bash"
date: 2009-01-02
forum: Programming Talk
---

### Post by grandars on 2009-01-02
First off: This is a problem I've run into on Mac OS 10.5.6, but bash is bash (almost) and this is rudimentary:

I have this script:

```

#!/bin/bash 

FILENAME="$1"

# filename must have movie extension
if [[ ! "$FILENAME" == *.{avi,mkv,mp4,mpg,mov} ]]; then
        echo "$FILENAME does not appear to be a movie file."
        exit
fi

```

And this happens:

```
dave@hal $ ./movkind tele.avi
tele.avi does not appear to be a movie file.

```

Why? I thought my *if* would only stop filenames **not** ending in .avi, .mkv etc...

---

### Post by Max Carey on 2009-01-02
When you use the == and != operators inside [[ ]], bash uses fairly simple pattern matching (not regular expressions). The { } syntax is not recognized, so you are simply trying to match the string literal "{avi,mkv,mp4,mpg,mov}". See [http://www.gnu.org/software/bash/manual/bashref.html#Pattern-Matching](http://www.gnu.org/software/bash/manual/bashref.html#Pattern-Matching)

You can use the =~ operator to test for regular expressions, i.e.

```
if [[ ! "$FILENAME" =~ ^.*\.(avi|mkv|mp4|mpg|mov)$ ]]; then
  echo "$FILENAME does not appear to be a movie file."
  exit
fi
```

---

### Post by ghostdog74 on 2009-01-02
use case,esac construct
```

case "${FILENAME##*.}" in
 avi|mp4|mkv|mov ) 
    echo "video file";;
esac

```

---

