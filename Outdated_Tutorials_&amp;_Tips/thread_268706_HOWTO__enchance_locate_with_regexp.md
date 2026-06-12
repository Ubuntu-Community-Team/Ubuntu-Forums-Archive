---
title: "HOWTO : enchance locate with regexp"
date: 2006-09-30
forum: Outdated Tutorials &amp; Tips
---

### Post by grizzly on 2006-09-30
In my opinion the default behaviour of locate is hardly usable this is specially true if one wants to find a directory, or a specific file that happens to share its name with a big directory. If you have used locate you would know what I am talking about.

Anyways here's a lil howto to drastically improve  locate with extremely simple regexp and scripts.

[COLOR="Red"]**SEARCH DIRECTORIES ONLY**[/COLOR]
```
#!/bin/bash

locate -r $1$ | grep $1 --color=always
```
Save this in file 'lo' ; move file in your $PATH ; & give this file permissions with "chmod u+x lo" ; 

Then use the script as :
"[COLOR="YellowGreen"]scriptname directoryname[/COLOR]", and you will get just a list of directories instead of huge incomprehensible list of gazillion files.
This  can also be used to search files by extension (.avi/jpg) as well.  Ex: "[COLOR="YellowGreen"]scriptname mpeg[/COLOR]" to search for mpeg files ( without quotes)

[COLOR="Red"]**SEARCH FOR FILES ONLY && WITHIN A SPECIFIC DIRECTORY!**[/COLOR]

This is my favourite! and dead useful!!```
#!/bin/bash
     
      if [ "$#" == "1" ]
      then
      locate $1 | egrep "$1([^/]+|$)" --color=always
          
      else
      locate $1 | egrep "$1.+?/.+?$2"
     
      fi
```
Again save and give permissions ;
Usage: 
1. FOR SEARCHING IN SPECIFIC DIRECTORY :
[COLOR="YellowGreen"]scriptname script tocd [/COLOR];
where script is the directory you want the search to take place and 'tocd' the file u want to search for. simple!
OR
2. TO SEARCH FOR FILENAME THROUGHOUT SYSTEM:
[COLOR="YellowGreen"]scriptname tocd[/COLOR] : to search for the file 'tocd' on the whole system
Q. Why use this??
A. "locate somefile" search may give 100's of results if  there is a directory with a billion files with the name of 'somefile'.. This thing fixes this behaviour

[COLOR="Red"]**OTHER LOCATE TRICKS**[/COLOR]
er i don't know any so plz do share
1. put the ouput in an array variable! how? er I don't know, sorry!
2.

================================
PROBLEMS:

note that its probable that these are not perfect.. and I know that they can be improved a LOT! but afaik they work as advertised (almost) ;)
If you do find  a problem plz do inform me ( with a solution ;) ) or do suggest improvements

---

