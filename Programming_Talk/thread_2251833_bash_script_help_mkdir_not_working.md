---
title: "bash script help mkdir not working?"
date: 2014-11-07
forum: Programming Talk
---

### Post by einstein**-7 on 2014-11-07
Just having problems with a simple bash script below that converts a sequence of dng files to exr... mkdir is not working??
Script below and errors.

 	

 	```
#!/bin/bash
#export TMPDIR=/media/......
for file in *.dng ; do
mkdir './Out/'$file'/'
/dng2exr $file './Out/'$file'/'
mkdir './Out/'$file'/EXR'
   for out in "./Out/$file/*.dng" ; do
      dcraw -c -w -H 1 -o 5 -q 3 -4 $out | convert - -depth 16 "./Out/$file/EXR/%06d.exr"
   done
done 
 	

``` 	

```


crush@crushmob:~/Videos$ dng2exr
mkdir: cannot create directory ‘./Out/Camera_1_2014-11-05_1746_C0000_000000.dng/’: No such file or directory
/usr/bin/dng2exr: line 5: /dng2exr: No such file or directory
mkdir: cannot create directory ‘./Out/Camera_1_2014-11-05_1746_C0000_000000.dng/EXR’: No such file or directory 

```

I understand what the "mkdir" line do but not sure what this line  is doing??

 ```

/dng2exr $file './Out/'$file'/' 

```

---

### Post by steeldriver on 2014-11-07
If the ./Out directory does not already exist, mkdir will not create the subdirectory ./Out/$file unless you add the -p option

```

       -p, --parents
              make parent directories as needed

```

Note that 

```

/dng2exr

```

specifies a file in the filesystem root directory - which is almost certainly NOT where the dng2exr command lives. If dng2exr is in a standard location that is on your PATH, you probably want to use 

```

dng2exr

```

without the leading /. The trailing '/' in 

```

'./Out/'$file'/'

```

is not necessary but you can do it if you really want. FWIW most people would use a different style of quoting

```

"./Out/$file/"

```

(the "..." double quotes allow $file to be expanded by the shell).

---

### Post by ofnuts on 2014-11-07
> **steeldriver said:**
> Note that 

```

/dng2exr

```

specifies a file in the filesystem root directory - which is almost certainly NOT where the dng2exr command lives. If dng2exr is in a standard location that is on your PATH, you probably want to use 

```

dng2exr

```

without the leading /

I'm wondering is this could be a confusion with the use of a backslash prefix to short-circuit command aliases...

---

### Post by Vaphell on 2014-11-07
OP, don't overcomplicate the path composition, just cram everything in double quotes, like steeldriver said. Your way of doing things is prone to whitespace related accidents (unquoted variables are bad for business generally)


yet another problem is that this is not really going to work

```
for out in "./Out/$file/*.dng"
```

wildcard symbols cannot be hidden from the shell inside quoted strings, bash has to see that * in order to perform matching. With fully quoted form bash will look for a file literally named  '*.dng'

```
for out in "./Out/$file"/*.dng
```

---

### Post by einstein**-7 on 2014-11-09
> **steeldriver said:**
> If the ./Out directory does not already exist, mkdir will not create the subdirectory ./Out/$file unless you add the -p option

```

       -p, --parents
              make parent directories as needed

```

Note that 

```

/dng2exr

```

specifies a file in the filesystem root directory - which is almost certainly NOT where the dng2exr command lives. If dng2exr is in a standard location that is on your PATH, you probably want to use 

```

dng2exr

```

without the leading /. The trailing '/' in 

```

'./Out/'$file'/'

```

is not necessary but you can do it if you really want. FWIW most people would use a different style of quoting

```

"./Out/$file/"

```

(the "..." double quotes allow $file to be expanded by the shell).

Didn't actually code this just coppied from the net.
OK ! turns out the /dng2exr line which i changed accidentally was originally /raw2dng which was a program I don't need anyway because I already have .dng's..
Below is the new script that works but i would like to copy the .dng files from the $file which is actually a folder to the new ./Out/$file/ dirrectory and then process the copies but the second script below which is my attempt doesn't seem to work? 

