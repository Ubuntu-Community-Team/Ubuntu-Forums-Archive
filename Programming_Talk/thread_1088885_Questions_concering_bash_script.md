---
title: "Questions concering bash script"
date: 2009-03-06
forum: Programming Talk
---

### Post by Nevon on 2009-03-06
Hello everyone,

I'm trying to write a relatively complex bash script that keeps track of what episodes of some tv-series that I have seen/not seen. I've only just started working on it, but I want to make sure that I get the general structure right before I get too deep into it. 

One of the things I want the script to be able to do is to scan a given directory and write the output to a file. For now I'm doing that this way:
```
seriesScan()
{
    ls -D1 $VIDEOS_DIR > $DATABASE_DIR/serieslist.db
}
```Note that this only allows one directory for all the series to be stored in, and it doesn't work if you for example categorize all your series into different directories depending on genre, year or something else. But that's an issue for later. For now we're going to assume that the user stores all his/her series like this Videos->Series-name->Video-Files. Anyway, while I want to run seriesScan every now and again in the background, I also want the user to be able to manually start a scan by writing: ```
./serieswatcher.sh -s
``` or ```
./serieswatcher.sh --scan
```This can be accomplished by using a case statement as such:```
case "$1" in
    -s | --scan) seriesScan;;
esac
```
But now what if I later decide that the user should be able to, for example, perform a scan and change seen/not-seen status of a certain file with the same command? Kind of like the way you can use multiple flags in most bash commands (ls -D1 ~/Videos, for example). How would I do that? Also, what if both flags require additional information to be run? Let's say the -s flag requires a directory to scan, as such: ```
./serieswatcher.sh -s ~/Movies
``` and the "set to not seen" flag (-n) requires a series name and a file to edit, as such: ```
./serieswatcher.sh -n Heroes S02E03
``` How would I be able to combine the two flags so that you could run this:```
./serieswatcher.sh -sn ~/Movies Heroes S02E03
``` to run a scan of ~/Movies and set the status of S02E03 of Heroes to not seen? 

Of course I'm not looking for you to write the code to be able to do all these things (although I would appreciate any input and help), I just want to know how to structure things properly to get the most flexibility out of this script.

---

### Post by Nevon on 2009-03-06
While my previous questions still stand, I now have a new problem. I've decided to put all the settings in a file called settings.conf in ~/.serieswatcher, and I would like to be able to edit them directly from the script using sed. For some reason this works for changing the prefered video player, but not for changing the folder containing the videos. 

```
"4")
            echo "Do you want to...?";
            echo "1) Set prefered video player?";
            echo "2) Set folder to scan for media?";
            echo 'Type "Back" to go back to the main menu.';
            read CHOICE2
            case $CHOICE2 in
                "1")
                    echo 'Type the command for launching the desired video player, e.g. "vlc" or "mplayer" without the quotes.';
                    read PLAYER
                    cat $DATABASE_DIR/settings.conf | sed -e "/VIDEO_PLAYER/s/$VIDEO_PLAYER/$PLAYER/g" > $DATABASE_DIR/settings.conf
                    VIDEO_PLAYER=$PLAYER
                    echo "$PLAYER set as prefered video player.";
                ;;
                "2")
                    echo 'Type the path of the directory you want to scan from your home directory. For example "~/Videos" or "/home/username/Movies".';
                    read DIRECTORY
                    cat $DATABASE_DIR/settings.conf | sed -e "/VIDEOS_DIR/s/$VIDEOS_DIR/$DIRECTORY/g" > $DATABASE_DIR/settings.conf
                    VIDEOS_DIR=$DIRECTORY
                    echo "$DIRECTORY set as directory to be scanned.";
                ;;
                "Back" | "BACK" | "back")
                ;;
                *)
                    echo "Invalid choice. Please try again.";
                ;;
            esac
        ;;
```

Settings.conf looks like this:
```
#Settings file for SeriesWatcher
#
#Prefered video player. Default is "vlc".
VIDEO_PLAYER = vlc

