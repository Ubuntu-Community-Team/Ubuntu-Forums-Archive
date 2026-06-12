---
title: "A script to convert flv to 3gp"
date: 2010-10-03
forum: Programming Talk
---

### Post by newsman on 2010-10-03
the following script was taken from here [http://blog.mypapit.net/2007/04/ffmpeg-based-batch-flv-to-3gp-converter-scripts.html](http://blog.mypapit.net/2007/04/ffmpeg-based-batch-flv-to-3gp-converter-scripts.html) but got taken offline and copyright is to another page which is offline (but nevertheless it was copied and modified and posted on another website ([http://knightlust.blogspot.com/2008/05/flv-to-3gp.html](http://knightlust.blogspot.com/2008/05/flv-to-3gp.html) )

Anyway initially the main line was not converting videos but giving aac coder error.. some googling led me to:

[http://ubuntuforums.org/showthread.php?t=988366](http://ubuntuforums.org/showthread.php?t=988366) (thanks unbuntuforum'ers)

Now the main line works but the script still does not work..

The script is:
```

#!/bin/bash
echo "fakap mp3-to-flv converter http://blog.fakap.net/mp3toflv/"
echo "Copyright (c) mypapit 2007"
echo ""
if (($# ==0))
then
    echo "Usage: flvto3gp [flv files] ..."
    exit
fi

echo $#
while (($# !=0 ))
do
	echo "$1"
        ffmpeg -i $1 -s 176x144 -vcodec h263 -r 28 -b 96k -ab 64 -acodec libfaac -ac 1 -ar 44100 $1.3gp
    shift
done
echo "Finished fakaping with flv-to-3gp converter"
echo "\"fakap all those nonsense!\""
echo ""

```

And the output is:
> fakap mp3-to-flv converter [http://blog.fakap.net/mp3toflv/](http://blog.fakap.net/mp3toflv/)
Copyright (c) mypapit 2007

flvto3gp.sh: 9: 22: not found
22
flvto3gp.sh: 17: 22: not found
Finished fakaping with flv-to-3gp converter
"fakap all those nonsense!

---

### Post by newsman on 2010-10-05
The tests as suspected were wrong, i was using arithmetic expansion instead

this appears to work 
```

#!/bin/bash
echo "fakap mp3-to-flv converter http://blog.fakap.net/mp3toflv/"
echo "Copyright (c) mypapit 2007"
echo ""
if [ $# -eq 0 ]
then
    echo "Usage: flvto3gp [flv files] ..."
    exit
fi

while [ $# -ne 0 ]
do
        ffmpeg -i $1 -s 176x144 -vcodec h263 -r 28 -b 96k -ab 64 -acodec libfaac -ac 1 -ar 44100 "$1".3gp
    shift
done
echo "Finished fakaping with flv-to-3gp converter"
echo "\"fakap all those nonsense!\""
echo ""

```

---

