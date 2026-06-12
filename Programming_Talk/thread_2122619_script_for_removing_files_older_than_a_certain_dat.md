---
title: "script for removing files older than a certain date"
date: 2013-03-05
forum: Programming Talk
---

### Post by Zukaro on 2013-03-05
I'm trying to write a script which removes older files from a certain directory.  Basically what I'm trying to do is run a Minecraft server, but previously the backup script I made filled up the HDD completely as there was no way for it to remove older backups on its own.  So what I'm trying to do now is write a script which will take care of that.

The backup script puts a date on the end of the world file (so for example: world_2013-03-05), and I'm trying to remove any file older than the date the script is run (to keep the backups current but to avoid filling the hard drive up).

This is what I've got so far, but I know it wont work.  I don't really know what to do to make it work (the variable "FILE" I didn't know what to add for that so it's currently empty still).

```
REMOVE="$(rm -rf)"
CHECK="$(ls /home/zukaro/Minecraft/Backup)"
FILE="$()"

if $CHECK < $(date +%F)
then
  $REMOVE $CHECK
else
  exit
fi
```

---

### Post by steeldriver on 2013-03-05
Is there any particular reason you can't use the actual file timestamp (mtime?)

If you need to work with the time as indicated by the filename, then how about turning both today's date and the filename date portion into seconds-since-1970-01-01, and then doing a straight integer comparison? i.e. base it on
```

$ filename="world_2013-03-04"
$ echo "${filename#world_}"
2013-03-04
$ date '+%s' --date="${filename#world_}"
1362373200

$ today=$(date '+%F')
$ today_secs=$(date '+%s' --date="$today")
$ echo "$today_secs"
1362459600

```
then you just need to check if 1362373200 is less than 1362459600

---

### Post by sisco311 on 2013-03-05
> **steeldriver said:**
> Is there any particular reason you can't use the actual file timestamp (mtime?)

If you need to work with the time as indicated by the filename, then how about turning both today's date and the filename date portion into seconds-since-1970-01-01, and then doing a straight integer comparison? i.e. base it on
```

$ filename="world_2013-03-04"
$ echo "${filename#world_}"
2013-03-04
$ date '+%s' --date="${filename#world_}"
1362373200

$ today=$(date '+%F')
$ today_secs=$(date '+%s' --date="$today")
$ echo "$today_secs"
1362459600

```
then you just need to check if 1362373200 is less than 1362459600

There is no need to convert the date to the seconds since epoch format. You can do a straight integer comparison on the YYYYMMDD format. Or in bash, you can use the < and > operators with [[ to sort lexicographically:
```

today=world_$(date '+%F')

cd path/to/files || exit 1

shopt -s nullglob
for file in *
do
    if [[ $file < $today ]]
    then
        printf '%s\n' "old file: $file"
    fi
done

```

@OP:
The real issue here is the backup script which creates unnecessary backups. You should focus on fixing that. ;)

---

### Post by Vaphell on 2013-03-05
how about using *find* with *-mtime* or *! -newer* combined with *-delete*?

---

### Post by Zukaro on 2013-03-07
I'm not really sure how I'd fix that backup script.  :P
The reason I'm putting a date in the name is so I can see which backups were made when, as well I don't want the backup to overwrite older backups until they've reached a certain age (at least a week, if not more).

Anyways; I'm going to do a bit of research on some of the commands you guys have mentioned so I can see which one would be the easiest and best for me to use.  :P  I'll get back to you once I either figure it out or get stuck again.  Thanks. :)
(also gotta do a bit of playing around with some of these commands and methods to see if they'll do exactly what I want them to do)

---

### Post by jamesbon on 2013-03-07
I am not sure as how to write exact syntax for the same 
but find combined with xargs should do the job

---

### Post by crtlbreak on 2013-08-11
I have the following (built on the knowledge of others and [Vaphell]("http://ubuntuforums.org/member.php?u=347382") above

sudo find /path/to/folder* -mtime +7 -exec rm -rf {} \;

It works as a cronjob daily to purge files older than 7 days

---