#Folder containing video files. Default is "~/Videos"
VIDEOS_DIR = Videos
```

Please note that I've declared the global variables VIDEO_PLAYER and VIDEO_DIR earlier in the script. 

Does anyone know what the problem might be?

---

### Post by ghostdog74 on 2009-03-06
sed does not do anything but show you the result. If you are using sed on a file and want the file contents to change, you can either pipe the results to a temp file and rename it back to original, OR you can use the sed -i option. Likewise, if you are using it to change a variable, remember to assign the result to a new variable, using backticks or $(....). And don't use cat with sed. Its unnecessary and its called useless use of cat.

---

### Post by Nevon on 2009-03-07
> **ghostdog74 said:**
> sed does not do anything but show you the result. If you are using sed on a file and want the file contents to change, you can either pipe the results to a temp file and rename it back to original, OR you can use the sed -i option. And don't use cat with sed. Its unnecessary and its called useless use of cat.

So the proper command would be? ```
sed -i "/VIDEOS_DIR/s/$VIDEOS_DIR/$DIRECTORY/g" $DATABASE_DIR/settings.conf
```

> **ghostdog74 said:**
> Likewise, if you are using it to change a variable, remember to assign the result to a new variable, using backticks or $(....).
I'm not sure what you mean by this, could you elaborate? As you can see, I'm setting a new value for the variable right after changing the settings.conf file. All of this is done in a loop, so it should be fine - I think. 

Maybe I should just show you my code in its entirety, so you see what I mean.

```
#!/bin/bash
#
#Script for keeping track of tv-series and what episodes
#have been watched.
#
#----------------VARIABLES---------------------------------------------------#
#
#Variables are to be read from ~/.serieswatcher/settings.conf.
#It's just not implemented yet.
#
DATABASE_DIR=~/.serieswatcher
VIDEOS_DIR=Videos
VIDEO_PLAYER=vlc
#
#----------------FUNCTIONS---------------------------------------------------#
#
#Checks to see if .serieswatcher exists and is writeable.
mainMenu ()
{
    echo "-------MENU-------";
    echo "1) Watch episode...";
    echo "2) Rescan collection...";
    echo "3) Set status of episode...";
    echo "4) Options";
    echo 'Type "Quit" to exit.';
}
dirCheck ()
{
    if [ ! -d "$DATABASE_DIR" ]; then
        mkdir $DATABASE_DIR
    fi
    if [ ! -w "$DATABASE_DIR" ]; then
        echo "$DATABASE_DIR is not writable. Run chmod a+w $DATABASE_DIR as root."; exit 1;
    fi
}
#Scans the video folder and saves the output in DATABASE_DIR/serieslist.db
seriesScan()
{
    ls -D1 $VIDEOS_DIR > $DATABASE_DIR/serieslist.db
}
#----------------SCRIPT------------------------------------------------------#
dirCheck
while [ 1 ]
do
    mainMenu
    read CHOICE
    case $CHOICE in
        "1")
            echo "Of what series?";
            exit
        ;;
        "2")
            echo "Scanning $VIDEOS_DIR...";
            echo "Found:";
            ls -D1v $VIDEOS_DIR
            seriesScan
            echo "Done!";
        ;;
        "3")
            echo "Of what series?";
            exit
        ;;
        "4")
            echo "Do you want to...?";
            echo "1) Set prefered video player?";
            echo "2) Set folder to scan for media?";
            echo 'Type "Back" to go back to the main menu.';
            read CHOICE2
            case $CHOICE2 in
                "1")
                    echo 'Type the command for launching the desired video player, e.g. "vlc" or "mplayer" without the quotes.';
                    echo "Currently selected player is: $VIDEO_PLAYER";
                    read PLAYER
                    sed -i "/VIDEO_PLAYER/s/$VIDEO_PLAYER/$PLAYER/g" $DATABASE_DIR/settings.conf
                    VIDEO_PLAYER=$PLAYER
                    echo "$PLAYER set as prefered video player.";
                ;;
                "2")
                    echo 'Type the path of the directory you want to scan from your home directory. For example "Videos" or "Movies".';
                    echo "Currently selected directory is: $VIDEOS_DIR";
                    read DIRECTORY
                    sed -i "/VIDEOS_DIR/s/$VIDEOS_DIR/$DIRECTORY/g" $DATABASE_DIR/settings.conf
                    VIDEOS_DIR=$DIRECTORY
                    echo "$DIRECTORY set as directory to be scanned.";
                ;;
                "Back" | "BACK" | "back")
                ;;
                *)
                    echo "Invalid choice. Please try again.";
                ;;
            esac
        ;;
        "Quit" | "QUIT" | "quit")
            echo "Thank you for using SeriesWatcher!";
            exit
        ;;
        *)
            echo "Invalid choice. Please try again.";
        ;;
    esac
