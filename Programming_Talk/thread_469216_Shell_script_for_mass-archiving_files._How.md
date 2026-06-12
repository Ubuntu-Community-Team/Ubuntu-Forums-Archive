---
title: "Shell script for mass-archiving files. How?"
date: 2007-06-09
forum: Programming Talk
---

### Post by IFailAtLinux on 2007-06-09
Hello,

I'm trying to make simple shell script to archive a lot of folders(and their contents) contained in one directory to different archives. It can be in .zip, .rar or .7z after archiving, but only those 3 are acceptable. I tried putting something together, but it never worked right. Well, I'm bad at describing things so I'll give an example of what I want to do. Let's say that after "ls" given directory I get:

```

Directory 1
Directory 2
...
Directory n-1
Directory n

```

Some(most) of the directories contain spaces, I don't know if that'll make things harder. In the efect of the script I want to get something like this:

```

Directory 1.zip //contains what "Directory 1" did contain
Directory 2.zip //contains what "Directory 2" did contain
...
Directory n-1.zip //contains what "Directory 3" did contain
Directory n.zip //contains what "Directory 4" did contain

```

Where extension can be .rar of .7z instrad of .zip. It would be nice if script would ask if it should delete original files if the archive is created successfully, but it's not necessary. I tried asking some people already, but no-one could do that. I would appreciate if someone could write something like that if it's not too much work, and if it is I would be content with some guidelines for how to write it. But still I'm better at learning from the source :)

---

### Post by FuturePast on 2007-06-09
```
for i in *; do zip -r "$i" "$i"; done;
``` or similar

---

### Post by yabbadabbadont on 2007-06-09
Do some research into the "rsync" command.  It can probably do all that you want.  It can be used to backup both to a local system or to remote ones as well.

---

### Post by IFailAtLinux on 2007-06-09
Thanks a bunch FuturePast, this works wonders. Well, I feel quite ashamed now, seeing how simple it was.

yabbadabbadont: I'm reading about rsync out of curiosity now, when I have some time as a lot of files are currently being archived. It's quite interesting command.

---

### Post by FuturePast on 2007-06-09
Unix in general, and shell scripting in particular requires a certain mindset which
takes a little time to get into. Just takes a little practice.

---

### Post by bashologist on 2007-06-09
Be careful with the last one. n_n
```
## zip the contents of each folder in the current directory into an archive:
for d in *; do if [ -d "$d" ]; then cd "$d"; zip -r "../$d.zip" *; cd ..; fi; done

## zip every folder in the current directory into an archive:
for d in *; do if [ -d "$d" ]; then zip -r "$d.zip" "$d"; fi; done

## zip everything in the current directory into an archive:
zip -r "${PWD##*/}.zip" *

## example recursively forces the deletion of the directory if zip returns true:
for d in *; do
        if [ ! -d "$d" ]; then
                continue
        fi
        if ! zip -r "$d.zip" "$d"; then
                continue
        fi
        read -p "Delete original directory [Y/n]? " delete
        if [[ "$delete" =~ y|Y ]]; then
                rm -rf "$d"
        fi
done
```

---

### Post by ghostdog74 on 2007-06-09
you can also use the tar command.

---

### Post by IFailAtLinux on 2007-06-11
bashologist: Thank you for detailed information and code. It looked scary at first, but I guess I just have to get used to syntax and thinking in it. But that comes after I get used to OCL and Java...

ghostdog74: I know, but I needed things in one of 3 formats I mentioned. Software that is working on it now doesn't support tar, unfortunately.

---

