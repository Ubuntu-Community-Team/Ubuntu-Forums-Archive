---
title: "Delete duplicate file from Text list"
date: 2014-09-28
forum: Programming Talk
---

### Post by johnathan3 on 2014-09-28
I have a list in a text file that contains the md5sum and full path to a file, the list has the original file with duplicate matches below.
The command i used:
find -not -empty -type f -printf "%s\n" | sort -rn | uniq -d | xargs -I{} -n1 find -type f -size {}c -print0 | xargs -0 md5sum | sort | uniq -w32 --all-repeated=separate &> duplist.txt

The file looks as such:

003babcff87660ded33e7fa38fe8a4c2  ./Vault/Admin PC backup/Pictures/iPhone/IMG_1191.PNG
003babcff87660ded33e7fa38fe8a4c2  ./Vault/AndroidGalaxyS4SD Backup/DCIM/Camera/IMG_1191.PNG

003f9da3bf0a405ee458eb1c5383eecb  ./All/Documents/School/Java/Prog 24178/Self Projects/BlackJack/6h.gif
003f9da3bf0a405ee458eb1c5383eecb  ./Vault/Admin PC backup/Documents/Kingston 16GB/Java/Prog 24178/Self Projects/BlackJack/6h.gif

004f736aae279939620ca3af165ee4e9  ./All/Documents/School/Java/Prog 24178/Week1/TestInterface.java
004f736aae279939620ca3af165ee4e9  ./All/Documents/School/Java/Prog 24178/Week1/TestInterface.java.bak
004f736aae279939620ca3af165ee4e9  ./Vault/Admin PC backup/Documents/Kingston 16GB/Java/Prog 24178/Week1/TestInterface.java
004f736aae279939620ca3af165ee4e9  ./Vault/Admin PC backup/Documents/Kingston 16GB/Java/Prog 24178/Week1/TestInterface.java.bak
004f736aae279939620ca3af165ee4e9  ./Vault/Admin PC backup/Documents/USB DRIVE/School Drive/Prog 24178/Week1/TestInterface.java
004f736aae279939620ca3af165ee4e9  ./Vault/USBKINGB ACK/School Drive/Prog 24178/Week1/TestInterface.java



I would like to used a script or command to go through the list and remove the secondary files. The first listed match is the file to keep, the matches below can be removed with confirmation.
The list is about 2000 entries

---

### Post by Vaphell on 2014-09-28
```
#!/bin/bash

while read -r md5 path
do
  [[ -z $md5 ]] && continue
  [[ $prevmd5 != $md5 ]] && prevmd5=$md5 && continue
  printf 'del: `%s` (%s)\n' "$path" "$md5"
  # rm "$path"
done < md5.txt
```

btw, there are programs that can find dupes for you

---

### Post by johnathan3 on 2014-09-28
Thanks for the reply. this works but will not propmt me yes or no to delete a file (in some cases there needs to be a duplicate)

I modified it to 

#!/bin/bash

while read -r md5 path
do
  [[ -z $md5 ]] && continue
  [[ $prevmd5 != $md5 ]] && prevmd5=$md5 && continue
  printf 'del: `%s` (%s)\n' "$path" "$md5"
 echo "Delete this file? "
 read input_variable
 echo "You entered: $input_variable"
 if $input_variable == yes
        then
                rm "$path"
        else
                end;
 fi


#   rm "$path"
done < duptestlist.txt



This does not work it just continues without stopping to wait for my input.
Same if I change the rm to rm -i for interactive input. but it just gets bypassed as well

---

### Post by Vaphell on 2014-09-28
```
#!/bin/bash

while read -r -u3 md5 path
do
  [[ -z $md5 ]] && continue
  [[ $prevmd5 != $md5 ]] && prevmd5=$md5 && continue
  printf 'del: `%s` (%s)\n' "$path" "$md5"
  read -p "Delete this file? " ans
  echo "You entered: $ans"
  [[ ${ans,,} =~ ^(y|ye|yes)$ ]] && rm "$path"
 # echo rm "$path"
done 3< duptestlist.txt
```

should match y, ye, yes (case insensitive)

edit: improvement for easier y/n (single keypress)

  ```
read -p "Delete this file (y/n)? " -n1 ans
  printf '\nYou entered: %s\n' "$ans"
  [[ ${ans,,} == y ]] ....
```

---

### Post by johnathan3 on 2014-09-28
Awesome, this works exactly how i needed it to! Thanks

---

