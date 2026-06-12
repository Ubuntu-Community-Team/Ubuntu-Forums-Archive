---
title: "More BASH help."
date: 2012-11-15
forum: Programming Talk
---

### Post by PinkFloyd102489 on 2012-11-15
```
ls --ignore="*.zip" --ignore="dump" --ignore="*.sh" --ignore="test*" > dump
cat dump

while read line; do

select np in "new" "pre"; 
        do
        echo "Is $line New or Pre?"
        case $np in
                new ) rm $line.zip && mv $line ~/work/New/Waiting/;;
                pre ) mv $lin.zip ~/work/Pre-Owned/ && rm -rf $line;;
        esac
done
done < dump

```

Basically what I want it to do is list out the directory and go line by line. For each directory, I want it to prompt me as to what to do with it and execute those based on the input.

I keep getting a "do unexpected, expected done".

---

### Post by Vaphell on 2012-11-15
does that *ls --ignore ...* line is supposed to produce list of directories?

either way you shouldn't use *ls* as a source of data and go with *find* instead
and you can skip the temp file
*while read -r ln; do ...; done < <( command )* will do the same directly.

---

### Post by PinkFloyd102489 on 2012-11-15
> **Vaphell said:**
> does that *ls --ignore ...* line is supposed to produce list of directories?

either way you shouldn't use *ls* as a source of data and go with *find* instead
and you can skip the temp file
*while read -r ln; do ...; done < <( command )* will do the same directly.

Duly noted, but that part isn't the problem. It's the loop portion. The ls portion is left over from a previous script, I just haven't taken it out yet.

---

### Post by Vaphell on 2012-11-15
don't you run the script with *sh script* by any chance? because i get 'Syntax error: "do" unexpected (expecting "done")' in that case, when i use *./script* (assuming #!/bin/bash) or *bash script* it doesn't throw that error.

most likely you will hit 2 problems
- script not waiting for input
```
while IFS= read -rd $'\0' -u3 line
do
  ...
done 3< <( find -mindepth 1 -maxdepth 1 ! "(" -iname "*.sh" -o -iname "*.txt" -o -iname "*.zip" -o -iname "dump" ")" -printf "%f\0" )
```
or
```
while IFS= read -rd $'\0' line
do
  list+=( "$line" )
done < <( find -mindepth 1 -maxdepth 1 ! "(" -iname "*.sh" -o -iname "*.txt" -o -iname "*.zip" -o -iname "dump" ")" -printf "%f\0" )

for l in "${list[@]}"
do
  ...
done
```
if you want only dirs *find -type d* would do the job without additional conditions on name
 
- infinite select loop
you actually have to break out of the loop, also you want to have another case when the match is 'none of the above' so you can retry (*break* jumps out of the loop, *continue* starts another iteration)
```

  echo "Is '$l' New or Pre?"
  select np in "new" "pre" 
  do
    case $np in
      new ) rm $line.zip && mv $line ~/work/New/Waiting/;;
      pre ) mv $lin.zip ~/work/Pre-Owned/ && rm -rf $line;;
      *** ) continue;;**
    esac
    **break**
  done
```

---

### Post by ofnuts on 2012-11-16
> **PinkFloyd102489 said:**
> ```
ls --ignore="*.zip" --ignore="dump" --ignore="*.sh" --ignore="test*" > dump
cat dump

while read line; do

select np in "new" "pre"; 
        do
        echo "Is $line New or Pre?"
        case $np in
                new ) rm $line.zip && mv $line ~/work/New/Waiting/;;
                pre ) mv $lin.zip ~/work/Pre-Owned/ && rm -rf $line;;
        esac
done
done < dump

```Basically what I want it to do is list out the directory and go line by line. For each directory, I want it to prompt me as to what to do with it and execute those based on the input.

I keep getting a "do unexpected, expected done".

Without a "break" statement in the new/pre case (or at the end if $np is not empty) you are going to loop forever on the first line, because you won't exit your first select.

---

