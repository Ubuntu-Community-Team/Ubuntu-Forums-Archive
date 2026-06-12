---
title: "Bash scripting with mtp-tools"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by Cerapter on 2012-07-19
In lack of compatible software for an old MP3 player like mine (I've tried it all), I'm writing my own bash scripts for transfering playlists. I got libmtp/mtp-tools, and the commands work perfectly, but are difficult to implement in a script.

For example, mtp-newfolder, upon completion, outputs something like this:
```
libmtp version: 1.3.3

New folder ID: 43722
```
And I want the ID for subsequent commands. After hours of painstaking testing with sed and grep, I gave up and succeded to obtain the ID using this script:
```

    oput=`mtp-newfolder ${gFolder} ${ind_music} 0`
    oput=${oput//[a-zA-Z]/ }
    set -- $oput
    folder_ID=$4

```

The output of the other tools make this method hard, if not impossible, and I don't like doing it this way. Now, I'm an amateur at most of this scripting, but I have two hopes in mind:

A) Somewhere, someplace, the ID is actually sent alone, and I can fetch it if only I know where to look.
B) I can rewrite the mtp-tools and change the output, or write my own that work as I wish. I know C, so I should manage this if only I knew how.

---

### Post by codemaniac on 2012-07-19
If I have understood your requirement clearly , you want to extract ID from the below output .

```
libmtp version: 1.3.3

New folder ID: 43722
```

try this below commandline .

```
echo 'libmtp version: 1.3.3\
> New folder ID: 43722' | awk -F":" '/ID/{print $2}'
```

---

### Post by Cerapter on 2012-07-19
Thank you, I am still considering this kind of method. However, I run into problems with the following output, from mtp-sendtr:

> libmtp version: 1.1.3 /home/cerapter/Musikk/Roteskuff/Hayley Westenra - Listen To The Wind.mp3,/Music/07.19 World collide/Hayley Westenra - Listen To The Wind.mp3,Hayley Westenra,(null),Listen to the Wind,(null),(null),(null),00,0,0,1 Sending track /home/cerapter/Musikk/Roteskuff/Hayley Westenra - Listen To The Wind.mp3 to /Music/07.19 World collide/Hayley Westenra - Listen To The Wind.mp3 type: mp3, 2 Sending track: Codec: ISO MPEG-1 Audio Layer 3 Title: Listen to the Wind Artist: Hayley Westenra Storage ID: 0 Sending track...  New track ID: 1475434407225 (100%)Where I wish to extract the ID, which I know (from later testing) to be only 147543. Here it is merged with the filesize in bytes, and both ID and this size can be any number of numerals!

So I'm primarily looking for a way of manipulating the tools themselves, to give the output I want.

---

### Post by glennric on 2012-07-19
Have you tried playedit?  You can install it by adding the ppa with
```
sudo add-apt-repository ppa:glennric/mtp
```
I had a similar problem with an mp3 player that used the mtp protocol and so I wrote this program to create and edit playlists on the device.  I can't guarantee it will work for your mp3 player, but if it does it may make things easier for you.  Please let me know if you try it, and if it works or not.

---

### Post by codemaniac on 2012-07-19
> **Cerapter said:**
> Thank you, I am still considering this kind of method. However, I run into problems with the following output, from mtp-sendtr:

Where I wish to extract the ID, which I know (from later testing) to be only 147543. Here it is merged with the filesize in bytes, and both ID and this size can be any number of numerals!

So I'm primarily looking for a way of manipulating the tools themselves, to give the output I want.

The output you have shared is not in a standard format for a Unix filter or text processing Utility to be parsed as per wish.

Can you please post a screenshot of your terminal , to understand the output layout better .I think the text you have posted above is wrapped up .

---

