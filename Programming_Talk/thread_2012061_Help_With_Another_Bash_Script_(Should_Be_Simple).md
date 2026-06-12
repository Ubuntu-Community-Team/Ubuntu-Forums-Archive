---
title: "Help With Another Bash Script (Should Be Simple)"
date: 2012-06-28
forum: Programming Talk
---

### Post by jlacroix on 2012-06-28
Hello again everyone. I'm needing assistance with another bash script. This time it's much easier than the one I was dealing with yesterday.

I originally written the script in a DOS Batch file, but I'd rather do this in Linux rather than Windows:
```
copy /b *.xml newfile.xml
```
All that command is doing is combining all XML files in a directory into a single XML file called "newfile.xml". It retains the alphabetical order (meaning the first XML file in alphabetical order in a directory listing is the first file copied into newfile.xml).

Basically I need to know how to do the same as my batch file in Linux. I tried to do "more *.xml" in the directory, but it shows file names inside the output. I also tried "cat *.xml > newfile.xml" but the output file doesn't have the contents in the right order.

---

### Post by The Cog on 2012-06-28
I think this will probalby do it:
```
cat *.xml > newfile.xml
```

---

### Post by Vaphell on 2012-06-28
how about
```
while read -r -d $'\0' file
do
  cat "$file"
done < <( find -type f -iname '*.xml' -print0 | sort -z ) > newfile.xml
```

---

### Post by jlacroix on 2012-06-28
> **The Cog said:**
> I think this will probalby do it:
```
cat *.xml > newfile.xml
```
As I mentioned, I tried that already, the output ends up being in the wrong order.

> **Vaphell said:**
> how about
```
while read -r -d $'\0' file
do
  cat "$file"
done < <( find -type f -iname '*.xml' -print0 | sort -z ) > newfile.xml
```
Same as above, it's not putting the files into the output file in the right order.

---

### Post by steeldriver on 2012-06-28
can you describe what's wrong about the order exactly (lower versus upper case? numeric versus alphanumeric?)

the behavior of 'cat' may be something to do with LC_COLLATE - not sure if that affects 'sort' as well

---

### Post by |{urse on 2012-06-28
> cat $(ls -t) > newfile.xml

That will concatenate the files by creation date, is that what you need?

---

### Post by jlacroix on 2012-06-28
> **steeldriver said:**
> can you describe what's wrong about the order exactly (lower versus upper case? numeric versus alphanumeric?)

the behavior of 'cat' may be something to do with LC_COLLATE - not sure if that affects 'sort' as well

> **|{urse said:**
> That will concatenate the files by creation date, is that what you need?

I can answer both with this. Say for example I have a directory with XML files in it. If I do an 'ls' I get this output:

A.xml
B.xml
C.xml
D.xml
E.xml

In that example, I want the newfile.xml to contain the contents of A.xml, B.xml, C.xml, D.xml and then E.xml in that order (alphabetical). However, that is not the case. The header information for example is in A.xml, but it is closer to being in the middle of the newfile.xml.

---

### Post by |{urse on 2012-06-28
Thats what we were asking, alphabetical or by timestamp..

> find . -name "*.xml" -maxdepth 0 -print0 | sort -z | xargs -0 cat > newfile.xml

Try that from your working directory.

---

### Post by jlacroix on 2012-06-28
> **|{urse said:**
> Thats what we were asking, alphabetical or by timestamp..



Try that from your working directory.

```
find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.
```

And after that, the newfile.xml is empty.

Thanks!

---

### Post by |{urse on 2012-06-28
actually just remove the -maxdepth 0.

---

### Post by jlacroix on 2012-06-28
> **|{urse said:**
> actually just remove the -maxdepth 0.
I had to change the output file name to "newfile.txt" to prevent it from processing itself. But, it's still the same problem, the files that are put into the newfile.txt are in the wrong (non-alphabetical) order. :(

---

### Post by Vaphell on 2012-06-28
```
find . -iname "*.xml" -print0 | sort -z
```
is the order returned by this line right?

---

### Post by ofnuts on 2012-06-28
> **jlacroix said:**
> I had to change the output file name to "newfile.txt" to prevent it from processing itself. But, it's still the same problem, the files that are put into the newfile.txt are in the wrong (non-alphabetical) order. :(

What do you call "non-alphabetical"? If this is because upper- and lowercase characters aren't sorted together then use "sort -zf" instead of "sort -z". But this is Unix territory, case in filenames is meaningful and you may have to change you design a bit in the long run.

---

### Post by jlacroix on 2012-06-28
I am sooooooooooo sorry guys. This was blowing my mind, because I always thought cat copied files in alphabetical order by default, and I had no clue why it wouldn't. The XML files were somehow damaged. I'm not sure what happened to them to garble the information in the wrong order, but I got fresh copies of them and the "cat *.xml > newfile.xml" works as expected.

Sorry!!!!!!

---

### Post by |{urse on 2012-06-28
Okay, I was completely confused, I KNOW that works normally! lol! Be sure to mark this sucker solved. ):P

---

