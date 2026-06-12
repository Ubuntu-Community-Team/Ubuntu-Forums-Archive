---
title: "Walk through 2 lists and change filenames per list"
date: 2011-11-10
forum: Programming Talk
---

### Post by saphil on 2011-11-10
I have to take a list of titles without spaces and use that list to rename the directories in a source directory.  Then zip all the items in the folder to another folder, in which an xml file named per the holding directory is also placed and then scp the folder to another server.

The directories in the directory are named.

1231 Sleepy
1242 Grumpy
1253 Dopey
1264 Happy
1275 Jumpy
1286 Deafy
1297 Dizzey
1308 Hickey
1319 Wheezy
1320 Baldy
1331 Gabby
and so on...

The titles in the list are:

Mutiny_on_the_Bounty_MGM_Clark_Gable_and_Charles_Laughton
Becky_Sharp_RKO_Miriam_Hopkins
Top_Hat_RKO_Fred_Astaire_and_Ginger_Rogers
The_Littlest_Rebel_20th_Century_Fox    Shirley_Temple
The_Informer_RKO_Victor_McLaglen
China_Seas_MGM_Clark_Gable_and_Jean_Harlow
Barbary_Coast_United_Artists_Miriam_Hopkins_and_Edward_G_Robinson
Captain_Blood_Warner_Bros_Errol_Flynn_and_Olivia_de_Havilland
Anna_Karenina_MGM_Greta_Garbo
and so on...

As you can see they are totally unconnected to the directory titles.

I made a piece that checks whether the counts of the 2 pieces are identical, and this part works.

```

#!/bin/sh -x
# the '-x' above is for debugging purposes and is removed in a real run.


echo "Enter the name and relative location of the title file"
read tfile
echo "Enter the directory location from which we will extract subdirectories and files."
read drectory

a=0
while read line
    do a=$(($a+1));
    # echo $a;
    done < "$tfile"
#echo "Final line count is: $a"
#echo $?

find "$drectory" -type d  > "c.dat"
cat ./c.dat
b=-1
while read line
    do b=$(($b+1));
    # echo $b;
    done < "c.dat"
echo "Folders and files in directory: $b"
echo "Final line count: $a"
#echo $?

j=$(echo "$a - $b" | bc)
#echo $j
if [ $j -ne 0 ]
    then
    echo "Whoa there, pardner - there is a problem with your data"
    # Clear the valued from the file and directory variables
    drectory=''
    tfile=''
    exit 113
    #echo $?
    break
else
    echo "The structure is balanced .. We will continue."
    #echo $?
fi

```I am imagining there will be something like this, however this does not seem to be a good structure
 
```

#pmarc is the full or relative path to the xml file
read pmarc
zext="_images.zip"
mext="_marc.xml"

# Walk through file and change the names of the folders to the names in the file.

targetd2="../zip_stage/"
mkdir $targetd2

for line in file:
    zip targetd2/$title/$title+$zext *.jpg  # Zip only the jpgs
    cp $pmarc $targetd2/$title/$title+$mext
    echo $title$mext " is in place." >> ziplog.log
    echo $title " and " $folder " zip done." >> ziplog.log
done

targetd3="../ftp_staging/"
cd $targetd2
# Copying the file structure to the ftp_staging directory
find * -type d -exec mkdir $targetd3\{\} \;
echo $targetd2 " directory structure is complete." >> ziplog.log
# putting the files you are hunting into the new directory structure
find . -name \*.zip -exec cp {} $targetd2{} \;
echo $targetd2 "*.zip files moved." >> ziplog.log
find . -name \*.xml -exec cp {} $targetd2{} \;
echo $targetd2 " ..complete." >> ziplog.log

for item in (ls $targetd3)
    scp -r item [servername]:/[target4_directory]/ > ziplog.log 2>&1
echo $title " has been copied to FTP server."
done

```

---

### Post by ofnuts on 2011-11-10
Just about the first step:

[LIST]
[*]I can't figure how you are supposed to guess into what "1275 Jumpy" should be renamed
[*]Using "while read line" to count line is overkill, "wc -l" is the canonical way to do it
[*]or while your use "while read line"  read the stuff in two arrays, you will need them later
[*]and actually you can init the two arrays with mapfile/readarray
[/LIST]
```

# Read source directories in array
mapfile -t oldnames < <(find . -maxdepth 1 -mindepth 1 -type d | sort)
# Read target names in array
mapfile -t newnames < data

echo "oldnames: ${#oldnames[@]} : ${oldnames[@]}"
echo "newnames: ${#newnames[@]} : ${newnames[@]}"

# Compare array sizes
[[ ${#oldnames[@]} -ne ${#newnames[@]} ]] && echo "Data inconsistent" && exit

```
[LIST]
[*]Do yourself (and anyone who will have to maintain the script) a favor and spell "directory" correctly
[*]I wonder why you clear "drectory" and "tfile" just before exiting?
[/LIST]

