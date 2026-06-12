---
title: "Bash Scripts for movies theatre booking system"
date: 2011-05-09
forum: Programming Talk
---

### Post by zaser3 on 2011-05-09
Hi guys,

How do i create seating plans in bash script? Example below.


      Screen
  A  B  C  D  E
1 X
2       X
3    X
4             X

1. How to I create this layout? So when I run the program, it will be empty initially. Like this.
      Screen
  A  B  C  D  E
1 
2       
3    
4             

2. Will prompt user to select seats
user key in: A2, B3 After will record the data and display the following for confirmation

      Screen
  A  B  C  D  E
1 
2 [COLOR="blue"]X[/COLOR]     
3    [COLOR="Blue"]X[/COLOR]
4             

X represents the seat that user selects, and ask for confirmation
Eg. User select total of _2_ seats for $10
To confirm, please Key Y or N to cancel: Y
(then it will store the data, other users that want to do booking will notice that the seats selected by previous user are already booked with an X)

Please help! Thank You!!

---

### Post by lloyd_b on 2011-05-09
> **zaser3 said:**
> Hi guys,

How do i create seating plans in bash script? Example below.


      Screen
  A  B  C  D  E
1 X
2       X
3    X
4             X

1. How to I create this layout? So when I run the program, it will be empty initially. Like this.
      Screen
  A  B  C  D  E
1 
2       
3    
4             

2. Will prompt user to select seats
user key in: A2, B3 After will record the data and display the following for confirmation

      Screen
  A  B  C  D  E
1 
2 [COLOR="blue"]X[/COLOR]     
3    [COLOR="Blue"]X[/COLOR]
4             

X represents the seat that user selects, and ask for confirmation
Eg. User select total of _2_ seats for $10
To confirm, please Key Y or N to cancel: Y
(then it will store the data, other users that want to do booking will notice that the seats selected by previous user are already booked with an X)

Please help! Thank You!!

Looks suspiciously like a homework problem...

A hint - while Bash doesn't support two dimensional arrays, you can emulate one using a single dimension array and offsets.  For example, "A" would be offset 0, "B" would be offset 4, "C" would be offset 8.  Then add the offset to the selected row (for instance for C3, you'd add the offset of 8 to 3, which would tell you that array[11] is associated with seat 3C).

A little trickery using the offsets in a 'for' loop would give you a simple way to display the seating chart.

Lloyd B.

---

### Post by zaser3 on 2011-05-09
> **zaser3 said:**
> Hi guys,

How do i create seating plans in bash script? Example below.


      Screen
  A  B  C  D  E
1 X
2       X
3    X
4             X

1. How to I create this layout? So when I run the program, it will be empty initially. Like this.
      Screen
  A  B  C  D  E
1 
2       
3    
4             

2. Will prompt user to select seats
user key in: A2, B3 After will record the data and display the following for confirmation

      Screen
  A  B  C  D  E
1 
2 [COLOR="blue"]X[/COLOR]     
3    [COLOR="Blue"]X[/COLOR]
4             

X represents the seat that user selects, and ask for confirmation
Eg. User select total of _2_ seats for $10
To confirm, please Key Y or N to cancel: Y
(then it will store the data, other users that want to do booking will notice that the seats selected by previous user are already booked with an X)

Please help! Thank You!!
Thanks, but I am new to Bash scripting,

How do you write offset in arrays? Do you have an example? 

Thank You!

---

### Post by Tony Flury on 2011-05-09
If this is homework - which I suspect it is, then we wont give you code examples. The way this forum works is that you have to show at least some attempt to get it right.

There are multiple ways of doing this - including of course using a language that supports the programming features that your application needs.

---

### Post by zaser3 on 2011-05-11
Yes it is a homework, but I need help in writing array offsets, how does it look like?

i know array is declared like this

array[20] but how to write into array in bash scripting?

Please Help, thank you

---

### Post by slavik on 2011-05-11
try google.

---

### Post by matt_symes on 2011-05-11
Hi

Have a read on the section arrays in this link.

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

If you want to learn shell scripting read the entire site and also have a look at [http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)

Understand about portability issues on bash and bourne (Posix) shells. It will help you understand the difference between [ ] against [[ ]] and $() against backticks ` ` etc. Make sure you use the correct syntax for the shell you are using on your course and it never goes amiss to explain the differences in your coursework.

Kind regards

---