```
#!/bin/bash
#export TMPDIR=/media/......
for file in *.dng ; do
mkdir -p "./Out/$file/"
#   for dng in "$file/" ; do
cp $file "./Out/$file/"
#   done

mkdir "./Out/$file/EXR"
   for out in "./Out/$file"/*.dng ; do
      dcraw -c -H 1 -o 0 -q 3 -4 $out | convert - -depth 16 "./Out/$file/EXR/%06d.exr"
   done
done
```

```
#!/bin/bash
#export TMPDIR=/media/......
for file in *_C* ; do
mkdir -p "./Out/$file/"
   for dng in "$file/" ; do
      cp $dng "./Out/$file/"
   done

mkdir "./Out/$file/EXR"
   for out in "./Out/$file"/*.dng ; do
      dcraw -c -H 1 -o 0 -q 3 -4 $out | convert - -depth 16 "./Out/$file/EXR/%06d.exr"
   done
done
```

thanks in advance!

---

### Post by einstein**-7 on 2014-11-09
Oh, and forgot to mention running the first version of the script above on the .dng files dirrectly I had to delete part of the file names because they contain multiple spaces and it didn't like this.. Also the folder with the dng's that  $file   points to contains spaces in the name so maybe thats causing problems?
below is the result of running the second script on the folder with spaces in the file name removed but the dng's inside still have spaces.


```
crush@crushmob:~/Videos$ dng2exr
cp: omitting directory ‘Camera_1_2014-11-05_1746_C0000/’
./Out/Camera_1_2014-11-05_1746_C0000/*.dng: No such file or directory
convert.im6: no decode delegate for this image format `/tmp/magick-GpvvSKxH' @ error/constitute.c/ReadImage/544.
convert.im6: no images defined `./Out/Camera_1_2014-11-05_1746_C0000/EXR/%06d.exr' @ error/convert.c/ConvertImageCommand/3044.
```

---

### Post by steeldriver on 2014-11-10
```

for dng in "$file/" ; do

```

isn't going to iterate over anything ($file expands to a single word)

I suggest you start over - explain exactly WHAT you want to do, and we will help you write the script. There are ways to make it handle filenames with spaces properly.

---

### Post by einstein**-7 on 2014-11-10
Alright, 
1: I would like to iterate over a list of folders that contain multiple spaces and all end in _C and create a new directory in ./ called " "converted" with each folder copied there and a sub folder called "exr"  eg.. ./converted/copied folder/exr.
2:  then iterate over the list of dng files (also containing spaces in the filename) within each folder copied in step 1 eg.  ./converted/"folder name"/" dng's inside" ... and output the results of the image conversion program to the "exr" subfolder.

---

### Post by Vaphell on 2014-11-10
in case of data with possible whitespace, double quotes are a must, otherwise you get hit by word splitting (imo this feature should be done away with because it was needed in ancient shells but other than that it only causes bugzorz). As long as you keep your filename/path variables in "" everywhere you are golden.

```

cp [COLOR="#FF0000"]$dng[/COLOR] "./Out/$file/"

dcraw -c -H 1 -o 0 -q 3 -4 [COLOR="#FF0000"]$out[/COLOR]
```
let's say you have a file 'abc def.dng'. Unquoted var will expand to [COLOR="#0000CD"]abc[/COLOR] [COLOR="#006400"]def.dng[/COLOR], 2 'words'.

```

for d in *_C
do
    [[ -d $d ]] || continue
    mkdir -p "converted/$d/exr"
    cp -t "converted/$d" "$d"/*.dng
    for dng in "converted/$d"/*.dng
    do
        dcraw -c -H 1 -o 0 -q 3 -4 "$dng" | convert - -depth 16 "./converted/$d/exr/%06d.exr"
    done
done
```

---

### Post by einstein**-7 on 2014-11-10
> **Vaphell said:**
> in case of data with possible whitespace, double quotes are a must, otherwise you get hit by word splitting (imo this feature should be done away with because it was needed in ancient shells but other than that it only causes bugzorz). As long as you keep your filename/path variables in "" everywhere you are golden.

