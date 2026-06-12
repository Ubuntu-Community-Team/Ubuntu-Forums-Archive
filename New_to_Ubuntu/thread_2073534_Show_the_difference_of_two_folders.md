---
title: "Show the difference of two folders"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by duncan12 on 2012-10-19
I have got my home directory into a bad situation with a mistyped rm command. I have now got as far as getting a backup onto an external hard drive as regular files.

So I have:

[LIST]
[*]**Folder A**: Current home directory: some files missing
[*]**Folder B**: Old home directory: some files out of date or don't exist in current home directory
[/LIST]

There are plenty of ways I've come across using diff, find etc. to compare the contents of two directories (**/home/duncan/** and **/media/FreeAgent\ GoFlex\ Drive/old_home/home/duncan/**) but that's not what I want.

I am not interested if a file exists in *Folder A* but not *Folder B*. I am not interested in anything inside a "dotfile" or "dotfolder". I am not interested in files where the contents differ.

I am **only** interested in files that exist in **Folder B** but not **Folder A**.

How can I check for this, without wasting resources checking various files byte-for-byte?

Thanks,
Duncan

---

### Post by duncan12 on 2012-10-25
bump

---

### Post by stinkeye on 2012-10-25
Freefilesync has a compare feature prior to syncing where you can choose a view.
eg in the attached pic I have chosen to only view files that will be newly created, not
those that will be overwritten.
ie it shows files that exist in the right pane but not the left.

[URL="https://launchpad.net/~freefilesync/+archive/ffs/+packages"][B][U][COLOR="DarkRed"]FreeFileSync PPA
[/COLOR][/U][/B][/URL]

---

### Post by Lars Noodén on 2012-10-25
What is the desired outcome?  If you want the two directories to contain the same files you could run rsync.

---

### Post by steeldriver on 2012-10-25
the best quick hack I could come up with is

```
#!/bin/bash

dirA=**/home/duncan/**
dirB=**/media/FreeAgent\ GoFlex\ Drive/old_home/home/duncan/**

while read -r -d $'\0' file; do 
    [ -f "$dirA"/"$file" ] || echo "$dirA" : "$file" not found
done < <(find "$dirB" -path '*/.*' -prune -o -type f -printf '%P\0')
```

Probably rsync has an option to list the out-of-sync files without actually syncing, as well

---

### Post by monkeybrain2012 on 2012-10-25
Try unison, it is in the repo.

---

### Post by drmrgd on 2012-10-25
> **steeldriver said:**
> the best quick hack I could come up with is

```
#!/bin/bash

dirA=**/home/duncan/**
dirB=**/media/FreeAgent\ GoFlex\ Drive/old_home/home/duncan/**

while read -r -d $'\0' file; do 
    [ -f "$dirA"/"$file" ] || echo "$dirA" : "$file" not found
done < <(find "$dirB" -path '*/.*' -prune -o -type f -printf '%P\0')
```

Probably rsync has an option to list the out-of-sync files without actually syncing, as well

Hmmmm....that actually gives me an idea.  I don't have time to test this, but it might be informative just the same.  If you include the -n option in Rsync, you'll get a dry run that will just show you what would happen if you actually run the script.  Rsync also allows you to easily exclude elements from tne backup.  So, if you were to run rsync in dry run mode, excluding what you don't care about and then capture the output to a text file, that might show you what files are different. 

Also, have you tried using the -q option of 'diff', which does show which skips the contents of the files and just shows which files are in A but not B and so on.  There is also the -x option which will allow you exclude files that match a pattern.  From the GNU documentation:

[http://www.gnu.org/software/diffutils/manual/html_node/Comparing-Directories.html](http://www.gnu.org/software/diffutils/manual/html_node/Comparing-Directories.html)

So, I think you might be able to exclude the dot files and directories with a '-x' option.  

Maybe you've tried all the diff options, already, though....

---

