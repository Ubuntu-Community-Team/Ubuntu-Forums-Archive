---
title: "Bash Scripting Question"
date: 2008-11-05
forum: Programming Talk
---

### Post by celian on 2008-11-05
I've recently received a large batch of .mpg's to be converted to a H.264 .mp4 format.

For this purpose I made a script to fetch the relative paths of all mpg's in a designated folder and pass them to my encoder one by one.

> 
#!/bin/bash
# Two-Pass x264 Encoding Script

set -x

# Make Directory
        mkdir H.264

# Search for all "filename".mpg files recursively

        find -name "*.mpg" | while read file;
 do

# Create output filename => ./H.264/filename.mp4

        filename=${file%*.mpg}.mp4
        output=./H.264/${filename##*"/"}

# Pass filename and output filename to encoder

        enc264 $file $output
        echo $file $output >> log

done



For some reason though, the script stops running after the first encoding, but if I remove the "enc264 $file $output" line, replacing it with any other kind of command (ex. "cp $file $output" which works), the script runs just fine and loops through every file on the list..

I've also tried inserting into my main script, the actual code from my "enc264" script, which looks like this:

> #!/bin/bash
# Two-Pass x264 Encoding Script
# Usage: ./264encode.sh input output.mp4

# Pass 1
ffmpeg -y -i $1 -pass 1 -b 512k -bt 512k -s 352x288 -vcodec libx264 -an -threads 0 -coder 1 -flags +loop -cmp +chroma -partitions -parti8x8-parti4x4-partp8x8-partp4x4-partb8x8 -me_method dia -subq 1 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -b_strategy 1 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -refs 1 -directpred 1 -bidir_refine 0 -trellis 0 -flags2 -bpyramid-wpred-mixed_refs-dct8x8+fastpskip -f mp4 /dev/null

# Pass 2
ffmpeg -y -i $1 -pass 2 -b 512k -bt 512k -s 352x288 -vcodec libx264 -acodec libfaac -ab 96k -ac 2 -threads 0 -coder 1 -flags +loop -cmp +chroma -partitions +parti8x8+parti4x4+partp8x8+partb8x8 -me_method umh -subq 8 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -b_strategy 1 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -refs 4 -directpred 3 -trellis 1 -flags2 +bpyramid+wpred+mixed_refs+dct8x8+fastpskip -f mp4 $2

Replacing $1 and $2 with $file and $output, like so:

> 
#!/bin/bash
# Two-Pass x264 Encoding Script

set -x

# Make Directory
        mkdir H.264

# Search for all "filename".mpg files recursively

        find -name "*.mpg" | while read file;
 do

# Create output filename => ./H.264/filename.mp4

        filename=${file%*.mpg}.mp4
        output=./H.264/${filename##*"/"}

# Pass filename and output filename to encoder

# Pass 1
ffmpeg -y -i $file -pass 1 -b 512k -bt 512k -s 352x288 -vcodec libx264 -an -threads 0 -coder 1 -flags +loop -cmp +chroma -partitions -parti8x8-parti4x4-partp8x8-partp4x4-partb8x8 -me_method dia -subq 1 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -b_strategy 1 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -refs 1 -directpred 1 -bidir_refine 0 -trellis 0 -flags2 -bpyramid-wpred-mixed_refs-dct8x8+fastpskip -f mp4 /dev/null

# Pass 2
ffmpeg -y -i $file -pass 2 -b 512k -bt 512k -s 352x288 -vcodec libx264 -acodec libfaac -ab 96k -ac 2 -threads 0 -coder 1 -flags +loop -cmp +chroma -partitions +parti8x8+parti4x4+partp8x8+partb8x8 -me_method umh -subq 8 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -b_strategy 1 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -refs 4 -directpred 3 -trellis 1 -flags2 +bpyramid+wpred+mixed_refs+dct8x8+fastpskip -f mp4 $output

echo $file $output >> log

done



But with the same result, it starts encoding like it should, but then automatically stops after the first file..

Again, replacing the ffmpeg command with another command, will run the script completely through all the files on my list.. It's like using that particular command makes the script jump out after the first item on the list.

Anyone know why this is happening?

---

### Post by geirha on 2008-11-06
Does the filenames (particularily the second, since that seems to cause the problem) contain any odd characters?

Also, your script will not work for files with spaces in them. Make sure to always quote variables with pathnames. In this case "$file" and "$output" instead of $file and $output. Without quotes, the spaces will be treated as argument seperators rather than part of the pathname. If that's the case that makes your script fail though, it should've given you an error message about it. No error messages are printed?

---

### Post by gvartser on 2008-11-07
Try this:
```

#!/bin/bash
#
if [ ! -d ./H.264 ]
then
     mkdir H.264
fi

filename=${file%*.mpg}.mp4
output=./H.264/${filename##*"/"}

(
    find . -name "*.mpg" -exec enc264 {} ${output} \;
) >> logfile.txt
```



/g

---

