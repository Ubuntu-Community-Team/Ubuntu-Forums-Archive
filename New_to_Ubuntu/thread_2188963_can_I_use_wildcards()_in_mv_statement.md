---
title: "can I use wildcards(?) in mv statement"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by squakie on 2013-11-20
I have a Raspberry Pi running OpenELEC that I can ssh to to do the work I need to do there from the command line.

Currently there is a folder there calle xbmc-shares, and within that are 3 subfolders:  PICTURES, MUSIC and VIDEOS.

In the process of scp'ing some files to the Pi, I accidently changed to suffice from ".mk4" to ".mpg".  The entire file is there, and if I rename one of them to have a ".mk4" suffix, it plays fine in xbmc.

So, since I have more than 1 of those mistakes, and they are in various subfolders within /xbmc-shares/VIDEOS, can I do anything like the following and have it work?

mv /storage/xbmc-shares/VIDEOS/*/*.mpg *.mk4

amd of so, will the resulting file still be in it's folder or will it be moved to the folder I'm in when I issue the command?

I need the output flle to be back in the same folder it was in.

---

### Post by Lars Noodén on 2013-11-20
You can use [globbing](http://manpages.ubuntu.com/manpages/trusty/en/man7/glob.7.html) with most system utilities, mv included.  

However, if you are doing a bulk rename, I would use the utility [rename](http://linux.die.net/man/1/rename), with the dry-run (-n) option instead.  Then once the output looks reasonable, remove the dry-run option and let it rename the files.  It uses Perl regular expressions to do the renaming.  

```

rename -n 's#\.mk4$#.mpg#' *.mk4

```

If you write the substitution(s) correctly, you can even use it to change folders.

---

### Post by squakie on 2013-11-20
Thanks Lars - I set up a test folder with a single .mpg file in it, as well as 2 subfolders containing .mpg files and other files.  I then tried:

rename 's/\.mpg/\.mk4/' *.mpg

And that works at the single directory level.  How do I make this walk the directory structure starting at the current directory and going through all subfolders (and some of thos subfolders have multiple layers of subfolders) ?

---

### Post by Lars Noodén on 2013-11-20
There might be a way with rename, but I can only think of a way with [find](http://manpages.ubuntu.com/manpages/saucy/en/man1/find.1.html).

```

find . -name '*.mpg' -execdir rename -n 's/\.mpg$/.mk4/' {} \;

```

-execdir makes rename run in the directory in which the file was found.

Unfortunately, that does not have a dry-run mode nor an undo option.  Backup with tar or something first.

---

### Post by squakie on 2013-11-20
Thanks Lars -  I need to do some backups before I proceed - last time I attempted something like that I mis-typed the first time and wiped everything out (on a 2tb drive for my media center!), so lesson learned and thank you for reminding me.

Not sure yet when I'll get to try that, but I'll let you know.

---

### Post by Lars Noodén on 2013-11-20
Also, if you have spaces in any of the file names, the {} should be quoted "{}"

---

