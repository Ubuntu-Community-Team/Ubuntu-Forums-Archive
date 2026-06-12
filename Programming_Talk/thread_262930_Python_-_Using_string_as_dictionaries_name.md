---
title: "Python - Using string as dictionaries name"
date: 2006-09-22
forum: Programming Talk
---

### Post by ironfistchamp on 2006-09-22
Hey all

Sorry another python question. As soon as these get annoying (assuming they haven't already) just tell me to shut up yeh? OK anyway I have a few data dictionaries (too many most likely I love them). I want to use a string to modify the data dictionary. Example:

```


#The data dictionaries

paul = {"height":"1.5 Metres", "Weight":"10 Stone", "Age": 52}
bob = {"height":"1.4 Metres", "Weight":"14 Stone", "Age": 44}

#The input
choice = raw_input("Who?")

#The loop using choice as the DD's name
for k, v in choice.iteritems()
   print k, v


```

Now I know this is wrong but I am wondering if there is a way to do this. If not I am going to have to rethink my whole idea. Can anyone shine some light on this? I just want to treat a string as the name of a DD.

Thanks

Ironfistchamp

---

### Post by maubp on 2006-09-22
#The data dictionaries

paul_dict = {"height":"1.5 Metres", "Weight":"10 Stone", "Age": 52}
bob_dict = {"height":"1.4 Metres", "Weight":"14 Stone", "Age": 44}

people_dict = {"paul" : paul_dict, "bob" : bob_dict}

#The input
choice = raw_input("Who?")

#The loop using choice as the DD's name
for k, v in people_dict[choice].iteritems() : print k, v

---

### Post by maubp on 2006-09-22
This would be a good point to learn how to write your own classes too.  For example,

class PersonalData :
[INDENT]def __init__(self, name, height, weight, age) :
[INDENT]self.name = name
self.height = height
self.weight = weight
self.age = age
[/INDENT]def __str__(self) :
[INDENT]return "%s, height %0.2f metres, %0.0f stone, %0.0f years" \
% (self.name, self.height, self.wieght, self.age)
[/INDENT][/INDENT]
test = PersonalData("Peter", 1.75, 13, 21)
print test

data = {"Peter" : PersonalData("Peter", 1.75, 13, 30),
        "Bob" : PersonalData("Bob", 1.5, 10, 52),
        "Paul" : PersonalData("Paul", 1.4, 14, 44)}

#The input
choice = raw_input("Who?")

print data[choice]

---

### Post by ironfistchamp on 2006-09-22
Awesome thanks. I didn't think of classes. I used them when writing this project in C++. Didn't think that you could use them in Python. Not sure why. Thanks very much I shall get right back to work.

Thanks again

Ironfistchamp

---

### Post by ironfistchamp on 2006-09-22
Gah I tried making a class and thats all good and actually works better for what I want to do but I am kind of running into the same problem. If someone could help with this I would be really happy.

```

#item module
class item:
    
    def __init__(self, itemname, itemtype, itemvalue):
	self.itemname=itemname        
        self.itemtype=itemtype
        self.itemvalue=itemvalue 
        
        
it_apple = item("Apple", "restorative", 20)

#inventory module
import cls
import miscfunc

def inventory(charinventory, charinventid):
    #characters inventory
    print "-----------"
    print "-INVENTORY-"
    print "-----------"
    print
    for k, v in charinventory.iteritems():
        print k, ".", v
    choice = input("Item ID: ")
    useitem(charinventory, choice)
    cls.clearscreen()    


def addtestitem(charinventory, charinventid, item):
    #add a test item to the inventory
    charinventory[charinventid] = item
   
def useitem(charinventory, choice):
    item = charinventory[choice]
    print item.name
    miscfunc.pauseingame()

```

Ok so the addtestitem function adds an item (from the class above) into a dictionary. The input then takes the ID number from the dictionary and passes it to useitem. I need useitem to extract the item from the dictionary so that I can use it. I just can't figure out how to do it. The above code is wrong as I have figured out. This is just getting a little compicated but I'm sure I will be able to do this with a little more help. Thanks for any you can give

Ironfistchamp

---

### Post by Wolki on 2006-09-22
> **ironfistchamp said:**
> 
    choice = input("Item ID: ")


You probably want to use raw_input(), or remember to type quotes everytime you enter something.

>     print item.name

And here you should get an attribute that actually exists - you called it item.itemname in the class definition, you must get item.itemname now.

Other than that it seems to work here, more or less.

---

