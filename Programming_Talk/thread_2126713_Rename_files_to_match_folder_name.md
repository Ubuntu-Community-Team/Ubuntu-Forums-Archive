---
title: "Rename files to match folder name"
date: 2013-03-18
forum: Programming Talk
---

### Post by mafi127 on 2013-03-18
I have around 80 folders. I need to rename *.iso files in the folders to match the folder name in the first place. eg.

folder/this.is.thefolder./ax.iso
folder/some.another.folder/ai.iso
folder/new.name/lks.iso

What I want to do is rename all the iso files in the folders to match the first folder name. like

folder/this.is.thefolder./this.is.thefolder.iso
folder/some.another.folder/some.another.folder.iso
folder/new.name/new.name.iso

---

### Post by ofnuts on 2013-03-18
> **mafi127 said:**
> I have around 80 folders. I need to rename *.iso files in the folders to match the folder name in the first place. eg.

folder/this.is.thefolder./ax.iso
folder/some.another.folder/ai.iso
folder/new.name/lks.iso

What I want to do is rename all the iso files in the folders to match the first folder name. like

folder/this.is.thefolder./this.is.thefolder.iso
folder/some.another.folder/some.another.folder.iso
folder/new.name/new.name.iso
The basename and dirname commands are your friends:
```

# assuming $f is a path to your file
dirpath=$(dirname f)
dirname=$(basename $dirpath)
mv $f $dirpath/$dirname.iso

```
The complete über-one-liner is left as an exercise for the reader :)

---

### Post by schragge on 2013-03-18
Provided that you have no more than one ISO image in each subfolder, here is the one-liner, even three of them:
```
rename -v[COLOR=#ff0000]n[/COLOR] 's:(/[^/]*)/[^/]*$:$1$1.iso:' folder/*/*.iso
```
```
for f in folder/*/*.iso;do dn="${f%/*}";[COLOR=#ff0000]echo[/COLOR] mv -v "$f" "${dn}/${dn##*/}.iso";done
```
```
find folder/* -maxdepth 0 -type d -execdir sh -c 'test -f "$0"/*.iso"&&[COLOR=#ff0000]echo[/COLOR] mv -v "$0"/*.iso "$0/${0##*/}.iso"' '{}' \;
``` The [COLOR=#FF0000]red[/COLOR] parts are for testing purposes, remove them when you're sure it works as advertised. The last one is slightly more safe: if there are several .iso files in a subfolder then *test -f $0/*.iso* will abort with an error message as it expects just one argument.

---

### Post by TheFu on 2013-03-18
If you can guaranty that none of the folders/files have spaces in the names, this is an easy script. If not, I'd run a "rename" script to replace all spaces with _ characters before starting.

The **Advanced Bash Scripting Guide** (google it) will help you learn to create simple scripts like this.  

- give a man a fish ... teach a man to fish ....

---

### Post by schragge on 2013-03-18
@**TheFu**. You're right. I've edited the scripts and added quoting.

---

### Post by mafi127 on 2013-03-18
Thank you all for fast answer. got it working for now :)

---

### Post by Vaphell on 2013-03-18
> **schragge said:**
> ```
ls folder/*/*.iso|xargs -rd\\n rename -v[COLOR=#ff0000]n[/COLOR] 's:(/[^/]*)/[^/]*$:$1$1.iso:'
```

while these would work with common charsets used in file names, what happens when you put newline in the filename? It's a legit extX char after all (only \0 and / are excluded)
To develop a 100% solid solution you need to either use builtin globs directly (without transforming them via pipes, it leads to information degradation), or use commands supporting  \0 as a delimiter (*find -print0*, *grep -Z*, *sort -z*, ...) and *while read -rd $'\0'* their output (or maybe xargs with -0 or whatever)

besides wouldn't ```
rename -v '...' folder/*/*.iso
``` work much better?

---

### Post by schragge on 2013-03-18
Yes, you're right of couse. Somehow, I didn't think of the most obvious solution: using shell globs directly in the file argument of *rename*. I've changed the first command as you suggested. Thanks.
 
As I recall now, I was thinking along the lines that if some of the subfolders don't contain .iso files at all then *ls* would skip them giving an error message on the standard error, but the files in other subfolders still would be renamed.
 
Now I see this would also work with the perl rename script alone as only those subfolders that contain .iso files get expanded by shell globbing. Moreover, even if no subfolders contained .iso files and shell globbing yielded *folder/*/*.iso* as a literal file name, *rename* would happily skip over file name it cannot find.

---

