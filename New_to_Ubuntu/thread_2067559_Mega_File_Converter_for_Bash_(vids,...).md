---
title: "Mega File Converter for Bash (vids,...)"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by frenchn00b on 2012-10-07
Hi,

For this absolute beginners, I can post you a bash script, very basic, that does convert files simply:

```

#!/bin/sh


DATENOW=`date +%Y%m%d-%H%M%S` 


if  [ "$1" = "--avi2ipod"    ]  ; then 
  # may require: libaacplus2
  echo "Convert the $1 : $2 => $DATENOW-newfile.mp4"
  ffmpeg -i "$2" input -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320×180 -title X $DATENOW-newfile.mp4
  TARGET="$DATENOW-newfile.mp4"
  [ -f "$TARGET" ]  && echo "Converted to $TARGET"
  exit
fi

if  [ "$1" = "--avi2divx"    ]  ; then 
  echo "Convert the $1 : $2 => $DATENOW-newfile.mp4"
  ffmpeg -i "$2" -s 640x480 -vcodec msmpeg4v2 $DATENOW-newfile.mp4
  TARGET="$DATENOW-newfile.mp4"
  [ -f "$TARGET" ]  && echo "Converted to $TARGET"
  exit
fi


if  [ "$1" = "--avi2mp4"    ]  ; then 
  echo "Convert the $1 : $2 => $DATENOW-newfile.mp4"
  mencoder "$2" -oac copy -ovc lavc -lavcopts vcodec=mpeg1video -of mpeg -o $DATENOW-newfile.mp4
  TARGET="$DATENOW-newfile.mp4"
  [ -f "$TARGET" ]  && echo "Converted to $TARGET"
  exit
fi


if  [ "$1" = "--pdf2jpg"    ]  ; then 
  echo "Convert the $1 to all jpg"
  convert -density 300 "$1" out-%d.jpg
  exit
fi


if  [ "$1" = "--pdf2txt"    ]  ; then 
  echo "Convert the $1 to all txt"
  convert "$1" out.txt
  exit
fi


if  [ "$1" = "--all-rot"    ]  ; then 
  mkdir Rotated
  LIST=` ls -1 ` 
  echo "$LIST" | while read -r TARGETFILE  ; do 
  TARGETFILEROTED="Rotated/Rot_$TARGETFILE"
  echo "Rotate the file...  ${TARGETFILE} -> ${TARGETFILEROTED}"
  [ "$2" = "--run"    ] && convert -rotate -90   "${TARGETFILE}"  "${TARGETFILEROTED}"
done
exit
fi




if  [ "$1" = "--all-jpg2png"    ]  ; then 
  convert  *.jpg image-%d.png
  exit
fi



```

Enjoy

---

### Post by FakeOutdoorsman on 2012-10-08
This must be for a very old version of ffmpeg:
```
$ ffmpeg -i IronMan.mkv -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320×180 -title X newfile.mp4
...
Unrecognized option 'aic'
Failed to set value '2' for option 'aic
```
Problem: *aic* is no longer an independent option.
Fix: *aic* is used with *-flags*.

```
$ ffmpeg -i IronMan.mkv -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell+aic -cmp 2 -subcmp 2 -s 320×180 -title X newfile.mp4
...
Unrecognized option 'title'
Failed to set value 'X' for option 'title'
```
Problem: -title is no longer an independent option.
Fix: *-title* is used with *-metadata*.

```

$ ffmpeg -i IronMan.mkv -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell+aic -cmp 2 -subcmp 2 -s 320×180 -metadata title=X newfile.mp4
...
Invalid frame size: 320×180.
```
Problem: × is not a valid character with *-s*.
Fix: use "x".

```
$ ffmpeg -i IronMan.mkv -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell+aic -cmp 2 -subcmp 2 -s 320x180 -metadata title=X newfile.mp4
...
[NULL @ 0x24501c0] [Eval @ 0x7fff79864750] Invalid chars 'b' at the end of expression '1200kb'
[NULL @ 0x24501c0] Unable to parse option value "1200kb"
[NULL @ 0x24501c0] Error setting option b to value 1200kb.

```
Problem: kb is not valid for *-ab* and *-b*.
Fix: use k.

```
$ ffmpeg -i IronMan.mkv -acodec aac -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +4mv+trell+aic -cmp 2 -subcmp 2 -s 320x180 -metadata title=X newfile.mp4
...
Invalid chars 'v' at the end of expression '4mv'
[NULL @ 0x26b21c0] Unable to parse option value "4mv+trell+aic"
[NULL @ 0x26b21c0] Error setting option flags to value +4mv+trell+aic.

```
Problem: *4mv* is not an option.
Fix: Use *mv4*.

```
$ ffmpeg -i IronMan.mkv -acodec aac -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +mv4+trell+aic -cmp 2 -subcmp 2 -s 320x180 -metadata title=X newfile.mp4
...
Undefined constant or missing '(' in 'trell'
[NULL @ 0x34ef1c0] Unable to parse option value "trell+aic"
[NULL @ 0x34ef1c0] Error setting option flags to value +mv4+trell+aic.
```
Problem: trell is not a flags option.
Fix: Use *-trellis <value>* or omit.

```
$ ffmpeg -i IronMan.mkv -acodec aac -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +mv4+aic -cmp 2 -subcmp 2 -s 320x180 -metadata title=X newfile.mp4
...
Codec is experimental but experimental codecs are not enabled, try -strict -2
```
Problem: the native AAC encoder is considered experimental.
Fix: add *-strict experimental* or *-strict -2*.

Finally, a working example:
```
ffmpeg -i IronMan.mkv -acodec aac -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +mv4+aic -cmp 2 -subcmp 2 -s 320x180 -metadata title=X -strict -2 newfile.mp4
```

---

