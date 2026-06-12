---
title: "HOWTO: Add the ubuntu release countdown image to your desktop"
date: 2009-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Johnny B on 2009-04-03
I couldn't seem to find any info on adding the countdown image to my desktop, but i eventually figured this out:

EDIT: Ubuntu 10.04 release: April 29, 2010.
 countdown image links for lucid are not available yet,
should be available April 1st
 
```
#!/bin/bash
#
#
#
# Karmic release October 29th 2009
# Lucid release April 29th 2010

	target=`date +%s --date="Apr 29 2010"`
	source=`date +%s`						# today
	diff=`expr $target - $source`					# difference between dates in seconds 
	days=`expr $diff / 86400`					# convert seconds to days
	((days++))							# round up
	#echo $days


if [ "$days" -lt "0" ] ;then days=0 ;fi
if [ "$days" -lt "29" ] ;then

	if [ ! -d $HOME/.countdown ] ;then
		mkdir $HOME/.countdown
	#else
	#	echo ".countdown exists"
	fi

	cd $HOME/.countdown
	if [ "$days" -lt "10" ] ;then
		echo $days
		#wget http://www.ubuntu.com/files/countdown/910/countdown-9.10-2/0$days.png
                #cp $HOME/.countdown/0$days.png $HOME/.countdown/count.png
	else
		echo $days
		#wget http://www.ubuntu.com/files/countdown/910/countdown-9.10-2/$days.png
                #cp $HOME/.countdown/$days.png $HOME/.countdown/count.png
	fi
else
	echo "$days days until the Ubuntu 10.04 release"
fi
#alternate image: http://www.ubuntu.com/files/countdown/910/countdown-9.10-1
```


you can make ~/.countdown and save the script there as day.sh, and add it to cron by:
#  chmod +x ~/.countdown/day.sh
#  crontab -e

and add the line: 
  01 1 * * * root  ~/.countdown/day.sh

when its less than 30 days until release just open the image ~/.countdown/count.png with the picframe screenlet or conky.

image from 9.04 release:
[[IMG]http://img99.imageshack.us/img99/6700/screenshot4l.th.png[/IMG]](http://img99.imageshack.us/i/screenshot4l.png/)

---

### Post by Johnny B on 2009-10-01
Updated!
[ATTACH]130411[/ATTACH][ATTACH]130412[/ATTACH]

---

### Post by yuli_capone on 2009-10-22
After a couple af days I've figured out how to do this...

Thanks!!

---

### Post by Anduu on 2009-10-23
Neat little script...I have a problem though.

If I execute the script through a terminal it works fine,however when i try to run it through cron i get and error:

```
date: extra operand `--date=29 Oct 2009 23:59:00'
Try `date --help' for more information.
expr: syntax error
expr: syntax error
/home/anduu/.countdown/countdown.sh: line 15: [: : integer expression expected
 days until the Ubuntu 9.10 release
Press ENTER to continue and close this window.
```

Any idea?

---

### Post by Johnny B on 2009-10-23
thats strange, it works for me
try changing:
> target=`**/bin/date** +%s --date="29 Oct 2009 23:59:00"`

---

### Post by Johnny B on 2009-10-23
also, make sure you got > #!/bin/bash at the first line

---

### Post by yuli_capone on 2009-10-23
I have a problem.
I got the script working yesterday,but he "stuck" at 7 days to go...instead of 6 days

---

### Post by Johnny B on 2009-10-24
sometimes the picframe screenlet does not update itself immediately. click it with your mouse or restart it.

---

### Post by Anduu on 2009-10-25
Ok so I fiddled around with the script a bit with no success.

I found a few vague references while Googling to incorrect environment variables and absolute path names explaining why functional bash scripts would fail to run as cron jobs,however no solutions were evident.

I returned the script to its original state and gave up for a while.When I got up today I checked my ~/.countdown folder and lo and behold it contained new .png images.Checked my logs and no error messages either.Just to be sure I modified the cron job to run every minute and it functioned correctly.

Anyway,best guess is something was messed up and a recent update corrected the problem.I could go through my update history to see what fixed things but I cant be bothered to put any more effort into it ;)

Thanks a lot :KS

---

