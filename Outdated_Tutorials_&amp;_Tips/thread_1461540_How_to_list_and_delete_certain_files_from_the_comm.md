---
title: "How to list and delete certain files from the command line"
date: 2010-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Malac on 2010-04-24
Thought I'd post this as I searched for hours finding a working "safe" solution to this problem.
 
This process is in two parts;
1st command:```
**[COLOR=red]sudo[/COLOR]** find [COLOR=green]**/home**[/COLOR] -type [COLOR=blue]**f**[/COLOR] -name "**[COLOR=purple]*~[/COLOR]**" -exec ls -fQ {} \; > **rmlist.txt**
```The **[COLOR=red]sudo[/COLOR]** is to make sure we don't get any access denied errors.
The [COLOR=green]**/home**[/COLOR] is the path we want to search within.
The [COLOR=blue]**f**[/COLOR] is the type in this case files (see "man find" for other types, d is directory)
The **[COLOR=purple]*~[/COLOR]** is the file mask we are looking for. In this case files ending in ~ character or backups.
These are listed to a file, **rmlist.txt**, for later removal using the ls command. The -fQ options here tell ls to not sort and place the results in quotes(this allows for filenames and directories with spaces in their name).
I like to review this file to make sure no "strays" have got in.
 
2nd Command:```
**[COLOR=red]sudo[/COLOR]** xargs rm -v < **rmlist.txt**
```This does the actual deleting;
Again the **[COLOR=red]sudo[/COLOR]** is used to make sure we don't get any access denied errors.
xargs is used to parse the file and pass the contents a line at a time to rm.
The -v option is used here to show files being deleted. You can omit this if you wish.
 
 
[COLOR=red]**WARNING**[/COLOR]:
This next command will not produce a file and will do the deleting [COLOR=red]**without any checks whatsoever**[/COLOR] and should only be used if you know what you are doing.
**USE WITH CAUTION!**```
**[COLOR=red]sudo[/COLOR]** find [COLOR=green]**/home**[/COLOR] -type [COLOR=blue]**f**[/COLOR] -name "**[COLOR=purple]*~[/COLOR]**" -exec rm -f {} \;
```**SLIGHTLY SAFER**
If you would like prompting on each file with this command change it to:```
**[COLOR=red]sudo[/COLOR]** find [COLOR=green]**/home**[/COLOR] -type [COLOR=blue]**f**[/COLOR] -name "**[COLOR=purple]*~[/COLOR]**" -exec rm -f[COLOR=DarkGreen]**i**[/COLOR] {} \;
``` This will prompt with a question for each file just enter **y** or **n** for yes or no.

And that's it.
Hope this helps.

---

