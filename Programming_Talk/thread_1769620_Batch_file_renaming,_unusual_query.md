---
title: "Batch file renaming, unusual query"
date: 2011-05-28
forum: Programming Talk
---

### Post by macroshaft on 2011-05-28
I'm not sure if this is the right place to ask but thought I'd give it a go.

Some time ago I used a terminal command to automatically rename load of zip files to 0000.zip, 0001.zip etc. Now I need to change them back.

They are karaoke tracks, contained in each zip are 2 identically named files, filename.mp3 and filename.cdg.

Can anyone think of a terminal command / script to automatically peek inside the zip, take the file name (song and artist) and then rename the zip to that filename? Otherwise it'll take me weeks as there's thousands of tracks.

Thanks

---

### Post by r-senior on 2011-05-28
As a very rough first thought:

Zipinfo will give you the list of files in the zip, so you could work out the new name for the zip file with something simple like:

```

newname=$(zipinfo -1 0000.zip | grep mp3 | sed -e 's/mp3/zip/g')

```

Then it's just a matter of writing a little script to iterate through the zip files, work out the new name as above and rename (or copy to a new directory).

---

### Post by ziekfiguur on 2011-05-28
You could use something like:
```

zipfile="file.zip"
newname=$(zipinfo -1 ${zipfile} | grep mp3 | sed -e 's/mp3/zip/g')
mv "${zipfile}" "${newname}"

```

I don't know how you did it last time, but you can probably fit this in the code you used then.

---

### Post by r-senior on 2011-05-28
I guess this would do it (WARNING: test it first):

```

#!/bin/bash

mkdir -p renamed

for file in *.zip; do
	newname=$(zipinfo -1 ${file} | grep mp3 | sed -e 's/mp3/zip/g')
	cp -pv "${file}" "renamed/${newname}"
done

```

You'd have to be in the directory containing the zip files and it would make copies under the new name in a 'renamed' directory.

---

### Post by macroshaft on 2011-05-28
This was the command used to rename them as they are now

i=2743; for f in *; do mv "$f" ./$(printf %04d $i).zip; ((i++)); done

---

### Post by macroshaft on 2011-05-28
> **r-senior said:**
> I guess this would do it (WARNING: test it first):

```

#!/bin/bash

mkdir -p renamed

for file in *.zip; do
	newname=$(zipinfo -1 ${file} | grep mp3 | sed -e 's/mp3/zip/g')
	cp -pv "${file}" "renamed/${newname}"
done

```

You'd have to be in the directory containing the zip files and it would make copies under the new name in a 'renamed' directory.

I presume I would just place this in a .sh file?

---

### Post by r-senior on 2011-05-28
That's right. Put it in something like rename_zip.sh and make it executable:

```

chmod +x rename_zip.sh

```

If it's in the directory with the zip files, run it like this:

```

./rename_zip.sh

```

But, do test it (or make backups) first. Please. ;)

---

### Post by macroshaft on 2011-05-28
I'm duplicating the directory as we speak. Will report back soon.

---

### Post by macroshaft on 2011-05-28
It simply produces this error:

```
bash: ./rename.sh: Permission denied
```

---

### Post by macroshaft on 2011-05-28
Ah, got it, but it turns out the tracks are prefixed:

Zoom Karaoke - 2-4-6-8 Motorway - Tom Robinson Band.zip

How would I remove the 'Zoom Karaoke - '?

---

### Post by r-senior on 2011-05-28
Is it always the same prefix? Or do you just need to lose the part up to the first hyphen?

---

### Post by macroshaft on 2011-05-28
> **r-senior said:**
> Is it always the same prefix? Or do you just need to lose the part up to the first hyphen?

They all start the same, since they are all official copies that is how they come from Zoom. But yes, I need to drop everything up to and including the first hyphen and the space after it.

---

