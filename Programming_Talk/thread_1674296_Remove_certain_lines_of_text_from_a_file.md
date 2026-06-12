---
title: "Remove certain lines of text from a file"
date: 2011-01-23
forum: Programming Talk
---

### Post by bcooperizcool on 2011-01-23
How can I remove certain lines of text from a text file?  Eg.
File a sample
```

/home/ubuntu/App.app/icon.png
/home/ubuntu/App.app/title.png
/home/ubuntu/App.app

```

How can I remove all the lines that contain .png and leave the others?   Code examples would be good, as that is easier for me! :)

Thanks!

---

### Post by cipherboy_loc on 2011-01-23
Something like (not tested):

```

sed 's/^.*\.png$//g' ./file.txt

```

If that works then run it with the -i option:

```

sed 's/^.*\.png$//g' ./file.txt -i

```
Cipherboy

---

### Post by bcooperizcool on 2011-01-23
Thanks!  I'll try that in a minuet!

---

### Post by geirha on 2011-01-23
```

ed -s file.txt <<< $'g/\.png$/d\nw'
# or
printf '%s\n' 'g/\.png$/d' w | ed -s file.txt

```

[http://bash-hackers.org/wiki/doku.php?id=howto:edit-ed](http://bash-hackers.org/wiki/doku.php?id=howto:edit-ed)

---

### Post by worksofcraft on 2011-01-23
> **bcooperizcool said:**
> How can I remove certain lines of text from a text file?  Eg.
File a sample
```

/home/ubuntu/App.app/icon.png
/home/ubuntu/App.app/title.png
/home/ubuntu/App.app

```

How can I remove all the lines that contain .png and leave the others?   Code examples would be good, as that is easier for me! :)

Thanks!

you can use grep here also.
The -v switch lists all the lines that DON'T match the expression... so
```

grep -v "\.png" file.txt

```
 should do it :)

---

### Post by ghostdog74 on 2011-01-23
> **bcooperizcool said:**
> How can I remove certain lines of text from a text file?  Eg.
File a sample
```

/home/ubuntu/App.app/icon.png
/home/ubuntu/App.app/title.png
/home/ubuntu/App.app

```

How can I remove all the lines that contain .png and leave the others?   Code examples would be good, as that is easier for me! :)

Thanks!

there are 2 notions to "removing lines". One is actual removal from the file itself. Another is just not printing them out (and redirecting those printed to another file)

awk (not printing them out)
```

awk '!/\.png$/' file > t && mv t file

```

sed (direct deletion method)
```

sed -i.bak 's/.*\.png$//' file

```

sed ( not print them)
```

 sed -i.bak -n '/\.png$/!p' file

```


ruby
```

ruby -i.bak -ne 'print if not /\.png$/' file


```
and there are others like grep , etc

---

### Post by slavik on 2011-01-24
> **cipherboy_loc said:**
> Something like (not tested):

```

sed 's/^.*\.png$//g' ./file.txt

```

If that works then run it with the -i option:

```

sed 's/^.*\.png$//g' ./file.txt -i

```
Cipherboy
there is also:
```

sed '/$PATTERN/d' file

```

That will remove the line completely instead of just removing the chars.

---

### Post by ghostdog74 on 2011-01-24
> **slavik said:**
> 
That will remove the line completely instead of just removing the chars.
no, that will not.

---

### Post by theDaveTheRave on 2011-01-24
personally I like the idea of printing it out first...

so the grep (as suggested by worksofcraft) - my preference
or the awk (ghostdog74) method.

then once you get the result you want you can just redirect the output to another file.

eg
```

grep -v "\.png" file.txt > file_no_png.txt

```

should do the trick (but not tested!)

D

---

### Post by Rany Albeg on 2011-01-24
I'd go with geirha's

---