### Post by Cerapter on 2012-07-20
> **glennric said:**
> Have you tried playedit?
I have tried my luck with playedit, and I'm willing to give it another try. I've been unable to install it correctly, because I cannot figure out how to meet this dependency:
```
checking for GUDEV... no
configure: error: Package requirements (gudev-1.0) were not met:

No package 'gudev-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GUDEV_CFLAGS
and GUDEV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```I cannot seem to find this gudev-package (I'm on Precise). I do have gir1.2-gudev-1.0, and this might do, but I'm not sure how to define this for playedit.

---

> **codemaniac said:**
> The output you have shared is not in a  standard format for a Unix filter or text processing Utility to be  parsed as per wish.

Can you please post a screenshot of your terminal , to understand the  output layout better .I think the text you have posted above is wrapped  up .
In the terminal, the output continually updates with the progress of the file transfer:
[IMG]http://file.cerapter.net/Screenshot_term.png[/IMG]
What I posted was the value I got when I tried to catch the output in this way:
```
oput=$(mtp-sendtr <args>)
```---

I have downloaded libmtp-dev and found the original C code of the mtp-tools. I will attempt to modify, compile and run these to see if that works. **EDIT**: I might have been wrong about this, I have been unable to compile these files, and I also can't seem to understand how to get at the source code, either.

---

### Post by Vaphell on 2012-07-20
use [code][/co****de] tags to preserve formatting
what happens when you **echo "$oput"**? is id on a separate line?

---

### Post by glennric on 2012-07-20
> **Cerapter said:**
> I have tried my luck with playedit, and I'm willing to give it another try. I've been unable to install it correctly, because I cannot figure out how to meet this dependency:
[CODE]checking for GUDEV... no
configure: error: Package requirements (gudev-1.0) were not met:

No package 'gudev-1.0' found

I cannot seem to find this gudev-package (I'm on Precise). I do have gir1.2-gudev-1.0, and this might do, but I'm not sure how to define this for playedit.


The correct package is libgudev-1.0-dev.  However, you do not need to compile it.  If you add the repository ppa:glennric/mtp that I mentioned before you can simply install it with "sudo apt-get install playedit" (or use the software center).

---

### Post by Cerapter on 2012-07-21
> **Vaphell said:**
> use  tags to preserve formatting
what happens when you **echo "$oput"**? is id on a separate line?
Unfortunately, it is not, and this is why I used the quote tag:
```
libmtp version: 1.1.3 /home/cerapter/Musikk/Roteskuff/Hayley Westenra -  Listen To The Wind.mp3,/Music/07.19 World collide/Hayley Westenra -  Listen To The Wind.mp3,Hayley Westenra,(null),Listen to the  Wind,(null),(null),(null),00,0,0,1 Sending track  /home/cerapter/Musikk/Roteskuff/Hayley Westenra - Listen To The Wind.mp3  to /Music/07.19 World collide/Hayley Westenra - Listen To The Wind.mp3  type: mp3, 2 Sending track: Codec: ISO MPEG-1 Audio Layer 3 Title:  Listen to the Wind Artist: Hayley Westenra Storage ID: 0 Sending  track...  New track ID: 1475434407225 (100%)                      
```
---
> **glennric said:**
> The correct package is libgudev-1.0-dev.  However, you do not need to compile it.  If you add the repository ppa:glennric/mtp that I mentioned before you can simply install it with "sudo apt-get install playedit" (or use the software center).
That's great news! I successfully installed playedit, started it, and it was about to load up my music player when this happened:
```
cerapter@Ancalagon:~$ playedit
Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)
cerapter@Ancalagon:~$ 

```I can try and access the core dump if there's anything useful there.

---

### Post by Kevin McCready on 2012-07-21
Sorry I can't help. But recommend Hayley singing Maori song 

E Pari Ra
In 1918, Paraire Tomoana composed this tangi to Maori solders lost in battle during World War 1. song is based on one sung in about 1824 by a young Hawkes Bay chief. Titirangi Pa had been overrun by Ngaphi and Uruwera warriors, and the chief's lover was being carried off into slavery.
[http://www.youtube.com/watch?v=KCYOYfRatQ8](http://www.youtube.com/watch?v=KCYOYfRatQ8)

---

### Post by glennric on 2012-07-21
> **Cerapter said:**
> 
That's great news! I successfully installed playedit, started it, and it was about to load up my music player when this happened:
```
cerapter@Ancalagon:~$ playedit
Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)
cerapter@Ancalagon:~$ 

```I can try and access the core dump if there's anything useful there.

Hmm, that is odd.  Yeah, if you can send me the core dump it would help.  It seems to be having a problem loading album art from the device.

---

### Post by Cerapter on 2012-07-22
> **glennric said:**
> Hmm, that is odd.  Yeah, if you can send me the core dump it would help.  It seems to be having a problem loading album art from the device.
I've uploaded a dump [here]("http://www.file.cerapter.net/core_bixpuf").

--

In the libmtp documentation are examples of mtp-programs, some of which seem to resemble the mtp-tools. I've tried to compile these, but so far I'm stuck at this point:
```
cerapter@Ancalagon:~/Downloads/MTP/c-attempt$ gcc sendtr2.c -lmtp -o sendtr2
sendtr2.c:12:20: fatal error: config.h: No such file or directory
compilation terminated.
cerapter@Ancalagon:~/Downloads/MTP/c-attempt$ 
```Whether this is due to a missing package, incorrect way of compiling, incomplete gcc installation, or some other reason, I do not yet know. In fact, a range of includes in this c file seem to be out of reach:
```
#include "config.h"
#include "common.h"
#include "util.h"
#include "connect.h"
#include "libmtp.h"
#include "pathutils.h"
```The exception is libmtp.h, which seems to be located correctly by the compiler. I guess these files could be part of the source code, which I do not yet have the wits to acquire.

---

### Post by Cerapter on 2012-07-23
I finally taught myself how to get at source codes. At first I thought I had to figure out git, but then I stumbled upon this:
```
sudo apt-get build-deb libmtp
sudo apt-get source libmtp
```Once I realized where the source was put (current directory), I soon found the original C files of the mtp-tools. After some selective commenting-out and minimizing of printf() commands, I navigated to the root folder of the source package and compiled:
```
./configure
make
make install
```I now have a unique build of the mtp-tools that output exactly what I want. I went ahead and tried out my own scripts (posted here in case anyone else want to try and do something like this):

/home/cerapter/scripts/playlist_main.sh:
```
#!/bin/bash

ind_music=87
ind_max=500

pFile=$(zenity --file-selection --filename="/home/cerapter/Downloads/"  --title="Choose your CSV playlist")

if [ $? != 1 ]; then
    pName=$(zenity --entry --title="Playlist name" --text="Enter the name of the playlist (0 for guess)" --entry-text "0")
    # apparently doesn't work
    if [ $? -eq 1 ]; then 
        pName="Blubb gakk"
    fi
    
    today=$(date +%m.%d)
    gFolder="${today} ${pName}"
    
    echo "Executing: mtp-newfolder \"${gFolder}\" ${ind_music} 0"
    
    # don't need folder ID, but get it anyway
    ind_folder=$(mtp-newfolder "${gFolder}" ${ind_music} 0)
    wait ${!}
        
    echo "Created folder with ID ${ind_folder}"

    arg_accum=""
    for (( c=0; c<=ind_max; c++ ))
    do
        pArgs=$(python /home/cerapter/scripts/playlist_transfer.py "${pFile}" "${pName}" "${gFolder}" $c)
        command="mtp-sendtr ${pArgs}"
        
        if [ "$pArgs" == "STOP" ]; then
            echo "Reached end of CSV list."
            break
        fi
        
        echo "Executing: 'mtp-sendtr ${pArgs}'"
        
        # get track IDs!
        ind_track=$(eval $command)
        wait ${!}
        
        echo "Sent track to track ID ${ind_track}"
        
        arg_accum="${arg_accum} -i ${ind_track}"
    done
    
    echo "Executing: mtp-newplaylist -n \"${pName}\" ${arg_accum}"
    
    # and then get playlist ID (don't need this either)
    ind_list=$(mtp-newplaylist -n "${pName}" $arg_accum)
    wait ${!}
        
    echo "Made playlist with ID ${ind_list}"
fi

```/home/cerapter/scripts/playlist_transfer.py:
```
#!/usr/bin/python

import string, csv, sys

# from bash script:
playlist_file = str(sys.argv[1])
playlist_name = str(sys.argv[2])
gFolder = str(sys.argv[3])
counter = int(sys.argv[4])

# get music player directory
path = "/Music/" + gFolder + "/"

# get the current line of the CSV
fList = csv.DictReader(open(playlist_file, 'r'))
fList = list(fList)

# if last line is reached, say STOP!
try:
    row = fList[counter]
    # use the data from this line
    fPath = row['Folder'] + "/" + row['Filename']
    gPath = path + row['Filename']

    # build the mtp-sendtr command
    lTrack = '-q -t "'+row['Title']+'"'
    lTrack = lTrack + ' -a "'+row['Artist']+'"'
    lTrack = lTrack + ' -l "'+row['Album']+'"'
    lTrack = lTrack + ' -g "'+row['Genres']+'"'
    lTrack = lTrack + ' -n '+row['Track']
    lTrack = lTrack + ' -y '+row['Year']
    lTrack = lTrack + ' -d '+row['Length']
    lTrack = lTrack + ' -s 0 "'+fPath+'" "'+gPath+'"'
    #oTrack.wavecodec = 

    print lTrack
except IndexError:
    print 'STOP'
```**I have not yet succeeded.** I get this error output after calling a command that should work, and which works if I run it by itself manually afterwards:
```
Executing: mtp-sendtr -q -t "Chronologie Part.4" -a "Jean Michel Jarre" -l "Chronologie" -g "New Age" -n 4 -y 1993 -d 239 -s 0 "/home/cerapter/Musikk/Artister/Jean Michel Jarre - Chronologie Part.4.mp3" "/Music/07.23 Snupp tupp/Jean Michel Jarre - Chronologie Part.4.mp3"
Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
usage: sendtr [ -D debuglvl ] [ -q ]
-t <title> -a <artist> -A <Album artist> -w <writer or composer>
    -l <album> -c <codec> -g <genre> -n <track number> -y <year>
       -d <duration in seconds> -s <storage_id> <local path> <remote path>
(-q means the program will not ask for missing information.)
```I'm now going to look into the C files again to trace back and troubleshoot this error. It does take a while, since between each attempt I have to wake up, unmount and clean up the player..

**EDIT: ** Script works now, updated code.

---

### Post by asmoore82 on 2012-07-23
Forgive me for asking, but have you tried the MTP plugin for Rhythmbox?

Or even better, just mounting it with mtpfs.

---

### Post by Cerapter on 2012-07-23
> **asmoore82 said:**
> Forgive me for asking, but have you tried the MTP plugin for Rhythmbox?

Or even better, just mounting it with mtpfs.
Of course, I might've overlooked it. But I'm pretty sure I tried that and that Rhythmbox crashed. Amarok and Clementine could find the player, but not do anything with it. I've also tried Qlix and MTP Navigator (both crash with strange error messages, or simply segmentation fault). gMTP I think also crashed, although it wouldn't be able to handle playlists anyway.

In fact, the player mounts fine and I can access it in nautilus. I can even transfer files by drag and drop and edit playlists in gedit - but these changes are unnoticed by the player. I realized that nautilus does not tell the player that a music file is a music file, so it's overlooked. And as for playlists, when I edit them, the name vanishes in the player, and if I add tracks, they are ignored.

I'm suspecting this is due to quirks of how MTP is implemented in my player, and it might be hard to work around it. Luckily, the mtp-tools work perfectly, thus my approach so far.

---

### Post by Cerapter on 2012-07-23
My script now works! It will load a .csv file (which is how gmusicbrowser exports playlists), make a new folder, send all tracks of the playlist to that folder, and add them all to a brand new playlist!

The only problem is that currently, *it takes more than 10 seconds for each and every file*. This due to the fact that it connects and disconnects the mp3 player between every upload. I guess I'd have to do some hard core rewriting of the mtp-tools to make it otherwise.

---

