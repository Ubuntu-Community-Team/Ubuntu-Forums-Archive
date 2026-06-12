---
title: "confused about regex, need some help"
date: 2008-05-31
forum: Programming Talk
---

### Post by b4t3m4n on 2008-05-31
Hey guys, the thing I always find myself needing from a REGEX is pulling data from a form like

Artist: Some Artist
Album: Some Album
Song: Some song

I want a regex that will run through a file containing entries like this and spit out all the Artists in the file for example.  Every time I try to make my own, it works, but it also prints out the Artist: tag along with the actual artist's name which is no use too me.  I just want the actual name of the artist, not the "Artist:" tag along with it.  I am using grep for this, or maybe there is a better way, I dunno.  This seems like it should be really simple, I am just really bad with regex.

Thanks for any help

---

### Post by HalPomeranz on 2008-05-31
The easiest thing for you to do is to just pipe the output of your grep command through sed:

```

grep ... | sed -r 's/^[^:]+:\s+//'

```

On each line of output, the above sed expression will remove everything up to and including the first colon plus any whitespace after the colon.  So a line like "Artist: some string" should get converted to just "some string".

---

### Post by ghostdog74 on 2008-05-31
since you data file is structured, meaning there are at least recognisable delimiters and standard format, using awk or equivalent that works well with fields is more appropriate tool then grep or sed
```


awk -F":" '/Artist/{print $2}' file

```

---

### Post by HalPomeranz on 2008-05-31
The problem with your awk expression is that it's going to leave leading whitespace at the beginning of each line, i.e., "Artist: some string" is going to be converted to "<whitespace>some string".  I was going to suggest using awk myself, but couldn't come up with a reasonable awk expression that would remove the header+whitespace from each line (I could do it with a Perl one-liner, but it would be messy to type).  sed was easier.

---

### Post by ghostdog74 on 2008-05-31
that's just trivial
```

 awk -F": " '/Artist/{print $2}' file

```

---

### Post by WW on 2008-05-31
Or even...
```

awk -F":[ \t]*" '/Artist/{print $2}' file

```

However, using the field separator this way will cause a problem if there is a colon in the data string.

---

### Post by b4t3m4n on 2008-05-31
thanks for all the posts guys, I will try some of this and see what I can get to work for me

---

### Post by HalPomeranz on 2008-05-31
Hmmm, I realized there's another issue with the awk solution.  What if there are colons later in the line?  For example a line like "Album: Journey: Greatest Hits".  The awk is just going to spit out $2 or "Journey" in this case, which is probably not what you want.

---

### Post by ghostdog74 on 2008-05-31
> **HalPomeranz said:**
> Hmmm, I realized there's another issue with the awk solution.  What if there are colons later in the line?  For example a line like "Album: Journey: Greatest Hits".  The awk is just going to spit out $2 or "Journey" in this case, which is probably not what you want.

you are getting way ahead. The awk solution is based on what sample data OP has given. It seemed structured to have only 1 colon. If its what you described, then it also trivial to modify to suit OP's need
```

awk -F"[ \t]*:[ \t]*" '/Artist/{$1="";sub(/^ +/,"");print}' file

```

---

### Post by WW on 2008-05-31
Instead of using the colon as the field separator in the awk command, you could process the line with the **sub** function before printing it:
```

awk "/^Artist: */ {sub(\"^Artist: *\",\"\"); print}" file

```
More generally,
```

export FIELD=Song
awk "/^${FIELD}: */ {sub(\"^${FIELD}: *\",\"\"); print}" file

```
(I assume that only spaces occur between the first colon and the start of the name.  Change **: *** to **:[ \t]*** if tabs can also occur.)

For example:
```

$ cat file
Artist:   Some Artist
Album:  Some Album
Song:   Some song
Artist: A. Artist
Album:  Awkward Arguments
Song:   Portrait of the Artist: My Story
$ export FIELD=Artist 
$ awk "/^${FIELD}: */ {sub(\"^${FIELD}: *\",\"\"); print}" file   
Some Artist
A. Artist
$ export FIELD=Song  
$ awk "/^${FIELD}: */ {sub(\"^${FIELD}: *\",\"\"); print}" file
Some song
Portrait of the Artist: My Story
$ 

```


EDIT: Or you could use sub like ghostdog74 did. :)

---

### Post by WW on 2008-05-31
If awk makes you feel awkward, you could use perl:
```

perl -n -e 'if (/^Artist: *(.*)/) {print "$1\n"}' file

```
For example,
```

$ cat file
Artist:   Some Artist
Album:  Some Album
Song:   Some song
Artist: A. Artist
Album:  Awkward Arguments
Song:   Portrait of the Artist: My Story
$ perl -n -e 'if (/^Artist: *(.*)/) {print "$1\n"}' file
Some Artist
A. Artist
$ perl -n -e 'if (/^Song: *(.*)/) {print "$1\n"}' file
Some song
Portrait of the Artist: My Story
$ 

```

---

