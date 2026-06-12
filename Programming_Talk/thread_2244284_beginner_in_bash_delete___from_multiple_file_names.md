---
title: "beginner in bash: delete _ from multiple file names"
date: 2014-09-15
forum: Programming Talk
---

### Post by Eunde on 2014-09-15
Hello
I am trying to remove parts of the name of multiple files.
The files were for example called 341F-3-F1_X.fastq or 341F-2-A1_X.fastq 
I managed to reduce the names to 3F1_.fastq or 2A1_.fastq. Now I would also like to remove the _ to make them e.g. 3F1.fastq (I should have probably remove it with the X) but the same script doesn't work for _ , I assume because _ has a different meaning. I used:
   

    ```

for old in directory/*.fastq
       do 
       new=$(echo $old | sed 's/_//g')
       mv "$old" "$new"
       done

```

I am very new to scripting, and would be very thankful for some help.

---

### Post by ofnuts on 2014-09-15
AFAIK there is nothing special about the underscore in regular expressions.

You can use the "rename" command. Basically it's an all-in-one "loop on file pattern; substitute part of the name, rename to new name".:

```
rename "s/_//g"  directory/*.fastq

```

For your initial names, that would be (***assuming you are in "directory"***)

```
rename -n 's/[^-]+-([^-]+)-([^_]+)_.\.fastq/$1$2.fastq/' *
```

In slow motion:
[LIST]
[*]cut the name in three parts:
[LIST]
[*]up to the first dash 
[*]anything from first to second dash 
[*]anything from second dash to following underscore (not included) 
[/LIST]
  
[*]build the new name using parts 2 and 3 and append '.fastq' 
[*]remove "-n" when hapy with result (with "-n" it only shows what it would do) 
[/LIST]

---

### Post by Eunde on 2014-09-15
Thanks a lot, for your fast reply and especially for your detailed explanations. 
It works now, however, the problem was not my code, but the folder name. I tried your 'rename-script' on a small batch, and it worked. Then I tried it again on the original folder and it didn't work either. I tried the same with mine, and it also worked on the small batch. It seems that it didn't work on the first folder, because the folder name has an underscore. At least this is the only reason I can imagine, since the two folders are in the same directory...
Anyway, at least I learned some bash!

---

### Post by Vaphell on 2014-09-15
having examples of troublesome paths would be nice

that said, you should construct your regex in a way that marks the filename part explicitly so there can be no ambiguosity

```
s:(.+)/[...]+-([...]+)-([...]+)_\.fastq:$1/$2$3.fastq:
```

first parenthesis should consume the dir, leaving only the filename up for grabs.

It's not bash but perl based rename though ;-)



bash:

```
for old in directory/*.fastq
do
    dir=${old%/*}
    fn=${old##*/}
    IFS='-_.' read -r _ n1 n2 _ _ <<< "$fn"
    echo mv "$old" "$dir/$n1$n2.fastq"
done
```

proof it works
```
$ old=/some/BS/341F-3-F1_X.fastq
$ dir=${old%/*}
$ fn=${old##*/}
$ IFS='-_.' read -r _ n1 n2 _ _ <<< "$fn"
$ echo "$dir/$n1$n2.fastq"
/some/BS/3F1.fastq
```

---

### Post by Eunde on 2014-09-15
OK, thanks. 
Well it was like this: 

bad path:
```
rename "s/_//g"  /home/arb/Desktop/**Joined_Fastq**/*.fastq
```

good path:
```
rename "s/_//g"  /home/arb/Desktop/**test**/*.fastq
```

But the interesting thing is that I only had problems with the Joined_Fastq path when i wanted to delete the underscore. For the numbers it worked fine.

---

### Post by Vaphell on 2014-09-15
do you have your original names or did you change them already and now have that dangling _?
In case of originals being available, start from scratch and nail the workflow perfectly. In general it's a bad idea to make irreversible changes during work-in-progress.
If it's just the dangling _ in front of extension, use

```
s/_(\.fastq)$/\1/
```

---

