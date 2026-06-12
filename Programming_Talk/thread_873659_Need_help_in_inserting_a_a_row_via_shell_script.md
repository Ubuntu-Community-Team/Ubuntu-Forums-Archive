---
title: "Need help in inserting a a row via shell script"
date: 2008-07-29
forum: Programming Talk
---

### Post by umshiva on 2008-07-29
:confused:
Hi Gurus and experts,

I am a beginner/intermediate in shell scripting /awk ....

I need a script that compares two tables and inserts the row which is absent

Table1
val1        value2              value3
P600290990  P6002909900209       AC
P600290990  P6002909900208       AC 
P898977787  P8989777871010       IC   
P989898989  P9898989891010       IP


Table2

val1        value2              value3 value4  value5
P600290990  P6002909900209       AC     10      r
P898977787  P8989777871010       IC      10     r
P989898989  P9898989891010       IP      10     r
 

Now in table2 if i dont have the "AC row" for that value1 , in this case 
 
for P600290990 i dont have P6002909900208 row then ,

I have to hardcode 10 and r as value4,value5 and then 
insert a row 

This has to be done for 4000 rows ,,,, can anyone plz help

Ur help will yeild a great help 

Thanks a Bunch in advance

---

### Post by ghostdog74 on 2008-07-29
i don't understand what is required of your output. better to show what your output looks like to confirm.

---

### Post by dwhitney67 on 2008-07-29
[ post deleted ]

---

### Post by umshiva on 2008-07-29
i need a script that compares the value2 of
table1 and table2 , in which value1 is the primary key 
in both table1 and table2

  if some values are absent in table2
                     
    my script should say ,

       o/p
           ***********
            when comparing table1 and table2 1 value was absent 
             in table2 
            **********
            #P6002909900208 for AC  #     
                
           should i insert this value in table2 
                 < if i say yes> 
            then 
                  the value1,value2,value3 has to be taken from
                   table1 for row which is absent

                    hardcode the value4,value5 as 10,r
                    
                     run the insert query
                      insert into table1 ('all 5 values') 
                     display a msg that insertion was succesful
                      

Please help me

---

### Post by Martin Witte on 2008-07-29
This is what I make from your issue:

You have file, say table1, which looks like
```
martin@sony:~$ cat table1
P600290990 P6002909900209 AC
P600290990 P6002909900208 AC
P898977787 P8989777871010 IC
P989898989 P9898989891010 IP

```and a file 'table2' which looks like
```
martin@sony:~$ cat table2
P600290990 P6002909900209 AC 10 r
P898977787 P8989777871010 IC 10 r
P989898989 P9898989891010 IP 10 r
```
To file table2 you want to add a row 
```
P600290990 P6002909900208 AC 10 r
```
as for this row the first three fields are in 'table1' but not in 'table2'. 

To achieve this you have to start looping over table1, then check if the first three fields of the line you have read match any of the lines in table2. If you don't find a match you add those three fields - extended with the string ' 10 r'. You can do this with a script like
```

martin@sony:~$ cat comp_tables.sh 
#!/bin/bash
typeset val_table1_1 val_table1_2 val_table1_3
typeset val_table2_1 val_table1_2 val_table2_3 val_table2_4 val_table2_5
typeset -i found

while read val_table1_1 val_table1_2 val_table1_3; do
	found=1
	while read val_table2_1 val_table2_2 val_table2_3 val_table2_4 val_table2_5; do
		if [[ $val_table1_1 = $val_table2_1 &&  $val_table1_2 = $val_table2_2 &&  $val_table1_3 = $val_table2_3 ]]; then
			found=0
		fi
	done < /home/martin/table2
	if [[ "$found" -eq 1 ]]; then
		echo "$val_table1_1 $val_table1_2 $val_table1_3 10 r" >>  /home/martin/table2
	fi
done <  /home/martin/table1
```
supposed your data files are in /home/martin ....

---

### Post by ghostdog74 on 2008-07-29
well, i hope i understood what's required.
```

awk 'FNR==NR{ a[$1SEP$2]=$3;next}
!($1SEP$2 in a){ print $0" 10 r"}' file2 file1

```
you can also use bash while/read loop, however for large number of records, it will run slower. you might also try uniq.

---

