---
title: "logging serial data from scientific equipment"
date: 2009-10-11
forum: Programming Talk
---

### Post by jrsy85 on 2009-10-11
Hi All,

I am having some trouble getting data sent from a ABX MICROS 60 to a relevant application.

The data is sent over a null modem @ 9600 8n1
Here is the problem:

gtkterm can see the data eg:
```

00723
ÿ RESULT
p 21
q 09/10/09 13h30mn16s
u 0000000000000001
s 0001
v                               
t R
€ D
! 000.1 l
2 03.42 l
3 00053 l
4  .329 l
5 00096  
6 015.6 l
7 00162 l
8 023.8 h
@ 00012 l
A 013.8 h
# --.--  
% --.--  
' --.--  
" --.--  
$ --.--  
& --.--  
W              B11 BBB   1   
```


I would like to get this data into gnumeric or Openoffice but all i can do so far is save the raw data with gtkterm, open it up and copy the data over, not very efficient when this is a fast machine that speeds up cell counting.

Any help would be greatly appreciated, i really dont want to go back to windoze and use twedge.

thanks,
Joel

---

### Post by zippaplick on 2009-10-11
If you can handle a little python, try pyserial. It makes serial programming really easy. Then you could use python's csv module to generate something (a csv file)  gnumeric or openoffice can import.

---

