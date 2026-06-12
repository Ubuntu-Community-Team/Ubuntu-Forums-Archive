---
title: "[PYTHON] Replace a document line"
date: 2011-07-19
forum: Programming Talk
---

### Post by GTMoraes on 2011-07-19
Hey, I'm doing a little program here. I'm a beginner, by the way.
It'll manage a cinema (a theorical one) and it'll be responsible for reserving the seats and counting how much money have been earned so far.

Well, at first I managed to make it create a text file when it doesn't exist and read it when it exists (believe me, it took a long time for me to discover. I'm a beginner), made it enumerate (from 1 to 100, which is the capacity of the theorical cinema), using one line each number (sounds easier to modify and edit) and be able to list every free seat and reserved seat independently.

So, right now, Line 1 represents seat 1, and so on. 
On the text file, "1" represents a free seat. R1 represents a reserved seat.

My big problem here is: How do I add the "R" infront of a number, inside my program? I'm thinking here the easiest way would be by replacing the chosen number by R*number*. As each number is on their respective line, I would only need a command/script to change the chosen line to R*number*.

I've googled a little and only found people suggesting to use text editors to replace the requested line as desired. That ain't what I'm aiming for.

What do you guys suggest? I'm open to learning =)

Thanks in advance.

P.S.: Also, if possible, I wish to make it like this too: If I try to reserve an already reserved seat, it comes out with an error.

