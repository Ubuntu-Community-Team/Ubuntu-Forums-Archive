---
title: "Help in script - Getting table name from a text file"
date: 2011-03-10
forum: Programming Talk
---

### Post by wissy on 2011-03-10
[SIZE=3]Hi guys,
  
I have been working on this since 3 days but wasn't able to achieve what I want [IMG]http://linux.unix.com/images/smilies/brickwall.gif[/IMG]
  
I have a big text that has the following format:[/SIZE]
[INDENT][INDENT][FONT=Arial][SIZE=2]Current max fieldLen for table1 (a):
Fld#    Width     MaxWidth  ERR  NAME
----        ------      --------------  ------  ---------
  2:        80         38             ***     field-name
  3:         4          2                        field-version
  4:        40         7                        field-value
  5:        90        116                      value-meaning
      
Current max fieldLen for table2 (b):
    [/SIZE][/FONT][FONT=Arial][SIZE=2]Fld#    Width     MaxWidth  ERR  NAME
----        ------      --------------  ------  ---------[/SIZE][/FONT][FONT=Arial][SIZE=2]
  2:        80        38                          field-name
  3:        4          2                            field-version
  4:       1998    720                          definition
  5:        2          2                            data-type
  8:        40       12                            field-format
 10:       4          2                             data
 11:        80      19                             split-length
      
Current max fieldLen for table3 (c):
    [/SIZE][/FONT][FONT=Arial][SIZE=2]Fld#    Width     MaxWidth  ERR  NAME
----        ------      --------------  ------  ---------[/SIZE][/FONT][FONT=Arial][SIZE=2]
  2:        10          5                          uic
  3:         2          1                           user-type
  4:         4          2                           chess-rels
  5:         4          0                           next-rels
  6:         6          0                           next-rels-active
  7:        16          3                  ***   security-format
  8:        30          6                          default-applid
  9:        15          6                          next-txid
 10:        80         19                       user-desc
 12:        16          5                        ci-acc-group
 13:        40          0                        ci-password
 
Current max fieldLen for table4 (d):
    [/SIZE][/FONT][FONT=Arial][SIZE=2]Fld#    Width     MaxWidth  ERR  NAME
----        ------      --------------  ------  ---------[/SIZE][/FONT][FONT=Arial][SIZE=2]
  3:        40          9                      type
  2:       120        193            ***    description
      
Current max fieldLen for table5 (e):
    [/SIZE][/FONT][FONT=Arial][SIZE=2]Fld#    Width     MaxWidth  ERR  NAME
----        ------      --------------  ------  ---------[/SIZE][/FONT][FONT=Arial][SIZE=2]
  2:        10          5                          aic
  3:        16          5                          name
  4:        30          8                          austpac-address
  5:        10          0                          user
 26:       20          5                          route-profile[/SIZE][/FONT]
  [/INDENT][/INDENT][FONT=Arial][SIZE=3]As you see, the column headers are fix. Also, I have the following fixed words in the beginning of every table "**[SIZE=2]*Current max fieldLen for*[/SIZE]**".
For some of these lines, in the error column, there are 3 stars.
  
Note: The table name is the word that could be found after "[/SIZE][/FONT][FONT=Arial][SIZE=3][B][SIZE=2][I]Current max fieldLen for".
  
[/I][/SIZE][/B][/SIZE][/FONT][FONT=Arial][SIZE=3]Basically,  I am  searching for a way in order to get the table name in case the  table has  "***" in the error column, in any of its fields.
  
For example, for this sample I provided, I need the output to be exactly:
  
  [B]table1
table3
table4[/B]
  
  
Why not **table2** or **table5**? Because they don't have any "***"
  
For now, I did a little bit of progress by using:
"
  [B][I]egrep "(^Current|\*\*\*)" filename.txt > test.txt
cat test.txt | awk '{print $5}' > test2.txt[/I][/B]
"
Could anyone help please?
  
Very much appreciated!
  
Regards.

NOTE: sorry for the bad format of the text file. I am attaching an image with the proper format.
  
  [/SIZE][/FONT]

---

### Post by kaibob on 2011-03-11
After seeing the excellent suggestion by DaithiF, I modified my earlier shell script to use a somewhat similar approach. It reads the text file line-by-line and assigns each word to an array variable. If a line is found with the string "Current max fieldLena", then the table name in array item 4 is assigned to to a variable named save. If a line is found with the string "***" in array item 3, then the content of the save variable is printed to the screen. 

```
#!/bin/bash

while read -r -a line ; do
  [[ "${line[*]}" = "Current max fieldLen"* ]] && save=${line[4]}
  [[ "${line[3]}" = \*\*\* ]] && echo $save
done < file.txt
```

---

### Post by DaithiF on 2011-03-11
in sed:
```
sed -n '/Current max fieldLen/{s/^.* for \([^ ]\+\).*$/\1/;h};/\*\*\*/{g;p}' thefile | uniq
```
which says:
when a line matching Current maxfieldlen is found, strip away text before and after the table name, and copy what remains into the hold buffer.
when a line matches *** get the contents of the hold buffer (ie. the last table name) and print it.

the pipe to uniq at the end is to eliminate the duplicate table names you would get if a table has more than one field error.

---

