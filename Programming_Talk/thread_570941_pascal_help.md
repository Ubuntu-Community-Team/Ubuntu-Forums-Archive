---
title: "pascal help"
date: 2007-10-08
forum: Programming Talk
---

### Post by snickers295 on 2007-10-08
can someone tell me in the code below how to get all of the variables into the file insted of just the first one?
```
program test;
uses crt;
var
f: file of string;
fname, lname, gender, country, age, data : string;
answer: char;
begin
Assign(f,'names.txt');
reset(f);
writeln('Enter your first name: '); readln (fname);
writeln('Enter your last name: '); readln (lname);
writeln('Enter your gender: '); readln (gender);
writeln('Enter your country: '); readln (country);
writeln('Enter Your age: '); readln (age);
clrscr;
writeln (fname);
writeln (lname);
writeln (gender);
writeln (country);
writeln (age);
write(f,fname,lname,gender,country,age);
write(f,lname);
writeln('Would you like to read the data of this file?: ');
readln (answer);
if (answer = 'y') then
clrscr;
reset(F);
read(f,data);
writeln (data);
end.
```

---

### Post by samjh on 2007-10-08
I think write only accepts one variable to write to file

So instead of ```
write(f,fname,lname,gender,country,age);
```
it should be one write per variable you want to write
```
write (f, fname);
write (f, lname);
write (f, gender);
write (f, country);
write (f, age);
```

---

### Post by snickers295 on 2007-10-08
my compiler (free pascal compiler 2.0.4) comes up with this:
```
test.psc(4,16) Error: Identifier not found "data"
test.psc(21,1) Error: Can't use readln or writeln on typed file
test.psc(21,19) Error: Illegal expression
test.psc(22,1) Error: Can't use readln or writeln on typed file
test.psc(22,19) Error: Illegal expression
test.psc(23,1) Error: Can't use readln or writeln on typed file
test.psc(23,20) Error: Illegal expression
test.psc(24,1) Error: Can't use readln or writeln on typed file
test.psc(24,21) Error: Illegal expression
test.psc(25,1) Error: Can't use readln or writeln on typed file
test.psc(25,17) Error: Illegal expression
test.psc(31,12) Error: Argument can't be assigned to
test.psc(34) Fatal: There were 12 errors compiling module, stopping

```

---

### Post by samjh on 2007-10-09
Sorry, should have been write not writeln.

---

### Post by snickers295 on 2007-10-09
this woked:
```
program test;
uses crt;
var
f: text;
fname, lname, gender, country, age, data : string;
answer: char;
begin
Assign(f,'names.txt');
reset(f);
writeln('Enter your first name: '); readln (fname);
writeln('Enter your last name: '); readln (lname);
writeln('Enter your gender: '); readln (gender);
writeln('Enter your country: '); readln (country);
writeln('Enter Your age: '); readln (age);
clrscr;
writeln (fname);
writeln (lname);
writeln (gender);
writeln (country);
writeln (age);
rewrite (f);
writeln (f,fname,' ',lname,' ',gender,' ',country,' ',age);
writeln('Would you like to read the data of this file?: ');
readln (answer);
if (answer = 'y') then
clrscr;
reset(f);
read(f,data);
writeln (data);
end.
``` instead of file of string i put text and now writeln will work.
one more thing though every time it writes the file it overwrites what it saved before. any idea how to get it to save data to the end of the file?
thanks

---

### Post by snickers295 on 2007-10-09
if possible could someone correct my program source?

---

