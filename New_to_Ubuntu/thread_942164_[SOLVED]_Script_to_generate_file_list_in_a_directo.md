---
title: "[SOLVED] Script to generate file list in a directory"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-10-08
I want to create a script to search for files with specific extensions on a directory, then create a list of these files and save the list as pls.

The idea is to monitor my TV recording folder and automatically create a playlist. The problem is that I don't have any idea how to do it. 

I imagine that I need a command to search files in the folder. I guess "find" command could do that. I could run the script with cron to monitor file changes a few times a day. Then I need something to write the file names with the following structure:

```
[playlist]
NumberOfEntries=4
Version=2
File1=~/Videos/20081008-23:33.avi
File2=~/Videos/20081008-23:46.avi
File3=~/Videos/20081008-23:57.avi
File4=~/Videos/20081008-23:59.avi
```

Any ideas will be much appreciated.

---

### Post by pytheas22 on 2008-10-08
This command would find all files with extension 'avi' in your /home folder (including subfolders), and write their names to a text file on your desktop called 'log.txt':
```

ls -R ~/ | grep -e '\.avi' > ~/Desktop/log.txt
```

This could be improved, but basically this is what you would need to do, I think.  Please let me know if you need any more information, or if you'd like me to explain what each part of the command does.

Also to get the 'File1=' stuff prefixed before the file names, you could use a few different tricks; I don't have time to write out the details now but can tomorrow if you can't figure it out.

---

### Post by asmoore82 on 2008-10-08
file: ~/bin/make_playlist
```
#!/bin/bash

ME="${0##*/}"
if [ "$#" -lt "2" ]; then
	echo "USAGE:  ${ME} <search_dir> <extension>" 1>&2
	exit 128
fi

[ ! "${1:0:1}" = "/" ] && echo 'WARNING: <search_dir> should be an absolute path' 1>&2

tmpfile="/tmp/${UID}_$$_$(date +%s)"

find "$1" -type f -iname "*.${2##*.}" > "$tmpfile"

echo    '[playlist]'
echo -n 'NumberOfEntries='
echo    "$(echo $( cat "$tmpfile" | wc | cut -c1-7 ) )"
echo    'Version=2'
cat "$tmpfile"

unlink "$tmpfile"

# End of File
```

---

### Post by lovinglinux on 2008-10-09
> **pytheas22 said:**
> This command would find all files with extension 'avi' in your /home folder (including subfolders), and write their names to a text file on your desktop called 'log.txt':
```

ls -R ~/ | grep -e '\.avi' > ~/Desktop/log.txt
```

This could be improved, but basically this is what you would need to do, I think.  Please let me know if you need any more information, or if you'd like me to explain what each part of the command does.

Also to get the 'File1=' stuff prefixed before the file names, you could use a few different tricks; I don't have time to write out the details now but can tomorrow if you can't figure it out.

Thank you very much. This works pretty fine. All I had to do was to replace the txt extension with pls. I figured out that I don't even need the pls content structure as long as I keep the generated playlist file in the same folder of the video files and open it with gnome-mplayer, which is the player I want to use. This will work for me like a charm.

I will work on my Firefox tutorial (link in my sig) to add this feature. I currently have a thumbnail in Firefox with a custom handler that launches the script with your code (see code below), so it first update the playlist and then start playing it. So I don't even have to create a cron job.

```
#!/bin/bash 

ls -R ~/Desktop/pvr | grep -e '\.avi' > ~/Desktop/pvr/playlist.pls

gnome-mplayer ~/Desktop/pvr/playlist.pls
```

Do you know how I could add more extensions to the same list?


> **asmoore82 said:**
> file: ~/bin/make_playlist
```
#!/bin/bash

ME="${0##*/}"
if [ "$#" -lt "2" ]; then
	echo "USAGE:  ${ME} <search_dir> <extension>" 1>&2
	exit 128
fi

[ ! "${1:0:1}" = "/" ] && echo 'WARNING: <search_dir> should be an absolute path' 1>&2

tmpfile="/tmp/${UID}_$$_$(date +%s)"

find "$1" -type f -iname "*.${2##*.}" > "$tmpfile"

echo    '[playlist]'
echo -n 'NumberOfEntries='
echo    "$(echo $( cat "$tmpfile" | wc | cut -c1-7 ) )"
echo    'Version=2'
cat "$tmpfile"

unlink "$tmpfile"

# End of File
```

Thank you very much for creating this script. It looks awesome, but I feel stupid, since I have no idea how to use it :oops: Do I need to send the variables to the script or do I need to replace <search_dir> <extension>?

---

### Post by pytheas22 on 2008-10-09
> Do you know how I could add more extensions to the same list?

