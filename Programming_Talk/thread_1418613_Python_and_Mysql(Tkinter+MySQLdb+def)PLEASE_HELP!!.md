---
title: "Python and Mysql(Tkinter+MySQLdb+def)PLEASE HELP!!!"
date: 2010-02-28
forum: Programming Talk
---

### Post by linux_mania on 2010-02-28
I want to make a programme for adding data in my my database(mysql).I did everything right and i can add,delete,change,get data using MySQLdb.
 My problem is when i want to add gui(Tkinter) i get error message.I googled and did everything to solve it but stucked.Please help me!!!!!

my code is:

[B]#-*- coding: utf-8 -*-
from Tkinter import *
import urunekle2
import MySQLdb


def Add():
        x1 = str(Entry.get(x))
        y1 = float(Entry.get(y))
        try:
            conn= MySQLdb.connect(host="localhost",
                                user="root",
                                passwd="Amelia83",
                                db="mydb")
            cursor=conn.cursor()
            cursor.execute("select curdate()")
      tar=cursor.fetchone()
            tar=str(tar[0])
            cursor.execute("""insert into urun
                            (adi,fiat,ek_tarih)
                             values
                            (%s, %s ,%s)""",(x1,y1 ,tar))  
    except  MySQLdb.Error, e:
      print "Error %d: %s" % (e.args[0],e.args[1])
            sys.exit(1) 

 

root = Tk()
 
x = Entry(root)
x.grid(row=0, column=0, columnspan=2)
 
y = Entry(root)
y.grid(row=0, column=2, columnspan=2)
 
text = Label(root, text="summa")
text.grid(row=1, column=0)
 
Button(root, text='add', command=Add).grid(row=2, column=0, columnspan=1)

 
root.mainloop()
[/B]
Error message i got in Terminal window is:

[I][B]Exception in Tkinter callback
Traceback (most recent call last):
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 1413, in __call__
    return self.func(*args)
  File "think.py", line 14, in Add
    db="mydb")
  File "/usr/lib/pymodules/python2.6/MySQLdb/__init__.py", line 81, in Connect
    return Connection(*args, **kwargs)
  File "/usr/lib/pymodules/python2.6/MySQLdb/connections.py", line 129, in __init__
    from converters import conversions
  File "/usr/lib/pymodules/python2.6/MySQLdb/converters.py", line 165, in <module>
    from decimal import Decimal
  File "/usr/lib/python2.6/decimal.py", line 3584, in <module>
    val = globals()[globalname]
KeyError: 'ROUND_CEiLiNG'
[/B][/I]


As i mentioned the code without Tkinter:

[B]#!/usr/bin/python
#-*- coding: utf-8 -*-
import sys
import MySQLdb
import time
import os
from Tkinter import *
os.system("clear")
def ekle(): 
     try:
             conn= MySQLdb.connect(host="localhost",
                                  user="root",
                                 passwd="Amelia83",
                                  db="mydb")
             cursor=conn.cursor()
             adi=raw_input("Ürün ad&#305;n&#305; giriniz  :")
             mon=input("Ürünün Fiat&#305;n&#305; giriniz :")
        cursor.execute("select curdate()")
             tar=cursor.fetchone()
             tar=str(tar[0])
             cursor.execute("""insert into urun
                                                          (adi,fiat,ek_tarih)
                                                           values
                                                          (%s, %s ,%s)""",(adi,mon ,tar))
         print "Data has been successfully added!!!"      
      except  MySQLdb.Error, e:
             print "Error %d: %s" % (e.args[0],e.args[1])
             sys.exit(1) 
ekle()
[/B]
works great.
Please help me.Why things go wrong.Thanks in advance to anyone who would contribute.

---

### Post by linux_mania on 2010-02-28
Note:I did indention in my code but i couldn't show it in thread.

---

