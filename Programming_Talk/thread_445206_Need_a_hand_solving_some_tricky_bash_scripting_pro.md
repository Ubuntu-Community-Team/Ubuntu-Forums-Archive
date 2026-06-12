---
title: "Need a hand solving some tricky bash scripting problems."
date: 2007-05-15
forum: Programming Talk
---

### Post by bb002 on 2007-05-15
Well I can't seem to get a grip on them....but first a little info about me and the network: I work for a school district that has deployed a one-to-one tablet program for the high school students and most the staff. Meaning one tablet laptop for each student. We are a relatively small district with about 1300 students and around 70 teachers. Currently the 1-to-1 is for high school students of which there are ~400. the students and staff are allowed to take their pc home. The tabets are all running WIndows XP tablet edition. We have about another 200-300 desktop out as well but they don't matter here other than giving the district a large network.


Now for the problems:

1) The motherboards in these laptops has a weak soldiering job for the cmos battery. which pops loose and re-soldering is a very temporary solution as it pops off again in a few days. The date resets to midnight of 1/1/1987.

2) Determining what network segment the station is on.


I'm more of a html/javascript/php programming when it come to programming. I know that the stations are running Windows XP but the "image" that we are installing next year has cygwin installed. We have the default installation cygwin with ssh, cron, and all of the CLI compression tools(gz, rar, zip, bz2, cabextract, and unshield[i think]) added. The install I have here of Cygwin feels almost like ubuntu's CLI-only install. minus the linux kernel, of course! :D


I have the bash script that checks the time almost finished minus a two things. first is the network segement detection. currently the that line exists as 
```

# network detection incomplete 10.234.7.6 always returned.
$theip=`./netsegdetect`

```

my if statement seems to be wrong and is always false even when MY logic says it should work....after all 1987 IS less than 2007 right??```

if [ `date "+%Y"` < 2007]; then
#the code to update the system time from the ntp server at $theip
# this code works fine just not my if comparison.
fi

```




But I also need a script to determine what network segment the laptop it is on.

[quote="Just some pseudo code for 'netsegdetect'!"]
1: grab the current station ip and assign it to the bash variable **curip** ---DONE.
2: compare the first three numbers of **$curip** to "10.234.6", "10.234.7", and "10.234.8"
2b: the ips are actually in are in an array if bash can do that? would make the process a simple for/while loop.
3: if there is a match print the ip "10.234.7.6" to the console and exit. ---Will be in the for/while loop of step 2.
4: if there is no match print the ip "200.250.250.6" to the console and exit. ---Will after the for/while loop of step 2.
[/quote]
I know how todo steps 1, 3, and 4. I just don't know how to change the station's ip of, for example, "10.234.8.234" into "10.234.8" and compare it to the ips in step 2...my guess is for sed being involved.....>_<





So anyone that can point out my bash shortcomings to me and offer a solution or two would be greatly appreciated!!

---

### Post by jyba on 2007-05-15
> 
my if statement seems to be wrong and is always false even when MY logic says it should work....after all 1987 IS less than 2007 right??```

if [ `date "+%Y"` < 2007]; then
#the code to update the system time from the ntp server at $theip
# this code works fine just not my if comparison.
fi
```

1. You need a space between "2007" and the bracket "]"
2. Use "-lt" rather than "<" for arithmetic comparison

so that should be:

```

if [ `date "+%Y"` -lt 2007 ]; then
...
fi
```
> 2: compare the first three numbers of $curip to "10.234.6", "10.234.7", and "10.234.8"

I am a complete dunce when it comes to IP addresses but if you just want to lop the last number off the end of $curip then you could try...
```

${curip%.*}
```
...which is shorthand for 'remove everything from the last "." onwards'.

So your test could be:

```

case "${curip%.*}" in
	10.234.6|10.234.7|10.234.8)
		echo "string $curip matched"
		;;
	*)
		echo "string $curip not matched"
		;;
esac
```

> 2b: the ips are actually in are in an array if bash can do that? would make the process a simple for/while loop.

Yes, bash can do simple arrays, but I'm unsure what your question is. Perhaps someone else can answer this bit.

---

### Post by bb002 on 2007-05-16
[quote="jyba"]I am a complete dunce when it comes to IP addresses but if you just want to lop the last number off the end of $curip then you could try...[/quote]That is exactly what I want to do thanks! And a "switch case" statement is probably better suited for what i need than a for/while loop.

[quote="jyba"]1. You need a space between "2007" and the bracket "]"[/quote]I dunno where that space went. It has to be in the bash script or I would have gotten a syntax error :confused: unless the < had something to do with it. I just realize that it was trying to insert the contents of the file **2007];**. lol
the "-lt" did the trick too.

My files are at work but I did a quick test of the pieces in question here at home and the two problems that have me stumped are now solved!

Thanks **jyba**!!

---