### Post by umshiva on 2008-07-29
> **ghostdog74 said:**
> well, i hope i understood what's required.
```

awk 'FNR==NR{ a[$1SEP$2]=$3;next}
!($1SEP$2 in a){ print $0" 10 r"}' file2 file1

```
you can also use bash while/read loop, however for large number of records, it will run slower. you might also try uniq.

I supoosose u are comapring the third column and secon column .... i could not understand this ..please tell me what it does

---

### Post by umshiva on 2008-07-29
> **ghostdog74 said:**
> well, i hope i understood what's required.
```

awk 'FNR==NR{ a[$1SEP$2]=$3;next}
!($1SEP$2 in a){ print $0" 10 r"}' file2 file1

```
you can also use bash while/read loop, however for large number of records, it will run slower. you might also try uniq.

I need to store the details of table1 in file1
        select * from table1 into file1
        select * from table2 to file2
second column (value2)  should be compared with value2 of file1

if some rows are absent then ,
                  run this query ,,,, please help me in comparin 
 
values and runining queries .....

i have to insert into table2 and commit it 
Please advice ...

thanks in advance

---

### Post by umshiva on 2008-07-29
> **Martin Witte said:**
> This is what I make from your issue:

You have file, say table1, which looks like
```
martin@sony:~$ cat table1
P600290990 P6002909900209 AC
P600290990 P6002909900208 AC
P898977787 P8989777871010 IC
P989898989 P9898989891010 IP

```and a file 'table2' which looks like
```
martin@sony:~$ cat table2
P600290990 P6002909900209 AC 10 r
P898977787 P8989777871010 IC 10 r
P989898989 P9898989891010 IP 10 r
```
To file table2 you want to add a row 
```
P600290990 P6002909900208 AC 10 r
```
as for this row the first three fields are in 'table1' but not in 'table2'. 

To achieve this you have to start looping over table1, then check if the first three fields of the line you have read match any of the lines in table2. If you don't find a match you add those three fields - extended with the string ' 10 r'. You can do this with a script like
```

martin@sony:~$ cat comp_tables.sh 
#!/bin/bash
typeset val_table1_1 val_table1_2 val_table1_3
typeset val_table2_1 val_table1_2 val_table2_3 val_table2_4 val_table2_5
typeset -i found

while read val_table1_1 val_table1_2 val_table1_3; do
	found=1
	while read val_table2_1 val_table2_2 val_table2_3 val_table2_4 val_table2_5; do
		if [[ $val_table1_1 = $val_table2_1 &&  $val_table1_2 = $val_table2_2 &&  $val_table1_3 = $val_table2_3 ]]; then
			found=0
		fi
	done < /home/martin/table2
	if [[ "$found" -eq 1 ]]; then
		echo "$val_table1_1 $val_table1_2 $val_table1_3 10 r" >>  /home/martin/table2
	fi
done <  /home/martin/table1
```
supposed your data files are in /home/martin ....



This does comparison but can you help me with the exact need plz

LOt of thanks

---

### Post by umshiva on 2008-07-29
can anyone help me !!!!plzplz

lot of thanks in advance

---

### Post by dwhitney67 on 2008-07-29
Umshiva -

Do the scripts given above not meet your needs?  I am confused.  You seem to want a script, yet you hint that you need help with an SQL query (to update a database table).  Can you please elaborate which do you need?

I cannot understand whether you want to update a flat-file or a database table.

---

### Post by umshiva on 2008-07-30
> **dwhitney67 said:**
> Umshiva -

Do the scripts given above not meet your needs?  I am confused.  You seem to want a script, yet you hint that you need help with an SQL query (to update a database table).  Can you please elaborate which do you need?

I cannot understand whether you want to update a flat-file or a database table.

Hi dwhitney ,

I want a script only which will take up the output of two tables and store it in two different files

compare that files second column and check for missing values
if some values are missing prompt the user abt missing values and insert the missing row

I hope i gave a good picture abt the problem now

---

### Post by umshiva on 2008-07-30
> **umshiva said:**
> Hi dwhitney ,

I want a script only which will take up the output of two tables and store it in two different files

compare that files second column and check for missing values
if some values are missing prompt the user abt missing values and insert the missing row

I hope i gave a good picture abt the problem now

Missing row should be inserted in the databse and not the file

---

