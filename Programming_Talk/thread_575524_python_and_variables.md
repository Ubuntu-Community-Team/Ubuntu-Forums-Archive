---
title: "python and variables"
date: 2007-10-14
forum: Programming Talk
---

### Post by Hairy_Palms on 2007-10-14
hi, im trying to get my head around why this doesnt work in python

```
globtoggle = 1
def clear(widget, treeView):
	toggle = globtoggle
	if (toggle == 1):
		globtoggle = 0
	else:
		globtoggle = 1
```

it gives me an error about
> UnboundLocalError: local variable 'globtoggle' referenced before assignment

but i cant figure it out. please help me! ty

---

### Post by Malibu Illusion on 2007-10-14
You have to specify the variable scope at the start of the function as global:

```
def clear(widget, treeView):
	global globtoggle
	globtoggle = 1

	toggle = globtoggle
	if (toggle == 1):
		globtoggle = 0
	else:
		globtoggle = 1
```

If you do not specify it as global, then it will treat the variable as local and also any changes that you make to it will be local scope.  For instance, if we had something like this under it:

```
def test():	
	globtoggle = 4
	print globtoggle
```

It would print the value 4.  However this would only be treated as local scope; the global variable "globtoggle" would not be updated.  For example:

```
def globdemo():
	print globtoggle
```

After executing "test", globdemo would return the value of the global variable you're looking to use.  It wouldn't be 4, it'd be 1 or 0 depending on the evaluation in "clear".

To create or update something in a global scope, it has to be specified as global before you change it:

```
def test2():
	global globtoggle	
	globtoggle = 4
```

That function would mean the global variable would be equal to 4 across every function upon which it is called, which is what you want.

Hope I've not confused you further.

Take care.

---

### Post by Quikee on 2007-10-14
> **Hairy_Palms said:**
> hi, im trying to get my head around why this doesnt work in python

```
globtoggle = 1
def clear(widget, treeView):
	toggle = globtoggle
	if (toggle == 1):
		globtoggle = 0
	else:
		globtoggle = 1
```

it gives me an error about


but i cant figure it out. please help me! ty

Because you have to declare that you want to access a global variable inside a function (to remind you coding like this is discuraging). 

```

globtoggle = 1
def clear(widget, treeView):
	global globtoggle
	toggle = globtoggle
	if (toggle == 1):
		globtoggle = 0
	else:
		globtoggle = 1

```

---

### Post by Hairy_Palms on 2007-10-14
```
def clear(widget, treeView):
	global toggle
        toggle = 1
	if (toggle == 1):
		toggle = 0
	else:
		toggle = 1
```

k ive got to this, but that means it will neveer execute the else commands, i want the variable to be set to one the first time it runs but to adopt the inverse from thereon, forcing it to 1 every time defats the loops purpose.

i cant intialise toggle outside the method because it doesnt exist yet and if i set it inside its always the same.

---

### Post by Malibu Illusion on 2007-10-14
```
global toggle
toggle = 1

def clear(widget, treeView):
	global toggle

	if (toggle == 1):
		toggle = 0
	else:
		toggle = 1
```

Something like that?

---

### Post by aks44 on 2007-10-14
Am I the only one to think that if you need a global variable then you've got a Design Problem(tm)?

---

### Post by Malibu Illusion on 2007-10-14
No, you're not.  But in this topic he's asking about how to use global variables and I'm merely answering that question.

If he wishes to use them that's entirely his own prerogative.

---

### Post by aks44 on 2007-10-14
> **Malibu Illusion said:**
> If he wishes to use them that's entirely his own prerogative.

And I can't help but thinking that someone who isn't even aware of how to use such a basic feature may well benefit from being hinted that what (s)he's trying to do is plain Evil. ;)


If the OP told us his/her real goal (not just what (s)he thinks (s)he needs to do, but what (s)he wants to do in the end) we could for sure suggest a better solution.

---

### Post by Hairy_Palms on 2007-10-14
ah thanks malibu thats exactly what i wanted :) 
whats bad about global variables aks44?

