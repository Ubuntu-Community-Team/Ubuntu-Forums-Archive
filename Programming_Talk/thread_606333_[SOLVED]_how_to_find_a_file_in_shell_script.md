---
title: "[SOLVED] how to find a file in shell script"
date: 2007-11-07
forum: Programming Talk
---

### Post by mdpalow on 2007-11-07
.

---

### Post by kast on 2007-11-07
```
if [ -f /home/$USER/*/grep-warn ]  # that's just a file on my desktop
then 
         echo "found it"
else 
         echo "cant find it"
fi

```

That works for me, and if I put a fake file in it will echo the "cant find"

---

### Post by mdpalow on 2007-11-08
.

---

### Post by mdpalow on 2007-11-08
.

---

### Post by yabbadabbadont on 2007-11-08
```
man find
```
:D

There is a bash wildcard technique using {,/OptionalDirName} but I've never messed with it myself.  You should be able to use the return code from the find command with multiple search paths to do what you need.

---

### Post by mdpalow on 2007-11-08
thanks...

I need to find the file using ' if ' because there is a condition I want to add IF it's found.

---

### Post by ghostdog74 on 2007-11-08
not really sure what you want, however, if you want to find a specific file, 
```

# find /home/$USER -user $USER -type f -name "specific_file.txt"

```
depend on whether you want to check ownership, you can remove the -user flag

---

### Post by yabbadabbadont on 2007-11-08
```
/home/daffy $ l temp/
total 4
-rw-r--r-- 1 daffy users 1190 2007-11-02 02:09 stuff.txt
/home/daffy $ MYFILELIST=$(find . -name stuff.txt 2>/dev/null)
/home/daffy $ echo $MYFILELIST
./temp/stuff.txt
/home/daffy $ MYFILELIST=$(find . -name stuff.notfound 2>/dev/null)
/home/daffy $ echo $MYFILELIST

/home/daffy $ if [ -z "$MYFILELIST" ]
> then
> echo "not found"
> else
> echo "found"
> fi
not found
/home/daffy $ MYFILELIST=$(find . -name stuff.txt 2>/dev/null)
/home/daffy $ echo $MYFILELIST
./temp/stuff.txt
/home/daffy $ if [ -z "$MYFILELIST" ]; then echo "not found"; else echo "found"; fi
found

```
The rest is left as an exercise for the student.  :D

---

### Post by mdpalow on 2007-11-08
thanks very much to all... I got it..

---

### Post by synss on 2007-11-08
> **mdpalow said:**
> thanks...

I need to find the file using ' if ' because there is a condition I want to add IF it's found.

I know it says solved but...

If you want to do something on the file that "find" found (example with echo, but can be replaced by any command)

```
find . -name "filename" -exec echo '{}' " found" \;
```

what is between **-exec** and **\;** will be run; the **'{}'** will be replaced by whatever has been found.

Please, have a look at
```
man find
```

---