### Post by Rany Albeg on 2011-05-28
There is a -c option for unzip to extract file to stdout.
I suspect that the output will show you only a representation of files and not file names themselves.
So just like you do not parse 'ls' output I will not try to parse unzip -c ( I'll just use it here to show you the contents of the zips )
Therefore you can use a temporary directory which will hold the extracted files. Then, grab the first file name in that directory and rename in accordance, repeating this method for all *.zip in PWD.
This is what I did:

```

rany:~/Desktop/foo_dir$ ls
0001.zip  0002.zip
rany:~/Desktop/foo_dir$ unzip -c 0001.zip 
Archive:  0001.zip
 extracting: name1.bar               

 extracting: name1.foo               

rany:~/Desktop/foo_dir$ unzip -c 0002.zip 
Archive:  0002.zip
 extracting: name2.bar               

 extracting: name2.foo               

rany:~/Desktop/foo_dir$ 
rany:~/Desktop/foo_dir$ rename_zips () 
> { 
>     local td=$(mktemp -d) newname i
>     for i in *.zip; do
> 
>         unzip "$i" -d "$td" >/dev/null 2>&1
>         arr=("$td"/*)
>         newname="${arr[0]##*/}"
>         mv -- "$i" "${newname%.*}.zip"
>         rm "${arr[@]}"
>     done
>     rmdir "$td"
> }
rany:~/Desktop/foo_dir$ rename_zips 
rany:~/Desktop/foo_dir$ ls
name1.zip  name2.zip
rany:~/Desktop/foo_dir$
```

Have a nice day.

---

### Post by macroshaft on 2011-05-28
> **Rany Albeg said:**
> There is a -c option for unzip to extract file to stdout.
I suspect that the output will show you only a representation of files and not file names themselves.
So just like you do not parse 'ls' output I will not try to parse unzip -c ( I'll just use it here to show you the contents of the zips )
Therefore you can use a temporary directory which will hold the extracted files. Then, grab the first file name in that directory and rename in accordance, repeating this method for all *.zip in PWD.
This is what I did:

```

rany:~/Desktop/foo_dir$ ls
0001.zip  0002.zip
rany:~/Desktop/foo_dir$ unzip -c 0001.zip 
Archive:  0001.zip
 extracting: name1.bar               

 extracting: name1.foo               

rany:~/Desktop/foo_dir$ unzip -c 0002.zip 
Archive:  0002.zip
 extracting: name2.bar               

 extracting: name2.foo               

rany:~/Desktop/foo_dir$ 
rany:~/Desktop/foo_dir$ rename_zips () 
> { 
>     local td=$(mktemp -d) newname i
>     for i in *.zip; do
> 
>         unzip "$i" -d "$td" >/dev/null 2>&1
>         arr=("$td"/*)
>         newname="${arr[0]##*/}"
>         mv -- "$i" "${newname%.*}.zip"
>         rm "${arr[@]}"
>     done
>     rmdir "$td"
> }
rany:~/Desktop/foo_dir$ rename_zips 
rany:~/Desktop/foo_dir$ ls
name1.zip  name2.zip
rany:~/Desktop/foo_dir$
```

Have a nice day.

I've done that bit now thanks. Now I need to remove the words 'Zoom Karaoke - ' from the beginning of the filenames.

---

### Post by r-senior on 2011-05-28
I think if you replace:

```

newname=$(zipinfo -1 ${file} | grep mp3 | sed -e 's/mp3/zip/g')

```

with

```

newname=$(zipinfo -1 ${file} | grep mp3 | sed -e 's/mp3/zip/g' | sed -e 's/Zoom Karaoke - //g')

```

That should do the trick, i.e. another replace using sed on the filename, but this time replacing "Zoom Karaoke - " with "".

---

### Post by macroshaft on 2011-05-28
> **r-senior said:**
> I think if you replace:

```

newname=$(zipinfo -1 ${file} | grep mp3 | sed -e 's/mp3/zip/g')

```

with

```

newname=$(zipinfo -1 ${file} | grep mp3 | sed -e 's/mp3/zip/g' | sed -e 's/Zoom Karaoke - //g')

```

That should do the trick, i.e. another replace using sed on the filename, but this time replacing "Zoom Karaoke - " with "".

I tried this and it outputs:
```
zipinfo:  cannot find or open Zoom, Zoom.zip or Zoom.ZIP.
```

for every zip file in the directory.

---

### Post by macroshaft on 2011-05-28
I've got it working but for some weird reason the output has no hyphens at all, not even between the artist and title.

Getting there though.

---

### Post by r-senior on 2011-05-28
That's because the script was expecting 0001.zip, etc. You must have a file in the directory now with a space in it. You can clean up and go back to where you started (recommended), or you can adapt the script to deal with filenames with spaces by adding double quotes:

```
newname=$(zipinfo -1 [COLOR="Red"]"${file}"[/COLOR] | grep mp3 | sed -e 's/mp3/zip/g' | sed -e 's/Zoom Karaoke - //g')
```

EDIT: This was in response to post #16

---

### Post by macroshaft on 2011-05-28
> **r-senior said:**
> That's because the script was expecting 0001.zip, etc. You must have a file in the directory now with a space in it. You can clean up and go back to where you started (recommended), or you can adapt the script to deal with filenames with spaces by adding double quotes:

```
newname=$(zipinfo -1 [COLOR="Red"]"${file}"[/COLOR] | grep mp3 | sed -e 's/mp3/zip/g' | sed -e 's/Zoom Karaoke - //g')
```

I got that thanks, it was attempting to run on the now extracted filenames (title - artist). Having run it on the original files it now extracts title artist but with no hyphen between.

---

### Post by r-senior on 2011-05-28
Hmm, not sure why you lose the other hyphens:

```

$ echo "Zoom Karaoke - The Beatles - White Album" | sed -e 's/Zoom Karaoke - //g'
The Beatles - White Album

```

EDIT - I'm a bit rusty with regular expressions, but you could try this for the stripping of the prefix:

```

sed -e 's/^Zoom Karaoke \- //g'

```

---

### Post by macroshaft on 2011-05-28
> **r-senior said:**
> Hmm, not sure why you lose the other hyphens:

```

$ echo "Zoom Karaoke - The Beatles - White Album" | sed -e 's/Zoom Karaoke - //g'
The Beatles - White Album

```

Ah, because out of 2778 files the 2 I chose to test it on don't have hyphens! Isn't that typical.


Thanks to everyone who replied you've all been a great help.

---

### Post by Rany Albeg on 2011-05-28
This is my version, assuming that the contents of the zip files is files names with the prefix 'Zoom Karaoke - '.
It will rename the all zip files in the current directory to the name of the first file in each archive, removing the leading 'Zoom Karaoke - ' that appears at the start of the file name.

```
rename_zips () 
{ 
    local td=$(mktemp -d) newname i
    for i in *.zip;
    do
        unzip "$i" -d "$td" > /dev/null 2>&1
        arr=("$td"/*)
        newname="${arr[0]##*/[COLOR="Red"]Zoom Karaoke - [/COLOR]}"
        mv -- "$i" "${newname%.*}.zip";
        rm "${arr[@]}";
    done;
    rmdir "$td"
}
```

See example above, the red part is the little modification I added to remove the wanted prefix from the file name.

---

### Post by macroshaft on 2011-05-28
One of these days I'll wrap my head round all of this. It's very humbling for someone who has complete mastery of DOS to suddenly find themselves out of their depth i a linux terminal!

---

