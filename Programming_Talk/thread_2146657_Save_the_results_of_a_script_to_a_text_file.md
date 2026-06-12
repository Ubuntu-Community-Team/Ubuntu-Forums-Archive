---
title: "Save the results of a script to a text file"
date: 2013-05-19
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-05-19
Hi Guys,

I have a bash script that uploads videos to YouTube.

```


#!/bin/bash




cd /media/Elements/"Video Staging"/
read -p "Enter a title for the video:" titletext
read -p "Enter a description:" desc
read -p "Enter the file name:" video


""youtube-upload --unlisted -m email -p password -t "$titletext" -c People --description="$desc" "$video"


```

The script and the YouTube uploader that makes everything possible run well.
After a video has been uploaded the url for that video is displayed in the terminal.

Is there a way I can have that url saved automatically to a text file?  I've looked around a bit and saw something called "script".
When I entered script path/to/text/file the upload script everything seemed to come to a stop and I was given a new prompt.
Obviously this is not the way to go.

Does anyone know how I can do this?

---

### Post by Vaphell on 2013-05-19
can't you redirect your script or youtube-upload line to some file?
```
./script >> file #whole output
```
```
youtube-upload --unlisted -m email -p password -t "$titletext" -c People --description="$desc" "$video" >> file # only this line
```
>> is append

it's easy to dump info in a tidy format to file, give example of youtube-upload output.

what's up with that ""? i don't think empty string in front of youtube-upload is needed for anything.

---

### Post by steeldriver on 2013-05-19
You can redirect the standard output stream from your script to a file with the '>' operator

```
./yourscript > results.txt
```

If you want to redirect any errors to the file as well, 

 ```
./yourscript > results.txt 2>&1
```

In newer versions of bash you can use &> instead of the [FONT=courier new]*> file 2>&1*[/FONT] syntax e.g.

```
./yourscript &> results.txt
```

Or if you want to capture in a file AND see it in the terminal, you can 'tee' the stream

```
./yourscript | tee results.txt
```
or
```
./yourscript 2>&1 | tee results.txt 
```

If you want to append to the file instead of overwrite is, use 'tee -a'

```
./yourscript 2>&1 | tee -a results.txt 
```

---

### Post by GrouchyGaijin on 2013-05-19
Thanks guys - I thought I had tried > file and had an error.
Must have been a typo since it works now.

---

