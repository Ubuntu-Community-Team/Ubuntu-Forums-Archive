---
title: "Grep output issue"
date: 2009-03-05
forum: Programming Talk
---

### Post by kaibob on 2009-03-05
I've encountered an issue that I'm unable to resolve and hoped one of you might be able to help. It's easier for me to give an example than to ask the question in the abstract.

I printed the following page--which is the Ubuntu Forums Code of Conduct--to a PDF document by way of cups-pdf:

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

On my computer, the first line of the first paragraph of the body of the PDF document is:

> By registering and participating in Ubuntu Forums discussions you agree to the following

I tried to use pdftotext and grep to locate and output the above line (and only the above line) with the following command:

```
pdftotext ubuntu.pdf - | grep -m 1 "By registering"
```

Unfortunately, this command outputs text that extends from one line above the seach text to six paragraphs below. I tried the grep context-line-control options but they did not help. I also looked at the man page for the pdftotext utility. The -layout option did work but the output was jumbled with complex PDF documents. The pdftotext utility also has an -eol option but that did not seem to help.

How can I get the above command to output the one line that contains the search text and only that one line?

BTW, I am using this command as part of a shell script to search PDF documents for specified text. I don't believe the script is pertinent, but I have included it below just in case (for now it uses the -layout option). The pdftotext utility is part of the poppler-utils package and may not be installed by default.

Thanks for the help. 

~~~

```
#!/bin/bash

# Search PDF files for a text string and ouput the file names and the
# line that contains the search string to the terminal and a text file.

# Prompt for search location.
echo -n "Enter (h)ome (r)oot (w)estern search location: "
read KEYPRESS

if [ "$KEYPRESS" = "" ] ; then 
echo
echo "You did not make a selection!"
echo
exit 1
elif [ $KEYPRESS = h ] ; then 
SEARCHDIR=/home/bob/
elif [ $KEYPRESS = r ] ; then 
SEARCHDIR="/ -xdev"
elif [ $KEYPRESS = w ] ; then 
SEARCHDIR=/media/WESTERN-EXT3/
else
echo
echo "You did not make a valid selection!"
echo
exit 1
fi

echo

# Prompt for search string.
echo -n "Enter search string: "
read SEARCHTEXT

if [ "$SEARCHTEXT" = "" ] ; then 
echo
echo "You forgot a search string!"
echo
exit 1
fi

# Write search parameters to text file.
if [ $KEYPRESS = r ] ; then
echo "Search location: /" > pdfinto.txt
else echo "Search location: $SEARCHDIR" > pdfinto.txt
fi
echo >> pdfinto.txt
echo "Search string: $SEARCHTEXT" >> pdfinto.txt


echo | tee -a pdfinto.txt

# Search for text and output to terminal and text file.
find $SEARCHDIR -iname *.pdf -type f 2>/dev/null | while read FILE ; do
STRINGMATCH=$(pdftotext -q -layout "$FILE" - | tr -s ' ' | grep -i -m 1 "$SEARCHTEXT")
if [ ! "$STRINGMATCH" == "" ]; then 
echo ~~~ | tee -a pdfinto.txt
echo "$FILE" | tee -a pdfinto.txt
echo "$STRINGMATCH" | tee -a pdfinto.txt
fi
done

echo ~~~ | tee -a pdfinto.txt
```

~~~

grep man page
[http://manpages.ubuntu.com/manpages/hardy/en/man1/grep.1.html](http://manpages.ubuntu.com/manpages/hardy/en/man1/grep.1.html)

pdftotext man page
[http://manpages.ubuntu.com/manpages/hardy/en/man1/pdftotext.1.html](http://manpages.ubuntu.com/manpages/hardy/en/man1/pdftotext.1.html)

---

### Post by croto on 2009-03-05
hi, can you post the text file output of pdftotext so I can reproduce the problem myself?

---

### Post by kaibob on 2009-03-06
> **croto said:**
> hi, can you post the text file output of pdftotext so I can reproduce the problem myself?
croto,

I converted the PDF of the Ubuntu Code of Conduct to text using the following:

```
pdftotext ubuntu.pdf ubuntu.txt
```

I have attached this text file, and it ignores paragraph breaks and divides up the page in ways and for reasons that I do not understand. So, the problem would appear to be with pdftotext and not grep. 

I have been using the pdftotext -layout option, which produces much better output than without this option. I guess my expectations were too high, and I should just be satisfied with what I'm getting with the -layout option. It's far from perfect but is usable in most instances. 

Anyway, thanks for the response and your request, which helped to clarify things for me. 

kaibob

---

