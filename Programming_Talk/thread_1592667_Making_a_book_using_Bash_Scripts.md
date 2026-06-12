---
title: "Making a book using Bash Scripts"
date: 2010-10-10
forum: Programming Talk
---

### Post by acreech on 2010-10-10
My son has written several short stories that we typed up and wanted to print in a booklet format. I found this website with instructions on how to make it a booklet 

[HTML]http://ospublish.constantvzw.org/tools/how-to-print-a-booklet-in-16-steps[/HTML]

The instructions work perfectly. So I wanted to automate the process some. My brother and I put together this script, however it has a few issues. 

```
#!/bin/bash

# Check usage
if ($1 == "" || $2 == "" || $1 == "-h" || $1 == "--help") then
   echo " "
   echo " "
   echo "Usage: mkbook name_of_file Number_of_Pages"
   echo "     command: mkbook newbook.pdf 10"
   echo " "
 
fi 
pdftops -paper match $1 1.ps
psbook -s $2 1.ps 2.ps
psnup -2 -PA5 2.ps 3.ps
ps2pdf 3.ps $1_Final.pdf
rm -f  1.ps 2.ps 3.ps
```

When you run this script it returns an error about line 4:

```
/home/acreech/bin/mkbook: line 4: Book_2.pdf: command not found
/home/acreech/bin/mkbook: line 4: 16: command not found
/home/acreech/bin/mkbook: line 4: Book_2.pdf: command not found
/home/acreech/bin/mkbook: line 4: Book_2.pdf: command not found [*] [1]
[2] [15] [14] [3] [4] [13] [12] [5] [6] [11] [10] [7] [8] [9] Wrote 16
pages, 167687 bytes [1] [2] [3] [4] [5] [6] [7] [8] Wrote 8 pages,
174588 bytes 
```

Also is there a way to make the program use the RAM when processing these commands, rather than using the hard drive to process all of this. 

Even with the errors, the script works. I am just trying to fine tune it. 

The last part is printing the book. This script also works, but I need to insert a pause in between the two print commands with some instructions to tell you to reverse the order of the pages and then re-insert them into the printer. Then require a keystroke to continue. something like hit 1 and enter to continue. That way the program know when you are ready to go on. 

I am new to programming and I have been learning python (which my brother does not know), so I have not learned a great deal about bash scripting. 

```
#!/bin/bash

# Check usage
if ($1 == "" || $2 == "" || $1 == "-h" || $1 == "--help") then
   echo " "
   echo " "
   echo "Usage: printbook myprinter filename"
   echo "     command: printbook cm1017 1stbook.pdf"
   echo " "
   exit 1
fi
lpr -P $1 -o page-set=even -#1 $2
lpr -P $1 -o page-set=odd -#1 $2
exit 0
```

The last thing is that the help function on both files does not work correctly. It does not print the information that we have listed under the then part of the loop. 

Thanks for any help with this minor project of mine.

---

### Post by acreech on 2010-10-10
I have got the printing script to run right, with exception to the help section of the loop. 

```

#!/bin/bash

# Check usage
if ($1 == "" || $2 == "" || $1 == "-h" || $1 == "--help") then
   echo " "
   echo " "
   echo "Usage: printbook myprinter filename"
   echo "     command: printbook cm1017 1stbook.pdf"
   echo " "
   exit 1
fi
lpr -P $1 -o page-set=even -#1 $2

echo "Take papers out of the Printer"
echo "Reverse Order of Papers and then re-insert them"
echo "Hit Any Key to Continue"
read
lpr -P $1 -o page-set=odd -#1 $2
echo " "
exit 0


```

---

### Post by acreech on 2010-10-10
I figured them out. so here they are for anyone that might have a use for this type of thing. It will certaintly make things easier for me. 

Save this in the ~/bin as mkbook This script will make a booklet with 8.5X11 paper
```

#!/bin/bash

# Check usage
if [[ $1 == "" || $2 == "" || $1 == "-h" || $1 == "--help" ]]; then
   echo " "
   echo " "
   echo "Usage: mkbook name_of_file Number_of_Pages"
   echo "     command: mkbook newbook.pdf 10"
   echo " "
   exit 1
fi 
mbn=`echo $1 | awk -F. '{print $1}'`
pdftops -paper match $1 1.ps
psbook -s $2 1.ps 2.ps
psnup -2 -PA5 2.ps 3.ps
ps2pdf 3.ps $mbn\_Final.pdf
rm -f  1.ps 2.ps 3.ps
exit 0

```

Save this script in ~/bin as printbook. It will print the book out and let you turn the pages over to print the second side. 

```

#!/bin/bash

# Check usage
if [[ $1 == "" || $2 == "" || $1 == "-h" || $1 == "--help" ]]; then
   echo " "
   echo " "
   echo "Usage: printbook myprinter filename"
   echo "     command: printbook photosmart-7150 1stbook.pdf"
   echo " "
   exit 1
fi
lpr -P $1 -o page-set=even -#1 $2

echo "Take papers out of the Printer"
echo "Reverse Order of Papers and then re-insert them"
echo "Hit Any Key to Continue"
read
lpr -P $1 -o page-set=odd -#1 $2
echo " "
exit 0



```

Enjoy

---