EDIT btw there was no end goal, it was more just an exercise in learning how to do things i can currently do in Basic in python.

---

### Post by ankursethi on 2007-10-14
Well, they clutter the entire namespace, for one. Also, accidentally changing them in just *one* function will mean that the same changes are reflected in *all* functions. This could lead to a potential disaster if you accidentally change the global's value and then forget about it.

It really becomes hard to keep track of the values of global variables in large programs. It might not matter much in small programs/scripts.

---

### Post by aks44 on 2007-10-14
Oh well, as long as this is just a coding exercise, that's not a problem then. ;)


To add to what ankursethi already said, global variables make your design unflexible.

Back to your example, how are you gonna do if you want to toggle another variable? What about if you need to be able to toggle a hundred different variables? Are you gonna write a hundred different functions, each handling a different global variable?

Good design practices include factorizing common code as much as possible, making it flexible enough to be reused, and easily maintenable. Global variables just forbid such factorization.


FWIW your "toggle" function should take the variable you want to toggle as an argument by reference, so that it doesn't depend on anything outside of it. This way it even adds more functionnality, as you'll be able to toggle any global or any local variable you want. Granted, as far as your coding exercise goes it is not a tremendous gain, but you better learn proper programming practices sooner rather than later... ;)

I don't know Python's syntax so unfortunately I can't show the relevant code, but maybe someone can?

---

### Post by Hairy_Palms on 2007-10-14
well to be fair i rarely use global variables in my other Programming, i usually only use them for file locations, id assume the  right way to do it, if i wass say referancing it from a button is to simply change a local variable under the button.clicked event (orwhatever its called in python) every time the buttons pressed then just call the clear method from that?

---

### Post by gnuman on 2007-10-14
> **Malibu Illusion said:**
> No, you're not.  But in this topic he's asking about how to use global variables and I'm merely answering that question.

If he wishes to use them that's entirely his own prerogative.

And it brings up an educational opportunity to show why global variables are avoided, which I see happened already in this thread.

I'm not good at generators, as I'm still learning, but couldn't someone show how a **[[COLOR="Blue"]yield statement [/COLOR]]("http://docs.python.org/ref/yield.html")**would be the pythonic way to do this without global variables?  Just curious.

---

### Post by pmasiar on 2007-10-14
Maybe better design is the object-oriented way: toggle is attribute of some object from your problem space. Instead of having it as global variable, add it to the object, including method of chaging it. So instead of dozens of global toggles (status flags), you have one: the "application" object, with app. status flags. It seems as little difference in small execrise, but big difference in real big project. HTH

---

### Post by cwaldbieser on 2007-10-15
> **gnuman said:**
> And it brings up an educational opportunity to show why global variables are avoided, which I see happened already in this thread.

I'm not good at generators, as I'm still learning, but couldn't someone show how a **[[COLOR="Blue"]yield statement [/COLOR]]("http://docs.python.org/ref/yield.html")**would be the pythonic way to do this without global variables?  Just curious.

```

def toggle():
    flag = True
    while True:
        yield flag
        flag = not flag

for t in zip(xrange(7), toggle()):
    print t

```

---

### Post by dwblas on 2007-10-16
I think you might want to learn classes next as they would simplify this and eliminate global variables```

class ToggleClass:
   def __init__(self):
      self.globtoggle = 1
      print "initial value =", self.globtoggle
   def clear(self):
      print "before value =", self.globtoggle
      if (self.globtoggle == 1):
		self.globtoggle = 0
      else:
		self.globtoggle = 2
      print "after value = ", self.globtoggle
#------------------------------------------------------------------------------
if __name__ == "__main__":
   TC = ToggleClass() ## initializes globtoggle as one and prints value
   get_key=raw_input( "variable initialized-->press any key " )
   TC.clear()
   TC.clear()
```

---

### Post by Wybiral on 2007-10-16
> **dwblas said:**
>  ... 

Oh no... You've mixed tabs and spaces!

---

### Post by dwblas on 2007-10-17
I copied the OP code.

---

