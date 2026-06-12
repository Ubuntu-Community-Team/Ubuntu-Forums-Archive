---
title: "scanf with enumerated types"
date: 2010-12-05
forum: Programming Talk
---

### Post by laus_deo on 2010-12-05
I keep trying to compile this program, and while it does compile I get this warning 

```
 warning: format ‘%u’ expects type ‘unsigned int *’, but argument 2 has type ‘unsigned int’
```

Heres the code for where that occurs

```
 	while(s != OVER)
 	{
		makeNextGuess(&row, &column, s);
                printf("Row %d, Column %d\n", row, column);

		printf("What was that\n");
		scanf("%u", s);
		
	}	
}

```

with me trying to scan in a previously declared enumerated type. (s)

does anyone know what to put in place of the '%u'?

---

### Post by trent.josephsen on 2010-12-05
It's not the format specifier; it's the argument.  s is not a pointer.

That said, there may be issues with passing a pointer to enum X where a pointer to unsigned is expected; or maybe it's covered by one of the explicit provisions.  I don't know.

---

### Post by laus_deo on 2010-12-05
But if I made it a pointer, you can't scanf to a pointer can you? Is there anyway to scanf to an enum? or am I going to have to find a different way to do this?

---

### Post by trent.josephsen on 2010-12-05
You can't scanf *into* a pointer (at least, not with C89, and I don't think it was introduced in C99), but you must *pass* scanf a pointer in order to have it put a value into a variable.

The fact that it's an enumerated type has nothing to do with the error you're currently seeing.  This snippet exhibits the same problem:

```
int i;
scanf("%d", i);
```

(it actually took two tries to write this wrong; my fingers typed the correct version all by themselves the first time.)  man scanf if you're still unclear on it.

However, as I said before, there might not be any requirement that a pointer-to-enum be freely convertible to pointer-to-unsigned.  There could be alignment or any number of other things screwing you up.  I was hoping somebody could come along to enlighten us on this point, but it might end in a search through the Standard anyway.

---

### Post by worksofcraft on 2010-12-05
[php]
/* change it so: */
		scanf("%u", &s);
[/php]

scanf needs to **WRITE** to your variable "s". To do that, scanf needs the memory address that says where to write to. Conversely, printf only needs the value to write and doesn't care what address it came from. That is why there is no & on the values you pass to printf but there is on the ones you read with scanf.

---

### Post by Arndt on 2010-12-05
> **worksofcraft said:**
> [php]
/* change it so: */
		scanf("%u", &s);
[/php]

scanf needs to **WRITE** to your variable "s". To do that, scanf needs the memory address that says where to write to. Conversely, printf only needs the value to write and doesn't care what address it came from. That is why there is no & on the values you pass to printf but there is on the ones you read with scanf.

The title and what the OP writes makes me think that, once the typing and addressing problems are solved, he wants to input the name of an enum as a string, and receive the correct number in the variable. That cannot be done.

---

### Post by laus_deo on 2010-12-06
Yeah, that got rid of the warning... I feel pretty stupid, just left out the ampersand. >.<

---

