---
title: "[SOLVED] calculating /home direcotry size in bytes"
date: 2008-12-19
forum: Programming Talk
---

### Post by pytheas22 on 2008-12-19
I'm trying to write a bash command to find the total size of all files in my /home directory (including subdirectories) added together.  This is what I've come up with:
```

sudo ls -lR /home | cut -d ' ' -f 5 | grep '[0-9].*' | grep -v '/' | awk '{ total += $1 } END { print total }'
```

The idea of this command is basically to go through /home recursively and use 'ls -l' to get the size in bytes for each file, then add it all together.

The problem is that this command is giving me a total of 3230653519 for the number of bytes in /home, or a little over 3 gigabytes.  However, according to 'df -h', /home (which is on its own partition) has 8.2 gigabytes being used.  I know there's some file-system overhead and other stuff that my calculation would overlook because 'ls -l' wouldn't see it, but I'm obviously missing much more than that if I have 5+ gigabytes unaccounted for.

So I'm trying to figure out what I'm missing in my approach.  Any pointers would be very welcome.

---

### Post by aquavitae on 2008-12-19
Have a look at the 'du' command - I think that is what you're looking for. It shows the space being used by a directory, recursively as required.  To get a listing of the total size of the home folder and its subdirectories use ```
du -csh /home/*
```
If you've got more than one user you might need sudo, but otherwise you shouldn't.

Hope this helps, even if it doesn't actually answer your question!

EDIT: A possible reason for the discrepancy in sizes; ls -l ignores hidden files (to include them use ls -la), including the trash and email folders. Maybe you've got a lot of deleted stuff in your trash which it isn't counting? There are a lot of other hidden folders too, but I think they are generally quite small.

---

### Post by pytheas22 on 2008-12-19
aquavitae: thanks for that.  Good point about missing hidden files--using ls with the -a argument turns up about 0.5 gigabytes of additional files.  However, 'du -csh /home/*' gives the same number as 'df -h'--8.2 gigabytes--for the total size of all files in /home.  So something's still missing somewhere.

I'm trying to do this because I have a web server with hundreds of users, and /home is rapidly running out of space for reasons that are unclear.  I'm concerned that someone may be doing something nasty, so I want to make sure that no one's hiding files from me that shouldn't be on the server.  The machine was basically left without an administrator for several months, logs for that period are inconsistent or non-existent and some other weird things have been happening since I started trying to take care of it.  So I'm worried about compromises, etc., and am open to more general ideas of how to figure out what's going on here.  Unfortunately, the system runs an old version of Red Hat that doesn't even have yum installed, so installing software (like root-kit scanners) is tricky.

---

### Post by mssever on 2008-12-19
I love baobab for these kinds of tasks. Of course, if your machine is old enough, you might not have it and may need to install it...

(The reason I'm on Ubuntu now is because I got sick of being unable to update my older Red Hat install. I haven't missed RH.)

---

### Post by aquavitae on 2008-12-19
du only shows the size of files (and folder overhead, but that's really small), so I'd trust it. You can change the arguments to give more detailed results, or maybe sort them by size. It sounds like you're really just trying a bit of detective work though, so scanning directory sizes might not be enough on its own. Is there something specific you're looking for? I can't think offhand of a way to efficiently hide files from the root user. The -chs anything obviously wrong in that output, i.e. one user using 5Gb or something?

---

### Post by unutbu on 2008-12-19
Go to a subdirectory so the output is not huge. 
Make sure there are files of different sizes (the number of digits in the size matter because of extra spaces).

Run 
```

ls -lR DIR
```

and

```

ls -lR DIR | cut -d ' ' -f 5
```

You should see a lot of lines that are blank. For example,
```

% ls -laR test

-rw-r--r--  1 user user  1007 2008-12-17 16:59 httpd.conf
-rw-r--r--  1 user user   974 2008-12-17 16:58 httpd.conf~
-rw-r--r--  1 user user  3534 2008-12-03 21:36 .massmove
-rw-r--r--  1 user user     0 2008-12-18 20:04 mnt
-rw-r--r--  1 user user 51208 2008-12-17 02:38 Release
-rw-r--r--  1 user user  9707 2008-12-19 08:09 rss.xml
-rw-r--r--  1 user user  9707 2008-12-19 08:09 rss.xml.1
-rw-r--r--  1 user user  9707 2008-12-19 08:09 rss.xml.2
-rw-r--r--  1 user user  9707 2008-12-19 08:09 rss.xml.3
-rw-r--r--  1 user user 28939 2008-12-16 14:52 yahoo

% ls -lR test | cut -d' ' -f 5
/data1/user/test:














51208




28939

```
I don't know exactly what's wrong with cut, but this should work better:

To print the size in bytes:```

sudo find /home -printf "%s\n" | awk '{sum+=$1} END {printf "%d\n", sum}'

```
To print the size in KiB (1K-blocks consumed):```

sudo find /home -printf "%k\n" | awk '{t+=$1} END {printf "%dKiB\n", t}'
```
(Note that a 1 byte file may consume 4 1K-blocks on a typical ext3 filesystem. du and df report 1K-blocks (KiB) consumed.)

---

### Post by mssever on 2008-12-19
Remember, too, that if you're using wildcards, [FONT=Courier New][COLOR=Green]*[/COLOR][/FONT] won't get dotfiles. You have to do [FONT=Courier New][COLOR=Green]* .*[/COLOR][/FONT] (note the space) to get everything.

---

### Post by stroyan on 2008-12-19
As unutbu noted, cut is not doing what you want.
It considers repeated spaces as delimiters between multiple (empty) fields.
The size field is often padded by multiple leading spaces.
So all files of less than 10000 bytes are not having their sizes counted.

---

### Post by pytheas22 on 2008-12-19
unutbu: thanks a lot, that did it!  And it makes a lot of sense...I guess I should have thought harder about how cut delimiters work.

The command you gave gives numbers that add up much better, although there's still a discrepancy of about ~1.5 gigabytes between the output of your command and the number given by 'df'.  This is strange because when I run the same commands on my Ubuntu desktop, I get numbers that match almost exactly.  But at least now I can see if the mystery space continues to grow while the files that I can account for stay the same...at least that way I'll know if things get worse.

Thanks to all for the responses.

---

