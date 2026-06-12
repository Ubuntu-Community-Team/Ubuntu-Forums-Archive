---
title: "Extract unique numbers in shell script"
date: 2008-11-18
forum: Programming Talk
---

### Post by kaibob on 2008-11-18
I need to compare one series of numbers with a second series of numbers and extract those numbers that are unique. Is there a way to do this? I will use the unique numbers for the INPAGES variable in the following shell script.

Thanks.

```

#!/bin/bash

# This script removes one or more pages from an existing PDF. 

# Name of PDF file from Nautilus Actions.
PDFNAME="$1"

# Total number of pages in PDF.
LASTPAGE=$(pdfinfo "$PDFNAME" | grep ^Pages | sed 's/Pages:[[:space:]]*//')

# List of all pages in PDF.
ALLPAGES=$(seq $LASTPAGE)

# List of pages to be deleted from PDF. 
OUTPAGES=$(zenity --entry --width=275 --text "Pages to delete")
if [ -z $OUTPAGES ] ; then exit 1 ; fi

# List of pages to be included in PDF. 
INPAGES=???

# Create PDF
pdftk "$PDFNAME" cat $INPAGES output .xxx.pdf
mv -f .xxx.pdf "$PDFNAME"

```

---

### Post by geirha on 2008-11-18
The sort and uniq commands should help on that.
```
$ echo -e '3\n2\n1' > nums1.txt
$ echo -e '2\n3\n4' > nums2.txt
$ sort -u nums1.txt nums2.txt
1
2
3
4

```

---

### Post by kaibob on 2008-11-18
geirha,

Thanks for the response. I did not adequately explain what I was trying to do, but your suggestions got me pointed in the right direction, and the script now works. It's a bit of a kludge and needs cleaning up, but I have copied it below FWIW.

There is one point that still confuses me. The only part of this script that was at all difficult involved extracting the unique numbers. For example, I had one variable that contained a series of numbers (e.g. 1 2 3 4 5), and a second variable that also contained numbers (e.g. 2 4). What I needed to do was create a third variable that contained those numbers in the first variable that are not present in the second variable (1 3 5 in this case). It seems that this could be done without all the temporary text files. 

Anyways, I did this script primarily as a learning experience, so I will continue to play around and refine it.

Thanks again for the help. 

kaibob

```
#!/bin/bash

# This script removes one or more pages from an existing PDF. 

# PDF file and directory from Nautilus Actions.
PDFNAME="$1"
PDFDIRECTORY="$2"

# Change to working directory
cd "$PDFDIRECTORY"

# Total number of pages in PDF.
LASTPAGE=$(pdfinfo "$PDFNAME" | grep ^Pages | sed 's/Pages:[[:space:]]*//')

# Create text file with all pages in PDF.
for PAGES in $(seq $LASTPAGE) ; do
echo "$PAGES" >> allpages.txt
PAGES=$((${PAGES} + 1))
done

# Get pages to be deleted from PDF. 
OUTPAGES=$(zenity --entry --width=275 --text "Pages to delete")
if [ -z $OUTPAGES ] ; then exit 1 ; fi

# Create text file with pages to be deleted from PDF.
echo -e ${OUTPAGES// /'\n'} > outpages.txt

# Create text file with pages to be retained in PDF.
sort -n allpages.txt outpages.txt | uniq -u > inpages.txt

# Create variable with pages from to be retained in PDF. 
INPAGES=$(cat inpages.txt)

# Create PDF
pdftk "$PDFNAME" cat $INPAGES output .xxx.pdf
mv -f .xxx.pdf "$PDFNAME"
```

---

### Post by geirha on 2008-11-18
Ah, I see. You can simplify that by using bash arrays. Consider this:

```

allpages=( $(seq 5) )          # Creates array [1,2,3,4,5] (indices start with 0)
outpages=( 2 4 )        

for page in "${outpages[@]}"; do
  # Unset the element correspoding to that $page.
  unset allpages[$page-1]       
  # The indeces are not shifted by removing elements.
done

inpages=( "${allpages[@]}" )   # Copy all elements that are not unset from $allpages
echo ${inpages[@]}             # 1 3 5

```

---

### Post by ghostdog74 on 2008-11-18
> **kaibob said:**
>  For example, I had one variable that contained a series of numbers (e.g. 1 2 3 4 5), and a second variable that also contained numbers (e.g. 2 4). What I needed to do was create a third variable that contained those numbers in the first variable that are not present in the second variable (1 3 5 in this case). 

```

#!/bin/bash
a="1 2 3 4 5"
b="2 4"
awk -v a="$a" -v b="$b" 'BEGIN{ 
 m=split(a,ar1," ")
 n=split(b,ar2," ")
 for( i in ar1){
    if (!(ar1[i] in ar2) ) {
            print ar1[i]
    }
 } 
}'

```
output:
```

# ./test.sh
4
5
3

```

---

### Post by kaibob on 2008-11-18
geirha,

Thanks for the help. I plugged the array code into my script and it works great. The script is much cleaner and executes faster.

I know nothing about arrays but will make that my new item to learn. They seem to be quite useful. 

Thanks again,

kaibob

```
#!/bin/bash

# Delete pages from PDF document.
# For use with Nautilus Actions.
# Nautilus Actions parameters: %f %d.

# Get PDF and directory names.
pdfname="$1"
pdfdirectory="$2"

# Change to working directory.
cd "$pdfdirectory"

# Obtain total number of pages in PDF.
lastpage=$(pdfinfo "$pdfname" | grep ^Pages | sed 's/Pages:[[:space:]]*//')

# Prompt for pages to be deleted from PDF. 
deletepages=$(zenity --entry --width=275 --text "Pages to delete ")
if [ -z $deletepages ] ; then exit 1 ; fi

# Create array variables.
allpages=( $(seq ${lastpage}) )
outpages=( $deletepages )

# Unset pages to be deleted.
for page in "${outpages[@]}"; do
unset allpages[$page-1]       
done

# Create array variable with pages to be retained.
inpages=( "${allpages[@]}" )   

# Delete pages from PDF.
pdftk "$pdfname" cat ${inpages[@]} output .xxx.pdf
mv -f .xxx.pdf "$pdfname"
```

---

### Post by slavik on 2008-11-18
man uniq

---

### Post by kaibob on 2008-11-18
@ghostdog74. Thanks for the reply. I wondered if awk might do what I want, but I have trouble with simple shell scripts and figured awk was beyond my abilities right now. I will look into awk using your post as a learning tool. 

@slavik. When I first began this last night, I thought uniq would be a simple answer, but I couldn't get it to work except in conjunction with sort and the text files made in my earlier script. I'm new to this and perhaps just did something wrong. But, thanks anyway.

---

### Post by slavik on 2008-11-18
yeah, uniq looks at adjacent lines (it does a one pass thing) so it does have to be used with sort.

---