[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Big Rig PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by An Sanct on 2011-07-19
If I understand you correctly, you are using lines like

(sample file #1)
```

*{bof}*
1
2
3
4
.
*(other numbers)*
.
98
99
100
*{eof}*
```

where each line represents a seat. Then replacing the whole line might be right solution for you

```
   
..
for line in open("file"):
line = line.replace("someword","newword")
..
```
*I don't say this is the whole code and I also don't state it is working - before some troll jumps on me again and hassles me for being a bad developer (not helping the thread in any other way)....

This way, you could also build a file, that looks like this (and is much more pleasing to look at ...)

(sample file #2)
```

*{bof}*
 f01,  f02,  f03,  f04, f05 , f06, f07, f08, f09 , f10
 f11,  f12,  f13,  f14, f15 , f16, f17, f18, f19 , f20
.
 *(other numbers)*
 .
 f81,  f82,  f83,  f84, f85 , f86, f87, f88, f89 , f90
 f91,  f92,  f93,  f94, f95 , f96, f97, f98, f99 , f0A
*{eof}*
```
* I used f## and f0A, to represent 100, so that there is no mistake what to change.

The sample code was taken from [here]("http://www.daniweb.com/software-development/python/threads/70426"), take a look :) it should interest you. 

My personal note :) 
There is a lot to optimize here, the loop in the link would have 100 steps with sample file #1 and 10 with sample file #2, that is a huge optimization :), you could also drop the lines and have a single line (unreadable, but fast) and then just count the occurrence of "R" in the file, to see how full this virtual venue is.

---

### Post by Bodsda on 2011-07-19
If your file looks like this
 
```

F1
F2
F3
F4
R5
R6
.
.
F99
F100

```
 
And you want to reserve a seat, I would do this
 
```

file = open("./seats", "r")
lines = file.readlines()
file.close()
 
seat_number = int(raw_input("Enter the seat number to reserve: "))
 
lines[seat_number] = "R%s" % seat_number
 
file = open("./seats", "w")
 
count = 0
for i in lines:
    file.write(lines[count])
    count += 1
 
file.close()

```
 
(code not tested)
 
HTH
Bodsda

---

### Post by TwoEars on 2011-07-19
> **Bodsda said:**
> 
 
And you want to reserve a seat, I would do this
 
```

file = open("./seats", "r")
lines = file.readlines()
file.close()
 
seat_number = int(raw_input("Enter the seat number to reserve: "))
 
lines[seat_number] = "R%s" % seat_number
 
file = open("./seats", "w")
 
count = 0
for i in lines:
    file.write(lines[count])
    count += 1
 
file.close()

```
 
(code not tested)
 
HTH
Bodsda

No no no! This is bad code to show to a beginner, considering the number of mistakes in it.

```

seat_number = int(raw_input("Enter the seat number to reserve: "))
```

Uncatched exception.

```
lines[seat_number] = "R%s" % seat_number
``` 

You've just converted seat_number to int - it's not a string, so %s is not the right thing to use.

```
count = 0
for i in lines:
    file.write(lines[count])
    count += 1
```
This is not how we do this in python. Not at all - you don't even need count, you have "i"! What about enumerate, if you did need a count? That's what you should use here. i is also a _very_ poor name for the variable in this case! i should only be used as a simple counter - not as a line! Perhaps a better name should be what it is, how about "line"?

What would be better is actually something like - 

```

f = open('seats.txt')
lines = f.readlines()
f.close()

seat_number = validate(raw_input("Enter the seat number to reserve: "))
# where validate is a function for the OP to write to ensure it's a valid int

lines[seat_number -1] = 'R%d' % seat_number

f = open('seats.txt','wb')
f.writelines(lines)
f.close()

```


@OP
Of course, this is not the ideal way of doing this - it involves loading the whole file into memory and then writing every line over again. 
For a better way, look into fileinput with inplace=1. Or for something with excessive search/writes like this, you should look into sqlite3.
Could you post all the code you've done so far, and some example text from your text file?

---

### Post by GTMoraes on 2011-07-19
Sure, I'll post the code when I get on my netbook.

I've reduced the number of seats. It'll be a 4x4 room now (as I started with Tkinter, I want to make a nifty graphical interface)

The text file is like this:
```

1
2
3
R4
R5
6
7
R8
M9
M10
R11
12
13
14
15
R16

```
Pure numbers are available seats
"R-Numbers" are reserved seats
"M-Numbers" are reserved seats, which have been bought half-price.

The codes above looks easy to implement, I'm thinking on something like:
· Ask for seat: "Which seat do you want to reserve? - *number"
» Check for availability (seems easy, it's just to check if the chosen line starts with a number or not. If it doesn't, it's reserved.). It would be done without user intervention.
· Ask for half-price: "Half price? - (Y or N)"
· Edit the text file.

I'll try to understand each code above. Thank you guys very much for the suggestions =)

An Sanct suggested to optimize the code, by placing the seats on a single line. At first I tried this, but I want to list the free seats (lines that doesn't start with R or M), reserved seats (lines that starts with R and M) and half-priced seats (lines that starts with M).
I just started on programmation and Python so um.. I don't know how would I make it read the free/reserved seats being on a single line

This looks great:

> **An Sanct said:**
> 
(sample file #2)
```

*{bof}*
 f01,  f02,  f03,  f04, f05 , f06, f07, f08, f09 , f10
 f11,  f12,  f13,  f14, f15 , f16, f17, f18, f19 , f20
.
 *(other numbers)*
 .
 f81,  f82,  f83,  f84, f85 , f86, f87, f88, f89 , f90
 f91,  f92,  f93,  f94, f95 , f96, f97, f98, f99 , f0A
*{eof}*
```


But I don't know how to make it - still, hehe.

By using an line-by-line approach, I'm thinking I'm getting an easier to edit file (and to search too), but when I want to list the free chairs, by example, I'm getting an output like this:
```

Seat free: 1

Seat free: 2

Seat free: 3

...

```

When I was using, at first, 100 chairs, it didn't look good at all. Also, this read/visual output was too slow (took a second to show every data).

I think, with an one-liner approach, I'll be able to fix this little issue, showing the free seats like this:
```

Seats free: 1, 2, 3, 4...

```

I'll pick my netbook soon and I'll post my actual code.
I won't be surprised if there are optimizations to be done =P
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Big Rig PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by GTMoraes on 2011-07-19
Here it goes.
I'm using a new reply for viewing' sake.

```

try:
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    reservation.close()
except IOError:
    reservation=open("reservation.pycine", "w+", encoding="utf-8")
    for chairs in range (1,17):
        reservation.write("%d\n" % chairs)
    reservation.close()

def reserve_seat():
    cad = input("Which seat to reserve? ")
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    for line in reservation:
        line = line.replace(cad, 'R'+cad)
    reservation.close
# Reservation doesn't work.

def available_seats():
    reservation=open("reservation.pycine", "r", encoding="utf-8")
    for seat in reservation.readlines():
        if seat[0]=="R":
            continue
        else:
            print("-"*5)
            print("Seat free: %s" % seat)
        reservation.close()
# Works, but not as beautifully as desired

def reserved_seats():
   reservation=open("reservation.pycine", "r", encoding="utf-8")
   for seat in reservation.readlines():
        if seat[0]=="R":
            print("Reserved seat: %s" % seat[1:])
        reservation.close()
# Same as above.
        
def income():
    b=0
    reservation=open("reservation.pycine", "r", encoding="utf-8")
    for seat in reservation.readlines():
        if seat[0]=="R":
            b=b+12
        if seat[0]=="M":
            b=b+6
        print(b)
        reservation.close()
# It outputs the whole counting operation - I only want the final number.

def options(option,a,z):
    while True:
        try:
            opt=int(input(option))
            if a <= opt <= z:
                return(opt)
        except:
            print("Invalid option. The valid options are between %d and %d" % (a,z))

def menu():
    print("""
PyCine 0.1b
1 - Reserve a seat
2 - View available seats
3 - View reserves
4 - View total income

0 - Quit.
""")
    return(opções("Choose an option: ", 0,4))
while True:
    option = menu()
    if option == 0:
        print("-"*30)
        b=input("Do you really want to quit?\nY/N: ")
        bl=b.lower()
        if bl=="y":
            print("Closing..")
            reservation.close()
            break
        else:
            continue
    elif option == 1:
        reserve_seat()
    elif option == 2:
        available_seats()
    elif option == 3:
        reserved_seats()
    elif option == 4:
        income()

```

I feel like an global variable will be pretty handy there, but I don't know how to use it properly - yet.

I also want to add there and function to, if there are no reserved seats, it outputs "There are no reserves!", same thing with free seats.
It might be easy, but I was looking forward to make the basic mechanics work.
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Big Rig PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by TwoEars on 2011-07-19
```
def income():
    b=0
    reservation=open("reservation.pycine", "r", encoding="utf-8")
    for seat in reservation.readlines():
        if seat[0]=="R":
            b=b+12
        if seat[0]=="M":
            b=b+6
        print(b)
        reservation.close()
# It outputs the whole counting operation - I only want the final number.
```
You're running print(b) inside the for loop, which is why it prints the entire operation.

reservation.close() is also inside the for loop, shouldn't be, same applies to reserved_seats, available_seats.



What you're after isn't simple, at least, not in the format you've given. Something simpler, like -

```

R,1,2,4,5
M,3,6
F,7

```

That way you can load it right into a dict. Of course, I'd use the pickle module - but tha't sprobably too complex for you right now.

```
f = open('fi.txt','r')

d = dict()
for line in f.readlines():
    seat_type = line[0]
    d[seat_type] = [int(x) for x in line[2:].split(',')]

f.close()

```

Editing files in-place is hard. If you can minimize the amount of lines there are in this file, then it will be much simpler to load the entire file and the write it all over again. 

Your code will be best suited to a class - hold the variables in memory while the program is running, and then when it's exited, it should save and write to file.

---

### Post by GTMoraes on 2011-07-19
> **TwoEars said:**
> ```
def income():
    b=0
    reservation=open("reservation.pycine", "r", encoding="utf-8")
    for seat in reservation.readlines():
        if seat[0]=="R":
            b=b+12
        if seat[0]=="M":
            b=b+6
        print(b)
        reservation.close()
# It outputs the whole counting operation - I only want the final number.
```
You're running print(b) inside the for loop, which is why it prints the entire operation.

reservation.close() is also inside the for loop, shouldn't be, same applies to reserved_seats, available_seats.

Hey, thanks! I didn't notice this. It's printing only the final number now.

The other ones didn't change anything.


> **TwoEars said:**
> 
What you're after isn't simple, at least, not in the format you've given. Something simpler, like -

```

R,1,2,4,5
M,3,6
F,7

```

That way you can load it right into a dict. Of course, I'd use the pickle module - but tha't sprobably too complex for you right now.

```
f = open('fi.txt','r')

d = dict()
for line in f.readlines():
    seat_type = line[0]
    d[seat_type] = [int(x) for x in line[2:].split(',')]

f.close()

```

Editing files in-place is hard. If you can minimize the amount of lines there are in this file, then it will be much simpler to load the entire file and the write it all over again. 

Your code will be best suited to a class - hold the variables in memory while the program is running, and then when it's exited, it should save and write to file.
I'm not too good with dictionaries, still working on it.
The way you proposed it looks cleaner and lighter: a line for reserved seats, another one for half-price seats and another for free seats. It'll even output like I want on available_seats and reserved_seats.

How i'd do that?

---

### Post by TwoEars on 2011-07-19
> **GTMoraes said:**
> Hey, thanks! I didn't notice this. It's printing only the final number now.

The other ones didn't change anything.



I'm not too good with dictionaries, still working on it.
The way you proposed it looks cleaner and lighter: a line for reserved seats, another one for half-price seats and another for free seats. It'll even output like I want on available_seats and reserved_seats.

How i'd do that?

Just because you don't _see_ what changed, it doesn't mean nothing changed ;) It saves unneeded calls to close the file, saving speed.

Indeed, and you'd only need to write 3 lines.

As for putting it into a class - classes are fairly complicated concepts - have a read of this [http://docs.python.org/tutorial/classes.html](http://docs.python.org/tutorial/classes.html)
and come back with any more questions you have.

---

### Post by GTMoraes on 2011-07-19
> **TwoEars said:**
> Just because you don't _see_ what changed, it doesn't mean nothing changed ;) It saves unneeded calls to close the file, saving speed.

Indeed, and you'd only need to write 3 lines.

As for putting it into a class - classes are fairly complicated concepts - have a read of this [http://docs.python.org/tutorial/classes.html](http://docs.python.org/tutorial/classes.html)
and come back with any more questions you have.

I've took a look at the link.. Looks fairly complicated...
I'm still trying to make the reserve_seat() to work. I've tried the first script and it's a no-go.

----

Cheap-debugging (using print), I've found and interesting fact.
```


>>> 

PyCine 0.1b
1 - Reserve a seat
2 - View available seats
3 - View reserves
4 - View total income

0 - Quit.

Choose an option: 2
-----
Seat free: 1

-----
Seat free: 2

-----
Seat free: 3

-----
Seat free: 4

-----
Seat free: 5

-----
Seat free: 6

-----
Seat free: 7

-----
Seat free: 8

-----
Seat free: 9

-----
Seat free: 10

-----
Seat free: 11

-----
Seat free: 12

-----
Seat free: 13

-----
Seat free: 14

-----
Seat free: 15

-----
Seat free: 16


PyCine 0.1b
1 - Reserve a seat
2 - View available seats
3 - View reserves
4 - View total income

0 - Quit.

Choose an option: 1
Which seat to reserve? 10
10
10
1

2

3

4

5

6

7

8

9

R10

11

12

13

14

15

16

Which seat to reserve? 10

PyCine 0.1b
1 - Reserve a seat
2 - View available seats
3 - View reserves
4 - View total income

0 - Quit.

Choose an option: 2
-----
Seat free: 1

-----
Seat free: 2

-----
Seat free: 3

-----
Seat free: 4

-----
Seat free: 5

-----
Seat free: 6

-----
Seat free: 7

-----
Seat free: 8

-----
Seat free: 9

-----
Seat free: 10

-----
Seat free: 11

-----
Seat free: 12

-----
Seat free: 13

-----
Seat free: 14

-----
Seat free: 15

-----
Seat free: 16


PyCine 0.1b
1 - Reserve a seat
2 - View available seats
3 - View reserves
4 - View total income

0 - Quit.

Choose an option: 0
------------------------------
Do you really want to quit?
S/N: s
Closing..
>>> 

```

so, it's just not saving the file.
How do I do it?

---

### Post by TwoEars on 2011-07-19
> **GTMoraes said:**
> I've took a look at the link.. Looks fairly complicated...
I'm still trying to make the reserve_seat() to work. I've tried the first script and it's a no-go.

Alright, let me give you a clue - 

Change the function to this -

```

def reserve_seat():
    cad = input("Which seat to reserve? ")
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    for line in reservation:
        print(type(line))
    reservation.close()

```
What does that tell you about the "line" variable? 
Is it special in anyway? 
How does it compare to say, ```
print(type("I am a plain old string"))
```
?

And then after to this - 

```

def reserve_seat():
    cad = input("Which seat to reserve? ")
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    seats = reservation.readlines()
    reservation.close()
    for line in seats:
        print(type(line))

```
What does that tell you about the file object "reservation"? 
Does it need to be open for this to work, or can it be closed?
What does this tell you about your function?

(Note, it's broken in another way too - but I'll get to that after you work this out :) )

---

### Post by TwoEars on 2011-07-19
Doh, in the time I wrote the reply, you had edited your text and had found the problem. Well done ;)

My suggestion to you is to find out how you save any old file - though, it's more a case of writing the file, not saving. See the above debugging process to work that one out ;)

My clue is that you've already done it once - look into your own code and see what can be reused, baring in mind you will have to write *a new copy* of the file - you can't edit the old one in-place easily.

---

### Post by GTMoraes on 2011-07-19
> **TwoEars said:**
> Doh, in the time I wrote the reply, you had edited your text and had found the problem. Well done ;)

My suggestion to you is to find out how you save any old file - though, it's more a case of writing the file, not saving. See the above debugging process to work that one out ;)

My clue is that you've already done it once - look into your own code and see what can be reused, baring in mind you will have to write *a new copy* of the file - you can't edit the old one in-place easily.

Good idea. Overwriting completely the original file, right?
I'll try doing this. Thanks for the tip =)

---

### Post by GTMoraes on 2011-07-19
lol I'm getting my **** beaten here. If I put the print(line) inside the for loop, it outputs the file just like I want.
If I put it outside the loop, it'll only print the last seat (16).
If I make it write inside the loop, the program keeps writing forever.

This forever write is kinda weird. It outputs the file like this (I've tried to reserve the 10th seat)
```

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
1
...
9
R10
11
...
16
1
...
9
RR10
11
...
16
1
...
9
RRR10
11
...
16
1
...
9
RRRR10
11
...

```
Hope you get it. The code I used was the following one:
```

def reserve_seat():
    cad = input("Which seat to reserve? ")
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    for line in reservation:
        line = line.replace(cad, 'R'+cad)
        reservation.write("%s" % line)
    reservation.close()

```
Outside the loop it prints a extra line with "16" (the last original line)

Looks like I'm too noob for this hehe

What do you suggest me to do?

---

### Post by TwoEars on 2011-07-19
> **GTMoraes said:**
> Good idea. Overwriting completely the original file, right?
I'll try doing this. Thanks for the tip =)

Yup, unless you want to spend time looking into seek and other complicated features of file objects. ;)

Now, for the other tip -

Say I have the code like you have, 

```

random_numbers = ['1','2','3','10']
number_reserved = '1'
for number in random_numbers:
    number = number.replace(number_reserved, 'This number has been edited')
    print(number)
print(random_numbers)

```
How many numbers from random_numbers are edited? Is this what you expected?

Is random_numbers updated, or is it the same as the original? 

Hope this helps.

---

### Post by TwoEars on 2011-07-19
> **GTMoraes said:**
> lol I'm getting my **** beaten here. If I put the print(line) inside the for loop, it outputs the file just like I want.
If I put it outside the loop, it'll only print the last seat (16).
If I make it write inside the loop, the program keeps writing forever.

This forever write is kinda weird. It outputs the file like this (I've tried to reserve the 10th seat)
```

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
1
...
9
R10
11
...
16
1
...
9
RR10
11
...
16
1
...
9
RRR10
11
...
16
1
...
9
RRRR10
11
...

```
Hope you get it. The code I used was the following one:
```

def reserve_seat():
    cad = input("Which seat to reserve? ")
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    for line in reservation:
        line = line.replace(cad, 'R'+cad)
        reservation.write("%s" % line)
    reservation.close()

```
Outside the loop it prints a extra line with "16" (the last original line)

Looks like I'm too noob for this hehe

What do you suggest me to do?

I would suggest first reading the contents, closing the file, reopen the file for writing (completely clearing the file wth 'w'), and then try your code.

---

### Post by GTMoraes on 2011-07-19
Certainly, I'm overlooking something.
It is replacing correctly, but it's not writing on the file.

I've tried doing what you suggested:
Read the contents, close the file, reopen the file for writing (completely clearing the file wth 'w'), and then running it.
I've did the following:
```


def reserve_seat():
    cad = input("Which seat to reserve? ")
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    for line in reservation:
        reservation.close()
        reservation=open("reservation.pycine", "w", encoding="utf-8")
        line = line.replace(cad, 'R'+cad)
        reservation.write("%s" % line)
    reservation.close()

```
this returns an I/O Error for me (Operation on closed file).

Then I tried this:
```

def reserve_seat():
    cad = input("Which seat to reserve? ")
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    for line in reservation:
        reservation=open("reservation.pycine", "w", encoding="utf-8")
        line = line.replace(cad, 'R'+cad)
        reservation.write("%s" % line)
    reservation.close()

```
It creates a new file... with only the "16" number on the first line.

I feel like I'm closer to solve this. Thank you for you help so far! I've learned a lot

---

### Post by TwoEars on 2011-07-19
```
def reserve_seat():
    cad = input("Which seat to reserve? ")
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    for line in reservation:
        reservation.close()
        reservation=open("reservation.pycine", "w", encoding="utf-8")
        line = line.replace(cad, 'R'+cad)
        reservation.write("%s" % line)
    reservation.close()
```

Well, here's another tip - you can read the entire contents of a file using the readlines method, for example -

```

reservation=open("reservation.pycine", "r+", encoding="utf-8")
seats = reservation.readlines()
reservation.close()
new_file = open("reservation.pycine", "w", encoding="utf-8")
for seat in seats:
    new_file.write(seat)
new_file.close()

```
Try adapting that for your usage and see my previous comment about the replace method.

---

### Post by GTMoraes on 2011-07-19
Oohhh, so that was it!
I needed to create another variable to handle the file modification.

With your help, I've managed to make it work!
Finally! The program now works!

I can now proceed with Tkinter. Hope I don't face such little problems hehe

Again, thank you very much!


P.S.: Just for the info, I needed to edit the file creation to instead of creating 1,2,3,4..., create 01,02,03..., otherwise when I reserve the seat 5, it would break the 15th seat, by renaming it to 1R5 hehe.
```

try:
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    reservation.close()
except IOError:
    reservation=open("reservation.pycine", "w+", encoding="utf-8")
    for seats in range (1,17):
        reservation.write("%02d\n" % seats)
    reservation.close()

```

---

### Post by TwoEars on 2011-07-19
> **GTMoraes said:**
> Oohhh, so that was it!
I needed to create another variable to handle the file modification.

With your help, I've managed to make it work!
Finally! The program now works!

I can now proceed with Tkinter. Hope I don't face such little problems hehe

Again, thank you very much!


P.S.: Just for the info, I needed to edit the file creation to instead of creating 1,2,3,4..., create 01,02,03..., otherwise when I reserve the seat 5, it would break the 15th seat, by renaming it to 1R5 hehe.
```

try:
    reservation=open("reservation.pycine", "r+", encoding="utf-8")
    reservation.close()
except IOError:
    reservation=open("reservation.pycine", "w+", encoding="utf-8")
    for seats in range (1,17):
        reservation.write("%02d\n" % seats)
    reservation.close()

```

That could've been resolved if you changed your 
```
        line = line.replace(cad, 'R'+cad)

```
to being encapsulated in an if statement. ;)

---

### Post by GTMoraes on 2011-07-19
> **TwoEars said:**
> That could've been resolved if you changed your 
```
        line = line.replace(cad, 'R'+cad)

```
to being encapsulated in an if statement. ;)

