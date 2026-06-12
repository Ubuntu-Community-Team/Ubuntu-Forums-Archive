---
title: "passing a full filepath in Bash"
date: 2009-07-20
forum: Programming Talk
---

### Post by prupert on 2009-07-20
Hi there

I'd be very gratefull if someone could help.
I've tried searching, but I can't find search terms that give the answer.

I have created a simple bash script, that converts the .ts and .m2ts files in a folder using handbrake. I then want to use mkvmerge to add chapter information to these mkv files that handbrake creates (so the adverts can be skipped).

In my transcode script I use this line to search for all the mkv files that handbrake has created earlier on in the script:

```
find /mnt/media/documents/ruperts/TV -name "*.mkv" -exec /home/server/scripts/mkvmerge.sh {} \; >> /mnt/media/documents/ruperts/TV/trans.log
```

In theory, this should find all the .mkv files in the folder and pass them one at a time to my mkvmerge.sh script. This is the contents of the mkvmerge.sh script:

```

#!/bin/bash
VIDEO=$1
ENC=${VIDEO##*/}
mkvmerge --chapters ${VIDEO%/*}/${ENC%%.*}.chap $VIDEO -o /media/video/Video/TV/${ENC%%.*}.mkv
```

The "--chapters" switch tells mkvmerge the full filepath and name of the .chap file. Then I pass it the name of the mkv file, and then I tell it where to save the output to with the "-o" switch. The problem I am having is that it isn't passing the full filepath to mkvmerge, as soon as there is a space in the filename, it treats that as the full file path (so it passes /media/documents/Ruperts/TV/The instead of /media/documents/Ruperts/TV/The Big Brother.mkv). I am sure I need to use double or single quotes somewhere, but I am not sure where.

The reason for all the crazy syntax stuff is that the files are named using the following method (a result of the files originally being created on a Windows XP box and being processed by batch script on that machine (as the advert checking software is Windows based)). Say the film is called ROBOCOP.ts, this is converted by Handbrake into ROBOCOP.ts.mkv, thus the chapter marker file is called ROBOCOP.ts.chap. I need to pass both the full path to the mkv file path (from the find command) and also the name of the .chap file as well.

To clarify, I have no problem getting mkvmerge to run, this isn't my issue, the problem I initially seem to have is how to pass the full file path to any program if it includes spaces.

Essentialy the steps I am trying to achieve are:

1) find all the files of type /PATH1/NAME1.mkv
2) for each file of type /PATH1/NAME1.mkv, process them with mkvmerge, also passing files of type /PATH1/NAME1.chap to mkvmerge (the file path and name is the same, except instead of it having a .mkv extention is has a .chap).

Can anyone suggest a solution to my problem, or a more gracefull way to achieve this via bash than using the find --exec command??

---

### Post by unutbu on 2009-07-20
Put quotation marks around the {}. This will protect single-arguments-with-spaces from being broken into multiple arguments.
```

find /mnt/media/documents/ruperts/TV -name "*.mkv" -exec /home/server/scripts/mkvmerge.sh "{}" \; >> /mnt/media/documents/ruperts/TV/trans.log

```
Another common way to solve this problem is to use "find . -print0" and "xargs -0":
```

find /mnt/media/documents/ruperts/TV -name "*.mkv" -print0 | xargs -0 -I{} /home/server/scripts/mkvmerge.sh {} >> /mnt/media/documents/ruperts/TV/trans.log
```

This prints the filename with a null character at the end. 
"xargs -0" then accepts this as input and breaks the filenames apart correctly.

---

### Post by prupert on 2009-07-20
Thanks very much for the speedy answer, I will try out the quotes as suggested and also read up on the print and xargs command to see how they work.

Thanks once again.

Regads
prupert

---

