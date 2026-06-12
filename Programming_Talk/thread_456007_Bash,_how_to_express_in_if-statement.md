---
title: "Bash, how to express in if-statement"
date: 2007-05-27
forum: Programming Talk
---

### Post by JermainWijnhard on 2007-05-27
Hi, want to write a script that sorts my downloads for me. The thing i want to make is:

**If** [some folder contains a file with 'aaa' in it's name]

**then** [COLOR="Red"]mv[/COLOR] /folder/*aaa* /otherfolder/aaa/

**else** [COLOR="Red"]echo[/COLOR] there is no file with 'aaa' in its name

**fi**

But i don't know how to express that 1st part. Can anyone help me?

---

### Post by Stephen Howard on 2007-05-27
maybe something like:
```

if [[ -e $file ]]
then
  echo "I could have added a mv command here if I felt like it"
else
  echo "no file to move"
fi
```

Or another way:

> ls aaa* | xargs -i mv {} /where/i/want/it/to/go

But a neater way would be something like this:

```
find ~/ -name 'aaa*' -exec mv '{}' /where/i/want/it/to/go \;
```

---

### Post by Stephen Howard on 2007-05-27
or even simpler:

```
mv aaa*  /where/I/want/to/move/matching/files
```

---

### Post by Stephen Howard on 2007-05-27
Also, have a browse of the [bash scripting guide]("http://www.tldp.org/LDP/abs/html/index.html")

---

### Post by ruy_lopez on 2007-05-27
```

found = 0
for FOLDER in `ls`
do
     if [ -d $FOLDER ]
     then
             for FILE in `ls $FOLDER`
             do
                   if [ -f $FILE ] & expr "$FILE" : '.*aaa.*' >/dev/null
                   then
                           mv $FOLDER/$FILE /otherfolder/aaa/
                           set found = 1
                   fi
             done
             if [ "0$found" -gt 0 ]
             then
                      set found = 0  # reset for next directory
             else
                      echo "filename with aaa substring not found in $FOLDER"
             fi
     fi
done
```

This kind of thing is better done with perl. It has better substring searching and manipulation.

---

### Post by ghostdog74 on 2007-05-27
> **ruy_lopez said:**
> 
This kind of thing is better done with perl. It has better substring searching and manipulation.

that's an overstatement. with what OP requires, it can done trivially like eg with the find command.

---

### Post by JermainWijnhard on 2007-05-27
So much help so fast, thank you guys!

---

