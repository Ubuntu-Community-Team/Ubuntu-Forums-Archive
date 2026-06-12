---
title: "How do I get My function to take in 2 instantiated class names?"
date: 2010-07-27
forum: Programming Talk
---

### Post by xaegis on 2010-07-27
I'm stuck and having trouble with getting my python function to take in the Agility Attribute of players1 and 2 and output them in a return.

```

def combatInititive(player1.Agility,player2.Agility):
	'''Function to set inititive'''
	if player1.Agility > player2.Agility:
		Fighter1 = player1, Fighter2 = player2
		return  Fighter1,Fighter2

```

I cant seem to make this work. Any Ideas on why?

Thanks,

-e

---

### Post by -grubby on 2010-07-27
Function arguments cannot have dots in them, because they denote namespaces and it makes no sense in a function argument. Are you trying to call the function without arguments (e.g., combatInitive()), and hoping that the argument will magically be passed to the function? It won't be.

From what I can see, you want the entire player instances.

Here's an example that should work:

```

def combatInitive(player1, player2):
    if player1.Agility > player2.Agility:
        return player1, player2

```

Calling it is as simple as...

```

player1 = Player() # Or however you define these
player2 = Player()  # instances; this is an example.

combatInitive(player1, player2)

```

I could give a bit more comprehensive advice if you were to share all your code; pretty please? Also, on a somewhat unrelated note, please follow Python [PEP 8](http://www.python.org/dev/peps/pep-0008/); it makes code a lot more readable.

---

### Post by Bachstelze on 2010-07-27
What you want is:

```
def combatInititive(player1, player2):
	'''Function to set inititive'''
	if player1.Agility > player2.Agility:
		Fighter1 = player1, Fighter2 = player2
		return  Fighter1,Fighter2
```

---

### Post by schauerlich on 2010-07-27
On the "def" line of a function definition, all you're doing it saying 1) what it will look like when your function is called (its name, how many arguments, etc) and 2) what the names of the arguments will be when you want to refer to them inside your function.

For example:
```
def myFunction(arg, another_arg):
```

What you're saying here is that you will make a function, called "myFunction," and it will have two arguments. Inside your function, you'll call the first argument "arg," and the second one "another_arg". You can't do something like:

```
def myFunction(arg.something, another_arg.something_else):
```

because you're trying to *do* something with your arguments, not just give them names. You can do whatever you want inside the function, though:

```
def myFunction(arg, another_arg):
    if arg.something == another_arg.something_else:
        print "You're right!"
        return True
    else:
        print "You're wrong!"
        return False
```

---

### Post by xaegis on 2010-07-27
Thank you all soo much for taking the time to look at this!

HUmm, well what would you suggest I do? I am attempting to to change the attack order of my characters based on numbers which are not static. My idea was to just swap containers for the characters in the Combat Function. So while if you go first as Fighter1 the first round(iteration) you could go second the next because if your number was lower then you would be in the Fighter2 slot.
Suggestions?

---

### Post by schauerlich on 2010-07-27
```

def combat(player1, player2):
    first_attacker, second_attacker = orderOfAttack(player1, player2)

    while is_battle_over() == False:
        first_attacker.attack(second_attacker)
        second_attacker.attack(first_attacker)
        first_attacker, second_attacker = orderOfAttack(first_attacker, second_attacker)

```

There are probably better ways of doing this, but, that should work.

---

### Post by xaegis on 2010-07-27
> **schauerlich said:**
> ```

def combat(player1, player2):
    first_attacker, second_attacker = orderOfAttack(player1, player2)

    while is_battle_over() == False:
        first_attacker.attack(second_attacker)
        second_attacker.attack(first_attacker)
        first_attacker, second_attacker = orderOfAttack(first_attacker, second_attacker)

```

There are probably better ways of doing this, but, that should work.

Thank you! I'll play around with that and see if I can get it to work. I dont quite understand what you are doing. Are you assigning (first_attacker,second_attacker) into second_attacker... I really don't understand the logic of what you are doing. Would you mind an explanation?

Thanks,

-e:)

---

### Post by schauerlich on 2010-07-27
Your function returns two thing, Fighter1 and Fighter2. It returns it as a "tuple", which is basically just a list that you can't change. You can either stick that tuple in a variable, and access individual elements just like you would a list, or "unpack" the tuple during assignment. This means you take out each element of the tuple and give it its own name, all at once. To unpack a tuple, you give as many variable names as there are elements in the tuple separated by commas before the equals sign. It's hard to explain, I'll give an example:

```
>>> def return_a_b():
...     return "a", "b" #this is where you create your tuple
... 
>>> foo = return_a_b() # assign the tuple to "foo"
>>> print foo[0]
a
>>> print foo[1]
b
>>> bar, baz = return_a_b() # unpack the tuple into "bar" and "baz"
>>> print bar
a
>>> print baz
b
```

more information [here](http://docs.python.org/tutorial/datastructures.html#tuples-and-sequences)

---

### Post by xaegis on 2010-07-27
> **schauerlich said:**
> Your function returns two thing, Fighter1 and Fighter2. It returns it as a "tuple", which is basically just a list that you can't change. You can either stick that tuple in a variable, and access individual elements just like you would a list, or "unpack" the tuple during assignment. This means you take out each element of the tuple and give it its own name, all at once. To unpack a tuple, you give as many variable names as there are elements in the tuple separated by commas before the equals sign. It's hard to explain, I'll give an example:

```
>>> def return_a_b():
...     return "a", "b" #this is where you create your tuple
... 
>>> foo = return_a_b() # assign the tuple to "foo"
>>> print foo[0]
a
>>> print foo[1]
b
>>> bar, baz = return_a_b() # unpack the tuple into "bar" and "baz"
>>> print bar
a
>>> print baz
b
```

more information [here](http://docs.python.org/tutorial/datastructures.html#tuples-and-sequences)

Awesome! Thank you I got it!


:D

---

