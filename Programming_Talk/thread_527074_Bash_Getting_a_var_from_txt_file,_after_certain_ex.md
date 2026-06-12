---
title: "Bash: Getting a var from txt file, after certain exp + keep a command open while cont"
date: 2007-08-16
forum: Programming Talk
---

### Post by kwaanens on 2007-08-16
I'm making a small script for myself, converting video, based on ffmpeg.

I'm using idvid from Tovid, shich shows output like this:

```
Analyzing file: '/media/arkiv/video/musikk/el_caco/el_caco_-_a_nice_day.wmv'. This may take several minutes...
=========================================================
               File: /media/arkiv/video/musikk/el_caco/el_caco_-_a_nice_day.wmv
              Width: 640 pixels
             Height: 480 pixels
       Aspect ratio: 1.33:1
             Frames: 0
           Duration: 00:03:33 hours/mins/secs
          Framerate: 1000.000 frames per second
       Video format: WMV1
      Video bitrate: 0 bits per second
---------------------------
Audio track 1 (Stream 0.0, AID 0):
---------------------------
              Codec: wmav2
            Bitrate: 192000 bits per second
      Sampling rate: 48000 Hz
```

The output from idvid is a little more filled with useless crap, so I grep the relevant info, and put it into a file, zenity outputs this file like so:
```
zenity --text-info --filename=/home/ketil/.wmvtoavi/log/out --width=600 --height=400
```

Now, I'd like to be able to pick out e.g. "640" after "Width" and "480" after "Height", and mash them up so that the default $aspect_ratio for this file is 640x480. Does anyone know how I can manage that?

----

Also, I'd like to keep having the zenity command given above open, while the next dialogs come up, and end it before the actual command is run. I tried with a while/do loop, but seems I don't really understand how it works. I've been scanning the abs-guide, but need some assistance in this (I guess, pretty easy) regard.

Thanks!

- Ketil

---

### Post by ghostdog74 on 2007-08-16
```

awk '{gsub("--height=","",$NF);gsub("--width=","",$(NF-1));print $NF,$(NF-1) }' file

```

---

### Post by kwaanens on 2007-08-16
I might be very dim, but do not understand this. Running the command on my file gets me:

 ```
awk '{gsub("--height=","",$NF);gsub("--width=","",$(NF-1));print $NF,$(NF-1) }' .wmvtoavi/log/out 
/media/arkiv/funnyvideos/bikerack.wmv File:
pixels 320
pixels 240
1.33:1 ratio:
0 Frames:
hours/mins/secs 00:00:29
second per
WMV2 format:
second per
0): AID
wmav2 Codec:
second per
Hz 32000
```

The file looks like:
               File: /media/arkiv/funnyvideos/bikerack.wmv
              Width: 320 pixels
             Height: 240 pixels
       Aspect ratio: 1.33:1
             Frames: 0
           Duration: 00:00:29 hours/mins/secs
          Framerate: 30.000 frames per second
       Video format: WMV2
      Video bitrate: 0 bits per second
Audio track 1 (Stream 0.0, AID 0):
              Codec: wmav2
            Bitrate: 40000 bits per second
      Sampling rate: 32000 Hz

So basically, it stripped "height" and "width", and for the others, it removed e.g. "Sampling rate" and moved "hz" in front of "32000".

So unless I don't understand anything, it looks like it doesn't do what I need.

- Ketil

---

### Post by duff on 2007-08-16
```
# WIDTH=$(grep 'Width:' .wmvtoavi/log/out | awk '{print $2}')
```

---

### Post by kwaanens on 2007-08-16
> **duff said:**
> ```
# WIDTH=$(grep 'Width:' .wmvtoavi/log/out | awk '{print $2}')
```

That one did the trick. I ended up doing:
```

WIDTH=$(grep 'Width:' .wmvtoavi/log/out | awk '{print $2}')
HEIGHT=$(grep 'Height:' .wmvtoavi/log/out | awk '{print $2}')
DEFAULT_FRAMESIZE="$WIDTH"x"$HEIGHT"
FRAMESIZE=`zenity --entry --text="Enter frame size. Default value has been read from input file. Change at will." --entry-text="$DEFAULT_FRAMESIZE"`
```

Probably could have been done smoother, but at least it works.

Now, my other problem, how do I keep the script from waiting at:
```
zenity --text-info --filename=/home/ketil/.wmvtoavi/log/out --width=600 --height=400
```
until I close it? It's nice to have the file information open while I go through the rest of the process.

- Ketil

---

### Post by Chaotic Thought on 2007-08-16
> **kwaanens said:**
> 
Now, I'd like to be able to pick out e.g. "640" after "Width" and "480" after "Height", and mash them up so that the default $aspect_ratio for this file is 640x480. Does anyone know how I can manage that?


If you want to save just the numbers for height and width, the trick I like to use is bash's parameter expansion to strip off the section before the number and then the section after the number. Suppose you save your command's output in a file "idvid.out", then we can use grep to save a line into a variable that looks like this (including the whitespace):

```
"          Width: 640 pixels"
```

We'll save this line into a variable, then strip off the beginning (from the beginning of the line up to and including the "Width: " part, then strip off the end (from the " pixels" part to the end of the line), then save the result in a new variable called $width, and then do the same thing for the height.

```

str=$(grep "Width" idvid.out)
str=${str##*Width: }
str=${str%% pixels*}
width=$str

str=$(grep "Height" idvid.out)
str=${str##*Height: }
str=${str%% pixels*}
height=$str

echo "${width}x${height}"

```


Sample output:

**640x480**


To find out more about bash's parameter expansion, do a search for "Parameter Expansion" in the bash(1) manpage.




----
> 
Also, I'd like to keep having the zenity command given above open, while the next dialogs come up, and end it before the actual command is run. I tried with a while/do loop, but seems I don't really understand how it works. I've been scanning the abs-guide, but need some assistance in this (I guess, pretty easy) regard.

Thanks!

- Ketil

If you add **&** to the end of your **zenity** command, then your script will *not* wait for zenity to finish. Otherwise, bash waits for zenity to return. Not sure if that's what you were asking, but give ampersand a try--it is one of the most powerful bash operators.

---

