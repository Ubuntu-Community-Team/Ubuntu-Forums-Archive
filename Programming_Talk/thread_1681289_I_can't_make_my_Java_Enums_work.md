---
title: "I can't make my Java Enums work"
date: 2011-02-03
forum: Programming Talk
---

### Post by skytreader on 2011-02-03
First, are enums preferred over final variables? Or are they more of a case-to-case basis. I usually have a series of final variables (like for, say, defining a certain grammar) like:

```

private final char LINE_TERMINATOR = ';';
private final char ADD = '+';
...and so on

```

With that I looked into enums as they seem to be a neater way to do things.

So here's my try:

```

public class PrimeEncoding{
	Vector<Integer> primes;
	
	private enum EncodingSymbol{
		IDENTITY('i'),
		USED_INDICATOR('|'),
		SKIPPED_INDICATOR('-'),
		USED_OPENER('['),
		USED_CLOSER(']'),
		SKIPPED_OPENER('{'),
		SKIPPED_CLOSER('}');
		
		private final char symbol;
		
		EncodingSymbol(char symbol){
			this.symbol = symbol;
		}
	}

        public String encode(int n) throws Exception{
		if(n >= HighBound){
			throw new Exception("encode: Number passed for encoding is greater than the specified upper bound.");
			System.exit(-1);
		} else{
			String encoding = "" + IDENTITY; // IT RAISES AN ERROR HERE!
			return encoding;
		}
	}

```

It tells me that IDENTITY is undefined. How do I make this work?

---

### Post by Some Penguin on 2011-02-03
```

EncodingSymbol.IDENTITY

```

*shrug* I'd say that using enums makes sense if they're logically the same type -- e.g. if something can be one of X different values.

---

### Post by V for Vincent on 2011-02-04
Enums in Java are great. There's an official tutorial which explains them really well.

To get this to compile, you need to add the Enum type, i.e. EncodingSymbol.IDENTITY. I doubt you'll get the result you were expecting, however. At least, I get the impression you want to append an 'i' to "". The toString() method won't give you back 'i', but EncodingSymbol.IDENTITY. You could override the Enum's toString() method to return that character as a String.

Enums are really useful if you want just a limited number of objects of a particular type. They're typesafe and every instance can even override instance methods. But I think they're not worth the boilerplate here - you could get by with constants.

---

### Post by forrestcupp on 2011-02-04
I think the line that throws an error should be
```
String encoding = "" + IDENTITY.symbol;

```

---

