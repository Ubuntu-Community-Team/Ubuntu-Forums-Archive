---
title: "C++ not computing equation"
date: 2011-04-27
forum: Programming Talk
---

### Post by jordanae on 2011-04-27
In my code I have an equation that will only result in a zero no matter what I put in. 
```

int pyVol() {
	int basef, heightf;
	cout << "Base in feet: ";
	cin >> basef;
	cout << "Height in feet: ";
	cin >> heightf;
	cout << "Volume of pyramid: " << 1/3*basef*heightf << " cubic feet" << endl;
	}

```
Any ideas? I'm assuming it's pretty obvious so I have a feeling I'm gonna look like an idiot :P
And also, if I were to declare basef and heightf as floats instead of ints would the user have to add a decimal space if the number is whole? Or would C++ just add a .0?

---

### Post by mdurham on 2011-04-28
I guess 1/3 always == 0

---

### Post by jordanae on 2011-04-28
Thanks! All I had to do was make basef and heightf float points and add a .0 to the one and the three because C++ apparently likes to be difficult with decimals :P

---

### Post by BkkBonanza on 2011-04-28
If you want to use int for calculations always do the multiplies before the divides as otherwise when fractional intermediate values being truncated will spoil the result. In your case it makes more sense to use double but there are cases where int is suitable with correct ordering of terms.

You needed the decimal points to tell the compiler the values were "double or float" not "int" but if you placed the /3 after the variables (which gives same result, and 1 is not needed at all), then you don't need the decimals since the variables are already known to be float. The compiler won't guess about "types" - it has to be told explicitly or implicitly via surrounding variables.

---

### Post by jordanae on 2011-04-28
> **BkkBonanza said:**
> If you want to use int for calculations always do the multiplies before the divides as otherwise when fractional intermediate values being truncated will spoil the result. In your case it makes more sense to use double but there are cases where int is suitable with correct ordering of terms.

You needed the decimal points to tell the compiler the values were "double or float" not "int" but if you placed the /3 after the variables (which gives same result, and 1 is not needed at all), then you don't need the decimals since the variables are already known to be float. The compiler won't guess about "types" - it has to be told explicitly or implicitly via surrounding variables.

Thanks, that cleared up a lot

---

### Post by BkkBonanza on 2011-04-28
Note also that the correct volume of pyramid would have basef twice, eg.

basef*basef*heightf/3

For a square base of width and length of basef.

---

