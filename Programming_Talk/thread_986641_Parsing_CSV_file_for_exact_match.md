---
title: "Parsing CSV file for exact match"
date: 2008-11-18
forum: Programming Talk
---

### Post by Mbengi Bongi on 2008-11-18
Guys,

I previously posted a thread about how to parse 2 csv files using BaSH/Shell Script.

I have been testing the various methods supplied by your kind selves, but am trying to streamline my script.

I basically need to know how to ask the script to validate user input and make sure its an **exact match** of the first value in each row in the file and if a match is not found an error message is returned.
 e.g.

file sample (**data1.csv**) - this file is parsed if the data input is 3 characters
[COLOR="Blue"]*Data, Station Name, Address, *
EUS, London Euston,  Address
VIC, London Victoria, Address[/COLOR]

if 4 characters are entered, **data2.csv** is parsed

if a match is not found in the relevant file, an error message is returned.

Any help at all would be much apprecated

---

### Post by slavik on 2008-11-18
WARNING!
Perl code ...

```

#!/usr/bin/perl
use strict;
use warnings;

my $searchtext = $ARGV[0]; #get first argument
my $file;

if (length $searchtext == 3) { $file = "data1.csv" }
elsif (length $searchtext == 4) { $file = "data2.csv" }
else { die "You entered $searchtext, which is not a string of length 3 or 4\n"; }

open FILE, $file or die $!;

for (my $line = <FILE>) {
  if ($line =~ /^$searchtext,.*?/) {
    die "$line \nMatch found on line $. in $file \n";
  }
}

die "Match not found!\n";

```

---

### Post by Mbengi Bongi on 2008-11-19
Thanks very much for yopur reply Slavik,

I have to say I'm not at all familiar with Perl.

Where would I introduce **echo/print** commands to display data from the files?

i.e. if a match was found for search text **EUS** i want the script to display :

Station Name: [COLOR="Blue"] London Euston[/COLOR]

Also, can you use ANSI escape codes in perl for colouring text?

Thanks Again

---

### Post by slavik on 2008-11-19
doubt on the escape codes for colors ... but look at the code carefully, you should be able to figure it out.

I also made a mistake, going to edit it to fix it.

---

### Post by Mbengi Bongi on 2008-11-19
Ok I'm guessing here: 

```
die "$line \nMatch found on line $. in $file \n";
```

Am I warm?  :confused:

---

### Post by Mbengi Bongi on 2008-11-19
Can this be done on Shell Script at all as opposed to Perl?

---

### Post by slavik on 2008-11-19
> **Mbengi Bongi said:**
> Can this be done on Shell Script at all as opposed to Perl?
yes, basically, you determine the file and the grep it for the expression ...

---

### Post by Mbengi Bongi on 2008-11-19
Ok, so I've done: 
```
while [ true ]
do
echo "Enter Station:"
read input
length=${#input}
if [ $length -eq 3 ]
then
SN=$(grep $input data1.csv | cut -d, -f2)
CRS=$(grep $input data1.csv | cut -d, -f3)
NLC=$(grep $input data1.csv | cut -d, -f4)
OP=$(grep $input data1.csv | cut -d, -f5)
elif [ $length -eq 4 ]
then
SN=$(grep $input data2.csv | cut -d, -f2)
CRS=$(grep $input data2.csv | cut -d, -f3)
NLC=$(grep $input data2.csv | cut -d, -f4)
OP=$(grep $input data2.csv | cut -d, -f5)
else
echo "Station Not found"
fi
echo "Station Name: $SN"
echo "CRS Code: $CRS"
echo "NLC: $NLC"
echo "Operator: $OP"
echo; echo
done

```

The problem I have so far is if I test for an incorrect match it echoes:  

```
Station Name:
CRS Code:
NLC:
Operator:
```

When all I want it to do is display an error message

---

### Post by nvteighen on 2008-11-19
> **Mbengi Bongi said:**
> Ok I'm guessing here: 

```
die "$line \nMatch found on line $. in $file \n";
```

Am I warm?  :confused:

I don't get what you're asking, but if you're curious, **die** in Perl makes the program print the message and stop. Usually, it's used for displaying a fatal error message, but you can use whenever you need to print+quit. ("die" = the program's last words :))

---

### Post by Mbengi Bongi on 2008-11-19
Basically what I want to achieve is

1. Script accepts user input 
2. The script validates the input if its 3 characters **data1.csv** is parsed, if 4 characters **data2.csv** is parsed
3. If a match is found, the values are displayed on screen
4. if no match is found an error message is displayed

Note: The user input is the 1st entry on each row in the csv files e.g.

**data1.csv** (Sample)

[FONT="Courier New"]EDB, Edinburgh, EDB, 9300, ScotRail
GLC, Glasgow Central, GLC, 9200,Network Rail[/FONT]

**data2.csv** (Sample)

[FONT="Courier New"]9300, Edinburgh, EDB, 9300, ScotRail
9200, Glasgow Central, GLC, 9200,Network Rail[/FONT]

If the user enters either **EDB** or **9300** the screen displays:

StationName:[COLOR="Blue"] Edinburgh[/COLOR]
CRS Code: [COLOR="blue"]EDB[/COLOR]
NLC: [COLOR="blue"]9300[/COLOR]
Operator:[COLOR="blue"] ScotRail[/COLOR]

The data in [COLOR="blue"]blue[/COLOR] is retrieved from the relevant file and will change depending on what input is entered, and if there isn't a match then an error message should be displayed.

Does that make sense?

---

