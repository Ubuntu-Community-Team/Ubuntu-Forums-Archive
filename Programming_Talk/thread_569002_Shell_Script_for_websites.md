---
title: "Shell Script for websites"
date: 2007-10-06
forum: Programming Talk
---

### Post by Epyonx on 2007-10-06
Hi Ubuntu Users, 

I am a college student. I am trying to make a script that automates a website with the use of my course notes. I just want to upload files somewhere, have them back up and have a  website created out of the files in the directory

I am a Ubuntu user. I am trying to create a script that does the following:
1. Backs up files in a certain directory
2. I want to have the script look thru a directory every day
a. Make a website link on a page that links to the document

This is what I Have so far"

#!/bin/bash
# Author: Me
#Purpose: Back up and website script

# Backup
rysnc /home/pedrop/notes  /backup

#website script   HERE I AM HAVING TROUBLE
# Can I do something like  

<a href=" ( name of file link)">name of notes of that day EG 10042007cst3506</a>
ls > ls.txt

I need to search the directory, go to a page and list all the files and make hyperlinks to the files inside a /var/www/html. I am just no user how to go about it OR if bash can even perform the function.

echo "<a href=" $file">name of file</a> I don't know how to make the concatenate work becuase I have " for the echo command and  then I need the " for html.


Thanks for any help, guidance or links.

A better explanation: I am a college student who takes a lot of classes, I like to type up my notes. I was thinking of a way to organized all my notes into a website with hyperlinks to my notes for each course. I wanted to find a way to check the contents of a directory(which contains all my notes) and create a page with hyperlinks so I can view these notes anywhere on the web. I was thinking that I would have to store all the files in the /var/www/html folder. Then make an HTML page thats gonna hold the links. I need a script thats gonna append to this html page and create hyperlinks. THe name of the hyperlink will reflect the name of the file.

I hope this explains my idea better.

---

### Post by Jussi Kukkonen on 2007-10-06
> 
I need to search the directory, go to a page and list all the files and make hyperlinks to the files inside a /var/www/html. I am just no user how to go about it OR if bash can even perform the function.


You'll need to be more specific about what you want --this is still pretty vague to me.

For the echo problem, try single quotes:```

echo "<a href='${file}'>name of file</a>"
```

---

