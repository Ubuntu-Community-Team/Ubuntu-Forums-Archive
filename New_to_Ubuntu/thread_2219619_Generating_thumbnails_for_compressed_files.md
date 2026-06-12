---
title: "Generating thumbnails for compressed files"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by ENigma885 on 2014-04-24
I have a pile of compressed files which contain scanned manga images. It's really hard to find the targeted file when the file names are not distinct enough. 

[SIZE=3]Is there a tool that can generate thumbnails for compressed files, basically .rar and .zip, to be displayed in file browsers namely Nautilus and/or Dolphin?
[/SIZE]

---

### Post by Vaphell on 2014-04-25
no idea if there is a tool for that, but i whipped up a script that uses 7zip and imagemagick

```
sudo apt-get install p7zip-full p7zip-rar imagemagick
```


```
#!/bin/bash

h_size=200
w_size=200

types=( '*.jpg' '*.png' '*.gif' )

# convert options
conv_opt=( -define jpeg:size=$((h_size*2))x$((w_size*2)) "-[${h_size}x${w_size}]" -strip )

for arch in "$@"
do
    echo "processing $arch..."
    pics=()
    while read -r day _ _ _ _ name
    do
        [[ $day = [0-9][0-9][0-9][0-9]-* ]] || continue
        pics+=( "$name" ) 
    done < <( 7z l -r -ssc- "$arch" "${types[@]}" )

    th_dir=${arch}_thumb
    mkdir -p "$th_dir"

    for f in "${pics[@]}"
    do
        echo "generating thumbnail for \`$f'"
        fn=${f##*/}
        7z e  -so "$arch" "$f" 2>/dev/null | convert "${conv_opt[@]}"  "$th_dir"/"${fn%.*}".gif
    done
    echo
done
```

it should create a subdir with thumbnails of a defined size. I tested it on a zip file with pics and some random .cbr (=rar'ed pics) slurped off the net, but it's possible it would work with any format supported by 7z.

when you call script, just feed it archive files to process

---

