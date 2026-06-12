---
title: "[SOLVED] bash enter multiple folders using for loop"
date: 2008-01-24
forum: Programming Talk
---

### Post by Claus7 on 2008-01-24
Hello,

I want to do the same post process in 28 folders. These have one specific pattern as far as their names is concerned :
number_name of folder, e.g. 1_folder1, 2_folder2 e.t.c..

With a for loop as that :
for ((i=1;i<=28;i+=1)); do

cd $i_(*something*)

cd ../
done

I think that with this way I can enter each folder, yet I do not know what I have to type in *something* so as to enter each folder at a time. Is it possible to do it that way?

Thank you in advance,
Rerards!

---

### Post by Claus7 on 2008-01-24
Hello,

the command : cd $i*_* 
seems to be better, yet it has problems with folder 1 and folder 2. They are recognised as folder 10 and 20 respectively.

Also the command : cd $i_* enters only folder 10!
Any ideas?
Regards!

---

### Post by geirha on 2008-01-24
This should loop through all directories in the current directory which matches the regex "[0-9]+_.*" i.e. a number followed by a '_' followed by zero or more symbols.

```
find . -maxdepth 1 -type d -regex '\./[0-9]+_.*' | while read dir; do
  cd "$dir"
  echo "do something in $dir ..."
  cd "$OLDPWD"
done
```

---

### Post by ghostdog74 on 2008-01-24
> **Claus7 said:**
> Hello,

I want to do the same post process in 28 folders. These have one specific pattern as far as their names is concerned :
number_name of folder, e.g. 1_folder1, 2_folder2 e.t.c..

With a for loop as that :
for ((i=1;i<=28;i+=1)); do

cd $i_(*something*)

cd ../
done

I think that with this way I can enter each folder, yet I do not know what I have to type in *something* so as to enter each folder at a time. Is it possible to do it that way?

Thank you in advance,
Rerards!

unless you have more than 1 directory level inside those folders , otherwise, using the for loop might be sufficient ( and your folders follow the same naming convention)

```

for d in [0-9]*_folder*
do
   ls $d
done

```

---

### Post by Claus7 on 2008-01-25
Hello,

thank you very much for your answers!

Now as far as my problem is concerned the code :

find . -maxdepth 1 -type d -regex '\./[0-9]+_.*' | while read dir; do
  cd "$dir"
  echo "do something in $dir ..."
  cd "$OLDPWD"
done

it sais that it will look only one level below the one that I'm working, for folders that their name begin with a number and only a number, which is followed by underscore and the rest of the name. While it does that it will enter the folder, do post process and exit with the environmental variable OLDPWD. I hope geirha that up to now I'm correct. It was very succinct, so I wanted to know what it does. It is working, yet with one small drawback. The output is not in a row, for exampe it doesn't enter 1_folder then 2_folder e.t.c..

I have to admit that I didn't expect the command find to be so extensive.

Gosthdog my regards! Mea culpa, yet in 1_folder1 and 2_folder2 I have to tell you that "folder" is not the same from folder to folder. It is entirely different.

My version of code in order to enter folder 1 then folder 2 and so on till 28, yet of cource not universal because every 10 folders I will have a problem is this :

```
for ((i=1;i<=28;i+=1)); do

if [ "$i" = "1" ]; then
    cd 1_NAME_folder1
elif  [ "$i" = "2" ]; then 
    cd 2_NAME_folder2
else
    cd $i*_*
fi

echo $i >> ../name.txt 
pwd >> ../name.txt
 
POST PROCESS

cd ../
done
```

Thank you once again,
Regards!

---

### Post by geirha on 2008-01-25
If you need to do it in such numerical order, then your for-loop is probably best, but if I understand the pattern correctly, then if you change ```
cd $i*_*
``` to ```
cd $i_*
``` It should work for all those folders.

---

### Post by Claus7 on 2008-01-25
Hello,

unfortunately the code 
```
cd $i_*
```
enters only folder ten, i.e. 10_folder_name 28 times!

I thought combining this with cd $i+_*, yet to no avail. 

Regards!

---

### Post by geirha on 2008-01-25
> **Claus7 said:**
> Hello,

unfortunately the code 
```
cd $i_*
```
enters only folder ten, i.e. 10_folder_name 28 times!

I thought combining this with cd $i+_*, yet to no avail. 

Regards!

Ah, yes I tested a little bit more now. For some reason when using $i_, it also takes the _ as part of the variable name, and that variable expands to an empty string, so you are practically doing "cd *" which will change into the first path in the list * expands to. So, enclose the variable in brackets like this:
```
cd ${i}_*
```

---

### Post by Claus7 on 2008-01-25
Hello,

very nice indeed! This is exactly what I was seeking.

Regards!

---

