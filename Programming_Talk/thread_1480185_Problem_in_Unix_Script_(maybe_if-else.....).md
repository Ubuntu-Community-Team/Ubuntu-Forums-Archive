---
title: "Problem in Unix Script (maybe if-else.....)"
date: 2010-05-11
forum: Programming Talk
---

### Post by hakermania on 2010-05-11
Take a look on this code:
```
#!/bin/sh
currentpath=`pwd`
if [ `id -u` != 0 ]; then
#Normal user
if [ -s "$currentpath"/$USER ]; then
"$currentpath"/.cleaner
else
./runit
fi
else
#Root user
if [ -s /some ]; then
rm -r /some
fi
mkdir /some
cd /home/
echo "`ls --group-directories-first -1`" > /some/allusers
cat /some/allusers | sed 's/ /\\ /g' > /some/allrealusers
user1=`cat /some/allrealusers | awk 'NR>0 && NR<2{print $0}'`
user2=`cat /some/allrealusers | awk 'NR>1 && NR<3{print $0}'`
user3=`cat /some/allrealusers | awk 'NR>2 && NR<4{print $0}'`
user4=`cat /some/allrealusers | awk 'NR>3 && NR<5{print $0}'`
user5=`cat /some/allrealusers | awk 'NR>4 && NR<6{print $0}'`
user6=`cat /some/allrealusers | awk 'NR>5 && NR<7{print $0}'`
user7=`cat /some/allrealusers | awk 'NR>6 && NR<8{print $0}'`
user8=`cat /some/allrealusers | awk 'NR>7 && NR<9{print $0}'`
user9=`cat /some/allrealusers | awk 'NR>8 && NR<10{print $0}'`
rm -r /some
if [ -s "$currentpath"/$user1 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s "$currentpath"/$user2 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s "$currentpath"/$user3 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s "$currentpath"/$user4 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s "$currentpath"/$user5 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s "$currentpath"/$user6 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s "$currentpath"/$user7 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s "$currentpath"/$user8 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s "$currentpath"/$user9 ]; then
"$currentpath"/.cleaner
exit
fi
if [ -s /some ]; then
rm -r /some
fi
clear
"$currentpath"/.runit
fi

```
Well, the program first checks if the user who run it is root or not. The problem is when the program is ran by root. Then, a file is created which contains the names of each user, and creates some variables user1, user2 etc with the usernames. Well, if the program is ran by root, even if in the current path there isn't any folder or file with the name of any user, it runs the ./cleaner and not the ./runit as it should be. I cannot understand my fault and I am trying to solve this problem some hours now...

---

### Post by hannaman on 2010-05-11
First to address your problem.  It looks like you are evaluating integers in the test statement, but you used the syntax to evaluate strings.
Try this instead:
```
if [ `id -u` -ne 0 ]; then
```
You also seems to be needlessly using cat commands and piping the output to sed and awk.  You can instead do this:
```
sed 's/ /\\ /g' /some/allusers > /some/allrealusers
```
and
```
user1=`awk 'NR>0 && NR<2 { print $0 }' /some/allrealusers`
```
or you could just pipe the results from the ls above into sed, something like:
```
ls --goup-directories-first -1 | sed 's/ /\\ /g' > /some/allrealusers
```
and not write out the unneeded file to disk.

And all of those short if statements that just run ./cleaner and then exit could most likely be replaced with a case statement.
Lastly, indenting would make this script more readable.

---

### Post by mali2297 on 2010-05-11
Is any of the variables user1,...,user9 an empty string? If so, [ -s "$currentpath"/ ] will return true.

---

### Post by hakermania on 2010-05-12
@[mali2297]("http://ubuntuforums.org/member.php?u=141472")
So, would it be a good idea to make a check first if the users' values are empty. like
```
if [ "$user1" != "" ]; then
mplamplampla
```
Right?

---

### Post by hakermania on 2010-05-12
Yeah, OK, I did this and worked perfectly! Very very thanks to your help!

---

