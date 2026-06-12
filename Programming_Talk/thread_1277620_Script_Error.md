---
title: "Script Error"
date: 2009-09-28
forum: Programming Talk
---

### Post by dunryc on 2009-09-28
Hi guys im running a script on my ubuntu box which downloads some pdf files from the guardian web site and uses pdftk to combine them all into one pdf file and saves it in the correct folder on my ebook reader this will be run by cron at 6 in the morning so i can read the paper on the train on the way to work but i keep getting the following error 

Script 

> #!/bin/bash

#download and combine the gaurdians daily g24 pdf's so we get one guardian pdf

cd /media/COOLER/Papers/Guardian
rm *.pdf

TODAY=`date +%Y_%m_%d`
wget -r -l1 -H -t1 -nd -N -np -A.pdf -erobots=off  [http://www.guardian.co.uk/g24](http://www.guardian.co.uk/g24)
pdftk *.pdf cat output guardian
rm *.pdf
rename  /media/COOLER/Papers/Guardian/guardian /media/COOLER/Papers/Guardian/"Gaurdian_$TODAY".pdf

and heres the error im getting 

> FINISHED --2009-09-28 20:09:28--
Downloaded: 33 files, 5.2M in 8.1s (662 KB/s)
Bareword found where operator expected at (eval 1) line 1, near "/media/COOLER"
	(Missing operator before COOLER?)
syntax error at (eval 1) line 1, near "/media/COOLER"

any help would be appreciated 

Thanks in advance dunryc

---

### Post by geirha on 2009-09-28
The error you are seeing is made by the rename command, which renames files using regular expressions, yet you ar using it as if it was the mv command, so I'm guessing you want mv rather than rename.

One more thing, you are not checking the exit status of the cd command. On the very next line you run rm *.pdf, regardless of whether cd managed to change to the directory or not, which means you could be removing the wrong pdf-files if you're unlucky.

So, maybe do something like:
```
cd /media/COOLER/Papers/Guardian || exit
```
which will exit the script if cd fails.

---

