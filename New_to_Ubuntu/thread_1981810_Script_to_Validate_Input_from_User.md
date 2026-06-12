---
title: "Script to Validate Input from User"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by smackheid on 2012-05-17
Hello,

I'm completely new to Linux and have jumped into the deep end. I've set up a server with Server 10.4 (just before 12.4 came out.)

I've created a simple script that accepts user input and stores it in a CSV file, but I need it to ensure that only a 12 digit number(no letters)is entered and that it always begins 447.........

Can someone point me in the right direction please?

Thanks
SmackHeid

---

### Post by CharlesA on 2012-05-17
Check out Python.

[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

---

### Post by steeldriver on 2012-05-17
If the scripting language you are using supports regular expression (regex) syntax, you can match a pattern like that, something like

```
^447[0-9]{9}$
```(start with literal 447 followed by exactly nine digits followed by end)

For example (modern versions of) bash should allow you to do

```
if [[ "$myvar" =~ ^447[0-9]{9}$ ]] then; ... 
```Without knowing more about your script it's hard to be more specific

---

### Post by smackheid on 2012-05-21
Thanks for the replies!!!

So the script simply accepts 12 digit number and adds it to a csv file, which is then uploaded to a FTP server just before midnight via crontab script. Another system reads the contents of the CSV file and processes requests based on the numbers entered and the rest of the contents of the CSV line.

Unfortunately, users can add anything and I've had the process jam further down the line because random 1 digit numbers were entered accidentally.

I will try your suggestion though.

Script as follows:

#!/bin/bash

echo "Please enter the MSISDN to be added to the MSISDN Override List:"
read MSISDN
clear
echo $MSISDN,TRUE >> /var/opt/projects/FTP/msisdn_list.csv
echo
echo $MSISDN added to the MSISDN Override List successfully:


Also, as much as learning Python seems to be inevitable, I will need to put it of for a couple of months at least. Thanks for the  suggestion though.

---

### Post by smackheid on 2012-05-22
Thanks to steeldriver. Your regexp did the trick. I'm very much obliged.

Thanks
Smackheid

---

### Post by steeldriver on 2012-05-22
Happy to help

---

