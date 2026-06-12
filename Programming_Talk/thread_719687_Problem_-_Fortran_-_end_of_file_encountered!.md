---
title: "Problem - Fortran - end of file encountered!?"
date: 2008-03-09
forum: Programming Talk
---

### Post by subduer on 2008-03-09
I have some problem with application programming in FORTRAN77.

The program works on the next way: it read numbers from input file [MKTE1.dat] and write output: MTKE1.mdm

When I stared: [MTKE1.exe MTE1.dat] from DOS it shows me:

run-time error F6501: READ (mkte1.dat)
- end of file encountered

there some problem with input files [mkte1.dat]. The numbers are OK. 
Does somebody know to control the source-code with input files?

tnx a lot if someone hel me;)
sory for bad english!

there is:
[source-code: 2 pictures]

[[IMG]http://img89.imageshack.us/img89/1770/strana111fu6.th.jpg[/IMG]](http://img89.imageshack.us/my.php?image=strana111fu6.jpg)

[[IMG]http://img212.imageshack.us/img212/9915/strana222hf0.th.jpg[/IMG]](http://img212.imageshack.us/my.php?image=strana222hf0.jpg)

Fortran.zip (MKTE1.EXE, DOSXMSF.EXE, MKTE1.DAT):

[http://rapidshare.com/files/97826598/Fortran.rar.html](http://rapidshare.com/files/97826598/Fortran.rar.html)

---

### Post by Fbot1 on 2008-03-09
I can't download the files, try attaching it.

---

### Post by subduer on 2008-03-09
ok.

I packed all in one file:
allinone.zip

best regards!

---

### Post by beren.olvar on 2008-03-09
are you sure your input file is ok?
you could try using "read"  this way:

do ...
read (unit,format,end=10)
enddo

10 continue

this way it handles the eof when reached

cheers

---

### Post by subduer on 2008-03-09
friend..

I dont't know want did you meen exactly..
here is input:

    5   18   19    2    1    4    8    2    1
 7694.0000 3762.0000
    0.0000    0.0000
   30.5273    2.6708
   60.1271   10.6020
   87.9000   23.5528
  113.0021   41.1295
  134.6705   62.7979
  152.2472   87.9000
  165.1980  115.6729
  173.1292  145.2727
  175.8000  175.8000
  173.1292  206.3273
  165.1980  235.9271
  152.2472  263.7000
  134.6705  288.8021
  113.0021  310.4705
   87.9000  328.0472
   60.1271  340.9980
   30.5273  348.9292
    0.0000  351.6000
    1    1    2        8.00000        0.00000
    2    2    3        8.00000        0.00000
    3    3    4        8.00000        0.00000
    4    4    5        8.00000        0.00000
    5    5    6        8.00000        0.00000
    6    6    7        8.00000        0.00000
    7    7    8        8.00000        0.00000
    8    8    9        8.00000        0.00000
    9    9   10        8.00000        0.00000
   10   10   11        8.00000        0.00000
   11   11   12        8.00000        0.00000
   12   12   13        8.00000        0.00000
   13   13   14        8.00000        0.00000
   14   14   15        8.00000        0.00000
   15   15   16        8.00000        0.00000
   16   16   17        8.00000        0.00000
   17   17   18        8.00000        0.00000
   18   18   19        8.00000        0.00000
    1    1    1    1    1    1.0000    1.0000    1.0000    1.0000
   19    1    1    1    1    1.0000    1.0000    1.0000    1.0000
    1 3762.0000    4     1000.00000
      210.00000      210.00000        0.30000        0.30000       80.76920


where to put your adds.. please tell me.

---

### Post by beren.olvar on 2008-03-09
the read statement has several options,
 you first have to put a number indicating the unit to read from,
then a format, after that you can put optional fields, for example:

do i=1,100
read(10,*) a,b,c
enddo
20 continue

while inside the loop this will read from unit 10 and store the 3 first fields into the variables a b and c. but, what happens if there are less than 100 rows??
then you will find an EOF (end of file) and your program will complain. so what we do is 

do i=1,100
read(10,*,end=20) a,b,c
enddo
20 continue

the extra parameter "end=20" tells the program when EOF reached, go right to label 20.
(the "20 continue" part)

I suggest you that if you are not very familiar to the language try looking at a tutorial ([http://www.math.hawaii.edu/~hile/fortran/fort7.htm](http://www.math.hawaii.edu/~hile/fortran/fort7.htm))

I coudn't spot the specific problem, but if you post the whole output of the program maybe something shows up.

other point, when it ask you for "EXIT TO LU?" or some... what do u put? i think there should be some unit(integer) not used in the code: try 150 or so

good luck!

---

### Post by subduer on 2008-03-11
There is full source-cod [ FSME.f ] and input file [ MKTE1.dat ].

[http://rapidshare.com/files/98835155/002.rar.html](http://rapidshare.com/files/98835155/002.rar.html)

I tried to run it from Force 2.0 and it shows me a wrong again.
There are some mistakes.

@beren.oval
tnx for tut. It is good!
I read the last post several times, but I didn't understand the last few words.

Can U try now, with source code?
I don't know what happened. There is no reading from mkte1.dat again!!

---

### Post by beren.olvar on 2008-03-13
I am sorry for the delay

the problem i can spot is that the format the program is waiting doesn't correspond with the input file,
this is easily fixed, wherever it says
  READ(103,number)
replace for
  READ(103,*)

that should work.

after doing so, and recompiling, you have to run your program this way:

```

rm MKTE1.MDM
./program
EXIT TO LU=?
77

<here goes the output>

```

you HAVE to delete MKTE1.MDM before running your code, because it is tagged as new.
your programs ask for LU, you have to input some integer like 77.

hope it works for you too!!!
cheers.

---

