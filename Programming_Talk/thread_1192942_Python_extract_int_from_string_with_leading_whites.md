---
title: "Python: extract int from string with leading whitespace"
date: 2009-06-20
forum: Programming Talk
---

### Post by mbeach on 2009-06-20
Hi,

Toying with python, and have come across something that doesn't seem to work as I thought it would.

Basically I have a file with a list of part numbers and qty's. The part number can repeat, so I've created a dictionary which uses the part number (which is alphanumeric) as the key, and the sum of qty as the value.

right now I have (which fails):
```
if line[23:30] not in self.items:
  self.items[line[23:30]] = int(line[7:10].strip())
else:
  self.items[line[23:30]] += int(line[7:10].strip())
```

The problem is the qty column is fixed width of 3, right justified, so occasionally has two leading spaces before the single digit. As a result I get an error like 
```

    self.items[line[23:30]] = int(line[7:10].strip())
ValueError: invalid literal for int() with base 10: ''
```

Without the strip() function I get the same error. I'm new to python, so was wondering if there is something simple I'm missing. 

As an aside, I'm pulling several bits of data out of a file hard coding these slice indexes all over the place - anyone have a much cleaner solution for that?

---

### Post by unutbu on 2009-06-20
```
    self.items[line[23:30]] = int(line[7:10].strip())
ValueError: invalid literal for int() with base 10: ''
```

The error is saying that line[7:10].strip() is an empty string.
So there must be a line where line[7:10] contains no number at all.

Perhaps if the data file is in space-separated columns, it would be better to use
the split() function:
[PHP]
For line in file_handle:
    row=line.split()
    quantity=row[0]
    part_number=row[1][/PHP]

If that doesn't work, please post a sample of the data file.

---

### Post by mbeach on 2009-06-20
yes, yes I see.

the file has a bunch of header information, then once I find a line with the column headers I start processing the lines. I thought I had a check for blank lines, but perhaps it is not working quite right.

The data file looks like:
```


SOME SUPPLIER NAME                        SHIP TO:
                                             SOME OTHER COMPANY TO SHIP TO
ACME ABC WAREHOUSE                           1234 SOME AVENUE
SOME CITY, SOME PROVINCE                     CITY, PROVINCE
A1A 1B1                                      B2B 1B2

Phone  (800) 123-4567                 
Fax    (800) 987-6543                 

PURCHASE ORDER 006463

CREATED 19062009 BY MBG

 ORDER QTY   REC QTY T YOUR PART NUMBER     DESCRIPTION                    COST

         2 _________ 0 ghjk128              TYLENOL COLD DM JR              5.23
         1 _________ 0 iujk200              JAM VIT D 1000 IU               3.88
         2 _________ 0 wsde426              REACH ANTIB T/BRUSH             1.13
         1 _________ 0 ghcv509              OS RED ZONE BODY SPR            3.93
         2 _________ 0 agpy111              CARMEX L/BALM MED BL            1.67

                                                TOTAL                      15.84


PURCHASE ORDER 006463

SUPPLIER


```

The code snippet I was using thus far (be easy - first python program for an actual purpose)
```

itemcount = 0
moreitems = 1

for line in self.sourcefile:
  #here we want to get to the line that starts with PURCHASE ORDER
  #and get the number that follows.
  if (not self.ponum) and (line[:14] == "PURCHASE ORDER"):
    self.ponum = line[15:21]
  #keep reading until get to ORDER QTY
  if line[1:10] == "ORDER QTY":
    itemcount = 1
  elif itemcount > 0:
    if line[45:53] == "   TOTAL":
      moreitems = 0
    if moreitems and line != "":
      #print line
      if line[23:30] not in self.items:
        #self.items[line[23:30]] = int(line[7:10].strip())
        self.items[line[23:30]] = line[7:10].strip()
      else:
        self.items[line[23:30]] += line[7:10].strip()

```
I'll continue on making sure I actually am skipping the blank lines.

Thanks for the quick response.

---

### Post by mbeach on 2009-06-20
whew, forum is back up.
I had a problem with the line checking to see if I was on a blank line.

I've replaced it with:
 if moreitems and line.strip() != "":

thanks for your help.

---

### Post by unutbu on 2009-06-20
It is probably better not to hard code a lot of column numbers.
It makes the program brittle.