### Post by unutbu on 2009-07-20
You might also need to put quotation marks around arguments to the mkvmerge command in your script:
```

mkvmerge --chapters "${VIDEO%/*}/${ENC%%.*}.chap" "$VIDEO" -o "/media/video/Video/TV/${ENC%%.*}.mkv"
```

---

### Post by prupert on 2009-07-20
AHA

That did it, yeah, your first correction still resulted in an error, but including the quotes in the mkvmerege.sh script fixed it.

Cheers, thanks loads for the help.

So, for completeness and to aid anyone else reading this looking for answer, this is what I ended up doing:

My transcode script, that is called by cron:
```

#!/bin/bash
# ffmpeg and mencoder script
# Written by FakeOutdoorsman and updated by mysoogal further updated by prupert
# Attribution-Noncommercial 3.0 Unported
# http://creativecommons.org/licenses/by-nc/3.0/deed.en
# trackback http://ubuntuforums.org/showthread.php?t=960627

echo trans.sh started on `date "+%m/%d/%y %l:%M:%S %p"` > /mnt/media/documents/ruperts/TV/trans.log
chmod -R 777 /mnt/media/documents/ruperts/TV

find /mnt/media/documents/ruperts/TV -name "*.ts" -exec /home/server/Desktop/handbrake/HandBrakeCLI -i {} -t 1 -c 1 -o {}.mkv -f mkv -w 720 -e xvid -b 1200 -2  -a 1 -E faac -B 160 -R 0 -6 dpl2 -D 1 -C 2  -v '{}' \; >> /mnt/media/documents/ruperts/TV/trans.log

find /mnt/media/documents/ruperts/TV -name "*.m2ts" -exec /home/server/Desktop/handbrake/HandBrakeCLI -i {} -t 1 -c 1 -o {}.mkv -f mkv -w 720 -e xvid -b 1200 -2  -a 1 -E faac -B 160 -R 0 -6 dpl2 -D 1 -C 2  -v '{}' \; >> /mnt/media/documents/ruperts/TV/trans.log

echo trans.sh finished on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log

echo attempting to add advert chapter markers on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log

find /mnt/media/documents/ruperts/TV -name "*.mkv" -exec /home/server/scripts/mkvmerge.sh "{}" \; >> /mnt/media/documents/ruperts/TV/trans.log

echo advert chapter markers added on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log
echo starting clear up on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log

find /mnt/media/documents/ruperts/TV -name "*.ts" -exec rm {} \; >> /mnt/media/documents/ruperts/TV/trans.log
find /mnt/media/documents/ruperts/TV -name "*.m2ts" -exec rm {} \; >> /mnt/media/documents/ruperts/TV/trans.log
find /mnt/media/documents/ruperts/TV -name "*.mkv" -exec rm {} \; >> /mnt/media/documents/ruperts/TV/trans.log
find /mnt/media/documents/ruperts/TV -name "*.edl" -exec mv {} /media/video/Video/TV \; >> /mnt/media/documents/ruperts/TV/trans.log
find /mnt/media/documents/ruperts/TV -name "*.txt" -exec mv {} /media/video/Video/TV \; >> /mnt/media/documents/ruperts/TV/trans.log
find /mnt/media/documents/ruperts/TV -name "*.chap" -exec mv {} /media/video/Video/TV \; >> /mnt/media/documents/ruperts/TV/trans.log

echo ts/m2ts files deleted and moved script stopped on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log

exit
```


And then this is the mkvmerge.sh script that the above script calls to add chpater markers to the mkv file.
```

#!/bin/bash
echo mkvmerge.sh started on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log
VIDEO=$1
ENC=${VIDEO##*/}
mkvmerge --chapters "${VIDEO%/*}/${ENC%%.*}.ts.chap" "$VIDEO" -o "/media/video/Video/TV/${ENC%%.*}.mkv"
```

And it all works very well so far, thanks!!

NOTE: for anyone else to use these scripts, they will have to change the locations etc. I have just posted them here so that people see what I ended up doing to fix the original problem I had.

---

