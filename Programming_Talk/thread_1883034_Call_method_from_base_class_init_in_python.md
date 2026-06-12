---
title: "Call method from base class init in python"
date: 2011-11-18
forum: Programming Talk
---

### Post by pelle.k on 2011-11-18
I'm all out of ideas here, and my google fu doesn't seem to be enough to crack this nut by myself, so here it is:
I have this class called **A**, it does some stuff in the **__init__**, and then calls function **morestuff()** from the init, to get the ball rolling. Now, i also have class **B** that inherits from **A**, which also does som stuff in it's **__init__**, and have method **morestuff()** that overrides the one in class A.

Now, here's the problem. On it's own, an instance of A does just fine. But an instance of B has this problem:
**B's __init__** calls **A's __init__** (well, with the help of super), **A's __init__** calls **morestuff()** which is effectively **B's morestuff()** since it's overridden there. But **B's morestuff()** is not ready to be run yet, since it's dependent on **B's __init__** to be run (or should i say finished, since **B's __init__** is running, it's just that it is executing **A's __init__** ATM so it's not finished) first!

Is this a common problem, with a common solution? Or is it just a broken design on my part? I do understand _why_ this isn't working, i just fail to see how to work around it effectively.
See, i want a method that can kick start the instance up and running _itself_, without doing it from the outside.
This would work
```
test = B()
test.morestuff()
```
since that would run **B's __init__**, **A's __init__** without running any methods just yet, and then run **B's morestuff()** that would also run **A's morestuff()**. Both init's ran before morestuff().
How do i achieve the same without having to run morestuff() separately from the instance object, like in the example, but from the init of the class itself?

---

### Post by crdlb on 2011-11-18
I would probably avoid this problem by keeping my base classes "abstract". So, the instantiatable derived classes would just call morestuff in their __init__.

---

### Post by ofnuts on 2011-11-18
> **pelle.k said:**
> I'm all out of ideas here, and my google fu doesn't seem to be enough to crack this nut by myself, so here it is:
I have this class called **A**, it does some stuff in the **__init__**, and then calls function **morestuff()** from the init, to get the ball rolling. Now, i also have class **B** that inherits from **A**, which also does som stuff in it's **__init__**, and have method **morestuff()** that overrides the one in class A.

Now, here's the problem. On it's own, an instance of A does just fine. But an instance of B has this problem:
**B's __init__** calls **A's __init__** (well, with the help of super), **A's __init__** calls **morestuff()** which is effectively **B's morestuff()** since it's overridden there. But **B's morestuff()** is not ready to be run yet, since it's dependent on **B's __init__** to be run (or should i say finished, since **B's __init__** is running, it's just that it is executing **A's __init__** ATM so it's not finished) first!

Is this a common problem, with a common solution? Or is it just a broken design on my part? I do understand _why_ this isn't working, i just fail to see how to work around it effectively.
See, i want a method that can kick start the instance up and running _itself_, without doing it from the outside.
This would work
```
test = B()
test.morestuff()
```since that would run **B's __init__**, **A's __init__** without running any methods just yet, and then run **B's morestuff()** that would also run **A's morestuff()**. Both init's ran before morestuff().
How do i achieve the same without having to run morestuff() separately from the instance object, like in the example, but from the init of the class itself?
In class B, define *B::morestuff()* to do nothing, and add a* B::evenmorestuff()* method called at the end of *B::__init__()*. *B::evenmorestuff()* can even call *A::moreStuff()*

---

### Post by simeon87 on 2011-11-19
> **ofnuts said:**
> In class B, define *B::morestuff()* to do nothing, and add a* B::evenmorestuff()* method called at the end of *B::__init__()*. *B::evenmorestuff()* can even call *A::moreStuff()*

That may not be an option, as morestuff() of B is intended to override morestuff() of A. Doing nothing may not be possible, depending on what A and B are and what morestuff() does.

---

### Post by pelle.k on 2011-11-19
Thanks for the replies. Now, the idea of morestuff is that it's a method that does stuff you might also do with the object  instance later on as well, such as adding items to a list. And so as to not duplicate that code in the init you want to call that method in the init, as well as to allow for a class that inherits this method, also to augment this action.
So, this method works nicely once all initialization is done (when you call it from the instance object), but not from the init (where i would like to use it as well).
Using an abstract class, and calling morestuff() from the classes that inherits from it solves the problem temporarily, but what about classes that inherit from those classes that call morestuff()? The problem remains, unless i misunderstood?
Please excuse any spelling or grammar mistakes, or bad wording, i'm posting this from my smartphone :)

---

### Post by nvteighen on 2011-11-19
I remember I had to sort out something like this in the past. This smells like a case of premature optimization...

I think the stuff at each morestuff() method could be placed at the __init__ itself, perhaps as a nested function. That'd solve the whole issue if that method is an auxiliary function only meant to be run when initializing some object.

If morestuff() is meant to be called in other contexts, then this might need some other solution.

---

### Post by pelle.k on 2011-11-19
> **nvteighen said:**
> I remember I had to sort out something like this in the past. This smells like a case of premature optimization...

I obsess over things like that, when i can't find a neater solution than the one at hand. As i said before, i already know how to active the same result, without introducing this side effect. You run morestuff()
```
test = B()
test.morestuff()
```
like this, from the object instance instead. it just bothers me you can't get the object initialized, and have it run it's own methods (like morestuff) from the __init__ without breaking inheritance really.

> **nvteighen said:**
> I think the stuff at each morestuff() method could be placed at the __init__ itself, perhaps as a nested function. That'd solve the whole issue if that method is an auxiliary function only meant to be run when initializing some object.

If morestuff() is meant to be called in other contexts, then this might need some other solution.
Indeed, i could just move the contents of morestuff to the init, but exactly as you point out in your last paragraph, this method is indeed meant to be run at other times than just during __init__, and i'm not very keen on code duplication like that.

**I better stop obsessing, and start producing some code, heh. Thanks for the help guys. Much appreciated, as always.**

---

### Post by ofnuts on 2011-11-19
> **simeon87 said:**
> That may not be an option, as morestuff() of B is intended to override morestuff() of A. Doing nothing may not be possible, depending on what A and B are and what morestuff() does.AS said above, It can be called, but later, in B::evenmorestuff() at the end of the B::__init__().

---

### Post by pelle.k on 2011-11-19
> **ofnuts said:**
> AS said above, It can be called, but later, in B::evenmorestuff() at the end of the B::__init__().

Hah! Quite clever, if perhaps a little messy :) Thanks for the tip!

```
class A(object):
	def __init__(self):
		super(A, self).__init__()
		self.a_arg = "a"
		self.a_morestuff()
		
	def a_morestuff(self):
		print self.a_arg # A
	
		
class B(A):
	def __init__(self):
		super(B, self).__init__()
		self.b_arg =  self.a_arg + "b"
		self.b_morestuff()
		
	def a_morestuff(self):
		pass
		
	def b_morestuff(self):
		# all inits should be finished executing now...
		print self.b_arg # AB
		# optional, just for fun :)
		super(B, self).a_morestuff()
		
		
class C(B):
	def __init__(self):
		super(C, self).__init__()
		self.c_arg = self.b_arg + "c"
		self.c_morestuff()
		
	def b_morestuff(self):
		pass
		
	def c_morestuff(self):
		# all inits should be finished executing now...
		print self.c_arg # ABC
		# optional, just for fun :)
		super(C, self).b_morestuff()
		
		
a = A()
print ""
b = B()
print ""
c = C()
```

returns
```
a

ab
a

abc
ab
a
```

---

