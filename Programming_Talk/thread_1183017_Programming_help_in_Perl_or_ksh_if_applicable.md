---
title: "Programming help in Perl or ksh if applicable"
date: 2009-06-09
forum: Programming Talk
---

### Post by smurphy_it on 2009-06-09
Good day.  I have an issue and am new to perl.  Here is my issue and what I wish to accomplish.  Any help would be greatly appreciated.

I have a csv file which has a filename reference to a specific date.  What I want to be able to do is to parse the file, looking for todays date, and then grab the first column entry on the line before it....  Clear as Mud ?

Here is a sample.  We'll call this sample.csv

ABC1157,20090606,201003
ABC1158,20090607,201003
ABC1159,20090608,201003
ABC1160,20090609,201003
ABC1161,20090610,201003
ABC1162,20090611,201003
ABC1163,20090612,201003
ABC1164,20090613,201003
ABC1165,20090614,201003

Now the script should be able to determine today's current date in YYYYMMDD format, then open up this file and find that date.  So if today is 20090609, and I search the sample.csv file above, I want to grab the ABC1159 entry and save as a variable.  Later on with additional processing, I will refer to that entry, then check if that file name exists in the directory.

I've been playing with it a little bit, and saw how some people were using the localtime to get it to print the current date, but when I tried to use that as a search pattern, it was only grabbing part of the date.  Snippet below.

my($day, $month, $year, $dexter) = (localtime)[3,4,5];
$month = sprintf '%02d', $month+1;
$day   = sprintf '%02d', $day;
$dexter = $year+1900, $month, $day;

open CSVFILE, "sample.csv" or die $!;
while ($line = <CSVFILE>) {
	  if ($line =~ m/($dexter)/) {

in the if line search patter above, if I put in the date 20090609 it will find it, if I use the $dexter variable, it will only look for 2009 and have multiple finds.

Would reading the entire file into an array be the better step here ?

---

### Post by EndOn9 on 2009-06-09
This line is your problem:
> **smurphy_it said:**
> 
$dexter = $year+1900, $month, $day;


If you want to concatenate these values together as a string you want:

$dexter = $year+1900 . $month . $day;

Also, I would recommend using a module like [Text::CSV:Simple]("http://search.cpan.org/~tmtm/Text-CSV-Simple-1.00/lib/Text/CSV/Simple.pm") to do CSV parsing. Even for a seemingly simple job, no need to reinvent the wheel!

---

### Post by ghostdog74 on 2009-06-09
> **smurphy_it said:**
> 
open CSVFILE, "sample.csv" or die $!;
while ($line = <CSVFILE>) {
	  if ($line =~ m/($dexter)/) {

you have been recommended to concatenate your $year $month $day variables together. in your while loop, you can split on ",". then check second element against your concatenated date eg
```

if ( $year.$month.$day == $splitted[1] )

```

---

### Post by smurphy_it on 2009-06-10
Thank you for your valuable information.  I'll make the changes.

---

### Post by smurphy_it on 2009-06-10
Ok, still one little problem.  The date works great thank you.  As for looking it up is my delima.  I can do the lookup of the date, but once I find it, I need to know what the value of the 1st column from the previous column.

EX.

ABC1159,20090608,201003
ABC1160,20090609,201003
ABC1161,20090610,201003

So if today is 20090610, when I do the search via data it will find that line, but what I really need is the value of the first column one line previous to my find.  In this case, it would be ABC1160 (from 20090609 line).

Is there an easy way to do this, or should there be other means.  Like creating a hash, etc.....  

Perhaps having a "row #" that could be returned, then I could look for the 1st n characters from the line before...

---

### Post by ghostdog74 on 2009-06-10
if its just to catch the previous line, you can set a variable
```

while ($line = <CSVFILE>) {
if ($line =~ m/($dexter)/) {
  # code to show previous line.
  # after that, break
}
previous=$line;

```

---

### Post by smurphy_it on 2009-06-11
Yes I want to grab the previous line but I only require the first word.  So if I have the "entire previous line" I could probably grep or cut out what I don't need.  Then I want to be able to do check to see if that file exists in the current directory.

---

