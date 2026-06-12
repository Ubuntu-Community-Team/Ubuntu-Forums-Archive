---
title: "Shell Programming Question"
date: 2009-04-01
forum: Programming Talk
---

### Post by cyberpunk_35 on 2009-04-01
Hi All - I'm new to the forums and new at shell programming, so I have a question about a program I somewhat copied out of a book and would like to manipulate - Here's what I have so far -

#!/bin/sh

echo "Is it morning?  Please answer yes or no"
read timeofday
if [ "$timeofday" = "yes" ]
then 
echo "Good Morning"
elif [ "timeofday" = "no" ]; then
echo "Good Afternoon"
else 
echo "Sorry - $timeofday is not recognized.  Enter yes or no."
exit 1
fi
exit 0

If you enter anything other than "yes or no", my program exits with "Sorry - $timeofday is not recognized.  Enter yes or no.", which is good! Do any of you know of a way to get my program to loop back to the first line where it asks, "Is it morning?  Please answer yes or no" if you enter anything other than "yes" or "no" instead of the program just exiting out?

If I enter, "I'm a noob programmer", I want the program to keep repeating itself until I enter either "yes" or "no".

Thank you in advance!

---

### Post by ghostdog74 on 2009-04-01
use a loop. check the bash link in my sig to learn about loops.

---

### Post by Tek-E on 2009-04-02
Like ghostdog74 said you should use a loop.
But i would also recommend that you use a case statement.
This way your program also wont exit after a string other than yes or no is entered.

---

### Post by Tek-E on 2009-04-02
For a CASE statement you could do the following.
NOTE: Wrote this off the top of my head. Excuse any possible errors

```

#!/bin/bash
echo "Is it morning? Please answer yes or no"
read timeofday
case $timeofday in
	"yes")
		echo "Good Morning"
		;;
	"no")
		echo "Good Afternoon"
		;;
	*)
		echo "Sorry - $timeofday is not recognized. Enter yes or no."
		./thisscriptsname.sh
		;;
esac
exit 0

```

---

### Post by jpkotta on 2009-04-02
It's perfectly fine to use a case statement, but if you're using Bash, there is a special select statement for this purpose.

```
#!/bin/bash

PS3="Please enter a number: "
select resp in yes no; do
    if [ "$resp" = "yes" ] ; then
	echo yes
	break
    elif [ "$resp" = "no" ] ; then
	echo no
	break
    fi
done
```

---

### Post by cyberpunk_35 on 2009-04-02
Thank you for the suggestions!

---

### Post by cyberpunk_35 on 2009-04-02
Thank guys - Here's what I did - 

echo "Sorry - $timeofday is not recognized. Enter yes or no."
./myscriptsname
fi
exit 0


It worked!

---

### Post by Tek-E on 2009-04-06
jpkotta:
Im glad you pointed that out to me :)
I was unaware of that. Thank you! :)

---

