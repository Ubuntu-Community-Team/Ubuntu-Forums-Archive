---
title: "Bash - list the oldest file in the directory"
date: 2009-09-08
forum: Programming Talk
---

### Post by falconindy on 2009-09-08
I'm working on what's become a far too complex backup routine, and I need a little bit of help. I don't want to get too detailed (because I'll go on forever), but I'll be making incrementals daily and full backups every Sunday and every 1st of the month. I'd only like to keep a specific number of full weeklies and dailies, so I figure whenever I make one of them, I'll just delete the oldest monthly or weekly backup I have (provided I'm over my quota). This is what I came up with to list that oldest file in the directory:

```
ls -l | sort -k 6 | head -$((`find ./* | wc -l` - 4)) | grep .bkup | cut -d ' ' -f 8
```It's ugly, but it works. However, I'm convinced there's a better way. My major complaint is the `sort -k` because it's not guaranteed portable with the `ls` command. Anyone able to rewrite/compress this into something neater?

Thanks in advance.

---

### Post by Reiger on 2009-09-08
ls has an option to sort by modification time. Think it's -t. Also find has a -mtime test which looks like it could be a test to find all files with modification time = <value>?

---

### Post by unutbu on 2009-09-08
Have a look at hyper_ch's backup.sh script: [http://ubuntuforums.org/showpost.php?p=6024283&postcount=7](http://ubuntuforums.org/showpost.php?p=6024283&postcount=7)

The part that removes backups that are older than 90 days is at the end:

```

for file in "$( $FIND $BACKUPDIR/old/ -maxdepth 1 -type d -mtime +$DAYS )"
do
  $RM -Rf $file
done
```

---

### Post by falconindy on 2009-09-08
> **Reiger said:**
> ls has an option to sort by modification time. Think it's -t. Also find has a -mtime test which looks like it could be a test to find all files with modification time = <value>?
Wow. I must have skipped over that -t flag when I read over `man ls`. Shame on me. The whole loop works flawlessly as:
```
while [ `ls -t *.bkup | wc -l` -gt 4 ]; do
    rm `ls -t *.bkup | head -1`
done
```That's way more civil. I'll just replace the '4' with whatever my set retention value is.

@unutbu: i came across that solution, but I don't want to have to calculate and define a date as "safe" to remove before. I'd rather rely on a count of the number of files in the directory to make sure that I have any many backups as I've defined for my retention period.

---

### Post by naphtha on 2012-02-10
```
OldestFile="$(ls -tr1|head -1)"
```img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by drs305 on 2012-02-10
Thanks for the input; this thread is probably older than the oldest file on his/her computer. 

Thread closed.

---

