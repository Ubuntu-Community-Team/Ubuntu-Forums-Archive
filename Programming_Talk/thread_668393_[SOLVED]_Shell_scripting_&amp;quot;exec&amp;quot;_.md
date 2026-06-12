---
title: "[SOLVED] Shell scripting &amp;quot;exec&amp;quot; question"
date: 2008-01-15
forum: Programming Talk
---

### Post by dwasifar on 2008-01-15
First off, the standard disclaimer: I am pretty new at shell scripting, and my work at this point is mainly hacked-together ideas and pieces from other people's.  Thank you in advance for your tolerance.  :)

I wrote a shell script that processes a file line by line to obtain path and file information.  (Amarok .m3u playlist files, if that matters.)  I use this structure to read the file in:
```

exec<"playlist.m3u"
while read line
do a=$(($a+1));
(various processing commands go here)
done

```

Generally this works pretty well.  Each line of the file winds up in the $line variable, and I can then work with it.  The only weird and unexpected thing is that it collapses multiple spaces within the string.  Since the strings contain file paths, this is a problem.  So, for example, I might have this string in the file:

/remote/mp3/Eno, Brian/1[COLOR="White"]__[/COLOR]1.mp3

(This filename would result from Grip ripping a track titled "1 / 1" and stripping the forward slash).

During script execution, $line would wind up containing this:

/remote/mp3/Eno, Brian/1[COLOR="White"]_[/COLOR]1.mp3

Note that the double space has been condensed to a single space.  Consequently nothing else I do with that string works, because it is no longer a correct path.

Why does this happen?  Is there anything I can do about it?  Is there a better way to process a file line by line in a script?  Will our heroes escape from the tiger?

---

### Post by dwasifar on 2008-01-15
I got my answer in another forum on daniweb.  I needed to quote my  variable -  "$line" and not $line - within my processing.

Thanks to everyone who offered help.

---

