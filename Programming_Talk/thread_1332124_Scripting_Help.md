---
title: "Scripting Help"
date: 2009-11-19
forum: Programming Talk
---

### Post by Rrslider on 2009-11-19
I need help with writing a script in ubuntu?
*** Write a script to prompt the user for a directory to list with the long list option.* Pipe the results to a paging filter (in case the listing is long enough to scroll) 

I don't know how to do this I'm lost please help

thanks

Here is a sample script how do I get this script to look like mine?

#!/bin/bash
# Script to make folder for photos
FOLDER=`date +%Y-%m-%d`
YFOLDER=`date +%Y`

# Check if folder already exists and make one if it doesn't
if [ -d ./$YFOLDER ]
then 
echo "Folder ./$YFOLDER already exists"
if [ -d ./$YFOLDER/$FOLDER ]
then
echo "Folder ./$YFOLDER/$FOLDER already exists"
else
mkdir ./$YFOLDER/$FOLDER
fi
else
mkdir $YFOLDER
mkdir $YFOLDER/$FOLDER
fi
exit 0

---

### Post by Rrslider on 2009-11-20
Hi,

I need help with writing a script in ubuntu?
*** Write a script to prompt the user for a directory to list with the long list option.* Pipe the results to a paging filter (in case the listing is long enough to scroll) 

I don't know how to do this I'm lost please help

thanks

Here is a sample script how do I get this script to look like mine?

#!/bin/bash
# Script to make folder for photos
FOLDER=`date +%Y-%m-%d`
YFOLDER=`date +%Y`

# Check if folder already exists and make one if it doesn't
if [ -d ./$YFOLDER ]
then 
echo "Folder ./$YFOLDER already exists"
if [ -d ./$YFOLDER/$FOLDER ]
then
echo "Folder ./$YFOLDER/$FOLDER already exists"
else
mkdir ./$YFOLDER/$FOLDER
fi
else
mkdir $YFOLDER
mkdir $YFOLDER/$FOLDER
fi
exit 0
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8352024") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8352024")

---

### Post by cariboo on 2009-11-20
Please don't double post on the same subject. I have merged your two post into a thread of it's own.

If this is a homework question you may not get any help, as it is against the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") to do someone's homework for them.

---

### Post by Aayu on 2009-11-20
What language(s) do you know/are using?  That script was unlike anything I have seen before..

---

### Post by dwhitney67 on 2009-11-20
> 
*** Write a script to prompt the user for a directory to list with the long list option.* Pipe the results to a paging filter (in case the listing is long enough to scroll)

These are very specific requirements; it must be homework-related.

---

### Post by Aayu on 2009-11-20
In which case, the best way to learn..  is to do it yourself ;)

---

