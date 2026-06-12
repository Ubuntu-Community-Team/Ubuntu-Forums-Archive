---
title: "[Free Pascal] document printing"
date: 2009-08-17
forum: Programming Talk
---

### Post by johnyjj2 on 2009-08-17
Hello!

I've got an application written in Turbo Pascal in early 90s. I need to migrate it into Free Pascal. Now it works properly with one exception - I cannot print graphs created by the application. In general my application contains two PAS files.

There are three functions/procedures in second file (cdf.pas):
```
{  function PrintCtrl(blad:integer):boolean;
```
and
```
{$IFDEF ColorPrinter}
  procedure WydrukEkranu; //procedure PrintTheScreen;
```
and
```
  procedure WydrukEkranu;
```
I guess this line (and many other with write and lst) are responsible for printing
```
  write(lst,'A',chr(8),'2');
```


 Where can I find informations how to rewrite this code in order to allow printing the graphs?
 Greetings!

---

