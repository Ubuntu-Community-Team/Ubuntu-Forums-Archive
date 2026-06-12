---
title: "fun with date using sed and variables"
date: 2007-10-28
forum: Programming Talk
---

### Post by nickoli on 2007-10-28
I wrote this script to convert twenty for hour time to am and pm format. I am not sure how to get my variable to work in the sed command in the pm section of my script any help would be appreciated. Thanks for your time.

#will convert  date to am and pm time
#first if statement focuses on 0-12 hours
a=`date | tr " " ":" | cut -d":" -f4
`
b=`expr $a – 12 `
if [ $a -lt 13 ]
then 
      echo  `date | cut -d" " -f4 | sed 's/\(.*\)\(:.*\)\(:.*\)/\1\2\3am/' `
else   # else statement will focus on pm time.
     echo `date | cut -d” “  -f4 | sed 's/\(.*\)\(:.*\)\(:.*\)/\$b\2\3pm/'`
fi

---

### Post by ghostdog74 on 2007-10-28
check the date man page, the %r format is supposed to give you locale's 12 hr clock time..if i don't get your requirements wrong.

---

