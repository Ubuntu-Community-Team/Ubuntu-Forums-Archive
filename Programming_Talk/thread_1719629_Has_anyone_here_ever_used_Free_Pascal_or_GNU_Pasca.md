---
title: "Has anyone here ever used Free Pascal or GNU Pascal?"
date: 2011-04-02
forum: Programming Talk
---

### Post by Learning Linux 2011 on 2011-04-02
Greetings,

I am new to Linux and Linux programming.

I used to program Turbo Pascal in DOS a long time ago.  I have some old programs that I thought I could copy and paste into Linux to get started.

I downloaded both Free Pascal and GNU Pascal, opened a terminal and tried to compile this Pascal program (one of the first programs I ever created) :

```
{This program reads in an integer and cubes it}

Program cube;
var n : integer;

Begin
writeln(' Please enter an integer and this program will cube it');
readln (n);
writeln( 'The cube of ' ,n, ' is ' , n * sqr(n), '.');
readln;
End.
```


I saved the file as Cube.pas in my Home directory.

Can anyone tell me how to get started using Linux?  Do I need to do something else? 
This program works in DOS using Turbo Pascal 7.

---

### Post by Vaphell on 2011-04-02
with gnu pascal
```
gpc Cube.pas -o cube
```
it will produce binary file named cube

---

### Post by Learning Linux 2011 on 2011-04-02
Thanks, that worked.

Now how do I actually *run* the file?  Lol, sorry, I'm new to this.

---

### Post by Vaphell on 2011-04-02
i admit, i forgot to mention that obvious 2nd step
```
./cube
```

---

### Post by Learning Linux 2011 on 2011-04-02
Thank you :D

---