done
```

---

### Post by Nevon on 2009-03-07
New issue entirely!

I'm using the sed command ```
sed -i "/VIDEO_PLAYER/s/$VIDEO_PLAYER/$PLAYER/g" $DATABASE_DIR/settings.conf
```to change the prefered video player to be used. That works perfectly. However, I also want to be able to change the directory to be scanned for videos. That would be done with a similar command: ```
sed -i "/VIDEOS_DIR/s/$VIDEOS_DIR/$DIRECTORY/g" $DATABASE_DIR/settings.conf
```However, if the path contains slashes (which it will), the command doesn't work. So I've tried using an alternative delimiter, for example @. Now for some reason the command no longer works. I've checked the documentation, and it's supposed to work - it just doesn't. 

Why is that?

---

### Post by geirha on 2009-03-07
You can change the delimiter for the s command, but not the address.
```
sed -i "/VIDEOS_DIR/s@$VIDEOS_DIR@$DIRECTORY@g" ...
```

BTW, bash's built-in read command has readline support which you enable with the -e option. That's handy when you want to input paths, since you can then use tab-completion.

```
read -e DIRECTORY
```

And for parsing options on the command line, have a look at the getopt command. There's an example of its use at /usr/share/doc/util-linux/examples/getopt-parse.bash

---

### Post by Nevon on 2009-03-08
> **geirha said:**
> You can change the delimiter for the s command, but not the address.
```
sed -i "/VIDEOS_DIR/s@$VIDEOS_DIR@$DIRECTORY@g" ...
```

BTW, bash's built-in read command has readline support which you enable with the -e option. That's handy when you want to input paths, since you can then use tab-completion.

```
read -e DIRECTORY
```

And for parsing options on the command line, have a look at the getopt command. There's an example of its use at /usr/share/doc/util-linux/examples/getopt-parse.bash

Thank you! Now it finally works! However, I don't get what the -e option in read does. I don't really see any difference when I try it.

---

### Post by geirha on 2009-03-08
> **Nevon said:**
> Thank you! Now it finally works! However, I don't get what the -e option in read does. I don't really see any difference when I try it.

Try this. Open a terminal and type in "read -e DIRECTORY", then when the read command is waiting for your input, type (without enter) "/h" followed by the tab-key. It should fill in "/home/" for you ...

---

### Post by Nevon on 2009-03-08
> **geirha said:**
> Try this. Open a terminal and type in "read -e DIRECTORY", then when the read command is waiting for your input, type (without enter) "/h" followed by the tab-key. It should fill in "/home/" for you ...

Ah, okay. That's neat. I'll be sure to use that.

---

### Post by Nevon on 2009-03-08
Now I have an entirely new question again. At first I wanted to be able to scan through a user specified directory, look for video files, sort them by series and season, and then somehow store that information in a text file. I quickly realized that I will never be able to accomplish that, since the user's directory structure and file naming may be completely different to that of mine. So now my idea was that I'd scan a directory for folders, use the folder names as names of series (usually you keep all your episodes of Desperate Housewives in a directory called Desperate Housewives, right?), then have the user select one of these directories, upon which I would recursively scan that directory for video files, look for SXXEXX (X being a number) and use that information to group the video files into seasons. Once I had done that, the user can choose what season and then what episode to watch (I also need a clever way of keeping check of what episodes have been watched or not). 

I figured the first part wouldn't be all that hard. So I tried something like this:
```
SERIES_LIST=$(ls -D1 $VIDEOS_DIR)
            PS3="Of what series?"
            select CHOICE3 in $SERIES_LIST
            do
                ls -D1 $VIDEOS_DIR/$CHOICE3
            done
```Sadly that doesn't quite work, as the directory names get cut up word by word, so in my case the output would be:```
1) Battlestar	 4) Lie		 7) Lost	10) Smallville	13) The
2) Galactica	 5) to		 8) Numb3rs	11) Stargate	14) Mentalist
3) Heroes	 6) me		 9) Skins	12) Atlantis
Of what series?
```

---

### Post by geirha on 2009-03-08
Use bash's pathname expansion instead of ls.
```
 