```

cp [COLOR=#FF0000]$dng[/COLOR] "./Out/$file/"

dcraw -c -H 1 -o 0 -q 3 -4 [COLOR=#FF0000]$out[/COLOR]
```
let's say you have a file 'abc def.dng'. Unquoted var will expand to [COLOR=#0000CD]abc[/COLOR] [COLOR=#006400]def.dng[/COLOR], 2 'words'.

```

for d in *_C
do
    [[ -d $d ]] || continue
    mkdir -p "converted/$d/exr"
    cp -t "converted/$d" "$d"/*.dng
    for dng in "converted/$d"/*.dng
    do
        dcraw -c -H 1 -o 0 -q 3 -4 "$dng" | convert - -depth 16 "./converted/$d/exr/%06d.exr"
    done
done
```

Tried your code and everything works great except it only creates one .exr file in the exr folder so i trid with an echo command in the "" for dng "" loop and all the correct names of the dng files roll through but no output except first?  ...sigh  Tried this below on filenames with no spaces to be sure it wasnt causing problems with the dcraw or convert programs and same result which is really bugging me because i had something similar to this working at the start just fine -- I had just renamed a handful of dng files to remove the spaces and it would simply output the exr's ...:mad:

```
mkdir "./EXR"
for dng in *.dng
   do
   echo $dng
   dcraw -c -w -H 1 -o 5 -q 3 -4 $dng | convert - -depth 16 ./EXR/%06d.exr
done

```

---

### Post by Vaphell on 2014-11-11
the spaces have nothing to do with it. The question is what that %06d at the end is supposed to do. It looks like an attempt to create a 6 digit wide, 0-padded number but without knowing details what number should that be and *convert* capabilities i can't say what you are expecting to get on the other end.

```
dcraw -c -w -H 1 -o 5 -q 3 -4 "$dng" | convert - -depth 16 ./EXR/"${dng%.*}".exr
```

maybe something like this is what you want, use the same name but change the extension. This should yield an output file for each input file.

---

### Post by einstein**-7 on 2014-11-11
> **Vaphell said:**
> the spaces have nothing to do with it. The question is what that %06d at the end is supposed to do. It looks like an attempt to create a 6 digit wide, 0-padded number but without knowing details what number should that be and *convert* capabilities i can't say what you are expecting to get on the other end.

```
dcraw -c -w -H 1 -o 5 -q 3 -4 "$dng" | convert - -depth 16 ./EXR/"${dng%.*}".exr
```

maybe something like this is what you want, use the same name but change the extension. This should yield an output file for each input file.

Yea came to the same conclusion when i realized that the script was still running even after the first file was visible. I just added a counter and did something like...

```
"./converted/$d/exr/fr%06d$Count.exr"
```

which just outputs the frames as  *fr0000001* or whatever the counter is at currently..  Only problem left is that the length of the file suffix changes when the counter reaches 10, 100 etc how would i format it so that the suffix is the same length number regardless of the counter value?  this messes with the program I am trying to import to as it expects uniform number strings.

---

### Post by Vaphell on 2014-11-12
you can use *printf* for that

example:

```
$ i=1; for x in {a..f}; do **printf -v idx '%06d' $((i++))**; echo "${x}_${idx}"; done
a_000001
b_000002
c_000003
d_000004
e_000005
f_000006
```

i is the counter here, starting from 1, incremented by 1 on every iteration.
the bolded part formats the value of $i to a 0-padded 6 digit wide format and puts the result in $idx variable.

---

### Post by einstein**-7 on 2014-11-13
> **Vaphell said:**
> you can use *printf* for that

example:

```
$ i=1; for x in {a..f}; do **printf -v idx '%06d' $((i++))**; echo "${x}_${idx}"; done
a_000001
b_000002
c_000003
d_000004
e_000005
f_000006
```

i is the counter here, starting from 1, incremented by 1 on every iteration.
the bolded part formats the value of $i to a 0-padded 6 digit wide format and puts the result in $idx variable.

Nice !! popped this in there and all is working great now!  Thanks to *steeldriver *and [I]Vaphell for all the help ! all others thanks as well !
[/I]

---

