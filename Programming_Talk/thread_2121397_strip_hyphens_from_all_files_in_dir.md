---
title: "strip hyphens from all files in dir"
date: 2013-03-01
forum: Programming Talk
---

### Post by ZenMasta on 2013-03-01
I have a folder with about 5700 files. The files are all named numerically but there are multiple dashes in each name

ie 978-1-234-5678-9.jpg

I want to completely remove the hyphen from all the file names. 

I tried this but it doesn't appear to do anything.
find media/images/ -type f -exec sed -i 's/-//g' {} \;


Any ideas?

---

### Post by steeldriver on 2013-03-01
'sed' is for editing the contents of the found files - you can either use the 'mv' command within a 'find', or just use the 'rename' command e.g.

```
rename -n -v 's/-//g' *.jpg
978-1-234-5678-9.jpg renamed as 978123456789.jpg
```

(the '-n' means dry run - remove it once you are certain it's matching filenames correctly)

---

### Post by LHammonds on 2013-03-01
Not 100% sure if this would work but try this:

```

for file in *.jpg
do
  echo "${file}" "`echo ${file} | sed 's/-//g'`"
done

```

If that looks correct, change "echo" to "mv" to perform the rename.

LHammonds

---

### Post by steeldriver on 2013-03-01
^^^ if you want to use mv in a loop instead of a one-shot rename, you could use a builtin bash substitution directly instead of sed though:-

 ```

for file in *.jpg
do 
  echo mv "${file}" "**${file//-/}**"
done

```

---

### Post by The Cog on 2013-03-02
> **ZenMasta said:**
> I have a folder with about 5700 files. The files are all named numerically but there are multiple dashes in each name

ie 978-1-234-5678-9.jpg

I want to completely remove the hyphen from all the file names. 

I tried this but it doesn't appear to do anything.
find media/images/ -type f -exec sed -i 's/-//g' {} \;


Any ideas?

**Aargh!!! Noooooo!!!**
That will corrupt all your images! It will remove the any '-' characters from the file **contents**. I hope you have a backup of all these images.

---

