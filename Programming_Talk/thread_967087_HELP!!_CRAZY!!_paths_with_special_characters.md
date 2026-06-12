---
title: "HELP!! CRAZY!! paths with special characters"
date: 2008-11-01
forum: Programming Talk
---

### Post by kakyoism on 2008-11-01
In a bash script, I wanted to use mencoder to extract specific part of a movie. See below
```
#! /bin/sh

fn=$1
st=$2
et=$3

echo $fn

mencoder -ss $st -endpos $et -ovc copy -oac copy $fn -o out.avi

```

However, when the input path ($fn) contains "-" or SPACE, mencoder just can't get the path right.

I tried to add double-quotation marks to it, in the script or on the fly with the input argument; neither worked.


This problem has driven me crazy for ages. Every time I thought double-quoting could clear my way it just blows here and there...


Help!!!

---

### Post by unutbu on 2008-11-01
Have you tried
```

#! /bin/sh

fn=$1
st=$2
et=$3

echo $fn
mencoder -ss "$st" -endpos "$et" -ovc copy -oac copy "$fn" -o out.avi
```
And also double-quoting the filename on the command line? I think you need to do both.

---

### Post by kakyoism on 2008-11-01
I did! It didn't work!

---

### Post by ghostdog74 on 2008-11-01
you will have to put quotes when you pass arguments to your script
```

./myshellscript.sh "first argument" "second"

```

---

### Post by kakyoism on 2008-11-01
Thx, but I did add quotes to my argument as you said....
That's why I'm asking...

---

### Post by ad_267 on 2008-11-01
Try this:

```
#! /bin/sh

fn="$1"
st="$2"
et="$3"

echo $fn
mencoder -ss "$st" -endpos "$et" -ovc copy -oac copy "$fn" -o out.avi
```

and then use quotes when calling the script.

---

### Post by ghostdog74 on 2008-11-01
don't just say "it doesn't work". Show us how is it that is doens't work. Errors, input samples, output formats , what you did, how you execute etc... anything that will help us to help you. we are not psychics.

---

### Post by kakyoism on 2008-11-01
Sorry guys, I thought this would be an obvious problem to you experts so I wasn't careful enough to give all the data.

BTW: my locale is Mandarin. Even my original script works with paths containing Mandarin characters, but here in the example there are Japanese characters, then even the revised version does not work!

This is my output with the revised script 


<Script>
----------
fn=$1
st=$2
et=$3

echo $fn
mencoder -ss "$st" -endpos "$et" -ovc copy -oac copy "$fn" -o out.avi


<Output>
----------------------------------------
kakyo@kakyo-laptop:/media/USB-DOWNLOAD/torrent/New Comer &#25105;&#30340;&#30005;&#24433;$ cut_movie.sh "&#23665;&#23822;&#33310; - New Comer.avi" "00:00:00" "00:31:00"

&#23665;&#23822;&#33310; - New Comer.avi
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: '&#23665;&#23822;&#33310; - New Comer.avi'
Failed to open &#23665;&#23822;&#33310; - New Comer.avi.
Cannot open file/device.


BTW: my locale is Mandarin. Even my original script works with paths containing Mandarin characters, but here in the example there are Japanese characters, then even the revised version does not work!

---

### Post by geirha on 2008-11-13
Could you add a line
```
ls "$fn"
``` too to see if ls finds the file? If it does, it's possibly a problem with mencoder.

---

