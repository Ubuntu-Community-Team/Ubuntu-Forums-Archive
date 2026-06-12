---
title: "batch file .sh; does not work on filenames with space in"
date: 2012-10-16
forum: Programming Talk
---

### Post by then_dude on 2012-10-16
Hello everybody,  i have made my first batch file :-)  but it does not work since there are spaces in my filenames, how to resolve this ? 
 thanks

 ps: the batchfile contains a print command. (to print double sided, and 2 pages per printed page.

 for file in *.pdf do   lp -o media=a4 -o sides=two-sided-long-edge -o number-up=2 $file.pdf done

---

### Post by SlugSlug on 2012-10-16
```
for FILE in *.pdf do   lp -o media=a4 -o sides=two-sided-long-edge -o number-up=2 `$FILE` done
```


Does that work?

---

### Post by steeldriver on 2012-10-16
Try quoting the variable

```
"$file"
```(I don't think you need $file**.pdf** since the name includes the .pdf extension unless you explicitly remove it)

```
for file in *.pdf; do   lp -o media=a4 -o sides=two-sided-long-edge -o number-up=2 "$file"; done
```I would recommend NOT using uppercase for your local variable names - it is bad practice (they should be reserved for system vars)

---

### Post by then_dude on 2012-10-16
thanks so much, that was the problem. 

just great. 

i have also found another batch file i would like to change a bit. 

it checks if the files are even or oneven, i would like to add an extra page to the oneven files. How do i do it. I know you can pdftk file_oneven with a blanc page but i don't know the syntaxs how to do it in a batch. 
thanks a lot


#!/bin/bash 
for file in *.pdf
do
  #get the number of pages
  numberofpages=`pdftk "$file" dump_data | sed -e '/NumberOfPages/!d;s/NumberOfPages: //'`
  echo -n "$file" 'has' $numberofpages 'pages, '
  uneven=$(($numberofpages % 2))
  if [ $uneven == 1 ]
  then 
    echo 'which is uneven'
  else
    echo 'which is even'
  fi
done

---

### Post by Vaphell on 2012-10-16
```
[/****code] tags are your friend
try this
[code]#!/bin/bash
for file in *.pdf
do
  #get the number of pages
  numberofpages=$( pdftk "$file" dump_data | awk '/NumberOfPages/{ print $2 }' )

  if (( numberofpages%2 ))
  then
    echo "odd number of pages"
    pdftk A="$file" B=**blank.file** cat **A1 B1 A2-end** output temp_file
    mv temp_file "$file"
  fi
done
```
*A1 B1 A2-end* describes the order, 1st page from A, 1st page from B, then A from 2nd to the end. Obviously you need to define the order you need. You also need empty pdf to act as filler (but avoid pdf extension, otherwise it will be merged with itself thanks to ***.pdf**).
Test if pdftk allows overwriting input files in place (edit: it doesn't). Run the script on some dummy files first to see if it works correctly.

---

### Post by then_dude on 2012-10-16
thanks a lot, that's works just perfectly. 
Great catch with the mv command at the end.

does someone knows a great tutorial about batch programming ? 

thanks

---

### Post by Lars Noodén on 2012-10-16
> **then_dude said:**
> does someone knows a great tutorial about batch programming ? 



It's called shell scripting these days, batch jobs are from the old mainframe days.  There are lots of tutorials and howtos around the net.  If you search a little you will find one targeted towards you interests and level.  

Probably one good place to start would be this one:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

and this one

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by drmrgd on 2012-10-16
I also really like Greg's Wiki.  I've especially learned a lot by consulting his Bash Pitfalls section:

[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)

---

### Post by then_dude on 2012-10-22
thanks guys,

i have looked a bit at the links. one of them is 864 pages :twisted; 

if somebody has a link to a document that i can print. cause i tend to read these things on the train... and is not 864 pages long...

if i find one i will post it. 
thanks again

---

### Post by sisco311 on 2012-10-22
You can download the Bash Guide @ Greg's Wiki in PDF format:
[http://stuff.lhunath.com/BashGuide.pdf](http://stuff.lhunath.com/BashGuide.pdf)

---

