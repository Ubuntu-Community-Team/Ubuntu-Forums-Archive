---
title: "[JAVA] Splitting String, Regex"
date: 2008-09-20
forum: Programming Talk
---

### Post by dr.silly on 2008-09-20
Anyone have a good way to do this:

I need to split a string that looks something like this:

```
Text text text {1:more text} Some more text {2:hi} blah blah {$1} blah {$2} o and also {3} blah blah

```

into an array that ends up looking like this:


```
["Text text text ", "{1:more text}", " Some more text ", "{2:hi}", " blah blah ", "{$1}", " blah ", "{$2}", " o and also ", "{3}", " blah blah"]
```

---

### Post by CptPicard on 2008-09-20
Well, java.util.Scanner lets you tokenize by those spaces by default (and has other options)... you can just buffer your text tokens depending on what they are (either a {} block or just "other text" blocks) and reconstitute them back into larger tokens once a new block begins.

---

### Post by kavon89 on 2008-09-20
Check this out:

[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#split(java.lang.String)](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#split(java.lang.String))

---

### Post by Reiger on 2008-09-20
There are String methods which perform regular expression matching AFAIK; but one can alternatively use these standard library classes Pattern & Matcher too (imported with: import java.util.regex.*; ).

To show an example (ignore some of the vars converted to a string, these are irrelevant for the example)
```

	protected final Pattern [] patterns = new Pattern [] {
		Pattern.compile("[^\\S]*\\["+cats0.toString()+"\\][^\\S]*"),
		Pattern.compile("[^\\S]*"+cats1.toString()+"[^\\S]*=[^\\S]*(\\d+)[\\s#;]*"),
		Pattern.compile("[^\\S]*"+cats2.toString()+"[^\\S]*=[^\\S]*(\\w+)[\\s#;]*")
	};

```

To see how these can be used, through the Matcher class:
```

	public void parseLine(String line) {
		Matcher m=null;
		boolean keepGoing=true;
		int i;
		
		for(i=0; keepGoing && i<patterns.length; i++) {
			m=patterns[i].matcher(line);
			keepGoing=! m.matches();
		}
		
		if(!keepGoing)
			switch (i) {
				case 1 : addEntry(m.group(1)); break;
				case 2 : addEntry(m.group(1), Integer.parseInt(m.group(2))); break;
				case 3 : addEntry(m.group(1), m.group(2)); break;
			}
	}

```

---

### Post by dr.silly on 2008-09-20
thanks im using string.split method how do I get it to include all of the instance of the regex that are removed from the array. 

My array is looking like this:

```
["Text text text ", " Some more text ", " blah blah ", " blah ", " o and also ", "blah blah"]
```

instead of like this:

```
["Text text text ", "{1:more text}", " Some more text ", "{2:hi}", " blah blah ", "{$1}", " blah ", "{$2}", " o and also ", "{3}", " blah blah"]
```

---

