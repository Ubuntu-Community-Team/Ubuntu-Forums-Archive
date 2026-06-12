---
title: "math help?"
date: 2009-11-15
forum: Programming Talk
---

### Post by MikeVaughanG on 2009-11-15
I am trying to make a program that will convert a speed input by a user, into a percentage of the speed of light.  but the result of my math is always 0. Can anyone help me out?

 BTW, I am VERY NEW to python. :)

```

l = 186282

cs= raw_input("How fast Are You Traveling Right now?")

csi = int(cs)
light = int(l)

(result) = (csi/100)*light

print(result)

```

---

### Post by CptPicard on 2009-11-15
You're doing integer division. Meaning that x/y = 0 if x < y and both are ints. Use a float for input or the speed of light value.

---

### Post by H4F on 2009-11-15
and the speed which inputs the user should be pretty high otherwise you will get 0.0000..% comparable to light speed

---

### Post by Can+~ on 2009-11-15
In math you can use short variable names for convenience, but in programming you should use long names for readability:

[PHP]# Convention: It's a constant, and should be UPPERCASE
LIGHTSPEED = 186282

# You can do all operations in a row
userspeed = float(raw_input("How fast are you travelling? "))

# This is how you should calculate percentage
print(userspeed/LIGHTSPEED*100)[/PHP]

And why insist on using US units instead of the SI ones (299792458 meters/second)?

---

### Post by The Cog on 2009-11-15
Use whatever units you find convenient. 1.8 trillion furlongs per fortnight seems fine to me.

In python, integer arithmetic always produces an integer answer, so that 22/7 equals 3. Foating point arithmetic always yields a float. So for this problem, I suggest you convert the input to float rather than int.

---