### Post by johnathan3 on 2014-10-02
Im still going at this, so far 16 GB recovered in images LOL

any way we can change this to mv the duplicate files to a specific top level folder and then keep the path ?

I tried but get messed up because the path contains ./path the dor slash for the directory i run it from.
I have created a Directory "Duplicates"

if the duplicate file is in "./foo/bar" i want it to be move to "./Duplicates/foo/bar" even if the full directory path does not exist.

I tried for a few hours but cant figure it out.

Thanks for any help.

---

### Post by Vaphell on 2014-10-02
```
dupepath=./Duplicates/${path#./}
mkdir -p "${dupepath%/*}"
mv "$path" "$dupepath"
```

if you run the search repeatedly, you may need to filter the ./Duplicates out so it doesn't show up in the results.

---

### Post by johnathan3 on 2015-07-22
I have come back to this again and want to learn how this script is working so that if i need, I can edit it later.
Can anyone explain what each line is doing? so I can add comments to mine.

this is what i have now:

```
#!/bin/bash
blue=$(tput setaf 4)
while read -r -u3 md5 path
do
  [[ -z $md5 ]] && continue
  [[ $prevmd5 != $md5 ]] && prevmd5=$md5 && continue
  echo "         "
  grep $md5 duplicatesMar182015.txt
  echo "         "
  dupepath=./.deleted/DefDupe/${path#./}
  printf '\e[1;31mdel: `%s` (%s)\n\e[m' "$path" "$md5"
  ls -alth "$path"
  echo "         "
  read -p "Delete this file (y/n)? " -n1 ans
  printf '\nYou entered: %s\n' "$ans"
  [[ ${ans,,} =~ ^(y|ye|yes)$ ]] &&  ls -alth /NAS/"$path" | awk '{print $5}' >> /NAS/savedspace.txt && mkdir -p "${dupepath%/*}" ; mv "$path" "$dupepath"
done 3< duplicatesMar182015.txt

```

---

### Post by johnathan3 on 2015-07-27
Still trying to fgure out what this code is doing I have the basic overview of what it does, but I want to add comments to it so that later on when i need to modify it, I have a better understanding of what each line is doing the the functions of each peice.

---

### Post by Vaphell on 2015-07-28
```
while read -r -u3 md5 path
do
    ...
done 3< duptestlist.txt
```

this loop assigns filedescriptor #3 to the input file and uses that fd3 to feed *read* on a per line basis. It's necessary to avoid collision with user input, funky things would happen if both the loop and user prompts were using the same default "channel".
md5 and path are variables to be filled, which implies 2 values in the row of input.


```
  [[ -z $md5 ]] && continue
```
this tests for emptiness of the md5, a proxy for "it's an empty line, skip it plz"

```
  [[ $prevmd5 != $md5 ]] && prevmd5=$md5 && continue 
```

this tests if previous line and the current line have different md5s. If they do, the currently tested file is legit and there is nothing to do here, so *continue* = skip to the next item on the list. 
  
```
  dupepath=./.deleted/DefDupe/${path#./}
  printf 'del: `%s` (%s)\n' "$path" "$md5"
```

if you get this far, this means that $prev_md5 and current $md5 are in fact the same (otherwise *continue* would skip), implying dupe. Destination path for removal is calculated, printf prints del message with file details.

```
  read -p "Delete this file? " ans
  echo "You entered: $ans"
  [[ ${ans,,} =~ ^(y|ye|yes)$ ]] && .... 
```

obvious


```
ls -alth /NAS/"$path" | awk '{print $5}'
```

this is not mine and i assume it's supposed to log file sizes. That said *stat -c %s "/NAS/$path"* is a less roundabout way to get that information. *stat --help* for a preview of available options.

---

### Post by johnathan3 on 2015-08-04
Awesome Thanks for the explanaitions!
Code:
while read -r -u3 md5 path
do
    ...
done 3< duptestlist.txt

So is the -u3 the users input?

And also what is 

blue=$(tput setaf 4)

---

### Post by Bakerconspiracy on 2015-08-16
> **Vaphell said:**
> ```
#!/bin/bash

while read -r md5 path
do
  [[ -z $md5 ]] && continue
  [[ $prevmd5 != $md5 ]] && prevmd5=$md5 && continue
  printf 'del: `%s` (%s)\n' "$path" "$md5"
  # rm "$path"
done < md5.txt
```

Ever feel like bash is the wrong toolset for some pattern matching at this level? I feel like you can have safety and fast implementation with a language like python for this problem.

---

