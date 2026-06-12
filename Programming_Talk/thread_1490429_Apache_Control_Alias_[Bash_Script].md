---
title: "Apache Control Alias [Bash Script]"
date: 2010-05-22
forum: Programming Talk
---

### Post by lonewaster on 2010-05-22
I got sick and tired of having to remember **/etc/init.d/apache2 <method>** every time I wanted to control my httpd, so I wrote an *'alias script'* that I now keep in my **/home/billy/bin** directory (I added my own bin for all my little bash scripts and the ilk) and now all I have to do is type
```
apachectrl <start/stop/restart>
```whenever I want to control the httpd.

So what's the ironic part in all this?
I've now found that I know **/etc/init.d/apache2** off by heart...so this *'alias script'* is kinda useless now :P

Well...not totally useless..I will probably use it still.
Here it is for anyone who might find themself having the same problem of remembering.

***NOTE: IF YOU WANT THIS TO WORK ON YOUR SYSTEM THEN YOU WILL NEED TO PUT THE SCRIPT IN A DIRECTORY FROM YOUR $PATH VARIABLE, OTHERWISE YOU'LL NEED TO TYPE IT'S PATH EVERY TIME YOU WANT*** ***TO CALL IT***.

To find out what directories are in your PATH, type the following in a terminal.
```
echo $PATH
```All the directories that command lists are viable options for putting this script in, so that you only have to type the following to do the business-
```
apachectrl <start/stop/restart>
```If you want to add your own folder to your PATH, then just search the forums as I'm sure it's been covered before..
Actually I think I may have done a bit on it in my backup script tutorial...
Search for "Easy Way To Backup Bash Script" And You Should Find It.

Hope This Has At Least Been...Entertaining :guitar:

darksider


[CENTER][I][B]APACHECTRL
[/B][/I][LEFT]```

#!/bin/bash
#        APACHE ALIAS SCRIPT
#            v1.0
#    createdBy        darksider
#    emailAddy    darksider@swedger.com
#    siteAddy    www.swedger.com
#
#  this script saves typing sudo '/etc/init.d/apache' to 'start/stop/restart'
#  so now all you have to type is 'apachectrl start/stop/restart'

if [[ $1 != "start" ]] && [[ $1 != "stop" ]] && [[ $1 != "restart" ]]; then
    echo "Apache Does Not Accept That Command..."
    echo "Please Use-"
    echo "./apachectrl <start/stop/restart>"
    echo ""
else
    echo "Telling Apache To $1"
    sudo /etc/init.d/apache2 $1
fi

```Just copy this into your favourite text editor, save the file as 'apachectrl' (don't give it a file suffix, unless you want to type that file suffix every time you call on the script!!) and copy it to one of the PATH folders (i mentioned this bit above ^^^)
[/LEFT]
[/CENTER]

---

### Post by DaithiF on 2010-05-24
Hi, why not just use aliases?  put these in your .bashrc file

```
alias astop="/etc/init.d/apache2 stop"
alias astart="/etc/init.d/apache2 start"
alias arestart="/etc/init.d/apache2 restart"

```

---

