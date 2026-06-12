---
title: "simple script to check if a file has been converted"
date: 2009-08-14
forum: Programming Talk
---

### Post by prupert on 2009-08-14
Hi

I have a transcode script that coverts my .ts files created by my HTPC into  .mkv files using handbrake. You can find the script at the end of the post here: 

[http://ubuntuforums.org/showthread.php?t=1218041](http://ubuntuforums.org/showthread.php?t=1218041)

Generally, it works really well, however, sometimes, and I am not sure why, Handbrake freaks out and crashes, and the files don't get converted. In case this happens, I want to add some checks to the end of my script, to check if the files were converted or not.

To do this, I was thinking I can use find to search for all .ts files in the source folder and then use find to search for all .mkv files in the destination folder and if the filenames are the same, then obviously the conversion has worked and it can delete the source files.

The problem I am having is, since the files are in two different folders, and since they now have different extentions, I have no clue how to get the script to check.

I have got this far:

```
#!/bin/bash
# an attempt to check that all the files were formed correctly

find /mnt/media/documents/ruperts/TV -name "*.ts" -print0 | xargs -0 ls > /home/server/scripts/temp.txt
# find /mnt/media/documents/ruperts/TV -name "*.ts" > /home/server/scripts/temp.txt
find /media/video/Video/TV/tmp/ -name "*.mkv" > /home/server/scripts/temp1.txt

if [ "/home/server/scripts/temp.txt" = "/home/server/scripts/temp1.txt" ]; then
	echo trans completed succesfully, starting clear up on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log
	find /media/video/Video/TV/tmp/ -name "*.mkv" -exec mv {} /media/video/Video/TV \; >> /mnt/media/documents/ruperts/TV/trans.log
	find /mnt/media/documents/ruperts/TV -name "*.ts" -exec rm {} \; >> /mnt/media/documents/ruperts/TV/trans.log
	find /mnt/media/documents/ruperts/TV -name "*.mkv" -exec rm {} \; >> /mnt/media/documents/ruperts/TV/trans.log
	find /mnt/media/documents/ruperts/TV -name "*.edl" -exec rm {} \; >> /mnt/media/documents/ruperts/TV/trans.log
	find /mnt/media/documents/ruperts/TV -name "*.txt" -exec rm {} \; >> /mnt/media/documents/ruperts/TV/trans.log
	find /mnt/media/documents/ruperts/TV -name "*.chap" -exec rm {} \; >> /mnt/media/documents/ruperts/TV/trans.log
	echo ts files deleted and moved script stopped on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log
else
	echo mkv not present, trans failed on `date "+%m/%d/%y %l:%M:%S %p"` >> /mnt/media/documents/ruperts/TV/trans.log
fi
```

But clearly this does not work. 

Essentially, say I had the following in /mnt/media/documents/ruperts/TV:

program 1.ts
program2.ts

If the transcode worked successfully, I should then have in /media/video/Video/TV/tmp/:

program 1.mkv
program2.mkv

So the script should hopefully find just the file names in both folders, so it should see:

program 1
program2

And thus it would know the transcode worked, but I dont know how I can parse the file names to get this result....

Can anyone help me??

Thanks

---

### Post by geirha on 2009-08-14
```

cd "/mnt/media/documents/ruperts/TV/" || { echo >&2 "Source folder not found"; exit 1; }
find . -type f -name "*.ts" -exec sh -c '[ -f "tmp/${1%.ts}.mkv" ]' _ {} \; -print

```

The above find should print all .ts-files that have a corresponding .mkv file under tmp/. So replacing -print with -delete should delete the converted ones. Please confirm that it works correctly first though.

EDIT: BTW, a better approach would be to check the exit status of handbrake for each conversion, and remove the source file right away if it completed successfully.

---

### Post by prupert on 2009-08-14
Wow, so simple, I guess it was the ${1%.ts}.mkv magic that I really needed. 

Thanks a lot, just test it and it works brilliantly.

Yeah, I guess using the handbrake exit status would be much more sensible, I guess I need to go off and figure out how to use that.

Thanks again ;)

Looks like handbrake doesn't deal with exit codes in the way you would expect. Its exit codes are only to show whether the program died or did not die, not whether the transcode worked or did not work. Ah well, your solution will suffice I feel.

---

