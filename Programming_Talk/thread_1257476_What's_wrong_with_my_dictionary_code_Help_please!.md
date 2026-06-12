---
title: "What's wrong with my dictionary code? Help please!"
date: 2009-09-03
forum: Programming Talk
---

### Post by Ally89 on 2009-09-03
Okay so I'm just beginning!
 
I'm given this file which contains the following:
 
toy201, Racing Car, AB239:2,DC202:2,FR277:2,JK201:1,YU201:1,EE201:1,FW201:1
toy101, Barbie Doll, AB139:2,DC102:2,FR177:2,JK101:1,YU101:1,EE101:1,FW101:1
toy301, Flying Kite, AB339:2,DC302:2,FR377:2,JK301:1,YU301:1,EE301:1,FW301:1
 
I am now to define a function that gives the following from the above file:
 
>>>load_prods(filename)
{'toy301': ('Flying Kite', [('AB339',2),('DC302',2),('FR377',2),('JK301),1),('YU301',1),('EE301',1),('FW301),1)])
 
.......(and the same for barbie doll and flying kite)........ }
 
 
So far I have:

[SIZE=2]def load_products(filename):[/SIZE]
[SIZE=2]filename = 'C:\Users\User\Desktop\cssetute\products.txt'[/SIZE]
[SIZE=2]f= open(filename, 'U')[/SIZE]
[SIZE=2]dictionary={}[/SIZE]
[SIZE=2]for line in f:[/SIZE]
[SIZE=2]list1 = line.strip().split(',')[/SIZE]
[SIZE=2]tuple_list=[][/SIZE]
[SIZE=2]for item in list1:[/SIZE]
[SIZE=2]line = line.rstrip()[/SIZE]
[SIZE=2]if ':' in item:[/SIZE]
[SIZE=2]text, num = item.split(":")[/SIZE]
[SIZE=2]tuple_list.append((text, int(num)))[/SIZE]
[SIZE=2]dictionary[list1[0]] = tuple_list[/SIZE]
[SIZE=2]f.close()[/SIZE]
[SIZE=2]return dictionary[/SIZE]

 
But when i load_prods('products.txt') it comes up with:
 
{'toy301': [(' AB339',2),('DC302',2),('FR377',2),('JK301),1),('YU301',1),('EE301',1),('FW301),1)]}
 
[SIZE=2]The name of the toy is missing and only one line comes up when I need the whole three toy lines to come up.[/SIZE]
[SIZE=2]Help thanks![/SIZE]

---

### Post by smartbei on 2009-09-04
Firstly, please post code in [code ] [/code ] tags (without the spaces). This makes it look nice and keeps indentation.

Secondly, This question is eerily similar to a similar question posted by stackee a day or two ago. That thread is still active, so you might want to take a look at it. [LINK]("http://ubuntuforums.org/showthread.php?t=1256718")

---

