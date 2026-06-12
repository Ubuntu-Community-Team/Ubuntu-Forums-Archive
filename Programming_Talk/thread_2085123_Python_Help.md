---
title: "Python Help"
date: 2012-11-17
forum: Programming Talk
---

### Post by Elfo33 on 2012-11-17
I'm new to using classes in Python, really Python in general, and I'm not sure what I'm doing wrong with this. I'm hoping someone can easily tell me how to fix this.

```
class Cp:
	x = x/1000
	def O2(self, x):
		self.state = 30.03235 + 8.772972*x + (-3.988133*x**2) + (0.788313*x**3) - 0.741599/(x**2)
	def N2(self, x):
		self.state = 19.50583 + 19.88705*x + (-8.598535*x**2) + (1.369784*x**3) + 0.527601/(x**2)
print(Cp.O2(1500))
```

---

### Post by Erik1984 on 2012-11-17
> **Elfo33 said:**
> I'm new to using classes in Python, really Python in general, and I'm not sure what I'm doing wrong with this. I'm hoping someone can easily tell me how to fix this.

```
class Cp:
    x = x/1000
    def O2(self, x):
        self.state = 30.03235 + 8.772972*x + (-3.988133*x**2) + (0.788313*x**3) - 0.741599/(x**2)
    def N2(self, x):
        self.state = 19.50583 + 19.88705*x + (-8.598535*x**2) + (1.369784*x**3) + 0.527601/(x**2)
print(Cp.O2(1500))
```

You are calling the method on the class itself and not an instance of the class. Try

```
c = Cp()
print(c.O2(1500))
```

EDIT: I didn't look carefully enough, there are more problems: the functions O2 and N2 should return a value if you  want to print something.

---

### Post by Erik1984 on 2012-11-17
It should work this way:
```
Class Cp:
    def O2(self, x):
        self.state = 30.03235 + 8.772972*x + (-3.988133*x**2) + (0.788313*x**3) $
        return self.state
    def N2(self, x):
        self.state = 19.50583 + 19.88705*x + (-8.598535*x**2) + (1.369784*x**3) $
        return self.state

c = Cp()
print(c.O2(1500))
```You didn't use the x defined inside the class so I removed it. The line x = x/1000 also presented an error as x wasn't defined yet.

---

### Post by Elfo33 on 2012-11-17
> **Euroman said:**
> It should work this way:
```
Class Cp:
    def O2(self, x):
        self.state = 30.03235 + 8.772972*x + (-3.988133*x**2) + (0.788313*x**3) $
        return self.state
    def N2(self, x):
        self.state = 19.50583 + 19.88705*x + (-8.598535*x**2) + (1.369784*x**3) $
        return self.state

c = Cp()
print(c.O2(1500))
```You didn't use the x defined inside the class so I removed it. The line x = x/1000 also presented an error as x wasn't defined yet.

Thanks for looking at this for me. However, I need to incorporate the x/1000 somehow. The idea is that x is a temperature, and for this equation to work, the given temperature (in K) is divided by 1000. I have a bunch of different elements that I need to incorporate into enthalpy and entropy classes/functions as well, so the idea was that I could create something that would give me a value for h.O2(T) vs h.N2(T). Additionally, I'll be using s.O2(T) in an fsolve to find what the temperature is.

Is there a better way to structure this?

---

### Post by MadCow108 on 2012-11-17
you are probably better of requiring a units library if you are concerned that users put in the wrong unit.
e.g. [https://bitbucket.org/kiv/unum](https://bitbucket.org/kiv/unum)

---

### Post by oldos2er on 2012-11-17
Moved to Programming Talk.

---

### Post by Vaphell on 2012-11-17
what i don't get is what do you you need that class for? what i see is just a bunch of functions that could be standalone.

if you need to get that /1000 you could simply go with
```
def O2( _x ):
  x = _x/1000.0
  return 30.03235 + 8.772972*x + (-3.988133*x**2) + (0.788313*x**3)


print( O2(1500) ) 

```

---

### Post by ofnuts on 2012-11-17
> **Vaphell said:**
> what i don't get is what do you you need that class for? what i see is just a bunch of functions that could be standalone.
[/code]
My thoughts exactly. If you don't keep data in class instances then using a class isn't bringing you much. There are languages (like Java) where everything is a class and you can't have stand-alone functions, so you define them as "static" functions in some utility class, but with Python you don't need this.

---

