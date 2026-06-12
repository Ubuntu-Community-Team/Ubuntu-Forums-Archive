---
title: "Question Yes do x No do not do x in bash script"
date: 2013-07-06
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-07-06
Hi Guys,

I have a Sony Walkman MP3 player that I use to listen to a podcast.
I have been downloading the podcast mp3s and then moving them to the walkman.

I am trying to write a script that will check the podcast for new episodes and then give me the choice of syncing any new episodes with the walkman or not.
The idea behind the choice is that if there were no new episodes downloaded, I wouldn't need the sync command to run.

Additionally, I want to be given the choice of cleaning out the download directory after syncing has completed.

I have gotten the check and download new episodes to work, but I'm doing something wrong with the choice to sync or not and the choice to delete or not.

```


#!/bin/bash
echo "This script is for Update Coast to Coast Podcast "
hpodder fetch 
**read -p "Press S to sync with the walkman. "  **[COLOR=#ff0000]*The script crashes here.*[/COLOR]
**read x**
**if [ "$x" = "S" ]**
**then**
**rsync -r -t -v --progress -s /home/john/podcasts/Coast_to_Coast_AM_Podcast /media/WALKMAN/MUSIC/Casts**
**else **
**echo "OK not syncing this time."**
**fi**
**read -p "Press D to delete files from podcasts"**
**read x**
**if [ "$x" = "D" ]**
**then**
**rm -f /home/john/podcasts/Coast_to_Coast_AM_Podcast/***
**fi**


```

The sync works fine if I remove the:

```


read -p "Press S to sync with the walkman. "  
read x
if [ "$x" = "S" ]
then


```

and just have the rsyn command run after the hpodder fetch command.

Could someone please help me understand what I am doing wrong?

---

### Post by DJ_Max on 2013-07-06
Would have helped if you mentioned the error message you received. But try this

```
read -p "Press S to sync with the walkman. " x

```

I don't understand why you have two read lines.
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html)

You should also be using ELSEIF

This is how I would do it

```
#!/bin/bash
echo "This script is for Update Coast to Coast Podcast "
hpodder fetch 
echo "Press S to sync with the walkman.\nPress D to delete files from podcasts "
read x
if [ "$x" = "S" ]
then
rsync -r -t -v --progress -s /home/john/podcasts/Coast_to_Coast_AM_Podcast /media/WALKMAN/MUSIC/Casts
echo "Syncing YESS new podcasts"
elif [ "$x" = "D" ]
then 
rm -f /home/john/podcasts/Coast_to_Coast_AM_Podcast/*
else
echo "Nothing"
fi
```

---

### Post by GrouchyGaijin on 2013-07-06
Thank you for the help.  I appreciate it.

Actually there was no error message.  The terminal just got to that point and then nothing - not even a blinking cursor.
The reason I had two read lines was that I wanted to be given the option of running the sync  and then later after the sync I wanted to be given the option of deleting the files from the podcasts directory.

Your script is much better than mine.  Yours works. :)  I'm going to the link you mentioned as soon as I post this.

I do have a question though, is there a way to change the S to sync or D to delete so that I have the option of deleting all the files after the sync is completed without rerunning the script?

---

### Post by DJ_Max on 2013-07-06
Than I would So entering ***Q*** would quit the program

```
#!/bin/bash
echo "This script is for Update Coast to Coast Podcast "
hpodder fetch 
until [ "$x" = "Q" ]; do
	echo "Press S to sync with the walkman.\nPress D to delete files from podcasts "
	read x
	if [ "$x" = "S" ]
	then
	rsync -r -t -v --progress -s /home/john/podcasts/Coast_to_Coast_AM_Podcast /media/WALKMAN/MUSIC/Casts
	echo "Syncing YESS new podcasts"
	elif [ "$x" = "D" ]
	then 
	rm -f /home/john/podcasts/Coast_to_Coast_AM_Podcast/*
	else
	echo "Nothing"
	fi
done
echo "Finished"
```

---

### Post by GrouchyGaijin on 2013-07-07
Thank you so much.
This really helps.

I modified it a bit to:

```


until [ "$x" = "Q" ]; do
echo "Press S to sync with the walkman or press D to delete files from podcasts. 
Press Q to quit. "
    read x
    if [ "$x" = "S" ]
    then
    rsync -r -t -v --progress -s /home/john/podcasts/Coast_to_Coast_AM_Podcast /media/WALKMAN/MUSIC/Casts
    echo "Syncing new podcast episodes"
    elif [ "$x" = "D" ]
    then 
    rm -f /home/john/podcasts/Coast_to_Coast_AM_Podcast/*
    
    echo "Deleted files from podcast folder"
    fi


```

---

