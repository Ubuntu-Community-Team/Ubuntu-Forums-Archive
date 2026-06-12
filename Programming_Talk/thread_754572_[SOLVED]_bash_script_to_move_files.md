---
title: "[SOLVED] bash script to move files"
date: 2008-04-13
forum: Programming Talk
---

### Post by murlosad on 2008-04-13
This is probably not as difficult as I'm making it, but I was wondering if anyone else might have some suggestions.

Here's what I want to do:

I'm trying to write a script to check a directory for a specific filetype (.torrent in this case) and then prompt for a directory to move each file to, one by one.

so if the script finds:
```
foo.torrent
foobar.torrent
foobarmoo.torrent
``` it will then ask which directory I want to move foo.torrent too, do that then move on to the next one.

so far I have:```
#!/bin/bash

SAVE_DIR ~/Desktop
cd $SAVE_DIR
ls *.torrent >> ~/.torrent_list
some parsing command here that outputs 1st .torrent as FILE

echo "select an option"
echo "[1] music"
echo "[2] movies"
echo "[3] tv"
echo "[4] software"
echo "[5] misc"

read CHOICE

case "$CHOICE" in

	"1" )
	mv $FILE ~/.rtorrent/music/
	;;
	
	"2" )
	mv $FILE ~/.rtorrent/movies/
	;;

	"3" )
	mv $FILE ~/.rtorrent/tv/
	;;

	"4" )
	mv $FILE ~/.rtorrent/software/
	;;
	
	"5" )
	mv $FILE ~/.rtorrent/misc/
	;;

esac

rm ~/.torrent_list

exit
```

basically I need something that can parse the created file and stop after finding the first .torrent file. from there I think the rest should work. I tested what I could and it moves the files fine.

Any suggestions would be appreciated. This is definitely not anything important, just a time saver (well, once I get it working anyway :))

---

### Post by ghostdog74 on 2008-04-14
> **murlosad said:**
> 
Any suggestions would be appreciated. This is definitely not anything important, just a time saver (well, once I get it working anyway :))
instead of asking for input, why not do everything in a config file
eg of config file

pattern="*.torrent"
destination="/somewhere"


then in the script, parse the config file and move the files.

---

### Post by murlosad on 2008-04-14
I thought about that, but the problem is that I want to move the torrents around depending on what they are, e.g. a movie goes into the movies directory, a linux distro into software, etc. and since torrents are not really named in any particular standard I don't think it a config file would be able to handle it.

Thanks for replying though.

I think I can do it with sed, but I've never used sed before so I'm still reading up on it.

---

### Post by stroyan on 2008-04-14
You don't need to run ls into a file and parse its output.
You can just have bash match the *.torrent pattern and work through the file names.
```

#!/bin/bash

SAVE_DIR ~/Desktop
cd $SAVE_DIR
for FILE in *.torrent
do

echo moving $FILE
echo "select an option"
echo "[1] music"
echo "[2] movies"
echo "[3] tv"
echo "[4] software"
echo "[5] misc"

read CHOICE

case "$CHOICE" in

        "1" )
        mv $FILE ~/.rtorrent/music/
        ;;

        "2" )
        mv $FILE ~/.rtorrent/movies/
        ;;

        "3" )
        mv $FILE ~/.rtorrent/tv/
        ;;

        "4" )
        mv $FILE ~/.rtorrent/software/
        ;;

        "5" )
        mv $FILE ~/.rtorrent/misc/
        ;;

esac
done

```

---

### Post by murlosad on 2008-04-14
Brilliant! I knew it had to be simpler than I was making it. Thank you very much sir, that does exactly what I want. I am a happy man tonight.

now it's time for sleep.

---

### Post by ghostdog74 on 2008-04-14
@OP, i hope you do not have that many torrent files, if not, you will be entering options like mad.

```

awk 'BEGIN{q="\047"}
{dir=""}
/avi|mpg|mpeg/{
  dir="~/.rtorrent/movies/"  
}
/mp3|wma/{
  dir="~/.rtorrent/music/"
}
{
 if (dir) {
  cmd = "mv "q FILENAME q" "dir
  print cmd
  system(cmd)
  nextfile
 }
}' /tmp/*.torrent

```

---

### Post by murlosad on 2008-04-14
> **ghostdog74 said:**
> @OP, i hope you do not have that many torrent files, if not, you will be entering options like mad.


lol, no not too many, I just tend to find two or three at a time, and usually I'm remoting into my desktop when I dl them, so it's easier to have a script do most of the work for me.

Thanks everybody for the help.

---

