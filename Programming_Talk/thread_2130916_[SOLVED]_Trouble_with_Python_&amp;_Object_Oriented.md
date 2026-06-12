---
title: "[SOLVED] Trouble with Python &amp; Object Oriented Concepts"
date: 2013-03-30
forum: Programming Talk
---

### Post by stuckne1 on 2013-03-30
So I'm trying to strengthen my object oriented skills at the same time I'm trying to learn python. I keep getting this error that I pasted at the very bottom. I have been struggling to figure out what the 2nd argument is and how to get rid of it.

Any ideas on what I'm doing wrong? Help greatly appreciated.

```

class Animal(object):
    ''' Non human, non plant thing '''
    def __init__(self, name=None, owner=None):
        self.name = name
        self.owner = owner
    
    def make_noise(self):
        print("null")
    
    def set_name(self, name):
        self.name = name
    
    def get_name(self):
        return self.name
    
    def set_owner(self, owner):
        self.owner = owner
        
    def get_owner(self):
        return self.owner
    
    #properties
    name = property(set_name, get_name)
    owner = property(set_owner, get_owner)
    
class Cat(Animal):
    ''' light weight furry creature '''
    def __init__(self, name=None, owner=None):
        super(Cat, self).__init__(name, owner)
        
    def make_noise(self):
        print("meow meow")

if __name__ == "__main__":
    print("beginning program...\n")
    
    newCat = Cat("johnny boy", "Sara")
    print("The cat's name is: " + newCat.name)
    print("The cat's owner is: " + newCat.owner)
    newCat.make_noise()

        

```

**_Output: _**
beginning program...


Traceback (most recent call last):
  File "systemPath/PythonOOB/src/animal.py", line 53, in <module>
    newCat = Cat("johnny boy", "Sara")
  File "systemPath/PythonOOB/src/animal.py", line 29, in __init__
    super(Cat, self).__init__(name, owner)
  File "systemPath/PythonOOB/src/animal.py", line 4, in __init__
    self.name = name
TypeError: get_name() takes exactly 1 argument (2 given)

---

### Post by stuckne1 on 2013-03-30
Instance variables were the same as the property. 

Solution...

Change Animal class to this...

```

class Animal(object):
    ''' Non human, non plant thing '''
    def __init__(self, name=None, owner=None):
[B][I]        self._name = name
        self._owner = owner[/I][/B]
    
    def make_noise(self):
        print("null")
    
    def set_name(self, name):
        **self._name = name**
    
    def get_name(self):
      **  return self._name**
    
    def set_owner(self, owner):
      **  self._owner = owner**
        
    def get_owner(self):
        **return self._owner**
    
    #properties
    name = property(get_name, set_name)
    owner = property(get_owner, set_owner)

```

---