Here is some food for thought:
[PHP]#!/usr/bin/env python
sourcefile=open('input','r')
itemcount=False
for line in sourcefile:
    line=line.strip()
    if line.startswith('PURCHASE ORDER'):
        ponum=line.split()[-1]
    elif line.startswith('ORDER QTY'):
        itemcount=True
    elif itemcount:
        if line.startswith('TOTAL'):
            break
        if line:
            data=line.split()
            part_number=data[3]
            order_quantity=data[0]
            print('%s of %s'%(order_quantity,part_number))
[/PHP]

---

### Post by Can+~ on 2009-06-21
> **unutbu said:**
> It is probably better not to hard code a lot of column numbers.
It makes the program brittle.

Here is some food for thought:
[PHP]#!/usr/bin/env python
sourcefile=open('input','r')
itemcount=False
for line in sourcefile:
    line=line.strip()
    if line.startswith('PURCHASE ORDER'):
        ponum=line.split()[-1]
    elif line.startswith('ORDER QTY'):
        itemcount=True
    elif itemcount:
        if line.startswith('TOTAL'):
            break
        if line:
            data=line.split()
            part_number=data[3]
            order_quantity=data[0]
            print('%s of %s'%(order_quantity,part_number))
[/PHP]

I was thinking the exact same thing, split by lines, then index.

I guess the Description is [4:-2] and the last number [-1].

---

### Post by mbeach on 2009-06-21
yes, I was thinking there must be a better way. I had thought about having some structure which contained the start and end column positions and use that somehow. I was aiming for something even more generic, but this is the first step.

I'd like to be able to define a set of rules where the generic elements are, then parse the file following those rules. The rules would somehow state the nickname for the piece of information being sought, the identifier for the correct line ( for example startswith('PURCHASE ORDER') or something like the ship to address which is known to be exactly on line 4, starting at column x to the next comma). I know this would make for a complicated rule set, but thought it might be a nice little project to work on. I've got loads of use for it. Ideally, I'd also like to be able to get all the info on a single pass through the file.

I really do like the simplicity of the split though - makes for much cleaner code, and for now, on this one off implementation, I'm going to use it. I think I decided against using split originally because the product descriptions will all have spaces and I thought that those would cause me issues. I see with your example, since the descriptions come after the part number and qty's, it is irrelevant how many spaces are in the descriptions. With the negative positions and slices, being able to grab the description is icing. Thanks for pointing that out Can+~.

Thanks for your assistance, I'll do some rewriting now and continue.

I do have a sideline question in response to
[PHP]print('%s of %s'%(order_quantity,part_number)) [/PHP]
I've been reading the python docs and wondering if since I'm just getting started with this language, do I go straight to 
[PHP]print('{0} of {1}').format(order_quantity,part_number)[/PHP]

