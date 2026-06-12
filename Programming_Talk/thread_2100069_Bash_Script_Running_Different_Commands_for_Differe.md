---
title: "Bash Script Running Different Commands for Different Versions of Apache"
date: 2012-12-31
forum: Programming Talk
---

### Post by cginf0s3c on 2012-12-31
Hi all, 

I'm trying to write a script that will basically run different commands for versions of Apache. For Apache 2 I just need it to run command. If the version is Apache 1 I need it to check if the output of a given command returns blank and check if a file exists. I want the code to exit 0 because these are considered fail conditions.

More specifically what I am trying to accomplish is this. 
If Apache version is 2 then run a command and if it does not contain the 'apache2' string then exit. Else if the apache version is 1 then check if a command output is not blank or a file is a regular file. I used /etc/passwd as a dummy file. If either condition is true I want the code to exit. 

Any pointers would be appreciated. Thanks!


```
#!/bin/bash

VERSION=`apache2 -v | grep "Server version"`
ENABLED=`ps -A | grep 'apache2'`

if [ $VERSION == *Apache/2* ];
then
	elif [[ $ENABLED == *"apache2"* ]];
	then
   	echo 'Apache service is enabled';
   	exit 0
else
if [ $Version | grep -q "Apache/1" ]
then 
elif [ -n $ENABLED -o -f /etc/passwd ]
then 
   echo "The test failed. Apache process running."
   exit 0 
fi
fi

```

---

### Post by Vaphell on 2012-12-31
instead of *ps | grep* you can use *pgrep*, it's much cleaner as the *grep apache2* process itself doesn't get caught

```
**VERSION**=`apache2 -v | grep "Server version"`
if [ **$Version** | grep -q "Apache/1" ]
```
Case doesn't match. I'd avoid all-caps names entirely, shell env vars are all caps by convention and you risk collision by accident.
I'd drop backticks `` too, they suck. Use $() instead
also you can't pipe variable directly to another command, you need to use *echo* or *printf* ( echo $var | ... ).

```
if [ $VERSION == *Apache/2* ];
```
that won't work, you probably want condition in the form of
```
if [[ $version =~ .*Apache/2.* ]]; ...
```

---

