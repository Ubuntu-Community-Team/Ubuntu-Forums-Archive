---
title: "Script challenge"
date: 2009-04-23
forum: Programming Talk
---

### Post by t-mo_ on 2009-04-23
I do not know programming (as you will see in my scripts...) but started to play around with conky and bash scripts. I made a font displaying hours, minutes and seconds arms (see Screenshot-1.png).

The job of the script is quite simple. It has to get the time and echo the fitting glyph. For example see the scripts.

Now there are two problems: 

My script is way to long. I think it would be possible to have this script much shorter (Crinos512 tried to improve it, but it does not work yet) [http://ubuntuforums.org/showpost.php?p=7123817&postcount=6627]("http://ubuntuforums.org/showpost.php?p=7123817&postcount=6627")

The conky update interval is not totally "in step". If I use my script to display the seconds arm it does not look like a precise clock. The seconds are updated randomly in a time range between approx. 0.5 to 1.5 seconds, no matter if I set the conky update interval to 1 second or below. I am looking for a better "pace maker" but do not know how or if this is possible. Maybe not with a bash script and conky...

This is the script for the hours arm
```
#!/bin/bash
# zoraclock.sh

# written by t-mo_

HOUR=`date | cut -c12-13`
MINUTE=`date | cut -c15-16`
SECOND=`date | cut -c18-19`

if [[ $HOUR = 00 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "A"
	elif [[ $MINUTE = 01 ]]
	then
	echo "A"
	elif [[ $MINUTE = 02 ]]
	then
	echo "A"
	elif [[ $MINUTE = 03 ]]
	then
	echo "A"
	elif [[ $MINUTE = 04 ]]
	then
	echo "A"
	elif [[ $MINUTE = 05 ]]
	then
	echo "A"
	elif [[ $MINUTE = 06 ]]
	then
	echo "A"
	elif [[ $MINUTE = 07 ]]
	then
	echo "A"
	elif [[ $MINUTE = 08 ]]
	then
	echo "A"
	elif [[ $MINUTE = 09 ]]
	then
	echo "A"
	elif [[ $MINUTE = 10 ]]
	then
	echo "A"
	elif [[ $MINUTE = 11 ]]
	then
	echo "A"
	elif [[ $MINUTE = 12 ]]
	then
	echo "B"
	elif [[ $MINUTE = 13 ]]
	then
	echo "B"
	elif [[ $MINUTE = 14 ]]
	then
	echo "B"
	elif [[ $MINUTE = 15 ]]
	then
	echo "B"
	elif [[ $MINUTE = 16 ]]
	then
	echo "B"
	elif [[ $MINUTE = 17 ]]
	then
	echo "B"
	elif [[ $MINUTE = 18 ]]
	then
	echo "B"
	elif [[ $MINUTE = 19 ]]
	then
	echo "B"
	elif [[ $MINUTE = 20 ]]
	then
	echo "B"
	elif [[ $MINUTE = 21 ]]
	then
	echo "B"
	elif [[ $MINUTE = 22 ]]
	then
	echo "B"
	elif [[ $MINUTE = 23 ]]
	then
	echo "C"
	elif [[ $MINUTE = 24 ]]
	then
	echo "C"
	elif [[ $MINUTE = 25 ]]
	then
	echo "C"
	elif [[ $MINUTE = 26 ]]
	then
	echo "C"
	elif [[ $MINUTE = 27 ]]
	then
	echo "C"
	elif [[ $MINUTE = 28 ]]
	then
	echo "C"
	elif [[ $MINUTE = 29 ]]
	then
	echo "C"
	elif [[ $MINUTE = 30 ]]
	then
	echo "C"
	elif [[ $MINUTE = 31 ]]
	then
	echo "C"
	elif [[ $MINUTE = 32 ]]
	then
	echo "C"
	elif [[ $MINUTE = 33 ]]
	then
	echo "C"
	elif [[ $MINUTE = 34 ]]
	then
	echo "C"
	elif [[ $MINUTE = 35 ]]
	then
	echo "C"
	elif [[ $MINUTE = 36 ]]
	then
	echo "D"
	elif [[ $MINUTE = 37 ]]
	then
	echo "D"
	elif [[ $MINUTE = 38 ]]
	then
	echo "D"
	elif [[ $MINUTE = 39 ]]
	then
	echo "D"
	elif [[ $MINUTE = 40 ]]
	then
	echo "D"
	elif [[ $MINUTE = 41 ]]
	then
	echo "D"
	elif [[ $MINUTE = 42 ]]
	then
	echo "D"
	elif [[ $MINUTE = 43 ]]
	then
	echo "D"
	elif [[ $MINUTE = 44 ]]
	then
	echo "D"
	elif [[ $MINUTE = 45 ]]
	then
	echo "D"
	elif [[ $MINUTE = 46 ]]
	then
	echo "D"
	elif [[ $MINUTE = 47 ]]
	then
	echo "D"
	elif [[ $MINUTE = 48 ]]
	then
	echo "E"
	elif [[ $MINUTE = 49 ]]
	then
	echo "E"
	elif [[ $MINUTE = 50 ]]
	then
	echo "E"
	elif [[ $MINUTE = 51 ]]
	then
	echo "E"
	elif [[ $MINUTE = 52 ]]
	then
	echo "E"
	elif [[ $MINUTE = 53 ]]
	then
	echo "E"
	elif [[ $MINUTE = 54 ]]
	then
	echo "E"
	elif [[ $MINUTE = 55 ]]
	then
	echo "E"
	elif [[ $MINUTE = 56 ]]
	then
	echo "E"
	elif [[ $MINUTE = 57 ]]
	then
	echo "E"
	elif [[ $MINUTE = 58 ]]
	then
	echo "E"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "E"
	fi
elif [[ $HOUR = 01 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "F"
	elif [[ $MINUTE = 01 ]]
	then
	echo "F"
	elif [[ $MINUTE = 02 ]]
	then
	echo "F"
	elif [[ $MINUTE = 03 ]]
	then
	echo "F"
	elif [[ $MINUTE = 04 ]]
	then
	echo "F"
	elif [[ $MINUTE = 05 ]]
	then
	echo "F"
	elif [[ $MINUTE = 06 ]]
	then
	echo "F"
	elif [[ $MINUTE = 07 ]]
	then
	echo "F"
	elif [[ $MINUTE = 08 ]]
	then
	echo "F"
	elif [[ $MINUTE = 09 ]]
	then
	echo "F"
	elif [[ $MINUTE = 10 ]]
	then
	echo "F"
	elif [[ $MINUTE = 11 ]]
	then
	echo "F"
	elif [[ $MINUTE = 12 ]]
	then
	echo "G"
	elif [[ $MINUTE = 13 ]]
	then
	echo "G"
	elif [[ $MINUTE = 14 ]]
	then
	echo "G"
	elif [[ $MINUTE = 15 ]]
	then
	echo "G"
	elif [[ $MINUTE = 16 ]]
	then
	echo "G"
	elif [[ $MINUTE = 17 ]]
	then
	echo "G"
	elif [[ $MINUTE = 18 ]]
	then
	echo "G"
	elif [[ $MINUTE = 19 ]]
	then
	echo "G"
	elif [[ $MINUTE = 20 ]]
	then
	echo "G"
	elif [[ $MINUTE = 21 ]]
	then
	echo "G"
	elif [[ $MINUTE = 22 ]]
	then
	echo "G"
	elif [[ $MINUTE = 23 ]]
	then
	echo "H"
	elif [[ $MINUTE = 24 ]]
	then
	echo "H"
	elif [[ $MINUTE = 25 ]]
	then
	echo "H"
	elif [[ $MINUTE = 26 ]]
	then
	echo "H"
	elif [[ $MINUTE = 27 ]]
	then
	echo "H"
	elif [[ $MINUTE = 28 ]]
	then
	echo "H"
	elif [[ $MINUTE = 29 ]]
	then
	echo "H"
	elif [[ $MINUTE = 30 ]]
	then
	echo "H"
	elif [[ $MINUTE = 31 ]]
	then
	echo "H"
	elif [[ $MINUTE = 32 ]]
	then
	echo "H"
	elif [[ $MINUTE = 33 ]]
	then
	echo "H"
	elif [[ $MINUTE = 34 ]]
	then
	echo "H"
	elif [[ $MINUTE = 35 ]]
	then
	echo "H"
	elif [[ $MINUTE = 36 ]]
	then
	echo "I"
	elif [[ $MINUTE = 37 ]]
	then
	echo "I"
	elif [[ $MINUTE = 38 ]]
	then
	echo "I"
	elif [[ $MINUTE = 39 ]]
	then
	echo "I"
	elif [[ $MINUTE = 40 ]]
	then
	echo "I"
	elif [[ $MINUTE = 41 ]]
	then
	echo "I"
	elif [[ $MINUTE = 42 ]]
	then
	echo "I"
	elif [[ $MINUTE = 43 ]]
	then
	echo "I"
	elif [[ $MINUTE = 44 ]]
	then
	echo "I"
	elif [[ $MINUTE = 45 ]]
	then
	echo "I"
	elif [[ $MINUTE = 46 ]]
	then
	echo "I"
	elif [[ $MINUTE = 47 ]]
	then
	echo "I"
	elif [[ $MINUTE = 48 ]]
	then
	echo "J"
	elif [[ $MINUTE = 49 ]]
	then
	echo "J"
	elif [[ $MINUTE = 50 ]]
	then
	echo "J"
	elif [[ $MINUTE = 51 ]]
	then
	echo "J"
	elif [[ $MINUTE = 52 ]]
	then
	echo "J"
	elif [[ $MINUTE = 53 ]]
	then
	echo "J"
	elif [[ $MINUTE = 54 ]]
	then
	echo "J"
	elif [[ $MINUTE = 55 ]]
	then
	echo "J"
	elif [[ $MINUTE = 56 ]]
	then
	echo "J"
	elif [[ $MINUTE = 57 ]]
	then
	echo "J"
	elif [[ $MINUTE = 58 ]]
	then
	echo "J"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "J"
	fi
elif [[ $HOUR = 02 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "K"
	elif [[ $MINUTE = 01 ]]
	then
	echo "K"
	elif [[ $MINUTE = 02 ]]
	then
	echo "K"
	elif [[ $MINUTE = 03 ]]
	then
	echo "K"
	elif [[ $MINUTE = 04 ]]
	then
	echo "K"
	elif [[ $MINUTE = 05 ]]
	then
	echo "K"
	elif [[ $MINUTE = 06 ]]
	then
	echo "K"
	elif [[ $MINUTE = 07 ]]
	then
	echo "K"
	elif [[ $MINUTE = 08 ]]
	then
	echo "K"
	elif [[ $MINUTE = 09 ]]
	then
	echo "K"
	elif [[ $MINUTE = 10 ]]
	then
	echo "K"
	elif [[ $MINUTE = 11 ]]
	then
	echo "K"
	elif [[ $MINUTE = 12 ]]
	then
	echo "L"
	elif [[ $MINUTE = 13 ]]
	then
	echo "L"
	elif [[ $MINUTE = 14 ]]
	then
	echo "L"
	elif [[ $MINUTE = 15 ]]
	then
	echo "L"
	elif [[ $MINUTE = 16 ]]
	then
	echo "L"
	elif [[ $MINUTE = 17 ]]
	then
	echo "L"
	elif [[ $MINUTE = 18 ]]
	then
	echo "L"
	elif [[ $MINUTE = 19 ]]
	then
	echo "L"
	elif [[ $MINUTE = 20 ]]
	then
	echo "L"
	elif [[ $MINUTE = 21 ]]
	then
	echo "L"
	elif [[ $MINUTE = 22 ]]
	then
	echo "L"
	elif [[ $MINUTE = 23 ]]
	then
	echo "M"
	elif [[ $MINUTE = 24 ]]
	then
	echo "M"
	elif [[ $MINUTE = 25 ]]
	then
	echo "M"
	elif [[ $MINUTE = 26 ]]
	then
	echo "M"
	elif [[ $MINUTE = 27 ]]
	then
	echo "M"
	elif [[ $MINUTE = 28 ]]
	then
	echo "M"
	elif [[ $MINUTE = 29 ]]
	then
	echo "M"
	elif [[ $MINUTE = 30 ]]
	then
	echo "M"
	elif [[ $MINUTE = 31 ]]
	then
	echo "M"
	elif [[ $MINUTE = 32 ]]
	then
	echo "M"
	elif [[ $MINUTE = 33 ]]
	then
	echo "M"
	elif [[ $MINUTE = 34 ]]
	then
	echo "M"
	elif [[ $MINUTE = 35 ]]
	then
	echo "M"
	elif [[ $MINUTE = 36 ]]
	then
	echo "N"
	elif [[ $MINUTE = 37 ]]
	then
	echo "N"
	elif [[ $MINUTE = 38 ]]
	then
	echo "N"
	elif [[ $MINUTE = 39 ]]
	then
	echo "N"
	elif [[ $MINUTE = 40 ]]
	then
	echo "N"
	elif [[ $MINUTE = 41 ]]
	then
	echo "N"
	elif [[ $MINUTE = 42 ]]
	then
	echo "N"
	elif [[ $MINUTE = 43 ]]
	then
	echo "N"
	elif [[ $MINUTE = 44 ]]
	then
	echo "N"
	elif [[ $MINUTE = 45 ]]
	then
	echo "N"
	elif [[ $MINUTE = 46 ]]
	then
	echo "N"
	elif [[ $MINUTE = 47 ]]
	then
	echo "N"
	elif [[ $MINUTE = 48 ]]
	then
	echo "O"
	elif [[ $MINUTE = 49 ]]
	then
	echo "O"
	elif [[ $MINUTE = 50 ]]
	then
	echo "O"
	elif [[ $MINUTE = 51 ]]
	then
	echo "O"
	elif [[ $MINUTE = 52 ]]
	then
	echo "O"
	elif [[ $MINUTE = 53 ]]
	then
	echo "O"
	elif [[ $MINUTE = 54 ]]
	then
	echo "O"
	elif [[ $MINUTE = 55 ]]
	then
	echo "O"
	elif [[ $MINUTE = 56 ]]
	then
	echo "O"
	elif [[ $MINUTE = 57 ]]
	then
	echo "O"
	elif [[ $MINUTE = 58 ]]
	then
	echo "O"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "O"
	fi
elif [[ $HOUR = 03 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "P"
	elif [[ $MINUTE = 01 ]]
	then
	echo "P"
	elif [[ $MINUTE = 02 ]]
	then
	echo "P"
	elif [[ $MINUTE = 03 ]]
	then
	echo "P"
	elif [[ $MINUTE = 04 ]]
	then
	echo "P"
	elif [[ $MINUTE = 05 ]]
	then
	echo "P"
	elif [[ $MINUTE = 06 ]]
	then
	echo "P"
	elif [[ $MINUTE = 07 ]]
	then
	echo "P"
	elif [[ $MINUTE = 08 ]]
	then
	echo "P"
	elif [[ $MINUTE = 09 ]]
	then
	echo "P"
	elif [[ $MINUTE = 10 ]]
	then
	echo "P"
	elif [[ $MINUTE = 11 ]]
	then
	echo "P"
	elif [[ $MINUTE = 12 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 13 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 14 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 15 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 16 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 17 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 18 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 19 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 20 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 21 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 22 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 23 ]]
	then
	echo "R"
	elif [[ $MINUTE = 24 ]]
	then
	echo "R"
	elif [[ $MINUTE = 25 ]]
	then
	echo "R"
	elif [[ $MINUTE = 26 ]]
	then
	echo "R"
	elif [[ $MINUTE = 27 ]]
	then
	echo "R"
	elif [[ $MINUTE = 28 ]]
	then
	echo "R"
	elif [[ $MINUTE = 29 ]]
	then
	echo "R"
	elif [[ $MINUTE = 30 ]]
	then
	echo "R"
	elif [[ $MINUTE = 31 ]]
	then
	echo "R"
	elif [[ $MINUTE = 32 ]]
	then
	echo "R"
	elif [[ $MINUTE = 33 ]]
	then
	echo "R"
	elif [[ $MINUTE = 34 ]]
	then
	echo "R"
	elif [[ $MINUTE = 35 ]]
	then
	echo "R"
	elif [[ $MINUTE = 36 ]]
	then
	echo "S"
	elif [[ $MINUTE = 37 ]]
	then
	echo "S"
	elif [[ $MINUTE = 38 ]]
	then
	echo "S"
	elif [[ $MINUTE = 39 ]]
	then
	echo "S"
	elif [[ $MINUTE = 40 ]]
	then
	echo "S"
	elif [[ $MINUTE = 41 ]]
	then
	echo "S"
	elif [[ $MINUTE = 42 ]]
	then
	echo "S"
	elif [[ $MINUTE = 43 ]]
	then
	echo "S"
	elif [[ $MINUTE = 44 ]]
	then
	echo "S"
	elif [[ $MINUTE = 45 ]]
	then
	echo "S"
	elif [[ $MINUTE = 46 ]]
	then
	echo "S"
	elif [[ $MINUTE = 47 ]]
	then
	echo "S"
	elif [[ $MINUTE = 48 ]]
	then
	echo "T"
	elif [[ $MINUTE = 49 ]]
	then
	echo "T"
	elif [[ $MINUTE = 50 ]]
	then
	echo "T"
	elif [[ $MINUTE = 51 ]]
	then
	echo "T"
	elif [[ $MINUTE = 52 ]]
	then
	echo "T"
	elif [[ $MINUTE = 53 ]]
	then
	echo "T"
	elif [[ $MINUTE = 54 ]]
	then
	echo "T"
	elif [[ $MINUTE = 55 ]]
	then
	echo "T"
	elif [[ $MINUTE = 56 ]]
	then
	echo "T"
	elif [[ $MINUTE = 57 ]]
	then
	echo "T"
	elif [[ $MINUTE = 58 ]]
	then
	echo "T"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "T"
	fi
elif [[ $HOUR = 04 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "U"
	elif [[ $MINUTE = 01 ]]
	then
	echo "U"
	elif [[ $MINUTE = 02 ]]
	then
	echo "U"
	elif [[ $MINUTE = 03 ]]
	then
	echo "U"
	elif [[ $MINUTE = 04 ]]
	then
	echo "U"
	elif [[ $MINUTE = 05 ]]
	then
	echo "U"
	elif [[ $MINUTE = 06 ]]
	then
	echo "U"
	elif [[ $MINUTE = 07 ]]
	then
	echo "U"
	elif [[ $MINUTE = 08 ]]
	then
	echo "U"
	elif [[ $MINUTE = 09 ]]
	then
	echo "U"
	elif [[ $MINUTE = 10 ]]
	then
	echo "U"
	elif [[ $MINUTE = 11 ]]
	then
	echo "U"
	elif [[ $MINUTE = 12 ]]
	then
	echo "V"
	elif [[ $MINUTE = 13 ]]
	then
	echo "V"
	elif [[ $MINUTE = 14 ]]
	then
	echo "V"
	elif [[ $MINUTE = 15 ]]
	then
	echo "V"
	elif [[ $MINUTE = 16 ]]
	then
	echo "V"
	elif [[ $MINUTE = 17 ]]
	then
	echo "V"
	elif [[ $MINUTE = 18 ]]
	then
	echo "V"
	elif [[ $MINUTE = 19 ]]
	then
	echo "V"
	elif [[ $MINUTE = 20 ]]
	then
	echo "V"
	elif [[ $MINUTE = 21 ]]
	then
	echo "V"
	elif [[ $MINUTE = 22 ]]
	then
	echo "V"
	elif [[ $MINUTE = 23 ]]
	then
	echo "W"
	elif [[ $MINUTE = 24 ]]
	then
	echo "W"
	elif [[ $MINUTE = 25 ]]
	then
	echo "W"
	elif [[ $MINUTE = 26 ]]
	then
	echo "W"
	elif [[ $MINUTE = 27 ]]
	then
	echo "W"
	elif [[ $MINUTE = 28 ]]
	then
	echo "W"
	elif [[ $MINUTE = 29 ]]
	then
	echo "W"
	elif [[ $MINUTE = 30 ]]
	then
	echo "W"
	elif [[ $MINUTE = 31 ]]
	then
	echo "W"
	elif [[ $MINUTE = 32 ]]
	then
	echo "W"
	elif [[ $MINUTE = 33 ]]
	then
	echo "W"
	elif [[ $MINUTE = 34 ]]
	then
	echo "W"
	elif [[ $MINUTE = 35 ]]
	then
	echo "W"
	elif [[ $MINUTE = 36 ]]
	then
	echo "X"
	elif [[ $MINUTE = 37 ]]
	then
	echo "X"
	elif [[ $MINUTE = 38 ]]
	then
	echo "X"
	elif [[ $MINUTE = 39 ]]
	then
	echo "X"
	elif [[ $MINUTE = 40 ]]
	then
	echo "X"
	elif [[ $MINUTE = 41 ]]
	then
	echo "X"
	elif [[ $MINUTE = 42 ]]
	then
	echo "X"
	elif [[ $MINUTE = 43 ]]
	then
	echo "X"
	elif [[ $MINUTE = 44 ]]
	then
	echo "X"
	elif [[ $MINUTE = 45 ]]
	then
	echo "X"
	elif [[ $MINUTE = 46 ]]
	then
	echo "X"
	elif [[ $MINUTE = 47 ]]
	then
	echo "X"
	elif [[ $MINUTE = 48 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 49 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 50 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 51 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 52 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 53 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 54 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 55 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 56 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 57 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 58 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "Y"
	fi
elif [[ $HOUR = 05 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 01 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 02 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 03 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 04 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 05 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 06 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 07 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 08 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 09 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 10 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 11 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 12 ]]
	then
	echo "a"
	elif [[ $MINUTE = 13 ]]
	then
	echo "a"
	elif [[ $MINUTE = 14 ]]
	then
	echo "a"
	elif [[ $MINUTE = 15 ]]
	then
	echo "a"
	elif [[ $MINUTE = 16 ]]
	then
	echo "a"
	elif [[ $MINUTE = 17 ]]
	then
	echo "a"
	elif [[ $MINUTE = 18 ]]
	then
	echo "a"
	elif [[ $MINUTE = 19 ]]
	then
	echo "a"
	elif [[ $MINUTE = 20 ]]
	then
	echo "a"
	elif [[ $MINUTE = 21 ]]
	then
	echo "a"
	elif [[ $MINUTE = 22 ]]
	then
	echo "a"
	elif [[ $MINUTE = 23 ]]
	then
	echo "b"
	elif [[ $MINUTE = 24 ]]
	then
	echo "b"
	elif [[ $MINUTE = 25 ]]
	then
	echo "b"
	elif [[ $MINUTE = 26 ]]
	then
	echo "b"
	elif [[ $MINUTE = 27 ]]
	then
	echo "b"
	elif [[ $MINUTE = 28 ]]
	then
	echo "b"
	elif [[ $MINUTE = 29 ]]
	then
	echo "b"
	elif [[ $MINUTE = 30 ]]
	then
	echo "b"
	elif [[ $MINUTE = 31 ]]
	then
	echo "b"
	elif [[ $MINUTE = 32 ]]
	then
	echo "b"
	elif [[ $MINUTE = 33 ]]
	then
	echo "b"
	elif [[ $MINUTE = 34 ]]
	then
	echo "b"
	elif [[ $MINUTE = 35 ]]
	then
	echo "b"
	elif [[ $MINUTE = 36 ]]
	then
	echo "c"
	elif [[ $MINUTE = 37 ]]
	then
	echo "c"
	elif [[ $MINUTE = 38 ]]
	then
	echo "c"
	elif [[ $MINUTE = 39 ]]
	then
	echo "c"
	elif [[ $MINUTE = 40 ]]
	then
	echo "c"
	elif [[ $MINUTE = 41 ]]
	then
	echo "c"
	elif [[ $MINUTE = 42 ]]
	then
	echo "c"
	elif [[ $MINUTE = 43 ]]
	then
	echo "c"
	elif [[ $MINUTE = 44 ]]
	then
	echo "c"
	elif [[ $MINUTE = 45 ]]
	then
	echo "c"
	elif [[ $MINUTE = 46 ]]
	then
	echo "c"
	elif [[ $MINUTE = 47 ]]
	then
	echo "c"
	elif [[ $MINUTE = 48 ]]
	then
	echo "d"
	elif [[ $MINUTE = 49 ]]
	then
	echo "d"
	elif [[ $MINUTE = 50 ]]
	then
	echo "d"
	elif [[ $MINUTE = 51 ]]
	then
	echo "d"
	elif [[ $MINUTE = 52 ]]
	then
	echo "d"
	elif [[ $MINUTE = 53 ]]
	then
	echo "d"
	elif [[ $MINUTE = 54 ]]
	then
	echo "d"
	elif [[ $MINUTE = 55 ]]
	then
	echo "d"
	elif [[ $MINUTE = 56 ]]
	then
	echo "d"
	elif [[ $MINUTE = 57 ]]
	then
	echo "d"
	elif [[ $MINUTE = 58 ]]
	then
	echo "d"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "d"
	fi
elif [[ $HOUR = 06 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "e"
	elif [[ $MINUTE = 01 ]]
	then
	echo "e"
	elif [[ $MINUTE = 02 ]]
	then
	echo "e"
	elif [[ $MINUTE = 03 ]]
	then
	echo "e"
	elif [[ $MINUTE = 04 ]]
	then
	echo "e"
	elif [[ $MINUTE = 05 ]]
	then
	echo "e"
	elif [[ $MINUTE = 06 ]]
	then
	echo "e"
	elif [[ $MINUTE = 07 ]]
	then
	echo "e"
	elif [[ $MINUTE = 08 ]]
	then
	echo "e"
	elif [[ $MINUTE = 09 ]]
	then
	echo "e"
	elif [[ $MINUTE = 10 ]]
	then
	echo "e"
	elif [[ $MINUTE = 11 ]]
	then
	echo "e"
	elif [[ $MINUTE = 12 ]]
	then
	echo "f"
	elif [[ $MINUTE = 13 ]]
	then
	echo "f"
	elif [[ $MINUTE = 14 ]]
	then
	echo "f"
	elif [[ $MINUTE = 15 ]]
	then
	echo "f"
	elif [[ $MINUTE = 16 ]]
	then
	echo "f"
	elif [[ $MINUTE = 17 ]]
	then
	echo "f"
	elif [[ $MINUTE = 18 ]]
	then
	echo "f"
	elif [[ $MINUTE = 19 ]]
	then
	echo "f"
	elif [[ $MINUTE = 20 ]]
	then
	echo "f"
	elif [[ $MINUTE = 21 ]]
	then
	echo "f"
	elif [[ $MINUTE = 22 ]]
	then
	echo "f"
	elif [[ $MINUTE = 23 ]]
	then
	echo "g"
	elif [[ $MINUTE = 24 ]]
	then
	echo "g"
	elif [[ $MINUTE = 25 ]]
	then
	echo "g"
	elif [[ $MINUTE = 26 ]]
	then
	echo "g"
	elif [[ $MINUTE = 27 ]]
	then
	echo "g"
	elif [[ $MINUTE = 28 ]]
	then
	echo "g"
	elif [[ $MINUTE = 29 ]]
	then
	echo "g"
	elif [[ $MINUTE = 30 ]]
	then
	echo "g"
	elif [[ $MINUTE = 31 ]]
	then
	echo "g"
	elif [[ $MINUTE = 32 ]]
	then
	echo "g"
	elif [[ $MINUTE = 33 ]]
	then
	echo "g"
	elif [[ $MINUTE = 34 ]]
	then
	echo "g"
	elif [[ $MINUTE = 35 ]]
	then
	echo "g"
	elif [[ $MINUTE = 36 ]]
	then
	echo "h"
	elif [[ $MINUTE = 37 ]]
	then
	echo "h"
	elif [[ $MINUTE = 38 ]]
	then
	echo "h"
	elif [[ $MINUTE = 39 ]]
	then
	echo "h"
	elif [[ $MINUTE = 40 ]]
	then
	echo "h"
	elif [[ $MINUTE = 41 ]]
	then
	echo "h"
	elif [[ $MINUTE = 42 ]]
	then
	echo "h"
	elif [[ $MINUTE = 43 ]]
	then
	echo "h"
	elif [[ $MINUTE = 44 ]]
	then
	echo "h"
	elif [[ $MINUTE = 45 ]]
	then
	echo "h"
	elif [[ $MINUTE = 46 ]]
	then
	echo "h"
	elif [[ $MINUTE = 47 ]]
	then
	echo "h"
	elif [[ $MINUTE = 48 ]]
	then
	echo "i"
	elif [[ $MINUTE = 49 ]]
	then
	echo "i"
	elif [[ $MINUTE = 50 ]]
	then
	echo "i"
	elif [[ $MINUTE = 51 ]]
	then
	echo "i"
	elif [[ $MINUTE = 52 ]]
	then
	echo "i"
	elif [[ $MINUTE = 53 ]]
	then
	echo "i"
	elif [[ $MINUTE = 54 ]]
	then
	echo "i"
	elif [[ $MINUTE = 55 ]]
	then
	echo "i"
	elif [[ $MINUTE = 56 ]]
	then
	echo "i"
	elif [[ $MINUTE = 57 ]]
	then
	echo "i"
	elif [[ $MINUTE = 58 ]]
	then
	echo "i"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "i"
	fi
elif [[ $HOUR = 07 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "j"
	elif [[ $MINUTE = 01 ]]
	then
	echo "j"
	elif [[ $MINUTE = 02 ]]
	then
	echo "j"
	elif [[ $MINUTE = 03 ]]
	then
	echo "j"
	elif [[ $MINUTE = 04 ]]
	then
	echo "j"
	elif [[ $MINUTE = 05 ]]
	then
	echo "j"
	elif [[ $MINUTE = 06 ]]
	then
	echo "j"
	elif [[ $MINUTE = 07 ]]
	then
	echo "j"
	elif [[ $MINUTE = 08 ]]
	then
	echo "j"
	elif [[ $MINUTE = 09 ]]
	then
	echo "j"
	elif [[ $MINUTE = 10 ]]
	then
	echo "j"
	elif [[ $MINUTE = 11 ]]
	then
	echo "j"
	elif [[ $MINUTE = 12 ]]
	then
	echo "k"
	elif [[ $MINUTE = 13 ]]
	then
	echo "k"
	elif [[ $MINUTE = 14 ]]
	then
	echo "k"
	elif [[ $MINUTE = 15 ]]
	then
	echo "k"
	elif [[ $MINUTE = 16 ]]
	then
	echo "k"
	elif [[ $MINUTE = 17 ]]
	then
	echo "k"
	elif [[ $MINUTE = 18 ]]
	then
	echo "k"
	elif [[ $MINUTE = 19 ]]
	then
	echo "k"
	elif [[ $MINUTE = 20 ]]
	then
	echo "k"
	elif [[ $MINUTE = 21 ]]
	then
	echo "k"
	elif [[ $MINUTE = 22 ]]
	then
	echo "k"
	elif [[ $MINUTE = 23 ]]
	then
	echo "l"
	elif [[ $MINUTE = 24 ]]
	then
	echo "l"
	elif [[ $MINUTE = 25 ]]
	then
	echo "l"
	elif [[ $MINUTE = 26 ]]
	then
	echo "l"
	elif [[ $MINUTE = 27 ]]
	then
	echo "l"
	elif [[ $MINUTE = 28 ]]
	then
	echo "l"
	elif [[ $MINUTE = 29 ]]
	then
	echo "l"
	elif [[ $MINUTE = 30 ]]
	then
	echo "l"
	elif [[ $MINUTE = 31 ]]
	then
	echo "l"
	elif [[ $MINUTE = 32 ]]
	then
	echo "l"
	elif [[ $MINUTE = 33 ]]
	then
	echo "l"
	elif [[ $MINUTE = 34 ]]
	then
	echo "l"
	elif [[ $MINUTE = 35 ]]
	then
	echo "l"
	elif [[ $MINUTE = 36 ]]
	then
	echo "m"
	elif [[ $MINUTE = 37 ]]
	then
	echo "m"
	elif [[ $MINUTE = 38 ]]
	then
	echo "m"
	elif [[ $MINUTE = 39 ]]
	then
	echo "m"
	elif [[ $MINUTE = 40 ]]
	then
	echo "m"
	elif [[ $MINUTE = 41 ]]
	then
	echo "m"
	elif [[ $MINUTE = 42 ]]
	then
	echo "m"
	elif [[ $MINUTE = 43 ]]
	then
	echo "m"
	elif [[ $MINUTE = 44 ]]
	then
	echo "m"
	elif [[ $MINUTE = 45 ]]
	then
	echo "m"
	elif [[ $MINUTE = 46 ]]
	then
	echo "m"
	elif [[ $MINUTE = 47 ]]
	then
	echo "m"
	elif [[ $MINUTE = 48 ]]
	then
	echo "n"
	elif [[ $MINUTE = 49 ]]
	then
	echo "n"
	elif [[ $MINUTE = 50 ]]
	then
	echo "n"
	elif [[ $MINUTE = 51 ]]
	then
	echo "n"
	elif [[ $MINUTE = 52 ]]
	then
	echo "n"
	elif [[ $MINUTE = 53 ]]
	then
	echo "n"
	elif [[ $MINUTE = 54 ]]
	then
	echo "n"
	elif [[ $MINUTE = 55 ]]
	then
	echo "n"
	elif [[ $MINUTE = 56 ]]
	then
	echo "n"
	elif [[ $MINUTE = 57 ]]
	then
	echo "n"
	elif [[ $MINUTE = 58 ]]
	then
	echo "n"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "n"
	fi
elif [[ $HOUR = 08 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "o"
	elif [[ $MINUTE = 01 ]]
	then
	echo "o"
	elif [[ $MINUTE = 02 ]]
	then
	echo "o"
	elif [[ $MINUTE = 03 ]]
	then
	echo "o"
	elif [[ $MINUTE = 04 ]]
	then
	echo "o"
	elif [[ $MINUTE = 05 ]]
	then
	echo "o"
	elif [[ $MINUTE = 06 ]]
	then
	echo "o"
	elif [[ $MINUTE = 07 ]]
	then
	echo "o"
	elif [[ $MINUTE = 08 ]]
	then
	echo "o"
	elif [[ $MINUTE = 09 ]]
	then
	echo "o"
	elif [[ $MINUTE = 10 ]]
	then
	echo "o"
	elif [[ $MINUTE = 11 ]]
	then
	echo "o"
	elif [[ $MINUTE = 12 ]]
	then
	echo "p"
	elif [[ $MINUTE = 13 ]]
	then
	echo "p"
	elif [[ $MINUTE = 14 ]]
	then
	echo "p"
	elif [[ $MINUTE = 15 ]]
	then
	echo "p"
	elif [[ $MINUTE = 16 ]]
	then
	echo "p"
	elif [[ $MINUTE = 17 ]]
	then
	echo "p"
	elif [[ $MINUTE = 18 ]]
	then
	echo "p"
	elif [[ $MINUTE = 19 ]]
	then
	echo "p"
	elif [[ $MINUTE = 20 ]]
	then
	echo "p"
	elif [[ $MINUTE = 21 ]]
	then
	echo "p"
	elif [[ $MINUTE = 22 ]]
	then
	echo "p"
	elif [[ $MINUTE = 23 ]]
	then
	echo "q"
	elif [[ $MINUTE = 24 ]]
	then
	echo "q"
	elif [[ $MINUTE = 25 ]]
	then
	echo "q"
	elif [[ $MINUTE = 26 ]]
	then
	echo "q"
	elif [[ $MINUTE = 27 ]]
	then
	echo "q"
	elif [[ $MINUTE = 28 ]]
	then
	echo "q"
	elif [[ $MINUTE = 29 ]]
	then
	echo "q"
	elif [[ $MINUTE = 30 ]]
	then
	echo "q"
	elif [[ $MINUTE = 31 ]]
	then
	echo "q"
	elif [[ $MINUTE = 32 ]]
	then
	echo "q"
	elif [[ $MINUTE = 33 ]]
	then
	echo "q"
	elif [[ $MINUTE = 34 ]]
	then
	echo "q"
	elif [[ $MINUTE = 35 ]]
	then
	echo "q"
	elif [[ $MINUTE = 36 ]]
	then
	echo "r"
	elif [[ $MINUTE = 37 ]]
	then
	echo "r"
	elif [[ $MINUTE = 38 ]]
	then
	echo "r"
	elif [[ $MINUTE = 39 ]]
	then
	echo "r"
	elif [[ $MINUTE = 40 ]]
	then
	echo "r"
	elif [[ $MINUTE = 41 ]]
	then
	echo "r"
	elif [[ $MINUTE = 42 ]]
	then
	echo "r"
	elif [[ $MINUTE = 43 ]]
	then
	echo "r"
	elif [[ $MINUTE = 44 ]]
	then
	echo "r"
	elif [[ $MINUTE = 45 ]]
	then
	echo "r"
	elif [[ $MINUTE = 46 ]]
	then
	echo "r"
	elif [[ $MINUTE = 47 ]]
	then
	echo "r"
	elif [[ $MINUTE = 48 ]]
	then
	echo "s"
	elif [[ $MINUTE = 49 ]]
	then
	echo "s"
	elif [[ $MINUTE = 50 ]]
	then
	echo "s"
	elif [[ $MINUTE = 51 ]]
	then
	echo "s"
	elif [[ $MINUTE = 52 ]]
	then
	echo "s"
	elif [[ $MINUTE = 53 ]]
	then
	echo "s"
	elif [[ $MINUTE = 54 ]]
	then
	echo "s"
	elif [[ $MINUTE = 55 ]]
	then
	echo "s"
	elif [[ $MINUTE = 56 ]]
	then
	echo "s"
	elif [[ $MINUTE = 57 ]]
	then
	echo "s"
	elif [[ $MINUTE = 58 ]]
	then
	echo "s"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "s"
	fi
elif [[ $HOUR = 09 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "t"
	elif [[ $MINUTE = 01 ]]
	then
	echo "t"
	elif [[ $MINUTE = 02 ]]
	then
	echo "t"
	elif [[ $MINUTE = 03 ]]
	then
	echo "t"
	elif [[ $MINUTE = 04 ]]
	then
	echo "t"
	elif [[ $MINUTE = 05 ]]
	then
	echo "t"
	elif [[ $MINUTE = 06 ]]
	then
	echo "t"
	elif [[ $MINUTE = 07 ]]
	then
	echo "t"
	elif [[ $MINUTE = 08 ]]
	then
	echo "t"
	elif [[ $MINUTE = 09 ]]
	then
	echo "t"
	elif [[ $MINUTE = 10 ]]
	then
	echo "t"
	elif [[ $MINUTE = 11 ]]
	then
	echo "t"
	elif [[ $MINUTE = 12 ]]
	then
	echo "u"
	elif [[ $MINUTE = 13 ]]
	then
	echo "u"
	elif [[ $MINUTE = 14 ]]
	then
	echo "u"
	elif [[ $MINUTE = 15 ]]
	then
	echo "u"
	elif [[ $MINUTE = 16 ]]
	then
	echo "u"
	elif [[ $MINUTE = 17 ]]
	then
	echo "u"
	elif [[ $MINUTE = 18 ]]
	then
	echo "u"
	elif [[ $MINUTE = 19 ]]
	then
	echo "u"
	elif [[ $MINUTE = 20 ]]
	then
	echo "u"
	elif [[ $MINUTE = 21 ]]
	then
	echo "u"
	elif [[ $MINUTE = 22 ]]
	then
	echo "u"
	elif [[ $MINUTE = 23 ]]
	then
	echo "v"
	elif [[ $MINUTE = 24 ]]
	then
	echo "v"
	elif [[ $MINUTE = 25 ]]
	then
	echo "v"
	elif [[ $MINUTE = 26 ]]
	then
	echo "v"
	elif [[ $MINUTE = 27 ]]
	then
	echo "v"
	elif [[ $MINUTE = 28 ]]
	then
	echo "v"
	elif [[ $MINUTE = 29 ]]
	then
	echo "v"
	elif [[ $MINUTE = 30 ]]
	then
	echo "v"
	elif [[ $MINUTE = 31 ]]
	then
	echo "v"
	elif [[ $MINUTE = 32 ]]
	then
	echo "v"
	elif [[ $MINUTE = 33 ]]
	then
	echo "v"
	elif [[ $MINUTE = 34 ]]
	then
	echo "v"
	elif [[ $MINUTE = 35 ]]
	then
	echo "v"
	elif [[ $MINUTE = 36 ]]
	then
	echo "w"
	elif [[ $MINUTE = 37 ]]
	then
	echo "w"
	elif [[ $MINUTE = 38 ]]
	then
	echo "w"
	elif [[ $MINUTE = 39 ]]
	then
	echo "w"
	elif [[ $MINUTE = 40 ]]
	then
	echo "w"
	elif [[ $MINUTE = 41 ]]
	then
	echo "w"
	elif [[ $MINUTE = 42 ]]
	then
	echo "w"
	elif [[ $MINUTE = 43 ]]
	then
	echo "w"
	elif [[ $MINUTE = 44 ]]
	then
	echo "w"
	elif [[ $MINUTE = 45 ]]
	then
	echo "w"
	elif [[ $MINUTE = 46 ]]
	then
	echo "w"
	elif [[ $MINUTE = 47 ]]
	then
	echo "w"
	elif [[ $MINUTE = 48 ]]
	then
	echo "x"
	elif [[ $MINUTE = 49 ]]
	then
	echo "x"
	elif [[ $MINUTE = 50 ]]
	then
	echo "x"
	elif [[ $MINUTE = 51 ]]
	then
	echo "x"
	elif [[ $MINUTE = 52 ]]
	then
	echo "x"
	elif [[ $MINUTE = 53 ]]
	then
	echo "x"
	elif [[ $MINUTE = 54 ]]
	then
	echo "x"
	elif [[ $MINUTE = 55 ]]
	then
	echo "x"
	elif [[ $MINUTE = 56 ]]
	then
	echo "x"
	elif [[ $MINUTE = 57 ]]
	then
	echo "x"
	elif [[ $MINUTE = 58 ]]
	then
	echo "x"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "x"
	fi
elif [[ $HOUR = 10 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "y"
	elif [[ $MINUTE = 01 ]]
	then
	echo "y"
	elif [[ $MINUTE = 02 ]]
	then
	echo "y"
	elif [[ $MINUTE = 03 ]]
	then
	echo "y"
	elif [[ $MINUTE = 04 ]]
	then
	echo "y"
	elif [[ $MINUTE = 05 ]]
	then
	echo "y"
	elif [[ $MINUTE = 06 ]]
	then
	echo "y"
	elif [[ $MINUTE = 07 ]]
	then
	echo "y"
	elif [[ $MINUTE = 08 ]]
	then
	echo "y"
	elif [[ $MINUTE = 09 ]]
	then
	echo "y"
	elif [[ $MINUTE = 10 ]]
	then
	echo "y"
	elif [[ $MINUTE = 11 ]]
	then
	echo "y"
	elif [[ $MINUTE = 12 ]]
	then
	echo "z"
	elif [[ $MINUTE = 13 ]]
	then
	echo "z"
	elif [[ $MINUTE = 14 ]]
	then
	echo "z"
	elif [[ $MINUTE = 15 ]]
	then
	echo "z"
	elif [[ $MINUTE = 16 ]]
	then
	echo "z"
	elif [[ $MINUTE = 17 ]]
	then
	echo "z"
	elif [[ $MINUTE = 18 ]]
	then
	echo "z"
	elif [[ $MINUTE = 19 ]]
	then
	echo "z"
	elif [[ $MINUTE = 20 ]]
	then
	echo "z"
	elif [[ $MINUTE = 21 ]]
	then
	echo "z"
	elif [[ $MINUTE = 22 ]]
	then
	echo "z"
	elif [[ $MINUTE = 23 ]]
	then
	echo "1"
	elif [[ $MINUTE = 24 ]]
	then
	echo "1"
	elif [[ $MINUTE = 25 ]]
	then
	echo "1"
	elif [[ $MINUTE = 26 ]]
	then
	echo "1"
	elif [[ $MINUTE = 27 ]]
	then
	echo "1"
	elif [[ $MINUTE = 28 ]]
	then
	echo "1"
	elif [[ $MINUTE = 29 ]]
	then
	echo "1"
	elif [[ $MINUTE = 30 ]]
	then
	echo "1"
	elif [[ $MINUTE = 31 ]]
	then
	echo "1"
	elif [[ $MINUTE = 32 ]]
	then
	echo "1"
	elif [[ $MINUTE = 33 ]]
	then
	echo "1"
	elif [[ $MINUTE = 34 ]]
	then
	echo "1"
	elif [[ $MINUTE = 35 ]]
	then
	echo "1"
	elif [[ $MINUTE = 36 ]]
	then
	echo "2"
	elif [[ $MINUTE = 37 ]]
	then
	echo "2"
	elif [[ $MINUTE = 38 ]]
	then
	echo "2"
	elif [[ $MINUTE = 39 ]]
	then
	echo "2"
	elif [[ $MINUTE = 40 ]]
	then
	echo "2"
	elif [[ $MINUTE = 41 ]]
	then
	echo "2"
	elif [[ $MINUTE = 42 ]]
	then
	echo "2"
	elif [[ $MINUTE = 43 ]]
	then
	echo "2"
	elif [[ $MINUTE = 44 ]]
	then
	echo "2"
	elif [[ $MINUTE = 45 ]]
	then
	echo "2"
	elif [[ $MINUTE = 46 ]]
	then
	echo "2"
	elif [[ $MINUTE = 47 ]]
	then
	echo "2"
	elif [[ $MINUTE = 48 ]]
	then
	echo "3"
	elif [[ $MINUTE = 49 ]]
	then
	echo "3"
	elif [[ $MINUTE = 50 ]]
	then
	echo "3"
	elif [[ $MINUTE = 51 ]]
	then
	echo "3"
	elif [[ $MINUTE = 52 ]]
	then
	echo "3"
	elif [[ $MINUTE = 53 ]]
	then
	echo "3"
	elif [[ $MINUTE = 54 ]]
	then
	echo "3"
	elif [[ $MINUTE = 55 ]]
	then
	echo "3"
	elif [[ $MINUTE = 56 ]]
	then
	echo "3"
	elif [[ $MINUTE = 57 ]]
	then
	echo "3"
	elif [[ $MINUTE = 58 ]]
	then
	echo "3"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "3"
	fi
elif [[ $HOUR = 11 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "4"
	elif [[ $MINUTE = 01 ]]
	then
	echo "4"
	elif [[ $MINUTE = 02 ]]
	then
	echo "4"
	elif [[ $MINUTE = 03 ]]
	then
	echo "4"
	elif [[ $MINUTE = 04 ]]
	then
	echo "4"
	elif [[ $MINUTE = 05 ]]
	then
	echo "4"
	elif [[ $MINUTE = 06 ]]
	then
	echo "4"
	elif [[ $MINUTE = 07 ]]
	then
	echo "4"
	elif [[ $MINUTE = 08 ]]
	then
	echo "4"
	elif [[ $MINUTE = 09 ]]
	then
	echo "4"
	elif [[ $MINUTE = 10 ]]
	then
	echo "4"
	elif [[ $MINUTE = 11 ]]
	then
	echo "4"
	elif [[ $MINUTE = 12 ]]
	then
	echo "5"
	elif [[ $MINUTE = 13 ]]
	then
	echo "5"
	elif [[ $MINUTE = 14 ]]
	then
	echo "5"
	elif [[ $MINUTE = 15 ]]
	then
	echo "5"
	elif [[ $MINUTE = 16 ]]
	then
	echo "5"
	elif [[ $MINUTE = 17 ]]
	then
	echo "5"
	elif [[ $MINUTE = 18 ]]
	then
	echo "5"
	elif [[ $MINUTE = 19 ]]
	then
	echo "5"
	elif [[ $MINUTE = 20 ]]
	then
	echo "5"
	elif [[ $MINUTE = 21 ]]
	then
	echo "5"
	elif [[ $MINUTE = 22 ]]
	then
	echo "5"
	elif [[ $MINUTE = 23 ]]
	then
	echo "6"
	elif [[ $MINUTE = 24 ]]
	then
	echo "6"
	elif [[ $MINUTE = 25 ]]
	then
	echo "6"
	elif [[ $MINUTE = 26 ]]
	then
	echo "6"
	elif [[ $MINUTE = 27 ]]
	then
	echo "6"
	elif [[ $MINUTE = 28 ]]
	then
	echo "6"
	elif [[ $MINUTE = 29 ]]
	then
	echo "6"
	elif [[ $MINUTE = 30 ]]
	then
	echo "6"
	elif [[ $MINUTE = 31 ]]
	then
	echo "6"
	elif [[ $MINUTE = 32 ]]
	then
	echo "6"
	elif [[ $MINUTE = 33 ]]
	then
	echo "6"
	elif [[ $MINUTE = 34 ]]
	then
	echo "6"
	elif [[ $MINUTE = 35 ]]
	then
	echo "6"
	elif [[ $MINUTE = 36 ]]
	then
	echo "7"
	elif [[ $MINUTE = 37 ]]
	then
	echo "7"
	elif [[ $MINUTE = 38 ]]
	then
	echo "7"
	elif [[ $MINUTE = 39 ]]
	then
	echo "7"
	elif [[ $MINUTE = 40 ]]
	then
	echo "7"
	elif [[ $MINUTE = 41 ]]
	then
	echo "7"
	elif [[ $MINUTE = 42 ]]
	then
	echo "7"
	elif [[ $MINUTE = 43 ]]
	then
	echo "7"
	elif [[ $MINUTE = 44 ]]
	then
	echo "7"
	elif [[ $MINUTE = 45 ]]
	then
	echo "7"
	elif [[ $MINUTE = 46 ]]
	then
	echo "7"
	elif [[ $MINUTE = 47 ]]
	then
	echo "7"
	elif [[ $MINUTE = 48 ]]
	then
	echo "8"
	elif [[ $MINUTE = 49 ]]
	then
	echo "8"
	elif [[ $MINUTE = 50 ]]
	then
	echo "8"
	elif [[ $MINUTE = 51 ]]
	then
	echo "8"
	elif [[ $MINUTE = 52 ]]
	then
	echo "8"
	elif [[ $MINUTE = 53 ]]
	then
	echo "8"
	elif [[ $MINUTE = 54 ]]
	then
	echo "8"
	elif [[ $MINUTE = 55 ]]
	then
	echo "8"
	elif [[ $MINUTE = 56 ]]
	then
	echo "8"
	elif [[ $MINUTE = 57 ]]
	then
	echo "8"
	elif [[ $MINUTE = 58 ]]
	then
	echo "8"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "8"
	fi
elif [[ $HOUR = 12 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "A"
	elif [[ $MINUTE = 01 ]]
	then
	echo "A"
	elif [[ $MINUTE = 02 ]]
	then
	echo "A"
	elif [[ $MINUTE = 03 ]]
	then
	echo "A"
	elif [[ $MINUTE = 04 ]]
	then
	echo "A"
	elif [[ $MINUTE = 05 ]]
	then
	echo "A"
	elif [[ $MINUTE = 06 ]]
	then
	echo "A"
	elif [[ $MINUTE = 07 ]]
	then
	echo "A"
	elif [[ $MINUTE = 08 ]]
	then
	echo "A"
	elif [[ $MINUTE = 09 ]]
	then
	echo "A"
	elif [[ $MINUTE = 10 ]]
	then
	echo "A"
	elif [[ $MINUTE = 11 ]]
	then
	echo "A"
	elif [[ $MINUTE = 12 ]]
	then
	echo "B"
	elif [[ $MINUTE = 13 ]]
	then
	echo "B"
	elif [[ $MINUTE = 14 ]]
	then
	echo "B"
	elif [[ $MINUTE = 15 ]]
	then
	echo "B"
	elif [[ $MINUTE = 16 ]]
	then
	echo "B"
	elif [[ $MINUTE = 17 ]]
	then
	echo "B"
	elif [[ $MINUTE = 18 ]]
	then
	echo "B"
	elif [[ $MINUTE = 19 ]]
	then
	echo "B"
	elif [[ $MINUTE = 20 ]]
	then
	echo "B"
	elif [[ $MINUTE = 21 ]]
	then
	echo "B"
	elif [[ $MINUTE = 22 ]]
	then
	echo "B"
	elif [[ $MINUTE = 23 ]]
	then
	echo "C"
	elif [[ $MINUTE = 24 ]]
	then
	echo "C"
	elif [[ $MINUTE = 25 ]]
	then
	echo "C"
	elif [[ $MINUTE = 26 ]]
	then
	echo "C"
	elif [[ $MINUTE = 27 ]]
	then
	echo "C"
	elif [[ $MINUTE = 28 ]]
	then
	echo "C"
	elif [[ $MINUTE = 29 ]]
	then
	echo "C"
	elif [[ $MINUTE = 30 ]]
	then
	echo "C"
	elif [[ $MINUTE = 31 ]]
	then
	echo "C"
	elif [[ $MINUTE = 32 ]]
	then
	echo "C"
	elif [[ $MINUTE = 33 ]]
	then
	echo "C"
	elif [[ $MINUTE = 34 ]]
	then
	echo "C"
	elif [[ $MINUTE = 35 ]]
	then
	echo "C"
	elif [[ $MINUTE = 36 ]]
	then
	echo "D"
	elif [[ $MINUTE = 37 ]]
	then
	echo "D"
	elif [[ $MINUTE = 38 ]]
	then
	echo "D"
	elif [[ $MINUTE = 39 ]]
	then
	echo "D"
	elif [[ $MINUTE = 40 ]]
	then
	echo "D"
	elif [[ $MINUTE = 41 ]]
	then
	echo "D"
	elif [[ $MINUTE = 42 ]]
	then
	echo "D"
	elif [[ $MINUTE = 43 ]]
	then
	echo "D"
	elif [[ $MINUTE = 44 ]]
	then
	echo "D"
	elif [[ $MINUTE = 45 ]]
	then
	echo "D"
	elif [[ $MINUTE = 46 ]]
	then
	echo "D"
	elif [[ $MINUTE = 47 ]]
	then
	echo "D"
	elif [[ $MINUTE = 48 ]]
	then
	echo "E"
	elif [[ $MINUTE = 49 ]]
	then
	echo "E"
	elif [[ $MINUTE = 50 ]]
	then
	echo "E"
	elif [[ $MINUTE = 51 ]]
	then
	echo "E"
	elif [[ $MINUTE = 52 ]]
	then
	echo "E"
	elif [[ $MINUTE = 53 ]]
	then
	echo "E"
	elif [[ $MINUTE = 54 ]]
	then
	echo "E"
	elif [[ $MINUTE = 55 ]]
	then
	echo "E"
	elif [[ $MINUTE = 56 ]]
	then
	echo "E"
	elif [[ $MINUTE = 57 ]]
	then
	echo "E"
	elif [[ $MINUTE = 58 ]]
	then
	echo "E"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "E"
	fi
elif [[ $HOUR = 13 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "F"
	elif [[ $MINUTE = 01 ]]
	then
	echo "F"
	elif [[ $MINUTE = 02 ]]
	then
	echo "F"
	elif [[ $MINUTE = 03 ]]
	then
	echo "F"
	elif [[ $MINUTE = 04 ]]
	then
	echo "F"
	elif [[ $MINUTE = 05 ]]
	then
	echo "F"
	elif [[ $MINUTE = 06 ]]
	then
	echo "F"
	elif [[ $MINUTE = 07 ]]
	then
	echo "F"
	elif [[ $MINUTE = 08 ]]
	then
	echo "F"
	elif [[ $MINUTE = 09 ]]
	then
	echo "F"
	elif [[ $MINUTE = 10 ]]
	then
	echo "F"
	elif [[ $MINUTE = 11 ]]
	then
	echo "F"
	elif [[ $MINUTE = 12 ]]
	then
	echo "G"
	elif [[ $MINUTE = 13 ]]
	then
	echo "G"
	elif [[ $MINUTE = 14 ]]
	then
	echo "G"
	elif [[ $MINUTE = 15 ]]
	then
	echo "G"
	elif [[ $MINUTE = 16 ]]
	then
	echo "G"
	elif [[ $MINUTE = 17 ]]
	then
	echo "G"
	elif [[ $MINUTE = 18 ]]
	then
	echo "G"
	elif [[ $MINUTE = 19 ]]
	then
	echo "G"
	elif [[ $MINUTE = 20 ]]
	then
	echo "G"
	elif [[ $MINUTE = 21 ]]
	then
	echo "G"
	elif [[ $MINUTE = 22 ]]
	then
	echo "G"
	elif [[ $MINUTE = 23 ]]
	then
	echo "H"
	elif [[ $MINUTE = 24 ]]
	then
	echo "H"
	elif [[ $MINUTE = 25 ]]
	then
	echo "H"
	elif [[ $MINUTE = 26 ]]
	then
	echo "H"
	elif [[ $MINUTE = 27 ]]
	then
	echo "H"
	elif [[ $MINUTE = 28 ]]
	then
	echo "H"
	elif [[ $MINUTE = 29 ]]
	then
	echo "H"
	elif [[ $MINUTE = 30 ]]
	then
	echo "H"
	elif [[ $MINUTE = 31 ]]
	then
	echo "H"
	elif [[ $MINUTE = 32 ]]
	then
	echo "H"
	elif [[ $MINUTE = 33 ]]
	then
	echo "H"
	elif [[ $MINUTE = 34 ]]
	then
	echo "H"
	elif [[ $MINUTE = 35 ]]
	then
	echo "H"
	elif [[ $MINUTE = 36 ]]
	then
	echo "I"
	elif [[ $MINUTE = 37 ]]
	then
	echo "I"
	elif [[ $MINUTE = 38 ]]
	then
	echo "I"
	elif [[ $MINUTE = 39 ]]
	then
	echo "I"
	elif [[ $MINUTE = 40 ]]
	then
	echo "I"
	elif [[ $MINUTE = 41 ]]
	then
	echo "I"
	elif [[ $MINUTE = 42 ]]
	then
	echo "I"
	elif [[ $MINUTE = 43 ]]
	then
	echo "I"
	elif [[ $MINUTE = 44 ]]
	then
	echo "I"
	elif [[ $MINUTE = 45 ]]
	then
	echo "I"
	elif [[ $MINUTE = 46 ]]
	then
	echo "I"
	elif [[ $MINUTE = 47 ]]
	then
	echo "I"
	elif [[ $MINUTE = 48 ]]
	then
	echo "J"
	elif [[ $MINUTE = 49 ]]
	then
	echo "J"
	elif [[ $MINUTE = 50 ]]
	then
	echo "J"
	elif [[ $MINUTE = 51 ]]
	then
	echo "J"
	elif [[ $MINUTE = 52 ]]
	then
	echo "J"
	elif [[ $MINUTE = 53 ]]
	then
	echo "J"
	elif [[ $MINUTE = 54 ]]
	then
	echo "J"
	elif [[ $MINUTE = 55 ]]
	then
	echo "J"
	elif [[ $MINUTE = 56 ]]
	then
	echo "J"
	elif [[ $MINUTE = 57 ]]
	then
	echo "J"
	elif [[ $MINUTE = 58 ]]
	then
	echo "J"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "J"
	fi
elif [[ $HOUR = 14 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "K"
	elif [[ $MINUTE = 01 ]]
	then
	echo "K"
	elif [[ $MINUTE = 02 ]]
	then
	echo "K"
	elif [[ $MINUTE = 03 ]]
	then
	echo "K"
	elif [[ $MINUTE = 04 ]]
	then
	echo "K"
	elif [[ $MINUTE = 05 ]]
	then
	echo "K"
	elif [[ $MINUTE = 06 ]]
	then
	echo "K"
	elif [[ $MINUTE = 07 ]]
	then
	echo "K"
	elif [[ $MINUTE = 08 ]]
	then
	echo "K"
	elif [[ $MINUTE = 09 ]]
	then
	echo "K"
	elif [[ $MINUTE = 10 ]]
	then
	echo "K"
	elif [[ $MINUTE = 11 ]]
	then
	echo "K"
	elif [[ $MINUTE = 12 ]]
	then
	echo "L"
	elif [[ $MINUTE = 13 ]]
	then
	echo "L"
	elif [[ $MINUTE = 14 ]]
	then
	echo "L"
	elif [[ $MINUTE = 15 ]]
	then
	echo "L"
	elif [[ $MINUTE = 16 ]]
	then
	echo "L"
	elif [[ $MINUTE = 17 ]]
	then
	echo "L"
	elif [[ $MINUTE = 18 ]]
	then
	echo "L"
	elif [[ $MINUTE = 19 ]]
	then
	echo "L"
	elif [[ $MINUTE = 20 ]]
	then
	echo "L"
	elif [[ $MINUTE = 21 ]]
	then
	echo "L"
	elif [[ $MINUTE = 22 ]]
	then
	echo "L"
	elif [[ $MINUTE = 23 ]]
	then
	echo "M"
	elif [[ $MINUTE = 24 ]]
	then
	echo "M"
	elif [[ $MINUTE = 25 ]]
	then
	echo "M"
	elif [[ $MINUTE = 26 ]]
	then
	echo "M"
	elif [[ $MINUTE = 27 ]]
	then
	echo "M"
	elif [[ $MINUTE = 28 ]]
	then
	echo "M"
	elif [[ $MINUTE = 29 ]]
	then
	echo "M"
	elif [[ $MINUTE = 30 ]]
	then
	echo "M"
	elif [[ $MINUTE = 31 ]]
	then
	echo "M"
	elif [[ $MINUTE = 32 ]]
	then
	echo "M"
	elif [[ $MINUTE = 33 ]]
	then
	echo "M"
	elif [[ $MINUTE = 34 ]]
	then
	echo "M"
	elif [[ $MINUTE = 35 ]]
	then
	echo "M"
	elif [[ $MINUTE = 36 ]]
	then
	echo "N"
	elif [[ $MINUTE = 37 ]]
	then
	echo "N"
	elif [[ $MINUTE = 38 ]]
	then
	echo "N"
	elif [[ $MINUTE = 39 ]]
	then
	echo "N"
	elif [[ $MINUTE = 40 ]]
	then
	echo "N"
	elif [[ $MINUTE = 41 ]]
	then
	echo "N"
	elif [[ $MINUTE = 42 ]]
	then
	echo "N"
	elif [[ $MINUTE = 43 ]]
	then
	echo "N"
	elif [[ $MINUTE = 44 ]]
	then
	echo "N"
	elif [[ $MINUTE = 45 ]]
	then
	echo "N"
	elif [[ $MINUTE = 46 ]]
	then
	echo "N"
	elif [[ $MINUTE = 47 ]]
	then
	echo "N"
	elif [[ $MINUTE = 48 ]]
	then
	echo "O"
	elif [[ $MINUTE = 49 ]]
	then
	echo "O"
	elif [[ $MINUTE = 50 ]]
	then
	echo "O"
	elif [[ $MINUTE = 51 ]]
	then
	echo "O"
	elif [[ $MINUTE = 52 ]]
	then
	echo "O"
	elif [[ $MINUTE = 53 ]]
	then
	echo "O"
	elif [[ $MINUTE = 54 ]]
	then
	echo "O"
	elif [[ $MINUTE = 55 ]]
	then
	echo "O"
	elif [[ $MINUTE = 56 ]]
	then
	echo "O"
	elif [[ $MINUTE = 57 ]]
	then
	echo "O"
	elif [[ $MINUTE = 58 ]]
	then
	echo "O"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "O"
	fi
elif [[ $HOUR = 15 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "P"
	elif [[ $MINUTE = 01 ]]
	then
	echo "P"
	elif [[ $MINUTE = 02 ]]
	then
	echo "P"
	elif [[ $MINUTE = 03 ]]
	then
	echo "P"
	elif [[ $MINUTE = 04 ]]
	then
	echo "P"
	elif [[ $MINUTE = 05 ]]
	then
	echo "P"
	elif [[ $MINUTE = 06 ]]
	then
	echo "P"
	elif [[ $MINUTE = 07 ]]
	then
	echo "P"
	elif [[ $MINUTE = 08 ]]
	then
	echo "P"
	elif [[ $MINUTE = 09 ]]
	then
	echo "P"
	elif [[ $MINUTE = 10 ]]
	then
	echo "P"
	elif [[ $MINUTE = 11 ]]
	then
	echo "P"
	elif [[ $MINUTE = 12 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 13 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 14 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 15 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 16 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 17 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 18 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 19 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 20 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 21 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 22 ]]
	then
	echo "Q"
	elif [[ $MINUTE = 23 ]]
	then
	echo "R"
	elif [[ $MINUTE = 24 ]]
	then
	echo "R"
	elif [[ $MINUTE = 25 ]]
	then
	echo "R"
	elif [[ $MINUTE = 26 ]]
	then
	echo "R"
	elif [[ $MINUTE = 27 ]]
	then
	echo "R"
	elif [[ $MINUTE = 28 ]]
	then
	echo "R"
	elif [[ $MINUTE = 29 ]]
	then
	echo "R"
	elif [[ $MINUTE = 30 ]]
	then
	echo "R"
	elif [[ $MINUTE = 31 ]]
	then
	echo "R"
	elif [[ $MINUTE = 32 ]]
	then
	echo "R"
	elif [[ $MINUTE = 33 ]]
	then
	echo "R"
	elif [[ $MINUTE = 34 ]]
	then
	echo "R"
	elif [[ $MINUTE = 35 ]]
	then
	echo "R"
	elif [[ $MINUTE = 36 ]]
	then
	echo "S"
	elif [[ $MINUTE = 37 ]]
	then
	echo "S"
	elif [[ $MINUTE = 38 ]]
	then
	echo "S"
	elif [[ $MINUTE = 39 ]]
	then
	echo "S"
	elif [[ $MINUTE = 40 ]]
	then
	echo "S"
	elif [[ $MINUTE = 41 ]]
	then
	echo "S"
	elif [[ $MINUTE = 42 ]]
	then
	echo "S"
	elif [[ $MINUTE = 43 ]]
	then
	echo "S"
	elif [[ $MINUTE = 44 ]]
	then
	echo "S"
	elif [[ $MINUTE = 45 ]]
	then
	echo "S"
	elif [[ $MINUTE = 46 ]]
	then
	echo "S"
	elif [[ $MINUTE = 47 ]]
	then
	echo "S"
	elif [[ $MINUTE = 48 ]]
	then
	echo "T"
	elif [[ $MINUTE = 49 ]]
	then
	echo "T"
	elif [[ $MINUTE = 50 ]]
	then
	echo "T"
	elif [[ $MINUTE = 51 ]]
	then
	echo "T"
	elif [[ $MINUTE = 52 ]]
	then
	echo "T"
	elif [[ $MINUTE = 53 ]]
	then
	echo "T"
	elif [[ $MINUTE = 54 ]]
	then
	echo "T"
	elif [[ $MINUTE = 55 ]]
	then
	echo "T"
	elif [[ $MINUTE = 56 ]]
	then
	echo "T"
	elif [[ $MINUTE = 57 ]]
	then
	echo "T"
	elif [[ $MINUTE = 58 ]]
	then
	echo "T"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "T"
	fi
elif [[ $HOUR = 16 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "U"
	elif [[ $MINUTE = 01 ]]
	then
	echo "U"
	elif [[ $MINUTE = 02 ]]
	then
	echo "U"
	elif [[ $MINUTE = 03 ]]
	then
	echo "U"
	elif [[ $MINUTE = 04 ]]
	then
	echo "U"
	elif [[ $MINUTE = 05 ]]
	then
	echo "U"
	elif [[ $MINUTE = 06 ]]
	then
	echo "U"
	elif [[ $MINUTE = 07 ]]
	then
	echo "U"
	elif [[ $MINUTE = 08 ]]
	then
	echo "U"
	elif [[ $MINUTE = 09 ]]
	then
	echo "U"
	elif [[ $MINUTE = 10 ]]
	then
	echo "U"
	elif [[ $MINUTE = 11 ]]
	then
	echo "U"
	elif [[ $MINUTE = 12 ]]
	then
	echo "V"
	elif [[ $MINUTE = 13 ]]
	then
	echo "V"
	elif [[ $MINUTE = 14 ]]
	then
	echo "V"
	elif [[ $MINUTE = 15 ]]
	then
	echo "V"
	elif [[ $MINUTE = 16 ]]
	then
	echo "V"
	elif [[ $MINUTE = 17 ]]
	then
	echo "V"
	elif [[ $MINUTE = 18 ]]
	then
	echo "V"
	elif [[ $MINUTE = 19 ]]
	then
	echo "V"
	elif [[ $MINUTE = 20 ]]
	then
	echo "V"
	elif [[ $MINUTE = 21 ]]
	then
	echo "V"
	elif [[ $MINUTE = 22 ]]
	then
	echo "V"
	elif [[ $MINUTE = 23 ]]
	then
	echo "W"
	elif [[ $MINUTE = 24 ]]
	then
	echo "W"
	elif [[ $MINUTE = 25 ]]
	then
	echo "W"
	elif [[ $MINUTE = 26 ]]
	then
	echo "W"
	elif [[ $MINUTE = 27 ]]
	then
	echo "W"
	elif [[ $MINUTE = 28 ]]
	then
	echo "W"
	elif [[ $MINUTE = 29 ]]
	then
	echo "W"
	elif [[ $MINUTE = 30 ]]
	then
	echo "W"
	elif [[ $MINUTE = 31 ]]
	then
	echo "W"
	elif [[ $MINUTE = 32 ]]
	then
	echo "W"
	elif [[ $MINUTE = 33 ]]
	then
	echo "W"
	elif [[ $MINUTE = 34 ]]
	then
	echo "W"
	elif [[ $MINUTE = 35 ]]
	then
	echo "W"
	elif [[ $MINUTE = 36 ]]
	then
	echo "X"
	elif [[ $MINUTE = 37 ]]
	then
	echo "X"
	elif [[ $MINUTE = 38 ]]
	then
	echo "X"
	elif [[ $MINUTE = 39 ]]
	then
	echo "X"
	elif [[ $MINUTE = 40 ]]
	then
	echo "X"
	elif [[ $MINUTE = 41 ]]
	then
	echo "X"
	elif [[ $MINUTE = 42 ]]
	then
	echo "X"
	elif [[ $MINUTE = 43 ]]
	then
	echo "X"
	elif [[ $MINUTE = 44 ]]
	then
	echo "X"
	elif [[ $MINUTE = 45 ]]
	then
	echo "X"
	elif [[ $MINUTE = 46 ]]
	then
	echo "X"
	elif [[ $MINUTE = 47 ]]
	then
	echo "X"
	elif [[ $MINUTE = 48 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 49 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 50 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 51 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 52 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 53 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 54 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 55 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 56 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 57 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 58 ]]
	then
	echo "Y"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "Y"
	fi
elif [[ $HOUR = 17 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 01 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 02 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 03 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 04 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 05 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 06 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 07 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 08 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 09 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 10 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 11 ]]
	then
	echo "Z"
	elif [[ $MINUTE = 12 ]]
	then
	echo "a"
	elif [[ $MINUTE = 13 ]]
	then
	echo "a"
	elif [[ $MINUTE = 14 ]]
	then
	echo "a"
	elif [[ $MINUTE = 15 ]]
	then
	echo "a"
	elif [[ $MINUTE = 16 ]]
	then
	echo "a"
	elif [[ $MINUTE = 17 ]]
	then
	echo "a"
	elif [[ $MINUTE = 18 ]]
	then
	echo "a"
	elif [[ $MINUTE = 19 ]]
	then
	echo "a"
	elif [[ $MINUTE = 20 ]]
	then
	echo "a"
	elif [[ $MINUTE = 21 ]]
	then
	echo "a"
	elif [[ $MINUTE = 22 ]]
	then
	echo "a"
	elif [[ $MINUTE = 23 ]]
	then
	echo "b"
	elif [[ $MINUTE = 24 ]]
	then
	echo "b"
	elif [[ $MINUTE = 25 ]]
	then
	echo "b"
	elif [[ $MINUTE = 26 ]]
	then
	echo "b"
	elif [[ $MINUTE = 27 ]]
	then
	echo "b"
	elif [[ $MINUTE = 28 ]]
	then
	echo "b"
	elif [[ $MINUTE = 29 ]]
	then
	echo "b"
	elif [[ $MINUTE = 30 ]]
	then
	echo "b"
	elif [[ $MINUTE = 31 ]]
	then
	echo "b"
	elif [[ $MINUTE = 32 ]]
	then
	echo "b"
	elif [[ $MINUTE = 33 ]]
	then
	echo "b"
	elif [[ $MINUTE = 34 ]]
	then
	echo "b"
	elif [[ $MINUTE = 35 ]]
	then
	echo "b"
	elif [[ $MINUTE = 36 ]]
	then
	echo "c"
	elif [[ $MINUTE = 37 ]]
	then
	echo "c"
	elif [[ $MINUTE = 38 ]]
	then
	echo "c"
	elif [[ $MINUTE = 39 ]]
	then
	echo "c"
	elif [[ $MINUTE = 40 ]]
	then
	echo "c"
	elif [[ $MINUTE = 41 ]]
	then
	echo "c"
	elif [[ $MINUTE = 42 ]]
	then
	echo "c"
	elif [[ $MINUTE = 43 ]]
	then
	echo "c"
	elif [[ $MINUTE = 44 ]]
	then
	echo "c"
	elif [[ $MINUTE = 45 ]]
	then
	echo "c"
	elif [[ $MINUTE = 46 ]]
	then
	echo "c"
	elif [[ $MINUTE = 47 ]]
	then
	echo "c"
	elif [[ $MINUTE = 48 ]]
	then
	echo "d"
	elif [[ $MINUTE = 49 ]]
	then
	echo "d"
	elif [[ $MINUTE = 50 ]]
	then
	echo "d"
	elif [[ $MINUTE = 51 ]]
	then
	echo "d"
	elif [[ $MINUTE = 52 ]]
	then
	echo "d"
	elif [[ $MINUTE = 53 ]]
	then
	echo "d"
	elif [[ $MINUTE = 54 ]]
	then
	echo "d"
	elif [[ $MINUTE = 55 ]]
	then
	echo "d"
	elif [[ $MINUTE = 56 ]]
	then
	echo "d"
	elif [[ $MINUTE = 57 ]]
	then
	echo "d"
	elif [[ $MINUTE = 58 ]]
	then
	echo "d"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "d"
	fi
elif [[ $HOUR = 18 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "e"
	elif [[ $MINUTE = 01 ]]
	then
	echo "e"
	elif [[ $MINUTE = 02 ]]
	then
	echo "e"
	elif [[ $MINUTE = 03 ]]
	then
	echo "e"
	elif [[ $MINUTE = 04 ]]
	then
	echo "e"
	elif [[ $MINUTE = 05 ]]
	then
	echo "e"
	elif [[ $MINUTE = 06 ]]
	then
	echo "e"
	elif [[ $MINUTE = 07 ]]
	then
	echo "e"
	elif [[ $MINUTE = 08 ]]
	then
	echo "e"
	elif [[ $MINUTE = 09 ]]
	then
	echo "e"
	elif [[ $MINUTE = 10 ]]
	then
	echo "e"
	elif [[ $MINUTE = 11 ]]
	then
	echo "e"
	elif [[ $MINUTE = 12 ]]
	then
	echo "f"
	elif [[ $MINUTE = 13 ]]
	then
	echo "f"
	elif [[ $MINUTE = 14 ]]
	then
	echo "f"
	elif [[ $MINUTE = 15 ]]
	then
	echo "f"
	elif [[ $MINUTE = 16 ]]
	then
	echo "f"
	elif [[ $MINUTE = 17 ]]
	then
	echo "f"
	elif [[ $MINUTE = 18 ]]
	then
	echo "f"
	elif [[ $MINUTE = 19 ]]
	then
	echo "f"
	elif [[ $MINUTE = 20 ]]
	then
	echo "f"
	elif [[ $MINUTE = 21 ]]
	then
	echo "f"
	elif [[ $MINUTE = 22 ]]
	then
	echo "f"
	elif [[ $MINUTE = 23 ]]
	then
	echo "g"
	elif [[ $MINUTE = 24 ]]
	then
	echo "g"
	elif [[ $MINUTE = 25 ]]
	then
	echo "g"
	elif [[ $MINUTE = 26 ]]
	then
	echo "g"
	elif [[ $MINUTE = 27 ]]
	then
	echo "g"
	elif [[ $MINUTE = 28 ]]
	then
	echo "g"
	elif [[ $MINUTE = 29 ]]
	then
	echo "g"
	elif [[ $MINUTE = 30 ]]
	then
	echo "g"
	elif [[ $MINUTE = 31 ]]
	then
	echo "g"
	elif [[ $MINUTE = 32 ]]
	then
	echo "g"
	elif [[ $MINUTE = 33 ]]
	then
	echo "g"
	elif [[ $MINUTE = 34 ]]
	then
	echo "g"
	elif [[ $MINUTE = 35 ]]
	then
	echo "g"
	elif [[ $MINUTE = 36 ]]
	then
	echo "h"
	elif [[ $MINUTE = 37 ]]
	then
	echo "h"
	elif [[ $MINUTE = 38 ]]
	then
	echo "h"
	elif [[ $MINUTE = 39 ]]
	then
	echo "h"
	elif [[ $MINUTE = 40 ]]
	then
	echo "h"
	elif [[ $MINUTE = 41 ]]
	then
	echo "h"
	elif [[ $MINUTE = 42 ]]
	then
	echo "h"
	elif [[ $MINUTE = 43 ]]
	then
	echo "h"
	elif [[ $MINUTE = 44 ]]
	then
	echo "h"
	elif [[ $MINUTE = 45 ]]
	then
	echo "h"
	elif [[ $MINUTE = 46 ]]
	then
	echo "h"
	elif [[ $MINUTE = 47 ]]
	then
	echo "h"
	elif [[ $MINUTE = 48 ]]
	then
	echo "i"
	elif [[ $MINUTE = 49 ]]
	then
	echo "i"
	elif [[ $MINUTE = 50 ]]
	then
	echo "i"
	elif [[ $MINUTE = 51 ]]
	then
	echo "i"
	elif [[ $MINUTE = 52 ]]
	then
	echo "i"
	elif [[ $MINUTE = 53 ]]
	then
	echo "i"
	elif [[ $MINUTE = 54 ]]
	then
	echo "i"
	elif [[ $MINUTE = 55 ]]
	then
	echo "i"
	elif [[ $MINUTE = 56 ]]
	then
	echo "i"
	elif [[ $MINUTE = 57 ]]
	then
	echo "i"
	elif [[ $MINUTE = 58 ]]
	then
	echo "i"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "i"
	fi
elif [[ $HOUR = 19 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "j"
	elif [[ $MINUTE = 01 ]]
	then
	echo "j"
	elif [[ $MINUTE = 02 ]]
	then
	echo "j"
	elif [[ $MINUTE = 03 ]]
	then
	echo "j"
	elif [[ $MINUTE = 04 ]]
	then
	echo "j"
	elif [[ $MINUTE = 05 ]]
	then
	echo "j"
	elif [[ $MINUTE = 06 ]]
	then
	echo "j"
	elif [[ $MINUTE = 07 ]]
	then
	echo "j"
	elif [[ $MINUTE = 08 ]]
	then
	echo "j"
	elif [[ $MINUTE = 09 ]]
	then
	echo "j"
	elif [[ $MINUTE = 10 ]]
	then
	echo "j"
	elif [[ $MINUTE = 11 ]]
	then
	echo "j"
	elif [[ $MINUTE = 12 ]]
	then
	echo "k"
	elif [[ $MINUTE = 13 ]]
	then
	echo "k"
	elif [[ $MINUTE = 14 ]]
	then
	echo "k"
	elif [[ $MINUTE = 15 ]]
	then
	echo "k"
	elif [[ $MINUTE = 16 ]]
	then
	echo "k"
	elif [[ $MINUTE = 17 ]]
	then
	echo "k"
	elif [[ $MINUTE = 18 ]]
	then
	echo "k"
	elif [[ $MINUTE = 19 ]]
	then
	echo "k"
	elif [[ $MINUTE = 20 ]]
	then
	echo "k"
	elif [[ $MINUTE = 21 ]]
	then
	echo "k"
	elif [[ $MINUTE = 22 ]]
	then
	echo "k"
	elif [[ $MINUTE = 23 ]]
	then
	echo "l"
	elif [[ $MINUTE = 24 ]]
	then
	echo "l"
	elif [[ $MINUTE = 25 ]]
	then
	echo "l"
	elif [[ $MINUTE = 26 ]]
	then
	echo "l"
	elif [[ $MINUTE = 27 ]]
	then
	echo "l"
	elif [[ $MINUTE = 28 ]]
	then
	echo "l"
	elif [[ $MINUTE = 29 ]]
	then
	echo "l"
	elif [[ $MINUTE = 30 ]]
	then
	echo "l"
	elif [[ $MINUTE = 31 ]]
	then
	echo "l"
	elif [[ $MINUTE = 32 ]]
	then
	echo "l"
	elif [[ $MINUTE = 33 ]]
	then
	echo "l"
	elif [[ $MINUTE = 34 ]]
	then
	echo "l"
	elif [[ $MINUTE = 35 ]]
	then
	echo "l"
	elif [[ $MINUTE = 36 ]]
	then
	echo "m"
	elif [[ $MINUTE = 37 ]]
	then
	echo "m"
	elif [[ $MINUTE = 38 ]]
	then
	echo "m"
	elif [[ $MINUTE = 39 ]]
	then
	echo "m"
	elif [[ $MINUTE = 40 ]]
	then
	echo "m"
	elif [[ $MINUTE = 41 ]]
	then
	echo "m"
	elif [[ $MINUTE = 42 ]]
	then
	echo "m"
	elif [[ $MINUTE = 43 ]]
	then
	echo "m"
	elif [[ $MINUTE = 44 ]]
	then
	echo "m"
	elif [[ $MINUTE = 45 ]]
	then
	echo "m"
	elif [[ $MINUTE = 46 ]]
	then
	echo "m"
	elif [[ $MINUTE = 47 ]]
	then
	echo "m"
	elif [[ $MINUTE = 48 ]]
	then
	echo "n"
	elif [[ $MINUTE = 49 ]]
	then
	echo "n"
	elif [[ $MINUTE = 50 ]]
	then
	echo "n"
	elif [[ $MINUTE = 51 ]]
	then
	echo "n"
	elif [[ $MINUTE = 52 ]]
	then
	echo "n"
	elif [[ $MINUTE = 53 ]]
	then
	echo "n"
	elif [[ $MINUTE = 54 ]]
	then
	echo "n"
	elif [[ $MINUTE = 55 ]]
	then
	echo "n"
	elif [[ $MINUTE = 56 ]]
	then
	echo "n"
	elif [[ $MINUTE = 57 ]]
	then
	echo "n"
	elif [[ $MINUTE = 58 ]]
	then
	echo "n"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "n"
	fi
elif [[ $HOUR = 20 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "o"
	elif [[ $MINUTE = 01 ]]
	then
	echo "o"
	elif [[ $MINUTE = 02 ]]
	then
	echo "o"
	elif [[ $MINUTE = 03 ]]
	then
	echo "o"
	elif [[ $MINUTE = 04 ]]
	then
	echo "o"
	elif [[ $MINUTE = 05 ]]
	then
	echo "o"
	elif [[ $MINUTE = 06 ]]
	then
	echo "o"
	elif [[ $MINUTE = 07 ]]
	then
	echo "o"
	elif [[ $MINUTE = 08 ]]
	then
	echo "o"
	elif [[ $MINUTE = 09 ]]
	then
	echo "o"
	elif [[ $MINUTE = 10 ]]
	then
	echo "o"
	elif [[ $MINUTE = 11 ]]
	then
	echo "o"
	elif [[ $MINUTE = 12 ]]
	then
	echo "p"
	elif [[ $MINUTE = 13 ]]
	then
	echo "p"
	elif [[ $MINUTE = 14 ]]
	then
	echo "p"
	elif [[ $MINUTE = 15 ]]
	then
	echo "p"
	elif [[ $MINUTE = 16 ]]
	then
	echo "p"
	elif [[ $MINUTE = 17 ]]
	then
	echo "p"
	elif [[ $MINUTE = 18 ]]
	then
	echo "p"
	elif [[ $MINUTE = 19 ]]
	then
	echo "p"
	elif [[ $MINUTE = 20 ]]
	then
	echo "p"
	elif [[ $MINUTE = 21 ]]
	then
	echo "p"
	elif [[ $MINUTE = 22 ]]
	then
	echo "p"
	elif [[ $MINUTE = 23 ]]
	then
	echo "q"
	elif [[ $MINUTE = 24 ]]
	then
	echo "q"
	elif [[ $MINUTE = 25 ]]
	then
	echo "q"
	elif [[ $MINUTE = 26 ]]
	then
	echo "q"
	elif [[ $MINUTE = 27 ]]
	then
	echo "q"
	elif [[ $MINUTE = 28 ]]
	then
	echo "q"
	elif [[ $MINUTE = 29 ]]
	then
	echo "q"
	elif [[ $MINUTE = 30 ]]
	then
	echo "q"
	elif [[ $MINUTE = 31 ]]
	then
	echo "q"
	elif [[ $MINUTE = 32 ]]
	then
	echo "q"
	elif [[ $MINUTE = 33 ]]
	then
	echo "q"
	elif [[ $MINUTE = 34 ]]
	then
	echo "q"
	elif [[ $MINUTE = 35 ]]
	then
	echo "q"
	elif [[ $MINUTE = 36 ]]
	then
	echo "r"
	elif [[ $MINUTE = 37 ]]
	then
	echo "r"
	elif [[ $MINUTE = 38 ]]
	then
	echo "r"
	elif [[ $MINUTE = 39 ]]
	then
	echo "r"
	elif [[ $MINUTE = 40 ]]
	then
	echo "r"
	elif [[ $MINUTE = 41 ]]
	then
	echo "r"
	elif [[ $MINUTE = 42 ]]
	then
	echo "r"
	elif [[ $MINUTE = 43 ]]
	then
	echo "r"
	elif [[ $MINUTE = 44 ]]
	then
	echo "r"
	elif [[ $MINUTE = 45 ]]
	then
	echo "r"
	elif [[ $MINUTE = 46 ]]
	then
	echo "r"
	elif [[ $MINUTE = 47 ]]
	then
	echo "r"
	elif [[ $MINUTE = 48 ]]
	then
	echo "s"
	elif [[ $MINUTE = 49 ]]
	then
	echo "s"
	elif [[ $MINUTE = 50 ]]
	then
	echo "s"
	elif [[ $MINUTE = 51 ]]
	then
	echo "s"
	elif [[ $MINUTE = 52 ]]
	then
	echo "s"
	elif [[ $MINUTE = 53 ]]
	then
	echo "s"
	elif [[ $MINUTE = 54 ]]
	then
	echo "s"
	elif [[ $MINUTE = 55 ]]
	then
	echo "s"
	elif [[ $MINUTE = 56 ]]
	then
	echo "s"
	elif [[ $MINUTE = 57 ]]
	then
	echo "s"
	elif [[ $MINUTE = 58 ]]
	then
	echo "s"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "s"
	fi
elif [[ $HOUR = 21 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "t"
	elif [[ $MINUTE = 01 ]]
	then
	echo "t"
	elif [[ $MINUTE = 02 ]]
	then
	echo "t"
	elif [[ $MINUTE = 03 ]]
	then
	echo "t"
	elif [[ $MINUTE = 04 ]]
	then
	echo "t"
	elif [[ $MINUTE = 05 ]]
	then
	echo "t"
	elif [[ $MINUTE = 06 ]]
	then
	echo "t"
	elif [[ $MINUTE = 07 ]]
	then
	echo "t"
	elif [[ $MINUTE = 08 ]]
	then
	echo "t"
	elif [[ $MINUTE = 09 ]]
	then
	echo "t"
	elif [[ $MINUTE = 10 ]]
	then
	echo "t"
	elif [[ $MINUTE = 11 ]]
	then
	echo "t"
	elif [[ $MINUTE = 12 ]]
	then
	echo "u"
	elif [[ $MINUTE = 13 ]]
	then
	echo "u"
	elif [[ $MINUTE = 14 ]]
	then
	echo "u"
	elif [[ $MINUTE = 15 ]]
	then
	echo "u"
	elif [[ $MINUTE = 16 ]]
	then
	echo "u"
	elif [[ $MINUTE = 17 ]]
	then
	echo "u"
	elif [[ $MINUTE = 18 ]]
	then
	echo "u"
	elif [[ $MINUTE = 19 ]]
	then
	echo "u"
	elif [[ $MINUTE = 20 ]]
	then
	echo "u"
	elif [[ $MINUTE = 21 ]]
	then
	echo "u"
	elif [[ $MINUTE = 22 ]]
	then
	echo "u"
	elif [[ $MINUTE = 23 ]]
	then
	echo "v"
	elif [[ $MINUTE = 24 ]]
	then
	echo "v"
	elif [[ $MINUTE = 25 ]]
	then
	echo "v"
	elif [[ $MINUTE = 26 ]]
	then
	echo "v"
	elif [[ $MINUTE = 27 ]]
	then
	echo "v"
	elif [[ $MINUTE = 28 ]]
	then
	echo "v"
	elif [[ $MINUTE = 29 ]]
	then
	echo "v"
	elif [[ $MINUTE = 30 ]]
	then
	echo "v"
	elif [[ $MINUTE = 31 ]]
	then
	echo "v"
	elif [[ $MINUTE = 32 ]]
	then
	echo "v"
	elif [[ $MINUTE = 33 ]]
	then
	echo "v"
	elif [[ $MINUTE = 34 ]]
	then
	echo "v"
	elif [[ $MINUTE = 35 ]]
	then
	echo "v"
	elif [[ $MINUTE = 36 ]]
	then
	echo "w"
	elif [[ $MINUTE = 37 ]]
	then
	echo "w"
	elif [[ $MINUTE = 38 ]]
	then
	echo "w"
	elif [[ $MINUTE = 39 ]]
	then
	echo "w"
	elif [[ $MINUTE = 40 ]]
	then
	echo "w"
	elif [[ $MINUTE = 41 ]]
	then
	echo "w"
	elif [[ $MINUTE = 42 ]]
	then
	echo "w"
	elif [[ $MINUTE = 43 ]]
	then
	echo "w"
	elif [[ $MINUTE = 44 ]]
	then
	echo "w"
	elif [[ $MINUTE = 45 ]]
	then
	echo "w"
	elif [[ $MINUTE = 46 ]]
	then
	echo "w"
	elif [[ $MINUTE = 47 ]]
	then
	echo "w"
	elif [[ $MINUTE = 48 ]]
	then
	echo "x"
	elif [[ $MINUTE = 49 ]]
	then
	echo "x"
	elif [[ $MINUTE = 50 ]]
	then
	echo "x"
	elif [[ $MINUTE = 51 ]]
	then
	echo "x"
	elif [[ $MINUTE = 52 ]]
	then
	echo "x"
	elif [[ $MINUTE = 53 ]]
	then
	echo "x"
	elif [[ $MINUTE = 54 ]]
	then
	echo "x"
	elif [[ $MINUTE = 55 ]]
	then
	echo "x"
	elif [[ $MINUTE = 56 ]]
	then
	echo "x"
	elif [[ $MINUTE = 57 ]]
	then
	echo "x"
	elif [[ $MINUTE = 58 ]]
	then
	echo "x"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "x"
	fi
elif [[ $HOUR = 22 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "y"
	elif [[ $MINUTE = 01 ]]
	then
	echo "y"
	elif [[ $MINUTE = 02 ]]
	then
	echo "y"
	elif [[ $MINUTE = 03 ]]
	then
	echo "y"
	elif [[ $MINUTE = 04 ]]
	then
	echo "y"
	elif [[ $MINUTE = 05 ]]
	then
	echo "y"
	elif [[ $MINUTE = 06 ]]
	then
	echo "y"
	elif [[ $MINUTE = 07 ]]
	then
	echo "y"
	elif [[ $MINUTE = 08 ]]
	then
	echo "y"
	elif [[ $MINUTE = 09 ]]
	then
	echo "y"
	elif [[ $MINUTE = 10 ]]
	then
	echo "y"
	elif [[ $MINUTE = 11 ]]
	then
	echo "y"
	elif [[ $MINUTE = 12 ]]
	then
	echo "z"
	elif [[ $MINUTE = 13 ]]
	then
	echo "z"
	elif [[ $MINUTE = 14 ]]
	then
	echo "z"
	elif [[ $MINUTE = 15 ]]
	then
	echo "z"
	elif [[ $MINUTE = 16 ]]
	then
	echo "z"
	elif [[ $MINUTE = 17 ]]
	then
	echo "z"
	elif [[ $MINUTE = 18 ]]
	then
	echo "z"
	elif [[ $MINUTE = 19 ]]
	then
	echo "z"
	elif [[ $MINUTE = 20 ]]
	then
	echo "z"
	elif [[ $MINUTE = 21 ]]
	then
	echo "z"
	elif [[ $MINUTE = 22 ]]
	then
	echo "z"
	elif [[ $MINUTE = 23 ]]
	then
	echo "1"
	elif [[ $MINUTE = 24 ]]
	then
	echo "1"
	elif [[ $MINUTE = 25 ]]
	then
	echo "1"
	elif [[ $MINUTE = 26 ]]
	then
	echo "1"
	elif [[ $MINUTE = 27 ]]
	then
	echo "1"
	elif [[ $MINUTE = 28 ]]
	then
	echo "1"
	elif [[ $MINUTE = 29 ]]
	then
	echo "1"
	elif [[ $MINUTE = 30 ]]
	then
	echo "1"
	elif [[ $MINUTE = 31 ]]
	then
	echo "1"
	elif [[ $MINUTE = 32 ]]
	then
	echo "1"
	elif [[ $MINUTE = 33 ]]
	then
	echo "1"
	elif [[ $MINUTE = 34 ]]
	then
	echo "1"
	elif [[ $MINUTE = 35 ]]
	then
	echo "1"
	elif [[ $MINUTE = 36 ]]
	then
	echo "2"
	elif [[ $MINUTE = 37 ]]
	then
	echo "2"
	elif [[ $MINUTE = 38 ]]
	then
	echo "2"
	elif [[ $MINUTE = 39 ]]
	then
	echo "2"
	elif [[ $MINUTE = 40 ]]
	then
	echo "2"
	elif [[ $MINUTE = 41 ]]
	then
	echo "2"
	elif [[ $MINUTE = 42 ]]
	then
	echo "2"
	elif [[ $MINUTE = 43 ]]
	then
	echo "2"
	elif [[ $MINUTE = 44 ]]
	then
	echo "2"
	elif [[ $MINUTE = 45 ]]
	then
	echo "2"
	elif [[ $MINUTE = 46 ]]
	then
	echo "2"
	elif [[ $MINUTE = 47 ]]
	then
	echo "2"
	elif [[ $MINUTE = 48 ]]
	then
	echo "3"
	elif [[ $MINUTE = 49 ]]
	then
	echo "3"
	elif [[ $MINUTE = 50 ]]
	then
	echo "3"
	elif [[ $MINUTE = 51 ]]
	then
	echo "3"
	elif [[ $MINUTE = 52 ]]
	then
	echo "3"
	elif [[ $MINUTE = 53 ]]
	then
	echo "3"
	elif [[ $MINUTE = 54 ]]
	then
	echo "3"
	elif [[ $MINUTE = 55 ]]
	then
	echo "3"
	elif [[ $MINUTE = 56 ]]
	then
	echo "3"
	elif [[ $MINUTE = 57 ]]
	then
	echo "3"
	elif [[ $MINUTE = 58 ]]
	then
	echo "3"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "3"
	fi
elif [[ $HOUR = 23 ]]; then
	if [[ $MINUTE = 00 ]]
	then
	echo "4"
	elif [[ $MINUTE = 01 ]]
	then
	echo "4"
	elif [[ $MINUTE = 02 ]]
	then
	echo "4"
	elif [[ $MINUTE = 03 ]]
	then
	echo "4"
	elif [[ $MINUTE = 04 ]]
	then
	echo "4"
	elif [[ $MINUTE = 05 ]]
	then
	echo "4"
	elif [[ $MINUTE = 06 ]]
	then
	echo "4"
	elif [[ $MINUTE = 07 ]]
	then
	echo "4"
	elif [[ $MINUTE = 08 ]]
	then
	echo "4"
	elif [[ $MINUTE = 09 ]]
	then
	echo "4"
	elif [[ $MINUTE = 10 ]]
	then
	echo "4"
	elif [[ $MINUTE = 11 ]]
	then
	echo "4"
	elif [[ $MINUTE = 12 ]]
	then
	echo "5"
	elif [[ $MINUTE = 13 ]]
	then
	echo "5"
	elif [[ $MINUTE = 14 ]]
	then
	echo "5"
	elif [[ $MINUTE = 15 ]]
	then
	echo "5"
	elif [[ $MINUTE = 16 ]]
	then
	echo "5"
	elif [[ $MINUTE = 17 ]]
	then
	echo "5"
	elif [[ $MINUTE = 18 ]]
	then
	echo "5"
	elif [[ $MINUTE = 19 ]]
	then
	echo "5"
	elif [[ $MINUTE = 20 ]]
	then
	echo "5"
	elif [[ $MINUTE = 21 ]]
	then
	echo "5"
	elif [[ $MINUTE = 22 ]]
	then
	echo "5"
	elif [[ $MINUTE = 23 ]]
	then
	echo "6"
	elif [[ $MINUTE = 24 ]]
	then
	echo "6"
	elif [[ $MINUTE = 25 ]]
	then
	echo "6"
	elif [[ $MINUTE = 26 ]]
	then
	echo "6"
	elif [[ $MINUTE = 27 ]]
	then
	echo "6"
	elif [[ $MINUTE = 28 ]]
	then
	echo "6"
	elif [[ $MINUTE = 29 ]]
	then
	echo "6"
	elif [[ $MINUTE = 30 ]]
	then
	echo "6"
	elif [[ $MINUTE = 31 ]]
	then
	echo "6"
	elif [[ $MINUTE = 32 ]]
	then
	echo "6"
	elif [[ $MINUTE = 33 ]]
	then
	echo "6"
	elif [[ $MINUTE = 34 ]]
	then
	echo "6"
	elif [[ $MINUTE = 35 ]]
	then
	echo "6"
	elif [[ $MINUTE = 36 ]]
	then
	echo "7"
	elif [[ $MINUTE = 37 ]]
	then
	echo "7"
	elif [[ $MINUTE = 38 ]]
	then
	echo "7"
	elif [[ $MINUTE = 39 ]]
	then
	echo "7"
	elif [[ $MINUTE = 40 ]]
	then
	echo "7"
	elif [[ $MINUTE = 41 ]]
	then
	echo "7"
	elif [[ $MINUTE = 42 ]]
	then
	echo "7"
	elif [[ $MINUTE = 43 ]]
	then
	echo "7"
	elif [[ $MINUTE = 44 ]]
	then
	echo "7"
	elif [[ $MINUTE = 45 ]]
	then
	echo "7"
	elif [[ $MINUTE = 46 ]]
	then
	echo "7"
	elif [[ $MINUTE = 47 ]]
	then
	echo "7"
	elif [[ $MINUTE = 48 ]]
	then
	echo "8"
	elif [[ $MINUTE = 49 ]]
	then
	echo "8"
	elif [[ $MINUTE = 50 ]]
	then
	echo "8"
	elif [[ $MINUTE = 51 ]]
	then
	echo "8"
	elif [[ $MINUTE = 52 ]]
	then
	echo "8"
	elif [[ $MINUTE = 53 ]]
	then
	echo "8"
	elif [[ $MINUTE = 54 ]]
	then
	echo "8"
	elif [[ $MINUTE = 55 ]]
	then
	echo "8"
	elif [[ $MINUTE = 56 ]]
	then
	echo "8"
	elif [[ $MINUTE = 57 ]]
	then
	echo "8"
	elif [[ $MINUTE = 58 ]]
	then
	echo "8"
	elif [[ $MINUTE = 59 ]]
	then	
	echo "8"
	fi
fi
exit 0
```
and this one I use for minutes and seconds arms
```
#!/bin/bash
# clocks.sh

# written by t-mo_


if [[ "$1" = 00 ]]
then
echo "A"
elif [[ $1 = 01 ]]
then
echo "B"
elif [[ $1 = 02 ]]
then
echo "C"
elif [[ $1 = 03 ]]
then
echo "D"
elif [[ $1 = 04 ]]
then
echo "E"
elif [[ $1 = 05 ]]
then
echo "F"
elif [[ $1 = 06 ]]
then
echo "G"
elif [[ $1 = 07 ]]
then
echo "H"
elif [[ $1 = 08 ]]
then
echo "I"
elif [[ $1 = 09 ]]
then
echo "J"
elif [[ $1 = 10 ]]
then
echo "K"
elif [[ $1 = 11 ]]
then
echo "L"
elif [[ $1 = 12 ]]
then
echo "M"
elif [[ $1 = 13 ]]
then
echo "N"
elif [[ $1 = 14 ]]
then
echo "O"
elif [[ $1 = 15 ]]
then
echo "P"
elif [[ $1 = 16 ]]
then
echo "Q"
elif [[ $1 = 17 ]]
then
echo "R"
elif [[ $1 = 18 ]]
then
echo "S"
elif [[ $1 = 19 ]]
then
echo "T"
elif [[ $1 = 20 ]]
then
echo "U"
elif [[ $1 = 21 ]]
then
echo "V"
elif [[ $1 = 22 ]]
then
echo "W"
elif [[ $1 = 23 ]]
then
echo "X"
elif [[ $1 = 24 ]]
then
echo "Y"
elif [[ $1 = 25 ]]
then
echo "Z"
elif [[ $1 = 26 ]]
then
echo "a"
elif [[ $1 = 27 ]]
then
echo "b"
elif [[ $1 = 28 ]]
then
echo "c"
elif [[ $1 = 29 ]]
then
echo "d"
elif [[ $1 = 30 ]]
then
echo "e"
elif [[ $1 = 31 ]]
then
echo "f"
elif [[ $1 = 32 ]]
then
echo "g"
elif [[ $1 = 33 ]]
then
echo "h"
elif [[ $1 = 34 ]]
then
echo "i"
elif [[ $1 = 35 ]]
then
echo "j"
elif [[ $1 = 36 ]]
then
echo "k"
elif [[ $1 = 37 ]]
then
echo "l"
elif [[ $1 = 38 ]]
then
echo "m"
elif [[ $1 = 39 ]]
then
echo "n"
elif [[ $1 = 40 ]]
then
echo "o"
elif [[ $1 = 41 ]]
then
echo "p"
elif [[ $1 = 42 ]]
then
echo "q"
elif [[ $1 = 43 ]]
then
echo "r"
elif [[ $1 = 44 ]]
then
echo "s"
elif [[ $1 = 45 ]]
then
echo "t"
elif [[ $1 = 46 ]]
then
echo "u"
elif [[ $1 = 47 ]]
then
echo "v"
elif [[ $1 = 48 ]]
then
echo "w"
elif [[ $1 = 49 ]]
then
echo "x"
elif [[ $1 = 50 ]]
then
echo "y"
elif [[ $1 = 51 ]]
then
echo "z"
elif [[ $1 = 52 ]]
then
echo "1"
elif [[ $1 = 53 ]]
then
echo "2"
elif [[ $1 = 54 ]]
then
echo "3"
elif [[ $1 = 55 ]]
then
echo "4"
elif [[ $1 = 56 ]]
then
echo "5"
elif [[ $1 = 57 ]]
then
echo "6"
elif [[ $1 = 58 ]]
then
echo "7"
elif [[ $1 = 59 ]]
then
echo "8"

fi

exit 0
```
I don't know if many of you are familiar with conky but here is my setup. If anyone wants to try it out, everything needed is in the .tar, and conky is in the repos.
```
# UBUNTU-CONKY

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes

use_spacer right
use_xft yes
xftalpha 0
update_interval 1

minimum_size 200 5

draw_shades no

draw_outline no 
draw_borders no
draw_graph_borders no
#font arial
xftfont moconkyfontone:size=12 asl compile asl compile
uppercase no
short_units yes

stippled_borders 3

border_margin 9
border_width 10

default_color white
#color1 e5e5e5
#color2 F1AA0E
#color3 white
#color4 white
#color5 white
#color6 white
#color7 white
#color8 white
#color9 white

own_window_colour grey
own_window_transparent yes

#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

gap_x 5
gap_y 35

cpu_avg_samples 2
max_specials 256
text_buffer_size 256

TEXT
${color 02003B}${voffset 0}${goto 15}${font conkybackgroundfi:size=13.5}EDDDDDDF${goto 15}EDDDDDDF${goto 15}EDDDDDDF${goto 15}EDDDDDDF${goto 15}EDDDDDDF
${voffset -2}${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD
${voffset -2}${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD
${voffset -2}${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD
${voffset -2}${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD
${voffset -2}${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD
${voffset -2}${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD
${voffset -2}${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD${goto 15}DDDDDDDD
${voffset -2}${goto 15}GDDDDDDC${goto 15}GDDDDDDC${goto 15}GDDDDDDC${goto 15}GDDDDDDC${goto 15}GDDDDDDC
${voffset -290}${color lightgrey}${goto 33}${font moconkyfontone:size=30}a
${voffset -59}${goto 36}${color 000478}${font moconkyfontone:size=29.5}${execpi 10 ./acorbattery.sh}
${voffset -58}${goto 33}${color black}${font moconkyfontone:size=30}A$color${font arial:size=12} ${font arial:size=6}



${color lightgrey}${goto 33}${font moconkyfontone:size=30}a
${voffset -53}${goto 38}${cpugraph cpu1 50,230 000000 000000}
${voffset -56}${goto 38}${cpugraph cpu2 50,230 000478 000478}
${voffset -68}${color 444444}${goto 55}${font 1900.80.5:size=39}CPU
${voffset -57}${goto 33}${color black}${font moconkyfontone:size=30}A$color${font arial:size=12} ${font arial:size=6}
${voffset -33}${color d5d5d5}${goto 185}${font 911 Porscha:size=6}C'    ${font 911 Porscha:size=10}${acpitemp}
${voffset -6}${color d5d5d5}${goto 185}${font 911 Porscha:size=6}ONE ${font 911 Porscha:size=10}${cpu cpu1}
${voffset -6}${color d5d5d5}${goto 185}${font 911 Porscha:size=6}TWO ${font 911 Porscha:size=10}${cpu cpu2}


${color lightgrey}${goto 33}${font moconkyfontone:size=30}a
${voffset -53}${goto 38}${memgraph 50,230 000000 000000}
${voffset -56}${goto 38}${memgraph 50,230 000478 000478}
${voffset -68}${color 444444}${goto 55}${font 1900.80.5:size=39}RAM
${voffset -57}${goto 33}${color black}${font moconkyfontone:size=30}A$color${font arial:size=12} ${font arial:size=6}
${voffset -33}${color d5d5d5}${goto 185}${font 911 Porscha:size=6}TOTAL
${voffset -1}${color d5d5d5}${goto 185}${font 911 Porscha:size=8}${memmax}
${voffset -1}${color d5d5d5}${goto 185}${font 911 Porscha:size=6}FREE
${voffset -1}${color d5d5d5}${goto 185}${font 911 Porscha:size=8}${memfree}


${color lightgrey}${goto 33}${font moconkyfontone:size=30}a
${voffset -53}${goto 38}${downspeedgraph wlan0 50,230 000000 000000}
${voffset -56}${goto 38}${upspeedgraph wlan0 50,230 000478 000478}
${voffset -68}${color 444444}${goto 55}${font 1900.80.5:size=39}NET
${voffset -57}${goto 33}${color black}${font moconkyfontone:size=30}A$color${font arial:size=12} ${font arial:size=6}
${voffset -33}${color d5d5d5}${goto 185}${font 911 Porscha:size=6}DOWN
${voffset -1}${color d5d5d5}${goto 185}${font 911 Porscha:size=8}${totaldown wlan0}
${voffset -1}${color d5d5d5}${goto 185}${font 911 Porscha:size=6}UP
${voffset -1}${color d5d5d5}${goto 185}${font 911 Porscha:size=8}${totalup wlan0}










${color 02003B}${goto 23}${font zoraclockD:size=110}I
${voffset -185}${color 3D5469}${goto 42}${font zoraclockD:size=90}L
${voffset -144}${color 98BAD8}${goto 42}M
${voffset -144}${color 7C9EC0}${goto 42}N
${voffset -228}${goto 135}${color white}${font 911 Porscha:size=12}1
${voffset 39}${goto 33}${font 911 Porscha:size=12}9
${voffset 39}${goto 128}${font 911 Porscha:size=12}5
${color 111111}${voffset -108}${goto 50}${font zoraclockH:size=80}${execpi 20 ./zoraclock.sh}
${color 111111}${voffset -115}${goto 30}${font zoraclockM:size=110}${execpi 20 date | cut -c15-16 | xargs ~/clocks.sh}${color d5d5d5}${font arial:size=6}

```
I appreciate any help on one or both of these problems. Thank you in advance

Timo

---

### Post by Sam Lars on 2009-04-24
Is there a way to combine conditions in the if statement to get a range for your numbers, something like
```
if [[ "$MINUTE" -ge "00" && "$MINUTE" -le "11" ]]
	then
	echo "A"
```

---

### Post by t-mo_ on 2009-04-27
Thanks for your answer, crinos512 solved the problem :)

---

