---
title: "[SOLVED] [Python] List of Choices, Removing if chosen"
date: 2008-08-08
forum: Programming Talk
---

### Post by TreeFinger on 2008-08-08
I have a class where the user will select a choice from a list. When the first user is created I would like to remove the choice of this user from the list for the second user. So if the list is [1, 2, 3] and user1 selects 2 the options for user2 should only be [1, 3].

How would I go about doing this? From java/c++ background I thought static variable but there is no such thing in python!

--edit

hmm I am thinking of making another object for the choices. that may solve my problem.

---

### Post by ghostdog74 on 2008-08-08
any of the array methods like index() ,pop() or remove() can be used. Look up the Python docs please.

---

### Post by TreeFinger on 2008-08-08
> **ghostdog74 said:**
> any of the array methods like index() ,pop() or remove() can be used. Look up the Python docs please.

I know how to remove an item from a list.

If I create another instance of the class the list is also re-created, containing a value I don't want to show up.

---

### Post by Lster on 2008-08-08
Do you mean something like:

[PHP]
options = set(a for a in xrange(1, 5+1))

class User:
	def __init__(this, option):
		this.option = option
		options.remove(option)


print options

User(2)
User(5)

print options
[/PHP]

---

### Post by ghostdog74 on 2008-08-08
you should show how your class look like, and how you invoke it and what you expect to see/get

---

### Post by MaxIBoy on 2008-08-08
Maybe you should create another list which just stores which items the class should create and which it shouldn't?

So if it shouldn't create user 2, this list would look like this:

[True, False, True]



The section of code that creates this menu should have access to this list, and use it when printing the menu.

---

### Post by Bachstelze on 2008-08-08
You could store the list as an atribute of your user class itself (as opposed to having one for each instance of it).

[PHP]#!/usr/bin/env python

class User:

    __choices = ["1", "2", "3", "4"]

    def __init__(self, name="") :
        self.__name = name

    def makeChoice(self) :
        print "Welcome %s!" % self.__name
        print "Your choices are %s. Which one do you wish to remove? " % self.__choices
        self.__choices.remove(raw_input())



Alice = User("Alice")
Barbara = User("Barbara")
Claire = User("Claire")
Alice.makeChoice()
Barbara.makeChoice()
Claire.makeChoice()

[/PHP]

This is obviously very dumb, as it does not check the validity of the input text, but you get the idea.

*EDIT: Obviously, Lster's solution of referencing the choices list outside the class would also work. However, referencing it inside the class allows you for example to make it private, so it can only be accessed from inside the class, and also avoids polluting your base namespace.*

---

### Post by TreeFinger on 2008-08-08
> **HymnToLife said:**
> You could store the list as an atribute of your user class itself (as opposed to having one for each instance of it).

```
#!/usr/bin/env python

class User:

    choices = ["1", "2", "3", "4"]

    def __init__(self, name="") :
        self.__name = name

    def makeChoice(self) :
        print "Welcome %s!" % self.__name
        print "Your choices are %s. Which one do you wish to remove? " % User.choices
        User.choices.remove(raw_input())



Alice = User("Alice")
Barbara = User("Barbara")
Claire = User("Claire")
Alice.makeChoice()
Barbara.makeChoice()
Claire.makeChoice()

```

This is obviously very dumb, as it does not check the validity of the input text, but you get the idea.

Thank you

---