To tell it to match more kinds of files, add more arguments to the 'grep' portion of the script, for example:
```

ls -R ~/ | grep -e '\.avi' **-e '\.mpg' -e '\.mov'** > ~/Desktop/log.txt
```

would also match .mov and .mpg files.

Also, another thing to keep in mind here is the possibility that some of your files will not have extensions on their names.  Is that an issue, or are all of your files always going to have extensions?  If they come from the Windows world, they probably will, but since Linux doesn't care about extensions, you get people sometimes (like me) who create files without adding extensions to their names.  You could still add in more functions to the script to tell it to match files regardless of extension, though...

Another issue that this will match any files or directories with '.avi' etc. anywhere in their names.  That's probably not an issue except in weird cases, but you can make things slightly better by adding in a $ to your regular expressions:

```

ls -R ~/ | grep -e '\.avi$' **-e '\.mpg$' -e '\.mov$'** > ~/Desktop/log.txt
```

The $ tells grep to match those strings only if they're at the end of a filename.  Still in really weird cases, you might match a false-positive, but it's less likely with the $ added in.

asmoore82: nice script; I wish I were good enough at bash to churn out something like that so fast.

---

### Post by lovinglinux on 2008-10-09
> **pytheas22 said:**
> To tell it to match more kinds of files, add more arguments to the 'grep' portion of the script, for example:
```

ls -R ~/ | grep -e '\.avi' **-e '\.mpg' -e '\.mov'** > ~/Desktop/log.txt
```

would also match .mov and .mpg files.

Cool. I was almost there, but I also added more "grep" command for each extension :mrgreen:

> **pytheas22 said:**
> Also, another thing to keep in mind here is the possibility that some of your files will not have extensions on their names.  Is that an issue, or are all of your files always going to have extensions?

Is not an issue, because I have already a script for recording TV that always add the avi extension. I just wanted to know how to add more extensions to watch video download folders.

> **pytheas22 said:**
> Another issue that this will match any files or directories with '.avi' etc. anywhere in their names.  That's probably not an issue except in weird cases, but you can make things slightly better by adding in a $ to your regular expressions:

```

ls -R ~/ | grep -e '\.avi$' **-e '\.mpg$' -e '\.mov$'** > ~/Desktop/log.txt
```

The $ tells grep to match those strings only if they're at the end of a filename.  Still in really weird cases, you might match a false-positive, but it's less likely with the $ added in.

Cool. Probably not an issue in my case, but this will make sure nothing weird happens.

Thank you very much.

> **pytheas22 said:**
> asmoore82: nice script; I wish I were good enough at bash to churn out something like that so fast.

I wish I could do that too :-)

I'm very curious to see how it works.

---

### Post by ghostdog74 on 2008-10-09
use the find command
```

find /path -type f \( -name "*.mp3" -o -name "*.avi" \) -print > playlist

```

---

### Post by lovinglinux on 2008-10-09
I have updated my Firefox Media Center tutorial (link in my sig) to include the playlist generator, with the proper credits to pytheas22. It is in the Section 9 of the tutorial.

---

### Post by lovinglinux on 2008-10-09
> **ghostdog74 said:**
> use the find command
```

find /path -type f \( -name "*.mp3" -o -name "*.avi" \) -print > playlist

```

Thank you very much. It also works pretty fine and allow to save the playlist on another directory. The only problem is that it doesn't sort the files properly. With the script provided by pytheas22 the files are listed in order, while this one is random. Do you know why?

---

### Post by ghostdog74 on 2008-10-09
> **lovinglinux said:**
> Thank you very much. It also works pretty fine and allow to save the playlist on another directory. The only problem is that it doesn't sort the files properly. With the script provided by pytheas22 the files are listed in order, while this one is random. Do you know why?

you can pass the results to sort command. man sort for more info

---

### Post by lovinglinux on 2008-10-09
> **ghostdog74 said:**
> you can pass the results to sort command. man sort for more info

The sort command works like a charm. Thanks again. 

Here is the script I'm using now:
```

find ~/[COLOR="Red"]**Desktop**[/COLOR] -type f \( -name "*.avi" \)  | sort > ~/[COLOR="Red"]**Playlists**[/COLOR]/tv.pls
```

---

### Post by lovinglinux on 2008-10-10
> **lovinglinux said:**
> Thank you very much for creating this script. It looks awesome, but I feel stupid, since I have no idea how to use it :oops: Do I need to send the variables to the script or do I need to replace <search_dir> <extension>?

Nevermind. I figure out how to use it. Just had to save it as for example "makelist" and run the following command on a terminal:

```
makelist ~/thedirectory avi > ~/thedirectory/playlist.pls
```

I still need to find out how to append "File1=" before the file path, otherwise it won't play on smplayer or any other player I have except gnome-mplayer.

I will try to find out myself, but if anyone knows how to do it it would be very helpful.

---