ref: 
[http://docs.python.org/library/string.html#new-string-formatting](http://docs.python.org/library/string.html#new-string-formatting)
[http://www.python.org/dev/peps/pep-3101/](http://www.python.org/dev/peps/pep-3101/)

and a sideline to that question (as I hi-jack my own thread), is there a cleaner way to write:
[PHP]
edi["subject"] = "S{0:30}{1:30}{2:20},{3:2}{4:67}{5:6}{6:9}{7:1}".format(company_name,
                                                                          company_address,
                                                                          company_city,
                                                                          company_prov," ",
                                                                          company_postal," ",
                                                                          company_backorder)
[/PHP]
ignoring the fact that these company_ variables could be done a different way. I've always like to not have a line go so wide if possible (just a personal coding preference).

What I'm doing here is taking one file that a legacy system kicks out, grabbing all the bits I need, and sending it on to a vender in a format they accept electronically. I figure I'll mention that in case someone knows of a utility that does just that. I enjoy the exercise though - good way to get into the language.

---

### Post by Greyed on 2009-06-21
YES!  Yes, my moment has arrived!  I can now impart the knowledge [gained and so trumpeted when it was useless for me to do it]("http://greydmiyu.wordpress.com/2008/12/11/not-so-clever-construct/").  But your case is the perfect place to use it...

```

>>> x = '   1'
>>> int(x)
1
>>> str(int(x))
'1'

```Done.  My life is now complete.  :D

(unless of course in the subsequent discussion you have pointed out you don't actually need it, I just read the first message and jumped in  *cough*)

---

### Post by mbeach on 2009-06-21
> **Greyed said:**
> YES!  Yes, my moment has arrived!
(unless of course in the subsequent discussion you have pointed out you don't actually need it, I just read the first message and jumped in  *cough*)

Funny stuff. Good Sunday morning laugh. It turned out that the problem was a blank line being used. So essentially I was getting:

```

>>> x = ''
>>> int(x)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: ''
>>> 

```

I had actually dug and found the same solution you suggest at
[http://code.activestate.com/recipes/303495/](http://code.activestate.com/recipes/303495/)
which I thought would solve all my problems. 

Appreciate the review and the humour - mb.

---

### Post by ghostdog74 on 2009-06-21
> **Greyed said:**
> 
```

>>> x = '   1'
>>> int(x)
1
>>> str(int(x))
'1'

```Done.  My life is now complete.  :D

well, i see no difference using strip() (unless i am missing something )
```

>>> x='    1'
>>> x.strip()
'1'


```

---

### Post by unutbu on 2009-06-21
mbeach, you are ahead of me in your Python 2.6 knowledge. 
I'm guessing by this:
[PHP]
print('{0} of {1}').format(order_quantity,part_number)  [/PHP]
you meant
[PHP]
print('{0} of {1}'.format(order_quantity,part_number)) [/PHP]
Other than that it looks fine, but I really don't know the new style for string formatting yet.


To prettify
[PHP]
edi["subject"] = ...  [/PHP]

you could do this:
[PHP]
edi["subject"] = (
    "S{0:30}{1:30}{2:20},{3:2}{4:67}{5:6}{6:9}{7:1}".format( company_name,
        company_address, company_city, company_prov," ", company_postal," ",
        company_backorder)) [/PHP] 
By enclosing the entire right-hand side in parenthesis, you are free to break up the expression on multiple lines.

Or you could use temporary variables:
[PHP]
args=(company_name, company_address, company_city, company_prov," ",
      company_postal," ", company_backorder)
edi["subject"] = "S{0:30}{1:30}{2:20},{3:2}{4:67}{5:6}{6:9}{7:1}".format(*args)[/PHP]

---

### Post by mbeach on 2009-06-21
Not sure I'm ahead of anything - just reading a lot, trying to make sure I'm following conventions/style guides etc from the get go. Getting vi to behave nicely etc in the midst of getting some actual work done.

You bring up an interesting point, which I cannot find much discussion about. Which is more correct as both seem to produce the same output:
[PHP]
print("hello {0:>30}").format("world")
print("hello {0:>30}".format("world"))
[/PHP]
or is it one of those 6 and 2x3 situations? I'm not a stickler for using the 'more correct', but more interested in where the 'gotcha' is going to burn me later.

Loving the args suggestion, but with all new info, forces one to read about *args and **args.....  I wasn't sure where it would be best to break the line with some \ characters, with the args listed out like that it makes it quite nice to deal with. Dang learning curves.

Thanks for your time and help.

---

### Post by Greyed on 2009-06-21
> **mbeach said:**
> Funny stuff. Good Sunday morning laugh. It turned out that the problem was a blank line being used. So essentially I was getting:

Nooooooo, it means my life is not complete any longer.  Ah well, that's what I get for not reading completely what is going on.

> Appreciate the review and the humour - mb.There is that.  :)


> **ghostdog74 said:**
> well, i see no difference using strip() (unless i am missing something )


Nah, I was missing something.  I glossed over the issue and just saw his question coupled with strip() not working.  So I knew from past experience that as long as you can int() something you can str() it and it will strip all non-integer data effectively.  You're correct in pointing out strip() works fine for spaces (regardless of my presumptions on this topic's first post).  However the original intent of that little trick was for leading zeroes.  It just works well for spaces, too, and I was just jumping the gun in suggesting it.

```

>>> x = '001'
>>> str(int(x))
'1'

```Chalk it up to my overenthusiasm and geek wow factor.  Kinda like knowing how to get a directory listing without using ls.  ;)

---

### Post by unutbu on 2009-06-21
For an explanation of *args and **args, see
[http://ubuntuforums.org/showpost.php?p=7327269&postcount=8](http://ubuntuforums.org/showpost.php?p=7327269&postcount=8)

---

