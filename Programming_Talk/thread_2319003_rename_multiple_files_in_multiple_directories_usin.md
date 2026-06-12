---
title: "rename multiple files in multiple directories using Bash scripting"
date: 2016-03-31
forum: Programming Talk
---

### Post by alex524 on 2016-03-31
I want to rename multiple files in multiple directories using Bash scripting. 
[COLOR=#222426][FONT=Helvetica Neue]I am using Linux 2.6.32-504.3.3.el6.x86_64. 
[/FONT][/COLOR]I have 772 such directories i.e from Nishi_001 to Nishi_772. [COLOR=#222426][FONT=Helvetica Neue]All of the Nishi directories contained in one parent directory.
[/FONT][/COLOR]Each directory has different number of files in it but in all directories, the naming of the files is similar as follows:


    sample_001samout
    sample_002samout
    sample_003samout
    sample_004samout
    .
    .
    sample_00Nsamout  N=maximum 18


I want to rename the files in each directory to a particular name specific for each directory e.g., for Nishi_001 it contains the following files:


    sample_001samout
    sample_002samout
    sample_003samout


to be renamed to the following format:


    130906_Hiseq3A_l3_017_Dr_Nishikawa_AAGGTACA_L003_R1_001samout
    130906_Hiseq3A_l3_017_Dr_Nishikawa_AAGGTACA_L003_R1_002samout
    130906_Hiseq3A_l3_017_Dr_Nishikawa_AAGGTACA_L003_R1_003samout


The new name is different for each of the 772 directories. I have a file containing a list of the new names e.g


    Nishi_003="130906_Hiseq3B_l7_003_Dr_Nishikawa_ATGCCTAA_L007_R1"
    Nishi_004="130906_Hiseq3B_l7_004_Dr_Nishikawa_AGTGGTCA_L007_R1"
    Nishi_005="130906_Hiseq3B_l7_005_Dr_Nishikawa_ACCACTGT_L007_R1"


All the files in a specific directory will all be renamed with the same name that will identify where the file came from. this new name will replace the phrase "sample" in all the files contained in that specific directory.


for example in the directory Nishi_001 the phrase "sample" in all the files
should be replaced with 


    "130906_Hiseq3A_l3_017_Dr_Nishikawa_AAGGTACA_L003_R1" 


which is the new name specific for Nishi_001 directory

---

### Post by TheFu on 2016-03-31
I'm finding it hard to understand.  Perhaps a simple:
```
old-nameA --> new-nameA 
old-nameB --> new-nameB 

```
would clarify it for me. I dunno.  Seeing the parts that need to change a step at a time would help.

I'd start with **find** and **rename**.  Not too hard, but a little work.  If the parts are too complex, **sed** might be desired too.  I tend to use sed for text *inside* the files.

Also - I wouldn't have **any** spaces in the file/directory names. That makes the scripting a tiny bit more effort to get correct.
So ... post what you've attempted at this point. The effort is important to the learning.

If these are media files, there might be better ways to do it using metadata and tools specifically designed for it - like mp3 tag managers.  May only help lurkers later, but worth a mention.

Lastly, sometimes it is easiest to make a simple, but huge, mv script.  

```
mv old-nameA new-nameA 
mv old-nameB new-nameB 
....
mv old-nameZZZZ new-nameZZZZ

```
Don't under estimate the power of a change-all search and replace inside an editor.

---

### Post by Vaphell on 2016-03-31
the script below sets up a test suite and runs the renaming procedure, according to the criteria

```
#!/bin/bash

# setting up testing data

dataset=.
mkdir -p "$dataset"/Nishi_{001..005}
touch "$dataset"/Nishi_{001..005}/sample_{001..003}samout

# creating the translation file

echo 'Nishi_001="130906_Hiseq3B_l7_001_Dr_Nishikawa_ATGC CTAA_L007_R1"
Nishi_002="130906_Hiseq3B_l7_002_Dr_Nishikawa_AGTG GTCA_L007_R1"
Nishi_003="130906_Hiseq3B_l7_003_Dr_Nishikawa_ATGC CTAA_L007_R1"
Nishi_004="130906_Hiseq3B_l7_004_Dr_Nishikawa_AGTG GTCA_L007_R1"
Nishi_005="130906_Hiseq3B_l7_005_Dr_Nishikawa_ACCA CTGT_L007_R1"' > trans.txt

# ----------------------------------------
# ------- meat starts here  --------------
# ----------------------------------------

trans_file=trans.txt              # file with dir_name -> replacement translation info
dataset=.                                  # root directory of the data source

# setting up the translation info

declare -A trans
while IFS='=' read key value
do
    trans[$key]=${value//\"}
done < "$trans_file" 


# looping over dirs/files and renaming

for d in "$dataset"/*/
do
    key=${d%/}
    key=${key##*/}
    value=${trans[$key]}
    for p in "$d"/*
    do
        f=${p##*/}
        newf=${f/#sample/$value}
        newp=$d/$newf
        mv -v "$p" "$newp"
    done
done
```

output


```
$ ./rename_files.bash
&#8222;./Nishi_001//sample_001samout&#8221; -> &#8222;./Nishi_001//130906_Hiseq3B_l7_001_Dr_Nishikawa_ATGC CTAA_L007_R1_001samout&#8221;
&#8222;./Nishi_001//sample_002samout&#8221; -> &#8222;./Nishi_001//130906_Hiseq3B_l7_001_Dr_Nishikawa_ATGC CTAA_L007_R1_002samout&#8221;
&#8222;./Nishi_001//sample_003samout&#8221; -> &#8222;./Nishi_001//130906_Hiseq3B_l7_001_Dr_Nishikawa_ATGC CTAA_L007_R1_003samout&#8221;
&#8222;./Nishi_002//sample_001samout&#8221; -> &#8222;./Nishi_002//130906_Hiseq3B_l7_002_Dr_Nishikawa_AGTG GTCA_L007_R1_001samout&#8221;
&#8222;./Nishi_002//sample_002samout&#8221; -> &#8222;./Nishi_002//130906_Hiseq3B_l7_002_Dr_Nishikawa_AGTG GTCA_L007_R1_002samout&#8221;
&#8222;./Nishi_002//sample_003samout&#8221; -> &#8222;./Nishi_002//130906_Hiseq3B_l7_002_Dr_Nishikawa_AGTG GTCA_L007_R1_003samout&#8221;
&#8222;./Nishi_003//sample_001samout&#8221; -> &#8222;./Nishi_003//130906_Hiseq3B_l7_003_Dr_Nishikawa_ATGC CTAA_L007_R1_001samout&#8221;
&#8222;./Nishi_003//sample_002samout&#8221; -> &#8222;./Nishi_003//130906_Hiseq3B_l7_003_Dr_Nishikawa_ATGC CTAA_L007_R1_002samout&#8221;
&#8222;./Nishi_003//sample_003samout&#8221; -> &#8222;./Nishi_003//130906_Hiseq3B_l7_003_Dr_Nishikawa_ATGC CTAA_L007_R1_003samout&#8221;
&#8222;./Nishi_004//sample_001samout&#8221; -> &#8222;./Nishi_004//130906_Hiseq3B_l7_004_Dr_Nishikawa_AGTG GTCA_L007_R1_001samout&#8221;
&#8222;./Nishi_004//sample_002samout&#8221; -> &#8222;./Nishi_004//130906_Hiseq3B_l7_004_Dr_Nishikawa_AGTG GTCA_L007_R1_002samout&#8221;
&#8222;./Nishi_004//sample_003samout&#8221; -> &#8222;./Nishi_004//130906_Hiseq3B_l7_004_Dr_Nishikawa_AGTG GTCA_L007_R1_003samout&#8221;
&#8222;./Nishi_005//sample_001samout&#8221; -> &#8222;./Nishi_005//130906_Hiseq3B_l7_005_Dr_Nishikawa_ACCA CTGT_L007_R1_001samout&#8221;
&#8222;./Nishi_005//sample_002samout&#8221; -> &#8222;./Nishi_005//130906_Hiseq3B_l7_005_Dr_Nishikawa_ACCA CTGT_L007_R1_002samout&#8221;
&#8222;./Nishi_005//sample_003samout&#8221; -> &#8222;./Nishi_005//130906_Hiseq3B_l7_005_Dr_Nishikawa_ACCA CTGT_L007_R1_003samout&#8221;
```

test it on the side first.

---

