---
title: "help matching a pattern in ksh"
date: 2009-04-01
forum: Programming Talk
---

### Post by DFord425 on 2009-04-01
I am trying to match a pattern in an if statment. I am trying to match '$\n' but its not working. Can someone tell me if this looks right
```
if [[ $line = "*@(\\$\n)" ]]
```

I have tried many different things but i cant seem to get it to work.

---

### Post by ghostdog74 on 2009-04-01
show sample strings/text you are doing pattern matching. describe what you want to find clearly. show your final output.

---

### Post by DFord425 on 2009-04-02
I am writing a script that reads in text from a file, line by line then prints out the text with line numbers. If the text has a $ at the end of the line, i have to treat the next line as the same line. So for example:
> 
Some text here$
   some more text here
Should be printed out as
> 
####    some text here some more text here

When i run the script, if the if statement is true, right now i echo the line to another file for testing but the other file never gets created.

Anyone have any ideas?

---

### Post by ghostdog74 on 2009-04-02
```

# more file
12345,ABCD,5
12345,DEFGH,7
34567,AXDFG,1
Some text here$
some more text here
45678,WERFG,2
Some1 text1 here1$
some1 more1 text1 here1
45678,WERFA,3

# awk 'ORS=/\$$/?" ":RS' file
12345,ABCD,5
12345,DEFGH,7
34567,AXDFG,1
Some text here$ some more text here
45678,WERFG,2
Some1 text1 here1$ some1 more1 text1 here1
45678,WERFA,3
                                        

```

---

### Post by DFord425 on 2009-04-02
thanks for your help, im not too familar with the awk command so i will go read up on it.

---

### Post by ghostdog74 on 2009-04-02
look at my sig for link to awk

---

### Post by DFord425 on 2009-04-02
Im a little confused about how to use multiple commands with awk. I know i use {} but do i have to put each command on a seperate line. I want to print a count, the line from the original file, then incriment the counter. Does it follow this format:
```
awk '{*command command2 command3*}' $file > $output
```

Thanks for you help

---

### Post by ghostdog74 on 2009-04-02
you can continue to put commands using ";"
```

awk '{command;command;command}' file

```
pls read the awk manual .

---

### Post by DFord425 on 2009-04-03
I am reading the manual but i keep getting this error and i cant figure out what it means. Its not in the manual, that i can see.
```
awk: Field  is not correct.
 The input line number is 1. The file is *file/name* The source line number is 1
```

Can anyone tell me what that means? Here is the code im using:
```
awk '{ ORS=/\$$/?" ":RS; print $count "\t" $0; count = count + 1 }' $temp
```

---

### Post by ghostdog74 on 2009-04-03
what exactly do you want to do? do you want to print the number of lines?
```

# awk 'ORS=/\$$/?" ":RS' file | nl
     1  12345,ABCD,5
     2  12345,DEFGH,7
     3  34567,AXDFG,1
     4  Some text here$ some more text here
     5  45678,WERFG,2
     6  Some1 text1 here1$ some1 more1 text1 here1
     7  45678,WERFA,3


```

---

### Post by DFord425 on 2009-04-03
I want to print out a line, if the line ends with $'\n'(newline character) then print out the next line on the same line. What you gave me before does that. But i also need to keep a running count of the lines so that i print the counter, \t(tab), line.

---

### Post by ghostdog74 on 2009-04-03
can you just show an example of the output you want?

---

### Post by DFord425 on 2009-04-03
> 
1890    GOTO / 12.02500, 0.00000, 20.82791, 0.500000, 0.000000, 0.866025
1891    CYCLE/REAM,DEPTH, 4.720000,IPM, 39.370079,CLEAR, 0.100000,DWELL$
1892    , 0.100000
1893    GOTO / 11.97500, 0.00000, 20.74131, 0.500000, 0.000000, 0.866025
1894    CYCLE/OFF
1895    RAPID
1896    GOTO / 12.72500, 0.00000, 22.04035, 0.500000, 0.000000, 0.866025
1897    RAPID
1898    GOTO / 12.72500, 2.80534, 22.04035, 0.500000, 0.000000, 0.866025
1899    RAPID
1900    GOTO / 12.72500, 7.80534, 22.04035, 0.500000, 0.000000, 0.866025
1901    RAPID
1902    GOTO / 12.72500, 7.80534, 22.04035, 0.000000, 1.000000, 0.000000
1903    FINI

except line 1892 is printed on line 1891

---

### Post by ghostdog74 on 2009-04-03
maybe i am tired, but i still don't get it. hope someone awake can help you.

---

### Post by DFord425 on 2009-04-03
Thanks for your help. What might be a little confusing is the original file does not have the lines numbered, i want to add those using a counter. So the original file would look like this
> 
GOTO  /   12.02500,    0.00000,   20.82791, 0.500000, 0.000000, 0.866025
CYCLE/REAM,DEPTH,    4.720000,IPM,   39.370079,CLEAR,    0.100000,DWELL$
,    0.100000
GOTO  /   11.97500,    0.00000,   20.74131, 0.500000, 0.000000, 0.866025
CYCLE/OFF
RAPID
GOTO  /   12.72500,    0.00000,   22.04035, 0.500000, 0.000000, 0.866025
RAPID
GOTO  /   12.72500,    2.80534,   22.04035, 0.500000, 0.000000, 0.866025
RAPID
GOTO  /   12.72500,    7.80534,   22.04035, 0.500000, 0.000000, 0.866025
RAPID
GOTO  /   12.72500,    7.80534,   22.04035, 0.000000, 1.000000, 0.000000
FINI

---

### Post by ghostdog74 on 2009-04-03
so what is wrong with this:
```
# awk 'ORS=/\$$/?" ":RS' file | nl
     1  GOTO / 12.02500, 0.00000, 20.82791, 0.500000, 0.000000, 0.866025
     2  CYCLE/REAM,DEPTH, 4.720000,IPM, 39.370079,CLEAR, 0.100000,DWELL$ , 0.100000
     3  GOTO / 11.97500, 0.00000, 20.74131, 0.500000, 0.000000, 0.866025
     4  CYCLE/OFF
     5  RAPID
     6  GOTO / 12.72500, 0.00000, 22.04035, 0.500000, 0.000000, 0.866025
     7  RAPID
     8  GOTO / 12.72500, 2.80534, 22.04035, 0.500000, 0.000000, 0.866025
     9  RAPID
    10  GOTO / 12.72500, 7.80534, 22.04035, 0.500000, 0.000000, 0.866025
    11  RAPID
    12  GOTO / 12.72500, 7.80534, 22.04035, 0.000000, 1.000000, 0.000000
    13  FINI


```

---

### Post by DFord425 on 2009-04-03
Nothing that works, sorry i didnt see that your suggested that before. thanks so much for your help.

---

