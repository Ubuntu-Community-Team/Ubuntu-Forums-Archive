---
title: "Using awk to search and print substring?"
date: 2013-11-11
forum: Programming Talk
---

### Post by stinkeye on 2013-11-11
I have the output from sensors in 
test.txt
```
it8720-isa-0228
Adapter: ISA adapter
in0:          +0.99 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.01 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.26 V  
fan1:        2636 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1149 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +[COLOR="#FF0000"]37[/COLOR].0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +38.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +80.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.250 V
intrusion0:  ALARM
```

I am trying to get the temp1 value as a whole number.

Using...
 ```
awk '/temp1/{print substr($2,2,3)}' test.txt
```
includes the decimal point...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **awk '/temp1/{print substr($2,2,3)}' test.txt**
37**.**
```

Does substr($2,2,3) mean the second string, second and third characters or am I understanding it wrong.

[COLOR="#FF0000"]_Edit_[/COLOR]
After testing, **substr($2,[COLOR="#FF8C00"]2[/COLOR],[COLOR="#EE82EE"]3[/COLOR])** appears to mean ...second string, print from [COLOR="#FF8C00"]**2**[/COLOR]nd character{start point), [COLOR="#EE82EE"]**3**[/COLOR] characters including start point.
eg this gives what I want.
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **awk '/temp1/{print substr($2,2,[COLOR="#EE82EE"]2[/COLOR])}' test.txt**
37
```
Is this correct?
Thanks.

---

### Post by steeldriver on 2013-11-12
It's correct as far as it goes, the usage is substr(string, **start**, **length**) as per the man page

However imho it's not a good idea to rely on the value having a particular number of characters - it would be more robust to do something like strip off the non-numeric characters and then print the resulting numeric value to the desired precision e.g.

```
awk '/temp1/ {gsub("[^0-9.+-]","",$2); printf("%.0f\n", $2)}'
```

---

### Post by stinkeye on 2013-11-12
> **steeldriver said:**
> It's correct as far as it goes, the usage is substr(string, **start**, **length**) as per the man page

However imho it's not a good idea to rely on the value having a particular number of characters - it would be more robust to do something like strip off the non-numeric characters and then print the resulting numeric value to the desired precision e.g.

```
awk '/temp1/ {gsub("[^0-9.+-]","",$2); printf("%.0f\n", $2)}'
```
Yep that would be better.
Doesn't really matter with celsius but if using Fahrenheit the temp output could be 2 or 3 characters.

Can you explain  how the code works.
Thanks.

---

### Post by Lars Noodén on 2013-11-12
```

awk '/temp1/ 
  {
     gsub("[^]","",$2); 
     printf("%.0f\n", $2);
   }'

```

Look for lines containing "temp1" and do the following on them.

Look in the second column/field and "globally" find and replace characters not in the set "0-9.+-" with and empty string
Do a formatted print of what's left in the second column/field, adding a newline (\n).

All of awk's functions are detailed in the manual page, though it can be daunting at first.

---

### Post by Lars Noodén on 2013-11-12
One thing about awk that I initially found unclear myself was the syntax.  Everything is basically an if-then statement.  If no arguments are given the $0 is assumed, which means the full line/record.  

So in pseudo code,

```

if ( /temp1/ =~ $0 ) then
  {
     gsub("[^]","",$2); 
     printf("%.0f\n", $2);
   }

```

---

### Post by stinkeye on 2013-11-12
Ok.
How exactly is this read **[^0-9.+-]**
Just don't quite get how the **[COLOR="#FF0000"]0[/COLOR]** in **+37.[COLOR="#FF0000"]0[/COLOR]°C** is removed.

---

### Post by Lars Noodén on 2013-11-12
It may be the formatting in printf.  

printf("%05.01f\n", $2)

---

### Post by stinkeye on 2013-11-12
> **Lars Noodén said:**
> It may be the formatting in printf.  

printf("%05.01f\n", $2)
So does the first part remove **°C** and **+** while
the printf rounds to a whole number.

Sorry about the silly questions...
just trying to understand enough for my own personal use without
learning all the ins and outs of awk.

---

### Post by Lars Noodén on 2013-11-12
For me, the decimal and the number following it is not removed:

```

$ echo "temp1:        +37.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor" | awk '/temp1/ {gsub("[^0-9.+-]","",$2); printf("%05.01f\n", $2)}'
037.0

```

The first part, gsub, removes the °C while leaving the plus sign.  The plus is in the set of allowed characters.  However, it gets interpreted away by %f in printf, as numbers are assumed to be positive.  If the line has "-37.0°C", printf prints it because the number is negative.

---

### Post by stinkeye on 2013-11-12
> **Lars Noodén said:**
> For me, the decimal and the number following it is not removed:

```

$ echo "temp1:        +37.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor" | awk '/temp1/ {gsub("[^0-9.+-]","",$2); printf("%05.01f\n", $2)}'
037.0

```

The first part, gsub, removes the °C while leaving the plus sign.  The plus is in the set of allowed characters.  However, it gets interpreted away by %f in printf, as numbers are assumed to be positive.  If the line has "-37.0°C", printf prints it because the number is negative.
Ok thanks, I'll have to look at the man page for printf to understand "**"%.0f\n"**" 
```
glen@Raring:~$ echo temp1 +**44.32**°C | awk '/temp1/ {gsub("[^0-9.+-]","",$2); printf("%.0f\n", $2)}'
44
glen@Raring:~$ echo temp1 +**44.67**°C | awk '/temp1/ {gsub("[^0-9.+-]","",$2); printf("%.0f\n", $2)}'
45
```

---

### Post by Lars Noodén on 2013-11-12
Try "%.0f\n", "%.01f\n" and "%.02f\n" for comparison.

---

### Post by stinkeye on 2013-11-12
> **Lars Noodén said:**
> Try "%.0f\n", "%.01f\n" and "%.02f\n" for comparison.
Aha , the lights on....(still nobody home though). ;) :p
Thanks.

---

