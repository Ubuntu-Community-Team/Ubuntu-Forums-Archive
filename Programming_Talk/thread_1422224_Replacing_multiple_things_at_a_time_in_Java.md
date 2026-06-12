---
title: "Replacing multiple things at a time in Java"
date: 2010-03-05
forum: Programming Talk
---

### Post by blazemore on 2010-03-05
I need to replace some characters in a given string with strings, eg. 'x' with "abcd", and 'y' with "bcde".
I can't use usual replace methods for this, because when I go to replace b, it will replace characters from the string that 'a' has already been replaced by.
I need both of these to operate on the same string at the same time, and not affect each others operation.
I hope I've made it clear, can anyone help?

---

### Post by Some Penguin on 2010-03-05
If X and Y have common letters, or X and Y can overlap with each other, you probably need to define how you're going to resolve such things.  e.g.


X = 'aaa';
b  = 'aab';

How do you intend to handle 'aaaaab' ?


I would suggest taking something like the following approach:
1- Use a StringBuilder to accumulate pieces of the result.
2- Use java.util.regex.Pattern / Matcher to build  a Matcher which will match *either*
    of the sequences you want.  Be sure to use \Q and \E to quote.
3- loop, initially on full string, using Matcher's find method.
    - if you find a match, use the 'start' and 'end' methods to find out where the match was.
    - Add everything that was before the match to the StringBuilder.
    - Add the replacement string to the StringBuilder.
    - Repeat on the rest of the string.
    - Once you don't find a match, well, add the entire string and you're done.

---

### Post by blazemore on 2010-03-05
> **Some Penguin said:**
> If X and Y have common letters, or X and Y can overlap with each other, you probably need to define how you're going to resolve such things.  e.g.


X = 'aaa';
b  = 'aab';

How do you intend to handle 'aaaaab' ?