---

### Post by saphil on 2011-11-10
Wow, thanks!
That is far cleaner than what I was grinding out.
The  thing about the names to folder conversion is that we can't know what  the titles are going to be - they will just be set in order  alpha-by-folder-name and we have faith they don't forget what they were  doing when they prepare the titles for me.

You are right.  I have already had code break over my "clever" $drectory variable.



I am looking at your suggestions and :
```

oldnames: 2 : ../ftarget7/example1 ../ftarget7/example2
newnames:  16 : clean_pup.py clean_pup.pyc find_pup.py find_pup.pyc flist.txt  ftp_up.py Pig.pdf pipes.py poke.pdf ww elevenses twelveses thitrteenses  fourteenses fifteenzes sisixteenxzes
Data inconsistent

```
This is great, or using a set of arrays that match
```

$ ./ntest.sh
oldnames:  16 : ../ftarget7/example1/1010 ../ftarget7/example1/11  ../ftarget7/example1/1111 ../ftarget7/example1/1212  ../ftarget7/example1/1313 ../ftarget7/example1/1414  ../ftarget7/example1/1515 ../ftarget7/example1/1616  ../ftarget7/example1/22 ../ftarget7/example1/33 ../ftarget7/example1/44  ../ftarget7/example1/55 ../ftarget7/example1/66 ../ftarget7/example1/77  ../ftarget7/example1/88 ../ftarget7/example1/99
newnames: 16 :  clean_pup.py clean_pup.pyc find_pup.py find_pup.pyc flist.txt ftp_up.py  Pig.pdf pipes.py poke.pdf ww elevenses twelveses thitrteenses  fourteenses fifteenzes sisixteenxzes

```

Now I am looking for the way to remove the path portion of the items in the oldnames array so I can mv oldname newname.

---

### Post by ofnuts on 2011-11-10
> **saphil said:**
> Now I am looking for the way to remove the path portion of the items in the oldnames array so I can mv oldname newname.My code only lists the 1st level directories. Otherwise look at basename/dirname.

---

