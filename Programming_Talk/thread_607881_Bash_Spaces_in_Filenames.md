---
title: "Bash: Spaces in Filenames"
date: 2007-11-09
forum: Programming Talk
---

### Post by timo1023 on 2007-11-09
First of all, I'm a bash newb, but I'm trying to write a program to play music for me. Here it is:

```

#!/bin/bash

select GENRE in /Music/*$1*;
do
   select ARTIST in $GENRE/*$2*;
   do
      select ALBUM in $ARTIST/*$3*;
      do
      path=$(echo $ALBUM|sed -e "s/ /\\\ /g")
      vlc $path/ &
      done
   done
done

```

Here's how it works:

```

tmellor@tmellor:~$ music Modern Radiohead Amne
1) /Music/Modern
#? 1
1) /Music/Modern/Radiohead
#? 1
1) /Music/Modern/Radiohead/Amnesiac
#? 1
VLC media player 0.8.6c Janus

```

Then it plays that album. The problem is when the genre, artist, or album folder has a space, it treats the filename as two different filenames:

```

tmellor@tmellor:~$ music Modern Explosions
1) /Music/Modern
#? 1
1) /Music/Modern/Explosions In The Sky
#? 1
1) /Music/Modern/Explosions  3) The
2) In                        4) Sky/**
#? 

```

If I try to run sed multiple times, it just makes spaces look like this "\\ " rather than "\ ". Can I get some help with making this work?

---

### Post by LaRoza on 2007-11-09
Use quotes, or use camel case in naming the files.

---

### Post by timo1023 on 2007-11-09
OK updated program:

```

#!/bin/bash

select GENRE in /Music/*$1*;
do
   select ARTIST in "$GENRE"/*$2*;
   do
      select ALBUM in "$ARTIST"/*$3*;
      do
      path=$(echo $ALBUM|sed -e "s/ /\\\ /g")
      vlc "$path/" &
      done
   done
done

```

It _seems_ like the program works now:

```

tmellor@tmellor:~$ music Modern Radiohead Kid
1) /Music/Modern
#? 1
1) /Music/Modern/Radiohead
#? 1
1) /Music/Modern/Radiohead/Kid A
#? 1
#? VLC media player 0.8.6c Janus

```

But I get a VLC error:

> 
Unable to open '/Music/Modern/Radiohead/Kid\ A/'


However, if I place the same command in the terminal it works:

```

tmellor@tmellor:~$ vlc /Music/Modern/Radiohead/Kid\ A/
VLC media player 0.8.6c Janus

```

Why won't it work from the script?

---

### Post by psusi on 2007-11-09
Because you are quoting AND escaping.  Pick one or the other.  The quotes you put around $path keep bash from interpreting the \ you had sed escape the spaces with, so vlc gets passed the \ which causes it to fail because the file does not have a \ in the name.

---

### Post by timo1023 on 2007-11-09
Whoops, looks like I was making this more complicated than it should have been. Here's the final working code if anyone is interested:

```

#!/bin/bash

#script for browsing  music

# example usage:
# music -a Radiohead

case "$1" in
   "-a")
         select ARTIST in /Music/*/*$2*;
         do
            select ALBUM in "$ARTIST"/*$3*;
            do
            vlc "$ALBUM" &
            exit
            done
         done
         ;;

   "-g")

         select GENRE in /Music/*$2*;
         do
            select ARTIST in "$GENRE"/*;
            do
               select ALBUM in "$ARTIST"/*;
               do
               vlc "$ALBUM" &
               exit
               done
            done
         done
         ;;
   "-b")
               select ALBUM in /Music/*/*/*$2*;
               do
               vlc "$ALBUM" &
               exit
               done
         ;;
   "-s")
               select SONG in /Music/*/*/*/*$2* /Music/*/*/*$2*;
               do
               vlc "$SONG" &
               exit
               done
         ;;
   *)
         select GENRE in /Music/*$1*;
         do
            select ARTIST in "$GENRE"/*$2*;
            do
               select ALBUM in "$ARTIST"/*$3*;
               do
               vlc "$ALBUM"/ &
               exit
               done
            done
         done
         ;;
   
esac



```

---