select CHOICE3 in "$VIDEOS_DIR"/* ; do
  ls "$CHOICE3"
done

```

---

### Post by Nevon on 2009-03-08
> **geirha said:**
> Use bash's pathname expansion instead of ls.
```
 
select CHOICE3 in "$VIDEOS_DIR"/* ; do
  ls "$CHOICE3"
done

```

Hey, that solved that little problem pretty much perfectly. Thank you very much. 

Now the question remains, how the heck do I scan those directories recursively, parse the results, somehow organize them according to season and episode number, and then present it to the user in a somewhat straightforward manner?

---

### Post by geirha on 2009-03-08
The find command is the tool to use for searching recursively.
A few examples
```

find "$CHOICE3"         # Lists all files and directories under "$CHOICE3"
find "$CHOICE3" -type d # Lists only directories, -type f for files only
find "$CHOICE3" -type f -exec file {} \;  # Run a command on each file, in this case the file-command

```

Read the man-page to see all the neat stuff the find command can do
```
man find
```

---

### Post by Nevon on 2009-03-08
> **geirha said:**
> The find command is the tool to use for searching recursively.
This would probably be my best guess as for how to search through the directories and list all the video files (with those extensions, anyway). 
```
find $VIDEOS_DIR/* -name *.flv -o -name *.mpg -o -name *.avi
```
However, when I try it out I get errors for every sub-directory in there, saying "<directory name> is a directory", and then it just dies. Even if I manually move to the last directory (meaning the one containing the videos) it throws a permission denied message at me. :???:

---

### Post by geirha on 2009-03-08
It's important that you quote the arguments for the -name options, or else, bash will expand those patterns.
```
... -name "*.flv" -o -name "*.mpg" ...
```

Also, make sure you always quote variables containing paths. If VIDEOS_DIR contains spaces, you'd get the same problem as with your select previously. Also, you don't need the ending * in this case. You want to give find one directory to search through.
```
find "$VIDEOS_DIR" ...
```

---

### Post by Nevon on 2009-03-08
> **geirha said:**
> It's important that you quote the arguments for the -name options, or else, bash will expand those patterns.
```
... -name "*.flv" -o -name "*.mpg" ...
```

Also, make sure you always quote variables containing paths. If VIDEOS_DIR contains spaces, you'd get the same problem as with your select previously. Also, you don't need the ending * in this case. You want to give find one directory to search through.
```
find "$VIDEOS_DIR" ...
```

The thing is, I don't want to give find just one directory to search through. Let me give you an example. 

Let's say I want to find all video files of the tv series Numb3rs. The directory structure of Numb3rs looks like this:
```
Numb3rs--|-Season 1-|-S01E01.avi
         |          |-S01E02.avi
         |          |-S01E03.avi
         |          |-S01E04.avi
         |-Season 2-|
         |          |-S02E01.avi
         |          |-S02E02.avi
         |          |-S02E03.avi
         |          |-S02E04.avi
         |-Season 3-|-S03E01.avi
                    |-S03E02.avi
                    |-S03E03.avi
                    |-S03E04.avi
```Now I want to list all the video files in these three directories by searching the parent directory Numb3rs. 

Right now I'm trying to accomplish this by doing ```
VIDEO_LIST=$(find "$CHOICE3" -name "*.flv" -o -name "*.mpg" -o -name "*.avi" | sort)
                    echo $VIDEO_LIST;
``` But it doesn't work, since find only searches through the selected directory, not the sub-directories within that directory.

---

### Post by geirha on 2009-03-08
With that directory structure, the following should find all those avi-files.
```
find Numb3rs -name "*.avi"
``` 

find searches recursively by default, you need to add special options for it to not search recursively. Could it be the files have uppercase extensions? .AVI instead of .avi, if so try with -iname instead of -name to make the search case insensitive.

---

### Post by Nevon on 2009-03-08
> **geirha said:**
> With that directory structure, the following should find all those avi-files.
```
find Numb3rs -name "*.avi"
``` 

find searches recursively by default, you need to add special options for it to not search recursively. Could it be the files have uppercase extensions? .AVI instead of .avi, if so try with -iname instead of -name to make the search case insensitive.

I think it was just me being a little retarded, feeding find something like "/home/nevon/Videos/TV//home/nevon/Videos/TV/Numb3rs" instead of just "/home/nevon/Videos/TV/Numb3rs". 

Now the next question arises. I need to somehow put all these videos in some kind of database, be it a textfile or otherwise, where I am able to set whether or not they've been watched. Any ideas as to how I should do this?

---

