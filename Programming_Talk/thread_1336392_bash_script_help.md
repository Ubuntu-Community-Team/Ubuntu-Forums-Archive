---
title: "bash script help"
date: 2009-11-24
forum: Programming Talk
---

### Post by sms552 on 2009-11-24
i have a script that is functioning but if a user makes a mistake on a line it wont go back to the previous line to correct. absolute beginner here with bash scripting any help would be awesome.. 


#!/bin/bash
#================================================= =======
# Script Name: phoneadd
# By:
# Date:
# Purpose: A shell script that sets up a loop to add
# new employees to the corp_phones file.
# Command Syntax: phoneadd
#================================================= =======
trap "rm ~/tmp/* 2> /dev/null; exit" 0 1 2 3
phonefile=./corp_phones
looptest=y
while [ $looptest = y ]
do
clear
tput cup 1 4 ; echo "Corporate Phone List Additions"
tput cup 2 4 ; echo "=============================="
tput cup 4 4 ; echo "Phone Number: "
tput cup 5 4 ; echo "Last Name : "
tput cup 6 4 ; echo "First Name : "
tput cup 7 4 ; echo "Middle Init : "
tput cup 8 4 ; echo "Dept # : "
tput cup 9 4 ; echo "Job Title : "
tput cup 10 4; echo "Date Hired : "
tput cup 12 4; echo "Add another? (y)es or (q)uit "
tput cup 4 18; read phonenum
if [ "$phonenum" = 'q' ]
then
clear ; exit
fi
tput cup 5 18 ; read lname
tput cup 4 18 ; read phonenum
tput cup 6 18 ; read fname
tput cup 7 18 ; read midinit
tput cup 8 18 ; read deptno
tput cup 9 18 ; read jobtitle
tput cup 10 18; read datehired

# Check to see if last name is not blank before you
# write to disk
if [ "$lname" > " "]
then
echo "$phonenum:$lname:$fname:$midinit:$deptno:$jobtitl e:$datehired" >> $phonefile
fi
tput cup 12 33 ; read looptest
if [ "$looptest" = 'q' ]
then
clear ; exit
fi

---

