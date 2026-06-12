---
title: "Batch replace strings in all files in a folder--when there are UNIX-style slashes"
date: 2010-12-12
forum: Programming Talk
---

### Post by tarahmarie on 2010-12-12
So I have a directory full of m3u files (playlists, which are essentially XML files). I moved my main directory full of music, and now need to replace all the paths in all those files.  I need to change

/home/tarahmarie/Music/ 

to

/data/Music/

The problem is that I'm not sure how to go about it, since there are slashes in that string, and the only way I've seen to do this via CL with perl is

```

find /path/to/start/from/ -type f | xargs perl -pi -e 's/applicationX/applicationY/g'

```

The problem is that I'd be doing this:

```

find /path/to/start/from/ -type f | xargs perl -pi -e 's/home/tarahmarie/data/g'

```

And I don't think that works, since I've got that extra slash in the string.

How might I modify this to work?

---

### Post by t4thfavor on 2010-12-12
lookup the syntax for sed and or awk, it should be very simple to setup a one liner to make this task happen.

---

### Post by tarahmarie on 2010-12-12
Right, but I'm trying to modify that perl script, since sed and awk are bloody complicated.

---

### Post by StephenDavison on 2010-12-12
Escape the directory separator with a back slash. 

's/home\/tarahmarie/data/g'

Try that.

Edited to add:
Like t4thfavor, my first thought was to use sed (stream editor) to do this.  It has the -i option to do in-place editing.  For this purpose, sed is no more complicated than using perl.  Here's something to get you started with sed.  This should be what comes after xargs.

```
sed -i 's/home\/tarahmarie/data/g'
```

2nd edit:
I tested the above command and it works with a file argument -- should also work fine with xargs.

---

### Post by t4thfavor on 2010-12-12
Definately intimidating until you start to understand them. Then it's just plain scary because you begin to understand them...

```

sed 's/\\home\\oldpath\\/\\home\\newPath\\/g' test.txt>> test2.txt

```

---

### Post by Arndt on 2010-12-13
> **t4thfavor said:**
> Definately intimidating until you start to understand them. Then it's just plain scary because you begin to understand them...

```

sed 's/\\home\\oldpath\\/\\home\\newPath\\/g' test.txt>> test2.txt

```

All of these support using a different separator than slash. Just use any one you want, like s#applicationX#applicationY#g

---

### Post by tarahmarie on 2010-12-13
> **Arndt said:**
> All of these support using a different separator than slash. Just use any one you want, like s#applicationX#applicationY#g

Can I specify that I want them written back to the same filename?

---

### Post by ziekfiguur on 2010-12-13
> **tarahmarie said:**
> Can I specify that I want them written back to the same filename?

If you use sed, the -i parameter makes it work in-place, so the changes will be made in the file instead of printed to the terminal.

---

### Post by StephenDavison on 2010-12-13
Have you read all the replies?  I posted that 16 hours ago.

---

### Post by tarahmarie on 2011-01-05
Here's my output when I try that:

```

/data/Music/testplay Hello! $sed -i 's/\\home/tarahmarie/Music\\/\\data/Music\\/g'
sed: -e expression #1, char 22: unknown option to `s'


```

---

### Post by Vox754 on 2011-01-05
> **tarahmarie said:**
> Here's my output when I try that:

```

/data/Music/testplay Hello! $sed -i 's/\\home/tarahmarie/Music\\/\\data/Music\\/g'
sed: -e expression #1, char 22: unknown option to `s'


```

Lol, what the heck are you doing?!

The answer has been given already (post #4).
```

sed -i 's/home\/tarahmarie/data/g' file.m3u

sed -i 's|home/tarahmarie|data|g' file.m3u

```

Think about it:
```

sed        # program
-i         # edit the same file
'     '    # single quotes prevent expansions by the shell
s          # replace

/old/new/
|old|new|  # the separators can be any character
+old+new+  # since the old string already contains a slash (/),
?old?new?  # use a different character
.old.new.  # etc.

g          # multiple replaces
file.m3u   # name of the file to operate on

```

---

### Post by tarahmarie on 2011-01-05
The problem was that I didn't understand that I was acting on files; my buddy offline actually gave me the correct answer, which was to append an asterix on the end so all file types were altered. I had m3u and xml playlists in the same directory.

I ended up using % as a delimiter; it jumps out at the eye a little more.

Thanks, all!

---

### Post by soltanis on 2011-01-05
So in other words you did this (in the appropriate directory)?

```

sed -i 's%home/tarahmarie%data%g' *

```

---

### Post by tarahmarie on 2011-01-06
> **soltanis said:**
> So in other words you did this (in the appropriate directory)?

```

sed -i 's%home/tarahmarie%data%g' *

```

Yep, though I added the Music subfolder as well to make sure all the correct strings were replaced.

---