Understood, but numerating from 01, 02 looks a little bit neater hehe

Here's the program. It's not optimized at all, I just wanted to make it work, then I'll work on optimization

```


try:
    reservas=open("reservas.pycine", "r+", encoding="utf-8")
    reservas.close()
except IOError:
    reservas=open("reservas.pycine", "w+", encoding="utf-8")
    for cadeiras in range (1,17):
        reservas.write("%02d\n" % cadeiras)
    reservas.close()

def reservar_cadeira():
    cad = input("Which seat to reserve? - ")
    meia = input("Half Price?(Y/N) - ")
    meial = meia.lower()
    if meial == "y":
        reservas=open("reservas.pycine", "r", encoding="utf-8")
        cadeiras=reservas.readlines()
        reservas.close()
        reservas2=open("reservas.pycine", "w", encoding="utf-8")
        for cadeira in cadeiras:
            cadeira = cadeira.replace(cad, 'M'+cad)
            reservas=open("reservas.pycine", "w", encoding="utf-8")
            reservas2.write("%s" % cadeira)
        reservas2.close()
    else:
        reservas=open("reservas.pycine", "r", encoding="utf-8")
        cadeiras=reservas.readlines()
        reservas.close()
        reservas2=open("reservas.pycine", "w", encoding="utf-8")
        for cadeira in cadeiras:
            cadeira = cadeira.replace(cad, 'R'+cad)
            reservas=open("reservas.pycine", "w", encoding="utf-8")
            reservas2.write("%s" % cadeira)
        reservas2.close()

def cadeiras_disponiveis():
    reservas=open("reservas.pycine", "r+", encoding="utf-8")
    for cadeira in reservas.readlines():
        if cadeira[0]=="R":
            continue
        elif cadeira[0]=="M":
            continue
        else:
            print("Available seat: %s" % cadeira)
    reservas.close()
def cadeiras_reservadas():
   reservas=open("reservas.pycine", "r+", encoding="utf-8")
   for cadeira in reservas.readlines():
        if cadeira[0]=="R":
            print("Reserved seat: %s" % cadeira[1:])
        elif cadeira[0]=="M":
            print("Reserved seat: %s" % cadeira[1:])
        reservas.close()
        
def receita():
    b=0
    reservas=open("reservas.pycine", "r", encoding="utf-8")
    for cadeira in reservas.readlines():
        if cadeira[0]=="R":
            b=b+1300
        if cadeira[0]=="M":
            b=b+650
    print("-"*5)
    print("The actual income is US$%5.2f" % (b/100))
    reservas.close()
def opções(opção,a,z):
    while True:
        try:
            opc=int(input(opção))
            if a <= opc <= z:
                return(opc)
        except:
            print("Invalid option. Choose between %d and %d" % (a,z))

def menu():
    print("""
PyCine 0.3b
1 - Reserve a seat
2 - View available seats
3 - View reserves
4 - View income

0 - Quit.
""")
    return(opções("Choose an option: ", 0,4))
while True:
    opção = menu()
    if opção == 0:
        print("-"*30)
        b=input("Do you really want to quit?\nY/N: ")
        bl=b.lower()
        if bl=="y":
            print("Quitting..")
            reservas.close()
            break
        else:
            continue
    elif opção == 1:
        reservar_cadeira()
    elif opção == 2:
        cadeiras_disponiveis()
    elif opção == 3:
        cadeiras_reservadas()
    elif opção == 4:
        receita()


```

It's in portuguese, but I translated the 'interface' to english, for viewer's pleasure

---

