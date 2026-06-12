---
title: "how to remove files older than some date"
date: 2011-04-24
forum: Programming Talk
---

### Post by Mia_tech on 2011-04-24
I'm creating a backup shell script, and it will remove backups older than a certain date

ls -lh | awk '{print $6 " " $8}' | sed -n '2011-04-10/p'

but 'sed' command is not quiet yet output what I want

any help appreciated

---

### Post by apollothethird on 2011-04-24
> **Mia_tech said:**
> I'm creating a backup shell script, and it will remove backups older than a certain date

ls -lh | awk '{print $6 " " $8}' | sed -n '2011-04-10/p'

but 'sed' command is not quiet yet output what I want

any help appreciated

Create a file with a name such as "datestamp" with the time of the cutoff date.

```
touch -t 201104010000 datestamp
```

Then use the find command:

```
find ! -newer datestamp -type f
```

The "datestamp" file is touched with the cutoff date.  The "201104010000" string is March 1, midnight 2011.

The "! -newer" will show files not newer (in other words older) than the file you created.  The "-type f" option is telling find to show only files.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by kurum! on 2011-04-24
You can also use a language , eg  Ruby 
```

Dir["*"].each do |file|
    mtime=File.stat(file).mtime.to_s.split[0]
    puts file if mtime < '2011-04-10'
end

```

---

