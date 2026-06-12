---
title: "sed script files not playing nicely!"
date: 2010-06-29
forum: Programming Talk
---

### Post by thaitang on 2010-06-29
I am having a lot of trouble, wasting a lot of time trying to get sed script files to run without problem. I have a list of scripts I want to run on a text file to turn it into a viewable html file for my mobile phone. Each of the single scripts when run in order/sequence one after another on the command line work fine. I end up with the file I want to view on my phone's browser. Then I put the sed scripts into a file enclosed in curly brackets (top and bottom as expected) without anoything other than the actual sed script (no sed command, no sed options, no surrounding quotes around the sed script). When I apply this file to a text file, the same file I applied all of the scripts one at a time on the command line and worked fine, the scripts do not all seem to get applied.

Perhaps I am wrong in my assumption that sed works line by line and makes changes before moving to the next line until the end of the file is reached, afterwhich the next sed script is read and sequentially applied to each of the lines in the text file, in which some of the lines have been altered by the previous sed script in the script file? If that is not the case then that must be where I am getting hung up assuming some lines in the text file to be altered from previous sed scripts in the script file.

This problem is enough to drive me to drink. Some script lines seem to run while other just do nothing, unless of course run one at a time from the command line. 


As an example, here is a chunk from the script file I am trying to apply to text files:

```
#reformat line numbers onto their own lines and delete all lines not ending with a zero or five
    s/^.*[1-4]   \(.*\)$/\1/g
    s/^.*[6-9]   \(.*\)$/\1/g
#    s/^\([0-9]*\)   \([A-Za-z']\)/<tr><td>\1<\/td><\/tr>\n\2/g
    s/^\([0-9]*\)   \([A-Za-z']\)/\1\n\2/g
            
#HTML TAG SECTION
    s/^\(25\)$/<tr><td><a href="#\1Top" name="\1"><u><b>\1<\/b><\/u><\/a><\/td><\/tr>/g
```After filtering out all line numbers other than ones ending with zero or five, and put them onto their lines (which all works fine from applying the script file) then the first sed script that follows to enclose applicable HTML tags and make the line number 25 a hyperlinked reference (for easy navigation while being viewed on my phone) does not get applied. 

However, if I run this line:

```
$ sed -i 's/^\(25\)$/<tr><td><a href="#\1Top" name="\1"><u><b>\1<\/b><\/u><\/a><\/td><\/tr>/g' textFile.txt
```the line that starts and ends with the number 25 gets the HTML tags applied as desired.

If anyone can help me out and show me the error of my ways with using sed script files (my commands all work fine on their own) you might just help save my liver in time!

cheers,
tt

---

### Post by DaithiF on 2010-06-29
Hi,
the problem is that sed doesn't work the way you think it does when you insert newlines.

To try to illustrate: 
If you have a line:
25 hello
and you apply a sed replace expression to add a newline after the line number:
sed 's/\([0-9]*\) /\1\n/'

You might think that you then have 2 lines:
25
hello
and that you could therefore match  /^25$/ and do something with that line, 
but in fact, you have a single 'line' in sed's pattern space, which looks like this:
25\nhello
and so to match the 25, you would need to do:
/^25\n/

hope that makes sense

---

### Post by thaitang on 2010-06-29
> **DaithiF said:**
> Hi,
the problem is that sed doesn't work the way you think it does when you insert newlines.

To try to illustrate: 
If you have a line:
25 hello
and you apply a sed replace expression to add a newline after the line number:
sed 's/\([0-9]*\) /\1\n/'

You might think that you then have 2 lines:
25
hello
and that you could therefore match  /^25$/ and do something with that line, 
but in fact, you have a single 'line' in sed's pattern space, which looks like this:
25\nhello
and so to match the 25, you would need to do:
/^25\n/

hope that makes sense
Well that is awesome! That was exactly what my problem was: thinking the changes sed makes are dynamic and happen after each line is processed. 

I have so many problems applying long sed script files, usually having to hack around to get them to work. I am certain this little nugget of knowledge will alleviate a lot of those headaches.

Thanks a million for answering the question asked and not suggesting better tools, that I know exist, with which to get the job done :)

Muchos appreciated!
tt

---

