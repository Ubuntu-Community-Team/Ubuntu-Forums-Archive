---
title: "modify compile tar need help"
date: 2008-11-10
forum: Programming Talk
---

### Post by atisz on 2008-11-10
hi

i would like to make an archive of my file system with directory structure and files that they contain, but only the name of the files with 0kB, empty files.

[COLOR="RoyalBlue"]tar cf fs.tar --no-recursion --files-from <(find / -type d)[/COLOR]

i have already tried this but it does not save the files, only the directory structure. 

can anybody help me with this? how could i modify and compile the tar to be able to do that. I mean i would like to get a function of tar e.g. 
([COLOR="RoyalBlue"]--zero-files[/COLOR]): 

tar --zero-files /home archive.tar

---

### Post by geirha on 2008-11-10
Why does it need to be an archive? why not just do ```
find / | gzip >fs.gz
```

Anyway, I guess you could recreate your directory structure in a temporary directory with empty files.
```

# Create a temporary directory in /tmp
tmpdir=`mktemp -d` ; echo $tmpdir  

# Recreate the directory structure into $tmpdir
sudo find / -type d -not -path "$tmpdir*" -printf "$tmpdir/%p\0" | xargs -0 mkdir -p

# Create empty files with same ownership and permissions as their non-empty counterparts
sudo find / -type f -not -path "$tmpdir*" \
            -exec touch --reference={} "$tmpdir"/{} \; \
            -exec chown --reference={} "$tmpdir"/{} \; \
            -exec chmod --reference={} "$tmpdir"/{} \;

cd "$tmpdir" ; tar cf /tmp/fs.tar .

```

---

### Post by atisz on 2008-11-17
thank you geirha you helped me a lot :)

---

