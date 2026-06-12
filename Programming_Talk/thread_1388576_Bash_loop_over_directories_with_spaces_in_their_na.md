---
title: "Bash: loop over directories with spaces in their names"
date: 2010-01-23
forum: Programming Talk
---

### Post by nmccrina on 2010-01-23
Okay, so I installed Debian, but when I moved my music collection back onto my computer from the external hard drive, somehow the permissions got all messed up. So I want to make a script that changes all the directories back to 755 and the flac files to whatever the hell is right for them.
The problem is, all the directories (well, most) and files have spaces in their names. For example, "Kate Bush/The Dreaming/1 - Sat in Your Lap.flac". So I can't get my Bash loop to work right. I was hoping to do something like

> 
for ARTIST in `ls -d *`
do
    chmod -v 755 $ARTIST
    for ALBUM in `ls -d *`
    do
        chmod -v 755 $ALBUM
        for TRACK in `ls *`
        do
            chmod -v 644 $TRACK
        done
    done
done


Unfortunately, ls ends up going nuts with the spaces present. ](*,) What's the best way to make this work with the spaces?

---

### Post by Hetor on 2010-01-23
chmod -R <permissions> /directory

---

### Post by daasdingo on 2010-01-23
I wouldn't do this with this loop,
you can simply use

```

find -type d

```

to get all the directories, and
```

find -type f

```
to get all the files;)

---

### Post by nmccrina on 2010-01-23
Thanks, guys! I have to run out now, but I'll try it when I get back! :popcorn:

---

### Post by sisco311 on 2010-01-23
```
find /path/to/dir -type f -exec chmod 0644 '{}' \;
find /path/to/dir -type d -exec chmod 0755 '{}' \;
```

---

### Post by JSeymour on 2010-01-23
In addition to sisco311's suggestion:
```

find /path/to/dir -type d -print |xargs -i chmod 755 {}
find /path/to/dir -type f -print |xargs -i chmod 644 {}

```The difference between sisco311's examples and those above is that, in sisco311's, *chmod* will be exec'd for each item found, whereas the *xargs* version can *chmod* several at a time.  Of course: If it's just a small collection, rather than thousands-upon-thousands of files and directories, it doesn't really matter.

Sometimes even the above can be defeated if the path- or filenames contain special characters, in which case more extreme measures must be taken, such as:
```

find /path/to/dir -type d -print |while read path; do path=`echo $path |sed 'editing commands go here'`; chmod 755 "$path"; done

```I've had to do the above in Samba shares where end-users have included no end of shell meta-chars in their file and directory names.  Sometimes it's been quite a challenge.

N.B.: In the above example, it's **exceedingly** wise to first run the above with an *echo* in front of the *chmod* command, to see what the command will actually do, before actually running the real thing.  Once-or-twice, thru hubris, I've failed to do that and gotten burned.  Haven't had to resort to restoring from backups, or trashed a system, *yet*, but the results were Not As Planned ;).

Jim

---

### Post by denarced on 2010-01-23
Actually if theres a lot of files and you wanna execute just one command, find can do that too
```

find /path/to/dir -type f -exec chmod 0644 '{}' \+
find /path/to/dir -type d -exec chmod 0755 '{}' \+

```

only difference to sisco311's suggestion is the end of the command: \+ instead of \; and it makes one big command. You should try something like echo first in huge commands like this one to make sure it really works like the way you want it to.

---

### Post by nmccrina on 2010-01-23
Cool beans! :)

I changed *everything* to 0755 with "chmod -R 755 *" (Hetor's suggestion), then just the files to 0644 with "find ./ -type f -exec chmod -v 0644 '{}' \;" (sisco311's suggestion).

It worked, and was a lot easier than going into each directory individually. :P Thanks again!

---