it would go to aaaaaaab, until the next iteration (I'm doing this multiple times, the string will get longer and longer)

---

### Post by hyperAura on 2010-03-06
what u can do is parse each character and store it to an array.. after that u should check which letters need to be changed and store them in another array and then perform the changes at the appropriate positions in the array u have stored.. this way u won't have any problems.. :)

lets say u have  "xubuntu is crazy"
so if u are replacing x and y in this case u mark in the array position[0] and position[15] that are going to be changed each by the appropriate substitute.. after u are done with the whole document u perform the substitution based on the positions u have stored..

---

### Post by blazemore on 2010-03-07
> **hyperAura said:**
> what u can do is parse each character and store it to an array.. after that u should check which letters need to be changed and store them in another array and then perform the changes at the appropriate positions in the array u have stored.. this way u won't have any problems.. :)

lets say u have  "xubuntu is crazy"
so if u are replacing x and y in this case u mark in the array position[0] and position[15] that are going to be changed each by the appropriate substitute.. after u are done with the whole document u perform the substitution based on the positions u have stored..

That's a great solution! I'll do that one I think.
If I have an array of characters, and I am replacing one of them with a string, will I need to split that string up into another array of characters and reinsert them into the original array?

---

### Post by LKjell on 2010-03-07
I suggest you read something about Huffman codes

---

### Post by blazemore on 2010-03-07
> **LKjell said:**
> I suggest you read something about Huffman codes

Huffman codes are a way of encoding data for transmission in the smallest possible size. They're designed to minimise the number of bits needed to encode information, and have absolutely nothing to do with this problem, other than the fact that both are computer-science related.

EDIT: Did you mean HashMap?

---

### Post by LKjell on 2010-03-07
The principle between Huffman coding and what you are trying to do is similar. The function you want to make is bijective otherwise you can't do multiple things at the same time.

---

### Post by blazemore on 2010-03-07
Could someone give me a quick example of code?
For example replacing
all instances of 'X' with "XY"
all instances of 'Y' with "Y+"

---

### Post by LKjell on 2010-03-07
```
public class Blaze {
	public static void main (String [] args)
	{
		String str = "XYXYXYXYXYXY";
		String decode = "";
		Blaze blaze[] = new Blaze[str.length()];

		for (int i = 0; i < str.length(); i++) {
			if (str.charAt(i) == 'X')
				blaze[i] = new X();
			else
				blaze[i] = new Y();
		}
		for (Blaze b : blaze) {
			System.out.print(b.toString());
		}
	}
}

class X extends Blaze {
	private String x = "XY";

	public String toString(){
		return x;
	}
}

class Y extends Blaze {
	private String y = "Y+";

	public String toString(){
		return y;
	}
}
```

---

### Post by blazemore on 2010-03-07
> **LKjell said:**
> ```
public class Blaze {
    public static void main (String [] args)
    {
        String str = "XYXYXYXYXYXY";
        String decode = "";
        Blaze blaze[] = new Blaze[str.length()];

        for (int i = 0; i < str.length(); i++) {
            if (str.charAt(i) == 'X')
                blaze[i] = new X();
            else
                blaze[i] = new Y();
        }
        for (Blaze b : blaze) {
            System.out.print(b.toString());
        }
    }
}

class X extends Blaze {
    private String x = "XY";

    public String toString(){
        return x;
    }
}

class Y extends Blaze {
    private String y = "Y+";

    public String toString(){
        return y;
    }
}
```

That's an interesting way of doing it, with the classes.
Why not, instead of
```
  blaze[i] = new X();
```

just do
```
blaze[i] = "XY";
```
Wouldn't that be a lot easier and have the same output?

---

### Post by LKjell on 2010-03-07
I was using classes since I been thinking too much about OOP. But of course you do not need them. Here is another way. I merged them so the below one uses string class to do the work still the same.

```
public class Blaze {
	public static void main (String [] args)
	{
		String str = "XYXYXYXYXYXY";
		Blaze blaze[] = new Blaze[str.length()];

		for (int i = 0; i < str.length(); i++) {
			if (str.charAt(i) == 'X')
				blaze[i] = new X();
			else
				blaze[i] = new Y();
		}

		for (Blaze b : blaze) {
			System.out.print(b.toString());
		}

		////////////////////////////

		System.out.println();
		String decode[] = new String[str.length()];

		for (int i = 0; i < str.length(); i++) {
			if (str.charAt(i) == 'X')
				decode[i] = "XY";
			else
				decode[i] = "Y+";
		}

		for (String b : decode) {
			System.out.print(b);
		}
	}
}

class X extends Blaze {
	private String x = "XY";

	public String toString(){
		return x;
	}
}

class Y extends Blaze {
	private String y = "Y+";

	public String toString(){
		return y;
	}
}
```

---

### Post by blazemore on 2010-03-19
Solved the problem.
Took in an uppercase string, replaced the relevent parts with lowercase in each rule ("X" with "fx" for example)
Converted back to uppercase after doing ALL the rules, ready for the next iteration.
Ugly hack? or elegant solution?
You decide.

---

### Post by LKjell on 2010-03-19
Show us your code

---

### Post by blazemore on 2010-03-19
> **LKjell said:**
> Show us your code
str is a BufferedReader
```

...

while (str != null)
            {
                i++;
                axiom = replace(axiom, str);
                str = reader.readLine();
            }

...

``````

    static String replace(String axiom, String rule)
    /* 
     * This function takes an axiom, and a rule in the form
     *  x:foo
     *  where x should be replaced by foo
     */
    {
        // get the character we want to replace
        String replaceChar = Character.toString(rule.charAt(0));
        
        // get what we want to replace it with, in lowercase
        String replaceString = rule.substring(2).toLowerCase();
        
        // do the replacement
        axiom = axiom.replaceAll(replaceChar, replaceString);
        return string;
    }

```

---

### Post by blazemore on 2010-03-19
For those who are curious, working full LSystem code is here:
[http://pastebin.com/dpv8Bq0A](http://pastebin.com/dpv8Bq0A)

---

### Post by LKjell on 2010-03-19
What is the angle for?

---

### Post by blazemore on 2010-03-20
> **LKjell said:**
> What is the angle for?

That's for later. Same with the commented new GraphicDisplay

See, I'm writing an LSystem. The final string is like a set of rules, where each character represents a drawing instruction.
See here: [http://en.wikipedia.org/wiki/L-system](http://en.wikipedia.org/wiki/L-system)

---

