---
title: "Help with bash script (dvd rip&gt;iso)"
date: 2007-05-18
forum: Programming Talk
---

### Post by tuckie on 2007-05-18
This is my script so far, that I have run as root via cron:
```
for directory in /mnt/raid/dump/*
do
        if [ -d "$directory" ] ; then
                echo $directory
                if ! test -d "$directory/VIDEO_TS" ; then
                        mv "$directory" /mnt/raid/dump/VIDEO_TS && mkdir "$directory" && mv /mnt/raid/dump/VIDEO_TS "$directory/VIDEO_TS"
                        echo "Created VIDEO_TS..."
                fi
                echo /mnt/raid/movies/${directory#"/mnt/raid/dump/"}
                mkisofs -dvd-video -udf -o "/mnt/raid/movies/${directory#"/mnt/raid/dump/"}.iso" "$directory"
                if [ -s "/mnt/raid/movies/${directory#"/mnt/raid/dump/"}.iso" ] ; then
                        rm -r "$directory" && echo "Deleting ${directory#"/mnt/raid/dump/"}..."
                fi
        fi
done
chown -R media:media /mnt/raid/movies
chmod -R 755 /mnt/raid/movies

```
It takes any directory from /mnt/raid/dump and attempts to make it into an iso locate at /mnt/raid/movies
The problem that I'm having is telling whether or not the folder is still being written to by dvd shrink, which is run from my windows machine connected via a samba share.  If the cron job runs, and dvd shrink is running, I'll get a bad iso generated, as well as it deleting the file from the dump directory.  Any other thoughts on improving the script would also be appreciated.

---

### Post by FuturePast on 2007-05-18
When dvd shrink is running you could put an empty file in the directory.
If that file is present then your script should skip the directory.
After dvd shrink finishes, the empty file gets deleted.

---

### Post by tuckie on 2007-05-18
how would I set that up to do that automatically?

---

### Post by tuckie on 2007-05-25
Does anyone have any idea as to why the script runs fine when I do a sudo ./scanmake.sh but only produces a 10 or so mb iso when I run it as a cron job?

---

### Post by jyba on 2007-05-25
This is a pure guess but I wonder if your script is a victim of the differences between bash and dash. When you run your script from the command line of a bash shell it works. When cron runs it using /bin/sh (which is symlinked to dash) it goes wrong.

Have you tried enforcing the use of bash by putting #!/bin/bash at the top of your script?

---

### Post by tuckie on 2007-05-26
> **jyba said:**
> This is a pure guess but I wonder if your script is a victim of the differences between bash and dash. When you run your script from the command line of a bash shell it works. When cron runs it using /bin/sh (which is symlinked to dash) it goes wrong.

Have you tried enforcing the use of bash by putting #!/bin/bash at the top of your script?

yep that was at the top of the script all along.  Is there some sort of timeout value that cron has or something (maybe)?

---

### Post by tuckie on 2007-05-30
UPDATE: I've realized that the script itself isn't finishing.  I was looking at the permissions in my movie folder and I realized that the chown and chmod lines weren't being executed (folder was still owned by root).  Any ideas as to why it would be stopping/erroring with a 108mb iso file?

---

