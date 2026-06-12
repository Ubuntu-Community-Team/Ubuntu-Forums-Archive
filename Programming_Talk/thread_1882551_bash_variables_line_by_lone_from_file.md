---
title: "bash variables line by lone from file"
date: 2011-11-17
forum: Programming Talk
---

### Post by crownedzero on 2011-11-17
I have a number of records in a file, each contains 25 fields. I need 2 of these fields assigned to variables. Everything I've come up with thus far isn't working...

my while read line; do just ends up displaying blank lines...

Any thoughts?

---

### Post by karlson on 2011-11-17
> **crownedzero said:**
> I have a number of records in a file, each contains 25 fields. I need 2 of these fields assigned to variables. Everything I've come up with thus far isn't working...

my while read line; do just ends up displaying blank lines...

Any thoughts?

Have you considered awk?

---

### Post by Vaphell on 2011-11-17
```
fs=','; while read a b; do echo a="$a" b="$b"; done < <(awk -F$fs '{ print $3, $7 }' in.txt)
```

for in.txt
```
1-1,1-2,1-3,1-4,1-5,1-6,1-7,1-8,1-9,1-10
2-1,2-2,2-3,2-4,2-5,2-6,2-7,2-8,2-9,2-10
```
output (3rd and 7th, fields separated by ,):
```
a=1-3 b=1-7
a=2-3 b=2-7
```

---

### Post by crownedzero on 2011-11-17
Sounding like awk is the way to go, I was thinking I could just use read line, and then refer to the different variables much like in the command line arg syntax, $1, $2 etc, I'll get some code posted in a few and go from there if I'm still having issues.

---

### Post by Vaphell on 2011-11-17
hmm, when i think about it awk is not necessary

you can easily do
```
while IFS=, read a1 a2 a3 ... a25; do echo $a2 $a10; done < in.txt
```
23 variables wont be used but who cares :-)
... or version with array

```
while IFS=, read -a arr; do echo ${arr[2]} ${arr[6]}; done < in.txt
```

---

### Post by crownedzero on 2011-11-18
```

#!/bin/bash

#script to inform users of their expired account

#declare variables as integers
declare -i user_epoch_time;
declare -i todays_epoch;

#option to clear logs
echo -n "Would you like to clear the log file? [y/N] "
read user_selection

	if [ $user_selection = y ] || [ $user_selection = Y ]; then
		rm expired_log*.txt
	fi

#while loop to iterate thru each line of the test file
while read user_email user_epoch_time; do
	todays_epoch=$(date +%s);
	#if comparison to find records that have expired
	if [ $todays_epoch -gt $user_epoch_time ]; then
		expired=$(date -d@$user_epoch_time)
		todays_date=$(date -d@$todays_epoch)
			echo "This email is to notify you that your account has expired on $expired" | mail -s "Account Expired" $user_email
			echo -en User: $user_email was notified on $todays_date that their account expired on $expired '\n' >> expired_log$todays_epoch.txt '\n'
	fi

done < <(cut -f 7,12 users_data_file.txt)

```

I don't know why but using awk I got concatenated data in the variables but I couldn't begin to figure out where it was coming from so I used the cut method. This is just a quick run down tell me what/where you think I might be able to improve.

---

### Post by geirha on 2011-11-19
A couple of example lines from the users_data_file.txt file would help.

---

