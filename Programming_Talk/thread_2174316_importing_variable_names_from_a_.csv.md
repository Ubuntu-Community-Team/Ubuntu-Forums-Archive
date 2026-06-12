---
title: "importing variable names from a .csv"
date: 2013-09-13
forum: Programming Talk
---

### Post by ben21 on 2013-09-13
Thanks in advance!  I'm trying to set up a batch processing script in bash.  I'm running several programs on specific pairs of stereo images to create a single 3D image.  There are about twenty pairs of images.  I'd like to have all the image names in a single directory, and setup a csv file that has the specific pairs of images in the same row.  The batch processing script would need to identify the two image names in the first row of the csv, process them, and then move on to the two image names in row 2.  

My question then, is is there a command to import the value at a specific coordinate in a csv?  For example, something like:

IMAGE1= imagepairs.csv(1,1)
IMAGE2=imagepairs.csv(2,1)

stereoprocess IMAGE1 IMAGE2 output-processedimage1, and then rename the variables as the next pair of images:

IMAGE1=imagepairs.csv(1,2)
IMAGE2=imagepairs.csv(2,2)

stereoprocess IMAGE1 IMAGE2 output-processedimage2

I hope this is clear, and thanks again.
Ben

---

### Post by sisco311 on 2013-09-13
Hi ben21,

and welcome to the forums.

Check out BashFAQ 001 (link in my signature) especially the /etc/passwd example. ;)


 Assuming that the c from CVS stands for comma (`,'), I think you want to do something like:
```
while IFS=, read -r file1 file2
do
    process "$file1" "$file2"
done < "$cvsfile"
```

---

