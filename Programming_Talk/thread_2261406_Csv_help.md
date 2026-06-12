---
title: "Csv help"
date: 2015-01-18
forum: Programming Talk
---

### Post by peter_brickles on 2015-01-18
Need help creating a csv script 

my script takes informaion from a web page and should compile it into a csv file howerver results are not as expected 

heres the script 

> 
#!/bin/bash

#namre of compnay 

echo "Company Name, Address,Number,Email Address " > North_West_Legal.csv


while read line; do
echo "Grabbing all pages for  $line"

curl $line > temp

company=$( cat temp | grep title | head -n1 | sed 's/<title>//g'| sed 's/<\/title>//g'|sed 's/ - The Law Society//g'| sed -e 's/^[ \t]*//'|sed ':a;N;$!ba;s/mark\n//g')
address=$( cat temp | grep -a2 Address | tail -n 1|sed 's/<br\/>//g'|sed 's/,/|/g'| sed -e 's/^[ \t]*//')
number=$( cat temp | grep Tel:|sed 's/^.\{,21\}//'|sed 's/<\/dd>//g'|sed '/^$/d;s/[[:blank:]]//g')
email=$(cat temp | grep -i -o '[A-Z0-9._%+-]\+@[A-Z0-9.-]\+\.[A-Z]\{2,4\}'| head -n 1|sed ':a;N;$!ba;s/mark\n//g')


echo $company,$address,$number,$email >> final.csv 
done < urls
 


i was expecting 

> Woodcocks Haworth &amp; Nuttall  ,West View| Princess Street| Haslingden| Rossendale| Lancashire| BB4 6NW| England ,01706213356 ,stephen.parr@whnsolicitors.co.uk


howver i get results on different lines 

> Woodcocks Haworth &amp; Nuttall  
 ,West View| Princess Street| Haslingden| Rossendale| Lancashire| BB4 6NW| England
,01706213356 
,stephen.parr@whnsolicitors.co.uk



Pulling my hair out with this one now an help would be appreciated

---

### Post by Vaphell on 2015-01-18
use [noparse]```

``` instead of > [/noparse] to post code

also some piece of original input would be nice so one can trace the whole workflow. Btw, you should be using some proper html/xml parser.

---

### Post by schragge on 2015-01-19
You manipulate data one line at a time. Different pieces of information (company name, address, email etc.) are on separate lines in the input file. The sed command sequence
```
sed ':a;N;$!ba;s/mark\n//g'
``` that is probably supposed to remove newlines from the input stream in your script is applied only to the content of the current line and thus useless.

+1 to using proper XML/HTML parser. You may try a combination of [xml2]("http://manpages.ubuntu.com/manpages/trusty/en/man1/xml2.1.html")/html2/2csv, or [ssconvert]("http://manpages.ubuntu.com/manpages/trusty/en/man1/ssconvert.1.html") that comes with gnumeric. I guess, LibreOffice Calc should be able to convert HTML to CSV, too.

---

