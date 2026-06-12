---
title: "Cron Job - Shell script encode/output"
date: 2008-05-23
forum: Programming Talk
---

### Post by editorreilly on 2008-05-23
Could anyone help me with this.  I am going to run a cron job on this script to encode .mov to .avi and push it up to my server.  

----------------
#!/bin/sh

mencoder=/usr/bin/mencoder

echo -n "input file: "
read input

echo -n "output file: "
read output

$mencoder -vf scale=320:240 ~/Desktop/dropbox/"$input".mov -o ~/Desktop/movies/upload"$output".avi -of avi -ofps 29.97 -ovc \
lavc -oac lavc -lavcopts vcodec=mpeg4:vbitrate=230:acodec=mp3:abitrate=64

HOST='xxx'
USER='xxx'
PASSWD='xxx'
FILE='~/Desktop/movies/upload/*.avi'

ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
cd /mywebsite.net/movies
mput $FILE
quit
END_SCRIPT

exit 0

----------

I like the way this works, but the user has to ssh from a remote computer to input the variables.

What I want to do is to automate it even more.  

I want to know if it is possible to have the script read the name of a file like "mymovie.mov" in the dropbox directory, encode it, and then rename it "mymovie.avi" without any input from the user.

Basically, I want the user to be able to drop a .mov file from a remote computer into ~/Desktop/dropbox/ and have it push to my server as a .avi without any work.  Were dealing with creative types....I have to make it foolproof.

Thanks for your help.

---

### Post by johnl on 2008-05-23
you can do something like the following:

```

#!/bin/bash

# set file seperate to be newline instead of space
# to prevent issues with spaces in file names.
IFS="$(echo -e "\n\r")"

# find all .mov files in ~/dropbox
for i in $(find ~/dropbox -name '*.mov'); do
    # test.mov -> test.avi
    NEW_NAME="$(basename "$i" "mov")avi"
    echo "converting $(basename "$i") to $(basename $NEW_NAME)..."

    # do the conversion here 
    # input = "$i"
    # output = /path/to/wherever/$NEW_NAME
    
    echo "Done!"
    #remove the file or move it to something else...
    #mv "$i" "$i.converted"
done

```

---

### Post by dtmilano on 2008-05-23
Take a look at inotify and pyinotify to be notified on filesystem events.

---

### Post by editorreilly on 2008-05-23
Thanks Johnl.  I tried what you wrote, and couldn't seem to get it to incorporate without some kind of error.  This is what I put in the script:
------------
#!/bin/sh

IFS="$(echo -e "\n\r")"

for i in $(find ~/Desktop/videodrop/TIA -name '*.mov'); do

    # test.mov -> test.avi

    NEW_NAME="$(basename "$i" "mov")flv"

    echo "converting $(basename "$i") to $(basename $NEW_NAME)..."

mencoder=/usr/bin/mencoder

$mencoder -vf scale=320:240 "$i" -o /home/cm01/Desktop/convertfolder/"$NEW_NAME".flv -of lavf -oac mp3lame -lameopts abr:br=56 -ovc lavc -lavcopts vcodec=flv:vbitrate=800000:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -srate 22050 -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames
------------------------
When I run it, I get 

' unexpectedline 3: syntax error at line 5: `do

How did I screw up?

Thanks again!

---

### Post by geirha on 2008-05-23
> **editorreilly said:**
> Thanks Johnl.  I tried what you wrote, and couldn't seem to get it to incorporate without some kind of error.  This is what I put in the script:
------------
#!/bin/sh

IFS="$(echo -e "\n\r")"

for i in $(find ~/Desktop/videodrop/TIA -name '*.mov'); do

    # test.mov -> test.avi

    NEW_NAME="$(basename "$i" "mov")flv"

    echo "converting $(basename "$i") to $(basename $NEW_NAME)..."

mencoder=/usr/bin/mencoder

$mencoder -vf scale=320:240 "$i" -o /home/cm01/Desktop/convertfolder/"$NEW_NAME".flv -of lavf -oac mp3lame -lameopts abr:br=56 -ovc lavc -lavcopts vcodec=flv:vbitrate=800000:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -srate 22050 -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames
------------------------
When I run it, I get 

' unexpectedline 3: syntax error at line 5: `do

How did I screw up?

Thanks again!

That script is a bash script, but you are trying to run it with sh, which doesn't understand the syntax. Change #!/bin/sh to #!/bin/bash

Is that the whole script btw? the for-loop is missing it's closing "done" keyword. I'd use a while-loop like this instead of overriding IFS btw:

```

#!/bin/bash

encode="/usr/bin/mencoder -of lavf -oac mp3lame -lameopts abr:br=56 -ovc lavc -lavcopts vcodec=flv:vbitrate=800000:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -srate 22050 -lavfopts"
find ~/Desktop/videodrop/TIA -name '*.mov' | while read file; do
  dest="$(basename "$file" .mov).flv"
  $encode -o "$dest" "$file"
done

```

---

### Post by editorreilly on 2008-05-23
Thanks geirha!  That did it, but I did have to add back in the: 

i_certify_that_my_video_stream_does_not_use_b_frames"

for it to work properly. I've got a lot to learn.  Thanks for taking the time to help!

---

### Post by jbennert on 2008-05-28
Hi editorreilly,

I need a working script like this. Could you please post the final version here. I have no idea how to set this up. I can only change a path in the code. So when trying to modify the code beeing posted here I get syntax errors. Mencoder and ffmpeg is installed on my server.

Thanks a lot.

---

