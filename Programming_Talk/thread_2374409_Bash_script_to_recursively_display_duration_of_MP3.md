---
title: "Bash script to recursively display duration of MP3 &amp; MP4 files"
date: 2017-10-15
forum: Programming Talk
---

### Post by oygle on 2017-10-15
There are some teaching sessions where the video duration/length is quite different to the audio lengths, and therefore I need to check the duration of all the videos and audios. I found this bash script to display the duration of MP3 files and simply modified it to display MP4 files as well ..

```

#!/bin/bash
for file in *.mp3 *.mp4
do
 duration=$(ffprobe "$file" 2>&1 | awk '/Duration/ { print $2 }')
 echo -e $duration"\t"$file
done | sort -n

```

and the output is ..

> 
00:29:06.67,    Session 3 - Session3Audio.mp3
00:29:30.60,    Session 3 - Session3Video.mp4
00:46:12.31,    Session 2 - Session2Audio.mp3
00:46:12.31,    Session 4 - Session4Audio.mp3
00:46:36.25,    Session 2 - Session2Video.mp4
00:54:45.74,    Session 1 - Session1Audio.mp3
00:55:09.70,    Session 1 - Session1Video.mp4
01:14:53.99,    Session 4 - Session4Video.mp4


but when I try the script in a higher level path/directory, where there are only folders (no files), the output is obviously an error because the script does not cater for going down all the paths recursively ..

> 
  *.mp3
        *.mp4


Can someone please tell me how to modify the bash script to make it do a recursive search. Also, I wanted to copy the output into a spreadsheet, so that the filename is first, then the duration. Is that simply a matter of adding a TAB character so that an import to the spreadsheet will be placed into columns.

---

### Post by norobro on 2017-10-15
Hi,


Use the find command and pipe it to the bash builtin read. ```
#!/bin/bash
find /root/dir -name "*.mp3" -o -name "*.mp4" | while read file;
do
 duration=$(ffprobe "$file" 2>&1 | awk '/Duration/ { print $2 }')
 echo -e $duration"\t"$file
done 

```
> **oygle said:**
>  Also, I wanted to copy the output into a spreadsheet, so that the filename is first, then the duration. 
Perhaps I misunderstand, but won't exchanging the the fields in the echo command do what you want?```
echo -e $file"\t"$duration
```

---

### Post by oygle on 2017-10-15
> **norobro said:**
> 
Use the find command and pipe it to the bash builtin read. ```
#!/bin/bash
find /root/dir -name "*.mp3" -o -name "*.mp4" | while read file;
do
 duration=$(ffprobe "$file" 2>&1 | awk '/Duration/ { print $2 }')
 echo -e $duration"\t"$file
done 

```


Great thanks, that works just fine, and goes down all the paths in a recursive manner.

> **norobro said:**
> 
Perhaps I misunderstand, but won't exchanging the the fields in the echo command do what you want?```
echo -e $file"\t"$duration
```

Yes that did it, thanks. here is the final version ..

```

#!/bin/bash
find /root/dir -name "*.mp3" -o -name "*.mp4" | while read file;
do
 duration=$(ffprobe "$file" 2>&1 | awk '/Duration/ { print $2 }')
 echo -e $file"\t"$duration
done | sort -n

```

---

### Post by oygle on 2018-01-14
That final solution isn't putting out a TAB in between the filename and the duration

```

#!/bin/bash
find ~/root/dir -name "*.mp3" -o -name "*.mp4" | while read file;
do
 duration=$(ffprobe "$file" 2>&1 | awk '/Duration/ { print $2 }')
 echo -e $file"\t"$duration
done | sort -n

```

I have tried modifying it to use ```
printf
``` but not sure how to use variables with "printf"

---

### Post by vasa1 on 2018-01-14
> **oygle said:**
> .... Also, I wanted to copy the output into a spreadsheet, so that the filename is first, then the duration. Is that simply a matter of adding a TAB character so that an import to the spreadsheet will be placed into columns.A tab isn't compulsory if you're using LibreOffice Calc.

You can use any other character that won't occur in your output. You could try #.

---

### Post by oygle on 2018-01-14
> **vasa1 said:**
> A tab isn't compulsory if you're using LibreOffice Calc.

You can use any other character that won't occur in your output. You could try #.

I use LibreOffice Calc and the "#" worked just fine, thanks very much.  :)

---

