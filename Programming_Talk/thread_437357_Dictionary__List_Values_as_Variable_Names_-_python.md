---
title: "Dictionary / List Values as Variable Names - python"
date: 2007-05-08
forum: Programming Talk
---

### Post by FuriousLettuce on 2007-05-08
I've only just started learning python in the last day or so, and I'm trying to create a simple function (inside a class getID()) that grabs some of the details of the user. Currently, I've got
```

class getID:
        "Gets the details of users by standard input"

        def getDetails(self):
                self.items = {"DOB" : "", "nationality" : "", "race" : ""}
                for e in self.items:
                        self.items[e] = raw_input("What is your %s? " % e)

```

This works in that I can do:
```

x = getID()
x.getDetails()
print x.items["DOB"], x.items["nationality"], x.items["race"]

```
However, I'm trying to modify it so I don't need the items dictionary, so I can just reference x.DOB, x.nationality etc. I tried 
```

for e in items
      self.e = raw_input(...)

```
This only appears to create a variable self.e, rather than self.DOB etc. I imagine that I might have to do something with __init__? I realise I could use UserDict to define x["DOB"] etc, but it would be nicer to reference as x.DOB. Does anybody know of a way to do this, and does anybody know what the preferred method would usually be?

PS Might somebody explain to me when convention dictates that my methods should begin def __xyz(self) rather than just def xyz(self)?

---

### Post by slash2314 on 2007-05-08
```

class Person(object):
	def __init__(self,DOB="",nationality="",race=""):
		self.__items = {}
		self.__DOB = DOB
		self.__nationality = nationality
		self.__race = race
		self.__items['DOB'] = DOB
		self.__items['nationality'] = nationality
		self.__items['race'] = race
	def get_dob(self):
		return self.__DOB
	
	def get_nationality(self):
		return self.__nationality
	
	def get_race(self):
		return self.__race
	
	def get_details(self):
		return self.__items


if __name__ == '__main__':
	jake = Person("01/01/3005","Plutonian","Akerklop")
	jakeItems = jake.get_details()
	print jakeItems['DOB']
	print jakeItems['nationality']
	print jakeItems['race']

```

Here is one way to do it.  I don't have any set methods, but if you really want the object to return a dictionary you might want to do it this way.  That way you can keep the data entering part out of the Person class.  The double underscore before methods and names sort of make them private by name mangling or unable to be manipulated from outside of the class.

---

### Post by FuriousLettuce on 2007-05-08
Thanks for the reply! So the double underscore denotes a private method / private variable? Thanks again for the heads up!

---

### Post by WW on 2007-05-08
What you originally asked for can be done by using eval and compile:

**getID.py**
```

class getID:
    "Gets the details of users by standard input"

    def getDetails(self):
        self.items = {"DOB" : "", "nationality" : "", "race" : ""}
        for e in self.items:
            eval(compile('self.%s = raw_input("What is your %s? ")' % (e,e),'<string>','single'))


if __name__ == '__main__':

    x = getID()
    x.getDetails()

    print "DOB:         ", x.DOB
    print "nationality: ", x.nationality
    print "race:        ", x.race

```
Sample run:
```

$ python getID.py
What is your DOB? Still looking for one
What is your nationality? earthling
What is your race? 5K
DOB:          Still looking for one
nationality:  earthling
race:         5K
$

```

---

### Post by FuriousLettuce on 2007-05-08
Thanks a lot WW - that's exatly what I was looking for.

---

### Post by WW on 2007-05-08
You're welcome.  By the way, the fact that it *can* be done that way doesn't mean it *should* be done that way. I think the simpler approach is clearer:
```

class getID:
    "Gets the details of users by standard input"

    def getDetails(self):
        self.DOB = raw_input("What is you DOB? ")
        self.nationality = raw_input("What is your nationality? ")
        self.race = raw_input("What is your race? ")

```

---

### Post by duff on 2007-05-08
WW - that's a little overly complicated.  Every class has a __dict__ object that let's you get at its attributes (that's why "dir" works).

```
class getID:
    "Gets the details of users by standard input"

    def getDetails(self):
        self.items = {"DOB" : "", "nationality" : "", "race" : ""}
        for e in self.items:
            self.__dict__[e] = raw_input("What is your %s? " % e)


if __name__ == '__main__':

    x = getID()
    x.getDetails()

    print "DOB:         ", x.DOB
    print "nationality: ", x.nationality
    print "race:        ", x.race
```

---

### Post by WW on 2007-05-09
Thanks, duff, that's much nicer than my hack.

---

