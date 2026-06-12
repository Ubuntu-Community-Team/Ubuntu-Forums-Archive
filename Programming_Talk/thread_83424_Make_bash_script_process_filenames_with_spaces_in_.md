---
title: "Make bash script process filenames with spaces in it ?"
date: 2005-10-28
forum: Programming Talk
---

### Post by kabus on 2005-10-28
Hi everybody,
I'm very new at bash scripting and just got my first script, a file mass renamer, to work.
Now I'd like to expand it by making it accept input filenames that contain spaces.
So far I've figured out a way to turn ' ' into '\ ' with sed :

```
sed -e "s/ /\\\ /g"
```

But no matter what I do I can't seem to get mv to accept this as input (ie as the source file).
This is what I'm trying to do :

```
for i in *; do 
	source=$(echo $i|sed -e "s/ /\\\ /g")
        mv $source $target
done
```

With $source, like above mv interprets an input like fi\ le\ 1 as multiple files.
When I do "$source" instead it gets interpreted as fi\\ le\\ 1. 

Any ideas ?
Is there a better way to do this ?

---

### Post by LordHunter317 on 2005-10-28
Variables containing spaces needs to be quoted, so the shell passes the whole variable as one argument:```
mv "$source" "$target"
```I'm not sure what you're using sed for, but it's not needed.

---

### Post by poptones on 2005-10-28
You cannot use for in a loop like that because "for" separates a list based on whitespace. It seems to be a "bug" in bash for that has turned into a "feature." Ev3en if you put double quotes around it ( "/this is/a/single/file path" ) for still splits the list of files by whitespace.

An easy way to do it is to prepare a list and feed it into while. 

while read file;do
 mv "$file" "$somewhere"
done<file_list.txt

---

### Post by kabus on 2005-10-28
Thanks, the While method works fine for me. :)

---

### Post by LordHunter317 on 2005-10-28
> **poptones]You cannot use for in a loop like that because "for" separates a list based on whitespace.[/quote]No, not in this case.  'for i in *' does indeed expand correctly in GNU bash.  Wildcard expansions are completely assigned into the variable.

OTOH, doing this:```
FOO="bin bash bar"
for i in $FOO  said:**
> Ev3en if you put double quotes around it ( "/this is/a/single/file path" ) for still splits the list of files by whitespace.You're confusing variable expansion with wildcard expansion, I think.  They don't follow the same rules.

---

### Post by poptones on 2005-10-28
Thanks LH. I knew there was a way around it but I never found a proper description of the problem and a solution (and yes, I've read the bash programming manual).

Believe it or not I posted my answer hoping someone would come along and better it :)

---

### Post by LordHunter317 on 2005-10-28
Well, it's not obvious.  It's more confusing because some older shells (especially ksh) don't process wildcard expansions in the same way.

But GNU bash at least (meaning, all Linux) does the right thing.

---

