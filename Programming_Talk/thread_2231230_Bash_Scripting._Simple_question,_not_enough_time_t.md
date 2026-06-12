---
title: "Bash Scripting. Simple question, not enough time to research it..."
date: 2014-06-24
forum: Programming Talk
---

### Post by intlvelvet on 2014-06-24
I am trying to edit a group of text files, by prepending a string (based on the filename of each text file) to the beginning of each line of each file.  My problem was mostly addressed in the following forum post: [http://www.unix.com/shell-programming-and-scripting/178902-append-variable-texts-beginning-each-line-all-files-directory.html](http://www.unix.com/shell-programming-and-scripting/178902-append-variable-texts-beginning-each-line-all-files-directory.html) .  The script that was ultimately proposed included as follows > [COLOR=#170072]for i in *.sco; do awk -v A=`basename $i .sco` '{a[NR]=$0;}END{for(i=1;i<=NR;i++){print A,a[i] >FILENAME;}}' $i; done[/COLOR].

This results in the filenames being prepended with the filename followed by a space.  However, I need it to be prepended with a filename followed by a comma - yielding a csv file.  I do not know how to parse that script, and do not have enough tile to learn how before I need this done.  Please help me if you can.  Thanks.

---

### Post by steeldriver on 2014-06-24
Simplest way would probably be to change the awk *output field separator*:

```

for i in *.sco; do awk **-v OFS=,** -v A=`basename $i .sco` '{a[NR]=$0;}END{for(i=1;i<=NR;i++){print A,a[i] >FILENAME;}}' $i; done

```

Not sure that reading the entire file into an awk array is a terribly good way of doing this however - there are many line-oriented ways to do it

---

### Post by intlvelvet on 2014-06-24
I don't know what that means, but I thank you nonetheless.  Hopefully this weekend I will have time to learn enough bash to become competent.  Thanks again.

---

