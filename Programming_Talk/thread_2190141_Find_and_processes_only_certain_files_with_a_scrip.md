---
title: "Find and processes only certain files with a script"
date: 2013-11-26
forum: Programming Talk
---

### Post by squakie on 2013-11-26
It seems like this should be doable, but I don't know how.  Here's the detail:

I have MANY media files on one of my Raspberry Pi media centers that I somehow messed up and they show internally as MPEG-PS even thought the external file type is some verion of .mp4, .m4v, etc.  I don't know how I did it.  Anyway,   XBMC on the Pi won't play the video from those files - it thinks they are just audio.  I need to find all of them so I can run them through OpenShot to export them as MP4 video files.

So, I connected the drive (USB hard drive) to my Ubuntu box, then set my working directory as follows:

cd /media/dave/xbmc-shares/VIDEOS

This directory contains many subdirectories in various trees.  I know I can search for a file type, such as any mpeg type file, following the trees by using find starting at the working directory as:

find . -name *.m??

This results in a list, containing the path from the working directory, of all files ending in .m'xx'.

I can also run mediainfo against each one of those files individually via:

mediaiinfo <my video file name here>

The output from mediainfo contains, amongst other things, something like MPEG-4, or in the case of the files I am looking for, MPEG-PS.[COLOR=#ff0000] (EDIT:  it appears it is PS - the letter "S", not P and the number 5 - bad eyeballs)[/COLOR]

I know I should be able to use grep somehow to find if the output of mediainfo contains MPEG-P5, but so far my attempts haven't worked:

mediainfo <my video file name here> | grep MPEG-P5

[COLOR=#ff0000]EDIT:  just fixed the grep itself:

mediainfo <my video file name here> | grep '[/COLOR]MPEG-PS'



So what do I really need?  Well, these were to be building blocks to (I hoped) some sort of script I could run from the "VIDEOS" directory that would print out the full path to only those files whose type, via mediainfo, is MPEG-P5.

Somehow I've got to find a way to automate all of this, and that's the first step.

Since you've seen what I've tried and what I want to do, could anyone help out here, step by step, explained in a way that myself and others not versed on the shell my be able to understand?  Not looking for "here it is", but rather "this is it, and line 'x' means to ....".

Thank you so much if you can help on any of this!

---

### Post by steeldriver on 2013-11-26
One nice way to do this kind of thing is with a while loop

```

while read -rd $'\0' file; do 
  *something with* "$file"
done < <(find */path/to/dir* -name '*.m??' -print0)

```

(the print0 ... read -d $'\0' stuff makes it safe for all kinds of filenames). Another fairly safe way would be something like

```

find */path/to/dir* -name '*.m??' -exec *something on* {} +

```

Which fits better depends what *something* you want to do on the files

---

### Post by squakie on 2013-11-26
Well, I found on the net what might be another piece to this - somehow walking files in a folder:

for file in *.{jpg,JPG}; do
if [[ -f "$file" ]]; then
echo "$file"
fi
done

So, I haven't had any luck yet, but perhaps something along these lines:

find . -name *.m?? > testfolder/
cd testfolder
for file in *.*; do
if [[mediainfo $file | grep 'MPEG-PS' ]]; then
echo "$file"
fi
done

I'm not really sure what that would be doing - I assume I could output the file name list from the find to a folder, use the for loop to run each one of those files through mediainfo and grep and print the filename?

Trying to do this I run into a couple of problems:

- the output of file names from the find has to go to a file, not a folder
- the file names will be in a ./some folder(s)/file name which could contain characters for which the entire file name output from the find needs to be in quotes

---

### Post by Bucky Ball on 2013-11-26
*Thread moved to **Programming Talk**.*

---

### Post by steeldriver on 2013-11-26
So how about

```

while read -rd $'\0' file; do 
  if mediainfo "$file" | grep -q 'MPEG-PS'; then
    echo "$file"
  fi
done < <(find /path/to/dir -name '*.m??' -print0)

```

or

```

while read -rd $'\0' file; do 
  mediainfo "$file" | (grep -q 'MPEG-PS' && echo "$file")
done < <(find /path/to/dir -name '*.m??' -print0)

```

---

### Post by squakie on 2013-11-26
I don't have any clue what you wrote - sorry.  Perhaps you could explain it to me - that would be greatly appreciated!

I also tried this but it didn't work:

#!/bin/bash

cd /media/dave/xbmc-shares/VIDEOS

find . -name *.m?? > /home/dave/videofilenames.txt

FILE = /home/dave/videofilenames.txt

while_read_LINE()
{
if [[mediainfo $LINE | grep 'MPEG-PS' ]]; then
echo $LINE >> checkthesefiles.txt
}
fi
done

---

### Post by Bucky Ball on 2013-11-26
@squakie: Please use [code] tags.

---

### Post by squakie on 2013-11-26
Well, this wants to run, but for some reason gives me a permissions error on writing a file in my own folder:

```
dave@davepc ~ $ cat testit.sh
#!/bin/bash

cd /media/dave/xbmc-shares/VIDEOS

find . -name *.m?? > /home/dave/videofilenames.txt

# $FILE = /home/dave/videofilenames.txt

[COLOR=#ff0000]EDIT:  This: [/COLOR]/home/dave/videofilenames.txt

[COLOR=#ff0000][/COLOR][COLOR=#ff0000]needed to be this:

cat [/COLOR][COLOR=#ff0000] [/COLOR]/home/dave/videofilenames.txt[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]

while read LINE
do

if [[mediainfo "$LINE" | grep 'MPEG-PS' ]]; then
echo $LINE >> checkthesefiles.txt
fi

done
dave@davepc ~ $ 


```

I don't understand why?  [COLOR=#b22222]EDIT: forgot the "cat" on the front of the file name.  This seems to work, however all output seems to be coming to the terminal, not being redirected to the file.


[/COLOR]

---

### Post by squakie on 2013-11-26
Okay, I think it is actually working.  It appears to be echoing to the screen as well as the file, and I guess I'm just not waiting long enough for it to finish.

EDIT:  NOPE.  Now it's not creating the file, and it just hangs there - I assume in the loop but I don't have a clue.  Help? ;)

---

### Post by squakie on 2013-11-26
> **steeldriver said:**
> So how about

```

while read -rd $'\0' file; do 
  if mediainfo "$file" | grep -q 'MPEG-PS'; then
    echo "$file"
  fi
done < <(find /path/to/dir -name '*.m??' -print0)

```

or

```

while read -rd $'\0' file; do 
  mediainfo "$file" | (grep -q 'MPEG-PS' && echo "$file")
done < <(find /path/to/dir -name '*.m??' -print0)

```

Just so I understand this:

the output of the find, the filenames are placed, via the -print0, into a file called 0. The while loop reads (-rd $'\0' file" reads that file line by line and does the processing?  Or is it 1 file name at a time is place in 0 and processed?

Thanks.

---

### Post by squakie on 2013-11-26
Please help??

I've done this:```
#!/bin/bash

cd /media/dave/xbmc-shares/VIDEOS
find . -name *.m?? > /home/dave/videofilenames.txt
cat /home/dave/videofilenames.txt | while read LINE;
   do

# for debugging:
echo "$LINE"

      if [[mediainfo "$LINE" | grep 'MPEG-PS' ]]; then
          echo $LINE >> /home/dave/checkthesefiles.txt
      fi
done 
echo "DONE...." 
```


and a snippet of the output:```
./WESTERNS/The.Proud.Rebel(1958)/The.Proud.Rebel.m4v
./testit.sh: line 11: [[mediainfo: command not found
grep: ]]: No such file or directory

```

From the echo I put in for debugging, I can see the file name string.  I believe the reason it is failing is because of the special characters "(" and ")" in the file name in the snippet of output.  There can also be other special characters in the file name, and that is why I was trying to quote it for the mediainfo string - I want it, for the example to read:

      if [[mediainfo "./WESTERNS/The.Proud.Rebel(1958)/The.Proud.Rebel.m4v" | grep 'MPEG-PS' ]]; then

I'm starting to think I need to quote the quoted string "$LINE" so that the result is quoted - I don't believe it is currently being quoted upon substitution.

How do you quote a substituted string?

[COLOR=#ff0000]EDIT:  I think maybe it's not finding mediainfo - so I added the full path:

      if [[/usr/bin/mediainfo.pyc \"$LINE\" | grep 'MPEG-PS' ]]; then
 
to which I now get:

"./WESTERNS/The.Proud.Rebel(1958)/The.Proud.Rebel.m4v"
./testit.sh: line 11: [[/usr/bin/mediainfo.pyc: No such file or directory 
 grep: ]]: No such file or directory

This makes me think 2 things:

- my quoted strings are working now that I "escaped" them
- for whatever reason it just plain isn't finding mediainfo itself

I don't get it at all.




EDIT-EDIT:  I tried adding another statement for debugging - mediainfo --help.  It does print out it's help, so at that point mediainfo is found.  Is this a case where it does something with a "sub-shell" and something isn't be "caught", "passed" or whatever?

Latest script:

#!/bin/bash

cd /media/dave/xbmc-shares/VIDEOS
find . -name *.m?? > /home/dave/videofilenames.txt
cat /home/dave/videofilenames.txt | while read LINE;
   do

# for debugging:
echo \"$LINE\"
mediainfo --help

      if [[mediainfo \"$LINE\" | grep 'MPEG-PS' ]]; then
          echo $LINE >> /home/dave/checkthesefiles.txt
      fi
done 
echo "DONE...." 

[/COLOR]

---

### Post by steeldriver on 2013-11-26
I still think you would be better off using the while ... read loop I posted previously. One obvious thing is that the [[ and ]] are operators that need space around them e.g.

```
**[[ **"$somevar" = "someval"** ]]**
```

That is likely the reason you get "[[mediainfo : command not found"

Regarding **-print0** it just tells find to output the found files to stdout exactly the same as a regular find command, except separated by null characters (character value 0) instead of newlines. The **-d $'\0'** tells read to expect nulls separating the list of files. This is overkill in most situations but strictly speaking the null character is the only character guaranteed not to be part of a filename, and it doesn't cost anything - so it's a good practice to get into. The '-r' argument to read says treat backslashes literal characters not as escape characters. No additional files are involved - the list of files is just buffered up and read one at a time and passed into whatever sequence of commands you stick in the middle part.

---

### Post by squakie on 2013-11-26
Thank you so much for the explanation!

Here's the script when I tried to incorporate my path and conditional in it:

```
[#!/bin/bash

while read -rd $'\0' file; do 
  if [[ mediainfo "$file" | grep 'MPEG-PS' ]]  then
     echo $file > dothesefiles.txt
  fi
done < <(find /media/dave/xbmc-shares/VIDEOS -name '*.m??' -print0
```


I get a different error now - apparently my "IF" must need some other part(s) to it:

```
./testit2.sh: line 4: conditional binary operator expected
./testit2.sh: line 4: syntax error near `"$file"'
./testit2.sh: line 4: `  if [[ mediainfo "$file" | grep 'MPEG-PS' ]]  then'

```

As you can tell - I really don't know what the heck I'm doing here ;)

EDIT:  Okay, I found out what the error is in my "if", but I really don't know how to fix it.  I tested the statement inside the [[ ]] with a single file in terminal, and the result is:

```
dave@davepc /media/dave/xbmc-shares/VIDEOS/ACTION ADVENTURE/Saving.Private.Ryan(1998) $ mediainfo Saving.Private.Ryan.mp4 | grep 'MPEG-PS'
Format                                   : MPEG-PS
dave@davepc /media/dave/xbmc-shares/VIDEOS/ACTION ADVENTURE/Saving.Private.Ryan(1998) $ 

```

I changed my script (didn't want to screw up more with your script until you see what I did to it):

#!/bin/bash

cd /media/dave/xbmc-shares/VIDEOS
find . -name *.m?? > /home/dave/videofilenames.txt
cat /home/dave/videofilenames.txt | while read LINE;
   do

# for debugging:
echo \"$LINE\"

if ( "[[ mediainfo \""$LINE"\" | grep 'MPEG-PS' ]]" == "Format                                   : MPEG-PS"); then
      echo $LINE >> /home/dave/checkthesefiles.txt
fi
done 
echo "DONE...." 


A line of the output now shows:
```
"./WESTERNS/The.Proud.Rebel(1958)/The.Proud.Rebel.m4v"
./testit.sh: line 11: [[ mediainfo "./WESTERNS/The.Proud.Rebel(1958)/The.Proud.Rebel.m4v" | grep 'MPEG-PS' ]]: No such file or directory
DONE....

```

So, I'm getting a quoted path to mediainfobut obviously still doing something wrong.  BTW - is there some way to substring in the shell?  The "Format                                   : MPEG-PS"  has LOT more spaces between the ":" and the "M", so I was wondering if there was a way to substring that down (like "contains" "MPEG-PS" only.

As soon as this works (I just want to see this script through) then I want to go back and do the same to your script and use it as it seems much cleaner.

---

### Post by squakie on 2013-11-26
Okay, found "cut".  Now trying to use it I'm getting a syntax error.

Script now:```
#!/bin/bash

cd /media/dave/xbmc-shares/VIDEOS
find . -name *.m?? > /home/dave/videofilenames.txt
cat /home/dave/videofilenames.txt | while read LINE;
   do

# for debugging:
echo \"$LINE\""
if ( \"[[ mediainfo \""$LINE"\" | grep 'MPEG-PS' ]]" | cut -f3 -d ' ' )\" == "MPEG-PS" ); then
      echo $LINE >> /home/dave/checkthesefiles.txt
fi
done 
echo "DONE...." 
```


Error message:

```
./testit.sh: line 10: syntax error near unexpected token `)'
./testit.sh: line 10: `if ( \"[[ mediainfo \""$LINE"\" | grep 'MPEG-PS' ]]" | cut -f 3 -d ' ')\" == "MPEG-PS" ); then'

```

All that I added was to do the compare on a substring of the output of grep to just the MPEG-PS part.

If I can get this working, then I can put the same "if" statement in your (steeldriver) script since it is much cleaner.

---

### Post by steeldriver on 2013-11-26
Did you try the version, exactly as I posted it? You don't need the [[ ... ]] test construct I think, you can just do

```

while read -rd $'\0' file; do 
  **if mediainfo "$file" | grep -q 'MPEG-PS'; then**
    echo "$file"
  fi
done < <(find /path/to/dir -name '*.m??' -print0[COLOR=#ff0000]**)**[/COLOR]

```

which uses the *exit status* of the grep command - successful exit (true) means the text was found

---

### Post by squakie on 2013-11-26
I just made my script as yours:

```
#!/bin/bash
cd /media/dave/xbmc-shares/VIDEOS 
while read -rd $'\0' file; do 
  if mediainfo "$file" | grep -q 'MPEG-PS'; then
    echo "$file" >> ~/checkthesefiles.txt
  fi
done < <(find . -name '*.m??' -print0)
echo "DONE...."
```

and it is working!  Thank you!  Just for my education, if I had changed the "if" to match yours, would my script have worked?

Just curious, as I'm really trying to learn ;)

Again, thank you SO MUCH!!

---

