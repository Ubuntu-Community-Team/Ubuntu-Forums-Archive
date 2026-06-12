---
title: "Bash script help (using mmv?)"
date: 2006-11-14
forum: Programming Talk
---

### Post by bem on 2006-11-14
Hello,

I hope someone can help me with the following.

I would like to write a script to move all files within a multilevel directory structure to a single upper level directory, and if necessary rename them so that any filesnames that would clash do not get overwritten.

I have been playing around for ages using some references from the web and cannot get anything to work. ](*,)  I have been going along the lines of the following:

```
#!/bin/bash

for i in $(~/current/new/*/*/*/*/*);
do
        mmv $i ~/current/#1#2#3#4#5
done
```

Could anyone advise where I am going wrong and point me in the right direction?  I'm sure I have made some glaring errors but do not yet know enough about scripting know where to start correcting it.  I've got to the point now where I'm ready to do it manually but would like to understand where I'm going wrong now that I have started.  In case you could not tell I have not written a script before.

Thanks a lot.

---

### Post by skymt on 2006-11-14
You may want to use the find command (note: code not tested):```
#!/bin/bash

for i in `find .` ; do
    if [ -e ~/current/"`basemane $i`" ] ; then
        n=1
        while [ -e ~/current/"`basename $i`".$n ] ; do
            n=$(( $n + 1 ))
        done
        mv "$i" ~/current/"`basename $i`".$n
    else
        mv "$i" ~/current/"`basename $i`"
    fi
done
```

Let me know if that works, doesn't work, or if you don't know what something in there is.

---

### Post by bem on 2006-11-15
Thank you skymt for the reply, I can't say much of it means anything to me yet but if I get stuck working it out I'll post back.  Cheers!

---

### Post by Arndt on 2006-11-15
> **bem said:**
> Hello,

I hope someone can help me with the following.

I would like to write a script to move all files within a multilevel directory structure to a single upper level directory, and if necessary rename them so that any filesnames that would clash do not get overwritten.

I have been playing around for ages using some references from the web and cannot get anything to work. ](*,)  I have been going along the lines of the following:

```
#!/bin/bash

for i in $(~/current/new/*/*/*/*/*);
do
        mmv $i ~/current/#1#2#3#4#5
done
```

Could anyone advise where I am going wrong and point me in the right direction?  I'm sure I have made some glaring errors but do not yet know enough about scripting know where to start correcting it.  I've got to the point now where I'm ready to do it manually but would like to understand where I'm going wrong now that I have started.  In case you could not tell I have not written a script before.

Thanks a lot.

'mmv' is a good tool, but where you are calling it in the above script, it can't know what to associate the #1-#5 with - the shell has already expanded the wildcards.

This should work:

```
$ mmv '~/current/new/*/*/*/*/*' '~/current/#1#2#3#4#5'

```

---

### Post by bem on 2006-11-15
Thanks Arndt, I think I understand now, mmv had no way of relating the #'s to the *'s the way I had written it.  I've used your suggestion directly at the command line and it did the job in no time at all :).

skymt, I had a play around with your script but it does not seem to work properly for me.  Depending which directory I run it from I get odd things happening.  Like just one level down of subdirectory copied with its contects to ~/current.  Or exisiting upper level files and directories renamed with .1 appended but nothing moved, and alot of "mv: cannot stat `./subdir1/subdir2': No such file or directory" or similar errors.

I've been trying to understand what the script is doing, and it looks to me like the line

```
if [ -e ~/current/"$i" ] ; then
```

will always be true, which is not what is intended, no?  The other problem seems to be that the script cannot differentiate between files and directories.  I've tried to make some alterations but since I don't know what I'm doing it just tends to make it stop doing anything at all :(  .  I would be interested to know how it could be fixed.

Thanks again.

---

### Post by skymt on 2006-11-15
I'm sorry my script didn't work for you. I made one small change (adding a basename substitution to the first if), but it probably still won't work, as it wouldn't solve all the problems you described. I don't really know what's wrong with it at this point, so if you got the job done with mmv, just forget about my suggestion.

---

### Post by bem on 2006-11-15
No problem, I wasn't sure how easy it would be to fix so thought I'd ask anyway.  Thanks for the suggestion though, I think I have learnt a few thing along the way. :)

---

