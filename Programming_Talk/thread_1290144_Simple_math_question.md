---
title: "Simple math question"
date: 2009-10-13
forum: Programming Talk
---

### Post by froggyswamp on 2009-10-13
Folks can anyone please show the steps how to determine x here?

x + (x*30)/100 = 117

---

### Post by cb951303 on 2009-10-13
first add the terms on the left:
130x/100 = 117

then pass the 100 to the right side:
130x = 11700

finally, pass the 130 to the right side
x = 11700/130 = 90

---

### Post by dominiquec on 2009-10-13
x + (x*30)/100 = 117 

(x*30)/100 = 117 - x

x*30 = (117 - x) * 100

x*30 = 11700 - x*100

x * 130 = 11700

x = 11700 / 130

x = 90

---

### Post by froggyswamp on 2009-10-13
Thank you very much both of you!! I know programming but no math, I'd like to learn some simple math but dunno where to start.

EDIT: here's the translation into Java:

```

public static void main(String[] args) {
	//RESOLVE: x+(x*30)/100 = 3.04
	System.out.println(resolve(30, 3.04f));
}

private static float resolve(int iPercents, float fRightNumber) {
	fRightNumber *= 100;
	iPercents += 100;
	float x = fRightNumber/iPercents;
	return x;
}

```

---

### Post by Can+~ on 2009-10-13
> **dominiquec said:**
> x + (x*30)/100 = 117 
(x*30)/100 = 117 - x
x*30 = (117 - x) * 100
x*30 = 11700 - x*100
x * 130 = 11700
x = 11700 / 130
x = 90

Factorization is far easier:

x + (x*30)/100 = 117

x(1 + 30/100) = 117

x(130/100) = 117

x = 117*100/130

---

### Post by Arndt on 2009-10-14
> **Can+~ said:**
> "Computer Science is no more about computers than astronomy is about telescopes." (Dijsktra)



It's Dijkstra, actually.

---

