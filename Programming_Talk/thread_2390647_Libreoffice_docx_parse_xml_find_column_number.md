---
title: "Libreoffice docx parse xml find column number"
date: 2018-05-01
forum: Programming Talk
---

### Post by Kevin McCready on 2018-05-01
I've been sent a docx file which doesn't open properly.

The error msg is:

File format error found at 
SAXParseException: "No input source"
SAXParseException: '[word/document.xml line 2]: unknown error', Stream 'word/document.xml', Line 2, Column 29965(row,col).

I've tried different builds, including the current one of Libreoffice. They make no difference.

I've tried quite a few different text and stream editors on the xml file (I extracted it from the docx archive with file-roller), but all without success. For example I tried libreoffice --calc but it said there were too many columns.

I would love to be able to find column 29965 in row 2 (the whole xml file presents as only two rows to many readers including I guess libreoffice and Sublime Text). When I load the xml file into firefox it presents as only 4550 rows.

I've attached the file. Please respect the contents by not sharing other than for solving this problem.

Any help would be appreciated.

---

### Post by norobro on 2018-05-01
Not sure that this is what you are looking for, but you can use xmllint to generate an html file. You can then read the html file in your browser.
```
$ xmllint --htmlout document.xml > document.html
```
I'm using chrome and it preserves Chinese characters > Lai Kei Sui (&#40654;&#23696;&#29790;)

---

### Post by Kevin McCready on 2018-05-01
Thanks for that. It was interesting that chromium-browser displayed the Chinese characters. But the problem is still there. I haven't been able to see any wrong formatting in "Column 29965".

Perhaps someone could help me write a little script that reads every < and increments it starting with 1. Then when I get to 29965 I can examine the row (assuming that is how libreoffice parses the xml file).

---

### Post by norobro on 2018-05-01
According to the docs the maximum number of columns in a sheet is 1024.  [https://wiki.documentfoundation.org/Faq/Calc/022](https://wiki.documentfoundation.org/Faq/Calc/022) 

My version of calc (LibreOffice 6.0.4.1 00m0(Build:1)) pops up a dialog containing the following:
> The data could not be loaded completely because the maximum number of columns per sheet was exceeded.


A simple awk script to print all of the fields delimited by '<':  ```
$ awk -F '<' '{for (i=1; i<=NF; ++i) {print i, "<"$i}}' document.xml
```
Don't know where the 29965 comes from as awk only counts 5372 fields in the second line.

---

### Post by Kevin McCready on 2018-05-01
Wow. Thanks for the awk idea. (I've spent the morning beginning to learn C++. It took me hours to give up and try codeblocks. Finally I made a working Hello World program.)

So I should learn awk.

I'm wondering what other delimiter libreoffice may be counting that gives the error message about 29965? Maybe it's the 29965th character in the file (a chinese character or something?). How can I rewrite the awk command to test this?

---

### Post by norobro on 2018-05-01
You can modify it like this:```
$ [FONT=monospace][COLOR=#000000]awk -F '' '{for (i=29960; i<=29970; ++i) {print i, $i}}' docu[/COLOR]ment.xml
[/FONT][FONT=monospace][COLOR=#000000]29960 o[/COLOR]
29961   
29962 <
29963 /
29964 w
29965 :
29966 t
29967 >
29968 <
29969 /
29970 w[/FONT]
```[FONT=monospace]

I would continue with C++. As you probably noticed, the awk syntax is very similar to C/C++ and once you've learned some of the basics of C++ awk will be easy to learn.[/FONT]

---

### Post by Kevin McCready on 2018-05-01
Thanks again for your help.  I was able to do the same but it didn't find the error. I'll change my tack to:
SAXParseException: "No input source". 

Maybe it was looking for another file that makes up the container of a docx file.

---

