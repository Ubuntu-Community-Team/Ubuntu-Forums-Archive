---
title: "Help For Some FFMEPG Commands"
date: 2008-05-30
forum: Programming Talk
---

### Post by yajur on 2008-05-30
i need Help For Some FFMEPG Commands,
First of all, I am not familiar with shell scripting, so I'm asking for your help. I want to do

I need to batch convert all my videos so i used the command for particular folder media/ipod so i used 

find /media/ipod -type f -exec mencoder {} -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=192 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=50 -vf scale,harddup -ofps 25 -zoom -xy 176 -o {}.mpg \;

now i need to convert all my avi videos to 3gp for folder via batch convert.please help for this commands

---

### Post by Quikee on 2008-05-30
> **yajur said:**
> i need Help For Some FFMEPG Commands,
First of all, I am not familiar with shell scripting, so I'm asking for your help. I want to do

I need to batch convert all my videos so i used the command for particular folder media/ipod so i used 

find /media/ipod -type f -exec mencoder {} -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=192 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=50 -vf scale,harddup -ofps 25 -zoom -xy 176 -o {}.mpg \;

now i need to convert all my avi videos to 3gp for folder via batch convert.please help for this commands

I don't know if this will work (it also uses ffmpeg instead of mencoder): 

```
find ~/downloads -name "*.avi" -type f -exec ffmpeg -i {} -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 \;

```

---

### Post by yajur on 2008-05-30
find ~/downloads -name "*.avi" -type f -exec ffmpeg -i {} -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 \;

Is this command help me in batch convert from avi to 3gp

I think i help in conversion of avi only,also can explain me cleraly bcz iam newbie to ffmepg

can give the exact command can batch convert the folder and subfolder from AVI to 3GP

---

### Post by yajur on 2008-06-01
ANy one can slove this issue

---

### Post by skullmunky on 2008-06-03
google told me:

[http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/](http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/)

```

ffmpeg -i video_clip.avi -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y clip.3gp

```

to convert avi to 3gp.  explanation:

-i video_clip.avi  : set the input file
-s qcif : set the size (resolution)
-vcodec, -acodec: set the codec.
-ar 8000 : audio rate is 8kHz
-r 25 : framerate is 25 frames per second

others i don't know but read the man page or ffmpeg docs until your eyes glaze over.

this does one file.  you need to batch convert a lot.  another way you can do this is using a loop in a shell script.  this one lists all the avi files in a directory:

```

for i in *.avi
do
echo $i
done

```

you need to put each of those into that ffmpeg command above, and also construct a new name with the .3gp extension.  in bash you can do that with this weird syntax:

```

for i in *.avi
do
echo $i
echo $i{%.avi}.3gp
done

```

the {%.avi} means chop off the .avi extension.  then .3gp gets added back.

so:

```

for i in *.avi
do
ffmpeg -i $i -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y ${i%.avi}.3gp
done

```

---

