---
title: "bash formating a text file"
date: 2008-03-15
forum: Programming Talk
---

### Post by dunryc on 2008-03-15
Hi all I've written a bash sript to parse some rss feeds into a text file that will hold the individual links, but I'm having a problem formating it correctly. The file contains links of varying lengths, 

ie 

> 
http://www.test.co.uk/test/main.jhtml?xml=/test/2008/03/09/st_justinepicardie.xml</link><guid


unfortunatly i cannot seem to remove the 

> </link><guid

from the end of each line is there any one liners that can do this ?

thanks dunryc

---

### Post by smartbei on 2008-03-15
Try:

```

sed -i "s/<\/link><guid//" <filename>

```

Replacing filename with the name of the file to be edited.

---

### Post by dunryc on 2008-03-15
thanks for the heads up  smartbei that worked great :-)

---

### Post by dunryc on 2008-03-15
oh dear I'm stuck again sed grep seem so hard to under stand the syntax of these commands  i now have a html file saved on disc with i wish to replace some words in, for example  

> 
src="/arts/graphics/2008/03/01/boenr101.jpg"


to something like 

> 
src="http://www.test.co.uk/arts/graphics/2008/02/24/bomoo124.jpg"


but i cant get sed to handle the quotation mark correctly ! any one had any experience with this ??

---

### Post by stroyan on 2008-03-15
If you want to pass double quotes to sed then the easiest way to quote it in the bash shell is to use single quotes around the argument.
The shell will pass on all double quotes that appear within single quotes.
If you want to use / in your pattern or replacement you can use a different character as the delimiter so / won't need special backslash quoting.
This uses @ as the delimiter.
```
sed 's@src="/@src="http://www.test.co.uk/@' input.html
```

---

### Post by ghostdog74 on 2008-03-15
> **dunryc said:**
> 
but i cant get sed to handle the quotation mark correctly ! any one had any experience with this ??


other ways.
```

 # awk 'BEGIN{OFS=FS="="}{$2="\"http://www.test.co.uk/arts/graphics/2008/02/24/bomoo124.jpg\""}{print}' htmlfile
src="http://www.test.co.uk/arts/graphics/2008/02/24/bomoo124.jpg"

```
or simple bash
```

while read -r line
do
 case $line in 
 "src=") echo 'src="http://www.test.co.uk/arts/graphics/2008/02/24/bomoo124.jpg"'
 esac  
done < "htmlfile"

```

---

### Post by dunryc on 2008-03-16
thanks for the heads up guys ill give it a try later dring the week when i get some time

---

