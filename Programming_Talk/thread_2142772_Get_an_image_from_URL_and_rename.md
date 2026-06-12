---
title: "Get an image from URL and rename"
date: 2013-05-06
forum: Programming Talk
---

### Post by danielito10 on 2013-05-06
[TABLE]
 	 	 		[TR]
 			[TD="width: 536"]Hello,

I have a large list in excel with 2 columns, column A is a number, ie: 999999. Column B is an URL of an image, ie: [http://www.xyz.com/images/123456.jpg](http://www.xyz.com/images/123456.jpg). 

I need to download the image to my server by ssh and immediately modify it to the number as in column A so the filename that will be stored in my server will be 999999.jpg instead 123456.jpg. Is that possible?

If not, how can I just download multiples images running one command and not copying the URL one by one. ie:

[http://www.xyz.com/images/123457.jpg](http://www.xyz.com/images/123457.jpg)
[http://www.xyz.com/images/123458.jpg](http://www.xyz.com/images/123458.jpg)
[http://www.xyz.com/images/123459.jpg](http://www.xyz.com/images/123459.jpg)
[http://www.xyz.com/images/123450.jpg](http://www.xyz.com/images/123450.jpg)

Thank you!!

Dan.
[/TD]
 		[/TR]
 	 [/TABLE]

---

### Post by ofnuts on 2013-05-06
To download a list of URLs, see "wget -i" or loop over the list and use curl).

---

### Post by danielito10 on 2013-05-06
Thank you for the quick reply.

Sorry I'm new in ssh commands. Can you please tell me an example how to copy the list I have in excel? It should be:

wget -i [http://www.xyz.com/images/123457.jpg](http://www.xyz.com/images/123457.jpg) [http://www.xyz.com/images/123458.jpg](http://www.xyz.com/images/123458.jpg) , etc?

Where should I copy the complete list of URL I have?

Thanks again!!

---

### Post by schragge on 2013-05-06
You should pass [wget -i]("http://www.gnu.org/software/wget/manual/html_node/Logging-and-Input-File-Options.html") a text file containing URLs. Excel and LibreOffice Calc allow exporting data in [CSV]("http://en.wikipedia.org/wiki/Comma-separated_values")-format. Do it, then extract URLs and numbers from CSV with shell's read, cut, sed, awk, perl, or some specialized tools like [csvtool]("http://manpages.ubuntu.com/manpages/raring/en/man1/csvtool.1.html"), [xml2]("http://manpages.ubuntu.com/manpages/raring/en/man1/xml2.1.html"), [ffe]("http://manpages.ubuntu.com/manpages/raring/en/man1/ffe.1.html"). Alternatively to CSV, you may use [TSV]("http://en.wikipedia.org/wiki/Tab-separated_values") if Excel supports it.

---

### Post by Vaphell on 2013-05-06
export your file to CSV format (comma-separated values) and open it in some text editor (eg gedit). You should get something like this:

```
111,"http://www.xyz.com/images/123457.jpg"
222,"http://www.xyz.com/images/123458.jpg"
333,"http://www.xyz.com/images/123459.jpg"
```

this short code should do the trick
```
while IFS=, read -r n url; do url=${url//\"/}; wget $url -O $n.jpg; done < urls.csv
```
this tells bash to read the file urls.csv line by line, use comma to cut it to fields named n and url and use them to construct wget command (wget *url* -O *output_file*)

---

### Post by Valpskott on 2013-05-07
Here's an quick and dirty solution. Mark and copy all the numbers from the first row, and paste it into a file that is "list1.txt" in your ssh session ("nano list1.txt" then press "ctrl + shift + v" to paste, and then "ctrl + o" to save).
Then copy the urls and paste it into a file that is "list2.txt"

Then paste this command into your ssh session. "nano download.sh && chmod +x download.sh" (without the quotes)

While in nano, paste these lines of code.

```

#!/bin/bash
line="1"

if [ ! -e pics ]; then
mkdir pics
fi

while read number
do

url=$(awk "NR==$line" list2.txt)
file=$(echo $url | sed -e 's/.*\///g')

wget $url &>/dev/null

mv $file pics/$number.jpg

line=$(($line + 1))

done < "list1.txt"


```


Save the file with "ctrl + o" (o as in Oscar)

then just type ./download.sh

Voila! All the pictures should now be in a new diretory called "pics" with the names from list1 :)

---

### Post by Vaphell on 2013-05-07
why bother? CSV is supported by any spreadsheet on earth, there is no risk of data misalignment (user can easily make error while copypasting) and a oneliner is way simpler than a dozen lines in a script.

---

### Post by danielito10 on 2013-05-12
Thank you very much to all of you!

---

### Post by rickyhu on 2014-03-18
> **danielito10 said:**
> 
Hello,

I have a large list in excel with 2 columns, column A is a number, ie: 999999. Column B is an URL of an image, ie: [http://www.xyz.com/images/123456.jpg](http://www.xyz.com/images/123456.jpg).

I need to [[COLOR=#272727]download the image from URL[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/download-from-url/") to my server by ssh and immediately modify it to the number as in column A so the filename that will be stored in my server will be 999999.jpg instead 123456.jpg. Is that possible?

If not, how can I just download [[COLOR=#272727]multiples images[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/") running one command and not copying the URL one by one. ie:

[http://www.xyz.com/images/123457.jpg](http://www.xyz.com/images/123457.jpg)
[http://www.xyz.com/images/123458.jpg](http://www.xyz.com/images/123458.jpg)
[http://www.xyz.com/images/123459.jpg](http://www.xyz.com/images/123459.jpg)
[http://www.xyz.com/images/123450.jpg](http://www.xyz.com/images/123450.jpg)

Thank you!!

Dan.


First thank you for posting this question but could you please mark the solution instead of just saying thank you. ;)By the way, my issue is how to rename the image based on Column values. I know how to load image from url and export it into Excel, right now. So your sharing will be a great help for me. Thanks in advance.:P

---

### Post by Vaphell on 2014-03-19
better start new thread instead of hijacking this one, even if the problem is very similar.

---

