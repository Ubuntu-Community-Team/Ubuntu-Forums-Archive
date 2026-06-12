---
title: "C++ Casting Error"
date: 2011-02-09
forum: Programming Talk
---

### Post by weems on 2011-02-09
I am having an error when I run the statement l = (int)69 - locationY. It results in a warning converting from int to float error.[http://codepad.org/evcZHUwp]("http://codepad.org/evcZHUwp")

---

### Post by MadCow108 on 2011-02-09
the error says it: locationY is float and you want to subtract it from an integer.

you must either explicitly cast/ceil/floor/round the float to an integer
```

69 - (int)locationY
//or
69 - ceilf(locationY)
//etc

```

or convert the integer to a float:
```

(float)69 - locationY
//or
69.f - locationY
//or for double precision
69. - locationY

```

note the the latter will be converted to an int again in the assignment to l.

---

### Post by cgroza on 2011-02-09
Should not that be int(69)? Maybe I missed something?

---

### Post by weems on 2011-02-09
If I cast locationY as an int it causes an infinite loop printing only "|"

---

### Post by nvteighen on 2011-02-10
> **cgroza said:**
> Should not that be int(69)? Maybe I missed something?

The C casting syntax is (type)argument. C++ inherited that syntax but also added the "constructor" syntax that you mention.

> **weems said:**
> If I cast locationY as an int it causes an infinite loop printing only "|"

Please post some code. (Enclose it between [NOPARSE]```

```[/NOPARSE] tags!!)

---

