---
title: "replace occurrences with a calculation in bash/shell/vim"
date: 2012-09-18
forum: Programming Talk
---

### Post by fuzzylogic25 on 2012-09-18
Hi,

Im trying to get an extract of all the files on my hard disk with file sizes. so far I am using this command:


$ find . -printf "%s\t%p\n"

which outputs something like this

23896242k       ./10945766938975-001.mp3

Now thats great, but id prefer if that value 23896242K (which comes from the %s in the command) was replaced with the calculated value 23896242/1024K (divide each occurrence by 1024).

Is this possible?

---

### Post by Bucky Ball on 2012-09-18
*Thread moved to **Programming Talk***

---

### Post by Vaphell on 2012-09-18
23896242K? is that 24GB? by dividing by 1024 you want to get megabytes? Shouldn't you multiply by 1024 to get bytes?
besides i don't see any k suffix when i run your command, according to manual %s is supposed to return bytes


either way this should get you started, it's straightforward and you can modify to suit your needs
```
while read -r s f
do
  # if you get K
  if [[ $s =~ .*K ]]
  then
    s=$((${s%K}/1024));
  else
    s=$((s/1024))
  fi
do printf "$s\t$f\n"; done < <( find .  -printf "%s\t%p\n" )
```

---

### Post by einonm on 2012-09-18
The command 'du -h /' will give you the output you want, I believe - print all files and sizes in human readable form. 

If you're doing this as a programming exercise, you could always check out the source of du from the coreutils source package.

---

### Post by ofnuts on 2012-09-18
> **fuzzylogic25 said:**
> Hi,

Im trying to get an extract of all the files on my hard disk with file sizes. so far I am using this command:


$ find . -printf "%s\t%p\n"

which outputs something like this

23896242k       ./10945766938975-001.mp3

Now thats great, but id prefer if that value 23896242K (which comes from the %s in the command) was replaced with the calculated value 23896242/1024K (divide each occurrence by 1024).

Is this possible?
With ls you can use about any "unit" for the size:
```

#For megs
ls -l --block-size 1048576 
#For gigs
ls -l --block-size 1073741824

```
Note that just dividing a size by 1024 to express it in a bigger unit isn't right... you have to add 1023 to it first... (the --block-size parameter does it for you)

---

### Post by trent.josephsen on 2012-09-18
I agree with einonm, du is probably the command you want. It takes some other options you might find useful, like -x, which traverses only one file system. Check du(1) for the whole list.

There's also an old [thread](http://ubuntuforums.org/showthread.php?t=885344) about sorting du's output that you might find interesting.

---

