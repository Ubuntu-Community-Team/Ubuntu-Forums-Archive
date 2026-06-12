---
title: "Rename files based on field in csv file - code snip"
date: 2009-12-14
forum: Programming Talk
---

### Post by samjaynes on 2009-12-14
I have a bunch of csv reports that are named in a confusing way.  There is a field in the second row of the file (a date) which I would like to rename the file via bash, etc.

So far this is what I have to get the value

for i in *csv; do sed -n '2p' $i | awk -F"," '{gsub("/", ""); print $11}'; done

How can I move this to renaming the file via mv or rename?

---

### Post by Rany Albeg on 2009-12-14
Hello ,

Can you please be more specific about your problem and give an example to the file?

Just a fast guess:

```
f_name=path_to_file             # name of file.
old=$(your above code)          # wanted pattern.
sed 's/$old/$new/'g -i $f_name  # edit the file.
```

In case i  didn't understand you correctly please give more information.

Have a nice day.

---

### Post by samjaynes on 2009-12-14
The folder contains several reports in csv, the old file name is the $i parameter.  The second row contains 
,,,,,,,,,,12/14/2009
which the gsub changes to 12142009.  

I was hoping to take the value from this output to rename the file.

So if report.csv contains ,,,,,,,12/14/2009 it would be renamed 12142009.csv
and report1.csv would be renamed 12152009.

Does that help?

---

### Post by Rany Albeg on 2009-12-14
Hi again.
I think you should first remove the ,,,,, from you pattern and then check if the result is a date by executing this:

```
foo="25/12/2005"
bool=0
if [[ "${foo}" =~ [0-9]{2}/[0-9]{2}/[0-9]{4} ]]; then
  bool=1
fi
```

then if it is in a date form you sould discard the '/'
and rename the csv file with 'mv' command

```
if ((bool)); then
    1) discard '/'
    2) rename the file
fi
```

---

### Post by samjaynes on 2009-12-14
> **Rany Albeg said:**
> Hi again.
I think you should first remove the ,,,,, from you pattern and then check if the result is a date by executing this:


the ,,,,, is a result of the csv file, and getting the second line with the sed function.  Then using the awk command with the file separator ",", I am able to obtain the date 12/15/2009 from the 10 field in the csv output.  gsub trims it to 12152009.

> 
```
foo="25/12/2005"
bool=0
if [[ "${foo}" =~ [0-9]{2}/[0-9]{2}/[0-9]{4} ]]; then
  bool=1
fi
```

then if it is in a date form you sould discard the '/'
and rename the csv file with 'mv' command


gsub remove the "/" from the output, therefore the output we are dealing with is 12152009 which is the name I would like to save it as.

> 
```
if ((bool)); then
    1) discard '/'
    2) rename the file
fi
```

[/QUOTE]

I am hoping that helps.  So running the bash command above on a directory of:
[LIST]
[*]report.csv
[*]report1.csv
[/LIST]
Would result in the window from (for i in *csv; do sed -n '2p' $i | awk -F"," '{gsub("/", ""); print $11}'; done)
[LIST]
[*]12142009
[*]12152009
[/LIST]
The result I want is -
[LIST]
[*]12142009.csv
[*]12152009.csv
[/LIST]
I was hoping to add the mv command to the bash statement above, but I am open to ideas.

---

### Post by ghostdog74 on 2009-12-14
```

shopt -s nullglob
for file in *.csv
do
    exec 4<"$file"
    read line <&4
    read line <&4
    exec 4<&-
    IFS=","
    set -- $line
    d=${@:(-1)} #get last element which is the date
    filename=${d//\//}
    echo mv "$file" ${filename}.csv
done



```

---

### Post by samjaynes on 2009-12-15
> **ghostdog74 said:**
> ```

shopt -s nullglob
for file in *.csv
do
    exec 4<"$file"
    read line <&4
    read line <&4
    exec 4<&-
    IFS=","
    set -- $line
    d=${@:(-1)} #get last element which is the date
    filename=${d//\//}
    echo mv "$file" ${filename}.csv
done



```

Thanks - I copied and pasted your code in a file called rename.sh

I executed the code (in cygwin right now since I am not at my Ubuntu box), and sh rename.sh, I receive the following error:

: invalid shell option nameullglob
rename.sh: line 3: syntax error near unexpected token `$do\r''

Any insight?

FIXED - Formatted file as UNIX, changed the shell option outside of the script, and removed the echo comment.

Thanks - perfect.

---

### Post by ghostdog74 on 2009-12-15
use bash on cygwin

---

### Post by samjaynes on 2009-12-15
> **ghostdog74 said:**
> use bash on cygwin

Thanks ghostdog - I have read several of your threads, thanks for your feedback.

I ran into two small issues: 
1) where the date field in the second line contained a date span - for example 12/11/2009 to 12/12/2009
2) the date for the beginning of the month is 12/1/2009, therefore the output is 1212009 which can be interrupted several ways

Therefore, I was looking at your regex statement and was wondering if we can do the following:
1) | remove spaces  
2) two options here with the date -
2a) replace slashes with - (dashes)(I tried ${d//\/-/} and ${d//\/\-/} with no luck
2b)   or is there a snippet of code that parses the date into YYYYMMDD format?

Again, thanks for reading this post and your feedback

---

### Post by ghostdog74 on 2009-12-15
your input sample does not show a date span. ples provide something accurate, if not 100%. Show what you input sample can look like again, then show what you want as output from that input sample.

---

### Post by samjaynes on 2009-12-16
> **ghostdog74 said:**
> your input sample does not show a date span. ples provide something accurate, if not 100%. Show what you input sample can look like again, then show what you want as output from that input sample.

Ghostdog - Thank you for your response.  Yes, my example provided in the first thread did not show the date span; that was something found after executing the code through the entire directory.  In 95% of the files, it is a singular date, such as 12/1/2009, 12/15/2009, and 12/16/2009.   

There was three situations (mostly weekly reports) that I ran into where the second row contained date ranges at the end of the csv record:
,,,,,,,3/14/2009 - 3/20/2009,
,,,,,,,12/6/2009 - 12/12/2009,
etc

So the preferred method would be to handle the date since the day part of the value is single digit to convert to YYYYYMMDD; then strip out all blank spaces.  For example, if ReportA.csv had the value:
,,,,,,,3/[COLOR="Red"]7[/COLOR]/2009 - 3/13/2009,
ReportA.csv would be renamed 200903[COLOR="Red"]07[/COLOR]-20090313.csv

I hope those examples help.  For the previous situations, we could just use the same date change to take values such as 
,,,,,,,,12/16/2009 or
,,,,,,,,12/7/2009 
and created 20091216.csv or 20091207.csv
*noting the addition of the 0 in the DD section.

Cheers,

---

### Post by samjaynes on 2009-12-18
Just checking to see if someone has seen my last post - I have been googling for solutions.  Tried sed or awk on the date... no luck so far.

---