### Post by ofnuts on 2011-11-10
> **saphil said:**
> The  thing about the names to folder conversion is that we can't know  what  the titles are going to be - they will just be set in order   alpha-by-folder-name and we have faith they don't forget what they were   doing when they prepare the titles for me.This is the kind of requirement I ask the "customer" to sign with his own blood (and maybe some of his kids').

> **saphil said:**
> Now I am looking for the way to remove the path portion of the items in the oldnames array so I can mv oldname newname.My code only lists the 1st level directories. Otherwise look at basename/dirname.

---

### Post by saphil on 2011-11-10
When I moved the script to the folder I was testing, it gave a cleaner response. It still gives the "./" at the beginning.  It really wouldn't matter, since I am moving the file to a different folder anyway.

```


lyrasis@LTS-CLOUDCTL-01:~/bin/LyrasisCode/ftarget7/example1$ ./ntest.sh
oldnames: 16 : ./1010 ./11 ./1111 ./1212 ./1313 ./1414 ./1515 ./1616 ./22 ./33 ./44 ./55 ./66 ./77 ./88 ./99
newnames: 16 : clean_pup.py clean_pup.pyc find_pup.py find_pup.pyc flist.txt ftp_up.py Pig.pdf pipes.py poke.pdf ww elevenses twelveses thitrteenses fourteenses fifteenzes sisixteenxzes


```

---

### Post by saphil on 2011-11-14
I hate to keep bugging you, but I am confused.
Can you help me find the extra (or missing " mark)

```

#!/bin/bash
# for changing the names of directories in the renaming stage.
echo "Enter the name and relative location of the title file"
read title_file
echo "cd to the directory you are processing"
echo "Enter the directory location and file name in which"
echo "  you will be changing directory names."
echo "enter the absolute or relative path to this directory."
echo "  ./  is valid for a relative path to the present working directory."
read directory
echo "$directory"
# Read source directories in array
mapfile -t oldnames < <(find "$directory" -maxdepth 1 -mindepth 1 -type d | sort)
# Read target names in array
mapfile -t newnames < "$title_file"

echo "oldnames: ${#oldnames[@]} : ${oldnames[@]}"
echo "newnames: ${#newnames[@]} : ${newnames[@]}"
directory2="../newNames/"
mkdir "${directory2}"
for i in "${oldnames[@]"
    do
        cp "${oldnames[${i}-1]" "$directory2${newnames[${i}-1]"
        #echo "${oldnames[${i}-1]" " is now "  "${newnames[${i}-1]"
        echo "${i}"
    done
exit 0

```The run gives an error -it says there is a missing quote on the line that says
```
        echo "${i}"

```

I have tried adding quotes where they made sense to me, however the issue is not cleared.

There is also an error about an unexpected EOF but I believe fixing the quote thing will fix this other error.

---

### Post by saphil on 2011-11-14
I found one omission.. 

> **saphil said:**
> I hate to keep bugging you, but I am confused.
Can you help me find the extra (or missing " mark)

```

#!/bin/bash
# for changing the names of directories in the renaming stage.
echo "Enter the name and relative location of the title file"
read title_file
echo "cd to the directory you are processing"
echo "Enter the directory location and file name in which"
echo "  you will be changing directory names."
echo "enter the absolute or relative path to this directory."
echo "  ./  is valid for a relative path to the present working directory."
read directory
echo "$directory"
# Read source directories in array
mapfile -t oldnames < <(find "$directory" -maxdepth 1 -mindepth 1 -type d | sort)
# Read target names in array
mapfile -t newnames < "$title_file"

echo "oldnames: ${#oldnames[@]} : ${oldnames[@]}"
echo "newnames: ${#newnames[@]} : ${newnames[@]}"
directory2="../newNames/"
mkdir "${directory2}"
for i in "${oldnames[@]"   # **[COLOR=DarkRed]this needs a closing curly bracket[/COLOR]**
    do
        cp "${oldnames[${i}-1]" "$directory2${newnames[${i}-1]"
        #echo "${oldnames[${i}-1]" " is now "  "${newnames[${i}-1]"
        echo "${i}"
    done
exit 0

```The run gives an error -it says there is a missing quote on the line that says
```
        echo "${i}"

```I have tried adding quotes where they made sense to me, however the issue is not cleared.

There is also an error about an unexpected EOF but I believe fixing the quote thing will fix this other error.

To simplify things, I hard-coded the directory we are working from

```
# for changing the names of directories in the renaming stage.
echo "Before you begin, cd to the directory you are processing"
echo "Enter Ctrl C to abort this action."
echo "Enter the name and relative location of the title file"
read title_file
#echo "Enter the directory location and file name in which"
#echo "  you will be changing directory names."
#echo "Enter the absolute or relative path to this directory."
#echo "  ./  is valid for a relative path to the present working directory."
#read directory
#echo "$directory"
directory="${PWD}/"
echo "$directory"

# Read source directories in array
mapfile -t oldnames < <(find "$directory" -maxdepth 1 -mindepth 1 -type d | sort)
# Read target names in array
mapfile -t newnames < "$title_file"

echo "oldnames: ${#oldnames[@]} : ${oldnames[@]}"
echo "newnames: ${#newnames[@]} : ${newnames[@]}"
directory2="../newNames/"
mkdir "${directory2}"
for i in "${oldnames[@]}"
    do
        h=(i-1)
        echo "$h is i minus one"
        cp ${oldnames[${h}] $directory2${newnames[${h}]
        #echo "${oldnames[${h}] is now ${newnames[${h}]"
        echo "${i}"
    done
exit 0
"../Renamer.sh" 54L, 2043C written 
```

output:

```
lyrasis@LTS-CLOUDCTL-01:~/bin/LyrasisCode/ftp_shush_puppy/Example3$ Renamer.sh
+ echo 'Before you begin, cd to the directory you are processing'
Before you begin, cd to the directory you are processing
+ echo 'Enter Ctrl C to abort this action.'
Enter Ctrl C to abort this action.
+ echo 'Enter the name and relative location of the title file'
Enter the name and relative location of the title file
+ read title_file
newOnes.txt
+ directory=/home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/
+ echo /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/
/home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/
+ mapfile -t oldnames
++ find /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/ -maxdepth 1 -mindepth 1 -type d
++ sort
+ mapfile -t newnames
+ echo 'oldnames: 3 : /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old1' /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old2 /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old3
oldnames: 3 : /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old1 /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old2 /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old3
+ echo 'newnames: 3 : New01' New02 New03
newnames: 3 : New01 New02 New03
+ directory2=../newNames/
/home/lyrasis/bin/Renamer.sh: line 52: unexpected EOF while looking for matching `"'
/home/lyrasis/bin/Renamer.sh: line 55: syntax error: unexpected end of file

```

---

### Post by saphil on 2011-11-14
Now I know I am talking to myself, but the answers are helping, nonetheless.
I found the first error - it is a large helping of curly braces

```

for i in "${oldnames[@][SIZE=4]**}**[/SIZE]"   # **[COLOR=DarkRed]this needs a closing curly bracket[/COLOR]**
     do         
        h="{$i}"
        cp "${oldnames[${h}]**[SIZE=4]}[/SIZE]**" "$directory2${newnames[${h}]**[SIZE=4]}[/SIZE]**"
        echo "${oldnames[${h}]**[SIZE=4]}[/SIZE]**" " is now "  "${newnames[${h}]**[SIZE=4]}[/SIZE]**"
        echo "${i}"
     done 
exit 0
```

It is still complaining about an unexpected EOF. hmm...

---

### Post by ofnuts on 2011-11-14
> **saphil said:**
> Now I know I am talking to myself, but the answers are helping, nonetheless.
I found the first error - it is a large helping of curly braces

```

for i in "${oldnames[@][SIZE=4]**}**[/SIZE]"   # **[COLOR=DarkRed]this needs a closing curly bracket[/COLOR]**
     do         
        h="{$i}"
        cp "${oldnames[${h}]**[SIZE=4]}[/SIZE]**" "$directory2${newnames[${h}]**[SIZE=4]}[/SIZE]**"
        echo "${oldnames[${h}]**[SIZE=4]}[/SIZE]**" " is now "  "${newnames[${h}]**[SIZE=4]}[/SIZE]**"
        echo "${i}"
     done 
exit 0
```It is still complaining about an unexpected EOF. hmm...
In your previous version "h=(i-1)" should really be "h=$(( i-1 ))" I think.

---

### Post by saphil on 2011-11-15
You are right ```
h=$((i-1))
``` gives me an integer answer.   I am glad you could see what I was trying to do.  Maybe renaming the files is as easy as 
```
mv ${oldnames[@]} ${newnames[@]} 
```... OK, it wasn't that simple, however this did work
```

# for changing the names of directories in the renaming stage.
echo "Before you begin, cd to the directory you are processing"
echo "Enter Ctrl C to abort this action."
echo "Enter the name and relative location of the title file"
read title_file

directory="${PWD}/"
echo "$directory"

# Read source directories in array
mapfile -t oldnames < <(find "$directory" -maxdepth 1 -mindepth 1 -type d | sort)
# Read target names in array
mapfile -t newnames < "$title_file"

echo "oldnames: ${#oldnames[@]} : ${oldnames[@]}"
echo "newnames: ${#newnames[@]} : ${newnames[@]}"
directory2="../newNames/"
if [ ! -d "${directory2}" ]; then
    mkdir "${directory2}"
fi
h=0
# is the incrementer for the 'mv' command.  It didn't work to do 'h=$((i-1))' because 'i' was a filename - the content of index[x] - this is the problem to which one of the weird errors was pointing
for i in "${oldnames[@]}"
    do

        #echo "$h is i minus one"
        mv ${oldnames[$h]}  ${directory2}${newnames[$h]}
        echo "${oldnames[$h]} is now ${newnames[$h]}"
        #echo "${i}"
        h=$((h+1))
    done
exit 0

# Output

lyrasis@LTS-CLOUDCTL-01:~/bin/LyrasisCode/ftp_shush_puppy/Example3$ Renamer.sh
Before you begin, cd to the directory you are processing
Enter Ctrl C to abort this action.
Enter the name and relative location of the title file
newOnes.txt
/home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/
oldnames: 3 : /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old1 /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old2 /home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old3
newnames: 3 : New01 New02 New03
/home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old1 is now New01
/home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old2 is now New02
/home/lyrasis/bin/LyrasisCode/ftp_shush_puppy/Example3/Old3 is now New03



```
Thanks so much for your excellent suggestions.  I am going to redirect the echo lines into a log file, so if the list comes to me in the wrong order, for some reason, I know what to do to fix it.

---

### Post by ofnuts on 2011-11-16
> **saphil said:**
> You are right ```
h=$((i-1))
``` gives me an integer answer.
Come to think of it, this isn't even needed. Your loop:
```

h=0
for i in "${oldnames[@]}"
     do
 ....
     h=(($h + 1))
    done
 
```can be coded as:
 ```

for ((h=0;h<${#oldnames[@]};h++)); 
do 
 ....
done

```And while we are at it
```

if [ ! -d "${directory2}" ]; then
    mkdir "${directory2}"

```is better done as:
```
mkdir -p $directory2
```It's also misleading to use $directory1 for something which is by design your current directory. But then at the same time a more Unixish-style command would take a that directory as a parameter.

---

